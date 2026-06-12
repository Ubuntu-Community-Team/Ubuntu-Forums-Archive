---
title: "Ubuntu can't start! Please help"
date: 2016-05-17
forum: Server Platforms
---

### Post by Daniel_Schmid on 2016-05-17
Hello Guys! 


I have a problem and need very fast an answer! ...


First of all, sorry for my english it isn't my first languague.


My problem is, that my Server can't start.


The Server was on ubuntu server 15.10 and i upgraded it (via SSH) to ubuntu server 16.04.


So after that, the server started sucessfully.

Then i made a reboot ... and now it don't start - it boot in GRUB rescue.


So i typed ```
ls
```. It says me (hd0) , (hd0,msdos1) , (hd0,msdos5) , (hd2), (hd3) usw.


When i tried to type ```
ls (hd0)
``` or ```
ls (hd0,msdos1)
``` or ```
ls (hd0,msdos5)
``` it says "unkown Filesystem!".

The same for the other drives (only 1 work and there isn't eaven 1 File on it!



I tried the "programm" "startup repair" via CD ... it didn't work for me. 


Here is the log: [http://paste.ubuntu.com/16399349/](http://paste.ubuntu.com/16399349/)



I hope some of you can help me fast :)


But please don't use difficulte words in english ... and im a newbie in ubuntu / linux ^^




Greatings

---

### Post by Bashing-om on 2016-05-17
Daniel_Schmid; Hello ;

Assuming (!!) that this system is NOT raid, and that the root install is on the 1st partition of the 1st hard drive (hd0,msdos1) :
what results:
```

set prefix=(hd0,msdos1)/boot/grub
set root=(hd0,msdos1)
insmod linux
linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```

If it boots .. we re-install grub .

[INDENT][INDENT]maybe YES
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by darkod on 2016-05-17
Can you connect a monitor and keyboard to the server and take a look? It's best to do that and boot it with the live cd of Ubuntu Desktop. That will allow you to work on fixing it.

Also, from the boot-repair output it seems you have LVM, right? And at least 4-5 disks. Are you using all of them? Because the LVM seems to be only on one disk, and the others are not included...Very strange setup...

---

### Post by Daniel_Schmid on 2016-05-19
> **darkod said:**
> Can you connect a monitor and keyboard to the server and take a look? It's best to do that and boot it with the live cd of Ubuntu Desktop. That will allow you to work on fixing it.

Also, from the boot-repair output it seems you have LVM, right? And at least 4-5 disks. Are you using all of them? Because the LVM seems to be only on one disk, and the others are not included...Very strange setup...


Thank you for your answer!

Yes i can take a look at the server. 

About LVM ... i honestly don't know - if it is pre instaled on Ubuntu then maybe yes ... 

Yes im using all off these drives and i had not 1 Problem for over 8 months .... :/


You sayed, that i should boot from a live cd and work on the repair. 


Can you say me (as a newbie) what should i try to fix it?


Greatings

> **Bashing-om said:**
> Daniel_Schmid; Hello ;

Assuming (!!) that this system is NOT raid, and that the root install is on the 1st partition of the 1st hard drive (hd0,msdos1) :
what results:
```

set prefix=(hd0,msdos1)/boot/grub
set root=(hd0,msdos1)
insmod linux
linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```

If it boots .. we re-install grub .
[INDENT][INDENT]maybe YES[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



Thank you for you for your answer!


I will try it out and will write here if it worked or not :)

---

### Post by darkod on 2016-05-19
Honestly, your system is a mess... You have formatted sda, sdd and sdf directly without even creating partition on them. Usually you create partition on the disk, one or more of them, and you format the partitions not the whole disk.

But that is not so important right now.

I would try moving the OS disk to the first SATA port on the board (so that it becomes /dev/sda). It's not necessary, but many people prefer it.

If you manage to boot it in live mode with the Desktop CD, open terminal and try first activating the LVM with:
```
sudo vgchange -ay
```

That should report that the LVM is active.

Once it is active, post the output of:
```
sudo vgdisplay
sudo pvdisplay
sudo blkid
```

After that we can give you more precise commands to run. The easiest thing to try is trying to install grub bootloader on the disk and try to boot. Maybe just the bootloader got messed up.

Have you tried booting the server from /dev/sdb? I see there is one grub bootloader on it but I can't be sure it's functional. You know how to control which HDD your server boots from, right? With a machine with 6 disks that knowledge is a must...

---

### Post by Daniel_Schmid on 2016-05-19
> **Bashing-om said:**
> Daniel_Schmid; Hello ;

Assuming (!!) that this system is NOT raid, and that the root install is on the 1st partition of the 1st hard drive (hd0,msdos1) :
what results:
```

set prefix=(hd0,msdos1)/boot/grub
set root=(hd0,msdos1)
insmod linux
linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```

If it boots .. we re-install grub .[INDENT][INDENT]maybe YES[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



So i tried it now.

It didn't worked.

```
set prefix=(hd0,msdos1)/boot/grub
set root=(hd0,msdos1)
```

no messages with these commands.

but with ```
insmod linux
``` ... there comme an error "unkown filesystem" ...

---

### Post by Daniel_Schmid on 2016-05-19
> **darkod said:**
> Honestly, your system is a mess... You have formatted sda, sdd and sdf directly without even creating partition on them. Usually you create partition on the disk, one or more of them, and you format the partitions not the whole disk.

But that is not so important right now.

I would try moving the OS disk to the first SATA port on the board (so that it becomes /dev/sda). It's not necessary, but many people prefer it.

If you manage to boot it in live mode with the Desktop CD, open terminal and try first activating the LVM with:
```
sudo vgchange -ay
```

That should report that the LVM is active.

Once it is active, post the output of:
```
sudo vgdisplay
sudo pvdisplay
sudo blkid
```

After that we can give you more precise commands to run. The easiest thing to try is trying to install grub bootloader on the disk and try to boot. Maybe just the bootloader got messed up.

Have you tried booting the server from /dev/sdb? I see there is one grub bootloader on it but I can't be sure it's functional. You know how to control which HDD your server boots from, right? With a machine with 6 disks that knowledge is a must...



Thank you!

I will try it tomorow or in 2-3 days and will report it hear! :)

> I see there is one grub bootloader on it but I can't be sure it's functional. You know how to control which HDD your server boots from, right


If you mean in the B.I.O.S, then yeas if not then please tell me how you mean it. 

Like i said im a total newbie and are "playing" with the server at home to learn :)
At the time i used the server only for owncloud, plex and to learn about ubuntu :D

