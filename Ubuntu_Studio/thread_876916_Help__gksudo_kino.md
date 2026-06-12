---
title: "Help : gksudo kino"
date: 2008-08-01
forum: Ubuntu Studio
---

### Post by Dreamerman on 2008-08-01
Hi. After trying for 4 days I managed to get KINO to recognise my DV camcoder Panasonic NV-DS50A. Prior to victory, I could not get raw1394 loaded via KINO initiated the usual GUI way. The only way KINO can detect my camcoder is via gksudo kino

Is this the only way I can use KINO or there is a step I am missing ?

Thanks

---

### Post by opscure on 2008-08-01
Well something about the application needs root (or at least higher then user) privileges.  It's likely something to do with port access or permissions set to the app.

Luckily, you can create a desktop shortcut that points directly to gksudo appname.  This will just call gksudo prior to the app starting.  You can also add this to your Applications toolbar and replace the current one which is just calling the application without sudo.   

Just right click the desktop and add launcher with the gksudo command in the command field.  It will just prompt you for the password prior to starting.

---

### Post by Dreamerman on 2008-08-01
> **opscure said:**
> Well something about the application needs root (or at least higher then user) privileges.  It's likely something to do with port access or permissions set to the app.

Luckily, you can create a desktop shortcut that points directly to gksudo appname.  This will just call gksudo prior to the app starting.  You can also add this to your Applications toolbar and replace the current one which is just calling the application without sudo.   

Just right click the desktop and add launcher with the gksudo command in the command field.  It will just prompt you for the password prior to starting.

Thanks. This is exactly what I did. Managed to capture video for the 1st time & all good - video & audio. Now the next step is to think about how to get *.dv to DVD format.

Cheers

---

### Post by cotcot on 2008-08-02
Have you add your user to the group 'video' ? 
It also might have something to do with the permissions of /dev/raw1394 or /dev/dv1394 but i suggest not to change these unless you have informed yourself on google or so.

About the conversion of dv to dvd. Have a look in the kino export menu. You can select DVD as file format under the 'mpeg' tab.

There are there are many other solutions. (blender, kdenlive, dvdstyler, devede, qdvdauthor, avidemux, ....)

---

### Post by Dreamerman on 2008-08-02
> **cotcot said:**
> Have you add your user to the group 'video' ? 
It also might have something to do with the permissions of /dev/raw1394 or /dev/dv1394 but i suggest not to change these unless you have informed yourself on google or so.

About the conversion of dv to dvd. Have a look in the kino export menu. You can select DVD as file format under the 'mpeg' tab.

There are there are many other solutions. (blender, kdenlive, dvdstyler, devede, qdvdauthor, avidemux, ....)

Thanks for that. I managed to get most out of kino & quite happy. Cheers

---

### Post by Erlander on 2008-08-02
Have a look here:

[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)


and in particular at post 3 here:


[http://ubuntuforums.org/showthread.php?t=839369&highlight=gksudo+kino](http://ubuntuforums.org/showthread.php?t=839369&highlight=gksudo+kino)



Rob

---

### Post by Dai777 on 2008-08-03
To set up kino to use raw1394 on Ubuntu Hardy Heron do the following:
type in the following in to the terminal:

sudo gedit /etc/udev/rules.d/40-permissions.rules
type in your password

copy the line 
KERNEL=="raw1394",			GROUP="disk"
and paste it so the are are two of them.

now change the second line so it reads.
KERNEL=="raw1394",			GROUP="video"

and comment out the first line

reboot your system and Kino should be set up to capturte video.

here is an example:
# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
#KERNEL=="raw1394",			GROUP="disk"
KERNEL=="raw1394",			GROUP="video"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"

---

