---
title: "USB port not seen in Virtualbox"
date: 2008-12-10
forum: Virtualisation
---

### Post by yankeeDDL on 2008-12-10
Hello,

I'm fairly new to Linux and Ubuntu.
I have installed Virtualbox on Ubuntu 8.10 and I cannot see the USB ports.
That's a bit of a problem because I have a USB Wi-Fi adapter so the virtual windows machine is not connected to the internet.

I read the "Virtualization mega thread" as well as a number of other USB-related threads.
Some info that perhaps are useful:
- I have downloaded virtualbox (2.0.6) from its website (as opposed to install it through synaptic or some other system)
- I have no idea if it's the PUEL version or not (how do I check)
- there are a few other 'strange" things happening: I have not enabled the floppy (in the config of the virtual machine), however, I can see it in windows
- I have shared a folder (the Ubuntu Desktop) but I cannot see it in the virtual machine

I think that verifying if I am using a PUEL version or not should be my first step, but I don't know how to do that.
Also, perhaps somebody can tell me where/how to get this PUEL version.
Note that if I hadn't read the "Mega-Thread" I would have never guessed that the version that I have installed of Virtualbox does not support USB's virtualization: all menues seem to be there and all the options that I wold expect (not that I'm an expert ...) are there.

Any thought or suggestion is appreciated. Thanks in advance.

---

### Post by Therion on 2008-12-10
Not sure actually, how to tell what version you're using, but if you're NOT using the Personal Use version there will be no USB support no matter what you do, period.  

Look at this tutorial skipping over the download section and going straight to the install section.  Maybe you DO have the Personal Use version and  you just need to kick-start the USB detection:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)


If the above solution fails all the downloads on this page are the Personal Use binaries for Virtual Box:

