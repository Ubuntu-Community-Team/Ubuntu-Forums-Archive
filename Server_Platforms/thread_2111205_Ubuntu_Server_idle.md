---
title: "Ubuntu Server idle"
date: 2013-02-01
forum: Server Platforms
---

### Post by albertone74 on 2013-02-01
Hi,
I am planning to move from Ubuntu Desktop to Ubuntu Server as I want to use my machine as a headless music server. I would appreciate if someone could tell me how I can make sure that after a certain time of inactivity (say 10-15 min) the server goes in stand-by to save energy and then, as soon as I play a song by using an app on my smartphone, the server wakes up again. I wouldn't know how to enable the idle mode from the terminal.
Many thanks in advance!):P

---

### Post by TheFu on 2013-02-01
I do not do this on my servers, since a delay can make potential clients leave, but in your case, with just you being involved, I'd start by searching the available man pages for power related commands:

$ **man -k power**

If you turn down the box too far, you might want to setup a WOL, Wake On Lan, method to wake up your system too, assuming your hardware supports it.  I use this with my XBMC machine every day.

Good luck!  I look forward to your solution!

---

### Post by albertone74 on 2013-02-01
> **TheFu said:**
> I do not do this on my servers, since a delay can make potential clients leave, but in your case, with just you being involved, I'd start by searching the available man pages for power related commands:
 
$ **man -k power**
 
If you turn down the box too far, you might want to setup a WOL, Wake On Lan, method to wake up your system too, assuming your hardware supports it. I use this with my XBMC machine every day.
 
Good luck! I look forward to your solution!
 
Hi,
First of all thanks for getting back to me.
My machine supports WOL. i checked that in the BIOS setting. Would you tell me how to setup a WOL under Ubuntu Server?
 
Just out of interest I am using the LogitechMediaServer on my machine.
 
Many thanks

---

### Post by tgalati4 on 2013-02-01
Just search "Wake LAN acpitool" on the forums for several tips.  Servers are designed to be responsive and run 24/7.  So putting a server to sleep kind of defeats the purpose.  You can set the disks to spin down, most modern green drives do that anyway.  You would have to install a script on each machine to send a magic packet to the server when you want to wake it up.  This wake up process can take 30 seconds or so because any housekeeping that is normally done during the idle time gets backed up and is now done on resume, slowing your system down, right when you want to use it.

There are ways to improve this maintenance scheduling, but you will have to spend time understanding how your server operates first.

---

### Post by albertone74 on 2013-02-03
> **tgalati4 said:**
> Just search "Wake LAN acpitool" on the forums for several tips.  Servers are designed to be responsive and run 24/7.  So putting a server to sleep kind of defeats the purpose.  You can set the disks to spin down, most modern green drives do that anyway.  You would have to install a script on each machine to send a magic packet to the server when you want to wake it up.  This wake up process can take 30 seconds or so because any housekeeping that is normally done during the idle time gets backed up and is now done on resume, slowing your system down, right when you want to use it.

There are ways to improve this maintenance scheduling, but you will have to spend time understanding how your server operates first.

Hi tgalati4,
Thanks to your feedback as well. I have been reading a lot about WOL and I found the following page

