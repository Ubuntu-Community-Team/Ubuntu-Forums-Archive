---
title: "I'm having trouble installing stuff with `sudo`."
date: 2005-06-25
forum: Repositories &amp; Backports
---

### Post by bttfpromo on 2005-06-25
I'm trying to install some stuff, but everytime I use sudo, it works, but when it asks for a password, I can't enter a password.

---

### Post by Xian on 2005-06-25
Are you saying that it rejects your password?
How and what are you trying to install?

---

### Post by bttfpromo on 2005-06-25
I'm trying to install my WUSB11 USB Adapter. But that's not really the point, the point is that sudo doesn't work at all. Also, It says:( [] = the blinking box)

```
Password:[]
``` 


I try to type, but it doesn't go through. So it just sits there blank.

---

### Post by Xian on 2005-06-25
[QUOTE=bttfpromo]But that's not really the point, the point is that sudo doesn't work at all. [/quote] 
Let's try it with something very common just to duplicate what you are experiencing on a command that I am more familiar with. Open a terminal and issue the command below. 

Does it freeze at the password line?
If so first check the obvious.....

* Is your numlock on?
* Is you caplock on?

```
$ sudo gedit /etc/fstab
```

---

### Post by bttfpromo on 2005-06-25
[QUOTE=Xian]Let's try it with something very common just to duplicate what you are experiencing on a command that I am more familiar with. Open a terminal and issue the command below. 

Does it freeze at the password line?
If so first check the obvious.....

* Is your numlock on?
* Is you caplock on?

```
$ sudo gedit /etc/fstab
```[/QUOTE]

No, it doesn't freeze it blinks. And Numlock is on.

---

### Post by Xian on 2005-06-25
[QUOTE=bttfpromo]No, it doesn't freeze it blinks. And Numlock is on.[/QUOTE]
So then this is the same behavior as before?
It still won't let you type or enter a password?

---

### Post by bttfpromo on 2005-06-25
Numlock was the problem. It works now. Anyway, is there anyone who knows how to install my Linksys WUSB11 v.2.6 adapter? I'm a Linux n00b.

---

### Post by Xian on 2005-06-25
Glad you got the sudo issue fixed. 
You may want to start a new thread regarding the WUSB11 config.

---

