---
title: "EeePC reviewer recommends replacing Linux with WinXP"
date: 2008-08-07
forum: The Cafe
---

### Post by Sporkman on 2008-08-07
> The other difference between the models is that the less-expensive 1000H runs Windows XP, while the 1000 runs Linux, the free operating system that the original Eee PCs also used. It looks like Asus figured it had to keep the price of the 1000 below $700, and the best way to do that was to scratch the license fee to Microsoft Corp.

The Linux version comes loaded with software that does all the basics, like Web surfing, e-mail, Skype, word processing, but to extend its capabilities with new software, you'll need to mess with typing commands to the operating system. There's a Linux version of my favorite free strategy game, "Battle for Wesnoth," but I couldn't figure out how to install it.

The Linux PC also exhibited some sluggish behavior that I didn't see on the XP version. Both models are among the very first products to use Intel's new ant-sized Atom processor, specifically designed for this sort of application. Performance otherwise seemed snappy, but video editing and the latest 3-D games are probably outside the processor's competence.

Linux is appropriate for smaller Eee PCs that are mostly used for Web surfing, but for a 10-incher that's almost as capable as a full-sized laptop, I think Windows is the better choice. You can install XP on the 1000 if you hook it up to an external CD drive. Users even report installing the more demanding Windows Vista with good results.

[http://news.yahoo.com/s/ap/20080806/ap_on_hi_te/tec_tech_test_eee_pc_2](http://news.yahoo.com/s/ap/20080806/ap_on_hi_te/tec_tech_test_eee_pc_2)

---

### Post by init1 on 2008-08-07
Hrm, I experienced quite the opposite when I tried out the Windows and Linux versions. The Linux version seemed to be faster. Of course, they probably weren't the same model, so I guess it's not fair to compare them.

---

### Post by Newuser1111 on 2008-08-07
> you'll need to mess with typing commands to the operating system

Which "Linux" were they using?

---

### Post by awalsh on 2008-08-07
Are they comparing the 1000H to the 1000? If so that should invalidate any comments about the OS's as one is a conventional magnetic hard drive and the other is solid state so their is bound to be some performance differences surely.

My 1000 Linux is being delivered tomorrow morning and one of the first things I will do is install Ubuntu and compile my own kernel for it. The modified Xandros that comes with it does not sound like it does justification to the name "linux"

---

### Post by aysiu on 2008-08-07
> **Newuser1111 said:**
> Which "Linux" were they using?
It's a specialized version of Xandros that Asus preinstalls.

The observation is accurate. Installation of software in Ubuntu is easy, because Ubuntu has an extensive set of repositories and Add/Remove and Synaptic. Adding an extensive and reliable set of repositories to Xandros is a bit trickier.

---

### Post by init1 on 2008-08-07
> **aysiu said:**
> It's a specialized version of Xandros that Asus preinstalls.

The observation is accurate. Installation of software in Ubuntu is easy, because Ubuntu has an extensive set of repositories and Add/Remove and Synaptic. Adding an extensive and reliable set of repositories to Xandros is a bit trickier.
I though Xandros was Debian based. If it is, most people will never need anything other than the default

---

### Post by Dremora on 2008-08-07
He's clearly been bought and paid for if he's pushing Vista on such a wimpy system.

---

### Post by aysiu on 2008-08-07
> **init1 said:**
> I though Xandros was Debian based. If it is, most people will never need anything other than the default
It's Debian-based, but it's not 100% compatible with Debian repositories, and the only repositories that are enabled by default are the Eee PC ones, which are quite limited, so you necessarily have to manually edit the /etc/apt/sources.list. There's no System > Administration > Software Sources.

---

### Post by init1 on 2008-08-07
> **aysiu said:**
> It's Debian-based, but it's not 100% compatible with Debian repositories, and the only repositories that are enabled by default are the Eee PC ones, which are quite limited, so you necessarily have to manually edit the /etc/apt/sources.list. There's no System > Administration > Software Sources.
Ah OK. No problem for a Linux user, but most people won't want to mess with that.

---

### Post by Dremora on 2008-08-07
> **aysiu said:**
> It's Debian-based, but it's not 100% compatible with Debian repositories, and the only repositories that are enabled by default are the Eee PC ones, which are quite limited, so you necessarily have to manually edit the /etc/apt/sources.list. There's no System > Administration > Software Sources.

Speaking of which...could one convert Ubuntu into Debian? ;)

