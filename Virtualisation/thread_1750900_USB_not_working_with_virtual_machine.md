---
title: "USB not working with virtual machine"
date: 2011-05-06
forum: Virtualisation
---

### Post by ClientAlive on 2011-05-06
Hi,

Running Ubuntu 10.04 in Oracle VM Virtual Box Version 4.0.6 r71334 (acquired like yesterday). Please be sure to see "NOTE:" at the end.

I've followed the instructions found in Section 4.2.2.1 of the help file for this app stated thus:

> Installation generally involves the following steps:

1) Before installing the Guest Additions, you will have to prepare your guest system for building external kernel modules. This works similarly as described in Section 2.3.2, &#8220;The VirtualBox kernel module&#8221;, except that this step must now be performed in your Linux guest instead of on a Linux host system, as described there.

Again, as with Linux hosts, we recommend using DKMS if it is available for the guest system. If it is not installed, use this command for Ubuntu/Debian systems: 

sudo apt-get install dkms

or for Fedora systems: 

yum install dkms

Be sure to install DKMS before installing the Linux Guest Additions. If DKMS is not available or not installed, the guest kernel modules will need to be recreated manually whenever the guest kernel is updated using the command 

/etc/init.d/vboxadd setup

as root.

2) Insert the VBoxGuestAdditions.iso CD file into your Linux guest's virtual CD-ROM drive, exactly the same way as described for a Windows guest in Section 4.2.1.1, &#8220;Installation&#8221;.

3) Change to the directory where your CD-ROM drive is mounted and execute as root:
sh ./VBoxLinuxAdditions.run

Then, in the terminal and in the detailed instructions that come right after that (not shown above), I am instructed to reboot the virtual machine (right?). So I reboot.

I login and insert my thumb drive and I see a series of three popups come up.

first - "discard is now unmounted"

second - "(name of my device) is not mounted" 

third - "(name of my device) is not mounted"

Ultimately it is mounted to the host and not the guest (maybe twice). When I go to eject the device in the host I find there are two instances (two windows) of my USB drive open.

I have also looked in the troubleshooting sections for this in the help file which says thus:

> 12.6.7. USB not working
If USB is not working on your Linux **host**, make sure that the current user is a member of the vboxusers group. On older hosts, you need to make sure that the user has permission to access the USB filesystem (usbfs), which VirtualBox relies on to retrieve valid information about your host's USB devices. The rest of this section only applies to those older systems.

I looked under Users and Groups > Advanced > User Priviledges tab (in the **host** o/s)
and "Use VirtualBox Virtualization solution" is in fact checked.

Finally . . .

NOTE: I'm not sure I have the filter set up right in settings in Virtual Box. I've attached a picture to show how it is set up currently.

Can anyone help me figure this out?

Thanks.
--------------------------------------------

Actually, when I just plugged in the camera to save the picture and attach it - I got the popup that it was mounted two times (two popups in a row both saying that). The virtual machine and Oracle Virtual Box are both closed (I closed them both before plugging in the camera). Also, when I clicked the button to "open F-spot" I get a single popup that says " . . . is now unmounted" then then I use the F-spot app like normal and it works fine.

This reminds me of something. When I began going through these instructions I may have had guest additions already installed but I wasn't sure it had been installed properly the first time so I went through the instructions thinking it would just over-write any instance that already existed. Not only this but the output from the terminal when I worked through the instructions in the help file let me to think the same operation thing happened twice - once in the step to install dpkg and onece in step three. The output looked the same. Could there be several installations of it on my machine?

In all of this I'm just stumped as to how to get this functioning properly. Now my host o/s seems to acting wierd too. Sure don't need any problems with it.

Any help would be very much appreciated.

Thank you.

---

### Post by ClientAlive on 2011-05-08
bump

Please someone

---

### Post by falko on 2011-05-09
Did you install the "VirtualBox 4.0 Oracle VM VirtualBox Extension Pack"?
Take a look at [http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-10.10-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-10.10-server)

---

