---
title: "can you recommend a rolling release, or a long release cycle, distro that's stable?"
date: 2008-02-16
forum: The Cafe
---

### Post by ice60 on 2008-02-16
I'm trying to find a distro that has a long release cycle, or rolling release. i don't like ubuntu's 6 month releases it's not long enough for me. my main desktop was installed over a year a go and i'm happy with it so i'm not in a big hurry to find something, but i have 2 HDDs so i want to set something up on the other HDD and slowly move over to that.

all i want is a stable distro with fairly good to excellent repos and that doesn't use KDE!

i haven't looked yet, but what i thought of was maybe something based on slackware (if the repos are good), or arch (is arch stable?), or debian or gentoo (i don't really know, but i thought gentoo might have had some community problem sometime a go with Daniel Robbins coming and going??)

would you pick one of those for your main desktop? or is there something else? thanks.

---

### Post by kellemes on 2008-02-16
One word.
Debian.

---

### Post by LaRoza on 2008-02-16
Slackware would be my choice.

Arch is stable, if you install stable software on it. Debian might be what you want, if you don't mind being a bit behind.

---

### Post by Xyhthyx on 2008-02-16
This should be in the other distros forum.

Anyways, there's Debian testing or sid if you still want to use apt (I use testing with a bit of sid), Foresight and its conary packaging system, Arch with pacman and Gentoo with emerge. All use rolling release.

---

### Post by ice60 on 2008-02-16
thanks for the replies :) i suppose as i'm not in a hurry i could pick 3 or 4 and try them out for a few weeks each, but i might just end up using whichever i install first!

i really can't make up my mind, gentoo is the only one i've never even installed out of the ones i mentioned. i just thought i can try them out in a VM first :D

i don't know anything about Foresight or conary, i've only heard conary mentioned a few times.

---

### Post by kellemes on 2008-02-16
> **ice60 said:**
> 
i haven't looked yet, but what i thought of was maybe something based on slackware (if the repos are good)

Zenwalk is based on Slackware and can be used rolling, search there forums for instructions. Zenwalk is a big surprise to me, it's very fast and includes a lot of fine tools to make the job of managing your system easy.
Package management using Netpkg (one of the options) is very straightforward and works fine.
XFCE is installed by default, Zenwalk shows off XFCE at it's best.
> 
or arch (is arch stable?)

Depends on the user I'm afraid ;-)
The quality of packages is very good imho.
Arch doesn't install a wm/dm at all, you have to setup X from the start, so the choice is yours.. By the way, Arch has KDEmod, this is a moded version of KDE that performs pretty fine and looks even better.

> 
or debian

Debian gives you a lot stability and a rather vanilla environment, this includes Gnome but don't expect a lot of bling bling. You (the user) has to mold the system as he wishes.
I use Debian Testing with a little sid. Always does the job and this makes me trust the system as no other distribution can. Just my personal opinion.

> 
 or gentoo (i don't really know, but i thought gentoo might have had some community problem sometime a go with Daniel Robbins coming and going??)

Gentoo is source-based, this gives you enormous control over your system, basically every package you 'emerge' will be compiled, and so you *can* control the compilation of packages as well as the installation. At least it will give you the feel of compiling your os for your system. Can be a pretty adictive feeling. ;-)
Also Gentoo gives you no wm/dm, you need to setup X.
By the way.. 'the community problems' are a sign of a very active and devoted community, so no reason to not use it because of this.

