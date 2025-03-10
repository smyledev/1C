## Обращение к элементам, реквизитам формы

Если реквизит формы имеет простой тип - Строка, Число, Дата, то получить значение реквизита можно просто по имени:
```bsl
Текст = НаименованиеТовара; // Наименование товара - это реквизит формы
```

Однако, таким образом невозможно получить реквизиты "сложного" типа - ТаблицаЗначений, ДеревоЗначений. Чтобы получить значение реквизита со "сложным" типом, нужно воспользоваться функцией РеквизитФормыВЗначение():
```bsl
ТекущаяТаблица = РеквизитФормыВЗначение("ВыбранныеОбъектыСтроительства");
```

Для установки значения "сложного" реквизита, можно воспользоваться функцией ЗначениеВРеквизитФормы(<Значение>, <ИмяРеквизита>), оба параметра обязательны.


> Функции РеквизитФормыВЗначение() и ЗначениеВРеквизитФормы() доступны только на Сервере.



## Объект

Строго говоря, такого ключевого слова в пределах формы нет. Просто, когда создается форма, например, форма элемента, 1С автоматически создает на форме реквизит с именем Объект. Через данный реквизит доступны свойства текущего объекта, который редактируется на форме.

Например, можно получать ссылку на текущий элемент справочника:
```bsl
СсылкаНаТекущийЭлемент = Объект.Ссылка;
```

или, более полная запись:

```bsl
СсылкаНаТекущийЭлемент = ЭтаФорма.Объект.Ссылка;
```


## ЭтотОбъект

Содержит сам объект. Предназначено для получения объекта в модуле объекта или модуле формы. 

Использование: Только чтение. 



## Установка заголовка
```bsl
УстановитьКраткийЗаголовокПриложения("Заголовок");
```

## Показать оповещение
```bsl
ПоказатьОповещениеПользователя("Какой-то текст уведомления");
```

## Показать предупреждение
```bsl
ПоказатьПредупреждение(, "Расчет не выполнен!");
```

##  Ввод данных от пользователя 
```bsl
Ответ = ВвестиСтроку("Введите данные:");
```

## Вопрос пользователю
```bsl
Если Вопрос("Загрузить?", РежимДиалогаВопрос.ДаНет) = КодВозвратаДиалога.Да Тогда ... КонецЕсли
```

##  Открытие каталого
```bsl
Режим = РежимДиалогаВыбораФайла.ВыборКаталога;
ДиалогОткрытияФайла = Новый ДиалогВыбораФайла(Режим);
ДиалогОткрытияФайла.ПолноеИмяФайла = КаталогВыгрузки;               
ДиалогОткрытияФайла.Заголовок = "Выберите каталог";	

Если ДиалогОткрытияФайла.Выбрать() Тогда
  КаталогВыгрузки = ДиалогОткрытияФайла.Каталог;
КонецЕсли;
```

##   Получение двоичных данных из временного хранилища и запись данных в файл
```bsl
ДвоичныеДанныеВыгруженногоФайла = ПолучитьИзВременногоХранилища(АдресВоВременномХранилище);
ДвоичныеДанныеВыгруженногоФайла.Записать(ПолноеИмяФайла);	
```

##  Запись текстовых данных в файл
```bsl
ЗаписьТекста = Новый ЗаписьТекста;
ЗаписьТекста.Открыть(ИмяФайлаМанифест);
ЗаписьТекста.Записать("VHF-Manifest-Version: 1.0");
ЗаписьТекста.Закрыть();
```
