---
title: "Windows Mobile on VMWare"
date: 2007-12-04
forum: Virtualisation
---

### Post by WeeManDan on 2007-12-04
Hi all,

I've installed VMware and am trying to use the virtual machine to control a Smartphone running Windows Mobile 6, Ubuntu doesn't seem to pick up the device at all, first off, are there any programs designed for WM to Ubunutu syncing and mounting? Also is there a way to force VMware to use the hardware USB rather than have to go VM-->Removable Devices --> USB Devices as at the moment, the phone isn't listed.

Thanks,

Dan

---

### Post by danielcreech on 2007-12-07
I'm trying to do the same, except under VirtualBox. When I first attach the phone (before starting VirtualBox), it appears that Ubuntu (Gutsy) identifies  it and loads a generic RNDIS driver for it. Then I start VB, Windows detects it as a "windows mobile device" but says that "The device cannot start. (Code 10)". At that point, Linux no longer seems to detect the device either AND when I physically disconnect the phone and plug it right into a WinXP-only machine with ActiveSync installed (on which the phone normally works fine) that computer says that the device has malfunctioned and Windows cannot detect it.

I have to physically power off and back on the phone to make it work under Windows again at all. So it appears VirtualBox is corrupting some setting within the phone itself. This is a T-Mobile Dash running WM6.

What in the world is going on ?

Thanks,
Daniel

---

### Post by thwint on 2008-04-22
Has anyone found a solution for this now?
I have exactly the same problem on Ubuntu Hardy with VMware Server 2.0.

When I plug in my mobile it is recognized as a new wired network device. Network Manager disconnects my existing wlan connection and connect to this device.

In VMware I can see the device as a "High Generic RNDIS" for which I can toggle the connected checkbox. When connected in the Windows guest I can see a "Windows Mobile-based Device #X" which doesn't work (This device cannot start. (Code 10)).

Is there a way to:
1. stop Ubuntu from disconneting my WLan connection and connecting to the Mobile "wired Network"
2. use the windows mobile device in my windows guest system

---

### Post by grubby on 2008-04-28
Ditto here with WM6 and Hardy using the VMWare player. Strangely, it did work once, but now nothing.

---

### Post by lazlong-wa on 2008-06-09
Just registered to give the answer:

Actually got it from:
[http://www.uluga.ubuntuforums.org/showthread.php?t=648608&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=648608&page=2)

My setup:
Ubuntu 8.04 AMD64 Host
VMware server 2 beta
Windows Mobile 6
Windows XP guest

On the WM5 (or WM6) device:
- go to settings/connections
- click 'usb to pc'
- turn off 'enable advanced network functionality'

Worked straightaway.

Not sure why the networking part did not work. I was about to add another interface if the above didn't work.

---

### Post by CyberAngel on 2008-08-08
> **grubby said:**
> Ditto here with WM6 and Hardy using the VMWare player. Strangely, it did work once, but now nothing.

Exactly the same for me :(

---

### Post by CyberAngel on 2008-08-08
> **lazlong-wa said:**
> Just registered to give the answer:

Actually got it from:
[http://www.uluga.ubuntuforums.org/showthread.php?t=648608&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=648608&page=2)

My setup:
Ubuntu 8.04 AMD64 Host
VMware server 2 beta
Windows Mobile 6
Windows XP guest

On the WM5 (or WM6) device:
- go to settings/connections
- click 'usb to pc'
- turn off 'enable advanced network functionality'

Worked straightaway.

Not sure why the networking part did not work. I was about to add another interface if the above didn't work.

I tried this solution but then active sync in the VM is not recognizing the device...

---

### Post by KatBuntu on 2008-08-08
There's a way to fully sinchronyze windows-mobile devices without creating a virtual machine, maybe this post at servitux, can be helpful.
[http://www.servitux.org/view.php/page/ipaqusb]("http://www.servitux.org/view.php/page/ipaqusb")
The HOW-TO is made for Debian :lolflag:

---

### Post by rabid9797 on 2008-10-05
> **danielcreech said:**
> I'm trying to do the same, except under VirtualBox. When I first attach the phone (before starting VirtualBox), it appears that Ubuntu (Gutsy) identifies  it and loads a generic RNDIS driver for it. Then I start VB, Windows detects it as a "windows mobile device" but says that "The device cannot start. (Code 10)". At that point, Linux no longer seems to detect the device either AND when I physically disconnect the phone and plug it right into a WinXP-only machine with ActiveSync installed (on which the phone normally works fine) that computer says that the device has malfunctioned and Windows cannot detect it.

I have to physically power off and back on the phone to make it work under Windows again at all. So it appears VirtualBox is corrupting some setting within the phone itself. This is a T-Mobile Dash running WM6.

What in the world is going on ?

Thanks,
Daniel

i have this exact same problem. 
i have a blackjack II so there is no usb-to-pc options(so i can't disable advanced networking functionality)
i have tried all of the methods for getting usb working(although i have no problem with it). my phone is recognized by ubuntu, and by windows(with the same results as the quoted post)

is there any more information available on this?

---

### Post by rabid9797 on 2008-11-10
Hey everyone. I found some more information on the problem, and a possible work-around.

[http://www.smartphonemag.com/cms/forum/topic/26436](http://www.smartphonemag.com/cms/forum/topic/26436)

> 


Been looking for the answer for weeks & weeks, like many, many thousands of others. Here's what I've found.

The root of the problem is that ActiveSync 4.x switched to an RNDIS TCP/IP connection method, rather than the old, reliable serial USB. Hence, if you're using firewalls or A/V solutions that in any way fiddle with your TCP/IP interface, ActiveSync would fail. Fail here means "no partnership," "could not connect," etc. etc. etc.

There is a method to change BACK to the old USB serial connection. Some phones/PDAs have the USB-to-PC connection icon & you can turn off "advanced network options" (approximate wording) in there. My HTC PPC6700 did NOT have this icon, so I was DOA.

I went to HTC's website, specified my phone & carrier & downloaded "ActiveSyncMode.sa.CAB." I downloaded it using a WiFi connection, direct to my phone. You could also save it to your SD card & launch it from there. It DID NOT LOAD on the first try, although the file launched. I did a soft reset and tried again & it worked. After install, there was an "ActiveSync Mode" icon under Settings. I switched the connection type to USB Serial and ActiveSync is currently humming away, synching up my media files.

So, find the "ActiveSyncMode.sa.CAB" download at your carrier's or your manufacturer's website. Contact their Tech Support if needed. Get it onto your phone via web or storage card. Load it up (soft reset if necessary) and live happily every after.

I found the ActiveSync Mode info on a Windows Mobile developer website -- not easy to find. So, if you have accounts in other forums where this topic is discussed, please repost this entry there. I intend to repost this in a few places, but wider distribution is better. There are lots of people trying hard resets, disabling firewall SW, etc., without getting anywhere


if you can find a place to download the cab, it might be possible to fix this from the phone itself

---

### Post by veloce on 2008-11-11
The issue is actually with network manager not with the virtual machine software. 

I have had this issue with a number of usb devices.  If Ubuntu recognises the device and sets it up, then it is no longer accessible to the vm as a usb device.

I never found an answer to the network manager issue - but I suggest that the question should be asked in a network manager part of the forum. Specifically: 

Is there any way to stop network manager from automatically taking control of specific hardware?

---

### Post by CyberAngel on 2008-11-11
> **veloce said:**
> The issue is actually with network manager not with the virtual machine software. 

I have had this issue with a number of usb devices.  If Ubuntu recognises the device and sets it up, then it is no longer accessible to the vm as a usb device.

I never found an answer to the network manager issue - but I suggest that the question should be asked in a network manager part of the forum. Specifically: 

Is there any way to stop network manager from automatically taking control of specific hardware?

I don`t think that it is a networkmanager issue because I killed networkmanager (because it was changing my default routes every time I was connecting the mobile device) and the problem was still there....

---

### Post by veloce on 2008-11-11
> **CyberAngel said:**
> I don`t think that it is a networkmanager issue because I killed networkmanager (because it was changing my default routes every time I was connecting the mobile device) and the problem was still there....

There must be two issues in this thread then.  This one:

> **thwint said:**
> Has anyone found a solution for this now?
I have exactly the same problem on Ubuntu Hardy with VMware Server 2.0.

When I plug in my mobile it is recognized as a new wired network device. Network Manager disconnects my existing wlan connection and connect to this device.


Is definitely to do with Network Manager.

So does your virtual machine see the usb hardware?

---

### Post by rabid9797 on 2008-11-11
I thought it was the network manager as well, but it's not. In Intrepid my device is automatically recognized, but then when i use the USB filter for virtualbox, virtualbox takes control over it(and it looks disconnected from ubuntu).

I think that if someone can solve the RDIS problem, everything will be fixed.

---

### Post by avessalom on 2008-12-29
Hi, 

it works for me ONLY in ActiveSync low speed mode.

Ubuntu Hardy 2.6.24-22-generic #1 SMP
Vmware Wokstation with VMplayer 2.0.5 build-109488
Windows XP Pro SP2 as guest.

PDA: ASUS A626 Windows Mobile 6

Settings -> connections -> USB settings -> ActiveSync (low speed)

best regards,

Ave

---

### Post by toneman77 on 2009-02-02
I have a slighty different problem.
Is it possible to connect my Windows mobile device on the client machine that connects to the VMWare server? I have installed VMWare server on my server machine and access it with the browser.

Is there another way other than walking to the server and plugging my phone in there?

---

### Post by CyberAngel on 2009-02-02
> **toneman77 said:**
> I have a slighty different problem.
Is it possible to connect my Windows mobile device on the client machine that connects to the VMWare server? I have installed VMWare server on my server machine and access it with the browser.

Is there another way other than walking to the server and plugging my phone in there?

Maybe you need something like this after a quick google search...
[http://www.fabulatech.com/usb-over-network-linux.html](http://www.fabulatech.com/usb-over-network-linux.html)

[http://www.usb-over-network.com/usb-for-remote-desktop-linux.html](http://www.usb-over-network.com/usb-for-remote-desktop-linux.html)
[http://www.usb-over-network.com/usb-for-remote-desktop.html](http://www.usb-over-network.com/usb-for-remote-desktop.html)

This is the first result I found...
Most probably more solutions will exist in the market.

---

### Post by rgl2020 on 2009-04-07
Anyone confirm that the cab file fix for this on the phone?  I just updated from Hardy to Intrepid and now I can't sync at all inside Vbox or VMWare.  On Hardy sometimes it would sync, and sometimes have problems.....it was hit or miss.  Does anyone know if this will be fixed in Intrepid?

---

