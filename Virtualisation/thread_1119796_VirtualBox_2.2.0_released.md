---
title: "VirtualBox 2.2.0 released"
date: 2009-04-08
forum: Virtualisation
---

### Post by ubu-for on 2009-04-08
VirtualBox 2.2.0 is now [available]('http://dlc.sun.com/virtualbox/vboxdownload.html#linux') with many [fixes and some new features]('http://www.virtualbox.org/wiki/Changelog').

---

### Post by linuxuser21 on 2009-04-08
> **ubu-for said:**
> VirtualBox 2.2.0 is now [available]('http://dlc.sun.com/virtualbox/vboxdownload.html#linux') with many [fixes and some new features]('http://www.virtualbox.org/wiki/Changelog').

Thank you.  I'll be updating it in about 2 hours.

---

### Post by alvarf on 2009-04-08
I´m running version 2.1.4 and want to upgrade to 2.2.0, but when I run the packager installer to install 2.2.0 is delivers the following error message: Error: Conflicts with the installed package 'virtualbox-2-1' resulting in not able to install the 2.2.0. package.

---

### Post by Perryg on 2009-04-08
> **alvarf said:**
> I´m running version 2.1.4 and want to upgrade to 2.2.0, but when I run the packager installer to install 2.2.0 is delivers the following error message: Error: Conflicts with the installed package 'virtualbox-2-1' resulting in not able to install the 2.2.0. package.

A couple of things that I found out.  If the guest is in a saved state and not shutdown.  The install gets upset.  Also if there are screen shots saved it bothers it as well.  Try to make sure that the above conditions have been met and if that does not work you can always un-install the 2.1.4 before you install 2.2.

---

### Post by Wharf Rat on 2009-04-08
I just upgraded to VB 2.2 but still have an ongoing problem.
Does anyone know why VB will not release the mouse?
After I press the R Crtl key, sometimes I see a trail on the Ubuntu desktop for a second then VB grabs the mouse.  The only  way out is to shutdown the VB session.

Just like real Windows,  Reboot to solve the problem.

---

### Post by bodhi.zazen on 2009-04-09
> **Wharf Rat said:**
> I just upgraded to VB 2.2 but still have an ongoing problem.
Does anyone know why VB will not release the mouse?
After I press the R Crtl key, sometimes I see a trail on the Ubuntu desktop for a second then VB grabs the mouse.  The only  way out is to shutdown the VB session.

Just like real Windows,  Reboot to solve the problem.

Try installing the Virtual Box additions, gives better mouse integration. I do not run guests without it ;)

---

### Post by UranUtan on 2009-04-09
> **alvarf said:**
> I´m running version 2.1.4 and want to upgrade to 2.2.0, but when I run the packager installer to install 2.2.0 is delivers the following error message: Error: Conflicts with the installed package 'virtualbox-2-1' resulting in not able to install the 2.2.0. package.

A member of VirtualBox.org forum offered the solution [http://forums.virtualbox.org/viewtopic.php?f=1&t=16197&start=30](http://forums.virtualbox.org/viewtopic.php?f=1&t=16197&start=30)

> sudo apt-get remove virtualbox-2.1
sudo apt-get install virtualbox-2.2

on my Ubuntu 64bit system and this worked fine for me.


---

### Post by alvarf on 2009-04-09
> **UranUtan said:**
> A member of VirtualBox.org forum offered the solution [http://forums.virtualbox.org/viewtopic.php?f=1&t=16197&start=30](http://forums.virtualbox.org/viewtopic.php?f=1&t=16197&start=30)

I got it installed :-). I removed the Virtualbox package using the Synaptic Package Manager and installed the new version on my Ubuntu 8.10 system. After booting the xVM guest (Windows XP) I installed the Virtualbox guest additions and everything is up and running, except I still have to manually active the USB device within my guest system to have my mouse being activated. Within the Vista guest host this is not needed and the mouse is automatically activated on the host as in the guest host.

PS. I saw the message on the Virtualbox.org forum after supplying the above solution. Both ways do resolve the problem :-).

---

### Post by iGama on 2009-04-09
One of the features I most wanted on VirtuaBox just got included in this release! 

The possibility for Host-Only Network, has vmware has :D