[http://askubuntu.com/questions/94754/how-to-enable-hibernation](http://askubuntu.com/questions/94754/how-to-enable-hibernation)

I would appreciate if you or thefu could tell me why I should add this override

sudoedit /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla

Also it is not fully clear the difference between suspend and hibernate. Am I write in saying that from an energy saving point of you it is better the hibernate option? I am not planning to run my music server 24/7. I am used to listen to my music mainly in the weekend and all I want to do is to suspend/hibernate my server only when I have to go out say for 2-3 hours and then when I get home I want to wake my server instead of switching on again.

Many thanks in advance.

Regards

---

### Post by tgalati4 on 2013-02-03
Hibernate copies RAM to swap then shuts down completely.  When you hit the power button, if a valid hibernation image is found on the swap partition, then it will boot with that, otherwise it will do a cold boot.  Unfortunately, it takes just as much time to boot a hibernate image as a cold boot, so it's really not useful.  That is why you need to enable it.  It's really only useful under certain circumstances.

Sleep and suspend are used interchangeably.  RAM is kept alive, but the processor stops and some parts of the PCI bus are kept alive (via acpitool) so you can use your mouse wiggle to wake, or keyboard power button to wake, or power button on the chassis.  Waking from sleep or Wake-on-LAN only takes 3 to 8 seconds.  That is what you want for your media server.

You can find WoL applications for your iPhone or Android device, or put a widget on each desktop/laptop in your household.

---

### Post by cariboo on 2013-02-03
I used [this howto]("http://wiki.xbmc.org/index.php?title=How-to:Set_up_Wake-On-Lan_(Ubuntu)"), to set up wol on my auxiliary server

---

### Post by TheFu on 2013-02-03
@tgalati4 explained the major aspects of suspend and hibernate fine, but there are reasons for each - like if you have 30 programs opened and modifying files in different projects, then both are very handy. You pick up exactly where you left off.

There are security concerns with both methods too, especially if you encrypt the HDD. Google will answer any questions about that.

If you'd like deeper knowledge on either, wikipedia is a good place to begin.

Suspend will use a little power, but probably less than $5/yr. Hibernate will use $0 in power.

You should also know that not all GPUs like it when you resume after hibernation or being suspending. My ATI will not reconnect audio over HDMI when waking up after suspend. There is no way to know if your setup will have the issue until you try it.

Should you use the hibernation override or not?  I can't say, but if you don't, then hibernation will not work on your system. Someone decided is was less useful, so no longer default according to that link.
[]("http://ubuntuforums.org/member.php?u=241895")

---

### Post by tgalati4 on 2013-02-03
Hibernate requires a swap disk or partition slightly larger than RAM.  Depending on your installation method, you may have no swap, small swap, or on a dual-boot system, a shared swap partition.  Any of these use cases will cause hiberation to fail.  So it's understandable to disable it unless your really need to use it.

---

### Post by albertone74 on 2013-02-05
**[B][COLOR="Black"][/COLOR]**[/B]> **tgalati4 said:**
> Hibernate copies RAM to swap then shuts down completely.  When you hit the power button, if a valid hibernation image is found on the swap partition, then it will boot with that, otherwise it will do a cold boot.  Unfortunately, it takes just as much time to boot a hibernate image as a cold boot, so it's really not useful.  That is why you need to enable it.  It's really only useful is certain circumstances.

Sleep and suspend are used interchangeably.  RAM is kept alive, but the processor stops and some parts of the PCI bus are kept alive (via acpitool) so you can use your mouse wiggle to wake, or keyboard power button to wake, or power button on the chassis.  Waking from sleep or Wake-on-LAN only takes 3 to 8 seconds.  That is what you want for your media server.

You can find WoL applications for your iPhone or Android device, or put a widget on each desktop/laptop in your household.

Hi,
Thanks a lot for you clarifications. I found them very helpful indeed!
At the moment I am using an app on my iPhone to wake my audio server up. So far I prefer the suspend option as it is quicker then hibernate. I would appreciate if you could explain to me the hybrid option. I found this definition:

"Hybrid-suspend is the process where the system does everything it needs to hibernate, suspends instead of shutting down. This means that your computer can wake up quicker than for normal hibernation if you do not run out of power, and you can resume even if you run out of power. s2both(8) is an hybrid-suspend implementation."

Now, what I would understand is that for a desktop (not laptop) this could better in my case as it would wake up quicker. I would like to have your opinion on that. Any disadvantage in using this option at all?
Many thanks

---

### Post by albertone74 on 2013-02-05
> **cariboo907 said:**
> I used [this howto]("http://wiki.xbmc.org/index.php?title=How-to:Set_up_Wake-On-Lan_(Ubuntu)"), to set up wol on my auxiliary server

Hi,
Thanks a lot for this link. I will read it to expand my knowledge about WOL!

---

### Post by albertone74 on 2013-02-05
> **TheFu said:**
> @tgalati4 explained the major aspects of suspend and hibernate fine, but there are reasons for each - like if you have 30 programs opened and modifying files in different projects, then both are very handy. You pick up exactly where you left off.

There are security concerns with both methods too, especially if you encrypt the HDD. Google will answer any questions about that.

If you'd like deeper knowledge on either, wikipedia is a good place to begin.

Suspend will use a little power, but probably less than $5/yr. Hibernate will use $0 in power.

You should also know that not all GPUs like it when you resume after hibernation or being suspending. My ATI will not reconnect audio over HDMI when waking up after suspend. There is no way to know if your setup will have the issue until you try it.

Should you use the hibernation override or not?  I can't say, but if you don't, then hibernation will not work on your system. Someone decided is was less useful, so no longer default according to that link.
[]("http://ubuntuforums.org/member.php?u=241895")

Hi,
Thanks a lot to you as well for all explanations. As I mentioned in my previous post I went for the suspend option and then for the override as well. I am also exploring the hybrid option..but I am not too sure about it. I would like to have your opinion as well on this matter.
Many thanks.

---

### Post by albertone74 on 2013-02-05
> **tgalati4 said:**
> Hibernate requires a swap disk or partition slightly larger than RAM.  Depending on your installation method, you may have no swap, small swap, or on a dual-boot system, a shared swap partition.  Any of these use cases will cause hiberation to fail.  So it's understandable to disable it unless your really need to use it.

I see now why this option has been disabled in the latest Ubuntu distros!:p

---

### Post by tgalati4 on 2013-02-05
I don't know what hybrid-suspend is, so I can't comment.  It looks like it's a newer suspend mode for newer machines.  To the OP, how many seconds does it take from hitting the "Wake" button on your iPhone to getting music to stream?  What kind of hardware are you running?

If you want to speed up resume, you can go through the resume scripts in /etc/acpi and comment out parts of it.  Some of the wake functions may not be needed with your hardware.  Be mindful of breakage and only make one change at a time.  You can usually shave a few seconds off of wake time.

---

### Post by TheFu on 2013-02-06
> **albertone74 said:**
> Hi,
Thanks a lot to you as well for all explanations. As I mentioned in my previous post I went for the suspend option and then for the override as well. I am also exploring the hybrid option..but I am not too sure about it. I would like to have your opinion as well on this matter.
Many thanks.

I don't know anything about hybrid.  That means it is probably new and filled with bugs that I don't want to deal with.  Give it a few years if you care about stability.  If your system only wakes up 20% - 80% of the time after being in hybrid mode, is that worth it?  It isn't for me.

I avoid experimental features.  Heck, I don't even bother with non-LTS Ubuntu releases anymore and haven't since 8.04.

---

### Post by albertone74 on 2013-02-08
Thanks all of you for your kind help on this matter. I found very helpful all your comments/clarifications. I am currently using the suspend option and I am quite happy with it. 
I might try the hybrid option in the weekend though:lolflag:
Thanks again. ):P

