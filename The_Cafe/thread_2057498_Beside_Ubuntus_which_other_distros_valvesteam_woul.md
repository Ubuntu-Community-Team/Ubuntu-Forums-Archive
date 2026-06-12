---
title: "Beside Ubuntus which other distros valve/steam would support their games?"
date: 2012-09-13
forum: The Cafe
---

### Post by icett on 2012-09-13
As you know Valve/Steam are busy these days to port their games to Linux and the first distro they are going to support their games would be Ubuntu as well as other buntus and Ubuntu based distros. But they say that they would also be supporting their games for other Linux distros. Which other Linux distros you think valve/steam would most likely provide support for their games? In my view the first one most likely would be Debian (stable), thereafter Fedora, Mageia, Opensuse..... What you think? There are also rumors that valve/steam may develop their own Linux distro for their games or they may develop their own hardware for their games. I personally believe valve/steam would most likely develop their own Linux OS with cooperation from the many disgruntled MS OEMs which they together may introduce in competition to MS Windows 8! :)

---

### Post by Lucradia on 2012-09-13
If it's ported to one Linux distro, it's ported to all of them. ubuntu is based on Debian by the way.

Support on the other hand, is another story.

---

### Post by Primefalcon on 2012-09-13
> **Lucradia said:**
> If it's ported to one Linux distro, it's ported to all of them. ubuntu is based on Debian by the way.

Support on the other hand, is another story.
They're only supporting Ubuntu apparently at launch... not all that surprising really considering Ubuntu probally has 9 times more marketshare than all the other Linux distro's combined

---

### Post by mevun on 2012-09-13
> **Lucradia said:**
> If it's ported to one Linux distro, it's ported to all of them. ubuntu is based on Debian by the way.

Support on the other hand, is another story.

I guess "ported" in the usual sense of just compilation might be true for almost any Linux, but not in the sense of installation with the default package manager for a distro.  Maybe that is what you mean by "support", but I usually think of "support" as being if you call them up, can they help you fix your problem.

---

### Post by kostkon on 2012-09-13
> **Primefalcon said:**
> They're only supporting Ubuntu apparently at launch... not all that surprising really considering Ubuntu probally has 9 times more marketshare than all the other Linux distro's combined
And because it's a real consumer Desktop OS that obviously is also backed by a company (please don't mention Fedora, it isn't).

---

### Post by vexorian on 2012-09-14
> **Lucradia said:**
> If it's ported to one Linux distro, it's ported to all of them. ubuntu is based on Debian by the way.

Support on the other hand, is another story.
It is really not that simple. With open source software that's often the case, because it is easy for packagers in other distros to adapt whatever happened to the original game to work in the new distro.

But with proprietary, small things like how it is linked could make it very difficult to adapt a game from Valve to any other distro. Some of the distros which use similar package methods (debian) or similarly full stacks (Fedora) might have it easier than others. But the more different a distribution is to ubuntu, the harder will be to port a proprietary game. Unless valve are planning something like a FOSS wrapper library that could itself be ported as a bridge and then the game would run on the wrapper.

---

### Post by Primefalcon on 2012-09-14
> **kostkon said:**
> And because it's a real consumer Desktop OS that obviously is also backed by a company (please don't mention Fedora, it isn't).
The comparison there would be red hat... but lets face it, thats not aimed at your typical home users either

---

### Post by mips on 2012-09-14
I suspect it will work on all Ubuntu versions (K/L/Xubuntu) and most distros based on ubuntu and *maybe* Debian & Debian based distros.

---

### Post by Jakin on 2012-09-14
> **mips said:**
> I suspect it will work on all Ubuntu versions (K/L/Xubuntu) and most distros based on ubuntu and *maybe* Debian & Debian based distros.


I believe that too. In the beginning atleast, something Debian is best bet. Certainly it would be available for other linux distro's overtime, though.

---

### Post by Primefalcon on 2012-09-14
> **Jakin said:**
> I believe that too. In the beginning atleast, something Debian is best bet. Certainly it would be available for other linux distro's overtime, though.
I bet for sure 100% it'll work on any Ubuntu derivitives such as mint... and around 70% sure it'll work on debian based ones... (thing is it could be reliant on stuff ubuntu specific packages, who knows until it lands)

---

### Post by forrestcupp on 2012-09-14
> **vexorian said:**
> It is really not that simple. With open source software that's often the case, because it is easy for packagers in other distros to adapt whatever happened to the original game to work in the new distro.

