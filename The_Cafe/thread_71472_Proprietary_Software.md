---
title: "Proprietary Software"
date: 2005-10-03
forum: The Cafe
---

### Post by brentoboy on 2005-10-03
No Flames Please.

Based on this thread, (which is going downhill) I want to start a fresh, more civil conversation.   :)   Humanity to all.
[http://www.ubuntuforums.org/showthread.php?t=71368](http://www.ubuntuforums.org/showthread.php?t=71368)
---
Proprietary Software:

Axioms:
1) Synaptic (or apt) is THE correct way to handle installing and updating packages
2) Ubuntu is free (as in freedom) and always will be
3) Some people want to use proprietary software (and even purchase it in some cases) 
4) Humanity to all, and linux = Choice means people should be allowed to use Linux in whatever way they want.

Conclusions based on these axioms:
1) Ubuntu is not responsible to support -  or offer proprietary stuff in their downloads, and should not offer anything as part of their distro that is a "30 day commercial" for a free app.  This is based on axiom #2

2) People who want a proprietary software  (such as vmware, nerolinux, diablo3forlinux, nvidia drivers, whatever) should be able to get it via syntaptic.   (based on Axiom #1 and #4)

How this SHOULD be done

1) Proprietary software companies should offer their own repositories which you would add to your sources list.
2) You can install what you want, and the proprietary software needs to protect itself with some kind of unlock code or internet registration or whatever stupid thing the company who distributes it wants to do.
3) Synaptic should auto update the proprietary stuff just like everything else, because it is just checking known repositories for existing stuff.

How this can become reality:

1) send your complaints to the folks at nero and vmware and ... whomeever ... Tell them to make an apt based repository with an ubuntu tree. so you can buy their stuff.
2) The wiki should contain info about how to go about getting specific popular packages.
---

Those people who want nothing to do with proprietary stuff dont ever have to care about it again.

---

please comment, lets work out a good idea and then submit it to developers if there is anything they actually need to do.

---

### Post by irish rebel on 2005-10-03
Excellent approach! In the referred to thread thats what I was advocating.

---

### Post by poofyhairguy on 2005-10-03
I think a better solution would be to make Impilinux the proprietary version of Ubuntu, instead of bending Ubuntu into that role:

[http://www.ubuntuforums.org/showthread.php?t=70349](http://www.ubuntuforums.org/showthread.php?t=70349)

---

### Post by irish rebel on 2005-10-03
on my Pc at home I use for the most part free software , my kids on the other hand want to play  URT2004 ,DOOM3, AND WARCRAFT so I buy the games and go thru hell installing them  I also subscribe to cedega because oldest son plays warcraft and it doesnt have a native port. I downloaded and paid for nero for linux simply because I didnt want to install all those kde libs just to burn cd's and dvd's with K3B. 
So yes I agree with your idea get these programs on the synaptic ubuntu branch and if people want them they can buy them.

---

### Post by 23meg on 2005-10-03
i don't endorse this approach. apt repositories should be totally disconnected with vendor based non-free software distribution. as i've suggested elsewhere, maybe an apt variant with advanced handling of unlock keys and extra secure cryptography would do the job, but apt itself should be isolated. one reason is, once it becomes possible to do this with apt, it can become commonplace, and may encourage a trend in new linux programmers to opt for such a distribution route. that would be against Debian's basic principles, and would be making a mess of an elegant distribution system that's based on a rigid, uncompromising ethical stance.

---

### Post by 23meg on 2005-10-03
> I downloaded and paid for nero for linux simply because I didnt want to install all those kde libs just to burn cd's and dvd's with K3B.

one question: were you honestly aware of the presence of Graveman and Gnomebaker?

---

### Post by poofyhairguy on 2005-10-03
[QUOTE=irish rebel]
So yes I agree with your idea get these programs on the synaptic ubuntu branch and if people want them they can buy them.[/QUOTE]

Problem is that its not our decision. With this plan as it is the developers of third party software must do all they work in making new repos. Why would they when they could just make a Redhat RPM (or a SUSE rpm) instead and hit almost just as large of desktop base, or just continue to deliver Windows software with a base 100 times that?

That is the essential problem.

---

### Post by brentoboy on 2005-10-03
[QUOTE=poofyhairguy]I think a better solution would be to make Impilinux the proprietary version of Ubuntu, instead of bending Ubuntu into that role:
[http://www.ubuntuforums.org/showthread.php?t=70349](http://www.ubuntuforums.org/showthread.php?t=70349)[/QUOTE]
I have to disagree.
Making another distro is not the right answer.
The whole problem with linux (when it comes to comercial software) is that there is not a standard to compile against.  Anther distro just makes folks ignore the linux group even more. 
There is strength in numbers.  In order to get blizard to make cool linux games, you've got to have a userbase that is large enough to target.

Core linux is free, and should stay that way, there should be no "comercial version" there are only commercial apps - for use on the free version.   they just have to be offered by comercial companies, not ubuntu directly (or indirectly).

---

### Post by floyd27 on 2005-10-03
you ccan also use your nero key for windows and it will work with linux..
its not "free" but you can aquire one on the net in no time...

---

### Post by Knome_fan on 2005-10-03
First off, good post brentoboy.
Some comments though.
Isn't what you describe pretty much the way it is now?
I mean nobody is stopping anyone from offering debs or their own repositories. All that's missing, as has been noted by many people already, is a nice way to install debs that are not in a repository.
@irish rebel: Don't get me wrong, there's nothing wrong with you using nero linux, but did you give gnome-baker and graveman a try recently? They may not be as full featured as nero (though I wouldn't really know, I never tried it), but they sure a quite nice.
@poofyhairguy:
I can't really follow you? What exactly should be reserved for Impilinux? If you mean coming preinstalled with non-free apps, I agree with you.

---

### Post by az on 2005-10-03
Dissalowing additional repositories would be against the basic pronciples of free software.

Impilinux is just a thing.  I doubt it will become the non-free cousin of Ubuntu.  If anything it is a local enterprise that Mark Shuttleworth is encouraging.

The way open source software works is that there is the source and the distributions distribute the applications.  If proprietary software is not available as source, then it is a third-party application.  Is it up to each and every third-party application developer to provide binaries for each and every linux distribution out there?  No.

It sounds like a middle-enterprise is needed to licence and redistribute all this third-party software.  So, for example, Poofyhairguy decides that he wants to distribute vwmare and some windows codecs.  Well, he goes to them and says that he wants to redistribute (sell) their stuff. He compiles and configures all the packages so that they install out-of-the-box and sells them, keeping his share of the profit.

Is what everybody saying that Ubuntu should provide a framework for this that is easier to plug into?

---

### Post by poofyhairguy on 2005-10-03
[QUOTE=Knome_fan]
@poofyhairguy:
I can't really follow you? What exactly should be reserved for Impilinux? If you mean coming preinstalled with non-free apps, I agree with you.[/QUOTE]

Thats the point. Its the best solution. I, you and Mark think that.

---

### Post by brentoboy on 2005-10-03
[QUOTE=poofyhairguy]Problem is that its not our decision. With this plan as it is the developers of third party software must do all they work in making new repos. Why would they when they could just make a Redhat RPM (or a SUSE rpm) instead and hit almost just as large of desktop base, or just continue to deliver Windows software with a base 100 times that?
That is the essential problem.[/QUOTE]
It is our decistion
We have to make noise to folks like vmware and make them host a repository that fixes the problem.

Look at thier forums - installation is a support cost.  They would love to make an install that works on our kernel and offer a simple way to install it without all the installation nightmare.  They just arent going to create a nice installer for every new linux platform that springs up.

---

### Post by poofyhairguy on 2005-10-03
[QUOTE=brentoboy]
There is strength in numbers.  In order to get blizard to make cool linux games, you've got to have a userbase that is large enough to target.
[/QUOTE]

If Impi is based on Ubuntu and it is run by Mark, my gut tells me that Mark won't let them be uncompatible.


So if you make a deb for one it will run on both. I was just saying that for better "out of the box" support, Impi should be where the emphasis goes.

---

### Post by poofyhairguy on 2005-10-03
[QUOTE=brentoboy]It is our decistion
We have to make noise to folks like vmware and make them host a repository that fixes the problem.
[/QUOTE]

Actually, I hear that VMware plans to make an Ubuntu version. So at some level you are correct.

---

### Post by UbuWu on 2005-10-03
I don't like the idea of adding repositories for every piece of commercial software I want to install. I think integrating autopackage + some kind of update mechanism for it would be better.

---

### Post by brentoboy on 2005-10-03
It is important that the ubuntu repositories dont contain comercial applications.
ubuntu's purpose is not to help people make money by selling software, or making it easy to distribute

the problem is squairly in the court of the person selling the software.
They need to host a repository with trees for all the distros they support.

We need to tell them that ubuntu is a large distro with a customer base.
Debian has lots of apt based derivites, that could be supported.  They just havent yet becuase debian has been a "free" as in "Freedom" distro, and therefor not a good target for comercial apps.

Ubuntu has changed that by making anyone and everyone able to use linux, and some people (like my boss) like to purchase software just so they have someone to call and complain to if thier's a problem.

---

### Post by UbuWu on 2005-10-03
[QUOTE=poofyhairguy]Actually, I hear that VMware plans to make an Ubuntu version. So at some level you are correct.[/QUOTE]

No vmware is adding support for installing ubuntu on it. It is not that they are making it easier to install vmware on ubuntu.

---

### Post by poofyhairguy on 2005-10-03
[QUOTE=UbuWu]No vmware is adding support for installing ubuntu on it. It is not that they are making it easier to install vmware on ubuntu.[/QUOTE]


I stand corrected.

---

### Post by az on 2005-10-03
[QUOTE=brentoboy]I
Debian has lots of apt based derivites, that could be supported.  They just havent yet becuase debian has been a "free" as in "Freedom" distro, and therefor not a good target for comercial apps.
Ubuntu has changed that by making anyone and everyone able to use linux, and some people (like my boss) like to purchase software just so they have someone to call and complain to if thier's a problem.[/QUOTE]

I am sure that your boss would have no trouble finding someone to pay to support all of the companie's linux boxes.  *No* trouble at all.  I am sure this has been true for the past five or ten years.

---

### Post by brentoboy on 2005-10-03
[QUOTE=azz]I am sure that your boss would have no trouble finding someone to pay to support all of the companie's linux boxes.  *No* trouble at all.  I am sure this has been true for the past five or ten years.[/QUOTE]

Yes, but what he really wants is the multi-thousand dollars worth of adobe photoshop licenses to carry over to linux, so he can have a safe network, and not loose all the psd files that the company thrives on.  and still take advantage of all the other free stuff out there that is ours to enjoy.

---

### Post by blastus on 2005-10-03
I don't have anything against proprietary software in general. Without some proprietary software we would not have some of the commercial innovation that has contributed to some open standards/formats. 

But most proprietary software is built on and encourages proprietary standards/formats, which in turn supports vendor lock-in, anti-competitive behavior, consumer manipulation, propaganda based on half-truths, neverending patents and software monopolies. But free software (as in freedom) encourages the exact opposite.

Proprietary software is not a bad thing as long as it is built on and endorses open standards/formats. Unfortunately, the most proprietary software vendors are tacitly against the full and unconditional adoption of purely open standards/formats--for the reasons I quoted above.

---

### Post by bob_c_b on 2005-10-03
[QUOTE=brentoboy]Yes, but what he really wants is the multi-thousand dollars worth of adobe photoshop licenses to carry over to linux, so he can have a safe network, and not loose all the psd files that the company thrives on.  and still take advantage of all the other free stuff out there that is ours to enjoy.[/QUOTE]

This is an unrealistic viewpoint, odds are good if Adobe did a Linux port you could not recycle your old Windows or Mac serial #s, you certainly can't do that now with the more current versions (no flipping between Mac or Windows any longer). 

I'm not sure we really want all the headaches that many proprietary vendors will bring to Linux. Better to continue supporting open code and open standards. A sudden burst of support from a company like Adobe will bring massive license restrictions to our free platform, don't forget Adobe is a founding memeber of the BSA.

I'm not sure where people are getting the idea that ANY distro can take out MS or move the market to open standards any time soon. This will be a slow process as more and more people realize that their data is held captive by commerical software companies and their "secret bits".  Mark wants to make sure Dapper Drake is the best possible option to Vista there is, but I doubt he has any illusions about somehow toppling MS in less than 18 months. Some of you need to scale back your dreams and know that much of the Linux community is just hoping and working towards "10X10", or 10% of the desktop market by 2010.

Now is not the time for F/OSS to start bending over for commercial software houses, now is the time to stick to our principals and vote with our money. Let the big software houses know you can live without them, stop begging them to take your money with inferior Wine/Cedega ports. If you can't live without Half Life 2 and PhotoShop you may have to live with Windows for a while longer, but polluting F/OSS with this stuff is good for no one. 

Want to show commercial support for Linux? Go buy UT2K4 with it's native Linux support. Buy Uplink and Darwinia from Introversion since they actively support Linux. Donate to the Mozilla Foundation (buy a t-shirt). O'reilly wants your money and does quite a bit for F/OSS. Donate to Canonical, Mandriva, OOo, etc... There are lots of ways to show Linux is commercially viable, start doing it.

---

### Post by brentoboy on 2005-10-03
[QUOTE=23meg]i don't endorse this approach. apt repositories should be totally disconnected with vendor based non-free software distribution. as i've suggested elsewhere, maybe an apt variant with advanced handling of unlock keys and extra secure cryptography would do the job, but apt itself should be isolated. one reason is, once it becomes possible to do this with apt, it can become commonplace, and may encourage a trend in new linux programmers to opt for such a distribution route. that would be against Debian's basic principles, and would be making a mess of an elegant distribution system that's based on a rigid, uncompromising ethical stance.[/QUOTE]

This is an interesting delima.

If apt supports the use of "subscription" repositories with keycodes and passwords, then people will do it.

If people do it, they might make money.  So, then it will become popular.

And before long, the Free stuff gets shut out by all the noisemakers out there, becuase it pays to make noise.

---
I have to admit, One of the things I have enjoyed the most since installing Ubuntu is that I dont have to find a keycode for every freeking thing I try to install.  And that I dont have to be tempted to be a pirate in order to make my pc do really basic things.

I would hate to encorage something that would ruin that beautiful paridice.

Im torn.

I want the best of both worlds!!! why cant I have everything!!!

---

### Post by bob_c_b on 2005-10-03
[QUOTE=brentoboy]
Im torn.
I want the best of both worlds!!! why cant I have everything!!![/QUOTE]

Learn to love the Pain!!!:)

---

### Post by brentoboy on 2005-10-03
[QUOTE=bob_c_b]Learn to love the Pain!!!:)[/QUOTE]

Tell that to my boss, my parents - and my wife.

:)

