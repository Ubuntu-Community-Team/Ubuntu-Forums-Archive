---
title: "Ubuntu Breezy Final, not as good as Suse 10"
date: 2005-10-14
forum: The Cafe
---

### Post by ubuntufans on 2005-10-14
I was excited about 5.10, installed it and redo the WPA supplicant and etc and works but started to have many problems with ndsiwrapper after a while (random disconnects and kernel panic)

so i downloaded suse 10, installed it and to my supprise it comes with ndiswrapper and wpa_supplicant (so no extra work needed) and apparently the network setup wizard is so easy to use to guide me to enter my wireless network info, and got into gnome bammm my wireless works out of box.

so i figured let's put it to another test, i grabbed a mimo wireless card from belkin, run ndiswrapper to install it and add hotplug entry to it rebooted, and guess what, it works still :p

i have to say, we should learn about how suse handles wireless as many people are starting to use them, i like ubuntu still, but hey there will always be place for improvement, and i hope we can take all the good stuff into ubuntu one day. for now, i'll stay with suse 10

---

### Post by erikpiper on 2005-10-14
Yah, but does Suse have APT or equivlelent?

---

### Post by bugi on 2005-10-15
[QUOTE=erikpiper]Yah, but does Suse have APT or equivlelent?[/QUOTE]

SUSE has YaST but you can also use apt, yum or red-carpet. SUSE is different, SUSE is big (5CDs), Ubuntu is more polished (1CD) and based on Debian while SUSE is based on Slackware and uses RPMs. So you can't easily compare them.

---

### Post by Knome_fan on 2005-10-15
[QUOTE=bugi]SUSE has YaST but you can also use apt, yum or red-carpet. SUSE is different, SUSE is big (5CDs), Ubuntu is more polished (1CD) and based on Debian while SUSE is based on Slackware and uses RPMs. So you can't easily compare them.[/QUOTE]

Suse is not based on Slack (where did you get this idea?) and there's also a 1 CD version. And though I obviously like (K)Ubuntu, I don't know why exactly I should consider it more polished than Suse.

---

### Post by asimon on 2005-10-15
[QUOTE=bugi]SUSE is based on Slackware and uses RPMs. So you can't easily compare them.[/QUOTE]
It _was_ based on Slackware long ago. S.u.S.E. Linux started as a German version of slackware. But they decided to move away from Slackware and thus based their distribution on Florian LaRoche's Jurix beginning with version 4.2. (The Jurix developer was later hired by S.u.S.E.). Today SUSE isn't based on any other distro any longer. Look at the packages, look at the development. They no longer take the packages from some other distro and add to them.

Besides SUSE 10.0 is an absolut fantastic distro. SUSE, *buntu, and Fedora are all great distros on their own (My Mandrake/Mandriva expierience is too old to say something about it). I'am happy that we can choose among so many great products.

Cheers

---

### Post by Nomearod on 2005-10-15
I installed Suse 10 in my Descktop but it was only till Ubuntu's 5.10 release, but know I installed Ubuntu with Suse.

Suse has a lot of programs, and it detected all my hardware with no problems ( even the printer was detected and started to work since the first boot ) and till now, i didn't had any problems. 

But I really liked Ubuntu 5.10, and with ndiswrapper my wireless card was detected in the laptop. The only thing that I don't like in Suse, is the YaST, because it doens't have many programs to install... 

But i'm a n00b...

Btw, sorry my bad english but I'm Portuguese... : /

---

### Post by az on 2005-10-15
[http://packages.ubuntu.com/breezy/net/wpasupplicant](http://packages.ubuntu.com/breezy/net/wpasupplicant)


wpa supplicant is in universe.

---

### Post by bugi on 2005-10-15
[QUOTE=Knome_fan]Suse is not based on Slack (where did you get this idea?) and there's also a 1 CD version. And though I obviously like (K)Ubuntu, I don't know why exactly I should consider it more polished than Suse.[/QUOTE]

Ok, SUSE _was_ based on Slack ;-) 1CD version is very old now (SUSE 9.1 Personal) so we can't compare it to the new Ubuntu 5.10 (well, maybe you are thinking about SUPER or SLICK but it is not the very same as "normal version"). By "more polished" i mean : less packages, less bugs, more stable (based on Debian), faster installation. SUSE is overloaded by applications and should be released on 1 or 2 CD version instead of 5CD. I don't like one more thing, for default KDE installation i need 4CDs, while Mandriva needs only 1CD.

