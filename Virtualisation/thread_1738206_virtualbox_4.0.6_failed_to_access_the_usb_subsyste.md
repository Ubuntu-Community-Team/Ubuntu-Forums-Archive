---
title: "virtualbox 4.0.6 failed to access the usb subsystem"
date: 2011-04-24
forum: Virtualisation
---

### Post by Canaryguy on 2011-04-24
Hello,

I'm running Ubuntu 10.10 x32 and I couldn't use my Pendrive in my virtual operating system.

For those having the same problem as I had with usb devices:

1º Download and install Virtualbox from [www.virtualbox.org](www.virtualbox.org)
2º Download and install extension pack from the same site.
3º Once installed open the Virtualbox

When I tried to go to the option USB a window appeared saying: "Failed to access the usb sybsystem" If not, you can stop reading.

4º Go to the Accessories >  Terminal and introduce:
if [ "`grep vboxusers /etc/group|grep $USER`" == "" ] ; then sudo usermod -G vboxusers -a $USER ; fi

Press enter and introduce your login password. After that it seems that nothing happened.

5º Reboot your computer.

6º Connect your Pendrive.

7º Open Virtualbox and go to USB. Hopefully you won't see the message again.

8º Choose "Add filter from device" (its icon is a usb wire with the symbol + " And now the name of your Pendrive should appear. Select it and press OK

9º Run your guest operating system who should now detect the Pendrive.

10º I hope this was of some help.

---

### Post by Tsu jan on 2011-04-25
Or simply add yourself to group "vboxusers" from System > Administration > Users and Groups, and then log out and log in.

I remember that I needed to do that with older versions of VirtualBox too.

---

### Post by RJ-king on 2011-04-26
Hello,

I have the same problem too.
I'm running ubuntu 10.10 x64 and the linux kernel version is 2.6.35-29 and 2.6.35-28, I already in the "vboxusers" group and  install the extension pack.
But this problem is still happened, and it also happened in VirtualBox 3.2 too.

I don't know why because the problem wasn't happened before...
IS anyone use ubuntu 10.10 x64 or another version, and have the same problem too?

---

### Post by blujay on 2011-04-26
```
$ groups
```  If vboxusers isn't listed...```
$ sudo adduser $USER vboxusers
```

You could rewrite your bash one-liner like this, much simpler:

```
$ if ! groups | grep vboxusers; then sudo adduser $USER vboxusers; else echo "You're already in vboxusers.  Must be a different problem."; fi
```

Thanks for posting this; I don't know how I got removed from vboxusers.

---

### Post by aeus on 2011-04-27
> **Canaryguy said:**
> Hello,

I'm running Ubuntu 10.10 x32 and I couldn't use my Pendrive in my virtual operating system.

For those having the same problem as I had with usb devices:

1º Download and install Virtualbox from [www.virtualbox.org]("http://www.virtualbox.org")
2º Download and install extension pack from the same site.
3º Once installed open the Virtualbox

When I tried to go to the option USB a window appeared saying: "Failed to access the usb sybsystem" If not, you can stop reading.

4º Go to the Accessories >  Terminal and introduce:
if [ "`grep vboxusers /etc/group|grep $USER`" == "" ] ; then sudo usermod -G vboxusers -a $USER ; fi

Press enter and introduce your login password. After that it seems that nothing happened.

5º Reboot your computer.

6º Connect your Pendrive.

7º Open Virtualbox and go to USB. Hopefully you won't see the message again.

8º Choose "Add filter from device" (its icon is a usb wire with the symbol + " And now the name of your Pendrive should appear. Select it and press OK

9º Run your guest operating system who should now detect the Pendrive.

10º I hope this was of some help.

Worked great with this guide and:
```
if ! groups | grep vboxusers; then sudo adduser $USER vboxusers; else echo "You're already in vboxusers.  Must be a different problem."; fi
```

Thanks!

---

### Post by yasir.elsharif on 2011-05-01
[SIZE=2]Thanks guys
That worked just fine with me :)
But what happened with this update why the users got removed from the group?
Anyway I am happy that I got my usb working again
Thanks
Yasir[/SIZE]

---

### Post by bmetz on 2011-05-01
I was drawn to this thread because VirtualBox USB stopped working after a recent series of Ubuntu updates (an effect of the updates were some other breakages, one catastrophic!).  Anyway, there was no problem with membership of the vboxusers group: it was still correct.  So the problem was elsewhere.

I don't know exactly what the problem was but I tried the classical approach: I re-installed VirtualBox and now USB works properly ;-)

I did notice during my snooping around that there weren't any device entries of the form /dev/vbox* when USB wasn't working.  Now that USB is working again, those entries exist, in particular some of the form /dev/vboxusb/*.  I am guessing that the problem was something to do with udev, in particular somehow related to /etc/udev/rules.d/10-vboxdrv.rules

---

### Post by gvazqu1 on 2013-02-22
Interesting, can't add myself (myusername_ to the vboxusers.... it says that I already am, but when I run 'groups' again it dows not show it.

```

myusername@myusername-lv01:~$ groups
myusername adm cdrom sudo dip plugdev lpadmin sambashare
myusername@myusername-lv01:~$ sudo adduser myusername vboxusers
The user `myusername' is already a member of `vboxusers'.
myusername@myusername-lv01:~$ groups
myusername adm cdrom sudo dip plugdev lpadmin sambashare
myusername@myusername-lv01:~$

```

---

### Post by gvazqu1 on 2013-02-22
Well, /etc/group says I do belong.....but VBox still complains that I am not. Who to believe?

```
myusername@myusername-lv01:~$ sudo egrep "^vboxusers" /etc/group 
vboxusers:x:125:myusername
```

> **gvazqu1 said:**
> Interesting, can't add myself (myusername_ to the vboxusers.... it says that I already am, but when I run 'groups' again it dows not show it.

```

myusername@myusername-lv01:~$ groups
myusername adm cdrom sudo dip plugdev lpadmin sambashare
myusername@myusername-lv01:~$ sudo adduser myusername vboxusers
The user `myusername' is already a member of `vboxusers'.
myusername@myusername-lv01:~$ groups
myusername adm cdrom sudo dip plugdev lpadmin sambashare
myusername@myusername-lv01:~$

```

---

