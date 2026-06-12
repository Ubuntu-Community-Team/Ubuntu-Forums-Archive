---
title: "What distro should I switch to?"
date: 2011-11-13
forum: Ubuntu, Linux and OS Chat
---

### Post by josephellengar on 2011-11-13
Hi there. I'm not trying to flame, annoy, or anything else. This is an honest question and I know that the Ubuntu community is great, so I hope that you can help me.

Anyway, I want to switch distros and am hoping that you can advise me on a good one to switch to. Below I list the things that I like and dislike about Ubuntu.

Likes:
Simplicity
Free (and gratis) software
Synaptic/Easy package management
Excellent and friendly community
Gnome 
Drivers for up-to-date hardware

Dislikes:
6-month release cycle
No security updates in that cycle (that is, I don't get real up to date software until the next update)
Unity (I think that Canonical is going to start focusing too much on Unity on various platforms and too little on the Desktop)
General "Jazz" of the new releases
Ubuntu One/having social networking forced on me

So, I guess what I am looking for is a distro that is equally friendly and usable, but requires system updates less frequently. Also, I would very much like updates for the *packages* more frequently, so that I get security updates for important things as they arrive. For example, I don't want to be on Firefox 6 when Firefox 8 was released two weeks ago. I do not want a rolling release; stability is very important to me. Also, I really don't want anything that is corporatized. If all else fails, I would be willing to go for a rolling release, but I would call myself on a scale of 1 to 10 perhaps a 6 in terms of my Linux knowledge. (Have worked with it, have a BSCS, but not too much).

Perhaps OpenSuse?

Thanks for the help!

---

### Post by Bachstelze on 2011-11-13
> **josephellengar said:**
> 
No security updates in that cycle (that is, I don't get real up to date software until the next update)

/facepalm

---

### Post by josephellengar on 2011-11-13
> **Bachstelze said:**
> /facepalm

Why? Firefox 3.6 is in Synaptic for me. (10.10) Firefox 8 is out. Calibre 0.7.18 in Synaptic. Calibre 0.8.26 is out. Openoffice 1.3 in Synaptic; Openoffice 3.3 is out. You get the idea.

---

### Post by Bachstelze on 2011-11-13
That has nothing to do with "security updates".

---

### Post by josephellengar on 2011-11-13
> **Bachstelze said:**
> That has nothing to do with "security updates".

Whatever. I say that Firefox 8 is more secure than Firefox 3.6. I was talking about the repository software specifically. Do you have suggestions or are you just nitpicking my language?

---

### Post by sandyd on 2011-11-13
> **josephellengar said:**
> Hi there. I'm not trying to flame, annoy, or anything else. This is an honest question and I know that the Ubuntu community is great, so I hope that you can help me.

Anyway, I want to switch distros and am hoping that you can advise me on a good one to switch to. Below I list the things that I like and dislike about Ubuntu.

Likes:
Simplicity
Free (and gratis) software
Synaptic/Easy package management
Excellent and friendly community
Gnome 
Drivers for up-to-date hardware

Dislikes:
6-month release cycle
No security updates in that cycle (that is, I don't get real up to date software until the next update)
Unity (I think that Canonical is going to start focusing too much on Unity on various platforms and too little on the Desktop)
General "Jazz" of the new releases
Ubuntu One/having social networking forced on me

So, I guess what I am looking for is a distro that is equally friendly and usable, but requires system updates less frequently. Also, I would very much like updates for the *packages* more frequently, so that I get security updates for important things as they arrive. For example, I don't want to be on Firefox 6 when Firefox 8 was released two weeks ago. I do not want a rolling release; stability is very important to me. Also, I really don't want anything that is corporatized. If all else fails, I would be willing to go for a rolling release, but I would call myself on a scale of 1 to 10 perhaps a 6 in terms of my Linux knowledge. (Have worked with it, have a BSCS, but not too much).

Perhaps OpenSuse?

Thanks for the help!
Use debian.

The current version is Debian Squeeze.
When you finish downloading, just edit /etc/apt/sources.list, and change "squeeze" to "stable". Now, you will have **stable** easy rolling releases. Normally, you would have to upgrade from squeeze to whatever the next version is. Now, the packages simply update to the new release by themselves without your intervention. Nothing else needs to be done about the rolling releases, they will just go and go and go....

Debian is also very clean and minimalistic. None of that social networking crap that comes bundeled in with other linux distros.

---

### Post by josephellengar on 2011-11-13
> **sandyd said:**
> Use debian.

The current version is Debian Squeeze.
When you finish downloading, just edit /etc/apt/sources.list, and change "squeeze" to "stable". Now, you will have **stable** easy rolling releases. Normally, you would have to upgrade from squeeze to whatever the next version is. Now, the packages simply update to the new release by themselves without your intervention. Nothing else needs to be done about the rolling releases, they will just go and go and go....

Debian is also very clean and minimalistic. None of that social networking crap that comes bundeled in with other linux distros.

Thanks for the suggestion! I was actually looking at Arch for the same minimalist reasons, but was worried I might not be competent enough. Does Debian have the same access to all of the packages that Ubuntu has? Specifically, I use some Qt software, like Kmymoney, that I can't go without. Among other things like LibreOffice. Is the software library the same size (or nearly so)? Otherwise, it's pretty similar to Ubuntu, right? Is there anything else that I should know before I make the switch? Of course I will test it on LiveCD first just to see.

---

### Post by Dr. C on 2011-11-13
> **sandyd said:**
> Use debian.

The current version is Debian Squeeze.
When you finish downloading, just edit /etc/apt/sources.list, and change "squeeze" to "stable". Now, you will have **stable** easy rolling releases. Normally, you would have to upgrade from squeeze to whatever the next version is. Now, the packages simply update to the new release by themselves without your intervention. Nothing else needs to be done about the rolling releases, they will just go and go and go....

Debian is also very clean and minimalistic. None of that social networking crap that comes bundeled in with other linux distros.

I agree with Debian as the suggestion.

---

### Post by beew on 2011-11-13
Well you do get security updates, what you don't get are feature updates. But there are ppas for most softwares if you want up to date features and bug fixes (Ubuntu does provides bug fixes if they are security related, but only those).

As for the 6 month release cycle, you don't have to update/upgrade your OS every 6 months though if you don't want to. Regular releases are supported for 18 months. People who upgrade every 6 months do so by chioce. Personally I think it is crazy to tie your update schedule to Ubuntu's release cycle. For one thing new releases tend to be buggy, it takes a month or two for the OS to become mature and solid, ppas to be set up etc, why would you want to trade in a version just when its rough edges got ironed out for the next beta quality offer?  

If you dislike Unity you can try other DEs like gnome shell, xfce, KDE or LXDE.

---

### Post by sandyd on 2011-11-13
> **josephellengar said:**
> Thanks for the suggestion! I was actually looking at Arch for the same minimalist reasons, but was worried I might not be competent enough. Does Debian have the same access to all of the packages that Ubuntu has? Specifically, I use some Qt software, like Kmymoney, that I can't go without. Among other things like LibreOffice. Is the software library the same size (or nearly so)? Otherwise, it's pretty similar to Ubuntu, right? Is there anything else that I should know before I make the switch? Of course I will test it on LiveCD first just to see.
Ubuntu is based on debian unstable. Theirs a few weird ubuntu-only packages, but those are the unity, gwibber packages, so it shouldn't bother you.

---

### Post by josephellengar on 2011-11-13
> **beew said:**
> Well you do get security updates, what you don't get is feature updates. But there are ppas for most softwares if you want up to date features and bug fixes (Ubuntu does provides bug fixes if they are security related, but only those).

As for the 6 month release cycle, you don't have to update/upgrade your OS every 6 months though if you don't want to. Regular releases are supported for 18 months. People who upgrade every 6 months do so by chioce. Personally I think it is crazy to tile your update schedule to Ubuntu's release cycle. For one thing new releases tend to be buggy, it takes a month or two for the OS to become mature and solid, ppas to be set up etc, why would you want to trade in a version just when its rough edges got ironed out for the next beta quality offer?  

If you dislike Unity you can try other DEs like gnome shell, xfce, KDE or LXDE.

My update schedule has long been 6 months- staying on the last release. That is, right now I am still using 10.10. I tried updating to 11.04 to keep up, but it didn't work. I was thinking I might switch to the LTS-only cycle, but I just don't like the direction that Ubuntu is going.

---

### Post by josephellengar on 2011-11-13
> **sandyd said:**
> Ubuntu is based on debian unstable. Theirs a few weird ubuntu-only packages, but those are the unity, gwibber packages, so it shouldn't bother you.

Thank you. You have been very helpful. So I guess the 14-Oct-2011 11:54  1.1G  download from [here]("http://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/") would be appropriate? If so I'll try it out on a live USB and let you guys know how it worked out tomorrow or so.

---

### Post by josephellengar on 2011-11-13
> **sandyd said:**
> Use debian.

The current version is Debian Squeeze.
When you finish downloading, just edit /etc/apt/sources.list, and change "squeeze" to "stable". Now, you will have **stable** easy rolling releases. Normally, you would have to upgrade from squeeze to whatever the next version is. Now, the packages simply update to the new release by themselves without your intervention. Nothing else needs to be done about the rolling releases, they will just go and go and go....

Debian is also very clean and minimalistic. None of that social networking crap that comes bundeled in with other linux distros.

So this is actually rolling? Is this because they always put the new packages into the same stable branch, regardless of the version number? Have you tested this before? I didn't see anything about rolling releases on the Debian website so ... you know.

---

### Post by 3Miro on 2011-11-14
When you say Gnome, do you mean Gnome 2 or Gnome 3. Debian comes with Gnome 2 (i.e. same as Ubuntu 10.04). Arch comes with Gnome 3 + Gnome-shell (Ubuntu 11.10 comes with Gnome 3 + Unity, Gnome-shell is optional).

In Ubuntu and Debian, you can get newer software for some programs if you use unofficial ppa. Debian 6 comes with Firefox 3.6 (actually Iceweasel, but it is essentially FF 3.6). As security holes are found, they are patched and you will keep getting security updates for Firefox 3.6. FF 8 may have new security concepts, but also many undiscovered bugs.

---

### Post by fantab on 2011-11-14
If you are looking for rock stable distros with outdated software versions then its either DEBIAN or CENTOS.

They will suit your preferences.

---

### Post by jjex22 on 2011-11-14
If you like 99% of Ubuntu but not where unity is going, I'd suggest Mint - they've decided to support a fork of gnome 2 into their next lts as far as I can tell (of course we don't know how successful that fork will be yet) in addition to gnome 3 and no mention of unity. 

I know Mint isn't often mentioned here.. I suspect some see it as the ex-wife that's now going after our Debian, but in truth the main releases are Ubuntu based and run very well - you can of course disable updates in any distro, but I don't recommend it. If you like LXDE however I'd go Lubuntu - it's finally caught up with mint lxde, which as taken a bit of a dive in version 11 IMHO.

---

### Post by Dry Lips on 2011-11-14
If I were you I'd check out Linux Mint Debian Edition (LMDE). It's basically
Debian testing coupled with the familiar Mint elegance...

---
edit: Sorry, I didn't notice that you said you didn't want a rolling release...
In that case, I agree with the others that Debian might suit you.

---

### Post by philinux on 2011-11-14
Moved to Other OS/Distro talk forum.

---

### Post by BrokenKingpin on 2011-11-14
I found that Xfce/Xubuntu was a great alternative if you do not like Unity. This doesn't get around the 6 month release cycle though, which I also dislike. I would prefer a rolling release, but I can't seem to find a rolling release distro that I like. So I just use PPAs to keep things a bit more up to date between releases.

You could look at openSUSE, which has a longer release cycle, and you can also enable the rolling repo tumbleweed.

You could also try LMDE, but I found it unstable and the software is fairly out of date (still on Xfce 4.6, even though 4.8 has been out for a year now).

You could also try Arch, which is a rolling release. I like this distro, but the setup is just too long for me.

---

### Post by snowpine on 2011-11-14
> **josephellengar said:**
> 6-month release cycle

Partially false; LTS releases are 24 months apart.

> **josephellengar said:**
> No security updates in that cycle (that is, I don't get real up to date software until the next update)

False; Ubuntu releases get 18 months of security updates (36 months for LTS).

> **josephellengar said:**
> Unity (I think that Canonical is going to start focusing too much on Unity on various platforms and too little on the Desktop)

False; KDE, Xfce, and LXDE are also well-supported, and Gnome is just a few clicks away.

> **josephellengar said:**
> General "Jazz" of the new releases
Ubuntu One/having social networking forced on me

Hard to argue with this. :)

> **josephellengar said:**
> Also, I would very much like updates for the *packages* more frequently, so that I get security updates for important things as they arrive. For example, I don't want to be on Firefox 6 when Firefox 8 was released two weeks ago. 

This is the dictionary definition of "rolling release" but then you say:

> **josephellengar said:**
> ...I do not want a rolling release...

I think you are going to have a hard time choosing a distro until you get your facts straight and figure out exactly what you want.

---

### Post by josephellengar on 2011-11-14
> Partially false; LTS releases are 24 months apart.
 
 
 
> False; Ubuntu releases get 18 months of security updates (36 months for LTS).
 
For Canonical packages only.
 
 
 
> False; KDE, Xfce, and LXDE are also well-supported, and Gnome is just a few clicks away.
 
But the focus is on Unity, not these other desktops. There won't be any innovation in these areas. (And I can't count Unity as innovation)
 
 
> This is the dictionary definition of "rolling release" but then you say:
 
 
I think you are going to have a hard time choosing a distro until you get your facts straight and figure out exactly what you want. 
 
Okay, as I said above when I say that I want package upgrades, I am talking about getting the third-party packages (like Firefox) into my machine. I am still on Firefox 3.6, which is not even supported by Mozilla anymore. (Not that I use Firefox, but you get the idea.) I explained this in posts 2-5.

---

### Post by josephellengar on 2011-11-14
For everyone, I will say it here: I am fine with a rolling release as long as it is stable. That is, what Dry Lips suggested (LMDE) might be perfect for me, if it uses the stable Debian branches, as with SandyD.
 
So I guess my question here is: Mint DE or Debian. And if I do what SandyD suggested in [post 6]("http://ubuntuforums.org/showpost.php?p=11454731&postcount=6") will this actually give me a rolling release? I didn't see anything about this on the Debian website, and like I said, I am competent but not advanced in Linux, so I'd just like some confirmation from a third party before I make the move. (You can't really tell that sort of thing from a LiveCD)

---

### Post by snowpine on 2011-11-14
> **josephellengar said:**
> Okay, as I said above when I say that I want package upgrades, I am talking about getting the third-party packages (like Firefox) into my machine. I am still on Firefox 3.6, which is not even supported by Mozilla anymore. (Not that I use Firefox, but you get the idea.) I explained this in posts 2-5.

You can have the latest Firefox with one simple command, it will take you 30 seconds to follow these instructions:

[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

> **josephellengar said:**
> For everyone, I will say it here: I am fine with a rolling release as long as it is stable. 

"Rolling release" is never "stable." This is a contradiction in terms; something cannot be "constantly changing" and yet "unchanging" simultaneously.

> **josephellengar said:**
> That is, what Dry Lips suggested (LMDE) might be perfect for me, if it uses the stable Debian branches, as with SandyD.

LMDE is based on the Debian rolling-release "Testing" branch; I cannot recommend this for an inexperienced user in search of stability.
 
> **josephellengar said:**
> So I guess my question here is: Mint DE or Debian. And if I do what SandyD suggested in [post 6]("http://ubuntuforums.org/showpost.php?p=11454731&postcount=6") will this actually give me a rolling release? I didn't see anything about this on the Debian website, and like I said, I am competent but not advanced in Linux, so I'd just like some confirmation from a third party before I make the move. (You can't really tell that sort of thing from a LiveCD)

If you think Ubuntu 11.10 is outdated then you are going to **hate** Debian! It is a very stability-oriented distro, the packages are comparable in age to Ubuntu 10.04 and the next release isn't due until early 2013.

Frankly I think all you need is to learn how to use PPA's for Firefox and your other favorite apps, and swich to Xfce or KDE desktop. Then you can stick with Ubuntu and your major concerns will be solved.

---

### Post by josephellengar on 2011-11-14
> **snowpine said:**
> You can have the latest Firefox with one simple command, it will take you 30 seconds to follow these instructions:
 
[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)
 
 
 
"Rolling release" is never "stable." This is a contradiction in terms; something cannot be "constantly changing" and yet "unchanging" simultaneously.
 
 
 
LMDE is based on the Debian rolling-release "Testing" branch; I cannot recommend this for an inexperienced user in search of stability.
 
 
 
If you think Ubuntu 11.10 is outdated then you are going to **hate** Debian! It is a very stability-oriented distro, the packages are comparable in age to Ubuntu 10.04 and the next release isn't due until early 2013.
 
Frankly I think all you need is to learn how to use PPA's for Firefox and your other favorite apps, and swich to Xfce or KDE desktop. Then you can stick with Ubuntu and your major concerns will be solved.
 

I know how to use PPAs, and I am by no means an inexperienced user. Anyway, this thread is getting off-topic. The fact that the packages in Ubuntu are outdated is not my biggest complaint; it's not even a main complaint. My primary complaint was the direction that Ubuntu is going, with all of the flashiness and social-networking crap. Since Debian doesn't have that, and since I can and do get up-to-date applications from other places, it sounds to me like Debian is great for me. So as soon as I get confirmation from another source that simply changing to the "Stable" debian branch gives me a rolling release, this thread is solved.

---

### Post by snowpine on 2011-11-14
> **josephellengar said:**
> Since Debian doesn't have that, and since I can and do get up-to-date applications from other places, it sounds to me like Debian is great for me. So as soon as I get confirmation from another source that simply changing to the "Stable" debian branch gives me a rolling release, this thread is solved.

Debian Stable is pretty much the polar opposite of "rolling release." If you really want rolling release, then you want something like Arch.

I love Debian, but predict you'll be very disappointed if you go into it expecting up-to-date software.

Sorry if I pulled the thread off-topic earlier.

---

### Post by jjex22 on 2011-11-14
My personal opinion of Debian versus Mint DE is Mint DE, but it's as usual a personal choice - I like it because it's packaged and gift wrapped and good to go. But of course the great thing about debian is that its really good for compiling exactly how you like it (unless you go for the default install everything) and you won't get this off the bat with mint DE.

From what you've said about being an ubuntu fan I'd have thought that mint DE would be the way to go, but it's always worth downloading both live cds and having a go on both!

---

### Post by Punz on 2011-11-14
Linux Mint is a great alternate to Ubuntu. It's actually based off Ubuntu. You can choose the Gnome GUI and the Package manager isn't to complicated to understand. The GUI is smooth. My mother-in-law didn't like Unity after we switched to 11.10 and the "Gnome" alternative in the Ubuntu Software Manager was a joke. I installed Linux Mint and she loves. It should be noted that my mother-in-law knows NOTHING about Linux or computers in general. She just uses her PC for Internet and pictures. If it works for her, it will work for you. 

Sorry to see you go though. 

Here is a link to Linux Mint. 
[http://linuxmint.com/]("http://www.linuxmint.com/")

---

### Post by beew on 2011-11-14
Debian testing, or LMDE is not really rolling, repos freeze before stable releases.  I get newer sofware packages with Ubuntu + ppas than from LMDE.

---

### Post by zhogan85 on 2011-11-14
> **snowpine said:**
> Debian Stable is pretty much the polar opposite of "rolling release." If you really want rolling release, then you want something like Arch.

I love Debian, but predict you'll be very disappointed if you go into it expecting up-to-date software.

Sorry if I pulled the thread off-topic earlier.

+1 for arch

---

### Post by LinuxFan999 on 2011-11-14
You could try Fedora too, but it has a short release cycle, like Ubuntu does. I would recommend Debian, if you want stability, or Linux Mint if you want an up-to-date distribution.

---

### Post by ratcheer on 2011-11-14
> **BrokenKingpin said:**
> 

You could also try Arch, which is a rolling release. I like this distro, but the setup is just too long for me.

You could install Archbang. It is much easier to configure than Arch. Once you have everything the way you want it, it is just Arch.

Archbang installs the Openbox desktop, but it can be changed. I have grown to like Openbox, though.

Tim

---

### Post by Dry Lips on 2011-11-14
I must admit that I've got very little experience with Debian, but apparently
Debian Testing isn't as "unstable" as you'd think. Here is a quote from a sticky
over at Debian User forums:
[I]
"Testing (currently "Squeeze"): After a while, a package in Sid with no  really bad bugs gets moved here(the exact time depends on the urgency of  the update). For this reason, it's much more stable than Sid. Since  packages are updately fairly quickly, it's recommended for desktop  users(don't let the name fool you - testing can be more stable than some  distros' (especially the-one-that-cannot-be-named) releases)."[/I]

[http://forums.debian.net/viewtopic.php?f=16&t=58557&p=338549#p338549](http://forums.debian.net/viewtopic.php?f=16&t=58557&p=338549#p338549)

---

### Post by Plumtreed on 2011-11-15
I'm not going to get on a soapbox to promote it but your 'wish-list' sounds like Fuduntu......which IS a rolling release!

It is well made, lightweight and fast.............but google Fuduntu (careful of the spelling) and visit the friendly forum.

---

### Post by Psyael on 2011-11-16
I'm going to go ahead and suggest the OP try a GNOME liveCD of today's release of OpenSUSE. I haven't sold myself on it completely yet, but it includes a nice, fairly no frills version of GNOME 3, non-OSS repositories are easy enough to add, etc. Since it's using RPMs and a mostly untouched GNOME-Shell 3.2, it feels just a little bit like Fedora, but a less strict and complicated.

They used to be on the six month cycle as original SUSE, but since becoming OpenSUSE they seem to vary between 6-12 months, looking at the Wikipedia history. Major *.0 releases are every two years, if nothing else. The next point release (12.2) isn't expected until next July. I doubt they'll go wild with the changes as Ubuntu and Mint do, since like the RedHat/Fedora situation OpenSUSE is basically just a community testbed for SUSE Enterprise, which has to be solidly reliable.

I like Linux Mint Debian in theory, but right now they're having transitional issues related to moving repositories from Debian to their own repositories in the future. Check back in a few months, I'd say.

---

### Post by zipmon on 2011-11-16
> **Psyael said:**
> I'm going to go ahead and suggest the OP try a GNOME liveCD of today's release of OpenSUSE. I haven't sold myself on it completely yet, but it includes a nice, fairly no frills version of GNOME 3, non-OSS repositories are easy enough to add, etc. Since it's using RPMs and a mostly untouched GNOME-Shell 3.2, it feels just a little bit like Fedora, but a less strict and complicated.

They used to be on the six month cycle as original SUSE, but since becoming OpenSUSE they seem to vary between 6-12 months, looking at the Wikipedia history. Major *.0 releases are every two years, if nothing else. The next point release (12.2) isn't expected until next July. I doubt they'll go wild with the changes as Ubuntu and Mint do, since like the RedHat/Fedora situation OpenSUSE is basically just a community testbed for SUSE Enterprise, which has to be solidly reliable.

I was going to suggest this as well, especially because you can choose which repository to use in OpenSUSE, and there's one called Tumbleweed which looks like exactly what you're looking for in terms of "rolling-release-lite"! It's a repository that gets new, stable feature-upgrades to packages as well as bug fixes. So, if an application has a new stable version to download on their website, it'd be in the Tumbleweed! Not bleeding edge or anything, but equivalent to having stable-channel PPA's installed for all your apps.

Also, SuSE (before it was Open) was the first Linux distro I ever used, and it's always been rock-solid. Plus, even though they use RPM package management, like Fedora, they do a lot to make it more user-friendly, including one-click installs off their website software database. (Sort of like an online Ubuntu Software Center!)

Good luck with your choice & have fun! :D

---

### Post by guimaster on 2011-11-25
> **sandyd said:**
> Use debian.

The current version is Debian Squeeze.
When you finish downloading, just edit /etc/apt/sources.list, and change "squeeze" to "stable". Now, you will have **stable** easy rolling releases. Normally, you would have to upgrade from squeeze to whatever the next version is. Now, the packages simply update to the new release by themselves without your intervention. Nothing else needs to be done about the rolling releases, they will just go and go and go....

Debian is also very clean and minimalistic. None of that social networking crap that comes bundeled in with other linux distros.

A while back I kept asking if what you suggest above is really possible. I was repeatedly told that this is not a good idea, because when the new "Stable" release comes out the entire system will break. I never could understand why the system would break, but that's what everyone told me.

---

### Post by jimrew111 on 2011-11-25
you could use sabayon? or mint 12?

---

### Post by snowpine on 2011-11-25
> **guimaster said:**
> A while back I kept asking if what you suggest above is really possible. I was repeatedly told that this is not a good idea, because when the new "Stable" release comes out the entire system will break. I never could understand why the system would break, but that's what everyone told me.

You should always read the Release Notes and follow the recommended update procedure.

For example here are the Release Notes for the current Squeeze including how-to-upgrade from Lenny:

[www.debian.org/releases/stable/releasenotes](www.debian.org/releases/stable/releasenotes)

---

