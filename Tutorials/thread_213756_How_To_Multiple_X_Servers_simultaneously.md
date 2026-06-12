---
title: "How To: Multiple X Servers simultaneously"
date: 2006-07-11
forum: Tutorials
---

### Post by Iesos on 2006-07-11
**_Intro._**
I don't shutdown my Window Manager (WM) too often. And I would like to keep it that way. But I still wanted a way to explore linux, in this case with focus on all the available WM's out there. I wanted to try them without shuting down every program I got running (grafical program that is). So I wanted to start a new X Server on say tty8 (tty1-6 text, and tty7 already got one X server). And here is how you can do that.
There are also other ways to use this HowTo. Say you are a family of 5, then everyone can use their own WM on tty7-11, and it takes no time to switch.

Observe: I haven't used linux too long, and if you need help: I'm not sure if I can help. But this worked (kindof) flawless for me, but you follow this on your own risk.

**_HowTo._**
First we need to start an X server on tty8

```
$ startx -display :1 -- :1 vt8 &
```

If you get a message that sounds kind of like "X Server allready running on display :1.0" (or just ':1') Then your DISPLAY is allredy set to :1. To realy run this command failsafe, make sure that your what your DISPLAY is, that is run:

```
$ echo $DISPLAY
```

This chould say ':0' or ':0.0'. If it says something else, say ':n.0' or ':n' do as bellow. Also make sure that when yo press Ctrl + Alt + F7 your grafical interface shows up, and the same command with F1 to F6 gives text interfaces. If Ctrl + Alt + FN, where N is a number between 1 and 12, gives the grafical interface then run

```
$ startx -display :n+1 -- :n+1 vtN+1 &
```

(n+1 and N+1 means add one to your n-number that is ':0.0' becomes ':1' (or ':1.0') and tty7 becomes tty8 )

Now there is suppose to be a X Server running on ttyN (or tty8 in the special case) whitch you can check by pressing Ctrl + Alt + FN+1 (F8 ). It shoud just be a grey (or balck and white) background with a X as a mouse pointer.
Now you want some WM in ttyN+1, then you can run

```
$ gnome-session -display :1 &
```

for the special case, or just

```
$ 'windowmanager' -display :n+1 &
```

for the general case (where 'windowmanager' is the startup command for the desired windowmanager). Sometimes "$ 'windowmanager' :n+1" will suffice.

**_Problems._**
Now you should have your WM (gnome) running on ttyN+1 (tty8 ).
This sould be it. At least I can't see why it souldn't work. But for me it didn't. So below I will explain my problems and the solution.

**First.**
The first problem whas when I tried to start the X Server, it just went up for a few seconds, and then it crached (with a "Warning: locale not supported by C library, locale unchanged" error). If you get this problem, try running:

```
$ xinit -display :n+1 -- :n+1 vtN+1 &
```

which will start an X Server [COLOR="Red"]and a xterm[/COLOR] on ':n+1' ttyN+1. And with this xterm you can start your WM's by typing the WM's start command.

**Second.**
This was my second problem. When I went back to ttyN (tty7) no programs could start. When I ran for example

```
$ xterm
```

I got the following error

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
```

This means that my user lost the rights to use ':0.0' (':n'). You sould be able to fix this by just

```
$ sudo xhost +
```

I'm not sure if this gives any setbacks in security. The above command allows everyone to use all ':i' (where i \in \mathbb{Z}_+ ), or all displays (as one would say in english). 
(If anyone figures out how to use xhost so that one gives say user nils access to ':1' and user kajsa access to ':2', I would be glad to know.)

**_The end._**
Now it should work, if it doesn't take a look at

[http://www.ubuntuforums.org/showthread.php?p=1240642](http://www.ubuntuforums.org/showthread.php?p=1240642)

which is the thread I made when trying to figure out how this works. If that didn't help, maybe a part of my source

[http://gentoo-wiki.com/HOWTO_get_2_users_on_1_pc](http://gentoo-wiki.com/HOWTO_get_2_users_on_1_pc)

will help you. And If that doesn't, you are welcome to post here, and I'll see what I can do about it.

Have fun.

---

### Post by darkjavi on 2012-02-17
It's been some time since this post was written, but this method is still working(success on ubuntu 12.04 Alpha2).

Thanks Iesos, this is what i was looking for. 
Now I'll do some experiments; my usual setup has 4 screens (with xinerama enabled), that causes problems on some fullscreen games, so being able to launch a spare X server with only 1 screen would make my life easier :D

---

### Post by oldos2er on 2012-02-17
Closed, necromancy.

---

