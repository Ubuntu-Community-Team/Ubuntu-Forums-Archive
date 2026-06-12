---
title: "USB Error In VirtualVox NS_ERROR_FAILURE (0x00004005)"
date: 2008-09-12
forum: Virtualisation
---

### Post by Clawson on 2008-09-12
Hello!

Sorry, i'm a new Ubuntu user (and so far it ROCKS!), but i'm trying to get a feel for the file structure and where everything is.

I have a my old copy of Windows Xp installed on a virtual machine within Ubuntu 8.04.  Everything seems to be working (LAN, Sound, Video) but i cannot get the USB drivers to work. I need windows xp to update my logitch remote for my TV and several other programs that do not work under WINE.  When i go to settings with in virtualbox i am getting this error.  I have also already read this thread: [http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745) in which i had to delete some # signs from a few lines in the /etc/init.d/mountdevsubfs.sh file.

Thanks for any and all help!

Matt


THE ERROR:

Failed to access the USB subsystem.

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}

---

### Post by jaime256 on 2008-09-14
I second this error. I just installed VirtualBox 2.0.2 and went into file, then preferences after running the program and then this error pops up. It looks like the program may be working, I still haven't added any vm's, but I also see this error without doing anything. So I don't know if the USB will work on the vm's. Do let me know if they work for you. Man, that registration window is annoying every time you open the program

Here's the picture of the error...

---

### Post by Clawson on 2008-09-18
Bump!

Does anyone have an idea on how to fix this error?

Thanks!

Matt

---

### Post by Clawson on 2008-09-18
Bump!

Does anyone have an idea on how to fix this error?

Thanks!

Matt

---

### Post by andysmith3 on 2008-09-18
helloreplica.com  provides a wide array of [Replica Watches](http://www.helloreplica.com/) and professional customer sevrice, our goal is to make every customer 100% satsfied. We are more than ready to show our unique prowess and fortes to gain our footing. And we also provide fast delivery service, we guarantee our listing price is lower than other competitor. welcome to oursite  [Replica Rolex Watches](http://www.helloreplica.com/)  [Rolex Watches](http://www.rolex2u.com/)   [replica rolex watches](http://www.rolex2u.com/) [replica rolex](http://www.rolex2u.com/)

---

### Post by QB89Dragon on 2008-09-18
Copy and paste this into a root (i.e. sudo bash) terminal
```

VBOX=$(grep vboxusers /etc/group | sed 's/vboxusers:x:\(.*\):.*/\1/')
mount -t usbfs -o devgid=$VBOX,devmode=664,nodev,noexec,nosuid none /proc/bus/usb
```

---

### Post by wrongman on 2008-10-24
is there a way to make it permanent? I've to add a line into fstab? will other programs be 'disturbed' by this?

---

### Post by metapaso on 2008-10-24
> **QB89Dragon said:**
> Copy and paste this into a root (i.e. sudo bash) terminal
```

VBOX=$(grep vboxusers /etc/group | sed 's/vboxusers:x:\(.*\):.*/\1/')
mount -t usbfs -o devgid=$VBOX,devmode=664,nodev,noexec,nosuid none /proc/bus/usb
```

This worked for me too.  Is there a way to make it permanent?

---

### Post by b0b138 on 2008-10-24
link in my sig :)

---

### Post by smbaf1 on 2008-11-07
thanks b0b138...fixed the issue i was having.  now just have to find the correct USB drivers for windows XP. Thanks again!

---

### Post by 186897 on 2008-11-13
Th!:popcorn:

---

### Post by 186897 on 2008-11-13
none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0

being XXX the group ID of your user when you look under System-Administration-Users&Groups for the group vboxusers.

and
 
sudo mount -a

---

### Post by hosch on 2009-02-21
I tried this as well - the first line went into my terminal just fine, but the second line is asking for me to be logged in as "root". I am the only one on the computer and am already the admin - is there a trick I am missing? less than a week on Linux so please be patient with my lack of knowledge:).

---

### Post by DouglasAWh on 2010-01-10
> **b0b138 said:**
> link in my sig :)

Your sig no longer appears to have a link...

---

### Post by medeiom on 2011-05-20
I tried this after upgrading to Ubuntu 11.04 (big mistake) and it did not work.  I get a message stating..
mount point /proc/bus/usb does not exist

Can anyone help?

Thanks so much

---

### Post by medeiom on 2011-05-20
I'm pretty new to Ubuntu and I have been trying relentlessly to figure this out.  Every time I insert a USB, I get the following..

 p, li { white-space: pre-wrap; }  VirtualBox is not currently allowed to access USB devices. You can change this by adding your user to the 'vboxusers' group. Please see the user manual for a more detailed explanation.




Now I tried looking for the vboxusers group, but it does not exist.  What am I doing wrong??:confused:

---

### Post by Hydrid on 2011-06-21
Result Code: 
NS_ERROR_FAILURE (0x00004005)

I have this error too! Can anyone help ? I hate when updates do things worst than better.

---

### Post by Hydrid on 2011-06-21
FIX this BUG Oracle !!! A lot of people have the same issue and its a shame for a so good program not the USB to WORK!

---

### Post by Presence on 2011-06-26
Here's how to get it working:

First thing you need to do is find out the id of the 'vboxusers' group. So:

```
grep vboxusers /etc/group
```

This will show something similar to vboxusers:x:XXX: where the XXX is the id of the group.

Now add this to /etc/fstab:

```
none /proc/bus/usb usbfs devgid=XXX,devmode=664,nodev,noexec,nosuid 0 0
```

Where the XXX is the id that you just found above.

The last thing to do is to add your user to the vboxusers group:

```
sudo usermod -a -G vboxusers user
```

Where user is your username.

---

### Post by anwarx on 2012-03-14
> **Presence said:**
> Here's how to get it working:

First thing you need to do is find out the id of the 'vboxusers' group. So:

```
grep vboxusers /etc/group
```This will show something similar to vboxusers:x:XXX: where the XXX is the id of the group.

Now add this to /etc/fstab:

```
none /proc/bus/usb usbfs devgid=XXX,devmode=664,nodev,noexec,nosuid 0 0
```Where the XXX is the id that you just found above.

The last thing to do is to add your user to the vboxusers group:

```
sudo usermod -a -G vboxusers user
```Where user is your username.

you man are the best it worked now like a charm with 11.0

thank you

---

### Post by anwarx on 2012-03-18
problem occur again :(

---

### Post by anwarx on 2012-03-18
i fixed this problem by install the extensions pack

---

