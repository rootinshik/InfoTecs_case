# Тестовое задание на стажировку в ИнфоТекс
## Задание:
Разработать систему машинного обучения, которая по списку статически импортируемых библиотек exe файла предсказывает, является ли этот файл зловредным.

Для выполнения задания предоставляются три выборки: обучающая, валидационная и проверочная. Выборки представлены в виде tsv файлов с тремя колонками:
1. `is_virus` – является ли файл зловредным
2. `filename` – имя файла для ознакомления
3. `libs` – через запятую перечисление библиотек, статически импортируемых этим файлом (использована библиотека LIEF для получения списка).

На обучающей выборке `train.tsv` следует обучать модель машинного обучения.

На валидационной выборке `val.tsv` требуется подсчитать, насколько хорошо модель справляется с файлами, которые она не видела при обучении.
```
True positive: 2
False positive: 20
False negative: 18
True negative: 60
Accuracy: 0.6200
Precision: 0.0909
Recall: 0.1000
F1: 0.0952
```

Решение основывается на самописном column transformer`е для отбора признаков. Так же учтена нежелательность ошибки второго рода, когда вирус остается незамеченным.
