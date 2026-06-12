---
title: "Why do people use FreeBSD?"
date: 2008-04-06
forum: The Cafe
---

### Post by tcpip4lyfe on 2008-04-06
Why do people use FreeBSD?  What is its' most common application?  I woke up and I realized I know nothing about it.

---

### Post by LaRoza on 2008-04-06
> **tcpip4lyfe said:**
> Why do people use FreeBSD?  What is its' most common application?  I woke up and I realized I know nothing about it.

Look here: [http://www.freebsd.org/](http://www.freebsd.org/)

---

### Post by Polygon on 2008-04-06
ive heard that while it is very secure like linux, but it places a special emphasis of stability, aka servers.

---

### Post by wersdaluv on 2008-04-06
> **tcpip4lyfe said:**
> Why do people use FreeBSD?  What is its' most common application?  I woke up and I realized I know nothing about it.

Good question. In what way is BSD better than Linux? Why use it if there's Linux? :)

---

### Post by Tomatz on 2008-04-06
Just install it in a vm and see for yourself ;)

---

### Post by chucky chuckaluck on 2008-04-06
> **wersdaluv said:**
> Good question. In what way is BSD better than Linux? Why use it if there's Linux? :)

there was a great article explaining the differences called "bsd for linux users", but the site seems to down, or dead. essentially, bsd seems to be more deliberate in its development, claiming that it tests the intergration of all its parts far longer and more critically than linux does (the more hostile bsd users tend to view linux as more of a series of hacks). it's at least as different (and probably more so) from ubuntu as another distro would be.

---

### Post by SunnyRabbiera on 2008-04-06
> **Polygon said:**
> ive heard that while it is very secure like linux, but it places a special emphasis of stability, aka servers.

Actually BSD is more secure then Linux, but for the desktop its not as good as Linux.
BSD is used for servers mainly, for servers it rocks.

---

### Post by odiseo77 on 2008-04-06
I have FreeBSD installed on my machine and although I enjoy setting it up, I haven't found one reason to use it as a desktop on a regular basis, so I keep it mainly for experimental purposes (eg. to know how it works, etc). I simply prefer Linux (I'm mainly a desktop user, not a server admin).

---

### Post by aktiwers on 2008-04-06
> **SunnyRabbiera said:**
> Actually BSD is more secure then Linux, but for the desktop its not as good as Linux.
BSD is used for servers mainly, for servers it rocks.

Heh It's not many years ago a Windows user would tell me the exact same thing about Linux compared to Windows.

---

### Post by Tomatz on 2008-04-06
More to the point...

...why use GNU-hurd???

:lolflag:

---

### Post by madjr on 2008-04-06
> **tcpip4lyfe said:**
> Why do people use FreeBSD?  What is its' most common application?  I woke up and I realized I know nothing about it.

here is a great comparison

bsd vs linux vs windows 2000

[http://www.freebsd.org/marketing/os-comparison.html](http://www.freebsd.org/marketing/os-comparison.html)

actually linux should start getting better in a few important points, specially the way they add hardware drivers

---

### Post by SunnyRabbiera on 2008-04-06
> **aktiwers said:**
> Heh It's not many years ago a Windows user would tell me the exact same thing about Linux compared to Windows.

Oh yes, but BSD is on its way.

---

### Post by plb on 2008-04-06
I used FBSD as a desktop for a number of years. FBSD actually used to be a lot faster than Linux until the 2.6 kernel. AFAIK, it was a FreeBSD dev who the gave Linux the added speed tinkering with the kernel. Also I believe FBSD used to be a lot more popular way back but it unfortunately took a hit in the courts...this is when Linux gained a lot of ground...when FBSD's future was uncertain.  Also, FreeBSD is an OS not just a kernel.

---

### Post by Sporkman on 2008-04-06
I've read in a fanboy's blog that BSD is *designed*, as opposed to Linux being *grown*.

Once I decided to do some reading up on how to set up a firewall in BSD as opposed to the way I do it in Linux via an IP tables script. The documentation I found on how to do it started off on some long lecture about the venerable history of BSD, saying that to understand how to set up a firewall we must understand the history of such-n-such functionality in BSD... I continued to scroll down & found the commands they finally got around to displaying to be very complicated & weird, and full of caveats.

Once I burned a FreeBSD live CD to attempt to try it out on my laptop. I got some sort of weird error messages about my graphics (iirc), otherwise it didn't work at all.

Recent benchmarks by BSD fans showed BSD to be 15% faster than linux, however that was disputed.

Seems like a lot more trouble than it's worth, if you ask me.

---

### Post by Dixon Bainbridge on 2008-04-06
Points to note:

You can run linux code in BSD but not vice versa

Its fast

Its stable

Its a bugger to get working properly

Linux pwns it for desktop use

Its fanboys are more annoying than any other OS, including Mac Users (but only just) :)

