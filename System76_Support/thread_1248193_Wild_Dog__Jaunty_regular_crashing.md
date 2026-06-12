---
title: "Wild Dog / Jaunty regular crashing"
date: 2009-08-23
forum: System76 Support
---

### Post by corey.abshire on 2009-08-23
While I enjoy it tremendously, my Wild Dog has a tendency to crash rather often. To the best of my memory, it has been doing this somewhat regularly since I started using it; maybe once or twice per week. Lately, I've been using it much more often, and noticed that in response it is crashing more often.

I'm looking for help on how to better determine exactly what it is that is causing this and take action to prevent it. I've tried inspecting as many log files as I could based on whatever I was doing at the time to diagnose the issue on my own but am ready to admit that I need help to get this solved.

My most recent actions are:

1) Run a full memtest+  (I read on one forum thread bad memory could sometimes cause random crashing - I ran it - it passed - no errors).
2) Upgrade to most recent flashplayer 64 bit from Adobe (I had read many different people having issues with the old one - I seem to have same frequency of crashes before and after. I followed instructions posted by Tom and it seems to work fine, but I still get random crashes.)
3) Upgrade to latest video driver - ATI latest propietary (I had read from many posts that video drivers can cause issues so I stay on the latest in hopes that it will have fixed whatever is causing my crashes)

I always install whatever updates come through the normal system updates. I don't install a lot other than that. A few programs available through Add/Remove programs is about it.

When it crashes, it typically fails in one of the following three modes:

1) Immediately black screen / reboot. (usually a slight pop from the speakers if they're turned up when it does this).
2) Screen freezes / mouse hangs and I have to hold down the power button until it dies and then press it again to turn it back on.
3) Screen gets all garbled and sound card emits some strange garbage and I have to hold down the power button until it dies and then press it again to turn it back on.

Mode 2 has been occuring the most often of late. It occured perhaps two or three times today alone, as I've used my computer quite a bit today.

I will attach my logs from the system76 log archive builder.

Can anyone help me out here?

Thanks! - corey

---

### Post by jdb on 2009-08-23
> **corey.abshire said:**
> While I enjoy it tremendously, my Wild Dog has a tendency to crash rather often. To the best of my memory, it has been doing this somewhat regularly since I started using it; maybe once or twice per week. Lately, I've been using it much more often, and noticed that in response it is crashing more often.

I'm looking for help on how to better determine exactly what it is that is causing this and take action to prevent it. I've tried inspecting as many log files as I could based on whatever I was doing at the time to diagnose the issue on my own but am ready to admit that I need help to get this solved.

My most recent actions are:

1) Run a full memtest+  (I read on one forum thread bad memory could sometimes cause random crashing - I ran it - it passed - no errors).
2) Upgrade to most recent flashplayer 64 bit from Adobe (I had read many different people having issues with the old one - I seem to have same frequency of crashes before and after. I followed instructions posted by Tom and it seems to work fine, but I still get random crashes.)
3) Upgrade to latest video driver - ATI latest propietary (I had read from many posts that video drivers can cause issues so I stay on the latest in hopes that it will have fixed whatever is causing my crashes)

I always install whatever updates come through the normal system updates. I don't install a lot other than that. A few programs available through Add/Remove programs is about it.

When it crashes, it typically fails in one of the following three modes:

1) Immediately black screen / reboot. (usually a slight pop from the speakers if they're turned up when it does this).
2) Screen freezes / mouse hangs and I have to hold down the power button until it dies and then press it again to turn it back on.
3) Screen gets all garbled and sound card emits some strange garbage and I have to hold down the power button until it dies and then press it again to turn it back on.

Mode 2 has been occuring the most often of late. It occured perhaps two or three times today alone, as I've used my computer quite a bit today.

I will attach my logs from the system76 log archive builder.

Can anyone help me out here?

Thanks! - corey

The last thing I see in the log is /dev/sdb1 being mounted, probably USB memory.
Did it crash when you plugged it in??

jdb

---

### Post by corey.abshire on 2009-08-24
No, it had been plugged in for a day or two. It has been crashing pretty regularly for months. I've only used that drive once or twice in the past few days and haven't noticed it make any difference. Thanks. - corey

---

### Post by jdb on 2009-08-24
> **corey.abshire said:**
> No, it had been plugged in for a day or two. It has been crashing pretty regularly for months. I've only used that drive once or twice in the past few days and haven't noticed it make any difference. Thanks. - corey

It's very strange that it had been plugged in for more than a day and it just mounted before the crash, they usually mount right away.
Since it's kind of a strange entry and it's the last entry before it crashed, it would be interesting to know if it shows up again next time it crashes.

jdb

---

### Post by gila_monster on 2009-08-24
Corey,

I'm not entirely familiar with the Wild Dog, so bear with me a bit. A couple of questions:

1) What kernel are you running?

2) Does WD use an nVidia GPU?

3) What filesystem is being used by root (/) and /home?

I had similar issues a while back. Turns out that certain kernels had some problems that may have been exacerbated by certain filesystems. There may also have been interactions with some nVidia drivers. As such, we may be able to try a few things.

---

### Post by thomasaaron on 2009-08-24
Cory, your Wild Dog has an ATI card.

We have seen some circumstances where the current ATI driver in Ubuntu's repositories acts somewhat lethargic. It may also be causing some freezing as well. There are new drivers that perform far better. To give it a try run the following commands in your terminal one at a time - they are rather long commands - you can cut and paste them (Applications > Accessories > Terminal)

echo deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

echo deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B22AB97AF1CDFA9 && sudo apt-get update

sudo apt-get upgrade

---

### Post by corey.abshire on 2009-08-24
> **jdb said:**
> It's very strange that it had been plugged in for more than a day and it just mounted before the crash, they usually mount right away.
Since it's kind of a strange entry and it's the last entry before it crashed, it would be interesting to know if it shows up again next time it crashes.

jdb

It mounts late in the restart cycle. I'm assuming you're talking about it being the last entry in the system log. I think that's because I collected the logs after it came back up, so you're seeing all the post restart messages in there. The last crash represented in the logs occurs at "Aug 23 21:40:19". The last event before it crashed is a cron job updating MOTD. Basically everywhere you see "restart." in that file is just after a crash. I don't see any where that drive mounting is the last thing before the crash event. Is that what you were talking about or did I miss something? Thanks. - corey

---

### Post by corey.abshire on 2009-08-24
> **gila_monster said:**
> 1) What kernel are you running?

# uname -a
Linux system76-pc 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

> **gila_monster said:**
> 2) Does WD use an nVidia GPU?

Nope, its ATI. You can see it in the xorg log. Its here:

ATI Technologies Inc RV770 [Radeon HD 4850] rev 0, Mem @ 0xd0000000/268435456, 0xe0020000/65536, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072

ATI Proprietary Linux Driver Version Identifier:8.64.3
ATI Proprietary Linux Driver Release Identifier: 8.64                                 
ATI Proprietary Linux Driver Build Date: Jul 14 2009 21:18:29

> **gila_monster said:**
> 3) What filesystem is being used by root (/) and /home?

ext3

# df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext3    14418532   8836080   4850032  65% /
...
/dev/sda3     ext3   939437748  25320288 866396764   3% /home
...

> **gila_monster said:**
> I had similar issues a while back. Turns out that certain kernels had some problems that may have been exacerbated by certain filesystems. There may also have been interactions with some nVidia drivers. As such, we may be able to try a few things.

Interesting. I'll keep an eye out for whether that may be a contributing factor.

Thanks. - corey

---

### Post by corey.abshire on 2009-08-24
> **thomasaaron said:**
> Cory, your Wild Dog has an ATI card.

We have seen some circumstances where the current ATI driver in Ubuntu's repositories acts somewhat lethargic. It may also be causing some freezing as well. There are new drivers that perform far better. To give it a try run the following commands in your terminal one at a time - they are rather long commands - you can cut and paste them (Applications > Accessories > Terminal)

echo deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

echo deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B22AB97AF1CDFA9 && sudo apt-get update

sudo apt-get upgrade

Ok ran that.

