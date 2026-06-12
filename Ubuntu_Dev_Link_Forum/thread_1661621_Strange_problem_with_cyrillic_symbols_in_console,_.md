---
title: "Strange problem with cyrillic symbols in console, mb bug?"
date: 2011-01-06
forum: Ubuntu Dev Link Forum
---

### Post by woto on 2011-01-06
Hi everyone, sorry for bad English. It's Ruby code.
**And later i tried same code on Python (of course with changes to Python language) and had same problem**

```
s = "&#1084;&#1080;&#1089;&#1090;&#1080;&#1082;&#1072;"

`touch #{s}`
`cat #{s}`
`cat < #{s}`

```
Can anybody tell why it's code fails? With

```
sh: cannot open &#1084;&#1080;&#65533;&#1090;&#1080;&#1082;&#1072;: No such file
```

But thic code works fine

```
s = "&#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1077;&#1090;" 
`touch #{s}` 
`cat #{s}` 
`cat < #{s}` 

```

Problem is only when Russian symbol '&#1089;' in the word and with symobol '<'

```
woto@woto-work:/tmp$ locale
LANG=ru_RU.UTF-8
LC_CTYPE="ru_RU.UTF-8"
LC_NUMERIC="ru_RU.UTF-8"
LC_TIME="ru_RU.UTF-8"
LC_COLLATE="ru_RU.UTF-8"
LC_MONETARY="ru_RU.UTF-8"
LC_MESSAGES="ru_RU.UTF-8"
LC_PAPER="ru_RU.UTF-8"
LC_NAME="ru_RU.UTF-8"
LC_ADDRESS="ru_RU.UTF-8"
LC_TELEPHONE="ru_RU.UTF-8"
LC_MEASUREMENT="ru_RU.UTF-8"
LC_IDENTIFICATION="ru_RU.UTF-8"
LC_ALL=

woto@woto-work:/tmp$ ruby -v 
ruby 1.8.7 (2010-01-10 patchlevel 249) [x86_64-linux] 

woto@woto-work:/tmp$ uname -a 
Linux woto-work 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 
UTC 2010 x86_64 GNU/Linux 

woto@woto-work:/tmp$ lsb_release -a 
No LSB modules are available. 
Distributor ID: Ubuntu 
Description:    Ubuntu 10.04.1 LTS 
Release:        10.04 
Codename:       lucid 

```

Another example

maybe this will be also useful to understand my problem

```
woto@woto-work:~/rails/avtorif$ touch &#1084;&#1080;&#1089;&#1090;&#1080;&#1082;&#1072;
woto@woto-work:~/rails/avtorif$ ruby -e "`cat < &#1084;&#1080;&#1089;&#1090;&#1080;&#1082;&#1072;`"
woto@woto-work:~/rails/avtorif$ ruby -e '`cat < &#1084;&#1080;&#1089;&#1090;&#1080;&#1082;&#1072;`'

sh: cannot open &#1084;&#1080;&#65533;&#1090;&#1080;&#1082;&#1072;: No such file
```

---

