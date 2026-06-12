---
title: "Problems with Jack XRUNS and sound cards"
date: 2008-07-22
forum: Ubuntu Studio
---

### Post by genepool on 2008-07-22
Hi folks,
I need some help with Jack and sound cards.  I am using a Xeon 3.06GhzX2 IBM Intellistation with 1gig ram and scsi 360 for home audio production and I am having a few problems since upgrading to ubuntustudio 8.10.  I mainly use Jack with Ardour for recording multi-track music and in 8.04 I had few if any problems.  

When I upgraded to 8.10 I started getting a lot of XRUNS in Jack.  After restarting the computer Jack would work well for a while then as a song I was building got more complex, additional tracks, plugins and automation the number of XRUNS would get higher.  I tried a lot of different Jack settings and it did not go away.  During troubleshooting I noticed first disabling hyper-threading in the BIOS helped but did not completely fix my problem.  Reading several other threads I began to think it was the built-in AC'97 audio that was the problem.  So, I looked around my house and found several old soundblaster cards and a Diamond MX300 Vortex 2.  I plugged in a PCI SBLive! Value and while the XRUNS went away the sound quality is much worse then the built in AC'97.

**Here are my questions:**
Does anyone have any recommendations or thoughts on inexpensive sound cards for or a trick to making the built-in AC'97 work happy with Jack.  I have a very limited budget and just enjoy recording some tunes at home.  

Does anyone think the Diamond MX-300 would work better?  

Does Jack or any Multimedia software take advantage of hyper-threading (does anything)?

Thanks

---

### Post by genepool on 2008-07-24
Bump

---

### Post by balleyne on 2008-11-17
For what it's worth, I've been having a similar issue. I'm using a Presonus Firepod with JACK and Ardour. In Ubuntu Studio 8.04, an xrun was fairly rare. Not non-existent, but they didn't happen often if at all. Since upgrading to 8.10, I get xruns even when my computer is sitting idle.

Not fun.

I haven't figured out what's going on though...

---

### Post by thorgal on 2008-11-18
my guess is that you have a different kernel. Does 8.10 come with an RT patched kernel ? I doubt it (but since I am using debian for my DAW, I cannot say). For what it's worth, the best realtime setup (xrun free) I achieved is what I am using right now :

- custom compiled kernel 2.6.24.3-rt3 (could be a higher 2.6.24 kernel revision but I stick to this .3 revision because it works nicely).
- jackdmp-1.9.0 : it just came out and works really well. 

I tried 2.6.27 which did not have an RT patch, it seemed to work well with audio but had problems with MIDI.

I have an intel board (based on i965) and use an RME HDSP card, which can sustain very small buffer operations (low lat). I disabled my onboard sound, totally useless in my DAW. No fancy graphics either, no 3D acc (so no compiz), it's just a DAW ;) 

I also tweaked the IRQ thread priorities (google the rtirq script). Of course, you need certain privileges to use RT processes (/etc/security/limits.conf). I right now have a rock solid setup at 1ms latency, even jamin which is resource hungry does not screw up! But of course, low lat is only necessary if you use software monitoring and want to monitor software FX while you are playing. If you use hardware FX and can use hardware monitoring, low lat is not necessary.


So my recommendation :
- kernel 2.6.24.x RT patched
- IRQ prio tweak (make sure your soundcard does not share interrupt with another device)
- disable everything you don't need (background services, 3D acc, etc).

---

### Post by mrufino1 on 2008-11-23
Thorgal, fantastic post! I am trying very hard to make linux audio work for me so I can get rid of windows. Unfortunately, right now I can run reaper with all of my firewire interfaces with no issues, so it is more on principle than need that I want to dump win. Can you explain some of your post? I "upgraded" to 8.10 stupidly (8.04 was working- shoul dhave left well enough alone!) and am now seeing that I may have to go back. I am not the best "under the hood," Is there a way to get a a different kernel, especially an earlier one? I am getting lots of xruns and very bad performance in reaper under wine (sluggish graphics). I seem to have stumbled on less xruns, although still a few here and there, not good for live recording. Thanks, hopefully what I asked makes some sense. Time to go to bed for the night!!

---

### Post by markbuntu on 2008-11-24
One thing that might help is to up the audio cpu priority and unlock the memory if you forgot to do so after upgrading to Intrepid.

Edit /etc/security/limits.conf and add or modify these lines

```

audio - memlock unlimited
audio - nice -10
audio - rtprio 99

```

---

### Post by thorgal on 2008-11-25
> **markbuntu said:**
> One thing that might help is to up the audio cpu priority and unlock the memory if you forgot to do so after upgrading to Intrepid.

Edit /etc/security/limits.conf and add or modify these lines

```

audio - memlock unlimited
audio - nice -10
audio - rtprio 99

```


little correction: the setting should read :
```

@audio - memlock unlimited
@audio - nice -10
@audio - rtprio 99

```

@ indicates a setting that applies to a unix group, here 'audio'. If you want to restrict things to you only, replace @audio with your username (without @).

---

### Post by mrufino1 on 2008-11-25
I edited the security file to have memlock unlimited, had it at 512000 before. I don't know if that will make any difference though because I have 512 ram anyway. In the jack panel, should I have "no memlock" checked? Now, by dumb luck the other night, I had it running for a while with only 2 xruns in a half hour- still not totally okay, I need none, but better. The problem is that when I had no xruns, reaper ran terribly as far as graphic updates go. Even when I switched back to the internal soundcard it was still running like that, and then after a restart and internal soundcard, reaper was running fine. 
In reference to some of the posts in this thread, my linux kernel , pasted from grub menu.lst

title		Ubuntu 8.10, kernel 2.6.27-3-rt
uuid		c0768647-9fe7-4868-bb1e-9e8626aa3c83
kernel		/boot/vmlinuz-2.6.27-3-rt root=UUID=c0768647-9fe7-4868-bb1e-9e8626aa3c83 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-3-rt
quiet


Is there a way to roll back to an earlier kernel while keeping 8.10? I don't know if I'm in the mood to redo my whole machine again. I may also look at some other options as far as music distros go, like JAD or MUSIX, but not totally sure yet. I love ubuntu for my day to day, but if there is something better for making music I am not opposed. Is that bad to say on the ubuntu forum? :). Anyway, I won't have time until tonight to test anything again but I appreciate the help so far.

---

### Post by thorgal on 2008-11-25
512MB of RAM ? ... that's not much ...
If you plan to record / playback only, that should be fine but as soon as you add more (virtual instruments, soft synths, etc) you will quickly reach some limit.

By the way, if you do use the onboard intel chip, set the number of periods per buffer to 3 in your jack setting. I did not see your jack setting so I assume you have it set to 2 by default. My crap latop using the ICH4 (old dell latitude with tha AC97 audio controller) works rather good nonetheless when I bump up the number of periods to 3.

---

### Post by Ng Oon-Ee on 2008-11-26
Just thought I'd confirm that Ubuntu Studio 8.10 does NOT have the rt kernel by default. There's one (rt-3) in the repos, but the no-dual-core bug and the shutdown/suspend/hibernate bugs are well and alive. This would be the main cause of xruns, I believe, trying to do complicated audio business with a generic kernel.

As to what to do about that, you can try to manually recompile an older kernel, but you'd have to really know what you're doing and how to solve the inevitable incompatibilities. Or you could go back to 8.04, that's recommended for Ubuntu Studio users for now.

---

