---
title: "Ubuntu Minimal"
date: 2020-02-29
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2020-02-29
Hello Ubuntu forum,

I downloaded and installed Ubuntu Minimal and after several try's everything is working well.

I installed a couple of different desktops although could not get them to run so I removed them and install Lubuntu desktop and success.

My question is about the life cycle will support end in 2021 or 2023.


Thanks


This is what I installed.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

This is what I installed it on.

```


thomas@ubuntu:~$ inxi -Fxz
System:    Host: ubuntu Kernel: 4.15.0-88-generic x86_64 bits: 64 gcc: 7.4.0 Desktop: LXDE (Openbox 3.6.1)
           Distro: Ubuntu 18.04.4 LTS
Machine:   Device: desktop System: Hewlett-Packard product: HP Compaq dc7800p Small Form Factor serial: N/A
           Mobo: Hewlett-Packard model: 0AA8h serial: N/A BIOS: Hewlett-Packard v: 786F1 v01.04 date: 07/18/2007
CPU:       Dual core Intel Core2 Duo E6550 (-MCP-) arch: Conroe rev.11 cache: 4096 KB
           flags: (lm nx sse sse2 sse3 ssse3 vmx) bmips: 9310
           clock speeds: max: 2333 MHz 1: 2105 MHz 2: 2107 MHz
Graphics:  Card: Intel 82Q35 Express Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) drivers: intel (unloaded: modesetting,fbdev,vesa)
           Resolution: 1152x720@59.97hz
           OpenGL: renderer: Mesa DRI Intel Q35 version: 1.4 Mesa 19.2.8 Direct Render: Yes
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-88-generic
Network:   Card: Intel 82566DM-2 Gigabit Network Connection driver: e1000e v: 3.2.6-k port: 1100 bus-ID: 00:19.0
           IF: enp0s25 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 160.0GB (4.8% used)
           ID-1: /dev/sda model: WDC_WD1600AAJS size: 160.0GB
Partition: ID-1: / size: 146G used: 7.2G (6%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 44.0C mobo: 41.0C
           Fan Speeds (in rpm): cpu: 1821 fan-2: 0 fan-3: 1242 fan-4: 1005
Info:      Processes: 152 Uptime: 7:05 Memory: 950.8/3864.5MB Init: systemd runlevel: 5 Gcc sys: 7.4.0
           Client: Shell (bash 4.4.201) inxi: 2.3.56 
thomas@ubuntu:~$ 


```

---

### Post by yetimon_64 on 2020-02-29
You could try the "ubuntu-support-status" command which will display the period of support for the various packages you have installed.
```
$ ubuntu-support-status --help
Usage: ubuntu-support-status [options]

Options:
  -h, --help          show this help message and exit
  --show-unsupported  Show unsupported packages on this machine
  --show-supported    Show supported packages on this machine
  --show-all          Show all packages with their status
  --list              Show all packages in a list
```

---

### Post by poorguy on 2020-02-29
Here's a small part of the output as it is pretty extensive and didn't want to post a large amount of code.

```


thomas@ubuntu:~$ ubuntu-support-status --show-all
Support status summary of 'ubuntu':

You have 1450 packages (77.2%) supported until April 2023 (Canonical - 5y)
You have 328 packages (17.5%) supported until April 2021 (Community - 3y)
You have 2 packages (0.1%) supported until April 2021 (Canonical - 3y)

You have 3 packages (0.2%) that can not/no-longer be downloaded
You have 95 packages (5.1%) that are unsupported


No longer downloadable:
firejail libdvdcss-dev libdvdcss2 


Supported until April 2021 (Canonical - 3y):
libbrotli1 libwoff1 


```

Probably will be best to do a clean install in 2021.

This was something I've always wanted to try and finally did successfully and learned a lot so not a waste of time imo.

Always like when I learn something about Linux no matter how long it takes doing so.


Thanks for you help and reply. :)

---

### Post by DuckHook on 2020-02-29
Minimal is a strange beast. Using it means that you are rolling a self-made, highly customized install using spare parts and odds & ends. The result is a bit of a Frankenstein's monster ("It lives! It lives!"). If you decide to go that route, it makes little sense to think of the final product as anything like an official "flavour" with a set EoL, because each component will have its own expiry date.

