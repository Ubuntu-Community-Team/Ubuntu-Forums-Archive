---
title: "Can't read some CDs and DVDs"
date: 2010-11-26
forum: System76 Support
---

### Post by Vidal Duval on 2010-11-26
Hi,

I own a Pangolin (panp5) with Ubuntu 10.10 and recently I experienced some difficulties with some CDs and DVDs. When I insert a disk in the drive, it begins to spin but it never "picks up". At some point the drive just stop spinning and nothing happens (not mounted, not mountable either). I can't read blank CDs or DVDs, but original CD or DVD movies read fine. I burned some movies a while back and some of them can be read without problems, some others just refuse to get read.

I tried using an external USB CD/DVD reader, same problem (spins then stops). The drive is being recognized and used to work fine. When I use the same drive on my wife's computer (running on windows) all is fine. I also tried reading disk while running a 10.10 livecd (from USB key).

Here's the output of lshw with...

...no disk:
```

  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW TS-L633A
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TM00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```

...a disk spinning:
```

  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW TS-L633A
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TM00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=busy

```

...a disk that stopped spinning:
```

  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW TS-L633A
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TM00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```

Thank you for your time, it's appreciated :)

---

### Post by poodoopealeoaph on 2011-01-24
I've been having the same issues. I did get it to work after installing ubuntu-restricted-extras through synaptic. The only thing about that though is that everything was working fine but after i got my first set of updates, it no longer works. I still can't figure out exactly what to do to get it working again though. So, if you try this and it works then good for you and if anyone comes across this that knows how I can get things working again that would be great...

---

### Post by isantop on 2011-01-24
You've got half of it; the first step is indeed to install Ubuntu Restricted Extras. However, there is an oft overlooked second part to DVDs.

In full:
```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```

That second line gets the DVD support working.

---

