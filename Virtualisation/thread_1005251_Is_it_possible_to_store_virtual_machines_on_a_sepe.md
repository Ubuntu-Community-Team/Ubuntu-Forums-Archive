---
title: "Is it possible to store virtual machines on a seperate partition?"
date: 2008-12-08
forum: Virtualisation
---

### Post by Jim_in_Germany on 2008-12-08
Hi,

I have Virtual Box installed running on my main partition (sda1).
This is also where I have my virtual machines saved (in my home folder) .
However, my Ubuntu partition is totally full. Is it therefore possible to store the virtual machines on a different partition (my hard disk is split into three partitions - Ubuntu, XP, Files)?

Am grateful for any help as I cannot use Ubuntu until I have freed up some space.

---

### Post by HotShotDJ on 2008-12-08
As long as the user that is running the VM has permissions to access the partition, there is no reason why you can't put the files anywhere you please.  I've heard of people storing the VDI directory on a USB drive.  Just point VirtualBox to the right place (and make sure the partition or USB drive is mounted) and you should be good to go.

---

### Post by bodhi.zazen on 2008-12-08
Yes you can.

---

### Post by sambita on 2008-12-08
Yes, i have mine in an external usb hard drive.
If you need instructions as to how to do this just let me know.

Keep in mind that, as HotShotDj said, youll need to have access permissions to the partition in which you want to place your vdi.

---

### Post by Jim_in_Germany on 2008-12-08
Cheers for the replies guys. I had hoped it was relatively easy to do, but as it has taken me ages to set up my guest machines just how I like them, plus the fact that Virtual Box has sometimes been a little temperamental, I thought it better to ask before starting to play around.
Anyways, I'll try it out and post back here if I have any trouble.

---

### Post by dcstar on 2008-12-10
If you are going to put your VMs on a separate partition then you should format that partition to the best performance FS you have available.

Most VMs use a few large files so you should use a FS optimised for that, rather than choosing a default FS that is not as well suited to VMs. I use Reiserfs for my VMs with mount options to reduce unnecessary writes.

---

### Post by Dedoimedo on 2008-12-10
Hello,
Not only that you can, you should. It should improve your performance, scalability and flexibility. If you make images of your operating system, it will help make them smaller. And if your other partition happens to reside on a second hard disk, then you'll see an even greater increase in performance.
Dedoimedo

---

### Post by Jim_in_Germany on 2008-12-11
Hi,

So, I tried moving my existing virtual machines and so far it didn't work. Let me explain:
I have two VMs running in an Ubuntu host (Ibex).
The VMs are loacted in /home/jim/.VirtualBox/VDI.
I moved these to my second hard drive and changed the default location for the vdi file in the 'Preferences' dialog of VirtualBox. This now points to /media/Speicher/VirtualBox/VDI.
Everything seemed to be good, yet when I tried to boot my VM from the VirtualBox console I got the message that VirtualBox couldn't locate the VDI file.
I checked in 'Preferences' and it was still pointing to /media/Speicher/VirtualBox/VDI.

Do I have to change the path elsewhere?
I had a good look at all the options and couldn't find anything useful.

Would be grateful for your help.

---

### Post by howefield on 2008-12-11
I make a backup of my vms using the "VBoxManage clonevdi source path destination path" so I keep an "untouched" copy of my vm.

And that is also how I would move them to another location. (You can't simply copy/paste the vm)

I'd then tell Virtualbox where the new disk is. If I remember correctly it is easier to set up a new vm in the VirtualBox settings windows after moving the vm, only takes a couple of minutes.

---

### Post by Jim_in_Germany on 2008-12-11
Hi,

Unfortuantely when I enter:
```
VBoxManage clonevdi /home/jim.VirtualBox/VDI/Windows\ XP.vdi /media/Speicher/VirtualBox/VDI/WinXP.vdi
```
I get:
```
Usage: VBoxManage clonevdi <uuid>|<filename> <outputfile>
```

When I enter:
```
VBoxManage clonevdi  c166ef37-8ea8-4a05-f1a2-5555dd9b1302|/home/jim/.VirtualBox/VDI/Windows\ XP.vdi /media/Speicher/VirtualBox/VDI/WinXP.vdi
```
I get
```
/home/jim/.VirtualBox/VDI/Windows XP.vdi: line 1: syntax error near unexpected token `>'
/home/jim/.VirtualBox/VDI/Windows XP.vdi: line 1: `<<< innotek VirtualBox Disk Image >>>'
```

Any idea what I'm doing wrong?

---

### Post by howefield on 2008-12-11
[QUOTE=Jim_in_Germany;6351324]```
VBoxManage clonevdi /home/jim.VirtualBox/VDI/Windows\ XP.vdi /media/Speicher/VirtualBox/VDI/WinXP.vdi
```


Syntax for your source path seems incorrect ?  

You have a space, back slash and a dodgy looking path to your vdi ;)

If you have created your vm in the default Virtualbox directory and the name of the vm is XP.vdi

Is it not ...
/home/jim/.VirtualBox/XP.vdi

Also, if your vm name has a space in it, eg, Windows XP.vdi you'll need to enclose it in quotes.

---

### Post by xebian on 2008-12-11
> **Jim_in_Germany said:**
> Hi,

So, I tried moving my existing virtual machines and so far it didn't work. Let me explain:
I have two VMs running in an Ubuntu host (Ibex).
The VMs are loacted in /home/jim/.VirtualBox/VDI.
I moved these to my second hard drive and changed the default location for the vdi file in the 'Preferences' dialog of VirtualBox. This now points to /media/Speicher/VirtualBox/VDI.
Everything seemed to be good, yet when I tried to boot my VM from the VirtualBox console I got the message that VirtualBox couldn't locate the VDI file.
I checked in 'Preferences' and it was still pointing to /media/Speicher/VirtualBox/VDI.

Do I have to change the path elsewhere?
I had a good look at all the options and couldn't find anything useful.

Would be grateful for your help.

Your problem is that the hard disk for the VM is still pointing to the old location.  The preference is a global setting which is ok for new VM's.

Existing VM's settings is changed by selecting it and then change in the Hard Disk.  In fact you should have got an error/warning message that it's vdi is missing during startup.  The bad one should be released/removed.  Then add a new one with the current location.

---

