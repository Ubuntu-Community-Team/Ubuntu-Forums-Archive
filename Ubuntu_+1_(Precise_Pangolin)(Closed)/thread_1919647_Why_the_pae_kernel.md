---
title: "Why the pae kernel"
date: 2012-02-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-02-03
**Update**: Please read this:

[http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM)

> The Ubuntu Technical Board weighed the pros and cons of non-PAE support and came to a decision. The board has decided they will support the non-PAE kernel option until the Ubuntu 12.10 release, so there will still be support in Ubuntu 12.04 LTS. The default i386 kernel in Ubuntu 12.04 LTS will become the PAE-enabled kernel, but the non-PAE flavor will be available.

Below are the details in full from the non-PAE discussion.

    Non-PAE kernel disposition
    * Kernel team would like to drop non-PAE kernel soon
    * TB members generally feel that (1) dropping the current default kernel is too much of a step, and (2) there is still a significant number of users which have non-PAE systems, based on Launchpad bug report data and an ubuntu-devel@ strawpoll
    * Maintaining the extra flavour is not much extra work, and not comparable to e. g. the -ti-omap4 kernel which is an entirely separate source tree
    * We need a way to prevent upgrades for non-PAE systems. Some options were mentioned:
    * Add update-manager check to not offer the upgrade if PAE is not available
    * Add libc6/linux preinst to abort the upgrade early if PAE is not available; that's not the best failure mode, but will prevent a safety net for users of `apt-get dist-upgrade`
    * '''Agreements''':
    **[COLOR="Red"]* Switch precise over to PAE kernel by default on i386; we retain the option to revert if it causes too much fallout (Colin)[/COLOR]**
    * Drop non-PAE flavour in 12.10; this will give non-PAE systems another 5 years of life time, which is considered enough
    * Further discuss upgrade strategy/checks

You'll notice that I specifically highlighted "Switch precise over to PAE kernel by default on i386; we retain the option to revert if it causes too much fallout", therefore **[COLOR="Red"]it is going to be extremely imperative that those with effected hardware file new bug reports[/COLOR]**!

I have no hardware effected by this change but you can read a brief summary of what my personal goals are regarding this here:

[http://ubuntuforums.org/showpost.php?p=11677511&postcount=100](http://ubuntuforums.org/showpost.php?p=11677511&postcount=100)

******************************

I just completed alpha 2 iso-testing and ran into a number of issues, one question I have is why a fresh install uses the "pae" kernel :confused:

Fresh install:

Linux lance-desktop 3.2.0-12-generic-pae #21-Ubuntu SMP Tue Jan 31 20:44:35 UTC 2012 i686 i686 i386 GNU/Linux

Upgrade from Oneiric:

Linux lance-desktop 3.2.0-12-generic #21-Ubuntu SMP Tue Jan 31 18:40:37 UTC 2012 i686 i686 i386 GNU/Linux

The hardware involved is:

Intel(R) Atom(TM) CPU  230   @ 1.60GHz
Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

Sorry to be so clueless ;)

---

### Post by sgage on 2012-02-03
PAE is a gimmick for allowing a 32-bit installation to access more than about 3.2 GB of RAM. If you're installing a 32-bit version, and the installer detects more than 3 GB of RAM (or maybe even if you don't - not sure), it gives you the PAE kernel. The non-PAE kernel is available in the grub menu under "Previous Linux Versions".

---

### Post by collisionystm on 2012-02-03
Technically 32 bit should be able to handle 4gb of memory.

Regardless PAE is just a hack. Time to upgrade into the current century and get a 64 bit system.

---

### Post by bmbaker on 2012-02-03
is there a way to convert a 32bit system to 64bit or do you have todo a new install?

---

### Post by collisionystm on 2012-02-03
> **bmbaker said:**
> is there a way to convert a 32bit system to 64bit or do you have todo a new install?

New install

---

### Post by kansasnoob on 2012-02-03
> **sgage said:**
> PAE is a gimmick for allowing a 32-bit installation to access more than about 3.2 GB of RAM. If you're installing a 32-bit version, and the installer detects more than 3 GB of RAM (or maybe even if you don't - not sure), it gives you the PAE kernel. The non-PAE kernel is available in the grub menu under "Previous Linux Versions".

Thanks, on that Intel box I have only 2GB of RAM. Further more I just checked an old VIA C-7/P4M800 box with only 1GB of RAM that I'd last used for testing Lubuntu, and both the live and alternate installs resulted in the pae kernel.

So I wonder if that's a bug :confused:

---

### Post by kansasnoob on 2012-02-03
> **collisionystm said:**
> Technically 32 bit should be able to handle 4gb of memory.

Regardless PAE is just a hack. Time to upgrade into the current century and get a 64 bit system.

Care to loan me a couple grand :rolleyes:

I can pay you $10 a month.

---

### Post by collisionystm on 2012-02-03
> **kansasnoob said:**
> Thanks, on that Intel box I have only 2GB of RAM. Further more I just checked an old VIA C-7/P4M800 box with only 1GB of RAM that I'd last used for testing Lubuntu, and both the live and alternate installs resulted in the pae kernel.

So I wonder if that's a bug :confused:

They give you the PAE kernel by default so you have the option to run more memory without having to futz with it.

Running the PAE is not a problem. Running to much RAM on a 32 bit is.

---

### Post by collisionystm on 2012-02-03
> **kansasnoob said:**
> Care to loan me a couple grand :rolleyes:

I can pay you $10 a month.

lol wish I could.

You can get a nice dell vostro desktop for 300 bucks from dell.

If you want a new laptop may i suggest a vostro 3000 series from dell. They are awesome. You can also finance through dell for the 10 or 12 bucks a month you are looking for lol.

Nice 17" screen.... have it and love it.

[http://www.dell.com/us/soho/p/vostro-3750/pd?&c=us&cs=ussoho1&l=en&s=soho&ST=vostro%203750&dgc=ST&cid=79568&lid=2031857&acd=sWmxMBWYc,19296647984,901q5c14135](http://www.dell.com/us/soho/p/vostro-3750/pd?&c=us&cs=ussoho1&l=en&s=soho&ST=vostro%203750&dgc=ST&cid=79568&lid=2031857&acd=sWmxMBWYc,19296647984,901q5c14135)

---

### Post by kansasnoob on 2012-02-03
> **bmbaker said:**
> is there a way to convert a 32bit system to 64bit or do you have todo a new install?

For sure you have to do a fresh install, but I just recently bought my first 64bit hardware. But I'm poor so I reused a matched set of RAM / two 1GB sticks = 2GB / and I found overall performance to be better with i386 :)

I know I could upgrade the RAM for under $50.00 but that's a lot of money to me :(

---

### Post by collisionystm on 2012-02-03
> **kansasnoob said:**
> For sure you have to do a fresh install, but I just recently bought my first 64bit hardware. But I'm poor so I reused a matched set of RAM / two 1GB sticks = 2GB / and I found overall performance to be better with i386 :)

I know I could upgrade the RAM for under $50.00 but that's a lot of money to me :(


I understand. I am in the same boat. I am lucky enough to play with different kinds of hardware because of my job lol. What I have at work and what I have at home are 2 different stories!

---

### Post by kansasnoob on 2012-02-03
> **collisionystm said:**
> lol wish I could.

You can get a nice dell vostro desktop for 300 bucks from dell.

If you want a new laptop may i suggest a vostro 3000 series from dell. They are awesome. You can also finance through dell for the 10 or 12 bucks a month you are looking for lol.

Nice 17" screen.... have it and love it.

[http://www.dell.com/us/soho/p/vostro-3750/pd?&c=us&cs=ussoho1&l=en&s=soho&ST=vostro%203750&dgc=ST&cid=79568&lid=2031857&acd=sWmxMBWYc,19296647984,901q5c14135](http://www.dell.com/us/soho/p/vostro-3750/pd?&c=us&cs=ussoho1&l=en&s=soho&ST=vostro%203750&dgc=ST&cid=79568&lid=2031857&acd=sWmxMBWYc,19296647984,901q5c14135)

My point is that it's a bit ridiculous to suggest that anytime someone encounters a problem they need to rush out and buy new hardware. I'll grant you that some hardware is not viable to support, but I still have an old Intel PII w/256MB of RAM that will run Lubuntu.

It's hardly anything to brag about, and Puppy is even better on it, but old does not equal dead. If it did I'd be dead :D

---

### Post by collisionystm on 2012-02-03
> **kansasnoob said:**
> My point is that it's a bit ridiculous to suggest that anytime someone encounters a problem they need to rush out and buy new hardware. I'll grant you that some hardware is not viable to support, but I still have an old Intel PII w/256MB of RAM that will run Lubuntu.

It's hardly anything to brag about, and Puppy is even better on it, but old does not equal dead. If it did I'd be dead :D

You don't need to rush out and buy new hardware. The only thing I did was explain what my opinion was of 32 bit and the PAE
I then offered suggestions for decent 64 bit hardware at a good price if you choose to go that route!

Its all personal choice

---

### Post by kansasnoob on 2012-02-03
OK, I've done a lot of searching, but before I get started just let me say I wouldn't have freaked out had I not encountered a butt load of other bugs :D

It appears that the devs had planned on dropping non-PAE in 12.04, but then they decided to postpone that until 12.10. Based on this install it would appear that they changed their minds again :D

It appears to have nothing to do with the other bugs I encountered ;)

Not a pleasant experience when you're testing iso-images, along with many iso-rebuilds, and a bug causes one to look for things that are different than usual.

---

### Post by sgage on 2012-02-03
I have a 64-bit computer, but I always use a 32-bit Linux installation. Fewer headaches. I've never encountered something I couldn't do that required 64-bits. Performance is great. I've got 4 GB RAM in my current rig, and I don't think I've ever exceeded 2 GB or so in actual use.

Perhaps one day, when the world is completely 64-bit, it will be a more compelling choice. But for now, 32-bit works just fine for me.

---

### Post by xyzzyman on 2012-02-03
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1) for lots of benchmarks comparing 686, 686PAE and x64. That atom is one of the few that's 64bits so who knows what improvement you'd see with a 64bit install. You must attempt it in the name of science!

---

### Post by jerrylamos on 2012-02-03
> **kansasnoob said:**
> But I'm poor so I reused a matched set of RAM / two 1GB sticks = 2GB / and I found overall performance to be better with i386 :)
I've heard about worse performance from more than one place.  Maybe even more disk space?? not sure about that.

Anyway tried 64bit on precise pangolin and at that time got a - lot - more bugs, so why bother....slower and might? take more space.

Jerry

---

### Post by kevpan815 on 2012-02-03
Re: Why the pae kernel, avoid it by using AMD64 instead. :-)

---

### Post by lucazade on 2012-02-04
> **jerrylamos said:**
> I've heard about worse performance from more than one place.  Maybe even more disk space?? not sure about that.

Anyway tried 64bit on precise pangolin and at that time got a - lot - more bugs, so why bother....slower and might? take more space.

Jerry

64bit myths:

Worse performance, slower = false
Better performance in cpu intensive tasks = true

Uses more disk space = false
Allocates double of ram compared to 32bit = true

It has more bugs = false
Nowadays 64bit is solid as 32bit = true

---

### Post by Bruno81 on 2012-02-04
So....if I can't buy a new laptop I can't run Ubuntu Precise Pangolin and other future versions of Ubuntu?
:shock:

---

### Post by kansasnoob on 2012-02-04
> **xyzzyman said:**
> [http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1) for lots of benchmarks comparing 686, 686PAE and x64. That atom is one of the few that's 64bits so who knows what improvement you'd see with a 64bit install. You must attempt it in the name of science!

The Atom 230 (which I have) is 32 bit. The Atom 330 is 64 bit :)

I almost spent the extra $10 to $15 for the 330, but I prefer canned soup to ramen noodle ;)

---

### Post by kansasnoob on 2012-02-04
> **sgage said:**
> I have a 64-bit computer, but I always use a 32-bit Linux installation. Fewer headaches. I've never encountered something I couldn't do that required 64-bits. Performance is great. I've got 4 GB RAM in my current rig, and I don't think I've ever exceeded 2 GB or so in actual use.

Perhaps one day, when the world is completely 64-bit, it will be a more compelling choice. But for now, 32-bit works just fine for me.

In my particular case, a few months ago I got my first 64bit hardware, AMD Sempron LE-1250, and I installed both 32bit Oneiric and 64bit Oneiric.

It's used mostly for streaming flash videos (I no longer have cable TV) and the 64bit install would use about 80% to 90% of my 2GB of RAM. But the 32bit install never goes above about 40% of RAM usage :)

So IMHO, if someone has 64bit hardware, go ahead and try both. Then use whatever works best for you :D

---

### Post by kansasnoob on 2012-02-04
> **Bruno81 said:**
> So....if I can't buy a new laptop I can't run Ubuntu Precise Pangolin and other future versions of Ubuntu?
:shock:

Who said that?

AFAIK from reading, but I could be wrong, there is nothing wrong with the "PAE" kernel. The elimination of "non-pae" is likely intentional, but I'm not 100% sure :D

Just ignore those who insist it's time to throw out your 32 bit hardware, it's nonsense!

---

### Post by kansasnoob on 2012-02-04
I'm not quite prepared to mark this solved yet, over the next couple of weeks I'll try to learn more about this.

---

