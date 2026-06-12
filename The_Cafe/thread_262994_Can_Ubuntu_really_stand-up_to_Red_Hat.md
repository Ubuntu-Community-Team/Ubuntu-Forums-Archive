---
title: "Can Ubuntu really stand-up to Red Hat"
date: 2006-09-22
forum: The Cafe
---

### Post by darkhatter on 2006-09-22
I know whats going to happen, but before the flame war starts. I like you ubuntu I know it has a lot of people using it, but its not even compatible with Red Hat how can it even dream. Suse can't do it and look what they have been doing. What I'm trying to say is why don't we come up with a package manager that lets people use rpm's and deb's together (no converting needed). Cause easy tasks went hard when I went to ubuntu (such as java)

on Red Hat, Suse, Slackware

goto java web site, download linux file, ./java----.bin answer yes, and it installs itself no work on my part. 

on Ubuntu

open firefox, goto ubuntufourms, and cry and ask for help

This is a EXTREME EXAMPLE but there are other things

---

### Post by Lord Illidan on 2006-09-22
Using rpms and deb together??? I guess only smart can do that...lol

---

### Post by darkhatter on 2006-09-22
lol I need to try out smart. But with Slackware I was able to install rpm's and tgz's(slackware package) together and they worked. Sometimes that lead to problems but I was able to fix them.

---

### Post by skymt on 2006-09-22
Java is in Multiverse. Installing it on Ubuntu involves opening your package manager, searching for "java" and picking a few packages. If that's too hard, use Automatix or EasyUbuntu. If that's too hard, well, the Ubuntu developers are working on it. Any of these is easier than your Red Hat example.

By the way, you can install RPMs. Use alien. Or, if you don't mind hosing your system, Red Hat rpm is in Universe.

---

### Post by NESFreak on 2006-09-22
> **darkhatter said:**
> 

goto java web site, download linux file, ./java----.bin answer yes, and it installs itself no work on my part.

on Ubuntu

open firefox, goto ubuntufourms, and cry and ask for help

This is a EXTREME EXAMPLE but there are other things

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

wiki's are easy to use/understand

java is simply in the repro's but you CAN install java the way you say. The instal just isn't as integated as from the repro's but it'll work. Instead of rpm ubuntu uses .deb. Just because you're used to Ret hat that doesn't makes it better.

NESFreak

---

### Post by darkhatter on 2006-09-22
the Java in ubuntu is old I want to run the newer versions from sun.

---

### Post by skymt on 2006-09-22
The JRE in the repos is two minor releases old. A lot of the packages in the repositories are older than that. The versions are what they are because these are the versions the Ubuntu team tested, and they know everything works together. Adding untested software increases the odds of something going wrong.

Also, there's no reason you can't install Java in Ubuntu the same way you did in Fedora. The .bin file will work exactly the same way. So it's an invalid comparison from the start.

---

### Post by darkhatter on 2006-09-22
I never used Red Hat for very long, but one of the reasons I stayed away from Debian (and the 5 billion clones) was its incompatibility with Red Hat. Red Hat is the Linux standard as it stands. I know all about debs, I never liked them but that's just me

---

### Post by teet on 2006-09-22
> **darkhatter said:**
> I never used Red Hat for very long, but one of the reasons I stayed away from Debian (and the 5 billion clones) was its incompatibility with Red Hat. Red Hat is the Linux standard as it stands. I know all about debs, I never liked them but that's just me

Dude, I hope you're joking.

Seriously, you're kidding right?

The whole reason I dropped red hat/fedora core was because of RPM's.  I hate them, plain and simple.  Wait, let me back up.  It's not the RPM format that I hate, it works well enough I suppose.  It the whole "scouring the internet for random files to get the RPM to actually install" part that I actually hate.  Package managers are the way to go, plain and simple. 

It sounds to me like you're just having trouble installing Java.  You knew how to install Java in redhat/fedora, but that method doesn't work in Ubuntu and now you're frustrated.  Take a step back, relax, breathe, and give it another go.  Ubuntu is not Red Hat.  Some things will be different at first.  I highly suggest using automatix or easyubuntu to do all the "common tasks" like installing media players, codecs, java, etc.

-teet

---

### Post by ComplexNumber on 2006-09-22
> It the whole "scouring the internet for random files to get the RPM to actually install" part that I actually hate.from your point of view, how does that differ from debian systems? :confused:

---

### Post by darkhatter on 2006-09-22
I know  sound angry, but its just the Ubuntu team has in a way bastardized Linux. They changed things such as the init system. I know they're trying to make a noob distro but I still find Suse(10.1 has a problem we know what it is), alot easier to work. I know yast is slow, but it gets the job done. With Ubuntu I have to *almost* do as much terminal work as I would with a slackware system, and thats just wrong for a *noob* distro. I love the forums but can't stand the distro is that possible

