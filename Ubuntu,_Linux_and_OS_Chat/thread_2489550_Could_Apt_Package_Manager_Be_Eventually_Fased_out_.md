---
title: "Could Apt Package Manager Be Eventually Fased out of LTS Releases?"
date: 2023-08-02
forum: Ubuntu, Linux and OS Chat
---

### Post by kabirgandhiok on 2023-08-02
Hi,

I can't help but wonder if the standard LTS release of Ubuntu will default to the new snap based Ubuntu Core and then eventually canonical may stop supporting the non-immutable, non-snap based LTS version. I mean the LTS may eventually become entirely snap based. And they may just restrict a choice between snap and deb packages to just their developmental, 6 monthly releases. So far the communication from canonical is clear, they will support both, but maybe that changes after the 24.04 LTS is out.

---

### Post by ian-weisser on 2023-08-02
Many things are *possible*. That does not mean they are likely.

Snap server has not replaced Ubuntu Server. They live happily side-by-side.

Snap desktop is experimental. Maybe it will work for many users, maybe it won't. That's what experiments are for.

There is no secret plan to abandon deb packages or apt. There never has been.

---

### Post by #&amp;thj^% on 2023-08-02
They are just recently, realizing that a preference for snaps are dwindling, so for now we have choices.
"I think personally" it will take a good 3-5 years before Canonical throws in the towel for snaps.
EDIT: Alan's Link:[https://github.com/popey/unsnap](https://github.com/popey/unsnap)

---

### Post by kabirgandhiok on 2023-08-02
> **ian-weisser said:**
> Many things are *possible*. That does not mean they are likely.

Snap server has not replaced Ubuntu Server. They live happily side-by-side.

Snap desktop is experimental. Maybe it will work for many users, maybe it won't. That's what experiments are for.

There is no secret plan to abandon deb packages or apt. There never has been.

They may not abandon apt or deb but just restrict it to their interim releases.

---

### Post by kabirgandhiok on 2023-08-02
> **1fallen said:**
> They are just recently, realizing that a preference for snaps are dwindling, so for now we have choices.
"I think personally" it will take a good 3-5 years before Canonical throws in the towel for snaps.
EDIT: Alan's Link:[https://github.com/popey/unsnap](https://github.com/popey/unsnap)
They have been throwing in the towel for a lot of their projects, maybe they don't this time. (I hope they do). I can't imagine using a Linux system that is locked down and cannot be changed, snaps or no snaps.

---

### Post by DuckHook on 2023-08-02
> **kabirgandhiok said:**
> …I can't imagine using a Linux system that is locked down and cannot be changed, snaps or no snaps.

This will never happen because the Linux ecosystem is self&#8209;correcting. Ubuntu is far from the only distro around and were Canonical to make as foolish a move as the one you posit, users would abandon them in droves.

Many of our own forum members have recently moved to Debian because of their distaste for snaps. That exodus is just a trickle compared to the torrent that would occur if Ubuntu were to become "locked down". This dynamic exists because of the FOSS nature of Linux and there's nothing that any corporation can do to stop it. FOSS enforces good behaviour on the whole ecosystem by punishing bad behaviour with easy forks and simple, limitless mobility. Canonical is well aware of this dynamic and would not shoot themselves in the foot.

---

### Post by ian-weisser on 2023-08-02
> **kabirgandhiok said:**
> I mean the LTS may eventually become entirely snap based.

> **kabirgandhiok said:**
> They have been throwing in the towel for a  lot of their projects, maybe they don't this time. (I hope they do).

Those seem contradictory predictions.



> **kabirgandhiok said:**
> And they may just restrict a choice between snap and deb packages to just their developmental, 6 monthly releases.

That's a direct contradiction of Mark Shuttleworth's keynote eight months ago at Ubuntu Summit 2022, where he specifically committed that Ubuntu will continue to be based upon Debian...including debs and apt. He been asked various similar questions since Ubuntu began, and I cannot find any record that he has ever deviated from that vision. Not once.

Not a single Ubuntu manager has breathed that such a change has ever been considered...and they historically tend to be fairly bad at keeping such important secrets.

---

