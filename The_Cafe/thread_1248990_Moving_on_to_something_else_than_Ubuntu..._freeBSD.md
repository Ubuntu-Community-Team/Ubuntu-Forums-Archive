---
title: "Moving on to something else than Ubuntu... freeBSD maybe?"
date: 2009-08-24
forum: The Cafe
---

### Post by pedrotuga on 2009-08-24
Please don't bash.
This is NOT a 'which is better' topic. If you intend to make such comparisons please do it somewhere else.

My experience using Ubuntu has been overall very positive, but it's time to move on. Ubuntu is not giving me what I want anymore, it became too unstable.

I've used windows in the past and linux has gave me what i wanted, a free open alternative with loads of software that simply works and does what is supposed to do. All the bloat and malfunctions of proprietary software gave me enough headaches and still do at work where i have to use them.

Unfortunately Ubuntu has given me more and more headaches lately. The major releases are too frequent for me and the compatibility string is rater short. Using an LTS version is an alternative but basically gets one stuck with a big percentage of really old software.

I love the package system and everything, but to be honest, these days it feels like the dependency tree is a porcelain doll.

I don't really know what to switch to. I though of puppy linux wich i've used a few times and felt pretty robust and well documented. That is still an option, but Maybe I would take the chance to try out something a bit different like FreeBSD which is said to be very stable.

Debian would be another

For those who know FreeBSD, as a desktop user, what big differences would i encounter? What kind of software is not so straight forward to run on freeBSD?
Advantages, disavantages?

I have many applications' data which i would like to keep and that is stored on ~/.appname, that will work normally in freeBSD as well, right?

Any other operative system suggestions?

---

### Post by HappyFeet on 2009-08-24
Windows? Mac?

---

### Post by &#32 Greg on 2009-08-24
Try Slackware or a source based distro- you get control and stability with most of them.

---

### Post by HappyFeet on 2009-08-24
But seriously, go to distrowatch and start burning cd's. If you want my opinion, give Mandriva One a shot. Has worked great for me.

---

### Post by OutOfReach on 2009-08-24
OpenSUSE or Fedora, I recommend

---

### Post by kk0sse54 on 2009-08-24
Freebsd is an excellent operating system that I've used as my primary desktop OS for the past few months. Other than a few nuisances here and there much of it should be pretty similar to linux. It's when you really start poking around that the not so obvious becomes quite dissimiliar especially under the hood.  As for software selection Fbsd ports system has over 20,000 ports which can be either compiled or installed as binary packages. A few things such as flash are not available natively but can installed and run through a linux compatibility layer which allows you to run linux binaries in fbsd.
 
I suggest reading over this for a more in depth comparison on freebsd and linux [http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php) 

*Remember the FreeBSD handbook is your friend :)

---

### Post by hockeyfighter09 on 2009-08-24
Arch is what stopped my distrohopping.  Rolling release, very stable in my experience using bleeding edge software, blazingly fast optimized for i686 and x86_64 and ultra customizable.  Sure the install takes awhile but its worth it, try it out to experience it yourself :popcorn:

---

### Post by DeadSuperHero on 2009-08-24
There's an experimental version of OpenSolaris out with KDE 4.3 in it. It's called Korona, maybe worth a look?

