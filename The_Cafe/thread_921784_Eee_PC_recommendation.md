---
title: "Eee PC recommendation?"
date: 2008-09-16
forum: The Cafe
---

### Post by DaVince21 on 2008-09-16
As of today I have an Eee PC, but I'd like to install XUbuntu on it because I'm used to that system and am not satisfied with the custom Xandros' simplicity and amount of software. However, there seems to be a custom XUbuntu especially for the Eee PC (EeeXUbuntu), but it's based on 7.10. There's also the current XUbuntu, which I use on my big lappy, and then there should be a new XUbuntu in a month or so, right?

So my question is this: what should I install? Which one works the best?

EDIT: While I'm at it, what's the best way to install from an SD card (or, if easier, USB key)? Don't have an external DVD-ROM drive.

---

### Post by in-dust-rial on 2008-09-16
hey,
without any real eee experience, i read on a german eee wiki, that there are some applications adding to ubuntu for next release, which should help to soupport netbooks.

just a hint, maybe its a myth... 

good luck makeing your choice

p.s.: try to search around, and there is tons of easy accessable information.
(also for the installation from sticks)

---

### Post by DaVince21 on 2008-09-16
Yeah, I heard about better notebook support too, but how much of it is relevant to the Eee? Also, I'm afraid I'll only find information that's too old for its own good, so some practical information from experienced users might help more. Unless you have some useful, up to date links?

---

### Post by in-dust-rial on 2008-09-16
well i guess the specs and version of your EEE are then an important part to the answer.
i amy translate or abstract some german forum posts, but only if i know your version of eee.
good luck

---

### Post by DaVince21 on 2008-09-16
Of course... I could just check out the hardware and see how well they're supported by Ubuntu/XUbuntu. >_<

About my Eee's version, it's an Eee PC 4G.

---

