---
title: "VMware and automation"
date: 2007-10-28
forum: Virtualisation
---

### Post by tjpren on 2007-10-28
Hi all,

I'm wanting to run an Engineering app in XP.  I've been experimenting with Vmware, with Ubuntu as host, with XP as a guest and the app running in XP.  The PC runs in a factory, (for thos interested its a SCADA app), and I want to have a bit of security.

I like the idea of running Ubuntu as a general user, so as to restrict possible access and damage to the PC, if people find a way out of XP.

My thoughts were to start Ubuntu as general user, then startup the VM app.  I've since found that as the installed apps were made under my admin account, they cannot be started from the VMware console.  I've found that I can run start XP usinng a command line (see my recent post).

This is fine, ecept I've no way of seeing the XP guest.  Running as a guest restricts my ability to start the VMconsole, and even see the VM I've strted.

I have found that I can rdesktop to XP.

It seems fine, but a little slow, I think because rdesktop is another app chewing up CPU.



Any thoughts or comments of achiving what I described in another way would be appreciated.

---

### Post by mikeyrb on 2007-10-29
Is there a reason why you would want to run ubuntu under windows xp, when it appears you are going to use none of the features ubuntu provides?  Seems far simpler to just run windows xp to me.

---

### Post by koenn on 2007-10-29
1/
the executable for the vmware console seems to be /usr/bi,/vmware, i s owned by root, byt executable by all. At least mine is. Maybe you should check that - I don't see what other reason there could be for not being able to start it. Maybe that 'guest' account needs a shell ? 

```
~$ ls -al /usr/bin/vmware
-r-xr-xr-x 1 root root 4570 2006-11-22 20:06 /usr/bin/vmware
```


2/ you should check the location of the vm machine and virtual disk files, the permissions on that location (directories), and the permissions on the files. eg if tha files are stored in your home directory, other accounts probably won't have sufficient access

3/ note that you can mark  virt. machines as private, so that only the account that created them, can access and use them. Maybe thati's where your problem comes from. You can reset that in the vmware console.

---

### Post by tjpren on 2007-10-30
Hi guys,
Thanks.
The reason for wanting to run XP as a guest on a Ubuntu host is security and stability - or at least thats my perception.  Certainly XP is a more difficult environment to lock down, and Linux appears to have security as an advantage.  My idea was that should XP crash, it should be a relativly straightforward restart from within a linux host.

I've found also that I can run my VMware machines from  a Linux user, by using the administrator logon credentials in the console.  A factory supervisor (or I suppose a remote support) could fire XP up from within the Ubuntu guest.

Anyway thats the reason for wanting to do it, and I generally feel quite happy about it working, but I'm open to any suggestions by others of better ways.

VMware seems to run OK, although I'm having issues with my parallel port at the present.  My XP app needs to see a dongle in the parallel port to run.  I've tried 
rmmod lp
without success.

Assuming I crack this, my next thought is to try Workstation, and look at creating a backup of the VM, so that I have some portability with it.  I'm hoping it gives me something like an image, so that if a Revert fails from the VMware console (if XP crashes), I've got an image I can load up

---

### Post by mikeyrb on 2007-10-30
I doubt you will gain any additional stability.  The Windows XP guest should perform the exact same virtualized as it would on the bare hardware.  However, you then add in the ability for linux to fail or vmware to fail.  Linux as a base should not give you additional stability.

How would virtualizing XP give additional security?  I cannot see how the security of linux would relate to the security of a virtualized OS.

Now, a valid point is that if the XP installation were to fail, you could quickly and easily drop in a new VM that was all ready to go.  How often do you predict that to happen?  What is your downtime (how long can it wait)?  Keep in mind that the linux install could fail also.  Would it be easier to just image the hard drive of an installed XP?  You definitely do not need workstation to make a backup.  Just copy the config and hard disk images and you are good to go.

Hope this helps.

---