### Post by kabirgandhiok on 2023-08-03
I hope my predictions, assumptions, speculations, all turn out to be wrong. I'd hate to see their standard LTS release default to all snaps and thus, locked down. Yesterday I chanced upon a YouTuber's review on Ubuntu Core, though still in its alpha stage, apparently he can't even edit his bashrc through the terminal, not even with sudo, and all software must be installed through the GUI not the terninal. Whether this way of interacting with the system remains just another option or becomes the default standard time will tell. 

Video: [https://www.youtube.com/watch?v=GwL0sTz1Kjs](https://www.youtube.com/watch?v=GwL0sTz1Kjs)

---

### Post by ian-weisser on 2023-08-03
> **kabirgandhiok said:**
> Yesterday I chanced upon a YouTuber's review on Ubuntu Core, though still in its alpha stage, apparently he can't even edit his bashrc through the terminal, not even with sudo, and all software must be installed through the GUI not the terninal.

The point of an Immutable Desktop is right there in the label. They cannot edit their .bashrc because that's what "Immutable" means. The use cases for such a desktop have been discussed in public repeatedly, as have the limitations that are obvious to everybody.

Once again, nobody at Canonical or in the Ubuntu community plans to "lock down" anything in the ways you describe.
Nobody at Canonical or in the Ubuntu Community plans to end debian package management.
Nobody at Canonical or in the Ubuntu Community plans to end Ubuntu Server in favor of Ubuntu Core.
Nobody at Canonical or in the Ubuntu Community plans to end Ubuntu Desktop in favor of (hypothetical) Ubuntu Core Desktop.

So go ahead and worry about it as much as you like. And if you discover that I'm wrong, please cite a source.

There are lots of other Linux distros. And non-Linux open source alternatives. As DuckHook succinctly pointed out, you have no obligation to follow a distro that you don't enjoy using.
There is no vendor lock-in here.

---

### Post by ajgreeny on 2023-08-03
I've been running Debian Unstable as a VM for some time now in KVM and with the currently easier installation of non-free packages it becomes a lot easier to use than it used to be.

It is, in my opinion, now very like Ubuntu in many ways and nowhere near as difficult as it was when I first used it probably 16 years ago.

And Debian, of course, does not offer snaps by default though they can be added if someone wants to do so. I suspect most Debian users shy away from snaps totally.  
I believe I could move from my current Xubuntu to Debian Xfce very easily and in some ways hardly notice the difference!

---

### Post by kabirgandhiok on 2023-08-03
> **ian-weisser said:**
> The point of an Immutable Desktop is right there in the label. They cannot edit their .bashrc because that's what "Immutable" means. The use cases for such a desktop have been discussed in public repeatedly, as have the limitations that are obvious to everybody.

Once again, nobody at Canonical or in the Ubuntu community plans to "lock down" anything in the ways you describe.
Nobody at Canonical or in the Ubuntu Community plans to end debian package management.
Nobody at Canonical or in the Ubuntu Community plans to end Ubuntu Server in favor of Ubuntu Core.
Nobody at Canonical or in the Ubuntu Community plans to end Ubuntu Desktop in favor of (hypothetical) Ubuntu Core Desktop.

So go ahead and worry about it as much as you like. And if you discover that I'm wrong, please cite a source.

There are lots of other Linux distros. And non-Linux open source alternatives. As DuckHook succinctly pointed out, you have no obligation to follow a distro that you don't enjoy using.
There is no vendor lock-in here.

Yes, there are tens of thousands of Linux distros out there, and there is no vendor lock-in here or anywhere. I may not have been around as much as other Linux users, nor do I have the experience or technical know how others probably do, but I do remember Ubuntu about 12+ years ago was downright buggy on all my systems and a hot mess that someone like I, with terribly limited knowledge, just couldn't wrap my head around. 

And now, after so many years coming back to where I started from, and seeing how bug free the OS as become evokes a very calming feeling, in that I don't have to switch distributions anymore. What I have always liked works, and it works well. With all the "obvious" customizations I always hoped gnome would have but only Ubuntu had the foresight to implement them. But then again, one can argue I could use KDE or any other environment, but in my opinion there's isn't an environment in Linux that's as polished and non windows-like as gnome out of the box. Sure I could go back to Arch and run an i3 or Awesome window manager and keep tinkering with it all day, but work keeps me busy. Ubuntu gives me what I like and with the right principles and philosophies it's the best bet.

---

### Post by mikodo on 2023-08-03
I'm still waiting on 20.04 to see what 24.04 will bring. Separate Dpkg and Snap OS versions, sounds hopeful to me.  Although, 'the proof will be in the pudding'.

---

### Post by gezzer2 on 2023-08-04
been with Ubuntu since the days of Warty (still have the install CD) then moved to Ubuntu LTS when the LTS first came out and remained with the LTS until 22.04 LTS.
i always believed that the LTS was the best, most stable, most reliable of Ubuntu and could be used in the corporate environment as it was rock solid. 
but i cant understand why they put snaps in the LTS, in the 6 monthly releases yes, as it seems not to be working as it should therefore makes the LTS work more like the 6 monthly release.

Unity wasn't a problem it didn't get in my way. systemd is not a problem, i used it as a DNS caching server, it doesn't get in my way. snaps no matter what i have tried gets in my way.
even after removing snaps it tries to get back into the system so then you have to play around to lock snaps out of the system which then reduces available deb software. snaps just gets in my way which is not what i want.

i had Debian 11 running in boxes but the snap version of boxes wouldn't allow USB pass-through and to get the deb of boxes from the software centre i had to remove snaps. and so on it went.

when Debian 12 was released i thought why not give it a shot and installed it directly on to my computer. the install was easy and the installer even easier and everything just worked.
so i would like to thank Ubuntu for all their hard work because it gave me a grounding in Debian Linux which i'm now using, which i hasten to add, is snap free and doesn't get in my way ...

---

### Post by grahammechanical on 2023-08-05
Ubuntu Core is a snap based OS without a desktop. If we do not like the development of Ubuntu Core with a desktop then do not switch to Fedora SilverBlue. It is an immutable desktop. And it seems far more advanced the Canonical's Ubuntu Core Desktop.

I do not move too far from Ubuntu Forums but I sometimes wonder if the kind of complaints people make about Canonical are made about the developers of other distributions on their forums. I have no desire to find out the answer, but I do wonder if there is any discussion on a Fedora forum about Fedora SilverBlue and how much of it is negative.

From early days Mark Shuttleworth set out to be disruptive. The Ubuntu that we are using now will continue because the promise of Long Term Support + Extended Security Maintenance will be kept. Although I can see Ubuntu Core + Desktop breaking the connection with Debian and Gnome. I can see Ubuntu Core being a subset of Linux code with subsets of Debian and Gnome and any other desktop as is necessary.

Regards

---

### Post by ian-weisser on 2023-08-05
> **grahammechanical said:**
> I sometimes wonder if the kind of complaints people make about Canonical are made about the developers of other distributions on their forums. 

Generally yes.

In some distro communities with lax moderation, some of the complaints are quite floridly horrible and hateful. And then quiet...since who wants to be there?

---

### Post by Tadaen_Sylvermane on 2023-08-05
> This will never happen because the Linux ecosystem is self&#8209;correcting.  Ubuntu is far from the only distro around and were Canonical to make as  foolish a move as the one you posit, users would abandon them in droves.

One would think. But I know here and on a few other forums plenty of people love to still bash systemd but they don't move on. They just sit and complain on the forums all the time but stick with their systemd distro. It's comical. Moving is to much work. It really depends on if your investment in time and resources to a given distro is worth abandoning for a philosophical reason. Not everyone will pick the philosophy side

---

### Post by kabirgandhiok on 2023-08-06
> **Tadaen_Sylvermane said:**
> One would think. But I know here and on a few other forums plenty of people love to still bash systemd but they don't move on. They just sit and complain on the forums all the time but stick with their systemd distro. It's comical. Moving is to much work. It really depends on if your investment in time and resources to a given distro is worth abandoning for a philosophical reason. Not everyone will pick the philosophy side

You make a very valid point. While you are right, over a period of time one does get comfortable with what one earlier disliked, there's always the dealbreaker. In my case it is an immutable system. If ever the immutable Ubuntu became the standard LTS, that's it.

---

### Post by BBQdave on 2023-08-08
> **DuckHook said:**
> This will never happen because the Linux ecosystem is self&#8209;correcting. Ubuntu is far from the only distro around and were Canonical to make as foolish a move as the one you posit, users would abandon them in droves.

...FOSS enforces good behaviour on the whole ecosystem by punishing bad behaviour with easy forks and simple, limitless mobility. Canonical is well aware of this dynamic and would not shoot themselves in the foot.

+1

Debian 12 is amazing, and if you are looking for a snap free .deb distro, Debian is your ticket :)

