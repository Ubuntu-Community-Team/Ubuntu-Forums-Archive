---
title: "New Gazelle and Wireless Troubles"
date: 2008-05-08
forum: System76 Support
---

### Post by Beridel on 2008-05-08
Hey, I just got my new gazelle in the mail today, and I must say I'm quite impressed with everything so far.  My issue right now though is that my wireless is not able to connect to my network at home.

Since my router isn't in the best location in my house, I found that with WPA security enabled it kills the connection distance, so I'm using MAC filtering.  First to describe what happens:

I can left-click the network manager and see my network (as well as a few others from the neighbors).  I'll click my network to attempt to connect and there is just the "swirly" icon that happens for a bit, and it gives up and reverts to the wired connection that is hooked up.

Once that did not work, I did all the easy things you would think of such as restarting the router, trying with/without MAC filtering, trying with/without WPA-PSK security, and it gives me the same thing each time.  I've tried doing a manual configuration and actually typing in the specific details for my network and that did not work as well.  I'm new to Ubuntu and linux so I would probably have more ideas if it were on a windows machine, but I think I've exhausted everything I know how to do on my new laptop.

And one more thing that is nitpicky, the lower right hand corner of the keyboard (where the right arrow is) is curled up slightly.  Nothing that affects actual use of the keyboard, just a little OCD thing I noticed.  Any recommendations on how to tinker with that to bend it back?

Thanks for the help in advance.

Router is a Linksys WRT54GX4 if you're curious.

---

### Post by garyedwardjohnston on 2008-05-08
You arent set up for having 2 connections.  Choose wired OR wireless, not both.

As for you curled keyboard, I'm assuming it is made of soft material.  If this is the case, when the computer is turned off, put something heavy on it.

---

### Post by Beridel on 2008-05-09
I know I'm not set up for two connections.  When I click network manager I see the "wired" option and then about 4 different wireless networks to choose from.  Wired will be selected initially, but then I select my wireless network to attempt to connect to it.  It won't, and it'll fall back on the ethernet LAN connection because that works.

Maybe because I'm unfamiliar with ubuntu, but I wouldn't think having an ethernet connection hooked up would affect my wireless capabilities.

---

### Post by thomasaaron on 2008-05-09
Try disconnecting your ethernet cable and then connecting to wireless. Does that work?

---

### Post by Beridel on 2008-05-09
Nope, I've tried that already as well.

---

### Post by thomasaaron on 2008-05-09
I realize you said you see wireless access points, but just confirm that your wireless switch is toggled to the right. (Yes, I know it is. ;)

Providing you're not too far away from your router, this thread...
[http://ubuntuforums.org/showthread.php?t=776175&highlight=mac+address](http://ubuntuforums.org/showthread.php?t=776175&highlight=mac+address)
...sounds similar to your issue. This person fixed it by disabling/re-enabling networing.

Have a look at that thread, and see if anything on it works for you.

---

### Post by Beridel on 2008-05-09
So I looked through that other thread, and my log looks like the same exact problem as TomL, but I don't know if I'm missing something but I can't really see what he did to fix it...

I looked at the link that you posted that documented the bug where Hardy was having issues with unencrypted networks, so I tried WPA encryption with network manager and then also manually putting in the info (disabling roaming mode).  It looks like it gets farther along, but then browsing in firefox still does not work.  I also tried disabling/enabling networking like you mentioned and that did not change anything.  I'm not sure what else I should try after looking through the posts you've forwarded me to.

Thanks for the help so far, I hope we can solve this.

And yeah, my wireless switch is to the right ;)

---

### Post by thomasaaron on 2008-05-09
Thanks. I hate to ask people about the wireless switch. Occupational hazard. ](*,)

So, that guy fixed it by right clicking on his networking icon in the upper right of his LCD and *disabling* networking and then *re-enabling* networking.

---

### Post by Beridel on 2008-05-09
I've tried that and it doesn't seem to change anything.  Still the same timing out issue.

---

### Post by thomasaaron on 2008-05-09
Please post the output of:
cat /etc/network/interfaces

