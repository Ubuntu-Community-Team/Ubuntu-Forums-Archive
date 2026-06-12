---
title: "xscreensaver will not start when unity starts"
date: 2012-10-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by odror on 2012-10-11
I followed the direction in [http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html](http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html)

In order to enable xscreensaver.
> nstall XSreenSaver with following commands:
sudo apt-get remove gnome-screensaver
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra

create file for autostart:

sudo gedit /etc/xdg/autostart/screensaver.desktop

copy and paste the following code in file:

[Desktop Entry]
Name=Screensaver
Type=Applicaton
Exec=xscreensaver -nosplash


but xscreensaver will not start on stafrtup. I can start it manualy after startup. Any iseas why and how to fix it.
Thanks

---

### Post by pqwoerituytrueiwoq on 2012-10-12
does it showup under 
this is in my /etc/xdg/autostart/xscreensaver.desktop
```
Exec=xscreensaver -no-splash
TryExec=xscreensaver

```
i think your issue is this
```
Exec=xscreensaver -no-splash - mine
Exec=xscreensaver -nosplash - yours
```

---

### Post by odror on 2012-10-12
> **pqwoerituytrueiwoq said:**
> does it showup under 
this is in my /etc/xdg/autostart/xscreensaver.desktop
```
Exec=xscreensaver -no-splash
TryExec=xscreensaver

```
i think your issue is this
```
Exec=xscreensaver -no-splash - mine
Exec=xscreensaver -nosplash - yours
```

I have tried it the way you did it. I still cannot get xscreensaver to start with unity.

In fact I have checked. -nosplash and -no-splash both work fine on a command line.

---

### Post by pqwoerituytrueiwoq on 2012-10-12
try this for the command
```
bash -c "while [ 0`pidof xscreensaver` -eq 0 ];do xscreensaver -no-splash &;sleep 5;done"
```

---

### Post by odror on 2012-10-12
> **pqwoerituytrueiwoq said:**
> try this for the command
```
bash -c "while [ 0`pidof xscreensaver` -eq 0 ];do xscreensaver -no-splash &;sleep 5;done"
```


I think you ment > bash -c "while [ 0`pidof xscreensaver` -eq 0 ];do xscreensaver -no-splash &sleep 5;done"
or > bash -c "while [ 0`pidof xscreensaver` -eq 0 ];do xscreensaver -no-splash ;sleep 5;done"

Any way either one works well in terminal but not at statrtup

---

### Post by odror on 2012-10-12
I would like to add that when I replace replace the screensaver.desktop with

> [Desktop Entry]
Name=Screensaver
Type=Applicaton
Exec=bash -c "sleep 20; xterm"
NoDisplay=false


I do not see an xterm after 20 seconds. I think that this startup file is being ignored. does any one know why and how to fix it.

Thanks

---

### Post by pqwoerituytrueiwoq on 2012-10-12
[FONT=Courier New]chmod +x[/FONT] it, unity may require that xfce does not at least in that folder
i attached the desktop file i have on my xubuntu install for xscreensaver
btw i did not make a typo in my 1 line script above, the & is to let the script run without waiting on xscreensaver to exit

---

### Post by odror on 2012-10-12
> **pqwoerituytrueiwoq said:**
> [FONT=Courier New]chmod +x[/FONT] it, unity may require that xfce does not at least in that folder
i attached the desktop file i have on my xubuntu install for xscreensaver
btw i did not make a typo in my 1 line script above, the & is to let the script run without waiting on xscreensaver to exit

I tried the +x it did not help. None of the other apps is +x.  I still think that the start-up command and probably others are being ignored. I do not know why.  (off the subject your typo error was typing &; you probably meant &. & acts like ;. so you do not need it. otherwise you get an error as I did when I tried it.)

---

### Post by pqwoerituytrueiwoq on 2012-10-12
probably needed a space between the & and ;

---

### Post by rburkartjo on 2012-10-12
i have never gotten xscreensavers to start in unity. can do it in xubuntu or xfce though, go figure

---

