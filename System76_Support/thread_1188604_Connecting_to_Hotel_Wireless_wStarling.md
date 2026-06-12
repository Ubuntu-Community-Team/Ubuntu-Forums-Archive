---
title: "Connecting to Hotel Wireless w/Starling"
date: 2009-06-15
forum: System76 Support
---

### Post by mrchuc on 2009-06-15
Hello Everyone,

I just received my new Starling a few days ago, just in time to make a week long business trip out of town. 

I had no problem connecting the Starling to my wireless network at home and to another network at work. 

But, here at the hotel where I am staying, I can't get on. It is the type of network where you have to run a browser and the hotel's network hijacks the page to get you to agree to terms of service before you can surf, check email, etc. 

The Starling can detect the nework. I see it when I pull down the wireless menu. When I choose the hotel's wireless, however, the little blue "comet" goes round and round and eventually a black box comes up saying "Disconnected - You are now offline." 

I have seen some posts in the Ubuntu forums about this problem on other configurations, but, I am pretty new to Linux and am not sure what some of the fixes mentioned mean.

Anyone else experience this? (By the way, the same problem occurs at my local Panera restaurant.)

Thanks in advance!

Charles
University City, MO

---

### Post by thomasaaron on 2009-06-16
Run this command from a terminal...

tail -f /var/log/syslog

...then try to connect and watch the terminal. After it fails, copy the messages it created to this thread.

---

### Post by mrchuc on 2009-06-16
Thanks, Thomas.

Here is the log:

> mrchuc@system76-netbook:~$ tail -f /var/log/syslog
Jun 16 11:47:46 system76-netbook NetworkManager: <info>  (wlan0): bringing up device. 
Jun 16 11:47:49 system76-netbook kernel: [31527.391798] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 16 11:47:49 system76-netbook NetworkManager: <info>  (wlan0): preparing device. 
Jun 16 11:47:49 system76-netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Jun 16 11:47:49 system76-netbook NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Jun 16 11:47:49 system76-netbook NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
Jun 16 11:47:51 system76-netbook kernel: [31528.936734] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:47:51 system76-netbook kernel: [31529.136242] wlan0: direct probe to AP f2e2e6b8 try 2
Jun 16 11:47:51 system76-netbook kernel: [31529.336130] wlan0: direct probe to AP f2e2e6b8 try 3
Jun 16 11:47:51 system76-netbook kernel: [31529.536128] wlan0: direct probe to AP f2e2e6b8 timed out
Jun 16 11:50:01 system76-netbook /USR/SBIN/CRON[15364]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Hotel WIFI' 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Hotel WIFI' requires no security.  No secrets needed. 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  Config: added 'ssid' value 'Hotel WIFI' 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  Config: set interface ap_scan to 1 
Jun 16 11:50:44 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning 
Jun 16 11:50:46 system76-netbook kernel: [31703.900892] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:50:46 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Jun 16 11:50:46 system76-netbook kernel: [31704.048631] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:50:46 system76-netbook kernel: [31704.120634] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:50:46 system76-netbook kernel: [31704.320121] wlan0: direct probe to AP f2e2e6b8 try 2
Jun 16 11:50:46 system76-netbook kernel: [31704.520128] wlan0: direct probe to AP f2e2e6b8 try 3
Jun 16 11:50:47 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Jun 16 11:50:47 system76-netbook kernel: [31704.720091] wlan0: direct probe to AP f2e2e6b8 timed out
Jun 16 11:50:56 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Jun 16 11:50:57 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Jun 16 11:50:58 system76-netbook kernel: [31715.592635] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:50:58 system76-netbook kernel: [31715.664632] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:50:58 system76-netbook kernel: [31715.864107] wlan0: direct probe to AP f2e2e6b8 try 2
Jun 16 11:50:58 system76-netbook kernel: [31716.064106] wlan0: direct probe to AP f2e2e6b8 try 3
Jun 16 11:50:58 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Jun 16 11:50:58 system76-netbook kernel: [31716.264103] wlan0: direct probe to AP f2e2e6b8 timed out
Jun 16 11:51:02 system76-netbook NetworkManager: <info>  wlan0: link timed out. 
Jun 16 11:51:07 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Jun 16 11:51:09 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Jun 16 11:51:09 system76-netbook kernel: [31727.144635] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:51:09 system76-netbook kernel: [31727.216636] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:51:09 system76-netbook kernel: [31727.416098] wlan0: direct probe to AP f2e2e6b8 try 2
Jun 16 11:51:10 system76-netbook kernel: [31727.616134] wlan0: direct probe to AP f2e2e6b8 try 3
Jun 16 11:51:10 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Jun 16 11:51:10 system76-netbook kernel: [31727.816097] wlan0: direct probe to AP f2e2e6b8 timed out
Jun 16 11:51:11 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating 
Jun 16 11:51:11 system76-netbook kernel: [31729.452635] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:51:11 system76-netbook kernel: [31729.524633] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:51:12 system76-netbook kernel: [31729.724098] wlan0: direct probe to AP f2e2e6b8 try 2
Jun 16 11:51:12 system76-netbook kernel: [31729.924148] wlan0: direct probe to AP f2e2e6b8 try 3
Jun 16 11:51:12 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Jun 16 11:51:12 system76-netbook kernel: [31730.124104] wlan0: direct probe to AP f2e2e6b8 timed out
Jun 16 11:51:21 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Jun 16 11:51:23 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Jun 16 11:51:23 system76-netbook kernel: [31741.008762] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:51:23 system76-netbook kernel: [31741.084639] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:51:23 system76-netbook kernel: [31741.284131] wlan0: direct probe to AP f2e2e6b8 try 2
Jun 16 11:51:23 system76-netbook kernel: [31741.484135] wlan0: direct probe to AP f2e2e6b8 try 3
Jun 16 11:51:24 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Jun 16 11:51:24 system76-netbook kernel: [31741.684132] wlan0: direct probe to AP f2e2e6b8 timed out
Jun 16 11:51:25 system76-netbook NetworkManager: <info>  wlan0: link timed out. 
Jun 16 11:51:33 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Jun 16 11:51:34 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Jun 16 11:51:34 system76-netbook kernel: [31752.552637] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:51:35 system76-netbook kernel: [31752.624638] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:51:35 system76-netbook kernel: [31752.824129] wlan0: direct probe to AP f2e2e6b8 try 2
Jun 16 11:51:35 system76-netbook kernel: [31753.024099] wlan0: direct probe to AP f2e2e6b8 try 3
Jun 16 11:51:35 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Jun 16 11:51:35 system76-netbook kernel: [31753.224127] wlan0: direct probe to AP f2e2e6b8 timed out
Jun 16 11:51:44 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Jun 16 11:51:45 system76-netbook NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation. 
Jun 16 11:51:45 system76-netbook NetworkManager: <info>  (wlan0): device state change: 5 -> 9 
Jun 16 11:51:45 system76-netbook NetworkManager: <info>  Activation (wlan0) failed for access point (Hotel WIFI) 
Jun 16 11:51:45 system76-netbook NetworkManager: <info>  Marking connection 'Auto Hotel WIFI' invalid. 
Jun 16 11:51:45 system76-netbook NetworkManager: <info>  Activation (wlan0) failed. 
Jun 16 11:51:45 system76-netbook NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Jun 16 11:51:45 system76-netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Jun 16 11:51:46 system76-netbook kernel: [31764.028353] wlan0: direct probe to AP f2e2e6b8 try 1
Jun 16 11:51:46 system76-netbook kernel: [31764.228089] wlan0: direct probe to AP f2e2e6b8 try 2
Jun 16 11:51:46 system76-netbook kernel: [31764.428126] wlan0: direct probe to AP f2e2e6b8 try 3
Jun 16 11:51:47 system76-netbook kernel: [31764.628111] wlan0: direct probe to AP f2e2e6b8 timed out


All the best...

Chuc

---

### Post by thomasaaron on 2009-06-16
Hmmm... there's no encryption on the hotel wireless. And nothing's really going *wrong* per se. They are just not able to associate. What kind of signal strength are you seeing. 

Can you connect if you get closer to router. Ask at the front desk where it is. Maybe you're out of range.

---

### Post by mrchuc on 2009-06-16
Hi Thomas,

Signal strength is excellent. It shows in the menu. Also I have my Mac G4 sitting beside it and it connects with no problem. My iPod Touch also hooks up without a problem. 

So far the Starling has had this problem at two sites: this hotel and a local restaurant. Both have the kind of setup where you have to run a browser before you can surf.

When it connects to a password protected site there seems to be no problem. (scratches head). Anything else to try?

Chuc

---

### Post by thomasaaron on 2009-06-16
Let's move this to email. You may have a problem with your wireless card. support(at)system76(dot)com.

---

### Post by xsswx on 2009-06-16
hello folks! curious if this one has been resolved. I have had trouble with a starling connecting wirelessly on a network at a college that has a web browser login. i have also had some problems on open networks. in both cases i can't seem to connect when i am showing a strong but not 100% signal strength.

