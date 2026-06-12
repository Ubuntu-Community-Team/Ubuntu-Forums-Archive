---
title: "How can we run X applications on Ubuntu Touch?"
date: 2016-01-10
forum: Ubuntu Phone and Tablet
---

### Post by ZICODIAN on 2016-01-10
I think that getting all of the standard X applications working is one of the absolutely key features that Ubuntu with Unity8 needs. I have seen some demonstrations that I suspect involve the use of a VNC setup, but what is the current best approach to doing this? Let's say I want to get a little PyQt application displaying in Unity8 or something as simple as xeyes working. How could I do this?

---

### Post by grahammechanical on 2016-01-10
Those demonstrations are using XMir and a Linux container (LXC).

The intention is to release a version of Ubuntu called Ubuntu Personal that is built on snappy Ubuntu core, runs on Mir, uses Unity 8, has transaction updates with the ability to roll back a failed system update and use snap packaging.

For Ubuntu Personal to come with all the standard applications that Ubuntu already has, the developers of the traditional applications will need to repackage their apps as snap packages. That will definitely not happen soon. The alternative is to run the deb packages in a Linux container for security and run the container on XMir. And it is those experiments that you are seeing.

I would like very much to see some kind of installable image that contains this code and can be updated over time into Ubuntu Personal. I thought that I had found that very thing with personal_x86.img but it has not been updated since 17th October. I now see that image as prove of concept.

This is what the developers are experimenting with

[https://launchpad.net/libertine](https://launchpad.net/libertine)

I cannot find any documentation for this project.

Regards.

---

### Post by krusty8 on 2016-02-08
You don't necessarily need LXC or Libertine for Xmir. Running xeyes is as simple as putting an xeyes.desktop file into /home/phablet/.local/share/applications

```
[Desktop Entry]
Name=xeyes
Type=Application
Terminal=false
Icon=/usr/include/X11/bitmaps/xlogo64
X-Ubuntu-Touch=true
X-Ubuntu-XMir-Enable=true
Exec=xeyes

```

Alternatively, you can change the Exec line to point to a shell script you write. That way you can, e.g., add some output redirection to help you debug problems. Or remove the X-Ubuntu-XMir-Enable line and start Xmir explicitly from your script. 

Have a look at the scripts here:
[LIST]
[*][http://forum.xda-developers.com/ubuntu-touch/help/easier-xmir-setup-t3303981](http://forum.xda-developers.com/ubuntu-touch/help/easier-xmir-setup-t3303981) 
[*][https://www.youtube.com/watch?v=XfMLzlki9XE](https://www.youtube.com/watch?v=XfMLzlki9XE) 
[/LIST]

---

### Post by grahammechanical on 2016-02-08
At some point in the not too distant future the Ubuntu for Devices OS will be converted to Snappy Ubuntu Core + Mir + Unity 8. When that happens applications that are not packaged as Snaps will not install. This is where Libertine/Puritin comes in. It is a snap. So it can be installed and it will install deb package applications and run them on Xmir but in a Linux container in order to comply with the Ubuntu for Devices security module.

This is what those videos were showing.

At present any application has the potential to access anywhere on the system. A lot depends on the good manners of the developer that applications are well behaved. Certain applications interact directly with the Xserver. But the X windowing system is going to be replaced. On Ubuntu it will be replaced by the Mir compositor. On other distributions it will be replaced by a compositor built to the Wayland protocol. When that happens those applications will need to run on Xmir or Xwayland. But the potential security vulnerabilities of those apps will remain.

On Ubuntu phone apps are very tightly controlled as to what they can access. On snappy Ubuntu core the kernel & the system are read only and apt-get does not work. 

The forth coming Ubuntu tablet is a convergence device. Plug in a monitor and we will be able to work with Firefox, Libreoffice & Gimp which are part of the limited set of Xapps available at present. Those apps will be running in a Linux container to keep them tightly under control. So, the purpose of the Linux container is security.

And it has been proved that Linux containers use a lot less system resources then regular virtual machines (VM) do. So, we can have multiple Linux containers available without a degradation of the user experience.

It is a neat solution that brings a great improvement to security in Ubuntu phones, tablets and in future the desktop.

Regards.

---

### Post by ShadowEO on 2016-02-08
> **krusty8 said:**
> You don't necessarily need LXC or Libertine for Xmir. Running xeyes is as simple as putting an xeyes.desktop file into /home/phablet/.local/share/applications

```
[Desktop Entry]
Name=xeyes
Type=Application
Terminal=false
Icon=/usr/include/X11/bitmaps/xlogo64
X-Ubuntu-Touch=true
X-Ubuntu-XMir-Enable=true
Exec=xeyes

```

Alternatively, you can change the Exec line to point to a shell script you write. That way you can, e.g., add some output redirection to help you debug problems. Or remove the X-Ubuntu-XMir-Enable line and start Xmir explicitly from your script. 

Have a look at the scripts here:
[LIST]
[*][http://forum.xda-developers.com/ubuntu-touch/help/easier-xmir-setup-t3303981](http://forum.xda-developers.com/ubuntu-touch/help/easier-xmir-setup-t3303981)
[*][https://www.youtube.com/watch?v=XfMLzlki9XE](https://www.youtube.com/watch?v=XfMLzlki9XE)
[/LIST]


Wow, it's great to see my tutorial linked here ^_^

I'm continuing to update that thread as I find more, this is an ongoing project for me until Convergence hits primetime and is comparable :)

---

