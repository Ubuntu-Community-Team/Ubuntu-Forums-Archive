---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1) while trying upgrade disto"
date: 2015-07-23
forum: Server Platforms
---

### Post by Thachakrit_Sonthi on 2015-07-23
Hi All,
This is my first post on this forum. I really need your helps. 

I'm using Ubuntu Server 14.04  (3.13.0-44-generic)
Today I run the command to upgrade distro

[HTML]sudo apt-get dist-upgrade[/HTML]

But it's not working well and show me a message >> You might want to run 'apt-get -f install' to correct these.
So I follow the recommendation. It looks good the the beginning but the process could not be done I got error messages like these.

[HTML]Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-58-generic_3.13.0-58.97_amd64.deb
 /var/cache/apt/archives/linux-image-3.13.0-55-generic_3.13.0-55.94_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/HTML]

-_- That make me feeling bad. Please help..

Thank you,

---

### Post by Thachakrit_Sonthi on 2015-07-23
Finally I know how to fix the issue. I found the solution from [http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-can%27t-clear-boot-because-of-dependencies-4175490871/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-can%27t-clear-boot-because-of-dependencies-4175490871/) 
 In my case, when I take look the  message. The system told that "failed to write (No space left on device)  in /boot partition"  It is because of too many old kernel versions. 

First go to /boot partition to see what are inside. Then remove the older versions.

[HTML]sudo apt-get remove linux-image-3.xxx-generic[/HTML]

Replace "xxx" which the kernel version you want to remove. Until you have enough space.

:)

---

### Post by v3.xx on 2015-07-23
There are several ways to remove old kernels.  This may help in future searches.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9)

---

