---
title: "HOW-TO restart apache2 when give you &quot;Unable to open logs&quot;"
date: 2007-01-02
forum: Server Platforms
---

### Post by soheil.moradi on 2007-01-02
Hello everybody,
I came and wanna learn you a little...

Maybe you couldn't restart or start Apache2 in the Ubuntu or other OS...

in the Ubuntu you should do following commands:

```
locate ports.conf
```

Now give you following results:

[B]***
/etc/apache2/ports.conf
****[/B]

ok, you should go to **ports.conf** located directory with follow command:

```
cd /etc/apache2/
```

Next you should edit ports.conf with a editor, I use nano to edit this file with follow command

```
sudo nano ports.conf
```

Next you should replace follow line with everything in the "ports.conf":

[PHP]Listen 127.0.0.1:8080[/PHP]

**Also You can replace xxx.xxx.xxx.xxx:8080 with 127.0.0.1:8080**

OK, now exit this file with pressing "Ctrl+X" » Y » <ENTER>

Next you should start your apache server with follow command:

```
sudo /etc/init.d/apache2 start
```

Enjoy;

Visit my website and help me with your comments: :KS  [http://www.irtik.com]("http://www.irtik.com")

---