---

### Post by thomasaaron on 2009-06-17
No, we're still working on this one via email.

---

### Post by mrchuc on 2009-06-17
Thanks to Tom, I am connected wirelessly at the hotel.

Turns out the only real problem was that I was not getting a strong enough signal for the Starling. Seems that it is not quite as good at receiving as my other laptop. When I took it out in the hall the signal jumped up and the Starling connected like a champ. I took it back in the hotel room and put it back on the desk and lost the connection. However, I discovered that there were places in my room where the Starling received a good signal. This is actually no different than my experiences with my other laptop--just the Starling seems a little more sensitive. My room is at the end of the hall and farthest from the router. When I have been in this situation before, it was a similar problem with my Mac.

Frankly, that is my only criticism of the Starling so far, and today, with it placed where it could receive (still in my room) it did extremely well. 

So, in short, it was a coincidence that both places that I failed to connect happened to be the kind where I had to run a browser to sign in. In both cases, I was getting a signal that was too weak to get connected.

Thanks, Tom, for all the help, both on the forum and via private email. Glad to do business with a company so dedicated to customer service! :)

Chuc

---

### Post by venomheir on 2009-08-03
Hello Team,
           I have purchased the starling 3 weeks ago, I connected wirelessly at home no problem, I love ubuntu, had installed it on other laptops at home, Had a friend who wanted to
purchase a netbook but wanted to test drive one before doing so.
I explained to her how great Ubuntu has worked for me and she could borrow my starling for a week, to my surprise she could not maintain or even see networks unless she was on top of them
6 feet???? I was so embarrassed and dissappointed, luckily system76 has info at knowledge base to install windows XP, She can now connect even when signal is at 45%. I will reinstall Ubuntu
when she is done, but this incident has killed System76 and Ubuntu from her even looking at it again. Any idea as to when an update will be out?? I refuse to give up such a great OS.

---

### Post by RichardK on 2009-08-04
I'm also having problems with a Starling refusing to connect to a wifi network.  Both at home and at work, there are locations where my Darter connects fine, but the new Starling can't/won't.

The log shows the following error after trying three or four times:
wlan0: direct probe to AP f60e76b8 timed out

Please help,
Richard

---

### Post by thomasaaron on 2009-08-04
Hi, Richard.

First run your system76 driver (System > Admin > System76 Driver > Install (tab) > Install (button)). 

Then reboot.

Does that help?

If not, what happens if you move closer to your access point?

---

### Post by RichardK on 2009-08-04
Not sure if I was already up to date or not.  However, now after hitting the Install button and rebooting, I'm at Sys76 Driver 2.3.6.

No improvement. The little signal strength meter shows about 50% strength for this network.  iwlist wlan0 scan shows quality=41/70 and signal level=-69 dBm. This signal is enough for my Daru2 and an Aspire One which I've used here, but not for the Starling.

Like others have posted, if I'm right on top of the AP (<15ft away), the netbook will connect.

Catching up on the threads here, I see there's one dedicated to improving the RTL8187 driver (I have the RTL8187B):
[http://ubuntuforums.org/showthread.php?t=1202015&page=7](http://ubuntuforums.org/showthread.php?t=1202015&page=7)
What's the status on that?

Thanks,
Richard

---

### Post by ShowMeGrrl on 2009-08-04
Yes, it seems that many people are having the same problem with Starling wi-fi: if you are not close to the access point, then you can't connect. That issue seems to be at the bottom of almost all wi-fi problems people are having on the Starling. The solution almost invariably is to move closer to the access point. 

Of course, this is not really a "solution" in cases where it is not convenient or possible to move closer. If I am in a library and everybody around me is connected and I'm not, I don't really believe that is satisfactory performance.

And let's face it: there are few functions on a netbook more important than wi-fi. The whole reason most people buy a netbook is portability -- staying connected in a wide variety of environments while outside your home.

C'mon System76, let's wipe the mud off the face here and get a fix to this problem! This is a golden opportunity to expand the Linux marketshare. If you don't get this fixed, you're going to blow it.

---

### Post by thomasaaron on 2009-08-04
Believe me, we are trying.

---

### Post by ShowMeGrrl on 2009-08-04
Glad to hear it! Please keep us informed.

---

### Post by thomasaaron on 2009-08-04
We just SUBSTANTIALLY increased the range and performance of the Starling wireless adapter. Also fixed the wireless LED bug.

Fix will be out via a new System76 driver in a few days.

---