---

### Post by Praful Patel on 2014-01-19
Apologize to awaken somewhat old - closed thread. 

Hello, I am currently setting up my mediaserver. I was looking for energy efficiency and searched and got this thread that you created. Looks like exact same idea. Would you mind sharing what have you done and if that has worked for you? Thank you.

---

### Post by prasys on 2014-02-09
> **Praful Patel said:**
> Apologize to awaken somewhat old - closed thread. 

Hello, I am currently setting up my mediaserver. I was looking for energy efficiency and searched and got this thread that you created. Looks like exact same idea. Would you mind sharing what have you done and if that has worked for you? Thank you.

Let me share my setup a bit. I thought of helping it out. I've written a small script (you can use crontab to cron it say every 5 minutes) , that will check if anyone is connected and streaming service , if so leave the server on. Otherwise suspend it (put it on standby)

but first you need to enable Wake-On-Lan , which can be done by reading 

[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

Make sure you have it turned on in BIOS !



There are several ways to automate it  , automatically suspend when someone is not using services (the script below does that) , and to wake it up automatically when a client tries to do it (you need an Apple Router) or alternatively if you use DD-WRT , you may try the script

[http://www.dd-wrt.com/wiki/index.php/Useful_Scripts#Web_Server_Wake-up](http://www.dd-wrt.com/wiki/index.php/Useful_Scripts#Web_Server_Wake-up) , it's for web-server all you need to do is simply change the port :) 

Else you would have to get a tool/script to wake it up 


```

#!/bin/bash
#"Are you still there ?"


#check for idle samba , needed for XBMC when browsing for movies so that it does not doze off !
if [ `lsof -i :445 | grep ESTABLISHED | wc -l` != "0" ]
then
echo "Samba (SMB) has a user connected"
exit 0
fi

#check for webmin user here - if we have , ignore 
if [ `lsof -i :10000 | grep ESTABLISHED | wc -l` != "0" ]
then
echo "webmin"
exit 0
fi

if [ `lsof -i :631 | grep ESTABLISHED | wc -l` != "0" ]
then
echo "Print Share has a user connected"
exit 0
fi

#check if someone is reading/writing file in a samba
if [ `/usr/bin/smbstatus | grep DENY | wc -l` != "0" ]
then
echo "Samba (SMB) lock exists"
exit 0
fi

if [ `pgrep rsync | wc -l` != "0" ]
then
echo "Process relating to rsync exists"
exit 0
fi

if [ `pgrep utserver | wc -l` != "0" ]
then
echo "Process relating to utorrent exists"
exit 0
fi

if [ `pgrep rtorrent | wc -l` != "0" ]
then
echo "Process relating to rtorrent exists"
exit 0
fi


##special deluge script to determine if we have torrents running
if [ `pgrep deluged  | wc -l` != "0" ]
then
echo "Process relating to deluged  exists"
# let's check if we have actual torrents running or not

        if [ ! -f /home/torrent/foo.txt ]; then
        echo "deluged is currently downloading"
        exit 0
        fi
fi

### following takes a while

netstat -ute > .netstat

### now use output for various tests:

if [ `cat .netstat | grep ftp | wc -l` != "0" ]
then
echo "Got user on FTP"
exit 0
fi

if [ `cat .netstat | grep telnet | wc -l` != "0" ]
then
echo "Got user on telnet"
exit 0
fi

if [ `cat .netstat | grep :5900 | wc -l` != "0" ]
then
echo "Got user on VNC"
exit 0
fi

if [ `cat .netstat | grep ssh | wc -l` != "0" ]
then
echo "Got user on SSH"
exit 0
fi

echo "SUSPEND!!"
pm-suspend
```

> **tgalati4 said:**
> I don't know what hybrid-suspend is, so I can't comment.  It looks like it's a newer suspend mode for newer machines.  To the OP, how many seconds does it take from hitting the "Wake" button on your iPhone to getting music to stream?  What kind of hardware are you running?

What Hybrid-suspend does is that first it will do what hibernate does , and after that it will just put the PC to sleep/standby. So in an event of power failure , your data is still saved , and you are able to resume where the PC is left off !

---

