---
title: "Audacious update tangle..."
date: 2010-04-17
forum: Ubuntu Studio
---

### Post by mango42 on 2010-04-17
Hi,

In a recent update, Audacious, a program I never use got into a mess (because I hadn't noticed it was listed for upgrade) with some odd looking dependencies. Would some kind soul be prepared to help me untangle the Catch22 I find myself in?

Crash Error report info panel sez:-

> Package problem - Sorry, the package "audacious-plugins 2.3-karmic~ppa1" failed to install or upgrade

and when I attempt to send the report, I get:

> The problem cannot be reported: This is not a genuine Ubuntu package

Back to the commandline, doing:

```
~$ sudo apt-get install -f
```

provides the following:-

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  audacious-plugins audacious-plugins-extra
The following packages will be upgraded:
  audacious-plugins audacious-plugins-extra
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2,340kB of archives.
After this operation, 1,839kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 143030 files and directories currently installed.)
Preparing to replace audacious-plugins-extra 2.1-1ubuntu1 (using .../audacious-plugins-extra_2.2-karmic~ppa3_i386.deb) ...
Unpacking replacement audacious-plugins-extra ...
dpkg: error processing /var/cache/apt/archives/audacious-plugins-extra_2.2-karmic~ppa3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/audacious/Output/crossfade.so', which is also in package audacious-plugins 0:2.1-1ubuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace audacious-plugins 2.1-1ubuntu1 (using .../audacious-plugins_2.2-karmic~ppa3_i386.deb) ...
Unpacking replacement audacious-plugins ...
dpkg: error processing /var/cache/apt/archives/audacious-plugins_2.2-karmic~ppa3_i386.deb (--unpack):
 trying to overwrite '/usr/share/audacious/paranormal/Presets/nenolod_-_technicolour_nightmare.pnv', which is also in package audacious-plugins-extra 0:2.1-1ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/audacious-plugins-extra_2.2-karmic~ppa3_i386.deb
 /var/cache/apt/archives/audacious-plugins_2.2-karmic~ppa3_i386.deb
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_motin_ppa_ubuntu_dists_karmic_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)


and this is where I run into a loop, as issuing:

```
sudo apt-get update
```

eventually returns:-

> Reading package lists... Done
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_motin_ppa_ubuntu_dists_karmic_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


Er, ...help? :confused:

---

### Post by philip5 on 2010-04-17
It's a content conflict (Should be fixed but haven't done it yet). If you uninstall audacious and reinstall it instead of just update it you should have it working. The problem is just when you do the updated and not when you use it afterward.

---

### Post by mango42 on 2010-04-18
Thanks for your suggestion, **philip5** but I definitely don't dare to uninstall this Audacious player because when I try that from Synaptic it tells me that **ubuntu-studio** must be removed also and that's the very *last* thing I want to happen now that I have a stable and smooth system.

Well, it was smooth until this problem turned up - now I cannot install *anything* new at all without a crash report halting everything.

Hey ho - my mistake for not noticing the update in the first place, I guess...

---

### Post by philip5 on 2010-04-18
> **mango42 said:**
> Thanks for your suggestion, **philip5** but I definitely don't dare to uninstall this Audacious player because when I try that from Synaptic it tells me that **ubuntu-studio** must be removed also and that's the very *last* thing I want to happen now that I have a stable and smooth system.

Well, it was smooth until this problem turned up - now I cannot install *anything* new at all without a crash report halting everything.

Hey ho - my mistake for not noticing the update in the first place, I guess...
ubuntu-studio is just a meta package with no content so it's mostly used for installing a bunch of pre-selected packages in a row. if you like then you can remove audacious that takes with it ubuntu-studio and then install them both again. That won't effect your system more than you will get an updated version of audacious (in this case).

This is the case if ubuntu-studio is the only package that will be unistalled. If there also are others then they might need other attendencies.

---

### Post by mango42 on 2010-04-19
> **philip5 said:**
> ubuntu-studio is just a meta package with no content so it's mostly used for installing a bunch of pre-selected packages in a row.


Thanks very much once again for your advice - I wasn't aware of that - to a user (at least us tyros!), it just looks like Synaptic is asking to wipe out 'Ubuntu Studio' in its entirety ;-)

So much to learn (and unlearn from that other OS mindset), so little time...

---

