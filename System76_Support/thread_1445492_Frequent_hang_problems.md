---
title: "Frequent hang problems"
date: 2010-04-02
forum: System76 Support
---

### Post by Ed.Corcoran on 2010-04-02
I'm having very frequent hangs that require a hard reboot. The hangs also cause corruption, so I have to boot to a liveCD and run fsck just to get the computer to boot from the hard drive.

It all started yesterday. I had shut down and unplugged my computer so I could dust out the case. When I plugged it back in, I started having these seemingly random and very frequent crashes.

I reopened the case and checked all the connections, so I don't think I messed up any physical parts. The dusting might have been a coincidence since it was the first time in weeks I'd shut down my computer. Since the last reboot, I'd installed lots of updates. My router/modem also had new firmware installed. AT&T did it remotely and without notifying me, so I don't know what changed in the firmware.

I've attached my syslog and quoted the part right before the crash. My computer is a Wild Dog and I'm running 9.10.

The crashes have happened both when I was listening to music and when I wasn't. They happened within a few minutes of boot and within a few hours. One even happened overnight when I wasn't using the computer.

```

Apr  2 14:43:03 system76-pc kernel: [  423.107859] BUG: Bad page state in process Xorg  pfn:a497d
Apr  2 14:43:03 system76-pc kernel: [  423.107865] page:ffffea0002401358 flags:0100000000008000 count:0 mapcount:-1024 mapping:(null) index:0
Apr  2 14:43:03 system76-pc kernel: [  423.107869] Pid: 1331, comm: Xorg Tainted: P           2.6.31-20-generic #58-Ubuntu
Apr  2 14:43:03 system76-pc kernel: [  423.107871] Call Trace:
Apr  2 14:43:03 system76-pc kernel: [  423.107879]  [<ffffffff810df324>] bad_page+0xd4/0x130
Apr  2 14:43:03 system76-pc kernel: [  423.107882]  [<ffffffff810e0aac>] __free_pages_ok+0x5c/0x4d0
Apr  2 14:43:03 system76-pc kernel: [  423.107886]  [<ffffffff81130561>] ? pollwake+0x51/0x60
Apr  2 14:43:03 system76-pc kernel: [  423.107890]  [<ffffffff81045c49>] ? __wake_up_common+0x59/0x90
Apr  2 14:43:03 system76-pc kernel: [  423.107893]  [<ffffffff81130420>] ? __pollwait+0x0/0xf0
Apr  2 14:43:03 system76-pc kernel: [  423.107896]  [<ffffffff810e0f36>] free_compound_page+0x16/0x20
Apr  2 14:43:03 system76-pc kernel: [  423.107900]  [<ffffffff810e4dd6>] put_compound_page+0x26/0x40
Apr  2 14:43:03 system76-pc kernel: [  423.107903]  [<ffffffff810e515e>] put_page+0x12e/0x140
Apr  2 14:43:03 system76-pc kernel: [  423.107908]  [<ffffffff814bab6c>] ? unix_stream_recvmsg+0x25c/0x570
Apr  2 14:43:03 system76-pc kernel: [  423.107912]  [<ffffffff81430ff8>] ? skb_release_data+0xc8/0xd0
Apr  2 14:43:03 system76-pc kernel: [  423.107915]  [<ffffffff81114b4d>] kfree+0xed/0x140
Apr  2 14:43:03 system76-pc kernel: [  423.107918]  [<ffffffff81430ff8>] skb_release_data+0xc8/0xd0
Apr  2 14:43:03 system76-pc kernel: [  423.107922]  [<ffffffff814bab6c>] ? unix_stream_recvmsg+0x25c/0x570
Apr  2 14:43:03 system76-pc kernel: [  423.107925]  [<ffffffff814309f9>] __kfree_skb+0x19/0xa0
Apr  2 14:43:03 system76-pc kernel: [  423.107928]  [<ffffffff81430afd>] kfree_skb+0x3d/0x90
Apr  2 14:43:03 system76-pc kernel: [  423.107931]  [<ffffffff814bab6c>] unix_stream_recvmsg+0x25c/0x570
Apr  2 14:43:03 system76-pc kernel: [  423.107934]  [<ffffffff81130510>] ? pollwake+0x0/0x60
Apr  2 14:43:03 system76-pc kernel: [  423.107938]  [<ffffffff8142bae9>] sock_aio_read+0x149/0x150
Apr  2 14:43:03 system76-pc kernel: [  423.107940]  [<ffffffff81130510>] ? pollwake+0x0/0x60
Apr  2 14:43:03 system76-pc kernel: [  423.107944]  [<ffffffff81078a30>] ? autoremove_wake_function+0x0/0x40
Apr  2 14:43:03 system76-pc kernel: [  423.107948]  [<ffffffff8111f472>] do_sync_read+0xf2/0x130
Apr  2 14:43:03 system76-pc kernel: [  423.107952]  [<ffffffff8107c523>] ? __hrtimer_start_range_ns+0x183/0x330
Apr  2 14:43:03 system76-pc kernel: [  423.107955]  [<ffffffff81078a30>] ? autoremove_wake_function+0x0/0x40
Apr  2 14:43:03 system76-pc kernel: [  423.107960]  [<ffffffff81224a11>] ? security_file_permission+0x11/0x20
Apr  2 14:43:03 system76-pc kernel: [  423.107963]  [<ffffffff8111fb21>] vfs_read+0x181/0x1a0
Apr  2 14:43:03 system76-pc kernel: [  423.107967]  [<ffffffff8112005c>] sys_read+0x4c/0x80
Apr  2 14:43:03 system76-pc kernel: [  423.107970]  [<ffffffff8152d2a9>] ? do_device_not_available+0x9/0x10
Apr  2 14:43:03 system76-pc kernel: [  423.107975]  [<ffffffff81012082>] system_call_fastpath+0x16/0x1b

```

