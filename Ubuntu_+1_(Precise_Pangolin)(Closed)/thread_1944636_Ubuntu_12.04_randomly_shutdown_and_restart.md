---
title: "Ubuntu 12.04 randomly shutdown and restart"
date: 2012-03-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Kegeg on 2012-03-21
I install the beta version of 12.04 and it randomly shutdown and restart by itself... I really don't know where to begin to fix this issue. 

Thank you

---

### Post by PhantomTurtle on 2012-03-21
Your going to have to provide a bit more info than that, like how to recreate it. I'm running 12.04 too and I have never had this problem.

---

### Post by HiImTye on 2012-03-21
probably have better luck in the [Ubuntu +1 (Precise Pangolin)]("http://ubuntuforums.org/forumdisplay.php?f=412") forum and with more detailed info[URL="http://ubuntuforums.org/forumdisplay.php?f=412"]
[/URL]

---

### Post by Andrew_P on 2012-03-21
> **Kegeg said:**
> I install the beta version of 12.04 and it randomly shutdown and restart by itself... I really don't know where to begin to fix this issue. 

Thank you

It would help if you describe your hardware.  Is it a laptop/portable or desktop/office system?  If it's an office system, do you have power management settings for a portable activated?  It's possible that the machine is simply going into sleep or hibernate mode based on settings you've selected.

---

### Post by oldos2er on 2012-03-21
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by Kegeg on 2012-03-23
> **Andrew_P said:**
> It would help if you describe your hardware.  Is it a laptop/portable or desktop/office system?  If it's an office system, do you have power management settings for a portable activated?  It's possible that the machine is simply going into sleep or hibernate mode based on settings you've selected.

I'm using a new Gateway NV57H13h Laptop running Ubuntu 12.04 (precise) 64-bit, Kernel Linux 3.2.0.20-generic,GNOME 3.3.92. The hardware is an Intel® Core™ i7-2670QM CPU @ 2.20GHz × 8, an NVIDIA GeForce GT 540M, 1GB VRAM with Optimus and CUDA. My power setting are not causing it to hibernate as I am working on the computer as it happens(it just did again and I had to rewrite this post...). Let me know what other kind of information you need.

Thank you

---

### Post by Kegeg on 2012-03-25
I don't know if there is command output you may need to find more about that but I'm quite lost in this...

---

### Post by AnrDaemon on 2012-03-26
At least, output from "uname -a" and "lsb_release -a" is required.

---

### Post by cariboo on 2012-03-26
Could it be an over-temp shut down?

---

### Post by Kegeg on 2012-03-26
> **cariboo907 said:**
> Could it be an over-temp shut down?

I don't think as my laptop isn't hot but maybe it's just not working right and maybe it is. Is there a way to monitor the temperature before a unexpected shutdown?

---

### Post by Kegeg on 2012-03-26
> **AnrDaemon said:**
> At least, output from "uname -a" and "lsb_release -a" is required.

```
uname -a

3.2.0-20-generic #32-Ubuntu SMP Thu Mar 22 02:22:46 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


lsb_release -a

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu precise (development branch)
Release:	12.04
Codename:	precise
```

---

### Post by VMC on 2012-03-26
Try looking at the log files "/var/log". Especially syslog, dmesg. See if any indication of failure.

---

### Post by cariboo on 2012-03-26
> **Kegeg said:**
> I don't think as my laptop isn't hot but maybe it's just not working right and maybe it is. Is there a way to monitor the temperature before a unexpected shutdown?

There is an indicator applet called indicator-sysmonitor available here:

