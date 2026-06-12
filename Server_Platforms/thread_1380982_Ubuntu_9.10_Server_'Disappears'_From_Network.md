---
title: "Ubuntu 9.10 Server 'Disappears' From Network"
date: 2010-01-14
forum: Server Platforms
---

### Post by theMagius on 2010-01-14
**_The Short Version_**
[LIST=1]
[*]Two Vista machines connected to a 2Wire wireless router (AT&T UVerse) via DHCP.
[*]One (headless) Ubuntu 9.10 Server machine connected (tried both wireless and wired at different times) to the same 2Wire router via a static IP.
[*]Samba is installed on the Ubuntu Server.
[*]Vista computers connect perfectly to Ubuntu Server.
[*]Various file transfers/communications ensue.
[*]Ubuntu Server 'disappears' from network.  Sometimes after a couple of minutes.  Sometimes longer.  Cannot ping server.  Cannot SSH into server.  It's just 'gone'.
[*]Reboot server.  Everything's fine (can ping, find, connect, etc.) until (some minutes later) server 'disappears' again.
[/LIST]

**_The Long Version_**

_Network Configuration_
```

|---------------------|
| Vista Machine #1    |\
| 192.168.1.70 (DHCP) |  \
|---------------------|   \
                           \
|---------------------|      |-----------------|
| Vista Machine #2    |----- | 2Wire Router    |
| 192.168.1.80 (DHCP) |      | 192.168.1.254   |
|---------------------|    / |-----------------|
                          /
|---------------------|  /
| Ubuntu Server       | / 
| 192.168.1.5 (static)|/
| workgroup = MY_NAS  |
|---------------------|

```

_First Test_
[LIST=1]
[*]Power on 2Wire Router and both Vista machines
[*]Power on Ubuntu Server
[*]Do *not* login to Server 
[*]From each Vista machine, ping 192.168.1.5.  Pings ok.
[*]From each Vista machine, Map Network Drive as \\MY_NAS\(user folder).  Maps ok.  Browses folders ok.
[*]From (either) Vista machine, start file backup (via Cobian Backup program for Windows; mapped to same network drive as above...) to \\MY_NAS\(user folder).  
[*]Somewhere during the file backup, failures begin (never at the same place).  File backup fails.  From each Vista machine, ping 192.168.1.5.  Pings fail.  
[*]From each Vista machine, ping other devices on the network.  Pings ok.  
[*]Attempt to SSH into Ubuntu Server from Vista Machine #1.  SSH does not connect.
[*]Reboot Vista Machine #1 into Ubuntu 9.10 Desktop Edition.  Ping 192.168.1.5.  Pings fail.
[*]Reboot Ubuntu Server.
[*]Ubuntu Server appears on network (again) at 192.168.1.5
[/LIST]

_Second Test_
[LIST=1]
[*]Power on 2Wire Router and Vista machine #2
[*]Power on Ubuntu Server
[*]Do *not* login to Server 
[*]From Vista #2, ping 192.168.1.5.  Pings ok.
[*]From Vista #2, Map Network Drive as \\MY_NAS\(user a folder).  Maps ok.  Browses folders ok.
[*]Power on Vista machine #1
[*]From Vista #1, ping 192.168.1.5.  Pings ok.
[*]From Vista #1, Map Network Drive as \\MY_NAS\(user b folder).  Map fails.
[*]From each Vista machine, ping 192.168.1.5.  Pings fail. 
[*]Attempt to SSH into Ubuntu Server from Vista Machine #1.  SSH does not connect.
[*]Reboot Ubuntu Server.
[*]Ubuntu Server appears on network (again) at 192.168.1.5
[/LIST]

**_The Question_**

Why won't my damned Ubuntu server just stay connected to the network?

Pulling my hair out,
-theMagius

---

### Post by CharlesA on 2010-01-14
Best thing to do would probably be to hook up a monitor and keyboard and wait for it to lose connection, then login physically and see what is going on.

Check ifconfig and whatnot.

Also, does the router support reserving IP addresses? If it does, make try using a dhcp assigned address and see if the problem still happens.

---

### Post by Shiva-Shinken on 2010-01-14
I am having similar issue with Server 9.10. And here is the interesting part... when the machine is connected to a keyboard and monitor, it will remain connected to the network without a problem (tested it for over 24 hours).  Restarting the machine without keyboard and monitor will make it drop network (and possibly be freezing up) within 10-15 minutes after starting up.

