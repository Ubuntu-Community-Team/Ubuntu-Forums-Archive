---
title: "The Perfect web server OS?"
date: 2009-08-31
forum: Server Platforms
---

### Post by ferreter007 on 2009-08-31
Hi all. 

I'm having a little problem deciding what OS I should use for my web server. 

A little background;

I procured a HP ML350 G3 server (Dual Xeon processors, RAID etc) from an old company which is current running Windows 2000 server (eurgh) and I have decided not to use it until I change the OS. 

However, finding the perfect OS is much harder than I thought it was going to be...

I have decided against Windows as I'm a solid linux user (used fedora, open suse, scientific linux, debian, ubuntu, kubuntu, pclinuxos and have currently settled on linux mint) but which distro? Another option I hadn't considered was FreeBSD.

I'm looking for something that will run quickly under heavy loads and preferably will work on the server however it needs upmost security and user friendlyness. Want to make a LAMP server with AJAX and Joomla CMS ideally but I'm open to suggestions.

A long story short would you all give your opinions on what OS to use (I know it's a bit biased asking in these forums however I know from experience that this community is top quality)  and why. I will be very grateful.

Thanks a lot in advance!

---

### Post by hessiess on 2009-08-31
It dousen't matter and is mostly down to personal peferance, Most Linux distros are basically exactly the same under the hood. I personally like Arch, as it is easy to configure the way I want it.

Ubuntu and fedora/REL (fedora is the dev version of REL) pritymuch just work out of the box so long as you can live with the default config, though customising can be more difficult.

---

### Post by Simian Man on 2009-08-31
CentOS (the free version of RHEL) would definitely be my choice, but if you are more used to Debian than that or Ubuntu would work too.  Don't use Fedora, it moves too fast for a server (unless you want to update it a fair amount).

---

### Post by Bachstelze on 2009-08-31
> **ferreter007 said:**
>  it needs upmost security and user friendlyness.

Competing goals. It's like having your cake and eat it too. ;)

If you want security: OpenBSD
If you want performance: FreeBSD
If you want user-friendliness: Ubuntu, OpenSuse or Fedora

Anything else is basically a balance between the three.

---

### Post by Vegan on 2009-08-31
> **HymnToLife said:**
> Competing goals. It's like having your cake and eat it too. ;)

If you want security: OpenBSD
If you want performance: FreeBSD
If you want user-friendliness: Ubuntu, OpenSuse or Fedora

Anything else is basically a balance between the three.

I have used FreeBSD for eons until I noticed Ubuntu was becoming popular. I finally came aboard only when it reached 8.04 LTS but I have been using updates as I needed some features that 8.04 was unable to achieve.

I am also using a more recent kernel but that is only because I am a developer.

I used FreeBSD for so a very long time (decades) so I am very familiar with it. Ubuntu was not a big problem when I switched. This is mainly due to the strong backwards compatibility that is present.

Readers here should be aware BSD is the original home for Unix System V which became a basis for fighting for years which discouraged adoption outside academia. FreeBSD is the freeware version of System V.

All open source came from this initiative back in the 1970s. Earlier open source is not so user friendly as machines were not very standardized as they are now.

---

### Post by ferreter007 on 2009-09-02
Excellent guys! Just the insight I was needing. I know a lot of linux is down to personal choice which is why I've been swapping around so much. 

I think, judging from this, I'm going to start with Debian as it will be a quick step from Mint. If it doesn't go well I think I might try Cent OS as RHEL is recommended for the ML350 G3 as a commercial application. I'll just have to try and make it as secure as possible and run a hardware firewall (possibly with IpCop but that's an entirely different thread!) just so I can have complete control over it. 

If I notice any decrease in performance then FreeBSD it is :-). 

Thanks a lot for all your help and if you have any other recommendations for software, leave them here please! I'm going to keep monitoring it.

---