But with proprietary, small things like how it is linked could make it very difficult to adapt a game from Valve to any other distro. Some of the distros which use similar package methods (debian) or similarly full stacks (Fedora) might have it easier than others. But the more different a distribution is to ubuntu, the harder will be to port a proprietary game. Unless valve are planning something like a FOSS wrapper library that could itself be ported as a bridge and then the game would run on the wrapper.
That's exactly what I was thinking. It's a lot harder to package proprietary things to work in other distros. The good thing is that you only have to get Steam to work with other distros. I'm sure the games themselves will be distro agnostic and their installation will be handled by Steam.

I kind of wish that they would just make a binary and dependency installer, like the old Loki ones, that installs it all to /home or /opt so they wouldn't have to worry about distros.

---

### Post by Lucradia on 2012-09-14
Deb + Alien = RPM.

Bam, done.

---

### Post by vexorian on 2012-09-14
> **Lucradia said:**
> Deb + Alien = RPM.

Bam, done.
Assuming valve distributes in .deb.

And if there is a dependency that is not portable, it would still not work.

We are talking about a proprietary games giant. It could even be against the ToS to port to another system.

---

### Post by forrestcupp on 2012-09-14
They're just starting with Ubuntu. It won't be that long before they have rpm versions out.

---

### Post by vexorian on 2012-09-14
How do we know that?

---

### Post by fontis on 2012-09-14
> **vexorian said:**
> How do we know that?

Because they said so themselves? :)


> 
Why Ubuntu? There are a couple of reasons for that. First, we&#8217;re just starting development and working with a single distribution is critical when you are experimenting, as we are. It reduces the variability of the testing space and makes early iteration easier and faster. Secondly, Ubuntu is a popular distribution and has recognition with the general gaming and developer communities. **This doesn&#8217;t mean that Ubuntu will be the only distribution we support. Based on the success of our efforts around Ubuntu, we will look at supporting other distributions in the future.**


Taken from the [Valve Linux blog]("http://blogs.valvesoftware.com/linux/").

---

### Post by vexorian on 2012-09-14
"Based on the success of our efforts around Ubuntu".

---

### Post by fontis on 2012-09-14
> **vexorian said:**
> "Based on the success of our efforts around Ubuntu".

Well yes, that is a fairly obvious statement isn't it?
I mean, if the biggest "market" attracts no success then why would they bother with continuing?

Assuming things go as we, and they, expect them to - the other distros should get their love with time.

---

### Post by doorknob60 on 2012-09-14
It should theoretically work (with some tweaking) on any distro. I've never seen anything made for Ubuntu that can't be made to work on Arch. Sure, it usually involves extracting the .deb file and installing a few different versions of libraries, but it's very doable, and easily made into an AUR package for easy installation. It just means they won't officially support it at first, which is smart. They don't want to have to worry about some obscure problem with Bill's Ultimate Linux 4.52, they want to just focus one one until everything works. I'm not worried.

---

### Post by Primefalcon on 2012-09-14
> **doorknob60 said:**
> It should theoretically work (with some tweaking) on any distro. I've never seen anything made for Ubuntu that can't be made to work on Arch. Sure, it usually involves extracting the .deb file and installing a few different versions of libraries, but it's very doable, and easily made into an AUR package for easy installation. It just means they won't officially support it at first, which is smart. They don't want to have to worry about some obscure problem with Bill's Ultimate Linux 4.52, they want to just focus one one until everything works. I'm not worried.
you can even do the same with the runescape gaming client... etract the msi file.... modify thelauncher to use your java executable and bang.. you have a native linux client that was designed for windows

---

### Post by vexorian on 2012-09-15
It would surely be nice if valve distributed their games in deb files. But that's not certain yet.

> **fontis said:**
> Well yes, that is a fairly obvious statement isn't it?
I mean, if the biggest "market" attracts no success then why would they bother with continuing?

Assuming things go as we, and they, expect them to - the other distros should get their love with time.
Yes. But we do not know yet if there will be enough a success to warrant that.

Even if it is very successful in ubuntu, I guess that the next step will still be exploratory, they will pick another popular distro and experiment. It will be a long time before they support many distributions.

And  we do not know for sure if the other distros they pick next will be rpm based.


> you can even do the same with the runescape gaming client... etract the msi file.... modify thelauncher to use your java executable and bang.. you have a native linux client that was designed for windows If it is java then it is not native in neither windows or Linux.

---

### Post by forrestcupp on 2012-09-15
> **vexorian said:**
> 
And  we do not know for sure if the other distros they pick next will be rpm based.

The very next one will probably still be deb based, but I'll bet that Fedora won't be far down the list.

---

