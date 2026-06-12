---
title: "UbuntuStudio 11.10 and Firebox...latency of 17ms???!?!?!"
date: 2012-03-19
forum: Ubuntu Studio
---

### Post by audiomodder on 2012-03-19
Hey everyone,

So I had an old netbook that I had running with Ubuntu 11.10 that I "upgraded" with the Studio packages (it's old enough that it doesn't have a DVD-ROM).  I could get a latency of around 8ms through Jack with it.  Sadly, it won't stay running for more than about 30 seconds now due to a power supply issue (I think).

So because the netbook is dying a horrible death, I took the opportunity to buy my wife a new computer and confiscated hers.  It's a Dell Studio 1737, and it has what I've been wanting in my audio rig for a while...a Firewire port.  I've got a Presonus Firebox that's been collecting dust for about 3 years waiting for me to use it.  This PC is superior in literally every single way when it comes to hardware.

So here's the problem...fresh install of 11.10 UbuntuStudio 64-bit.  I've set the IRQ priorities for Yenta and Firewire, I THINK I've shut off CPU freq scaling (I have my doubts..is there a decent way to tell?  everything I find for this is for 10.04 or earlier...).  The best I can get for latency is about 17ms, which is awful for me.  It doesn't matter if it's the on-board audio (Intel ICH9) or the Firebox, it's all about 17ms...which makes me think something else is going on.

What's interesting is that with just UbuntuStudio and updates with the standard repositories, I get an xrun callback every 5 seconds exactly when I try lower latencies, but I also get D-BUS errors every time I try to stop Jack (and it dies a horrible, painful death).  I read a forum post talking about KX Studio, so I added their repositories, and now it's about every 8 seconds, and PulseAudio throws errors about not running (my wife has heard "@&*@$%! !$%%$@*& PULSE AUDIO @#%^%^!$!!!!!" more times than I think I care to count)...but the D-BUS errors are gone and Jack at least shuts down nicely.  Still, the best I can do for latency is around 17ms.

I've now been working on this for every waking moment for about 3 days (including temporarily loading Windoze back on it so that I could update the BIOS) and I'm at my wit's end.  Anybody have any ideas?

---

### Post by sgx on 2012-03-19
Hi. htop is an app that shows running processes,
and may reveal some default bloatware that is polling
the system every few seconds.

The bios can be accessed at powerup by some keypress,
usually flashed onscreen only for a millisecond, to spare
the Vista tech support desk dealing with educated users.
It would be worth temporarily shutting down all the
wireless, camera, and networking there.

cpu scaling should be turned off via ubuntu

Use the presonus external power supply

32 bit system should be installed

Your onboard ricoh firewire may be an issue in some cases.
Some companies recommend using some TI firewire interface:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16839328006&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-PC+Cards/PCMCIA+Add-on+Cards-_-Syba-_-39328006](http://www.newegg.com/Product/Product.aspx?Item=N82E16839328006&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-PC+Cards/PCMCIA+Add-on+Cards-_-Syba-_-39328006)

compare results when running the qjackctl Periods/Buffer setting
between two and three and four.
Cheers

killall pulseaudio

that command can help, during any particular session.
pulse will be back on reboot.

---

### Post by jejeman on 2012-03-19
> killall pulseaudio

that command can help, during any particular session.
pulse will be back on reboot. Pulseaudio will be back immediatelly. It's needed to turn off autospawn.
```
echo "autospawn = no" > ~/.pulse/client.conf
```
> it would be worth temporarily shutting down all the
wireless, camera, and networking there.That is completly true. On my laptop I need to turn off wireless.
> fresh install of 11.10 UbuntuStudio 64-bit.I recommend 10.04 if it supports the laptop hardware.
> I THINK I've shut off CPU freq scaling (I have my doubts..is there a decent way to tell? To check run
```
cat /proc/cpuinfo | grep MHz
```
Personaly I've find out that for lowlatency with Jack minimum 2GHz modern cpu is needed (e.g. core2duo).
Check the IRQ sharing.
```
cat /proc/interrupts
```

---

### Post by audiomodder on 2012-03-19
Alright, a quick update after trying some things.

Finally got Pulse to back off (thank you).  I wish I had a choice of the firewire, but sometimes you take what you can get :)

In looking through my interrupts, I noticed that my firewire interrupt is called "firewire_ohci", which I'd seen before, but it finally registered with me that when i configured my IRQ, that had been set to "firewire" per the UbuntuStudio firewire instructions.  Changed that to "firewire_ohci" and suddenly I can drop to about 5ms when only Jack is running with no xruns.

BUT

When i start anything else up, i get Jack errors and the xruns start (this one from qsynth)

 p, li { white-space: pre-wrap; }  Mon Mar 19 17:42:06 2012: [1m[31mERROR: JackEngine::XRun: client = qsynth was not run: state = 2[0m
 Mon Mar 19 17:42:06 2012: [1m[31mERROR: JackAudioDriver::ProcessGraphAsync: Process error[0m
 [COLOR=#cc66cc]17:42:11.457 XRUN callback (4).[/COLOR]

Everything seems to SOUND ok, and when I pump up the latency a bit, I can get rid of it.  I'm getting about 6 of the "ProcessGraphAsync" errors as soon as I start up a process.  What's weird is that I'm watching my CPU graph and it's not peaking about about 70%, even when things are starting up.  It's sitting around 15% when things are idle and I'm still getting xruns while it's there.

I'm running a 2Ghz Dual Core with 4Gb or RAM, so no issue there.  There's no CPU Frequency Scaling option in my Power Manager, or I would have shut that off.  When I checked, it said both cores were running at just under 2GHz (1995MHz).  In my BIOS there's something with scaling, but it's "choose between 2 frequencies and multiple"....I have it set to 2.

Any other ideas?

---

