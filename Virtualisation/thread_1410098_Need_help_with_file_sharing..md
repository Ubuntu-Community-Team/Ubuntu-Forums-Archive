---
title: "Need help with file sharing."
date: 2010-02-18
forum: Virtualisation
---

### Post by GARoss on 2010-02-18
iMac OS X 10.6.2 Host
VirtualBox 3.1.4 PUEL
WinXP Guest
Ubuntu Guest

Here's what I can do. In WinXP Guest I can connect to USB card reader & shared folder on Mac Host. No sweat!

In Ubuntu Guest I cannot connect to either of them but they are listed in VirtualBox VM/Devices.
I've read this;
[http://forums.virtualbox.org/viewtopic.php?t=8669#p33944](http://forums.virtualbox.org/viewtopic.php?t=8669#p33944)
It basically says USB card reader is plug & play, then points to the Ubuntu site for further assistance where they assume you have an Ubuntu host, not another OS host, trying to connect. So no help there.

For folder sharing, following this tutorial 
[http://forums.virtualbox.org/viewtopic.php?f=3&t=15868](http://forums.virtualbox.org/viewtopic.php?f=3&t=15868)
just gives me errors & after reading other post on the net, gives them errors, too.

Sorry, but I don't get it. It would seem these would show up on Ubuntu in Places/Network, not stuck in a folder some place.
I'm too old I guess!;) Need a step by step how-to.

All suggestions are appreciated.

---

### Post by GARoss on 2010-02-18
Made some progress with USB card reader. It does work, but it's tricky. 
All along, I've had the USB card reader plugged in. Naturally, Mac (Host) is reading it so Ubuntu (Guest) can't.
The way I got it to work was to unmount/eject the card reader from Mac (card reader is still plugged in to USB), then in VB/Devices find the shared USB device & check it, then unplug the USB card reader (make sure your mouse is activated in the Ubuntu window, then replug in the USB card reader. It takes a few seconds but opens a window. This doesn't always work the 1st time but eventually it will.
HTH some other lost soul!:D

---

### Post by SecretCode on 2010-02-18
USB devices should work without problems in an Ubuntu guest. Just be aware that if you attach a USB device to a guest, it disappears from the host without any warning. Not good if you were writing data to it! But this happens for any guest.

Shared folders: I presume you have successfully installed the vbox guest additions in the Ubuntu guest. Folder sharing requires this!

Automatic mounting of shared folders does not happen, though. You need to mount them with a mount command, or by editing /etc/fstab.
E.g.
```
sudo mount -t vboxsf share ~/host
```
as explained in your second link.

---

### Post by GARoss on 2010-02-18
> **SecretCode said:**
> USB devices should work without problems in an Ubuntu guest. Just be aware that if you attach a USB device to a guest, it disappears from the host without any warning. Not good if you were writing data to it! But this happens for any guest.

Shared folders: I presume you have successfully installed the vbox guest additions in the Ubuntu guest. Folder sharing requires this!

Automatic mounting of shared folders does not happen, though. You need to mount them with a mount command, or by editing /etc/fstab.
E.g.
```
sudo mount -t vboxsf share ~/host
```
as explained in your second link.

Thanks,
I'm missing something (I said I was old!;) ). The shared folder in Mac (host) is called *vbshare*. So, I typed in terminal;

```
sudo mount -t vboxsf share ~/vbshare
```

and get;

```
/sbin/mount.vboxsf: mounting failed with the error: No such file or directory
```

What am I missing or doing wrong?](*,)
Thanks

---

### Post by Morbius1 on 2010-02-18
To automount the host shared directory you might want to try this in the Ubuntu guest:

Open **Terminal**
Type **mkdir /home/gaross/Host**
[COLOR=Blue]*Changing gaross to your actual user name*[/COLOR]

Type **gksu gedit /etc/fstab**
Add the following line to fstab:
```
vbshare /home/gaross/Host vboxsf rw 0 0

```Save the file, exit gedit, and back in the Terminal

Type [B]sudo mount -a
[/B]
You should be able to access your vbshare folder through [B]/home/gaross/Host

[/B]I'm assuming here that the name you gave the mac host shared directory is: vbshare

[COLOR=Blue]Edit: Sorry. In my haste I left one option out of that line in fstab. It should read:[/COLOR]
```
vbshare /home/gaross/Host vboxsf rw,[COLOR=Blue]uid=1000[/COLOR] 0 0

```

The uid=1000 will make you the owner of the mount point and all files will have you as the owner.
To make sure that uid=1000 is correct for you open a Terminal and type: **id**

---

### Post by GARoss on 2010-02-18
> **Morbius1 said:**
> To automount the host shared directory you might want to try this in the Ubuntu guest:

Open **Terminal**
Type **mkdir /home/gaross/Host**
[COLOR=Blue]*Changing gaross to your actual user name*[/COLOR]

Type **gksu gedit /etc/fstab**
Add the following line to fstab:
```
vbshare /home/gaross/Host vboxsf rw 0 0

```Save the file, exit gedit, and back in the Terminal

Type [B]sudo mount -a
[/B]
You should be able to access your vbshare folder through [B]/home/gaross/Host

[/B]I'm assuming here that the name you gave the mac host shared directory is: vbshare

[COLOR=Blue]Edit: Sorry. In my haste I left one option out of that line in fstab. It should read:[/COLOR]
```
vbshare /home/gaross/Host vboxsf rw,[COLOR=Blue]uid=1000[/COLOR] 0 0

```

The uid=1000 will make you the owner of the mount point and all files will have you as the owner.
To make sure that uid=1000 is correct for you open a Terminal and type: **id**

Thanks. Yes, it's uid=1000. Did as you said & got */sbin/mount.vboxsf: mounting failed with the error: Protocol error*

Sorry but I don't have the experience to work through this.

---

### Post by GARoss on 2010-02-18
Morbius1,
I've got it working!:popcorn: I had 2 folders as shared. VB/Devices must have the desired folder **highlighted** for this to work. Made that change it it's working. Now I need to keep it permanent.
Thanks!

---

### Post by SecretCode on 2010-02-19
> **GARoss said:**
> Thanks,
I'm missing something (I said I was old!;) ). The shared folder in Mac (host) is called *vbshare*. So, I typed in terminal;

```
sudo mount -t vboxsf share ~/vbshare
```

and get;

```
/sbin/mount.vboxsf: mounting failed with the error: No such file or directory
```

What am I missing or doing wrong?](*,)
Thanks

Looks like you've got it sorted via fstab ... but what you were doing wrong with the mount command was putting the share name in the wrong place. Should have been:

```
sudo mount -t vboxsf vbshare ~/host
```
where ~/host is some (empty) directory you've created.

---