---

### Post by Lord Illidan on 2005-10-15
I believe that being able to use wifi drivers under a distro without excessive configuration and the like is more important than having apt or synaptic. What's the good of having synaptic if you can't connect to the internet because of your problematic wifi drivers?

---

### Post by Manny C on 2005-10-15
[quote=Lord Illidan]I believe that being able to use wifi drivers under a distro without excessive configuration and the like is more important than having apt or synaptic. What's the good of having synaptic if you can't connect to the internet because of your problematic wifi drivers?[/quote] 
Good point Lord Illidan. I am not sure why people choose to use WPA. Anyone have good reasons for doing this when WEP works fine in Breezy?

It worked for me anyway. The install process picked up my wifi chip, asked me which network interface i wanted to use as default (ie. wired or wireless), chose wireless, filled in ESSID and WEP key and had my WIFI network working straight away. Upon bootup, Kubuntu picks up the fact that I like WIFI and dhclients the network so that when I log in, WIFI works perfectly. And the interface in KDE for wifi is terrible in comparison with some of the Gnome interfaces (Wifi-Radar, GTK-Wifi et al.)

The solution to all the world's wifi ills, is to use WEP (and make sure you don't own an obscure WIFI device ;) )

---

### Post by az on 2005-10-15
[QUOTE=Lord Illidan]I believe that being able to use wifi drivers under a distro without excessive configuration and the like is more important than having apt or synaptic. What's the good of having synaptic if you can't connect to the internet because of your problematic wifi drivers?[/QUOTE]

Most of the drivers that are available for distribution are on the install cd.

I value free software.  I would not want unlicenced or proprietary software laying around my system without my wanting it there.  In Ubuntu, all I have to do is remove the linux-restriced-modules package and everything on my box is GPL compatible.

How do you do that with SUSE?

---

### Post by kestasjk on 2005-10-15
WEP is inherently insecure, anyone can break into an access point if it's only been secured with WEP, whereas WPA is relatively quite secure (not as secure, or easy to manage, as 802.11i though).

That having been said 5.10 is great, hardware detection for my laptop is much better, and where I once had to use XP I now have a choice. :) Great job Ubuntu team!

---

### Post by Lovechild on 2005-10-15
I never really liked SuSE, YaST bugged me as it produced some funky configuration results and the default dependencies caused it to isntall all sorts of stuff I didn't need - cleaning it up was much more work than cleaning up Ubuntu.

Not to mention as a GNOME user, their GNOME has never been very good, and the official updates killed my desktop more than once. Their KDE is much better so for that section of users SuSE might appeal more. 

The good thing about SuSE is that previously when Internet connection was rare in some places, SuSE came with every piece of new software ever so often - I guess that's why it grew popular, but it's not really an especially good distro IMHO.

---

### Post by mstlyevil on 2005-10-15
[QUOTE=Lovechild]I never really liked SuSE, YaST bugged me as it produced some funky configuration results and the default dependencies caused it to isntall all sorts of stuff I didn't need - cleaning it up was much more work than cleaning up Ubuntu.

Not to mention as a GNOME user, their GNOME has never been very good, and the official updates killed my desktop more than once. Their KDE is much better so for that section of users SuSE might appeal more. 

The good thing about SuSE is that previously when Internet connection was rare in some places, SuSE came with every piece of new software ever so often - I guess that's why it grew popular, but it's not really an especially good distro IMHO.[/QUOTE]

 I downloaded and played with Suse 10 for about a day. They are right in that propietary software and drivers are included on trhe install. The downside to that was the hurdles Suse put in your way to get things like codecs. I got them installed and then had trouble getting amule,and azureus. The people on the forums are rude and seem to think the answer to every problem is to google it. I had trouble finding extra sources and then the servers were so overun that they either would not work or that they had a very bad connection. Suse is much more polished when it comes to the eye candy. They still lack a little in the user friendly department. I installed Kubuntu to see the difference (I used KDE in Suse because that is what everyone recommended) and I am going to tell you that Kubuntu takes a little longer to set up because you have to install all those programs yourself, but I am able to find everything I want and I did not have to google it.

