# Kalman  
**Дослідження впливу параметрів**  
1. Матриця коваріації шуму процесу  
При збільшенні значення матриці коваріації шуму процесу фільтр Кальмана більше довіряє вимірюванням і менше передбаченням моделі.  
Q = 1:  
![](Q1.png)  
Q = 10:  
![](Q10.png)  
Q = 100:  
![](Q100.png)
2. Матриця коваріації шуму вимірювання  
У разі збільшення значення матриці коваріації шуму вимірювання знижується довіра до вимірювання, і навпаки, зменшення цього значення робить фільтр Калмана більш чутливим до нових вимірювань.  
R = 1:  
![](R1.png)  
R = 10:  
![](R10.png)  
R = 100:  
![](R100.png)
4. Початкова матриця коваріації  
Збільшення призводить до того, що фільтр на початку стає менш впевненим у своєму стані. При зменшенні фільтр більш впевнений у початкових оцінках, тому на початку реакції на зміни будуть повільнішими.  
P = 0,1:  
![](P01.png)  
P = 1:  
![](P1.png)  
P = 10:  
![](P10.png)  
5. Початкова оцінка стану  
Якщо початкова оцінка не відповідає реальному початковому стану, фільтру знадобиться більше часу на коригування. Якщо початкова оцінка близька до реального значення, фільтр швидко стабілізується і буде давати точніші результати від самого початку.  
x = 0:  
![](X0.png)  
x = 10:  
![](X10.png)  
x = 50:  
![](X50.png)  
6. Постійна складова сигналу  
При збільшенні зсуву фільтр зможе адаптуватися до нових середніх значень сигналу, але це може зайняти більше часу. Зменшення зсуву дозволить швидше відстежувати зміни.  
offset = 0:  
![](ffset0.png)  
offset = 10:  
![](offset10.png)  
offset = 50:  
![](offset50.png)  
7. Загальний час моделювання  
При збільшенні часу, фільтр має більше часу для стабілізації. Зменшення часу може призвести до того, що фільтр не встигне повністю "налаштуватися", і його оцінки залишаться неточними або нерівномірними.  
total_time = 1:  
![](total_time1.png)  
total_time = 5:  
![](total_time5.png)  
total_time = 0.3:  
![](total_time03.png)  
---  
**Порівняння результатів**  
1. Q = 1;  
   R = 10;  
   P = 1;  
   x = 0;  
   offset = 10;  
   total_time = 1;  
![](comb1.png)  
Помірне значення Q забезпечує збалансовану реакцію фільтра на зміни, дозволяючи йому адаптуватися до сигналу.  
Значення R вказує на відносно високу довіру до вимірювань, тому фільтр активно коригує свої оцінки на основі шумних вимірювань.  
Дисперсія шуму до фільтрації буде значною, тоді як після фільтрації вона зменшиться, оскільки фільтр коректує значення.  
2. Q = 0.1;  
   R = 1;  
   P = 0.1;  
   x = 5;  
   offset = 15;  
   total_time = 0.5;  
![](comb2.png)  
Низьке значення Q робить фільтр більш впевненим у своїх передбаченнях, призводячи до повільнішої адаптації до нових змін у сигналі.  
Низьке значення R означає, що фільтр надає велику довіру вимірюванням, що призводить до менших корекцій у прогнозах.  
Дисперсія після фільтрації може залишитися відносно низькою, оскільки фільтр не коригує результати сильно, а просто відображає шум.  
3. Q = 5;  
   R = 50;  
   P = 10;  
   x = 0;  
   offset = 0;  
   total_time = 5;  
![](comb3.png)  
Високе значення Q знижує впевненість фільтра в передбаченнях, що призводить до більшої чутливості до змін у вимірюваннях.  
Висока дисперсія в R призводить до того, що фільтр менш довіряє вимірюванням, що може викликати збільшення шуму в оцінках.  
Дисперсія до фільтрації буде високою, і хоча фільтр зменшить її, вона залишиться вищою через чутливість до шуму.  
4. Q = 1;  
   R = 1;  
   P = 5;  
   x = 10;  
   offset = 5;  
   total_time = 2;  
![](comb4.png)  
Помірне значення Q дозволяє фільтру адаптуватися до шуму, але не занадто агресивно.  
Низьке значення R дозволяє фільтру довіряти вимірюванням, що призводить до активного коригування.  
Дисперсія до фільтрації помітно знижується після фільтрації, оскільки фільтр забезпечує якісну корекцію.  
5. Q = 2;  
   R = 20;  
   P = 0.5;  
   x = 0;  
   offset = 12;  
   total_time = 3;  
![](https://github.com/MKroppp/Kalman/blob/main/Screenshots/comb5.png)  
Значення Q в 2 призводить до того, що фільтр зберігає певну чутливість до шуму, але не занадто агресивну.  
Високе R робить фільтр менш чутливим до вимірювань, але він не може покладатися на них.  
Перед фільтрацією дисперсія буде високою, але після фільтрації вона значно зменшиться, оскільки фільтр адаптується до зсуву сигналу.  
