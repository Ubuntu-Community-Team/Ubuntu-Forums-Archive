---
title: "HOWTO: Autologin and Autostart XFCE (just pushing power button)"
date: 2005-05-02
forum: Tutorials
---

### Post by peekpt on 2005-05-02
[CENTER]**Are you tired off typing logins? Don't want to load heavy/waste of time login managers?** [/CENTER]

This guide let's you have autologin  and autostart for your XFCE:  :razz: 

Let's open a console and then create the file *autologin.c*

```
sudo nano autologin.c
```

and  paste this code inside (middle mouse button will paste the text you underline):

```

int main() {
     execlp( "login", "login", "-f", "your_user_here", 0);
 }

```

replace the string: your_user_here with the user you want to autologin. (ctrl+X to save) btw, use your prefered editor.

Let's compile.. you will need to have gcc installed:

```
sudo gcc -o autologin autologin.c
```

copy the compiled autologin file into /usr/local/sbin

```
sudo cp autologin /usr/local/sbin
```

now we need to edit the file /etc/inittab

```
sudo nano /etc/inittab
```

search for this:

```
1:2345:respawn:/sbin/getty 38400 tty1
```

put a # to comment this line and add this new line:

```

1:2345:respawn:/sbin/getty -n -l /usr/local/sbin/autologin 38400 tty1

```

it will look like this:
```

#1:2345:respawn:/sbin/getty 38400 tty1
1:2345:respawn:/sbin/getty -n -l /usr/local/sbin/autologin 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5

```

this will make the autologin stuff...



let's make the autostart:

```
nano .bash_profile
```

put this code on the bottom and save it

```

if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
    startxfce4
fi

```


then you just have to remove your login manager :
```

sudo apt-get remove gdm xdm kdm

```

reboot your machine 

I used this page as guide:

[http://www.dicas-l.unicamp.br/dicas-l/20030129.shtml](http://www.dicas-l.unicamp.br/dicas-l/20030129.shtml)

---

### Post by abowman on 2005-05-05
All I did was install Xfce with synaptic and then opened up the Login Screen Setup which can be found under Settings and clicked on Auto Login and selected a user.

---

### Post by anggarda on 2005-05-06
abowman, I think you missread the title of his thread. 

His howto is the *efficient way of loading xfce on a light system. 

The various, login managers, utilise memory in the background. 

Salut.

---

### Post by telmo on 2005-05-06
I'll try it... But if i screw my Ubuntu... I'LL KICK YOUR ASS!!! (gently!) :)
Just kidding!

---

### Post by peekpt on 2005-05-06
[QUOTE=telmo]I'll try it... But if i screw my Ubuntu... I'LL KICK YOUR ASS!!! (gently!) :)
Just kidding![/QUOTE]
 :grin: I just did this because it's no need to load gdm (lloading extra libs)  when you are the only user on the system... I have the autologin running on my laptop with a customized kernel. It boots fast and with the autologin faster.
xfce  rox... \\:D/

---

### Post by wirjo on 2005-05-30
[QUOTE=peekpt]:grin: I just did this because it's no need to load gdm (lloading extra libs)  when you are the only user on the system... I have the autologin running on my laptop with a customized kernel. It boots fast and with the autologin faster.
xfce  rox... \\:D/[/QUOTE]
 How do you bring back the login manager that you deleted?

---

### Post by ChrisNiemy on 2006-03-16
Works even better when you uses "startx" instead of "startxfce4" in the ~/.bash_profile 

Otherwise I got problems with font savings etc. 

 Looks like this (compared with first post here):
```

if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
    startx
fi

```

Thanks so much for this! Just great! Couldn`t think of this would work. So cool :D

---

### Post by conor on 2006-03-19
This is a great idea!   I have a few problems though.  When I turn on the computer the autologin works and then xfce4 will begin to load.  After a few milliseconds though it boots me out to the command line again and I have to type "sudo startx".  Then everything runs as root.  What did I do wrong?

[COLOR=ORANGE]Nevermind, I was wrong.  It works now.[/COLOR]

---

### Post by Haegin on 2006-03-29
If you are using a newer version of ubuntu you will need to
```

sudo apt-get install gcc-3.4

```
then replace
```

sudo gcc -o autologin autologin.c

```
with
```

sudo gcc-3.4 -o autologin autologin.c

```
so it compiles correctly

---

### Post by peschkaj on 2006-05-03
Wouldn't it also be possible to use something like sysv-rc-conf to remove gdm from the boot order and still use the method you described?

---

### Post by Haegin on 2006-05-05
No reason why not. Try it if you want?

---

### Post by blair on 2006-05-14
Thanks for the tip. I will try this. I do have a question however. I *DO* want a graphical login for one of my PCs to keep my kids out of my stuff. I did a Ubuntu server install and then loaded xfce-desktop. Now when my system boots, it only boots to a prompt. I can manually startx or startxfce, but how do I get an auto-login prompt on system boot up. I tried both xdm and gdm, but could get neither to work. Everything appears fine in init.d and I have a default-display-manager file created. 

Any suggestions appreciated. Thanks.

---

### Post by pvanhoof on 2013-01-22
> **Haegin said:**
> If you are using a newer version of ubuntu you will need to
```

sudo apt-get install gcc-3.4

```
then replace
```

sudo gcc -o autologin autologin.c

```
with
```

sudo gcc-3.4 -o autologin autologin.c

```
so it compiles correctly

Why don't you just use rungetty tty1 --autologin USERNAME instead of compiling a autologin.c yourself? Rungetty supports this stuff just fine.

---

### Post by pvanhoof on 2013-01-22
No idea why people here are recommending to compile a autologin.c file yourself. Just use rungetty in /etc/inittab:

Step 1 (on your minimal install):
> apt-get install rungetty

Replace in /etc/inittab
> 1:2345:respawn:/sbin/getty 38400 tty1

With
> 1:2345:respawn:/sbin/rungetty tty1 --autologin USERNAME

You can use exec in .bash_profile of USERNAME and you can also pass the command rungetty must execute (man rungetty) in the inittab file.

For systemd follow the guides on how to configure getty (getties) in systemd, and use rungetty instead of getty.

---