---

### Post by Knome_fan on 2005-10-15
> **bugi]Ok, SUSE _was_ based on Slack  said:**
> 
ages ago...

[QUOTE=bugi]
1CD version is very old now (SUSE 9.1 Personal) so we can't compare it to the new Ubuntu 5.10 (well, maybe you are thinking about SUPER or SLICK but it is not the very same as "normal version"). 

Super also provides an unmodified normal version.

[QUOTE=bugi]
By "more polished" i mean : less packages, less bugs, more stable (based on Debian), faster installation.
[/quote]
Installation might be faster with ubuntu, but that's about it. And calling especially kubuntu more stable than Suse is simply a sad joke.

[QUOTE=bugi]
 SUSE is overloaded by applications and should be released on 1 or 2 CD version instead of 5CD. I don't like one more thing, for default KDE installation i need 4CDs, while Mandriva needs only 1CD.[/QUOTE]
Again, take the one CD install.
And though cutting down on some applications I doubt that Suse comes with significantly more applications in a default KDE install than Kubuntu.


@mstlyevil:
Suse repositories really are easy to find:
[http://www.opensuse.org/Package_Repositories](http://www.opensuse.org/Package_Repositories)

And then add the packman repos and off you go:
[http://www.opensuse.org/Additional_YaST_Package_Repositories](http://www.opensuse.org/Additional_YaST_Package_Repositories)

---

### Post by mstlyevil on 2005-10-15
I found them, but the servers were so overloaded at the time that it was a pain getting what I wanted. Also, I had packman and it still did not offer amule and azureus. Suse is a good distro, it is till too early to go to Suse 10. Kubuntu is just easier to get some extra software right now because it is more backwards compatible. I'll try Suse 10 again in a month or so when it gets it act together.

---

### Post by Muhammad on 2005-10-15
[QUOTE=Knome_fan]Suse is not based on Slack (where did you get this idea?) and there's also a 1 CD version. And though I obviously like (K)Ubuntu, I don't know why exactly I should consider it more polished than Suse.[/QUOTE]

Link?

---

### Post by Qrk on 2005-10-15
The one CD version can be found on the opensuse website.


I found SuSE much easier to use on the surface than Ubuntu. There were more GUI ways to configure it. But that made it more difficult when I wanted to change things with the command line. All of that auto-configuration didn't like when I manually edited a text file. 
So therefore I recommend SuSE to everyone who wants to try linux; even sometimes over Ubuntu (if they aren't the best with computers) but I stick with Ubuntu.
Really Ubuntu is excellent and very friendly to the unexpirenced. But there are better distros out there for the noob.

---

### Post by bugi on 2005-10-15
> **Knome_fan]Super also provides an unmodified normal version.[/quote]
Super is experimental, just look at this :
> The SUPER project concentrates on creating packages and modifications to SUSE Linux in the following areas:

    * Speed
    * Graphical Attractiveness
    * Missing features
    * **General Experiments**, **bleeding edge**.

> Installation might be faster with ubuntu, but that's about it. And calling especially kubuntu more stable than Suse is simply a sad joke.

Hey , but i didn't say **K**ubuntu, i said **U**buntu (because Kubuntu 5.04 was really buggy for me)  said:**
> Again, take the one CD install.
And though cutting down on some applications I doubt that Suse comes with significantly more applications in a default KDE install than Kubuntu.
Installing 3 text editors by default is not too much (OOo, Kate, KWrite, and few smaller)? And there are more cons, i.e. you can't turn off just cron, to turn off cron you will have to turn off hal daemon O_o (in previous versions like 9.1, 9.2 there wasn't such a problem).

---

### Post by Knome_fan on 2005-10-15
[QUOTE=Muhammad]Link?[/QUOTE]
[http://www.opensuse.org/1_CD_install](http://www.opensuse.org/1_CD_install)

There you'll find a modified version and a normal version.

[QUOTE=bugi]
Hey , but i didn't say Kubuntu, i said Ubuntu (because Kubuntu 5.04 was really buggy for me) Imo Ubuntu (thanks to Debian and Gnome) _is_ more stable because i noticed simply less crashes. Gnome in SUSE is a joke, KDE works very good but still isn't without bugs (i.e. there are some (the same) apps that still crash in 9.3 and new 10 version).
[/QUOTE]
Kubuntu is also based on Debian, which also according to you doesn't make it stable, so...
Anyway, I haven't tried Suse's Gnome very intensively, but I didn't notice any stability issues. And things like beagle, ifolder simply work, which is great.

[QUOTE=bugi]Installing 3 text editors by default is not too much (OOo, Kate, KWrite, and few smaller)?[/QUOTE]
First off, OOo certainly is a lot of things, but not a text editor.
And if you think Kate and Kwrite are too much, tell the kubuntu devs, as both are installed by default on Kubuntu (which isn't too surprising, as they are the very same app, only with different frontends.)

> And there are more cons, i.e. you can't turn off just cron, to turn off cron you will have to turn off hal daemon O_o (in previous versions like 9.1, 9.2 there wasn't such a problem).
Excuse me???????

---

### Post by Lovechild on 2005-10-15
The SUPER project seems to be run by the former Yoper ricer who favors things like compiling with -O3 and using Reiser4, now I'm all for optimization, but that is a very poorly researched way to do it.

---

### Post by cowlip on 2005-10-15
Well I tried Suse 10, and have tried suse 9, and I still don't think much of it.  I think synaptic is a much better way of downloading programs, and all the repositories weren't working.

---

### Post by mstlyevil on 2005-10-15
I will have to admit there is a lot I like about Suse better than Kubuntu. The gui is a little more polished and they have better eye candy out of the box. I like the fact that if you use the evaluation version that realplayer,adobe,flash and Java are already installed and ready to use. For a noob, it can be a little more of a pain finding help because the Suse community seems fractured with different forums and web sites. Also I want Amule and Azureus which seem to be a little elusive for Suse 10 right now unless you know how to compile it yourself. Overall it takes me less time to install and set up Kubuntu than it does Suse because I am spending so much time trying to figure out how to get it configured the way I want it. Suse is not better than Kubuntu or vise versa. They are just different and they both have different ways of doing things.

---

### Post by bugi on 2005-10-15
> **Knome_fan][http://www.opensuse.org/1_CD_install](http://www.opensuse.org/1_CD_install)

There you'll find a modified version and a normal version.[/quote]
I would not call it normal version, it is still separate project based on normal version. If SUSE team call it the official version i will agree with you  said:**
> Kubuntu is also based on Debian, which also according to you doesn't make it stable, so...
Anyway, I haven't tried Suse's Gnome very intensively, but I didn't notice any stability issues. And things like beagle, ifolder simply work, which is great.
Lucky you :-)

> First off, OOo certainly is a lot of things, but not a text editor.
And if you think Kate and Kwrite are too much, tell the kubuntu devs, as both are installed by default on Kubuntu (which isn't too surprising, as they are the very same app, only with different frontends.)
Again, i don't compare SUSE and Kubuntu but SUSE and Ubuntu (because i think that Ubuntu is more polished than Kubuntu too ;-) )


> Excuse me???????
Sorry for my bad English, i will try once more ;-)
I don't use cron daemon so i want to have it disabled. But if i try to disable cron daemon, YaST says it has to disable also hal daemon which i really need for my hardware to run properly. In previous version cron was "independent". This is what i call "not polished " :-)

---

### Post by TravisNewman on 2005-10-15
ok I"ll chime in on the Suse vs Breezy debate.

I have Suse installed right now, and I love it. I have breezy installed right now and I love it. Oddly enough, Suse seems to do things faster than Breezy, and Suse 10's Gnome is so so so much better than previous versions.  Suse also has the only KDE that I can enjoy using. Installing xfce, blackbox, etc, are also easy and aren't crippled at all. WPA works out of the box, without having to install extra packages. My printer works out of the box, without having to install extra packages. This is all on opensuse with no proprietary packages at all.

That said, there are a lot of weird issues. Mostly with Yast. While I love the simplicity of Yast, it just seems to break stuff all too often. The grub editor isn't very robust (though yay that they have one) and the X configuration got really hosed. For some reason, KDM was broken after I used it 3 times, and before I changed anything. Doesn't really bother me as I prefer GDM, but still a little odd. Overall Suse is very pleasant, but, like I said, odd things crop up. 

Breezy has it's share of odd things, but, because I'm more proficient with deb based systems than with anything else, I can fix them easier. It seems to be much easier to trim down and customize Breezy than with Suse 10. Breezy worked better out of the box with my laptop's functions than Suse 10 did, but I haven't fully tested things out with Suse yet, it could just be cranky.

They have their pros and cons, but Suse is shaping up to be hella good now that they've opened up the development process. I **use **Ubuntu, and I don't see that changing any time soon, but I've been trying out most of the big distros ever since I've been using Linux, and I see the progress between suse 9.3 and suse 10 to be the best jump yet. 

Good for them. It's not a threat to us at the Ubuntu camp, it's an addition to the Gnu/Linux community, and that's always a good thing. 

As far as what the topic states, I'm not sure I agree that Breezy final is not **as good** as Suse 10, but the jump in quality between Suse 9.3 and 10 is, in my opinion, a bigger jump in quality than between Hoary and Breezy.

---

### Post by bbrown on 2005-10-16
I haven't tried SuSe 10 yet but I have tried both ubuntu and kubuntu. Both are very good. I have used SuSe since ver 7 and have liked them. The last version I used was 9.3. This is the first distro that has caused me to look away since then. I generally check out new versions of other linuxes which is how this version got my attention. 

By the way as far as wifi goes this version rocks. I tried the live version on my Toshiba A25 and eveything worked out of the box even the wifi (athros). I would have to install the package for the function keys for them to work. 

I generally perfer a menu system for administration. Like when I work on AIX, HPUNIX, or (horror up horror) SCO (The origional from Santa Cruz). A menu system for administration is the only thing I think that would make it easer for New be's. 

The problem with Yast is it uses a configuration folder and the files there. This is what to me always made editing files harder because it wasn't consitant.

I also agree about SuSe support. The support here seems much better. If I have a problem I don't need to spend days, weeks, or months reading to type a line to fix something. That is one of the things that got me interested here. When someone has a problem, someone actually tries to help.  This will help spread liniux better than anything.

---

### Post by asimon on 2005-10-16
[QUOTE=azz]Most of the drivers that are available for distribution are on the install cd.[/quote]

SUSE Linux OSS 10.0 doesn't come with propritary stuff, although you can add all stuff that is missing from the boxed version from some [extra repository](ftp://ftp4.gwdg.de/pub/linux/suse/apt/SuSE/10.0-i386/RPMS.extra/) via internet . Only the boxed version, called SUSE Linux 10.0 (without the OSS) and the evaluation iso you can download contain the propritary stuff (including drivers) on the media.

[QUOTE=azz]I value free software.  I would not want unlicenced or proprietary software laying around my system without my wanting it there.  In Ubuntu, all I have to do is remove the linux-restriced-modules package and everything on my box is GPL compatible.

How do you do that with SUSE?[/QUOTE]

Although the package is not called linux-restriced-modules (it's something like kernel-default-nongpl-2.6.13-8.i586.rpm) you can uninstall packages on SUSE too, yes really!  ;-)

Besides from that all propritary stuff that comes with SUSE Linux (not the OSS version) is lisenced. SUSE/Novel has of course license agreements with the respective parties.

Regarding that Gnome desktop. Many people say that SUSE's Gnome is not good. Is that impression from older SUSE version or the current 10.0? I only use Gnome sporadically but from the looks the SUSE version seems fine to me. Even Beagle is started automatically and works like expected. Can people who say Gnome on SUSE is bad give some details (apart from Background and widget style). Thanks.

---

### Post by Muhammad on 2005-10-16
[QUOTE=Knome_fan][http://www.opensuse.org/1_CD_install](http://www.opensuse.org/1_CD_install)

There you'll find a modified version and a normal version.[/QUOTE]

Thanks alot for the link, I will go try it out now, but I ain't removin ubuntu ya hear :p

---

### Post by az on 2005-10-16
[QUOTE=asimon]Although the package is not called linux-restriced-modules (it's something like kernel-default-nongpl-2.6.13-8.i586.rpm) you can uninstall packages on SUSE too, yes really!  ;-)
.[/QUOTE]


I did not know that.  Debian and hence Ubuntu take a clear stance (which some people consider extreme), by properly separating firmware and kernel modules, for example.  SUSE traditionaly being a commercial distribution and only recently gaining a community orientation (an ubuntu trend?) makes me skeptical.

---