---

### Post by Demio on 2006-09-22
My last RH experience can be summarized in the following:
1- rpm "insert package here". "package" depends on ....
2- rpm "package1" | "pakacge2".... 

Aaah dependency hell >.< *burn server*.
*Install Debian*
apt-get install apache2.... 
done

*whew*

---

### Post by skymt on 2006-09-22
> **ComplexNumber said:**
> from your point of view, how does that differ from debian systems? :confused:

On Debian systems, everything is already in the repositories, and nothing (usually) conflicts. If there's something not in the repositories that offers a .deb, it will usually install fine. When there isn't even a .deb, the configure-make-checkinstall cycle will make one for you.

Compare that to Red Hat systems, where you have SuSe RPMs, Mandrake RPMs, Fedora RPMs, and a billion other types of RPMs, that all depend on the same packages with different names, and there's no easy way to track everything down. It can take hours. When you factor the relatively small size of Fedora Yum repositories compared to Debian/Ubuntu Apt, well, you get a giant headache.

I've used Fedora. In fact, it was my first Linux. I didn't know what I was missing in Ubuntu, so I assumed the problems with Fedora were common to Linux. I was so wrong. Ubuntu has been almost entirely trouble-free. Everything installs fine.

---

### Post by skymt on 2006-09-22
> **darkhatter said:**
> They changed things such as the init system.

What did they change in the init system? It seems the same as every other sysvinit system I've worked with.

---

### Post by ComplexNumber on 2006-09-22
> **skymt said:**
> On Debian systems, everything is already in the repositories, and nothing (usually) conflicts. If there's something not in the repositories that offers a .deb, it will usually install fine. When there isn't even a .deb, the configure-make-checkinstall cycle will make one for you.

Compare that to Red Hat systems, where you have SuSe RPMs, Mandrake RPMs, Fedora RPMs, and a billion other types of RPMs, that all depend on the same packages with different names, and there's no easy way to track everything down. It can take hours. When you factor the relatively small size of Fedora Yum repositories compared to Debian/Ubuntu Apt, well, you get a giant headache.

I've used Fedora. In fact, it was my first Linux. I didn't know what I was missing in Ubuntu, so I assumed the problems with Fedora were common to Linux. I was so wrong. Ubuntu has been almost entirely trouble-free. Everything installs fine.
there's one thing you've missed out. just like there are are fedora rpm, mandrake rpms, etc......there is exactly the same situation with debian systems. try installing debian debs on ubuntu - it has the exact same ability to break your system on both deb and rpm.
it seems like you're imagining non-existant problems. where is this "giant headache" that you speak of? - i've never encountered it. 
also, i have no idea where you get this idea from:
> When there isn't even a .deb, the configure-make-checkinstall cycle will make one for you.

anyway, the LSB chose rpm over deb as being the superior package manager, so go figure.

---

### Post by teet on 2006-09-22
> **ComplexNumber said:**
> from your point of view, how does that differ from debian systems? :confused:

It doesn't.  I never said that I thought DEB's were superior to RPM's.  

I've run into dependency issues when trying to install *.deb files I've found on the internet.  I said package managers were the way to go.

However, I can usually just use aptitude/synaptic to install any missing dependencies without much problem.  I assume you could do likewise in fedora/redhat with 'yum'.

-teet

---

### Post by ComplexNumber on 2006-09-22
>   I said package managers were the way to go.
thats true. i use smart 100% of the time. i tried synaptic, but it has too many problems and it is incredibly slow compared to Smart.
i've never used the command line to install anything except for demo purposes.

> 
I assume you could do likewise in fedora/redhat with 'yum'.
you can. also, you don't have to use yum. you are free to use apt exactly the same as one uses them on debian systems. although apt for rpm is rumoured to be unmaintained. the future seems to be with yum and rpm.

---

### Post by skymt on 2006-09-23
> **ComplexNumber said:**
> there's one thing you've missed out. just like there are are fedora rpm, mandrake rpms, etc......there is exactly the same situation with debian systems. try installing debian debs on ubuntu - it has the exact same ability to break your system on both deb and rpm.I've installed quite a few Debian Debs on my Ubuntu box. It's running fine. If any don't, dpkg has tools to deal with it. Better tools, in my experience, than RPM has.

Besides, Debian has official packaging standards, that most packagers follow. It seems like the RPM standard is "whatever the distribution does."> **ComplexNumber said:**
> it seems like you're imagining non-existant problems. where is this "giant headache" that you speak of? - i've never encountered it.You're forgetting, I speak from experience. I used Fedora Core 3 for six months. It was horrible. FreshRPMs, Dag's RPMs, a tiny selection of official RPMs, and they all conflicted in various ways. And then there's apt-rpm. It's, obviously, Apt for RPM, only the official repository doesn't support it, but it has better dependency handling, and Synaptic works with it. So you have to try Synaptic first. If that comes up with a conflict, try yum. If that doesn't work, find the RPMs on the web. Then, as a last resort, install from source.

