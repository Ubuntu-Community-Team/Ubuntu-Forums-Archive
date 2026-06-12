---
title: "Linux Kernel 4.4"
date: 2020-07-21
forum: Ubuntu, Linux and OS Chat
---

### Post by O)9(yo&amp;# on 2020-07-21
I am currently running Ubuntu 14.04, with Extended Security Maintenance. I recently saw the following info concerning Linux Kernel 4.4:

"[COLOR=#202122][FONT=sans-serif]16th LTS release, maintained from January 2016 to February 2022.[/FONT][/COLOR][SUP][[70]]("https://en.wikipedia.org/wiki/Linux_kernel_version_history#cite_note-Active_kernel_releases-70")[/SUP][SUP][[171]]("https://en.wikipedia.org/wiki/Linux_kernel_version_history#cite_note-171")[/SUP][COLOR=#202122][FONT=sans-serif] Canonical will provide extended support until April 2021.[/FONT][/COLOR][SUP][[172]]("https://en.wikipedia.org/wiki/Linux_kernel_version_history#cite_note-172")[/SUP][COLOR=#202122][FONT=sans-serif] As the first kernel selected for Super Long Term Support (SLTS), the Civil Infrastructure Platform will provide support until at least 2026, possibly until 2036.[/FONT][/COLOR][COLOR=#202122][FONT=sans-serif]   ([/FONT][/COLOR]https://en.wikipedia.org/wiki/Linux_kernel_version_history)

So, what operating systems could I use with this kernel, going forward in time? for example, could I upgrade 14.04 to 16.04, and keep this kernel? And are there any other Linux systems I could use with this kernel into the next several years that it has support? Could I for example use a 'buntu 18- or 20-based system, keeping this kernel? 

The reason is I am using an old computer with original graphics, that needs Nvidia 304 drivers, and kernel 4.4 is the last one that supports this driver.

---

### Post by mastablasta on 2020-07-22
> **michael_diemer said:**
> I am currently running Ubuntu 14.04, with Extended Security Maintenance. I recently saw the following info concerning Linux Kernel 4.4:

"[COLOR=#202122][FONT=sans-serif]16th LTS release, maintained from January 2016 to February 2022.[/FONT][/COLOR][SUP][[70]]("https://en.wikipedia.org/wiki/Linux_kernel_version_history#cite_note-Active_kernel_releases-70")[/SUP][SUP][[171]]("https://en.wikipedia.org/wiki/Linux_kernel_version_history#cite_note-171")[/SUP][COLOR=#202122][FONT=sans-serif] Canonical will provide extended support until April 2021.[/FONT][/COLOR][SUP][[172]]("https://en.wikipedia.org/wiki/Linux_kernel_version_history#cite_note-172")[/SUP][COLOR=#202122][FONT=sans-serif] As the first kernel selected for Super Long Term Support (SLTS), the Civil Infrastructure Platform will provide support until at least 2026, possibly until 2036.[/FONT][/COLOR][COLOR=#202122][FONT=sans-serif]   ([/FONT][/COLOR]https://en.wikipedia.org/wiki/Linux_kernel_version_history)

So, what operating systems could I use with this kernel, going forward in time? for example, could I upgrade 14.04 to 16.04, and keep this kernel? And are there any other Linux systems I could use with this kernel into the next several years that it has support? Could I for example use a 'buntu 18- or 20-based system, keeping this kernel? 

The reason is I am using an old computer with original graphics, that needs Nvidia 304 drivers, and kernel 4.4 is the last one that supports this driver.

debian maybe? ELTS: [https://wiki.debian.org/LTS/Extended](https://wiki.debian.org/LTS/Extended)    or centOS.? 
same as Red hat: [https://access.redhat.com/support/policy/updates/errata](https://access.redhat.com/support/policy/updates/errata)
EOL: [https://wiki.centos.org/FAQ/General#What_is_the_support_.27.27end_of_life.27.27_for_each_CentOS_release.3F](https://wiki.centos.org/FAQ/General#What_is_the_support_.27.27end_of_life.27.27_for_each_CentOS_release.3F)


CIP& debian for SLTS kernel:  [https://lwn.net/Articles/749530/](https://lwn.net/Articles/749530/)

the issue is not just kernel but also xserver and xorg. but let us know if you find a good option. i also have old PC with nvidia.

i had similar problem but different chip (AMD). 14.04 had proprietary drivers, 16.04 support was dropped (xserver) and opensource were not on par. 18.04 opensource work well, so i installed that. so the idea is that it might be good to test the opensource noveau driver every once in a while to see if it works well or not. mazbe even with latest version. or just monitor the state of driver at least, to see if all features important to you are enabled and working. that is what i did with radeon drivers. i followed their table. and once i saw most stuff is supported i switched to opensource.

---

### Post by O)9(yo&amp;# on 2020-07-22
> **mastablasta said:**
> debian maybe? ELTS: [https://wiki.debian.org/LTS/Extended](https://wiki.debian.org/LTS/Extended)    or centOS.? 
same as Red hat: [https://access.redhat.com/support/policy/updates/errata](https://access.redhat.com/support/policy/updates/errata)
EOL: [https://wiki.centos.org/FAQ/General#What_is_the_support_.27.27end_of_life.27.27_for_each_CentOS_release.3F](https://wiki.centos.org/FAQ/General#What_is_the_support_.27.27end_of_life.27.27_for_each_CentOS_release.3F)


CIP& debian for SLTS kernel:  [https://lwn.net/Articles/749530/](https://lwn.net/Articles/749530/)

the issue is not just kernel but also xserver and xorg. but let us know if you find a good option. i also have old PC with nvidia.

i had similar problem but different chip (AMD). 14.04 had proprietary drivers, 16.04 support was dropped (xserver) and opensource were not on par. 18.04 opensource work well, so i installed that. so the idea is that it might be good to test the opensource noveau driver every once in a while to see if it works well or not. mazbe even with latest version. or just monitor the state of driver at least, to see if all features important to you are enabled and working. that is what i did with radeon drivers. i followed their table. and once i saw most stuff is supported i switched to opensource.

Ah, xserver and xorg are part of the problem, I'm not surprised. While many Linuxers despise Nvidia, I have had far more problems with open source drivers.

As to newer systems maybe working better, I tried a bunch. Zorin 12 and 15; Xubuntu 16, Mubuntu 16, even Lubuntu 16 were all no go's. Same for Lite 4 and LXLE 18 (16 may have worked but had other problems). I assumed anything later than 14 is unlikely to work, except maybe the ultra lights, like Puppy, Vector etc. Bodhi did work, but it's kind of weird. The Nouveau drivers were the culprit in all of these. 

I'll check into the links you provided, but I'm not a fan of Debian. Never tried Centos; Tried Fedora awhile back but wasn't my cup of Joe either.

---

### Post by mastablasta on 2020-07-23
to get latest nouveau you should either load latest kernel i Ubuntu or run a more edge distro (e.g. Manjaro). it could be there is also a PPA that will just patch the current kernel with latest drivers.

Debian is just as Ubuntu. if you don't have latest hardware, then Debian stable is a very good solution.  the only thing is that things preinstalled in Ubuntu have to be installed. so maybe instead of pure debian a better choice is a distro that make sit easier to use. Bunsenlabs Linux is one of them. not sure how they do it now, but in old days the stuff Ubuntu install by default was installed by simple script that asked user "do you want this, do you want that" etc. for example it would say "Do you want libre office? Y/n "
then you have those aimed at older PC like AntiX and MX Linux. note you can just install the desktop of your choice to these if you don't like the default.

---