I use this mode allot, and had to create a local virtual network manually and associate it in virtualbox. Now I don't need to do this any more :D

Its getting better and better.

---

### Post by johnaaronrose on 2009-04-10
I'm using Intrepid with VirtualBox 2.2. I've created a vm with Network setting of Bridged Network using wlan0 (my standard device for communicating with router as I don't used wired networking). However when trying to install Debian, there is no repo communication (hangs on apt config) though it does get the time. Any ideas?

---

### Post by johnaaronrose on 2009-04-10
VirtualBox 2.2 works fine for NAT network. But either Bridged Networking doesn't work or Bridged Networking only works for Wired connection to router. My guess is the latter.  I'll check it out and post the result.

---

### Post by bodhi.zazen on 2009-04-10
Argh ...

VBox still does not allow a 64 bit guest on my 64 bit processors. Guess I shall stay with KVM or VMWare.

---

### Post by afrodeity on 2009-04-11
I was running an XP VM with 2.1 with no problems. Then I had a crash after I accidently wrote over my MBR (another story) and am trying to set up the VM again. I downloaded 2.2, created the new VM and there are a lot of problems.

1. DVD Drives not opening inside VM

2. Shared folder not coming up inside VM

3. Networking not coming up (this is a biggy, because I noticed how quickly I got the Internet running the first time)

Now I am trying to downgrade to 2.1 but getting this error:Could not load the settings file '/home/afrodeity/.VirtualBox/VirtualBox.xml'.
Cannot convert settings from version '1.7-linux'.
The source version is not supported.


Result Code: 
VBOX_E_XML_ERROR (0x80BB000A)
Component: 
VirtualBox
Interface: 
IVirtualBox {339abca2-f47a-4302-87f5-7bc324e6bbde}


How do I delete the settings file? Can't see it in my terminal.

---

### Post by bodhi.zazen on 2009-04-11
First, remove 2.2.0 completely.

Then 

```
rm -rf ~/.Virtualbox
```

Take care, that command will delete your data and all your VM (if you store them in the default location).

If that is the case, 

```
rm -rf ~/.Virtualbox/VirtualBox.xml
```

---

### Post by gmaniac on 2009-04-11
> **bodhi.zazen said:**
> Argh ...

VBox still does not allow a 64 bit guest on my 64 bit processors. Guess I shall stay with KVM or VMWare.

 you propably didn't select the 64bit when creating the vm!

---

### Post by afrodeity on 2009-04-11
Gosh, this one is for the manual - after trying to do this via terminal, and failing, and having reinstalled about seven or eight times, I finally figured out the solution - View > Show hidden files <ctrl> H. I deleted the VirtualBox.xml file and Virtualbox opens, and takes you through a dialogue. My faith is restored.

---

### Post by bodhi.zazen on 2009-04-11
> **gmaniac said:**
> you propably didn't select the 64bit when creating the vm!

:lolflag: something so silly, you are correct, it is now working.

---

### Post by Staesys on 2009-04-12
**UPDATE:** Nevermind, a reboot seems to have fixed it.

I just upgraded to 2.2.0 and now I'm getting the following error when trying to load my XP Pro virtual machine. I upgraded by removing the old version via synaptic and installing the .deb I downloaded from the link it offered to upgrade.

```
Failed to start the virtual machine pauls_xppro.
Failed to load VMMR0.r0 (VERR_NO_MEMORY).
Unknown error creating VM (VERR_NO_MEMORY).

<Details>

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {9511bc54-15ee-4ddf-808e-472aba03809c}
```

---

### Post by bodhi.zazen on 2009-04-12
> **gmaniac said:**
> you propably didn't select the 64bit when creating the vm!

And sad to say , this does not work at all for my other box :(

```
$ uname -m 
**[COLOR=blue]x86_64[/COLOR]**
```And yes, I have the 64 bit version of Virtualbox installed :lolflag:

---

### Post by dustrho on 2009-09-01
> **afrodeity said:**
> I finally figured out the solution - View > Show hidden files <ctrl> H. I deleted the VirtualBox.xml file and Virtualbox opens, and takes you through a dialogue. My faith is restored.

Doing exactly this resolved my VirtualBox issue! Thanks for the tip!

---

### Post by steveneddy on 2009-09-01
I wonder why you don't just add the ppa for 3.0?

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