I'm running Ubuntu to use and understand the distro and use of snaps. So far, function is the same (with my basic workstation set up) as Fedora 38 Gnome and Debian 12 Gnome. I'm not sure what snaps gain you, but their function is the same as a .deb or .rpm.

As mentioned before in the forum, there is a significant size jump in the distro with snaps. Fedora 38 Gnome and personal data around 8GB. Debian 12 Gnome and personal data around 8GB. Ubuntu 22.04 (with snaps) and personal data around 15GB.

This difference in OS size is not a problem for me. I set up a basic GNU/Linux workstation and modern drives are huge. My oldest laptop (with Ubuntu loaded) has a 65GB SSD, I don't even come close to filling the drive - 15GB of 65GB.

I'm guinea pigging along with Ubuntu snaps :)

---

### Post by Tadaen_Sylvermane on 2023-08-08
The thing they give you is self containment. A snap can run on any linux distro without being compiled against it assuming you have the snapd daemon running. All dependencies are included in the snap. Whether or not this is a positive is up for debate. Since you can effectively have countless versions in a set of snaps you lose all benefits of the shared library model. Normally a security update to one library fixes every program that relies on it in a shared library system. AppImage and Flatpak are similar in concept to snaps and require each to be updated separately. This assumes they ever get updated in the first place.

