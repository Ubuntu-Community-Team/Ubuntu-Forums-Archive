---
title: "How can I change the default date format (using LC_TIME)"
date: 2018-08-20
forum: Ubuntu, Linux and OS Chat
---

### Post by goron2 on 2018-08-20
[COLOR=#242729][FONT=Arial]How do I change the format of date command by modifying LC_TIME in locale?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Currently the **day of month** uses %e format. I need it to be displayed in %d format.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**Current Format:**
```
[FONT=Consolas]
date 

[/FONT][FONT=Consolas]Thu Aug 9 18:26:11 IST 2018

[/FONT]
```[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**Expected format:**[/FONT][/COLOR]
```
date

Thu Aug 09 18:26:11 IST 2018
```


Here is my **locale**

```
localelocale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_IN
LANGUAGE=
LC_CTYPE=en_IN
LC_NUMERIC="en_IN"
LC_TIME=en_DK
LC_COLLATE="en_IN"
LC_MONETARY="en_IN"
LC_MESSAGES="en_IN"
LC_PAPER="en_IN"
LC_NAME="en_IN"
LC_ADDRESS="en_IN"
LC_TELEPHONE="en_IN"
LC_MEASUREMENT="en_IN"
LC_IDENTIFICATION="en_IN"
LC_ALL=
```


**date_fmt** in **LC_TIME** section from from **/usr/share/i18n/locales**

```
date_fmt    "<U0025><U0061><U0020><U0025><U0062><U0020><U0025><U0065>/<U0020><U0025><U0048><U003A><U0025><U004D><U003A><U0025><U0053><U0020>/
<U0025><U005A><U0020><U0025><U0059>"
```

I have referred this [post]("https://ccollins.wordpress.com/2009/01/06/how-to-change-date-formats-on-ubuntu/") to modify the date output .

Im using **ubuntu server 16.04 xenial**

Please let me know how can i achieve this.

---