FWIW, I love Minimal because it's the only thing that will still install on some of my really old 32-bit boxes. If you keep it updated, and *do-release-upgrade* consistently, I don't see why you can't keep running it until Canonical decides to drop support for some critical component. But you shouldn't (and needn't) think of it as a wholistic flavour like Lubuntu. Think of it more as a rolling release, in which the various components get continually updated (so long as you actually do keep current with your *apt full-upgrade*).

---

### Post by yetimon_64 on 2020-02-29
> **DuckHook said:**
> ...The result is a bit of a Frankenstein's monster ("It lives! It lives!")....
That is a good description my trusty ol' 14.04 install, a real monster all right ;). The most enjoyable install I have done in 13 years on Ubuntu. It was very stable and performed beautifully for about 4 years for me. It would do as I wanted, for example, little things like being able to click on notifications in Unity and have them go away :D. It was definitely customizable like Frankenstein's monster with "bits" from several DE's all mashed together in my case.

Feels like I'll have to get back into the "lab" soon and build another monster with bionic. As a base to build from the minimal installer is great i.m.o. Cheers, yeti.

---

### Post by poorguy on 2020-02-29
You make sense Duckhook and to be honest I really didn't know how to look at what I had created other than it was Ubuntu 18.04 to build on top of.

I know that I was sure having hell getting a desktop to run as some would display although wouldn't open anything.

The good is I learned a lot and I was confused a lot but I did finally get it to come together and work which was great.

At least I know the Ubuntu base is current and I may continue to see if I can get Xfce4 desktop working on it.

This may not be any real accomplishment for you Linux gurus but for a basic Linux user it's A-OK and I did have fun with it.

Hmm a Frankenstein distro that's cool because all of my computers are Frankenstein builds using bits and pieces from here and there. :D

---

### Post by DuckHook on 2020-02-29
> **poorguy said:**
> …I really didn't know how to look at what I had created other than it was Ubuntu 18.04 to build on top of.
If you look at it as a quasi-rolling release, then the next time you invoke *do-release-upgrade*, you will be at 20.04 and completely up to date. No worries about EoL. The process should also upgrade the DE and whatever else you added. Just try to stay away from PPAs, third-party extensions, self-compiled binaries, etc. Those things tend to bork upgrades. But other than those, all of my Frankenstein's Monster builds have upgraded rather nicely (knock on wood).

FWIW, even when a build upgrades with no problems, I sometimes take the opportunity to reinstall from scratch anyway, simply to clean out the accumulated cruft (more the result of my tinkering than anything else). Minimal-based builds are really quite versatile that way.
> …I know that I was sure having hell getting a desktop to run as some would display although wouldn't open anything.

The good is I learned a lot and I was confused a lot but I did finally get it to come together and work which was great.

At least I know the Ubuntu base is current and I may continue to see if I can get Xfce4 desktop working on it.
You may find the sticky in my sig "The Best 'buntu Flavour" to be useful guidance when installing things like DEs, WMs, etc.
> This may not be any real accomplishment for you Linux gurus but for a basic Linux user it's A-OK and I did have fun with it.
We all deserve to pat ourselves on the back when we conquer our own mountains. Your mountains are every bit as hard to climb for you as theirs are for Linux gurus. Kudos to you!
> Hmm a Frankenstein distro that's cool because all of my computers are Frankenstein builds using bits and pieces from here and there. :D
I always did think that the monster got a bad rap. Broadway should do a musical with the Monster as the sympathetic poor misunderstood hero: something like "Wicked".

---

### Post by tea for one on 2020-03-01
> **poorguy said:**
> At least I know the Ubuntu base is current and I may continue to see if I can get Xfce4 desktop working on it.

If you wish to explore a Xubuntu minimal installation, this ISO may help with the initial set-up.

[https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/)

Best wishes

---

### Post by poorguy on 2020-03-01
> **DuckHook said:**
> If you look at it as a quasi-rolling release, then the next time you invoke *do-release-upgrade*, you will be at 20.04 and completely up to date. No worries about EoL. The process should also upgrade the DE and whatever else you added. Just try to stay away from PPAs, third-party extensions, self-compiled binaries, etc. Those things tend to bork upgrades. But other than those, all of my Frankenstein's Monster builds have upgraded rather nicely (knock on wood).

Cool good to know.
I've for the most stick with what comes OOTB and don't use PPAs etc although have in the past with mixed results.

> **DuckHook said:**
> 
FWIW, even when a build upgrades with no problems, I sometimes take the opportunity to reinstall from scratch anyway, simply to clean out the accumulated cruft (more the result of my tinkering than anything else). Minimal-based builds are really quite versatile that way.

Yep clean installs work best from my experience.
I like to tinker and tweak my computers where possible to help out performance.

> **DuckHook said:**
> 
You may find the sticky in my sig "The Best 'buntu Flavour" to be useful guidance when installing things like DEs, WMs, etc.

Cool I'll check them out as tried and tested and proven resources is always helpful.

> **DuckHook said:**
> 
We all deserve to pat ourselves on the back when we conquer our own mountains. Your mountains are every bit as hard to climb for you as theirs are for Linux gurus. Kudos to you!

Thanks for the compliment and encouragement it's rewarding when things come together and work. 

> **DuckHook said:**
> 
I always did think that the monster got a bad rap. Broadway should do a musical with the Monster as the sympathetic poor misunderstood hero: something like "Wicked".

Me to as with this the monster was someone's project pieced together.


Thanks DuckHook.

---

### Post by poorguy on 2020-03-01
> **tea for one said:**
> If you wish to explore a Xubuntu minimal installation, this ISO may help with the initial set-up.

[https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/)

Best wishes

I tried the Xubuntu core a few years back although bailed due to my lack of Linux knowledge and patience.

When I started with this project I originally wanted the Xfce desktop although never could get it to work however I'm going to check out DuckHooks signature and see what I can learn and it's very possible I'm missing a few dependencies somewhere.

This is an adventure. ;)

