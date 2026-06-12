---
title: "My Ubuntu/Linux Experience - rant and questions"
date: 2008-02-06
forum: South Carolina Team - US
---

### Post by recluse2 on 2008-02-06
I just put Ubuntu 7.10 on my 2nd machine, this one is capable of running Compiz, so now I can fool with it for the first time without the live CD. I really like Compiz. It really adds to the user experience. It makes you feel like you have a really powerful computer, and with the ability of Linux to run nicely on older hardware it makes you feel like you have gotten the most out of the hardware you have spent your money on. I tried Compiz once before, but it did not run at all off the Live CD, so I never fooled with it again, but this leads me to a question for the Linux community as a whole.

One thing I have noticed in the process of experimenting on all of the Distros and different versions of Distro's is that each one seems to have its own distinct problems or pluses. For example: I tried Knoppix (various versions) on one PC. Some of my hardware worked on one version and some did not on a different version. You would think that I would gain functionality with the newest version and more software features would work, but this is not what I experienced - I lost some functionality and gained some functionality irregardless of whether it was a newer or older version of the Distro and even between the Distro's. I experienced the same thing on Ubuntu, gOS, PC Linux OS, Linspire, DSL, Knoppix STD, and Suse. 

I was wondering if you other guys have experienced the same issues.

I do have to admit, that over all it has gotten better, but I still feel somewhat iffy about upgrading to a newer version of a distro for fear of losing some functionality of my hardware, or a favorite software feature.

Ubuntu 7.10 has obviously gotten better than earlier versions of Ubuntu. I think I started with a version 5.xx and seen mainly nothing but improvement. I decided at v7.04 that the next version (in my Mind) would be "ready for prime-time" and that I would actually install it on a machine that I use daily. However, I still need my XP on at least 1 of my machines, for the simple fact that I use Newsleecher and there is no good Linux replacement that I have found, and I must have XP on my Laptop because of its portability, and increased chances of being lost or stolen, I use PGP Whole Disk Encryption to keep my banking and other passwords and data secure. Again, no Linux alternative.

Comments , suggestions, and airing of grievances welcome...

---

### Post by xarquid on 2008-02-06
> **recluse2 said:**
> 
One thing I have noticed in the process of experimenting on all of the Distros and different versions of Distro's is that each one seems to have its own distinct problems or pluses....I lost some functionality and gained some functionality irregardless of whether it was a newer or older version of the Distro and even between the Distro's. I experienced the same thing on Ubuntu, gOS, PC Linux OS, Linspire, DSL, Knoppix STD, and Suse....
I was wondering if you other guys have experienced the same issues.
.....
Comments , suggestions, and airing of grievances welcome...

Greetings!

Thank you for posting and welcome!

I will tell you, and be completely honest in my post (I always am, but you don't know me -- so I am just putting this out there). I will look to get to know you :-) Start talking more...you seem like a great person with insightful information. You would bring a lot to our community and help improve Ubuntu as a project overall.

Back to your rant/question. This is common in all distributions, especially on certain hardware setups (or PCs). For example, IBM laptops (Lenovo in specific) are usually guaranteed to support modern distros out of the box (Debian 3 or 4, Ubuntu current version or even the last version, SuSE current, Knoppix etc.). Some other PCs, perhaps like the one you are using, hardware support is still spotty.

While Linux developers are working hard to support hardware with the initial setup -- it's not always guaranteed. Some distros will work with some hardware (simply because of developmental choices when it comes to installer packages) and some will support other hardware choices (this is still very "spotty," as I used to the term earlier) when it comes down to WiFi chipsets (for example). 

I think you've experienced this first hand. A lot of times users must learn to correct this on their own. This is while Linux developers catch up with hardware (or hardware begins to release more open source drivers -- to better support the open source community, whether than so much proprietary code)...

You can usually do simple Google searches or searches on this Forum (which has a wealth of information) to help troubleshoot certain issues. And if you can't find something after looking, then feel free to post. I had a problem with my WiFi card a few years ago on a Debian installation so I simply did a search on Google for "IBM Lenovo Atheros WiFi Debian" and it yielded a ton of results. I realized it was as simple as downloading a file from one website and running a simple command. Sometimes, it's not this simple...but, this is how we learn :-)

