---
title: "New devices to use exFAT"
date: 2009-12-11
forum: The Cafe
---

### Post by Frak on 2009-12-11
[http://arstechnica.com/microsoft/news/2009/12/microsoft-licenses-out-exfat-file-system.ars?utm_source=rss&utm_medium=rss&utm_campaign=rss](http://arstechnica.com/microsoft/news/2009/12/microsoft-licenses-out-exfat-file-system.ars?utm_source=rss&utm_medium=rss&utm_campaign=rss)

tl;dr: New high capacity devices (Phones, Cameras, SDXC, SSDs) will very likely be formatted with exFAT. Linux can't write to exFAT, and can barely read it.

Solution: Volume Licensing - [http://www.microsoft.com/iplicensing/productDetail.aspx?productTitle=exFAT%20File%20System%20Licensing%20Program](http://www.microsoft.com/iplicensing/productDetail.aspx?productTitle=exFAT%20File%20System%20Licensing%20Program)
or treat it like all the other legally-grey implementations and host it on medibuntu.

---

### Post by Chronon on 2009-12-11
Reverse engineering for the purpose of interoperability seems to be protected in almost all localities.

---

### Post by SunnyRabbiera on 2009-12-11
Someone will crack it, as usual.

---

### Post by earthpigg on 2009-12-11
i am not concerned :D

---

### Post by Psumi on 2009-12-11
> **earthpigg said:**
> i am not concerned :D

Because you do not use such devices? :|

In the future, I might want to get a digital camera. But some jerk from launchpad or a linux distro may say, "If you cannot make/compile, or do this, this and that yourself, you do not belong in the linux world."

Which is a very annoying slap in the face I get a lot.

---

### Post by phrostbyte on 2009-12-11
[http://userweb.kernel.org/~hirofumi/exfat/exfat.tar.gz](http://userweb.kernel.org/~hirofumi/exfat/exfat.tar.gz)

That patch adds read only exFAT support to the Linux kernel. You can be sure that if exFAT ever gets popular, Linux will support it fully.

Regarding the legal threat.. that despite Microsoft's instance that they own this technology, they have no valid patent on the fundamental functionality of this FS yet. Even in the United States (where software patents are legal) it has yet to pass the USPTO. The USPTO is still accepting dispute claims from the public and could reject the patent application (perhaps based on prior art - Fat32). And should they get this patent, and if they attempt to enforce this patent against Linux users, they may trigger a countersuit from the OIN. And this is a non-issue in Europe where software patents are largely unenforceable.

And I won't get into the anti-trust implications (using their advantage as the Windows developer to leverage a new business). Anti-trust violation is not something Microsoft enjoys hearing, but they hear it a lot. :p

> i am not concerned 

And you shouldn't be. :)

---

### Post by earthpigg on 2009-12-11
> **Psumi said:**
> Because you do not use such devices? :|


in addition to what the poster above me said...

...United States and Japanese laws have zero affect on the operating system i choose to use. Ubuntu is based in the UK, Linux Mint in Ireland, Masonux (which could rapidly become Debian-based or maybe even something else, if the need arose) is based in my brain, Slackware based in some other dude's bedroom, Red Flag in Mainland China, etc etc.

Furthermore, history has shown time and time again that coders move faster and smarter than legislators. in the event of certain websites being blacklisted by US DNS servers, p2p file sharing will always be available to me.

I will always have access to an up-to-date GNU/Linux system regardless of any e-Fascism on the part of the US Government and it's sponsors in Redmond.

So, as I said, I am not concerned that there will be a time in the near/medium future that I am unable to find a digital camera that I can use.

---

### Post by Psumi on 2009-12-11
> **earthpigg said:**
> in addition to what the poster above me said...

...United States and Japanese laws have zero affect on the operating system i choose to use. Ubuntu is based in the UK, Linux Mint in Ireland, Red Flag in Mainland China, Masonux in my bedroom, etc etc.

Furthermore, history has shown time and time again that coders move faster and smarter than legislators. in the event of certain websites being blacklisted by US DNS servers, p2p file sharing will always be available to me.

I will always have access to an up-to-date GNU/Linux system regardless of any e-Fascism on the part of the US Government and it's sponsors in Redmond.

So, as I said, I am not concerned that there will be a time in the near/medium future that I am unable to find a digital camera that I can use.

Sounds like you are being rather... high and mighty on your seat there. That is not a good thing to be honest, we have feelings too.

---

### Post by earthpigg on 2009-12-11
> **Psumi said:**
> Sounds like you are being rather... high and mighty on your seat there. That is not a good thing to be honest, we have feelings too.

i think 'high and mighty' is a bit unfair.

i am merely acknowledging that the US Federal government has a lot less influence on what goes down on the internet than many people think.... and, since it's inception, GNU/Linux has been completely based around the internet for every aspect of it's development and distribution.

so, i am not concerned about exFAT.

somewhere out there is a person much smarter than me that is working hard at implementing full kernel-level support, and my hat is off to him. or her. or them.

i am confident in his/her/their success, and confident in the notion that no big bad evil empire will be able to stop the distribution of our kernel.

---

### Post by 3rdalbum on 2009-12-11
Everyone knows the advantages of exFAT over FAT; but what's the advantage over NTFS?

---

### Post by Psumi on 2009-12-11
> **3rdalbum said:**
> Everyone knows the advantages of exFAT over FAT; but what's the advantage over NTFS?

That it is PHAT?

---

### Post by Frak on 2009-12-11
> **3rdalbum said:**
> Everyone knows the advantages of exFAT over FAT; but what's the advantage over NTFS?
exFAT has less of an overhead than NTFS. It uses Bitmap allocation, so deletes and allocations are faster. exFAT tables are smaller than FAT tables, which are smaller than NTFS tables.

Though,

It has slower read speeds than NTFS, but faster write speeds than NTFS. This makes it good for realtime recording devices, but makes it bad for mechanical system drives. You can negotiate the benefit in SSDs.

---

### Post by earthpigg on 2009-12-11
> It has slower read speeds than NTFS, but faster write speeds than NTFS. This makes it good for realtime recording devices, but makes it bad for mechanical system drives. You can negotiate the benefit in SSDs.

ah, ive been wondering in the back of my head what places using Windows Ultra Mega Server 2050 infrastructure used for databases.

---

### Post by Frak on 2009-12-11
Reminds me, [http://www.tuxera.com/products/exfat-for-embedded-systems/](http://www.tuxera.com/products/exfat-for-embedded-systems/)

There are proprietary drivers already available for Linux.

---

### Post by SunnyRabbiera on 2009-12-11
> **Frak said:**
> Reminds me, [http://www.tuxera.com/products/exfat-for-embedded-systems/](http://www.tuxera.com/products/exfat-for-embedded-systems/)

There are proprietary drivers already available for Linux.

Well thats good, even proprietary drivers are welcome if they work.

---

### Post by RiceMonster on 2009-12-11
> **SunnyRabbiera said:**
> Well thats good, even proprietary drivers are welcome if they work.

Yup. The kernel devs may have issues with proprietary drivers, but as a someone who doesn't develop the Kernel, it's fine with me.

---

### Post by Dr. C on 2009-12-12
> **SunnyRabbiera said:**
> Well thats good, even proprietary drivers are welcome if they work.

Proprietary drivers will not be the answer here. It will be reversed engineered and released as FLOSS likely before any mass adoption of the format. There is already experimental read support. Furthermore will Microsoft take on the OIN in patent armageddon?

---

### Post by earthpigg on 2009-12-12
> Furthermore will Microsoft take on the OIN in patent armageddon?

no, just bully smaller corporations like TomTom into playing ball with them.

a private company that doesn't need to keep stockholders happy, that has enough money to make it seem worthwhile for Microsoft, and with an owner that both cares and has a spine, and who is suitable for OIN to back... is who we need MS to pick a fight with regarding this stuff.

would be nice, but i don't think that will happen.

---

### Post by 3rdalbum on 2009-12-12
> **earthpigg said:**
> no, just bully smaller corporations like TomTom into playing ball with them.

And then those smaller corporations like Tomtom will join the OIN :-)

---

### Post by Exodist on 2009-12-12
> **phrostbyte said:**
> [http://userweb.kernel.org/~hirofumi/exfat/exfat.tar.gz]("http://userweb.kernel.org/%7ehirofumi/exfat/exfat.tar.gz")

that patch adds read only exfat support to the linux kernel. You can be sure that if exfat ever gets popular, linux will support it fully.

Regarding the legal threat.. That despite microsoft's instance that they own this technology, they have no valid patent on the fundamental functionality of this fs yet. Even in the united states (where software patents are legal) it has yet to pass the uspto. The uspto is still accepting dispute claims from the public and could reject the patent application (perhaps based on prior art - fat32). And should they get this patent, and if they attempt to enforce this patent against linux users, they may trigger a countersuit from the oin. And this is a non-issue in europe where software patents are largely unenforceable.

And i won't get into the anti-trust implications (using their advantage as the windows developer to leverage a new business). Anti-trust violation is not something microsoft enjoys hearing, but they hear it a lot. :p



and you shouldn't be. :)
qft++

---

### Post by madhi19 on 2009-12-13
Why the hell are the industry even playing ball with that licensing scam when they could just use an open source file system instead. The industry could put together a legal consortium behind an open format and dare MS to try playing their usual extortion tactic!

---

### Post by Frak on 2009-12-13
> **madhi19 said:**
> Why the hell are the industry even playing ball with that licensing scam when they could just use an open source file system instead. The industry could put together a legal consortium behind an open format and dare MS to try playing their usual extortion tactic!
Because exFAT gets the job done for many of the industry leaders. They like exFAT. You could put an open source file system on those devices, but good luck if they work in the end.

Also, how is it a "licensing scam"?

---