### Post by ClientAlive on 2011-05-09
> **falko said:**
> Did you install the "VirtualBox 4.0 Oracle VM VirtualBox Extension Pack"?
Take a look at [http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-10.10-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-10.10-server)


Well I thought I had. I had something like that and it showed up on the desktop of the guest o/s. I just downloaded it to my host o/s desktop again now to compare file names but now there's some problem with vb when I go to start it up. I don't think I moved any folder or anything to do with it. Prob have to start over with it. Try to get it right this time.

Thanks for the advice.

Jake

---

### Post by AlexGeddylfson on 2011-05-10
I've installed the extension pack and it still has not helped me. I really need to get this fixed too. =(

---

### Post by ClientAlive on 2011-05-10
Yes. While looking around in my files I see that I already had that same, extension pack, file on my machine and do recall installing it. I recall now that that is why I was confused. Can't understand what could have went wrong that it did not work for me. In the course of trying to correct the situation (as mentioned in my first post) I think something happened that sort of messed up something else in the machine - my host o/s I mean.

Jake

---

### Post by Hedgehog1 on 2011-05-11
Greetings!

If your host OS is Ubuntu, you need to add your user to the 'vboxusers' group to be able to use USB from vbox:

[IMG]http://img190.imageshack.us/img190/5285/vboxusers.png[/IMG]

You may need to reboot after this change for it to take effect.

***The Hedge***

:KS

---

### Post by wilee-nilee on 2011-05-11
The extension pack is installed in a different manner then the guest additions as well.
[http://forums.virtualbox.org/viewtopic.php?f=24&p=164806](http://forums.virtualbox.org/viewtopic.php?f=24&p=164806)

---

### Post by ClientAlive on 2011-05-11
> **Hedgehog1 said:**
> Greetings!

If your host OS is Ubuntu, you need to add your user to the 'vboxusers' group to be able to use USB from vbox:

[IMG]http://img190.imageshack.us/img190/5285/vboxusers.png[/IMG]

You may need to reboot after this change for it to take effect.

***The Hedge***

:KS


Thanks Hedgehog1. Got ya. Reading wilee-nilee's post I think I may have missed something.


> **wilee-nilee said:**
> The extension pack is installed in a different manner then the guest additions as well.
[http://forums.virtualbox.org/viewtopic.php?f=24&p=164806](http://forums.virtualbox.org/viewtopic.php?f=24&p=164806)


I'm sorry. I should have caught this before but are you saying there are 2 additional things to add to virtual box? So if you count virtual box itself there's a grand total of 3 things in play here?

So the only file I have besides virtual box itself is filename:

> 
Oracle_VM_VirtualBox_Extension_Pack-4.0.6-71344.vbox-extpack


---

### Post by wilee-nilee on 2011-05-11
The newest Vbox just has this additions added but it is not done the same way as the guest addons. You have to be in the users group as hedgehog shows as well.

---

### Post by Dedoimedo on 2011-05-12
No need to reboot after adding new group.
Just logout/login.
Dedoimedo

---

### Post by ClientAlive on 2011-05-12
Yeah, I'm in the users group and have been. Since it has been that way for some time now, I'm sure I have rebooted many times since then.

Something someone said . . .

> **wilee-nilee said:**
> The extension pack is installed in a different manner then the guest additions as well.
[http://forums.virtualbox.org/viewtopic.php?f=24&p=164806](http://forums.virtualbox.org/viewtopic.php?f=24&p=164806)

. . . led me to believe that the total package (as I'll call it) invloved a total of 3 element - not 2, as I had previously thought. One of those element, of course, being virtual box itself. Clearly another is the extension pack. I had thought that was all there is to it. Then I hear "guest additions". I had thought that the extension pack and guest additions are one in the same. Clearly virtual box and the extension pack are two separate physical installations file. So then am I supposed to look for an additional installation package/file called guest additions? Or is it already in there? And in where if it is? Did it come with the virtual box install or is it in the extension pack?

:confused:


> So the only file I have besides virtual box itself is filename:

[Quote]
Oracle_VM_VirtualBox_Extension_Pack-4.0.6-71344.vbox-extpack
[/Quote]

---

