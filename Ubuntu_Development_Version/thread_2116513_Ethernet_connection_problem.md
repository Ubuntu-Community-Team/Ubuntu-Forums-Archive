---
title: "Ethernet connection problem"
date: 2013-02-16
forum: Ubuntu Development Version
---

### Post by Budovi on 2013-02-16
Hi,

I have problems with ethernet (eth0 Wired connection) since I installed Raring (for about 4 days). I'm considering raising a bug report related to the kernel, but I thought it might be good idea to consult it there :)

So, the problem is: System boot -> everything ok. After some random time, in scale of minutes to hours, connection becomes totally unresponsive at one moment. It looks like packets are not considered to be delivered correctly, or become corrupted somewhere. Here is ifconfig output:
```
~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr e0:69:95:41:f8:ab  
          inet addr:<snip> Bcast:<snip>  Mask:255.255.254.0
          inet6 addr: <snip> Scope:Link
          inet6 addr: <snip> Scope:Global
          inet6 addr: <snip> Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81684 errors:0 dropped:5210 overruns:5208 frame:5208
          TX packets:48967 errors:0 dropped:0 overruns:0 carrier:7
          collisions:0 txqueuelen:1000 
          RX bytes:103994188 (103.9 MB)  TX bytes:5672165 (5.6 MB)
```I can reconnect to the internet by pulling out the cable and reconnecting it with some delay.

At first, in my opinion, no chance for hardware fault. Reasons: 1, working with Windows 2, tried different cable 3, worked with Precise (which I had before)

I tried set up MTU, forced kernel to not apply power saving for ethernet card, just because of similar bugs found. With no success.

Also purged network-manager and reinstalled it, now I'm considering "downgrade" it to precise version downloaded from packages.ubuntu.com . I turned on network debugging, but at the fault time, there is no record in syslog (I will attach it to this post...). Example times when problem occurred (watched with mtr, approx.): 6:17:45, 6:20:08, 6:24:02, 6:27:20

I downloaded mainline kernel but after boot up I just realized I'm not able to connect to the network without (missing) manager :oops: . So if you can "redirect me" to the right place to start debugging this way, I have no problem with that.

Thanks for help.

---

### Post by carl4926 on 2013-02-16
Was it not working from the Live session either?

---

### Post by Budovi on 2013-02-16
Hmm I really did not try that, that should not be problem...

---

### Post by carl4926 on 2013-02-16
> **Budovi said:**
> Hmm I really did not try that, that should not be problem...

I'm just trying to establish if you had that either in the Live Session or if you noticed when running the installer (because it checks for an active connection)

I take it 12.04 or 12.10 Live sessions have working eth0 ?

What about wireless? Do you have it?

---

### Post by Budovi on 2013-02-16
Downloading new daily image, will try "more precisely" then.

During installation there wasn't problem obviously, check - ok, I also checked to download updates (but not 100% sure if it happend, but did not noticed anything wrong). I ran live session for about an hour from USB before install, and I tried update packages and installed unity-tweak-tool for try. Everything was perfect.

Before Raring, I was using Precise for about a year (also alpha releases) and never had problems.

I doubt if it is related, but I find out that running "restart networking" or equivalent calls (init.d script, service networking restart) causes unity to crash, with reboot as an only option.

Wireless connection - I haven't noticed any problems, works flawlessly...

---

### Post by carl4926 on 2013-02-16
Well it is development so....
I installed kubuntu yesterday alpha2
And no issues

But I moved on and started testing something else.

Things to check are:
If the driver is loaded
Is rfkill reporting anything?

---

### Post by dino99 on 2013-02-16
a few questions:

- is that 13.04 installation a fresh one or a PP dist-upgrade ?
- have you purged all the related network installed packages, then reinstalled  them ?
- resolv.conf has been replaced by resolvconf (folder) some times ago; if you still have that oldish resolv.conf, then delete it as it disturb the system now.
- have you paid attention to the different logs to find usefull errors ? (/var/log/)

note: networkmanager has been a real pain with some chipsets a while back (might be resolved now), but wicd is a very good alternative in case of troubles.

---