### Post by xyzzyman on 2012-02-04
> **lucazade said:**
> 64bit myths:
Uses more disk space = false
Allocates double of ram compared to 32bit = true

You're right on everything except 64bit using double the RAM. The pointers are twice as long, so you wind up using 5-20% more RAM. And unless you are using all your RAM the performance gains are worth it.

---

### Post by xyzzyman on 2012-02-04
> **kansasnoob said:**
> The Atom 230 (which I have) is 32 bit. The Atom 330 is 64 bit :)

I almost spent the extra $10 to $15 for the 330, but I prefer canned soup to ramen noodle ;)

Oh, I was just going by what Intel lists, and they show the 230 as 64bit, and the 330 just being the dual-core while the 230 is single core.

And if you can afford ramen you're not that poor. :) Rice & beans is even cheaper. Canned goods and ramen are for people who are too lazy to be very poor and cook. lol I did get the point of buying the day old loaves of bread and using ketchup packets taken from a mcdonalds for about 6 months. Sometimes mixing it up if I could get mustard packets. Then I learned to go to the asian markets, and the joy of 10 pound bags of rice and 5 pound bags of dried beans.

---

### Post by kansasnoob on 2012-02-04
> And if you can afford ramen you're not that poor. Rice & beans is even cheaper. Canned goods and ramen are for people who are too lazy to be very poor and cook. lol I did get the point of buying the day old loaves of bread and using ketchup packets taken from a mcdonalds for about 6 months. Sometimes mixing it up if I could get mustard packets. Then I learned to go to the asian markets, and the joy of 10 pound bags of rice and 5 pound bags of dried beans.

OK, I'm not really poor. I'm not living in a gutter yet. Does that make you happy?

I make decisions regarding what I can or can NOT afford!

But this is all OT!!!!!!!!!!!!!

The question was about the PAE kernel because I needed answers! This nonsense about users needing to upgrade to 64 bit is just that, ABSOLUTE NONSENSE!!!!!!!!!!!

And if it continues I'll report future posts to the mods!

We've already had one user ask:

> So....if I can't buy a new laptop I can't run Ubuntu Precise Pangolin and other future versions of Ubuntu?


Happy yet?

Ubuntu is not now, nor has it ever been the domain of the rich!!!!!!!!!!!!!!!!

---

### Post by lucazade on 2012-02-04
> **xyzzyman said:**
> You're right on everything except 64bit using double the RAM. The pointers are twice as long, so you wind up using 5-20% more RAM. And unless you are using all your RAM the performance gains are worth it.

from my tests ram usage on a 64bit machines is almost double.. yep, you're right about pointers len

> The main disadvantage of 64-bit architectures is that, relative to 32-bit architectures, the same data occupies more space in memory (due to longer pointers and possibly other types, and alignment padding). This increases the memory requirements of a given process and can have implications for efficient processor cache utilization
[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by zika on 2012-02-04
> **lucazade said:**
> from my tests ram usage on a 64bit machines is almost double.. yep, you're right about pointers lenIn order to be Precise (pun intended) You should define &#8222;ram usage&#8220; since there is (as far as I know) different way of maintaining pagecache etc...
If I restrict (with appropriate switches in sysctl and similar) such differences between 32 and 64 bit architecture I do not see more difference than from pointers and similar inherent ones...

---

### Post by cariboo on 2012-02-04
Can we get this thread back on topic, how wealthy or not someone is irrelevant to the original question.

---

### Post by danniel on 2012-02-04
To be honest, I don't see the reason for this PAE switch made by Ubuntu. Those who have more than 3 GB of RAM can install the 64 bit version anyway. Meanwhile, I can't use (at least) the default 32 bit Ubuntu on my older machines *(for example an Asus EEE PC 701 with 2 GB of RAM)* because it complains about the lack of PAE.

**32 bit with PAE by default = a barrier for easy Ubuntu adoption**

I think it's better to make the 64 bit download the default one, and for older machines provide a 32 bit download, without the PAE requirement.

---

### Post by collisionystm on 2012-02-04
> **danniel said:**
> To be honest, I don't see the reason for this PAE switch made by Ubuntu. Those who have more than 3 GB of RAM can install the 64 bit version anyway. Meanwhile, I can't use (at least) the default 32 bit Ubuntu on my older machines *(for example an Asus EEE PC 701 with 2 GB of RAM)* because it complains about the lack of PAE.

**32 bit with PAE by default = a barrier for easy Ubuntu adoption**

I think it's better to make the 64 bit download the default one, and for older machines provide a 32 bit download, without the PAE requirement.


At this moment 32 bit works with almost all computers. 64 bit does not.

Having 32 bit with PAE = EASY ubuntu adoption because its practically guaranteed to fire up for someone who knows nothing of computers.

End of story.

---

### Post by xyzzyman on 2012-02-04
> **danniel said:**
> I think it's better to make the 64 bit download the default one, and for older machines provide a 32 bit download, without the PAE requirement.

[http://www.phoronix.com/scan.php?page=news_item&px=MTAxMTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTAxMTQ)

Canonical thinks the same thing and 64 bit is the new 'recommended' AKA Default download starting with 12.04.

---

### Post by kansasnoob on 2012-02-04
First of all, apologies to everyone for turning this into a "have's and have not's" discussion. That was never my intention. Whether or not we have the financial capability to upgrade hardware should never truly influence our questions or answers on the forums ;)

Now that that's out of the way, danniel gets us back to business:

> To be honest, I don't see the reason for this PAE switch made by Ubuntu. Those who have more than 3 GB of RAM can install the 64 bit version anyway. Meanwhile, I can't use (at least) the default 32 bit Ubuntu on my older machines (for example an Asus EEE PC 701 with 2 GB of RAM) because it complains about the lack of PAE.


Here I don't have an answer :confused:

The new PAE kernel seems OK on all of my hardware, the oldest being VIA C-7 w/P4M800 graphics and only 1GB of RAM.

So I haven't needed to figure out how to boot non-pae by default, any thoughts?

Also, as I expect this conversation to continue, does anyone know how to tell if their hardware is 64bit compatible or not in one command?

I just know mine because I bought and installed it, but many may not know.

---

### Post by effenberg0x0 on 2012-02-04
> **kansasnoob said:**
> 
Also, as I expect this conversation to continue, does anyone know how to tell if their hardware is 64bit compatible or not in one command?I just know mine because I bought and installed it, but many may not know.

I use this two to check for 32/64-Bit:
```
lshw -C processor
cat /proc/cpuinfo

```
The second one show you a lot of indications for 64: long Mode, addressing, etc.
And this to check for pae:
```
cat /proc/cpuinfo | grep -i pae
```Regards,
Effenberg

---

### Post by xyzzyman on 2012-02-04
[http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM)

The decision was originally to drop PAE support at the Developers Summit last November. It was decided in December to keep it as a fall back for one more LTS. PAE has been supported by Intel and AMD hardware since the mid to late 90's, and if it wasn't for Pentium M's not supporting PAE there probably wouldn't be a non-PAE kernel now.

@kansasnoob: I'm curious what effenberg's commands show for your processor, as both wikipedia and intel show the 230 as supporting 64bit with no notes of diffent models. I have an Aspire Revo AR1600-U910H packed away with an Atom 230 in it and I had Windows 64bit Ultimate on it (I can't remember which version of Ubuntu I put on it), so I'm wondering what the difference is with your 230.

---

### Post by danniel on 2012-02-04
> **collisionystm said:**
> Having 32 bit with PAE = EASY ubuntu adoption because its practically guaranteed to fire up for someone who knows nothing of computers.

32 bit without PAE does the same, but for even more hardware :)

> **xyzzyman said:**
> Canonical thinks the same thing and 64 bit is the new 'recommended' AKA Default download starting with 12.04.

And considering the above, the "PAE by default" thing makes even less sense.


**Well, I hope that at least Xubuntu will offer a non-PAE easy download option.**

---

### Post by kevpan815 on 2012-02-04
> **kansasnoob said:**
> **Update**: [Webupd8 has it down]("http://www.webupd8.org/2012/02/ubuntu-1204-lts-precise-pangolin-alpha.html"):



So sgage's responses are the only proper responses, everything else is [FUD]("http://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt")!

******************************

I just completed alpha 2 iso-testing and ran into a number of issues, one question I have is why a fresh install uses the "pae" kernel :confused:

Fresh install:

Linux lance-desktop 3.2.0-12-generic-pae #21-Ubuntu SMP Tue Jan 31 20:44:35 UTC 2012 i686 i686 i386 GNU/Linux

Upgrade from Oneiric:

Linux lance-desktop 3.2.0-12-generic #21-Ubuntu SMP Tue Jan 31 18:40:37 UTC 2012 i686 i686 i386 GNU/Linux

The hardware involved is:

Intel(R) Atom(TM) CPU  230   @ 1.60GHz
Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

Sorry to be so clueless ;)

Yes, if you go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) you will notice that all of the Pre-Release 3.3.0 X86 Mainline Kernels that are proposed for 12.04 are Pae enabled by default. This includes the 3.3.0 Nightly Build Kernels as well!

---

### Post by xyzzyman on 2012-02-04
> **kevpan815 said:**
> Yes, if you go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) you will notice that all of the Pre-Release 3.3.0 X86 Mainline Kernels that are proposed for 12.04 are Pae enabled by default. This includes the 3.3.0 Nightly Build Kernels as well!

Those kernels are NOT proposed for 12.04. 12.04 is going to use 3.2 not 3.3. The mainline kernel PPA is free of ubuntu patches and exists for troubleshooting to see if fixes have already occurred up stream. If you want to keep track of what's released, security update and proposed for kernels you can always check [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux).

---

### Post by sgage on 2012-02-04
> **kansasnoob said:**
> First of all, apologies to everyone for turning this into a "have's and have not's" discussion. That was never my intention. Whether or not we have the financial capability to upgrade hardware should never truly influence our questions or answers on the forums ;)

Now that that's out of the way, danniel gets us back to business:



Here I don't have an answer :confused:

The new PAE kernel seems OK on all of my hardware, the oldest being VIA C-7 w/P4M800 graphics and only 1GB of RAM.

So I haven't needed to figure out how to boot non-pae by default, any thoughts?

Also, as I expect this conversation to continue, does anyone know how to tell if their hardware is 64bit compatible or not in one command?

I just know mine because I bought and installed it, but many may not know.

As far as default boot, I think if you go to /etc/default and edit "grub", the very first item is GRUB_DEFAULT. It comes set to 0, which is the first item in the grub menu. 1 would be rescue mode, and I'll bet 2 would be the first item in "Previous Linux Versions".

When you're done fiddling around and save the file, run update-grub and try a reboot.

You can also set the boot delay (GRUB_TIMEOUT) and some other boot options.

---

### Post by kevpan815 on 2012-02-04
> **xyzzyman said:**
> Those kernels are NOT proposed for 12.04. 12.04 is going to use 3.2 not 3.3. The mainline kernel PPA is free of ubuntu patches and exists for troubleshooting to see if fixes have already occurred up stream. If you want to keep track of what's released, security update and proposed for kernels you can always check [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux).

NOT TRUE. Take a look at 3.3.0 RC2, is says that it is specifically designed 2 run on 12.04 and nothing else. The Nightly Builds of 3.3.0 say the same thing! Just FYI.

---

### Post by kansasnoob on 2012-02-04
> **sgage said:**
> As far as default boot, I think if you go to /etc/default and edit "grub", the very first item is GRUB_DEFAULT. It comes set to 0, which is the first item in the grub menu. 1 would be rescue mode, and I'll bet 2 would be the first item in "Previous Linux Versions".

When you're done fiddling around and save the file, run update-grub and try a reboot.

You can also set the boot delay (GRUB_TIMEOUT) and some other boot options.

Yes, but what if you're running a multi-boot like mine and another grub is in charge?

There must be a way to switch to non-pae?

That said I'm having no kernel related problems with this pae kernel ............ or not that I can tell so far.

I encountered a lot of bugs during Alpha 2 iso-testing and I wondered about the pae kernel, but none of those bugs turns out to have been kernel related.

So I'm thinking this new pae kernel is fine, just new and different :)

If someone has a kernel related bug they should report it.

---

### Post by sgage on 2012-02-04
> **kansasnoob said:**
> Yes, but what if you're running a multi-boot like mine and another grub is in charge?

There must be a way to switch to non-pae?

That said I'm having no kernel related problems with this pae kernel ............ or not that I can tell so far.

I encountered a lot of bugs during Alpha 2 iso-testing and I wondered about the pae kernel, but none of those bugs turns out to have been kernel related.

So I'm thinking this new pae kernel is fine, just new and different :)

If someone has a kernel related bug they should report it.

I guess you would just do the edit of /etc/default/grub in the installation that holds the controlling grub. Boot it up and at the grub menu, count how many items it is down to the kernel you want and make that default.

