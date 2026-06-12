---
title: "sudo or gksudo/kdesu"
date: 2006-12-28
forum: The Cafe
---

### Post by Frak on 2006-12-28
Do you use sudo or gksudo/kdesu?

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by dbbolton on 2006-12-28
sudo is two less keystrokes to worry about.

---

### Post by angkor on 2006-12-28
Where's the 'both' option on the poll? ;)

Usually I stick with sudo, but for graphical apps I use gksudo.

---

### Post by roachk71 on 2006-12-28
For some reason, programs and utilities which need kdesu won't work after sudo is used, so I bypass that problem using kdesu. Sudo isn't a problem in GNOME, though. :KS

---

### Post by shrimphead on 2006-12-28
I use both, depends whether I'm working graphically or on the command line

---

### Post by 3rdalbum on 2006-12-28
If it's a graphical program, I use gksudo. If it's text-based, I use sudo. I don't use kdesu anymore, as it takes too long to load on Gnome and I can't customise it.

---

### Post by MaximB on 2006-12-28
I use "sudo" only to install things and edit files... otherwise why would I need to use "su" anyway ?

---

### Post by juky on 2008-03-14
Since I am a newbie, I was not aware of gksudo... but thaks to this forum, I will use it more often!

Cheers!

---

### Post by aysiu on 2008-03-14
It really shouldn't be a matter of more or less often. It should depend on what kind of application you're running. For example: ```
sudo fdisk -l
``` or ```
sudo apt-get update
```

If it's a terminal application, you should use *sudo*. If it's a graphical application, you should use *gksudo* or *kdesu*. For example: ```
gksudo gdmsetup
``` or ```
kdesu konqueror
```

---

### Post by kevdog on 2008-03-14
I dont get the point of this poll.  The situations the commands are to be used are mutually exclusive not inclusive.  I guess my question would be if I were not using gnome or kde, what would the equivalent sudo statement be.  If I installed e17 and then wanted to open gedit or something similar, would I use sudo or gksu?

Can't you get by with gksu rather than gksudo?

---

### Post by aysiu on 2008-03-14
> **kevdog said:**
> I dont get the point of this poll.  The situations the commands are to be used are mutually exclusive not inclusive.  I guess my question would be if I were not using gnome or kde, what would the equivalent sudo statement be.  If I installed e17 and then wanted to open gedit or something similar, would I use sudo or gksu?

Can't you get by with gksu rather than gksudo?
For Gedit, you would use *gksudo*

---

### Post by kevdog on 2008-03-14
Is the requirement for gksu or kdesu specific to the window manager (kde vs metacity) or the desktop manager (gnome vs kde)?

---

### Post by aysiu on 2008-03-14
> **kevdog said:**
> Is the requirement for gksu or kdesu specific to the window manager (kde vs metacity) or the desktop manager (gnome vs kde)?
It's dependent on the toolkit the application uses. So if I launch KWrite in Gnome, I'll still do ```
kdesu kwrite
``` and not ```
gksudo kwrite
``` QT apps use *kdesu* and GTK apps use ```
gksudo
```

---

### Post by jobsonandrew on 2008-04-15
I just always use sudo.. I have only ever used gksudo when I followed a guide and wanted to do it by the letter...

Dont you get exactly the same result with just sudo? I dont get the point of gksudo :S

---

### Post by aysiu on 2008-04-15
> **jobsonandrew said:**
> 
Dont you get exactly the same result with just sudo? I dont get the point of gksudo :S No. Read this: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

