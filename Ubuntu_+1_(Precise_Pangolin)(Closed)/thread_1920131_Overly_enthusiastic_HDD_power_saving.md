---
title: "Overly enthusiastic HDD power saving"
date: 2012-02-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by pressureman on 2012-02-04
I just installed 12.04 alpha 2 yesterday, and I noticed that when I disconnect AC from my notebook, my HDD starts to spin down (and up) every few seconds.

This is a bit of deja vu, as one of the previous Ubuntu releases had this problem (10.10 IIRC), and even earned the reputation of a HDD killer.

Has anybody else noticed this, or are you all running SSDs? ;-)

As a workaround for now, I've just been executing "hdparm -B 254 /dev/sda", whenever I switch to battery.

---

### Post by xyzzyman on 2012-02-04
What is it currently defaulting to? There are alot of power tweaks in 12.04, and I'm in my live usb right now doing a fresh install so I'll check upon reboot, but if changing that setting with hdparm is fixing it, it sounds like your HDD's PM is funky and doesn't handle power management well itself. But I'll still check with my drive in about 10 minutes.

EDIT: I do remember they were thinking about re-enabling ALPM, and that doesn't work for everyone. I'm not sure if they wound up enabling it or not yet.

---

### Post by xyzzyman on 2012-02-04
Yeah, my fresh install is defaulting to 254. No issues with it spinning up/down or parking either. So I guess we do need to find what yours is defaulting to and see where it's getting changed.

---

### Post by pressureman on 2012-02-04
I just booted up from battery, and the APM_level = 1.

If I plug in AC, it goes up to 254. Disconnect AC, and it goes back to 1.

The most annoying thing is that the HDD makes an odd "grunt"-like noise when it spins down :? which is quite distracting.

---

### Post by pressureman on 2012-02-04
I should mention, my notebook is a Thinkpad T500, and the HDD model is a Samsung HM251JJ (250 GB, 7200 RPM), with firmware version 2AA00_00.

---

### Post by xyzzyman on 2012-02-04
This was a fresh install, no reuse of home, no laptop tools installed, etc?? Correct?

I checked my /var/lib/pm-utils/power.d/95hard-apm and it is still set to be 254 on AC, and 128 on battery... It works along with laptop-mode-tools so something is wrong your system from defaults.

---

### Post by pressureman on 2012-02-04
Totally fresh install, formatted partition, installed with alpha 2.

My system doesn't have laptop-mode-tools installed (although does have laptop-detect).

I also don't have a /var/lib/pm-utils directory, although the pm-utils package is installed.

I'll try manually setting hdparm -B 128 on battery and see how it goes.

---

### Post by xyzzyman on 2012-02-04
Sorry, /usr/lib/pm-utils/power.d, not /var

the laptop-mode-tools package isn't installed by default, and I don't have it either. I think parts may be in another package that is installed because there's references in it in the script that switches between 128 and 254, but I haven't looked too deep at the code.

---

### Post by xyzzyman on 2012-02-04
What does this look like for you in a terminal?

```
sudo hdparm -i /dev/sda

/dev/sda:

 Model=Hitachi HTS543232L9A300, FwRev=FB4OC40C, SerialNo=081218FB2400LECYG98A
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=7114kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=625142448
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

```

It chooses what to set by the AdvancedPM # returned in that command it seems. Maybe your HDD is telling Ubuntu to use 1?

---

### Post by pressureman on 2012-02-04
Yes, it appears that my HDD automatically sets APM_level to 1 if a value of 127 or less is specified by hdparm.

```

sudo hdparm -B 127 /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0x7f (127)
 APM_level	= 1

```

Setting 128 works:

```

sudo hdparm -B 128 /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

```

```

sudo hdparm -i /dev/sda

/dev/sda:

 Model=SAMSUNG HM251JJ, FwRev=2AA00_00, SerialNo=xxxx
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=488397168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```

Since pm-utils sets APM_level to 127 when on battery, and my HDD seemingly reduces that all the way down to 1, I get rather excessive spinning down and up.

Manually setting it to 128 was fine (but may in fact never spin down...).

---

### Post by xyzzyman on 2012-02-04
That's odd as my pm-utils script says it's supposed to be 128 in the comments at the beginning. It also shows ```
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
``` weather I have it set as 128 or 254. You may want to submit a bug report to [https://bugs.launchpad.net/ubuntu/+source/pm-utils](https://bugs.launchpad.net/ubuntu/+source/pm-utils) if you can't find one already there.

Also can you edit /etc/hdparm.conf? Everything is normally commented out by default, so maybe uncomment the appropriate and reboot and see if it works.

---

### Post by pressureman on 2012-02-05
Odd indeed, since my 95hdparm-apm script has:

```

# This script adjusts hard drive APM settings using hdparm. The hardware
# defaults (usually hdparm -B 127) cause excessive head load/unload cycles
# on many modern hard drives. We therefore set hdparm -B 254 while on AC
# power. On battery we set hdparm -B 127, because the head parking is
# very useful for shock protection.

```

With AC disconnected (so, APM_level=1), I tried

```

sudo hdparm -S 48 /dev/sda

/dev/sda:
 setting standby to 48 (4 minutes)

```

But within a few seconds the HDD had spun down... certainly not four minutes worth.

It definitely seems like this HDD has an incomplete implementation of APM.

I'd really rather just leave APM_level on 128 when on battery. I accept that it might never spin down, but to be perfectly honest, if I know my notebook is going to be idle for a long time, I'll shut it down. Running a few apps simultaneously is nearly always going to ensure occasional HDD activity every few seconds, so it's a futile effort.

---

### Post by pressureman on 2012-02-05
I notice in /lib/hdparm/hdparm-functions (from package "hdparm")

```

    egrep -v '^[[:space:]]*(#|$)' /etc/hdparm.conf |
    {
        # set our default global apm policy here.
        if hdparm_try_apm "$WANTED_DISK"; then
            if hdparm_is_on_battery; then
                hdparm_set_option -B127
            else
                hdparm_set_option -B254
            fi
        fi

        ...

```

The oneiric version of this package uses a value of 128 instead of 127.... and that kinda solves the mystery (at least for me).

The package changelog also points it out:

> 
hdparm (9.37-0ubuntu2) precise; urgency=low

  * debian/hdparm-functions, debian/95hdparm-apm, debian/hdparm.conf.5: if we
    really want disk policy to allow spinning down on battery, we need to set
    -B *127*, not -B 128.  The comments in the historical pm-utils script
    make it clear that this was the intent all along.  Thanks to Anmar Oueja
    for catching this!

 -- Steve Langasek <steve.langasek@ubuntu.com>  Wed, 04 Jan 2012 13:57:57 -0800


Somebody else had already reported this bug too: [https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/913050](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/913050)

---

### Post by laborg on 2012-02-05
Hi! 

I'm suffering from the same problem (Thinkpad T500, but different HD: SAMSUNG HN-M101MBB). Spinning down way to often... Did you file a bug? 

regards,

---

### Post by pressureman on 2012-02-05
> **laborg said:**
> I'm suffering from the same problem (Thinkpad T500, but different HD: SAMSUNG HN-M101MBB). Spinning down way to often... Did you file a bug?

[https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/913050](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/913050)

---

### Post by laborg on 2012-02-05
> **pressureman said:**
> [https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/913050](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/913050)

sry, didn't see the link in your previous post. Maybe it's not a hd problem, but the notebook? In my case (Thinkpad T500, Samsung HD) the -B 127 value sticks, but it still spins down way too often...

---

