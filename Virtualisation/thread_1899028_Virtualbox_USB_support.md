---
title: "Virtualbox USB support?"
date: 2011-12-22
forum: Virtualisation
---

### Post by Rockin-ubu on 2011-12-22
I'm actually not a noob :), (only to this forum) and  i've used ubuntu for 4 years now, but only used virtualbox for about one year. I now have been trying to sync my ipod in windows through virtualbox but was having a probem in getting it to read USB. No i'm not running the open source version from the software center and I got my Deb. from the Oracle website. My problem is when I plug in any USB device, It (of course) reads it in ubuntu but not in virtualbox:confused:. there isnt even any grayed out letters. I have downloaded the extention pack and am running the most current version, 4.8.1

Any help would be appreciated.

there should be screenshots.

---

### Post by Rockin-ubu on 2011-12-22
Actually its more like im trying to JAILBREAK my ipod  :P

---

### Post by cortman on 2011-12-22
You've gone on the VBox main menu to Devices>USB Devices> and selected the iPod, right?

---

### Post by Rockin-ubu on 2011-12-22
Its not on the choice list :(

---

### Post by Learning Linux 2011 on 2011-12-22
I'm not sure if this is the problem you are running into, but VirtualBox "grabs" anything connected via USB from the host operating system.  So if the iPod is connected to the Linux host and then the Windows in the VirtualBox tries to grab it, Linux may not be releasing it to Windows.  Make sure Windows is running before you try to connect the iPod.

Also, I think cortman means "Machine --> Settings... --> USB"
but I think you have already tried that. (Your Virtual Machine needs to be turned off for that to work anyway).
You can use that to filter which USB devices that VirtualBox should use, but that requires more effort.

---

### Post by CharlesA on 2011-12-22
Make sure you have the extension pack installed and that you are a member of the vboxusers group.

---

### Post by spcwingo on 2011-12-23
You can download the extension pack that CharlesA mentioned about here:

[http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack]("http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack")

---

### Post by haqking on 2011-12-23
> **CharlesA said:**
> Make sure you have the extension pack installed and that you are a member of the vboxusers group.

> **spcwingo said:**
> You can download the extension pack that CharlesA mentioned about here:

[http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack]("http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack")

+1 However the OP said in first post he had the extensions pack.

Make sure you are in vboxusers group and restart your machine.


```
sudo usermod -a -G vboxusers username 
```

If you still have issues after that then make a USB filter

---

### Post by spcwingo on 2011-12-23
I will not post while sleep deprived.
I will not post while sleep deprived.
I will not post while sleep deprived.

:lolflag:

---

### Post by CharlesA on 2011-12-23
Whoops. I must have missed that part. Thanks haqking!

vboxusers group is the way to go then.

---

### Post by Rockin-ubu on 2011-12-23
All tested............ Grrrrr......:mad: Any other Ideas??

---

### Post by Learning Linux 2011 on 2011-12-24
You might want to go to Virtual Box's web site forums [https://forums.virtualbox.org/](https://forums.virtualbox.org/)
as this seems like more of a VirtualBox issue. 

Here are a few more things I thought about:

USB is working in Linux, right?  Are you sure the USB port you are using isn't bad or damaged?

Have you installed the VirtualBox Guest Additions into Windows?

I'm just guessing, but could it be a 64-bit vs. 32-bit issue?  

Have you tried the previous version of VirtualBox (4.0.4 I think)?  I'm running 32-bit Ubuntu 11.04 with VirtualBox 4.0.4

How did you install VirtualBox?  Did you download it from the web site, or from within Linux?  If you downloaded it straight from the web site, you may want to try Linux's internal download tool.

You do have iTunes installed and running in Windows?

Which version of Linux are you running?  I'm not sure this is relevant to you, but it says older versions of Linux may access USB differently than newer versions:   [https://www.virtualbox.org/manual/ch03.html#idp11216576](https://www.virtualbox.org/manual/ch03.html#idp11216576)

---

### Post by Rockin-ubu on 2011-12-25
Well.... All tried and no success. :( any hackers know anything?
(I only hack websites). :)

---

### Post by Rockin-ubu on 2011-12-25
And I am currently running 10.10?

---

### Post by haqking on 2011-12-26
> **Rockin-ubu said:**
> And I am currently running 10.10?

Does your filter that you created have the device in it or is it just an empty filter ?

The filter needs to have your device listed.

And so you are in the vboxusers group yes ?

Linux itself can see the device yes ?

and is it USB in general or just this device ?

---

### Post by Learning Linux 2011 on 2012-01-04
I think I may have found the solution to this.  I think the problem lies with the VirtualBox OSE that Ubuntu provides.  Apparently Ubuntu compiles its own version of VirtualBox, which (apparently) doesn't work right. 
 I completely uninstalled VirtualBox OSE 4.0.4 (that I downloaded from Ubuntu using the sudo apt-get command) 
I removed it by using the command-line terminal (sudo apt-get remove virtualbox-ose and follow the directions).  I tried uninstalling it from the Ubuntu Software Center, but that didn't work right for some reason.

Then I downloaded VirtualBox 4.1.8 directly from [www.virtualbox.org]("http://www.virtualbox.org") 
I found the specific version for my system (in this case Natty 11.04) and installed it (the downloaded file is self extracting/installing.  I just put it on my desktop).  That fixed the problem for me.  USB works fine and some other things have cleared up as well.  

I also downloaded the extension pack (which I'm not too familiar with admittedly) and I guess that allows USB 2.0.  I right-clicked the file and chose to open it with VirtualBox (located in /usr/bin/) but I think there are other ways.

---

### Post by jeliocranch on 2012-01-04
I'm a week late to the party, but bump to the comment about adding you as a user to vboxusers.  I was getting so frustrated with USB connectivity, but once I did that, viola.  That being said, I haven't tried an iphone or ipod yet, but my other phone syncs just fine.

---

### Post by haqking on 2012-01-05
> **Learning Linux 2011 said:**
> I think I may have found the solution to this.  I think the problem lies with the VirtualBox OSE that Ubuntu provides.  Apparently Ubuntu compiles its own version of VirtualBox, which (apparently) doesn't work right. 
 I completely uninstalled VirtualBox OSE 4.0.4 (that I downloaded from Ubuntu using the sudo apt-get command) 
I removed it by using the command-line terminal (sudo apt-get remove virtualbox-ose and follow the directions).  I tried uninstalling it from the Ubuntu Software Center, but that didn't work right for some reason.

Then I downloaded VirtualBox 4.1.8 directly from [www.virtualbox.org]("http://www.virtualbox.org") 
I found the specific version for my system (in this case Natty 11.04) and installed it (the downloaded file is self extracting/installing.  I just put it on my desktop).  That fixed the problem for me.  USB works fine and some other things have cleared up as well.  

I also downloaded the extension pack (which I'm not too familiar with admittedly) and I guess that allows USB 2.0.  I right-clicked the file and chose to open it with VirtualBox (located in /usr/bin/) but I think there are other ways.

The first post from the OP states he didnt get it from the software centre.

Cheers

---

### Post by Learning Linux 2011 on 2012-01-05
oops, lol

lost sight of that.  I assume he was/is using the correct version. Every version of Ubuntu has a different version of VirtualBox apparently.


There is something else to try I think:
Start virtualbox from a terminal using the 'sudo virtualbox' command

that seems to open a different virtualbox.

---

### Post by haqking on 2012-01-05
> **Learning Linux 2011 said:**
> 
There is something else to try I think:
Start virtualbox from a terminal using the 'sudo virtualbox' command

that seems to open a different virtualbox.


That means running virtual box as root not a different version.

Then the any machine you create would be owned by root, not ideal.

Besides if it worked as root then it is a permission issue and as said before the user needs to be in the vboxusers group.

Cheers

---

### Post by Learning Linux 2011 on 2012-01-05
I didn't mean a different version of virtualbox, I meant a different instance of virtualbox with root privileges.
I offered it as a troubleshooting tool.

---

### Post by Rockin-ubu on 2012-01-06
Thanks Guys!! Got it figured out I had to do the v-box user-group command that Haqking mentioned

:)

---

### Post by haqking on 2012-01-08
> **Rockin-ubu said:**
> Thanks Guys!! Got it figured out I had to do the v-box user-group command that Haqking mentioned

:)

cool, glad you got it sorted.

peace

---

### Post by hlmyers on 2012-01-08
> **spcwingo said:**
> You can download the extension pack that CharlesA mentioned about here:

[http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack]("http://download.virtualbox.org/virtualbox/4.1.8/Oracle_VM_VirtualBox_Extension_Pack-4.1.8-75467.vbox-extpack")

OK I've downloaded it numerous times, but exactly how does one install it?

I double click the file and it opens the VB manager but doesn't appear to do any with the extension.

BTW I'm running WinXp in the VB within Ubuntu 10.10

Help

Thanks,'

Harry

---

### Post by howefield on 2012-01-08
From the VirtualBox File menu select Preferences, then extensions and click on the add package button on the right hand side of the window.

The rest should be fairly clear.

---

### Post by Learning Linux 2011 on 2012-01-08
> **hlmyers said:**
> OK I've downloaded it numerous times, but exactly how does one install it?

I double click the file and it opens the VB manager but doesn't appear to do any with the extension.

BTW I'm running WinXp in the VB within Ubuntu 10.10

Help

Thanks,'

Harry

I just right-clicked it and chose "open with" and selected VirtualBox

---

### Post by deeperDATA on 2012-01-14
I am experiencing the same issues Rockin was however I have followed all of these steps and I can not get any of my USB devices to recognize.

Host: Ubuntu 11.10 x64
Guest: Windows 7 x64 Home Premium
VirtualBox 4.1.8

Please help! :(

---

### Post by haqking on 2012-01-15
> **deeperDATA said:**
> I am experiencing the same issues Rockin was however I have followed all of these steps and I can not get any of my USB devices to recognize.

Host: Ubuntu 11.10 x64
Guest: Windows 7 x64 Home Premium
VirtualBox 4.1.8

Please help! :(

So you are a member of the vboxusers group ?

and have extensions pack installed ?

and have selected the device from the device menu ? or it is greyed out ?

---

### Post by deeperDATA on 2012-01-15
For whatever reason it works after I added myself to vbox user group but I had done that before. I'm assuming I entered the syntax incorrectly. Well this works for me. Definitely solved. Thank you.

```
sudo usermod -a -G vboxusers username 
```

---

### Post by haqking on 2012-01-15
> **deeperDATA said:**
> For whatever reason it works after I added myself to vbox user group but I had done that before. I'm assuming I entered the syntax incorrectly. Well this works for me. Definitely solved. Thank you.

```
sudo usermod -a -G vboxusers username 
```

well as for the whatever reason, it is simple, the reason is you need to be in the group ;)

if you did it before then i am guessing like you say you did something wrong and you werent in the group.

Glad you got it sorted.

cheers

---