*I may have that a bit off but it's the general idea*

---

### Post by BBQdave on 2023-08-08
> **Tadaen_Sylvermane said:**
> The thing they give you is self containment. A snap can run on any linux distro without being compiled against it assuming you have the snapd daemon running. All dependencies are included in the snap.

Perhaps not the intended benefit, but I did have one application use case where the up to date snap of Darktable allowed me to load a current version of Darktable with the function I needed. This was not available as a .deb (at the time) with Ubuntu 22.04. Though that is the only case where a snap was beneficial in function over the .deb package.

I can see the benefit of loading snaps with the dependencies included, to give you current software and function.

---

### Post by lammert-nijhof on 2023-08-08
> **grahammechanical said:**
> Ubuntu Core is a snap based OS without a desktop. If we do not like the development of Ubuntu Core with a desktop then do not switch to Fedora SilverBlue. It is an immutable desktop. And it seems far more advanced the Canonical's Ubuntu Core Desktop.


Addressing another misunderstanding about snaps. The other immutable system are based on having two OS images on disk, one to run and one for the updates.  After the update you reboot from the newer image. 

In the Ubuntu Core case the desktop and kernel are divided in snaps, e.g networking or printing are snaps. Those snaps will be updated using largely the current mechanism in combination with the facilities of Ubuntu Pro.  E.g the new print-snap will be downloaded and installed, but the new version will be activated, when e.g the print queue is empty. You can already see those phases, if you use "snap refresh". Currently in Ubuntu-Pro the kernel is updated and prepared for usage and as soon as a (re)boot occurs, the new kernel will be activated. For me in the Caribbean a power-fail restart will happen at least once per day, so now I don't have to manually reboot my system for a kernel update, my electricity company takes care of it :)  In future I will never have to update my system manually anymore, it will happen on the fly :)

In other words the new Ubuntu Core Desktop will be more advanced than the other relative simple immutable systems.

---

### Post by mikodo on 2023-08-15
> **Tadaen_Sylvermane said:**
> **All dependencies are included in the snap. Whether or not this is a positive is up for debate. Since you can effectively have countless versions in a set of snaps you lose all benefits of the shared library model. Normally a security update to one library fixes every program that relies on it in a shared library system. AppImage and Flatpak are similar in concept to snaps and require each to be updated separately. This assumes they ever get updated in the first place.**

Herein lie my objections to Snaps et al. So it is with a great many users.   

With Snaps we lose our shared library system, and its' combined security updates. I don't see this changing with AppImage, Flatpak, nor with Snaps.   

Many of us who hold alliance to Ubuntu, do not want to have to leave  because of this, but are feeling the pressure to do so. Many people have felt their 'hands have been forced' already, to leave Ubuntu, and have done so. This is an unfortunate circumstance of, Canonical forcing Snaps on Ubuntu. 

