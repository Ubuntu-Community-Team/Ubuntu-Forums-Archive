---
title: "[SOLVED] Ubuntuzilla 4.3.0-amd64.deb is for i386 architecture?!"
date: 2007-08-18
forum: Ubuntuzilla
---

### Post by wilberfan on 2007-08-18
I just downloaded and tried to install the ubuntuzilla-4.3.0-0ubuntu1-amd64.deb on my Feisty 64-bit machine, and got the following!:
> [COLOR="Red"]
Error: Wrong architecture 'i386'[/COLOR]

WTF?!

---

### Post by lrosa on 2007-08-18
Confirmed. Got the same problem.

---

### Post by nanotube on 2007-08-18
> **wilberfan said:**
> I just downloaded and tried to install the ubuntuzilla-4.3.0-0ubuntu1-amd64.deb on my Feisty 64-bit machine, and got the following!:


WTF?!

hmm.. exactly at what point did you get that error? during running the ubuntuzilla script? during running the install of the .deb?

---

### Post by wilberfan on 2007-08-18
> **nanotube said:**
> hmm.. exactly at what point did you get that error? during running the ubuntuzilla script? during running the install of the .deb?

It was immediately upon trying to install the .deb....

---

### Post by nanotube on 2007-08-18
whoops! i accidentally forgot to set the "architecture" part of the .deb control file to amd64, so it got set to the default of i386. i have just put up the fixed 4.3.0 release for amd64, please try again. ;) 

thanks for reporting the error!

---

### Post by wilberfan on 2007-08-18
Worked fine that time!

The .deb installed perfectly--and the script itself ran fine.

:guitar:

---

### Post by nanotube on 2007-08-18
great! thanks for testing! :)

just to make sure, did the mozilla software that you installed using ubuntuzilla script work fine, too?

---

### Post by wilberfan on 2007-08-18
> **nanotube said:**
> great! thanks for testing! :)

just to make sure, did the mozilla software that you installed using ubuntuzilla script work fine, too?

The Thunderbird (2.0.0.6) that I installed via the Ubuntuzilla script installed and runs fine--except for the failure of the audio-notify feature.   (Please see latest posting in [this thread]("http://ubuntuforums.org/showpost.php?p=3213912&postcount=17")!)

---

### Post by nanotube on 2007-08-18
> **wilberfan said:**
> The Thunderbird (2.0.0.6) that I installed via the Ubuntuzilla script installed and runs fine--except for the failure of the audio-notify feature.   (Please see latest posting in [this thread]("http://ubuntuforums.org/showpost.php?p=3213912&postcount=17")!)

aha... well... so we're still in the same boat regarding audio-notify... i would be very curious to see if other 64bit users experience the same problem, or if it is specific to your particular setup. i hope i can get some more testers :)

---

### Post by lrosa on 2007-08-19
The script now works as expected, thanks! 
Unfortunately the sounf notification does not work.


ciao,
luigi

---

### Post by nanotube on 2007-08-19
hey, could either or both of you 64bit users check to see if you have package lib64asound2 package installed? (the lib32asound2 should also have been installed, as a dependency of the ubuntuzilla package).

thanks!

---

### Post by lrosa on 2007-08-19
I couldn't find such package in Ubuntu repositories for Ubuntu 7 AMD64.

According to [http://packages.ubuntu.com/dapper/libs/lib64asound2](http://packages.ubuntu.com/dapper/libs/lib64asound2) is only available for PowerPC

I found references to lib64asound2 for AMD64 for previous versions of Ubuntu.

:confused:

---

### Post by nanotube on 2007-08-19
hi, 
oh yes, sorry, my fault. ;) i see now, according to [http://packages.ubuntu.com/feisty/libs/lib64asound2](http://packages.ubuntu.com/feisty/libs/lib64asound2)
it is only for i386 and powerpc

[http://packages.ubuntu.com/feisty/libs/libasound2](http://packages.ubuntu.com/feisty/libs/libasound2)
however should be available for amd64. could you check that one?

and also
[http://packages.ubuntu.com/feisty/libs/libesd-alsa0](http://packages.ubuntu.com/feisty/libs/libesd-alsa0)

and also
[http://packages.ubuntu.com/feisty/libs/libasound2-plugins](http://packages.ubuntu.com/feisty/libs/libasound2-plugins)

if any of those are not installed, could you check if installing them from the repos (and rebooting, for good measure) makes the audio notify work?

thanks! :)

---

### Post by lrosa on 2007-08-19
> **nanotube said:**
> [http://packages.ubuntu.com/feisty/libs/libasound2](http://packages.ubuntu.com/feisty/libs/libasound2)
however should be available for amd64. could you check that one?

I have it. Just the library, not the -dev and -plugins

> **nanotube said:**
> and also
[http://packages.ubuntu.com/feisty/libs/libesd-alsa0](http://packages.ubuntu.com/feisty/libs/libesd-alsa0)

I have it too.

> **nanotube said:**
> and also
[http://packages.ubuntu.com/feisty/libs/libasound2-plugins](http://packages.ubuntu.com/feisty/libs/libasound2-plugins)

No, not this one. I have installed it along with the dependency libpulse0. Unfortunately nothing changed.
I tried to change the .WAV file without any luck. Of course the WAV files play fine with Totem media player.

Thank you for your support.

---

### Post by nanotube on 2007-08-19
Thanks for your quick response!

well, at this point, i'm all out of ideas for now. my only hope is that wilberfan will get something out of contacting mozilla's own support forum /bugzilla (or you could do that as well, if you feel up to it).

see this thread for more info (and messages from error console):
[http://ubuntuforums.org/showthread.php?p=3213912](http://ubuntuforums.org/showthread.php?p=3213912)

Thanks!

---

### Post by wilberfan on 2007-08-19
> **nanotube said:**
> Thanks for your quick response!

...my only hope is that wilberfan will get something out of contacting mozilla's own support forum /bugzilla (or you could do that as well, if you feel up to it).

Not to be a party pooper, but to be honest, I'm too new at this to really know how or who to contact at Mozilla...  :confused:

I'm certainly interested in learning about what's causing the problem--but I'm not sure I'm the best qualified to be the torch bearer in this crusade!   :lolflag:

---

### Post by nanotube on 2007-08-19
> **wilberfan said:**
> Not to be a party pooper, but to be honest, I'm too new at this to really know how or who to contact at Mozilla...  :confused:

I'm certainly interested in learning about what's causing the problem--but I'm not sure I'm the best qualified to be the torch bearer in this crusade!   :lolflag:

ok, then i'll try opening a thread/bug report with mozilla, and post the link to it back here so you can take a look. since i don't actually have 64bit ubuntu, if they ask me to perform any tests, i won't be able to - so that'll be up to you. :)

---

### Post by wilberfan on 2007-08-19
I don't mind testing something -- if it's pitched at my level...!  :)

---

### Post by kiwi-pete on 2008-12-09
Scuse me for seeming a bit of a noob, but where can I get a Lives.deb amd64 file for Ubuntu 8.10 please?

---

### Post by nanotube on 2008-12-09
> **kiwi-pete said:**
> Scuse me for seeming a bit of a noob, but where can I get a Lives.deb amd64 file for Ubuntu 8.10 please?

what's a "Lives.deb" ? if you are looking for the ubuntuzilla amd64 deb (which is what this thread is about), you can get it from [http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

### Post by kiwi-pete on 2008-12-10
):P Thanks, sorted now.

---

