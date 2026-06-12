---
title: "Installing OpenSuse, any things I should be aware of?"
date: 2009-06-07
forum: The Cafe
---

### Post by billgoldberg on 2009-06-07
Just for kicks I decided to install OpenSuse over Ubuntu 9.04 *(the iso is downloading right now)*.

I'm going for the KDE version.

I never used a RPM based distro before.

What are some of the biggest differences between Ubuntu and OpenSuse?

---

### Post by FalloutMan on 2009-06-07
the fact that there are a few features missing and my sound didnt work made me leave OS and go to ubuntu. i dunno its alright but imho ubuntu is better.

---

### Post by SuperSonic4 on 2009-06-07
I found OpenSUSE to be quite clunky and relatively confusing as to sorting out my repos and installing stuff from nvidia.

---

### Post by MikeTheC on 2009-06-07
I, too found OpenSuSE to be inadequate. Don't get me wrong, there are definitely some neat things about it. Scribus, for instance, runs *considerably* better on it, and their startup manager looks a heck of a lot more professional. However, and especially under a KDE install, both their app launcher and software installation manager (yast, I believe) are not at all intuitive or user-friendly. The Gnome install is a little bit better, but not much.

In short, it lasted about a day on my system.

Might I suggest that, with respect, you should wait another couple days until Fedora 11 is released and then usethat if you want to try an RPM-based distro.

---

### Post by billgoldberg on 2009-06-07
> **MikeTheC said:**
> I, too found OpenSuSE to be inadequate. Don't get me wrong, there are definitely some neat things about it. Scribus, for instance, runs *considerably* better on it, and their startup manager looks a heck of a lot more professional. However, and especially under a KDE install, both their app launcher and software installation manager (yast, I believe) are not at all intuitive or user-friendly. The Gnome install is a little bit better, but not much.

In short, it lasted about a day on my system.

Might I suggest that, with respect, you should wait another couple days until Fedora 11 is released and then usethat if you want to try an RPM-based distro.

I didn't realize that a new Fedora release is coming out.

I'm in the process of burning the iso image right now, after failing the get it installed from my usb drive.

If I don't like it, I will give Fedora a try.

---

### Post by MikeTheC on 2009-06-07
> **billgoldberg said:**
> I didn't realize that a new Fedora release is coming out.

I'm in the process of burning the iso image right now, after failing the get it installed from my usb drive.

If I don't like it, I will give Fedora a try.

Yeah, they're defaulting to ext4 and aiming for a 20 sec max boot time from kernel load to GDM log-in. In my experience it usually takes about 18 seconds on my 2.7 GHz Athlon 5200+. That to me is *very* impressive.

---

### Post by Screwdriver0815 on 2009-06-07
the biggest difference is that opensuse uses this so called "one click install" for activating repositories and to install some things like the graphics drivers.

For that you have to search on the opensuse site for a one click install link. This leads the package manager (yast) to the right place where to find the repo respectivly the install data for the desired software.

This is a little bit confusing.

using rpm instead of deb is not such a big difference. 

My experience was also that the help and support always repeats all the knowledge, the User already knows while the real existing questions remain unanswered. 

But anyway: good luck! (meant serious, not sarcastic)

---

### Post by gnomeuser on 2009-06-07
with openSUSE, the packman repo contains all the codec stuff, you can add it directly via YaST.

Also YaST while powerful is all to confusing and a lot of it's functionality should be replaced with automatic configuration like has been done upstream by Fedora (and which you have here on Ubuntu).

It's a very nice distro, especially the KDE edition I hear is a superior KDE offering (mostly since pretty much all the original SuSE employees use KDE and thus it gets tested and polished). 

I really like openSUSE, having used Fedora and Ubuntu though it does feel a bit like the middle sibling. It doesn't have the vast community of contributors that Fedora boasts and it doesn't have the huge following of users Ubuntu does. Yet they do a lot of interesting work and openSUSE is a very solid offering. 

Fedora 11 is coming out in 2 days, it might be worth it to have a look at that as well (and you are most welcome to poke me for help, I used to be a Fedora developer so I know my way around the system - in general though it works beautifully and rpmfusion.org provides those pesky legally encumbered packages).

---

### Post by billgoldberg on 2009-06-07
Thus far I'm pretty impressed by the KDE version of OpenSuse.

I still have to get used Yast a bit, but I like what I see thus far.

I hope I still feel the same way after the updates are installed and I actually start doing stuff on it.

