---
title: "How To Permanently Mount Shared Folder With fstab in 10.4"
date: 2010-05-01
forum: Virtualisation
---

### Post by Aurora@FleetBuzz on 2010-05-01
I am running Ubuntu 10.4 virtually (Virtualbox) on a Vista host.  I created a mount point, "Windows-Share" in the Media folder to mount my shared folder "don".

I can manually mount using this command:

> sudo mount -t vboxsf don /media/windows-share

I attempted to automatically mount this shared folder by adding the following command to fstab:

> don /media/windows-share vboxsf auto 0 0

On boot up, I get the following error message:
[B]"An error occurred while mounting /media/windows-share. . . "
[/B]

I am offered a choice of selecting "s" to skip, or "m" to fix manually.  Since I really don't know what I'm doing, I select "s".

However, when the system is done booting up, my drive is mounted!

[Note:  the above line was added to fstab in Ubuntu 9.10 and worked perfectly!  I'm at a loss to explain why it won't work in 10.4]

I would like to get rid of that annoying message on boot up, while still automatically mounting my shared folder.

Does anyone have any suggestions?

---

### Post by dcstar on 2010-05-02
> **Aurora@FleetBuzz said:**
> I am running Ubuntu 10.4 virtually (Virtualbox) on a Vista host.  I created a mount point, "Windows-Share" in the Media folder to mount my shared folder "donj".

I can manually mount using this command:



I attempted to automatically mount this shared folder by adding the following command to fstab:



On boot up, I get the following error message:
[B]"An error occurred while mounting /media/windows-share. . . "
[/B]

I am offered a choice of selecting "s" to skip, or "m" to fix manually.  Since I really don't know what I'm doing, I select "s".

However, when the system is done booting up, my drive is mounted!

[Note:  the above line was added to fstab in Ubuntu 9.10 and worked perfectly!  I'm at a loss to explain why it won't work in 10.4]

I would like to get rid of that annoying message on boot up, while still automatically mounting my shared folder.

Does anyone have any suggestions?

Yes, use the Search function:

[http://ubuntuforums.org/showthread.php?t=1440320](http://ubuntuforums.org/showthread.php?t=1440320)

---

### Post by Aurora@FleetBuzz on 2010-05-02
I did try the search function, thanks.  Appreciate the link, though.

The referenced thread opines that the solution is a "work around"?  In other words, the faster boot speeds of 10.4 cause this issue?  The "work around" is to create another executable file?  One question then:

What is the syntax to mount the drive using the example I gave?  Is it something like this:

> mount don /media /windows-share 

---

### Post by Aurora@FleetBuzz on 2010-05-02
I followed the instruction linked on the thread dcstar was kind enough to provide.

I tried creating the file **/etc/init.d/local** on two separate virtual machines, running two different host OS (XP and Vista).  On both machines, the terminal crashed when I ran the command:

> sudo vi /etc/init.d/local

However...I was able to edit an existing file **/etc/init.d/rc.local**.

I added the following to the end of the file, saved & re-booted.

> mount.vboxsf -w Don /media/windows-share

It worked.  Not elegant or pretty, but it worked.

---

### Post by Morbius1 on 2010-05-02
It appears as though there is a bug report for this:

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/530179](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/530179)

---

### Post by drupalfever on 2012-02-14
Hi, guys.

I got it working on my VirtualBox.

Here is the description of my setup:

My Host Machine: Windows 7
My VirtualBox Client Machine: Linux CentOS 6.2
My VirtualBox Version: 4.1.8 r75467
My Shared Folder Name: "DropBox"
My Shared Folder Windows Path: "C:\Dropbox"
My Mount Point in Linux: "/DropBox/"

I opened the the fstab file with nano as follows:
```
[root@localhost /] # nano /etc/fstab
```At the end of the file I entered:
```
DropBox  /DropBox   vboxsf  defaults  0 0
```The first word of the above entry is the VirtualBox "Shared Folder Name".
The second word in the above entry is the path of the folder that I created in Linux and that I am using as the Mount Point for the Share Folder.

I pressed the following keystrokes to save and close Nano:
Ctrl+O
Enter
Ctrl+x

It worked perfectly for me. :P

---

