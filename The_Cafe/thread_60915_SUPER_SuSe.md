---
title: "SUPER SuSe"
date: 2005-08-29
forum: The Cafe
---

### Post by drizek on 2005-08-29
Im dual booting suse 10 beta 3 and breezy right now. i like them both, but i am leaning towards suse, for now at least. i might have to rethink the whole thing once i can compare KDE 3.5 implementations. 

anyway, before i got into ubuntu, my favorite distro was yoper. yoper is a distro much like ubuntu, but it was much faster and easier to use. 

Anyway, the head yoper developer was doing it all by himself, and decided he was just going to stop. yoper right now is being developed by others, but obviously it was a messy transition. 

So anyway, the ex yoper developer, andreas, is now working on a project for novell called SUPER. SUPER stands for SUse Performance Enhanced Release.

It has a lot of the cool features of yoper, but with more developers and the suse community to fall back on. 

here are the features which i thought were pretty cool

Single CD
i686 optimized packages(kernel and other major packages. minor things will be i386 and available from the main suse repos)
Prelinking
Preloading(loads major packages like KDE and OOo at the beggining of the boot, so they open up quicker once hte system has finished booting)
Support for Win32Codecs out of the box (mp3, DVD, etc)
Ability to install ATI drivers as easily as nvidia ones