---

### Post by darkod on 2016-05-19
Yes, in the BIOS. You can try booting from /dev/sdb, the 74GB disk. I'm not sure what type of disk it is, it looks like the old SCSI disks according to the size. See if that helps.

If not, post the output of those commands when you can.

---

### Post by Daniel_Schmid on 2016-05-19
> **darkod said:**
> Yes, in the BIOS. You can try booting from /dev/sdb, the 74GB disk. I'm not sure what type of disk it is, it looks like the old SCSI disks according to the size. See if that helps.

If not, post the output of those commands when you can.


If you are interested of it or if it can help, it is not an SCSI :)

It is a 15k SAS from IBM :)

---

### Post by Daniel_Schmid on 2016-05-20
> **darkod said:**
> Honestly, your system is a mess... You have formatted sda, sdd and sdf directly without even creating partition on them. Usually you create partition on the disk, one or more of them, and you format the partitions not the whole disk.

But that is not so important right now.

I would try moving the OS disk to the first SATA port on the board (so that it becomes /dev/sda). It's not necessary, but many people prefer it.

If you manage to boot it in live mode with the Desktop CD, open terminal and try first activating the LVM with:
```
sudo vgchange -ay
```

That should report that the LVM is active.

Once it is active, post the output of:
```
sudo vgdisplay
sudo pvdisplay
sudo blkid
```