That daemon.log is interesting. Are you trying to connect to the Internet wirelessly via System > Administration > Networking?

---

### Post by Beridel on 2008-05-09
auto lo
iface lo inet loopback

Thats my /etc/network/interfaces

Woops, forgot to address your other question.  No, everything I've tried so far is through clicking the network manager in the system tray and either just clicking the wireless network or clicking manual configuration, disabling roaming mode for my wireless and then typing in everything manually.

---

### Post by thomasaaron on 2008-05-09
OK.

Your daemon log clearly shows you being asked for the code and entering it.
Then it clearly shows the connection attempt failing on a timeout...

> May  9 11:17:13 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>120s), failing activation. 

The problem really looks like an issue with your router -- it's not accepting the connection. Could be signal strength too, I suppose. Possibly even a blocked mac address.

It doesn't look like a misconfiguration on the part of network manager, otherwise, that would be reflected in the log.

---

### Post by Beridel on 2008-05-09
Well now it shows something slightly different after messing with the manual config, going back to roaming mode, then disabling/re-enabling networking.  It shows the wireless bars instead of the two computer icon for the network manager.  Thing is all the network bars are grey, and when you hover over it says "Wireless network connection to 'Frank' (0%)"

Perhaps it is the router, but we have 4 other computers all with different network cards connecting to the same router.  Perhaps its something with the intel network driver?  I really don't know at this point.  My next troubleshooting step was going to be to bring it over to someone else's house and try it out there, but do you have any other ideas?

Thanks so far for the responses.

Also as a side note, I've now moved up to the office where the router is so its not network strength and I triple checked the MAC address.

---

### Post by thomasaaron on 2008-05-09
I don't think it is the drive. This driver is being used everywhere with every imaginable router.

Your options seem to be:

*Signal Strength (how strong is your signal when you view it by clicking onthe networking icon?)

*Non-Exact configuration of network manager to the router. It literally has to be exact. Please describe your configuration on both the router and network manager.

*A setting in your router that is thwarting your connection. I'd try it out at a friends house, or a free wifi coffee house.

---

### Post by Beridel on 2008-05-10
So I took it over to a friend's house that has a pretty standard wireless setup, and I had the same problem there as I do at home.  So I'm thinking its not my router but something with either hardware or software.

Also I've done a little google researching and it seems other people we're having this same issue with the intel 4965 in hardy alpha/beta but that a lot of them have resolved it.  I've tried a few things to no avail, like trying it with wicd instead of network manager, but no luck so far.  Would trying out a 3945 intel wireless card make a difference?  Don't know what else to try now.

---

### Post by TomLawell on 2008-05-11
This is TomL and I agree your problem sounds the same as mine! The only new wrinkle to my problem is that I can connect to an unsecured neighbor's network. Thomas thought that I needed to use WEP but that did not help. I am still broken but when I need connection I either use the neighbor's or I use cat5!
I am just lying in wait! :>

Thanks.

---

### Post by ctsdownloads on 2008-05-11
> **TomLawell said:**
> This is TomL and I agree your problem sounds the same as mine! The only new wrinkle to my problem is that I can connect to an unsecured neighbor's network. Thomas thought that I needed to use WEP but that did not help. I am still broken but when I need connection I either use the neighbor's or I use cat5!
I am just lying in wait! :>

Thanks.

If it smells like a duck, quacks like a duck - it's a duck. Despite everyone having MAC filtering disabled to the best of their knowledge, I am willing to bet that it is worth heading to a big box store for a little experiment. Before you do, double check that you have the latest router firmware. 

If it is still failing, pick up a new 802.11g (no pre N routers if possible) router and *hold onto the receipt*. Set it up, test it with zero security settings. Success? Then the router(s) in question are not handing off things for some reason. 

*_Even if it works with XP_*, I have seen this happen with Linksys many times with specific Linux distros - no idea why. I know, this makes zero sense, but trust me, you might be shocked at the results.

Basically, "borrow" a router for testing that is new, not used and can potentially save you hours of wasted time.

