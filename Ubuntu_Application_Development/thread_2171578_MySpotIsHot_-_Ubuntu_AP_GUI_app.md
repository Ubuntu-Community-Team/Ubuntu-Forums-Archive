---
title: "MySpotIsHot - Ubuntu AP GUI app"
date: 2013-08-31
forum: Ubuntu Application Development
---

### Post by vrabec-matej on 2013-08-31
Hello, I've written an application that controls hostapd to setup an Access Point. Runs with gtkdialog. I tested it only on Ubuntu 13.04 for the time being.

It's still a beta version and dunno if it works for everybody, for me it does, so any feedback would be appreciated :)

Anybody willing to test it, here it is:

[https://github.com/Krofek/MySpotIsHot](https://github.com/Krofek/MySpotIsHot)


Needed packages: 
subversion autoconf libgtk2.0-dev bison dnsmasq hostapd iw gksu
Also needs gtkdialog

Autoinstall everything:
Should also compile and install everything with an autoinstall script that downloads needed packeges, compiles and installs gtkdialog, since it isn't in the repositories anymore, makes an executable command (myspotishot) and a gnome menu item (pkexec myspotishot - adds policy):

```
curl https://raw.github.com/Krofek/MySpotIsHot/master/installgui.sh -L > installgui.sh && chmod +x installgui.sh && ./installgui.sh
```

It looks like this:

[IMG]https://raw.github.com/Krofek/MySpotIsHot/master/myspotishotgui.png[/IMG]

I hope i posted this in the right section.

Best regards, Krofek

---

### Post by mrdragon333 on 2013-11-05
Doesn't seem to work on my system. Can you please help me out.
> dav@dav-HP-Pavilion-g6-Notebook-PC ~ $ curl [https://raw.github.com/Krofek/MySpotIsHot/master/installgui.sh](https://raw.github.com/Krofek/MySpotIsHot/master/installgui.sh) -L > installgui.sh && chmod +x installgui.sh && ./installgui.sh  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  2719  100  2719    0     0   1829      0  0:00:01  0:00:01 --:--:--  1956
./installgui.sh: line 54: syntax error near unexpected token `<<<'
./installgui.sh: line 54: `<<<<<<< HEAD'




---