After that we can give you more precise commands to run. The easiest thing to try is trying to install grub bootloader on the disk and try to boot. Maybe just the bootloader got messed up.

Have you tried booting the server from /dev/sdb? I see there is one grub bootloader on it but I can't be sure it's functional. You know how to control which HDD your server boots from, right? With a machine with 6 disks that knowledge is a must...



[COLOR=#000000]So i toke pictures of the outputs.[/COLOR]

[COLOR=#000000]I havent made it with a live system, because i don't have a CD with that space.[/COLOR]

[COLOR=#000000]So i made it with the installation CD via system repair -> then open a shell.[/COLOR]

[COLOR=#000000]If it is important, that i make this from a live CD, then please tell it to me. [/COLOR]:smile:


[COLOR=#000000]So i uploaded here the screens (it is on german idk if you can help with this because of the german). If not then please say it and i will do it again on english.[/COLOR]


[COLOR=#000000]Here are the screens: [/COLOR][http://postimg.org/gallery/3axcssnaa/55b10866/](http://postimg.org/gallery/3axcssnaa/55b10866/)



[COLOR=#000000]Hope someboddy can help me with these ... and like i sayd it for sevaral times, im a newbie and are learning to use ubuntu/linux [/COLOR]:smile:

---

### Post by Daniel_Schmid on 2016-05-22
> **Daniel_Schmid said:**
> [COLOR=#000000]So i toke pictures of the outputs.[/COLOR]

[COLOR=#000000]I havent made it with a live system, because i don't have a CD with that space.[/COLOR]

[COLOR=#000000]So i made it with the installation CD via system repair -> then open a shell.[/COLOR]

[COLOR=#000000]If it is important, that i make this from a live CD, then please tell it to me. [/COLOR]:smile:


[COLOR=#000000]So i uploaded here the screens (it is on german idk if you can help with this because of the german). If not then please say it and i will do it again on english.[/COLOR]


[COLOR=#000000]Here are the screens: [/COLOR][http://postimg.org/gallery/3axcssnaa/55b10866/](http://postimg.org/gallery/3axcssnaa/55b10866/)



[COLOR=#000000]Hope someboddy can help me with these ... and like i sayd it for sevaral times, im a newbie and are learning to use ubuntu/linux [/COLOR]:smile:




Somebody has an idea? :(:confused:

---

### Post by darkod on 2016-05-22
1. Did you try to boot from sdb, the 74GB disk?

2. If that doesn't work, try reinstalling grub from the system repair shell:
```
sudo vgchange -ay
sudo mount /dev/Heim-Server-vg/root /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

Reboot and again try booting from sdb, the 74GB disk.

---

### Post by Daniel_Schmid on 2016-05-23
> **darkod said:**
> 1. Did you try to boot from sdb, the 74GB disk?

2. If that doesn't work, try reinstalling grub from the system repair shell:
```
sudo vgchange -ay
sudo mount /dev/Heim-Server-vg/root /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

Reboot and again try booting from sdb, the 74GB disk.


Thank you for your answer!

1. Yes i tryed to boot from the 74GB disk.

2. So. I have done the commands in the repair shell. 
Then i rebootet.
Now the system dosen't start from grub resecue ... but it start from the "normal" grub.

Here is a image: [http://postimg.org/image/cyf04n3uz/](http://postimg.org/image/cyf04n3uz/)


Greatings :)

---

### Post by Daniel_Schmid on 2016-05-23
> **darkod said:**
> 1. Did you try to boot from sdb, the 74GB disk?

2. If that doesn't work, try reinstalling grub from the system repair shell:
```
sudo vgchange -ay
sudo mount /dev/Heim-Server-vg/root /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

Reboot and again try booting from sdb, the 74GB disk.



[B]UPDATE:


[/B]So i tried something.


I write ```
[COLOR=#333333][FONT=monospace]cat (ThePath)[/FONT][/COLOR][COLOR=#333333][FONT=monospace]/etc/issu[/FONT][/COLOR]
```[COLOR=#333333][FONT=monospace]e

I become a "info": [/FONT][/COLOR][COLOR=#333333][FONT=monospace]Ubuntu 16.04 \n \l

So after this, i typed some other commands:

[/FONT][/COLOR]```

set root=(ThePath)/
```

Then i typed ```
ls
```

Everything seems to be good at the point and i saw the root folders.


Then i tried this:

```
linux /boot/vmli (and typed TAB to autofill it)
```

Nothing founded ...

After this, i typed```
 ls /boot
```

There was no file with the name vmlinux - logical that it havent found anything.

[U]Then i saw there is a file with the name "vmlinux" and "vmlinux.old" in the / folder.
[/U]
So i tried the same:

```
linux /vmlinuz root=/dev/sda1
```


Now i became an error! 
The text was something like this: "Error: no such File founded!"


I think im on the right way :D




After this, i booted with the CD again.

I typed in the shell:

```
sudo apt-get remove linux-generic linux-image-generic linux-headers-generic
```

So i removed it.

Then i tried to install them again with ```
sudo apt-get install linux-generic
```

I became an error code, that the server cant connect to the de.ubuntu* servers!

But before i removed them, i tried to reinstall them and this alone worked ...



Now i'm very confused ...



Hope this can help you guys to help me:D

---

### Post by darkod on 2016-05-23
Hold on, when you are talking about "repair shell" do you mean the recovery mode entry from grub or a shell running from a cd? Because there is a difference.

A shell running from a cd (like the live mode for example) is not your OS installed on the disks.

The recovery mode is your OS installed on the disks.

If you try to load the recovery mode from grub, does it work? If it does, it should show you like small menu. From that menu select "drop to root shell". That should open a shell as root, and you can work directly on your OS. But don't do anything right now, just let us know if it loads or not...

If you can't load the recovery mode, get the ubuntu desktop ISO (download it if you don't have it), and make a cd or usb with it, so you can boot the server in live mode. That can help you work and try to fix it. But remember, working in live mode is NOT your OS. Using apt-get is not working in the place that you think it is. From live mode you will have to use something like chroot to work on the OS. But that is also something we will discuss later, just let us know which way you can work: recovery mode or live cd?

---

### Post by Daniel_Schmid on 2016-05-23
> **darkod said:**
> Hold on, when you are talking about "repair shell" do you mean the recovery mode entry from grub or a shell running from a cd? Because there is a difference.

A shell running from a cd (like the live mode for example) is not your OS installed on the disks.

The recovery mode is your OS installed on the disks.

If you try to load the recovery mode from grub, does it work? If it does, it should show you like small menu. From that menu select "drop to root shell". That should open a shell as root, and you can work directly on your OS. But don't do anything right now, just let us know if it loads or not...

If you can't load the recovery mode, get the ubuntu desktop ISO (download it if you don't have it), and make a cd or usb with it, so you can boot the server in live mode. That can help you work and try to fix it. But remember, working in live mode is NOT your OS. Using apt-get is not working in the place that you think it is. From live mode you will have to use something like chroot to work on the OS. But that is also something we will discuss later, just let us know which way you can work: recovery mode or live cd?


Only for the case, can you say me how to get in in the recovery mode from grub? just for the case ... i dont want to risk / oversee something

---

### Post by darkod on 2016-05-23
The recovery mode is the entry that has (recovery mode) next to it. For example, when you boot the grub menu starts like:
Ubuntu
Ubuntu (recovery mode)
...

If you select that second one, that is the recovery mode. After that it should open a small menu, and in it you have to select "drop to root shell". If that works, it will open a command line as root inside your OS. By default it will be in read-only but you can change that easily. The main problem is to see if you can load the recovery mode root shell or not.

---

### Post by Daniel_Schmid on 2016-05-23
> **darkod said:**
> The recovery mode is the entry that has (recovery mode) next to it. For example, when you boot the grub menu starts like:
Ubuntu
Ubuntu (recovery mode)
...

If you select that second one, that is the recovery mode. After that it should open a small menu, and in it you have to select "drop to root shell". If that works, it will open a command line as root inside your OS. By default it will be in read-only but you can change that easily. The main problem is to see if you can load the recovery mode root shell or not.



Ah yeah now i know what you mean.

So i dont even try it, because i know, that i dont even see the recovery mode! 
When i start the server, it is booting directly in GRUB (like on the screen) [http://postimg.org/image/cyf04n3uz/](http://postimg.org/image/cyf04n3uz/)

---

### Post by darkod on 2016-05-23
If you are not getting any grub menu then better to download the desktop ISO and make a cd or usb, boot with it in live mode (Try Ubuntu). That will load a fully functioning live mode with GUI and running from the cd/usb.

In the live mode you can open a terminal and work to try repair the server OS.

That is what I would do in your place...

---

### Post by Daniel_Schmid on 2016-05-25
> **darkod said:**
> If you are not getting any grub menu then better to download the desktop ISO and make a cd or usb, boot with it in live mode (Try Ubuntu). That will load a fully functioning live mode with GUI and running from the cd/usb.

In the live mode you can open a terminal and work to try repair the server OS.

That is what I would do in your place...


So i made a live CD and it seams to work but with some lags...



Could you say me now, what i have to do? :D


Greatings

---

### Post by darkod on 2016-05-25
OK, now boot the server with the cd into live mode, open a terminal and first activate the LVM, mount the root LV and open chroot into it:
```
sudo vgchange -ay
sudo mount /dev/Heim-Server-vg/root /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

From this point on you are inside a chroot in your server OS, which means you are running commands as root inside the server OS, not the live mode.

First try to install grub on /dev/sdb and update it:
```
grub-install /dev/sdb
update-grub
```

While you are here try to list the kernels because you were doing some kernel removing earlier and I'm not sure what you did exactly:
```
dpkg --list | grep linux-image
```

Post here the output of that, just copy paste the text output inside CODE tags.

Then exit the chroot and unmount the temporary mounted root LV:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

After that reboot the server making sure you boot from the /dev/sdb disk which should be the 74GB disk. Let us know if that fixes it...

---

### Post by Daniel_Schmid on 2016-05-31
> **darkod said:**
> OK, now boot the server with the cd into live mode, open a terminal and first activate the LVM, mount the root LV and open chroot into it:
```
sudo vgchange -ay
sudo mount /dev/Heim-Server-vg/root /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

From this point on you are inside a chroot in your server OS, which means you are running commands as root inside the server OS, not the live mode.

First try to install grub on /dev/sdb and update it:
```
grub-install /dev/sdb
update-grub
```

While you are here try to list the kernels because you were doing some kernel removing earlier and I'm not sure what you did exactly:
```
dpkg --list | grep linux-image
```

Post here the output of that, just copy paste the text output inside CODE tags.

Then exit the chroot and unmount the temporary mounted root LV:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

After that reboot the server making sure you boot from the /dev/sdb disk which should be the 74GB disk. Let us know if that fixes it...



Thank you for the answer!

I tried
 ```
sudo vgchange -ay
sudo mount /dev/Heim-Server-vg/root /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```


No error


```
grub-install /dev/sdb
update-grub
```

Error:

> failed to get canonical path of '/cow 


What should i do now?

---

### Post by darkod on 2016-05-31
If that is the message after 'update-grub' try running the last block of code (to umount) and reboot the server as normal (without the live cd) to see if it helped despite the error.

Let us know.

---

### Post by Daniel_Schmid on 2016-06-04
> **darkod said:**
> If that is the message after 'update-grub' try running the last block of code (to umount) and reboot the server as normal (without the live cd) to see if it helped despite the error.

Let us know.

I tried it and i also made ```
sudo apt-get update && apt-get upgrade
```


It seams to work! :)


I will test it for 1-2 weeks and if there is an error, i will report it here. :)



Thank you for your help!

---

### Post by darkod on 2016-06-04
No problem, you're welcome.

So the server boots now without the cd? From the hdd?

---

