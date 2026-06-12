---
title: "Network Manager"
date: 2007-08-20
forum: System76 Support
---

### Post by palintheus on 2007-08-20
How would I switch to a LAN connection with restarting my laptop? If I have been using WiFi and go plug in the ethernet cable, the network manager never refreshes to let me use the wired connection.

edit: this is on a daru2, I have also tried the restore/update buttons on the Sys76 driver.

---

### Post by beuno on 2007-08-20
Network Manager does this automatically for me, and you can always click on the applet and select the wired/wireless network.

Are you running Feisty with Gnome?

---

### Post by palintheus on 2007-08-20
I am running Feisty with Gnome. When I plug the cable in the option for the wired network stays greyed out, and I am unable to select it.

---

### Post by ackey on 2007-08-20
I also was unable to connect to a wired network after using wireless.

---

### Post by saxamo on 2007-08-20
I can confirm this. I can't even utilize an Ethernet connection unless I boot the laptop with it plugged in.

---

### Post by thomasaaron on 2007-08-20
If I've already got a wireless connection, I can plug in an ethernet cable and connect to it no problem. I do have to click the network manager icon twice, though.

Sounds like a network manager bug. I'll try to do some testing on it this week to see if I can duplicate the problems you're seeing.

---

### Post by palintheus on 2007-08-20
I left it plugged in for a good 20 minutes and checked every few minutes to see if I could switch with no luck

---

### Post by thomasaaron on 2007-08-21
OK, I just booted up without an ethernet cable plugged in. Then plugged it in, restarted network manager, and voila! No problem.

Give this a try:
Go to a command line after plugging in the cable and enter:

sudo /etc/dbus-1/event.d/25NetworkManager restart

If that works, you can simplify the process by creating a custom launcher on your upper panel. Use this command for it...

gksu sudo /etc/dbus-1/event.d/25NetworkManager restart

Then all you should have to do is click the launcher to get your wired connection up and running.

---

### Post by palintheus on 2007-08-21
hmmm, no dice. 

I know the ethernet works. I have used it, had to plug it in prior to boot though.

Edit: I did reboot with the cable plugged in and if I did that I could switch back and forth with no issue. And, if I unplugged the cable, network manager would grey out the option, and it would be avail once I plugged it back in, but only when the cable is plugged in on boot.

---

### Post by poetbeware on 2007-08-21
I can confirm this on my Darter3. If I boot with eth0 plugged in, then I can switch from wireless to wired with wild abandon. If I boot without eth0 plugged in, then no amount of command line stuff will make the wired connection work. I have to reboot.

The "sudo /etc/dbus-1/event.d/25NetworkManager restart" command didn't work, ifconfig seems to have no effect these days?

---

### Post by thomasaaron on 2007-08-22
OK. I just confirmed this one on the shop darter (daru2). If you boot up without the ethernet connected, it doesn't seem to be able to acquire it.

Could someone file a bug report on this one.

Also, any new Pangolins out there with the same problem?

---

### Post by palintheus on 2007-08-22
Done:

