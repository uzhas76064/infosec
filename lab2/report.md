
---
## Front matter
title: "Лабораторная работа №2"
subtitle: "Дискреционное разграничение прав в Linux. Основные атрибуты"
author: "Хватов Максим Григорьевич"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux

# Выполнение лабораторной работы

Захожу в учетную запись, созданную на предыдущей ЛР. Через терминал, используя команду ```useradd guest```  создаю нового пользователя с именем guest. Задаю пароль с помощью команды ```passwd guest```.

![Рис. 1](image/1.jpg){#fig:001 width=70%}

Вхожу в систему от имени guest и выполняю в терминале команды ```whoami``` ```id``` ```pwd```

![Рис. 2](image/2.jpg){#fig:002 width=70%}
![Рис. 3](image/3.jpg){#fig:003 width=70%}

Просматриваю файл /etc/passwd командой ```cat /etc/passwd```

![Рис. 4](image/4.jpg){#fig:004 width=70%}

![Рис. 5](image/5.jpg){#fig:005 width=70%}

uid - 1001
gid - 1001

Определяю существующие в системе директории командой ```ls -l /home``` и получаю список директорий. Установлены пава на запись чтение и выполнение(wrx).

![Рис. 6](image/6.jpg){#fig:006 width=70%}

Создаю в домашней директории поддиректорию dir1 командой ```mkdir dir1``` и проверяю права предыдущими командами и список директорий. Затем снимаю с директории dir1 все атрибуты командой ```chmod 000 dir1```


 ![Рис. 7](image/7.jpg){#fig:007 width=70%}

 При попытке создать файл в директории я получаю отказ из-за неимения прав администратора

  ![Рис. 8](image/8.jpg){#fig:008 width=70%}



|Операция|Минимальные права на директорию|Минимальные права на файл|
|-|--------|---|
|Создание файла|drwx|rwx|
|Удаление файла|drwx |rwx|
|Чтение файла| drwx|rwx|
|Запись в файл| drwx|rwx|
|Переименование файла|drwx|rwx|
|Создание поддиректории|d--x|drwx|