I had already upgraded to the latest ATI driver, but looks like this updated a bunch of xorg stuff that hopefully might help. Here's a list of what it updated:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  fglrx-modaliases kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data
  libdrm-intel1 libdrm2 libvorbis-dev libvorbis0a libvorbisenc2 libvorbisfile3
  nvidia-173-modaliases nvidia-180-modaliases nvidia-96-modaliases php5-cli
  php5-common xserver-xorg-input-synaptics xserver-xorg-video-ati
  xserver-xorg-video-intel xserver-xorg-video-nv xserver-xorg-video-openchrome
  xserver-xorg-video-radeon xserver-xorg-video-sisusb
24 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 32.8MB of archives.
After this operation, 172kB disk space will be freed.

It hadn't crashed today (yet) but I haven't used it that much today. I'll go for a reboot now and hopefully it'll help. Will let you know. 

Please let me know if there's anything else I could try in the interim. Also, was wondering if there is anything else you'd recommend settting to have the system generate more information during a crash to help in troubleshooting. The logs don't seem to be providing much value in this situation as-is.

Thanks. - corey

---

### Post by jdb on 2009-08-24
> **corey.abshire said:**
> It mounts late in the restart cycle. I'm assuming you're talking about it being the last entry in the system log. I think that's because I collected the logs after it came back up, so you're seeing all the post restart messages in there. The last crash represented in the logs occurs at "Aug 23 21:40:19". The last event before it crashed is a cron job updating MOTD. Basically everywhere you see "restart." in that file is just after a crash. I don't see any where that drive mounting is the last thing before the crash event. Is that what you were talking about or did I miss something? Thanks. - corey

Yeah, I see that now, I wasn't thinking too straight.
Whatever it is, it sure isn't leaving any clues in the log files.

jdb

---

### Post by gila_monster on 2009-08-24
> **corey.abshire said:**
> # uname -a
Linux system76-pc 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux



Okay, we can rule out ext4 and nVidia, then. My recollection is that the 2.6.28-15 kernel was supposed to resolve the issues the earlier versions experienced, but I don't recall seeing anything that states that specifically. I have a newer kernel installed right now, so I can't verify anything directly. Might want to do a quick search on the Forums about the kernel, though.

---

### Post by corey.abshire on 2009-08-26
Ok, so here's an update since my last one. After I completed the update recommended by Tom, I have not experienced a crash while using the computer, but have seen that its restarted on two occasions while I was away (once during the night, once while I was away at work). 

Even though my microwave and oven clocks weren't blinking, for some reason I wanted to suspect power outage or brownout could cause something like that since I was away and didn't have anything running on the machine I could remember. Which made me start thinking if for some reason every few days while I'm using it if I don't get clean power it could be sensitive to that and be causing my crashes.

So, since I'd been considering it for a while anyway, I went ahead and purchased a fairly decent UPS tonight - an APC XS 1500. Its one of the models that has the AVR technology, so hopefully this will rule power problems completely out of the picture.

Here's a brief summary of actions I've taken over the last few days to really attack this issue, for anyone else who may be experiencing similar issues:

1. apply all patches from update manager as usual
2. install latest video driver from ATI
3. remove nspluginwrapper based flash plugin and install newly released 64 bit version from Adobe
4. add x-sources repositories mentioned by Tom and fetch updated xorg and related updates
5. put entire machine behind UPS to eliminate potential power issues

Hopefully tonight is the beginning of a very long uptime. I'll keep you guys posted and see if the actions I've taken during the past few days finally leaves me with a stable system. 

Current uptime:

23:16:23 up 25 min,  2 users,  load average: 0.28, 0.12, 0.10

Lets see if I can make it a month without a crash or restart from tonight.

Thanks for your help and guidance thus far. - corey

---

### Post by jdmelton on 2009-08-28
corey,

Most of the time we do not think about it, but our power supply can be a real problem. This does not sound like it is your only problem, yet it can be a part of it. I used to live in Charleston, South Carolina in the 1980's and our voltage would sometimes drop to 104 VAC. That is bad. Some of the reasons were old power lines, manual voltage controls, and inattentive staff (my opinion). At the time I was working for Charelston Naval Shipyard and we monitored voltage, so that is how I became aware of this problem.

I also experienced drops to 109 VAC in Kansas City, Kansas. This happened during heavy rains. It still happens to my folks who live in rural Kansas. Here in Richmond, Virginia, I have seen voltage as low as 109 VAC. My UPS beeps regularly as voltage often dips below its setpoint. The actual 'specification' is 110 VAC. Below 110 VAC the current draw is too high for most house type appliances and this will damage them over time.

I always suggest that everyone use an AVR type power supply on their home desktops and Internet routers. Brown-outs are bigger trouble makers, over time, than outright power loss. Laptops are not as susceptible due to the battery. Many laptop power supplies, such as my Serval P3, work with 100 to 240 VAC.

The next time your computer freezes, restarts, or your Internet connection suddenly stops, go test your supply voltage if you have a volt meter. You might be unpleasantly surprised.

---

### Post by corey.abshire on 2009-08-28
> **jdmelton said:**
> corey,

Most of the time we do not think about it, but our power supply can be a real problem. This does not sound like it is your only problem, yet it can be a part of it. I used to live in Charleston, South Carolina in the 1980's and our voltage would sometimes drop to 104 VAC. That is bad. Some of the reasons were old power lines, manual voltage controls, and inattentive staff (my opinion). At the time I was working for Charelston Naval Shipyard and we monitored voltage, so that is how I became aware of this problem.

I also experienced drops to 109 VAC in Kansas City, Kansas. This happened during heavy rains. It still happens to my folks who live in rural Kansas. Here in Richmond, Virginia, I have seen voltage as low as 109 VAC. My UPS beeps regularly as voltage often dips below its setpoint. The actual 'specification' is 110 VAC. Below 110 VAC the current draw is too high for most house type appliances and this will damage them over time.

I always suggest that everyone use an AVR type power supply on their home desktops and Internet routers. Brown-outs are bigger trouble makers, over time, than outright power loss. Laptops are not as susceptible due to the battery. Many laptop power supplies, such as my Serval P3, work with 100 to 240 VAC.

The next time your computer freezes, restarts, or your Internet connection suddenly stops, go test your supply voltage if you have a volt meter. You might be unpleasantly surprised.

I had seen this a few times on some of my previous computers over the years as well. Now that I have it behind the AVR / UPS, that cause should be eliminated for me.

And so, it crashed again today, even behind the UPS. Total uptime was just under 36 hours. It was running fine this morning since the last uptime I posted, but when I came home from lunch it was froze up. I had to hold the power down for a few seconds to force it to turn off and then turn it back on. I noted the time on the system clock in the panel at the top said 11:25 am, but it was actually 12:08 pm. Just wanted to point this out in case anyone has a look at the logs.

So, my logs are attached. Anyone have any ideas what I can do next to continue troubleshooting?

Thanks. - corey

---

### Post by corey.abshire on 2009-08-28
One thing I have noticed in a few of the logs just before a crash is something like this:

Aug 28 07:11:45 system76-pc -- MARK --
Aug 28 07:31:45 system76-pc -- MARK --
Aug 28 07:43:39 system76-pc syslogd 1.5.0#5ubuntu3: restart.
Aug 28 08:11:45 system76-pc -- MARK --
Aug 28 08:31:45 system76-pc -- MARK --
Aug 28 08:51:45 system76-pc -- MARK --
Aug 28 09:11:45 system76-pc -- MARK --
Aug 28 09:31:45 system76-pc -- MARK --
Aug 28 09:45:07 system76-pc kernel: [125630.418617] ath5k phy0: unsupported jumbo
Aug 28 10:11:45 system76-pc -- MARK --
Aug 28 10:31:45 system76-pc -- MARK --
Aug 28 10:51:45 system76-pc -- MARK --
Aug 28 11:05:39 system76-pc kernel: [130461.925605] ath5k phy0: unsupported jumbo
Aug 28 12:08:25 system76-pc syslogd 1.5.0#5ubuntu3: restart.
Aug 28 12:08:25 system76-pc kernel: Inspecting /boot/System.map-2.6.28-15-generic
Aug 28 12:08:25 system76-pc kernel: Cannot find map file.
Aug 28 12:08:25 system76-pc kernel: Loaded 56164 symbols from 45 modules.