[https://launchpad.net/indicator-sysmonitor](https://launchpad.net/indicator-sysmonitor)

---

### Post by mattgen88 on 2012-03-27
I'm actually having the same problem, so you're not alone.

intel core i7, nvidia 9800gt, using latest 12.04 as of time of posting. 

I can't seem to figure out what exactly is happening. Sometimes I just get kicked to the login screen, other times my mouse will move but nothing will respond to clicking, other times I get what appears to be corrupted video output with blinking pixels that change as I type, and finally other times my computer completely reboots. I've never had this sort of instability from an ubuntu beta build and I don't expect it to be in this state so close to release (and an LTS, nonetheless).

I'm hoping this bug gets fixed soon. I'm trying to tracedown what is causing it and have been going through my logs when it occurs. 

I unfortunately don't know much about the log outputs so it is difficult for me to discern what might be output corresponding to the crashing.

---

### Post by PhantomTurtle on 2012-03-27
> **mattgen88 said:**
> I'm actually having the same problem, so you're not alone.

intel core i7, nvidia 9800gt, using latest 12.04 as of time of posting. 

I can't seem to figure out what exactly is happening. Sometimes I just get kicked to the login screen, other times my mouse will move but nothing will respond to clicking, other times I get what appears to be corrupted video output with blinking pixels that change as I type, and finally other times my computer completely reboots. I've never had this sort of instability from an ubuntu beta build and I don't expect it to be in this state so close to release (and an LTS, nonetheless).

I'm hoping this bug gets fixed soon. I'm trying to tracedown what is causing it and have been going through my logs when it occurs. 

I unfortunately don't know much about the log outputs so it is difficult for me to discern what might be output corresponding to the crashing.

This is probably just a bug and will probably be fixed by the time of the release(it is still in beta 1 so far). Also if it is fixed then there probably is an update out.

---

### Post by ron_digital on 2012-03-27
> **PhantomTurtle said:**
> This is probably just a bug and will probably be fixed by the time of the release(it is still in beta 1 so far). Also if it is fixed then there probably is an update out.

This problem has been reported by several users, I googled and I only found questions and very little productive answers.

I have the exact same problem on the 11.10 64bit, even the screen flickering and mouse problem are the same, I've noticed the has to do with power device management, when I turn on the computer with power cord disconnected the error doesn't occur and everything runs fine on battery, but when i reconnect the power, it starts to randomly restart and became glitchy.

The only partial workaround I could found was related to a program called Jupiter, which helps the computer to better manage the power devices, you can find it on Synaptic Package Manager, so far the restars have been reduced a lot, but still happen every now and then.

I hope Ubuntu fix this bug before release the stable version of 12.04 and honestly I'm seriously considering a downgrade to 10.10.

---

### Post by Kegeg on 2012-03-27
> **ron_digital said:**
> This problem has been reported by several users, I googled and I only found questions and very little productive answers.

I have the exact same problem on the 11.10 64bit, even the screen flickering and mouse problem are the same, I've noticed the has to do with power device management, when I turn on the computer with power cord disconnected the error doesn't occur and everything runs fine on battery, but when i reconnect the power, it starts to randomly restart and became glitchy.

The only partial workaround I could found was related to a program called Jupiter, which helps the computer to better manage the power devices, you can find it on Synaptic Package Manager, so far the restars have been reduced a lot, but still happen every now and then.

I hope Ubuntu fix this bug before release the stable version of 12.04 and honestly I'm seriously considering a downgrade to 10.10.

Now that you are mentioning it, I also have screen freeze and glitch. I'll try the workaround for now and I hope we can find a solution for that. I don't know if this could be related, but I also have some brightness issue that won't dim to save power...

---

### Post by Kegeg on 2012-03-28
> **ron_digital said:**
> 
The only partial workaround I could found was related to a program called Jupiter, which helps the computer to better manage the power devices, you can find it on Synaptic Package Manager, so far the restars have been reduced a lot, but still happen every now and then.


I tried installing Jupiter, but it haven't chance anything, it happens as often... Could that bee a graphic problem? I have Bumblebee install on the machine.

---

### Post by Kegeg on 2012-03-31
I've looked at the syslog and found that everytime juste before the reboot those 2 lines are always present and the same: 
> Mar 27 14:56:53 kevin-NV57H AptDaemon: INFO: Quitting due to inactivity
Mar 27 14:56:53 kevin-NV57H AptDaemon: INFO: Quitting was requested
Anyone knoes if it's relevant?

---

### Post by ron_digital on 2012-03-31
> **Kegeg said:**
> I tried installing Jupiter, but it haven't chance anything, it happens as often... Could that bee a graphic problem? I have Bumblebee install on the machine.
Did you disconnect the power and stayed on battery for while, I'm asking because on battery ubuntu runs smoothly, also wanna know if your computes is a 64bit machine?

I think all examples I saw were on 64bits machines and I have a netbook Acer AOD250 that runs ubuntu 11.10 since the release and never had none of these errors, not one single time, that makes me think that its software error but only for 64bit machines.

I will install a 32bit version just to check if got the same errors, I'll keep you posted.

cheers,
Ronald.

---

### Post by Kegeg on 2012-04-01
> **ron_digital said:**
> Did you disconnect the power and stayed on battery for while, I'm asking because on battery ubuntu runs smoothly, also wanna know if your computes is a 64bit machine?

I think all examples I saw were on 64bits machines and I have a netbook Acer AOD250 that runs ubuntu 11.10 since the release and never had none of these errors, not one single time, that makes me think that its software error but only for 64bit machines.

I will install a 32bit version just to check if got the same errors, I'll keep you posted.

cheers,
Ronald.

Yes I have a 64bits machine, and it also happens when only on battery, but a little less often. I wish it will be fixed by the time of the final release, but I don't know if that could be a hardware compatibility issue, as I got my laptop only a couple month ago.

---

### Post by mattgen88 on 2012-04-03
I'm using a 64bit OS

my 32bit laptop is running fine using lubuntu.

---

### Post by meborc on 2012-04-03
Sure sounds like a problem with the Nvidia Optimus (graphic card switching)... Have you ever had restarts while doing something graphic intensive like playing a 3d game?

---

### Post by mattgen88 on 2012-04-03
Nearly everytime I've had a crash it was scrolling through a web page. 

I have an nvidia card 8800gt. I have had the problem in gnome-shell, ubuntu classic, ubuntu unity. It happens most severely (system lockup) in gnome-shell, least often in ubuntu classic. But it still happens. 

I've switched nvidia drivers as well with no luck. So I think it might be a bug with x server. 

I also seem to get this:
Apr  3 14:21:54 UBUNTU kernel: [45817.041516] WorkerPool/5751[5751]: segfault at 17 ip 00007fd51f9619fe sp 00007fd525984f30 error 6 in libc-2.15.so[7fd51f836000+1b2000]

Apr  3 14:43:08 UBUNTU gnome-session[5557]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.#012

Apr  3 14:43:09 UBUNTU kernel: [47092.150898] Chrome_IOThread[6219] general protection ip:7fcbbf90ac3e sp:7fcbaba31280 error:0 in chrome[7fcbbeaf1000+4298000]

I think they might be related, not entirely sure

---

### Post by OGpmpdog on 2012-04-03
Hi all,

I've been having this same problem - random shutdowns/restarts.  

This rarely happens but I'm just letting you know you are not alone :)

I'm testing with a T61 laptop: Core2 CPU, and Nvidia graphics card.

I always use DC power (the battery died 2 years ago).

---

### Post by Kegeg on 2012-04-04
> **meborc said:**
> Sure sounds like a problem with the Nvidia Optimus (graphic card switching)... Have you ever had restarts while doing something graphic intensive like playing a 3d game?

I don't really play any game on that computer, but it mostly happens when I'm trying to copy large files from an external hardrive. So I'm not sure if that would be cause by the Nvidia Optimus, is there a way I could monitor that to see if it's related?

Thanks

---

### Post by meborc on 2012-04-04
my idea concerning crashes while playing games was that during 3D gameplay, graphics are heavily used, so there should be no graphics switching... so if you play 3D game for a long while and you have no crash -> crashes should be due to graphics switching...

but I am just guessing blind here :D

---

### Post by Ender985 on 2012-04-12
I'm having the same problem, the session just suddenly logs me out , generally when scrolling a website. I'm sitting on a Nvidia graphics card, 64bit 3.2.0-23-generic kernel, and my logs show this:

```
Apr 12 14:25:05 ubtu kernel: [10109.544638] show_signal_msg: 45 callbacks suppressed
Apr 12 14:25:05 ubtu kernel: [10109.544643] Xorg[6253]: segfault at 800000070 ip 00007ff00aae2af9 sp 00007fff0d993cb0 error 4 in nvidia_drv.so[7ff00aa81000+6e0000]
Apr 12 14:25:05 ubtu gnome-session[6392]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.#012
Apr 12 14:25:05 ubtu kernel: [10109.627950] soffice.bin[7517]: segfault at 56620c70 ip 00007fd8e56748d3 sp 00007fffc5130310 error 4 in libc-2.15.so[7fd8e5639000+1b2000]
Apr 12 14:25:05 ubtu acpid: client 6253[0:0] has disconnected

```

I had the propietary Nvidia drivers installed but I will now try to uninstall them and see if the issue repeats again.

---

### Post by shadowfirebird on 2012-04-12
I'm getting this too but it's my unscientific, tentative conclusion that:

* It's not just one bug.  I've had kernel panics, hangs, forced surprise reboots and X crashes.  Probably all had different causes.

* It's getting better as I keep installing updates.  Today I've just had one X crash.  

The updates are coming thick and fast.  Keep installing 'em, and wait a week or so.  At least, that's what I'm doing.  It is dissapointing, I know, but it can only get better.

---

### Post by Kegeg on 2012-04-12
> **shadowfirebird said:**
> I'm getting this too but it's my unscientific, tentative conclusion that:

* It's not just one bug.  I've had kernel panics, hangs, forced surprise reboots and X crashes.  Probably all had different causes.

* It's getting better as I keep installing updates.  Today I've just had one X crash.  

The updates are coming thick and fast.  Keep installing 'em, and wait a week or so.  At least, that's what I'm doing.  It is dissapointing, I know, but it can only get better.

I'm having the same, and me too it is getting better as I install the update, so hopefully with the final release it will be fix.

---

### Post by Kegeg on 2012-04-16
Okay, I did some testing, and here is what I got if that can help

-I tried to reinstall bumblebee like said on the stable ppa website ([https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)), it didn't work
-I tried to install the most recent kernel version to see if it could have been fixed ([http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/current/)), it didn't work
-I noticed that when I was only playing music with the lid closed it continue all day long without any reboot (it occurs at least once per hour usually). So i guest it have something to do with the display

---

### Post by shadowfirebird on 2012-04-17
Have you tried Ubuntu 2D?  Maybe the issue is Compiz.

---

### Post by Kegeg on 2012-04-18
> **shadowfirebird said:**
> Have you tried Ubuntu 2D?  Maybe the issue is Compiz.

I've tried that for two days (with 2D and gnome 3) and it works for now. No crash in 2 days when I usually have one per hour. 

I'll try to fix compiz then

Thanks

---

### Post by Kegeg on 2012-04-24
> **Kegeg said:**
> I've tried that for two days (with 2D and gnome 3) and it works for now. No crash in 2 days when I usually have one per hour. 

I'll try to fix compiz then

Thanks

I talked too fast, all the possible option crashed at one point... Ubuntu 3D and 2D, Gnome 3, Gnome normal and even gnome normal without effect

---

### Post by kevpatts on 2012-04-25
I deactivated the nVidia drivers via the "Additional Drivers" dialogue box and I'm not having any problems any more.

---

