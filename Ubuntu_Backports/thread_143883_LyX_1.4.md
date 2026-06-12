---
title: "LyX 1.4"
date: 2006-03-13
forum: Ubuntu Backports
---

### Post by tassou on 2006-03-13
[http://www.lyx.org/](http://www.lyx.org/)

Nice improvements, could be very good for lyx users.

Thank you.

---

### Post by topyli on 2006-03-18
There are packages on the lyx.org site: [ftp://ftp.lyx.org/pub/lyx/bin/1.4.0/ubuntu/](ftp://ftp.lyx.org/pub/lyx/bin/1.4.0/ubuntu/)

---

### Post by whu on 2006-03-28
Yes but... it sould be nice to have it in universe... and I'm using amd64... ftp lyx site doesn't offer this package...

---

### Post by acorrigan on 2006-04-06
i agree, 

i'm and am64 + lyx user.  by the way does anyone know if this new version makes lyx not so ugly (compared to when it's in KDE or windows)

---

### Post by durruti on 2006-05-01
[QUOTE=acorrigan]i agree, 

i'm and am64 + lyx user.  by the way does anyone know if this new version makes lyx not so ugly (compared to when it's in KDE or windows)[/QUOTE]

It's better... they've redesigned the menus as well, so takes a bit of getting used to, finding where things were put, but I guess there's a logic to it.

---

### Post by Dryer Lint on 2006-05-02
Is there a way to make the binary .deb packages from the LyX homepage work on Dapper?

It has dependencies to a few libraries I have installed but the name is slightly different, so dpkg won't install them.

---

### Post by topyli on 2006-05-07
[QUOTE=Dryer Lint]Is there a way to make the binary .deb packages from the LyX homepage work on Dapper?
[/QUOTE]
There are instructions on the LyX wiki: [http://wiki.lyx.org/LyX/LyXOnDebian#toc6](http://wiki.lyx.org/LyX/LyXOnDebian#toc6)
1.4.1 is out with important bug fixes, so those of us who have built 1.4.0 will have to build again :)

EDIT: I successfully built packages as per the instructions above, but also noticed the wiki says that the Sid packages are also installable on Dapper: here's the sources.list line:

deb [http://lyxondebian.free.fr/](http://lyxondebian.free.fr/) sid main contrib non-free # (only qt frontend, only i386)

Matej's packages also include dvipost in case you need the change tracking feature: 

[http://matej.ceplovi.cz/progs/debian/lyx/](http://matej.ceplovi.cz/progs/debian/lyx/)

---

### Post by cpbl on 2006-05-15
> I successfully built packages as per the instructions above, but also noticed the wiki says that the Sid packages are also installable on Dapper: here's the sources.list line:

deb [http://lyxondebian.free.fr/](http://lyxondebian.free.fr/) sid main contrib non-free # (only qt frontend, only i386)

Not for me. I added the source but when upgrading lyx (even if I remove lyx first), I get:

```
 sudo apt-get install lyx-qt dvipost
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  dvipost: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu18 is to be installed
  lyx-qt: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu18 is to be installed
          Depends: libgcc1 (>= 1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
          Depends: libstdc++6 (>= 4.1.0) but 4.0.3-1ubuntu5 is to be installed
E: Broken packages

```

---

### Post by zipeppe on 2006-05-16
I have some throubles with lyx-gtk:

[http://ubuntuforums.org/showthread.php?t=176230]("http://ubuntuforums.org/showthread.php?t=176230")

---

### Post by zipeppe on 2006-05-16
I have some throubles with lyx-gtk:  ](*,) 

[http://ubuntuforums.org/showthread.php?t=176230]("http://ubuntuforums.org/showthread.php?t=176230")

---

### Post by topyli on 2006-05-23
[QUOTE=zipeppe]I have some throubles with lyx-gtk:  ](*,) 

[http://ubuntuforums.org/showthread.php?t=176230]("http://ubuntuforums.org/showthread.php?t=176230")[/QUOTE]

The GTK+ port is still experimental and guaranteed to be very unstable. FWIW, my LyX 1.4.1 packages for Dapper can be found here: [http://topyli.wordpress.com/packages/](http://topyli.wordpress.com/packages/)
Only the Qt frontend, the GTK one is broken and the XForms interface is way too obsolete :)

---

### Post by cpbl on 2006-05-24
> FWIW, my LyX 1.4.1 packages for Dapper can be found here: [http://topyli.wordpress.com/packages/](http://topyli.wordpress.com/packages/)

Thanks toplyi.
 Installing these two packages with 

```
 sudo dpkg -i ./lyx-common_1.4.1-1.lyx.org.1_i386.deb  ./lyx-qt_1.4.1-1.lyx.org.1_i386.deb 
```

worked! Finally I have LyX 1.4.x. However, using gdebi rather than dpkg to install them did not work, even though gdebi is the default program that Dapper suggests when downloading .deb in firefox... 

c

---

### Post by topyli on 2006-05-24
[QUOTE=cpbl]
However, using gdebi rather than dpkg to install them did not work, even though gdebi is the default program that Dapper suggests when downloading .deb in firefox... 
[/QUOTE]
The packages depend on each other. dpkg is able to sort it out because you're installing them both at once. gdebi will always complain when you try to install one of them alone.
Anyway, good to hear they work on somebody else's box besides mine :)

---

### Post by NicS on 2006-05-30
Works for me too..., thanks for the packaging!
Unfortunate that gtk port does not work. 
Lyx could get a bit of Gnome HIG, which is a desperate need for it IMHO

---

