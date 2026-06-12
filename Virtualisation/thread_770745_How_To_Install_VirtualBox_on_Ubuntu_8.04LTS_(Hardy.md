---
title: "How To: Install VirtualBox on Ubuntu 8.04LTS (Hardy Heron) [Tutorial]"
date: 2008-04-27
forum: Virtualisation
---

### Post by SendDerek on 2008-04-27
This guide is intended to help users fully install VirtualBox and all of it's features which don't work out of the box such as USB support.  I also have [**this tutorial**]("http://www.derekhildreth.com/blog/how-to-install-virtualbox-on-ubuntu-804lts-hardy-heron-tutorial/") (and others) on [ **my blog**]("http://derekhildreth.com/blog").  It's designed to be quick and painless, so let's get started:


[SIZE="4"][COLOR="DarkRed"]Download VirtualBox:[/COLOR][/SIZE]
Use the following links to download VirtualBox according to your CPU architecture.  If you don't know what this means, you'd probably just better go with the i386 pacakge.

**i386:**
[http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb](http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb)
**AMD64**
[http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb](http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb)

[SIZE="1"]*Note:  The VirtualBox that you have in the Add/Remove Programs list is different because it is the Open Source Edition.  This is generally more difficult to configure, so use the normal VirtualBox program found in the link above.* [/SIZE]

[SIZE="4"][COLOR="DarkRed"]Install VirtualBox:[/COLOR][/SIZE]
Double-click on the package you just downloaded and you will be prompted to install it.

[COLOR="DarkRed"][SIZE="4"]Setup Permissions:[/SIZE][/COLOR]
This can be done in two different ways.  The graphical way or the command line way.

**Via Command Line:**

[COLOR="Gray"][In Terminal][/COLOR] ```
sudo usermod -G vboxusers -a username
```

**Via Graphical Menus:**

Goto *System -> Administration -> Users and Groups*.

Click on the "*Unlock*" button and then enter in your password.

Click on the "*Manage Groups*" button.

Find the "*vboxusers*" group which is probably at the very bottom of the list, highlight it by clicking again,  and click once more on "*Properties*".

Make sure there's a check mark next to your user's name, and you're finished.

[COLOR="DarkRed"][SIZE="4"]Setup USB:[/SIZE][/COLOR]
USB is disabled by default, so you'll probably want to enable it.  Otherwise you'll get an error when you go into the "Settings" of your virtual machine.  To  correct this, you'll need to edit the *mountdevsubfs.sh* file:

[COLOR="Gray"][In Terminal][/COLOR] ```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

Inside, you'll see a block of code that looks like this:
[INDENT][I]#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb[/I][/INDENT]

Change it to look like this (uncomment out the region by deleting the "#'s"):

[INDENT][I]#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb[/I][/INDENT]

Save the changes, log out, and then log back in again for the changes to take place.

[COLOR="DarkRed"][SIZE="4"]Other:[/SIZE][/COLOR]
The VirtualBox Guest Additions image (.iso) file is located here:
[http://www.virtualbox.org/download/1.5.6/VBoxGuestAdditions_1.5.6.iso](http://www.virtualbox.org/download/1.5.6/VBoxGuestAdditions_1.5.6.iso)

[COLOR="DarkRed"][SIZE="4"]Minor Troubleshooting:[/SIZE][/COLOR]
With these instructions, I was able to get my virtual machine working perfectly in VirtualBox.  If you have any problems, please let me know by commenting below.  I will help to resolve your issue and then place it with the solution in this section of the tutorial.  Thank you.

**Package Dependencies**
If you run across a problem with dependencies (like libxercese27 which is included in the libxalan110 package), you'll have at this point to either install it first or go ahead with the installation and run "sudo apt-get -f install" to correct the problems.
*Thanks Princey*

**Compilation of the kernel module FAILED! Error**
While trying to install VirtualBox you receive an error like this:
```
"Compilation of the kernel module FAILED!

VirtualBox will not start until this problem is fixed. Please consult '/var/log/vbox-install.log' to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute '/etc/init.d/vboxdrv' setup as root."
```

[COLOR="Red"]Run the command "sudo /etc/init.d/vboxdrv setup" and see if that helps.[/COLOR] (not yet confirmed)

---

### Post by mihai.ile on 2008-04-28
Very simple and works just fine onmy Ubuntu Hardy 8.04 final. Thank you

---

### Post by ThrobbingBrain66 on 2008-04-28
I can't seem to enable USB support.  I tried your guide, and this one: [http://forum.notebookreview.com/showthread.php?t=242936](http://forum.notebookreview.com/showthread.php?t=242936)

The step you mention seems to be the same as in the link, yet when I go to the settings of my virtual machine, there is no listing for USB.

EDIT: I've been using the version in the Hardy repos, I'll try the version from the website.

---

### Post by SendDerek on 2008-04-29
> **ThrobbingBrain66 said:**
> I can't seem to enable USB support.  I tried your guide, and this one: [http://forum.notebookreview.com/showthread.php?t=242936](http://forum.notebookreview.com/showthread.php?t=242936)

The step you mention seems to be the same as in the link, yet when I go to the settings of my virtual machine, there is no listing for USB.

EDIT: I've been using the version in the Hardy repos, I'll try the version from the website.

The version in the repos is the open source version.  Not the same thing at all.  I'm honestly not sure how to enable USB in that one.  You'd think it would be the same process, but it's not.  Sorry!

---

### Post by SendDerek on 2008-04-29
> **mihai007 said:**
> Very simple and works just fine onmy Ubuntu Hardy 8.04 final. Thank you

Great!  I'm glad to hear it worked out for you.  You're welcome.

---

### Post by paisley_aus on 2008-04-29
Confirming successful installation on AMD64 (Hardy 8.04).

Thanks for the great Tutorial!

---

### Post by lyndaj70 on 2008-04-29
I got it to acknowledge usb okay, but I get an error message about being unable to locate my kernel so it can't add the drivers to my kernel.  Any ideas?

---

### Post by lyndaj70 on 2008-04-29
Okay, I got it to work, but I pulled in another tutorial, which you can find here: [http://www.lostechies.com/blogs/jason_meridth/archive/2008/04/27/using-the-gutsy-gibbon-ubuntu-7-10-non-ose-version-of-virtualbox-with-your-hardy-heron-ubuntu-8-04-install.aspx]("http://www.lostechies.com/blogs/jason_meridth/archive/2008/04/27/using-the-gutsy-gibbon-ubuntu-7-10-non-ose-version-of-virtualbox-with-your-hardy-heron-ubuntu-8-04-install.aspx")

I used that to install the repository into Synaptic, then as I selected VirtualBox I installed the headers for my kernel, which worked.  Apparently this method didn't have headers for my kernel (or I did something wrong - we'll just say I did something wrong).

Thanks for the tutorial!:popcorn:

---

### Post by SendDerek on 2008-04-29
You're welcome!

I'm glad it all worked out okay. :-D

---

### Post by Stian on 2008-04-29
> **SendDerek said:**
> 
[SIZE="4"][COLOR="DarkRed"]Download VirtualBox:[/COLOR][/SIZE]
As of this writing, there is no specific download for 8.04LTS (Hardy Heron), so you will be downloading the version built for 7.10 (Feisty Fawn).

Goto the [VirtualBox download hompage](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI), scroll down to the bottom, click on the "Platform" drop-down menu, and select "Ubuntu 7.10 i386" to download the package.  Note: If you have a 64bit computer, download the "Ubuntu 7.10 AMD64" package.
There are hardy packages, but you have to look a bit around to find them.. [http://www.virtualbox.org/download/1.5.6/](http://www.virtualbox.org/download/1.5.6/)

---

### Post by Devlin67 on 2008-04-29
Worked perfectly on Acer 5102WLMI with 8.04

---

### Post by Wheazel on 2008-04-29
> **Stian said:**
> There are hardy packages, but you have to look a bit around to find them.. [http://www.virtualbox.org/download/1.5.6/](http://www.virtualbox.org/download/1.5.6/)

Much faster download as well.
Works like a charm...

---

### Post by mtgmutton on 2008-04-29
I'm having a bit of a problem here... When I try to install the non-OSE version of VirtualBox, I get the following error message:

 "Compilation of the kernel module FAILED!                                 

    VirtualBox will not start until this problem is fixed. Please consult '/var/log/vbox-install.log' to find out why the kernel module does not  compile. Most probably the kernel sources were not found. Install them and execute '/etc/init.d/vboxdrv' setup as root."

I have no idea what to do...  :(  Any help would be greatly appreciated

---

### Post by Princey on 2008-04-29
Thanks for the HowTo, but it must be noted that some systems (was in my case for sure) that libxalan110 must be installed as it contains the package/library libxercese27 and installation will fail. You'll have at this point to either install it first or go ahead with the installation and run "sudo apt-get -f install" to correct the problems. 

Also of note seeing that it will have to build a component against your kernel headers that build essential and kernel headers should be installed first. Otherwise, great tutorial.

---

### Post by Princey on 2008-04-29
> **mtgmutton said:**
> I'm having a bit of a problem here... When I try to install the non-OSE version of VirtualBox, I get the following error message:

 "Compilation of the kernel module FAILED!                                 

    VirtualBox will not start until this problem is fixed. Please consult '/var/log/vbox-install.log' to find out why the kernel module does not  compile. Most probably the kernel sources were not found. Install them and execute '/etc/init.d/vboxdrv' setup as root."

I have no idea what to do...  :(  Any help would be greatly appreciated

As you read in the tutorial, the one in the repos are much harder to configure. You're better off using the free packages from the virtual website linked to in the tutorial.

---

### Post by SendDerek on 2008-04-29
> **mtgmutton said:**
> I'm having a bit of a problem here... When I try to install the non-OSE version of VirtualBox, I get the following error message:

 "Compilation of the kernel module FAILED!                                 

    VirtualBox will not start until this problem is fixed. Please consult '/var/log/vbox-install.log' to find out why the kernel module does not  compile. Most probably the kernel sources were not found. Install them and execute '/etc/init.d/vboxdrv' setup as root."

I have no idea what to do...  :(  Any help would be greatly appreciated


I was sure this was going to come up eventually.  Now, I'm not 100% sure that this will work in Ubuntu, but it worked everytime for Fedora 8: Go ahead and type in the command "sudo /etc/init.d/vboxdrv setup" and see what happens.  Otherwise, post your log in an attachment from /var/log/vbox-install.log.

---

### Post by SendDerek on 2008-04-29
> **Princey said:**
> Thanks for the HowTo, but it must be noted that some systems (was in my case for sure) that libxalan110 must be installed as it contains the package/library libxercese27 and installation will fail. You'll have at this point to either install it first or go ahead with the installation and run "sudo apt-get -f install" to correct the problems. 

Also of note seeing that it will have to build a component against your kernel headers that build essential and kernel headers should be installed first. Otherwise, great tutorial.

That's an interesting point.  I thought that I had installed VirtualBox on a fresh install of 8.04, but after checking my terminal history, I did have build-essentials installed first.  I will update the tutorial ASAP.  Thanks.

---

### Post by Princey on 2008-04-30
No problem, mate. I'm having one small issue with my setup though. My install went flawlessly after the small hiccup I spoke about. I can see my host machine, I can browse my local network with the computers downstairs, two of which runs Windows. However, I don't have internet access within the guest (running WinXP SP2). Currently I use NAT, no other connection works. For that matter, if I chose direct through host, bridge or any other, virtual box will not load the vm and will report an error message. Still trying to figure what went wrong there.

---

### Post by mtgmutton on 2008-04-30
> **SendDerek said:**
> I was sure this was going to come up eventually.  Now, I'm not 100% sure that this will work in Ubuntu, but it worked everytime for Fedora 8: Go ahead and type in the command "sudo /etc/init.d/vboxdrv setup" and see what happens.  Otherwise, post your log in an attachment from /var/log/vbox-install.log.

I tried this, and this is what showed up in the terminal: 
"* Stopping VirtualBox kernel module vboxdrv                          [ OK ]
* Recompiling VirtualBox kernel module vboxdrv                      
* Look at /var/log/vbox-install.log to find out what went wrong"

So I went into "/var/log/vbox-install.log" and got this:
"Makefile:75: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop."

---

### Post by tgpfx on 2008-04-30
I have followed all the steps (AMD64) and get the following error message

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}

Help anyone ?

---

### Post by Princey on 2008-04-30
> **mtgmutton said:**
> I tried this, and this is what showed up in the terminal: 
"* Stopping VirtualBox kernel module vboxdrv                          [ OK ]
* Recompiling VirtualBox kernel module vboxdrv                      
* Look at /var/log/vbox-install.log to find out what went wrong"

So I went into "/var/log/vbox-install.log" and got this:
"Makefile:75: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop."

That's because you don't have your build essentials installed. Run the following command in the terminal then try re-installing virtual box. ```
sudo apt-get install build-essential linux-headers-`uname -r`
```

@tgpfx I ran into the same problem but can't remember what I did to get it working under Hardy Heron beta. Now that I did a fresh install, I just can't figure for now what I did to get it working. I'll give it a go when I get home and post back my results.

---

### Post by PureW on 2008-05-01
> **tgpfx said:**
> I have followed all the steps (AMD64) and get the following error message

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.
...

I get this message too, when trying to enter the settings of my VM:
> 
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Resultatkod: 
0x80004005
Komponent: 
Host
Gränssnitt: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Anropare: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}



---

### Post by spyros71 on 2008-05-01
Great how to. Worked fine for me. Many thanks :)

---

### Post by Princey on 2008-05-01
For those getting the USB error, if you had followed the HowTo as described, you still will get the error message cropping up ***UNTIL*** you reboot. For those who haven't, here's the directions again:

Enter ```
sudo gedit /etc/init.d/mountdevsubfs.sh
``` in the terminal (substitute gedit with either kedit/kate/kwrite if you're using Kubuntu). Scroll down to the following lines> #
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usbremove the # mark from mkdir down to mount so it looks now like this > #
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

The HowTo states to log out and back in, but the changes won't fully work ***UNTIL*** you reboot. So, restart and you'll notice that the error message no longer appears.


On a side note, can anyone tell me why I can't get Internet using NAT on the xp guest in Virtual box? I'm thinking of purging everything and starting afresh.

---

### Post by wahoobob on 2008-05-01
I have it working - but I was not able to figure a way to get WXP to use the other Hard disk partitions for getting a file into word, etc.  Is this possible?

---

### Post by Princey on 2008-05-01
Try adding that folder as part of the shared folders in the settings section of that virtual machine before it's booted up. There are other ways to do it, but I opted for that method. To me, it's the easiest.

---

### Post by wahoobob on 2008-05-01
Can you give me a quick course on how to do that?  I looked and don't see how to add a folder when I bring that up.  I enabled guest extras, but the only thing that shows up is the primary master.

---

### Post by OldTimeTech on 2008-05-01
I want to thank all in this post....I've got my virtualbox running and installing as I write this...again thanks ;))

---

### Post by Green_Star on 2008-05-01
.
.
.
.
.
This guide is wonderful, I think if you add a section about adding host networking then that would be great.

Because NAT case will not help me when I am testing some configuration/services like web server, asterisk etc or using remote login with xp-pro installed in virtualbox.
.
.
.
.
.

---

### Post by dstark on 2008-05-01
Thanks so much for the wonderful directions. I'm very new to Ubuntu, so those helped *a lot*. To betray my ignorance further, how does one start virtualbox after setting it up this way?

Installing the ose version from the repository produces an icon under applications, but after installing virtualbox the way suggested in this thread, I don't see an equivalent icon or anything and I don't yet have the savvy to know what else to try ;-).

Thanks so much!

---

### Post by Princey on 2008-05-01
> **wahoobob said:**
> Can you give me a quick course on how to do that?  I looked and don't see how to add a folder when I bring that up.  I enabled guest extras, but the only thing that shows up is the primary master.

Once you have virtual box open, scroll down to shared folders as seen here [IMG]http://i307.photobucket.com/albums/nn285/emmjey/OtherForums/vbox1.png[/IMG]

Click on it and the next box should open open to something like this [IMG]http://i307.photobucket.com/albums/nn285/emmjey/OtherForums/vbox2.png[/IMG]

To your right, click on the green icon with the + sign and add whatever folder you desire.

---

### Post by Princey on 2008-05-01
> **dstark said:**
> Thanks so much for the wonderful directions. I'm very new to Ubuntu, so those helped *a lot*. To betray my ignorance further, how does one start virtualbox after setting it up this way?

Installing the ose version from the repository produces an icon under applications, but after installing virtualbox the way suggested in this thread, I don't see an equivalent icon or anything and I don't yet have the savvy to know what else to try ;-).

Thanks so much!

I'm trying to understand what you're asking, does that mean you have the both installed or you installed the version from innotek? The way you asked seems a bit confusing, however, just in case you used the one from innotek site, it should create a shortcut automatically on your desktop. I'd suggest if you previously installed the ose packages from the repositories, you completely purge it before following this tutorial.

---

### Post by arrrghhh on 2008-05-02
great tut - i already used these methods to install VB on gutsy.  however, ever since i upgraded to hardy my USB devices have been greyed out (except for my printer...).  like when i go to the devices -> usb menu the devices appear there but are greyed out.  i have filters setup for them, and i have followed this tut.  i tried reinstalling virtualbox but that didn't seem to work.  not sure how to remove software that wasn't installed via apt-get or repo...  thanks!

update:

thanks to xxzeenoxx in [this](http://ubuntuforums.org/showthread.php?t=341740) thread, i got usb working.  here's the stuff that helped me:

> 
-Create a group called "usbfs" and add yourself to it.

-In terminal issue the following command:

sudo gedit /etc/fstab

-In this file paste the following lines, and change the group ID according to the group ID that is shown for the group "usbfs".


# 1001 is the USB group ID
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0


-Save and close file.


-In terminal, issue the following command:

VBoxManage list usbhost

-Use the output of this command to set up the filters for USB devices under VirtualBox.

-Reboot


*USB DEVICES HAVE TO BE UNMOUNTED BEFORE VIRTUAL MACHINE CAN RECOGNIZE THEM*


...I hope this helps.


---

### Post by drhiii on 2008-05-02
I look forward to using this Tutorial.  Thank goodness it exists!

QUick question before proceeding... should I remove any version of VirtualBox before installing based on the Tut here?  I had a prior version of VB working, upgraded to 8.04, it broke, I followed one other recommendation for foxing the problem but the install was not quite sucessful tho I did get farther...

Question becomes, should I remove prior version?  Not the .vdi file, just the VB installation?

tx a mil

---

### Post by Princey on 2008-05-02
If you used the packages from Innotek's website, I think you should uninstall the older packages first.```
sudo dpkg -r packagename
``` where packagename = name of virtualbox package. 

P.S. That's the command for removing apps manually installed through .deb files outside of using the apt-get or the repositories.

---

### Post by dstark on 2008-05-02
Thanks, Princey.

I managed to get the OSE version working by following the directions [here]("https://help.ubuntu.com/community/VirtualBox?highlight=(virtualbox)") for Gutsy and letting the updater upgrade the software for Hardy.

Thanks, again.

---

### Post by grindboy on 2008-05-02
Cheers man. I have VB installed but after going from 7.10 to 8.04 it threw up an odd error when starting XP. So I uninstalled it reinstalled it (following your guide) and now XP is back in all its proprietary glory!

---

### Post by rialto on 2008-05-02
thanks so much for this howto, I was able to get windows installed and everything works except for my mouse.  Does anyone know how i can get the mouse working?  It keeps telling me i have to capture it and something about guest additions.  help me out?

edit: I have also tried to install it by devices>install guest additions

but when i did this nothing happened.

---

### Post by Princey on 2008-05-02
You first need to mount your guest additions as an iso in the cd manager under the options for the vm that you're running. When you boot xp, just do what you did to install the tools. See the screenshot [here]("http://ubuntuforums.org/showpost.php?p=4855883&postcount=31") to see what I'm talking about. By the way, what type of mouse are you using? Ps2 or usb?

---

### Post by cor2y on 2008-05-02
Help i followed this tutorial VirtualBox seems to be working but when i launch the guest os (windows xp) i just get a black screen.
The vdi is one that came with me through 3 versions of ubuntu, when i installed the new VirtualBox deb i got a message saying it had to update so i clicked the save option everything went ok.
Now the guest os window says its running but all i see is a black screen.

---

### Post by cheeseman557 on 2008-05-02
> **Princey said:**
> That's because you don't have your build essentials installed. Run the following command in the terminal then try re-installing virtual box. ```
sudo apt-get install build-essential linux-headers-`uname -r`
```


I'm having that same problem with the linux-headers bit. I updated ubuntu today and installed the newest version according to synaptic (linux-header-2.6.24-15, 2.6.24-16, and 2.6.24-17). uname -r returns "2.6.24-12-generic". the log file says:

```
Makefile:75: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

```

How do I fix this? Thanks! :)

---

### Post by Princey on 2008-05-02
Using synaptic, remove the other headers except 2.6.24-17 and run the command again, then resume with your installation.

---

### Post by cheeseman557 on 2008-05-02
Ahh, that doesn't work! :( Same error.

I also have "linux-image-2.6.24-12-generic", 15, 16, 17 installed too. Should I remove everything except 17? Thanks!

---

### Post by Princey on 2008-05-02
Yes, that's what I meant. Remove all others besides the latest current headers.

---

### Post by arrrghhh on 2008-05-02
it is a good practice to uninstall packages before installing new ones, but the innotek people allow for simple upgrades.  just run the .deb file and it'll take care of the rest!

---

### Post by aldodefilippi on 2008-05-03
A number of days ago I downloaded a version of VirtualBox for my Ubunty gutsy OS. Since then I have not been able to open my CD drive. I keep being told that the media is not mounted. When I tried to configure the CDROM in VirtualBox the drop down window had no contents. How do I restore access to my CD drive from Ubuntu? Thanks

---

### Post by drhiii on 2008-05-03
Thank you thank you.   Am up and running again.  I had an error still when trying to run the .VDI file, but someone on the VB forums pointed me to a simple solution, it worked, and I am back up and running.  

I am yet again, grateful to this community for coming to the aid of a regular user who gets lost now and then.  Much appreciated.  I can only think that karma rewards those who come ot the aid of n00bs like me.

regards, drh


> **SendDerek said:**
> This guide is intended to help users fully install VirtualBox and all of it's features which don't work out of the box such as USB support.  I also have [**this tutorial**]("http://derekhildreth.com/blog/index.php/2008/04/how-to-install-virtualbox-on-ubuntu-804lts-hardy-heron-tutorial") (and others) on [ **my blog**]("http://derekhildreth.com/blog").  It's designed to be quick and painless, so let's get started:


[SIZE="4"][COLOR="DarkRed"]Download VirtualBox:[/COLOR][/SIZE]
Use the following links to download VirtualBox according to your CPU architecture.  If you don't know what this means, you'd probably just better go with the i386 pacakge.

**i386:**
[http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb](http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb)
**AMD64**
[http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb](http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb)

[SIZE="1"]*Note:  The VirtualBox that you have in the Add/Remove Programs list is different because it is the Open Source Edition.  This is generally more difficult to configure, so use the normal VirtualBox program found in the link above.* [/SIZE]

[SIZE="4"][COLOR="DarkRed"]Install VirtualBox:[/COLOR][/SIZE]
Double-click on the package you just downloaded and you will be prompted to install it.

[COLOR="DarkRed"][SIZE="4"]Setup Permissions:[/SIZE][/COLOR]
This can be done in two different ways.  The graphical way or the command line way.

**Via Command Line:**

[COLOR="Gray"][In Terminal][/COLOR] ```
sudo usermod -G vboxusers -a username
```

**Via Graphical Menus:**

Goto *System -> Administration -> Users and Groups*.

Click on the "*Unlock*" button and then enter in your password.

Click on the "*Manage Groups*" button.

Find the "*vboxusers*" group which is probably at the very bottom of the list, highlight it by clicking again,  and click once more on "*Properties*".

Make sure there's a check mark next to your user's name, and you're finished.

[COLOR="DarkRed"][SIZE="4"]Setup USB:[/SIZE][/COLOR]
USB is disabled by default, so you'll probably want to enable it.  Otherwise you'll get an error when you go into the "Settings" of your virtual machine.  To  correct this, you'll need to edit the *mountdevsubfs.sh* file:

[COLOR="Gray"][In Terminal][/COLOR] ```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

Inside, you'll see a block of code that looks like this:
[INDENT][I]#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb[/I][/INDENT]

Change it to look like this (uncomment out the region by deleting the "#'s"):

[INDENT][I]#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb[/I][/INDENT]

Save the changes, log out, and then log back in again for the changes to take place.

[COLOR="DarkRed"][SIZE="4"]Minor Troubleshooting:[/SIZE][/COLOR]
With these instructions, I was able to get my virtual machine working perfectly in VirtualBox.  If you have any problems, please let me know by commenting below.  I will help to resolve your issue and then place it with the solution in this section of the tutorial.  Thank you.

**Package Dependencies**
If you run across a problem with dependencies (like libxercese27 which is included in the libxalan110 package), you'll have at this point to either install it first or go ahead with the installation and run "sudo apt-get -f install" to correct the problems.
*Thanks Princey*

**Compilation of the kernel module FAILED! Error**
While trying to install VirtualBox you receive an error like this:
```
"Compilation of the kernel module FAILED!

VirtualBox will not start until this problem is fixed. Please consult '/var/log/vbox-install.log' to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute '/etc/init.d/vboxdrv' setup as root."
```

[COLOR="Red"]Run the command "sudo /etc/init.d/vboxdrv setup" and see if that helps.[/COLOR] (not yet confirmed)

---

### Post by bornakke on 2008-05-03
> **arrrghhh said:**
> *USB DEVICES HAVE TO BE UNMOUNTED BEFORE VIRTUAL MACHINE CAN RECOGNIZE THEM*

Managed to get my printer to work without, but how do you unmount a printer? Or are the reason why it worked without that you don't need to unmount printers?

Thank you for you great solution!

---

### Post by kurtfagerburg on 2008-05-03
I'm still getting the following entry in the install log file (/var/log/vbox-install.log) when I run sudo /etc/init.d/vboxdrv setup:

Makefile:75: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

What config file am I supposed to specify the KERN_DIR in and how do I determine the directory my current Linux kernel sources are in?

Thanks for the stuff here.  I've been looking for the Hardy VirtualBox packages and couldn't find them anywhere except in your link (I'm still a newbie and not well versed in how to find the packages outside of Synaptic).

---

### Post by schlox on 2008-05-03
I have no problems with Virtualbox installation. I also installed XP. My problem is about the sound.

Although I see the speaker icon at the Start menu right side, I do not hear any sound. I tried everything as I do at XP but still I don't hear any sound.

Any comments?


Thanks in advance.
Schlox


I solved the problem. Make the Audio input method to PULSEAUDIO then it was totally ok.

---

### Post by schlox on 2008-05-03
I have a problem with usb. But I think it occurred because of another reason. Please have a look at my virtual box window:

[IMG]http://sharepic.us/out.php/i6577_ScreenshotVirtualBoxOSE.png[/IMG]

So at the Details screen, there is no USB-ports part!!!

Actually, I have removed the #s from "mountdevsubfs.sh" but I think my problem is because of something else.

The reason why I installed Virtualbox and then windows was only for webcam chat. And now I am not able to use usb devices. Please somebody help me...

---

### Post by schlox on 2008-05-03
in addition to the previous entry, I want to add the following output if it may help:

schlox@ScHLoX:~$ VBoxManage list usbhost
VirtualBox Command Line Management Interface Version 1.5.6_OSE
(C) 2005-2008 innotek GmbH
All rights reserved.

[!] FAILED calling Host->GetUSBDevices(CollPtr.asOutParam()) at line 1958!
[!] Primary RC  = 0x80004001
[!] Full error info present: false, basic error info present: false

---

### Post by mistywindow on 2008-05-03
Really appreciated your post SendDerek.
I sweated blood trying to get VirtualBox running from the Synaptics installer in Hardy Heron. You saved my bacon.

---

### Post by Princey on 2008-05-03
@ schlox, which of the virtual box are you using? From the repositories or the free commercial version from sun innotek?

@aldodefilippi uninstall virtual box and see if you will regain access of your CD Drive.

---

### Post by olavjunior on 2008-05-04
Does anyone know how to start the guest os directly without starting VrtualBox first? (I had a quick starter in Gutsy, but can't remember the command)

---

### Post by be4truth on 2008-05-04
> **ThrobbingBrain66 said:**
> I can't seem to enable USB support.  I tried your guide, and this one: [http://forum.notebookreview.com/showthread.php?t=242936](http://forum.notebookreview.com/showthread.php?t=242936)

The step you mention seems to be the same as in the link, yet when I go to the settings of my virtual machine, there is no listing for USB.

EDIT: I've been using the version in the Hardy repos, I'll try the version from the website.

I add this line to my /etc/fstab file.

```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

Then I log out and in and the USB works without any problems.

---

### Post by lyndaj70 on 2008-05-04
> 
Compilation of the kernel module FAILED! Error
While trying to install VirtualBox you receive an error like this:
Code:

"Compilation of the kernel module FAILED!

VirtualBox will not start until this problem is fixed. Please consult '/var/log/vbox-install.log' to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute '/etc/init.d/vboxdrv' setup as root."

Run the command "sudo /etc/init.d/vboxdrv setup" and see if that helps. (not yet confirmed)

I had the exact same problem.  When you use Synaptic to install Virtualbox, make sure to go to the suggested packages and select the linux headers that match your kernel.  I believe that it generally installs the generic kernel headers, whereas some have other kernels, like the "rt" kernel that Ubuntu Studio installs.  

Once you install that header then go to your command line and execute '/etc/init.d/vboxdrv' setup as root.  That should solve your problem.

Hope this helps!
Lynda

---

### Post by be4truth on 2008-05-04
> **lyndaj70 said:**
> I had the exact same problem.  When you use Synaptic to install Virtualbox, make sure to go to the suggested packages and select the linux headers that match your kernel.  I believe that it generally installs the generic kernel headers, whereas some have other kernels, like the "rt" kernel that Ubuntu Studio installs.  

Once you install that header then go to your command line and execute '/etc/init.d/vboxdrv' setup as root.  That should solve your problem.

Hope this helps!
Lynda

Are you aware that the Open Source version doesn't have USB support?

---

### Post by laffys on 2008-05-05
Ok everything was working until the kernel update was done, now i get the following;


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
Any thoughts on fixing this?

---

### Post by lyndaj70 on 2008-05-05
> **be4truth said:**
> Are you aware that the Open Source version doesn't have USB support?
  Yes, I am.  You have to install the repos for the regular VirtualBox in Synaptic to get usb.  Everything else applies, because the VirtualBox repos also have the linux headers needed.  You just have to pick which one you need for your kernel.  I have heard that there is a workaround to get things like usb usb jumpdrives and such working, but I never fooled with it so I don't know anything about it.

---

### Post by laffys on 2008-05-06
Well I found what to do and thanks.

Here is what i did;

sudo /etc/init.d/vboxdrv setup

---

### Post by daflame on 2008-05-07
For those of you that still want to run the open source edition virtualbox from the Hardy repos you still can, but you will need an updated virtualbox-ose-modules package.  I have built such a package (I was tired of waiting for the developers to release it.  However, I have noticed that they just committed a package to the universe proposed repos yesterday so if you want these packages you can have them, but I suspect in two days everything will work again.

---

### Post by rialto on 2008-05-07
Hi, I can't get the mouse to work.  Currently, I'm just using a laptop mouse touchpad and I've tried it over and over, I even thought it could have been the previous install of Virtual-Box OSE that could have corrupted it but nothing.  Please help me out ^^;

Current Computer: Latitude D410

---

### Post by Lothas on 2008-05-08
I've been using VB for a while now but since I upgraded to Hardy it's been hardly working. USB won't work anymore. I can see 3 devices plugged in but I can't give any of them to the Guest (Win XP). I have added 2 of the devices in Settings and still not working. Right-clicking the USB icon on the running VM will show the list of USB devices in grey and I can't select anyone :(

Other than that, shared folders are still pretty crappy and Win XP gets stuck much more often than with 7.10 :mad:

---

### Post by IncadudeF on 2008-05-09
same here i cant get usb to work and now my network doesnt work. I cant use the internet on my guest os windows xp and cant get any usb devices to work. :(  I just want to use VB to use a messenger to video chat with people in Peru.

---

### Post by gtr@frii.com on 2008-05-09
I got USB working following the tutorial.  I cannot get the mouse to work.  Mouse clicks just take me through the "You have clicked the ..." dialogue box from which you can supposedly set up capture or not.  Also you can supposedly get things to work with the right control key.  Nothing seems to work.  Trying to load guest additions by clicking devices-> guest additions
also doesn't do anything.  It kind of hints that you can select that with the (Underlined) i key, but that didn't work with any combination of alt, ctrl, shift ...  I've tried this with both a ps-2 and a usb mouse.  The keyboard (i.e., arrow keys) works fine regardless of the icon toggled with the right control key.  This is with the sun version 1.6.  I was just attempting to get familiar with virtual box from a dual boot XP Pro and Hardy Heron ubuntu box.  It's a relatively fast dual core Intel with 2 gig of ram and the guest OS I am trying is 7.04 Xubuntu.  At this point all I get is the live cd up which eventually goes to screen saver. w/o the mouse, I don't have a clue how to actually install the guest.

Anyone got any ideas?

---

### Post by rdoolen on 2008-05-14
I am also having problems getting mouse integration to work on my WindowsXP guest. I started with VirtualBox 1.5.4 on Gutsy, upgraded to 1.5.6 on Hardy and then to 1.6 on Hardy. In every case I get the same problem. I do have Guest additions installed. I also have a KDE4 virtual machine as a guest and the mouse integration works fine in that VM. 

Here is how my mouse behaves. If I have mouse integration enabled, the mouse doesn't respond to motion. In fact, if the pointer is visible in the VM, and I drag the mouse over the window, the pointer moves down and to the right -- no matter what direction I move the mouse. It will do this until it is out of sight in the bottom corner. The mouse does respond to the button clicks.

If I disable mouse integration, the mouse works fine, but I have to capture and release it.

I have also tried multiple mice, all PS/2.

Thanks for any help.

---

### Post by nitewulf on 2008-05-14
Ok, stupid question:  I installed virtual box, how do i run it?  I don't see it anywhere.

---

### Post by mistywindow on 2008-05-15
It should show up in Applications > System Tools.

---

### Post by be4truth on 2008-05-15
> **nitewulf said:**
> Ok, stupid question:  I installed virtual box, how do i run it?  I don't see it anywhere.

You can start it in a terminal

```
VirtualBox
```

---

### Post by taurusx5 on 2008-05-15
Currently, I have Ubuntu 7.10 and have Virtualbox Closed Source Edition already installed. I have 2 questions:

1) Will upgrading to Ubuntu 8.04 affect the USB feature in my closed source edition of virtualbox?

2) Will I have to uninstall my virtualbox before I upgrade to 8.04, and then reinstall virtualbox? 

3) Will upgrading to 8.04 affect guest additions in virtualbox?

---

### Post by andlinux21 on 2008-05-16
Thanks for the HOWTO I got this installed on my Toshiba laptop.  My problem is i dont have a right Ctrl key and dont know how to change  the key function needed to exit Virtual box back to my main screen can anyone help me change that hotkey?

---

### Post by gusman21 on 2008-05-16
> **taurusx5 said:**
> Currently, I have Ubuntu 7.10 and have Virtualbox Closed Source Edition already installed. I have 2 questions:

1) Will upgrading to Ubuntu 8.04 affect the USB feature in my closed source edition of virtualbox?

2) Will I have to uninstall my virtualbox before I upgrade to 8.04, and then reinstall virtualbox? 

3) Will upgrading to 8.04 affect guest additions in virtualbox?

1: Yes, but it is fixable.
do your upgrade.  once complete add the following lines to your /etc/fstab

```
 

# USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 
```

2: no
3: no

Good Luck!

---

### Post by Gourgi on 2008-05-17
in case anyone is interested there is virtualbox 1.6.0 available 
i found the discussion here
[http://ubuntuforums.org/showthread.php?t=788016&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=788016&highlight=virtualbox)

btw **great guide** :popcorn:

i 've seen around the forums an older guide for virtualbox that explained about the guest-addons, i'm looking for it now and i'll edit my post

[[COLOR="Red"]edit[/COLOR]] 
here it is, look at step 2
[http://ubuntuforums.org/showthread.php?t=603661](http://ubuntuforums.org/showthread.php?t=603661)
[[COLOR="Red"]/edit[/COLOR]]

also there is a detailed thread about virtualbox's snapshots, take a look
[http://ubuntuforums.org/showthread.php?t=689982&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=689982&highlight=virtualbox)

---

### Post by spoonernash on 2008-05-18
Has any one gotten virtualbox running on 8.04 server edition? I am trying to determine the minimum X related dependencies.

I have been trying to get virtualbox to run on 8.04 server (no X) headless, as described around page 90 of the virtualbox user manual, so that I can access windows installs from a ppc mac using rdp. I forced the package install without some X related dependencies because I wanted to avoid getting X installed on this server. It seemed to get installed. I tried to test it by starting a damm small linux live cd in a vm. I started the vm and then connected with rdesktop from another computer. I got the initial dsl boot screen, so it seems to work. But when I hit enter to boot, the vm dies after a few seconds and the console where the vm was started has a message about waiting 15 seconds for a debugger to attach and then killing the vm when one does not.

Any advice?

---

### Post by be4truth on 2008-05-18
> **andlinux21 said:**
> Thanks for the HOWTO I got this installed on my Toshiba laptop.  My problem is i dont have a right Ctrl key and dont know how to change  the key function needed to exit Virtual box back to my main screen can anyone help me change that hotkey?

Open VirtualBox. Go to File/Preferances/Input.
To be honest: It is a good idea to check the preferences of a software before you ask questions like this. Thx

---

### Post by perpetus on 2008-05-22
> **SendDerek said:**
> This guide is intended to help users fully install VirtualBox and all of it's features which don't work out of the box such as USB support.  I also have [**this tutorial**]("http://www.derekhildreth.com/blog/how-to-install-virtualbox-on-ubuntu-804lts-hardy-heron-tutorial/") (and others) on [ **my blog**]("http://derekhildreth.com/blog").  It's designed to be quick and painless, so let's get started:


[SIZE="4"][COLOR="DarkRed"]Download VirtualBox:[/COLOR][/SIZE]
Use the following links to download VirtualBox according to your CPU architecture.  If you don't know what this means, you'd probably just better go with the i386 pacakge.

**i386:**
[http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb](http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb)
**AMD64**
[http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb](http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb)

[SIZE="1"]*Note:  The VirtualBox that you have in the Add/Remove Programs list is different because it is the Open Source Edition.  This is generally more difficult to configure, so use the normal VirtualBox program found in the link above.* [/SIZE]

[SIZE="4"][COLOR="DarkRed"]Install VirtualBox:[/COLOR][/SIZE]
Double-click on the package you just downloaded and you will be prompted to install it.

[COLOR="DarkRed"][SIZE="4"]Setup Permissions:[/SIZE][/COLOR]
This can be done in two different ways.  The graphical way or the command line way.

**Via Command Line:**

[COLOR="Gray"][In Terminal][/COLOR] ```
sudo usermod -G vboxusers -a username
```

**Via Graphical Menus:**

Goto *System -> Administration -> Users and Groups*.

Click on the "*Unlock*" button and then enter in your password.

Click on the "*Manage Groups*" button.

Find the "*vboxusers*" group which is probably at the very bottom of the list, highlight it by clicking again,  and click once more on "*Properties*".

Make sure there's a check mark next to your user's name, and you're finished.

[COLOR="DarkRed"][SIZE="4"]Setup USB:[/SIZE][/COLOR]
USB is disabled by default, so you'll probably want to enable it.  Otherwise you'll get an error when you go into the "Settings" of your virtual machine.  To  correct this, you'll need to edit the *mountdevsubfs.sh* file:

[COLOR="Gray"][In Terminal][/COLOR] ```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

Inside, you'll see a block of code that looks like this:
[INDENT][I]#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb[/I][/INDENT]

Change it to look like this (uncomment out the region by deleting the "#'s"):

[INDENT][I]#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb[/I][/INDENT]

Save the changes, log out, and then log back in again for the changes to take place.

[COLOR="DarkRed"][SIZE="4"]Other:[/SIZE][/COLOR]
The VirtualBox Guest Additions image (.iso) file is located here:
[http://www.virtualbox.org/download/1.5.6/VBoxGuestAdditions_1.5.6.iso](http://www.virtualbox.org/download/1.5.6/VBoxGuestAdditions_1.5.6.iso)

[COLOR="DarkRed"][SIZE="4"]Minor Troubleshooting:[/SIZE][/COLOR]
With these instructions, I was able to get my virtual machine working perfectly in VirtualBox.  If you have any problems, please let me know by commenting below.  I will help to resolve your issue and then place it with the solution in this section of the tutorial.  Thank you.

**Package Dependencies**
If you run across a problem with dependencies (like libxercese27 which is included in the libxalan110 package), you'll have at this point to either install it first or go ahead with the installation and run "sudo apt-get -f install" to correct the problems.
*Thanks Princey*

**Compilation of the kernel module FAILED! Error**
While trying to install VirtualBox you receive an error like this:
```
"Compilation of the kernel module FAILED!

VirtualBox will not start until this problem is fixed. Please consult '/var/log/vbox-install.log' to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute '/etc/init.d/vboxdrv' setup as root."
```

[COLOR="Red"]Run the command "sudo /etc/init.d/vboxdrv setup" and see if that helps.[/COLOR] (not yet confirmed)
He,

I am having trouble with this virtual box. I succeded in installing the virtualbox, but the problem is that when I use to the virtualbox to install a Windows XP, the virtualbox does not capture the keyboard. I need to hit enter at a step to keep running the Windows XP installation but no way to move on. Any hint?

Thanks

---

### Post by gusman21 on 2008-05-22
> **perpetus said:**
> He,

I am having trouble with this virtual box. I succeded in installing the virtualbox, but the problem is that when I use to the virtualbox to install a Windows XP, the virtualbox does not capture the keyboard. I need to hit enter at a step to keep running the Windows XP installation but no way to move on. Any hint?

Thanks

have you tried to click on the running virtual box window?

---

### Post by be4truth on 2008-05-22
To enable the USB I always added so far since versin 1.5 this line into /ect/fstab

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0


I had never any problems with the usb and VirtualBox

After adding your name to the vbox group you have to log out and in so that the changes are effective.

---

### Post by perpetus on 2008-05-23
Yes I added the user to the vboxusers group.

> **gusman21 said:**
> have you tried to click on the running virtual box window?

Yes I did and I get a popup informing me that the the virtualbox will capture the mouse and the keyboard, which I accept by clicking on the "capture" button. I then hit the "enter" key as the windows xp setup program is asking me to do. But nothing happens.

Your help is still desperately needed. Thanks.

Maybe I should give more info about the computer I am using: hp pavilion dv2000. I am pasting below the settings of the VB


General
Name Windows XP
OS Type Windows XP
Base Memory 400 MB
Video Memory 64 MB
Boot Order Floppy, CD/DVD-ROM, Hard Disk
ACPI Enabled
IO APIC Disabled
VT-x/AMD-V Disabled
PAE/NX Disabled

Hard Disks
IDE Primary Master NewHardDisk3.vdi [Normal, 10.09 GB]

CD/DVD-ROM
Image Windows.XP.PRO.French.Pre.SP3.ULTIMATE EDITION -V5.0 By Mad Dog[Get24].iso

Floppy
Not mounted

Audio
Host Driver Null Audio Driver
Controller ICH AC97

Network
Adapter 0 PCnet-FAST III (NAT)

Serial Ports
Port 0 COM1, Disconnected
Port 1 COM2, Disconnected

USB
Device Filters 0 (0 active)

Shared Folders
None

Remote Display
Disabled

Regards,
Perpetus

---

### Post by styrofoam cup on 2008-05-23
I have a problem similar to the one above. When I click in the window, and then click capture - but the mouse does not capture. I am using a USB mouse and think this may be part of the problem. The usb mouse shows in the devices menu, under usb devices, but is greyed out and the mouse over tool tip says the mouse is unavailable.
I have not been able to get the guest additions to install either. I do have it set in the cd/dvd rom and mounted.

edit - more info. I tried it out with a regular ps2 mouse and it was still the same. I removed the virtual disk and machine and the virtualbox package (the good one, not the OSE one), then reinstalled the package and setup everything again. It was the same effect. I am using Hardy 64bit. Keyboard capturing works ok.

Thanks.

---

### Post by loco on 2008-05-25
Great tutorial, now the USB devices appear... but they appear in GREY! and I cant select them. Any idea how to fix it?



EDIT: I "found" the solution following the tutorial here [http://forum.notebookreview.com/showthread.php?t=242936t](http://forum.notebookreview.com/showthread.php?t=242936t)

Now usb devices are not grey :)

---

### Post by 1467 on 2008-05-26
i still get 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by 1467 on 2008-05-26
fixed ty grat tutorial

---

### Post by wahoobob on 2008-05-28
> **lyndaj70 said:**
> Yes, I am.  You have to install the repos for the regular VirtualBox in Synaptic to get usb.  Everything else applies, because the VirtualBox repos also have the linux headers needed.  You just have to pick which one you need for your kernel.  I have heard that there is a workaround to get things like usb usb jumpdrives and such working, but I never fooled with it so I don't know anything about it.

I installed Virtualbox 1.60 from the Sun site and it runs XP just fine.  Running in seamless mode works but there is only the xp virtual drive available and I can't get it to see USB items, or my home folder.  Do I need to uninstall and go to synaptic?  I'm not the greatest with the terminal so any details would be appreciated.

---

### Post by wahoobob on 2008-05-28
Now that virtualbox is in Sun, the 1.6 version is there.  Are these instructions still the same?  I have not been able to get it to share the home folder or look at USB devices.  Sorry about the double post - I got lost in the structure......

---

### Post by kurtfagerburg on 2008-05-28
Just wanted to say thanks to everybody for the information here.  I was able to get my XP partition running through VirtualBox and it works great.  Guess this will be an acceptable mid point until all MS products become totally obsolete.

Long live Ubuntu!!!!

---

### Post by wahoobob on 2008-05-29
I got the vbox working and now I open it today and it says:
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason.  Re-setup the kernel module by executing "/etc/init.d/vboxdrv setup" as root.
VBox status code: -1908 (VERR_VM_DRIVER_NET_INSTALLED)

Any idea what is going on?  I ran the command and it straightened out ??? ( I guess) the problem, but any idea what the problem was?

Still can't work out the problem of the files in home and usb items being accessible to XP.

---

### Post by thkaal on 2008-05-29
I hope this works.  Five other attempts at installing VB on Hardy has resulted in...  Loss of usb wireless, loss of sound, and no video card detection on boot up of Ubuntu.  However, VB seems to work except for graphics.  And removing vb does not bring back anything, only complete reinstall.

I'm on an HP using an old geforce 2 vc.

---

### Post by styrofoam cup on 2008-06-01
yea, using 1.6 fixed some of my probs too. also RTFM to get mouse integration (and guest additions) working. IE install from inside windows, after mounting the iso. :KS

---

### Post by cascades on 2008-06-03
I was going crazy here, couldn't get VirtualBox 1.6.0 working on Hardy. I had 1.5.6 working fine under Gutsy.

At starting a virtual machine it kept hanging with the message "Starting the virtual machine... 0%".

Tried all possible settings, nothing helped. But I found the problem in the end... KVM was the culprit; removing the kernel module kvm_intel solved everything! I now removed KVM all together.

In case somebody else is struggling with this, I thought I let everyone know.

---

### Post by encrypted on 2008-06-04
I downloaded the file virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb but everytime I double click it, I get the error "Error: Wrong Architecture i386". I have a core 2 duo processor so I have no clue why it's giving me the error. Any tips on this ?

---

### Post by zeroameca87 on 2008-06-04
I have installed VirtualBox successfully thanks to this guide but i get this error message upon starting up:


Could not load the settings file '/home/un1co/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'version' has a value, '1.3-linux', that does not match its #FIXED value, '1.2-linux'
Location: '/home/un1co/.VirtualBox/VirtualBox.xml', line 5, column 83.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}

 

ANY HELP??

---

### Post by Gourgi on 2008-06-05
> **encrypted said:**
> I downloaded the file virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb but everytime I double click it, I get the error "Error: Wrong Architecture i386". I have a core 2 duo processor so I have no clue why it's giving me the error. Any tips on this ?
**[COLOR="Red"]Wrong Architecture[/COLOR]**
you've downloaded 1386.deb but it looks like you use ubuntu amd64 
try download the ubuntu 8.04 AMD from sun's download page
[http://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/VerifyItem-Start/virtualbox_1.6.0-30421_Ubuntu_hardy_amd64.deb?BundledLineItemUUID=my5IBe.oE2QAAAEaI5wnfVhf&OrderID=yZ1IBe.o4RkAAAEaD5wnfVhf&ProductID=r.1IBe.oZ1wAAAEZ_qkZKqcY&FileName=/virtualbox_1.6.0-30421_Ubuntu_hardy_amd64.deb](http://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/VerifyItem-Start/virtualbox_1.6.0-30421_Ubuntu_hardy_amd64.deb?BundledLineItemUUID=my5IBe.oE2QAAAEaI5wnfVhf&OrderID=yZ1IBe.o4RkAAAEaD5wnfVhf&ProductID=r.1IBe.oZ1wAAAEZ_qkZKqcY&FileName=/virtualbox_1.6.0-30421_Ubuntu_hardy_amd64.deb)

---

### Post by encrypted on 2008-06-05
I actually have a core2 duo processor on a vaio notebook so I'm pretty certain it wasnt the AMD issue

---

### Post by Gourgi on 2008-06-05
> **encrypted said:**
> I actually have a core2 duo processor on a vaio notebook so I'm pretty certain it wasnt the AMD issue

write in terminal
```

uname -a

```
if the output is 
```

Linux gourgi 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_[COLOR="Red"]**64**[/COLOR] GNU/Linux

```
(see the 64) then i think you need amd64.deb

---

### Post by encrypted on 2008-06-05
Thanks for the response, I'll give amd64 a whirl regardless and see if it works.

---

### Post by encrypted on 2008-06-05
> **Gourgi said:**
> write in terminal
```

uname -a

```
if the output is 
```

Linux gourgi 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_[COLOR="Red"]**64**[/COLOR] GNU/Linux

```
(see the 64) then i think you need amd64.deb

just wanted to thank you for this, I am in fact running what you have posted above. But how can that be, I have a Intel Centrino sticker on the damn notebook... :confused:

---

### Post by toastermm on 2008-06-07
Great guide, I had v-box installed and running fine until the last kernel update.

I also had the v-box driver error, but no sweat, it always  goes away after I quickly reinstall v-box. This time, I now have a new error...  I have no idea how to fix it.

I'm running ubuntu hardy 8.04, on AMDX64 and here is my vbox start up error:

```

VirtualBox - Critical Error
Failed to create the VirtualBox COM object.
The application will now terminate.

details:
Could not load the settings file '/home/toastermm/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'version' has a value, '1.3-linux', that does not match its #FIXED value, '1.2-linux'
Location: '/home/toastermm/.VirtualBox/VirtualBox.xml', line 5, column 83.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}

```

Can't really find a solution online, maybe my search-fu is weak.

---

### Post by meepok88 on 2008-06-07
After the current updating, Virtualbox no longer working. Besides that,  found that even my menu.lst was modified.

---

### Post by mistywindow on 2008-06-07
> **meepok88 said:**
> After the current updating, Virtualbox no longer working. .....
There is hope. :smile:
I'm fully updated and it's still working for me.

---

### Post by Gourgi on 2008-06-08
> **mistywindow said:**
> There is hope. :smile:
I'm fully updated and it's still working for me.

me too
uname -r 
```

2.6.24-19-generic

```

---

### Post by robert2205 on 2008-06-08
i have a little problem in this guide [http://ubuntuforums.org/showthread.php?t=770745&highlight=download+hardy+heron](http://ubuntuforums.org/showthread.php?t=770745&highlight=download+hardy+heron) i have opened the 
Mountrevsubfs.sh but there is nothing in it ?? what shall i do ?? in the guide there stay there should be a text in it and i shall delete that text and put the another text in ... but can i copy the text there is in guide and put it into the document ?? will that still work ?  :confused: please help

---

### Post by Forlong on 2008-06-08
> **robert2205 said:**
> i have a little problem in this guide [http://ubuntuforums.org/showthread.php?t=770745&highlight=download+hardy+heron](http://ubuntuforums.org/showthread.php?t=770745&highlight=download+hardy+heron)
Then why don't you reply to that thread instead of starting a new one?

Also, please use more specific thread titles.
It's not nice to force people to read your thread in order to find out if they can help you.
> **robert2205 said:**
> i have opened the Mountrevsubfs.sh but there is nothing in it ??
Did you make sure to use the exact path of the guide?
You can copy and paste the command to the terminal.

Gedit will open a new document for you, if you run it with a path to a file that doesn't exist yet.

---

### Post by robert2205 on 2008-06-08
is this the 3d box ? :) :)

---

### Post by branque on 2008-06-09
I got problem with VirtualBox and kernel module at Ubuntu 8.04 desktop after a kernel update, but solve it by your advice in a console. Thank you!

x@y:~$ uname -a
Linux x 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux
x@y:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for x: 
 * Stopping VirtualBox kernel module                                                                                                           *  done.
 * Recompiling VirtualBox kernel module                                                                                                        *  done.
 * Starting VirtualBox kernel module                                                                                                           *  done.
x@y:~$

---

### Post by toastermm on 2008-06-09
> **branque said:**
> I got problem with VirtualBox and kernel module at Ubuntu 8.04 desktop after a kernel update, but solve it by your advice in a console. Thank you!

x@y:~$ uname -a
Linux x 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux
x@y:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for x: 
 * Stopping VirtualBox kernel module                                                                                                           *  done.
 * Recompiling VirtualBox kernel module                                                                                                        *  done.
 * Starting VirtualBox kernel module                                                                                                           *  done.
x@y:~$


I got the exact same thing, except I'm running the server version.

But when I try to start VirtualBox, I still have the COM object error as described before:

```
VirtualBox - Critical Error
Failed to create the VirtualBox COM object.
The application will now terminate.

details:
Could not load the settings file '/home/toastermm/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'version' has a value, '1.3-linux', that does not match its #FIXED value, '1.2-linux'
Location: '/home/toastermm/.VirtualBox/VirtualBox.xml', line 5, column 83.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}
```

---

### Post by TFrog on 2008-06-09
First of all, I'd like to thank the starter of this thread.  The tutorial worked great except with version 1.5.6 I couldn't get the usb working properly to recognize my printer even though I loaded the proper drivers into WinXP VM.  I upgraded to the Sun VirtualBox 1.6.2 and it cured that issue and created another one.  It appears VirtualBox 1.6.2 has some issues with the graphics program Cheese.  I no longer get any video preview with Cheese.  BTW.  Version 1.6.2 removes the necessity to download the other dependencies that 1.5.6 needed.  If anyone has a clue as to how to get the preview back in Cheese, I'd love to hear it.  I've already opened a ticket with VirtualBox about this issue.  And before someone asks, I removed and re-installed Cheese to make sure it wasn't an issue with Cheese.

Upon further investigation, the USB support does not work well with usb printing (HP PSC F380).  I've since removed the commericial version of VirtualBox and installed the repo version of VirtualBox as I really have no need for USB support in a virtual machine.

---

### Post by matthekc on 2008-06-09
kevin@kevin-laptop / $ sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
kevin@kevin-laptop / $ sudo /etc/init.d/vboxdrv status
 * VirtualBox kernel module is not loaded.
kevin@kevin-laptop / $ modprobe vboxdrv
FATAL: Module vboxdrv not found.

So do I need to install modprobe.ko again I marked this to install but :confused:

virtualbox-ose module for linux-image-2.6.24-18-386
VirtualBox is a free PC virtualization solution allowing you to run a wide
range of PC operating systems on your Linux system. This includes Windows,
Linux, FreeBSD, DOS, OpenBSD and others.

This package provides the virtualbox-ose module (vboxdrv.ko) for the
2.6.24-18-386 kernel.

You likely do not want to install this package directly, but the
virtualbox-ose-modules-386 meta package instead.

---

### Post by Yuki_Nagato on 2008-06-09
I got USB support working after following your steps, but I had to do a complete restart.  I am still trying to figure out the rest of my junk, so I will be back.

---

### Post by saratchandra on 2008-06-10
> **robert2205 said:**
> is this the 3d box ? :) :)

No, it isn't. Virtualbox is used to run another operating system like windows inside ubuntu

---

### Post by robert2205 on 2008-06-10
i have do every thing there stay in this guide and when i load it then it say ( FATAL : Could not read from the boot Medium! system halted) what thats mean or what do i gonna do ? :(

---

### Post by saratchandra on 2008-06-10
> **robert2205 said:**
> i have do every thing there stay in this guide and when i load it then it say ( FATAL : Could not read from the boot Medium! system halted) what thats mean or what do i gonna do ? :(

Did you install any OS in virtualbox?

---

### Post by Epidemic_HardyBoy on 2008-06-11
Thanks man!

---

### Post by pacice on 2008-06-12
.



Then I log out and in and the USB works without any problems.[/QUOTE]


I followed the tut, and got Virtualbox working great, except the USB devices were not available.
After reading the replys, I followed the device of be4truth and added the following line to to /etc/fstab. Logged out and logged in again.
Now everything works great.

[QUOTE=be4truth;4876794]I add this line to my /etc/fstab file
```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

I also checked the /etc/group file and the plugdev = id 46.

Thanks to all who put this together

Phil

---

### Post by toastermm on 2008-06-12
> **toastermm said:**
> I got the exact same thing, except I'm running the server version.

But when I try to start VirtualBox, I still have the COM object error as described before:

```
VirtualBox - Critical Error
Failed to create the VirtualBox COM object.
The application will now terminate.

details:
Could not load the settings file '/home/toastermm/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'version' has a value, '1.3-linux', that does not match its #FIXED value, '1.2-linux'
Location: '/home/toastermm/.VirtualBox/VirtualBox.xml', line 5, column 83.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}
```

Anyone else have a VirtualBox COM object error?

---

### Post by Digitallad on 2008-06-18
There is a new Virtual box out! V 1.6 It sorted out all my problems but just make sure that you completely remove the previous one!

---

### Post by Cotopaxi on 2008-06-18
First of all, thanks for the tutorial.

After the installation, when I want to start the Windows Guest OS, a terminal windows opens up and says:

"FATAL: No bootable medium found! System halted.

Can anybody help me out with this one?


2nd point: How do I install a Windows-Program now?

Thanks

---

### Post by philinux on 2008-06-18
> **Cotopaxi said:**
> First of all, thanks for the tutorial.

After the installation, when I want to start the Windows Guest OS, a terminal windows opens up and says:

"FATAL: No bootable medium found! System halted.

Can anybody help me out with this one?


2nd point: How do I install a Windows-Program now?

Thanks

You've probably got it still pointing to the cdrom for a boot disk or iso image. Check out the settings for your guest.

---

### Post by Cotopaxi on 2008-06-19
Philinux, thanks for your reply!

What is actually going wrong is that I did not know that you have to PHISICALLY INSTALL Windows! So this is the next step, I will take.

One question: I do not want to install Windows XP with all of its bulk and trash. Does it make sense to build a Windows PE (with Bart PE builder) to have less bulk and rubbish, and install this as the guest operative system?

---

### Post by lovas on 2008-06-19
I've VBox up and running with an XP guest on a hardy host. Following the guide here [http://www.virtualbox.org/wiki/Advanced_Networking_Linux]("http://www.virtualbox.org/wiki/Advanced_Networking_Linux") I've created a connection between the host and the guest only. The problem is that this connection is a kind of one-way: the host can reach the guest via any port, but the guest can only ping the host, but can't see it on 80 or 8080.

Can anyone help?

The steps to create the connection:
```

sudo tunctl -t tap1 -u lovas
sudo ip link set up dev tap1
sudo brctl addbr br0
sudo brctl addif br0 tap1
sudo ip link set up dev br0
sudo ip addr add 172.16.0.1/24 dev br0
sudo ip route add 172.16.0.0/24 dev br0

```
and the guest's IP is 172.16.0.2

---

### Post by qwerty9967 on 2008-06-20
I had the problem where it wouldn't find boot medium.  But then I changed the boot order so that CD/DVD-ROM was before Floppy and it worked.  Hope this helps.

---

### Post by Cherrybark on 2008-06-22
Thanks for the tutorial and updates.

"Mouse Capture problems" and the "missing Virtual Box launcher" can be corrected by remembering the logout / login sequence after modifying the group permissions.  Don't ask how I know...

---

### Post by Nchalada on 2008-06-26
>  Encrypted wrote
I am in fact running what you have posted above. But how can that be, I have a Intel Centrino sticker on the damn notebook... 

the x86_64 / AMD64 is in reference to 64 bit instructions, not the chip that's in the machine.

Intel Core 2 chips are natively 64 bit, not just 32 bit (x86)

Nchy

---

### Post by slickliketeflon on 2008-06-27
I installed virtualbox in 8.04 with kernel 2.6.24.19 using the synaptic package manager. My machine has hardware virtualization support (amd fx62) and 4gb ram. I currently have windows xp pro sp3 and mandriva one 2008 (both 32 bit) running dual instances of prime95 as well as the hypervisor running dual instances. That makes 6 instances of prime95 running at the same time. WOW! And this is all on open source software too. (minus the microsoft of course)

Not that I'm the only person taking advantage of novelty hardware/software usage meant for servers and the like; anybody can utilize this technology. Linux amazes me more and more every day.

---

### Post by darknightx on 2008-06-29
Hi!

This how to is great... works fine but there is a problem. After installing VirtuaBox, my sound failed. I think VirtualBox removed my audio drivers . now I cant set the up. How can I detect or enable sound drivers.i tried all the possible combinations: AlSA,ESD ,Autodetect and pulseaudio

 My sound card is Sound  Blaster 24 bit, and Im using 8.04 

Thanks

---

### Post by philinux on 2008-06-29
With the machine powered off, use settings.

You will find audio on the list click this and change the default to pulse audio.

---

### Post by darknightx on 2008-06-29
Thanks for taking a time to answer... the point is that I already removed the virtual machine, but I still cant set up audio drivers.
Do yo know who to re-detect the audio configuration? The same was as the installer do ? 

Regards

---

### Post by chubbtech on 2008-07-01
great howto!!!  thanx a bunch:guitar:

---

### Post by alillowr on 2008-07-01
I am having issues with connecting to the internet.  I followed the instructions in the first post and the virtual box installs fine, I managed to get xp running but in the device manager the network controller isnt installed properly.  I installed the guest tools and that did not change it, tried updating the driver in the device manager and it would not find a "better driver".  It still shows a conflict.

When powered off under the box settings in network it shows 3 options when using NAT for hardware and all 3 have the same results.  the options are:

Adapter types:

PCnet-FAST III (Am79c973)

PCnet-FAST III (Am79c973)

Intel PRO/1000 MT Desktop (82540EM)

In the xp box under network connections it does not show anything and when I go to setup a new network connection using network setup wizard it states that it cannot detect my network hardware.

How do I go about troubleshooting this issue.

---

### Post by Edigido on 2008-07-01
Okay, so I've got Virtual Box up an running (and I love it!!), but the CD that I've got in the drive won't always read.  I think it maybe a problem with the Laptop, but I'm more sure that it's a problem with the VM.  Any ideas?

---

### Post by bburtin on 2008-07-02
> **darknightx said:**
> After installing VirtuaBox, my sound failed.

Yep, same thing here.  I did a good number of searches and couldn't find any way to get audio working again, short of reinstalling.  If anyone has any suggestions, I'd appreciate hearing them.

---

### Post by Robocoastie on 2008-07-04
how do I get networking (internet) working in wxp guest on virtualbox? I put /dev/net/tut in the vboxusers group and chmod 755 permitted it but it still doesn't work.

*update* Nevermind I found the problem. I had the wrong device selected in the networking section.

---

### Post by rcdeacon on 2008-07-05
Excellent and simple tutorial. Great job, Thanks.

---

### Post by jamesdcarroll on 2008-07-06
Awesome.... thanks! 

This need to be made a 'sticky'

---

### Post by rogerdean on 2008-07-10
Hello folks

Many thanks indeed to everyone who has contributed here. I've got XP on VirtualBox 1.6.2 working pretty well, with USB, network and all.

The last puzzle is folder sharing which, judging from this forum, seems to be working ok for most people. So far I've got the folder selected in the Settings but it doesn't show up in the guest's VirtualBox Shared Folders (as per the screenshots)

Can anyone help me out please?
Cheers
Roger

---

### Post by Shaythong on 2008-07-10
> **rogerdean said:**
> Hello folks

Many thanks indeed to everyone who has contributed here. I've got XP on VirtualBox 1.6.2 working pretty well, with USB, network and all.

The last puzzle is folder sharing which, judging from this forum, seems to be working ok for most people. So far I've got the folder selected in the Settings but it doesn't show up in the guest's VirtualBox Shared Folders (as per the screenshots)

Can anyone help me out please?
Cheers
Roger

Believing that you've installeed Virtual Box Guest Additions 1.5.6 from this tutorial then you should try to reinstall Guest Additions v.1.6.2 (or maybe even 1.5.6).

---

### Post by rogerdean on 2008-07-10
Hi there Shaythong

Yup, I've got guest additions 1.6.2 installed... That should be the appropriate version

---

### Post by finwalia on 2008-07-10
hi,

I am a totally new to Linux !!!!!   I was trying to install VB but encountered problems while trying to install  ---  

with i386 i get the error message as "error dependency is not satisfiable:libqt3-mt"

with amd 64  i get error message as "wrong architecture -amd 64"


please help  !!!!


My hardware details are

anurag@newdesktop:~$ id
uid=1000(anurag) gid=1000(anurag) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(anurag)
anurag@newdesktop:~$ sudo lshw
[sudo] password for anurag: 
newdesktop                
    description: Desktop Computer
    product: M61SME-S2
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=30303141-3444-4631-3433-3432FFFFFFFF
  *-core
       description: Motherboard
       product: M61SME-S2
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
       serial: Fri Aug 24 18:51:45 2007
       slot: &#65533;FDD
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F4 (06/21/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.3.3
          slot: Socket M2
          size: 3GHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
     *-cpu:1
          description: CPU
          product: Athlon
          vendor: AMD
          physical id: 4
          bus info: cpu@1
          version: 15.3.3
          slot: Socket M2
          size: 3GHz
          capacity: 3200MHz
          clock: 200MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1 DISABLED
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-through
     *-memory:0
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 400 MHz (2.5 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM 400 MHz (2.5 ns) [empty]
             physical id: 1
             slot: A1
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1a:4d:f1:43:42
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=10.95.18.11 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi2
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: ATA Disk
             product: ST3250310AS
             vendor: Seagate
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 6RY8ZQCJ
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=57495749
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 9ae94563-4c53-3d47-8375-7284574f4029
                size: 37GiB
                capacity: 37GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2008-07-08 11:45:29 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 195GiB
                capacity: 195GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 48GiB
              *-logicalvolume:1
                   description: W95 FAT16 (LBA) partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 48GiB
              *-logicalvolume:2
                   description: HPFS/NTFS partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 73GiB
              *-logicalvolume:3
                   description: Linux swap / Solaris partition
                   physical id: 8
                   logical name: /dev/sda8
                   capacity: 3812MiB
                   capabilities: nofs
              *-logicalvolume:4
                   description: Linux filesystem partition
                   physical id: 9
                   logical name: /dev/sda9
                   logical name: /
                   logical name: /dev/.static/dev
                   capacity: 20GiB
                   configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S223F
             vendor: TSSTcorp
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: SB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=open
     *-display UNCLAIMED
          description: VGA compatible controller
          product: GeForce 6100 nForce 430
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list
          configuration: latency=0
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
anurag@newdesktop:~$

---

### Post by yetiARC on 2008-07-10
After having read dozens of forum posts, I can hard(l)y believe it, but I'm still too dumb to get USB working on my WinXP guest.
Using a fresh install of Hardy, I closely followed your tutorial together with a few other tips given in the follow up posts. Looks like this got me close to getting USB to work, but I'm not quite there, yet.
Here's my screenshot:

[IMG]http://wundergraben.de/Priv/Bildschirmfoto-2.png[/IMG]

USB devices are recognized in the virtual machine, but they they don't show up in Windows (no USB memory stick in Win Explorer; USB printer not recognized).

Help would be greatly appreciated; this has already cost me a couple of nights ...

Thanks

---

### Post by rogerdean on 2008-07-11
probably you've tried this, but what foxed me for a while was the fact that a flashdisk (for example) has to be unmounted in linux before it'll be picked up in xp. i plugged it in _after_ the xp machine started, and it popped up...

---

### Post by yetiARC on 2008-07-11
> **rogerdean said:**
> probably you've tried this, but what foxed me for a while was the fact that a flashdisk (for example) has to be unmounted in linux before it'll be picked up in xp. i plugged it in _after_ the xp machine started, and it popped up...

thanks; yes I had tried this before.
Went back to double check all the USB settings and found that I had enabled the USB EHCI Controller (which is supposed to provide USB 2.0 support) in the VBox USB settings. After removing the check mark and restarting the virtual machine, USB in WinXP finally came to life. 

Seems like at least for some systems (mine is pretty new), enabling the EHCI controller results in the Windows guest not being able to pick up the USB from VBox.

I'm really glad, everything is working now. Thanks to many helpful people in this forum.

---

### Post by jkirby on 2008-07-12
awesome, thanks.  very clear instructions

---

### Post by jkirby on 2008-07-12
Hmm, I spoke too soon.  VirtualBox installs well but when I go to install the Windows Vista that came with my computer, the windows install fails and says "attempting to load a 64-bit application, however this cpu is not compatible with 64-bit mode".  

I'm running

Ubuntu 8.04
Kernel 2.6.24-19-generic
GNOME 2.22.2
Dual CPU, Intel Core2 Duo T5550

I'm trying to install Windows Vista Home Premium 64-bit/32-bit with SP1 which came with my Gateway laptop

Any thoughts?

Thank you

---

### Post by Jim_in_Germany on 2008-07-13
Great how_to.
Thanks for that!

Just as a point of interest, before my virtualbox will support usb devices I have to able to access /proc/bus/usb/*

One way to do this is:
sudo chown -R root:vboxusers /proc/bus/usb

See here: [URL="https://help.ubuntu.com/community/VirtualBox"]https://help.ubuntu.com/community/VirtualBox

[/URL]

---

### Post by kiwidipstick on 2008-07-13
Hi, I followed yr howto and I get this response:

Could not load the settings file '/home/james/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'version' has a value, '1.3-linux', that does not match its #FIXED value, '1.2-linux'
Location: '/home/james/.VirtualBox/VirtualBox.xml', line 3, column 83.
Any suggestions please. Kind Regards, James.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}

---

### Post by Ryadt on 2008-07-15
Great How-to..
Works perfectly.
thx.:biggrin:

---

### Post by rogerdean on 2008-07-16
> **jkirby said:**
> Hmm, I spoke too soon.  VirtualBox installs well but when I go to install the Windows Vista that came with my computer, the windows install fails and says "attempting to load a 64-bit application, however this cpu is not compatible with 64-bit mode".  

I'm running

Ubuntu 8.04
Kernel 2.6.24-19-generic
GNOME 2.22.2
Dual CPU, Intel Core2 Duo T5550

I'm trying to install Windows Vista Home Premium 64-bit/32-bit with SP1 which came with my Gateway laptop

Any thoughts?

Thank you


Are you running Ubuntu 32bit or 64? If it's the 32bit Ubuntu then maybe VirtualBox can't access the CPU in 64bit mode.

Have no idea in all honesty, but that just occurred to me :)

---

### Post by crazy ivan on 2008-07-18
Hey RogerDean, still having **trouble with "Shared Folders"?** Try a reinstall of "Guest Additions", reboot the vm and then "cmd > net use ...". Seems to be a bug in VB - but this way it worked for me and lots of others...

---

And for anyone installing 1.6.2 at the moment. Do not worry about downloading "Guest Additions" from any mirror. They are available through "vmwindow > Devices > Add "Guest Additions".

---

### Post by rogerdean on 2008-07-19
Ivan, thanks very much indeed! Had to do a bit of digging to remind myself about the windows cmd, and this post from elsewhere helped...


 Re: virtualbox shared folders....?
here's a quick guide
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type "net use t: \\vboxsvr\Crimethinc"(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be net use t: \\vboxsvr\music)

t: will be the virtual drive where your shared folder becomes mounted

---

### Post by genexxa27 on 2008-07-19
Hi there, I got the VirtualBox to work with the usb support working too.My question is, When i have my cam in, it comes up as a unknown usb device with the right codes. When i use it in xp it sees it but when i turn it on i get a black screen. Its a Logitech QuickCam 9000 Pro. Just wondering if someone else has one and if they got it workin and what they did to get it to capture and image. Thank you.

---

### Post by xItachi on 2008-07-20
> **rogerdean said:**
> Ivan, thanks very much indeed! Had to do a bit of digging to remind myself about the windows cmd, and this post from elsewhere helped...


 Re: virtualbox shared folders....?
here's a quick guide
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type "net use t: \\vboxsvr\Crimethinc"(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be net use t: \\vboxsvr\music)

t: will be the virtual drive where your shared folder becomes mounted


I've already setup the shared folder and I did what you said but it says the folder could not be found.  I've also checked in windows explorer and it does not show up.  I'm using Ubuntu Hardy as host and Windows XP Professional as guest.  I've also tried restarting the VM.  Any ideas? Thanks!

---

### Post by L.B. on 2008-07-21
I followed tutorial and got virtualbox installed on Hardy.I did set up for usb. I can see usb's  in the VM menu and add by name or description,but when I start xp the usb's are grey in drop box. I found that someone said to add line to etc/fstab, but don't know how to find etc/fstab, or add this line, # USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0      sorry for being the dumb one but I just switched from windows and don't have much clue.plz. help. :confused:

---

### Post by genexxa27 on 2008-07-23
L.B 
I used this:
sudo gedit /etc/fstab
That gets you into the editor so you can add the code line

---

### Post by no_silhouette on 2008-07-23
I followed all the instructions here. But I have one slight problem. I dont know the command to start it in the terminal, and its not anywhere in my dropdown applications menu. Is there something I overlooked?

---

### Post by no_silhouette on 2008-07-23
Never mind, it was a error I made. I now feel stupid for it:lolflag:

---

### Post by no_silhouette on 2008-07-23
When i try to start the Windows partition for the first time, I get this message:

---

### Post by helknight on 2008-07-23
Thank you so much.. I desperately wanted to see a tutorial as good as this.. there was no problem installing Virtual Box on OpenSUSE but it always failed on Ubuntu.. Thanx once again:KS:KS:KS

---

### Post by Mattevt on 2008-07-24
I have Virtualbox working (and thank you very much for this tutorial), however USB seems to be enabled but I can't see my External hard drive or my MP3 player when I plug them in. Any ideas?

---

### Post by mistywindow on 2008-07-24
> **Mattevt said:**
> ... I can't see my External hard drive or my MP3 player when I plug them in. Any ideas? ... 
Have you set them up as shared folders?

---

### Post by Mattevt on 2008-07-24
> **mistywindow said:**
> Have you set them up as shared folders?

I've figured out my usb problem (I love this forum).  I've shared my music folder from Ubuntu, can someone tell me how to access it from XP virtualbox.

---

### Post by mistywindow on 2008-07-24
> **Mattevt said:**
> .... can someone tell me how to access it from XP virtualbox.

Open VirtualBox.
Click on your XP VM but don't launch it.
Click on the Settings icon.
Click on the Shared Folders icon.
Click on the Add a Shared Folders icon on the far right - has a little green + sign on it.
Navigate to the folder you wish to share.

It's worth noting that when you add shared folders, they must be available for the VM to start. If you share a USB drive and it's not plugged in, the VM won't start.

---

### Post by Mattevt on 2008-07-25
> **mistywindow said:**
> Open VirtualBox.
Click on your XP VM but don't launch it.
Click on the Settings icon.
Click on the Shared Folders icon.
Click on the Add a Shared Folders icon on the far right - has a little green + sign on it.
Navigate to the folder you wish to share.

It's worth noting that when you add shared folders, they must be available for the VM to start. If you share a USB drive and it's not plugged in, the VM won't start.

I've done that, I just want to know where to find it in windows.

---

### Post by davidpeace on 2008-07-25
I have a 64 bit machine. Downloaded the 64 bit vbox edition. When I try to set up a virtual machine I get:

"This kernel requires an x86-64 CPU, but only detected an i1586 CPU. Unable to boot - please use a kernel appropriate for your CPU."


I'm running Ubuntu 8.04 desktop and want to use the same as a guest to experiment with without breaking the host os. Any ideas?

---

### Post by ivana787 on 2008-07-29
Thanks so much for this tutorial. It was a breeze and everything is running well! But the problem I have right now is creating a windows vm. It always gets a blue screen (bsod) everytime it will proceed with the installation. My motherboard is MSI K9A2-GM. I have a SATA driver for it but the issue is that the floppy drive, although it is mounted, dont show the content. I tried creating a floppy image of the floppy drive content, and mount it. This one can see the content/drivers but the bsod still appears when it proceed with the installation. I also experimented with the Extended features but it did not work. Hope you could help me with this. 

Thanks a lot.

---

### Post by friendofpugs on 2008-07-29
I get the exact same thing. When windows goes to reboot to finish the installation, all I get is a blue screen too. Though at setup it said that some parameters were not set or something and installation couldn't continue. Sigh...
I need to run Windows/IE to check the cross browser compatibility of my web site designs. Hopefully someone will come along and help this noob out. :)
Is this the famous blue screen of death that I don't deal with in Ubuntu?

/EDIT/ I spoke too soon, I just checked VirtualBox and everything's installing as planned. Thank you, Bill Gate$!

---

### Post by Princey on 2008-07-30
@ Davidpeace: You're running the 32 bit version of Ubuntu that's why.

---

### Post by johnlvs2run on 2008-07-31
1) downloaded virtualbox 1.6.2
[http://www.virtualbox.org/download/1.6.2/virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb](http://www.virtualbox.org/download/1.6.2/virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb)
2) double clicked to install
3) set permissions
4) enabled usb in terminal
5) downloaded virtualbox guest additions image .iso
[http://www.virtualbox.org/download/1.6.2/VBoxGuestAdditions_1.6.2.iso](http://www.virtualbox.org/download/1.6.2/VBoxGuestAdditions_1.6.2.iso)
6) have not done anything with the iso (still learning)

7) typed "virtualbox" in the terminal and got the following response

> The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found

What am I missing?

---

### Post by johnlvs2run on 2008-08-01
places > find
name > virtual
look in folder > file system > 66 files
click > virtualbox > in "/usr/lib/virtualbox

It opened!!!  Now registered.  :)

Any clues why it says "not found" in the terminal?

---

### Post by gusman21 on 2008-08-01
> **ivana787 said:**
> Thanks so much for this tutorial. It was a breeze and everything is running well! But the problem I have right now is creating a windows vm. It always gets a blue screen (bsod) everytime it will proceed with the installation. My motherboard is MSI K9A2-GM. I have a SATA driver for it but the issue is that the floppy drive, although it is mounted, dont show the content. I tried creating a floppy image of the floppy drive content, and mount it. This one can see the content/drivers but the bsod still appears when it proceed with the installation. I also experimented with the Extended features but it did not work. Hope you could help me with this. 

Thanks a lot.

Are you trying to do a winXP install with the "F6" floppy?  If so, you do not need it.  A winXP VM install should not need anything except the CD (or iso) to complete a fresh, vanilla install.

---

### Post by gusman21 on 2008-08-01
> **Mattevt said:**
> I've done that, I just want to know where to find it in windows.

Go to my network places and click "Entire Network".  There will be an item called "VirtualBox Shared Folders".  Look in there. If you do not see entire network, press f5 to refresh the screen.

---

### Post by orrorin on 2008-08-01
> **johnlvs2run said:**
> places > find
name > virtual
look in folder > file system > 66 files
click > virtualbox > in "/usr/lib/virtualbox

It opened!!!  Now registered.  :)

Any clues why it says "not found" in the terminal?

Because I believe the name of the binary is 'VirtualBox' (case-sensitive) :)

---

### Post by johnlvs2run on 2008-08-02
> **orrorin said:**
> Because I believe the name of the binary is 'VirtualBox' (case-sensitive) :)

Thanks.  :)

---

### Post by davidpeace on 2008-08-02
Princey: No, I'm running the amd-64 version as the host. I have gotten virtual box to work with the 32 bit version of Ubuntu, but that doesn't meet my needs, because if I break it, is what I'm doing breaking the 32 bit but stable on 64? Don't know. That's why I want the 64 bit version to run in vbox.

---

### Post by kkfok1 on 2008-08-11
Thank you

---

### Post by sangcXL3 on 2008-08-14
hei,,
im really new in linux.
previusly ive installed vbox and successfully run it by default
with no usb support.

here bit details
ubuntu 8.04
amd64
guest-windows xp
then i faced a prob.
i cant share the folder though ive installed the guest adition in my guest.

i entered the 
net use x:\\vboxsvr\\share

but then,the cmd reply, 

there is no such network (kind of this statemnt)

ive done few things

-ive unninstall the OSE vbox.
-reinstall based on this tutorial(thanks!!!)
-currntly re-installing the wxp.

so..
anyone could sort out?
:(:(

---

### Post by sangcXL3 on 2008-08-14
ive finished reinstall my wxp,yet,the prob is still there..
here i post my screenshot.windows that show what ive shared and the cmd result in windows.

[[IMG]http://thumbnails8.imagebam.com/1118/90d23011172488.gif[/IMG]](http://www.imagebam.com/image/90d23011172488)

---

### Post by sangcXL3 on 2008-08-14
ive figured out it!

ive mistype the comand!

suppose..

net use x: \\vboxsvr\blabla

but...
ive mistyped it with no space between : and \\

tq!

---

### Post by pschalkx on 2008-08-18
Hi Thanks!!!!

It worked the first time.

Rgds,

Philip

---

### Post by CastilleV on 2008-08-23
I get this error:
[img]http://img395.imageshack.us/img395/2151/virtualboxji1.png[/img]

---

### Post by Uchiha_madara on 2008-09-01
thanks a lot, but i need to ask if this package depend on anther 
package's

---

### Post by prabath_fun on 2008-09-08
Hi,
 I am getting following error when I plug my USB Mass storage device

" Failed to attach USB device USBest Tech..... Device [01XX] to Virtual machine XP.
Not permitted to open the USB device, check usbfs options
Result code: 0x80004005
component: console
interface: ............"

I have checked the group "usbfs" and myself got added in it. Still, I am getting this message.

Host: Ubuntu 8.04
Guest OS: Windows XP SP2

Please help me to solve it.
With Thanks,
PrAbAtH

---

### Post by prabath_fun on 2008-09-10
Hi,
   I followed the below steps and got it.
Setup USB:
**Step1:** 
In Terminal 
sudo gedit /etc/init.d/mountdevsubfs.sh
**Step 2: **
Inside - the lines 
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
Changed to: 
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

**Step 3:**
Save and Exit.

**Step 4:**
 Created a group called "usbfs" and "vboxusers" and added myself to it.
**Step 5:**
In terminal:
sudo gedit /etc/fstab
In file, pasted the following lines, and changed the group ID according to the group ID that was shown for the group "usbfs".
# 1001 is the USB group ID
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
**Step 6:**
Save and close file.
**Step 7:**
In terminal
  VBoxManage list usbhost
**Step 8:**
 Used the output of above command to set up the filters for USB devices under VirtualBox.
**Step 9:**
In terminal 
gksudo gedit /etc/udev/rules.d/40-permissions.rules
**Step 10:**
Change the line
# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",                    MODE="0664"
to 

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device", GROUP="vboxusers", MODE="0664"
**Step 11:**
  Reboot

---

### Post by chargersfan420 on 2008-09-10
Hey Everyone,

The tutorial is great, i managed to get my USB flash drives connected to my Virtual-XP.

The webcam on the other hand took a step backward.  It worked fine with Cheese before following these steps, but now it doesnt work at all.  If i use Cheese, i get a TV test pattern with TV-static in the bottom right corner.  Virtual-XP recognizes the webcam, but when i try to use it, it says "Creation of the video preview failed.  Please check the device connection and make sure that the device is not being used by another application or user."

```

$ VBoxManage list usbhost

UUID:               0e674c19-8db1-4ef0-80ef-bdc11649f183
VendorId:           0x5986 (5986)
ProductId:          0x0200 (0200)
Revision:           0.4 (0004)
Product:            Lenovo Easy Camera
Address:            /proc/bus/usb/004/003
Current State:      Available

```

Anyone have any ideas?

---

### Post by Dyffo on 2008-09-16
> **SendDerek said:**
> This guide is intended to help users fully install VirtualBox and all of it's features which don't work out of the box such as USB support.  I also have [**this tutorial**]("http://www.derekhildreth.com/blog/how-to-install-virtualbox-on-ubuntu-804lts-hardy-heron-tutorial/") (and others) on [ **my blog**]("http://derekhildreth.com/blog").  It's designed to be quick and painless, so let's get started:


[SIZE="4"][COLOR="DarkRed"]Download VirtualBox:[/COLOR][/SIZE]
Use the following links to download VirtualBox according to your CPU architecture.  If you don't know what this means, you'd probably just better go with the i386 pacakge.

**i386:**
[http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb](http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_i386.deb)
**AMD64**
[http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb](http://www.virtualbox.org/download/1.5.6/virtualbox_1.5.6-28266_Ubuntu_hardy_amd64.deb)

[SIZE="1"]*Note:  The VirtualBox that you have in the Add/Remove Programs list is different because it is the Open Source Edition.  This is generally more difficult to configure, so use the normal VirtualBox program found in the link above.* [/SIZE]

[SIZE="4"][COLOR="DarkRed"]Install VirtualBox:[/COLOR][/SIZE]
Double-click on the package you just downloaded and you will be prompted to install it.

[COLOR="DarkRed"][SIZE="4"]Setup Permissions:[/SIZE][/COLOR]
This can be done in two different ways.  The graphical way or the command line way.

**Via Command Line:**

[COLOR="Gray"][In Terminal][/COLOR] ```
sudo usermod -G vboxusers -a username
```

**Via Graphical Menus:**

Goto *System -> Administration -> Users and Groups*.

Click on the "*Unlock*" button and then enter in your password.

Click on the "*Manage Groups*" button.

Find the "*vboxusers*" group which is probably at the very bottom of the list, highlight it by clicking again,  and click once more on "*Properties*".

Make sure there's a check mark next to your user's name, and you're finished.

[COLOR="DarkRed"][SIZE="4"]Setup USB:[/SIZE][/COLOR]
USB is disabled by default, so you'll probably want to enable it.  Otherwise you'll get an error when you go into the "Settings" of your virtual machine.  To  correct this, you'll need to edit the *mountdevsubfs.sh* file:

[COLOR="Gray"][In Terminal][/COLOR] ```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

Inside, you'll see a block of code that looks like this:
[INDENT][I]#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb[/I][/INDENT]

Change it to look like this (uncomment out the region by deleting the "#'s"):

[INDENT][I]#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb[/I][/INDENT]

Save the changes, log out, and then log back in again for the changes to take place.

[COLOR="DarkRed"][SIZE="4"]Other:[/SIZE][/COLOR]
The VirtualBox Guest Additions image (.iso) file is located here:
[http://www.virtualbox.org/download/1.5.6/VBoxGuestAdditions_1.5.6.iso](http://www.virtualbox.org/download/1.5.6/VBoxGuestAdditions_1.5.6.iso)

[COLOR="DarkRed"][SIZE="4"]Minor Troubleshooting:[/SIZE][/COLOR]
With these instructions, I was able to get my virtual machine working perfectly in VirtualBox.  If you have any problems, please let me know by commenting below.  I will help to resolve your issue and then place it with the solution in this section of the tutorial.  Thank you.

**Package Dependencies**
If you run across a problem with dependencies (like libxercese27 which is included in the libxalan110 package), you'll have at this point to either install it first or go ahead with the installation and run "sudo apt-get -f install" to correct the problems.
*Thanks Princey*

**Compilation of the kernel module FAILED! Error**
While trying to install VirtualBox you receive an error like this:
```
"Compilation of the kernel module FAILED!

VirtualBox will not start until this problem is fixed. Please consult '/var/log/vbox-install.log' to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute '/etc/init.d/vboxdrv' setup as root."
```

[COLOR="Red"]Run the command "sudo /etc/init.d/vboxdrv setup" and see if that helps.[/COLOR] (not yet confirmed)
Hi Derek - done as you suggest - but still get this error message  - any ideas

 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

---

### Post by ripin1 on 2008-09-17
i did the instructions and when i go to terminal and type virtualbox it says it is not installed. what do i do?

---

### Post by The Tronyx on 2008-09-19
> **ripin1 said:**
> i did the instructions and when i go to terminal and type virtualbox it says it is not installed. what do i do?

I'm getting the same error after following this tutorial and am a bit curious myself.

---

### Post by Paul86fxr on 2008-09-20
I have everything(system) working great except the USB devices, it says 'device unavailable' or status 'unavailable' the usb devices are there but dull and unavailable. any ideas?
running hardy
xVM Virtualbox

---

### Post by Dr.Fritz on 2008-09-21
> **prabath_fun said:**
> 
**Step 9:**
In terminal 
gksudo gedit /etc/udev/rules.d/40-permissions.rules
**Step 10:**
Change the line
# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",                    MODE="0664"
to 

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device", GROUP="vboxusers", MODE="0664"
**Step 11:**
  Reboot
1.there is no such line in my 40-permissions.rules
2.also when i run the command to see my usb devices in terminal all statuses are "unavailable"
3.i have followed all steps i have found in several howtos(and here ofc) but when i am in xp(VM) and go Devices----> USB all my Usb devices are listed but grayed out, thus untickable :(
4. it might be useful to inform u that just by selecting add usb filter in VB USB GUI it succesfully had the information of all my usb devices, so i dint have to add anything out of the terminal output of the Usb-listing command
5. usb devices are Sony ericsson K800i(i want to be able to import my contacts) and a samsung printer
any1 have a clue :confused:

help would be highly appreciated :)

---

### Post by prabath_fun on 2008-09-22
Hi Dr.Fritz,
  If you are using Ubuntu8.04(Hardy), then you have to edit
"/etc/udev/rules.d/40-basic-permissions.rules" file as specified.
   After editing this you can either add USB from add filter Icon in VirtualBox (you can do this, only, when your Virtual Machine is not running) or use "VBoxManage list usbhost" command in terminal to get USB device details.
   I am using my USB Mass storage device without any problem. 
   I have not tried phone memory, yet. One point - To make use of Phone memory (K800), check that your phone is in "File transfer" mode for file transfer. To import contacts in XP-VM, you may need some tool for it. Ex.My Phone Explorer and Phone should be in "Phone Mode".
   I have W810i, I will try and update you.

---

### Post by Dr.Fritz on 2008-09-22
thanks for ur answer, but i think u didnt fully understand what the problem is.. in my "/etc/udev/rules.d/40-basic-permissions.rules" there is no such line.
and in virtualmachines configuration settings i can see all my usb devices but when i start my virtual machine in the menu devices--->Usb devices all my devices are there, but greyed out, untickable.
by the way either in phone or file transfer mode ubuntu can "see" K800, oh and i think the tool is sony ericsson's Pc Suite(or not?)

---

### Post by Dr.Fritz on 2008-09-22
thanks for ur answer, but i think u didnt fully understand what the problem is.. in my "/etc/udev/rules.d/40-basic-permissions.rules" there is no such line.
and in virtualmachine's configuration settings i can see all my usb devices but when i start my virtual machine in the menu devices--->Usb devices all my devices are there, but greyed out, untickable.
by the way either in phone or file transfer mode ubuntu can "see" K800, oh and i think the tool is sony ericsson's Pc Suite(or not?)

---

### Post by howefield on 2008-09-22
Apologies if I don't understand your question, but there are two things I need to do to get USB working in virtuabox, they are

IN terminal type
```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

Uncomment the last 4 lines above to look like this:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

In terminal
```
sudo gedit /etc/fstab
```

Append this to the fstab then save/exit:

## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

Then a reboot.

---

### Post by Dr.Fritz on 2008-09-22
yes, i have done all of those... but silly me i found out that in my groups i had usbfs , but had unticked my name :) sorry for wasting ur time, well looks like problems fixed :guitar:

---

### Post by zoeken on 2008-09-22
Hello!
I have instaled virtualbox2.0_2.0.2-36488_Ubuntu_hardy_amd64.deb, everything seems to be fine, and it works (i did not verify the USB yet) but when i try to install a 64 bit OS the OS setup process says that my CPU is 32 bit (CPU = AMD64 X2 3800+ ) and it can't be installed. How to fix this??




[COLOR="Red"]In the mean wile i find out what's the problem :D = VIRTUALBOX DOES NOT HAVE 64 BIT SUPPORT FOR GUEST OS !!! source:[url]http://forums.virtualbox.org/viewtopic.php?t=3941&postdays=0&postorder=asc&start=0[/COLOR]   -  available for old version, version 2.0.2 that i use, it has 64 bit support if you check the box for Enable VT-x/AMD-V (but you don't want to know how slow became the guest, at least on my computer)

To bad... so as a solution i must keep both VMware(for testing other OS) :( and Virtualbox (for running XP with some stuff i need) :)

---

### Post by mr104bits on 2008-09-26
Many thanks for ubuntu master, i'm newbie in ubuntu...:)

---

### Post by umang26 on 2008-09-26
well, i installed virtual box and it works fine. I'm just not sure what to do when it asks me "How do you want to partition your disk". I clicked on the guided option and it asks for username and pass, after entering which it gives me a warning and says i could loose data and the follwing are the partitions on which are going to be formated.
partition#1 of scsi1 (0,0,0) (sda) as ext3
partition#5 of scsi1 (0,0,0) (sda) as swap
now i also created a 3rd partiton after all this using partition manager for ubuntu.
What do i do if i want to install ubuntu on that partition? If that partition is not of any use then i can delete it. Now is it safe to click next where it lists the two partitions viz.
partition#1 of scsi1 (0,0,0) (sda) as ext3
partition#5 of scsi1 (0,0,0) (sda) as swap
I just can bare to loose any data from my D Drive which is not the one on which Windows is installed.
Please tell me if i can press Next and go further without harming my D Drive.
Thanks

---

### Post by bark50 on 2008-09-28
I have Virtualbox ose installed on my system.  It runs Windows XP and works well, but I think I'd like to give a try at the Sun Virtualbox because of its usb support and seamless mode.  A couple of questions:

1.When I go to synaptic to uninstall Virtualbox ose, should I also uninstall all those Virtualbox ose modules listed?
2.Assuming all goes well and I get the proprietary Virtualbox installed (famous last words), will I also have to reinstall XP in it?  Or does the uninstall of the ose leave XP as a “leftover” that the new Virtualbox will automatically recognize?
3.I'm running Hardy now.  If I upgrade next month to Intrepid, will this new Virtualbox break?

Thanks, folks!

---

### Post by AgentZ86 on 2008-10-01
Deleted my post

---

### Post by 10gallons on 2008-10-02
Just in case this helps someone else. I was having alot of trouble getting my USB devices to work in VirtualBox 2.0.2 on Hardy. I followed lots of threads including this one on how to get them to work.

I rebooted several times while trying to get them to work, but it wasn't until I powered down and back up that the USB devices began to work.

Don't know why, but that's what happened.

---

### Post by fowlsound on 2008-10-02
Forgive the repeat question if it's been asked, but is there a converter from Sun to convert windows partitions, or is it still best to use the vmware converter and run that image in virtualbox?

My google-fu has failed me on this question.

---

### Post by AgentZ86 on 2008-10-03
> **SendDerek said:**
> This guide is intended to help users fully install VirtualBox and all of it's features which don't work out of the box such as USB support.  I also have [**this tutorial**]("http://www.derekhildreth.com/blog/how-to-install-virtualbox-on-ubuntu-804lts-hardy-heron-tutorial/") (and others) on [ **my blog**]("http://derekhildreth.com/blog").  It's designed to be quick and painless, so let's get started:


Regarding your USB instruction from this page link above where noted:

[QUOTE]Setup USB:

USB is disabled by default, so you’ll probably want to enable it.  Otherwise you’ll get an error when you go into the “Settings” of your virtual machine.  To  correct this, you’ll need to edit the mountdevsubfs.sh file:

[In Terminal] sudo gedit /etc/init.d/mountdevsubfs.sh

Inside, you’ll see a block of code that looks like this:

    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount –rbind /dev/bus/usb /proc/bus/usb

Change it to look like this (uncomment out the region by deleting the “#’s”):

    #
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount –rbind /dev/bus/usb /proc/bus/usb

Save the changes, log out, and then log back in again for the changes to take place.

I basically installed the VirtualBox from the Applications/Add/Remove section and then from synaptic I installed the (ose-module-generic) the one that matches my kernel etc.

Anyhow, regarding your USB instruction, should this also work for me since I did not install per your instructions ?

I'm using Ubuntu 8.04 32bit version and all is working well, however I've not tried any USB devices such as webcam etc. to see if that will work ?
Please advise
Thanks

---

### Post by ethos101 on 2008-10-05
> **AgentZ86 said:**
> Anyhow, regarding your USB instruction, should this also work for me since I did not install per your instructions ?

Hi, I'm not the OP but I did follow the tutorial and finally got USB to work after about 9 hours of troubleshooting and hunting around the net.  The one thing I had to do wasn't included in this tutorial was add a line to the end of /etc/fstab by doing:
```
sudo gedit /etc/fstab
```
I added this to the end of the file:
```
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0
```
Then the part I think that caused me the most trouble was that I had to reboot after I added that.  I think you can do like a "mount -a" or something, I didn't try it, instead of rebooting.

Hope this helps.

To the OP:  Should this be added to the tutorial?  I don't know.

---

### Post by Matt_TX on 2008-10-05
Hi,

I'm new to Ubuntu and VirtualBox and I'm having some problems that I hope the good people of this forum can help me with.

I'm running Ubuntu 8.04 (Hardy) and VirtualBox 2.0.2.

I've managed to install VirtualBox without any issues, I have a Windows XP guest running, guest additions are installed and everything appears to be working fine.  I made the changes to /etc/init.d/mountdevsubfs.sh to enable the code that provides USB support.  However, I want to be able to connect my cellphone to to the Windows XP so I can use "ActiveSync" and copy files back and forth.  I've tried everything I can find to get this to work, and no matter which solution I try, I get one of two issues...

Either A) I get the "Not permitted to open the USB device, check usbfs options." or...
B) As soon as I start my Windows VM my keyboard and mouse lock up and I have to reboot my entire system (cold boot - removing power cord).  It's like VirtualBox takes control of them and won't allow me to go back to my desktop.

I also tried making the changes described to /etc/udev/rules.d/40-basic-permissions.rules, including changing the "MODE" value to "0666" from "0664".  I've also tried adding "GROUP="vboxusers" to the line in the file.  It has no effect whatsoever.  Here is a copy paste of it currently looks like (returned to default after changes did not work):

> # USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"


Additionally, I have edited the /etc/fstab file.  This causes my keyboard and mouse to lock as soon as I start my Windows VM. I added the following line:

> 
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0


I tried various options for this line, including changing it to say devmode=666, and creating a separate group called "usbusers" as described in this tutorial:
[http://forum.notebookreview.com/showthread.php?t=242936](http://forum.notebookreview.com/showthread.php?t=242936)

It's been two days now, and I still can't figure this out.  I have been on every forum, read nearly all the posts and nothing seems to work - I always get one of the two outcomes described above.  

In terms of hardware, I have a run-of-the-mill Dell desktop and a wireless Dell keyboard and mouse.

If anyone can help, I would really be grateful.  This is new to me and I am trying as hard as I can to get everything to work.

Thanks in advance for your help...

---

### Post by squidmaster on 2008-10-12
I keep getting this message
> 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

All the drivers ARE installed so I don't know what it's talking about...

---

### Post by Maruca on 2008-10-24
SendDerek you made my day...:)

I finally go virtualbox to run! thank you so much!!!! *dies of exhaustion*

---

### Post by tjwilli on 2008-10-25
Thanks so much for this tutorial. I've been trying to get USB working with the OSE version in the repository until I saw this. Very easy to follow. Once I changed the group id in /etc/fstab to the vboxusers group, everything worked.

One question though: Is it possible to access my USB thumbdrive in linux while virtualbox is still running?

---

### Post by loveandequality on 2008-12-08
this does not work with me please i need help.

i keep getting this even in 2.0

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code:
NS_ERROR_FAILURE (0x00004005)
Component:
Host
Interface:
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}

---

### Post by lyndaj70 on 2008-12-08
This is what I did, but it isn't a perfect solution:

 <alt><f2> then gksu gedit

put in your pw

then open file etc --> init.d --> mountdevsusbfs.sh

go to the lines "# magic to make the usb work" 

uncomment the next 4 lines (don't uncomment the magic line)

restart your pc.

Now, you have to make sure you are a member of vboxusers group.  I think there is another group you are supposed to create but for the life of me I never remember that part, and so I came up with the next part of this.  If anyone knows that last part please post so I can write it down and start doing it right :p.  

Whenever I want to run virtualbox instead of trying to remember that last group I just hit alt f2 and type gksu VirtualBox, or I create a link to it to avoid having to remember the last step (which I forgot to write down).

Hope this helps,
L

---

### Post by prabath_fun on 2008-12-10
for tjwilli,
   Yes. Just by unmounting from virtual box. That is click on the devices -> USB devices and mounted device from tool bar of running virtual machine.
   Simultaneous access is not possible.

for loveandequality,
You have to edit /etc/fstab file as below.

include following line in /etc/fstab
 
none /proc/bus/usb usbfs devgid=xxx,devmode=660 0 0 

Add at the end of the document. 
Attention: xxx as a group, vboxusers.

If vboxusers group is not created, crate it and add it in root.

  I did as above for Virtualbox2.0.2 in Ubuntu8.10 and got worked.

Prabath

---

### Post by rahul_bhise on 2009-01-07
i did exactly as you said but when i type virtual box in terminal it says 
```
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found
```

---

### Post by bpalone on 2009-01-07
Try typing "VirtualBox" without the quote marks.  Remember Linux is case sensitive.  It should also be available from the Applications drop down menu, as System Tools and Sun xVM VirtualBox from the GUI.  If neither of these work, then I would guess you did something wrong in the install and will have to do it again.

---

### Post by rahul_bhise on 2009-01-08
i didnt type it in quote mark and i also reinstalled the virtualbox.deb package but no use
> rahul@uhome:~$ VirtualBox
The program 'VirtualBox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: VirtualBox: command not found

---

### Post by rahul_bhise on 2009-01-08
i think i solved it
first i installed these packages through synaptic
```
dkms (2.0.19-0ubuntu2)
linux-image (2.6.24.22.24)
```
then as said [hear]("http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu-810-intrepid-ibex/") i did
In Synaptic, click Settings > Repositories. Click the “Third-Party Software”tab. Click Add and enter:
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free

Save the VirtualBox GPG key from [here]("http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc"), then import it into Synaptic by clicking Settings > Repositories > Authentication > Import Key File.
Click the Reload button in Synaptic to reload the repositories.
there wa an error message saying
> W: GPG error: http://download.virtualbox.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
but suddinly there was a update avavliable in update manager which updated my virtualbox from (1.5.6-28266_Ubuntu_hardy) to 1.6.6-35336_Ubuntu_hardy
and whin i tiped VirtualBox in run application (alt+F2) the virtual box started.

---

### Post by pstefanini on 2009-02-21
I'm IN.  IT's ALIVE!!!  

Oh... I have to re-register with XP... I didn't think about that!

THANK YOU ALL VERY MUCH.... I'll keep in touch!...

---

### Post by westieman on 2009-03-03
Derek,

I'm migrating a Vista guest from VMware Server to Virtual Box hosted by Hardy.  I installed 2.1.4 & can boot up the guest just fine.  I pointed Virtual Box to the VMWare (Vista guest) files.  There was no need to chown, as my user was already the owner of the files.  The only other thing I did was set the HAL checkbox in Virtual Box so Vista would be happy.

However, Vista cannot connect to the internet (I've tried using NAT and Host Interface) and I'm getting errors saying that Vista cannot install the driver(s) for the various virtual ethernet boards--I've tried both AMDs and both Intel options.  In addition, I am getting error messages saying that Vista is trying to install a device driver for an (unnamed) base system device--but it always fails to install the driver.  I cannot tell what "base system device" is missing a driver.

I also get a message saying that VMware tray has stopped working.  I am not running VMware when I get this message--only Virtual Box.

In addition, when I try to mount the guest additions CD image, it never shows up on the Vista desktop.

Finally, I cannot get the USB port to see my memory stick.

Do you have any suggestions on how I may troubleshoot my installation?

Thanks for your help!

---

### Post by westieman on 2009-03-03
After rebooting Ubuntu I was able to mount the guest additions CD image and install the guest additions and device driver for the AMD virtual ethernet card.  So, the good news is that I now have internet access on the Vista guest.

I am still getting the "VMware tray has stopped working" error message.  Do I need to uninstall VMWare to get rid of this message?

I have a USB filter for my Kingston memory stick in the Virtual Box settings.  However, when I plug in the memory stick, I cannot select it or mount it from the menu--it's greyed out.  Can someone let me know how to solve this one?

Thanks for your help!

---

### Post by Revery on 2009-04-02
Every time I go to try and download the guest additions, I get this from virtualbox's website.


Forbidden

You don't have permission to access /download/1.5.6/VBoxGuestAdditions_1.5.6.iso on this server.

Full URL is this [http://www.virtualbox.org/download/1.5.6/VBoxGuestAdditions_1.5.6.iso]("http://www.virtualbox.org/download/1.5.6/VBoxGuestAdditions_1.5.6.iso")

I can't find anywhere else to get this.  Does anyone know?

---

### Post by iBurger on 2009-04-04
> update 2: I was just plain stupid. Head over to the virtualbox website and downloaded the latest PUEL 2.2, if you want usb support out of the box.

---

### Post by computermacgyver on 2009-05-18
Same problem here. Permission denied.

---

### Post by kd0afk on 2009-05-18
> **Princey said:**
> For those getting the USB error, if you had followed the HowTo as described, you still will get the error message cropping up ***UNTIL*** you reboot. For those who haven't, here's the directions again:

Enter ```
sudo gedit /etc/init.d/mountdevsubfs.sh
``` in the terminal (substitute gedit with either kedit/kate/kwrite if you're using Kubuntu). Scroll down to the following linesremove the # mark from mkdir down to mount so it looks now like this 

The HowTo states to log out and back in, but the changes won't fully work ***UNTIL*** you reboot. So, restart and you'll notice that the error message no longer appears.


On a side note, can anyone tell me why I can't get Internet using NAT on the xp guest in Virtual box? I'm thinking of purging everything and starting afresh.
That block of code is not there.

---

### Post by jsaulters on 2009-07-14
> **Revery said:**
> Every time I go to try and download the guest additions, I get this from virtualbox's website.


Forbidden

You don't have permission to access /download/1.5.6/VBoxGuestAdditions_1.5.6.iso on this server.

Full URL is this [http://www.virtualbox.org/download/1.5.6/VBoxGuestAdditions_1.5.6.iso]("http://www.virtualbox.org/download/1.5.6/VBoxGuestAdditions_1.5.6.iso")

I can't find anywhere else to get this.  Does anyone know?


After much searching, I found the file available for download on 
the Romanian Education Network:

[http://ftp.roedu.net/pub/mirrors/gentoo.org/distfiles/](http://ftp.roedu.net/pub/mirrors/gentoo.org/distfiles/)

I would, however, like to find an .md5sum of the original file from virtualbox.org, to ensure that this one hasn't been tampered with.

Hope this helps.

---

### Post by misswham on 2009-08-10
I already have xp and ubuntu 8.04 installed on my pc.  Is this install gonna be different since I already have the both of them on my pc and will I be able to use ubuntu and sync my blackberry in windows outlook on xp without having to log out and back into xp?  Also i have a lexmark printer that wont work inside linux, will I be able to print with virtual box?

---

### Post by berteh on 2009-08-11
thanks for this tutorial.

> **SendDerek said:**
> 
[COLOR="DarkRed"][SIZE="4"]Setup Permissions:[/SIZE][/COLOR]
(...)
**Via Command Line:**

[COLOR="Gray"][In Terminal][/COLOR] ```
sudo usermod -G vboxusers -a username
```


I rather suggest the following code that does not need to be edited.
```
sudo adduser $LOGNAME vboxusers
```

B.

---

### Post by ozzman2 on 2009-09-17
> **jsaulters said:**
> After much searching, I found the file available for download on 
the Romanian Education Network:

[http://ftp.roedu.net/pub/mirrors/gentoo.org/distfiles/](http://ftp.roedu.net/pub/mirrors/gentoo.org/distfiles/)

I would, however, like to find an .md5sum of the original file from virtualbox.org, to ensure that this one hasn't been tampered with.

Hope this helps.


Thanks for that buddy!  :)

---

### Post by nazmieski on 2009-12-08
Hi guys,

I just installed the new version of Virtual box 3.1..0 on my Hardy heron LTS.  I installed it using Gdebi Package Installer. after finished installed the latest version of virtual box i restart my notebook. Then when i launch the Virtualbox it appears error;

**Failed to create the VirtualBox COM object**.
 **The application will now terminate.**
 **Error in /home/mnra/.VirtualBox/VirtualBox.xml (line 3) -- Cannot handle settings version '1.2-linux'.**
 **/home/vbox/vbox-3.1.0/src/VBox/Main/VirtualBoxImpl.cpp[420] (nsresult VirtualBox::init()).**

can someone help me to solved this problem? im newbie and dont know what to do on fixing this error. 



Peace...

---

### Post by AgentZ86 on 2009-12-11
Did you uninstall the old version of virtual box first ?

You may have to open synaptic package manager find the vbox stuff, synaptic may insist you uninstall other things dependent on vbox too.

uninstall all that stuff, then go to Sun Website and re-install the latest linux version of vbox.

This should do it, and your original windows or other virtual machines should stay intacted.

I hope this helps

---

### Post by hoppings on 2010-03-20
Hi, I still cannot get USB to work.

You said "Inside, you'll see a block of code that looks like this:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb"

but the window that came up was blank.

Nevertheless, I copied and pasted what you said to change it to and saved it.

I logged out and logged in again but the USB still do not work.

Any suggestions?

---

### Post by nderic77 on 2010-05-01
> **hoppings said:**
> Hi, I still cannot get USB to work.

You said "Inside, you'll see a block of code that looks like this:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb"

but the window that came up was blank.

Nevertheless, I copied and pasted what you said to change it to and saved it.

I logged out and logged in again but the USB still do not work.

Any suggestions?

Same here... FWIW, I am now running a Lucid 64 bit host.

USB is critical for me, as I want to be able to sync my Ipod and Blackberry with their windows apps.

---

### Post by PamanGembuL on 2010-09-26
Hi all, how-to open an existing vmware image on virtualbox? Is it posibble if I open vmware image on virtualbox or is it must to convert first?

---

### Post by memilanuk on 2010-09-27
No idea, but you'd probably be better off starting your own thread rather than hijacking this one...

---