There are two things I want to point out about this. One is the restart line at Aug 28 07:43:39. I'm not sure why thats there. I was using it this morning around that time, and it clearly did not restart then. I hadn't seen this in previous restarts.

The other thing is the  "ath5k phy0: unsupported". I had done some googling and learned that this is related to the wifi adapter, and that others had reported issues with this. Notice that the last entry of it before the real restart is at 11:05 am, but the system clock was hung at 11:25 am. So, if it is somehow related, its quite delayed. But I did see several articles online that pointed to that as a potential issue.

One of the recommendations was to switch to the madwifi adapter. I had tried this 2 or 3 days ago but wifi didn't work immediately, and I didn't feel it was a strong enough possibility to get it set up, so I switched back. Interested to know others thoughts on this line of reasoning. 

Thanks. - corey

---

### Post by corey.abshire on 2009-08-29
Another crash this morning apparently. I wasn't using it yet, it had already finished the reboot by the time I started using it. Logs attached.

---

### Post by corey.abshire on 2009-08-29
Another crash, just now, while I was in the middle of writing a document in OpenOffice. Logs attached.

---

### Post by thomasaaron on 2009-08-31
Neither set of logs shows the ath5k unsupported error. However, the first set shows...

> Aug 29 08:59:57 system76-pc dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 192.168.1.1 port 67
Aug 29 09:00:01 system76-pc /USR/SBIN/CRON[25346]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Aug 29 09:00:01 system76-pc /USR/SBIN/CRON[25347]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 29 09:00:07 system76-pc dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 192.168.1.1 port 67

...your wireless card trying to connect about 1 minute before the crash.

Can you try removing your wireless card and seeing if that stops the freezes?

---

### Post by corey.abshire on 2009-08-31
> **thomasaaron said:**
> Neither set of logs shows the ath5k unsupported error. However, the first set shows...



...your wireless card trying to connect about 1 minute before the crash.

Can you try removing your wireless card and seeing if that stops the freezes?

Yep, I had noticed that too. I'll have to go fork over some money for a network cable long enough to stretch across my living room, but yes, I'll try it if you think it might help. 

Also, just had another crash. This time I had tried disabling dual head, but looks like thats not it. Logs attached. 

Also, I plan on writing a small script tonight to run sar constantly in the background and write to alternating files of about 60 entries each of a 2 second polling interval. Hopefully this will tell us even more about whats going on just before a crash occurs. Maybe a spike in processor or io for some process. Please let me know your thoughts on this plan, and whether I should post the sar output here as well.

Thanks. - corey

---

### Post by jdb on 2009-08-31
> **corey.abshire said:**
> Yep, I had noticed that too. I'll have to go fork over some money for a network cable long enough to stretch across my living room, but yes, I'll try it if you think it might help. 

Also, just had another crash. This time I had tried disabling dual head, but looks like thats not it. Logs attached. 

Also, I plan on writing a small script tonight to run sar constantly in the background and write to alternating files of about 60 entries each of a 2 second polling interval. Hopefully this will tell us even more about whats going on just before a crash occurs. Maybe a spike in processor or io for some process. Please let me know your thoughts on this plan, and whether I should post the sar output here as well.

Thanks. - corey

I think sar gets its data from logs in /var/log/sa/

The logs are updated by cron entries, usually hourly.

You might want to tell cron to run the sysstat job more often.

jdb

---

### Post by corey.abshire on 2009-09-01
> **corey.abshire said:**
> Yep, I had noticed that too. I'll have to go fork over some money for a network cable long enough to stretch across my living room, but yes, I'll try it if you think it might help. 

Ok. I blacklisted ath5k and also physically removed the card (logs attached showing no ath5k in prior 2 restarts). Will report back whether it has an impact soon. Thanks. - corey

---

### Post by corey.abshire on 2009-09-01
Another crash, with ath5k blacklisted and wifi card physically removed.  Logs attached. 

Also, I had sar running as mentioned earlier. I didn't see anything out of the ordinary in it so I turned it back off since it was causing a bunch of noise to be generated in the logs. 

So, not sure where to look next. 

This sucks. This machine has crashed around once a day ever since I've had it. I've had several linux boxes before this and none of them did this. I can see several other threads related to frequent random crashes in the System76 forum - is this a common thing with System76 machines? Does anyone have any data as to how prevalent this issue is, particularly with Wild Dogs? 

Thanks. - corey

---

### Post by corey.abshire on 2009-09-01
Is it worth investigating whether this is some sort of watchdog failure?

corey@system76-pc:~/projects/nocrash/sar$ ps -ef | grep watchdog
root         5     2  0 21:03 ?        00:00:00 [watchdog/0]
root         8     2  0 21:03 ?        00:00:00 [watchdog/1]
root        11     2  0 21:03 ?        00:00:00 [watchdog/2]
root        14     2  0 21:03 ?        00:00:00 [watchdog/3]

I can see 4 watchdogs running right now. I'm assuming there's one process per CPU, but can anyone confirm that's how it works?

Since I was using my machine the last time it crashed, and it didn't appear to have anything wrong with it, it just restarted for no reason, one theory here could be that for some reason the process that is supposed to be writing to /dev/watchdog all the sudden decides to not do that any more, and so the kernel decides its time to restart.

Maybe something is causing watchdog to stop writing, or maybe the process itself just fails. Not sure, need some help on that.

Also, I tried to find /etc/watchdog.conf to see how its configured, and tried to check the man for watchdog from within my terminal but no luck on either front. Anyone have any idea how its configured on the Wild Dog? Also, I read something about hardware watchdogs - anyone know if the Wild Dog has one?

Thanks. - corey

---

### Post by corey.abshire on 2009-09-01
Found this in the logs:

[   24.681259] iTCO_vendor_support: vendor-support=0
[   24.682225] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   24.682306] iTCO_wdt: Found a ICH10R TCO device (Version=2, TCOBASE=0x0460)
[   24.682349] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)

So apparently it is a hardware watchdog. 

Still searching for clues on how exactly it works and whether it could be an issue.

---

### Post by thomasaaron on 2009-09-02
Cory,

We have this problem on about five Wild Dogs (out of who knows how many hundreds out there). The problem is, so far I've not been able to discover a common link. All of the logs are substantially different.

So, it doesn't *appear* to be a *common* problem. 

Also, it doesn't appear that you have just one thing going on, which further complicates figuring it out. For example, in one of your previous logs, you had this...

GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 

...just about the time of the crash. I'm not sure if that's the issue, but I've definitely seen in in connection with freezes before.

Unfortunately, it's not in your most recent log.

Would you like for us to bring your system in and have a look? I'm happy to do so. The only other thing that comes to mind is re-imaging. But who wants that hassle?

---

### Post by corey.abshire on 2009-09-02
> **thomasaaron said:**
> Cory,

We have this problem on about five Wild Dogs (out of who knows how many hundreds out there). The problem is, so far I've not been able to discover a common link. All of the logs are substantially different.

So, it doesn't *appear* to be a *common* problem. 

Also, it doesn't appear that you have just one thing going on, which further complicates figuring it out. For example, in one of your previous logs, you had this...

GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 

...just about the time of the crash. I'm not sure if that's the issue, but I've definitely seen in in connection with freezes before.

Unfortunately, it's not in your most recent log.

Would you like for us to bring your system in and have a look? I'm happy to do so. The only other thing that comes to mind is re-imaging. But who wants that hassle?

I'd certainly be willing to consider letting you have a look if you think that will help. I would even be willing to consider reimaging if I had a firmer understanding of what that could help (seems like the software would just get itself back into the same state its in right now). 

I need to leave right now to go out of town for a few days, and will give it some thought while I'm away. I'll let you know when I get back. If you or anyone else there has any other things for me to try before shipping it back or reimaging please go ahead and post it in the meantime. Also, thanks again for your help. - corey

---

### Post by corey.abshire on 2009-09-08
> **corey.abshire said:**
> I'd certainly be willing to consider letting you have a look if you think that will help. I would even be willing to consider reimaging if I had a firmer understanding of what that could help (seems like the software would just get itself back into the same state its in right now). 