---

### Post by DuckHook on 2020-03-01
> **tea for one said:**
> If you wish to explore a Xubuntu minimal installation, this ISO may help with the initial set-up.

[https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/)

Best wishes
I'm sure you know what you are doing and may even know this dev personally, but for general users out there who may come across this thread: it is not advisable to download OSes from unknown/untrusted sources. "Thar be dragons" and all that.

Best stick to trusted sources and the official repos.

---

### Post by poorguy on 2020-03-01
> **DuckHook said:**
> I'm sure you know what you are doing and may even know this dev personally, but for general users out there who may come across this thread: it is not advisable to download OSes from unknown/untrusted sources. "Thar be dragons" and all that.

Best stick to trusted sources and the official repos.

I use the Ubuntu Community link from the Ubuntu forums.

---

### Post by poorguy on 2020-03-01
Wow I'm like a kid in a candy store.

I just did a fresh install **Ubuntu minimal** with **LXDE Slim Desktop** and **added the bits and pieces needed **and everything is working awesome. :D

**DuckHook** I now truly understand your statement ***"The result is a bit of a Frankenstein's monster ("It lives! It lives!")." ***as that is exactly what it is.

It's time to start using my new creation.
[B]

[SIZE=3]Thanks to everyone for the suggestions / advice and help.[/SIZE][/B] \\:D/

---

### Post by soufianta on 2020-03-08
Hello guys,

I've created a thread on this subject. I was figuring out if a minimal ubuntu install was like every "minimal install" without any bloat. So if I'm reading correctly, a minimal install is like a beast but is highly customisable and reliable if we upgrade it until some pieces aren't supported anymore ? I'm trying to have an Arch like install (kiss) but with a deb based distro :-)

---

### Post by Chanath on 2020-03-09
> **DuckHook said:**
> I'm sure you know what you are doing and may even know this dev personally, but for general users out there who may come across this thread: it is not advisable to download OSes from unknown/untrusted sources. 

Unit193 >> [https://wiki.ubuntu.com/Unit193](https://wiki.ubuntu.com/Unit193)

---