It is still under development, but im really interested in it. 
Main page: [http://www.opensuse.org/index.php/SUPER](http://www.opensuse.org/index.php/SUPER)
Benchmarks: [http://www.opensuse.org/index.php/SUPER_standard_benchmark](http://www.opensuse.org/index.php/SUPER_standard_benchmark)

So what do you guys think about this? i personally cant wait to try it out for myself(if you havent noticed yet, lol)

---

### Post by manicka on 2005-08-29
It looks like a kde only release. It may interest kubuntu users

---

### Post by drizek on 2005-08-29
[QUOTE=manicka]It looks like a kde only release. It may interest kubuntu users[/QUOTE]
 yes it is, but its a community project, so im sure that there will be a gnome version out eventually. really, all it takes is to change a couple of things in the preload settings and to recompile gnome for i686.

---

### Post by benplaut on 2005-08-29
SWAG?

Suse With Apt-Get... if they had that, but with actual apt-get (not apt runing on top of RPM), i would use it


/me feals like a traitor  :roll:

---

### Post by drizek on 2005-08-29
[QUOTE=benplaut]SWAG?

Suse With Apt-Get... if they had that, but with actual apt-get (not apt runing on top of RPM), i would use it


/me feals like a traitor  :roll:[/QUOTE]
 why?

in my experience, rpm>deb

any dependency problems or whatever that you had when using rpm's were due to either bad packaging or a bad package manager. if you use smartPM with suse(or any distro), then any "dependency hell" problems will go away. 

and you shouldnt feel like a traitor. there is nothing wrong with using another distro. thats what linux is all about anyway.

---

### Post by drizek on 2005-09-02
The new release with beta 4 looks to be even better. 

3 seconds to launch OOo writer
**26 seconds from grub to KDE desktop**

thats pretty impressive right there, considering suse is about as fully featured as you can get, and they havent even finished doing optimizations yet. if they use initing, reiser 4 and reduce some of the default services, im sure it will bootinto KDE in under 18 seconds.

[http://opensuse.org/index.php/SUPER_standard_benchmark](http://opensuse.org/index.php/SUPER_standard_benchmark)

---

### Post by benplaut on 2005-09-02
[QUOTE=drizek]The new release with beta 4 looks to be even better. 

3 seconds to launch OOo writer
**26 seconds from grub to KDE desktop**

thats pretty impressive right there, considering suse is about as fully featured as you can get, and they havent even finished doing optimizations yet. if they use initing, reiser 4 and reduce some of the default services, im sure it will bootinto KDE in under 18 seconds.

[http://opensuse.org/index.php/SUPER_standard_benchmark](http://opensuse.org/index.php/SUPER_standard_benchmark)[/QUOTE]

oh, god... that is *fast*

i might actually use this, despite my love of apt  :?

---

### Post by drizek on 2005-09-02
[QUOTE=benplaut]oh, god... that is *fast*

i might actually use this, despite my love of apt  :?[/QUOTE]

my computer is a little slower than the system they did the benchmarks with, but it took me about 50 seconds to get to kde. not bad at all, but i thought it would do better. although it might just be because i need to mount more drives and stuff like that. that said, it only took about 4 seconds to lauch openoffice, which was a good thing. the distro right now is pretty unpolished, but they are going to release another iso in a couple days taht is i686 optimized, which should improve performance some more. its not the standards suse desktop like i thought it would be, its pretty much a standard kde desktop with no suse branding. 

but the most noticeable missing thing here is Yast. they are going to put it back in soon, but with apt instead, which i think is a great idea. i like suse a lot, but using YOU was a pain at times. 

anyway, its promising, but im not converting just yet. now i just need to figure out how to apply deltas on the beta3 isos so i can install beta4 proper.

---

### Post by felix.rommel on 2006-01-11
(SUPER)SUSE 10 is the fastest distro I used and still use because it's much faster than Breezy. I hope that they will integrate the preload stuff like they did in SUPER in Dapper.

The only thing I have seen so far is that there is a program "preload" in the Dapper repository available which speeds up Firefox and Openoffice a lot! The only remaining problem is that the bootup time is ca. 20 s slower because some stuff is preloaded.

Now they only have to optimize Dapper like SUPER so that the boot time with preload gets a lot better.

But one thing which is a real big showstopper for SUSE is that some USB sticks like mine are sooo slow. I could write with 4 KByte/s on it... I had to disable the sync option and now it's fast again. But this is not userfriendly and I don't understand how they could not resolve this bug because it is very important for people to use their USB sticks with good speed. If they see how slow it is they may never use their SUSE box again...

---

### Post by Iandefor on 2006-01-11
Preloading seems to be the only place where SUSE outperforms SUPER. Interesting. I might check this out sometime.

---

### Post by drizek on 2006-01-11
the problem with the usb sticks is that they only work in usv 1.1 mode, so they are a ton slower than they are in kubuntu. im sure they will work this out for 10.1. anyway, i think SUPER might be dead as a result of the layoffs novell did....

---

### Post by Dr. Nick on 2006-01-12
looks cool, curse this small laptop hard drive.
Not sure i want to toss ubuntu for it since it takes so long to configure anything with 128mb of ram and a p2.

May have to backup then test it out.

---

### Post by drizek on 2006-01-12
no, dont mess with this on that hardware. you should use somethign like vector linux on that though.

---

### Post by Dr. Nick on 2006-01-12
[quote=drizek]no, dont mess with this on that hardware. you should use somethign like vector linux on that though.[/quote]

lol, ubuntu is actually usable and not to painful on it. I think ubuntu will stay, if it isnt broke dont fix it :)

If i try it out ill do it on my desktop from my signature. Ill keep an eye on it and wait till a newer release and try it out.

---

### Post by poofyhairguy on 2006-01-12
[QUOTE=drizek]
but the most noticeable missing thing here is Yast. [/QUOTE]

Sounds like a plus. I have always thought that SUSE was the second best distro (it would be first if it had a repo with 17000+ packages like Ubuntu has) but I disliked YAST.

No YAST sounds tasty.

---

### Post by drizek on 2006-01-12
well, like i said, i think it is dead. kinda sad. 

anyway, they eventually did get around to adding yast in there. i dunno what hte last suse release you used was, but for me yast works pretty well.

---

### Post by jsgotangco on 2006-01-12
We've been using SuSE as well in my wife's laptop...she prefers it over Ubuntu though (which really hurts my pride being involved in the project) :(

But i do like it though...

---

### Post by towsonu2003 on 2006-01-12
just wanted to thank the OP. Such brief overviews in the Community chat are very useful... you dont get everything fron the distrowatch weekly u know ;)

I surely will give it a try some time, although I'm addicted to apt/synaptic...

the slowness is kinda (emphasis on 'kinda') bugging me, but I think it's more about my ati card & my ignorance of proper configuration than ubuntu itself in my case. hopefully in dapper my ati will be well supported (without breaking the modem)...

again>thanks!

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-01-12
Just wanted to point out that you can use apt and synaptic with Suse. So if that is holding someone back from trying out Suse, don't be too afraid because of it.

About Yast: Though it sure is far from perfect, it certainly does provide a lot of the things that are missing from Ubuntu right now.

---

### Post by manicka on 2006-01-12
[QUOTE=SuperDiscoMachine V.5.7-3]
About Yast: Though it sure is far from perfect, it certainly does provide a lot of the things that are missing from Ubuntu right now.[/QUOTE]

like?

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-01-12
[QUOTE=manicka]like?[/QUOTE]
A graphical frontend to set up stuff. Just look at all the posts of people having problems configuring their X-server. Yast, or rather sax, provides a graphical way to do this, Ubuntu doesn't.

Or how about configuring your broadband or modem connection. Again, no nice graphical way to do it in Ubuntu, but Yast provides such a way.

How about if you want to configure your hard disks? Ubuntu: edit fstab. Suse: Use Yast. And what about enabling/disabling dma?

Really, there are lots and lots of examples. Yast certainly has it's problems and I think relying on upstream tools like kde-guidance or the gnome-system-tools as Ubuntu does to a large extent is ultimately the better way, but Yast right now provides Suse users with a graphical front end to almost every configuration option.

If you read about the problems many people here have when they need to edit config files by hand, I think this is a good thing for many users. And of course 99% of the complaints you find in the frequent "Why Linux isn't ready for the desktop" posts here that deal with the lag of graphical configuration tools are void, because othere distros like Suse with Yast provide these tools.

---

### Post by manicka on 2006-01-12
hmm, it's been that long since I've used SuSe that I forgot about lots of those. I just found Yast a bit flakey when doing some critical tasks like setting up Samba. 

In Ubuntu I found a nice howto here and had it up and running in minutes whereas  I battled for hours to achieve the same with SuSE/Yast. Sometimes a good howto and a config file can be a much easier way to do things, but for new users I guess Yast does most things pretty welll and is easy to use.

---

### Post by towsonu2003 on 2006-01-12
[QUOTE=manicka]
In Ubuntu I found a nice howto here and had it up and running in minutes whereas  I battled for hours to achieve the same with SuSE/Yast. Sometimes a good howto and a config file can be a much easier way to do things, but for new users I guess Yast does most things pretty welll and is easy to use.[/QUOTE]
I had problems finding documentation for suse as well, compared to ubuntu (and its howtos). possibly my fault though...

---

### Post by Dr. Nick on 2006-01-12
[quote=towsonu2003]I had problems finding documentation for suse as well, compared to ubuntu (and its howtos). possibly my fault though...[/quote]
 
From my little suse expeirence and what I have heard from a few others online, the suse forums are not as active and not as useful as these ubuntu forums. I am sure their are some very helpful people over their , dont get me wrong, but their documentation wasnt as easy to find Ubuntus in my opinion

---

