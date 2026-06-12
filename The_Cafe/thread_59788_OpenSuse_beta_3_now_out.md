---
title: "OpenSuse beta 3 now out"
date: 2005-08-25
forum: The Cafe
---

### Post by Brunellus on 2005-08-25
great googly moogly, those guys are churning out betas FAST.  And I thought the Ubuntu snapshots were quick....

---

### Post by KingBahamut on 2005-08-25
They are drastically trying to catch up with Fedora.

---

### Post by byen on 2005-08-25
wow..that was damn fast! wonder how good the releases are?...I know Suse and love it but...looks like this time around...there are out to takeover..  that brings a question to my mind:
Which one of these pops out offsprings faster than the other? :
Rabbits or Suse?

PS- Just a bad joke....no ill-will whatsoever.

---

### Post by Dragonfly_X on 2005-08-25
[QUOTE=byen]wow..that was damn fast! wonder how good the releases are?...I know Suse and love it but...looks like this time around...there are out to takeover..  that brings a question to my mind:
Which one of these pops out offsprings faster than the other? :
Rabbits or Suse?

PS- Just a bad joke....no ill-will whatsoever.[/QUOTE]

I think when suse is concerned, the Penguin is kicking the Rabbits ass

---

### Post by Knome_fan on 2005-08-25
And for the first time in ages they offer an official ppc version! Yay!

---

### Post by poofyhairguy on 2005-08-25
[QUOTE=Brunellus]great googly moogly, those guys are churning out betas FAST.  And I thought the Ubuntu snapshots were quick....[/QUOTE]

Man...SUSE is picking up steam. Just as I thought, the move to openness it making development explode.

---

### Post by Lovechild on 2005-08-25
Churning out releases that fast is just bad for testing, that is why Fedora puts out only 3 test releases, reasonably spaced out over the development cycle.

---

### Post by tommy04 on 2005-08-25
Okay, does Suse 10 = OpenSuse or what? I keep hearing about Suse 10 betas, so I was wondering...

---

### Post by asimon on 2005-08-26
[QUOTE=Lovechild]Churning out releases that fast is just bad for testing, that is why Fedora puts out only 3 test releases, reasonably spaced out over the development cycle.[/QUOTE]
A big difference is that Fedora has an open and public development repository. Thus you can update packages between test releases to check if a bug was really fixed and can give feedback without the need to wait several weeks before you can test a fix.

OpenSUSE don't have such a development repository yet, only the open betas. I think it would only increase the duplicate counter in their bugzilla if they wait several weeks between betas.

Anyhow, the speed and number of fixed bugs the SUSE team does every week is astonishing. Looks like they're hard working folk.

I also hope they will create something like Fedora Extras. The package quality of some third-party repositories for SUSE is bad (no bug-tracking, no peer review, no set quality standards, etc).

---

### Post by benplaut on 2005-08-26
[QUOTE=tommy04]Okay, does Suse 10 = OpenSuse or what? I keep hearing about Suse 10 betas, so I was wondering...[/QUOTE]

yeah... i'm gonna try it when it comes out- see how it compares to Fedora 5 (when released)  :grin: 

/me hides from non-ubuntu-user bashers  :roll:

---

### Post by KiwiNZ on 2005-08-26
I am currently using Suse 9.3 and love it , but ,these Betas are coming out way too fast . The development lead times are too short ,I seriously doubt their Q/A

---

### Post by asimon on 2005-08-26
[QUOTE=KiwiNZ]I seriously doubt their Q/A[/QUOTE]
Why? Their open betas are much more stable than the (closed) betas for SUSE 9.3 were. You may want to have a look at their bugzilla, and how fast they respond to bugs or how many they fix between betas. I don't doubt their QA. My expierience with filing bugs for Fedora is not as good, thus I don't see time between betas as a good measure for QA. I think it's more reasonable to count the number of fixed bugs instead of the number of passing days. But we will see how buggy SL10 will be.

---

### Post by drizek on 2005-08-26
how do you people download them? im getting 35KBs on a 3.5 GB file using bittorrent. by the time im done downloading htis beast, their next weekly release will be out