[http://www.virtualbox.org/wiki/Linux_Download](http://www.virtualbox.org/wiki/Linux_Download)

Select your architecture, and Ubuntu version, from the list of download links and reinstall if need be.  Then refer back to the tutorial and start from scratch.  Do NOT use the Virtual Box download link in the tutorial though, it goes to an older version.

---

### Post by yankeeDDL on 2008-12-10
Hi, thanks for the quick reply.
I looked at the tutorial ... and I realized that I had not enabled USB at the time I installed Windows.
Meaning, I did install Windows with the USB marked as disabled (I did not think about that).
Then I went back and changed the settings AFTER I completed the installation of Windows. Do you think this can be the problem?

I also followed the link to download but I get a "page not found" error.

---

### Post by yankeeDDL on 2008-12-10
Hello Therion,
I went to the Virtualbox website in the download section.
I saw that the first group of binaries are the "PULE" versions. I definitely got the binary form there, so I should have the PULE version.

The only possible reason at this point seems that I did not enable USB before installing windows. 
I find it strange that one can change the setings after installation if they have no effect on the virtual OS though. So I suspect there may be a differen reason ...

---

### Post by jdc.84 on 2008-12-10
Hi Therion,

I have the correct version installed of Virtual box on Ubunto 8.1, the one direct from their website. I had a look at the tutorial you posted; it's nice and easy to follow.

Typing into the terminal:
sudo gedit /etc/init.d/mountdevsubfs.sh

brings up a page of script but i cannot see anywhere:
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb.

I tried copying and pasting it into various places with out the  #'s but it still brings up the error message that the tutorial is talking about. I am not using Gutsy either.

Do you have any ideas?? 

Any help would be much appreciated as spent hours fiddling so far and not got very far.

Thanks, 
John

---

### Post by bodhi.zazen on 2008-12-10
There is an alternate method, it is a minor edit to /etc/fstab and is posted in the virtualization mega thread under USB devices.

---

### Post by davidyu on 2008-12-10
There's a virtualbox user guide available.
Pls reference:[https://help.ubuntu.com/community/VirtualBox#Sharing%20Folders%20Between%20Host%20and%20Guest](https://help.ubuntu.com/community/VirtualBox#Sharing%20Folders%20Between%20Host%20and%20Guest)

---

### Post by binbash on 2008-12-11
[http://ubuntuforums.org/showpost.php?p=4745128&postcount=13](http://ubuntuforums.org/showpost.php?p=4745128&postcount=13)

---

### Post by yankeeDDL on 2008-12-12
Hello, thanks everyone for the help.
I went through all suggestions and they all seem different.
Some are differnet in a concerning way, for example, the link posted by binbash requires me to add this string to /etc/fstab
none /proc/bus/usb usbfs devgid=1000,devmode=664 0 0
while in the megathread it says:
usbfs   /proc/bus/usb   usbfs   auto,devmode=666   0   0

In any case, I followed the indications in the link posted by binbash and the PC stopped rebooting: after the system clock check (OK) the system would halt.
I tried to revert the changes made by booting with the Ubuntu CD: I think I made all the changes back but the PC still won't boot.
I ended up re-installing the partition. I have not tried yet to setup VirtualBox (run out of time): will try today.
I confirm that I'm using (perhaps I should say I was using) the PULE version, NOT The version provided in the add/remove programs in Ubuntu.

---

### Post by yankeeDDL on 2008-12-14
Hello,

just to give you all an update.
I tried all suggestions that I found (that were recommended in this thread or that I found on other threads).

Nothing worked.
I did get one small step closer though.
Now I see the two USB devices in the devices menu but they're grayed out.
I think what's key is having the correct devgid in the line that is added to the /etc/fstab
# usbfs
none    /proc/bus/usb   usbfs   devgid=1001,devmode=664 0       0

If you look around, most post indicate a different devgid.
I did find a post explaining how to find the correct devgid: this post is the most clear and helpful, at least it was for me:
[http://ubuntuos.com/index.php?option=com_content&task=view&id=15&Itemid=1](http://ubuntuos.com/index.php?option=com_content&task=view&id=15&Itemid=1)

Still, it does not work.
I'm giving up cause I found a decent workaround: I have setup shared folders and I can pass data from the usb sticks to those folders (in Ubuntu) and then see them in the Vbox.
A bit cumbersome, but works and for what I need is good enough.

I have to say a couple of things:
1) I am quite impressed with Ubuntu: I had tried Linux before but it just needed too much in-depth knowledge to be workable. Ubuntu is more user-friendly despite the fact that its retaining the core of Linux's mechanism and way of operating.
2) This said ... as far as ease of use goes, it's still a far cry from Windows. Being able to use a USB port in a vritualbox should not require reading pages and pages of forums. All software has troubles, but I can see quite some margins to grow.
To be clear, this is the one single thing that puts Windows ahead. For everything else, there's no comparison: I am officially an Ubuntu supporter :)
3) The community support in Linux is amazing. Despite not being able to find a solution, I have bumped into dozens of people eager to help. I hope that after some practice I'll be able to contribute too. I consider myself quite an advanced Windows user (been using DOS/Windows for the past 20 years): I think I'll be able to become "handy" quickly. Wish me luck ;)

Thank you all again for the help.

[edit]: corrected a few typos.

---

### Post by talofo on 2008-12-14
Right now, I'm also unable to get USB to work and I believe I have also the PUEL version.
I've also read some solutions around.

Eatch time I go to system setting I'm getting this:


Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}


sudo gedit /etc/fstab

I already have added a line to the bottom with this:

none /proc/bus/usb usbfs devgid=1001,devmode=666 0 0


The other solution that I've seen:
sudo gedit /etc/init.d/ mountdevsubfs.sh

I cannot apply since my file is very different and as not any #magic comment or something.



Regards,
MEM

---

### Post by talofo on 2008-12-14
> **yankeeDDL said:**
> 

Still, it does not work.
I'm giving up cause I found a decent workaround: I have setup shared folders and I can pass data from the usb sticks to those folders (in Ubuntu) and then see them in the Vbox.
A bit cumbersome, but works and for what I need is good enough.


yes but, and if later on you want to have a usb something connect, that only has windows drivers? It would be nice to allow usb on windows to,

Don't give up :D

Regards,
MEM

UPDATE:
Well... I've follow the network think. Hope this can be solved by some exp user. :(

---

### Post by yankeeDDL on 2008-12-14
Hello MEM,