[https://bugs.launchpad.net/system76/+bug/134093](https://bugs.launchpad.net/system76/+bug/134093)

---

### Post by octathlon on 2007-08-22
> **thomasaaron said:**
> 
Also, any new Pangolins out there with the same problem?

I tested this with mixed results.  After booting up without a cable plugged in, I connected to my wireless.  Then I plugged in the cable and NM immediately switched to the wired connection.  I made sure that was working then unplugged the cable.  

NM then tried to reconnect to the wireless connection but never succeeded, eventually timing out.  I tried clicking on the network name to restart the connection, plugging/unplugging the cable again, disabling/reenabling wireless, but it could never reconnect until I logged out and back in, then it immediately connected.

---

### Post by thomasaaron on 2007-08-23
OK, I just tested this on a panv3 (the new Pangolin) and it does not experience this problem. So it seems exclusive to the DarU2 (the new Darters).

I'm going to focus on tracking and fixing it through the bug report.

Also, there is another post addressing some networking problems with Ocathalon's panv3. I don't think those issues are related to this one.

---

### Post by ackey on 2007-08-23
I don't know if this is a related problem:

I'm trying to set up a wireless access point, but when my laptop connects to it isn't able to connect to the network.  I've been assuming that the problem is me, my network, or the access point.  But if the laptop isn't able to connect to the network when plugged into the wall, should I assume it won't connect when connecting to the access point plugged into the wall?  

Is this related?  Should I not bother fighting with it until the ethernet issue is sorted out?

---

### Post by palintheus on 2007-08-23
Do you boot up with the ethernet cable plugged in? If so, sounds like its a seperate issue, if you plug it in after boot, it would be related to this. 

As far as the WiFi, are you setting it up with any security, such as, MAC filtering, WEP, WPA, WPA2?

---

### Post by ackey on 2007-08-23
I haven't actually tried booting with the ethernet cable plugged in (too few cables, too many computers..) and I am using WEP with the access point.  

I consider it highly likely that it is still my fault, but I wanted to check to see if it is obvious to others that the problems are associated.  I had assumed all of my networking problems were my fault, so it is slightly reassuring to hear that network manager is a bit buggy.

---

### Post by palintheus on 2007-08-23
I have never tried WEP, but it works with my WPA network.

---

### Post by poetbeware on 2007-08-24
Hi, I've used my new Darter with both WEP and WPA and WPA2 networks without a hitch. In fact this little thing has connected to about a dozen or so wifi networks without a single problem. So I don't think your access point problem is related to the ethernet thing.

-Paul

---

### Post by gb5757870 on 2007-08-24
I'm pretty much having the same problem. All was fine up until about 10 days ago then suddenly the wired connection won't play ball. Have tried heaps of commands to get it working (from the forums) and it's driving me nuts. I have to use a wireless USB adapter to connect.

This is after many reboots. It's at the stage now where the "wired" option no longer even appears under network manager. I should point out that I dual-boot with windows and the wired connection has no problems

---

### Post by thomasaaron on 2007-08-27
Is this problem occuring only after suspending/hibernating or is this the case after a fresh boot?

Also, more often than not, when the wired connection does not appear, it is because networking configurations have been set via System > Administration > Networking. Unless you just have some very special configuration needs, I'd avoid configuring in this way. Instead, it is better to use the little icon in the upper right only (Network Manager). The other way tends to hose the interfaces file.

To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to 
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little 
computer monitor).

---

### Post by gb5757870 on 2007-09-03
Much thanks for your suggestions.

To answer your question, this occurs on a fresh boot.

I followed your suggestions and have certainly made some progress! At least now the "Wired Network" appears as an option under Network Manager. But when I select the Wired Network it makes a connection but does not give me an IP address. Which makes me wonder if somehow my router is not the cause of these problems. The problem with this theory is that the following do work:
1. XP that I dual-boot with on the same computer
2. My laptop that is running the same version of Ubuntu picks up an IP address.

So maybe for some reason the router has an issue with my MAC address on Ubuntu??? I'm going to try and put another NIC in and see if that makes a difference. Totally weird.

Any other suggestions?

*** UPDATE ***

Maybe it's because I was standing on one foot or facing east, but it's working now. I opened my PC to install a TV card and now after booting up, it's fine. I'm bewildered.

Thanks for the help!

GB

---

### Post by steveneddy on 2007-09-04
> **thomasaaron said:**
> OK, I just tested this on a panv3 (the new Pangolin) and it does not experience this problem. So it seems exclusive to the DarU2 (the new Darters).

I'm going to focus on tracking and fixing it through the bug report.

Also, there is another post addressing some networking problems with Ocathalon's panv3. I don't think those issues are related to this one.

I have a Serval Performance version 1 and I have the same issue. 

I am at school, without a wireless connection to test, but I believe that at home I can't get it to connect to a wired connection unless it is plugged in before I boot the machine.

EDIT:

I tried that fix about two posts up by thomas. I'll let you know how it works on my Serval.

EDIT #2:

I unplugged the ethernet cable from my laptop after class - then plugged it back in to see it it would automagically connect.

It did. The fix above "repaired" the network manager connection.

Thanks!

EDIT:

After a cold boot, the Ethernet connection still needs to be plugged in before the PC is turned on to connect.

Bummer.

---

