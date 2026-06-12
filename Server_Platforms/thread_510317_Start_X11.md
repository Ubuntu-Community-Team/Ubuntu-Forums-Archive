---
title: "Start X11"
date: 2007-07-26
forum: Server Platforms
---

### Post by dpj23 on 2007-07-26
I running a test using Ubuntu Server 7.04...  I really would like to configure it to run X-11 for the software that I have to test out...  So, I stuck with one of 2 things...  

1.  edit the run level from 3 to 5

2. renaming the root password

3. starting x11

So, I guess I should start by asking the commands for changing the root password, the rest would just fall into place after that....

---

### Post by koenn on 2007-07-26
1- to go to runlevel 5 : 
```
init 5 
```
or
```
telinit 5
```
You'll probably need to do this with sudo, so ```
sudo telinit 5
```
I don't understand why you'd want this to start X, Ubuntu only uses 2 rl : maintenance mode (rl 1, root console) and rl 2 (everything, including X) - it only makes sense if you've customized the runlevels. 

To permanently change the default runlevel, you'd have to edit inittab, but i think that got replaced by upstart in newer then 6.06 releases so I don't realy know


2- 
```

sudo -s
passwd root
>enter new UNIX password
>enter new UNIX password
exit

```
You'll be asked for *your* password after the sudo -s. Then you'll have a root shell and you can change the passwd
Ubuntu's oficial polcy is NOT to do this. Are you shure you need to ?


3- These start your X window system - that's enough for GUI apps to show on screen.
```
startx
```
alternative : 
```
xinit
```


If you also installed a window manager, you may want to start that, eg
```
startfluxbox
``` This wil also start X

If you've installed a display manager (xdm, gdm, kdm) you can start X + the windows manager through the display manager : 
```
xdm
```

---