---

### Post by bob_c_b on 2005-10-03
[QUOTE=brentoboy]Tell that to my boss, my parents - and my wife.
:)[/QUOTE]

Like I said before, in some sitautions some people can't just eliminate Windows. My wife doesn't like Linux, but she loves her Mac. I use Windows at work all day, but whenever possible I replace a piece of proprietary software with F/OSS, have replaced a number of utility servers with Linux boxes, etc... You do the best you can whenever you can and rest assured we are making a dent.

But truly, you can't have it both ways. No doubt some commercial software will transition nicely to Linux, but we should be careful who we invite in, MS isn't the only bad apple in that barrel.

---

### Post by sinbad782 on 2005-11-21
I think having some proprietary software is fine in Synaptic through the non-free/multiverse repos. But then if you are distributing large bits of software like commercial games this probably isn't the best way. 

I guess you could add in modules to Synaptic for handling software download account passwords etc, but then this would be easier to achieve using something like Linspire's CNR which uses a web-based interface. As long as the software being distributed is packaged correctly (as debs so that APT knows about it) it should be easier to download from multiple, dynamic sources rather than from a static list of repos, and since the interface is web-based, you can change the look and maintain this easily too. An attractive web catalogue of available software can look really nice - for a good example see:

[http://www.apple.com/macosx/applications/](http://www.apple.com/macosx/applications/)

The other general point regarding Linux, is that it still isn't easy enough for third-parties to create unified packages which are distribution-agnostic - see for example, Opera or Skype where there are tons of different packages for the different mainstream distros.  

I definitely think that standardisation initiatives like the LSB deserve support and that enabling the creation of single self-contained 'GNU/Linux' packages is something worth working towards. Maybe something like autopackage might provide a good front-end for all the various package managers (apt, rpm, portage, pacman etc.)

---

### Post by poofyhairguy on 2005-11-21
[QUOTE=sinbad782]I think having some proprietary software is fine in Synaptic through the non-free/multiverse repos. But then if you are distributing large bits of software like commercial games this probably isn't the best way. 

I guess you could add in modules to Synaptic for handling software download account passwords etc, but then this would be easier to achieve using something like Linspire's CNR which uses a web-based interface. As long as the software being distributed is packaged correctly (as debs so that APT knows about it) it should be easier to download from multiple, dynamic sources rather than from a static list of repos, and since the interface is web-based, you can change the look and maintain this easily too. An attractive web catalogue of available software can look really nice - for a good example see:

[http://www.apple.com/macosx/applications/](http://www.apple.com/macosx/applications/)

The other general point regarding Linux, is that it still isn't easy enough for third-parties to create unified packages which are distribution-agnostic - see for example, Opera or Skype where there are tons of different packages for the different mainstream distros.  

I definitely think that standardisation initiatives like the LSB deserve support and that enabling the creation of single self-contained 'GNU/Linux' packages is something worth working towards. [/QUOTE]

Klik

[http://klik.atekon.de/](http://klik.atekon.de/)

---

