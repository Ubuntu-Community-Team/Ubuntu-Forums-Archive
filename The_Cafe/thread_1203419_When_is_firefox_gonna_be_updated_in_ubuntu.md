---
title: "When is firefox gonna be updated in ubuntu?"
date: 2009-07-03
forum: The Cafe
---

### Post by bhishan on 2009-07-03
When is firefox gonna be updated to v3.5 in ubuntu?

---

### Post by ~sHyLoCk~ on 2009-07-03
> **bhishan said:**
> When is firefox gonna be updated to v3.5 in ubuntu?

It isn't already in the repos?

---

### Post by bhishan on 2009-07-03
> **~sHyLoCk~ said:**
> It isn't already in the repos?

Do I have to do it manually or will the update manager do it automatically?

---

### Post by ~sHyLoCk~ on 2009-07-03
> **bhishan said:**
> Do I have to do it manually or will the update manager do it automatically?

Once it's in the repos, it will be upgraded aiutomatically, just run your update manager.

---

### Post by el cameleon on 2009-07-04
So the remaining question is: when will it be available in the repos?

---

### Post by NilsE on 2009-07-04
> **el cameleon said:**
> So the remaining question is: when will it be available in the repos?

It is in the repos but it will not install automatically.  Go into Synaptic and search on firefox-3.5 and install it from there.  It will not remove your current version, it will copy the profile and will run side by side with the older version.

---

### Post by PlancksCnst on 2009-07-04
Are you sure it's int the official repos, not a PPA? It's definitely not in mine (yes, I updated).

---

### Post by ogcub on 2009-07-04
It's already in proposed for jaunty, but without correct logo and named Shiretoko. So, maybe in a month or two it will be corrected. Also tool tip still says firefox beta :). Finally it's summertime in northern hemisphere, so nobody is in a rush :)

---

### Post by cc8balla on 2009-07-04
3.5 beta 4 is in the repos. NOT the RC of 3.5

My guess is that Canonical is still working on it? They have their "own" version of it to make sure its compatible with the current version of Ubuntu. 

I hope its soon though.

---

### Post by John.Michael.Kane on 2009-07-04
You will have to maualy install firefox-3.5, it is in the normal repositories, and is not listed as b4.

Running apt-cache on machine with no ppa's gives the below output.
```
apt-cache show firefox-3.5
Package: firefox-3.5
Priority: optional
Section: universe/web
Installed-Size: 3600
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: amd64
Version: 3.5+nobinonly-0ubuntu0.9.04.1
Replaces: firefox-3.1
Provides: firefox-3.1, www-browser
```

---

### Post by stimpack on 2009-07-04
Just install from mozilla site and let it autoupdate itself like you would on any other OS. I don't see the point of repos in this case.

---

### Post by ikt on 2009-07-04
> **PlancksCnst said:**
> Are you sure it's int the official repos, not a PPA? It's definitely not in mine (yes, I updated).

[IMG]http://images50.fotki.com/v1529/fileSrwV/12b9d/7/1533997/7711139/firefox35.jpg[/IMG]

---

### Post by LodeRunner on 2009-07-04
> **ikt said:**
> [IMG]http://images50.fotki.com/v1529/fileSrwV/12b9d/7/1533997/7711139/firefox35.jpg[/IMG]

That is an older version of 3.5, which cannot run the latest version (0.4) of Mozilla Weave browser sync. Also, it is unbranded ("Shiretoko"), and remains so even if you install the Firefox 3.5 branding package.  Because it is unbranded, websites will complain about you running an old browser, etc.  Also, you CANNOT use different versions of Weave together (e.g. Windows partition using 0.4, Ubuntu using 0.3) because each version of Weave will completely delete and overwrite what the other version saved, without prompt. Extremely annoying, but it's a Feature not a Bug[tm].

I wish that more devs would do what Truecrypt does and just let you download a .deb.  I understand the stability and compatibility offered by a repository system, but of what use is it if you cannot use the programs you need?

---

### Post by Sand &amp; Mercury on 2009-07-04
I was under the impression it wouldn't get updated in the main repos at all and we'd have to wait for Karmic.

---

### Post by hessiess on 2009-07-04
Dont bother updating instantly, I just updated Arch, including FF3.5 and it is verry buggy.

---

### Post by UKBB on 2009-07-04
> **hessiess said:**
> Dont bother updating instantly, I just updated Arch, including FF3.5 and it is verry buggy.
 
Very buggy, I installed Shiretoko and when I go full screen on a youtube video it shuts down.

---

### Post by HappyFeet on 2009-07-04
I'm in no hurry for it. I can wait until it ships with Karmic.

---

### Post by calrogman on 2009-07-04
> **hessiess said:**
> Dont bother updating instantly, I just updated Arch, including FF3.5 and it is verry buggy.

Except that, you know, the firefox 3.5 package in Arch is entirely different from the one in the Ubuntu repos...

---

### Post by cc8balla on 2009-07-04
> **John.Michael.Kane said:**
> You will have to maualy install firefox-3.5, it is in the normal repositories, and is not listed as b4.


I stand corrected then :D

Now that I have 3.5 installed, I wish the fonts would look good, as at the moment, its terrible.

---

### Post by ratcheer on 2009-07-04
Lifehacker says to install it this way:

```

wget -O - http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2 | tar xj -C ~

```

