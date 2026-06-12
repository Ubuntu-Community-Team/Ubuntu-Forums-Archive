---
title: "Access USB in UBuntu Server Edition 9.04"
date: 2009-07-01
forum: Server Platforms
---

### Post by Chetan26 on 2009-07-01
Hi ,
      Iam trying to  copy some files from USB stick  into UBuntu  server Edition.But Iam not able to access the USB from the terminal.

When I run sudo fdisk -l

Iam able to see the USB in dev/sdh1 

But Its not accesssible.

Can you pls tell me how to access the stick from terminal .


Many thanks
Chetan

---

### Post by TwiceOver on 2009-07-01
You need to mount the usb drive

sudo mount /dev/sdh1 /insert/your/mount/point/here

For me I made a directory in /media called flashdrive so:

sudo mount /dev/sdh1 /media/flashdrive

---

### Post by Chetan26 on 2009-07-01
I made a directory in Media called flashdrive 

when i run sudo mount /dev/sdh1/media/flashdrive   it says  cannot mount?


can you provide some help



Thanks
Chetan

---

### Post by TwiceOver on 2009-07-01
> **Chetan26 said:**
> I made a directory in Media called flashdrive 

when i run sudo mount /dev/sdh1/media/flashdrive   it says  cannot mount?


can you provide some help



Thanks
Chetan

Make sure there is a space in there between your device and mount point...

sudo mount /dev/sdh1 /media/flashdrive

---

### Post by Chetan26 on 2009-07-01
yea there is some space , when i run fdisk -l

it shows the drive in /dev/sdh

so I run the command  and get following o/p

sudo mount /dev/sdh/media/flashdrive

mount : can't find  /dev/sdh/media/flashdrive  in/etc/fstab or /etc/mstab

---

### Post by TwiceOver on 2009-07-01
> **Chetan26 said:**
> yea there is some space , when i run fdisk -l

it shows the drive in /dev/sdh

so I run the command  and get following o/p

sudo mount /dev/sdh/media/flashdrive  <---- IS THIS WHAT YOU ARE RUNNING?  IF SO THIS IS WRONG...  There needs to be a space between the device and the mount point /dev/sdh1 /media/flashdrive

mount : can't find  /dev/sdh/media/flashdrive  in/etc/fstab or /etc/mstab

No not space on the drive... a space in the command you are running.  See above.

---

### Post by smeerbartje on 2009-07-01
Dude, this should not be a 'linux for dummy'-forum.... no, let me correct myself: 'linux for people who don't use google'-forum.

---

### Post by baietzel15 on 2009-07-01
first: use GOOGLE
second: copy and paste theese 2 commands in the terminal:

sudo mkdir /media/flashdrive
sudo mount /dev/sdh1   /media/flashdrive

---

### Post by lukeiamyourfather on 2009-07-01
Wow, pulling the Google card I see. Kind of ironic don't you think? Since most of the time where does Google find the answers, forums! When answering questions its not just answering it for the one dude or lady, but for everyone that might have the same issue in the future. Now if somebody searches for USB drive and Ubuntu Server there will be at least one answer out there. Building a larger knowledge base one thread at a time.

Sure they could've searched for how to mount a drive, but users not familiar with mounting drives might not know where to start the search, or that its even called mounting a drive and not something else. This forum is for helping people out, so maybe that's where the focus should be.

For the original poster, if you have problems with getting a command to work in the future you should check out the help or manual for the command to make sure you have the syntax, arguments, and options correct. For example try this in the terminal.

```
man mount
```

And if you're not familiar with using the manual try this.

```
man man
```

Yes, the manual even has a page on itself. Sometimes commands won't have a manual entry but sometimes will have built in help with --help, or -h, or just try the command without any arguments and sometimes it'll try and help you out. Cheers

---

