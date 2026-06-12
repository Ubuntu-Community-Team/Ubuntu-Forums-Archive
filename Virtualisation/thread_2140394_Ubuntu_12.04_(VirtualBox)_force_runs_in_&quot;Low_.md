---
title: "Ubuntu 12.04 (VirtualBox) force runs in &quot;Low Graphics Mode&quot; than freezes"
date: 2013-04-29
forum: Virtualisation
---

### Post by WileeDarklight on 2013-04-29
Hello all!

I've recently set up a VM with Ubuntu for some work related projects.  I initially started with the install for 12.04, but once installed to the VM's harddisk image and I tried to run it normally it told me it had to run in Low Graphics Mode.  When I try to run "startx", it gets part way through the Start/Stop Services and then hard freezes.  

I tried to install 10.04 and update to 12.04 to see if that made a difference and, huzzah! All worked well! I spent a day or two setting up all of the required applications and downloading everything I needed and it started working away.  No problems, thus far and I could boot it up normally. 

Today, I came in and that same install is back to square one... It runs in Low Graphics Mode and freezes!!  

This is exceptionally aggravating, since I lost all of that progress and those few days getting it to work.

I'm new to Linux in general so if it involves any commands, assume I know nothing Linux related.

I've searched around these forums for similar problems but I can't find anything relevant. 

Here's what I've got running in case it makes a difference:
Win7 x86
Oracle VirtualBox 4.2.12
Ubuntu 12.04

---

### Post by babarehner on 2013-04-30
Unfortunately I have the same problem. My host is Windows 7. My workaround was to reinstall VirtualBox 4.2.10 and stay with that. Not a solution but in checking the VirtualBox site the low graphics problem appears to pop up with the upgrade to 4.2.12 after the upgraded guest additions is installed. I have dkms installed on my virtual Ubuntus so I do not know if an Ubuntu without dkms would also have the problem- another workaround check. The VirtualBox page stated that a clean install of 4.2.12 would not produce the problem but since I have over a 100 vms I have not checked that out. Good luck.

---

### Post by jhazard112 on 2013-05-23
Hi WileeDarklight,

I don't know if you found and answer to your issue, but in case you haven't, I wanted to let you know what worked for me.

I booted my guest of 12.04 while holding <shift> down.  Once I got to the prompt for regular boot, or (recovery mode) I chose recovery mode.
I then enabled networking, and dropped into a root shell.

Go to the devices, and make sure that VBoxGuestAdditions.iso is checked.

Type in the following:

mkdir /media/cdrom - This "Makes a Directory" for the cdrom
mount /dev/cdrom /media/cdrom - This mounts the directory that you just made (i.e. /media/cdrom)
cd ../media/cdrom - This command changes the directory to /media/cdrom directory

Once this is complete, just to make sure everything is good type:

ls - this will list the contents of the directory (much like dir does in windows)

If this file is present "VBoxLinuxAdditions.run" type the following (if not troubleshoot what happened previously):

sh ./VBoxLinuxAdditions.run

Once it completes and you are back to the prompt type "reboot" and it should reboot.  If not choose "Boot Normally" or something like this and it should boot into the desktop with no issues.

Full disclosure, I am able to get to the login screen of Ubuntu, but when I go to login, it aborts automatically.  I am working on that issue right now.

Let me know if this helps you at all.

J

---

### Post by jhazard112 on 2013-05-23
Just to add to my last post.  When you are at the login screen, if you click the Ubuntu symbol next to the account name, and change it to "2D" it should work.

---

