---
title: "Need help is installing gnome on Ubuntu Server 8.04"
date: 2009-07-28
forum: Server Platforms
---

### Post by Avinash.Rao on 2009-07-28
Dear all,

I am in the process of choosing a GUI for my ubuntu server 8.04 on Sun Fire Server 4150!! I have installed Ubuntu Server 8.04 - 64-bit edition from the CD and I am wondering what is the correct way to install Gnome Desktop.

I read few threads and many say, Desktop can be installed through apt-get install ubuntu-desktop? Won't this replace the server kernel? or what does this package have? 

I went through the Gnome site, they have released a new version of Gnome i.e 2.26 at [http://torrent.gnome.org/](http://torrent.gnome.org/) now what is the difference between this and the standard ubuntu desktop edition available in the ubuntu site?

I will be running LTSP + Samba + Squid on the server so i need to know the best way to do this and the correct tested version.

I also have the Ubuntu Desktop CD, can i install just the GUI from the CD from my server kernel? 

Many Thanks
Avinash

---

### Post by dragos2 on 2009-07-28
> **Avinash.Rao said:**
> Dear all,

I am in the process of choosing a GUI for my ubuntu server 8.04 on Sun Fire Server 4150!! I have installed Ubuntu Server 8.04 - 64-bit edition from the CD and I am wondering what is the correct way to install Gnome Desktop.

I read few threads and many say, Desktop can be installed through apt-get install ubuntu-desktop? Won't this replace the server kernel? or what does this package have? 

Many Thanks
Avinash

```

apt-get install xorg gnome-core gdm

```

---

### Post by wojox on 2009-07-28
This will install a scaled down version of gnome gui:

```
sudo aptitude install x-window-system-core gnome-core
```

For the full featured version of gnome gui:

```
sudo aptitude install x-window-system-core gnome
```

---

### Post by dragos2 on 2009-07-28
> **wojox said:**
> This will install a scaled down version of gnome gui:

```
sudo aptitude install x-window-system-core gnome-core
```For the full featured version of gnome gui:

```
sudo aptitude install x-window-system-core gnome
```

Why not xorg-core ?

Also he should install gdm to avoid policy kit hell as I have been told, but I did
not encountered problems without it.

There is still a small bug regarding fast-user-switch-applet which can be deleted
at first log in.

---

### Post by Avinash.Rao on 2009-07-28
so,   x-window-system-core gnome-core, xorg gnome-core gdm will give me the basic GUI?

I am wondering if i should install the gnome-desktop-environment to avoid installing everything manually, would that help.. ?

---

### Post by dragos2 on 2009-07-28
> **Avinash.Rao said:**
> so,   x-window-system-core gnome-core, xorg gnome-core gdm will give me the basic GUI?

I am wondering if i should install the gnome-desktop-environment to avoid installing everything manually, would that help.. ?

Sorry, but: are you nuts ?

It will destroy your server installation.

---

### Post by az on 2009-07-28
> **dragos2 said:**
> Sorry, but: are you nuts ?

It will destroy your server installation.

Huh?  It may not be the best solution but it won't destroy anything.

Will installing Ubuntu-desktop replace the server kernel?  No.  But if you have some funky hardware that is not working properly with the server kernel (such as some multimedia keyboards or game controllers...), then you may want to run your server with the desktop kernel.

The Ubuntu-desktop package is a meta package that depends on many other packages.  It will install quite a lot.  It may or may not be the best choice for you.  But it won't harm your server installation per se.


The version of Gnome in Ubuntu is the version that was current when that release of Ubuntu was published.  Gnome releases on the same schedule as Ubuntu, so the changes are most small incremental things.

Can you install the desktop from the live Desktop cd?  No.  The live cd does not contain packages for installation - just a complete system that can be run from CD and "transplanted" onto a hard drive as an installation - in that sense, it's all-or-nothing.  You can't install just one component using the live cd.

---

### Post by Krijk on 2009-07-28
Why don't you install xubuntu-desktop (sudo apt-get install xubuntu-desktop)?

It doesn't use a lot of RAM/CPU and is quick (and easy) to do. I use it all the time to install a desktop on top of the server (usually LTS). It hasn't given me any (performance) issues.

---

### Post by Avinash.Rao on 2009-07-28
Thank you for your replies. Then how do i get LTSP working?? just a plain Xwindows system is not enough for the setup we have here. 
We need Openoffice and many other applications? 

There has to be a proper solution for LTSP on Ubuntu Server 8.04. Everybody gives me different information. All i want is to run a server kernel on my Sun Fire Server, so that it can make use of the hardware completely and have proper window system for LTSP users?  I wouldn't have bothered about GUI if not for LTSP! 

I cannot afford to run a desktop kernel on a Sun Fire server! :D

Thanks



> **az said:**
> Huh?  It may not be the best solution but it won't destroy anything.

Will installing Ubuntu-desktop replace the server kernel?  No.  But if you have some funky hardware that is not working properly with the server kernel (such as some multimedia keyboards or game controllers...), then you may want to run your server with the desktop kernel.

The Ubuntu-desktop package is a meta package that depends on many other packages.  It will install quite a lot.  It may or may not be the best choice for you.  But it won't harm your server installation per se.


The version of Gnome in Ubuntu is the version that was current when that release of Ubuntu was published.  Gnome releases on the same schedule as Ubuntu, so the changes are most small incremental things.

Can you install the desktop from the live Desktop cd?  No.  The live cd does not contain packages for installation - just a complete system that can be run from CD and "transplanted" onto a hard drive as an installation - in that sense, it's all-or-nothing.  You can't install just one component using the live cd.

---

### Post by Avinash.Rao on 2009-07-28
I did this on a different machine but i am having to configure each and everything when it comes to LTSP? Its really driving me crazy.. 


> **Krijk said:**
> Why don't you install xubuntu-desktop (sudo apt-get install xubuntu-desktop)?

It doesn't use a lot of RAM/CPU and is quick (and easy) to do. I use it all the time to install a desktop on top of the server (usually LTS). It hasn't given me any (performance) issues.

---

### Post by az on 2009-07-28
> **Avinash.Rao said:**
> Thank you for your replies. Then how do i get LTSP working?? just a plain Xwindows system is not enough for the setup we have here. 
We need Openoffice and many other applications? 

There has to be a proper solution for LTSP on Ubuntu Server 8.04. Everybody gives me different information. All i want is to run a server kernel on my Sun Fire Server, so that it can make use of the hardware completely and have proper window system for LTSP users?  I wouldn't have bothered about GUI if not for LTSP! 

I cannot afford to run a desktop kernel on a Sun Fire server! :D

Thanks

So just install ubuntu-desktop package and don't worry about the desktop kernel.  Ubuntu-desktop doesn't install it.

And if you are getting conflicting information about LTSP, see here:
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by Avinash.Rao on 2009-07-28
Ok thank you! :)

