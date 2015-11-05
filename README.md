#include <iostream>
#include <windows.h>
#include <math.h>
#include <stdio.h>

using namespace std;

int main()
{
	SetConsoleOutputCP(1251);
	int n, m;
	//Здесь вводится размерность(n,m) и сами элементы массива
    cout<<"Введите размерность массива и его элементы: "<<endl;
	cin>>n>>m;
	int **mas = new int*[n];
	for (int i = 0; i < n; ++i)
		mas[i]=new int [m];
	for(int i=0; i<n; i++)
		for(int j = 0; j<m; j++)
			cin>>mas[i][j];
	//Здесь этот массив выводится на экран, можно сказать просто для красоты и удобства
	cout<<"Массив имеет вид: "<<endl;
	for (int i = 0; i < n; ++i)
	{
		for (int k = 0; k < m ; ++k)
		{
			cout<<mas[i][k]<< ' ';}
			cout << "\n";
	}
	//Седловые точки
	int min = 0;
	int max = 0;
	int *cmax= new int[3];
	int *rmin= new int[3];
	//Массив минимумов в строках
	 for(int i = 0; i<n; i++)
	 {
		int min= mas[i][0];
		for(int j = 0; j<m; j++)
			if(min>mas[i][j])
					min = mas[i][j];
					rmin[i]= min;
	 }
	//Массив максимумов в столбцах
	for(int j = 0; j<m; j++)
	 {
		int max = mas[0][j];
		for(int i = 0; i<n; i++)
			if(max<mas[i][j])
					max = mas[i][j];
					cmax[j]= max;
	 }
     //Результат
	 cout<<"Координаты седловых точек: ";
	 for(int i = 0; i<n; i++){
		for(int j = 0; j<m; j++){
			if(mas[i][j]==rmin[i] && mas[i][j]==cmax[j])
			{
			cout<<"("<<i+1<<","<<j+1<<")";
			}
		}
	 }

	for(int i=0;i<n;i++)
        delete []mas[i];
    delete []mas; cout<<endl;
	system("pause");
	return 0;
}

