---
title: "reconsidering"
date: 2005-07-07
forum: The Cafe
---

### Post by KezzerDrix on 2005-07-07
Hello,

I tried Ubuntu once before, I liked it and was even getting used to gnome.  However, I was having some issues that made me leave.

A. I could not get my Tv card to work and I asked several times for help and recieved no answers.

B. Sound issues, I could not play ut2004 without pulling up a terminal and typing in killall -9 esd.  This was irratating more than anything else, but would sometimes lock up my pc if I forgot to do it and would always result in no sound if I forgot.

I am wondering if these sound issues have been reconciled? And if the hardware support has gotten better?

Why would I want to come back?
A. The community
B. The repository
C. Metadistro updated every 6 months
D. Just recieved a free cd in the mail :)

Can ubuntu use any deb? If I find a deb that I want to use but is not in Ubuntu's repository can I still use it?

Thanks
Kezz

---

### Post by nocturn on 2005-07-07
Welcome back

A lot of deb files will work.  Some are build for Debian however, they might work but if they depend on newer or older software then Ubuntu has, they will fail (because of dependencies).

There's no harm in trying though.

---

### Post by Lord Illidan on 2005-07-07
[QUOTE=KezzerDrix]Hello,

Can ubuntu use any deb? If I find a deb that I want to use but is not in Ubuntu's repository can I still use it?

Thanks
Kezz[/QUOTE]
Well, yes, if you have the dependencies..

just do : sudo dpkg -i *****.deb

---

### Post by frodon on 2005-07-07
[QUOTE=KezzerDrix]Can ubuntu use any deb? If I find a deb that I want to use but is not in Ubuntu's repository can I still use it?[/QUOTE]
Of course you can !
All you need is to download the .deb file and type :  ```
suso dpkg -i your_deb_file.deb
```
I can't help you for your tv card because I have never had problems with my tv card (miro pctv), maybe your tvcard is not really compatible.

---

### Post by Wolki on 2005-07-07
[QUOTE=KezzerDrix]
A. I could not get my Tv card to work and I asked several times for help and recieved no answers.[/quote]

Probably because noone had experience with your tv card. I suggest getting linux compatible one.

> B. Sound issues, I could not play ut2004 without pulling up a terminal and typing in killall -9 esd.  This was irratating more than anything else, but would sometimes lock up my pc if I forgot to do it and would always result in no sound if I forgot.

Write a simple shell script that kills esd, starts ut2004 and restarts esd after ut2004 exits. I'm sure someone can help you with that, it should be really easy. Or just kill esd at startup. However, without esd you likely won't be able to hear sounds from multiple sources at the same time, depending on your hardware.

> Can ubuntu use any deb? If I find a deb that I want to use but is not in Ubuntu's repository can I still use it?

If the dependencies are covered by ubuntu surely. A lot of the new debian packages depend on a newer version of clib than Hoary has, and won't work (esp. do not try to install that version of clib on ubuntu). Usually, it's better to try to get this package into universe or backports.

---

### Post by poofyhairguy on 2005-07-07
[QUOTE=KezzerDrix]
A. I could not get my Tv card to work and I asked several times for help and recieved no answers.[/QUOTE]

If you install the program "tvtime" and it works, good, if not....

> B. Sound issues, I could not play ut2004 without pulling up a terminal and typing in killall -9 esd.  This was irratating more than anything else, but would sometimes lock up my pc if I forgot to do it and would always result in no sound if I forgot.

That doesn't get fixed to next release in October.

> 
Can ubuntu use any deb? If I find a deb that I want to use but is not in Ubuntu's repository can I still use it?


You can try. I use random debs....

---

### Post by KezzerDrix on 2005-07-07
My tv card is an aver studio, it has worked with every distro I have tried except this one.   Maybe, once I reinstall I can try to find someone with an answer.

I think I can kill esd in gnome and tell it to use alsa only.

That is cool about the random debs thanks for the tips.

Kezz

---

### Post by aysiu on 2005-07-07
[QUOTE=KezzerDrix]My tv card is an aver studio, it has worked with every distro I have tried except this one.   Maybe, once I reinstall I can try to find someone with an answer.

I think I can kill esd in gnome and tell it to use alsa only.

That is cool about the random debs thanks for the tips.

Kezz[/QUOTE] If it worked with every other distro, is there any reason you want to use Ubuntu in particular? I love Ubuntu, but it works with my hardware. If Ubuntu doesn't work with your hardware, use something else. It's not worth the effort.

---

### Post by KezzerDrix on 2005-07-08
I always find it interesting when people say "use something else" I stated my reasons for reconsidering Ubuntu in my first post.  I am simply curious as to if it has been fixed or if a fix may be available for me.  I have found a possible cure for my sound issues and if I can get the tvcard working Ubuntu may be the right distro for me.  I currently use PCLinuxos, it is absolutely wonderful, the only draw back is that the repository seems a little limited, and I have had some trouble installing third party software that there are debs for so I want to try ubuntu again.  No distro seems to have it all correct.  So I will probably install windows/pclinux/ubuntu and see which one of the linux versions win out.

---

### Post by aysiu on 2005-07-08
[QUOTE=KezzerDrix]I always find it interesting when people say "use something else" I stated my reasons for reconsidering Ubuntu in my first post.[/QUOTE] I understand. Of course your reasons for reconsidering Ubuntu are perfectly fine. In fact, they're the reasons I use Ubuntu myself, but I don't have TV card and sound card issues that you have. And what good is having a "good community" if they can't answer your questions about your tv card? The "good community" is good for me, because it answers all my questions.

The truth is that, for the most part, Linux is Linux. It's a lot easier to add repositories than it is to get hardware to be detected properly. And a lot of the suggestions and help this community offers can be applied to any distro.

---

### Post by poofyhairguy on 2005-07-08
[QUOTE=KezzerDrix]  I am simply curious as to if it has been fixed or if a fix may be available for me. [/QUOTE]

Did you file a bug report last time? We have not had another release yet...but if you filled (or will file) a bug report then maybe that problem will be fixed by then....

---

### Post by KezzerDrix on 2005-07-08
No, I didn't but if I have the same problem this time I will. :)

---

### Post by poofyhairguy on 2005-07-08
[QUOTE=KezzerDrix]No, I didn't but if I have the same problem this time I will. :)[/QUOTE]

Thanks...thats how OSS software works and how things get better.

---

### Post by KezzerDrix on 2005-07-08
The first time I tried Ubuntu I was really new.  I have learned alot since then and forgot even more of it. :)

---