Live DVD: [http://genunix.org/dist/korona/Korona-0.0.2.iso](http://genunix.org/dist/korona/Korona-0.0.2.iso)

Phoronix Article: [http://www.phoronix.com/scan.php?page=article&item=korona_opensolaris_kde&num=1](http://www.phoronix.com/scan.php?page=article&item=korona_opensolaris_kde&num=1)

---

### Post by CJ Master on 2009-08-24
> **hockeyfighter09 said:**
> Arch is what stopped my distrohopping.  Rolling release, very stable in my experience using bleeding edge software, blazingly fast optimized for i686 and x86_64 and ultra customizable.  Sure the install takes awhile but its worth it, try it out to experience it yourself :popcorn:

This. Once you get it set up you'll love it TO DEATH.

---

### Post by chucky chuckaluck on 2009-08-24
> **C!oud said:**
> A few things such as flash are not available natively but can installed and run through a linux compatibility layer which allows you to run linux binaries in fbsd.

is the linux compatibility layer to freebsd what wine is to linux, metaphorically speaking?

---

### Post by yabbadabbadont on 2009-08-24
> **chucky chuckaluck said:**
> is the linux compatibility layer to freebsd what wine is to linux, metaphorically speaking?

I'm not positive, but I believe that it is at a lower level than that.  Kernel level, I think.

---

### Post by Grifulkin on 2009-08-24
Yeah Slackware or Arch I have heard very good things and hope to be moving to one of them myself soon, as soon as I get home and can really mess with it.

---

### Post by kk0sse54 on 2009-08-24
> **chucky chuckaluck said:**
> is the linux compatibility layer to freebsd what wine is to linux, metaphorically speaking?

For the most part, yes. Both of them are compatibility layers but the linux compatibility layer is a hell of a lot more reliable often times without any sort of performance hit and is more integrated into the system.

---

### Post by Firestem4 on 2009-08-24
If you like the Ubuntu APT-Manager but want more stability check out Debian. Though it is moving to a quicker-release schedule than previously known its still pretty distanced enough for the stability to remain.

i am a big fan of Arch Linux. The overall quality is astounding IMO and with a rolling release you always have the latest and up to date software.

Mandriva is a very rock-solid Distro as far as I have used it. (Granted i haven't truly spent much time using it but its a nice distro. It is RPM based as well which is similar to Feodra/OpenSUSE.)

---

### Post by kk0sse54 on 2009-08-24
> **yabbadabbadont said:**
> I'm not positive, but I believe that it is at a lower level than that.  Kernel level, I think.

Yes it is but you are required to install a linux_base port or install the libraries manually.

---

### Post by Ichtyandr on 2009-08-24
Try PC-BSD if you fancy KDE, very easy to setup and based on FreeBSD. I went back to Ubuntu because of love for Gnome

---

### Post by tubasoldier on 2009-08-24
I would reccomend using a virtualbox to mess around with other distros before you decide to make the switch. That way you save all those disks for something else and there are no worries about losing data.

Arch is great but I've never had the guts to use it on a production machine. maybe i'm just paranoid

Mandriva is great. the system configuration tool is top notch.

PCLinuxOS is OK. It seems to have a lot of the bugs that plagued the Mandriva 2006 release, which I believe is the one it was forked from. I could be wrong about that.

I've used Fedora and thought it worked well but it is pretty bleeding edge and things don't always work.

I've always found at least one showstopper issue with OpenSuse.

FreeBSD was fun but I had wireless issues and needed to move on.


Good luck on your quest.

---

### Post by Gen2ly on 2009-08-24
Give FreeBSD a go.  It's a good OS.  Learning how to use FreeBSD isn't gonna be that much more of a learning curve now that you know Ubuntu.  If your problem is stability though the drivers... are alot like Linux's.  Perhaps you caught one of those bugs.  If it is a bug, I'd consider using a heavily populated distro (generally they get fixed better in these), so like a previous user suggested you might try Fed11 or OSuse.

---

### Post by karlmp on 2009-08-24
|

---

### Post by Firestem4 on 2009-08-24
PCBSD is another good Operating System/Distro. I not totally sure of the significant differences between FreeBSD and PC-BSD but ive been wanting to try it out myself.

[www.pcbsd.org](www.pcbsd.org)

---

### Post by HappinessNow on 2009-08-24
> **pedrotuga said:**
> Please don't bash.
This is NOT a 'which is better' topic. If you intend to make such comparisons please do it somewhere else.

My experience using Ubuntu has been overall very positive, but it's time to move on. Ubuntu is not giving me what I want anymore, it became too unstable.

I've used windows in the past and linux has gave me what i wanted, a free open alternative with loads of software that simply works and does what is supposed to do. All the bloat and malfunctions of proprietary software gave me enough headaches and still do at work where i have to use them.

Unfortunately Ubuntu has given me more and more headaches lately. The major releases are too frequent for me and the compatibility string is rater short. Using an LTS version is an alternative but basically gets one stuck with a big percentage of really old software.

I love the package system and everything, but to be honest, these days it feels like the dependency tree is a porcelain doll.

I don't really know what to switch to. I though of puppy linux wich i've used a few times and felt pretty robust and well documented. That is still an option, but Maybe I would take the chance to try out something a bit different like FreeBSD which is said to be very stable.

Debian would be another

For those who know FreeBSD, as a desktop user, what big differences would i encounter? What kind of software is not so straight forward to run on freeBSD?
Advantages, disavantages?

I have many applications' data which i would like to keep and that is stored on ~/.appname, that will work normally in freeBSD as well, right?

Any other operative system suggestions?

Macpup Opera or PC-BSD

> **Ichtyandr said:**
> Try PC-BSD if you fancy KDE, very easy to setup and based on FreeBSD. I went back to Ubuntu because of love for Gnomeyou can also use Gnome or e17 on PC-BSD.

> **Firestem4 said:**
> PCBSD is another good Operating System/Distro. I not totally sure of the significant differences between FreeBSD and PC-BSD but ive been wanting to try it out myself.

[www.pcbsd.org]("http://www.pcbsd.org")Again, PC-BSD is a very good option.

---

### Post by tubasoldier on 2009-08-24
> **Firestem4 said:**
> PCBSD is another good Operating System/Distro. I not totally sure of the significant differences between FreeBSD and PC-BSD but ive been wanting to try it out myself.

[www.pcbsd.org](www.pcbsd.org)


PC-BSD is really FreeBSD with a nice graphical install that holds your hand the whole way. I liked using it but the PBI installer packages were obnoxious, reminding me too much of windows. I just wanted all packages available in a repository as opposed to having to install each single package separately.

---

### Post by Ichtyandr on 2009-08-24
> **&#20170 said:**
> 

you can also use Gnome or e17 on PC-BSD.



This is true of course, but turns out a bit masochistic. KDE works great there though, utilities nicely integrated etc. 

With PC-BSD I also liked the fact that my nvidia drivers were already included.

---

### Post by HappinessNow on 2009-08-24
> **Ichtyandr said:**
> This is true of course, but turns out a bit masochistic. KDE works great there though, utilities nicely integrated etc. 

With PC-BSD I also liked the fact that my nvidia drivers were already included.

PC-BSD has to be one of the best KDE centric distros out of anything by BSD and Linux. PC-BSD blows Kubuntu away!

---

### Post by hanzomon4 on 2009-08-24
> **karlmp said:**
> all operating systems suck

Primus sucks

---

### Post by karlmp on 2009-08-25
|

---

### Post by CJ Master on 2009-08-25
In my experiences FreeBSD seemed not on par with linux.

> **karlmp said:**
> what the heck is Primus?

Your mom.

OH YES I JUST WENT THERE! :D

---

### Post by RiceMonster on 2009-08-25
> **CJ Master said:**
> Your mom.

OH YES I JUST WENT THERE! :D

Dude, karlmp's mom play's a MEAN bass.

---

### Post by karlmp on 2009-08-25
[http://esr.ibiblio.org/?p=628](http://esr.ibiblio.org/?p=628)

[http://www.haiku-os.org/about/faq#3](http://www.haiku-os.org/about/faq#3)

@ pedrotuga

i recommend you to go first with another linux distro and then bsd

---

### Post by blueturtl on 2009-08-25
If stability is the only problem you have with Ubuntu, you should love Debian.

I made the move myself and it's been great.

You only really need the latest and greatest when it comes to stuff like Firefox and OpenOffice which are available to the latest stable Debian through backports.

If you need propriatory stuff like video drivers, you might have to set them up manually as Debian is more conservative than Ubuntu about that sort of thing.

---