As I stated in this thread earlier, the only solution for this, that I can see for Ubuntu, would be to have both dpkg and snaps OS offered by Canonical. This allowing people to choose which Ubuntu system they wish to use. With out that, many people are feeling *forced to change to another distro like ** DEBIAN ** to be without the likes of Snaps.

---

### Post by DuckHook on 2023-08-15
> **mikodo said:**
> Herein lie my objections to Snaps et al. So it is with a great many users.   

With Snaps we lose our shared library system, and its' combined security updates. I don't see this changing with AppImage, Flatpak, nor with Snaps.   

Many of us who hold alliance to Ubuntu, do not want to have to leave  because of this, but are feeling the pressure to do so. Many people have felt their 'hands have been forced' already, to leave Ubuntu, and have done so. This is an unfortunate circumstance of, Canonical forcing Snaps on Ubuntu. 

As I stated in this thread earlier, the only solution for this, that I can see for Ubuntu, would be to have both dpkg and snaps OS offered by Canonical. This allowing people to choose which Ubuntu system they wish to use. With out that, many people are feeling *forced to change to another distro like ** DEBIAN ** to be without the likes of Snaps.
I agree with your assessment. A lot of old Ubuntu users feel compelled to change to Debian or some other distro because of Snaps. But most of those concerns (not all) are addressable without having to leave Ubuntu.

The only real workaround that could be considered as "required" at this point is to do something about Firefox. And this forum has witnessed many solutions, from installing the standalone version to tweaking apt to install the PPA version.

I am one of the few who are truly "stuck" with Snaps because I use LXD, which is only available as a Snap. But even in my case, Firefox is an old&#8209;fashioned deb package using one of the above workarounds.

I suppose one can say that it is frustrating and ought to be unnecessary to have to look for workarounds, but Linux is acknowledged as a geek OS. Workarounds are also needed in other distros to fill in for their shortcomings. I daresay that many users resort to workarounds for the proprietary OSes too.

I haven't found Snap LXD to be so bad that it prevents me from using it. In fact, it has been well behaved and trouble free.

I'm not in love with Snaps because it has many drawbacks (like the aforementioned bloat and breakage of the shared library philosophy), but it is also unfair to characterize it as just all negatives. The fact is that Snaps allow app authors to issue up&#8209;to&#8209;date apps even for LTS releases nearing EOL and, in the case of ESR, far beyond EOL.

Those who change distros are perfectly within their rights to do so. But citing Snaps as the reason is a bit of an overreaction, IMO.

I do like your suggestion of having both debs and Snaps though.

---

### Post by mikodo on 2023-08-16
@DuckHook:

Well, once there is a "work around" providing Security Updates for snaps, then concerns might be addressed. Currently, this "work around" isn't available. 

 See again:  > **Tadaen_Sylvermane said:**