I have been troubleshooting Linux wireless for years, this is why I always have an alternative for testing. If it fails, take it back for a full refund. This is my best, least time wasted suggestion from troubleshooting similar experiences of MAC address filtering gone wrong.

---

### Post by ctsdownloads on 2008-05-11
If testing with the new router still fails, try this as a last ditch effort:

([Borrowed from here]("http://ubuntuforums.org/showpost.php?p=4559250&postcount=1"))

Which HAL are you rockin' with?

> apt-cache madison hal

You should be gazing at something *like*:

> hal (0.5.11~rc2-1ubuntu2) hardy; urgency=low
* debian/rules: build using --with-deprecated-keys, since we don't want to
break packages that were assuming this worked right up through beta.
LP: #204768.

If not, run those updates.

Yes you do have that version of HAL, but still no love? Try this:

Download and save this to disk: [http://launchpadlibrarian.net/12498252/network-manager_0.6.6-0ubuntu1_i386.deb](http://launchpadlibrarian.net/12498252/network-manager_0.6.6-0ubuntu1_i386.deb) Then double-click it to install. It will likely complain about being older, but I believe will install nonetheless. If you rather, uninstall the existing NM first.

> sudo aptitude remove network-manager

That will take care of the back and front ends for you.

Got it working, great. Now let's prevent Ubuntu from "fixing" your network-manager ever again:

> sudo aptitude hold network-manager

You can also check the NM version with:

> apt-cache madison network-manager

---

### Post by Beridel on 2008-05-11
Thanks for the response cts.

I don't think I'll be able to get out today to go pick up a router to test that, but if I'm following what you are saying, its that someone could turn on the MAC address filtering on a router, then later turn it off but the router doesn't really turn it off?  So thats why I'd need to try a brand new one that hasn't been messed with at all?  And then if I find that the new router works, that means I have to switch routers? And not use MAC filtering anymore?

Since I won't be able to try that today, I looked at the second solution you posted and I got very different results for apt-cache madison hal:

beridel@ubuntu:~$ apt-cache madison hal
       hal | 0.5.11~rc2-1ubuntu8 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
       hal | 0.5.11~rc2-1ubuntu7 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
       hal | 0.5.11~rc2-1ubuntu7 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
       hal | 0.5.11~rc2-1ubuntu8 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources

It looks like the same version number with a bunch of repository urls or something, but without any of the other lines that your output had.  And it says I'm all up to date at this point (using a cat5 connection).

As for downgrading to a previous NM, I'm on the amd64 build so that package won't work for me and the 6.6.0 package for the 64 bit build looks to be the current one and the one I have installed now:

beridel@ubuntu:~$ apt-cache madison network-manager
network-manager | 0.6.6-0ubuntu5 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
network-manager | 0.6.6-0ubuntu5 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources

So I'm not sure what to do in regards to the second option.

Thanks again for the response.

---

### Post by ctsdownloads on 2008-05-11
> **Beridel said:**
> Thanks for the response cts.

I don't think I'll be able to get out today to go pick up a router to test that, but if I'm following what you are saying, its that someone could turn on the MAC address filtering on a router, then later turn it off but the router doesn't really turn it off?  So thats why I'd need to try a brand new one that hasn't been messed with at all?  And then if I find that the new router works, that means I have to switch routers? And not use MAC filtering anymore?

Since I won't be able to try that today, I looked at the second solution you posted and I got very different results for apt-cache madison hal:

beridel@ubuntu:~$ apt-cache madison hal
       hal | 0.5.11~rc2-1ubuntu8 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
       hal | 0.5.11~rc2-1ubuntu7 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
       hal | 0.5.11~rc2-1ubuntu7 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
       hal | 0.5.11~rc2-1ubuntu8 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources

It looks like the same version number with a bunch of repository urls or something, but without any of the other lines that your output had.  And it says I'm all up to date at this point (using a cat5 connection).

As for downgrading to a previous NM, I'm on the amd64 build so that package won't work for me and the 6.6.0 package for the 64 bit build looks to be the current one and the one I have installed now:

beridel@ubuntu:~$ apt-cache madison network-manager
network-manager | 0.6.6-0ubuntu5 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
network-manager | 0.6.6-0ubuntu5 | [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources

So I'm not sure what to do in regards to the second option.

Thanks again for the response.


As for the router thing, that is basically it. Rare, but I have seen MAC filtering fail to disable for whatever reason. :)

Sorry, wrong package:
[http://launchpadlibrarian.net/12498329/network-manager_0.6.6-0ubuntu1_amd64.deb](http://launchpadlibrarian.net/12498329/network-manager_0.6.6-0ubuntu1_amd64.deb)

So you will want to uninstall the existing 0.6.6-0ubuntu5 and then will be replacing it with the above linked 0.6.6-0ubuntu1 (AMD 64). After changing versions from ubuntu5 back to ubuntu1, do not forget to:

> sudo aptitude hold network-manager

If this fails, I would go back to my point on changing out the router. And if that *still* fails, might be interesting to toss Wicd into the mix, understanding that I have not had a lot of success with it recently. It is architecture neutral.
[http://wicd.sourceforge.net/screenshot.php](http://wicd.sourceforge.net/screenshot.php)

General settings for Wicd include using WEXT for WPA, WPA encryption set to WPA 1/2 in the app itself for WPA 2 Personal on the router.

---

### Post by Beridel on 2008-05-12
So now after messing around the older version of network-manager and having no luck, I went back to the current version (ubuntu5) and now I get no network icon in the systray...

I looked through TomL's thread again and someone had him run some commands to just diagnose the problem, and my outputs are a bit different from his:

lshw -C network
 *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:4c:60:e7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:6f:ef:83
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

iwconfig
wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:4c:60:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:157600 (153.9 KB)  TX bytes:157600 (153.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:6f:ef:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-6F-EF-83-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

dmesg to follow...

---

### Post by Beridel on 2008-05-12
Having issues posting the text straight in (says something about too many images) so I'll just upload the text file.

---

### Post by thomasaaron on 2008-05-12
To get your icon back, go to System > Preferences > Sessions > Start-up Programs. See if there is a Start-up program called 'Network Manager / Network Manager Applet.'

If there is, enable it. If not, Add it.
For the command, use:  nm-applet --sm-disable

Then reboot your computer. Icon?

Honestly, I don't think that all of this messing with HAL and re-loading Network Manager is going to solve the problem, but it is likely to result in a hosed system. I've never heard of anybody having to do any of that on our laptops.

The problem is most likely your router, or its MAC settings. Your previous logs showed that it is seeing the router, offering it the code, and then timing out. It is timing out because the router is not responding to it. So, if you are sure you have everything set appropriately in Network Manager, the problem is likely in your router.

The firmware upgrade idea was a good one. So was testing with a different router.

---

### Post by ctsdownloads on 2008-05-12
> **thomasaaron said:**
> 

Honestly, I don't think that all of this messing with HAL and re-loading Network Manager is going to solve the problem, but it is likely to result in a hosed system. I've never heard of anybody having to do any of that on our laptops.

I agree, but wanted to toss that out there if the router swap failed. Because at that point, the install is a no joy anyway, ya know? So hosing HAL is of little consequence by that point. Well and to be brutally honest, while I am speaking of made for Windows computers of course, I have had success doing this as a last ditch effort and NM does tend to regress like a stuck pig with little notice - Feisty vs Gutsy with RaLink chipsets, for example. Yeah, most of it was the change in the new wireless stack between 7.04 and 7.10, but I believe changes made to NM were also key as well. Obviously, made for Linux hardware is in a different boat, but when all else fails... :)

Sorry, I had to nitpick. It's just been a really annoying day here in Washington State today. :P

---

### Post by thomasaaron on 2008-05-12
> Because at that point, the install is a no joy anyway, ya know? So hosing HAL is of little consequence by that point.
but when all else fails... 

That is true. :lolflag:

> Sorry, I had to nitpick. It's just been a really annoying day here in Washington State today.

I hear ya. Right now it is about 70 degrees outside in Denver.
Tomorrow they are calling for snow!! IT'S MAY, FOR PETE'S SAKE!! Talk about annoying...

---

### Post by ctsdownloads on 2008-05-12
> **thomasaaron said:**
> That is true. :lolflag:



I hear ya. Right now it is about 70 degrees outside in Denver.
Tomorrow they are calling for snow!! IT'S MAY, FOR PETE'S SAKE!! Talk about annoying...

Wow, that is wild - summer one day, winter the next - you have to love Colorado! :)

---

### Post by Beridel on 2008-05-12
Alright, so I went to Best Buy today to "borrow" two new routers for tonight with my credit card.  I got two standard wireless G routers (both of them having nothing to do with wireless N, made sure ;) ).  One was a belkin and the other a dynex (which is best buy's home brand).  I think I conducted an experiment that would have made my middle school teachers proud, the same who loved to talk about the scientific method:

I had three computers for my experiment: 1) My system76 gazelle laptop 2) my sister's brand new vaio laptop 3) one of the office desktops.  For each router I would connect up the desktop, configure the router for our ISP and set it to no security or MAC filtering, and then check to see if the internet works.  Then I would see if my sister's laptop would connect, see if it could see the desktop, access the internet, make use of the router, etc.  And then finally I would try and connect my gazelle using NM by left clicking the systray icon and connecting to the wireless network.  So that was my method, now for the results ;)

