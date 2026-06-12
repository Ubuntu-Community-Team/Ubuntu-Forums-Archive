---
title: "Wordpress / PHP"
date: 2016-02-24
forum: Ubuntu Development Version
---

### Post by 0N3 on 2016-02-24
When I open my [http://localhost/wordpress](http://localhost/wordpress) I get the error
```
[COLOR=#000000][FONT=Times New Roman]Your PHP installation appears to be missing the MySQL extension which is required by WordPress.[/FONT][/COLOR]
```

I have checked my PHP.ini file and unchecked the extension=mysql & extension=mysqli I have also tried uncheck each one individually and restart apache and still this problem persists. I have installed lamp-server^, apache and mysql.Every forum I hav checked is saying it's my PHP.ini file but I have followed the instructions by unchecking the extension=mysql & extension=mysqli and I still can't access my wordpress.

---

### Post by SeijiSensei on 2016-02-24
Try this:
```
sudo apt-get install php5-mysql
```
Then restart Apache.

---

### Post by 0N3 on 2016-02-24
I have that installed it says it's the newest version

---

### Post by SeijiSensei on 2016-02-25
I'm assuming that MySQL is running.  You can check quickly by running the command
```
telnet localhost 3306
```
You should see
```
Trying ::1...
telnet: connect to address ::1: Connection refused
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

```
followed by some gibberish.

Let's also make sure that Apache is loading the MySQL extension.  Create a file called info.php in the website's root directory that contains the line:
```
<?php phpinfo() ?>
```

Now view that file from a browser.  Scroll down the page and make sure you see the mysql and mysqli sections of the report.

---

### Post by 0N3 on 2016-02-25
I was on 16.04 when this error occurred (clean install) I went back to 14.04 (clean install) and followed exact same procedures and it works as it always did perfectly fine. Maybe it's a bug in 16.04 that apache isn't loading the extensions of MYSQL. I am going to install 16.04 (clean install) again and double check this and thanks for your help SeijiSensei. I will post back later with the output of ```
telnet localhost 3306
``` I'll create the php file too and post back the information. Many thanks again!

---

### Post by 0N3 on 2016-02-25
Is this post posted in the wrong section of the forum or if it is a 16.04 issue report it in the 16.04 sub forum?

---

### Post by howefield on 2016-02-25
> **0N3 said:**
> Is this post posted in the wrong section of the forum or if it is a 16.04 issue report it in the 16.04 sub forum?

If you are dealing with 16.04, then yes, the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427"). Otherwise here is fine.

---

### Post by QIII on 2016-02-25
Moved to **Ubuntu Development Version**

---

### Post by 0N3 on 2016-02-25
Go raibh mile maith agat :)

---

### Post by howefield on 2016-02-25
> **0N3 said:**
> Go raibh mile maith agat :)

tá fáilte romhat

I believe :)

---

### Post by QIII on 2016-02-25
Yes...

Tá fáilte romhat!

(Most of the rest of the Irish I know is from my grandfather swearing and from dirty pub songs, so don't ask me for more!)

---

### Post by 0N3 on 2016-02-25
Yes / or as gaeilge "sea" pronounced sha

---

### Post by 0N3 on 2016-02-25
All is working now after a fresh install I have disabled some PPA's I use maybe that was an issue I will enable them and try reproduce the issue and take it from there. Thanks all for your help! Should I mark this as solved or wait and try reproduce the issue? This is my 3rd time installing wordpress on Ubuntu 16.04 and the only time successful so I am not sure if it is successful or not due to the PPA's so should I mark this solved?

---

