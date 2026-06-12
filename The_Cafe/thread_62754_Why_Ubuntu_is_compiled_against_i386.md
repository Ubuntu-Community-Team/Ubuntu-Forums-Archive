---
title: "Why Ubuntu is compiled against i386?"
date: 2005-09-05
forum: The Cafe
---

### Post by Teo on 2005-09-05
Hi
Why or rather what for Ubuntu is compiled against i386? IMVHO it should be compiled against i686.
I know there are kernel images compiled against i686 and k7 but so what, if apps are still compiled against i386 :/
What's more! It's almost impossible to work with Ubuntu on machines such as 486, P100 etc... even K6-2 or PIII sometimes are to slow to handle Ubuntu and Gnome (please remember here Ubuntu's philosophy).
Ubuntu is a specific distro with a specific philosophy and trying making Ubuntu to run on a P200 just to run it is beside the purpose.

Please tell me why Ubuntu and apps for Ubuntu isn't compiled against i686 by default? (K7's can handle them too) - thx to that Ubuntu SHELL BE faster.

ps. IMHO compiling against i686 should be a standard for all apps in next (6.0x) version of Ubuntu - like in PLD distro.
ps2. I'm a AMD AthlonXP's owner - not any Intel junkie :)

---

### Post by poofyhairguy on 2005-09-05
[QUOTE=Teo]
What's more! It's almost impossible to work with Ubuntu on machines such as 486, P100 etc... even K6-2 or PIII sometimes are to slow to handle Ubuntu and Gnome (please remember here Ubuntu's philosophy).[/QUOTE]

Not for use as non graphical server. Those do fine for that. Ubuntu has a server install option, so that about half the reason things are compiled for 386.

> 
Ubuntu is a specific distro with a specific philosophy and trying making Ubuntu to run on a P200 just to run it is beside the purpose.

Unless the purpose is a good server with the same OS as your desktop.

> 
Please tell me why Ubuntu and apps for Ubuntu isn't compiled against i686 by default? 


Here is the other half of your answer:

> 
 Ubuntu packages for the i386 architecture are compiled using the i486 instruction set (-march=i486), with instruction choices based on the Pentium 4 processor (-mcpu=pentium4). This combination provides benefits for modern processors without sacrificing compatibility with older and embedded devices.

[http://www.ubuntulinux.org/support/documentation/faq/optimised-packages](http://www.ubuntulinux.org/support/documentation/faq/optimised-packages)

---

### Post by Teo on 2005-09-05
[QUOTE=poofyhairguy]Not for use as non graphical server. Those do fine for that. Ubuntu has a server install option, so that about half the reason things are compiled for 386.
Unless the purpose is a good server with the same OS as your desktop.[/quote]
OK I can't say Ubuntu isn't a distro for a server but I CAN say Ubuntu is a bad choice when installing as a server on a 486 or P100 machine (kernel 2.6 is too heavy).
There are much better (and lighter) distros made for this purpose, so someone who want to install a server system on a P100 like machine WON'T choose Ubuntu.

---

### Post by drizek on 2005-09-05
then why not have the important things that arent going to be used on a server or even a lowend desktop complied for i686?

KDE, OOo and gnome are the three that would be most usefull.

Edit: reread your post. does that mean there is no performance hit at all?

---

### Post by poofyhairguy on 2005-09-05
[QUOTE=Teo]
There are much better (and lighter) distros made for this purpose, so someone who want to install a server system on a P100 like machine WON'T choose Ubuntu.[/QUOTE]

Maybe. Maybe the person has a lot of experiance with Ubuntu, uses it on the desktop and then uses it to run a server. There is something to be said for not having to relearn things. There are people like that on these very forums.

Ubuntu isn't that bad of server OS. Its based on Debian- THE server distro- but is has newer software in many cases than Sarge.

2.6 might be kinda heavy, but it can still do the job.

---

### Post by Brunellus on 2005-09-05
[QUOTE=Teo]OK I can't say Ubuntu isn't a distro for a server but I CAN say Ubuntu is a bad choice when installing as a server on a 486 or P100 machine (kernel 2.6 is too heavy).
There are much better (and lighter) distros made for this purpose, so someone who want to install a server system on a P100 like machine WON'T choose Ubuntu.[/QUOTE]
 big effin' deal.  Why should we care what distribution/kernel/whatever someone chooses to run on his cobbled-together server?

I know that sound arrogant, but seriously, folks.  If there are better tools out there for your intended job, well, USE 'em.  Ubuntu is a good tool for the desktop, for most people.

---

### Post by Teo on 2005-09-05
[QUOTE=poofyhairguy]Maybe. Maybe the person has a lot of experiance with Ubuntu, uses it on the desktop and then uses it to run a server. There is something to be said for not having to relearn things. There are people like that on these very forums.[/QUOTE]
YES there are ppl who use Ubuntu as a server system but how many of them use a 486 or P100 like machine to do such a job?
I think those machines are at least i686 compatible machines.

Poll is needed to solve this issue - It's a good thing and I won't say a thing if community want i386 than i686 :).

---

### Post by bored2k on 2005-09-05
[QUOTE=Teo]YES there are ppl who use Ubuntu as a server system but how many of them use a 486 or P100 like machine to do such a job?
I think most of those machines (if not all) are at least i686 compatible machines.

Poll is needed to solve this issue - It's a good thing and I won't say a thing if community want i386 than i686. :)[/QUOTE]
 If you really want someone to take notice of your demands, join the mailing list, IRC and wherever more the devs get together. Discussing it here is not really useful :?.