Belkin Wireless G router:
Desktop hooked up fine, properly setup the router, accessed the internet
Sister's laptop found and connected to the wireless internet fine, could see the desktop through the network
My Gazelle could see the network as strong as could be, but would not connect.  While tail -f /var/log/daemon.log it caught up on "Old device 'wlan0' activating, won't change' and then would repeat that step maybe 8 times until it gave up and put wlan0 to sleep (I'll attach a sample in the following post of what I've been seeing up this entire time while trying to get it work, always has been the same)

ASIDE: Its slightly different when I disable roaming and try manually setting it up (entering the network id and setting it to Auto DHCP), it says it claims an IP address that is always the same regardless of which network, something like 169.241.etc and then it times out.  I'll attach an example of that as well in the following post.

Dynex Wireless G router:
Same exact results as the Belkin, with both the desktop and my sister's laptop connecting, seeing each other, able to access the internet with my gazelle seeing the network at full strength and then timing out.

So thats the experiment I did, I'll probably go return the two routers tomorrow.  I'll leave the interpreting of the results up to you two guys.  Thanks again for taking the time to look at this too, I do appreciate the help!

And that weather sounds all too familiar to me.  I remember last year towards the end of school at U of Michigan we had 2 weeks of beautiful 70 degree spring weather, and then we had a blizzard for two days.  And this was in April, gah!

