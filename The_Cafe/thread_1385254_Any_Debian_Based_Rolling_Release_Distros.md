---
title: "Any Debian Based Rolling Release Distros?"
date: 2010-01-19
forum: The Cafe
---

### Post by BrokenKingpin on 2010-01-19
I am looking for a rolling release distro based on Debian. I hate the 6 month release cycle of Ubuntu, as well as the 10 year (ok a bit exaggerated) release cycle of Debian. So I wanted something I don't have to reload every 6 months for the latest stuff, and that keeps relatively up to date packages in the repos.

I think Debian Sid (unstable branch) is a rolling release, but I have heard that the system can be unstable due to the nature of the package updates. Also, it says on their website that Sid isn't supported by the security team, which is concerning.

There is also Sidux, but this in theory has the same problems as Debian Sid, as that is what it is based on.


So does anyone know of a Debian based rolling release distro?

---

### Post by Techsnap on 2010-01-19
Debian testing?

---

### Post by Psumi on 2010-01-19
> **Techsnap said:**
> Debian testing?

Don't you mean sidux?

[http://en.wikipedia.org/wiki/Sidux](http://en.wikipedia.org/wiki/Sidux)

Besides that, no, there are none that I know of.

---

### Post by Techsnap on 2010-01-19
No I mean the testing branch of Debian. [http://www.debian.org/releases/testing/](http://www.debian.org/releases/testing/)

---

### Post by TheNosh on 2010-01-19
> **Psumi said:**
> Don't you mean sidux?

[http://en.wikipedia.org/wiki/Sidux](http://en.wikipedia.org/wiki/Sidux)

Besides that, no, there are none that I know of.

no, i'm pretty sure he means Debian Testing. like he said.

debian has stable, testing, and unstable versions. if i'm not mistaken, both testing and unstable are rolling release. think of testing as being like a current ubuntu release and stable as being more like an LTS. that's not quite how it works with debian, but it's close enough for a simple explanation.

sidux is based on debian unstable (sid) and the idea is that they have made it safe to use. i've never used it, so i don't know how true that is.

---

### Post by Techsnap on 2010-01-19
Basically, Debian testing is probably going to be the most stable rolling release you're going to find anyways.

---

### Post by walkerk on 2010-01-19
> **Psumi said:**
> Don't you mean sidux?

[http://en.wikipedia.org/wiki/Sidux](http://en.wikipedia.org/wiki/Sidux)

Besides that, no, there are none that I know of.

sidux rocks. I've been using it for about 2 years now. I got tired of updating every six months and I wanted software as it was released. Every now and then your experience a snag but some Linux know how will provide a work around until a fix is released by the sidux team. The latest was the new release of Xorg... HAL now handles input devices while your xorg.conf only configures your video...

---

### Post by Techsnap on 2010-01-19
> **walkerk said:**
> sidux rocks. I've been using it for about 2 years now...

Does anyone read the OP before posting?

---

### Post by Hallvor on 2010-01-19
> **Techsnap said:**
> Basically, Debian testing is probably going to be the most stable rolling release you're going to find anyways.

If you know what you are doing it should work very well. If you don`t, expect problems.

If you want an *easy* rolling release distro with Gnome, perhaps this is a better one, though not based on Debian: [http://linuxgator.org/home/index.html](http://linuxgator.org/home/index.html)

---

### Post by Skripka on 2010-01-19
> **Techsnap said:**
> Basically, Debian testing is probably going to be the most stable rolling release you're going to find anyways.

Meh.  Rolling releases are just that, sooner or later you need brains to fix something.  There isn't much of a hierarchy of "stable" in rolling releases.

---

### Post by walkerk on 2010-01-19
> **Techsnap said:**
> Does anyone read the OP before posting?

Merely showing my support for sidux. Show me a rolling release distro that does not have security/stability issues and I'll shut up. Until then, keep your unfriendly comments to yourself. Thanks :)

---

### Post by llawwehttam on 2010-01-19
> **Skripka said:**
> Meh.  Rolling releases are just that, sooner or later you need brains to fix something.  There isn't much of a hierarchy of "stable" in rolling releases.

I agree. Personally I like ARCH .

---

### Post by Psumi on 2010-01-19
> **llawwehttam said:**
> I agree. Personally I like ARCH .

One that's easy to use and set up as well, Arch does not fit that description, but it's what you like.

---

### Post by Ginsly on 2010-01-19
> **Hallvor said:**
> If you know what you are doing it should work very well. If you don`t, expect problems.

If you want an *easy* rolling release distro with Gnome, perhaps this is a better one: [http://linuxgator.org/home/index.html](http://linuxgator.org/home/index.html)

? Testing is pretty stable. I would hardly describe myself as a Linux genius, and I've been using testing for around a year now with no problems. If you've been practicing with Ubuntu for a while, you should be fine. The only time there is much of an issue is during the freeze period, so many people advise changing back to the release name (squeeze for this release) until testing is released as stable, and testing is unfrozen again and doing a "dist-upgrade" back to testing.... 

I haven't experienced a freeze period yet, so I can't comment on how this period will be for you, but i have done dist-upgrades from stable to testing, and testing to unstable before, without much issue but you will have to make up your own mind about that!!

Just be aware that in your /etc/apt/sources.list, you will need to make sure you have "testing" rather than "squeeze" for it to be a "rolling" distro. Otherwise you will just stay with the same branch when testing goes stable.

Good luck :D

---

### Post by kerry_s on 2010-01-19
debian testing is great, i've got a laptop that has been using it for 4 years.

also you should not confine yourself to just debian, like the others said arch is a rolling release as well.

---

### Post by ~sHyLoCk~ on 2010-01-19
> **walkerk said:**
> Merely showing my support for sidux. Show me a rolling release distro that does not have security/stability issues and I'll shut up. Until then, keep your unfriendly comments to yourself. Thanks :)

Slackware -current and Gentoo stable.

---

### Post by Xbehave on 2010-01-19
sidux (sid + a few packages for easy installation)
debian sid
debian testing (it does go through feature freezes so not rolling 100% of the time)
MEPIS (well sort of it has a rolling release app repo, over a stable base)
Ubuntu

Personally i would go with sid/sidux, but i've also heard good things about MEPIS (they recently released 8.0.15 and 8.5 is in beta4)

> **~sHyLoCk~ said:**
> Slackware -current and Gentoo stable.
Holly ignoring the topic batman! :O

---

### Post by Uncle Spellbinder on 2010-01-19
Ubuntu can be made into a "rolling release" of sorts. Adding some PPA's and other Ubuntu compatible repos to your sources.list makes it as close to a rolling release as you'll get with an Ubuntu install anyway.

---

### Post by kellemes on 2010-01-19
> **BrokenKingpin said:**
> I am looking for a rolling release distro based on Debian.

Debian Testing..

---

### Post by Frak on 2010-01-19
> **Psumi said:**
> Don't you mean sidux?

[http://en.wikipedia.org/wiki/Sidux](http://en.wikipedia.org/wiki/Sidux)

Besides that, no, there are none that I know of.
No, he means Debian Testing.

---

### Post by Eisenwinter on 2010-01-19
> **Psumi said:**
> One that's easy to use and set up as well, Arch does not fit that description, but it's what you like.
Arch can be very easily installed. Given a good connection, I could set up a stable Arch system with X, a window manager, and all my needed programs within 30 minutes.

You just follow the linear installation process, and read the wiki if you enouncter something you don't understand.

---

### Post by Techsnap on 2010-01-19
Enough with the Arch! The OP specified Debian based. Seems most threads now are always steered into Arch.

---

### Post by Eisenwinter on 2010-01-19
> **Techsnap said:**
> Enough with the Arch! The OP specified Debian based. Seems most threads now are always steered into Arch.
That's because Arch is god. All people who use Arch treat it like their god. I believe in Arch.

I take minimalism to an extreme, not just with computers. My apartment is minimalistic too!

---

### Post by Techsnap on 2010-01-19
I'll say it now so everyone who cares a damn [and who have really had it with the Arch love in] is aware. As much as people know I dislike Ubuntu, Arch is higher on the crap list than Ubuntu for me :).

---

### Post by Eisenwinter on 2010-01-19
> **Techsnap said:**
> I'll say it now so everyone who cares a damn [and who have really had it with the Arch love in] is aware. As much as people know I dislike Ubuntu, Arch is higher on the crap list than Ubuntu for me :).
Now I must insult you, because you insulted my god, which is Arch.

---

### Post by Skripka on 2010-01-19
> **Eisenwinter said:**
> Now I must insult you, because you insulted my god, which is Arch.

Flamewar!!!!

---

### Post by Xbehave on 2010-01-19
Seriously this is why nobody likes Arch users (with the exception of handy), you fill all threads with arch spam, the guy asked about a **[SIZE="5"]debian[/SIZE]** based Rolling Release.

If it wasn't for all your spam OP might see the sensible posts regarding **[SIZE="5"]debian[/SIZE]** based Rolling Releases (debian & MEPIS(ish)).

p.s i see Skripka is being as useful as ever.

---

### Post by Psumi on 2010-01-19
> **Eisenwinter said:**
> Now I must insult you, because you insulted my god, which is Arch.

*sigh* Can't we just have a peaceful conversation without going to this?

---

### Post by Icehuck on 2010-01-19
> **Eisenwinter said:**
> 
I take minimalism to an extreme, not just with computers. My apartment is minimalistic too!

This made me LOL!

---

### Post by Skripka on 2010-01-19
> **Psumi said:**
> *sigh* Can't we just have a peaceful conversation without going to this?

Evidently not.  At least folks aren't pulling rulers out and measuring their.....yet....

---

### Post by Techsnap on 2010-01-19
Thanks to the OP for starting this thread, this thread has convinced me to install Debian Testing. The weekly images weren't there so I had to install Debian Lenny from the net install and then run an upgrade to testing after changing sources.

One thing though, it wouldn't create a lilo.conf properly so I had to do it by hand [Won't use GRUB I Can't stand it]. Apart from that I'm very impressed, it's installing KDE as we speak.

---

### Post by Uncle Spellbinder on 2010-01-19
> **Xbehave said:**
> Seriously this is why nobody likes Arch users (with the exception of handy), you fill all threads with arch spam, the guy asked about a **[SIZE="5"]debian[/SIZE]** based Rolling Release.

If it wasn't for all your spam OP might see the sensible posts regarding **[SIZE="5"]debian[/SIZE]** based Rolling Releases (debian & MEPIS(ish)).
+1

I personally have absolutely nothing against Arch. But when the topic of the thread is DEBIAN BASED rolling distros, Arch has no business being mentioned at all.

I have to admit that many Arch users seem like Evangelical Christians. They just HAVE to push their view on anyone and everyone. This is an UBUNTU forum.

---

### Post by Techsnap on 2010-01-19
> I have to admit that many Arch users seem like Evangelical Christians. They just HAVE to push their view on anyone and everyone.

I've found they're becoming more prevalent than new Ubuntu users getting it all wrong.

Also I've now got Debian testing all up and running with KDE and I'm really impressed, it's certainly a change from Slackware and I've had to screw around with APT a bit to get it to ignore some dependencies I Know I don't need but it's a nice OS.

---

### Post by kerry_s on 2010-01-19
> **Techsnap said:**
> Thanks to the OP for starting this thread, this thread has convinced me to install Debian Testing. The weekly images weren't there so I had to install Debian Lenny from the net install and then run an upgrade to testing after changing sources.

One thing though, it wouldn't create a lilo.conf properly so I had to do it by hand [Won't use GRUB I Can't stand it]. Apart from that I'm very impressed, it's installing KDE as we speak.

with the net installer select expert install, then you'll get the option to choose testing as your install, you'll also get other options, like having a sudo system instead of root.

---

### Post by Techsnap on 2010-01-19
Thanks for the tip, but it's already up and running, I'll do that next time I install it though. 

> having a sudo system instead of root.

No thanks, can't stand sudo

---

### Post by kerry_s on 2010-01-19
> **Techsnap said:**
> Thanks for the tip, but it's already up and running, I'll do that next time I install it though. 



No thanks, can't stand sudo

:lolflag:

by the way, heres the testing images:
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/)

---

### Post by Techsnap on 2010-01-19
Heh, they weren't there a few hours ago.

---

### Post by BrokenKingpin on 2010-01-19
I think I will give Debian Testing a try. Thanks for all the input.

---

### Post by gn2 on 2010-01-19
Once you have a separate /home partition changing to a new version of Ubuntu is very simple and only takes minutes.
It's certainly no hardship.
"Rolling release" is a solution looking for a problem.

---

### Post by RiceMonster on 2010-01-19
> **gn2 said:**
> Once you have a separate /home partition changing to a new version of Ubuntu is very simple and only takes minutes.
It's certainly no hardship.
"Rolling release" is a solution looking for a problem.

But then you have to wait 6 months for new versions of software to be added to the repos. Yes, they are ways of getting newer versions, but rolling release makes it more convenient.

---

### Post by Skripka on 2010-01-19
> **RiceMonster said:**
> But then you have to wait 6 months for new versions of software to be added to the repos. Yes, they are ways of getting newer versions, but rolling release makes it more convenient.

And odds are it will run better, as new software is tested against new software-not 6 month old software.

---

### Post by Rhapsody on 2010-01-19
I'm using Debian testing (with some packages from unstable and experimental) myself, and I'm liking it a hell of a lot. It seems to be the perfect sweet spot between cutting edge and outdated. You get just enough of a buffer zone to avoid critical bugs from brand-new packages, which is all I want or need.

As for the lack of security team support, I wouldn't worry about it. The security in stable comes from backporting fixes to old packages, but the security in testing/sid comes from simply using the newest packages, which have the latest security fixes anyway. It's still a good idea to subscribe to the [debian-security-announce mailing list](http://lists.debian.org/debian-security-announce/) though, to keep yourself informed about what security exploits there are and what versions are affected.

It's also worth looking at the possibility of setting up a [mixed testing/unstable system](http://forums.debian.net/viewtopic.php?f=16&t=15612). It sounded mad to me when it was first suggested, but I'm using it right now and it works perfectly. It gives you the advantage of being able to upgrade certain packages to unstable ([or even experimental](http://wiki.debian.org/DebianExperimental)) while keeping most of the system at testing. It's a bit more of an advanced thing than using a plain testing system, but has its advantages.

---

### Post by Eclipse. on 2010-01-19
Debian unstable.

Get it from either installing testing then upgrading or installing sidux which is unstable on a cd.

---

### Post by phrostbyte on 2010-01-19
> **Uncle Spellbinder said:**
> Ubuntu can be made into a "rolling release" of sorts. Adding some PPA's and other Ubuntu compatible repos to your sources.list makes it as close to a rolling release as you'll get with an Ubuntu install anyway.

Also, ubuntu+1 (currently Lucid) is like a "rolling release" :D Complete with almost guaranteed breakage.

---

### Post by phrostbyte on 2010-01-19
> **Skripka said:**
> And odds are it will run better, as new software is tested against new software-not 6 month old software.

Personally I'd like a system where user facing applications (if possible) are rolling release, and the kernel/X.org and various low level libraries and daemons are only upgraded on a new release. Best of both worlds IMO.

The most absurd thing is Ubuntu lagging Firefox releases. If just THAT could be fixed, it would be a big improvement.

---

### Post by Techsnap on 2010-01-19
> Personally I'd like a system where user facing applications (if possible) are rolling release, and the kernel/X.org and various low level libraries and daemons are only upgraded on a new release. Best of both worlds IMO.

I suppose you could use OpenSUSE + OpenSUSE Build Service repos, I guess this would be the best way since they're upstream packages in there usually.

---

### Post by Eclipse. on 2010-01-19
> **phrostbyte said:**
> Also, ubuntu+1 (currently Lucid) is like a "rolling release" :D Complete with almost guaranteed breakage.

Sorta but not really since it will begin to freeze up soon.Rolling releases never go through stabilisation periods.

---

### Post by Techsnap on 2010-01-19
> Sorta but not really since it will begin to freeze up soon.Rolling releases never go through stabilisation periods.

Slackware -current and Debian testing do in a roundabout way, between the new "stable" version being released and then the new testing applications hitting the package trees. Though it's not a long time, you can jump off into Stable if you get what I mean.

---

### Post by Xbehave on 2010-01-19
> **phrostbyte said:**
> Personally I'd like a system where user facing applications (if possible) are rolling release, and the kernel/X.org and various low level libraries and daemons are only upgraded on a new release. Best of both worlds IMO.

The most absurd thing is Ubuntu lagging Firefox releases. If just THAT could be fixed, it would be a big improvement.
I think that is what MEPIS offers.

---

### Post by Skripka on 2010-01-19
> **phrostbyte said:**
> Personally I'd like a system where user facing applications (if possible) are rolling release, and the kernel/X.org and various low level libraries and daemons are only upgraded on a new release. Best of both worlds IMO.


Meh, the older the kernel+Xorg etc the more likely you are to have issues with newer/brand new user apps/plugins etc.

O'er on the Opera boards, there was a guy a week or so ago who seemed astonished that Opera 10, Moonlight 2, and 8.04 Hardy Heron did not seem to get along at all....Granted this is an extreme case with 2 year old kernel+Xorg+etc and brand new software, but it demonstrates the point.

Methinks for best results with brand new software, you're best off running it in an environment as identical as possible to that environment which it was written for.  Most of the time, that is new software running on new software IME.

---

### Post by Uncle Spellbinder on 2010-01-19
> **phrostbyte said:**
> ...The most absurd thing is Ubuntu lagging Firefox releases. If just THAT could be fixed, it would be a big improvement.> **Xbehave said:**
> I think that is what MEPIS offers.

So does the Ubuntuzilla repo. The most current stable releases of Firefox, Thunderbird and SeaMonkey. 

If all someone wants are several apps to always be up-to-date, then there are PPA repos and official repos for that. I've never been without the most current versions of all my important apps on any version of Ubuntu.

---

### Post by Xbehave on 2010-01-19
> **Skripka said:**
> Granted this is an extreme case with 2 year old kernel+Xorg+etc and brand new software, but it demonstrates the point.
Actually Xorg and the Kernel have a very stable API, its usually the libraries that cause problems.

---

### Post by Dharmachakra on 2010-01-19
> **Uncle Spellbinder said:**
> So does the Ubuntuzilla repo. The most current stable releases of Firefox, Thunderbird and SeaMonkey. 


If you're trying to stay away from Debian itself, this is probably the best solution. I still would recommended that you at least try Debian Testing. There's plenty of documentation to get it set up as well. 

I don't think SimplyMEPIS offers very up-to-date packages. I remember noticing that the packages were a few packages behind Ubuntu when I gave it a test run.

---

### Post by Techsnap on 2010-01-19
> I don't think SimplyMEPIS offers very up-to-date packages. I remember noticing that the packages were a few packages behind Ubuntu when I gave it a test run.

Yep, I agree, same experience last time I tried Mepis. Mepis is a good distro though anyways.

---

### Post by Techsnap on 2010-01-20
Right, it's all up and running now and I have to say I'm VERY Impressed with the standards of the packages and generally how everything is running. Debian has definitely improved a great deal since I last used it 5 or 6 years ago.

Just in case anyone is wondering its got 2.6.30 & KDE 4.3.4. I'm using Opera so I'm not sure about Firefox. 

There are still no weekly builds for Debian Testing on the Debian site for some reason. The ones which are there are for sid which I don't want to run on this system but anyhow here's my recommended path for upgrading from Lenny to Testing:

1. Download the Debian Lenny Net install.
2. Perform a Standard system install. 
3. Boot into it and change the /etc/apt/sources.lst changing lenny to either testing or squeeze. If you choose to use squeeze you will automatically leave the testing branch when squeeze is released. 
4. Run the following (as root):

```
aptitude update && aptitude install aptitude apt dpkg linux-image-2.6 && reboot
```

5. Boot into the newest kernel and run this:

```
aptitude dist-upgrade && reboot
```

The reason you must upgrade and boot the new Kernel first is because udev will give you errors if you do not.

**If you don't use KDE never mind about this:**

```
aptitude install kdebase kdelibs kdeutils xorg alsa-utils
```

This method DOES install KDM so you can either reboot or run startx as a **normal user** after installing using the above command.

Again thanks to the OP for creating this thread and inspiring me to try Debian again, I'm very impressed with it so far. It's a lot different to Slackware but the main thing is packaging differences which are easy to work around. APT Is a heck of a lot slower than what I'm used to but who cares as long as the system works properly.

---

### Post by Zoot7 on 2010-01-20
Debian "Testing" or Debian "Unstable" are the ones I'd recommend. They're both truly rolling, and despite their names, are for the most part fairly solid. (at least in my experience)
"Squeeze" is another one to consider, but that wouldn't be rolling per se, as it goes through several feature freezes and ultimately transitions to the Stable release.

I've always preferred Debian's more conservative way of doing things than Ubuntu's, for instance you won't find an installation of Pulseaudio in Debian, you can install it, mind you but it's not forced upon you. Also if you decide you don't want Gnome around at all you can remove it entirely (I don't think you can do this with Ubuntu).
Debian has a lot more going for it in terms of installation options too, for instance you can install the whole shebang including a Desktop like you do with Ubuntu, or you can just install the base system and add to it in bits and pieces like you do with Arch.

---

### Post by Techsnap on 2010-01-20
> Also if you decide you don't want Gnome around at all you can remove it entirely

Or better yet you don't have to install Gnome at all :)

---

### Post by ~sHyLoCk~ on 2010-01-20
> **Techsnap said:**
> Or better yet you don't have to install Gnome at all :)

True. Use netinst. ;)

---

### Post by Zoot7 on 2010-01-20
> **Techsnap said:**
> Or better yet you don't have to install Gnome at all :)
Haha, that be what I should have said. :tongue:

---

### Post by kevCast on 2010-01-20
> **Techsnap said:**
> There are still no weekly builds for Debian Testing on the Debian site for some reason.

[http://www.debian.org/devel/debian-installer/]("http://www.debian.org/devel/debian-installer/")

---

### Post by Techsnap on 2010-01-20
[http://cdimage.debian.org/cdimage/weekly-builds/](http://cdimage.debian.org/cdimage/weekly-builds/) 

No builds. I had to use the Lenny net install and update it to Testing using what I posted [Above](http://ubuntuforums.org/showpost.php?p=8694834&postcount=55).

> [http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

Wouldn't these be sid?

---

### Post by kevCast on 2010-01-20
> **Techsnap said:**
> [http://cdimage.debian.org/cdimage/weekly-builds/](http://cdimage.debian.org/cdimage/weekly-builds/) 

No builds. I had to use the Lenny net install and update it to Testing using what I posted [Above](http://ubuntuforums.org/showpost.php?p=8694834&postcount=55).



Wouldn't these be sid?

No. Debian doesn't provide sid .isos. You'd have to change your /etc/apt/sources.list to run it.

---

### Post by Techsnap on 2010-01-20
Ah right, Thanks for clearing that up.

---

### Post by kevCast on 2010-01-20
> **Techsnap said:**
> Ah right, Thanks for clearing that up.

No worries, glad to help a Slacker. ;)

---

### Post by ~sHyLoCk~ on 2010-01-20
Omg so many slackers suddenly! :O

---

### Post by Techsnap on 2010-01-21
Well that was a lot of fun using Debian, I really liked how much more stable it was  than Ubuntu and how it was a lot lighter than I thought (It totally wiped the floor with Arch). Anyways it's back to Slackware now, not because Debian broke, but because of familiarity, it's always best to use what you're most confident with I believe. Debian will be taking a permanent residence in VirtualBox replacing the Arch VM I had there.

---

### Post by Nerd King on 2010-01-21
Debian's actually pretty cool when you go from netinst. I'm currently knocking around a few distros to create something light so currently i'm fiddling with arch and debian, and downloading slack to see what I can do. Seriously though, I love building from netinst, the knowledge that it's yours, custom-built, to your specs. Nothing beats it.

---

### Post by Techsnap on 2010-01-21
>  I love building from netinst, the knowledge that it's yours, custom-built, to your specs.

Absolutely agree.

---

### Post by ~sHyLoCk~ on 2010-01-21
> **Xbehave said:**
> 
Holly ignoring the topic batman! :O

I mostly ignore your useless posts and I did this time as well but I thought I should make an effort to clarify your doubts. My post that you quoted was for the person I had quoted while replying. He asked for a stable rolling distro and **not specified debian-based** as he claimed all rolling release distros are unstable! I wasn't replying to the OP which should be pretty obvious since I had quoted the person above me while replying. See let me explain further, when you quote someone and then reply you are actually replying him and not the OP. *phew*  this is the last time I swear I'll explain things to you. :D

---

### Post by snowpine on 2010-01-21
By the way, all you Debian noobs should check out the smxi script from smxi.org. It is a very easy way to keep your system up to date, as well as install useful stuff.

---

### Post by Skripka on 2010-01-21
> **~sHyLoCk~ said:**
> I mostly ignore your useless posts and I did this time as well but I thought I should make an effort to clarify your doubts. My post that you quoted was for the person I had quoted while replying. He asked for a stable rolling distro and **not specified debian-based** as he claimed all rolling release distros are unstable!

I'd check the thread header, and then hit the edit button.  And fast if I was you.

---

### Post by ~sHyLoCk~ on 2010-01-21
> **Skripka said:**
> I'd check the thread header, and then hit the edit button.  And fast if I was you.

why?

---

### Post by Techsnap on 2010-01-21
That and I don't know how many times me and others have pointed out that is says DEBIAN based.

---

### Post by ~sHyLoCk~ on 2010-01-21
Where does it in this post says Debian based?

> **walkerk said:**
> Merely showing my support for sidux. Show me **a rolling release distro** that does not have security/stability issues and I'll shut up. Until then, keep your unfriendly comments to yourself. Thanks :)

---

### Post by Skripka on 2010-01-21
> **~sHyLoCk~ said:**
> why?

Post hoc, ergo propter hoc.

---

### Post by Techsnap on 2010-01-21
Learn to read:

> I am looking for a rolling release distro based on Debian.

FIRST LINE FIRST POST!

---

### Post by Skripka on 2010-01-21
> **Techsnap said:**
> Learn to read:



FIRST LINE FIRST POST!

Ding ding ding.  We have a winnar.

---

### Post by ~sHyLoCk~ on 2010-01-21
> **Techsnap said:**
> Learn to read:



FIRST LINE FIRST POST!

As I said I was replying to walkerk and not the OP. Even though the OP was talking about Debian based, my reply was for walkerk that rolling release stable distros do exist. Stop repeating the same thing over and over again. Come out of the infinite loop. :) exit 1.

---

### Post by Techsnap on 2010-01-21
It's still not answering the question of the OP, perhaps you should have made a Sidux thread. It's not just you it's other people as well.

---

### Post by ~sHyLoCk~ on 2010-01-21
> **Techsnap said:**
> It's still not answering the question of the OP, perhaps you should have made a Sidux thread. It's not just you it's other people as well.

I did not intend to answer the OP's question. I answered the person whom I quoted. Do you guys not understand the concept of "quoting"? See I'm quoting and replying, to you and not to skripka or handy! :P

---

### Post by MaxIBoy on 2010-01-21
Debian Testing is good. Seemed to work OK for the 30 seconds I ran on it between upgrading from Lenny and upgrading to Sid after two different fresh installs. (Seriously though, I have used it extensively and it's a great distro. I was just impatient to get Xinput 2 as soon as possible.)

These days, I use Debian Unstable with the Experimental repositories enabled, because that's... how I roll. (Ba-dum Tish!)

Or you can try Sidux, it's a stabilized rolling release based on (and kept mostly in sync with) Debian Unstable. Haven't tried it myself, so I can't really recommend it. But that might be what works for you.

---

### Post by Techsnap on 2010-01-21
Yes, I just reloaded Debian testing and installed XFCE.

---

### Post by snowpine on 2010-01-21
Sidux and Arch are really the two main contenders for "best rolling release distro for former Ubuntu users." (IMHO) Sidux is great because it's a ready-to-go Live CD, you just pop it in and you have a full Sidux install in less than 15 minutes. Because Ubuntu is based on Debian Sid, Sidux is a great "preview" of what future Xubuntu/Kubuntu releases might be like. (No Gnome at the present time.) It is also easy for Ubuntu users because, being Debian based (as per the OP) it uses apt package management. Arch (as you know) is more roll-your-own (but don't let that intimidate you; it is an easy and fun weekend project for anyone with a DIY mindset). Because Arch is "desktop agnostic" you can easily install Gnome to make it look like Ubuntu. The "drawback", of course, is that it's not Debian-based. In my opinion this is not a bad thing from a stability point of view: Debian Sid/Testing is very much geared towards testing new features for the next Debian Stable release as its end goal, whereas Arch isn't testing for anything and is designed to be "stable" (in the "usable and reasonably bug free" sense of the word) as-is. Debian (especially Testing) also has a tendency to be "cyclical" in the sense that it freezes for a while prior to a Stable release, then gets really exciting for a while afterwards.

Either way, rolling releases have their own challenges, for sure. Really it's just a question of how you prefer to divvy up your system maintenence: a little bit each week (rolling release) or a lot every 6 months (time based release).

---

### Post by kevCast on 2010-01-21
The big problem/one of the great things about Debian is its policy. It's the reason my wireless doesn't work in testing, why they don't have python 2.6, and why the rest of it is so cohesive and awesome.

---

### Post by eric71 on 2010-01-28
There's two Debian testing based distros I've tried in addition to the Debian testing weekly iso itself:

A very Ubuntu-esque distro, Gnome-based using Synaptic is Parsix.

A live cd with installer with either KDE or Xfce versions is PureOS. It has an installer, but there were some quirks related to permissions when I used it, so maybe this one isn't quite ready for production systems.

I also have used the KDE testing isos from Debian. I get a little frustrated because it's very difficult to do some administrator setup things - I can never seem to get graphical apps to run as su from terminal. It makes it harder to update sources.list, access external drives, etc.

As other people have mentioned, Mepis does keep major apps updated even running over a stable Lenny base. And I've found that enabling squeeze repos to install a few packages and then hashing them out again can solve the situations where newer things aren't in Mepis' repository.

I've been on a bit of a quest for an up to date rolling distro, and have been bouncing between many. Chakra will be nice when it is a little more mature, but I keep being drawn back to Debian and trusty Synaptic.

---

### Post by amarendra on 2010-02-20
[deleted] --

---

### Post by amarendra on 2010-02-20
How can that be done? How to make Ubuntu almost a rolling-release?

---

### Post by Tibuda on 2010-02-20
> **amarendra said:**
> How can that be done? How to make Ubuntu almost a rolling-release?

You can always use the development version (lucid right now). You'll have to change your sources.list every 6 months.

---

### Post by swoll1980 on 2010-02-20
> **llawwehttam said:**
> I agree. Personally I like ARCH .

Didn't realize Arch was based off Debian, or was that just your way of trying to squeeze Arch into every single thread?

---

### Post by TeemuN on 2010-04-18
I noticed that in Debian testing the firefox [version is still 3.5]("http://packages.debian.org/squeeze/iceweasel") (also in sid) but in Ubuntu 9.10 the version is 3.6.3 if you install from [launchpad repos.]("https://launchpad.net/%7Emozillateam") Is there a reason to keep this older version or are developers just busy? 

This really makes no sense to me as I was thinking to change from Ubuntu to Debian only for more recent versions of software and this doesn't seem very "rolling" to me. Also I want to install sofware from repos, not to lurk billion web pages for newer .debs.

---

### Post by snowpine on 2010-04-18
> **TeemuN said:**
> I noticed that in Debian testing the firefox [version is still 3.5]("http://packages.debian.org/squeeze/iceweasel") (also in sid) but in Ubuntu 9.10 the version is 3.6.3 if you install from [launchpad repos.]("https://launchpad.net/%7Emozillateam") Is there a reason to keep this older version or are developers just busy? 

This really makes no sense to me as I was thinking to change from Ubuntu to Debian only for more recent versions of software and this doesn't seem very "rolling" to me. Also I want to install sofware from repos, not to lurk billion web pages for newer .debs.

Debian has more of an emphasis on stability than Ubuntu; contrary to popular belief, packages are tested before they go into Sid and it isn't really a "bleeding edge" distro at all. Many packages in Ubuntu are newer than even the "unstable" branch of Debian (I consider this a bad thing; Ubuntu is somewhat notorious for rushing buggy software into "stable" releases).

Sid is currently in a fairly stable state; a lot of big changes (Iceweasel 3.6 and KDE 4.4 come to mind) are being held back because the Debian team is focused on then next stable release (Squeeze). Once Squeeze comes out later this year, there will be a big flood of new packages into Sid and eventually Testing, and things will be pretty exciting for a while. :)

Are you sure you really need a "rolling release"? In my experience, many users who *think* they need rolling release really just want a stable distro with the newest Firefox, OpenOffice, etc. (which is really easy to achieve with any distro).

---

### Post by Laxman_prodigy on 2010-04-18
> **snowpine said:**
> Debian has more of an emphasis on stability than Ubuntu; contrary to popular belief, packages are tested before they go into Sid and it isn't really a "bleeding edge" distro at all. Many packages in Ubuntu are newer than even the "unstable" branch of Debian (I consider this a bad thing; Ubuntu is somewhat notorious for rushing buggy software into "stable" releases).

Sid is currently in a fairly stable state; a lot of big changes (Iceweasel 3.6 and KDE 4.4 come to mind) are being held back because the Debian team is focused on then next stable release (Squeeze). Once Squeeze comes out later this year, there will be a big flood of new packages into Sid and eventually Testing, and things will be pretty exciting for a while. :)

Are you sure you really need a "rolling release"? In my experience, many users who *think* they need rolling release really just want a stable distro with the newest Firefox, OpenOffice, etc. (which is really easy to achieve with any distro).

Will Debian Squeeze be released late this year?

---

### Post by snowpine on 2010-04-18
> **Laxman_prodigy said:**
> Will Debian Squeeze be released late this year?

Debian does not have fixed release dates. It's ready when it's ready.

---

### Post by Laxman_prodigy on 2010-04-18
> **snowpine said:**
> Debian does not have fixed release dates. It's ready when it's ready.


I wonder what would happen to all those Debian-based distros if Debian wasn't there working hard?:lolflag:

---

### Post by TeemuN on 2010-04-18
> **snowpine said:**
> Debian has more of an emphasis on stability than Ubuntu; contrary to popular belief, packages are tested before they go into Sid and it isn't really a "bleeding edge" distro at all. Many packages in Ubuntu are newer than even the "unstable" branch of Debian (I consider this a bad thing; Ubuntu is somewhat notorious for rushing buggy software into "stable" releases).

Sid is currently in a fairly stable state; a lot of big changes (Iceweasel 3.6 and KDE 4.4 come to mind) are being held back because the Debian team is focused on then next stable release (Squeeze). Once Squeeze comes out later this year, there will be a big flood of new packages into Sid and eventually Testing, and things will be pretty exciting for a while. :)

Are you sure you really need a "rolling release"? In my experience, many users who *think* they need rolling release really just want a stable distro with the newest Firefox, OpenOffice, etc. (which is really easy to achieve with any distro).

Well, that makes sense, thank you. The Debian installation would have become mainly for testing (at least at first) and for trying to build system from scratch without programs that I don't even know of. Ubuntu and a couple of ppa:s work very well for me.

---

### Post by renkinjutsu on 2010-04-18
> **TeemuN said:**
> I noticed that in Debian testing the firefox [version is still 3.5]("http://packages.debian.org/squeeze/iceweasel") (also in sid) but in Ubuntu 9.10 the version is 3.6.3 if you install from [launchpad repos.]("https://launchpad.net/%7Emozillateam") Is there a reason to keep this older version or are developers just busy? 

This really makes no sense to me as I was thinking to change from Ubuntu to Debian only for more recent versions of software and this doesn't seem very "rolling" to me. Also I want to install sofware from repos, not to lurk billion web pages for newer .debs.

You can also add ubuntu PPA's to your debian sources.list.. i've done this without any harmful effects.

---

### Post by kevCast on 2010-04-18
> **TeemuN said:**
> I noticed that in Debian testing the firefox [version is still 3.5]("http://packages.debian.org/squeeze/iceweasel") (also in sid) but in Ubuntu 9.10 the version is 3.6.3 if you install from [launchpad repos.]("https://launchpad.net/%7Emozillateam") Is there a reason to keep this older version or are developers just busy? 

This really makes no sense to me as I was thinking to change from Ubuntu to Debian only for more recent versions of software and this doesn't seem very "rolling" to me. Also I want to install sofware from repos, not to lurk billion web pages for newer .debs.

You could pull Iceweasel from experimental, although I wouldn't advise it. On my sid install, I normally just pull the latest stable firefox and xulrunner from mercurial and build them myself. That way I don't have the whole Iceweasel thing, and I get updates in a timely manner. Plus I needed xulrunner for conkeror. I'd stay far away from untrusted .debs from the internet.

[https://developer.mozilla.org/en/Build_Documentation]("https://developer.mozilla.org/en/Build_Documentation")
[https://developer.mozilla.org/En/Simple_Firefox_build]("https://developer.mozilla.org/En/Simple_Firefox_build")
[http://markshroyer.com/blog/2009/07/firefox-35-debian-amd64.html]("http://markshroyer.com/blog/2009/07/firefox-35-debian-amd64.html")

---

### Post by L_V on 2011-05-29
[_Debian is Working on a Rolling Version of their Distro_]("http://lxnews.org/2011/03/21/debian-working-on-rolling-version/")

[_Unofficial Debian Monthly Testing Snapshot Release (version 2011.03 final)_]("http://lists.debian.org/debian-devel/2011/03/msg00347.html")

---

### Post by Artemis3 on 2011-05-29
Debian could have solved the "always obsolete" issue by implementing PPAs. Backports, unfortunately, most of the time don't have what you need when you need, and the Unstable/Testing branches can break from time to time.

We should see if this is any better than using unstable+experimental...

ubuntu minimal + ppa also does a fine job.

Adding Ubuntu PPAs to Debian? Only for experts, it involves the same risks of using Ubuntu repositories in a Debian install, it can break havoc, ie, not a recommended...

But if Debian had its own official PPA server, and anything there self-compiled against stable, it would make a worlds difference.

---

### Post by BrokenKingpin on 2011-05-30
I was running the Linux Mint Debian Edition, but a recent update broke my system... so back to Ubuntu for now.

---

