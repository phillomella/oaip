## 4 лабораторная работа.Обратная польская запись.
Написать программу формирования ОПЗ и расчета полученного выражения. Разработать удобный интерфейс ввода исходных данных и вывода результатов. Язык программирования С++.
## Алгоритм кода.
Создается ОПЗ -обратная польская запись из строки.
Обратное польское выражение хранится в виде выходной строки, используемой в дальнейшем при генерации объектного кода. В ходе преобразования инфиксного выражения в обратное польское порядок всех переменных и констант не меняется, а порядок операторов выходной строки соответствует их приоритетам.
В main согласно варианту записываются значения и само выражение
(a+b)*(c-d)/(e) в инфиксной форме.
Создается стек для работы с ОПЗ.
Понадобится стек для переменных типа  char,так как исходное выражение получаем в виде строки.
Рассматривается поочередно каждый символ, если символ скобка ,то она помещается в стек. Если символ, находящийся на вершине стека имеет приоритет, больший или равный приоритету текущего символа, то извлекаем символы из стека в выходную строку до тех пор, пока выполняется это условие. Если стек все еще пуст, или находящиеся в нем символы имеют меньший приоритет, чем приоритет текущего символа, то помещаем текущий символ в стек.
Алгоритм на примере из варианта: (a+b)*(c-d)/(e)

Символ|Действие|Состояние стека после совершения действия
---|---|---
(| Помещается в стек|(
a| Переменная, помещается в выходную строку|+(
b| Переменная,помещается в выходную строку|+(+
)| Закрывающая скобка. Извлекаем из стека в выходную строку все символы, пока не встретим открывающую скобку. Затем уничтожаем обе скобки.|+
*| Знак операции, который имеет приоритет 3. Проверяем стек: на вершине находится символ '+', приоритет которого равен 2.Просто помещаем символ в стек |+*
(| Открывающая скобка. Помещаем в стек.|+*(|
|c| Переменная. Помещаем ее в выходную строку|+*(|
|d| Переменная. Помещаем ее в выходную строку|+*(-|
|)| Закрывающая скобка. Извлекаем из стека в выходную строку все символы, пока не встретим открывающую скобку.Затем уничтожаем обе скобки.|+|

Теперь вся входная строка разобрана, но в стеке еще остаются знаки операций, которые должны быть просто извлечены в выходную строку. Поскольку стек - это структура, организованная по принципу LIFO, сначала извлекается символ '*', затем символ '+'.

[Ссылка на видео с работой кода](https://drive.google.com/file/d/15VE6MmusfGUcUb3SptN7Q7c5ENCy1VDx/view?usp=sharing)