> All dependencies are included in the snap. Whether or not this is a positive is up for debate. Since you can effectively have countless versions in a set of snaps you lose all benefits of the shared library model. Normally a security update to one library fixes every program that relies on it in a shared library system. AppImage and Flatpak are similar in concept to snaps and require each to be updated separately. This assumes they ever get updated in the first place.

  Addendum: 

 I might as well add this for any lurkers that haven't seen it before. Possibly, it will aid in understanding of the Security Issues with snaps:

  [https://wiki.debian.org/Flatpak#Security_Warning_Note](https://wiki.debian.org/Flatpak#Security_Warning_Note)

---

### Post by kevdog on 2023-08-23
IDK @DuckHook. I greatly respect most of your opinions, but Snaps just suck.  They are slow and take up a lot of room.  I've moved some of servers to Debian and some actually over to Arch.  I really like Ubuntu and actually more invested in this forum community to be honest, however the Snaps seems to become more invasive with every LTS release.  I've been with linux a long time and with Ubuntu since Edge Eft. Hell I loved the Feisty distribution.  My Linux knowledge has greatly increased and I'm now using a ton of installations within hypervisors -- proxmox and xcp-ng.  Through just a lot of experimenting and wasting time over the years, I become pretty proficient with Linux.  Is there a role for immutable distributions -- YES there are without a doubt.  Is there a role for immutable distributions in my workflow -- absolutely not.  Today is Ubuntu offering me a better experience or ease of use features I can't find in other distributions -- and sadly the answer is no -- it is not.  Do I like my Ubuntu server installations -- absolutely!!!! But switching to another distro -- particularly an apt based Distro such as Debian for server use -- really isn't that difficult or complicated.  LXC containers can be simply used in Proxmox without LXD.  Snaps are a problem particularly in light of a lot of the other options from other distributions.  I don't think a lot of users outside the Ubuntu ecosystem use snaps, and other containerization options such as flatpack and docker just have a lot larger user base.

---

### Post by ian-weisser on 2023-08-23
Sigh. The endless stream of snap-hate.
Sigh. The stream of snap-hate that's sometimes proxy for Canonical-hate.

It's all just so...tedious. How can so much anger be so flaccid and dull?
So needlessly melodramatic. (Kneel, hand over my heart, pointing to the future with/without Flatpak!)

---

### Post by exploder on 2023-08-26
@ ian-weisser

I think it is more disappointment than hate. Most rely on the LTS releases these days. Ubuntu 22.04 was a train wreck of bugs on release, snaps, package management, NVIDIA issues, install issues, it was like a beta release. It's clear to anyone that releasing on time was more important than the quality of the release. I ran 22.04 on most of my systems hoping that the bugs would get fixed over time. Instead, I ended up with "phased updates" randomly being installed on some systems breaking things... Kernel upgrades being installed that I never wanted, totally screwing up one of my systems.

If 22.04 was a car, I would tell you that it's going to be the prettiest one in the junkyard! Adding snaps that work poorly does not help the situation either, they clearly are not mature enough for daily use. The point is that the majority of users look to the LTS release to use for 2 to 5 years use and it should be of reasonably good quality, that's clearly not the case with this release. 

Ubuntu is starting to fade in popularity. Articles written about Ubuntu draw far more negative comments than in the past. Even Ubuntu fans are finding the quality of Ubuntu very hard to defend. Many user's have simply moved to Debian. Some developer's have even left Ubuntu. I know DistroWatch stats are not real accurate but you can see Ubuntu is steadily declining where Debian is enjoying quite an upward trend. Given Debian's reputation this might indicate user's choosing quality over new features.

If snaps worked as well as flatpak and none were installed by default all the complaining would likely settle down. Again, looking at Debian's trends, user's are enjoying stability with updated flatpak apps available if they choose to go that route. My personal experience is that this works amazingly well! Ubuntu is presented with a choice already made to use snaps, Debian leaves the choice up to the user. You can see why user's feel snaps are forced on them.

Many have thought Ubuntu development cycles are too short, this very well could account for some of the quality issues. Poor quality, in my mind is the biggest thing hurting the Ubuntu desktop.

---

### Post by ian-weisser on 2023-08-26
Seems like you had a couple bad experiences, and I sure empathize. That seems really frustrating

Counterexample: Back in 2021 I polled my local LUG their daily driver. 100% of them used Ubuntu to get work done. Even the angries who had been historically Ubuntu-averse and quite vocal about it. They use Ubuntu now, they just don't make any noise about it. Last year, one of those formerly-angries mentioned that he "threw Ubuntu onto" his new box for testing, believing that it was most likely to work. It did. He later replaced it with something else for his experimenting and playing.

And I think we've all seen the angries who claim "I'm leaving Ubuntu forever!" ...return a few cycles later, pretending that they hadn't slammed the door behind them.

I've seen Ubuntu-is-declining articles since about 2008. Increasing popularity of Debian is not a threat to Ubuntu. I view it as a measure of Ubuntu's success at contributing upstream to improve Debian. A firehose of testing and integration feedback and bugfixes flow upstream from Ubuntu. Mozilla, Gnome, KDE, Debian, and lots of other projects have lots of activity from Ubuntu developers, including volunteer and third-party-paid and Canonical-paid.

We are currently waist-deep in testing for 23.10. We need folks like you, who have been burned, so you know what fire looks like. We NEED you, please (pretty please!) to try a pre-release spin of 23.10, find some rough edges in your actual workflow, and file some great, usable bugs. Test your hardware on newer kernels using the Live environment, and report those pain points! Now is when the developers are paying the most attention. Now is when your experience can make the biggest difference. Don't wait for 24.04 -- spot the issues and get them fixed now, when it's easier.

---

### Post by #&amp;thj^% on 2023-08-26
> **ian-weisser said:**
> 
We are currently waist-deep in testing for 23.10. We need folks like you, who have been burned, so you know what fire looks like. We NEED you, please (pretty please!) to try a pre-release spin of 23.10, find some rough edges in your actual workflow, and file some great, usable bugs. Test your hardware on newer kernels using the Live environment, and report those pain points! Now is when the developers are paying the most attention. Now is when your experience can make the biggest difference. Don't wait for 24.04 -- spot the issues and get them fixed now, when it's easier.
=d>=d>=d>
But I agree frustration can sound like hate, and there is a difference.
The Tone can take that in any direction.....

---

### Post by ademccade on 2023-08-26
:popcorn:[QUOTE=kabirgandhiok;14152939]

I only used to use apt-get but now working on snap and pip.
:lolflag:

---

### Post by TheFu on 2023-08-26
> **kabirgandhiok said:**
> They have been throwing in the towel for a lot of their projects, maybe they don't this time. (I hope they do). I can't imagine using a Linux system that is locked down and cannot be changed, snaps or no snaps.

For straight end-users who just want to buy a device and have it update itself for the next 10 yrs, snaps are fantastic.  That's where the highly specific "ubuntu core" distro plays.  Think of a TV box that you plug in and manage using a built-in web server only.  You want it to update, but don't want the hassle of doing the maintenance yourself.  Perfect use.  A no-touch system that just works.

And for some server things, I have to admit that having a snap deployment is growing on me. They aren't perfect and there are some real problems when a server self-updates without approval and it breaks.  If it doesn't break, which happens much more often, it is fantastic.  I'm running a snap version of nextcloud inside a dedicated LXC container.  About 4 months ago, I found that a major upgrade in nextcloud effectively broke that system.  I spent a few hours troubleshooting and found that it had performed a major upgrade from v24 --> v25 without asking.  I thought I'd setup the snap to never upgrade from the current major release to the next.  I'm 95% certain I'd done that.  But then it did.  About 2 weeks later, nextcloud started working. I'm thinking it did another upgrade without asking.  One of the flaws is that snaps can't be downgraded across major releases.  If you don't ask about a major upgrade, then the software should make downgrades possible.  

Last week, the nextcloud snap upgraded from v25 to v26 .... again violating my wishes and without asking.  Fortunately, nothing broke with that upgrade ... well, besides that fact that when I've told it to be on v25/stable that is ignored.  That's broken.

I don't see Ubuntu going 100% Ubuntu Core. That would be like shooting yourself in the head and Canonical knows this.

At my LUG, we have desktop users of Ubuntu/PopOS, Mint, MX Linux, Debian and Fedora. Only 2 people actually use Linux at their $real_job on their desktop.

---

### Post by agentl074 on 2023-08-28
I don't ever see this happening... it would go against FOSS principals. Snaps are great, but everything is APT at the base level.

---

### Post by grahammechanical on 2023-08-28
This link has some relevance to this discussion. It is an official explanation.

[https://ubuntu.com/blog/ubuntu-core-an-immutable-linux-desktop](https://ubuntu.com/blog/ubuntu-core-an-immutable-linux-desktop)

About ten years ago Ubuntu published an immutable desktop OS. It was called Ubuntu Desktop Next or Ubuntu personal. I installed it and it worked. Not very usable due to next to no applications. It was not developed beyond Ubuntu 14.10 code. 

> 
We should always be working to identify new technologies that could  improve Ubuntu Desktop in the context of our other values and implement  them in a thoughtful, mission-aligned manner.
[B]
Ubuntu 23.10:[/B] In parallel we are also working on [Ubuntu Core Desktop]("https://ubuntu.com/blog/ubuntu-core-an-immutable-linux-desktop"),  an immutable version of the classic desktop experience, an additional  choice &#55357;&#56898; for Linux Desktop users designed to improve security, quality  and stability.

Ubuntu Desktop - charting the future.

[https://ubuntu.com/blog/ubuntu-desktop-charting-a-course-for-the-future](https://ubuntu.com/blog/ubuntu-desktop-charting-a-course-for-the-future)

Regards

---