### Post by tjpren on 2007-10-31
Thanks Mickyrb, valid points to consider.

In regard to copying the config and hard disk image, I presume some instruction like:
navigating to the Virtual machine directory and executing
tar cvpzf backup.tgz 
is the go ?

---

### Post by mikeyrb on 2007-10-31
That would work.  Depending on how you set it up, you may only have two files: the configuration file and the hard disk image.  Though if you tell it to break up the hard disk image (such as 2-GB per file), then you'll have multiple.

---

### Post by Delvien on 2007-11-01
Isn't it against the VMware EULA to use it for a business if you don't have a license ?

---

### Post by mikeyrb on 2007-11-01
It would help if you could read the EULA and highlight such a section.  I just read through the VMware Server EULA and found no such mention.

---

### Post by bazz on 2007-11-03
> **tjpren said:**
> Hi all,

I'm wanting to run an Engineering app in XP.  I've been experimenting with Vmware, with Ubuntu as host, with XP as a guest and the app running in XP.  The PC runs in a factory, (for thos interested its a SCADA app), and I want to have a bit of security.

I like the idea of running Ubuntu as a general user, so as to restrict possible access and damage to the PC, if people find a way out of XP.

My thoughts were to start Ubuntu as general user, then startup the VM app.  I've since found that as the installed apps were made under my admin account, they cannot be started from the VMware console.  I've found that I can run start XP usinng a command line (see my recent post).

This is fine, ecept I've no way of seeing the XP guest.  Running as a guest restricts my ability to start the VMconsole, and even see the VM I've strted.

I have found that I can rdesktop to XP.

It seems fine, but a little slow, I think because rdesktop is another app chewing up CPU.



Any thoughts or comments of achiving what I described in another way would be appreciated.

I'm doing something like that, but a bit different set up...more for automation lab. Not sure if this will help but look here. [http://forum.freespire.org/showthread.php?t=10932](http://forum.freespire.org/showthread.php?t=10932) 
The config posted there needs to be redone, because I have some bug fixes in the set up config. I am now using VMware workstation
Anyone want to work on an automation distro????
As for the permissions problem. You need to set the permissions for all the vmware files for the user you want to use them. For example I have a directory call vmware machines. I created a group called vmusers. I set the permissins of the vmware machines directory for the group vmuses to have read and write to that directory. Or you could do each file for the user. I'm not sure but maybe chmod 777 vmware machines might work.

---

### Post by FrankVdb on 2007-11-06
> **tjpren said:**
> 
VMware seems to run OK, although I'm having issues with my parallel port at the present.  My XP app needs to see a dongle in the parallel port to run.  I've tried 
rmmod lp without success.

Assuming I crack this, my next thought is to try Workstation, and look at creating a backup of the VM, so that I have some portability with it.  I'm hoping it gives me something like an image, so that if a Revert fails from the VMware console (if XP crashes), I've got an image I can load up

I found some info on how to get a parallel port working on VMware:

[http://pubs.vmware.com/esx254/admin/wwhelp/wwhimpl/common/html/wwhelp.htm?context=admin&file=esx25admin_running.5.36.html](http://pubs.vmware.com/esx254/admin/wwhelp/wwhimpl/common/html/wwhelp.htm?context=admin&file=esx25admin_running.5.36.html)

Don't know if this also applies to the free versions of their software (e.g. Player).

Me too I'm looking to get a dongle working on a virtual machine. I'd like to use VirtualBox to run XP within Ubuntu because of translation memory software I need for my business.

---

### Post by tjpren on 2007-11-08
Hi all,

Managed to crack the parallel port issue:

sudo su
chmod 666 /dev/parprt0
rmmod lp

Also, remove any user of the parallel port.  I had used the Cups driver to try and get a printer working, so I had to delete the printer.
Reference:
[http://communities.vmware.com/message/60351](http://communities.vmware.com/message/60351)

Now VMware XP runs, and my SCADA App can see the parallel port OK.

---

