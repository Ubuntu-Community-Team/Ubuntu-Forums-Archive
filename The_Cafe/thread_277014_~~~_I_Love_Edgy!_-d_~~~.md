---
title: "~~~ I Love Edgy! :-d ~~~"
date: 2006-10-13
forum: The Cafe
---

### Post by unlokia on 2006-10-13
Hello all!.

I would simply like to say that I have never been a great Gnome fan - not one bit. I have installed various versions of UBUNTU, over the last 2 years, and almost always I have promptly removed them, due to my disliking the general appearance and behaviour.

Until now!.

Edgy Eft beta - I downloaded the CD iso last night, and I have to be honest - beforehand I had watched a talk on [http://video.google.com](http://video.google.com) about the upcoming release, and it just jumped out and bit me as a fabulous distro. In fact, so much so that I have FINALLY said my goodbyes to Windoze XP, and did a:

[COLOR="Red"]```
matt@matt-laptop:~$ dd if=/dev/zero of=/dev/hda bs=512 count=1
```

**Now I would THOROUGHLY discourage *YOU* trying the above code**[/COLOR], unless you wanna say bye bye to your whole hdd - what this does is to erase the MBR and partition table and fill it with zeros - not ideal unless you're SURE you want to wipe it!.

Anyhow (digressing aside) I have killed off the XP beastie, and replaced a dual-boot XP+Mandriva with a whole bundle of Edgy goodness :D :D.

VERY impressed with the distro so far - only one point - when I allowed it to install updates, WHY does it download them at a measly 32kbps when I have 6mb adsl?!. Oh well it was bearable!.

I thoroughly recommend you pointing your browsers to:

[http://releases.ubuntu.com/edgy/ubuntu-6.10-beta-desktop-i386.iso]("http://releases.ubuntu.com/edgy/ubuntu-6.10-beta-desktop-i386.iso")

(that is the ISO for PC (Intel x86) desktop CD)

Try the livecd functionality of the cd first - if you are suitably entertained/impressed, then the very SAME cd allows you to commit to installing the Beta... but as always, this *IS* a beta, and be warned!

I see the kernel/Alsa development is moving on nicely, for FINALLY I now have two distros (this and Mandriva 2007) which give me out-of-the-box sound on my INTEL-HDA sound system.

---

### Post by BoneKracker on 2006-10-14
At the risk of sounding like a premature ejaculator, I second your opinion.

---

### Post by TheMono on 2006-10-14
To speed up your updates, a lot of countries have specific mirrors of the repo's - ie, 

deb [http://nz.archive.ubuntu.com/](http://nz.archive.ubuntu.com/) etc.... If you live in New Zealand...

Just substitute your country code for nz and you should speed up a bit.

---

### Post by aysiu on 2006-10-14
I have to say I'm also very impressed with Edgy. It's lightning fast and a lot stabler than Dapper was in pre-release.

By the way, I've moved this from Absolute Beginner to Ubuntu Cafe. If you've been installing Ubuntu for the past two years, you're hardly a beginner, and this type of thread seems more discussion-oriented than support-oriented.

---

### Post by slimdog360 on 2006-10-14
> **aysiu said:**
> I have to say I'm also very impressed with Edgy. It's lightning fast and a lot stabler than Dapper was in pre-release.

By the way, I've moved this from Absolute Beginner to Ubuntu Cafe. If you've been installing Ubuntu for the past two years, you're hardly a beginner, and this type of thread seems more discussion-oriented than support-oriented.
holy cow, how long have you been a mod. I thought they would have made you a mod ages ago.

---

### Post by punkforpez on 2006-10-14
i upgraded to edgy the other night, so far it's been way more stable than dapper was and i've had no problems!  i even went so far to upgrade my main computer -.-

---

### Post by Reshin on 2006-10-14
Is this normal? When doing sudo aptitude dist-upgrade, first there's dependency problems with python, second it wants to leave some of the packages to current (ie. ubuntu-desktop, ubuntu-minimal, etc). Is it safe to just type y? :???: 

BTW, archive.ubuntu.org was slow as hell. Full upgrade was gonna take 8-11 hours... ](*,)

---

### Post by NeoLithium on 2006-10-14
Well, I just upgraded to edgy now (Running my updates, so I should have everything back up to my pimping style right away.)  Definitely, sign me up; this is outstanding.  First reboot, was quick, runs nice and smooth; plus the new graphics and style are very nice (I have Kubuntu); all I could say when I first took the CD out was WOW.

I had no speed problems when I was updating, like always, my updates were set to Canadian mirrors, and I had outstanding speed.  Count me on being one of the seeders for when the final release is out...

---

### Post by PriceChild on 2006-10-14
> **slimdog360 said:**
> holy cow, how long have you been a mod. I thought they would have made you a mod ages ago.aysiu used to be a mod but stepped down a while back.

With the upcoming release of Edgy, ubuntu-geek decided a few more staff members were needed, and so aysiu was asked to join the team again!

Pricey

---

### Post by BoneKracker on 2006-10-14
good choice

---

### Post by unlokia on 2006-10-14
Exactly when IS the final release of Edgy Eft, due?!

:D

Date please, and not "End of Oct" :mrgreen:

---

### Post by fuscia on 2006-10-14
> **unlokia said:**
> Exactly when IS the final release of Edgy Eft, due?!

:D

Date please, and not "End of Oct" :mrgreen:

oct. 26th, supposedly.

---

### Post by picpak on 2006-10-14
> **Reshin said:**
> Is this normal? When doing sudo aptitude dist-upgrade, first there's dependency problems with python, second it wants to leave some of the packages to current (ie. ubuntu-desktop, ubuntu-minimal, etc). Is it safe to just type y? :???: 

BTW, archive.ubuntu.org was slow as hell. Full upgrade was gonna take 8-11 hours... ](*,)

Um...no, that's not normal. Try running

```
sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
```

and post the output of it.

Also, try using uk.archive.ubuntu.com. It's really fast for me.

---

### Post by unlokia on 2006-10-14
Ahhh cool :D I can't wait!!

---

### Post by Rackerz on 2006-10-14
If your going to use uk.archive.ubuntu.com were do you change the settings so you can make it use the UK servers?

---

### Post by PriceChild on 2006-10-14
> **Rackerz said:**
> If your going to use uk.archive.ubuntu.com were do you change the settings so you can make it use the UK servers?```
sudo nano /etc/apt/sources.list
```and edit appropriately.

26th is the expected release day... it can (and probably will) change.

---

### Post by raublekick on 2006-10-14
i am really excited to install edgy when the floodgates are opened. but i was just thinking: this is really the first time that i felt i didn't really "need" to upgrade to the next release. dapper covers pretty much everything i need now, and if it weren't for the big updates like upstart then i probably wouldn't be excited for edgy at all!

---

### Post by denad on 2006-10-14
Could someone give me the basics about whats so cool about edgy?

---

### Post by unlokia on 2006-10-14
> i am really excited to install edgy when the floodgates are opened. but i was just thinking: this is really the first time that i felt i didn't really "need" to upgrade to the next release. dapper covers pretty much everything i need now, and if it weren't for the big updates like upstart then i probably wouldn't be excited for edgy at all!

Well put it this way dude - it has converted me from a non-ubuntu-ee to an ubuntu-ee overnight!. Try it - backup your install and install Edgy beta if possible, or run inside a Virtual Machine - trust me it is a LOVELY os!!.

As for what it has that is better than previously... I am new to Edgy so I cannot expand on this - just ask about!.

:D

---

### Post by raublekick on 2006-10-15
> **unlokia said:**
> Well put it this way dude - it has converted me from a non-ubuntu-ee to an ubuntu-ee overnight!. Try it - backup your install and install Edgy beta if possible, or run inside a Virtual Machine - trust me it is a LOVELY os!!.

As for what it has that is better than previously... I am new to Edgy so I cannot expand on this - just ask about!.

:D

I've been thinking about installing the beta alongside my Dapper install, but I've also been thinking about all of the burned ISO discs sitting on my desk that I use only once or twice hehe.

---

### Post by chaosgeisterchen on 2006-10-15
> **denad said:**
> Could someone give me the basics about whats so cool about edgy?

Cool facts of edgy are that it's feeling far more stable than Dapper which is intended to be the 'stable' one among the two. And it's lightning fast, a more than only significant speed increase.

---

### Post by dada1958 on 2006-10-15
All good to hear, BUT how many times you can install the OS on different machines? :)

