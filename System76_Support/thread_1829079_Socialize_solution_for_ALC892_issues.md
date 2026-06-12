---
title: "Socialize solution for ALC892 issues"
date: 2011-08-20
forum: System76 Support
---

### Post by bbossola on 2011-08-20
Hi, I recently bougth a machine with the same hardware of System76 Bonobo and I am experiencing problems with the ALC892 audio subsystem (plug headphones - speakers still play sound)

As appears that you solved this issue in your drivers, can you socialize the solution?

Cheers,

    Bruno

---

### Post by osx424242 on 2011-08-20
> **bbossola said:**
> As appears that you solved this issue in your drivers, can you socialize the solution?

Just an FYI, the driver software that System76 has written is open source and available for download from [http://planet76.com/repositories/](http://planet76.com/repositories/) ; it's just python so you can extract the files from the .deb and look through them yourself to see what they've done.  If you know the abbreviation of the model of computer you're looking for, it can be fairly straightforward to search for that string and find out what the driver is changing on the system.

---

### Post by bbossola on 2011-08-28
Thanks, I already downloaded the driver and it works exclusively on System76 machines (they are probably checking somewhere the model) that's the reason why I was asking to socialize the solution of a common problem (if you look for ALC892 issues on google you will find this is quite a hot topic)

Opening a DEB and digging into it in order to search a solution is not exactly what I was looking for... looks more like M$ reverse engineering... when I say "socializing" I mean it :)

@System76 can you please share your thought about this?

---

### Post by jdb on 2011-08-29
> **bbossola said:**
> Thanks, I already downloaded the driver and it works exclusively on System76 machines (they are probably checking somewhere the model) that's the reason why I was asking to socialize the solution of a common problem (if you look for ALC892 issues on google you will find this is quite a hot topic)

Opening a DEB and digging into it in order to search a solution is not exactly what I was looking for... looks more like M$ reverse engineering... when I say "socializing" I mean it :)

@System76 can you please share your thought about this?

It's just reading well commented Python source, nothing magic.
It's open source, it's intended to be read by anyone, not exactly reverse engineering.
The only reason i can think of that someone would be willing to take the
effort to do that, and it's not really that much effort,  is that they don't have a System76 computer.
Most of the people on this forum have System76 computers.
You'd probably be better of in a forum that someone who has your
brand of computer might be on.
If you take the time to look at the code (good learning experience)
and figure it out yourself, don't forget to socialize it :).

jdb

---

### Post by jbelmonte on 2011-08-29
I don't work for System76, but I pretty sure they send their fixes upstream to the Ubuntu developers so the fixes can get incorporated into future kernels.

---

### Post by isantop on 2011-08-30
If you've installed the .deb, then all of the python source code is located in /opt/system76/. You can browse it there, too.

---

### Post by bbossola on 2011-10-08
> **jdb said:**
> It's just reading well commented Python source, nothing magic.
It's open source, it's intended to be read by anyone, not exactly reverse engineering.
[...]
If you take the time to look at the code (good learning experience)
and figure it out yourself, don't forget to socialize it :).

jdb

Of course, and I quickly patched it. To be fair, a patch for my system is just one line of code, and I think that System76 could have afforded that. However, not all of Ubuntu users are developers keen to tackle the configuration of their system at that level. Ubuntu is a distro "for human being", a style that I personally appreciate (at the end of the day I ame a developer, not a sysadmin... please do not bother me about fixing your pc, your printer, your internet... if I only had a cent...) 

About socializing, I'd be happy to do that as the license is (as far as I can see) GPL. So, as soon as I get a formal confirmation from a system76 guy on this thread, I will do that.

p.s. the driver is improving the situation (headphone exclusion now works, and sound quality of speakers is much better) but still there's a lot of background noise recorded with the mic, with cracklings sometimes

---

### Post by isantop on 2011-10-10
You're free to share whatever fixes you'd like. You're even free to port the driver to other Hardware and operating systems as you see fit. System76 owns the artwork, but that's pretty simple to change. Other than that, all of the code is GPL.

I had a quick chat with one of the driver devs, and although he sees no problem with it, he's concerned that the driver isn't particularly valuable to a broader audience. We mostly use the driver to get support for specific cutting edge hardware, while we push those fixes upstream to get fixed for Ubuntu as a whole. For example, the audio issue you were having is now fixed in Ubuntu 11.10. Given this limited scope, the usefulness of the driver is a bit limited outside of System76.

You're, of course, free to share anything you learn about getting a particular problem solved.

---