I need to leave right now to go out of town for a few days, and will give it some thought while I'm away. I'll let you know when I get back. If you or anyone else there has any other things for me to try before shipping it back or reimaging please go ahead and post it in the meantime. Also, thanks again for your help. - corey

Hi Tom - I'm back now, and I have thought of a few questions and concerns about your offer:

1. Cost

Would you anticipate there being any cost to me as part of the fix, or would this be covered under the warranty. Also, who pays for shipping?

2. Shipping

As mentioned above, who pays? Also, due to the other shipping issues we've seen on the forum, I would definitely be wanting insurance both ways. Who pays for that?

Also, I have already discarded my original packing material. Would system76 be sending empty material for me to repack, or should I take it for instance to a UPS store for packing.

3. Timing

How long do you anticipate having my computer after it arrives? My fear hear is sending it off and having it gone for months with minimal communication.

4. Loaner

Is system76 prepared to send a replacement, equivalent, Wild Dog for me to use in the interim? This would make it easier to cope with not having it hear for a while. Also, we could reuse the shipping materials back and forth.

5. Methodology

What else do you plan on testing that I can't test here? For instance, are hardware issues suspected to any degree. If so, would you be making any such replacements as part of the warranty, and would you be in communication with me before doing so.

-

Thanks again for the offer. I look forward to you're response.

- corey

---

### Post by thomasaaron on 2009-09-08
Hi, Corey.

Have you gotten any freezes using the usb keyboard I sent and a usb mouse (i.e. no wireless?)

Have you checked to see if you get freezes without using gnome-do?

I would like to have both of those verified before bringing the computer in.

> 1. Cost

Would you anticipate there being any cost to me as part of the fix, or would this be covered under the warranty. Also, who pays for shipping?


No, you're still under warranty. Unless there is user damage.

> 2. Shipping

As mentioned above, who pays? Also, due to the other shipping issues we've seen on the forum, I would definitely be wanting insurance both ways. Who pays for that?

Also, I have already discarded my original packing material. Would system76 be sending empty material for me to repack, or should I take it for instance to a UPS store for packing.

We would pay for shipping, and we always insure packages. However, insurance actually paying up is usually dependent on proper packing. We do not provide packing materials, but we will provide detailed packing instructions.

> 3. Timing

How long do you anticipate having my computer after it arrives? My fear hear is sending it off and having it gone for months with minimal communication.

It would probably be more like a week or two.

> 4. Loaner

Is system76 prepared to send a replacement, equivalent, Wild Dog for me to use in the interim? This would make it easier to cope with not having it hear for a while. Also, we could reuse the shipping materials back and forth.

We don't provide loaners.

> 5. Methodology

What else do you plan on testing that I can't test here? For instance, are hardware issues suspected to any degree. If so, would you be making any such replacements as part of the warranty, and would you be in communication with me before doing so.

First we have to reproduce the problem. In your case it should be pretty easy based on how often it has occured during the course of this thread.

Most likely re-imaging the machine and installing the drivers from the ppa would be the first line of attack. If that doesn't fix the problem, it most likely is hardware.

Then, we'd start swapping things out: power supply, graphics card, cpu, motherboard, etc...

Any hardware replacements would be covered under warranty, unless they were deemed to be user-inflicted damage.

---

### Post by corey.abshire on 2009-09-08
I had a crash just now. Logs attached.

> **thomasaaron said:**
> Have you gotten any freezes using the usb keyboard I sent and a usb mouse (i.e. no wireless?)

I wasn't aware you sent a USB (non-wireless) keyboard. I have not received it yet if you have. I don't have one to try unless I go buy one or get the one you've sent. Can you please send a tracking number via email?

I already have a USB (non-wireless) mouse I can try. I can go ahead and start using that instead if you want me to test that before I get the keyboard.

> **thomasaaron said:**
> Have you checked to see if you get freezes without using gnome-do?

I don't have that program installed at all (just confirmed) and wasn't even aware of it until you mentioned it here.

> **thomasaaron said:**
> I would like to have both of those verified before bringing the computer in.

Will do, as soon as I get the keyboard.

> **thomasaaron said:**
> First we have to reproduce the problem. In your case it should be pretty easy based on how often it has occured during the course of this thread.

Most likely re-imaging the machine and installing the drivers from the ppa would be the first line of attack. If that doesn't fix the problem, it most likely is hardware.

If re-imaging is first line of attack, I guess I might as well go ahead and try that here. It would lead to a shorter turn-around time for me if it works and less costs for you. If changing the mouse/keyboard doesn't help I'll try it out. If there's any special way you want me to do it, and in particular, if there's anything you want me to make sure I *don't* install, please let me know.

> **thomasaaron said:**
> Then, we'd start swapping things out: power supply, graphics card, cpu, motherboard, etc...

Ok. If the above two things don't work lets go for it and you can swap out as much as is necessary to find and resolve the issue.

Of course, you'll be able to repeat the reimage, if you want, once you get it there, but if that's going to fix it I'd prefer to avoid sending it in.

If you have any concerns or suggestions about this please let me know.

Thanks. - corey

---

### Post by thomasaaron on 2009-09-09
> I wasn't aware you sent a USB (non-wireless) keyboard. I have not received it yet if you have. I don't have one to try unless I go buy one or get the one you've sent. Can you please send a tracking number via email?

I didn't. I'm sorry, but I got you mixed up with Ed.Corcoran (he has the other wild dog post). It's getting hard to keep it all straight! At any rate, I sent him my only extra keyboard. If you can borrow one, though, it probably wouldn't hurt to eliminate wireless devices for testing. There is a fair chance they are playing a part in his issue, but it may not have any bearing on yours.

> 
I don't have that program installed at all (just confirmed) and wasn't even aware of it until you mentioned it here.

Yeah, scratch that one.

Restore instructions are here...

> You can download a CD image for Ubuntu here...
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
...I recommend using 9.04 64-bit.

Once you've downloaded the CD image, you will need to burn it to a CD. However, it must be burned as an *image* and not as a *data * CD. Otherwise, it will not be bootable. Instructions for this vary based on which operating system you are using to burn the CD. Instructions for various operating systems are here.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Here are instructions for re-imaging your machine...
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)
...including instructions for downloading, installing and running your System76 driver.


---

### Post by corey.abshire on 2009-09-09
I tried to download the system 76 driver but it says:
-

**Forbidden**

 You don't have permission to access /repositories/ on this server.




-

I tried both just following the links you sent, and again after logging in to the system76.com website.

---

### Post by thomasaaron on 2009-09-09
Please stand by.

Our web server was updated and the permissions got hosed on the repositories. It should be up soon.

---

### Post by corey.abshire on 2009-09-09
> **thomasaaron said:**
> Please stand by.

Our web server was updated and the permissions got hosed on the repositories. It should be up soon.

Ok. I've reimaged the machine completely based on the instructions. I'll keep it like this for a while and see if it crashes like before I install anything else. Will let you know how it goes.

---

### Post by corey.abshire on 2009-09-10
> **corey.abshire said:**
> Ok. I've reimaged the machine completely based on the instructions. I'll keep it like this for a while and see if it crashes like before I install anything else. Will let you know how it goes.

24 hours and no crashes...

corey@system76:~$ uptime
 19:11:01 up 1 day, 3 min,  6 users,  load average: 0.18, 0.14, 0.10

Lets see if it can make it to 48.

---

### Post by corey.abshire on 2009-09-10
> **corey.abshire said:**
> 24 hours and no crashes...

corey@system76:~$ uptime
 19:11:01 up 1 day, 3 min,  6 users,  load average: 0.18, 0.14, 0.10

Lets see if it can make it to 48.

Ok, kind of had a crash just now. 

I say kind of because it didn't crash like it was doing before. I had plugged in that same sandisk that was mentioned earlier in the thread and was copying a huge file to it. While it was copying I went back to watch some TV. When I came back the screensaver was on. When I hit a key to get back to the screen, it showed me the desktop and all the windows, but they were frozen. The mouse would move, but I couldn't select any windows or move them around. It was weird. 