---

### Post by Teo on 2005-09-05
[QUOTE=bored2k]If you really want someone to take notice of your demands, join the mailing list, IRC and wherever more the devs get together. Discussing it here is not really useful :?.[/QUOTE]
THX for a good advice :)

Posting it in a forum's devel section is a good idea?

---

### Post by poofyhairguy on 2005-09-05
[QUOTE=Teo]
Poll is needed to solve this issue - It's a good thing and I won't say a thing if community want i386 than i686 :).[/QUOTE]

In the end...this just may be one of those "Mark decisions." Like the names or the fact that Hoary had that weird nautilus. Since Mark pays, he calls a few shots every now and then.

You might want to see if you can get him on board....mailing lists as bored said.

---

### Post by Takis on 2005-09-06
My understanding is that i386 CPU instructions are understood by everything since the, well, 386. That includes all AMD chips. This way when you install Ubuntu on an x86 you can be guaranteed it will work with the CPU - then, later, you can switch the kernel to the version that corresponds with your particular class of CPU to gain performance hits.

It's kind of like asking why does the installer look so hideous - because it pretty much guarantees functionality on all systems. I can't say I've run across a graphics card recently that couldn't draw 640x480 in 4 colours.

---

### Post by Teo on 2005-09-06
[QUOTE=Takis]My understanding is that i386 CPU instructions are understood by everything since the, well, 386. That includes all AMD chips. This way when you install Ubuntu on an x86 you can be guaranteed it will work with the CPU - then, later, you can switch the kernel to the version that corresponds with your particular class of CPU to gain performance hits.[/QUOTE]
Chips that won't support i686 instructions are to slow to handle Ubuntu (even as a server without GUI) - so I really can't see a reason why Ubuntu is compiled against i386 :/
Besides how many ppl would like to run Ubuntu as a server on a AMD K5, K6 or P200MMX like machines - could be 1%? Is it worth?
IMHO compiling Ubuntu against i386 and installing Ubuntu on a system that won't support i686 instructions is a mismanagement.

Yes there are linux-images compiled for i686 and k7 - so what when apps in repos are still compiled against i386 :mad:

i686 compatible chips are:
K6-2 and newer
PentiumPro, PentiumII and newer

PLEASE tell me a good reason why to support 386, 486, Pentium, PentiumMMX, K5 and K6 - chips that even can't handle Ubuntu?
Is it just for support, to say: "yes we support all x86 chips"?
Is it just for this few percents who still owns P100 and K5's, those who should chose other distro?

ps. When I say "compiling Ubuntu against i686" I'm talkin' 'bout compiling Ubuntu Linux and all software in repos.
ps2. On a i686-compiled system you can still run i386-compiled software - if needed.

Edited:
> It's kind of like asking why does the installer look so hideous - because it pretty much guarantees functionality on all systems. I can't say I've run across a graphics card recently that couldn't draw 640x480 in 4 colours.
Honestly, I don't care 'bout CLI installer and I like it as it is - installer is simple and fast, as it should be :) But pls don't mix two different things together - it's not the same case.