OTOH, I've never had any trouble with the pae kernel, and I've been using it since it first started being installed (Lucid? Maverick? don't remember). I sure wouldn't worry about it. If push came to shove, just delete the pae kernel (making sure you have the vanilla kernel installed first).

---

### Post by xyzzyman on 2012-02-04
> **kevpan815 said:**
> NOT TRUE. Take a look at 3.3.0 RC2, is says that it is specifically designed 2 run on 12.04 and nothing else. The Nightly Builds of 3.3.0 say the same thing! Just FYI.

This is OT, but you can apply them to a 11.10 build. I've applied 3.3 kernels from mainline that said precise. Stop with your wise-*** "Just FYI". I was only correcting you that they aren't proposed kernel updates, as they are not going to be included in 12.04. 

If you think I am lying, please read:

[https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

The reason they say 'Precise' is listed on them is:
> **Why do mainline kernel builds have a -<series> suffix?**
Each mainline build is named by the base upstream version suffixed with an Ubuntu release name, 2.6.35-maverick. This tells us the upstream version which was built, and additionally which configuration was used to build it. This tells us which release is most compatible with the kernel as built. This does not prevent the kernel being used on other releases, though it is most likely to work correctly on the release it is build for, or earlier ones. The further away from your base kernel release you are the more likely that there will be an incompatible userspace interaction which will prevent them working for you.

See, it specifically says it most likely will work with older releases... Not 'nothing else' as you are trying to claim.

---

### Post by xyzzyman on 2012-02-04
> **sgage said:**
> If push came to shove, just delete the pae kernel (making sure you have the vanilla kernel installed first).

You can install a non-PAE ubuntu kernel from the repo's without having to install a vanilla kernel.

In 3 pages, I haven't found anyone that has suggested why you would want to switch to a non-PAE kernel if your CPU supports the extensions. Does anyone have any empirical proof that it adds overhead when you are using less than 4GB's of RAM? PAE adds hardware support for the NX bit which saves the OS from having to emulate it, which comes into play with preventing buffer overflow exploits.

---

### Post by sgage on 2012-02-04
> **xyzzyman said:**
> You can install a non-PAE ubuntu kernel from the repo's without having to install a vanilla kernel.

In 3 pages, I haven't found anyone that has suggested why you would want to switch to a non-PAE kernel if your CPU supports the extensions. Does anyone have any empirical proof that it adds overhead when you are using less than 4GB's of RAM? PAE adds hardware support for the NX bit which saves the OS from having to emulate it, which comes into play with preventing buffer overflow exploits.

I'm sorry - my imprecise language. All I meant by vanilla was non-PAE - and indeed, it's right in the repos.

In fact, to add to the confusion, I thought Ubuntu still installed the non-PAE kernel, but I notice in my latest install they do not. 

Anyway, I meant well :KS

---

### Post by xyzzyman on 2012-02-04
> **sgage said:**
> I'm sorry - my imprecise language. All I meant by vanilla was non-PAE - and indeed, it's right in the repos.

In fact, to add to the confusion, I thought Ubuntu still installed the non-PAE kernel, but I notice in my latest install they do not. 

Anyway, I meant well :KS

So the question is more for the very rare person who can't support PAE, does Ubiquity detect this and install the non-PAE? Other than maybe a late model Pentium M, anyone else with non-PAE hardware isn't going to be running Ubuntu but more likely (X)Lubuntu which would have to make their own decision.

---

### Post by nm_geo on 2012-02-04
> **kansasnoob said:**
> Yes, but what if you're running a multi-boot like mine and another grub is in charge?

There must be a way to switch to non-pae?

That said I'm having no kernel related problems with this pae kernel ............ or not that I can tell so far.

<snip>

If someone has a kernel related bug they should report it.

kansas you got me so curious I have been tweaking experimenting ...
Yes you can just use synpatic to install the generic non-pae kernel.. I just did ..

```
Linux greg 3.2.0-12-generic #21-Ubuntu SMP Tue Jan 31 18:40:37 UTC 2012 i686 i686 i386 GNU/Linux
```I also multi-boot way to many versions takes me hours just to update LL to PP plus squeeze and WindozXP.  But my controlling grub is installed in my LL and I run Grub-Customizer to help me make grub changes quickly.

Question was your install a regular Ubuntu or Lubuntu 12.04?  

My recent Lubuntu 12.04 iso that I dd to my flash drive has the pae kernel too.. I have not installed it yet..

By the way no big performance change obviously.  I do have 4GB of RAM but i never use it all anyway.  Yes I could run 64-bit and have but see no great gain for me..

---

### Post by jerrylamos on 2012-02-04
lubuntu 12.04 A2 daily build Feb 4 won't boot on IBM Thinkpad T40 "kernel requires pae".

Actually running lubuntu 12.04 Alpha 1 updated to today running O.K.

Nice peppy responsive notebook.  I'd think it was the perfect target for lubuntu.  Not so.

Jerry

---

### Post by xyzzyman on 2012-02-04
> **jerrylamos said:**
> lubuntu 12.04 A2 daily build Feb 4 won't boot on IBM Thinkpad T40 "kernel requires pae".

Actually running lubuntu 12.04 Alpha 1 updated to today running O.K.

Nice peppy responsive notebook.  I'd think it was the perfect target for lubuntu.  Not so.

Jerry

TADA! It's a Pentium M.

---

### Post by kansasnoob on 2012-02-05
> **xyzzyman said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM)

The decision was originally to drop PAE support at the Developers Summit last November. It was decided in December to keep it as a fall back for one more LTS. PAE has been supported by Intel and AMD hardware since the mid to late 90's, and if it wasn't for Pentium M's not supporting PAE there probably wouldn't be a non-PAE kernel now.

@kansasnoob: I'm curious what effenberg's commands show for your processor, as both wikipedia and intel show the 230 as supporting 64bit with no notes of diffent models. I have an Aspire Revo AR1600-U910H packed away with an Atom 230 in it and I had Windows 64bit Ultimate on it (I can't remember which version of Ubuntu I put on it), so I'm wondering what the difference is with your 230.

Possibly inconclusive:

```
lance@lance-desktop:~$ lshw -C processor
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Intel(R) Atom(TM) CPU  230   @ 1.60GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.12.2
       serial: 0001-06C2-0000-0000-0000-0000
       size: 1600MHz
       **width: 64 bits**
       capabilities: fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 64 bits
          capabilities: logical
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
lance@lance-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  230   @ 1.60GHz
stepping	: 2
cpu MHz		: 1600.061
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
bogomips	: 3200.12
[B]clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical[/B], 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  230   @ 1.60GHz
stepping	: 2
cpu MHz		: 1600.061
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
bogomips	: 3200.12
[B]clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical[/B], 48 bits virtual
power management:

lance@lance-desktop:~$ cat /proc/cpuinfo | grep -i pae
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts

```

---

### Post by kansasnoob on 2012-02-05
> **xyzzyman said:**
> TADA! It's a Pentium M.

Just reading a bit more:

[http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNzM)

Something interesting:

> Switch precise over to PAE kernel by default on i386; we retain the option to revert if it causes too much fallout (Colin) 

So bug reporting will be crucial :D

---

### Post by xyzzyman on 2012-02-05
> **kansasnoob said:**
> Possibly inconclusive:

```
lance@lance-desktop:~$ lshw -C processor
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Intel(R) Atom(TM) CPU  230   @ 1.60GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.12.2
       serial: 0001-06C2-0000-0000-0000-0000
       size: 1600MHz
       **width: 64 bits**
       capabilities: fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 64 bits
          capabilities: logical
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
lance@lance-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  230   @ 1.60GHz
stepping	: 2
cpu MHz		: 1600.061
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
bogomips	: 3200.12
[B]clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical[/B], 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  230   @ 1.60GHz
stepping	: 2
cpu MHz		: 1600.061
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
bogomips	: 3200.12
[B]clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical[/B], 48 bits virtual
power management:

lance@lance-desktop:~$ cat /proc/cpuinfo | grep -i pae
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts

```

Nope. Your CPU can run 64bit just like Intel says and many others have.

---

### Post by VinDSL on 2012-02-05
Interesting!

Just for giggles, I installed a Linux 3.2.0-14-generic-pae kernel...

...even though I don't have a 64-bit processor, nor over 1 GB RAM.

```
vindsl@Zuul:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 3.40GHz
stepping	: 5
microcode	: 0x1b
cpu MHz		: 3407.294
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips	: 6814.58
clflush size	: 64
cache_alignment	: 128
**[COLOR="DarkRed"]address sizes	: 36 bits physical, 32 bits virtual[/COLOR]**
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 3.40GHz
stepping	: 5
microcode	: 0x1b
cpu MHz		: 3407.294
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips	: 6815.86
clflush size	: 64
cache_alignment	: 128
**[COLOR="DarkRed"]address sizes	: 36 bits physical, 32 bits virtual[/COLOR]**
power management:

vindsl@Zuul:~$ 

```

Specs for this rig are in my sig.

Anyway, everything seems to be running fine on this single-core, Socket 478, Intel P4 Extreme Edition.

Who woulda thunk it?!?!?  :)

---

### Post by cariboo on 2012-02-05
I have an atom 230 powered system that I use for running XBMC, at one point I installed a 64-bit version, but as the system only has 1GiB of ram, I didn't see any advantages when running it, so on the next install I just installed the 32-bit version. The system does exactly what it was intended for, so I see no reason, even if it is capable of running a 64-bit version, to change.

One thing I have to note, though is that I installed a PCI, not PCI-e video card so that I could connect to the TV via one of the HDMI ports, I may try a 64-bit version just to see if there is a difference, though I doubt it.

---

### Post by xyzzyman on 2012-02-05
> **VinDSL said:**
> Interesting!

Just for giggles, I installed a Linux 3.2.0-14-generic-pae kernel...

...even though I don't have a 64-bit processor, nor over 1 GB RAM.


Specs for this rig are in my sig.

Anyway, everything seems to be running fine on this single-core, Socket 478, Intel P4 Extreme Edition.

Who woulda thunk it?!?!?  :)

All P4's support PAE. Intel started rolling it out with Pentium Pro's in 1995. P3's and newer all have it. Pentium M's were the bastard child of processor's in the last decade that don't.

---

### Post by xyzzyman on 2012-02-05
> **cariboo907 said:**
> I have an atom 230 powered system that I use for running XBMC, at one point I installed a 64-bit version, but as the system only has 1GiB of ram, I didn't see any advantages when running it, so on the next install I just installed the 32-bit version. The system does exactly what it was intended for, so I see no reason, even if it is capable of running a 64-bit version, to change.

One thing I have to note, though is that I installed a PCI, not PCI-e video card so that I could connect to the TV via one of the HDMI ports, I may try a 64-bit version just to see if there is a difference, though I doubt it.

For XBMC it probably doesn't matter. When I was using XBMC on mine under Ubuntu I had it using VDPAU so all 1080p playback was being offloaded to the video card so I was still using under 25% CPU with BRay rips. If you were using it for normal use the 10-20% performance increase of anything that uses the CPU could be worth it.

---

### Post by VinDSL on 2012-02-05
> **xyzzyman said:**
> All P4's support PAE. Intel started rolling it out with Pentium Pro's in 1995. P3's and newer all have it. Pentium M's were the bastard child of processor's in the last decade that don't.
Heh!  This is a bastard too!

This P4EE is actually a derivative of a Xeon MP (32-bit) on a Socket 478 pinset.

I didn't *know* if it would work, or not... but, it does.  ;)

---

### Post by kansasnoob on 2012-02-05
> **xyzzyman said:**
> Nope. Your CPU can run 64bit just like Intel says and many others have.

Well I'll try 64bit on here soon then, just to see what happens. I'd have sworn when I bought this Jetway MoBo that it said 32bit.

---

### Post by effenberg0x0 on 2012-02-05
> **kansasnoob said:**
> Well I'll try 64bit on here soon then, just to see what happens. I'd have sworn when I bought this Jetway MoBo that it said 32bit.

x86-64 is there in the capabilities flags in the output you pasted, and so is PAE. It should work

Regards,
Effenberg

EDIT: lm is there too, in the cpuinfo.

---

### Post by lucazade on 2012-02-05
I still have an old Thinkpad T40 with a Pentium M, an impressive machine like all thinkpads. Haven't tried yet precise on it, oneiric works like a charm.
In case there is only PAE support I'll chroot the iso and replace the kernel with a non-PAE one.

---

### Post by VinDSL on 2012-02-05
> **lucazade said:**
> In case there is only PAE support I'll chroot the iso and _replace the kernel with a non-PAE one_.
I fear this will become more difficult, as time marches on...

SOURCE:  [https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Alpha2](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Alpha2)  
( PrecisePangolin/TechnicalOverview/Alpha2 - Ubuntu Wiki )


> **[SIZE="+1"]Linux kernel 3.2[/SIZE]**

Alpha-2 includes the 3.2.0-12.21 Ubuntu kernel which is based on the most recent v3.2.2 upstream stable kernel. This is an update from the 3.2.0-2.5 kernel which shipped in Alpha-1 (based on upstream v3.2-rc3 ). **As with Alpha-1, the Alpha-2 kernel no longer carries a separate amd64 -server [COLOR="DarkRed"]and -generic kernel flavor[/COLOR]. These have been merged to help reduce the maintenance burden over the life of this LTS release.** AUFS also remains disabled in the Alpha-2 kernel. Anyone needing AUFS is encouraged to migrate to overlayfs. We have pulled in the latest overlayfs updates to the Alpha-2 kernel. We have also dropped a set of seccomp_filter patches we were carrying as there were no consumers of these patches at this time. We will re-evaluate their necessity in future Ubuntu releases.

---

### Post by lucazade on 2012-02-05
> **VinDSL said:**
> I fear this will become more difficult, as time marches on...

