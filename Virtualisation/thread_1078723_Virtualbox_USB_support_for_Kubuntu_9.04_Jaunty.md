---
title: "Virtualbox USB support for Kubuntu 9.04 Jaunty"
date: 2009-02-23
forum: Virtualisation
---

### Post by janthonywj on 2009-02-23
I'm sort of a newb, and I'm trying out Kubuntu Jaunty for now, why not... I'm running Virtualbox OSE, but I want to try and have my blackberry sync with the XP VM, so I'll need USB support. 

Anyone know how to get a version of Virtualbox PEUL (It's PEUL right?) that will work with Jaunty Alpha 4? (OR, some other way of getting USB support.)

---

### Post by bodhi.zazen on 2009-02-23
Virtualilzation is dependent on the kernel, not necessarily the version of Ubuntu you are using.

9.04 is in alpha and I do not expect VMWare / VirtualBox to package anything prior to it's release.

---

### Post by howefield on 2009-02-23
> **janthonywj said:**
> Anyone know how to get a version of Virtualbox PEUL (It's PEUL right?) that will work with Jaunty Alpha 4? (OR, some other way of getting USB support.)

As said above you are not likely to get a PUEL (Personal Use and Evaluation Licence) version for Jaunty till a few days after the full release of Jaunty.

But it is not unknown for the current versions of Virtualbox to work in the pre releases of Ubuntu, search google, you might get a howto..

---

### Post by HotShotDJ on 2009-02-23
> **janthonywj said:**
> Anyone know how to get a version of Virtualbox PEUL (It's PEUL right?) that will work with Jaunty Alpha 4? (OR, some other way of getting USB support.)

> **bodhi.zazen said:**
> Virtualilzation is dependent on the kernel, not necessarily the version of Ubuntu you are using.

9.04 is in alpha and I do not expect VMWare / VirtualBox to package anything prior to it's release.

> **howefield said:**
> But it is not unknown for the current versions of Virtualbox to work in the pre releases of Ubuntu, search google, you might get a howto..Both bodhi.zazen's and howefield's responses are correct. You MIGHT be able to get the PUEL version for Intrepid to work for you.  I normally recommend adding the proper Sun repositories in order to get the PUEL edition.  In your case, I would try something a little different.  It MAY or MAY NOT work.  Remember, Jaunty is still in development, and you cannot expect it to be all that stable (although, some past "Beta" version of Ubuntu have been surprisingly stable -- but don't count on it!)

DISCLAIMER:  This is NOT a recommendation.  My actual recommendation for your situation would be to either replace your Jaunty installation with either Hardy (8.04 LTS) or Intrepid (8.10) and follow the instructions [HERE]("http://ubuntuforums.org/showthread.php?t=1074160") OR to stick with Jaunty's OSE version until after Jaunty is officially released.

WARNING: The following instructions have NOT been tested by me.  They may work for you.  They may fail to work for you.  They may completely FUBAR your system.  VirtualBox may work today, but then self-destruct with the next set of updates to Jaunty.  By following these instructions, you are assuming any and all risks for yourself.

**ACKNOWLEDGEMENT OF DISCLAIMERS & WARNINGS:  By following the below instructions and executing any of the listed commands and/or procedures, you are acknowledging that you have read and understood the above Disclaimer and Warning!**

Before starting, make sure you have installed the package "build-essential"

Now you MUST completely remove the OSE version from your system.  Open your package manager (in Kubuntu, I believe that would be Adept), and then search for and remove all packages related to VirtualBox that are installed.

Next, download the Intrepid package of VirtualBox: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Open your file browser (Dolphin?) and then click on the downloaded file to install (I'm not sure what the KDE equivalent to gdebi is).  If it installs properly, then go ahead and add yourself to the "vboxusers" group and enable USB support as outlined [HERE]("http://ubuntuforums.org/showthread.php?t=1074160")

Reboot your system and see if you can open VirtualBox and your guestOS.  It might work correctly (the PUEL installation process should have built the kernel modules for you).  You might have to manually run the following command in a terminal:```
sudo /etc/init.d/vboxdrv setup
```Also, every time Jaunty gives you a new kenel, you may need to run the above command.

---

### Post by janthonywj on 2009-02-23
> **HotShotDJ said:**
> Both bodhi.zazen's and howefield's responses are correct. You MIGHT be able to get the PUEL version for Intrepid to work for you.  I normally recommend adding the proper Sun repositories in order to get the PUEL edition.  In your case, I would try something a little different.  It MAY or MAY NOT work.  Remember, Jaunty is still in development, and you cannot expect it to be all that stable (although, some past "Beta" version of Ubuntu have been surprisingly stable -- but don't count on it!)


Thank you very much. I was thinking this might work, but didn't want to even try it until someone told me I wasn't an idiot for thinking about it. 

I did it, and I'm running the new Virtualbox just fine for now. I've added the guest additions just fine, but I haven't figured out how to add the user to the "vboxusers" group yet as the instructions were for Gnome and I'm running KDE. I'm sure I can figure this part out though. 

I understand I'm running an Alpha, and I have no expectations of it being stable, hence, development. So far though, other than some processes not responding on start up, everything has been surprisingly stable. Hopefully Virtualbox will continue to work. 

Thanks again to all of you. Another problem solved. I learn everyday.

---

### Post by bodhi.zazen on 2009-02-23
Thank you for letting us know it works.

I usually do the opposite, keep a stable desktop and run the Alpha release in virtualization :lolflag:

---

### Post by toasterboy1 on 2009-02-24
I am also running kubuntu jaunty with the intrepid virtualbox deb install. I have lost the usb ability when running as a normal user ever though they are part of the vboxusers group. However to add yourself go to:

Applications->System->KUser

under groups there should be vboxusers just double click it and move your user to the left side.

---

### Post by janthonywj on 2009-02-24
> **bodhi.zazen said:**
> Thank you for letting us know it works.

I usually do the opposite, keep a stable desktop and run the Alpha release in virtualization :lolflag:

I know, I know. I'm not technically correct. I'd do it that way, but with my modest machine, it wouldn't be worth it to test Jaunty, and then I couldn't be satisfied with having the latest and the greatest OS. 

> **toasterboy1 said:**
> I am also running kubuntu jaunty with the intrepid virtualbox deb install. I have lost the usb ability when running as a normal user ever though they are part of the vboxusers group. However to add yourself go to:

Applications->System->KUser

under groups there should be vboxusers just double click it and move your user to the left side.

Thanks, I set it all up but I haven't had the chance to plug in my Blackberry Storm and see if it works correctly. I'll post when I find out. 

On to the next issue I can better...

---

### Post by infinitezero on 2009-04-06
I installed VirtualBox 2.1.0 deb for Ubuntu 8.10 ("Intrepid Ibex") and it works just fine for me in 9.04 Beta. 

[http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu](http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu)



There are two versions of Virtual Box:
- OSE (Open Source Edition) which is in the repos
- Closed Source Edition, or Standard, or just plain &#8220;Virtual Box&#8221;

OSE does not have USB support. There are a few other features from the closed source version that aren&#8217;t included in OSE, you can see the list here. So, if you want to have USB support in VirtualBox, you need to install closed source edition and make a change to /etc/fstab. Here are the steps:

1. Remove OSE
$ sudo apt-get autoremove virtualbox-ose

2. Add the VirtualBox repo for Intrepid Ibex. Click System > Administration > Software Sources. Click the &#8216;Third Party Software&#8217; tab. Click &#8216;Add&#8217; and enter:
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

Save the VirtualBox GPG key from here, then import it into Synaptic by clicking the &#8216;Authentication&#8217; tab and then &#8216;Import Key File&#8217;.

Click the &#8216;Reload&#8217; button in Synaptic to reload the repositories.

3. Install virtualbox-2.1 by selecting it in Synaptic, or running this command from a terminal:
$ sudo apt-get install virtualbox-2.1

4. Add yourself to the vboxusers group:
$ sudo gpasswd -a YOURUSERNAME vboxusers

5. Find the devgid for &#8216;vboxusers&#8217;:
$ grep vboxusers /etc/group

It will return something like:
vboxusers: x:123:username

Add this line to the bottom of /etc/fstab, replace the devgid number with your devgid:
none /proc/bus/usb usbfs devgid=123,devmode=664 0 0

After you reboot you should now have USB support in VirtualBox.

Last tested on Ubuntu 9.04 Beta.

---

### Post by andrew.46 on 2009-04-08
Hi,

To allow usb access to usb drives / cameras / ext hdds etc when using the OSE version a neat trick is to simply place a symlink to the usb device in your 'shared' folder. Perhaps not much help with 'sync' software but helpful for simple access.

All the best,

Andrew

---

### Post by ubu-for on 2009-04-08
> **janthonywj said:**
> I'm sort of a newb, and I'm trying out Kubuntu Jaunty for now, why not... I'm running Virtualbox OSE, but I want to try and have my blackberry sync with the XP VM, so I'll need USB support.
The OSE version has no USB support but you can try the all new Sun version 2.2.0 for Jaunty! :D

[http://ubuntuforums.org/showthread.php?t=1119796](http://ubuntuforums.org/showthread.php?t=1119796)

---