BTW, i think that the quality of the betas is actaully pretty high. they fix a TON of stuff every week, and from the reviews ive read, they are doing some great work.

---

### Post by asimon on 2005-08-27
[QUOTE=drizek]how do you people download them? im getting 35KBs on a 3.5 GB file using bittorrent. by the time im done downloading htis beast, their next weekly release will be out[/quote]
Yes bittorrent is usually rather slow.

I downloaded beta 1 and 2 from [ftp://ftp.gwdg.de/pub/opensuse/distribution/](ftp://ftp.gwdg.de/pub/opensuse/distribution/) and got full speed. (This server is not far away from my place).

For beta3 I updated beta 2 via Yast, see [Update SUSE to next version](http://opensuse.org/index.php/Update_SUSE_to_next_version).

If you still have the beta2 isos around you can download the delta isos for beta3 and save a lot of traffic, see [README.delta.iso](http://ftp.gwdg.de/pub/opensuse/distribution/SL-10.0-OSS-beta3/iso/README.delta-iso).

---

### Post by Mishura on 2005-08-27
This is interesting.  I started my experience with Linux with SuSE, and it always has a soft spot in my heart :) .

I wonder, with a Open version of Suse, some of the things that made it stand out (proprietary addons) won't be included.  I hope that there is a repo that can easily install these extra stuff.. and I hope they stop crippling Xine/Mplayer/etc..  just ship it w/o the codecs..

Also, do they plan on using a Apt-4-rpm deal?  That would rock, and use Yast as a Apt frontend.

---

### Post by jdong on 2005-08-27
[QUOTE=KiwiNZ]I am currently using Suse 9.3 and love it , but ,these Betas are coming out way too fast . The development lead times are too short ,I seriously doubt their Q/A[/QUOTE]
KiwiNZ, you have to keep two things in mind:

1) SuSE has a huge, skilled developer team. I've filed a few bug reports with them, most being resolved in a few hours. Also, I've been following PlanetSuSE blogs, and their developers are doing work everywhere. There's some rewriting gnome-volume-manager for better performance as we speak. They do get a significant number of bug fixes per beta release, and each beta is more usable than the previous.

2) SuSE betas are handled like stable releases. They don't have a "live repository", like Breezy right now. Once a beta is released, it stays in that state for the week or so. As a result, you really do need to snapshot frequently to keep users "in the loop" about development activity. I personally like this. One major beef I have with Breezy is that a system that works today may not work after tommorrow's dist-upgrade, primarily due to bad luck (pulling an update of a package before the maintainer's finished his work). With SuSE, there's some assurance that the beta milestones are usable to some degree.

---

### Post by jdong on 2005-08-27
[QUOTE=Mishura]I wonder, with a Open version of Suse, some of the things that made it stand out (proprietary addons) won't be included.  I hope that there is a repo that can easily install these extra stuff.. and I hope they stop crippling Xine/Mplayer/etc..  just ship it w/o the codecs..
[/quote]

Well, from the way it looks now, it seems like the net downloadable ISO's will only have OSS, but there will be yast installation repos available for restricted software. Probably, the retail editions will contain the proprietary stuff, too. (of course, it's too early to know for sure).

As far as crippling the stuff, I really don't like them doing it, but at least it causes these programs to show meaningful error messages, with a link to a page describing the problem. I personally don't have a problem with it (installing a new mplayer RPM from the codecs package provider is just as easy as just the codecs), and understand that Novell has to keep things legal.

> 
Also, do they plan on using a Apt-4-rpm deal?  That would rock, and use Yast as a Apt frontend.
Hard to say. They've included APT in the base system, and have repomd for YUM in the YAST installation sources. As far as replacing YaST's dependency resolver with APT, I personally DISAGREE. I've found that YaST is much more flexible at dependency checking than APT. When there's multiple ways of solving dependency problems, YaST lets you choose. You can also ignore certain dependency checks (if you know what you're doing!), and YaST will remember that for the future. Very useful if you need to install single RPMs that aren't specifically for SuSE, but you can't do much about it (i.e. commercial software)

---