---

### Post by John.Michael.Kane on 2006-10-15
@dada1958 Ubuntu,and All Linux Distro's have no set amount of install times or limits on the amount of machines you can install on.

Enduser has a thousand machines One ubuntu cd will install on all them.

---

### Post by Mr. Picklesworth on 2006-10-15
Yep, Edgy is awesome.

I love Ubuntu's release schedules, too.
It's a huge update including a new version number and a lot of nice cleanups, but it's coming out so soon!
[https://wiki.ubuntu.com/EdgyReleaseSchedule](https://wiki.ubuntu.com/EdgyReleaseSchedule)

Especially wonderful is that, as usual, I don't have to enter a CD key.
...And, I can update from Dapper to Edgy, hardly restarting the computer at all!


Here is that video on Google, btw:
[http://video.google.ca/videoplay?docid=3993036491329342354&q=edgy+eft](http://video.google.ca/videoplay?docid=3993036491329342354&q=edgy+eft)

And a very attractive Compiz video, whose eye candy is superior to two other major eye-candy selling operating systems... just for the heck of it:
[http://video.google.ca/videoplay?docid=8350072959777475145&q=edgy+eft](http://video.google.ca/videoplay?docid=8350072959777475145&q=edgy+eft)
Too bad it's such a low-res video. And that my big old computer is too old to run Compiz :(
There is probably a better one on YouTube...

Edit:
Oh, and, yes, that first video on Google is amazing.
I'd venture to say that Ubuntu is coming to be the most accessible OS out there.
Package descriptions, for example, are apparently automatically translated to your native language :)
(Unfortunately I can't really use that feature often since I speak English)


Edgy - in many fields - defeats the other major operating systems out of the box.

Many subtle improvements since Dapper in terms of default applications, such as a Wiki-ish note-taking application and a new Add/Remove programs system which:
-Automatically gets package descriptions translated to your native language via Rosetta (if only English wasn't my native language :( )
-Has a package ranking feature, which uses statistics gathered from particular machines (your choice, statistic gathering is not on by default) to suggest packages
-Is, as always, just plain awesome

Many graphical enhancements, it's definitely more stable, and other little cool things.
Of course, all the default software is beautifully integrated.


The only thing I found a bit imperfect was the translation thing using Rosetta, but I have strong expectations that it will get better.
I'm hoping in the future that translations could be done entirely in a GUI without having to open a web browser (the amount of stuff required to do it seems a bit intimidating, so it would become a much more powerful tool if anyone could and would use it in 5 minutes).
It would be even more cool if it could fall back to computer translations via Google or some such, which I suspect could actually be done without changing the client code...


It is simply amazing how they managed this.
Not only is Ubuntu practically caught up with Mac OS and Windows, but they've actually got fresh innovation in here!

---

### Post by Koori23 on 2006-10-16
I love Edgy.. It's probably the most fluid Ubuntu Release yet.. Gnome 2.16 was a pretty massive improvement in speed I think. I still can't figure out why they shipped Firefox 2 Beta with it though.. I was kinda hoping to see GnuZilla. Firefox 2 can't seem to get flash sites right, it keeps crashing. 

I really must say congrats though, Edgy is a superb release.

---

### Post by dto on 2006-10-16
> **Koori23 said:**
> Firefox 2 can't seem to get flash sites right, it keeps crashing. 

I was having this problem when someone pointed out that you need X to be running in 24-bit mode instead of 16-bit. I switched and all my Flash problems went away. 8)

---

