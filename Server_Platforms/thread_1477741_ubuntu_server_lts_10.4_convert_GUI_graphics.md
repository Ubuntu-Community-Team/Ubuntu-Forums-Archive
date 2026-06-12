---
title: "ubuntu server lts 10.4 convert GUI graphics"
date: 2010-05-09
forum: Server Platforms
---

### Post by salim.madni on 2010-05-09
hello,

how can i convert the ubuntu server into gui except gnome,xbuntu,kde enviornment. as they are very heavy. the purpose is basic trouble shooting like network card,internet browser,terminal command line shell prompt,login logout etc.

rgds

---

### Post by uberlinuxnerd on 2010-05-09
> **salim.madni said:**
> hello,

how can i convert the ubuntu server into gui except gnome,xbuntu,kde enviornment. as they are very heavy. the purpose is basic trouble shooting like network card,internet browser,terminal command line shell prompt,login logout etc.

rgds

XFCE isn't that heavy for modern systems... but if that is still to much try OpenBox

---

### Post by salim.madni on 2010-05-09
dear sir i have try the openbox blackbox, the machine restart but still text command line coming. how to start the services as setup installation has been done. guide further

---

### Post by gazj on 2010-05-09
> **salim.madni said:**
> dear sir i have try the openbox blackbox, the machine restart but still text command line coming. how to start the services as setup installation has been done. guide further

Have you installed xorg?

You may need to tell your server to start up in graphical mode, have not used ubuntu for years but most likely start at file /etc/inittab

---

### Post by salim.madni on 2010-05-09
this is what i was asking exactly how to do it? i have install already xorg also.

---

### Post by Mirko Scurk on 2010-05-09
Have you tried with issuing startx command.

#startx

Then let us know what is result.

If your X is properly configured you should get GUI.

---

### Post by rajabi on 2010-07-08
i typed startx
after i typed it said"the program 'startx' is currently not installed. you can install it by typing: sudo apt-get install xinit  "
i typed this order but after asking me my password it said:
" reading package tree...done
building dependency tree
reading state information....done
E: couldn't find package xinit 
"

now what shall i do? :-(

---

### Post by The Real Dave on 2010-07-09
[This Ubuntu Doc]("https://help.ubuntu.com/community/Installation/LowMemorySystems") will help you install a low memory Graphical Environment. I'd advice Openbox, as it's extremely light, and quite easy to configure. A suitable command would be something like

```
sudo apt-get install xorg openbox obconf openbox-themes tint
```

You can then start Openbox after logging in by excuting 

```
startx
```

[This guide]("http://urukrama.wordpress.com/openbox-guide/") should tell you everything you need to know about Openbox.

---

### Post by arrrghhh on 2010-07-09
Perhaps something like webmin or ebox would be better suited - it's a graphic interface for troubleshooting issues on the server, but remotely.  Obviously you need network connectivity to the device for this to be useful, so perhaps it is not for you...

But, it's usually not recommened to install a GUI over a -server based distro.  There has been some banter about this on the forums, and everyone is entitled to their own opinion - but I am of the opinion that if you need a GUI, install ubuntu-deskop.  If you want a stripped version of Ubuntu that'll run on bare hardware because it is stipped, install the -server edition.

---