---

### Post by Beridel on 2008-05-12
Here are the two logs for using the systray setup and then the manual setup:

Systray setup:
beridel@ubuntu:~$ tail -f /var/log/daemon.log
May 12 18:58:02 ubuntu NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May 12 18:58:02 ubuntu NetworkManager: <info>  SUP: response was '0' 
May 12 18:58:02 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4672616e6b' 
May 12 18:58:02 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 12 18:58:02 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
May 12 18:58:02 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 12 18:58:02 ubuntu NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May 12 18:58:02 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
May 12 18:58:02 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 12 18:58:08 ubuntu NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May 12 18:58:43 ubuntu last message repeated 3 times


Manually setup:
beridel@ubuntu:~$ tail -f /var/log/daemon.log
May 12 19:11:57 ubuntu avahi-autoipd(wlan0)[5946]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
May 12 19:11:57 ubuntu avahi-autoipd(wlan0)[5946]: Successfully called chroot().
May 12 19:11:57 ubuntu avahi-autoipd(wlan0)[5946]: Successfully dropped root privileges.
May 12 19:11:57 ubuntu avahi-autoipd(wlan0)[5946]: Starting with address 169.254.9.118
May 12 19:12:02 ubuntu avahi-autoipd(wlan0)[5946]: Callout BIND, address 169.254.9.118 on interface wlan0
May 12 19:12:04 ubuntu avahi-daemon[5192]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.118.
May 12 19:12:04 ubuntu avahi-daemon[5192]: New relevant interface wlan0.IPv4 for mDNS.
May 12 19:12:04 ubuntu avahi-daemon[5192]: Registering new address record for 169.254.9.118 on wlan0.IPv4.
May 12 19:12:06 ubuntu avahi-autoipd(wlan0)[5946]: Successfully claimed IP address 169.254.9.118
May 12 19:12:09 ubuntu NetworkManager: <info>  Updating allowed wireless network lists. 
May 12 19:12:47 ubuntu ntpdate[6161]: can't find host ntp.ubuntu.com 
May 12 19:12:47 ubuntu ntpdate[6161]: no servers can be used, exiting