---

### Post by billgoldberg on 2009-06-07
> **gnomeuser said:**
> 
Fedora 11 is coming out in 2 days, it might be worth it to have a look at that as well (and you are most welcome to poke me for help, I used to be a Fedora developer so I know my way around the system - in general though it works beautifully and rpmfusion.org provides those pesky legally encumbered packages).

I might take you up on that offer. :p

---

### Post by billgoldberg on 2009-06-07
Yup, as I feared something went wrong.

After installing my graphic card drivers, and rebooting, it stopped working.

No errors, my screen just won't come on anymore for OpenSuse.

I have no idea why.

I boot up, log in and the my monitor keeps trying to switch between digital and analog input after a while that goes away and the power light of the monitor goes off and on again forever.

I guess I will try Fedora next.

I'll be using Win7 for a day or two.

---

### Post by glotz on 2009-06-07
[http://en.wikipedia.org/wiki/Novell#Agreement_with_Microsoft](http://en.wikipedia.org/wiki/Novell#Agreement_with_Microsoft)

---

### Post by CJ Master on 2009-06-07
> **glotz said:**
> [http://en.wikipedia.org/wiki/Novell#Agreement_with_Microsoft](http://en.wikipedia.org/wiki/Novell#Agreement_with_Microsoft)

Who cares? :)

---

### Post by gnomeuser on 2009-06-07
> **billgoldberg said:**
> 
I guess I will try Fedora next.

In that case in preparation:

[http://rpmfusion.org/](http://rpmfusion.org/)

There you will find repos (easily enablable, just follow the guide) that contain encumbered stuff like codecs, drivers and additionally packages. Use it wisely, you shouldn't need to install codecs, once the repo is enabled when you play a file PackageKit should pull in the required packages.

---

### Post by billgoldberg on 2009-06-07
> **gnomeuser said:**
> In that case in preparation:

[http://rpmfusion.org/](http://rpmfusion.org/)

There you will find repos (easily enablable, just follow the guide) that contain encumbered stuff like codecs, drivers and additionally packages. Use it wisely, you shouldn't need to install codecs, once the repo is enabled when you play a file PackageKit should pull in the required packages.

Thanks for the heads up, it will come in handy.

---

### Post by SunnyRabbiera on 2009-06-07
I have toyed around with OpenSuse 11.1 is not that great though.
11.0 is much more stable on my system

---

### Post by HappyFeet on 2009-06-07
> **billgoldberg said:**
> 
After installing my graphic card drivers, and rebooting, it stopped working.


Same thing happened to me after installing the Nvidia 180 drivers. After reboot, all I could get was a command prompt. I went into xorg.conf and changed nvidia to vesa and was able to get back to a desktop, but could not figure out why the nvidia drivers won't work. When all was said and done, I just wiped it out and moved on. 

I wasn't looking to replace ubuntu, just trying something new. I thought opensuse was solid, (except for the video issue) but it won't be replacing ubuntu for me anytime soon.

---

### Post by billgoldberg on 2009-06-08
> **HappyFeet said:**
> Same thing happened to me after installing the Nvidia 180 drivers. After reboot, all I could get was a command prompt. I went into xorg.conf and changed nvidia to vesa and was able to get back to a desktop, but could not figure out why the nvidia drivers won't work. When all was said and done, I just wiped it out and moved on. 

I wasn't looking to replace ubuntu, just trying something new. I thought opensuse was solid, (except for the video issue) but it won't be replacing ubuntu for me anytime soon.

That's the thing, I could figure it out if I got to a command prompt, but I can't.

---

### Post by Crafty Kisses on 2009-06-08
> **gnomeuser said:**
> Also YaST while powerful is all to confusing and a lot of it's functionality should be replaced with automatic configuration like has been done upstream by Fedora (and which you have here on Ubuntu).
How is YaST confusing one bit?

---

### Post by billgoldberg on 2009-06-08
Little update, I got it working.

The next problem was the sound.

It just didn't work.

I had to ran alsaconf and then I had to add my user to the audio group.

No biggie, but not exactly user friendly.

I must say I enjoy OpenSuse's implementation of KDE.

Much more stable than the Kubuntu one.

---

### Post by xArv3nx on 2009-06-08
> **billgoldberg said:**
> Little update, I got it working.

The next problem was the sound.

It just didn't work.

I had to ran alsaconf and then I had to add my user to the audio group.

No biggie, but not exactly user friendly.

I must say I enjoy OpenSuse's implementation of KDE.

Much more stable than the Kubuntu one.
which is funny because opensuse's kde is one major release behind kubuntu's latest kde. :p

---

### Post by gnomeuser on 2009-06-08
> **Codename said:**
> How is YaST confusing one bit?

It's a separate tool that fails to integrate, coming from a world where we put things in the right places, attempt to pick good defaults and doing things automatically that just seems wrong. It's a relic from the 90's and a major transitioning should have been undertaken when it was open sourced after Novell bought SuSE.

Aside that it presents an awful lot of options, and it's poorly tested. Take their fingerprint enroller e.g., it doesn't give  you feedback at all, it doesn't set the fingerprint reader for anything except login when perhaps one might also like to use it for policykit stuff. 

It's to big, it's prone to breakage and it's generally not pleasant to use. 

I have higher expectations from my computer than what YaST is capable of providing.

---

### Post by jimi_hendrix on 2009-06-08
> **billgoldberg said:**
> I didn't realize that a new Fedora release is coming out.

I'm in the process of burning the iso image right now, after failing the get it installed from my usb drive.

If I don't like it, I will give Fedora a try.

i have had it running for a few days so far... it rocks

---

### Post by Sublime Porte on 2009-06-08
> **Installing OpenSuse, any things I should be aware of?**[B]

Yes, Novell is a Microsoft-friendly company.

Their distro should be avoided at all costs. Anyone who buys into the Microsoft ownership of patents in Linux should be rejected outright.
[/B]

---

### Post by jimi_hendrix on 2009-06-08
> **MikeTheC said:**
> Yeah, they're defaulting to ext4 and aiming for a 20 sec max boot time from kernel load to GDM log-in. In my experience it usually takes about 18 seconds on my 2.7 GHz Athlon 5200+. That to me is *very* impressive.

no not fully ext4 to my knowledge...when i install they demand my /boot is ext3 because they are using an older grub :(

---

### Post by Skripka on 2009-06-08
> **billgoldberg said:**
> 
Much more stable than the Kubuntu one.

Not too surprising ;)

---

### Post by growled on 2009-06-08
> **billgoldberg said:**
> 
I must say I enjoy OpenSuse's implementation of KDE.

Much more stable than the Kubuntu one.

Not in my world. Kubuntu beats openSuse too bad to even talk about. I've never got why people slag on Kubuntu. It's stable, it's fast, and it has the best community and documentation behind it. openSuse 11.1 is buggy as heck and Yast is just terrible.

---

### Post by hoagie on 2009-06-08
I tried openSuse and it was very unstable and a pain to configure. If you want a nice implementation of KDE 4 try Mandriva 2009.1. Rock solid!

---

### Post by billgoldberg on 2009-06-08
> **growled said:**
> Not in my world. Kubuntu beats openSuse too bad to even talk about. I've never got why people slag on Kubuntu. It's stable, it's fast, and it has the best community and documentation behind it. openSuse 11.1 is buggy as heck and Yast is just terrible.

I can only talk about my own experiences.

I installed the Kubuntu desktop in Ubuntu and KDE (plasma?) crashed every 10 minutes.

Also, there seems to be a bug with kde and ubuntu on my pc that causes xorg to take up 88% of my cpu.

I'm not claiming here OpenSuse is the best distro around, I still think Ubuntu is, but it's a decent one.

---

### Post by billgoldberg on 2009-06-08
> **Sublime Porte said:**
> Yes, Novell is a Microsoft-friendly company.

Their distro should be avoided at all costs. Anyone who buys into the Microsoft ownership of patents in Linux should be rejected outright.
[/B]

I know that, but I don't see the problem.

I'm not in the anti-windows camp.

Also, you do realize that Ubuntu comes with [Mono]("http://www.mono-project.com/Main_Page"), which is Novell tech?

---

### Post by unknownPoster on 2009-06-08
lol @ anti-novell trolls.

Anyway...

I desperately want to try the most recent release openSuSE, but it will not install correctly for me. I would like to say that I'm doing something wrong, but I doubt it... something just doesn't work correctly, it could be some random laptop hardware I have or something...

About 3 years ago, when I was first messing around with Linux I installed a release of openSuSE. I thought it was very professionally made and the aesthetics were pleasing. At the time, since I was coming from Synaptic/apt-get,  YAST confused the hell out of me... so I scrapped it fairly quickly.

---

### Post by Sublime Porte on 2009-06-08
> Also, you do realize that Ubuntu comes with [Mono]("http://www.mono-project.com/Main_Page"), which is Novell tech?

Yes, but I don't see Canonical lining up to validate Microsoft's rubbish patent claims.
Anyway I don't use mono (as far as I'm aware), and I disagree with the whole point of it.

> lol @ anti-novell trolls.

Hate to break it to you, but troll doesn't mean "anyone who says something I don't agree with".
A troll is someone who says things merely to incite others. My intention is not to incite anyone, but to inform people about the dangers of supporting those companies that have bought into the whole Microsoft patent deal. those companies will end up hurting Linux and open source software, by giving some credibility to Microsoft's claims. Therefore a conscientious Linux user would avoid them, and withdraw their support for them.

---

### Post by unknownPoster on 2009-06-08
> **Sublime Porte said:**
> 

Their distro should be avoided at all costs. Anyone who buys into the Microsoft ownership of patents in Linux should be rejected outright.



Sounds like trolling to me. Even though Novell produces a high quality, and FREE, operating system they should be avoided just because they have a deal with Microsoft.

Get over yourself...

Any distribution that has commercial backing and corporate viability probably contributing more to open source than some purely "free" distribution. Novell, along with RedHat, is getting Linux out there in the corporate world. I can't complain about that.

---

### Post by MikeTheC on 2009-06-08
I'm glad to know things are going better for the OP.

---

### Post by NightwishFan on 2009-06-08
I would rather use OpenSUSE personally. I do not have the internet on my main PC, so I like the DVD installer, and YAST, as well as the general feel of the system.

However! 11.1 seems to not work... at all.. I would rather the devs follow a 'Withhold a feature rather than include a broken one' philosophy.

Examples:

KDE4 Phonon Gstreamer Backend does NOT work with Amarok, and breaks my sound often.

Not only are Gstreamer and Phonon buggy, but they run on top of Pulseaudio by default, which is broken....

So I need to remove Alsa-Plugins-Pulse, manually find RPMS for KDE3-Amarok and XINE, Remove Xine-Pulse.

This means it is not good for my desktop. Since 90% of what I do revolves around listening to and composing/recording music.


I do not blame the devs much. When something 'does' work, it works amazingly. It is just not for me. Perhaps I will try 11.2 :D

---

### Post by Sublime Porte on 2009-06-08
> Sounds like trolling to me
Get over yourself....

As stated above, trolling is not merely disagreeing with or criticising something _you_ happen to like. Indeed somebody certainly needs to get over themself.

> Even though Novell produces a high quality, and FREE, operating system they should be avoided just because they have a deal with Microsoft.

Obviously your definition of free is limited to the 'free beer' scenario. Any company that enters into an agreement with companies like Microsoft, validating their claims to IP ownership over parts of GNU/Linux is doing nothing but damaging the freedom of GNU/Linux. Just because you're not paying money for it today, doesn't mean it fits our definition of 'free'.

Some have spent a long time contributing to, using and supporting the various free software projects that make up GNU/Linux, and we don't want to sit back and watch some corporation come in, claim to represent us, and then sell out our project to the highest bidder. Obviously that means little to you, as you view it merely in terms of cost.

---

### Post by unknownPoster on 2009-06-08
> **Sublime Porte said:**
> 

Some have spent a long time contributing to, using and supporting the various free software projects that make up GNU/Linux, and we don't want to sit back and watch some corporation come in, claim to represent us, and then sell out our project to the highest bidder. Obviously that means little to you, as you view it merely in terms of cost.

So I assume you go through the source code of your kernel, Gnome, and KDE and remove every line that Novell contributed to.

The truth is that without the contributions of Novell or RedHat we wouldn't be where we are right now.

I'm done with this though. It's gone way off topic.

I apologize to the OP for derailing this.

---

### Post by MikeTheC on 2009-06-08
[font=arial]**Positive Things You Should Know About OpenSuSE:**[/font]
[list][*] It is hardened against attacks which utilize Vogon poetry;
[*] Had NCC-1701's computer systems been running it at the time, it would not have been vaporized by the Genesis Device;
[*] Rumor has it a U.N.I.T. technician was spotted installing it on their servers;
[*] Your regular coffee was secretly replaced by freeze-dried OpenSuSE crystals and you didn't notice the difference;
[*] Even Chuck Norris cannot close SuSE[/list]

---