Again, welcome! And I hope I provided some insight into my experience based on your insights thus far with distros. They all come with different "tastes" and different choices as far as hardware support is concerned...and eventually (and hopefully...) this will all be resolved.

Sincerely,

Craig Hufstetler / xq / xarquid

---

### Post by recluse2 on 2008-02-07
I look forward to getting to know you too xq, and that is what I am here for, to add something to the community and help spread Ubuntu because I love it.

I am quite familiar with searching Google and these forums to get the answers I need. I have been using the Internet regularly since 1995, and using computers intermittently since Apple II, and to parallel- going from XP to Ubuntu, for me, was like going from DOS to the first GUI on a mac when I was in 6th grade. It is a whole new, exiting experience. The first time I've been exited about anything with computers for a long time.

In regards to your answer, I figured that was pretty much what I was experiencing, and I guess it is to be expected with such a massive- global- open source project with so many developers and countless hardware choices. I think that the future of the Linux community is so bright, and I think that the best way to get there is possibly a single search-able clearing house for fixes to these problems.

For example: right now, the problem I am having is that I cannot boot into XP on this machine through GRUB. The problem is due to the fact that I have 3 drives on this PC. Drive 1 has XP on it and an Acronis True Image partition for backup of the XP install on that drive. Drive 2 is just a storage drive that is tightly integrated into that XP install in that it contains "My Documents" and the pagefile for XP, but it also allows me to use it for the Ubuntu Install as a storage device for whatever I want to put in it, and, I can still easily access everything I use daily in my XP install. Drive 3 is a very small 4Gb Drive that is exclusively Ubuntu. (I can have an outstanding amount of Apps and a modern operating system and still have space leftover for more on only a 4Gb Drive. (God I love Ubuntu!))

When I installed Ubuntu on the 4Gb drive It was a painless process that I feel a child could have done due to the insightful programming and ingenuity of the Linux community, but it apparently did not detect the XP install due to the configuration of this computer. Searching the Ubuntu Forums and Google gave me the answer I was looking for, and I edited the /boot/grub/menu.lst to reflect the XP install on the proper partition of the proper drive on this machine. While I was searching for the answer, I noticed countless threads in the forums from people having similar problems, and countless webpages and blog posts devoted to this very problem, which made me think of the idea of a single clearing house.

Wouldn't it be nice to be able to go to a single place, find the problem you are having and then find the single definitive answer to your problem, then the developer of the software could implement the fix in the future releases, so you could finally eliminate that entry from the clearing house because it wouldn't be a problem anymore?

This is just a suggestion, an idea that could possibly help the community, and possibly advance OSS to every PC in the world.

---

### Post by breaking on 2008-02-07
Alternatives:  pgp - use luks... it is cross platform.  though the ubuntu-alt-cd supports whole disk encryption i found it easier to do it manually. google search for "luks root howto"
I am currently running with my whole root encrypted and it works just fine.

Luks is:
GPL - no worries on freedoms
already integrated into ubuntu (and other distros)
integrated with hal and gnome-mount
ubuntu alt cd can make an encrypted root install!

General:
[http://blog.fubar.dk/?p=64](http://blog.fubar.dk/?p=64)
[http://searchenterpriselinux.techtar...196256,00.html](http://searchenterpriselinux.techtar...196256,00.html)

Luks linux automounter
cryptsetup (look in your package manager)

Windows luks tools:
[http://www.freeotfe.org/screenshots_pc.html](http://www.freeotfe.org/screenshots_pc.html)

ext2 for win:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

newsgroup downloader thingy:

enable your software sources (or just run Automatix once to do it for you)

then search for "newsgroup" in your package manager.

i found 4 of em just by doing this simple search.  there is probably more.

---

### Post by recluse2 on 2008-02-07
> **breaking said:**
> Alternatives:  pgp - use luks... it is cross platform.  though the ubuntu-alt-cd supports whole disk encryption i found it easier to do it manually. google search for "luks root howto"
I am currently running with my whole root encrypted and it works just fine.

First time I ever heard of this app, I might give it a try, I should mention that TrueCrypt just came out with a new version today that has Whole Disk Encryption, I might give it a try also, as for your recommendations for Newsgroups, I tried what you suggested long ago and nothing close. There is the option to run Newsleecher in Wine, but not 100%.

---