---

### Post by UbuWu on 2005-09-06
[QUOTE=Teo]
PLEASE tell me a good reason why to support 386, 486, Pentium, PentiumMMX, K5 and K6 - chips that even can't handle Ubuntu?
Is it just for support, to say: "yes we support all x86 chips"?
Is it just for this few percents who still owns P100 and K5's, those who should chose other distro?

ps. When I say "compiling Ubuntu against i686" I'm talkin' 'bout compiling Ubuntu Linux and all software in repos.
ps2. On a i686-compiled system you can still run i386-compiled software - if needed.
[/QUOTE]

Like already said in the 2nd post in this thread:
> All x86 Ubuntu packages are actually compiled tuned for pentium4
systems. The only thing that's not enabled is the small number of
post-486 specific instructions (e.g. cmov) or extensions (e.g. SSE)
and they aren't actually useful for the overwhelming majority of code.
When they are useful (e.g. in media players, etc.), these instructions
or extensions are usually detected and used at run time.

See [here](http://www.ubuntuforums.org/showthread.php?t=13753) for more info...

---

### Post by BoyOfDestiny on 2005-09-06
Ah glad someone brought this up... What I would like to know is if there is a i486 (I think that would be a nice compromise assuming it exists and makes a difference). 

I haven't used a 386 since I was 9. (off topic: Fortunately I can run DOSBox to play willy beamish etc and other games I played on my 386...) 

Granted 486 is old as well, but I found it somewhat decent back in the day (had a 486dx2 66 mhz, and then a 486dx4 before I went to a pentium 120...the improvemnt seemed minimal since I had win95 on it...)

Conclusion: Who on this earth is using a 386 for either a server or desktop... and are they installing ubuntu on them.

EDIT: Nevermind... After checking the link above...

- Ubuntu packages are compiled using the i486 instruction set (not i386),
choosing between equivalent instruction sequences based on the choice
which should perform best on Pentium 4 CPUs (-march=i486 -mcpu=pentium4).

---

### Post by supernaut on 2005-09-07
Compiling for i686 is a bad idea, as AMD K6 and K6-2 processors use the 586 instruction set, and many of these processors are perfectly capable of running Ubuntu, albeit a little slowly (I say this from personal experience). Perhaps compiling for i586 is a good compromise, as I doubt anyone is going to really bother with Ubuntu on a 486 or lower (and if they do, they're mad). Even then though, how much of a performance advantage do this optimisations offer, realistically? I'm not doubting there is any, just wondering if it is significant.

---

### Post by Teo on 2005-09-07
[QUOTE=UbuWu]Like already said in the 2nd post in this thread: See [here](http://www.ubuntuforums.org/showthread.php?t=13753) for more info...[/QUOTE]
THX for a link, it explains a lot.

Edited:
> 
Like already said in the 2nd post in this thread:
[QUOTE]All x86 Ubuntu packages are actually compiled tuned for pentium4
systems. The only thing that's not enabled is the small number of
post-486 specific instructions (e.g. cmov) or extensions (e.g. SSE)
and they aren't actually useful for the overwhelming majority of code.
When they are useful (e.g. in media players, etc.), these instructions
or extensions are usually detected and used at run time.[/QUOTE]
BTW AMD users and P4 instructions set: [link](http://ubuntuforums.org/showpost.php?p=131556&postcount=6)

---

### Post by npaladin2000 on 2005-09-07
[QUOTE=supernaut]Compiling for i686 is a bad idea, as AMD K6 and K6-2 processors use the 586 instruction set, and many of these processors are perfectly capable of running Ubuntu, albeit a little slowly (I say this from personal experience). Perhaps compiling for i586 is a good compromise, as I doubt anyone is going to really bother with Ubuntu on a 486 or lower (and if they do, they're mad). Even then though, how much of a performance advantage do this optimisations offer, realistically? I'm not doubting there is any, just wondering if it is significant.[/QUOTE]

That's why I advocated compiling for i586 earlier in the thread.  Mandrake/Mandriva has done it from the beginning.  I WOULD like to see a performance comparison on similar hardware, assuming someone had the facilities to do so (I actually do, but I'm not sure I have the time to compile Ubuntu entirely from source....although I suppose I could do it on my old Athlon overnight or something.  And maybe in a VM on my P4 server just to look at the difference on both chips.

---

### Post by poofyhairguy on 2005-09-07
[QUOTE=supernaut]Compiling for i686 is a bad idea, as AMD K6 and K6-2 processors use the 586 instruction set, and many of these processors are perfectly capable of running Ubuntu, albeit a little slowly (I say this from personal experience). Perhaps compiling for i586 is a good compromise, as I doubt anyone is going to really bother with Ubuntu on a 486 or lower (and if they do, they're mad). Even then though, how much of a performance advantage do this optimisations offer, realistically? I'm not doubting there is any, just wondering if it is significant.[/QUOTE]

On the Debian mailing lists, I have seen evidence that for non 586 procs, compiling for 486 is faster than compiling for 586.

---

### Post by Teo on 2005-09-07
[QUOTE=poofyhairguy]On the Debian mailing lists, I have seen evidence that for non 586 procs, compiling for 486 is faster than compiling for 586.[/QUOTE]
On AthlonXP and Duron chips Pentium4 instructions set won't work and in this situation AMD chips will use only 486 instructions (according to this: [link](http://ubuntuforums.org/showpost.php?p=131556&postcount=6)), so for AMD Duron/AthlonXP users there are two ways:
1. buy Pentium4
or
2. buy AMD64

---

### Post by madjo on 2005-09-07
[QUOTE=Teo]On AthlonXP and Duron chips Pentium4 instructions set won't work and in this situation AMD chips will use only 486 instructions (according to this: [link](http://ubuntuforums.org/showpost.php?p=131556&postcount=6)), so for AMD Duron/AthlonXP users there are two ways:
1. buy Pentium4
or
2. buy AMD64[/QUOTE]
 My AMD xp2600+ works fine under the current Ubuntu (5.04).. and I really see no need in this i386 thing being discarded... I don't think the speed increase all that much greater...

And NO! I will *not* change to AMD64, and most certainly not to Intel, just because an Intel user wants his computer to go just a little bit faster, while making Ubuntu less compatible with other brands...
if you so desperately need that increase in speed, recompile the kernel yourself...

---

### Post by poofyhairguy on 2005-09-07
[QUOTE=madjo]
if you so desperately need that increase in speed, recompile the kernel yourself...[/QUOTE]

There are already custom compiled kernels in the repo.

What is much more likely than Ubuntu changing gears is someone forking Ubuntu to make a high performance version. Like this:

[http://www.opensuse.org/index.php/SUPER](http://www.opensuse.org/index.php/SUPER)

---

### Post by Teo on 2005-09-07
[QUOTE=madjo]And NO! I will *not* change to AMD64, and most certainly not to Intel, just because an Intel user wants his computer to go just a little bit faster, while making Ubuntu less compatible with other brands...
[/QUOTE]
I'm a AMD AthlonXP (Thorton) user :grin:

---

### Post by jdong on 2005-09-07
[QUOTE=npaladin2000]That's why I advocated compiling for i586 earlier in the thread.  Mandrake/Mandriva has done it from the beginning.  I WOULD like to see a performance comparison on similar hardware, assuming someone had the facilities to do so (I actually do, but I'm not sure I have the time to compile Ubuntu entirely from source....although I suppose I could do it on my old Athlon overnight or something.  And maybe in a VM on my P4 server just to look at the difference on both chips.[/QUOTE]

1) Compiling with i586 results in *SLOWER* code than 486 on non-586 processors (i.e. Pentium 4's, Athlons, etc etc etc)

2) Optimizing across the board is a terrible idea period. There are numerous packages (Python+OpenMosix especially) that behave erratically under optimization, and I've gotten some of my scientific simulations to spit back incorrect results on -O2! WINE also breaks with anything greater than -O. -march/-mcpu anything will cause breakage.

3) Not all programs benefit from optimization. Multimedia players and IMLib (image resizer) benefit greatly from SSE's, but these instruction sets cause hell with other floating point operations. Some stuff, like the GNOME desktop environment or Firefox/Mozilla, benefit little from optimization but occaisionally behave really strangely with higher optimizations.

Optimizations are enabled on a package-by-package basis -- that's the correct way to do it.

---

