---
title: "status of suspend-to-ram + gazelle value + edgy"
date: 2006-11-13
forum: System76 Support
---

### Post by rgoldber on 2006-11-13
Hello-  

Just got my gazelle value.  Snappy little beast.  However, suspend-to-ram/resume is inconsistent at best.  Edgy has caused problems for another of my laptops in this department as well.

I noticed a post from Carl from a couple weeks ago that says edgy broke suspend.

Suspend-to-ram is a make or break thing for me, so I guess I'm wondering what the current status of this is.  If there are no existing or imminent work-arounds or fixes, I'll need to back down to dapper, or a sarge+etch mix.

That said, am I correct to assume that S3 on dapper will work flawlessly?  Also, what is the status of the ipw3945 in dapper?

Thanks-
Ryan

---

### Post by crichell on 2006-11-13
Hi Ryan - S3 and ipw3945 work well in Dapper.  I'll start diving into suspend in Edgy over the next couple of days.  I don't have a work around yet.

---

### Post by rgoldber on 2006-11-13
Works for me.  Ok, I've backed down to dapper (xubuntu though, I generally prefer xfce for some arcane reasons).  I realize I've stepped out of the "supported configuration" arena now, but how does a person disable the "wireless kill switch" on this particular piece of hardware?

Thanks-
Ryan

---

### Post by rgoldber on 2006-11-13
Ah, ignore my followup above.  I, uh, hadn't rebooted after a kernel upgrade.  (I swear I thought I had...)  Anyhow, wireless goes on and off with as expected with keyboard switch.

---

### Post by yogamatt1970 on 2006-11-20
Carl, just wondering what the status of this issue is - do you have suspend to RAM working with edgy yet?

---

### Post by crichell on 2006-11-20
Yes - but using feisty's kernel.  We're trying decide whether or not this is the best route to take.

---

### Post by MasterPi on 2007-02-14
I'm running feisty and here is the status of my Suspend the last time I played with it (a few days ago):

My laptop goes into and comes out of suspend fine, except when running Beryl/AIGLX it definitely kills all input devices after 2-10 minutes of being resumed.  I am able to restart GDM through SSH from another computer and run normally for at least another few minutes at which point it may do the same thing.  I also think this might've happened once while not running Beryl/AIGLX but I need to do more testing to be sure.  For the most part I've been avoiding suspending because I don't always have another computer around to SSH in with and I worry about hard-resetting it.

The other thing that happens with suspend is I'm pretty sure it kills rebooting automatically.  What I mean by this is that after I suspend, and try to reboot, the system shuts down the whole way (the progress bar finishes) but then sits there not powering off or rebooting.  I have to hold in my power button to do a hard power off then again to power on then it continues.

I think Suspend may also be messing with my wireless/NetworkManager but I haven't been paying enough attention to when errors occur to say that it's related.

::EDIT:: I have the:
Pangolin Value
- Original Operating System - Ubuntu 6.06 LTS (Dapper Drake) Linux
- Processor - Intel Core Duo Core Duo T2400 1.83GHz 2MB 667FSB
- Memory - 2 GB DDR2 667 MHz (2 x 1 GB)
- Hard Drive - 80 GB 7200 RPM
- CD/DVD Drive - CD-RW / DVD-RW (Dual Layer)
- Hardware Warranty - 1 Yr. Ltd. Warranty and Technical Support

Bought it early lastsummer. (June/July 2006)

---

### Post by crichell on 2007-02-14
This thread is a little old - just for clarity Suspend and Hibernate is fixed in Edgy with the standard Ubuntu kernel.  Soon I'll start a new thread with the fix we've implemented and we can gather different experiences.

Beryl can definantly break Suspend - I received and email from a customer last night stating that Beryl RC2 and Suspend are working.

For wireless edit your /etc/default/acpi-support file.  Adjust the following line to read:

```
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="snd_hda_intel snd_hda_codec ipw3945"
```

The first two modules help restore sound - unloading and loading the module seems to help.  The last module "ipw3945" is the wireless driver.

---

### Post by AusIV4 on 2007-02-14
My Gazelle Value suspends just fine with Beryl. That said, I got my Gazelle Monday afternoon, so I was on Beryl RC2 from the get go, which according to Carl's source, works fine. I had a little bit of trouble with hibernate, but it turned out my swap partition hadn't been activated. Since I've done that, everything seems to be working well.

---

### Post by MasterPi on 2007-02-14
sweet, Beryl RC2 just showed up in my updates =D

thanks for the help with the sound/wireless (though I hadn't noticed problems with the sound but why not give the module a reload for kicks)  I'm not sure why I didn't think of reloading the wireless module when I was having problems.

---

### Post by griffjon on 2007-02-14
I'm running 2.6.17.11-generic (edgy) and suspend-to-ram "works" in that I don't have to reboot, but my session is destroyed or lost, and I have to log back in to KDE (also running compiz, which is probably the source of my problems

suspend-to-disk/hibernate works... sometimes.

---

### Post by medomedo on 2007-03-18
Using 2.6.17.11-generic patched with suspend2 (2.2.9), suspend to RAM works if Beryl is not used. When Beryl is used, I need to ctrl+alt+F1 then back to session "ctrl+alt+F7" otherwise I get backofflight screen with mouse. 

I need also to run manually a command to get the wireless-LAN back.
# echo 1 > /proc/driver/wireless/radio
Does anyone know who to automize this.

Also I needed to restart alsa-utils to get sound back. Adding STOP_SERVICES="alsa-utils" in the file /etc/default/acpi-support didn't help.


When 2.6.20-6-generic OR 2.6.20-6-lowlatency patched with suspend2 (2.2.9), then the USB doesn't come back after resumption. when I rmmod the modules and modprob them back the USB mouse comes back but moves in a very very slow manner.

HW: FujitsuSiemens pro 2000: Centrino 1.5GHz, 1.3G RAM, i855 graphics card.

---

### Post by MasterPi on 2007-03-18
Suspend-to-ram mostly works for me now except for two problems:
- After resuming, my CPU or clock or something goes crazy frequency-wise and I get side-effects like repeated keyyyyyyyyyyyyyyyys and Gaim going idle/auto-away very quickly.  I've tried unloading the cpu_freq module and it's dependencies, to no avail, I'm not sure if I tried reloading them afterwards.  It's not a consistent problem either, it's like little bursts of speed.
- I'm still having the same problem as I did when I first got my Pangolin (see prev. post for specs) where after suspending the computer will not automatically power-off on halt or reboot, and I have to hold down the power button once it's reached the end of the shutdown progress bar.

---

### Post by tux_rox on 2007-03-19
Sorry I'm such a noob, but what's the difference between Suspend and Hibernate?  In Windows, it was either "screensaver time" or Sleep.

---

### Post by crichell on 2007-03-19
Suspend stores you current session (open docs, apps, etc.) into RAM and places your computer into a lower power usage mode.  Hibernate stores your current session to the hard disk and places the computer into a no power usage state.  Restoring from Suspend takes about 5 seconds.  Restoring from hibernate is about 20 seconds.

---