[http://lifehacker.com/5306169/install-firefox-35-on-ubuntu-with-one-command](http://lifehacker.com/5306169/install-firefox-35-on-ubuntu-with-one-command)

I haven't tried it yet, though. Also, there are other posts on that page indicating there may be better ways to do it.

Tim

---

### Post by cc8balla on 2009-07-04
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

That is how I installed it. 

I've fixed several annoyances so far, i.e. bookmark toolbar collapsing, but the fonts is beyond me atm. 

I've altered my fontconfig, and that did nothing.

---

### Post by aysiu on 2009-07-04
> **ratcheer said:**
> Lifehacker says to install it this way:

```

wget -O - http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5/linux-i686/en-US/firefox-3.5.tar.bz2 | tar xj -C ~

```

[http://lifehacker.com/5306169/install-firefox-35-on-ubuntu-with-one-command](http://lifehacker.com/5306169/install-firefox-35-on-ubuntu-with-one-command)

I haven't tried it yet, though. Also, there are other posts on that page indicating there may be better ways to do it.

Tim
Having gone through numerous versions of Firefox in Ubuntu over the years, I still think the best way for impatient users to install Firefox is to get the Mozilla .tar.bz2 file and "install" it with symlinks:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Sure, 3.5 is coming into the Ubuntu repositories, but what about when 3.6 comes out? Or 3.6.1? Or 3.6.2? If you're the sort of person who wants the latest Firefox the very day it comes out, you'll be constantly frustrated if you have to keep waiting either days, weeks, or months for it to show up in the repositories.

---

### Post by gtr225 on 2009-07-04
But when will the Firefox meta-package replace 3.0 with 3.5 final?

---

### Post by pjalegria on 2009-07-04
I read that FF3.5 ill not be on Jaunty oficial repositories :lolflag:

---

### Post by Closed_Port on 2009-07-04
[http://www.asoftsite.org/s9y/](http://www.asoftsite.org/s9y/)

To sum it up: 3.5 final will be in universe soon but if you can't wait for it, use the mozilla-security ppa.

---

### Post by gtr225 on 2009-07-04
> **pjalegria said:**
> I read that FF3.5 ill not be on Jaunty oficial repositories :lolflag:

Not even as a backport?

---

### Post by Merk42 on 2009-07-04
> **aysiu said:**
> Sure, 3.5 is coming into the Ubuntu repositories, but what about when 3.6 comes out? Or 3.6.1? Or 3.6.2? If you're the sort of person who wants the latest Firefox the very day it comes out, you'll be constantly frustrated if you have to keep waiting either days, weeks, or months for it to show up in the repositories.

I guess I personally can wait a couple days, it's just that with Ubuntu's policy on updates it's not really clear if Jaunty/Hardy users will get it **at all**

Why do we have to wait more than a few days (if at all) though?
Shouldn't the testing be done with the Release Candidate so that way when Mozilla says it goes final it can quickly be in the repositories?

Oh wait, the repositories were never even updated past beta 4...

---

### Post by Closed_Port on 2009-07-04
> **Merk42 said:**
> 
Why do we have to wait more than a few days (if at all) though?
Shouldn't the testing be done with the Release Candidate so that way when Mozilla says it goes final it can quickly be in the repositories?

That's exactly what they did. But they didn't do it in the normal repos, but in ppas. After all, that's what ppas are there for. And that's the reason why the final was available in the ppas of ubuntu mozilla developers on the day of the release and why it will be available shortly in the normal repos...

---

### Post by darolu on 2009-07-04
> **pjalegria said:**
> I read that FF3.5 ill not be on Jaunty oficial repositories :lolflag:

Can you link us to your source please?

[quote=Closed port]That's exactly what they did. But they didn't do it in the normal repos, but in ppas. After all, that's what ppas are there for. And that's the reason why the final was available in the ppas of ubuntu mozilla developers on the day of the release and why it will be available shortly in the normal repos...[/quote]
Where did you read it will be available shortly?

I personally haven't read any official response about Firefox 3.5 and I do think it is necessary for it to be available on normal repositories so normal people can normally update their software using Update Manager.

But in the meanwhile, if you want to use FF 3.5 (which I personally like very much and haven't found a single bug yet) the best way, in my opinion, is to download the already compiled version from [http://www.firefox.com](http://www.firefox.com) untar it, create a launcher and use it.

---

### Post by SunnyRabbiera on 2009-07-04
You know there should be a sticky on this matter, as we are unsure if Firefox 3.5 will come to the official repositories.

---

### Post by Closed_Port on 2009-07-04
> **darolu said:**
> 
Where did you read it will be available shortly?

[http://www.asoftsite.org/s9y/](http://www.asoftsite.org/s9y/)
The writer is the admin of the mozilla securtiy team.

> **darolu said:**
> 
But in the meanwhile, if you want to use FF 3.5 (which I personally like very much and haven't found a single bug yet) the best way, in my opinion, is to download the already compiled version from [http://www.firefox.com](http://www.firefox.com) untar it, create a launcher and use it.
No, you should do as god intended and use a paa. ;-D
Seriously, as it mentioned in the linked blog post, the final 3.5 is in the mozilla-security ppa and it works fine, too. I'm writting this post with it.

---

### Post by jdunn on 2009-07-04
question:  Firefox 3.5 **is** in the repositories but why isn't the Firefox metapackage linked to it?  Firefox is supposed to be one of the few programs that Ubuntu provides regular package updates for.

---

### Post by 23meg on 2009-07-04
> **Merk42 said:**
> I guess I personally can wait a couple days, it's just that with Ubuntu's policy on updates it's not really clear if Jaunty/Hardy users will get it **at all**

[The policy itself]("https://wiki.ubuntu.com/StableReleaseUpdates") is very clear. [The widely circulated official FAQ]("http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html") posted by Alexander Sack of the Ubuntu Mozilla Team, is also pretty clear regarding which release will get what kind of updates and when.

Did you read these before posting? If you did, you may want to state what precisely you found unclear; that can help improve things for the future.

> **Merk42]Why do we have to wait more than a few days (if at all) though?
Shouldn't the testing be done with the Release Candidate so that way when Mozilla says it goes final it can quickly be in the repositories?[/QUOTE]
[URL="https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition"]

The Firefox 3.5 transition spec[/URL] can give you an idea why it is so.

[QUOTE=Merk42 said:**
> Oh wait, the repositories were never even updated past beta 4...

What we have in Jaunty is a snapshot dated March 30, which is *before* Firefox Beta 4, and right after the Jaunty beta freeze. Pushing later testing milestones into a stable release as stable release updates was likely deemed not worth the effort by the Mozilla team, since it's a stable release, and testing can be done in Karmic and/or via the team PPAs.

---

### Post by Mr. Picklesworth on 2009-07-05
Edit: Don't mind me.

> **23meg said:**
> What we have in Jaunty is a snapshot dated March 30, which is *before* Firefox Beta 4, and right after the Jaunty beta freeze. Pushing later testing milestones into a stable release as stable release updates was likely deemed not worth the effort by the Mozilla team, since it's a stable release, and testing can be done in Karmic and/or via the team PPAs.

...From which arises the question: Why was it uploaded in the first place?

Sure, we can expect the user to use PPAs, but wouldn't the end user expect the unstable release candidate firefox-3.5 to be updated in the end? This seems especially logical, from an end user's perspective, when firefox-3.5 is in fact final and stable in the outside world.

I'm not saying that this *needs* to be updated within Jaunty's official repository or I'll melt, but it seems to me that user friendliness is not given enough thought with the repositories, and this is a fine example of common sense being thrown out the window for no good reason.

---

### Post by 23meg on 2009-07-05
[QUOTE=Mr. Picklesworth]...From which arises the question: Why was it uploaded in the first place?[/QUOTE]

To start the transition from Firefox 3.1 to 3.5. See [bug #352995]("https://launchpad.net/bugs/352995").

[QUOTE=Mr. Picklesworth]Sure, we can expect the user to use PPAs, but wouldn't the end user expect the unstable release candidate firefox-3.5 to be updated in the end? This seems especially logical, from an end user's perspective, when firefox-3.5 is in fact final and stable in the outside world.[/QUOTE]

It *is* being updated in the end. Or am I misunderstanding you?

[QUOTE=Mr. Picklesworth]I'm not saying that this *needs* to be updated within Jaunty's official repository or I'll melt, but it seems to me that user friendliness is not given enough thought with the repositories, and this is a fine example of common sense being thrown out the window for no good reason.[/QUOTE]

What is not "user friendly" about Firefox [being given an exception]("https://wiki.ubuntu.com/StableReleaseUpdates/MicroReleaseExceptions") to the SRU policy, which if it were to be applied without one, would rule out an update of this significance? Again, I may be misunderstanding something.

---

### Post by Mr. Picklesworth on 2009-07-05
Ooops. I was :redface:
Thanks for the clarification and the patience!

It does seem silly to ship a soon-outdated pre-release as a stand in, since it is unstable and sure to generate a few obsolete bug reports. An imaginative default home page for Ubuntu's package, pointing users who want to help test towards the mozilla-daily ppa (for example), or at least letting them know that the package is not totally up to date, could do the trick there.

---

### Post by thered on 2009-07-05
I've read most of the threads about upgrading to Firefox 3.5.  I'm not interested in shiretoko, betas ,alphas or compiling from source.

I just want my browser, the most important application on my PC, to be the best and up to date.

Why can't the Ubuntu people (Canonical) just update it as they do all my other software or OS?

I love Ubuntu, best Linux distro ever - but as it says, or used to, 'Linux for human beings..' 

So please, let's just do it, put it on the update system or whatever it is, but let's have best and let's have it now.

---

### Post by Tibuda on 2009-07-05
> Why can't the Ubuntu people (Canonical) just update it as they do all my other software or OS?
They do with Firefox the same as they do with all other software. They keep the stable version from the release date. All jaunty software are from april (except security updates), to keep the system stability. If you want a newer version you need a PPA (best way), a deb (easier way) or other source. It is not that hard. Firefox 3.5 will surely be the default for karmic.

---

### Post by cariboo on 2009-07-05
It will be the default in Karmic Koala. I installed it from the Karmic repositories, and even though it still has the Shiretoko label, according to Help-->About. I'm using 3.5 final.

See screenshot.

---

### Post by izizzle on 2009-07-05
We wait till they release 9.10.

---

### Post by thered on 2009-07-05
> We wait till they release 9.10.

I hate to seem obtuse, but no one can tell me ***why*** we have to wait.  How hard can it be?

---

### Post by SunnyRabbiera on 2009-07-05
Currently the update to Firefox 3.5 is optional as there have been reports of bugs all over.
Ubuntu typically sticks to stable software, even Jaunty has this in mind for the most part.
For Hardy through Jaunty, you could try PPA's.
But 3.5 will be default on Karmic.

---

### Post by Tibuda on 2009-07-06
> **thered said:**
> I hate to seem obtuse, but no one can tell me ***why*** we have to wait.  How hard can it be?

Stability. It was not tested in jaunty, and is being tested for karmic.

---

### Post by Johnsie on 2009-07-06
I don't buy the 'stability' thing. I think it's just that it would take too much work to keep every package in the repositories up to date for every application.

Most people will more than likely have to wait until Karmic comes out. This is not an ideal situation. Firefox 3.5 is already easily available for the two other major operating systems and runs quite well on them. Ubuntu needs to be more competitive.

Ubuntus problem is that Cannonical control when most users update software. Sometimes I think it would be better to allow the application developers to decide. Firefox on Windows updates itself but with Ubuntu you have to wait on Cannonical or do a manual updgrade.

---

### Post by Tibuda on 2009-07-06
> **Johnsie said:**
> Ubuntus problem is that Cannonical control when most users update software. Sometimes I think it would be better to allow the application developers to decide. Firefox on Windows updates itself but with Ubuntu you have to wait on Cannonical or do a manual updgrade.

They allow. It is called PPA.

---

### Post by Johnsie on 2009-07-06
Try explaining PPA to a granny or the average joe. That's why I said 'most users'. Yes, some technical computer enthusiasts can reconfigure their repositories, but in the grand scheme of things those people are a minority of computer users. Linux designers need to stop thinking like experts and put themselves in the shoes of beginners, otherwise Linux will always be perceived a geeks-only system.

---

### Post by Tibuda on 2009-07-06
> **Johnsie said:**
> Try explaining PPA to a granny or the average joe. That's why I said 'most users'. Yes, some technical computer enthusiasts can reconfigure their repositories, but in the grand scheme of things those people are a minority of computer users. Linux designers need to stop thinking like experts and put themselves in the shoes of beginners, otherwise Linux will always be perceived a geeks-only system.

Granny or the average joe don't care for Firefox 3.5 and are fine with 3.0. Most of these kind of users think the '[little e]("http://tbn0.google.com/images?q=tbn:22MgH7hPJdxn7M:http://h2odeskmod.files.wordpress.com/2007/10/internet-explorer.png%3Fw%3D128%26h%3D128%26h%3D128")' is THE Internet.

---

### Post by Johnsie on 2009-07-06
That doesn't mean they shouldn't be able to have it or be informed that it is avalaible, with an easy way/option to upgrade. The fact is that many users have had to read howtos just to do a manual upgrade of something that could've been automatic.

---

### Post by Tibuda on 2009-07-06
They are able. They just have to learn something new. Add a new entry to System > Admin > Software sources, and install the firefox-3.5 package. I just think it should have the same package name, but this is not that hard.

---

### Post by Johnsie on 2009-07-06
That's simply not as efficient as clicking 'yes' on a 'Would you like to upgrade firefox?' prompt.

Just because we computing enthusiasts like to learn about computing doesn't mean that everyone else does. That's why Linux still has the geeks-only reputation. Things are over-complicated when actually they could be quite simple.

---

### Post by Tibuda on 2009-07-06
Or as efficient as keeping with Firefox 3.0. Easier than clicking yes. Bleeding edge is not something avg joe wants.

I realise there's one annoying thing about PPAs for the user: it's really hard to add a PPA key. I think [this blog got a good solution]("http://doctormo.wordpress.com/2009/06/01/ubuntu-apt-url-and-the-white-list/").

EDIT: What you want is a distro that uses the rolling release model, like Arch. Canonical chose not to use this model because it would be a pain to support it, with very few benefits.

---

### Post by Skripka on 2009-07-06
> **Johnsie said:**
> That's simply not as efficient as clicking 'yes' on a 'Would you like to upgrade firefox?' prompt.

Just because we computing enthusiasts like to learn about computing doesn't mean that everyone else does. That's why Linux still has the geeks-only reputation. Things are over-complicated when actually they could be quite simple.

No things are more complicated than they appear.

Firefox has lots of depends--you update to the latest Firefox, you may need other system-critical depends updated as well, potentially destabilizing your system.

If you want the latest and greatest move to a rolling release distro.  Ubuntu has always had a 6 month delay on every software in it's repositories.

---

### Post by CaseSensative on 2009-07-06
It takes 5 minutes to install 3.5. Maybe 2 minutes to look for the codes. I found it very easy i don't think you should be harsh. I came to ubuntu to do things myself and not wait, and guess what. We have both options so yeah be happy.

---

### Post by Closed_Port on 2009-07-06
Uhm, firefox-3.5 will be available in the normal repos. In fact, it's already in proposed. So all people have to do to get firefox-3.5 is, oh my god, install firefox-3.5.

So what exactly is the problem?

---

### Post by Viva on 2009-07-06
> **Johnsie said:**
> Try explaining PPA to a granny or the average joe. That's why I said 'most users'. Yes, some technical computer enthusiasts can reconfigure their repositories, but in the grand scheme of things those people are a minority of computer users. Linux designers need to stop thinking like experts and put themselves in the shoes of beginners, otherwise Linux will always be perceived a geeks-only system.

Grannies don't know how to install software in windows either. The average Joe takes less time learning how to add a repository than he did to install a software in windows.

---

### Post by kingofpain on 2009-07-06
> **Closed_Port said:**
> Uhm, firefox-3.5 will be available in the normal repos. In fact, it's already in proposed. So all people have to do to get firefox-3.5 is, oh my god, install firefox-3.5.

So what exactly is the problem?

The problem is that you don't get Firefox 3.5, but a pre release of 3.5.1 (called Minefield) which is... a pre release, not the official STABLE version of firefox 3.5.

---

### Post by Justin Trouble on 2009-07-06
> **kingofpain said:**
> The problem is that you don't get Firefox 3.5, but a pre release of 3.5.1 (called Minefield) which is... a pre release, not the official STABLE version of firefox 3.5.

No, you get the final version of Firefox 3.5, but without the Firefox branding. It's named after the development code name Shiretoko. This can cause some compatibility problems with some web sites and Firefox addons.

Currently 3.5 beta 4 is in the main repos, 3.5 final is in Jaunty proposed-updates and will be moved to main soon (if not already today).

---

### Post by eldragon on 2009-07-06
people, if you want to know why there is a version freeze on ubuntu, then install a rolling release distro like arch, and you will know from first hand why this is the case, there are usually glitches, and annoyances with new versions, if you are avid enough to circumvent them, or downgrade if needed, then this would not be a problem. but most users complain when stuff break. something that ubuntu tries to avoid. and if you are experienced enough to fix a rolling release distro, then you will probably be able to handle the task of installing ff3.5 on ubuntu.

either way, sticking to stable release cycles seems like the sane way to go.

anyway, complaining about it will not change anything, since this is a topic that has been discussed to death.

my advice: if you can afford downtime, install a rolling release distro. if you cannot. well, dont ;)

---

### Post by init1 on 2009-07-06
> **Johnsie said:**
> I don't buy the 'stability' thing. I think it's just that it would take too much work to keep every package in the repositories up to date for every application.

Most people will more than likely have to wait until Karmic comes out. This is not an ideal situation. Firefox 3.5 is already easily available for the two other major operating systems and runs quite well on them. Ubuntu needs to be more competitive.

Ubuntus problem is that Cannonical control when most users update software. Sometimes I think it would be better to allow the application developers to decide. Firefox on Windows updates itself but with Ubuntu you have to wait on Cannonical or do a manual updgrade.
Perhaps you would like a more cutting-edge distro like Debian Unstable then. They get packages newer than distros like Ubuntu.

---

### Post by stinger30au on 2009-07-06
> **thered said:**
> I hate to seem obtuse, but no one can tell me ***why*** we have to wait.  How hard can it be?

Ubuntu is *NOT* a rolling release distro

ubuntu team release security updates and thats it

every 6 months when a new version comes out it will have the newest versions in it

if you really cant live with out FF 3.5 *NOW* theres a few choices, you can build from source yourself, or get swiftfox

[http://getswiftfox.com/index.htm](http://getswiftfox.com/index.htm)

---

### Post by Closed_Port on 2009-07-06
> **kingofpain said:**
> The problem is that you don't get Firefox 3.5, but a pre release of 3.5.1 (called Minefield) which is... a pre release, not the official STABLE version of firefox 3.5.

No, you don't. If you do get 3.5.1 you probably have the mozilla-daily ppa enabled.

---

### Post by Merk42 on 2009-07-06
Seems Jaunty got updated.
However the branding is still Shiretoko.
It also still wants to open up 3.0.11 as the default, I'm sure that's something I have to do on my end but I don't know what.

---

### Post by gtr225 on 2009-07-06
Well I was tired of waiting and downloaded Firefox 3.5 directly from Mozilla, extracted the tar.gz file and it works fine. This is the same thing I have to do with Vuze inorder to have an up-to-date version of it. I understand Ubuntu's update policy and such, but c'mon this is Firefox. Probably one of the most used applications in Ubuntu. Also 3.5 has been in beta seemingly forever, so it's probably pretty darn stable by now.

---

### Post by X-BANE on 2009-07-06
Are we actually going to get an official Canonical update of Firefox 3.5(to replace 3.0.11) in Jaunty's lifetime?

---

### Post by Viva on 2009-07-06
> **X-BANE said:**
> Are we actually going to get an official Canonical update of Firefox 3.5(to replace 3.0.11) in Jaunty's lifetime?

Probably not, but that is not how ubuntu releases work.

---

### Post by X-BANE on 2009-07-06
> **Viva said:**
> Probably not, but that is not how ubuntu releases work.

This is why Canonical will always be playing catchup with the big boys. They seem to get the fact that most end users want simplicity, but unfortunately not that they would like up to date software also. Of course the usual answer is "well if you don't like waiting, go and download it", which essentially means I may as well being using Windows... :rolleyes:

---

### Post by aysiu on 2009-07-06
> **X-BANE said:**
> This is why Canonical will always be playing catchup with the big boys. They seem to get the fact that most end users want simplicity, but unfortunately not that they would like up to date software also. Of course the usual answer is "well if you don't like waiting, go and download it", which essentially means I may as well being using Windows... :rolleyes:
I think most users have no idea that Firefox 3.5 just came out. I think most users could wait until October to get it. And, in fact, when October does come around, a large minority of Firefox 3.0 users will probably still be using 3.0 and be none the wiser.

Unless by "most end users" you mean "most early adopters of Linux."

---

### Post by 23meg on 2009-07-07
> **Johnsie said:**
> 
Ubuntus problem is that Cannonical control when most users update software. Sometimes I think it would be better to allow the application developers to decide. Firefox on Windows updates itself but with Ubuntu you have to wait on Cannonical or do a manual updgrade.

The firefox-3.5 package has only ever been introduced into the Universe component in Jaunty, which is maintained by the Ubuntu community, not Canonical.

---

### Post by X-BANE on 2009-07-07
> **23meg said:**
> The firefox-3.5 package has only ever been introduced into the Universe component in Jaunty, which is maintained by the Ubuntu community, not Canonical.

That just about says it all. I think it's time to move onto a rolling release. I am absolutely fed up of Canonical's stupid waiting games.

---

### Post by aysiu on 2009-07-07
> **X-BANE said:**
> That just about says it all. I think it's time to move onto a rolling release. I am absolutely fed up of Canonical's stupid waiting games.
Ubuntu has from the very start been on a six-month release schedule, and that is the plan going forward.

Perhaps instead of *Ubuntu* changing into a rolling release distro, *you* should go to a rolling release distro? PCLinuxOS and Arch Linux are rolling release distros you might want to check out.

It seems to me there are a lot of power users on these forums who get frustrated at new versions of applications not immediately appearing in repos. These power users would be better off with power-user distros (Arch, for example). For the computer illiterates out there (who probably don't even know a new version of Firefox has been released), waiting until October for things to update to new versions isn't going to bother them. It's actually a convenience for them to have everything updated all at once instead of having to keep track of the tech news... or just stay with outdated apps altogether.

---

### Post by X-BANE on 2009-07-07
> **aysiu said:**
> Ubuntu has from the very start been on a six-month release schedule, and that is the plan going forward.

Perhaps instead of *Ubuntu* changing into a rolling release distro, *you* should go to a rolling release distro? PCLinuxOS and Arch Linux are rolling release distros you might want to check out.

That is exactly what I meant, and yes PCLinuxOS does look interesting. I think it's time to wave goodbye to Ubuntu.

---

### Post by X-BANE on 2009-07-07
> **aysiu said:**
> It seems to me there are a lot of power users on these forums who get frustrated at new versions of applications not immediately appearing in repos. These power users would be better off with power-user distros (Arch, for example). For the computer illiterates out there (who probably don't even know a new version of Firefox has been released), waiting until October for things to update to new versions isn't going to bother them. It's actually a convenience for them to have everything updated all at once instead of having to keep track of the tech news... or just stay with outdated apps altogether.

Your opinion on "illiterates" is somewhat patronising. Not everyone is an idiot.

---

### Post by sertse on 2009-07-07
Good, wave goodbye to Ubuntu. It's not for you, but to imply because it's not for your needs that Ubuntu therefore sucks doesn't make sense.  There is already a reasonable explanation why it is staying with the 3.0.x series for 9.04, the fact you disagree doesn't means it wrong, multiple viewpoints can be all valid.

Is it patronising? If someone cares about computers so much that they know 3.5 is released AND they know they want it. They would also knowledgeable enough about computer be curious/accepting/unintimated etc by PPAs, to know how to get it that way.

---

### Post by nielsek on 2009-07-07
just install 3.5 if you want it. i use chrome its not in the repos either.

---

### Post by lswest on 2009-07-07
I think it's pretty clear (from Ubuntu's description) that applications aren't going to be updated regularly as "security updates" are available until the releases' end of life, but that's all.  Ubuntu aims to provide a secure, stable and easy to use Linux distribution, not a bleeding edge OS with bugs and time spent fixing things.  If you don't want that kind of a system, Ubuntu isn't the right distribution for you, but there are others.  If you want bleeding-edge, change distribution, since that's something you can actually do.  Trying to get Canonical to change their goal?  Not very likely.  And it's not like the updated packages aren't available somewhere.  It's easier to install a package in a round-about way (or change from Ubuntu) than it is to complain about it and try to get the developers to change their goals and beliefs in order to satisfy the occasional user.  I personally think even finding and adding a PPA is much easier and less time-consuming than it is to go to a manufacturer's website, find the model of your computer, and download every driver and OEM software bundle off the website for your computer if you re-install it, or want to update it (sure, there are update programs, but they only generally update programs already installed).

---

### Post by Delever on 2009-07-07
I respect developer's time packaging stuff and I understand the need to focus that effort in the most efficient manner. However, as Ubuntu gets more popular, there is more varied demand for both stability and latest versions. Basically - more work is needed, but if there are people who are willing to do extra packaging work, it should not be a problem. And if there is a worry about stability - use backports channel, or maybe new channel dedicated to that.

Just don't say it's impossible because rules say so.

---

### Post by Merk42 on 2009-07-07
> **aysiu said:**
> I think most users have no idea that Firefox 3.5 just came out...

Yes, because there wasn't a massive influx of threads asking about how to install Firefox 3.5 or anything...

---

### Post by lswest on 2009-07-07
> **Delever said:**
> Just don't say it's impossible because rules say so.

I don't think it's impossible, but it won't be easy to bring about that change, and the OP (as I understood it) wanted the updated packages in the default enabled repositories (that rules out backports and the like), since PPAs are the same idea after all.  The easiest alternative would be to simply find a distribution that suits you, instead of forcing the distribution you use to suit your needs.  Or, if you want to make a change, create a .deb repository that is easily added (PPAs have the keys that sometimes cause issues), with clear instructions, and host the packages yourself.  Not saying those are the only way to bring it about, but probably the two most likely to actually get it done (in my opinion).

---

### Post by kevdog on 2009-07-07
I'd really just like a good tutorial on how to use PPA's.  I have used many PPAs in the past, but some are more confusing than others.  I think it is quite imbicile to tell people to use PPAs and avoid telling them how to exactly do this, or point them to a well explained documentation on how to do this!

---

### Post by steeleyuk on 2009-07-07
> **kevdog said:**
> I'd really just like a good tutorial on how to use PPA's.  I have used many PPAs in the past, but some are more confusing than others.  I think it is quite imbicile to tell people to use PPAs and avoid telling them how to exactly do this, or point them to a well explained documentation on how to do this!

In my opinion, people should only use PPAs if they can cope with any breakage. Those people that can do that will easily be able to find out how to add a PPA to their repo list.

---

### Post by LowSky on 2009-07-07
Got to love people complaining about free software. Maybe Ubuntu should just use Epiphany instead.... I wonder how many "average joes" would notice. Most people just want to use the internet, they wouldn't know if there wasa new version unless they were bombarded with ads from TV.


just to be clear Shiretoko Is what Firefox 3.5 is called in Arch by defualt. Just so these people know Firefox always goes by its code name on Arch installs.

the complaint here is why cant you get the update like you can on Windows, well, thats because Firefox is built for Windows, us linux people are actually a second fiddle. And Linux actually likes to control is software from an administrator, not from any user who likes to click yes to any popup that strolls across the screen.

---

### Post by aysiu on 2009-07-07
> **Merk42 said:**
> Yes, because there wasn't a massive influx of threads asking about how to install Firefox 3.5 or anything...
I don't mean Ubuntu users. I mean computer users in general, most of whom are on Windows and, as I said, have no idea Firefox 3.5 just came out.

Do you actually believe the Ubuntu Forums members are representative of the computing population at large?

---

### Post by aysiu on 2009-07-07
> **X-BANE said:**
> Your opinion on "illiterates" is somewhat patronising. Not everyone is an idiot.
I never said *anyone* was an idiot, let alone *everyone*.

I was saying that the vast majority of computer users are computer illiterate (many by their own proclamation), and computer illiterates do not care about installing the latest Firefox the week it comes out. Most of them are, in fact, wholly unaware a new Firefox even came out at all.

Power users like yourself (and like most Ubuntu Forums members) are not representative of the populace at large.

> **LowSky said:**
> Got to love people complaining about free software. Maybe Ubuntu should just use Epiphany instead.... I wonder how many "average joes" would notice. That was actually a notion that came up a lot a few years ago:
[What do you think about Epiphany being the default browser for Ubuntu?](http://ubuntuforums.org/showthread.php?t=543957)

Now it seems people who don't use Firefox are more fascinated with Opera or alpha Chrome.

---

### Post by Merk42 on 2009-07-07
> **aysiu said:**
> I don't mean Ubuntu users. I mean computer users in general, most of whom are on Windows and, as I said, have no idea Firefox 3.5 just came out.

Do you actually believe the Ubuntu Forums members are representative of the computing population at large?

Considering you said about most users waiting until October I took you to only be talking about Ubuntu users.

---

### Post by chrisccoulson on 2009-07-07
Firefox 3.5 will not be the default browser in current stable releases because the regression potential is just too high. The development cycle is for introducing and testing the latest and greatest. Once the development version is stable, updates should be (and are) restricted to major bug fixes and fixes for regressions only.

Because the automatic updates in Firefox are disabled, the average user won't even know what Firefox 3.5 is or that it even exists, so they won't care. Remember - average Windows user will only upgrade their browser when it pesters them to do so. As already pointed out, the people who care can easily install from a PPA (and firefox-3.5 is even in universe anyway).

The other issue is that there are lots of applications that are linked to xulrunner. Updating the default version of Firefox would require porting all users to the new version of xulrunner, so the regression potential isn't just with Firefox itself. All of these need to be ported and tested (which is also a lot of work):
```
chr1s@chris-desktop:~$ apt-cache rdepends xulrunner-1.9
xulrunner-1.9
Reverse Depends:
 |moonlight-plugin-mozilla
  xulrunner-1.9-venkman
  xulrunner-1.9-dom-inspector
  xulrunner-1.9-gnome-support
  xulrunner-1.9-dev
  firefox-3.0
  xulrunner-1.9-dbgsym
  xulrunner-1.9-dbgsym
  flashplugin-installer
  xulrunner-1.9-venkman
  xulrunner-1.9-dom-inspector
  videolink
  tuxguitar
  sugar-web-activity
  python-hulahop
  prism
 |mozplugger
  mozilla-nukeimage
 |mozilla-helix-player
 |moonlight-plugin-mozilla
  miro
  midbrowser
  listen
  libswt-mozilla-gtk-3.4-jni
  libgtk-mozembed-ruby1.8
  libgecko2.0-cil
  kazehakase-gecko
  gnome-web-photo
  galeon
  evolution-rss
  conkeror
  chmsee
  yelp
  xulrunner-1.9-gnome-support
  xulrunner-1.9-dev
  liferea
  firefox-3.0
  epiphany-gecko

```

---

### Post by aysiu on 2009-07-07
> **Merk42 said:**
> Considering you said about most users waiting until October I took you to only be talking about Ubuntu users.
Go back and re-read [my comment in the context of what I was replying to](http://ubuntuforums.org/showpost.php?p=7573678&postcount=42). It should make more sense.

---

### Post by Merk42 on 2009-07-07
> **aysiu said:**
> Go back and re-read [my comment in the context of what I was replying to](http://ubuntuforums.org/showpost.php?p=7573678&postcount=42). It should make more sense.

Well I still think it could be read either way...

So let's re-ask the question, but only pertaining to Ubuntu users.

Would you say that a good deal of **Ubuntu users** have no idea that Firefox 3.5 have been released?  That they could wait until October and some (Hardy users) would still be using it post October and be none the wiser?

---

### Post by aysiu on 2009-07-07
> **Merk42 said:**
> Well I still think it could be read either way...

So let's re-ask the question, but only pertaining to Ubuntu users.

Would you say that a good deal of **Ubuntu users** have no idea that Firefox 3.5 have been released?  That they could wait until October and some (Hardy users) would still be using it post October and be none the wiser?
I think the current population of Ubuntu users would like to have Firefox 3.5 in Jaunty, but I also think as a group they are perfectly capable of copying and pasting one single command into the terminal to get it.

Simplistically speaking (we can get into finer categories if you want), there are two kinds of users--power users and average users. Average users I would define as not self-sufficient--they are more likely to ask for help with computers than to give help. Power users are the opposite. They are the computer problem go-to people in families or among a circle of a friends.

If so-called average users are using Ubuntu, they won't care about getting Firefox 3.5 before October. They'll generally have no idea that Firefox 3.5 even came out at all.

If so-called power users are using Ubuntu, they should have the know-how to use their mouse to highlight a single command, right-click it, copy it, and then open a terminal, right-click, and paste the command, and hit Enter.

I'm just getting tired of users like X-BANE pretending that Ubuntu would never make it with so-called average users, because of Firefox not being updated immediately. The vast majority of computer users have no idea Firefox 3.5 just came out. They don't care about getting the latest version of Firefox right away, within a few months, or even within a year.

---

### Post by Quake on 2009-07-07
Firefox 3.5 is now available on Ubuntu 9.04's default repository. It doesn't replace Firefox 3.0 but rather copies your current profile.

---

### Post by Merk42 on 2009-07-07
> **aysiu said:**
> I think the current population of Ubuntu users would like to have Firefox 3.5 in Jaunty, but I also think as a group they are perfectly capable of copying and pasting one single command into the terminal to get it.

Simplistically speaking (we can get into finer categories if you want), there are two kinds of users--power users and average users. Average users I would define as not self-sufficient--they are more likely to ask for help with computers than to give help. Power users are the opposite. They are the computer problem go-to people in families or among a circle of a friends.

If so-called average users are using Ubuntu, they won't care about getting Firefox 3.5 before October. They'll generally have no idea that Firefox 3.5 even came out at all.

If so-called power users are using Ubuntu, they should have the know-how to use their mouse to highlight a single command, right-click it, copy it, and then open a terminal, right-click, and paste the command, and hit Enter.

I'm just getting tired of users like X-BANE pretending that Ubuntu would never make it with so-called average users, because of Firefox not being updated immediately. The vast majority of computer users have no idea Firefox 3.5 just came out. They don't care about getting the latest version of Firefox right away, within a few months, or even within a year.

Well I think there's a bit of a flaw in that breakdown (maybe because you were being overly general).

You're assuming that the people that would want Firefox 3.5 would be savvy enough to know how to install it.  If that were the case, why are/were there so many threads about how to get it?

Also, I installed the firefox-3.5 package, which finally updated yesterday, but it's still Shiretoko. I'm also not savvy enough to know how to get it to default to 3.5 and not 3.0.11.  That step I think more than "sudo apt-get firefox-3.5"

---

### Post by kickwin on 2009-07-07
> **aysiu said:**
> 
If so-called average users are using Ubuntu, they won't care about getting Firefox 3.5 before October. They'll generally have no idea that Firefox 3.5 even came out at all.

I beg to differ. IMO, what you have said would be true for average Windows users but not for average or even novice Ubuntu users. 

Is it now for sure that firefox won't be updated to 3.5 before October?

---

### Post by aysiu on 2009-07-07
> **Merk42 said:**
> Well I think there's a bit of a flaw in that breakdown (maybe because you were being overly general).

You're assuming that the people that would want Firefox 3.5 would be savvy enough to know how to install it.  If that were the case, why are/were there so many threads about how to get it?

Also, I installed the firefox-3.5 package, which finally updated yesterday, but it's still Shiretoko. I'm also not savvy enough to know how to get it to default to 3.5 and not 3.0.11.  That step I think more than "sudo apt-get firefox-3.5"
Well, with anything *new* there is a learning curve. That's wwhy people post threads. When I was a new Ubuntu user, I asked many of the same questions.

Now that I've had a few years of Ubuntu under my belt, I'm not expert, but I know how to install the newest Firefox. I also created a little tutorial for new users on how to do it:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

If you are using Ubuntu now, you are an early adopter. That's a fact. If you're an early adopter, you may have to do a little more legwork than someone who comes on when more of an infrastructure is in place.

And, you're also being a bit of a sacrificial lamb. The early adopters are very helpful in getting Ubuntu going, but they are not ultimately Ubuntu's target audience. If they were, this would be called "Ubuntu: Linux for Geeks," not "Ubuntu: Linux for Human Beings" (of course, geeks are, by definition, also human beings, but it's meant to be a little tongue-in-cheek). Ubuntu also would be a rolling release with a lot of breakage and beta software. It would have a lot of confusing options during installation about what software packages you want installed or not installed.

If you're a power user, you can easily do a Google search for "install firefox 3.5 jaunty" and install it yourself. If you're an average user, you can easily wait until October to get it... or even just stick with Firefox 3.0.

We're just in an awkward place right now, because Ubuntu's ultimate target audience is not its current primary userbase.

---

### Post by aysiu on 2009-07-07
> **kickwin said:**
> I beg to differ. IMO, what you have said would be true for average Windows users but not for average or even novice Ubuntu users. 

Is it now for sure that firefox won't be updated to 3.5 before October?
I'm starting to get a little annoyed here. Are people even reading my posts before responding to them? [quote=aysiu]**If so-called average users are using Ubuntu**, they won't care about getting Firefox 3.5 before October. They'll generally have no idea that Firefox 3.5 even came out at all.[/quote] Most of the current novice Ubuntu users are not so-called average users. They are Windows power users who are only novices in the sense that they are new to Ubuntu and the world of Linux, not that they are novice computer users.

I've said what I've had to say. At this point I'm just repeating myself. If you want more details, read [An Experiment in Ubuntu. For Windows Users.](http://ubuntuforums.org/showthread.php?t=1205956)

---

### Post by jpeddicord on 2009-07-07
Merged the two threads in here on this.

---

### Post by Simian Man on 2009-07-07
It's not a question of "average users vs. power users".  There are average users who want to have the latest software but aren't necessarily the most technically inclined.  There are also people who have great technical skills but don't care about, or want, the latest releases (think Slackware users).  I think that assuming average users don't know or care about upgrades and power users do is a bit silly.

In general, if you want the latest software, Ubuntu is not the distribution for you.

---

### Post by gtr225 on 2009-07-07
I think I agree with aysiu. If you want Firefox 3.5 that bad, go get it yourself. If your too lazy to get it yourself, you can wait till October.

---

### Post by jpeddicord on 2009-07-07
> **gtr225 said:**
> I think I agree with aysiu. If you want Firefox 3.5 that bad, go get it yourself. If your too lazy to get it yourself, you can wait till October.

Well said.

---

### Post by Closed_Port on 2009-07-07
> **gtr225 said:**
> I think I agree with aysiu. If you want Firefox 3.5 that bad, go get it yourself. If your too lazy to get it yourself, you can wait till October.

Argh!
Repeat after me: 
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.
It's in the repos, you just have to install it.

---

### Post by Merk42 on 2009-07-07
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default

---

### Post by lovinglinux on 2009-07-07
> **Merk42 said:**
> The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default


I have updated the "Installing Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567) with a detailed explanation of each installation method provided, comparing the most important differences.

---

### Post by Quake on 2009-07-07
> **Merk42 said:**
> The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default
The branding is still Shiretoko, and it doesn't make it default

It will be the default browser in Ubuntu 9.10. And even though the banding is Shiretoko, it's Firefox 3.5.

So basically, you'll have Firefox 3.0 and Firefox 3.5 on your computer.

---

### Post by Merk42 on 2009-07-07
> **lovinglinux said:**
> I have updated the "Installing Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567) with a detailed explanation of each installation method provided, comparing the most important differences.
Thank you for the update, I'll read through it later.


> **Quake said:**
> It will be the default browser in Ubuntu 9.10. And even though the banding is Shiretoko, it's Firefox 3.5.

So basically, you'll have Firefox 3.0 and Firefox 3.5 on your computer.
I know all that, I'm just saying a user that would install **firefox-3.5** through the repositories would expect something called **firefox** to be installed.  They might also expect the new version to replace the old and/or become the new default.

All I'm saying is that lot of users that want 3.5 don't know about it being in the repositories (which up until the other day were still beta).  Even if they do know about it, it most likely does not result in the expected behavior.

---

### Post by Simian Man on 2009-07-08
> **gtr225 said:**
> I think I agree with aysiu. If you want Firefox 3.5 that bad, go get it yourself. If your too lazy to get it yourself, you can wait till October.

The point of repositories is to avoid things like this.  Sure you could install it by circumventing the package manager, but having to do that is a hassle.  Ubuntu has big repos, but there's not much benefit of that when many of the applications are out of date :\.

The fact is Firefox is a major application (probably the most important for most users), and 3.5 is a major release.  I can understand not providing it for older releases like 8.04 and 8.10, but not providing this update for the current release is just ridiculous.  People have a right to be peeved at that.

---

### Post by Closed_Port on 2009-07-08
> **Simian Man said:**
> The point of repositories is to avoid things like this.  Sure you could install it by circumventing the package manager, but having to do that is a hassle.  Ubuntu has big repos, but there's not much benefit of that when many of the applications are out of date :\.

The fact is Firefox is a major application (probably the most important for most users), and 3.5 is a major release.  I can understand not providing it for older releases like 8.04 and 8.10, but not providing this update for the current release is just ridiculous.  People have a right to be peeved at that.

I agree with much of what you say, but I'd like to point out again that Ubuntu is providing firefox 3.5.

---

### Post by 23meg on 2009-07-08
> **Closed_Port said:**
> I agree with much of what you say, but I'd like to point out again that Ubuntu is providing firefox 3.5.

And I'd like to repeat that Ubuntu is providing Firefox 3.5 **through an exception** to its regular policy regarding stable release updates. This policy is listed on a public website, is widely known (as well as being widely unknown), and **ideally, should be taken into consideration by people who set out to decide whether or not to use Ubuntu at all**. The more that happens, the less damage we take from the social problem of people "being peeved" about things a while after they started using Ubuntu, because they didn't know a basic fact about Ubuntu.

---

### Post by brookie on 2009-07-08
> **izizzle said:**
> We wait till they release 9.10.

i hope not. i couldn't even get 9.04 to work on my machine. maybe some of us (me) should be more worried about upgrading our old machines, rather than upgrading our browsers. hee hee. :)

---

### Post by sertse on 2009-07-08
> **Simian Man said:**
>  People have a right to be peeved at that.

No, they don't. Ubuntu actually has the right to be peeved at users "culture of entitlement". It is the user's fault for expecting Ubuntu to do something that is outside it's purpose. There are already reasonable reasons given as to why Ubuntu sticks to 3.0.X in Jaunty.

---

### Post by Closed_Port on 2009-07-08
> **23meg said:**
> And I'd like to repeat that Ubuntu is providing Firefox 3.5 **through an exception** to its regular policy regarding stable release updates. This policy is listed on a public website, is widely known (as well as being widely unknown), and **ideally, should be taken into consideration by people who set out to decide whether or not to use Ubuntu at all**. The more that happens, the less damage we take from the social problem of people "being peeved" about things a while after they started using Ubuntu, because they didn't know a basic fact about Ubuntu.
I think people would still be peeved, after all, Ubuntu is a general operating system and to many people that means that they should be able to easily install newer software.

And though I found most of the drama about ff 3.5 in ubuntu simply silly, I don't think people being peeved is necessarily a bad thing. On the contrary, it helps ubuntu evolve.

For example iirc that's how we got backports. As far as I recall it started out as a project outside of ubuntu and there were many discussions about what to do with it but finally it became part of ubuntu. Now, if people had done as you want them to do, this wouldn't have happened.

Now, personally I think not making newer software more easily available to it's users is one of the weak points of Ubuntu. That doesn't mean that I know how to solve this problem, I don't, but in my opinion this is a part of ubuntu that can and should improve.

---

### Post by 23meg on 2009-07-08
> **Closed_Port said:**
> I think people would still be peeved, after all, Ubuntu is a general operating system and to many people that means that they should be able to easily install newer software.

Even though there is some room for improvement, people *can* easily install most newer software in Ubuntu, "easily" and "newer" being somewhat relative. That doesn't mean they don't have to learn anything new, or that they don't have to know about the consequences of at least the most basic Ubuntu policies, or that they won't occasionally have to deal with some inconveniences (as is the case with all other operating systems).

> **Closed_Port said:**
> And though I found most of the drama about ff 3.5 in ubuntu simply silly, I don't think people being peeved is necessarily a bad thing. On the contrary, it helps ubuntu evolve.

For example iirc that's how we got backports. As far as I recall it started out as a project outside of ubuntu and there were many discussions about what to do with it but finally it became part of ubuntu. Now, if people had done as you want them to do, this wouldn't have happened.

The "being peeved" that I define as a problem is being peeved and doing nothing other than complaining and spreading misinformation as a result of it. What you're talking about is being dissatisfied with the state of things as they are, and doing something to fix them, and to the contrary, that's exactly what I want more of. I'd like more people to *be aware of* the consequences of Ubuntu's current policies; not accept them as a fate and be done with them.

---

### Post by Closed_Port on 2009-07-08
> **23meg said:**
> 
The "being peeved" that I define as a problem is being peeved and doing nothing other than complaining and spreading misinformation as a result of it. What you're talking about is being dissatisfied with the state of things as they are, and doing something to fix them, and to the contrary, that's exactly what I want more of. I'd like more people to *be aware of* the consequences of Ubuntu's current policies; not accept them as a fate and be done with them.
Then I misunderstood you and I totally agree.

---

### Post by kingofpain on 2009-07-08
OK ok, lots of guys here saying that Ubuntu is providing in fact Firefox 3.5. But I have a question: if so, why is called Shiretoko and not Firefox? And why the shortcut to Shiretoko in the main menu of Ubuntu says "Firefox 3.5 BETA"? Somebody forgot to change this? :-k
And what's this "Mozilla Firefox for Ubuntu" thing? Firefox is independent platform and can be run directly from an extrated archive (like eclipse). Why does it need a special build for Ubuntu? Eclipse has a build for Ubuntu?

---

### Post by Closed_Port on 2009-07-08
> **kingofpain said:**
> OK ok, lots of guys here saying that Ubuntu is providing in fact Firefox 3.5. But I have a question: if so, why is called Shiretoko and not Firefox? 

Alexander Sack of the ubuntu mozilla team explains their reasons on his blog:
[http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html](http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html)

> **kingofpain said:**
> 
And why the shortcut to Shiretoko in the main menu of Ubuntu says "Firefox 3.5 BETA"? Somebody forgot to change this? :-k

That's probably exactly what happened.

> **kingofpain said:**
> 
And what's this "Mozilla Firefox for Ubuntu" thing? Firefox is independent platform and can be run directly from an extrated archive (like eclipse). Why does it need a special build for Ubuntu? Eclipse has a build for Ubuntu?
It doesn't need a special build for ubuntu and most software could probably be run from an extracted archive. However, that's not how software management works on linux and that's not how it is supposed to work. For example, package manager make it a lot easier for you and your system to keep track of the installed software, keep it updated, etc. 

As for eclipse:
[http://packages.ubuntu.com/search?keywords=eclipse&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=eclipse&searchon=names&suite=jaunty&section=all)

---

### Post by Merk42 on 2009-07-08
> **23meg said:**
> The "being peeved" that I define as a problem is being peeved and doing nothing other than complaining and spreading misinformation as a result of it. What you're talking about is being dissatisfied with the state of things as they are, and doing something to fix them, and to the contrary, that's exactly what I want more of. I'd like more people to *be aware of* the consequences of Ubuntu's current policies; not accept them as a fate and be done with them.

I know you and I have butted heads before about my being dissatisfied.
What then should I do about my dissatisfaction about how this is handled? Again I don't mind having to install the firefox-3.5 package, I just dislike the behavior of said package.
There are already bugs telling it to at least change the user agent to Firefox, and, if the link Closed_Port is true, changing Shiretoko to Firefox in the menu seems to be WON'T FIX

I just feel this sort of thing will probably happen again with 3.6 in Karmic (or Karmic+1).  This, like possbily the backports, needs to be a situation where Canonical may need to think about how they handle these situations for the future.

---

### Post by 23meg on 2009-07-09
> **Merk42 said:**
> I know you and I have butted heads before about my being dissatisfied.
What then should I do about my dissatisfaction about how this is handled?

You can (possibly along with a group of volunteers) package a branded Firefox 3.5 that replaces Firefox 3.0 in your PPA. It's going to be quite a bit of work maintaining all the required library upgrades if you want your users to have a good experience, and that may help you understand the rationale behind the policies that lead to your dissatisfaction. Which brings us to:

You can also spare some time to ask around and learn the rationales behind the current stable release update and branding policies, as well as the  upcoming package archive reorganization; that will certainly help you in devising possible future solutions. 

You may also want to provide better and more popular documentation on Ubuntu's update policy targeted to new users, or on upgrading to Firefox 3.5, that alleviates the dissatisfaction for those dissatisfied the same way you were.

---

### Post by chrisccoulson on 2009-07-09
> **23meg said:**
> It's going to be quite a bit of work maintaining all the required library upgrades if you want your users to have a good experience, and that may help you understand the rationale behind the policies that lead to your dissatisfaction. 

I know this link has already been posted somewhere in this thread, but for an idea of the level of work involved to migrate to Firefox-3.5 by default whilst maintaining a good, consistent user experience for everybody, then the desktop-karmic-firefox-3.5 blueprint is well worth a read:
[https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-karmic-firefox-3.5]("https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-karmic-firefox-3.5")

It's not just a case of dropping Firefox 3.5 in. It involves many other parts of the desktop too, and is quite a significant amount of work, requiring a lot of testing (which is exactly what is currently happening in Karmic).

---

### Post by pastalavista on 2009-07-09
I like Shiretoko. Everybody's got regular old Firefox. Ubuntu should just keep the Shiretoko name.. if Mozilla wouldn't mind.

---

### Post by gtr225 on 2009-07-09
I still can't figure out the problem here. I installed Firefox 3.5, made it the default browser for me and installed the user agent switcher for some sites that don't recognize Shiretoko and instead have it set to Firefox 3.5. Now everything works flawlessly for me. I don't understand why this is still an issue.

---

### Post by Merk42 on 2009-07-10
> **gtr225 said:**
> I still can't figure out the problem here. I installed Firefox 3.5, made it the default browser for me and installed the user agent switcher for some sites that don't recognize Shiretoko and instead have it set to Firefox 3.5. Now everything works flawlessly for me. I don't understand why this is still an issue.

My issue is that making it default and changing it from Shiretoko to Firefox doesn't happen automatically.

How did you personally go about doing it? I saw some youtube video about renaming things in /usr/bin

---

### Post by lswest on 2009-07-10
> **Merk42 said:**
> How did you personally go about doing it? I saw some youtube video about renaming things in /usr/bin

What he probably did was go to System-->Preferences-->Preferred Applications, and change the default web browser to the /usr/bin/firefox-3.5 file.

The user agent switcher is an extension for firefox, and allows you to set up custom profiles to make Firefox seem like some other web browser running on a different platform (if you so want).

---

### Post by gtr225 on 2009-07-10
> **lswest said:**
> What he probably did was go to System-->Preferences-->Preferred Applications, and change the default web browser to the /usr/bin/firefox-3.5 file.

The user agent switcher is an extension for firefox, and allows you to set up custom profiles to make Firefox seem like some other web browser running on a different platform (if you so want).

That's exactly what I did. The reason I use the user agent switcher was for [www.facebook.com](www.facebook.com) and [www.slacker.com](www.slacker.com) which seem to think Shiretoko is an incompatible browser. So instead it addresses itself as Firefox 3.5. Also in addition to that I removed the Firefox shortcut on my top panel and replaced it with Shiretoko. I hope this can end all the pointless complaining.

---

### Post by Merk42 on 2009-07-12
> **gtr225 said:**
> I hope this can end all the pointless complaining.

Yes, pointless, users aren't allowed to express dissatisfaction with anything Ubuntu.  How dare they not love everything 100%! Or well I suppose since **you** don't agree with it, it's pointless.

I am going to look into the link chrisccoulson posted to actually contribute. Although that has to do with Karmic, where's the stuff on the Jaunty package? I see [this](https://launchpad.net/ubuntu/jaunty/+package/firefox-3.5), but no discussion and given the lack of branding I don't consider it 'done'
Where would I go to ask about "the rationales behind the current stable release update and branding policies, as well as the upcoming package archive reorganization"? Even if I did find someone wouldn't they basically say "well that's how it is so take it or leave it"?

It just boggles my mind how this stuff works

**Windows**: Firefox notifies user of new version, user clicks OK everything gets upgraded
**OSX**: Firefox notifies user of new version, user clicks OK everything gets upgraded
**Ubuntu**: No notification, user does sudo apt-get firefox-3.5, gets Shiretoko instead, has to manually change shortcuts and branding and get an extension to make some websites (like aforementioned Facebook) work.

---

### Post by gtr225 on 2009-07-12
> **Merk42 said:**
> Yes, pointless, users aren't allowed to express dissatisfaction with anything Ubuntu.  How dare they not love everything 100%! Or well I suppose since **you** don't agree with it, it's pointless.

I am going to look into the link chrisccoulson posted to actually contribute. Although that has to do with Karmic, where's the stuff on the Jaunty package? I see [this](https://launchpad.net/ubuntu/jaunty/+package/firefox-3.5), but no discussion and given the lack of branding I don't consider it 'done'
Where would I go to ask about "the rationales behind the current stable release update and branding policies, as well as the upcoming package archive reorganization"? Even if I did find someone wouldn't they basically say "well that's how it is so take it or leave it"?

It just boggles my mind how this stuff works

**Windows**: Firefox notifies user of new version, user clicks OK everything gets upgraded
**OSX**: Firefox notifies user of new version, user clicks OK everything gets upgraded
**Ubuntu**: No notification, user does sudo apt-get firefox-3.5, gets Shiretoko instead, has to manually change shortcuts and branding and get an extension to make some websites (like aforementioned Facebook) work.
I find this pointless because a workaround has been found. At first when I read 3.5 came out I was pissed waiting for an update. I searched the forums, found this thread, and installed the package from the repositories. Making it the default and changing the user agent I figured out on my own. I hate to say it but you guys are being real lazy. Yes it would be lovely if Firefox 3.5 would auto-update in Ubuntu, but that would go against the Ubuntu update policy. However, they offer it in the repositories. And if that's not easy enough for you, you can go to [www.getfirefox.com](www.getfirefox.com), download the tar.gz file, unzip it and run it from there. Problem solved, end of discussion.

---

### Post by Merk42 on 2009-07-12
> **gtr225 said:**
> I find this pointless because a workaround has been found. At first when I read 3.5 came out I was pissed waiting for an update. I searched the forums, found this thread, and installed the package from the repositories. Making it the default and changing the user agent I figured out on my own. I hate to say it but you guys are being real lazy. Yes it would be lovely if Firefox 3.5 would auto-update in Ubuntu, but that would go against the Ubuntu update policy. However, they offer it in the repositories. And if that's not easy enough for you, you can go to [www.getfirefox.com](www.getfirefox.com), download the tar.gz file, unzip it and run it from there. Problem solved, end of discussion.

I have no problem with having to install the package.
I have a problem with the package being lacking branding which causes incompatibility (and possibly confusion to users).

It just seems sort of half-done.  Why bother updating the package from beta4 if you're not going to fully update it?
Don't give me that "go to website etc" answer, then why does Ubuntu ever bother upgrading packages at all?  I mean, why do the transition to 3.5 for Karmic, or upgrade Jaunty to OOo 3 instead of 2? After all, the user could just manually do it.

---

### Post by steeleyuk on 2009-07-12
Its all about support from Canonical's perspective. If you expect users to do their own donkey work, of which there are several ways to install apps, how do you expect to support them?

---

### Post by monsterstack on 2009-07-12
> **Merk42 said:**
> I have no problem with having to install the package.
I have a problem with the package being lacking branding which causes incompatibility (and possibly confusion to users).

It just seems sort of half-done.  Why bother updating the package from beta4 if you're not going to fully update it?
Don't give me that "go to website etc" answer, then why does Ubuntu ever bother upgrading packages at all?  I mean, why do the transition to 3.5 for Karmic, or upgrade Jaunty to OOo 3 instead of 2? After all, the user could just manually do it.

As others have explained elsewhere in this thread, [here](http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html")'s your reason:

> 11:11 < asac> we only use official branding for our default browser
11:11 < asac> (default for jaunty is 3.0)
11:11 < asac> also we explicitly want both to be installable side by side
11:11 < asac> and same branding would make them indistinguishable on your desktop
11:11 < asac> another point to consider is that branding is part of top-level UI
11:11 < asac> and changing (top-level) UI is not something we do in stable/security updates anyway

Can everybody stop complaining now? Please?

---

### Post by Closed_Port on 2009-07-12
> **Merk42 said:**
> 
I have a problem with the package being lacking branding which causes incompatibility (and possibly confusion to users).

The branding is not the problem and doesn't cause the incompatibility. The problem is the wrong useragent and the useragent has nothing to do with branding.

That said, the wrong useragent is simply a bug and the best way to go about it is probably to file a bug report.

> **Merk42 said:**
> 
It just seems sort of half-done.  Why bother updating the package from beta4 if you're not going to fully update it?

But they did fully update it.

---

### Post by Merk42 on 2009-07-12
> **Closed_Port said:**
> The branding is not the problem and doesn't cause the incompatibility. The problem is the wrong useragent and the useragent has nothing to do with branding.

That said, the wrong useragent is simply a bug and the best way to go about it is probably to file a bug report.


But they did fully update it.

I apologize for the confusion about branding/useragent. I have [filed a bug](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/398525) about the incompatibility.
EDIT apparently it was a duplicate, odd as I didn't see it when I searched before hand.
Oh well, I guess that just means other people "pointlessly complained" about this as well.

---

### Post by Closed_Port on 2009-07-12
> **Merk42 said:**
> I apologize for the confusion about branding/useragent. I have [filed a bug](https://bugs.edge.launchpad.net/ubuntu/+source/ubufox/+bug/347972/comments/23) about the incompatibility.
EDIT apparently it was a duplicate, odd as I didn't see it when I searched before hand.
Oh well, I guess that just means other people "pointlessly complained" about this as well.
Could you post a link to the bug? Your link goes to a comment on a different bug report.
Thanks.

---

### Post by gtr225 on 2009-07-12
I'm only 24, but I'm feeling like an old man here. I remember the days of Red Hat 9 where I had to manually compile GAIM and all it's dependencies just to get the GTK2 version of it working. Now we have users complaining about branding in Firefox 3.5 as if it's a real problem? I'm sorry to all who disagree, I do understand your issue, but there is so much more important work out there to be done to Ubuntu that this minor issue really needs to take a back seat. If only everyone here was as passionate about Firefox 3.5 auto-updating as they were spreading Ubuntu around to friends and family, then we might be getting somewhere.

---

### Post by Merk42 on 2009-07-12
> **Closed_Port said:**
> Could you post a link to the bug? Your link goes to a comment on a different bug report.
Thanks.

Oh sorry, wrong URL, that was the link I had saying that I figured it'd go under Won't Fix

[My bug](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/398525)
[The pre-existing bug](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211)

> **gtr225 said:**
> ...If only everyone here was as passionate about Firefox 3.5 auto-updating as they were spreading Ubuntu around to friends and family, then we might be getting somewhere.

I do spread the word, convinced my brother to get the (Dell) Ubuntu version of his Netbook.

---

### Post by gtr225 on 2009-07-12
> **Merk42 said:**
> Oh sorry, wrong URL, that was the link I had saying that I figured it'd go under Won't Fix

[My bug](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/398525)
[The pre-existing bug](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211)



I do spread the word, convinced my brother to get the (Dell) Ubuntu version of his Netbook.

That's great

---

### Post by dicairo on 2009-07-12
i tried firefox 3.5 from synapatic, but it does not work well i was unable to chat on facebook, the search engine does not work and i cant copy any text .
So i downloaded it from mozilla and its work pretty fast and for the moment every thing is ok. At the end i was preferring  do a simple update but i think that canonical team does not have time hahahahh:p  so i did it with my self

---

### Post by Closed_Port on 2009-07-12
> **Merk42 said:**
> Oh sorry, wrong URL, that was the link I had saying that I figured it'd go under Won't Fix

[My bug](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/398525)
[The pre-existing bug](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211)

Thanks!

---

### Post by gtr225 on 2009-07-12
> **dicairo said:**
> i tried firefox 3.5 from synapatic, but it does not work well i was unable to chat on facebook, the search engine does not work and i cant copy any text .
So i downloaded it from mozilla and its work pretty fast and for the moment every thing is ok. At the end i was preferring  do a simple update but i think that canonical team does not have time hahahahh:p  so i did it with my self

As I mentioned, because of the user agent being Shiretoko, Facebook won't work properly unless you use a user agent switcher.

---

### Post by 23meg on 2009-07-12
> **Merk42 said:**
> Yes, pointless, users aren't allowed to express dissatisfaction with anything Ubuntu.  How dare they not love everything 100%! Or well I suppose since **you** don't agree with it, it's pointless.

The classic straw man, once again. Never gets old.

Many users *have* expressed their dissatisfaction, in this thread and others. They've been given what I think are polite and satisfactory explanations as to why things work the way they work. They can keep expressing the same dissatisfaction in slightly different terms, like you've been, but that won't help them fix their dissatisfaction, or help anyone else help them.

And by the way, aren't other people in turn allowed to express *their* dissatisfaction with the way some users express their dissatisfaction? 

> **Merk42]Where would I go to ask about "the rationales behind the current stable release update and branding policies, as well as the upcoming package archive reorganization"?[/QUOTE]

The [ubuntu-devel-discuss mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss"), or if you want it Mozilla-specific, the [ubuntu-mozillateam list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-mozillateam"). (or the respective IRC channels: #ubuntu-devel or #ubuntu-mozilla on Freenode). If you visit those places, please don't start out demanding and complaining about things like you've been doing here all along. That will make it more likely for the relevant people to respond to you.

[QUOTE=Merk42]Even if I did find someone wouldn't they basically say "well that's how it is so take it or leave it"?[/QUOTE]

They will probably say "That's how it works said:**
> **Windows**: Firefox notifies user of new version, user clicks OK everything gets upgraded
**OSX**: Firefox notifies user of new version, user clicks OK everything gets upgraded

Right, except that:

**Windows**: User does not get the advantages of shared libraries, centralized software repositories, unified translations, vendor-specific patches, vendor-side integration, extensions in repositories, vendor guarantee of security updates for OS support period.

**OSX**: User does not get the advantages of shared libraries, centralized software repositories, unified translations, vendor-specific patches, vendor-side integration, extensions in repositories, vendor guarantee of security updates for OS support period.

In Ubuntu, you get all of those. And if you don't care about those, you can grab a binary straight from Mozilla and run it. You'll be able to update it to the latest release as soon as it's out, exactly like in the Windows and OSX builds.

Good bargain? Use Ubuntu. Not a good bargain? Stop using Ubuntu and use an alternative (not necessarily Windows or OSX), or stop complaining and preferably start working on measures to alleviate the inconvenience for others who also may not think it's a good bargain in the short term, and/or on fixing it in the long term.

---

### Post by gtr225 on 2009-07-12
> **23meg said:**
> The classic straw man, once again. Never gets old.

Many users *have* expressed their dissatisfaction, in this thread and others. They've been given what I think are polite and satisfactory explanations as to why things work the way they work. They can keep expressing the same dissatisfaction in slightly different terms, like you've been, but that won't help them fix their dissatisfaction, or help anyone else help them.

And by the way, aren't other people in turn allowed to express *their* dissatisfaction with the way some users express their dissatisfaction? 



The [ubuntu-devel-discuss mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss"), or if you want it Mozilla-specific, the [ubuntu-mozillateam list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-mozillateam"). (or the respective IRC channels: #ubuntu-devel or #ubuntu-mozilla on Freenode). If you visit those places, please don't start out demanding and complaining about things like you've been doing here all along. That will make it more likely for the relevant people to respond to you.



They will probably say "That's how it works; here's why it works that way, and here are the conditions that need to change in order for it to work another way in the future. If you can help make those conditions change, that will make it more likely that things will work how you want in the future."



Right, except that:

**Windows**: User does not get the advantages of shared libraries, centralized software repositories, unified translations, vendor-specific patches, vendor-side integration, extensions in repositories, vendor guarantee of security updates for OS support period.

**OSX**: User does not get the advantages of shared libraries, centralized software repositories, unified translations, vendor-specific patches, vendor-side integration, extensions in repositories, vendor guarantee of security updates for OS support period.

In Ubuntu, you get all of those. And if you don't care about those, you can grab a binary straight from Mozilla and run it. You'll be able to update it to the latest release as soon as it's out, exactly like the Windows and OSX builds.

Good bargain? Use Ubuntu. Not a good bargain? Stop using Ubuntu and use an alternative (not necessarily Windows or OSX), or stop complaining and preferably start working on measures to alleviate the inconvenience for others who also may not think it's a good bargain in the short term, and/or on fixing it in the long term.

Well said

---

### Post by lovinglinux on 2009-07-13
> **23meg said:**
> The classic straw man, once again. Never gets old.

Many users *have* expressed their dissatisfaction, in this thread and others. They've been given what I think are polite and satisfactory explanations as to why things work the way they work. They can keep expressing the same dissatisfaction in slightly different terms, like you've been, but that won't help them fix their dissatisfaction, or help anyone else help them.

And by the way, aren't other people in turn allowed to express *their* dissatisfaction with the way some users express their dissatisfaction? 



The [ubuntu-devel-discuss mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss"), or if you want it Mozilla-specific, the [ubuntu-mozillateam list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-mozillateam"). (or the respective IRC channels: #ubuntu-devel or #ubuntu-mozilla on Freenode). If you visit those places, please don't start out demanding and complaining about things like you've been doing here all along. That will make it more likely for the relevant people to respond to you.



They will probably say "That's how it works; here's why it works that way, and here are the conditions that need to change in order for it to work another way in the future. If you can help make those conditions change, that will make it more likely that things will work how you want in the future."



Right, except that:

**Windows**: User does not get the advantages of shared libraries, centralized software repositories, unified translations, vendor-specific patches, vendor-side integration, extensions in repositories, vendor guarantee of security updates for OS support period.

**OSX**: User does not get the advantages of shared libraries, centralized software repositories, unified translations, vendor-specific patches, vendor-side integration, extensions in repositories, vendor guarantee of security updates for OS support period.

In Ubuntu, you get all of those. And if you don't care about those, you can grab a binary straight from Mozilla and run it. You'll be able to update it to the latest release as soon as it's out, exactly like in the Windows and OSX builds.

Good bargain? Use Ubuntu. Not a good bargain? Stop using Ubuntu and use an alternative (not necessarily Windows or OSX), or stop complaining and preferably start working on measures to alleviate the inconvenience for others who also may not think it's a good bargain in the short term, and/or on fixing it in the long term.

Well said indeed.

---

### Post by gtr225 on 2009-07-13
Just noticed a quick way to fix the Shiretoko user agent permanently, without installing an extenstion. Go to about:config and find the string general.useragent.extra.firefox . Change that string from Shiretoko/3.5 to Firefox/3.5 and [www.facebook.com](www.facebook.com) and [www.slacker.com](www.slacker.com) now work perfectly all the time. You will notice the difference in Help --> About Shiretoko.

---

### Post by K.Mandla on 2009-07-13
> **23meg said:**
> the classic straw man, once again. Never gets old.

Many users *have* expressed their dissatisfaction, in this thread and others. They've been given what i think are polite and satisfactory explanations as to why things work the way they work. They can keep expressing the same dissatisfaction in slightly different terms, like you've been, but that won't help them fix their dissatisfaction, or help anyone else help them.

And by the way, aren't other people in turn allowed to express *their* dissatisfaction with the way some users express their dissatisfaction? 



The [ubuntu-devel-discuss mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss"), or if you want it mozilla-specific, the [ubuntu-mozillateam list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-mozillateam"). (or the respective irc channels: #ubuntu-devel or #ubuntu-mozilla on freenode). If you visit those places, please don't start out demanding and complaining about things like you've been doing here all along. That will make it more likely for the relevant people to respond to you.



They will probably say "that's how it works; here's why it works that way, and here are the conditions that need to change in order for it to work another way in the future. If you can help make those conditions change, that will make it more likely that things will work how you want in the future."



right, except that:

**windows**: User does not get the advantages of shared libraries, centralized software repositories, unified translations, vendor-specific patches, vendor-side integration, extensions in repositories, vendor guarantee of security updates for os support period.

**osx**: User does not get the advantages of shared libraries, centralized software repositories, unified translations, vendor-specific patches, vendor-side integration, extensions in repositories, vendor guarantee of security updates for os support period.

In ubuntu, you get all of those. And if you don't care about those, you can grab a binary straight from mozilla and run it. You'll be able to update it to the latest release as soon as it's out, exactly like in the windows and osx builds.

Good bargain? Use ubuntu. Not a good bargain? Stop using ubuntu and use an alternative (not necessarily windows or osx), or stop complaining and preferably start working on measures to alleviate the inconvenience for others who also may not think it's a good bargain in the short term, and/or on fixing it in the long term.
I wish I wrote that. =D>

---

### Post by badmedic on 2009-07-13
I apologize in advance to those who see this as pointless complaining... but the current implementation of Firefox 3.5 via synaptic is pretty disappointing.

I realize there are workarounds for the user agent problem, and a rational for the misleading branding, but not setting expectations for the average user ahead of time makes it all feel more like a hack job than it really is.

At the very least, the description in Synaptic should explain what you are really getting... a beta of the browser branded "Shiretoko" that does not replace FF 3. (Nothing indicated Beta to me, and nothing indicated alternate branding. I even installed the extra package firefox-3.5-branding!!! Who knows what that did.)

Better yet would be to also figure out a way to keep some form of Firefox branding on it so that a non-technical user won't feel disappointed or uncomfortable with the result. (Having come from the world of Windows adware, malware, etc. the appearance of a new application I did not think I had asked for made me suspicious, and I am a fairly technical user!)


On a side note, I also think that Canonical should make a better effort to keep the browser up-to-date if they are going to push the Safe, Easy, Advanced OS messaging so much in their branding. Keeping your browser up to date is a security basic, and shouldn't be pushed off to a future release.

I am sorry if this comes across as a rant. It is not intended to be that. I love using Ubuntu and have no intention of leaving it. I just think that expressing a critical view when something is wrong might help make it even better in the future.

---

### Post by Tibuda on 2009-07-13
> **badmedic said:**
> At the very least, the description in Synaptic should explain what you are really getting... a beta of the browser branded "Shiretoko" that does not replace FF 3. (Nothing indicated Beta to me, and nothing indicated alternate branding. I even installed the extra package firefox-3.5-branding!!! Who knows what that did.)

firefox-3.5 package is not beta anymore for some time. It was beta in april, but not now. I only agree that it should explain the Shiretoko branding in the package description.

> On a side note, I also think that Canonical should make a better effort to keep the browser up-to-date if they are going to push the Safe, Easy, Advanced OS messaging so much in their branding. Keeping your browser up to date is a security basic, and shouldn't be pushed off to a future release.

3.5 is a major update, not a security fix release.

---

### Post by badmedic on 2009-07-13
> firefox-3.5 package is not beta anymore for some time. 
My mistake... I thought I saw "Beta" in my installation's "about" screen.

> 3.5 is a major update, not a security fix release.
I guess I understand the distinction, but in the case of something like the default browser I consider this is a weakness in Canonical's methodology. Keeping your web browser up to date sure seems like a security fix to me... even if it requires a version update.

---

### Post by Tibuda on 2009-07-13
> **badmedic said:**
> My mistake... I thought I saw "Beta" in my installation's "about" screen.
Probably because you have installed it before the final version became available in the "universe" repositories.

---

### Post by badmedic on 2009-07-13
Nah... I only installed it a few days ago! When I first saw "Shiretoko" I got freaked out, did a search to find out what the $%^&#$ it was and read it was a beta. :grin:

---

### Post by Tibuda on 2009-07-13
> **badmedic said:**
> Nah... I only installed it a few days ago! When I first saw "Shiretoko" I got freaked out, did a search to find out what the $%^&#$ it was and read it was a beta. :grin:

Yes, Shiretoko is the name of the beta, but [Canonical chose to keep this name in final release]("http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html") for people that want to keep both versions installed. What does your [Help > About]("http://ubuntuforums.org/attachment.php?attachmentid=120944&d=1247490281") says?

---

### Post by badmedic on 2009-07-13
I understand it's not a beta... just saying I was confused. :lolflag:

---

### Post by virusiidx on 2009-07-13
I just upgraded my Firefox to 3.5 using [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/"). I'm surprised this hasn't been brought up yet, or maybe I missed it. But it seems like one of the easiest ways to upgrade if you're not satisfied with the other methods.

---

### Post by lovinglinux on 2009-07-13
> **virusiidx said:**
> I just upgraded my Firefox to 3.5 using [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/"). I'm surprised this hasn't been brought up yet, or maybe I missed it. But it seems like one of the easiest ways to upgrade if you're not satisfied with the other methods.

Oh, yeah, [it has been brought up several times](http://ubuntuforums.org/showthread.php?t=1200781). I lost count how many times I posted the instructions below :) 

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

BTW, I have compiled Firefox 3.5 from Mozilla and couldn't be happier.

---

### Post by 23meg on 2009-07-13
> **badmedic said:**
> 
I guess I understand the distinction, but in the case of something like the default browser I consider this is a weakness in Canonical's methodology. Keeping your web browser up to date sure seems like a security fix to me... even if it requires a version update.

Firefox 3.0, being the default browser, and in the "main" component, will receive security fixes and bug fixes for the support period of Ubuntu 9.04.

[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by virusiidx on 2009-07-13
> **lovinglinux said:**
> Oh, yeah, [it has been brought up several times]("http://ubuntuforums.org/showthread.php?t=1200781"). I lost count how many times I posted the instructions below :) 

Oh, sorry, but I was referring to being mentioned in this thread. I know it's been mentioned before on this forum, which is how I found it in the first place. :P

---

### Post by dragos240 on 2009-07-13
I just got firefox 3.5 from the ubuntu repositories, but I find 2 things wierd. The first is that I have to launch firefox-3.5 not firefox, and also, firefox is called shiretoko evidently.

---

### Post by lovinglinux on 2009-07-13
> **dragos240 said:**
> I just got firefox 3.5 from the ubuntu repositories, but I find 2 things wierd. The first is that I have to launch firefox-3.5 not firefox, and also, firefox is called shiretoko evidently.

See the "Install Other Versions" section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). It explains all these questions in the "Method Comparison" topic.

---

### Post by mdsmedia on 2009-07-15
> **23meg said:**
> The classic straw man, once again. Never gets old.

Many users *have* expressed their dissatisfaction, in this thread and others. They've been given what I think are polite and satisfactory explanations as to why things work the way they work. They can keep expressing the same dissatisfaction in slightly different terms, like you've been, but that won't help them fix their dissatisfaction, or help anyone else help them.

And by the way, aren't other people in turn allowed to express *their* dissatisfaction with the way some users express their dissatisfaction? 



The [ubuntu-devel-discuss mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss"), or if you want it Mozilla-specific, the [ubuntu-mozillateam list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-mozillateam"). (or the respective IRC channels: #ubuntu-devel or #ubuntu-mozilla on Freenode). If you visit those places, please don't start out demanding and complaining about things like you've been doing here all along. That will make it more likely for the relevant people to respond to you.



They will probably say "That's how it works; here's why it works that way, and here are the conditions that need to change in order for it to work another way in the future. If you can help make those conditions change, that will make it more likely that things will work how you want in the future."



Right, except that:

**Windows**: User does not get the advantages of shared libraries, centralized software repositories, unified translations, vendor-specific patches, vendor-side integration, extensions in repositories, vendor guarantee of security updates for OS support period.

**OSX**: User does not get the advantages of shared libraries, centralized software repositories, unified translations, vendor-specific patches, vendor-side integration, extensions in repositories, vendor guarantee of security updates for OS support period.

In Ubuntu, you get all of those. And if you don't care about those, you can grab a binary straight from Mozilla and run it. You'll be able to update it to the latest release as soon as it's out, exactly like in the Windows and OSX builds.

Good bargain? Use Ubuntu. Not a good bargain? Stop using Ubuntu and use an alternative (not necessarily Windows or OSX), or stop complaining and preferably start working on measures to alleviate the inconvenience for others who also may not think it's a good bargain in the short term, and/or on fixing it in the long term.
Thank you. There have been some good and bad posts in this thread. Altogether an interesting "discussion", on Ubuntu policies, how to use up to date software, a number of other points.

Not that I disagree with it, but I think holding package versions back is one of the greatest negatives in a 6 monthly release cycle, such as Ubuntu's. Once again, not that I disagree with it. 

There are lots of alternative distros, different methods of obtaining the later versions.

It's a difficult balancing act.

I, for one, am pretty satisfied with using whichever Firefox version is default, receiving the updates as they roll out, and, 6 months later, upgrading Ubuntu to receive all those wonderful updated packages.

What I often ponder, though, is when users have problems with a particular release of Ubuntu, let's say the latest release, because it's broken some piece of hardware compatibility, and it's suggested that they go back to an earlier release, or LTS, which was compatible. 

They then are "stuck" with the (in this case) 12-18 month old releases of packages, unless they use one of the alternative methods of obtaining the later packages. 

Then it comes down to the differences in ease of obtaining and installing programs, which, to me, is a big advantage in Linux, if you're using the repos.

I'm still learning, and don't really care if I've got Firefox 3.0 or 3.5, as long as the Ubuntu team is providing security updates, and then when 9.10 comes around, I'll have the pleasure of updating the packages as they come with the new release of the OS.

I used Dapper until well after Hardy was released. I think I flirted with non-Ubuntu Firefox during that period and may have had to reinstall Ubuntu at some stage and was back with the Ubuntu Firefox. To me it's all a learning experience and having Firefox 1.5 instead of 2.x was a minor annoyance at times. It still beats the he!! out of the alternative.

---

### Post by kingofpain on 2009-07-18
> **23meg said:**
> Good bargain? Use Ubuntu. Not a good bargain? Stop using Ubuntu and use an alternative (not necessarily Windows or OSX)
Now this is really arrogant. 
My bad... I thought that free software is made from passion FOR THE USERS.
But instead of "how can we change things for you to like it even more", we get a "this is how WE like it, if you don't, then use something else".
I don't get it... why make a product that suits ONLY YOUR needs and wishes?:confused:
This is not my idea of free software.

> **23meg said:**
> or stop complaining and preferably start working on measures to alleviate the inconvenience for others who also may not think it's a good bargain in the short term, and/or on fixing it in the long term.

That's why simply users come here to complain for: because they do NOT know how to do that, and expect some help. Instead of arguing, YOU could do that for them... otherwise, why do you visit the forum after all? Not for helping people up?

---

### Post by steeleyuk on 2009-07-18
> **kingofpain said:**
> Now this is really arrogant. 
My bad... I thought that free software is made from passion FOR THE USERS.
But instead of "how can we change things for you to like it even more", we get a "this is how WE like it, if you don't, then use something else".
I don't get it... why make a product that suits ONLY YOUR needs and wishes?:confused:
This is not my idea of free software.

Free software, and Ubuntu in particular is made for the users. You, me and everyone else. Which is why they have a policy of not updating software except for security issues/major fixes. That has been adopted to ensure that 9 out of 10 people don't encounter any problems related to new software releases. It's not tailored to a specific person or group of people, its aimed at the majority.

23meg is right, if Ubuntu isn't suited to your needs, use something else.

---

### Post by 23meg on 2009-07-18
> **kingofpain said:**
> Now this is really arrogant. 

No, it's just realistic.

> **kingofpain said:**
> My bad... I thought that free software is made from passion FOR THE USERS.
But instead of "how can we change things for you to like it even more", we get a "this is how WE like it, if you don't, then use something else".

I never said that. 

> **kingofpain]I don't get it... why make a product that suits ONLY YOUR needs and wishes?:confused:
This is not my idea of free software.[/QUOTE]

Neither Firefox nor Ubuntu suits only my needs and wishes. Nor do they suit the needs and wishes of a small minority.

What is your idea of free software? If it's being able to get everything you want in the exact shape and form and time you want, for free, you're not going to get it. Sorry to be realistic said:**
> That's why simply users come here to complain for: because they do NOT know how to do that, and expect some help.

No, nobody asked "How can I make it easier for people to install Firefox 3.5, and/or better explain to them why they can't just upgrade to it straight away?" or "What can I do to help Ubuntu ship up to date software to its users in a more convenient way in the future? How can we solve this problem?".

[QUOTE=kingofpain]Instead of arguing, YOU could do that for them... otherwise, why do you visit the forum after all? Not for helping people up?[/QUOTE]

No, I don't visit *this* forum for helping people; this forum is for general discourse, not technical help.

---

### Post by Merk42 on 2009-07-19
Well 3.5.1 is out and updated.  However the bug I filed (which was a [duplicate](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211)) it still not fixed, instead they want to tell **every website on the planet** to not use browser sniffing.

> **23meg said:**
> 
No, nobody asked "How can I make it easier for people to install Firefox 3.5, and/or better explain to them why they can't just upgrade to it straight away?" or "What can I do to help Ubuntu ship up to date software to its users in a more convenient way in the future? How can we solve this problem?".

I'd like to think I (eventually) did just that.  If you don't think I have, I'll officially ask now.

Also if your answer has to do with coding, that is kingofpain's point.

---

### Post by running_rabbit07 on 2009-07-19
I have been looking around and I haven't been able to find an answer to this question. 

When will the FF3.5 be in the repositories for 8.04LTS? 

I have tried to CLI the install and practically killed my machine.

I am at the point where I know I will be waiting for it to be in the repositories, so I was just wandering when.

---

### Post by ratcheer on 2009-07-19
I just downloaded FF 3.5.1 from the official Mozilla Firefox web site and followed the instructions to install it. Then, I just had to point my tray icon to the new install. Finally, I deleted it off the Applications menu and re-added it as the new version. The new version picked up all my bookmarks and other settings, automatically.

It was a piece of cake and I am an Ubuntu newbie.

Tim

---

### Post by collinp on 2009-07-19
Firefox 3.5 will not be included in the repositories of any other release besides the 9.10 Karmic Koala release, as it is a new version and not a bug fix or security update for the already existing version. At most it will be in the backports repository of your relevant release.

---

### Post by Tibuda on 2009-07-19
> **Hellow said:**
> Firefox 3.5 will not be included in the repositories of any other release besides the 9.10 Karmic Koala release, as it is a new version and not a bug fix or security update for the already existing version. At most it will be in the backports repository of your relevant release.

It is already in universe for jaunty, but it got a different brand and is in a different package ([firefox-3.5]("apt:firefox-3.5")), which means the update manager won't update it.

---

### Post by running_rabbit07 on 2009-07-19
Is there a way to install via GUI on 8.04? I don't see the Shireteko version in Synaptic.
I would really like to have 3.5 on here, I know on Windows it runs way faster than IE.

---

### Post by 23meg on 2009-07-20
> **Merk42 said:**
> Well 3.5.1 is out and updated.  However the bug I filed (which was a [duplicate](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211)) it still not fixed, instead they want to tell **every website on the planet** to not use browser sniffing.

Very first reply on that bug:

[QUOTE=Alexander Sack]Could you please come up with a list of high impact websites that break with Shiretoko in user-agent, but work with Firefox?

Also be specific about which features are broken and how we can reproduce.

With that info we will be able to understand better if we agree with you on "changing an about:config value in Fi^H^HShiretoko to have it report as Firefox (since that's what it really is) would be a huge benefit to users" :).[/QUOTE]

Contributing to that list (which it seems you didn't) increases the chances of the issue being sorted out the way you like. Complaining about "the bug still not being fixed" in an unrelated forum does not. It also produces misinformation, which in turn damages the project, and in the long run, labels you as someone who produces little other than misinformation. Please stop it.

[QUOTE=Merk42]I'd like to think I (eventually) did just that.  If you don't think I have, I'll officially ask now.[/QUOTE]

You sort of did, with an "..even if I did, wouldn't it be useless?" tone, and I responded.

[QUOTE=Merk42]Also if your answer has to do with coding, that is kingofpain's point.[/QUOTE]

It may or may not, and kingofpain's reply doesn't say anything about coding. Nevertheless, in this particular case, a list of important websites that break with Shiretoko is being asked for. That's not a coding task; it's a non-technical task, yet nobody complaining here seems to have contributed to it.

---

### Post by Merk42 on 2009-07-21
> **23meg said:**
> Contributing to that list (which it seems you didn't) increases the chances of the issue being sorted out the way you like.
But I meantioned Facebook and pointed out that it's the [4th most popular site on the Internet](http://www.alexa.com/topsites) in my [original bug filing](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/398525). 

> **23meg said:**
> Complaining about "the bug still not being fixed" in an unrelated forum does not. It also produces misinformation, which in turn damages the project, and in the long run, labels you as someone who produces little other than misinformation. Please stop it.
While the status is confirmed, it is not fixed (don't insert the word 'being' I didn't say that) so how is that misinformation?

> **23meg said:**
> You sort of did, with an "..even if I did, wouldn't it be useless?" tone, and I responded.
Then don't say "Nobody asked..."

> **23meg said:**
> It may or may not, and kingofpain's reply doesn't say anything about coding.
It didn't you're right, it talked about needing to do things people like himself didn't know how to do.  I'm only assuming coding right now until kingofpain says otherwise.  So if that is the case, how would someone as you put it "*start working on measures to alleviate the inconvenience for others who also may not think it's a good bargain in the short term, and/or on fixing it in the long term.*"
or as you told me "*...package a branded Firefox 3.5 that replaces Firefox 3.0 in your PPA.*" without coding?
The only other option you gave me was to "*learn the rationales behind the current stable release update and branding policies*", which doesn't seem like something I can contribute to.

> **23meg said:**
> Nevertheless, in this particular case, a list of important websites that break with Shiretoko is being asked for. That's not a coding task; it's a non-technical task, yet nobody complaining here seems to have contributed to it.
Again, like I said, I did. I didn't bother to mention it in the older bug because it already was.

---

### Post by Keyper7 on 2009-07-21
> **kingofpain said:**
> Now this is really arrogant.

Wrong.

Arrogance would be trying to convince you that Ubuntu's way is the correct one and that you are wrong.

23meg, instead, is stating that different people have different needs and it's impossible for Ubuntu to satisfy everyone.

It's an admission of a limitation. The *exact opposite* of arrogance.

---

### Post by 23meg on 2009-07-21
> **Merk42 said:**
> But I meantioned Facebook and pointed out that it's the [4th most popular site on the Internet](http://www.alexa.com/topsites) in my [original bug filing](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/398525). 

You could in the very least repost that to the active bug. It's not a good idea to assume anybody looks at duplicates.

[QUOTE=Merk42]While the status is confirmed, it is not fixed (don't insert the word 'being' I didn't say that) so how is that misinformation?[/QUOTE]

**This** is misinformation:

[QUOTE=Merk42]instead they want to tell **every website on the planet** to not use browser sniffing.[/QUOTE]

When I look at the bug, the very first comment I see is asking for a list of prominent websites in an effort to determine whether it's a good idea to change the default user agent string. That means there's an intention to switch the user agent string and resolve the issue exactly the way you want, and the feasibility of that is being evaluated. Ignoring that, and only reporting the obvious fact that "it's still not fixed", and making it seem as if the only suggested resolution is that users convince every website to stop using user agent sniffing is misrepresenting the position of the developers working on the issue, thus intentionally spreading misinformation to serve for your case. 

By the way, "Confirmed" is a status to which anyone can set any bug to. It doesn't mean "it's been acknowledged that this is a real bug" (that's "Triaged"). 

[QUOTE=Merk42]Then don't say "Nobody asked..."[/QUOTE]

OK, *one* person *kind of asked*, by saying "..even if I asked, wouldn't it be useless?", after about 150 posts, and after I asked them to ask.

Pretty close to "nobody asked".

[QUOTE=Merk42]It didn't you're right, it talked about needing to do things people like himself didn't know how to do.  I'm only assuming coding right now until kingofpain says otherwise.  So if that is the case, how would someone as you put it "*start working on measures to alleviate the inconvenience for others who also may not think it's a good bargain in the short term, and/or on fixing it in the long term.*"
or as you told me "*...package a branded Firefox 3.5 that replaces Firefox 3.0 in your PPA.*" without coding?
The only other option you gave me was to "*learn the rationales behind the current stable release update and branding policies*", which doesn't seem like something I can contribute to.[/QUOTE]

People without coding skills have written documentation, installation scripts and informative blog posts on "the problem" that seem to have helped others.

Setting up a PPA is not exactly a "coding" task either; it's a packaging task, though it's still rather technical.

---

### Post by Merk42 on 2009-07-21
> **23meg said:**
> You could in the very least repost that to the active bug. It's not a good idea to assume anybody looks at duplicates.
I think you misunderstood, the reason I didn't mention Facebook was not because I had mentioned it in the bug I filed, 398525, but that it was already mentioned in bug #397211, the second post.


> **23meg said:**
> When I look at the bug, the very first comment I see is asking for a list of prominent websites in an effort to determine whether it's a good idea to change the default user agent string...
Look at the later posts, especially those [by](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211/comments/8) [Micah](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211/comments/10) [Gersten](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211/comments/14).  In fact, this is the response I got when I was first notified my bug was a duplicate


"*If you can find a contact for Facebook, please let them know that the User Agent is not a good way of determining the browser.*"

If it was just a matter of saying "site X doesn't work" then why would I need to try and contact the admin for the website?  I'm not the only one that came to [that conclusion](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211/comments/11) either.
 
> **23meg said:**
> OK, *one* person *kind of asked*, by saying "..even if I asked, wouldn't it be useless?", after about 150 posts, and after I asked them to ask.

Pretty close to "nobody asked".
So then given the bug only has confirmed and instead of just a list is asking for the people to contact the developers, I guess it's pretty close to "instead they want to tell every website on the planet to not use browser sniffing."


> **23meg said:**
> People without coding skills have written documentation, installation scripts and informative blog posts on "the problem" that seem to have helped others.

Setting up a PPA is not exactly a "coding" task either; it's a packaging task, though it's still rather technical.
Well there's that documentation from LovingLinux.  Not sure if there is a PPA or not.  My point is, was, and always has been, why should users have to jump through hoops to get an updated version of a flagship application.  More specifically, why is the package firefox-3.5 in the default repos when it does not produce the expected result?

---

### Post by pastalavista on 2009-07-21
I think it's time for me to unsubscribe from this thread... talk about beating dead horses

---

### Post by BLTicklemonster on 2009-07-21
> **pastalavista said:**
> I think it's time for me to unsubscribe from this thread... talk about beating dead horses

I was hoping that jumping to the last page would allow me to see a fix, not a hijack fest.

---

### Post by 23meg on 2009-07-21
> **Merk42 said:**
> I think you misunderstood, the reason I didn't mention Facebook was not because I had mentioned it in the bug I filed, 398525, but that it was already mentioned in bug #397211, the second post.

OK, I stand corrected.

> **Merk42 said:**
> Look at the later posts, especially those [by](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211/comments/8) [Micah](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211/comments/10) [Gersten](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211/comments/14).  In fact, this is the response I got when I was first notified my bug was a duplicate

"*If you can find a contact for Facebook, please let them know that the User Agent is not a good way of determining the browser.*"

If it was just a matter of saying "site X doesn't work" then why would I need to try and contact the admin for the website?  I'm not the only one that came to [that conclusion](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211/comments/11) either.

Telling websites not to use user agent sniffing and changing your browser's user agent are not mutually exclusive strategies. The former scores higher on theoretical correctness but lower on immediate effects, and the latter, the opposite. This is even more true for this specific case, given the short useful lifetime of the firefox-3.5 Jaunty package (since most users who will be using Firefox 3.5 will have upgraded to Karmic in a few months).

> **Merk42 said:**
> So then given the bug only has confirmed and instead of just a list is asking for the people to contact the developers, I guess it's pretty close to "instead they want to tell every website on the planet to not use browser sniffing."

It's not asking people to "contact the developers", whatever that means; it's asking people to name those websites right there in the comments, in an effort to determine the feasibility of switching the user agent string. 

> **Merk42 said:**
> Well there's that documentation from LovingLinux.  Not sure if there is a PPA or not.  My point is, was, and always has been, why should users have to jump through hoops to get an updated version of a flagship application.  More specifically, why is the package firefox-3.5 in the default repos when it does not produce the expected result?

Those questions have been thoroughly answered multiple times in this and other related threads. The firefox-3.5 package description issue is worthy of a bug report.

---

### Post by 23meg on 2009-07-21
> **BLTicklemonster said:**
> I was hoping that jumping to the last page would allow me to see a fix, not a hijack fest.

This is not a support forum, and the discussion that has ensued from the original question is pretty much on topic by the standards of this forum.

---

### Post by netJackDaw on 2009-08-04
> **badmedic said:**
> I apologize in advance to those who see this as pointless complaining... but the current implementation of Firefox 3.5 via synaptic is pretty disappointing.

I realize there are workarounds for the user agent problem, and a rational for the misleading branding, but not setting expectations for the average user ahead of time makes it all feel more like a hack job than it really is.

At the very least, the description in Synaptic should explain what you are really getting... a beta of the browser branded "Shiretoko" that does not replace FF 3. (Nothing indicated Beta to me, and nothing indicated alternate branding. I even installed the extra package firefox-3.5-branding!!! Who knows what that did.)

Better yet would be to also figure out a way to keep some form of Firefox branding on it so that a non-technical user won't feel disappointed or uncomfortable with the result. (Having come from the world of Windows adware, malware, etc. the appearance of a new application I did not think I had asked for made me suspicious, and I am a fairly technical user!)


On a side note, I also think that Canonical should make a better effort to keep the browser up-to-date if they are going to push the Safe, Easy, Advanced OS messaging so much in their branding. Keeping your browser up to date is a security basic, and shouldn't be pushed off to a future release.

I am sorry if this comes across as a rant. It is not intended to be that. I love using Ubuntu and have no intention of leaving it. I just think that expressing a critical view when something is wrong might help make it even better in the future.

I totally agree with you. My point of view exactly. Keep it up

---

### Post by daverich on 2009-08-04
> **netJackDaw said:**
> I totally agree with you. My point of view exactly. Keep it up

+1.

I gave up and just downloaded the binary, which is brilliant as you actually dont need to install it, just run it from the folder. hoorah - something easy in linux!

Kind regards

Dave Rich

---

### Post by stimpack on 2009-08-04
> **daverich said:**
> +1.

I gave up and just downloaded the binary, which is brilliant as you actually dont need to install it, just run it from the folder. hoorah - something easy in linux!


Everyone should do this, dunno how this thread is 18pages long. Download from Mozilla now!. You need browser security updates as soon as possible and Firefox autoupdates itself, dont rely on repos.

Repos have their place, but this is not one of them.

---

### Post by Old Marcus on 2009-08-04
> **stimpack said:**
> Everyone should do this, dunno how this thread is 18pages long. Download from Mozilla now!. You need browser security updates as soon as possible and Firefox autoupdates itself, dont rely on repos.

Repos have their place, but this is not one of them.

Unfortunately Ubuntu blocks its auto update function, any way to stop this? At the moment I have to manually download the updated version from mozilla and replace the old version manually.

---

### Post by stimpack on 2009-08-12
My updates are not blocked, it is installed in my user directory if that makes any difference.

---

### Post by Tibuda on 2009-08-12
> **stimpack said:**
> Everyone should do this, dunno how this thread is 18pages long. Download from Mozilla now!. You need browser security updates as soon as possible and Firefox autoupdates itself, dont rely on repos.

Repos have their place, but this is not one of them.

Not everyone. Only who wants FF 3.5. Canonical releases security updates for 3.0. My father's bank got a FF addon that won't work in 3.5, so no, I should not update it before the bank updates the addon.

---