---

### Post by aysiu on 2008-08-07
> **init1 said:**
> Ah OK. No problem for a Linux user, but most people won't want to mess with that.
Yeah, if you want to scare off a Windows user, give them these instructions:
[http://wiki.eeeuser.com/addingxandrosrepos](http://wiki.eeeuser.com/addingxandrosrepos)

---

### Post by aysiu on 2008-08-07
> **Dremora said:**
> Speaking of which...could one convert Ubuntu into Debian? ;)
No. Ubuntu isn't fully compatible with Debian either, which I don't really understand. Maybe someone who understands .deb packages better can explain it.

---

### Post by Joeb454 on 2008-08-07
I often consider becoming a technology journalist. That way at least 1 of them would know what they're talking about

---

### Post by Dremora on 2008-08-07
> **aysiu said:**
> Yeah, if you want to scare off a Windows user, give them these instructions:
[http://wiki.eeeuser.com/addingxandrosrepos](http://wiki.eeeuser.com/addingxandrosrepos)

Anyone that kind of half knows what they're doing can get an Ubuntu system set up, and it doesn't really take a genius to set up APT repositories either.

But I agree that this would scare off many Windows users. :lolflag:

---

### Post by smartboyathome on 2008-08-07
[thread hijack]
Anyone here using the EeePC 900/901 and know if LVM works with it? Just wondering, as I am thinking of buying an EeePC soon and there is a meeting today at the local LUG on LVM (which allows you to combine HDDs among other things! :D). If so, I will most likely get it in a couple months.
[/thread hijack]

Anyway, that reviewer obviously was completely unaware that they were compairing 2 different models, as the 1000H comes with a normal HDD and the 1000 doesn't, among other things.

---

### Post by Dremora on 2008-08-07
> **aysiu said:**
> No. Ubuntu isn't fully compatible with Debian either, which I don't really understand. Maybe someone who understands .deb packages better can explain it.

I would think that by carving out all the stuff that obviously won't work and replacing your APT sources with Debian Unstable or something, Update Manager would go for it and maybe you might have a Debian system.

Of course I would rather just format my Ubuntu partition and go Debian directly, but I do love playing with stuff like this.

---

### Post by Methuselah on 2008-08-07
Funny thing is that if you look at reviews from actual users (like on amazon) you find many of them loving linux after a bit of apprehension.
I looked up a few customer reviews when I was buying one myself.

He might be talking about sluggishness in launching OpenOffice, this takes a few seconds.
Still, OOo is pretty heavy and a default windows install has the advantage of not including a productivity suite. </sarcasm>

---

### Post by aysiu on 2008-08-07
> **Methuselah said:**
> Funny thing is that if you look at reviews from actual users (like on amazon) you find many of them loving linux after a bit of apprehension.
I looked up a few customer reviews when I was buying one myself.
I noticed the same thing:
[I don&#8217;t know about &#8220;the desktop,&#8221; but Linux appears to be ready for the ultra-mobile PC](http://www.psychocats.net/ubuntucat/i-dont-know-about-the-desktop-but-linux-appears-to-be-ready-for-the-ultra-mobile-pc-2/)

---

### Post by Sealbhach on 2008-08-07
This recommendation by the reviewer does not take into consideration security, viruses, malware. 

I would not sleep easy recommending Windows to anyone.


.

---

### Post by aysiu on 2008-08-07
> **Sealbhach said:**
> This recommendation by the reviewer does not take into consideration security, viruses, malware. 

I would not sleep easy recommending Windows to anyone.


.
Well, unfortunately, the version of Xandros Asus packages with the Eee isn't much more securely constructed than XP is. It allows you to *sudo* without any password authentication... ever. And if you try to add password authentication, it won't boot up.

Granted, I don't think there are any threats out there that take advantage of this poor security implementation, but it still is essentially running as root all the time.

---

### Post by coolglobal on 2008-08-07
The operating system on the eeepc works fine.

Tell him he's dreaming! Just another slave to the system.

---

### Post by Methuselah on 2008-08-07
> **aysiu said:**
> I noticed the same thing:
[I don’t know about “the desktop,” but Linux appears to be ready for the ultra-mobile PC](http://www.psychocats.net/ubuntucat/i-dont-know-about-the-desktop-but-linux-appears-to-be-ready-for-the-ultra-mobile-pc-2/)

Hmm, nice collection of observations at that link.
I was pleasantly surprised myself.

---

### Post by Sporkman on 2008-08-07
> **Joeb454 said:**
> I often consider becoming a technology journalist. That way at least 1 of them would know what they're talking about

:lol: Indeed.

---

### Post by cardinals_fan on 2008-08-07
> **aysiu said:**
> Well, unfortunately, the version of Xandros Asus packages with the Eee isn't much more securely constructed than XP is. It allows you to *sudo* without any password authentication... ever. And if you try to add password authentication, it won't boot up.

Granted, I don't think there are any threats out there that take advantage of this poor security implementation, but it still is essentially running as root all the time.
Fail.

(Xandros, not you :))

---

### Post by Mr.Auer on 2008-08-08
Just my personal experiences with the Xandros on Eee pc 701..
1) When you enable Advanced mode (normal KDE desktop), the OS no longer asks for a login password...And many options in KDE settings dont work correctly.
2) It is not possible to add users, or change the default username that is ... "user". The name asked for in first boot is used only for the users "real name", not username.
3) sudo does not ask for password. It is not possible to enable sudo authentication - if you do, the OS will not boot - it uses passwordless sudo in boot scripts (so I read).
4) By default, there is portmap and samba open to the net. Samba is 2 yrs old version, and root-ownable by a known exploit, remotely. Great.
5) Iptables has been left out of the kernel compile. Thats right. You have no iptables. That is, if you dont get the kernel sources and recompile with iptables.
6) Asus repos are not signed, and contain just a few packages. To get any software, you need to add some community / user repos. And risk breakage at some point, as Xandros is not directly Debian compatible, being a fork..