I once had an RPM that depended on itself, before it could be installed. Sure, just careless packaging, but I've never had anything like that with Ubuntu.

The next distribution I used was Gentoo, and I have to say, it was a breath of fresh air in comparison, even though I had to recompile my kernel 5 times to get my mouse working.> **ComplexNumber said:**
> also, i have no idea where you get this idea from: <what I said about checkinstall>Have you ever used checkinstall? Check it out.> **ComplexNumber said:**
> anyway, the LSB chose rpm over deb as being the superior package manager, so go figure.[quote=Someone on the LSB mailing list, around 1999]The "rpm" command -- *or some subset thereof* might be specifiable if is
considered that this capability is important enough -- personally, I
would say it is, since otherwise there would be no way for a script to
install a package, and no way for a file browser to know how to install
a package.  However, there should be no requirement that the command
"rpm" invokes the program from Red Hat software.  If it is a script that
wraps "dpkg", then fine :)[/quote](Here's the [source](http://lists.debian.org/lsb-spec/1999/09/msg00040.html).) The script is called "alien". If you read through that discussion, you'll find that it wasn't exactly a unanimous decision, and was mainly focused on the existing prevalence of RPM, due to the popularity of Red Hat. If the standard were being made today, they may have chosen Deb, since Ubuntu is clearly one of the most popular distributions, and variants are constantly appearing.

I realize that the next paragraph says it would be good to have the wrapper use RPM syntax, to be invisible to the user. That would be fairly easy to do, if someone wanted to make a script around alien, package it as, say, fake-rpm, and have it install by default.

Here's another juicy bit from the same discussion:> It doesnt matter how the rpm was built or what installed it. It matters that
it installs everywhereOf course. RPMs install everywhere. Why didn't I realize that while I was fighting yum for hours at a time?

The only thing that installs everywhere is source. The next-best thing is a package, of whatever format, from an official repository. Ubuntu has a larger official repository than Fedora.

Oh, and about the packaging formats themselves? I have one thing to say. Debconf. Never install a server without it.

---

### Post by ComplexNumber on 2006-09-23
> Better tools, in my experience, than RPM has.you must be joking. for installing locally, rpm definitely has the edge. i didn't find a way to install them locally on ubuntu, even though dpkg -i is meant to do the trick. it didn't for me, though. the facilities of dpkg are a cross between between being crippled and unintuitive.


> Have you ever used checkinstall?i used it for a few years, but i don't anymore because i found it it to be unreliable, contrary, and a pain. i don't make rpms anymore, and to install source code i use gpaco.

> 
You're forgetting, I speak from experience. I used Fedora Core 3 for six months.i'm not forgetting anything. too little experience IMO. i've used it for several years, and still am. 


> 
It was horrible. FreshRPMs, Dag's RPMs, a tiny selection of official RPMs, and they all conflicted in various ways.the only ones that have a compatibility issue are freshrpms and dag. livna, dries, atrpms, fedora official, and freshrpms are all thats required, and they are 100% compatible.
> 

If the standard were being made today, they may have chosen Deb, since Ubuntu is clearly one of the most popular distributions, and variants are constantly appearing.well, have you heard any hint of them changing their mind?  well then, theres your answer. considering the length of time that ubuntu and mepis etc has been popular for, they've had much more than enough time for the debian counter-argument, so its obvious that they know that they've already  made the correct decision.

---

### Post by skymt on 2006-09-23
> **ComplexNumber said:**
> you must be joking. for installing locally, rpm definitely has the edge. i didn't find a way to install them locally on ubuntu, even though dpkg -i is meant to do the trick. it didn't for me, though. the facilities of dpkg are a cross between between being crippled and unintuitive.Okay. This is my last post in this thread, if you refuse to be rational. dpkg -i isn't "meant to do the trick", it really does install packages locally. If it doesn't for you, that means your system is seriously messed up. It is not a flaw with dpkg. It's a bit like saying "the brake pedal in my car doesn't work, so all brake pedals are bad, so just use the emergency brake."

Google "rpm vs deb". It's pretty clear who wins.

RPM is just like Windows: an inferior piece of software that won because it met the need first. That, as any Linux user could tell you, doesn't mean it's any better.

---

### Post by ComplexNumber on 2006-09-23
its me whos being rational. dpkg is well and truly crippled. the only option to install locally is dpkg -i. compare that the wealth of options that rpm provides. given what you've said, i doubt that you have even used rpm.


> 
Google "rpm vs deb". It's pretty clear who winhehe i wonder why that is. its because the hits are mosty links to clueless people mindlessly repeating the same old "rpm...blah blah...dependency hell" chant. and just like sheep, others continue to chant it without even knowing why or what the heck they are talking about.



> RPM is just like Windows: an inferior piece of software that won because it met the need first. That, as any Linux user could tell you, doesn't mean it's any better.only from a naive point of view. the LSB has chosen rpm and is not showing any signs of deviating from the correct choice,  despite the much trumpetted debian revival. they've made the correct choice, and thats that.

---

### Post by weatherman on 2006-09-23
when lsb choose rpm over deb ubuntu didn't even exist. Today's choice might have been different.

---

### Post by darkhatter on 2006-09-23
> **skymt said:**
> What did they change in the init system? It seems the same as every other sysvinit system I've worked with.

when I change to init level 3 on every other distro BUT Ubuntu it will kill x

---

### Post by darkhatter on 2006-09-23
dep-Hell does not exsit for any distro other then slackware (Slapt-get fixes this) so don't bring that up anymore, I'm sick of hearing this. I find there is better support for rpm on distro then there is for dep. This turned into a flamewar so can a admin close it or move it somewhere else. I started this thread because I was angry at the Ubuntu team, who thought it was a good idea to change the init-levels on me. For example when I switch to run level 3 on any distro but Ubuntu it stops x for me. 

for the record Ubuntu comes with about 5000 offically supported packages, I believe Suse has about half of that (3.5g of them).

Anyways I figured out how to fix the problem, I installed Suse and everything went back to normal, anyway stop the fighting were all on the same side, and 10.2 got alot better. The default kde install was about 1.5 g and they only have one redundent package (2 vector editors). I see Ubuntu as more of a hype distro. They give it away for free, it looks nice, its good to use, has nice hardware support, the point being it gives you a good linux experience, but thats all I can see it doing I think Mark (thats his name right) is creating a distro so everyone can have Linux not to take over the market. I'm glad he's doing this its nice to see "african-americans" doing good things. I have a role-model now. I wish you guys the best of Luck.

I guess thats my way of saying goodbye.

~Andrew~ 

*typed from OpenSuse 10.2 alpha KDE

---

### Post by Demio on 2006-09-23
Well good for you.

Now for my question...
Who gives a damn?

Regards,
Demio

P.S.: Obviously Ubuntu is doing something right, since right now it's the most used desktop distro. And even Google as adapted Ubuntu on it's servers....

I guess you're just frustrated that this isn't just like you want it to be, or how you are used it to be and post crap posts like this.

Anyways, give me a Debian based distro any day over any RH based one. :rolleyes:

---

### Post by Lord Illidan on 2006-09-23
Hey everybody is free to choose what distro he/she likes.. I like Fedora Core 5, for instance.

As for dep hell...well, with smart and yumex, and [The Unofficial Fedora FAQ]("http://www.fedorafaq.org/#installsoftware") I got along quite well, I didn't even have to search the forums.

That's one thing.

With SUSE, yes, I used to get dependency errors..perhaps SUSE is SUSE...but Fedora is no longer the nightmare it used to be.

---

### Post by ComplexNumber on 2006-09-23
**darkhatter**
for a kde distro, you can't go far wrong with suse. in fact, it gave me the best kde experience of all.  if i were to choose kde, i would choose suse, without a doubt. canonical and associated developers only have a limited amount of resources, and whilst they keep on releasing more and more Xbuntu this or Ybuntu that, they can only ever be jack of all trades but master of none.  its true that ubuntu is more hype and buzzword than substance. its just another distro, nothing more, nothing less.

---

### Post by Demio on 2006-09-23
More hype and buzzwrod than substance? What substance are you talking about, it's a freaking OS. The substance are the apps you run in it, and it can run at least as many apps as any RH fork can, and even more....

---

### Post by Lord Illidan on 2006-09-23
> **ComplexNumber said:**
> **darkhatter**
for a kde distro, you can't go far wrong with suse. in fact, it gave me the best kde experience of all.  if i were to choose kde, i would choose suse, without a doubt. canonical and associated developers only have a limited amount of resources, and whilst they keep on releasing more and more Xbuntu this or Ybuntu that, they can only ever be jack of all trades but master of none.  its true that ubuntu is more hype and buzzword than substance. its just another distro, nothing more, nothing less.

I agree bout that.. The amount of hype **is **astounding. It is a good distro, an excellent one, but without these forums, I wouldn't have spent as long on it as I did.

---

### Post by Demio on 2006-09-23
What's wrong about hype though? If attracts more people to Linux then it's a darn good thing.

---