### Post by DaVince21 on 2008-09-16
After finding [https://wiki.ubuntu.com/MeetingLogs/openweekhardy/EeePC](https://wiki.ubuntu.com/MeetingLogs/openweekhardy/EeePC) I've decided I'll wait till the next version of XUbuntu. Thanks in-dust-rial for suggesting I look around myself a bit more. Didn't know there was so much information on it already! :)

---

### Post by in-dust-rial on 2008-09-16
german user forum reports that installation like described here:

[http://www.ubuntu-eee.com/index.php5?title=User_Guides]("http://www.ubuntu-eee.com/index.php5?title=User_Guides")
works. and problems can be solved.
issues are: long boot time and the huge kernel.
but you may get a smaller kernel out there and the eeeubuntu is also promising to offer smaler kernels soon.
example for a kernel is here: [http://array.org/ubuntu/]("http://array.org/ubuntu/")
(ppl claim to be satisfied (50 seconds boottime))

i cant validate if this is something completely different, but its official:
[http://www.canonical.com/node/72]("http://www.canonical.com/node/72")
(but seems tobe directed to intel-atom)

something else...not ready?:
[http://www.eeepclinuxos.com/]("http://www.eeepclinuxos.com/")
some ppl like this german project:
[http://fluxflux.net/fluxflux-eee/index-en.html]("http://fluxflux.net/fluxflux-eee/index-en.html")
(page eng.)
no infos on this:
[http://murga-linux.com/puppy/viewtopic.php?search_id=1743416936&t=25896]("http://murga-linux.com/puppy/viewtopic.php?search_id=1743416936&t=25896")


mainly xandros is referred to be the stable solution.


the above information is a rapid fly-through some german forum stuff.
good luck

---

### Post by in-dust-rial on 2008-09-16
=) oh nice you found some stuff...
i still recommend at least the official link i proposed!

yeah,
my impression is, wait for a overwhelming xandros killer =)

hf

---

### Post by DaVince21 on 2008-09-16
Ah, thanks a lot! This is really going to help my research into finding the best solution. :) My main concerns right now are hardware compatibility, power management and speed/optimizations (especially since stuff like Xandros's heavier apps like OOo seem optimized).

Btw, I can read *some* German, so that shouldn't become much of a problem. :)

Edit: Ooh, that customized kernel sounds awesome.

---

### Post by RedPandaFox on 2008-09-16
> **DaVince21 said:**
> Ah, thanks a lot! This is really going to help my research into finding the best solution. :) My main concerns right now are hardware compatibility, power management and speed/optimizations (especially since stuff like Xandros's heavier apps like OOo seem optimized).

Btw, I can read *some* German, so that shouldn't become much of a problem. :)

Edit: Ooh, that customized kernel sounds awesome.

EEEPCLinuxOS is good, Iv tried pretty much all the EEE Custom distros out there, I have about 20 CDs with EEE distros on them, Wasn't overly impressed with EEEXubuntu thow

---

### Post by DaVince21 on 2008-09-17
I don't think I'd want to install EeeXUbuntu now, one of the reasons being it's another seperate branch and I don't know how successful upgrading to 8.04/8.10 from there would be. Judging by the votes and articles I've read so far it looks like I'll be "risking" installing the current XUbuntu after all.

RedPandaFox: I'm kind of attached to Ubuntu... Will give regular PCLinuxOS a try on my desktop just to see if I'll like it more, later. :)

---

### Post by piccoloprincipe on 2008-09-17
> **DaVince21 said:**
> I don't think I'd want to install EeeXUbuntu now, one of the reasons being it's another seperate branch and I don't know how successful upgrading to 8.04/8.10 from there would be.

I have an eeeXubuntu on a Eeepc 700. It's working pretty fine but it's still the 7.10 release (newers don't exist yet).
Today I put Xubuntu Hardy (8.04) live cd on usb stick and run it. Result was two proprietary drivers for wireless loaded, and no wireless working.
So I put Xubuntu Ibex alpha (wannabe 8.10) and run it. Result was one proprietary driver loaded, and no wireless working.
Since typing ten commands to recompile drivers every time I upgrade the kernel makes me feel stupid, I will keep eeeXubuntu until out-of-the-box wireless will be shipped with (X|K)Ubuntu; if I wanted to compile drivers I would have installed a Gentoo...

---

### Post by bingoUV on 2008-09-17
I use eeebuntu standard 1.0(not eeeXubuntu) and all hardware is supported out of the box (not tested wireless LAN).

For performance reasons, I uninstalled gnome and installed openbox. But gnome also runs accpetably fast on the eeepc 701 4GB.

---

### Post by DaVince21 on 2008-09-18
Installed XUbuntu 8.04, and indeed, no wireless. Found an article which has a repository for specially compiled eee kernels, but that kernel won't activate wireless either (as it should, according to the page: [http://www.array.org/ubuntu/index.html](http://www.array.org/ubuntu/index.html)). Audio goes to max volume without mixers working, cam won't be detected...

This was exactly what I was afraid of: a ton of hardware not being detected. :( I'll see what happens when the big upgrade comes, and maybe reinstall at that point if necessary. At least my eeePC is more usable than with the default Xandros install now...

EDIT: nevermind about the wireless. This hack:
[http://www.array.org/ubuntu/hacks.html?id=5&device=701&dist=hardy](http://www.array.org/ubuntu/hacks.html?id=5&device=701&dist=hardy)
actually not only enabled the Fn+F2 key, but also added the wireless stuff to the network manager! Phew! :D

---

### Post by markp1989 on 2008-09-18
what i done on both me eees, is start from CLI, 

then add openbox , or another light wm of your choice
and the array kernel [http://www.array.org/ubuntu/](http://www.array.org/ubuntu/) which gets most hardware working 
installed wicd network manager, on nm-applet, which ever one you prefer 
installed fbpanel  or another panel of your choice 

set openbox to run fbpanel and wicd on log in 

gives you a minimal system. then just add the programs that you need.

all im looking for now is a light battery applet.

---

### Post by smartboyathome on 2008-09-18
Anyone try any of [these SSD drives]("http://www.mydigitaldiscount.com/CategoryProductList.jsp?cat=Browse+By+Brand%3AMyDigitalSSD:MyDigitalSSD+PCI+Express+PCI-e+SSDs") for the EeePC? If so, would you recommend them? I'm now thinking of getting the 32GB MLC SSD from them when I buy my EeePC.

---

### Post by t0p on 2008-09-18
Some relevant links:

[www.eeeuser.com/]("http://www.eeeuser.com/") - site has a very good wiki for all eeepc issues.  And there's an excellent user forum.

[How to install eeebuntu]("http://www.eeebuntu.org/forum/viewtopic.php?t=133").

---