---

### Post by thomasaaron on 2010-04-02
Hey, Ed.

I would also try re-seating the memory and the graphics card (blowing it out before replacing components).

If that doesn't fix it, could you please attach full logs (System > Admin > System76 Driver > Support > Create) after the next reboot-after-crash. That kind of looks hardware-ish. But I'd like to have a look at some of the other logs.

---

### Post by Ed.Corcoran on 2010-04-03
Resetting the memory and video card didn't fix it. It crashed overnight. I rebooted and was about to post the forum with my logs.tar file and it crashed again! Right now, I'm running from a 10.04 beta1 live CD. 

When it crashed overnight, I had left Chromium open. When it crashed a few minutes ago, I also had Chromium open because I was visiting the forum. Maybe that had something to do with it?

Anyway, I'm going to install 10.04 beta 1 to an external hard drive. After I finish that, I'll boot from my main 9.10 install and see if running Firefox instead of Chrome helps. If it doesn't, I'll uninstall Flash and see if that helps. If that doesn't help, I'll work from the 10.04 beta installed on the external drive. If that crashes too, it's likely a hardware problem.

I've attached a logs.tar that was generated after the crash that happened overnight. I rebooted at about 12:15 today (April 3rd). The second crash happened at about 12:30 today. I'm attaching a second tarball of the logs for it as well. That one, however, I made myself (as I'm booting from a LiveCD), so it doesn't have all the stuff the first one does.

---

### Post by Ed.Corcoran on 2010-04-03
For some reason, 10.04beta1 kept crashing when I tried to install it to an external HD. I tried two different ones, too. 

So I installed 9.04 onto an external, as I had a 9.04 CD laying around. This worked. I'm running 9.04 off the external right now. If I have any crashes I'll post about it.

---

### Post by Ed.Corcoran on 2010-04-04
I've been using 9.04 off the external for most of the day with no trouble. I had a crash, but it was different than my usual crashes. The mouse stopped working and then the keyboard stopped working, but there was a long enough gap between for me to save my stuff. I had two keyboards plugged in at the time, so that might be it.

Anyway, I haven't booted back into 9.10 to check how it's doing. I also haven't done any experiments involving Flash. I'm trying to do some homework and write a paper, so I'm not going to mess with the stable, if not ideal, situation I have right now.

---

### Post by thomasaaron on 2010-04-05
When you do get back around to using 9.10 or 10.04, try with only one keyboard installed and run Firefox instead of Chromium to eliminate both of those as suspects.

---

### Post by Ed.Corcoran on 2010-04-13
I finally got around to getting back to my main 9.10 install. I used it for most of the day without opening a web browser and I had no problems. I ran my updates and backups and everything was good. 

Then, tentatively, I started up Midori, a minimal browser. That caused no problems. Now I'm using Chrome and am still having no problems. If anything happens, I'll post here again.

---

### Post by Ed.Corcoran on 2010-04-15
I had another crash this morning at 10:14am. It took me until now to finally get it to boot back into the main partition. After the crash, my home partition won't mount unless I do some fscking.

Anyway, here's the logs. I had to reboot a few times, so the actual crash is probably pretty near the top.

---

### Post by Atamisk on 2010-04-15
Add me to this list. (Sorry if this counts as threadjacking!)

This same sudden crash forcing hard reboot happens every time i run firefox or any other memory-heavy process like celestia. i get an apport report that talks a lot about x-serv as well. If it's the same sort of problem (monitor goes off?), it may be related to an update. my 9.10 install did this immediately after i ran update manager as well. (Also a lucid install on the same system exhibits the same issue!)

ALSO: Can you stably run Chrome from xterm? I can, almost indefinitely. when i try to run it from GNOME, no dice.

EDIT: AARGH! i just noticed I'm in the wrong forum. got here from a search. What i posted might still help, so i'll leave it.

---

### Post by Ed.Corcoran on 2010-04-15
Had another crash/hang.

When I rebooted, I again had problems with my /home partition mounting. I hit esc to go to a recover console, manually mounted it, and then hit ctr+D to continue booting. ubuntu loaded with no problems after that.

---

### Post by thomasaaron on 2010-04-16
Hmmm... That's a lot to sift through, but you sure have a lot of invalid query packet messages prior to your last restart.

```
Apr 15 15:49:54 system76-pc avahi-daemon[969]: Invalid query packet.
Apr 15 15:51:05 system76-pc avahi-daemon[969]: last message repeated 2 times
Apr 15 16:02:14 system76-pc avahi-daemon[969]: Invalid query packet.
Apr 15 16:03:35 system76-pc avahi-daemon[969]: last message repeated 2 times
Apr 15 16:09:29 system76-pc avahi-daemon[969]: Invalid query packet.
Apr 15 16:10:36 system76-pc avahi-daemon[969]: last message repeated 5 times
Apr 15 16:17:01 system76-pc CRON[6240]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 15 16:17:04 system76-pc avahi-daemon[969]: Invalid query packet.
Apr 15 16:18:06 system76-pc avahi-daemon[969]: last message repeated 2 times
Apr 15 16:25:55 system76-pc avahi-daemon[969]: Invalid query packet.
Apr 15 16:27:07 system76-pc avahi-daemon[969]: last message repeated 5 times
Apr 15 16:42:10 system76-pc avahi-daemon[969]: Invalid query packet.
Apr 15 16:43:38 system76-pc avahi-daemon[969]: last message repeated 5 times
Apr 15 17:01:42 system76-pc avahi-daemon[969]: Invalid query packet.
Apr 15 17:03:09 system76-pc avahi-daemon[969]: last message repeated 5 times
Apr 15 17:12:15 system76-pc avahi-daemon[969]: Invalid query packet.
Apr 15 17:13:39 system76-pc avahi-daemon[969]: last message repeated 2 times
Apr 15 17:17:01 system76-pc CRON[6604]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 15 17:27:58 system76-pc avahi-daemon[969]: Invalid query packet.
Apr 15 17:29:10 system76-pc avahi-daemon[969]: last message repeated 2 times
Apr 15 17:41:30 system76-pc avahi-daemon[969]: Invalid query packet.
Apr 15 17:42:41 system76-pc avahi-daemon[969]: last message repeated 6 times
Apr 15 17:50:16 system76-pc pulseaudio[2666]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Apr 15 17:50:16 system76-pc pulseaudio[2666]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Apr 15 17:50:16 system76-pc pulseaudio[2666]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Apr 15 17:52:04 system76-pc avahi-daemon[969]: Invalid query packet.
Apr 15 17:53:12 system76-pc avahi-daemon[969]: last message repeated 2 times
Apr 15 17:54:12 system76-pc avahi-daemon[969]: last message repeated 9 times
Apr 15 18:30:50 system76-pc kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
```


Try stopping the avahi daemon right after you boot by running...

```
sudo stop avahi-daemon
```

If that works, we can make it permanent.

Also, please let me know the time on your system clock when it freezes next time. That will help me zero in on it in the logs.

---

### Post by Ed.Corcoran on 2010-04-17
I had a crash sometime last night between midnight and when I sat down at my computer this afternoon at 1:30pm. I've attached the logs. The Avahi thing showed up again, so I stopped the process as soon as I managed to get my machine to boot.

---

### Post by Ed.Corcoran on 2010-04-18
I had a crash today at 2:18. Avahi was stopped, so that wasn't it. The only thing that showed up in syslog was a bunch of activity from the optical drive, as I was ripping a DVD.

I also figured out how to get my computer to boot right after a crash. What happens is the /home partition won't mount when mountall is called. However, if I boot into a recovery console, I can mount it manually using /dev/sda3 rather than the UUID that mountall and fstab use. After it mounts, I can reboot and then mountall mounts it correctly. 

I don't understand why, but at least I can recover from a crash faster now. Back when I was having similar crash problems when I first got the machine, I didn't have this same problem on boots.

---

### Post by thomasaaron on 2010-04-19
OK, I'm not seeing anything pertinent in the logs, and I don't think we can solve this one in the forums.

Most likely the problem is either the memory or the graphics card. I'm voting right now for the graphics card, as memory typically leaves a trail in the logs. Graphics cards often don't.

Let's move this one to email/phone.

support...at...system76...dot...com

---

