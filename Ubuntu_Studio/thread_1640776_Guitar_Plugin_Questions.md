---
title: "Guitar Plugin Questions"
date: 2010-12-08
forum: Ubuntu Studio
---

### Post by dawiba on 2010-12-08
Hi Everyone

I've been using Windows for most of the last year and in the process I've been using VST plugins.

One of those plugins was Amplitube. I know there's Guitarix and Rakkarack in Linux and I managed to install Rakkarack but got nowhere with Guitarix. I'd like to stick to Linux plugins as far as possible, so

Can anyone offer help with installing Guitarix?
Are there any other amp sim plugins in Linux?

Thanks

---

### Post by AutoStatic on 2010-12-08
If you use Lucid Lynx then I've got the latest version in my PPA: [https://launchpad.net/~autostatic/+archive/ppa](https://launchpad.net/~autostatic/+archive/ppa)

And you could try Jack-Rack and maybe some of the presets from this site: [http://offog.org/stuff/racks/](http://offog.org/stuff/racks/)

But Guitarix is by far the most versatile and best-sounding alternative when it comes to amp simulation. Especially with some decent IR files.

---

### Post by dawiba on 2010-12-08
Thanks Autostatic

I tried installing Guitarix again but no joy. I guess there must be something I'm not doing right as it's been a while since I used Ubuntu. Either that or it is difficult to install, which wouldn't make sense.

I'm using 10.10 (Meerkat?) so I guess I can't use your PPA. Thanks anyway.

---

### Post by sgx on 2010-12-08
> **dawiba said:**
> Thanks Autostatic

I tried installing Guitarix again but no joy. I guess there must be something I'm not doing right as it's been a while since I used Ubuntu. Either that or it is difficult to install, which wouldn't make sense.

I'm using 10.10 (Meerkat?) so I guess I can't use your PPA. Thanks anyway.

So until I work out how to install, it's the Digitech pedal for just now :)
Hi, for guitarix,

libzita-convolver2_2.0.0-2.1_i386.deb

was needed for guitarix on my setup,
so you might experiment with a few versions of it. Rackarrack is great for fx, but you'll want to go through each soundset, and adjust the volumes, as some are way too loud, and save the set. The help section is also a great read, and explains some details and new capabilities.

The calf plugins are also excellent.

Cheers
You can manually download the file from many PPAs, click 
'View package details' in the fine print. Click on the one you want, you'll see something like

------------------------------------------------------------------------------------------------------------

Available diffs

    * diff from 0.0.18.5-0ubuntu1 (in Ubuntu) to 0.0.19+git20101115-0lucid0~autostatic0 (497.4 KiB)

Builds

    * [FULLYBUILT] amd64
    * [FULLYBUILT] i386

Built packages

    * calf-plugins pack of audio plugins - effects and instruments

Package files

    * calf-plugins_0.0.19+git20101115-0lucid0~autostatic0_amd64.deb (5.0 MiB)
    * calf-plugins_0.0.19+git20101115-0lucid0~autostatic0_i386.deb (4.8 MiB)
    * calf_0.0.19+git20101115-0lucid0~autostatic0.dsc (1.3 KiB)
    * calf_0.0.19+git20101115-0lucid0~autostatic0.tar.gz (11.4 MiB)

-------------------------------------------------------------------------------------------------------------
There may be dependencies to fetch from

[http://www.debian.org/distrib/packages#view](http://www.debian.org/distrib/packages#view)

and experiment with versions.

Cheers

---

### Post by dawiba on 2010-12-09
Thanks sgx

I followed your instructions and was able to install Guitarix from Autostatic's PPA. It seemed to work fine, then.........

Because I'd been installing/uninstalling and generally messing around with lots of different software, I did

```
sudo apt-get autoremove
```

and

```
sudo apt-get autoclean
```

Lo and behold I couldn't start Jack because jackd had been uninstalled. So I reinstalled using Synaptic but it wanted to uninstall Guitarix in the process. So that's where I am just now with Jack reinstalled and Guitarix uninstalled. I'm happy to use my pedal for guitar sounds in Linux just now, so I'm not bothered about having Guitarix installed at the moment.

Incidentally, I installed jackd2. Would that be the right one for Ubuntu 10.10? It seems to work fine (for that matter, so does jackd1 :))

Thanks for the advice on Calf plugins. I had already installed them and they are pretty good. I'm also trying out some linuxdsp plugins which I'm also liking. My wallet might have to come out for them :D

---

### Post by sgx on 2010-12-10
;) If it ain't broke, don't fix it ;)

I used to tinker a lot, but forget more than I learn.
Hopefully jack2 and ardour will be on the 2011 agenda.

You'll get it working, keep notes :)
Cheers

---