thanks for the support :)
Maybe I'll give it another shot.
If you see my last comment you will notice some tips about devgid.
You're using 1001: are you sure it's the right one?
Look for vboxusers  as explained here: [http://ubuntuos.com/index.php?option=com_content&task=view&id=15&Itemid=1](http://ubuntuos.com/index.php?option=com_content&task=view&id=15&Itemid=1)

In my case th egroup id was 125. 
That solved the error:
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

You should see the USB devices showing up in the settings form (click on add filter and see all the devices connected).

Hope this helps you a bit.
Good luck.

---

### Post by smo0th on 2008-12-14
hi

have you installed the vboxadditions?

---

### Post by yankeeDDL on 2008-12-14
Mmmmm. I don't think so.
I installed the "Guest Additions" from the devices menu. That's what allowed me to see teh shared folders.
Is that what you're referring to?

I googled vboxadditions and I found some threads talking about some vboxadditions.run files, however, in virtualbox.org I could not find any download which remotely looked like that.

---

### Post by talofo on 2008-12-14
> **yankeeDDL said:**
> Hello MEM,

thanks for the support :)
Maybe I'll give it another shot.
If you see my last comment you will notice some tips about devgid.
You're using 1001: are you sure it's the right one?
Look for vboxusers  as explained here: [http://ubuntuos.com/index.php?option=com_content&task=view&id=15&Itemid=1](http://ubuntuos.com/index.php?option=com_content&task=view&id=15&Itemid=1)

In my case th egroup id was 125. 
That solved the error:
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

You should see the USB devices showing up in the settings form (click on add filter and see all the devices connected).

Hope this helps you a bit.
Good luck.

Thanks a lot! The error is gone for me to. But I cannot get the USB drive. I mean, I believe I do it right, I enable the usb, no errors, then on device, I choose the USB that is pluged but... well, nothing happens. Anyway. I will give a break for a while. I will learn about seamless mode virtualization and see how can I work and, maybe there, I notice that I don't need usb AT all on m$. :)


Regards,
ME

---

### Post by talofo on 2008-12-15
Ok. It's done.

After we get no USB errors we must;

1) on the virtualbox we go to settings;

2) Then we click usb (both check if we want usb2 support)

Are the usb enable now? Nop. We have to add a filter, so:

3) Plugin your device, then click on: "Add filter from device", and select your options.

4) Close the window by pressing OK and Start your virtualmachine.

5) After the guest machine installs the USB (in this case was XP), you are done.


Hope this helps somehow. Anyway... I really believe that run thinks on a good seameless mode may disable this USB on guess machine need. But... the time will tell.


Regards,
MEM

ps- the link you have gave me, I've not follow the second step. The "mount with permissions step" or something, because... well I've not understand and I've seen some posts referring only the first step, and my ubuntu was more recent that the one on the tutorial so, only step 1. And till now, np.

---

### Post by yankeeDDL on 2008-12-17
Nope ... not working for me.
As I said, I see the USB devices in the Devices -> USB menu of the VBox but they are grayed out. If I click on any of them, I cannot enable them.
And yes, I did go into Settings -> USB and added filters.
I tried both enabling and disabling the filters, I tried enabling only one filter, I tried re-installing the Guest Additions. Nothing. Nada. It just does not work for me.
I am using a relatively old laptop (it's an old Dell Inspiron) so it may just not be possible to get it to work with "standard" drivers.

---

### Post by smo0th on 2009-01-14
> **yankeeDDL said:**
> Mmmmm. I don't think so.
I installed the "Guest Additions" from the devices menu. That's what allowed me to see teh shared folders.
Is that what you're referring to?

I googled vboxadditions and I found some threads talking about some vboxadditions.run files, however, in virtualbox.org I could not find any download which remotely looked like that.

Ok good, so I assume you already mounted the 'vboxadditions' iso which is around 26 MB, well, you go to terminal and type 
```

cd /media/cdrom
sudo ./VBoxLinuxAdditions-x86.run 

```
It installs everything and tells you to restart in order to complete everything, so you restart and once you do so, USB should be working.

Does this work for you?

---

### Post by HotShotDJ on 2009-01-14
The Virtualization Mega-Thread regarding USB support in Virtualbox contains a link to [THIS]("http://ubuntuforums.org/showthread.php?t=1015763") post, which, if followed to the letter, USB support will work for you.  The the recommendation to edit /etc/init.d/mountdevsubfs.sh is obsolete.  Do not do it unless you are running an old version of Ubuntu.

Regarding Guest Additions, you do not need to download anything or run anything from a terminal.  Simply start your Virtual Machine.  In the toolbar above the OS window, click on Devices and then choose "Install Guest Additions.  If you are in full screen mode, press Right-Ctrl+F to return to windowed mode so that you can see the tool bar.

---