SOURCE:  [https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Alpha2](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Alpha2)  
( PrecisePangolin/TechnicalOverview/Alpha2 - Ubuntu Wiki )

oh my gosh!
Then I'll use a vanilla kernel or I will bump Oneiric kernel version.
thanks for the info anyway :)

---

### Post by bubbajunk on 2012-02-05
I just downloaded Ubuntu 12.04 LTS Daily Build to check it out. I've been using Ubuntu on my Thinkpad T42 since 10.04. I put the ISO on a USB to create a live usb using Unetbootin. When I went to boot, I got the message saying that the Kernel needs PAE and my CPU doesn't support it. Never got that before.

I didn't even know what PAE was until yesterday. I found this thread and many others discussing the potential decision to drop support for non-PAE CPUs. My ThinkPad T42 has an Intel Pentium M processeor with 400MHz FSB. Apparently Intel decided to cut corners and not support PAE with this processor. I'd hate to have to ditch Ubuntu just because of the non-PAE CPU support. The Thinkpad works fine with 11.10 currently installed. 

Sounds like the decision has been to delay dropping support until 12.10. My understanding is that PAE kernel version will be the default for the i386 iso. Does that mean there will be another ISO file for non-PAE, or do you have to somehow change out the kernel in the default ISO? How would I go about merging (not sure if that's the right terminology) the non-PAE kernel with the i386 iso file to create a live USB to try out 12.04?

Would someone be able to outline the steps? Any help would be appreciated.

---

### Post by xyzzyman on 2012-02-05
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/897786](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/897786)

Reading it, I think you might be able to use the alternate CD as that uses debian-installer instead of ubiquity. I'm not positive though. I'm downloading the alterate x86 cd to try out in a virtualbox without PAE enabled as we speak.

Update: The alternate CD also only includes the PAE kernel to boot. I updated the ISO with the the non-pae kernel extracted out and placed as vmlinuz, but then all the modules are built pointing to generic-pae and not generic so they both fail to boot fully boot.

---

### Post by jerrylamos on 2012-02-05
Kansasnoob,

> AUFS also remains disabled in the Alpha-2 kernel. Anyone needing AUFS is encouraged to migrate to overlayfs.
What is "AUFS" and how do I migrate to overlayfs when booting the install CD?  Or install USB or install booting directly from the .iso file?  

Thanks, Jerry

---

### Post by xyzzyman on 2012-02-05
> **jerrylamos said:**
> Kansasnoob,


What is "AUFS" and how do I migrate to overlayfs when booting the install CD?  Or install USB or install booting directly from the .iso file?  

Thanks, Jerry

If you have to ask you don't use it. It allows directories to be "together" and overlap each other. It's been in the process of being phased out for awhile, now it's just complete. I've always disabled it when compiling my own kernel from Ubuntu sources (It's not in mainline)

---

### Post by MoreOrLess on 2012-02-05
I read the the installer is supposed to fall back to non-pae on those CPU's that don't support it, but the fallback isn't working yet (sorry, I can't remember where I read it).

The non-pae kernel should be around in Precise, which is supported for another 5 years, so Pentium M owners can disband the lynch mob (at least until Precise is EOL).

---

### Post by xyzzyman on 2012-02-06
> **MoreOrLess said:**
> I read the the installer is supposed to fall back to non-pae on those CPU's that don't support it, but the fallback isn't working yet (sorry, I can't remember where I read it).

The non-pae kernel should be around in Precise, which is supported for another 5 years, so Pentium M owners can disband the lynch mob (at least until Precise is EOL).

That's the thing, no one can find where any of the developers have said that. I've searched launchpad and the kernel teams mailing lists and can't find anything (I have a core 2 duo not a pentium M so I really don't care. lol) :guitar:

It's going to add at least 30-40 megs to the ISO though so I'm wondering if they really are going to.

---

### Post by cariboo on 2012-02-06
There was a discussion about this at the technical board meeting December 12 2011, you can view the minutes [here]("https://wiki.ubuntu.com/TechnicalBoard/TeamReports/11/December")

---

### Post by VinDSL on 2012-02-06
> **bubbajunk said:**
> I'd hate to have to ditch Ubuntu just because of the non-PAE CPU support.[...]
I've been running Ubu Unity 3D on Liquorix 3.2.0-4.dmz.1 (non-PAE) all day.  Works great!

Matter of fact, I've always preferred Liquorix over Ubu patched kernels.  But, we're supposed to be testing Ubu kernels, so I switch back n' forth.

Anyway, there's more than one way to skin a cat, you know?  ;)

---

### Post by xyzzyman on 2012-02-06
> **VinDSL said:**
> I've been running Ubu Unity 3D on Liquorix 3.2.0-4.dmz.1 (non-PAE) all day.  Works great!

Matter of fact, I've always preferred Liquorix over Ubu patched kernels.  But, we're supposed to be testing Ubu kernels, so I switch back n' forth.

Anyway, there's more than one way to skin a cat, you know?  ;)

So your network works properly with 3.2 kernels or still broken? Tried a fresh install of a daily to see?

---

### Post by VinDSL on 2012-02-07
> **xyzzyman said:**
> So your network works properly with 3.2 kernels or still broken? Tried a fresh install of a daily to see?
I haven't tried network-manager in a week or two.  Wicd works fine.

I haven't done a fresh install since 11.10.  LoL!  Realized this, yesterday, when submitting an apport bug report.

I'll try network-manager soon.  Maybe the problem is fixed.

You need to be careful when switching back n' forth between network managers.  Unfortunately, you can't have more than one installed at a time -- and simply enable this one, or that one. You have to remove one, and install the other.  If "the other one" isn't sitting in your cache, you're screwed, 'cause you can't download it without a network manager.  

It's sorta like playing with dynamite -- one false move and BOOM!

Anyway, I'll try network-manager again and report back later.  

Gotta update my Facebook account first.  LoL!  :D

---

### Post by bubbajunk on 2012-02-07
> **VinDSL said:**
> I've been running Ubu Unity 3D on Liquorix 3.2.0-4.dmz.1 (non-PAE) all day.  Works great!



Ok, so for the more casual somewhat technical types like myself, how do you go about using a different Linux kernel than the one that is bundled with the iso? I've never used anything but the bundled kernel so I have no idea how to do it. 

And is it possible to switch the kernel in the iso so that you can create a live usb with a different kernel, or do you have to install first?

---

### Post by kansasnoob on 2012-02-07
> **bubbajunk said:**
> Ok, so for the more casual somewhat technical types like myself, how do you go about using a different Linux kernel than the one that is bundled with the iso? I've never used anything but the bundled kernel so I have no idea how to do it. 

And is it possible to switch the kernel in the iso so that you can create a live usb with a different kernel, or do you have to install first?

Good question. I asked one at "answers":