---

### Post by Sef on 2008-04-06
> bsd vs linux vs windows 2000

It was a great comparison, but it is too outdated to be useful anymore.

---

### Post by HermanAB on 2008-04-06
For many years people used BSD Jails as a sort of virtual server system.  Since Linux now has several similar systems, the need for BSD has decreased.  

BSD is really just a different kernel.  Al the usual utilities are GNU anyway, so the actual difference with a Linux distribution is minor.

---

### Post by puccaso on 2008-04-06
i have a dell inspiron 9400..
1gig ram, 128 graphics ati radeon x1400 mobile.. 1.8ghz dual core..


gutsy used to just sit over 400 meg idle memory usage.. 
freebsd with gnome 2.0 used to use just over 100.

bare in mind - people mistake linux for an operating system. its not - its a kernel - a way for the hardware to talk to the software.. so saying linux was grown is more accurate..  

us linux guys talk about the X server not being required  to run a computer, when we talk to windows users... 

well forget the xserver.. the linux kernel needs loads of usermode software and deamons to run.

bsd doesnt.

the bsd has a core system, and that core system runs the whole system. the kernel works different, hal (which has been included now and dbus) work different.. 

it is a pain, and i use hardy cos im using a desktop
but

and heres a big but - 

IF UBUNTU WERE TO CREATE A BSD based on freebsd or something

that would be AWESOME..
then we'd be unstopable..

---

### Post by Sporkman on 2008-04-06
> **puccaso said:**
> and heres a big but - 

IF UBUNTU WERE TO CREATE A BSD based on freebsd or something

that would be AWESOME..
then we'd be unstopable..

Debian is already doing it:

[http://www.us.debian.org/ports/kfreebsd-gnu/](http://www.us.debian.org/ports/kfreebsd-gnu/)

---

### Post by DahVid on 2008-04-06
I use it because of the robust Ports package management system.

---

### Post by ibuclaw on 2008-04-06
Hurd is only useful if you want multiple systems syncing together as one.

At least, that's the impression I get from their[ home site.]("http://www.gnu.org/software/hurd/hurd.html")

If you use apps such as blender, I can see it being a great tool.

For general desktop use, unfortunately not.

[EDIT]
Just downloading Debian/BSD right now :)

Regards

---

### Post by the_darkside_986 on 2008-04-06
There's a desktop-friendly FreeBSD distro known as PC-BSD. 1.3 was awesome but 1.4 was somewhat disappointing. It is nearly impossible for me to get nvidia drivers installed in FreeBSD but PC-BSD makes that easy. Also PC-BSD, which uses KDE, runs very smoothly on older desktops with only 256 MB of RAM and a Pentium II. 

I don't really care too much for PC-BSD's unique packaging system (PBI) not because it is bloated, but because it usually doesn't resolve all dependencies. The KDevelop PBI never would work properly for me.

---

### Post by Sporkman on 2008-04-06
> **tinivole said:**
> 
Just downloading Debian/BSD right now :)


Let us know how it goes. Me curious,,, :)

---

### Post by ibuclaw on 2008-04-06
How wicked is that as a bootsplash?