Anyway, I tried unplugging the sandisk and it didn't unfreeze. So, I switched to a terminal with CTRL-ALT-F1 and that worked. And I tried to kill some programs (firefox, etc...) that way but it didn't seem to help. I switched back to the desktop and at that point it was pretty much completely locked up.

So, I had to power cycle it to get it back up.

Unforetunately it doesn't seem like the same behaviour I saw before, but also I don't feel it was up long enough to confirm that the same behaviour won't still exist if it had stayed up longer without this issue. 

So for now I guess I'll try to leave it completely alone and not even copy any files to my sandisk. 

It sucks though because here I've got this sweet Wild Dog sitting here and its basically worthless to me right now. Ugh.

Keep in mind the machine is freshly reimaged with absolutely nothing installed extra aside from the updates, system76 driver, and enabling the ATI driver, as instructed on the system76 restore page.

Logs attached from the crash. Note the spurious restart in the log (it didn't actually restart at that time, again, not sure why it gets there):

Sep 10 08:07:24 system76 syslogd 1.5.0#5ubuntu3: restart.

and the Xorg segault at 21:26:55 just before the crash event:

Sep 10 21:26:55 system76 kernel: [94741.923255] Xorg[6461]: segfault at 290 ip 00007f55d9284345 sp 00007fffe555db90 error 4 in fglrx_drv.so[7f55d9175000+3f6000]

If anyone has any other advice or words of encouragement for dealing with this bummer of a situation please send.

I'm tempted to just put my system76 up on ebay or something and go for something else at this point. Not happy.

- corey

---

### Post by corey.abshire on 2009-09-10
> **thomasaaron said:**
> Cory, your Wild Dog has an ATI card.

We have seen some circumstances where the current ATI driver in Ubuntu's repositories acts somewhat lethargic. It may also be causing some freezing as well. There are new drivers that perform far better. To give it a try run the following commands in your terminal one at a time - they are rather long commands - you can cut and paste them (Applications > Accessories > Terminal)

echo deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

echo deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B22AB97AF1CDFA9 && sudo apt-get update

sudo apt-get upgrade

Should I go ahead and try this again due to the Xorg issue I just experienced, or should I give it more time to crash again before then?

---

### Post by thomasaaron on 2009-09-11
Yes, that last freeze is definitely ati driver related. Install the ppa drivers.

---

### Post by corey.abshire on 2009-09-12
> **thomasaaron said:**
> Yes, that last freeze is definitely ati driver related. Install the ppa drivers.

Ok, installing now. Looks like it stayed up for a pretty long time before I'm installing:

corey@system76:~/Projects/SPP/src$ uptime
 11:27:31 up 1 day,  8:53,  5 users,  load average: 0.02, 0.01, 0.00

Not sure I can recall it making it more than 24 hours before. Hopefully it will continue to do so after I install the ppa drivers.

---

### Post by corey.abshire on 2009-09-12
> **corey.abshire said:**
> Logs attached from the crash. Note the spurious restart in the log (it didn't actually restart at that time, again, not sure why it gets there):

Sep 10 08:07:24 system76 syslogd 1.5.0#5ubuntu3: restart.

Here's one thing that's odd. Looks like there is another spurious restart entry in the log, even though it did not restart. What could be causing that? I usually see such an entry in there before a real crash, so I'm thinking if I wasn't going to restart here in a few due to reinstalling the ppa drivers that I would see a crash, since I see this log entry again.

Sep 12 06:54:43 system76 -- MARK --
Sep 12 07:14:43 system76 -- MARK --
Sep 12 07:34:43 system76 -- MARK --
Sep 12 07:43:27 system76 syslogd 1.5.0#5ubuntu3: restart.
Sep 12 07:54:43 system76 -- MARK --
Sep 12 08:14:43 system76 -- MARK --
Sep 12 08:34:43 system76 -- MARK --

Are those entries normal for the Wild Dog, or is this an indication of some problem specific to my machine?

Logs attached.

---

### Post by corey.abshire on 2009-09-12
> **corey.abshire said:**
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B22AB97AF1CDFA9 && sudo apt-get update

Ok, ppa drivers are installed, and the machine is restarted. The results of running that last command are attached.

---

### Post by corey.abshire on 2009-09-13
> **corey.abshire said:**
> Ok, ppa drivers are installed, and the machine is restarted. The results of running that last command are attached.

Over 24 hours and no crash...

corey@system76:~/Projects/SPP/src$ uptime
 17:18:08 up 1 day,  5:33,  4 users,  load average: 0.04, 0.08, 0.08

---

### Post by thomasaaron on 2009-09-14
Sweet. Keep me posted.

---

### Post by corey.abshire on 2009-09-14
> **thomasaaron said:**
> Sweet. Keep me posted.

Definitely. Just hit 48.

corey@system76:~$ uptime
 12:17:02 up 2 days, 32 min,  4 users,  load average: 0.11, 0.16, 0.10

Very cool.

So, assuming this has removed the crashes, what are my next steps?

In particular:


[LIST=1]
[*]How long should we wait before installing the rest of the software? It is still a default installation + upgrades + system76 driver + ubuntu-x-swat driver upgrades. Is 36 hours enough, or should we try to go a whole week?
[*]What procedure should we use to install the remainder of the software to ensure the crashing does not return?
[*]Assuming this eliminates the doubt of a hardware related issue, is there a desire to restore the full backup I took before reimaging to try and diagnose what went wrong in software; or should I continuing rebuilding from the default installation and just restore my documents as required from the home directory of my prior backup?
[/LIST]

Thanks again. I'm crossing my fingers and hoping that this has restored the stability I am looking forward to with this system.

---

### Post by thomasaaron on 2009-09-14
I'd let it run a little longer.

Then start re-installing as you need things. A couple of programs at a time should be no problem. If problems start back up, we'll have a record of what was done, and we can work it from there.

---

### Post by corey.abshire on 2009-09-15
> **thomasaaron said:**
> I'd let it run a little longer.

Then start re-installing as you need things. A couple of programs at a time should be no problem. If problems start back up, we'll have a record of what was done, and we can work it from there.

72 hours and still good.

corey@system76:~$ uptime
 12:00:50 up 3 days, 16 min,  3 users,  load average: 0.49, 0.26, 0.13

I could get used to this! :)

Is it ok in your mind to go ahead and restore a few things, or should we go for more?

Do I need to manually maintain a log of what I install, or is there something in the system I'm unaware of that will do it for me?

---

### Post by thomasaaron on 2009-09-15
It seems pretty stable. 

Keep a manual log, and give each app / activity plenty of opportunity to hose something.

---

### Post by corey.abshire on 2009-09-15
> **thomasaaron said:**
> It seems pretty stable. 

Keep a manual log, and give each app / activity plenty of opportunity to hose something.

Ok, will do. Thanks for your help on this.

---

### Post by corey.abshire on 2009-09-17
> **corey.abshire said:**
> Ok, will do. Thanks for your help on this.
 
Looks like I had another crash while I was out this morning, around 1 hour ago. Logs are attached. 
 
I also found that synaptic does write a log for each action it takes. Its available in the menu in the Synaptic Package Manager application, and also available in the .synaptic directory under root. I made a tarball of all those files and attached them as well (fairly small). 
 
I also maintained a list manually of all the software I had installed during that first (and only, thus far) batch. Here is the list:
 
Adobe Flashplayer
Gstreamer ffmpeg video plugin
Gstreamer extra plugins
Project Management
R
Celestia (GNOME)
Stellarium
LaTeX
Emacs Snapshot (GTK)
ImageJ
QCaD
SBCL
 
And finally, here is a mapping of files in the synaptic logs to the programs listed above:
 
2009-09-11.021950.log             Initial update from Ubuntu (during reimage)            
2009-09-15.123946.log             Additional update from Ubuntu (regular update)            
2009-09-15.203213.log             Both Gstreamer packages listed.
2009-09-15.203250.log             Project Planner
2009-09-15.203338.log             Celestia (GNOME)
2009-09-15.203417.log             Stellarium
2009-09-15.203946.log             Emacs Snapshot
2009-09-15.204112.log             ImageJ
2009-09-15.204214.log             QCaD
2009-09-15.204915.log             SBCL
2009-09-15.205344.log             R
2009-09-15.210024.log             TeX
2009-09-15.214822.log             Sun JRE 6 (for ImageJ)
            
My estimate of the uptime at the time of the crash is around 39 hours (from around 10:00 PM on 9/15 to around 12:00 pm this morning, 9/17.
 
It exhibited the strange behaviour as before in the logs where there are a few spurious restart records that aren't accompanied by a real restart, followed a few hours later by a real crash/restart.
 
Most of my suspicion is around Adobe Flashplayer, since its likely the most unstable item in the list of applications I installed. I followed the instructions you posted previously to install it. Should I simply delete that file to go ahead and uninstall, or should I wait for another crash to confirm the behaviour is now reintroduced? Or do you have something else in mind?

---

### Post by thomasaaron on 2009-09-17
Well, those logs only show about a five hour period, and I don't see anything pointing to a reason for the crash.

There is no flash segfault.

Go ahead and post logs immediately after the next crash.

---

### Post by thomasaaron on 2009-09-17
Also, not sure if it is related, but I found this bug on the emacs snapshot version (which it looks like you have installed)...

[https://bugs.launchpad.net/ubuntu/+source/emacs22/+bug/231034](https://bugs.launchpad.net/ubuntu/+source/emacs22/+bug/231034)

Was emacs open when it crashed? If so, will it freeze with the repo version of emacs? Or if emacs isn't open?

---

### Post by corey.abshire on 2009-09-17
> **thomasaaron said:**
> Well, those logs only show about a five hour period, and I don't see anything pointing to a reason for the crash.
 
There is no flash segfault.
 
Go ahead and post logs immediately after the next crash.
 
How do you mean five hour period? There should be data in there from the last few days but for some reason I'm unable to check it from here. I'll check again when I get to the machine again.
 
Also, will post again after the next crash.

---

### Post by corey.abshire on 2009-09-17
> **thomasaaron said:**
> Also, not sure if it is related, but I found this bug on the emacs snapshot version (which it looks like you have installed)...
 
[https://bugs.launchpad.net/ubuntu/+source/emacs22/+bug/231034](https://bugs.launchpad.net/ubuntu/+source/emacs22/+bug/231034)
 
Was emacs open when it crashed? If so, will it freeze with the repo version of emacs? Or if emacs isn't open?
 
Yes emacs was running, and it is pretty much always running on my machine. I have emacs-snapshot on there now, and also on there before the reimage near the last few weeks. Before that I had emacs-22 on there at first (this is before the reimage) almost immediately after I first turned on the machine after receiving it from you guys.
 
I suppose its possible it could be an emacs issue, but the behaviour I experience doesn't seem to match the description there. 
 
Should I wait for another crash before trying uninstalling it to see if we can confirm that's causing it?
 
Also, regarding the idea I posted earlier, could something in the description of the bug at the link you posted be linked to the watchdog?

---

### Post by thomasaaron on 2009-09-17
> Should I wait for another crash before trying uninstalling it to see if we can confirm that's causing it?

Sure, let's get one more set of crash logs before uninstalling it.
Then another if it crashes again. If it crashes after uninstalling it, just re-install it and enjoy. We'll keep digging.

> Also, regarding the idea I posted earlier, could something in the description of the bug at the link you posted be linked to the watchdog?

Not that I'm aware of.

---

### Post by jdb on 2009-09-17
> **corey.abshire said:**
> 
SBCL
 


I guess I'm not the only Lisp nut on this forum :)

jdb

---

### Post by corey.abshire on 2009-09-17
> **jdb said:**
> I guess I'm not the only Lisp nut on this forum :)

jdb


:)  Nope, and apparently I'm not either.

---

### Post by corey.abshire on 2009-09-17
> **thomasaaron said:**
> Sure, let's get one more set of crash logs before uninstalling it.
Then another if it crashes again. If it crashes after uninstalling it, just re-install it and enjoy. We'll keep digging.

Ok, will do.

---

### Post by corey.abshire on 2009-09-18
> **corey.abshire said:**
> Ok, will do.
I had another crash just now. Logs attached. 

Also, I figured out why you could only see a few hours last time. The system had already rolled messages over to messages.0, but the system76 utility only captures messages. When I was looking, I was clicking on the messages.0 without realizing you wouldn't be able to see that. So I copied messages.0 into that tmp system76 directory and recreated the archive with that as well.

Like before, there weren't any segfaults or other such entries before the crash. It just froze up and restarted without warning. Emacs was running, as was a few other programs such as OpenOffice and Firefox (with flashplayer).

Any recommendations on what to try next?

---

### Post by thomasaaron on 2009-09-18
Let's try it without emacs.

I'm getting ready to send out an email to all of my Wild-dog-issues cases. We'll probably move this to an email issue, as I need to compare several Wild Dogs.

---

### Post by corey.abshire on 2009-09-18
> **thomasaaron said:**
> Let's try it without emacs.

I'm getting ready to send out an email to all of my Wild-dog-issues cases. We'll probably move this to an email issue, as I need to compare several Wild Dogs.

Ok. 

Just to clarify, should I completely uninstall emacs-snapshot and restart, or just restart and not open it?

---

### Post by thomasaaron on 2009-09-18
Just don't open it. That should be sufficient.

I'm experimenting with emacs on my end to.

---

### Post by corey.abshire on 2009-09-18
> **thomasaaron said:**
> Just don't open it. That should be sufficient.

I'm experimenting with emacs on my end to.

Ok. I went ahead and deactivated the menu item just to make sure I don't accidentally click it out of habit, and then restarted the machine. I'll let you know if I see a crash.

---

### Post by corey.abshire on 2009-09-27
> **thomasaaron said:**
> Let's try it without emacs.

I'm getting ready to send out an email to all of my Wild-dog-issues cases. We'll probably move this to an email issue, as I need to compare several Wild Dogs.

Just an update for anyone else following this thread. I am still having the issue. We're still trying to solve it over email. If we come up with a solution, it will be posted here. If it goes on for a while, I'll post updates.

---

### Post by val67 on 2009-09-27
Thanks Corey,

Are you aware of other Wild Dog users experiencing the same problem, or is it just you?

Val.

---

### Post by corey.abshire on 2009-09-27
> **val67 said:**
> Thanks Corey,

Are you aware of other Wild Dog users experiencing the same problem, or is it just you?

Val.

Hi Val. I have been told there are at least 4 or 5 others that system76 is aware of, and have seen at least 2 others on this forum. Tom Aaron from system76 has been collecting responses to a series of questions he sent us via email over the past week and should be getting back with us shortly to share the results. Having said that, I don't think its clear now whether the crashes on each of the 4 or 5 machines have the same cause, or whether this is potentially a hidden issue on other Wild Dogs that users either aren't triggering or aren't reporting. - corey

---

### Post by val67 on 2009-09-27
> **corey.abshire said:**
> Hi Val. I have been told there are at least 4 or 5 others that system76 is aware of, and have seen at least 2 others on this forum. Tom Aaron from system76 has been collecting responses to a series of questions he sent us via email over the past week and should be getting back with us shortly to share the results. Having said that, I don't think its clear now whether the crashes on each of the 4 or 5 machines have the same cause, or whether this is potentially a hidden issue on other Wild Dogs that users either aren't triggering or aren't reporting. - corey

Thanks. I just wanted to make sure if I ordered a Wild Dog it would not have the same problems, but from your response this might not be the case.

---

### Post by jbelmonte on 2009-09-28
> **corey.abshire said:**
> Hi Val. I have been told there are at least 4 or 5 others that system76 is aware of, and have seen at least 2 others on this forum. Tom Aaron from system76 has been collecting responses to a series of questions he sent us via email over the past week and should be getting back with us shortly to share the results. Having said that, I don't think its clear now whether the crashes on each of the 4 or 5 machines have the same cause, or whether this is potentially a hidden issue on other Wild Dogs that users either aren't triggering or aren't reporting. - corey

Well, the Wild Dog we received at the end of January 2009 has not experienced any crashes. My son uses it for standard stuff such as working with Open Office documents, playing music, watching YouTube videos, etc. He also installed and uses Windows XP in VirtualBox. The system came with Intrepid, and he decided not to move to Jaunty, so that may mean something. His configuration is:

*Graphics : 1 GB ATI Radeon 4850 PCI-Express x16 GDDR3 (2 x DVI, S-Video, DVI to HDMI, DVI to VGA)
*Hard Drive : 1 TB SATA II 300Mbps - 7200 rpm 32 MB Buffer
*LCD Monitor : 26” KDS Widescreen LCD (1920 x 1200)
*Memory : 8 GB - 4 x 2 GB - DDR 2 - 800 MHz
*Operating System : Ubuntu 8.10 (Intrepid Ibex) 64 Bit Linux
*Optical Drive : CD-RW / DVD-RW
*Processor : Quad Core Q9550 2.83 GHz FSB 1333 MHz L2 12 MB
*Speakers : 2.1 - Logitech X-230 - 2 Satellites, 1 Subwoofer
*Wireless : 802.11 bg

Good luck solving the crashing issue. I know how difficult it can be to find the cause sometimes.

---

### Post by corey.abshire on 2009-09-28
> **jbelmonte said:**
> Well, the Wild Dog we received at the end of January 2009 has not experienced any crashes. My son uses it for standard stuff such as working with Open Office documents, playing music, watching YouTube videos, etc. He also installed and uses Windows XP in VirtualBox. The system came with Intrepid, and he decided not to move to Jaunty, so that may mean something. His configuration is:
 
*Graphics : 1 GB ATI Radeon 4850 PCI-Express x16 GDDR3 (2 x DVI, S-Video, DVI to HDMI, DVI to VGA)
*Hard Drive : 1 TB SATA II 300Mbps - 7200 rpm 32 MB Buffer
*LCD Monitor : 26” KDS Widescreen LCD (1920 x 1200)
*Memory : 8 GB - 4 x 2 GB - DDR 2 - 800 MHz
*Operating System : Ubuntu 8.10 (Intrepid Ibex) 64 Bit Linux
*Optical Drive : CD-RW / DVD-RW
*Processor : Quad Core Q9550 2.83 GHz FSB 1333 MHz L2 12 MB
*Speakers : 2.1 - Logitech X-230 - 2 Satellites, 1 Subwoofer
*Wireless : 802.11 bg
 
Good luck solving the crashing issue. I know how difficult it can be to find the cause sometimes.
 
Thanks jbelmonte, that's interesting. That's exactly the same configuration as mine except for the O/S version. I wonder if this is somehow a Jaunty thing. I had thought about trying 8.04 LTS to see if that made a difference, but have been holding off on changing anything else until I hear back from Tom. Maybe I'll give this a shot if nothing else works. Thanks. - corey

---

### Post by corey.abshire on 2009-09-28
> **val67 said:**
> Thanks. I just wanted to make sure if I ordered a Wild Dog it would not have the same problems, but from your response this might not be the case.
 
YMMV
 
Tom seems convinced its constrained to just the 4 or 5 and I'm sure he would know better than me. Plus I think they have a 30 day money back guarentee, so if you get it and it does the same thing and you don't want to mess with it I guess you could just send it back before then.
 
Hopefully soon mine and the other folks that are having the issues machines won't be crashing any more either and then there won't be any doubt at all.

---

### Post by val67 on 2009-10-04
Hi Corey,

I was wondering if the crash problem has been sorted out.

Looking at some other threads pertaining the Wild Dog, to me it hints that the ATI card may be the culprit, but I may be wrong.

---

### Post by corey.abshire on 2009-10-04
> **val67 said:**
> Hi Corey,

I was wondering if the crash problem has been sorted out.

Looking at some other threads pertaining the Wild Dog, to me it hints that the ATI card may be the culprit, but I may be wrong.

Hi val67. No, unfortunately it hasn't progressed much at all since my last post. Its been crashing pretty regularly every 6 hours to 2 days as it was before, and I've been sending Tom the logs directly over email as soon as it does, as he requested. I've tried various combinations of not running various programs to try to narrow it down, but nothing that seems to directly correlate to the crashes.

I haven't heard back from Tom yet on the consolidated information. He had already confirmed in his first email requesting information 2 weeks ago that everyone who had the problem had an ATI card, but haven't received any further any information since then. I haven't gone out and bought an equivalent nvidia card yet to test out for myself whether that helps, as I believe since its still under warranty system76 should do that. Hope to hear back from Tom very soon on this.

---

### Post by val67 on 2009-10-04
I wonder why S76 is sticking to ATI cards, when the NVIDIA ones are better supported in Linux in general.

---

### Post by corey.abshire on 2009-10-04
> **val67 said:**
> I wonder why S76 is sticking to ATI cards, when the NVIDIA ones are better supported in Linux in general.

I seem to remember asking something to that effect shortly after I got my machine. I wanted to switch to the rt kernel to do musical things but it failed to start, miserably and violently. This was back around April or May when I first got it. I worked with Tom and basically we determined it was due to known issues with ATI drivers / cards. So I decided to stop trying and just stick with the regular kernel. I asked why they would sell the ATI driver if it has so many issues, and I believe the response was basically it came down to performance vs value. The ATI cards in their testing just yielded far better performance per $ spent. I'm paraphrasing of course, but Tom, if my memory is innaccurate, please correct me.

Beyond that though, I've noticed that for the Leopard, they use only nvidia. If they had offered the Leopard at the time I was purchasing a computer, I would have got that instead. I wanted the top of the line, and at that point the Wild Dog was the best they offered.

---

### Post by corey.abshire on 2009-10-10
Just wanted to post a brief update about this issue. Its still happening, but at least it seems like we're making progress. The latest idea is around the motherboard and memory. Kingston is shipping some new memory to me to try out to see if its something to do with that. There is reason to think it may be. Tom is working with Intel to ask about the motherboard. I'll post more after a while or whenever its resolved, whichever comes first.

---

### Post by TheBuzzSaw on 2009-10-13
I found another source of my crashes: my D-Link wireless card. I had one laying around doing nothing. I figured, why not? It'd be cool if my desktop had wireless capability. It did in fact work, but I found myself never using it (I have a wired connection anyway). So, I took it out, and my computer stopped freezing periodically.

This confirms my previous assessment (at least for my Wild Dog, anyway) that it is very sensitive to loose/improper hardware connections. First it was my DVD drive. Then it was my wireless card.

I haven't had a system lockup in quite some time. If you've tried everything else, I urge you to audit your hardware. ;)

---

### Post by corey.abshire on 2009-10-13
> **TheBuzzSaw said:**
> I found another source of my crashes: my D-Link wireless card. I had one laying around doing nothing. I figured, why not? It'd be cool if my desktop had wireless capability. It did in fact work, but I found myself never using it (I have a wired connection anyway). So, I took it out, and my computer stopped freezing periodically.

This confirms my previous assessment (at least for my Wild Dog, anyway) that it is very sensitive to loose/improper hardware connections. First it was my DVD drive. Then it was my wireless card.

I haven't had a system lockup in quite some time. If you've tried everything else, I urge you to audit your hardware. ;)

Thanks for the tip. Glad yours is working well now; it gives me hope for mine. I've gone over the connections internally 3 or 4 times now and pretty much ruled loose/improper connections out at this point, though when I first received the machine quite a bit was loose or not connected at all. Also, I bought mine with a D-Link WIFI card and had suspected that as well, but we ruled that out by completely removing it for a few days and the crashes continued. 

I'm feeling pretty hopeful about the memory replacement based on the responses I got from Kingston and the fact that changing the timing to their recommendation seems to have increased the frequency of the crashes. My RMA with them is on back order so it will be a few days before I'll know whether it helps or not, but once I get it I'll post back with an update.

---

### Post by SysKoll on 2009-10-13
Corey,

Did you experience further problems? I have intermittent crashes on a Wild Dog Performance and I was wondering how your problems got fixed.

---

### Post by corey.abshire on 2009-10-13
> **SysKoll said:**
> Corey,

Did you experience further problems? I have intermittent crashes on a Wild Dog Performance and I was wondering how your problems got fixed.

Hi SysKoll. Its not fixed yet, I still get frequent crashes, random reboots, freezes, etc... Please email support at nospam system76.com and let Tom know you are also having the issue. He is collecting information from everyone who's having the issue to help find patterns and hopefully a common solution. - corey

---

### Post by thomasaaron on 2009-10-14
I'm still waiting on Intel. I'll call them back today and see if they've figured anything out.

Meanwhile, we've sent one computer in for a mobo swap out to see if that fixes the issue.

---

### Post by corey.abshire on 2009-10-17
> **corey.abshire said:**
> Thanks for the tip. Glad yours is working well now; it gives me hope for mine. I've gone over the connections internally 3 or 4 times now and pretty much ruled loose/improper connections out at this point, though when I first received the machine quite a bit was loose or not connected at all. Also, I bought mine with a D-Link WIFI card and had suspected that as well, but we ruled that out by completely removing it for a few days and the crashes continued. 

I'm feeling pretty hopeful about the memory replacement based on the responses I got from Kingston and the fact that changing the timing to their recommendation seems to have increased the frequency of the crashes. My RMA with them is on back order so it will be a few days before I'll know whether it helps or not, but once I get it I'll post back with an update.

Just a quick update - I received the memory today several hours earlier and installed it immediately. Uptime right now:

 00:20:07 up  7:09,  4 users,  load average: 1.60, 2.12, 3.07

Hopefully this has fixed it, but it will take many more hours before I'm convinced.

---

### Post by corey.abshire on 2009-10-17
> **corey.abshire said:**
> Just a quick update - I received the memory today several hours earlier and installed it immediately. Uptime right now:

 00:20:07 up  7:09,  4 users,  load average: 1.60, 2.12, 3.07

Hopefully this has fixed it, but it will take many more hours before I'm convinced.

Well, 24 hours and still looks good.

corey@system76:~$ uptime
 17:26:21 up 1 day, 15 min,  5 users,  load average: 0.00, 0.01, 0.04

I've been using it a lot too - normally I think it would have failed by now.

---

### Post by unutbu on 2009-10-17
We're rooting for you, corey!

---

### Post by corey.abshire on 2009-10-18
> **unutbu said:**
> We're rooting for you, corey!

Thanks unutbu! I made it to 48 hours so far and still looking good.

$ uptime
 17:25:33 up 2 days, 15 min,  5 users,  load average: 0.96, 0.59, 0.32

I'm pretty hopeful at this point, and so started giving some thought to how long I should wait before I could celebrate and feel comfortable its really solved. I wrote a little perl script (attached) to compute uptimes based on all my logs over the past several weeks,  and created a control chart (also attached) based on that output. I found that while I'm well past the average (18 hours), to be statistically safe I have to make it past around 63 hours. 

Right now I'm thinking if I can make it a whole week I'd be feeling really comfortable calling it solved. I'll post one more once I make it past the 72 hour mark, and then hopefully another one after that when I've gone 7 days, and then at that point we can probably safely call it solved for my machine.

---

### Post by thomasaaron on 2009-10-19
I'd celebrate now! That way, if it crashes, you at least got to celebrate! :popcorn:

---

### Post by corey.abshire on 2009-10-19
> **thomasaaron said:**
> I'd celebrate now! That way, if it crashes, you at least got to celebrate! :popcorn:

Hey, maybe I should, I just made it passed 72 hours!

$ uptime
 17:38:15 up 3 days, 27 min,  2 users,  load average: 0.21, 0.32, 0.27

:popcorn:

For anyone else reading this, here's another post I found a while back that I found interesting:

[http://vip.asus.com/forum/view.aspx?id=20090208012832440&board_id=1&model=P5Q3&SLanguage=en-us&page=5](http://vip.asus.com/forum/view.aspx?id=20090208012832440&board_id=1&model=P5Q3&SLanguage=en-us&page=5)

A user by the name of koljaho wrote on 5/21/09 the following:
[INDENT]Got the ram changed from KVR1333D3N9/2G (9905403 - 011.**A02LF**) to KVR1333D3N9/2G (9905403 - 011.**A01LF**).

Everything is working fine now with auto mode. 
[/INDENT]I found that this is the exact same type of memory that I had in my Wild Dog. This post came up in a search for 9905403-011.**A02LF** that I ran after Kingston asked me to inspect the memory and report those numbers.

When they replaced my memory, I took note of the new numbers. Sure enough, the replacements they sent were also slightly different: the new ones are 9905403-011.**A03LF**.

Admittedly, this is not enough data to say conclusively that if its **A02LF** then it definitely has issues, but I felt that its an interesting enough coincidence that others may find it useful.

Also, I wanted to note that it wasn't like we hadn't suspected memory a few times already during our troubleshooting. I ran memtest+ once initially for over two passes and it went fine, and then again a few weeks later for several hours and it still came back fine (picture attached). Based on this, I'm not sure you want to rule memory completely out just because it happens to pass memtest+.

Anyway, I'll go ahead and leave my machine up for the rest of the 7 days to increase the comfort level that its truly resolved as I had said in my prior post, and will report back at that time. 

Also, I'll go ahead and take the opportunity to offer a great big **thanks** to everyone for your help, advice, and encouragement to help me reach this point. Thanks!

---

### Post by thomasaaron on 2009-10-20
Thanks.

I'm reporting this to our repair facility. They are working on one of the dawgs... changing the mobo.

I'll have them look into this as well.

---

### Post by thomasaaron on 2009-10-20
Corey, you emailed me the conversation and case information with Kingston. I hope you don't mind, but I passed all that info to one of our techs.

He is going to call Kingston and reference that case number to discuss the issue with them.

I'm not sure if he will hit a wall with Kingston... trying to access your case et al. If he does, I may need you to contact Kingston and give them approval.

I appreciate your help on this.

---

### Post by corey.abshire on 2009-10-21
> **thomasaaron said:**
> Corey, you emailed me the conversation and case information with Kingston. I hope you don't mind, but I passed all that info to one of our techs.

He is going to call Kingston and reference that case number to discuss the issue with them.

I'm not sure if he will hit a wall with Kingston... trying to access your case et al. If he does, I may need you to contact Kingston and give them approval.

I appreciate your help on this.

That's fine Tom. Will do if needed.

---

### Post by corey.abshire on 2009-10-23
Hi everyone. Just wanted to let you know that I made it the whole week.

$ uptime
 17:12:14 up 7 days, 1 min,  3 users,  load average: 0.31, 0.19, 0.39

Thanks again for your help and support.

- corey

---

### Post by val67 on 2009-10-23
Congrats!

So what was the real cause of the crashes?

Val.

---

### Post by corey.abshire on 2009-10-23
> **val67 said:**
> Congrats!

So what was the real cause of the crashes?

Val.

Faulty memory.

---

### Post by TheBuzzSaw on 2009-10-23
That's awesome. I'm glad it eventually got figured out! Just make sure your hardware is all behaving, and the freezing goes away! <3 Wild Dog

---

### Post by nanonils on 2010-02-04
I had essentially identical issues albeit somewhat less frequent (2/day to 1/week crash) with my WildDog but tried to sit them out hoping that the steady stream of updates would fix it. I had purchased mine in June 2009 (yes - I tried to fanboyish sit it out for that long). 

My four memory modules were:
3x
Kvr 133303n9/2g
Bvme1640944
Bt0905783252200873

1x
Bvme1640924
(otherwise identical numbers)

I hope that this will cure my box so I can again look my Mac obsessed colleagues in the eye and claim "rock solid linux"... 

Kingston customer service was great and they cross ship in two days (meaning I sent my memory when I receive theirs). Will post the outcome.

---

### Post by nanonils on 2010-02-19
I finally got my memory replacement from Kingston after a 2 week wait (partially due to two blizzards). I'm happy to report that there have been no crashes for the last 4 days of continued "on" while running some very memory heavy tasks. Also ran memtester for 28 cycles overnight and all is fine.

---

### Post by savantelite on 2010-06-28
I am confused. What do I need to do to make my Wild Dog stop freezing?

---

### Post by nanonils on 2010-06-28
Contact system76. They will give you a case number and phone number to contact Kingston who shipped defective memory that ended up in some system76 computers. Kingston will ship express ship you new memory (hopefully).

---