[https://answers.launchpad.net/ubuntu/+question/187093](https://answers.launchpad.net/ubuntu/+question/187093)

I hope to find some definitive answers :D

---

### Post by cariboo on 2012-02-07
I haven't needed to use a different kernel for years, but you can compile a kernel yourself, see the howto [here]("https://help.ubuntu.com/community/Kernel/Compile"). The process creates debs for:

[LIST]
[*]linux-headers<version number>generic-pae<version number + build date and time>i386 
[*]linux-headers<version number><version number + build date and time>all
[*]linux-image<version number>genric<version number + build date and time>i386
[/LIST]

See [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc2-precise/") for examples. Or you can use the debs that I just linked to. You then install in the following order:

[LIST]
[*]linux-headers-3.3.0-030300rc2_3.3.0-030300rc2.201201311735_all.deb
[*]linux-headers-3.3.0-030300rc2-generic-pae_3.3.0-030300rc2.201201311735_i386.deb
[*]linux-image-3.3.0-030300rc2-generic-pae_3.3.0-030300rc2.201201311735_i386.deb
[/LIST]

Using dpkg. I used the i386 package as an example here, but it works the same for amd64.

If all went well when you compiled your own kernel, you should be able to boot using it.

I may be wrong here, but you should be able to force which kernel is used from the i386 Live CD's initial install screen, by adding the correct kernel parameters, if your cpu isn't detected correctly.

---

### Post by xyzzyman on 2012-02-07
> **cariboo907 said:**
> I may be wrong here, but you should be able to force which kernel is used from the i386 Live CD's initial install screen, by adding the correct kernel parameters, if your cpu isn't detected correctly.

You can't. The non-pae kernel isn't there. If you try to just replace the vmlinuz file, it then fails to boot as the modules aren't there inside the squash file.

---

### Post by VinDSL on 2012-02-08
> **xyzzyman said:**
> So your network works properly with 3.2 kernels or still broken? Tried a fresh install of a daily to see?

> **VinDSL said:**
> I haven't tried network-manager in a week or two.  Wicd works fine.[...]

Anyway, I'll try network-manager again and report back later.
Alrighty then...

Got home from work, and decided to give network-manager a try.

The app-indicator for network-manager has an X in the middle of it.

I have no network connection - LAN, WAN, or anything else.

And, this machine hard-locks on shutdown (Ubu 3.2 kernel, and Liquorix 3.2).

Bottom line:  Same ol' thing.  Nothing has changed. So, I'm back to wicked (Wicd)...

---

### Post by kansasnoob on 2012-02-08
Got my answer:

[http://ubuntuforums.org/showpost.php?p=11673790&postcount=333](http://ubuntuforums.org/showpost.php?p=11673790&postcount=333)

But the current manifests for the Xubuntu and Lubuntu daily images show they're shipping with the pae kernel :(

---

### Post by kansasnoob on 2012-02-08
BTW I think this link should always list the latest mini.iso:

[http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

It's been a long time since I used one, as I recall not very multi-boot friendly :(

---

### Post by jerrylamos on 2012-02-08
?  IBM Thinkpad T40 Pentium M here doesn't do Unity-3D does Unity-2D just fine.  Doesn't do pae.

Lubuntu pangolin precise pae install 20120207 working fine, see below.  Some installs of precise pangolin like Alpha2 20120204 complain about no pae and stop early in boot.  Others like this one running O.K.?? 

```
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux ThinkPad-T40 3.2.0-14-generic-pae #23-Ubuntu SMP Fri Feb 3 23:33:53 UTC 2012 i686 i686 i386 GNU/Linux

model name	: Intel(R) Pentium(R) M processor 1500MHz
```

Go figure.  Installed, updated, removed Chromium, installed aptitude, gparted, Firefox 11.0 up and running Adobe Flash full speed just fine.

?

Jerry

---

### Post by kansasnoob on 2012-02-08
> **jerrylamos said:**
> ?  IBM Thinkpad T40 Pentium M here doesn't do Unity-3D does Unity-2D just fine.  Doesn't do pae.

Lubuntu pangolin precise pae install 20120207 working fine, see below.  Some installs of precise pangolin like Alpha2 20120204 complain about no pae and stop early in boot.  Others like this one running O.K.?? 

```
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux ThinkPad-T40 3.2.0-14-generic-pae #23-Ubuntu SMP Fri Feb 3 23:33:53 UTC 2012 i686 i686 i386 GNU/Linux

model name	: Intel(R) Pentium(R) M processor 1500MHz
```

Go figure.  Installed, updated, removed Chromium, installed aptitude, gparted, Firefox 11.0 up and running Adobe Flash full speed just fine.

?

Jerry

I don't have a Pentium M, but the February 8th Lubuntu i386 daily manifest shows only pae:

```
linux-generic-pae	3.2.0.14.14
linux-headers-3.2.0-14	3.2.0-14.23
linux-headers-3.2.0-14-generic-pae	3.2.0-14.23
linux-headers-generic-pae	3.2.0.14.14
linux-image-3.2.0-14-generic-pae	3.2.0-14.23
linux-image-generic-pae	3.2.0.14.14
```

Ultimately I'm going to have to rely on those with effected hardware to deal with this.

---

### Post by xyzzyman on 2012-02-08
> **jerrylamos said:**
> ?  IBM Thinkpad T40 Pentium M here doesn't do Unity-3D does Unity-2D just fine.  Doesn't do pae.

Lubuntu pangolin precise pae install 20120207 working fine, see below.  Some installs of precise pangolin like Alpha2 20120204 complain about no pae and stop early in boot.  Others like this one running O.K.?? 

```
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux ThinkPad-T40 3.2.0-14-generic-pae #23-Ubuntu SMP Fri Feb 3 23:33:53 UTC 2012 i686 i686 i386 GNU/Linux

model name	: Intel(R) Pentium(R) M processor 1500MHz
```

Go figure.  Installed, updated, removed Chromium, installed aptitude, gparted, Firefox 11.0 up and running Adobe Flash full speed just fine.

?

Jerry

Can you run a ```
grep PAE /boot/config-3.2.0-14-generic-pae
```

That'll show if PAE is actually turned on in the installed kernel. If it says CONFIG_X86_PAE=y then run a **cat /proc/cpuinfo** just to make sure that pae isn't listed under the flags.

---

### Post by jerrylamos on 2012-02-08
xyzzyman, as you requested:

```
jerry@ThinkPad-T40:~$ grep PAE /boot/config-3.2.0-14-generic-pae
CONFIG_X86_PAE=y

jerry@ThinkPad-T40:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 9
model name	: Intel(R) Pentium(R) M processor 1500MHz
stepping	: 5
microcode	: 0x7
cpu MHz		: 600.000
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2
bogomips	: 1196.18
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 32 bits virtual

```

Whatever that means to someone who knows the bits.  pae isn't listed.

Jerry

---

### Post by kansasnoob on 2012-02-08
What I've been able to find, only the following CPU's are not supported by pae:

Intel CPUs prior to Pentium II 
**[COLOR="Red"]400Mhz Pentium M[/COLOR]**
VIA C3
Geode LX

Of course I can't be sure, but I just tried an old 335mhz PII and even it works with pae :)

---

### Post by xyzzyman on 2012-02-08
> **kansasnoob said:**
> What I've been able to find, only the following CPU's are not supported by pae:

Intel CPUs prior to Pentium II 
**[COLOR="Red"]400Mhz Pentium M[/COLOR]**
VIA C3
Geode LX

Of course I can't be sure, but I just tried an old 335mhz PII and even it works with pae :)

Yeah, that's why they're cutting non-PAE support. You did make a mistake as it's not 400MHz Pentium M's... You got that 400MHz from the 400 MT/s FSB speed. There were some later series Pentium M's with 533 MT/s FSB's that they did re-enable the PAE/NX support.

---

### Post by kansasnoob on 2012-02-09
> **xyzzyman said:**
> Yeah, that's why they're cutting non-PAE support. You did make a mistake as it's not 400MHz Pentium M's... You got that 400MHz from the 400 MT/s FSB speed. There were some later series Pentium M's with 533 MT/s FSB's that they did re-enable the PAE/NX support.

Oops, thanks for the correction.

---

### Post by jerrylamos on 2012-02-09
"kernel requires feature pae and won't boot" shows up on some precise pangolin live boots on my 1.5 gHz Pentium M Thinkpad T40 and sometimes it doesn't.  pae is not listed on the flags.  pab is I have no idea what that is.

So I try one or the other zsync of the .iso until I find one that will boot, example 20120207, even though the generic-pae shows up in /boot and the cpuinfo does not show the pae flag.

Anyone know if the pae function is even being used on precise pangolin?

Thanks, Jerry

p.s.  The T40 running lubuntu precise pangolin just fine, full speed video on BBC news with flash firefox (takes less disk space than chromium and I've read less memory too).

---

### Post by cariboo on 2012-02-09
@jerrylamos, my Atom 270 powered netbook uses the pae kernel.

---

### Post by xyzzyman on 2012-02-09
> **cariboo907 said:**
> @jerrylamos, my Atom 270 powered netbook uses the pae kernel.

All atom's support PAE.

---

### Post by nm_geo on 2012-02-09
> **kansasnoob said:**
> BTW I think this link should always list the latest mini.iso:

[http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

It's been a long time since I used one, as I recall not very multi-boot friendly :(

 Decided to try the non-pae mini.iso this afternoon after cloning my HD.  Wish i had better results to report, the non-pae did not install a kernel from the archive.. So I decide to flush the attempt and see what I could do with the pae mini.iso which did grab a kernel and I am waiting on the lubuntu-desktop to complete to see if it worked.  We will see..

I will probably try that non-pae mini again this weekend when I have more time.

---

### Post by kansasnoob on 2012-02-09
> **nm_geo said:**
> Decided to try the non-pae mini.iso this afternoon after cloning my HD.  Wish i had better results to report, the non-pae did not install a kernel from the archive.. So I decide to flush the attempt and see what I could do with the pae mini.iso which did grab a kernel and I am waiting on the lubuntu-desktop to complete to see if it worked.  We will see..

I will probably try that non-pae mini again this weekend when I have more time.

I was just going to report the same thing ........... no kernel modules found :(

Also the mini.iso's are notorious for "no network interface found" errors. IMHO it makes almost more sense to just install Oneiric and upgrade.

---

### Post by nm_geo on 2012-02-09
> **kansasnoob said:**
> I was just going to report the same thing ........... no kernel modules found :(

Also the mini.iso's are notorious for "no network interface found" errors. IMHO it makes almost more sense to just install Oneiric and upgrade.

I would agree but i am getting it installed on my laptop right now.  Well it is the pae kernel but I wanted to see the mini.iso work or not work.  It sure ain't saving me any time.. Slow as Xmas here.  The alternate CD seems to be the best method for me to install anything.. Ubiquity hates me too :D

---

### Post by nm_geo on 2012-02-09
> **kansasnoob said:**
> I was just going to report the same thing ........... no kernel modules found :(

Also the mini.iso's are notorious for "no network interface found" errors. IMHO it makes almost more sense to just install Oneiric and upgrade.

Okay that would be interesting I have an Oneric that I might just try that on.  Any bets I will be offered a linux-image that has PAE in it.  

You know I reverted to the non-pae in my Ubuntu PP 12.04 and the very next upgrade wanted to install the PAE kernel.. I think they want us to use the PAE kernel ;) which I can run just fine on all my hardware.

---

### Post by xyzzyman on 2012-02-10
> **nm_geo said:**
> Okay that would be interesting I have an Oneric that I might just try that on.  Any bets I will be offered a linux-image that has PAE in it.  

You know I reverted to the non-pae in my Ubuntu PP 12.04 and the very next upgrade wanted to install the PAE kernel.. I think they want us to use the PAE kernel ;) which I can run just fine on all my hardware.

They aren't migrating to PAE kernel so much the large memory support, but as the fact it then enables NX-bit support which is very effective on protecting from buffer overflow exploits. Maybe it's 'cuz they know of a huge security flaw that can't be patched other than by turning on PAE and they just can't tell us!! :P I have no tin foil to make a new hat, and aluminum is not as effective.

Seriously though, I don't know why some people are against running a PAE kernel, as it's not going to harm performance or anything. Anyone who is worried about performance is probably compiling their own kernel anyways specific to just their own hardware.

---

### Post by nm_geo on 2012-02-10
[QUOTE=xyzzyman; snip .. :P I have no tin foil to make a new hat, and aluminum is not as effective.

Seriously though, I don't know why some people are against running a PAE kernel, as it's not going to harm performance or anything. Anyone who is worried about performance is probably compiling their own kernel anyways specific to just their own hardware.[/QUOTE]

I totally agree with everything you said, but we are testers and we like a challenge. So we put on our little tin foil hats on and get after it...:P

All my hardware loves pae kernels.. In fact I have no fault with them either.  

My mini.iso finally finished here on my laptop and other than the login page blinks out and I see partial Unity it worked.. LOL  Oh well, I have a good install of Lubuntu on another partition that works as it should.  I think it may need some breakage now.. out

---

### Post by kansasnoob on 2012-02-10
I just decided to have a look at a Oneiric --> Precise upgrade that I did during iso/upgrade testing, and it had remained pure non-pae, but I decided to update it and things get strange. The upgrade installs some pae parts:

```
linux-generic (3.2.0.12.12) to 3.2.0.15.15
linux-headers-generic (3.2.0.12.12) to 3.2.0.15.15
linux-headers-generic-pae (3.2.0.12.12) to 3.2.0.15.15
linux-image-generic (3.2.0.12.12) to 3.2.0.15.15
```

But only the non-pae shows up in grub:

```
lance@lance-desktop:~$ sudo update-grub
[sudo] password for lance: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-15-generic
Found initrd image: /boot/initrd.img-3.2.0-15-generic
Found linux image: /boot/vmlinuz-3.2.0-12-generic
Found initrd image: /boot/initrd.img-3.2.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin

```

Just FYI the pae kernel works fine for me too :)

---

### Post by dino99 on 2012-02-10
> **kansasnoob said:**
> I just decided to have a look at a Oneiric --> Precise upgrade that I did during iso/upgrade testing, and it had remained pure non-pae, but I decided to update it and things get strange. The upgrade installs some pae parts:

```
linux-generic (3.2.0.12.12) to 3.2.0.15.15
linux-headers-generic (3.2.0.12.12) to 3.2.0.15.15
linux-headers-generic-pae (3.2.0.12.12) to 3.2.0.15.15
linux-image-generic (3.2.0.12.12) to 3.2.0.15.15
```

But only the non-pae shows up in grub:

```
lance@lance-desktop:~$ sudo update-grub
[sudo] password for lance: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-15-generic
Found initrd image: /boot/initrd.img-3.2.0-15-generic
Found linux image: /boot/vmlinuz-3.2.0-12-generic
Found initrd image: /boot/initrd.img-3.2.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin

```

Just FYI the pae kernel works fine for me too :)

How can you says its working as linux-image-generic-pae has not been installed ? So you are still running the "generic" kernel, not the "pae".

---

### Post by kansasnoob on 2012-02-10
> **dino99 said:**
> How can you says its working as linux-image-generic-pae has not been installed ? So you are still running the "generic" kernel, not the "pae".

Where do I say "it's working"?

I only said the latest update installed **some** pae parts :)

The separate statement, "Just FYI the pae kernel works fine for me too", is in regards to the fact that I'm having no problems with the pae kernel. I'm just looking for a reasonable method of installing a non-pae system from scratch so we'll have an answer for those who really need non-pae.

---

### Post by kansasnoob on 2012-02-10
My comment #6 here fairly well explains what I'm doing:

[https://answers.launchpad.net/ubuntu/+source/linux-meta/+question/187166](https://answers.launchpad.net/ubuntu/+source/linux-meta/+question/187166)

> Here's what I know ...... errm, more accurately "what I think I know" ....... so far:

(1) Upgrades from Oneiric w/non-pae to Precise remain non-pae, so those performing upgrades should be OK.

(2) Using the non-pae mini.iso should work:

[http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://www.us.archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

Now, I'd think both of those procedures will be problematic for those without fairly fast ethernet. Additionally I need to do some testing on my own with the mini.iso, for example I'm unsure about the need for "--no-install-recommends" when installing the various desktop environments.

(3) I'm currently waiting for a definitive answer from the Lubuntu devs as to whether or not they'll rebuild their iso's with the non-pae kernel. It would seem somewhat sensible for Lubuntu and Xubuntu to do so since their target audience is older, less powerful hardware.

So ultimately I need some time to get some additional answers, and to perform some testing. I will be responding to both of these forum threads as I learn more:

[http://ubuntuforums.org/showthread.php?t=1919647](http://ubuntuforums.org/showthread.php?t=1919647)

[http://ubuntuforums.org/showthread.php?t=1870442](http://ubuntuforums.org/showthread.php?t=1870442)

Please be patient, my target date for having a definitive answer is March 1st (the proposed release date for Precise Beta 1).

**But testing with 20120208 non-pae mini.iso resulted in failure, no kernel modules could be found on the server**!

---

### Post by kansasnoob on 2012-02-10
Apologies for the communication error with dino99, I was unclear in my prior post.

I know as threads grow, and grow it's hard to keep up, a bit ridiculous for someone to read each and every post when a thread gets several pages long :)

So I made some edits to my OP. Please let me know if I made any errors. Many thanks in advance :D

---

### Post by dino99 on 2012-02-10
> **kansasnoob said:**
> Apologies for the communication error with dino99, I was unclear in my prior post.

I know as threads grow, and grow it's hard to keep up, a bit ridiculous for someone to read each and every post when a thread gets several pages long :)

So I made some edits to my OP. Please let me know if I made any errors. Many thanks in advance :D

no problem brother, you were right and i was not false :) simply talking of 2 different tests :)

---

### Post by SemiExpert on 2012-02-10
In recent months, I've finally gained complete confidence in 64-bit Linux.  The PAE kernel issue is rapidly becoming a moot point.  Yes, there are still older systems, and some very downmarket recent CPUs, that are 32-bit, but I don't think that very many are running 4GB of RAM or more.  In any case, Ubuntu is rapidly becoming too "heavyweight" for older hardware, short of a minimal install.

---

### Post by nm_geo on 2012-02-10
> **kansasnoob said:**
> My comment #6 here fairly well explains what I'm doing:
 
[https://answers.launchpad.net/ubuntu/+source/linux-meta/+question/187166](https://answers.launchpad.net/ubuntu/+source/linux-meta/+question/187166)
 
 
 
**But testing with 20120208 non-pae mini.iso resulted in failure, no kernel modules could be found on the server**!
 
Interesting I had the same issue but Julien said he got it done in the Lubuntu users mail. I will try again this weekend with the non-pae mini.iso.. Just maybe he stopped at the kernel install page while we tried to get the linux-generic kernel.

---

### Post by jerrylamos on 2012-02-10
10+ year old 2002?? IBM Thinkpad R31 running lubuntu precise pangolin A2:

```
jerry@Thinkpad-R31:~$ grep PAE /boot/config-3.2.0-14-generic-pae
CONFIG_X86_PAE=y
jerry@Thinkpad-R31:~$ ls /boot
abi-3.2.0-14-generic-pae     grub                             memtest86+.bin            System.map-3.2.0-14-generic-pae
config-3.2.0-14-generic-pae  initrd.img-3.2.0-14-generic-pae  memtest86+_multiboot.bin  vmlinuz-3.2.0-14-generic-pae
jerry@Thinkpad-R31:~$ 

jerry@Thinkpad-R31:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 11
model name	: Intel(R) Celeron(TM) CPU                1066MHz
stepping	: 1
microcode	: 0x1d
cpu MHz		: 1066.566
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
bogomips	: 2133.13
clflush size	: 32
cache_alignment	: 32
address sizes	: 36 bits physical, 32 bits virtual
power management:
MemTotal:         499344 kB
[CODE]

Note that old Celeron does have a pae flag.

Runs internet O.K. videos are pretty jerky.

Jerry

p.s  biggest ubuntu problems have been the Intel graphics controller:
[CODE]jerry@Thinkpad-R31:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
```
which has not run compiz since Intrepid.  No problem to me I even run the newere pc's Unity-2D to get rid of Compiz bugs and Compiz overhead even when running full screen applications...

---

### Post by kansasnoob on 2012-02-10
It looks like you can totally mimic the mini.iso using the alternate CD this way:

Select language

Press F4

Select Install Command Line System

Press enter

Then the CLI install begins, but sadly you'll still be faced with the same errors, like:

No network interface found

No kernel modules found

So, ATM installing a non-pae system is just a dream :(

Adding, for the anal among us, I do NOT need non-pae but some people will need it!

If I limited my testing to only what effects me I wouldn't really be a tester :D

---

### Post by kansasnoob on 2012-02-10
> **jerrylamos said:**
> 10+ year old 2002?? IBM Thinkpad R31 running lubuntu precise pangolin A2:

```
jerry@Thinkpad-R31:~$ grep PAE /boot/config-3.2.0-14-generic-pae
CONFIG_X86_PAE=y
jerry@Thinkpad-R31:~$ ls /boot
abi-3.2.0-14-generic-pae     grub                             memtest86+.bin            System.map-3.2.0-14-generic-pae
config-3.2.0-14-generic-pae  initrd.img-3.2.0-14-generic-pae  memtest86+_multiboot.bin  vmlinuz-3.2.0-14-generic-pae
jerry@Thinkpad-R31:~$ 

jerry@Thinkpad-R31:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 11
model name	: Intel(R) Celeron(TM) CPU                1066MHz
stepping	: 1
microcode	: 0x1d
cpu MHz		: 1066.566
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
bogomips	: 2133.13
clflush size	: 32
cache_alignment	: 32
address sizes	: 36 bits physical, 32 bits virtual
power management:
MemTotal:         499344 kB
[CODE]

Note that old Celeron does have a pae flag.

Runs internet O.K. videos are pretty jerky.

Jerry

p.s  biggest ubuntu problems have been the Intel graphics controller:
[CODE]jerry@Thinkpad-R31:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
```
which has not run compiz since Intrepid.  No problem to me I even run the newere pc's Unity-2D to get rid of Compiz bugs and Compiz overhead even when running full screen applications...

This is not about being able to run Compiz. Some people can't install at all :(

---

### Post by MoreOrLess on 2012-02-10
> **jerrylamos said:**
> 10+ year old 2002?? IBM Thinkpad R31 running lubuntu precise pangolin A2:

That's irrelevant to this thread and to your Pentium M system, which doesn't have pae...

---

### Post by effenberg0x0 on 2012-02-10
(Keep in mind I'm really tired and haven't really read the entire discussion.)

What if you add a mem=4096M kernel parameter at the kernel cmdline? Wouldn't that sort of override CONFIG_HIGHMEM64G=y and act like if CONFIG_HIGHMEM4G=y was set in the kernel config? Or then you just get a panic?
(I don't have non-pae hw to test).

Regards,
Effenberg

---

### Post by kansasnoob on 2012-02-10
> **effenberg0x0 said:**
> (Keep in mind I'm really tired and haven't really read the entire discussion.)

What if you add a mem=4096M kernel parameter at the kernel cmdline? Wouldn't that sort of override CONFIG_HIGHMEM64G=y and act like if CONFIG_HIGHMEM4G=y was set in the kernel config? Or then you just get a panic?
(I don't have non-pae hw to test).

Regards,
Effenberg

No idea, but all suggestions are welcome :D

Since I don't have any effected hardware I can't effectively test that but I certainly hope someone will.

Many thanks :D

---

### Post by kansasnoob on 2012-02-10
It would be awesome if someone could confirm this bug and include an effected hardware profile:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/930447)

---

### Post by xyzzyman on 2012-02-10
> **kansasnoob said:**
> No idea, but all suggestions are welcome :D

Since I don't have any effected hardware I can't effectively test that but I certainly hope someone will.

Many thanks :D

If you do a virtualbox, you not only have to make sure 'PAE/NX' is not checked, but **also** run with VT-X **disabled**. Then you'll have a virtual machine with no PAE flag and you'll get the error.

---

### Post by xyzzyman on 2012-02-10
> **effenberg0x0 said:**
> (Keep in mind I'm really tired and haven't really read the entire discussion.)

What if you add a mem=4096M kernel parameter at the kernel cmdline? Wouldn't that sort of override CONFIG_HIGHMEM64G=y and act like if CONFIG_HIGHMEM4G=y was set in the kernel config? Or then you just get a panic?
(I don't have non-pae hw to test).

Regards,
Effenberg

CONFIG_X86_PAE=y is the relevant config option so I don't think that'll make a difference.

---

### Post by nm_geo on 2012-02-10
:P> **kansasnoob said:**
>  <Snip>
Adding, for the anal among us, I do NOT need non-pae but some people will need it!

If I limited my testing to only what effects me I wouldn't really be a tester :D


[LIST]
[*][SIZE=4]LMAO.. [SIZE=1]kansas I be thinking some of those anal peeps are commentors not testers anyway you made my day THX  :P
[/SIZE][/SIZE]
[/LIST]

---

### Post by effenberg0x0 on 2012-02-10
> **xyzzyman said:**
> CONFIG_X86_PAE=y is the relevant config option so I don't think that'll make a difference.

Hey xyzzyman,

I think I didn't express myself decently. Of course .config will do nothing if a kernel is not rebuilt. But, I was considering if no memory is used over the 4GB limit, the panic on boot could be avoided. Considering CONFIG_X86_PAE=y depends on CONFIG_HIGHMEM64G=y, if one limits ram usage to 4GB via kernel boot parameter, I wondered if it would be like when when you set CONFIG_HIGHMEM4G=y (which would invalidate CONFIG_X86_PAE=y).

In other words, if you have a pae-kernel in non-pae hardware, but you force the kernel to stay under 4GB: is that enough to boot, or do you get a panic anyway?

I thought it would be a good shot. But I have just tested a pae-kernel in a non-pae VM and no matter what kernel parameter I try, the "get an adequate Kernel" shows. You can't even kexec into a pae-kernel without crashing.

Regards,
Effenberg

---

### Post by xyzzyman on 2012-02-10
> **effenberg0x0 said:**
> Hey xyzzyman,

I think I didn't express myself decently. Of course .config will do nothing if a kernel is not rebuilt. But, I was considering if no memory is used over the 4GB limit, the panic on boot could be avoided. Considering CONFIG_X86_PAE=y depends on CONFIG_HIGHMEM64G=y, if one limits ram usage to 4GB via kernel boot parameter, I wondered if it would be like when when you set CONFIG_HIGHMEM4G=y (which would invalidate CONFIG_X86_PAE=y).

In other words, if you have a pae-kernel in non-pae hardware, but you force the kernel to stay under 4GB: is that enough to boot, or do you get a panic anyway?

I thought it would be a good shot. But I have just tested a pae-kernel in a non-pae VM and no matter what kernel parameter I try, the "get an adequate Kernel" shows. You can't even kexec into a pae-kernel without crashing.

Regards,
Effenberg

I've only looked through the kernel source tree about 10 minutes, but it seems that enabling PAE is akin to the type of change of moving it to Core2 instead of just x86. It's not just enabling additional support, but it actually makes a difference on everything being compiled. So it's either PAE or not, no matter what RAM is in the unit or what limits you place. :( The message when you try boot is hard coded in as a hard stop instead of an actual kernel panic. I've read that you used to be able to boot further with a PAE kernel on non-PAE, so I think they've added on that on purpose 'cuz it's a guaranteed crash.

---

### Post by dcstar on 2012-02-10
> **kansasnoob said:**
> What I've been able to find, only the following CPU's are not supported by pae:

Intel CPUs prior to Pentium II 
**[COLOR="Red"]400Mhz Pentium M[/COLOR]**
VIA C3
Geode LX

Of course I can't be sure, but I just tried an old 335mhz PII and even it works with pae :)

At last, someone with a relevant contribution to the discussion - well done.

There is no reason that I have yet seen **not** to use a PAE kernel for compatible i386 systems. The only "downside" is a slightly fatter kernel with the PAE code - which won't even be used if there is less than 4GB of RAM installed.

If the only reason to keep a non-PAE kernel around is to support the tiny number of existing systems currently in use that need it, then that is a pretty poor reason and it is no wonder it is being phased out.

If people want to cling onto 32-bit distributions then that is their problem, some of us have been using 64-bit Ubuntu for many years now without any significant issues (especially now Adobe have got their act together with the Flash plugin). PAE is as irrelevant to us in the same way EMS became irrelevant when the 486 CPU was released.

---

### Post by kansasnoob on 2012-02-11
I just spent a few hours chasing my own tail :oops:

One of the problems I was having with the non-pae mini.iso was a "no network interface found" error on my preferred testing box. It typically multi-boots Win XP and at least two *ubuntu's, and strangely I was connecting to my ethernet OK using any OS I tried, but if I'd run:

```
lspci | grep Ethernet
``` 

There simply was no terminal output whatsoever :confused:

I must've looked in the BIOS at least 4 times before I found that "Onboard LAN device" was disabled :(

How in the world that happened, or why I still had a connection at all, I'll never understand. Don't you just hate wasting time and finding the problem was the idiot between the chair and the keyboard :redface:

---

### Post by jerrylamos on 2012-02-11
My opinion, no pc's with non-pae and more than 3 GB memory were -ever- built so ubuntu  can save some code by not even checking....

Jerry

---

### Post by danniel on 2012-02-11
> **kansasnoob said:**
> and include an effected hardware profile

How do you do that? I tried with *apport-collect* but it says that I'm not the bug submitter.

---

### Post by danniel on 2012-02-11
> **dcstar said:**
> There is no reason that I have yet seen **not** to use a PAE kernel for compatible i386 systems.
............
If people want to cling onto 32-bit distributions then that is their problem, some of us have been using 64-bit Ubuntu for many years now without any significant issues 
First you say that there's no reason not to use PAE, and later you mention that people should use 64 bit :)

I agree that 64 bit is the way to go (but keep the 32 bit without PAE for older systems). PAE is useless.

---

### Post by dino99 on 2012-02-11
> **danniel said:**
> 

 PAE is useless.

You only speaking for yourself

---

### Post by xyzzyman on 2012-02-11
> **jerrylamos said:**
> My opinion, no pc's with non-pae and more than 3 GB memory were -ever- built so ubuntu  can save some code by not even checking....

Jerry

Without the check it will wind up crashing even with less than 3GB's of RAM as everything gets compiled expecting the NX bit for security. The check was put in the kernel to block the inevitable.

---

### Post by kansasnoob on 2012-02-11
> **danniel said:**
> How do you do that? I tried with *apport-collect* but it says that I'm not the bug submitter.

Yes, "apport-collect" only works for the original bug reporter AFAIK.

Do you have hardware that's effected by the change to pae?

If so just select "this bug effects me too", then subscribe to the bug. You'll see on the right side where it'll say "you are (or not)" subscribed to the bug report.

Then add a comment including some basic info about your CPU:

```
cat /proc/cpuinfo
```

If you prefer creating a text file from that command you could run:

```
cat /proc/cpuinfo > CPU_info.txt
```

Then the output will show up in your home folder so you can just attach the file.

Have I helped you or only confused you?

IMHO it's imperative for those effected to report this! I'm not effected so I can only express my opinion. After much thought my opinion is simple:

(1) Ubuntu/Canonical decided to support non-pae throughout the Precise life-cycle.

(2) Both pae and non-pae are now in the repos and it'll remain that way throughout the five year Precise life-cycle.

(3) While non-pae is in the repos and supported it's going to be difficult for someone requiring non-pae to perform a fresh install of Precise.

(3a) Apparently the only way to do so will be upgrading from a Oneiric install or using the non-pae mini.iso

(3b) Both of those procedures require relatively fast ethernet, but many people with older hardware are also likely to have a slow connection.

(4) It would be much better to release Precise with non-pae as the default. Since all required parts of both pae and non-pae will be in the repos it would be easy for those who desire pae to choose to use it after installation, but those who require non-pae will have to jump through a lot of hoops to install a non-pae system.

(5) I need to follow up on this a lot, but so far it seems that after the initial upgrade from either Lucid or Oneiric no pae packages are installed, but recent updates begin to install some "parts" of the pae kernel that only add to system bloat!

Ultimately, since I have no effected hardware, I can only act as an advocate of whet I think should be done. It's going to be up to those directly effected to get this changed!!!!!!!!!!!!!

---

### Post by kansasnoob on 2012-02-11
> **xyzzyman said:**
> Without the check it will wind up crashing even with less than 3GB's of RAM as everything gets compiled expecting the NX bit for security. The check was put in the kernel to block the inevitable.

+1!

If it were just easy there'd be no controversy ;)

---

### Post by kansasnoob on 2012-02-11
> **danniel said:**
> First you say that there's no reason not to use PAE, and later you mention that people should use 64 bit :)

I agree that 64 bit is the way to go (but keep the 32 bit without PAE for older systems). PAE is useless.

Agreed. IMHO this is akin to the Xorg devs deciding to change the "kill-x" shortcut. At one point it devolved to where one of the devs blamed his cat.

DUH :confused:

Most cats have four paws so they can easily hit any 3 or 4 key combo :D

But I do blame my dogs for a lot of stuff I do :redface:

---

### Post by xyzzyman on 2012-02-11
> **kansasnoob said:**
> 
(4) It would be much better to release Precise with non-pae as the default. Since all required parts of both pae and non-pae will be in the repos it would be easy for those who desire pae to choose to use it after installation, but those who require non-pae will have to jump through a lot of hoops to install a non-pae system.

I wonder if the energy is better directed at (l/x)ubuntu for them to build their live cd with the non-pae kernel. The argument for change on the ubuntu side is weak because anyone with affected hardware is not going to be able to use unity well, and it's a simple configuration change for the (l/x)ubuntu team because the packages are there and just has to be built with the other kernel...

PS: Thank you for using effected and not affected. :)

---

### Post by kansasnoob on 2012-02-11
> **xyzzyman said:**
> I wonder if the energy is better directed at (l/x)ubuntu for them to build their live cd with the non-pae kernel. The argument for change on the ubuntu side is weak because anyone with affected hardware is not going to be able to use unity well, and it's a simple configuration change for the (l/x)ubuntu team because the packages are there and just has to be built with the other kernel...

PS: Thank you for using effected and not affected. :)

I already checked with Lubuntu, they won't. I'd appreciate someone checking with Xubuntu :)

---

### Post by jerrylamos on 2012-02-11
> **xyzzyman said:**
> Without the check it will wind up crashing even with less than 3GB's of RAM as everything gets compiled expecting the NX bit for security. The check was put in the kernel to block the inevitable.

Hmmm.  This comment is from IBM Thinkpad T40 which does not have a pae flag:

```
flags: fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2
 
jerry@ThinkPad-T40:~$ grep PAE /boot/config-3.2.0-15-generic-pae
CONFIG_X86_PAE=y
```

and is running lubuntu precise pangolin A2

Maybe by mistake nothing's using pae or NX bit (is there a flag for that?).

Some precise daily builds do a check and won't boot, I suspect this daily build 20120207 updated to -15-generic-pae didn't check so it runs O.K.??

Jerry

---

### Post by xyzzyman on 2012-02-11
> **jerrylamos said:**
> Hmmm.  This comment is from IBM Thinkpad T40 which does not have a pae flag:

```
flags: fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2
 
jerry@ThinkPad-T40:~$ grep PAE /boot/config-3.2.0-15-generic-pae
CONFIG_X86_PAE=y
```

and is running lubuntu precise pangolin A2

Maybe by mistake nothing's using pae or NX bit (is there a flag for that?).

Some precise daily builds do a check and won't boot, I suspect this daily build 20120207 updated to -15-generic-pae didn't check so it runs O.K.??

Jerry

Can you do an ls on the /boot directory and a uname -a? It's not really important, just wondering why you're the first report I've found of anyone getting a kernel with PAE enabled to boot up without the kernel refusing as it's coded in upstream and all distro's are affected 'cuz it's not an ubuntu sauce.

---

### Post by jerrylamos on 2012-02-11
> **xyzzyman said:**
> Can you do an ls on the /boot directory and a uname -a? It's not really important, just wondering why you're the first report I've found of anyone getting a kernel with PAE enabled to boot up without the kernel refusing as it's coded in upstream and all distro's are affected 'cuz it's not an ubuntu sauce.

Sure:

```
jerry@ThinkPad-T40:~$ ls /boot
abi-3.2.0-15-generic-pae     grub                             memtest86+.bin            System.map-3.2.0-15-generic-pae
config-3.2.0-15-generic-pae  initrd.img-3.2.0-15-generic-pae  memtest86+_multiboot.bin  vmlinuz-3.2.0-15-generic-pae

jerry@ThinkPad-T40:~$ uname -a
Linux ThinkPad-T40 3.2.0-15-generic-pae #24-Ubuntu SMP Tue Feb 7 23:30:35 UTC 2012 i686 i686 i386 GNU/Linux
```

I have run straight ubuntu precise pangolin on this T40 but at the moment have two lubuntu precise pangolin, lucid LTS, and a meerkat installed.

Somewhere in this thread said said 400 MHZ Pentium M wouldn't run, this is a 1 GHZ Pentium M with 768 MB memory.

Jerry

---

### Post by xyzzyman on 2012-02-11
> **jerrylamos said:**
> Sure:

```
jerry@ThinkPad-T40:~$ ls /boot
abi-3.2.0-15-generic-pae     grub                             memtest86+.bin            System.map-3.2.0-15-generic-pae
config-3.2.0-15-generic-pae  initrd.img-3.2.0-15-generic-pae  memtest86+_multiboot.bin  vmlinuz-3.2.0-15-generic-pae

jerry@ThinkPad-T40:~$ uname -a
Linux ThinkPad-T40 3.2.0-15-generic-pae #24-Ubuntu SMP Tue Feb 7 23:30:35 UTC 2012 i686 i686 i386 GNU/Linux
```

I have run straight ubuntu precise pangolin on this T40 but at the moment have two lubuntu precise pangolin, lucid LTS, and a meerkat installed.

Somewhere in this thread said said 400 MHZ Pentium M wouldn't run, this is a 1 GHZ Pentium M with 768 MB memory.

Jerry

Your cpuinfo says it's a 1.5GHz. The PAE supporting Pentium M's weren't made until 1.6GHz. I wonder if it's actually one of those, and purposely downclocked to 1.5GHz? They do that at times at the factory. And however cpuinfo gets the flags is different than the kernel does which may be reading it at a lower level? The relevant files in the kernel tree are /arch/x86/boot/cpu.c and cpustr.h and it's pretty straightforward of how it checks for a long list of required cpu flags.

It's also 400 MT/s FSB. They never made 400MHz Pentium M's.

Is there anything in your dmesg log related to PAE or NX bit or memory addressing?

---

### Post by VinDSL on 2012-02-11
> **xyzzyman said:**
> It's also 400 MT/s FSB. They never made 400MHz Pentium M's.[...]
Sounds like a "Banius-512", so called:

SOURCE: [http://www.cpu-world.com/CPUs/Celeron_M/Intel-Celeron%20M%20340%20RH80535NC021512.html](http://www.cpu-world.com/CPUs/Celeron_M/Intel-Celeron%20M%20340%20RH80535NC021512.html)

Frequency: .6 - 1.5 GHz / Bus: 400 MHz  ;)

---

### Post by jerrylamos on 2012-02-11
> **xyzzyman said:**
> Your cpuinfo says it's a 1.5GHz. .... The relevant files in the kernel tree are /arch/x86/boot/cpu.c and cpustr.h and it's pretty straightforward of how it checks for a long list of required cpu flags.

Is there anything in your dmesg log related to PAE or NX bit or memory addressing?

xyzzyman, only thing search found was the pae in the title.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-15-generic-pae (buildd@zirconium) (gcc version 4.6.2 (Ubuntu/Linaro 4.6.2-12ubuntu1) ) #24-Ubuntu SMP Tue Feb 7 23:30:35 UTC 2012 (Ubuntu 3.2.0-15.24-generic-pae 3.2.5)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002ff60000 (usable)
[    0.000000]  BIOS-e820: 000000002ff60000 - 000000002ff77000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002ff77000 - 000000002ff79000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002ff80000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: IBM 23736U0/23736U0, BIOS 1RETDNWW (3.19 ) 10/13/2005
```

NX might have a workaround according to above dmesg info.

Yes, slip of the finger, it's 1.5 GHZ.

Any way to check on the other bits you mentioned?

Thanks, Jerry

---

### Post by xyzzyman on 2012-02-11
> **VinDSL said:**
> Sounds like a "Banius-512", so called:

SOURCE: [http://www.cpu-world.com/CPUs/Celeron_M/Intel-Celeron%20M%20340%20RH80535NC021512.html](http://www.cpu-world.com/CPUs/Celeron_M/Intel-Celeron%20M%20340%20RH80535NC021512.html)

Frequency: .6 - 1.5 GHz / Bus: 400 MHz  ;)

I don't see any CPU's clocked at 400 MHz on there. I think the Celeron M's were just half L2 cache'd Pentium M's, but were also sold as Centrino's, so they don't support PAE & NX until the end when they switched to 533 MT/s FSB's.

---

### Post by VinDSL on 2012-02-11
> **xyzzyman said:**
> I don't see any CPU's clocked at 400 MHz on there.[...]
Maybe that site is wrong.  Let's try Intel...  ;)

SOURCE:  [http://ark.intel.com/products/27353/Mobile-Intel-Pentium-4-Processor---M-1_50-GHz-512K-Cache-400-MHz-FSB](http://ark.intel.com/products/27353/Mobile-Intel-Pentium-4-Processor---M-1_50-GHz-512K-Cache-400-MHz-FSB)

We don't know what's in there... Jerry doesn't even know.  LoL!

However, it would appear that some Pentium Ms had a 400 MHz FSB.  Yes?

---

### Post by xyzzyman on 2012-02-12
> **VinDSL said:**
> Maybe that site is wrong.  Let's try Intel...  ;)

SOURCE:  [http://ark.intel.com/products/27353/Mobile-Intel-Pentium-4-Processor---M-1_50-GHz-512K-Cache-400-MHz-FSB](http://ark.intel.com/products/27353/Mobile-Intel-Pentium-4-Processor---M-1_50-GHz-512K-Cache-400-MHz-FSB)

We don't know what's in there... Jerry doesn't even know.  LoL!

However, it would appear that some Pentium Ms had a 400 MHz FSB.  Yes?

That's the FSB speed, not the CPU speed.

EDIT: I edited the post 'cuz I posted too early... I don't know why it reposted it?

---

### Post by xyzzyman on 2012-02-12
> **VinDSL said:**
> Maybe that site is wrong.  Let's try Intel...  ;)

SOURCE:  [http://ark.intel.com/products/27353/Mobile-Intel-Pentium-4-Processor---M-1_50-GHz-512K-Cache-400-MHz-FSB](http://ark.intel.com/products/27353/Mobile-Intel-Pentium-4-Processor---M-1_50-GHz-512K-Cache-400-MHz-FSB)

We don't know what's in there... Jerry doesn't even know.  LoL!

However, it would appear that some Pentium Ms had a 400 MHz FSB.  Yes?

That's the FSB speed, not the CPU speed. Funny thing is those Pentium M's are actually just a 100MHz FSB that are quad pumped so they should be listed as 400 MT/s ([http://en.wikipedia.org/wiki/Front-side_bus](http://en.wikipedia.org/wiki/Front-side_bus)). The marketing department lists them at 400 MHz which is incorrect. I've never had a problem with HDD MFG's using base-10 instead of base-2, but what they do is like saying a 4 lane highway with a speed limit of 100MPH is actually a 400MPH speed limit.

---

### Post by jerrylamos on 2012-02-12
precise pangolin 12.04 should not do a check of the pae flag and refuse to boot - see my posts above, 

This non-pae non-NX is running lubuntu precise pangolin just fine.  I have run ubuntu precise pangolin 12.04 on it but don't at the moment.  

Compiz -3D code doesn't run on its level of ATI video, but -2D runs just fine.  I've got -2D and -3D on other test pc's so I've been running lubuntu here for testing purposes.

Since this thread came up, I think I'll install -2D in another partition to verify function.

Note this notebook is circa 2005 (from the bios date) which is in my opinion not that old, and it is quite happy to run BBC videos full speed.  I don't view this pc as being obsolete.

Now I don't know how to feed this pae info back to development - a launchpad bug?

Thanks, Jerry

---

### Post by kansasnoob on 2012-02-12
Regarding the non-pae mini.iso I decided to give things a new look since I figured out that networking problem. I already new that the 20120208 image was borked so I dl'ed and burned the 20120209 iso (newest ATM).

First test, I chose CLI install rather than just "install" because I wanted to check on the need for 'python-software-properties'.

I have very fast ethernet, slightly exceeding 5000 kbps, and the initial CLI install took 45 minutes, then I had to boot into recovery mode, choose enable networking, then choose drop to root, followed by:

```
apt-get install ubuntu-desktop
```

The downloads and installation took another 55 minutes :(

So I'm repeating by just choosing "install" to see what happens but using the CLI install appears to take a minimum of 1 hour and 40 minutes with a DL speed of 5000+ kbps :o

How jacked is that :confused:

---

### Post by xyzzyman on 2012-02-12
> **jerrylamos said:**
> precise pangolin 12.04 should not do a check of the pae flag and refuse to boot - see my posts above, 

This non-pae non-NX is running lubuntu precise pangolin just fine.  I have run ubuntu precise pangolin 12.04 on it but don't at the moment.  

Compiz -3D code doesn't run on its level of ATI video, but -2D runs just fine.  I've got -2D and -3D on other test pc's so I've been running lubuntu here for testing purposes.

Since this thread came up, I think I'll install -2D in another partition to verify function.

Note this notebook is circa 2005 (from the bios date) which is in my opinion not that old, and it is quite happy to run BBC videos full speed.  I don't view this pc as being obsolete.

Now I don't know how to feed this pae info back to development - a launchpad bug?

Thanks, Jerry

The check is not done by Ubuntu, it's in the mainline kernel source so place the blame correctly. The sauce patches are just supposed to add functionality that hasn't made it to mainline (newer version of apparmor or the ureadahead support) & backports. According to everything I've read about their internal structure for the kernel is that everything they change has to be submit-worthy for upstream change. So if you want the kernel not to check for PAE support you'll have to go upstream and message Linus Torvalds, [email]torvalds@osdl.org[/email]. Go ahead. Email him.

Your best bet is to start looking at the kernel source, and figure out why your Pentium M passes the PAE check when no one elses does. That's the best way to learn is to dig and and figure it out yourself sometimes, because you have something different than everyone else.

---

### Post by xyzzyman on 2012-02-12
Wouldn't it be easier if anyone really cares about a 12.04 build with non-PAE kernel, to just make their own build and distribute it when the final release is out? If you look up, alot of the other distro's have already had this discussion and they've gone with PAE in years past.

---

### Post by jerrylamos on 2012-02-12
> **xyzzyman said:**
> Your best bet is to start looking at the kernel source, and figure out why your Pentium M passes the PAE check when no one elses does. That's the best way to learn is to dig and and figure it out yourself sometimes, because you have something different than everyone else.

"when no one elses does" do you have some users that have reported this?

Since precise pangolin is running fine on this non-pae pc then checking for the flag is going to block precise pangolin from running on pc's where it will run just fine.

I'm not a developer and have no ability to read/modify/recompile the kernel source.

Jerry

---

### Post by kansasnoob on 2012-02-12
> **xyzzyman said:**
> Wouldn't it be easier if anyone really cares about a 12.04 build with non-PAE kernel, to just make their own build and distribute it when the final release is out? If you look up, alot of the other distro's have already had this discussion and they've gone with PAE in years past.

My only concern is testing official Ubuntu images and upgrades ................ well, I do give in to using PPA's where needed and tweaking things, but if the two methods for keeping non-pae remain using the non-pae mini.iso and upgrading from either Lucid or Oneiric that's what I'll focus on :D

If someone else wants to pursue a different path I have no problem with that.

---

### Post by kansasnoob on 2012-02-12
> **jerrylamos said:**
> "when no one elses does" do you have some users that have reported this?

Since precise pangolin is running fine on this non-pae pc then checking for the flag is going to block precise pangolin from running on pc's where it will run just fine.

I'm not a developer and have no ability to read/modify/recompile the kernel source.

Jerry

My thought is simply:

If you have effected hardware please report it!

If your hardware is not effected but you still want to do some testing please test the non-pae mini.iso:

[http://ubuntuforums.org/showthread.php?t=1924455](http://ubuntuforums.org/showthread.php?t=1924455)

Or install Lucid and/or Oneiric, then upgrade and be sure that non-pae remains non-pae.

That said, the final Lucid "step-release" comes on the 16th of this month :)

---

### Post by effenberg0x0 on 2012-02-12
Something interesting happened, I thought I should share with you. I have a Dell Vostro Laptop which didn't had BIOS PAE support, although the CPU is a Intel C2D that supports PAE. I'm not gonna use this laptop anymore, so I was installing PP "Senior Edition" and will give it to my mother. But I made a very stupid mistake: I had a password set on Boot and forgot what it was (it's been off for months now). And I was really not in the mood to open it, find the battery and remove it to clear the BIOS. 

Then a friend of mine knew a guy who sells "master" passwords for any brand of laptop. So, I got in touch with the guy, donated to him via PayPal, sent him my Dell Service Tag number and within minutes se sent me a BIOS password.

It worked, I was inside the BIOS as usual but... the BIOS now had twice more options. And the option to enable NX an PAE was there (it never was, not even in BIOS administrator mode).

I enabled it and tested a 32-Bit PAE-Enabled kernel and, of course, it worked. I mailed the guy again and he told me most "Master" BIOS passwords, for all brands, allow you to set the NX/PAE option.

So, if you got some hardware that should support it cpu-wise, but don't have any options to enable it in the BIOS, consider looking on the net or ask you equipment manufacturer for a BIOS "Master" password and you might be able to enable it.

Regards,
Effenberg

---

### Post by kansasnoob on 2012-02-12
> **effenberg0x0 said:**
> Something interesting happened, I thought I should share with you. I have a Dell Vostro Laptop which didn't had BIOS PAE support, although the CPU is a Intel C2D that supports PAE. I'm not gonna use this laptop anymore, so I was installing PP "Senior Edition" and will give it to my mother. But I made a very stupid mistake: I had a password set on Boot and forgot what it was (it's been off for months now). And I was really not in the mood to open it, find the battery and remove it to clear the BIOS. 

Then a friend of mine knew a guy who sells "master" passwords for any brand of laptop. So, I got in touch with the guy, donated to him via PayPal, sent him my Dell Service Tag number and within minutes se sent me a BIOS password.

It worked, I was inside the BIOS as usual but... the BIOS now had twice more options. And the option to enable NX an PAE was there (it never was, not even in BIOS administrator mode).

I enabled it and tested a 32-Bit PAE-Enabled kernel and, of course, it worked. I mailed the guy again and he told me most "Master" BIOS passwords, for all brands, allow you to set the NX/PAE option.

So, if you got some hardware that should support it cpu-wise, but don't have any options to enable it in the BIOS, consider looking on the net or ask you equipment manufacturer for a BIOS "Master" password and you might be able to enable it.

Regards,
Effenberg

I wonder if flashing the BIOS on some of these Pentium M's would be an option :confused:

I'm totally clueless.

---

### Post by xyzzyman on 2012-02-12
> **kansasnoob said:**
> I wonder if flashing the BIOS on some of these Pentium M's would be an option :confused:

I'm totally clueless.

While it's possible for microcode to be updated via a BIOS flash, you wouldn't be able to do that much via that sort of update. Those are just very small fixes.

---

### Post by kansasnoob on 2012-02-12
> **xyzzyman said:**
> While it's possible for microcode to be updated via a BIOS flash, you wouldn't be able to do that much via that sort of update. Those are just very small fixes.

I really had no idea.

ATM I'm going to focus on what I know:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/897786/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/897786/comments/9)

[https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000367.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000367.html)

I test, that's what I do. So I'll test the non-pae mini.iso and watch what happens during upgrades from Lucid and Oneiric to Precise.

---

### Post by jerrylamos on 2012-02-13
> **kansasnoob said:**
> I really had no idea.

ATM I'm going to focus on what I know:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/897786/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/897786/comments/9)

[https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000367.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000367.html)

I test, that's what I do. So I'll test the non-pae mini.iso and watch what happens during upgrades from Lucid and Oneiric to Precise.

For what it's worth, I downloaded the regular pae I think mini.iso and installed it on this IBM Thinkpad T40 which has no pae flag.  Messages during the install were "generic-pae" files being fetched.  When I booted the install the /boot files were generic without the pae.  Runs fine.

Jerry

---

### Post by xyzzyman on 2012-02-14
> **jerrylamos said:**
> For what it's worth, I downloaded the regular pae I think mini.iso and installed it on this IBM Thinkpad T40 which has no pae flag.  Messages during the install were "generic-pae" files being fetched.  When I booted the install the /boot files were generic without the pae.  Runs fine.

Jerry

Now download and add the pae kernel and see what happens. :) Come on, it's science!

---

### Post by jerrylamos on 2012-02-14
> **xyzzyman said:**
> Now download and add the pae kernel and see what happens. :) Come on, it's science!

O.K., how do I do that?

Jerry

---

### Post by kansasnoob on 2012-02-14
I have a request, but first let me state what I currently think to be true. Note that I'm basing this mostly on responses at Launchpad which I think is one of our most trusted sources.

There will be three "official" paths for attaining a non-pae kernel:

#1: Upgrade from Oneiric (11.10)

#2: Upgrade from Lucid (10.04) - this seems quite reasonable since 10.04.4 is due in just a couple of days.

#3: Use the non-pae mini.iso which I'm currently testing:

[http://ubuntuforums.org/showthread.php?t=1924455](http://ubuntuforums.org/showthread.php?t=1924455)

Now comes the request :)

I've already checked with the Lubuntu devs and they will not be rebuilding with the non-pae kernel:

[https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000367.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000367.html)

So [B]could someone check with the Xubuntu devs?
[/B]
I've got my hands full :redface:

Once I know what Xubuntu's plan is I can update my OP with totally accurate info :D

I personally only care about the official Ubuntu policy regarding this change, but I have no problem with others choosing a different path. I have no plans, or desire to create a non-pae rebuild myself.

---

### Post by jerrylamos on 2012-02-14
For what it's worth, this is from an IBM Thinkpad T40 which does not have a pae flag.  The install was from the regular mini.iso yesterday, The .iso was dated Feb 9.

During install the messages said "generic-pae" however on booting after install the boot modules were all generic.

So if you're curious like I was, try installing the regular mini.iso on a non-pae pc.  It worked for me.

Jerry

---

### Post by jerrylamos on 2012-02-14
Anybody else out there trying anything?  This is live 20120214 daily build:

ubuntu@lubuntu:~$ cat /proc/version
Linux version 3.2.0-15-generic-pae (buildd@zirconium) (gcc version 4.6.2 (Ubuntu/Linaro 4.6.2-12ubuntu1) ) #24-Ubuntu SMP Tue Feb 7 23:30:35 UTC 2012

On a T40 that has no pae flag.  A few weeks ago, it wouldn't boot because the live environment checked for the pae flag.  Maybe the check is broken, and maybe no software is using the pae function?

I'm having fun testing & installing anyway.  precise pangolin is supposed to be very LTS, i.e. stable, which is to say "boring" for this tester....not that there aren't bugs, just not any that are stopping me (yet!).

Jerry

---

### Post by jerrylamos on 2012-02-14
> **xyzzyman said:**
> Now download and add the pae kernel and see what happens. :) Come on, it's science!

Here you are:

jerry@ThinkPad-T40:~$ cat /proc/version
Linux version 3.2.0-16-generic-pae (buildd@zirconium) (gcc version 4.6.2 (Ubuntu/Linaro 4.6.2-14ubuntu1) ) #25-Ubuntu SMP Tue Feb 14 04:00:45 UTC 2012

Installed from
[http://cdimage.ubuntu.com/lubuntu/daily-live/current/precise-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/daily-live/current/precise-desktop-i386.iso)

precise-desktop-i386.iso            14-Feb-2012 17:25  554M  Desktop CD for PC (Intel x86) computers (standard download)

erry@ThinkPad-T40:~$ grep PAE /boot/config-3.2.0-16-generic-pae
CONFIG_X86_PAE=y

model name	: Intel(R) Pentium(R) M processor 1500MHz
flags		: fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2

synaptic crash on reloading after adding partners to repositories, launchpad bug report started.

Otherwise running fine, removed chromium, added firefox & flash, ... usual install goodies.

Jerry

---

### Post by nm_geo on 2012-02-14
Okay I got one using the non-pae mini.iso.  

It is rather a mess but has a clean non-pae kernel...20120209 mini.iso

Linux greg 3.2.0-16-generic #25-Ubuntu SMP Tue Feb 14 02:48:46 UTC 2012 i686 i686 i386 GNU/Linux

I wish I had not tired the install but had gone for command line.  The taskel on the 20120209 mini.iso did not have a Lubuntu choice or a Ubuntu with LXDE..  I did try to get lubuntu-desktop eventually for terminal but it said unavailable so I loaded up Ubuntu straight..Then kinda converted to Lubuntu .. Well I am using it right now anyway..

I have the mini.iso from today and I also have another partition just itchin' to be filled maybe tomorrow maybe tonight..  

i don;t think new users are gonna want to try this..
:P

---

### Post by jerrylamos on 2012-02-14
> **nm_geo said:**
> Okay I got one using the non-pae 20120209 mini.iso

Linux greg 3.2.0-16-generic #25-Ubuntu SMP Tue Feb 14 02:48:46 UTC 2012 i686 i686 i386 GNU/Linux

I wish I had not tired the install but had gone for command line.  The taskel on the 20120209 mini.iso did not have a Lubuntu choice or a Ubuntu with LXDE..  
Hmmm.  I tried the straight regular mini.iso install on a thinkpad without the pae flag.

During install it said it was fetching generic-pae.

After install /boot showed generic and no pae in sight.

And tasksel had lubuntu choice which is what I used.

Runs O.K. but I then in another partition installed the regular lubuntu daily build 20120214 as in post 158 above.

They both run.  A little extra getting the mini up to speed, agreed, not something a newbie would prefer.

Jerry

---

### Post by nm_geo on 2012-02-14
> **jerrylamos said:**
> Hmmm.  I tried the straight regular mini.iso install on a thinkpad without the pae flag.

During install it said it was fetching generic-pae.

After install /boot showed generic and no pae in sight.

And tasksel had lubuntu choice which is what I used.

Runs O.K. but I then in another partition installed the regular lubuntu daily build 20120214 as in posts above.

They both run.  A little extra getting the mini up to speed, agreed, not something a newbie would prefer.

Jerry 

kansasnoob is going to kill -9 us LOL..
We need to writing this stuff in the testing post. Care to join me..

---

### Post by zika on 2012-02-15
Non-pae is back to "daily"... :)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2012-02-15-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2012-02-15-precise/)

---

### Post by jerrylamos on 2012-02-15
> **nm_geo said:**
> kansasnoob is going to kill -9 us LOL..
We need to writing this stuff in the testing post. Care to join me..

Where's the testing post?

Jerry

---

