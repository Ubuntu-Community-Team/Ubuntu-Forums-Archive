---
title: "Myserver.com (works) -- www.MyServer.com goes  to default"
date: 2009-02-13
forum: Server Platforms
---

### Post by mistypotato on 2009-02-13
Hi again,

I'm making great progress with my new ubuntu server.

I can get to my site using [http://MySite.com](http://MySite.com)

but not.....

http://[COLOR="Red"]www[/COLOR].MySite.com

Can anyone point me in the right direction?
I do have a line in my config that says....
ServerAlias [www.MySite.com](www.MySite.com) MySite.com

thx


*(MySite.com is a fictious name used here for example's sake)

---

### Post by gjoellee on 2009-02-13
> **mistypotato said:**
> Hi again,

I'm making great progress with my new ubuntu server.

I can get to my site using [http://MySite.com](http://MySite.com)

but not.....

[http://[COLOR=Red]www](http://[COLOR=Red]www)[/COLOR].MySite.com

Can anyone point me in the right direction?
I do have a line in my config that says....
ServerAlias [www.MySite.com]("http://www.MySite.com") MySite.com

thx


*(MySite.com is a fictious name used here for example's sake)

It works fine for me. It may be Firefox that is "tricking" you. Open Firefox and press CTRL+Shift+Delete and then select all the options and click on "Clear Proivate Data". That should do the trick. Then close Firefox using this command:
```
killall firefox
``` that should clear all firefox processes if you are having more then one process made by firfox running.

---

### Post by mistypotato on 2009-02-13
um...

I used "MySite.com" as an example.  It's really not my site nor do I have anything to do with it.

Maybe I should have used [www.ThisIsJustATestName.com](www.ThisIsJustATestName.com) :confused:

---

### Post by mistypotato on 2009-02-13
Also,

I don't "think" that leaving the default site there would matter would it?

If you have an alias set up, it's going to look for that and if it finds it, it will redirect to that site whether or not the 000-default site is still enabled or not?

In fact, it would seem to me that leaving the default site might be good to leave in place as a catch all for people who try to get to your web root?

---

### Post by mistypotato on 2009-02-13
Ok...Got it again.

It was a matter of using the wildcard [SIZE="5"]"*" [/SIZE]in front instead of "www",

---

### Post by Maheriano on 2009-02-13
Are you using bind9?

---

### Post by mistypotato on 2009-02-13
> **Maheriano said:**
> Are you using bind9?


I'm sorry.....I dont have a clue what bind9 is.

---

