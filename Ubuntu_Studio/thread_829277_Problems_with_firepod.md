---
title: "Problems with firepod"
date: 2008-06-14
forum: Ubuntu Studio
---

### Post by wurdien on 2008-06-14
Hi,

I have just installed Ubuntu Studio to my computer. As sound card I have Presonus Firepod. I read from internet that many people had succesfully used firepod under Linux. However, I haven't had luck with it.

When I first time tried Firepod under Gentoo system, it worked well (I recorder only few seconds to see it works). However, after reboot it didn't work anymore... I reinstalled a lot of software but nothing helped. I thought that something in system had completely messed up so I decided to reinstall it. Instead of Gentoo I installed Ubuntu Studio, but same problems were still there.

When I start jack there are several chances what can happen.
If started from QJackCtl is might say ```
cannot complete execution of the processing graph (Success)
zombified - calling shutdown handler
```

If started from terminal it says
```
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
Aborted
```

Sometimes it may flood hundreds of "cannot complete execution of the processing graph" lines.

Sometimes I am able to start Ardour before jack crashes. Usually, in this condition, playback doesn't work. If I press play button nothing happens, it doesn't even turn green.

Sometimes I am able to even play that. I don't know if I could hear something from headphones connected to firepod, however, if I try to record something there will be only some loud noise. I mean, volume meter shows as high as it can and recorded track is just full of noise (seen as red).

I have tried this on both Gentoo and Ubuntu Studio, and same problems exist on both systems. I have also tried card under Windows, and it works with it.

EDIT: This problem got solved by installing ffado and using it instead of freebob. I don't know if there's some difference (maybe in firmware?) with FP10 and firepod, because FP10 which I am using didn't work, however maybe firepod would have had better success (IF there's difference)

---

### Post by vivichrist on 2008-09-03
yep I have a similar problem ... jackd crashes and connection is left hanging and i have to switch th FP1o off and on again to reset it. after several attempts I finally get a stable connection. have you installed on the FP10 the latest firmware? this stuff only started happening with jack 0.109.2. I am stumped. I've posted a bug with libfreebob and jackd at launchpad. but I doubt anyone will do anything about it.

---

### Post by vivichrist on 2008-09-03
I would take a look at doing an:

```
apt-build install --rebuild --reinstall jackd
```

and make sure you have libiec61883-dev and libavc1394-dev installed this seems to have made my stability problems with jackd dropping firewire connections go away, with ardour anyway. however hydrogen crashes jackd in the same way as previously mentioned ...?

---

### Post by vivichrist on 2008-09-03
actually now that I have rebooted this no longer works. I now think that this kind of error is hardware dependant so may be a problem with libiec1394, libraw1394 or the kernel module for the firewire controller.

---