> 
would you pick one of those for your main desktop? or is there something else? thanks.
Well yes, I'm using Debian. ;-)
Anyway, take a look at your options..
[http://distrowatch.com/]("http://distrowatch.com/")
Good luck and have fun.

Edit: Also see [Sidux]("http://sidux.com/").
Heard only good things about it **and** rolling indeed.

---

### Post by Kernel Sanders on 2008-02-16
> **kellemes said:**
> One word.
Debian.

:guitar:

---

### Post by gn2 on 2008-02-16
If you can wait a while there's a good long term support version of a very popular distro which is due out in April.

It's called Ubuntu Hardy Heron and will be fully supported for three years.

---

### Post by %hMa@?b&lt;C on 2008-02-16
i strongly recommend debian lenny or sid.

---

### Post by ice60 on 2008-02-16
thanks for the help everyone, after reading through this thread and thinking more about it, i'm going to use either arch or debian. i did use arch very briefly once (until i managed to format the drive by mistake lol) and i really liked how quick everything was - booting and the system in general. however, i just decided to go with debain 

[img]http://www.scuba2000.com/forum/images/smilies/Ifireworks3.gif[/img]

---

### Post by plb on 2008-02-16
debian++ I've been using *nix systems for nearly 10years and nothing beats the stability of debian stable.

---

### Post by ice60 on 2008-02-16
well, now i don't know what to install? i thought most people used the testing version. which should i use? kellemes said "I use Debian Testing with a little sid" what does that mean? install testing and use sid repos?? Sid is the stable one, right?

i'm sure i've got debian installed in a VM, so i do have one of the ISOs somewhere, i'll have to check which one it is.

[color=blue]EDIT[/color] i looked in /etc/debian_version, in the VM debian i've got, and it says 4.0, is that testing?

---

### Post by plb on 2008-02-16
no etch is stable, testing is lenny (next stable release due in september), sid is unstable... If you want stability go with etch.

---

### Post by ice60 on 2008-02-16
> **plb said:**
> no etch is stable, testing is lenny (next stable release due in september), sid is unstable... If you want stability go with etch.
thanks, i'll have a look and see which versions i've got, i've definitely got debian 4.0 i'll check which one that is. i think i want to use lenny, it's not unusual for someone to use lenny as their main desktop is it? i don't want to use it if it's not recommended.

---

### Post by cprofitt on 2008-02-16
Hmm...
 
so far on my journey I would recommend the following:
 
Debian (stable) with backports for things you really want/need (this is not a rolling distro though)
 
or
 
Arch which has been very stable and has an excellent wiki. I like pacman better than apt at this point because I can use
```

pacman -Qdt

```
 
To get a list of packages installed as dependencies, but no longer in use by any currently installed packages. It might be available in apt, but I have not found the command.
 
I have tossed aside:
 
Fedora
openSuse
Gentoo
Slackware
 
I like Ubuntu but currently while I am learning it seems to do too much automagically for me.
 
For a rolling distro I would recommend Arch for stability I really like Debian.

---

### Post by cprofitt on 2008-02-16
> **ice60 said:**
> thanks, i'll have a look and see which versions i've got, i've definitely got debian 4.0 i'll check which one that is. i think i want to use lenny, it's not unusual for someone to use lenny as their main desktop is it? i don't want to use it if it's not recommended.
 
You can use Lenny (though there are issues wit doing so as I found out from a Deb Dev) so I would recommend using Etch and using backports for the things you need.

---

### Post by Miguel on 2008-02-16
If you want stability, go for Debian stable (etch). Forget about anything else. Well, may be slack is close, but my experience with Debian stable has been superb.

If you want a rolling release, Arch is good. I liked it, although I lacked the devotion and knowledge to make it really shine. Well, it's that, or the Ubuntu gnome packages are better. Another choice might be Debian testing. It's usually good, although progress stagnates a couple of months before releasing stable and sometimes small breakage occurs (nautilus last month sucked, for example). 

Finally, debian allows apt-pinning (does this work in ubuntu?). This allows you to have the core (binutils, kernel, basic libs, compiler...) from stable and gnome from testing. You might even install the latest gnuplot from unstable.

And as you asked, I run Ubuntu on my laptop, but the two desktop PC's I manage run Debian Testing.

> **PrivateVoid said:**
> 
Arch which has been very stable and has an excellent wiki. I like pacman better than apt at this point because I can use
```

pacman -Qdt

```

I'm sure you'll love deborhpan. In both ubuntu and debian.

---

### Post by leftorvo on 2008-02-16
Debian, then pick stable, testing, or unstable based on your choice on how to balance stability with newer programs.

---

### Post by ice60 on 2008-02-16
OK, i got it, thanks for the help. stable with backports sounds perfect, i've got the etch iso somewhere already. i'll lookup apt-pinning too.

---

### Post by plb on 2008-02-16
BTW Debian also has a forum if you have questions forums.debian.net :)

---

### Post by LookTJ on 2008-02-16
Simple answer, Arch Linux.

---

### Post by farruinn on 2008-02-16
> **Miguel said:**
> Finally, debian allows apt-pinning (does this work in ubuntu?).

It does. I would be surprised if the apt in Ubuntu differed from the apt in Debian.

And OP, Ubuntu LTS - long term support. It sounds like this is exactly what you're looking for.

---

### Post by cprofitt on 2008-02-17
> **Miguel said:**
> I'm sure you'll love deborhpan. In both ubuntu and debian.

Hmm... I will have to give that a try... kinda thought I missed a Synaptic or apt-get command to do what I found with pacman.

---

### Post by cookdav on 2009-10-03
If you want a Debian-based distro that has a true
rolling-release-cycle, try 'sidux'.

[Tho, it's based on 'sid', which is defined as "unstable", 
but the net result is that sidux is very stable and yet always stays
at the cutting-edge of newest-code for most all packages!]

It achieves this by the developers overiding anything that's 'broken'
by a version in their own repository that isn't broken.

[Don't know if I'm explaining it very well.  But, try it and you'll
like it!  I've been using sidux for almost 2 years now, and I only
saw a breakage from updates ONCE during all that time (and the fix
for those effected was posted with just 2 days after it occurred).]

sidux ROCKS!

---

### Post by szymon_g on 2009-10-03
RHEL, CentOS/ScientificLinux, SLED/SLES, debian

---

### Post by earthpigg on 2009-10-03
holy necrophilia! 

:D

---

### Post by Skripka on 2009-10-03
> **earthpigg said:**
> holy necrophilia! 

:D

Holy Year-And-A-Half Old Threads, Batman!

---

### Post by ninjapirate89 on 2009-10-03
> **earthpigg said:**
> holy necrophilia! 

:D

:lolflag:

---

### Post by cariboo on 2009-10-03
Closed for thread necromancy

---

