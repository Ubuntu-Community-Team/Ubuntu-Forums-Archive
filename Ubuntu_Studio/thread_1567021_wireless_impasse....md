---
title: "wireless impasse..."
date: 2010-09-03
forum: Ubuntu Studio
---

### Post by Marco.75 on 2010-09-03
Hi! Hope that someone can help me...

I switched from plain Ubuntu-desktop to Ubuntu-Studio, and I like it very much... but there's a problem with my wireless adapter.
I have an usb adapter from ralink (driver is RT73USB) which they say it's really linux friendly. Actually under Ubuntu-desktop the adapter worked flawlessly... I just plugged it in and it was detected... I inserted my WPA key and got an internet connection.

Under Ubuntu-studio the adapter is recognized but I don't get how I can connect to the internet... there are no applets on the upper panel... what can I do?

---

### Post by cchhrriiss121212 on 2010-09-03
Wireless connections and network manager are left out of the OS in  Ubuntu Studio. This is intentional as it interferes with audio  processing, so be careful to close it (it being "nm-applet") if you want to produce music.

Find out how to install network manager from your studio disk [here]("http://ubuntuforums.org/showthread.php?t=1525705"). If you have a wired connection handy you could also just plug in and download it from the repos, which is slightly easier.

---

### Post by Marco.75 on 2010-09-03
thank you, I'll try this solution and post here the results.
Personally I've never had issues with wireless and music production, not under windowz neither under ubuntu-desktop.
I have a working connection with an ethernet cable... you say that it's easier this way... could you point me to the packages I should download?

---

### Post by cchhrriiss121212 on 2010-09-03
Search for network manager in software center, it will install all the necessary dependencies for you.
It's not a major problem, but it can cause an increase of Xruns/glitches when using jack, depending on your hardware.

---

### Post by Marco.75 on 2010-09-03
ok tried the solution above... I installed the packages from the DVD (there's no "software center" in ubuntu-studio) everything installed fine... restarted the system but nothing appears on the upper panel (no applet, nothing!)... 
I looked at the kernel messages when I plug in my wireless usb adapter... they are the same that shows in ubuntu-desktop... they end with:

"ADDRCONF (NETDEV_UP): wlan0: link is not ready"

at this point when I'm in ubuntu-desktop a window pops up, I give my WPA key, and kernel says "link becomes ready"...

I have no clue...

NOTE:

if I type "nm-applet" or "NetworkManager" from the terminal I get a message saying they are both already running!

---

### Post by cchhrriiss121212 on 2010-09-03
The guy in that other thread had the same issue:
			 		   		 		 		> I got the applet running with help from post #10 of this thread:
[http://ubuntuforums.org/showthread.php?t=1074132](http://ubuntuforums.org/showthread.php?t=1074132)

"sudo restart network-manager"

---

### Post by Marco.75 on 2010-09-03
got wireless working! It's quite late here in Italy... tomorrow I'll post the details.
Many thanks in advance to cchhrriiss121212 for pointing me in the right direction.

---

### Post by Marco.75 on 2010-09-04
Here's how I did it:

1- installed from ubuntu-studio dvd the network manager and its applet (all the packages under: /pool/main/n/network-manager  and  /pool/main/n/network-manager-applet)

2 - checked if "notification area" applet was in the panel (it was there) if not you should add it, because the connection manager applet should appear there.

3 - restarted the system, but no applet showing... so I opened the terminal and typed:
"sudo restart network-manager" and the applet appeared. Inserted my usb-wireless adaper, and after being detected, my WPA key and got internet connection... BUT: after a system restart the applet disappears again! :confused:

4 - I found a permanent solution here --> [http://ubuntuforums.org/showthread.php?t=1074132&page=2](http://ubuntuforums.org/showthread.php?t=1074132&page=2)  post number 12 : I compeared **/etc/network/interfaces **file from ubuntu-studio and the one in my ubuntu-desktop live cd and in the latter one there was no mention to eth0, so I commented out everything leaving just the following lines:

auto lo
iface lo inet loopback

and restarted the network service typing in the terminal

sudo service network-manager restart

this worked for me, making the nm-applet permanent on the panel.

Hope this helps. ):P

---

### Post by halfsoul on 2010-09-18
I found this thread very helpful, so I made a Wiki Page with these instructions:

[Ubuntu Studio Network Setup]("http://help.ubuntu.com/community/UbuntuStudioNetworkSetup")

Please check it out and correct as necessary.

Thanks again.

---

