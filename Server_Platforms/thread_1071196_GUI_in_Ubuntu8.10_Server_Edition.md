---
title: "GUI in Ubuntu8.10 Server Edition"
date: 2009-02-15
forum: Server Platforms
---

### Post by Gaurang02 on 2009-02-15
HI;

I installed Ubuntu8.10 server edition in my pc.When i start pc so i got the command prompt for sudo code...

and i want to GUI in this Edition so how can i get it...?


Waiting for reply..

Thanks
Regards
Gaurang

---

### Post by kerry_s on 2009-02-15
you really need to be more detailed, which gui do you want, are you talking full blown desktop, just the basics or you want a light window manager?

will give you a login manager and xfce4:
**sudo apt-get install xorg gdm xfce4**

reboot and you'll get a log in screen.

---

### Post by spinanicky on 2009-02-16
Why would you want the GUI on the server... you might as well just get the standard ubuntu and install LAMP?!

---

### Post by steveneddy on 2009-02-16
For the Ubuntu Desktop, in terminal run

```
sudo apt-get install ubuntu-desktop
```

start and stop the GUI via command line by

```
sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm stop
```

---