Used it for a couple weeks before installing Ubuntu :) Used eee-Ubuntu, then applied all fixes and a custom kernel, and removed all unneeded packages (openoffice 100+megs, all cd-rom related stuff etc.). It feels very quick and responsive, even with the CPU scaled down a little. Would never dream of installing XP on it :p

---

### Post by Sycron on 2008-08-08
I've tried alot default Xandros, but is not for me... i dislike it for some reasons .. it is let's say a bit bloated, i can't use it as a full linux and has security holes, like aysiu says...

---

### Post by Brunellus on 2008-08-08
> **aysiu said:**
> It's Debian-based, but it's not 100% compatible with Debian repositories, and the only repositories that are enabled by default are the Eee PC ones, which are quite limited, so you necessarily have to manually edit the /etc/apt/sources.list. There's no System > Administration > Software Sources.
the eee user community has done a pretty good job of documenting "reliable" repos:  

[http://wiki.eeeuser.com/#software](http://wiki.eeeuser.com/#software)

That said, I told my dad to get XP on his eeepc 1000--he'll be dealing in a mostly Windows environment, and I'll be a very long way away from him.  He's running Ubuntu on his lappy now, and isn't too fussed with it. 

On my own eee, I run Asus's Xandros.  I haven't had too many problems--but then, I stick mostly to the defaults.  The only thing I've really added is LaTeX.  I may remap Capslock to ESC to make vim use a little easier.

---

### Post by Brunellus on 2008-08-08
> **coolglobal said:**
> The operating system on the eeepc works fine.

Tell him he's dreaming! Just another slave to the system.
There's a level of practicality that comes with software recommendations.  My dad's been running ubuntu for a while, but he opted for the XP eee pc.  We'll see how he likes things on XP again--then maybe he'll switch back.

---

### Post by init1 on 2008-08-08
> **Methuselah said:**
> 
He might be talking about sluggishness in launching OpenOffice, this takes a few seconds.

Yeah, takes a while on my computer too. I'm sure MS Office wouldn't be very fast either. 

> 
Still, OOo is pretty heavy and a default windows install has the advantage of not including a productivity suite. </sarcasm>
The Windows version of the EEEPC has StarOffice.

---

### Post by geogur on 2008-08-08
i left my eeepc with the default zandros in full desktop mode . i have the 701 the only thing i had to do was install 2g ram and this fixed any speed issues i had 512mb could not keep up .  PS. i thought ubuntu was debian based am i wrong ?

---

### Post by aysiu on 2008-08-08
> **geogur said:**
> i left my eeepc with the default zandros in full desktop mode . i have the 701 the only thing i had to do was install 2g ram and this fixed any speed issues i had 512mb could not keep up .  PS. i thought ubuntu was debian based am i wrong ?
With the default Xandros, don't you have to recompile the kernel to get it to recognize 2 GB of RAM?

Yes, Ubuntu is Debian-based. So is Xandros.

---

### Post by Twitch6000 on 2008-08-08
Isn't Xandros Also a Linux that made a deal with Microsoft?
If so that would make since to why its so **Limited**.

If I were to get a eeepc with Xandros I would just put Ubuntu or PClinuxOS on it and be done.Ofcourse for the normal user this is not so easy.

---

### Post by BettaSharma on 2008-08-08
Those who want Windows are probably better off just buying DELL VOSTRO 1000 (laptop) which sells for $399.

---

### Post by cardinals_fan on 2008-08-08
> **Twitch6000 said:**
> Isn't Xandros Also a Linux that made a deal with Microsoft?
If so that would make since to why its so **Limited**.
Yes, but Xandros is limited because it's targeted at naive users who enjoy running as root.  The deal with Microsoft has nothing to do with it.

---

### Post by Twitch6000 on 2008-08-08
> **cardinals_fan said:**
> Yes, but Xandros is limited because it's targeted at naive users who enjoy running as root.  The deal with Microsoft has nothing to do with it.

Oh ok I was just taking a guess.
Either way though I wouldn't use it lol.

---

### Post by smartboyathome on 2008-08-08
I'm going to get an Eee soon (as soon as a month or two, that is). I think I will install Arch on it with E17. :)

---

### Post by zmjjmz on 2008-08-08
I'm not getting an EeePC!
Especially after hearing all this crap going on.

EDIT: Unfortunately, in the majority of the reviews I've seen for similar products (in terms of price) like the gPC, gBook, Cloudbook, etc. the sentiment is "install XP and it's magical happy fairy land".
Everex must just suck *** at implementing their OS.
EDIT2: New censoring system I see.

---

### Post by cardinals_fan on 2008-08-08
> **zmjjmz said:**
> I'm not getting an EeePC!
Especially after hearing all this crap going on.

EDIT: Unfortunately, in the majority of the reviews I've seen for similar products (in terms of price) like the gPC, gBook, Cloudbook, etc. the sentiment is "install XP and it's magical happy fairy land".
Everex must just suck *** at implementing their OS.
EDIT2: New censoring system I see.
gOS was a poor choice, and Everex handled it exceptionally badly.

---

### Post by Brunellus on 2008-08-08
Instead of bashing in ignorance, why not try an eee pc?  

The default Xandros setup is actually quite sane--especially considering the initial concept of the eee 701 as a portable internet device with a few other things added.  If you're expecting an eeepc (of any type/size) to be your primary machine, you might need to think differently.  

I use my eeepc as a mobile PC--and am willing to live with a few compromises to keep my mobility.

---

### Post by Canis familiaris on 2008-08-08
> **Brunellus said:**
> Instead of bashing in ignorance, why not try an eee pc?  

The default Xandros setup is actually quite sane--especially considering the initial concept of the eee 701 as a portable internet device with a few other things added.  If you're expecting an eeepc (of any type/size) to be your primary machine, you might need to think differently.  

I use my eeepc as a mobile PC--and am willing to live with a few compromises to keep my mobility.

Nobody's bashing the eeePC. I think Xandros is being criticized rather.

---

### Post by mikjp on 2008-08-08
I've read only favourable reports by those who installed Mandriva on their EeePC. Should be fully compatible with EeePC out of the box.

Greetings,

mikko

---

### Post by zmjjmz on 2008-08-08
Wasn't there a rumor sometime ago that Xandros on the Eee was being replacified?

---

### Post by mrgnash on 2008-08-08
> The Linux version comes loaded with software that does all the basics, like Web surfing, e-mail, Skype, word processing, but to extend its capabilities with new software, you'll need to mess with typing commands to the operating system. There's a Linux version of my favorite free strategy game, "Battle for Wesnoth," but I couldn't figure out how to install it.

The man is clearly a simpleton.

---

### Post by JT9161 on 2008-08-09
> The other difference between the models is that the less-expensive 1000H runs Windows XP, while the 1000 runs Linux, the free operating system that the original Eee PCs also used. It looks like Asus figured it had to keep the price of the 1000 below $700, and the best way to do that was to scratch the license fee to Microsoft Corp.

The Linux version comes loaded with software that does all the basics, like Web surfing, e-mail, Skype, word processing, but to extend its capabilities with new software, you'll need to mess with typing commands to the operating system. There's a Linux version of my favorite free strategy game, "Battle for Wesnoth," but I couldn't figure out how to install it.

The Linux PC also exhibited some sluggish behavior that I didn't see on the XP version. Both models are among the very first products to use Intel's new ant-sized Atom processor, specifically designed for this sort of application. Performance otherwise seemed snappy, but video editing and the latest 3-D games are probably outside the processor's competence.

Linux is appropriate for smaller Eee PCs that are mostly used for Web surfing, but for a 10-incher that's almost as capable as a full-sized laptop, I think Windows is the better choice. You can install XP on the 1000 if you hook it up to an external CD drive. Users even report installing the more demanding Windows Vista with good results.

Those are some pretty bad reasons for not using the Linux version, I would be more worried about no password needed for sudo. Also Is it possible for the EEE to run a light distro like Damn Small or Puppy ? I think that would be perfect for UMPCs.

---

### Post by Mr.Auer on 2008-08-09
I love the machine (Eee 701 4 GB). Its just great. Ive been using it more than my other, fast, new, widescreen 22" boxes :) Actually its the first laptop Ive ever bought (because it came without Windows and was so small), have had just some old second hand one.

Only issue I had was Xandros, mostly the sudo / other security issues, and things done against the Common Unix Wisdom. I did get it to do everything (all prgs I need, compiled a few) in Advanced mode. But like Ubuntu better - and I stripped everything unnecessary out of buntu, and stopped all services I dont need. With the custom kernel its pretty fast imho, and runs everything including video, flash, music, flawlessly. With Compiz on. Dont think it needs a lightweighter distro than that :) I did get rid of OpenOffice, since it takes over 100 megs of space.

Have a few SD cards of 4-8 GB also, to take stuff with me, like videos for a trip, or music and books.

---

### Post by VMan on 2008-08-18
I got the 1000H.  I couldn't afford the extra $150 for the linux (1000) version.  It costs more simply because it comes with two 1.8 inch solid state drives instead of the single SATA HD that comes with the 1000H.  I immediately pulled the stock HD out and put in a 160G that I had laying around.  I re-installed Windows XP from the recovery DVD.  I then took the remaining 80G and installed Ubuntu Hardy.  I couldn't be more happy with this itty bitty laptop.  I'm using it right now to post this.  I only boot into XP to use two pieces of external hardware that won't work in any linux and when I want to use the free WiFi at Books-A-Million (their WiFi login wont work with linux).  Literally everything else is done with Ubuntu.

---