[[IMG]http://img402.imageshack.us/img402/9715/debianbsdfk6.th.jpg[/IMG]](http://img402.imageshack.us/my.php?image=debianbsdfk6.jpg)

Ermm... I may have to come back in an hour on the installation (says experts only) 8)
[[IMG]http://img167.imageshack.us/img167/84/debianbsd2om5.th.jpg[/IMG]](http://img167.imageshack.us/my.php?image=debianbsd2om5.jpg)

But download it!
It's only 99MB... Well worth the effort!
[http://glibc-bsd.alioth.debian.org/install-cd/](http://glibc-bsd.alioth.debian.org/install-cd/)

Regards
Iain

---

### Post by forrestcupp on 2008-04-06
> **wersdaluv said:**
> Good question. In what way is BSD better than Linux? Why use it if there's Linux? :)

Why use Linux when there's Windows?

One thing no one has really mentioned is that some people like the BSD license better than GPL.  Some people believe that the BSD license is a much freer license.

Also the fact that BSD is a complete OS that is more unified instead of a potpourri of things thrown together like Linux distros are.

I use Linux because it is more mainstream and has a lot of support.  But I think if a BSD had just as much support, it would probably be a better OS.

---

### Post by ibuclaw on 2008-04-06
OK, I'm a bit stuck on a partition issue...

Erm... Does FreeBSD need a swap partition?

I'm really not sure...

[EDIT]
Answer is Yes... I've just been shouted at by the installation for not putting one in :lolflag:

---

### Post by Meson on 2008-04-06
There is a much more defined line between the OS and userspace in BSDs.  Developement is also slow and steady.  Linux developers add features quickly but that leads to buggy code and such.  It may take longer for your hardware to be supported by BSD, but when it finally is, it will work smoothely and correctly.

---

### Post by puccaso on 2008-04-06
well debian also do linux

but ubuntu does it better..

gentoo tried to do a mobile gentoo thing

but ubuntu does it better..

---

### Post by Sporkman on 2008-04-06
> **puccaso said:**
> well debian also do linux

but ubuntu does it better..

gentoo tried to do a mobile gentoo thing

but ubuntu does it better..

...

> 
Nobody does it better
Makes me feel sad for the rest
Nobody does it half as good as you
Baby, you're the best

I wasn't looking but somehow you found me
It tried to hide from your love light
But like Heaven above me
The spy who loved me
Is keeping all my secrets safe tonight

And nobody does it better
Though sometimes I wish someone could
Nobody does it quite the way you do
Why'd you have to be so good?

The way that you hold me
Whenever you hold me
There's some kind of magic inside you
That keeps me from running
But just keep it coming
How'd you learn to do the things you do?

And nobody does it better
Makes me feel sad for the rest
Nobody does it half as good as you
Baby, baby, darlin', you're the best

Baby, you're the best
Darlin', you're the best
Baby, you're the best
Baby, you're the best
Baby, you're the best
Baby, you're the best

---

### Post by puccaso on 2008-04-06
hahahhaa:lolflag:

Jolene, jolene, jolene, jolene
Im begging of you please dont take my man
Jolene, jolene, jolene, jolene
Please dont take him just because you can
Your beauty is beyond compare
With flaming locks of auburn hair
With ivory skin and eyes of emerald green
Your smile is like a breath of spring
Your voice is soft like summer rain
And I cannot compete with you, jolene

He talks about you in his sleep
Theres nothing I can do to keep
From crying when he calls your name, jolene

And I can easily understand
How you could easily take my man
But you dont know what he means to me, jolene

Jolene, jolene, jolene, jolene
Im begging of you please dont take my man
Jolene, jolene, jolene, jolene
Please dont take him just because you can

You could have your choice of men
But I could never love again
Hes the only one for me, jolene

I had to have this talk with you
My happiness depends on you
And whatever you decide to do, jolene

Jolene, jolene, jolene, jolene
Im begging of you please dont take my man
Jolene, jolene, jolene, jolene
Please dont take him even though you can
Jolene, jolene


[I]
ok so jolene is the linux kernel
and dolly sincing is the glibc on bsd - whatever its called klibc i think.



[/I]

---

### Post by tubasoldier on 2008-04-06
> **the_darkside_986 said:**
> There's a desktop-friendly FreeBSD distro known as PC-BSD. 1.3 was awesome but 1.4 was somewhat disappointing. It is nearly impossible for me to get nvidia drivers installed in FreeBSD but PC-BSD makes that easy. Also PC-BSD, which uses KDE, runs very smoothly on older desktops with only 256 MB of RAM and a Pentium II. 

I don't really care too much for PC-BSD's unique packaging system (PBI) not because it is bloated, but because it usually doesn't resolve all dependencies. The KDevelop PBI never would work properly for me.


I really hated the PBI packaging system too. It was too much like windows. I had to install every single friekin package seperately. AAHHGGH!

There is another called DesktopBSD that works rather well. It really is a quick and easy install of FreeBSD that uses the robust ports system.

---

### Post by puccaso on 2008-04-06
i know but
why do all these bsd distro's use kde..? 
i mean i could do with xfce - but they should use gnome2.2 by now... 

this is why ubuntu should get into the act

---

### Post by tubasoldier on 2008-04-06
They use KDE for a number of reasons. I'm not going to start a flamewar over Desktop Managers, but you still have a choice.

Just because they use KDE by default does not mean that Gnome is unavailable. It is easily installable.

---

### Post by puccaso on 2008-04-06
it is
i've tried it

however all the distro tweaks have been done for kde.. all the system-config stuffs for bsd, are all done for kde.. 

i mean linux said linux users should use kde because it "conforms" better to standards,

---

### Post by odiseo77 on 2008-04-06
> **puccaso said:**
> it is
i've tried it

however all the distro tweaks have been done for kde.. all the system-config stuffs for bsd, are all done for kde.. 

i mean linux said linux users should use kde because it "conforms" better to standards,

FreeBSD comes with Gnome (you just have to select it in the installer, when you choose the set of packages to install).

---

### Post by tubasoldier on 2008-04-06
> **puccaso said:**
> 
however all the distro tweaks have been done for kde.. all the system-config stuffs for bsd, are all done for kde.. 


All the Ubuntu distro tweaks have been done for Gnome, treating KDE like a redheaded stepchild. Feels good to be a second class citizen doesn't it?

---

### Post by puccaso on 2008-04-06
well we have kubuntu.. and if u check the hardy blueprints it will give that redhead a nice make over into an arabian beautiful brunette.. 

tho i have to admit, redheads are cute.. 

but it back up my point, ubuntu should do bsd. :)

any ideas for names?

ubuntubsd?
bsdutunu?
bubuntusd?
freebuntu?
busundu?
busundu---! ithink thats the one


im gonna install freebsd 7 now and give it a try
lets see what its like

see u in bsd world

---

### Post by ibuclaw on 2008-04-07
> **puccaso said:**
> 
any ideas for names?

ubuntubsd?
bsdutunu?
bubuntusd?
freebuntu?
busundu?
busundu---! ithink thats the one


UbuntuBSD - concatenating two words isn't really the ubuntu way, else we'd have UbuntuKDE instead of Kubuntu.

FreeBuntu - That isn't very useful. Since Ubuntu is FREE to anyway! This would be bad publicising and give off the impression that the other distros aren't Free.

BubuntuSD - This is close, I think you are in the right frame of thinking, but I think that the "Bubu" part is a bit of a tongue twisting thing to say.

Perhaps removing the first two letters
```
 BuntuSD *{Bun-Too-Ess-Dee}* 
```

or if that doesn't make it obvious that it is Ubuntu over the hood.
Then I propose:
```

uBuntuSD *{Ooo-Bun-Too-Ess-Dee}*
FuBuntuSD *{Foo-Bun-Too-Ess-Dee}*
FruBuntu *{Froo-Bun-Too}* (my favourite)
FruBuntuSD *{Froo-Bun-Too-Ess-Dee}*
FrunBuntuSeD* {Froo-Bun-Toos-D}*

```

:popcorn:

Regards

---

### Post by fissionmailed on 2008-04-07
Well I'm downloading it and going to install it on my oollldddd laptop. :)

---

### Post by aaaantoine on 2008-04-07
> **puccaso said:**
> 
bsdutunu?


How about BuSunDu?

---

### Post by Sporkman on 2008-04-07
BSD-buntu.

That settles it. I have spoken. You may all move on, nothing more to discuss.

So... What's with the devil & pitchfork, anyway? How would that figure in to BSD-buntu CE?

---

### Post by ibuclaw on 2008-04-07
Have a look at [Ubuntu SE]("http://ubuntusatanic.org/news/").

That's a very devilish look that would go well with it.

Though I'd remove all hex stars and replace them with the plush toy that is FreeBSD (Afterall we want a Child-Friendly OS).
:popcorn:

---

### Post by forrestcupp on 2008-04-07
Ubuntu will never make a BSD distro because the philosophy is totally different.

---

### Post by ibuclaw on 2008-04-07
> **forrestcupp said:**
> Ubuntu will never make a BSD distro because the philosophy is totally different.

True, but it won't stop people from making a third party OS, if the incentive and brainpower just so happen to meet in a chatroom and follow through with the idea.

Besides, FreeBSD follows the same Debian-esck way of treating software.

For example, I don't think that KDE4.0 has even appeared in any Ports Tree yet...
Not for a few years until the technology becomes maturely stable.

And I could be wrong on the MITS License, but you should be able to move it onto any license you wish. So you can make it/present it in a way that is more close to home with Ubuntu.

I may be wrong though...

---

### Post by Istonian on 2008-04-07
Meh, i've tried BSD and I did not like it. Maybe someday I will give it another go, but Linux is far more advanced as far as desktop use IMO,

---

### Post by LinuX-M@n1@k on 2008-04-17
I installed FreeBSD today and couldn't set up my network. I installed Gnome with it, but when I log in to gnome as root and go to System > Administration > Network I get an error message:
"You don't have privileges" (or something like that)
I installed Ubuntu again and now (maybe) I'm going to install Arch Linux or Slackware. Just for fun..

Though, I'd preffer FreeBSD instead of any Windows OS :)
[IMG]http://www.stderr.de/funstuff/windows-freebsd.jpg[/IMG]
:lolflag:

---

### Post by LaRoza on 2008-04-17
> **Sporkman said:**
> 
So... What's with the devil & pitchfork, anyway? How would that figure in to BSD-buntu CE?

It is a daemon [http://en.wikipedia.org/wiki/Daemon_(computer_software](http://en.wikipedia.org/wiki/Daemon_(computer_software))

---

### Post by Ozor Mox on 2008-04-17
Haha great picture Linux-Maniac! Damn!

I was extremely proud of myself the other day when I got FreeBSD installed in a VM, and then got Xorg and GNOME installed on top of it and it worked nicely. Last time it blew up on several occasions. It's a very nice operating system, but it's rather bettered by Linux for the desktop, plus I prefer GPL licensing to BSD. (Windows could use BSD code legally, yuck!)

---

### Post by LaRoza on 2008-04-17
> **Ozor Mox said:**
> Haha great picture Linux-Maniac! Damn!

I was extremely proud of myself the other day when I got FreeBSD installed in a VM, and then got Xorg and GNOME installed on top of it and it worked nicely. Last time it blew up on several occasions. It's a very nice operating system, but it's rather bettered by Linux for the desktop, plus I prefer GPL licensing to BSD. (Windows could use BSD code legally, yuck!)

It does use BSD code (for networking I believe)

---

### Post by quinnten83 on 2008-04-18
> **LinuX-M@n1@k said:**
> 
[IMG]http://www.stderr.de/funstuff/windows-freebsd.jpg[/IMG]
:lolflag:
Yeah, I have a question. What if you're a woman? Would using free BSD make you a lesbian?

p.s. GOD i hope that image shows, cause otherwise I will come accross as misogynistic prick.

---

### Post by thisllub on 2008-04-18
I f the IPW3945 wireless driver worked properly and VirtualBox worked at all I would use it as my main os.

Low memory use stable and fast. It works better than any other os on my laptop. ACPI causes hanging in every Linux I have tried but works flawlessly in FreeBSD.

---

### Post by LightB on 2008-04-18
FreeBSD is a great OS, though in all honestly, compared to Linux it's like taking a step back in time when it comes to usefulness as a desktop OS, not to say that it's useless. But the fairly recent v7 has made some great strides in performance and other things. Nothing more to say really, if you're interested, try it. Costs nothing to do so.

---

### Post by LinuX-M@n1@k on 2008-04-18
> **quinnten83 said:**
> Yeah, I have a question. What if you're a woman? Would using free BSD make you a lesbian?

p.s. GOD i hope that image shows, cause otherwise I will come accross as misogynistic prick.

No, it won't made you a lesbian :) Maybe FreeBSD will be more careful with you :D

Sorry for the off topic:
For lesbians: [Lesbian (Debian-based)]("http://lesbian.mine.nu/")

---

