---
title: "Audacity missing Jack Option in device options"
date: 2009-04-17
forum: Ubuntu Studio
---

### Post by talkfig on 2009-04-17
Studio 8.04.1 Amd64

Fresh Install, Realtime kernel,

Seems like Audacity & Jack do not want to play together
like they did on my older Studio release.

Jack Connection kit is not available under preferences &
no ports for audacity under QJackCtl patchbay.

Internal Sound card options do show up in Audacity preferences
External (USB) soundcard available sometimes - not sure why
it disappears..

Is anyone having similar issues?

Audacity 1.3.4beta
jackd 0.109.2

---

### Post by babarosa on 2009-04-18
Visit "www.getdeb.net" and download the latest version of audacity (v1.3.7) for your system (64bit, Hardy). Is the "jack audio connection kit" still missing in the menu to choose from?

Greetings, Michael

---

### Post by talkfig on 2009-04-19
Installed Audacity 1.3.7 & even fewer options are available - no jack...

1.3.7 has an about "info" function showing the build components -
no libjack - is this possible?


Cheers!
mdf

---

### Post by babarosa on 2009-04-19
> 1.3.7 has an about "info" function showing the build components -
no libjack - is this possible?


No, that can't be the reason, "libjack" doesn't show at my audacity either though it works fine with jackd.

To my mind, the "jackd 0.109.2" is the troublemaker. Do you mind searching ppa launchpad ([https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas), for example this one [https://launchpad.net/~khashayar/+archive/ppa](https://launchpad.net/~khashayar/+archive/ppa)) for more recent jackd-versions or compiling it by yourselves?

Greetings, Michael

---

### Post by g-raf on 2009-09-06
I have the same problem with Jack & Audacity in Ubuntu Studio 9.04. This problem started when i got a new USB soundcard and changed the ALSA settings for the USB soundcard. Before that, Jack and Audacity worked fine. I prefer to use the USB soundcard since audio production will be much better than using the HDA Intel soundcard. I recently wrote a post about this problem. Anyone have some ideas on how to fix this?

---

### Post by talkfig on 2009-10-17
I fixed this by installing 64studio 3.0 - beta3

I like it..

& it uses ubuntu repos

did have some install issues w SATA/AHCI on my old Asus
board.

---

### Post by martinistudio on 2009-10-17
1) jackd 0.109.2 is not a good version
2) Audacity and Jack is not the best combination in general

---