### Post by Budovi on 2013-02-16
@carl4926:
Either I'm incredibly lucky, or live session does not suffer from this bug... I ran it for approx. 2,5 hours wit automatized page reloading and mtr to simulate conditions. :confused:

Driver is loaded and some of its responses are found in syslog (disconnected/connected cable). So it's looking that works. Maybe not correctly.

rfkill list contains wireless only and I haven't found anything about it. It would be really strange.

@dino99:
This is clean installation approx. 5 days old.

I purged 4 packaged related to "network-manager" (network-manager, -pptp, -gnome, -pptp-gnome) and also deleted configuration folders (which dpkg refused to remove, because of files inside).

I immidiately deleted "/etc/resolv.conf" in "hope" :D and lost capability of resolving names. :D Luckily, I ran "resolvconf -u" and it generated warning, that symbolic link to "/run/resolvconf/resolv.conf" is missing, so I fixed that deleted symlink and it is working again. So still used, as "compatibility symlink" i guess.

I checked deeply only syslog and used grep to find something in other logs by time.

I was using network-manager in precise with no problem for year, I will try Precise's version probably. Thanks for the tip to alternative...

@ both
Thank you for your time, I really appreciate that help.

---

### Post by VinDSL on 2013-02-16
> **dino99 said:**
> note: networkmanager has been a real pain with some chipsets a while back (might be resolved now), but wicd is a very good alternative in case of troubles.
> **Budovi said:**
> Thanks for the tip to alternative...
Dino's alternative is golden!  ;)

Some time ago (after an incremental upgrade) I started experiencing all sorts of network connection problems.  Most of the time, this machine wouldn't connect at all.  But, after several restarts, it would occasionally connect, then go into a pattern/scenario similar to your situation, as described above.

Purging NM and installing WiCD worked perfectly! I considered it as a temporary workaround, as we're supposed to be testing NM, you know? But, WiCD sustained me flawlessly in the interim. 

I switched back n' forth between managers, for a couple of months, expecting NM to be fixed, but it never happened.

Finally, I started wondering if the problem was my onboard, pseudo, southbridge driven, network chipset. So, I dug a NIC out of my closet -- an ancient NetGear network card with a real live DEC Tulip chipset -- installed it -- switched back to NM -- and haven't had a problem since.

* BTW, no other distros have connection problems on this box, even with the onboard network chipset, except the latest Ubu dev releases.

Anyway, that's my two-cents...  :)

---

### Post by Budovi on 2013-02-16
You can guess now :D

I have purged network-manager 0.9.7.995 and installed Precise version 0.9.4.1 . There was a problem with bluetooth dependency (of network-manager-gnome package) but I did not care, it worked and installation of that package could just messed up everything else.

Restarted and problem was still there. It's stupid that problem appeared from "nothing"... And with fact it works with live session - just WTF? :confused:

Then I have installed Wicd, and I'm now running about 2 hours without any problems. Only thing I regret is GUI which is not so... ergonomic... And as I can see there is not appindicator for this app, that means, no longer "white-list workaround" in Raring and no tray icon. I hope I did not missed any package.

Also I hope I will be able to set up WPA2-Enterprise network with own certificate. It is stupid that I cannot add wireless network without being in range, so still I don't know.

---

### Post by Budovi on 2013-02-16
After few more hours... It works... Ugly way. Hate this situation. I just cannot understand. I would raise a bug, but... as there is nothing to "catch on" and I'm alone for now, I think it won't have any effect and it will expire soon.

Obviously, problem with restart networking is still there. It is already reported as a bug on Launchpad and for 4 months just "confirmed". I know that fixing this type of bugs is not easy task, but....

Except this two stupid bugs I really like Raring... Thanks for all your time, I should probably resign now - and I hate that fact.

---

### Post by cariboo on 2013-02-16
I ran into the same problem as VindDSL on two of my systems. They both have the same motherboard, but different ***cpus*** :-D  and different ram. They are Nvidia based motherboards, and use the forcedeth driver.

The system I'm using right now, was getting so annoying I replaced the onboard NIC with a D-Link DGE-530T, and haven't had a problem since. The other system hasn't been updated to Raring, and is still running 12.04, and as little as I have used it over the last 6 months, the problem with that system seems to have gone away too. I'd suggest as VinDSL did that Network Manager is the problem.

---