In the previous version of ubuntu server, the machined hummed along happily without any problems.  Once I did a clean install of this new version (9.1) is when all the problems have cropped up :(

Being new to Linux, I am feeling a bit frustrated needless to say.

CC

May not be relevant info, but the server is connected to mostly Windows 7 and XP machine environment.

---

### Post by neoanderthal on 2010-01-14
what do your logs tell you?
at first blush, it sounds like your machine is powering off your ethernet adapter and/or going to sleep. 
have you checked your power config in your BIOS?

---

### Post by theMagius on 2010-01-14
> **neoanderthal said:**
> what do your logs tell you?
at first blush, it sounds like your machine is powering off your ethernet adapter and/or going to sleep. 
have you checked your power config in your BIOS?

I realize that the ethernet controller in the BIOS may be a possibility.  But, if this were the case, wouldn't the disconnects occur after exactly 'x' number of minutes in each test that I ran (as opposed to random timeouts)?

Also, I'm it bit ignorant of the Linux file system.  Is there a single, encompassing directory for log files?  Or are there multiple directories for multiple hardware logs in Linux?

Thanks,
-theMagius

---

### Post by theMagius on 2010-01-14
> **Shiva-Shinken said:**
> And here is the interesting part... when the machine is connected to a keyboard and monitor, it will remain connected to the network without a problem (tested it for over 24 hours).  Restarting the machine without keyboard and monitor will make it drop network (and possibly be freezing up) within 10-15 minutes after starting up.

Hmmm...  Now that you mention it, I don't recall having these difficulties when the monitor was hooked up to the server box.

I'll try the experiments again later tonight with the 'head' on the machine.

Thanks,
-theMagius

---

### Post by theMagius on 2010-01-14
> **CharlesA said:**
> Also, does the router support reserving IP addresses? If it does, make try using a dhcp assigned address and see if the problem still happens.

The router has reserved all IP address (suffixes) above 60 for DHCP allocation.  My former NAS box (not Ubuntu) was located at 192.168.1.4, and worked flawlessly on the network.

Thanks,
-theMagius

---

### Post by Shiva-Shinken on 2010-01-14
> **neoanderthal said:**
> what do your logs tell you?
at first blush, it sounds like your machine is powering off your ethernet adapter and/or going to sleep. 
have you checked your power config in your BIOS?

Well, it is not a "sleep" problem, as I have been disconnected while using the server (was creating some Samba shares).  Again, the server was headless and I was accessing it via Putty (SSH) remotely.  At the moment it stopped responding, I noticed that all connections to it were down, no ping, no webmin etc.

---

### Post by Shiva-Shinken on 2010-01-14
Verified the "headless" setup again... without a monitor, the connection crapped out on me withing 15-20 minutes.  Frustrated I plugged in both keyboard and monitor, and lo-and-behold, the PC run just fine for over 5 hours until I voluntarily shut it down.  Strange I tell ya, strange.

PS:  While researching this problem, I came across another forum with someone saying the same thing (about headless setup).

CC

---

### Post by theMagius on 2010-01-15
> **Shiva-Shinken said:**
> Verified the "headless" setup again... without a monitor, the connection crapped out on me withing 15-20 minutes.  Frustrated I plugged in both keyboard and monitor, and lo-and-behold, the PC run just fine for over 5 hours until I voluntarily shut it down.  Strange I tell ya, strange.

Confirmed on my end, also.  Repeated both tests with a monitor connected to the system and had 100% file transfer and system login functionality between all computers for several hours.


> PS:  While researching this problem, I came across another forum with someone saying the same thing (about headless setup).

Would you be able to provide a link to the other forum post?

I'd like to get a bug put into Ubuntu's defect-tracking system (SVN?) as soon as possible.

Thanks,
-theMagius

CC

---

### Post by Shiva-Shinken on 2010-01-15
Let me dig that up, I will post as soon as I get it.

Update:  After work, I looked for the post, but won't you know it, could not locate it.  I will post if I find it again.

CC

---

### Post by Shiva-Shinken on 2010-01-15
Found it... read reply #6:

[http://serverfault.com/questions/80520/ubuntu-server-9-10-freezes-up-after-10-minutes]("http://serverfault.com/questions/80520/ubuntu-server-9-10-freezes-up-after-10-minutes")

> A bit of a blind one, should've worked it out far sooner... but just in case anyone else is set up the same, I also get, or believed I had the same problem... but my solution seems a lot simpler than expected.

I usually keep my server without any attached peripherals, no keyboard, screen or anything... with 9.04 that seemed absolutely fine. Or course I connect and managed it therefore over ssh but after 10 minutes or so, after the upgrade to 9.10, all woudl appear to freeze, even singing a ping to the server would come back without response...

After trying all the related fixed, I eventually went to plug a monitor in to possibly work on graphics problem that many people seem to blame for this... before long the problem occurred again and I went to plug in a keyboard directly to the server. At that moment I realised the connection had become active again... Now, I have left the keyboard attached for about 12 hours and I have had no problems so far... Any ideas on why a lack of keyboard could give this effect?

Anyway, I know it likely shouldn't be here, but I though someone may have tried all fixes remotely like myself and would benefit from this.


:)

CC

---

### Post by Shiva-Shinken on 2010-01-19
theMagius, have you found out any more info/solution to this issue yet?

CC

---

### Post by yourik on 2010-04-04
> **Shiva-Shinken said:**
> theMagius, have you found out any more info/solution to this issue yet?

CC
The solusion worked for me was to add nomodeset to /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **nomodeset**"taken form :[http://serverfault.com/questions/80520/ubuntu-server-9-10-freezes-up-after-10-minutes](http://serverfault.com/questions/80520/ubuntu-server-9-10-freezes-up-after-10-minutes)

---

### Post by larry.jef on 2010-04-14
> **yourik said:**
> The solusion worked for me was to add nomodeset to /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **nomodeset**"taken form :[http://serverfault.com/questions/80520/ubuntu-server-9-10-freezes-up-after-10-minutes](http://serverfault.com/questions/80520/ubuntu-server-9-10-freezes-up-after-10-minutes)
Don't forget to run
$ sudo update-grub
after all.

---