---

### Post by jdb on 2008-05-12
This is what that section of my log looks like:

May 12 18:22:57 dads NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
May 12 18:22:57 dads NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
May 12 18:22:57 dads NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May 12 18:22:57 dads dhclient: wmaster0: unknown hardware address type 801
May 12 18:22:58 dads NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
May 12 18:22:58 dads dhclient: wmaster0: unknown hardware address type 801
May 12 18:22:59 dads dhclient: DHCPREQUEST of 192.168.15.101 on wlan0 to 255.255.255.255 port 67
May 12 18:23:00 dads dhclient: DHCPACK of 192.168.15.101 from 192.168.15.1
May 12 18:23:00 dads avahi-daemon[5307]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.15.101.
May 12 18:23:00 dads avahi-daemon[5307]: New relevant interface wlan0.IPv4 for mDNS.
May 12 18:23:00 dads avahi-daemon[5307]: Registering new address record for 192.168.15.101 on wlan0.IPv4.
May 12 18:23:00 dads dhclient: bound to 192.168.15.101 -- renewal in 38420 seconds.
May 12 18:23:00 dads NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface wlan0 
May 12 18:23:00 dads NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 

It looks like your DHCP deamon isn't starting.
Don't know why......

If you boot to an Ubuntu liveCD will it connect??

jdb

---

### Post by thomasaaron on 2008-05-13
OK, let's make your science teacher even more proud. Here are two more considerations:

1. There is a chance that your configurations are so hosed after all of this experimentation that Network Manager couldn't work properly if it wanted to. Boot your computer from a live CD and see if it will connect to the wireless network. Use the router of your choice. If you can connect, then we know it is a configuration issue, and your wireless card is fine.

2. There was a bug in network manager that kept it from connecting to UNSECURED networks. It did not affect all computers the same. It seemed to be related to certain computer/router/configuration combinations. Let's rule that out. Try setting up WPA encryption. Can you connect? If not, try that from a live CD as well. (Leave Mac filtering OUT of the equation.)

Hopefully these two experiments will give us a definitive answer as to whether we need to replace your wireless card, re-image your computer, etc...

---

### Post by Beridel on 2008-05-13
I burned myself a copy of the Ubuntu 8.04 live CD, making sure it had the correct MD5 sum.  I had a few troubles burning it, after 3 tries and checking for "disk integrity" each time it would always say 1 error was found.  But it booted it up into the live session of ubuntu fine.  Using NM, I got the same thing that has been happening each time.  It could see networks fine, but would just time out at "Old device 'wlan0' activating, won't change."  I first tried it with no security setup, and then with WPA security setup (both with no MAC filtering).  Neither one worked.

Whats the next step for me to try?

---

### Post by thomasaaron on 2008-05-13
Send me an email at support(at)system76(dot)com.

---

### Post by king20878 on 2008-05-16
This is a shot in the dark, but I had a very similar problem recently, and like you tried everything.  In the end I switched the router from using TKIP to AES for the encryption and suddenly everything works.  It even connects using Network Manager which it never did before.  Worth a try.

---