> **az said:**
> So just install ubuntu-desktop package and don't worry about the desktop kernel.  Ubuntu-desktop doesn't install it.

And if you are getting conflicting information about LTSP, see here:
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by Avinash.Rao on 2009-07-29
How can i install Ubuntu-Desktop version 8.04 on a Ubuntu 9.04 Server edition.
If i do a apt-get ubuntu-desktop, it installs the latest version and that is 9.04!
But, i want Ubuntu Desktop 8.04 on my server.

Thanks


> **az said:**
> So just install ubuntu-desktop package and don't worry about the desktop kernel.  Ubuntu-desktop doesn't install it.

And if you are getting conflicting information about LTSP, see here:
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by Avinash.Rao on 2009-07-29
How do i install ubuntu 8.04 desktop on a ubuntu 8.04 or 9.04 server kernel? Is this possible??

---

### Post by az on 2009-07-29
> **Avinash.Rao said:**
> How do i install ubuntu 8.04 desktop on a ubuntu 8.04 or 9.04 server kernel? Is this possible??

No.

---

### Post by Avinash.Rao on 2009-08-01
Oh man!! There has to be a solution for server installations! I want to deploy LTSP on Server 8.04 and why isn't there an option to install Desktop 8.04?


> **az said:**
> No.

---

### Post by keymanu on 2009-08-03
Hello All

Here's something for you. i built a system from spare parts it's a 1.6Ghz chip with 256Mb ram.

I've try loading everything on it and what I could get on it was... ubuntu-server6.06 

now all i need is a gui for it. I loaded up gnome by aptitude installing gdm

it comes back can't stat /etc/X11/X no such file

any help?

---

