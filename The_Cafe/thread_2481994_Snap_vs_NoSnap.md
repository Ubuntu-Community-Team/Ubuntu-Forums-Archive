---
title: "Snap vs NoSnap"
date: 2022-12-15
forum: The Cafe
---

### Post by VMC on 2022-12-15
This topic has come up several times in various forums.
In case you have no idea what Snap is or isn't, here's one view from Linux Mint guide:
[https://linuxmint-user-guide.readthedocs.io/en/latest/snap.html](https://linuxmint-user-guide.readthedocs.io/en/latest/snap.html)

Ubuntu uses Snap [obviously]. I've read that many have already left Ubuntu just because of Snap.
I've always been curious as to the count of those opposed or not.
Tell us your opinion.

---

### Post by zebra2 on 2022-12-15
The farther into development snap goes the better it works and Ubuntu Software that supports it is better than it has ever been in past releases.  It now support both snap and dev installations. I am currently using 22.10 on my primary system and choose snap for app instead of dev when there is a choice. So far all works well.  Nice to have a built-in firewall that I don't have to deal with. 

I use 22.04 on my secondary system and using snap by default with no complaints there either.

---

### Post by lammert-nijhof on 2022-12-15
I love snaps, because:
- Snaps have been considerably sped up. 
- I still run Ubuntu 16.04 ESM (Extended Security Maintenance) and I'm very happy that the snap allows me to run it with the latest stable versions of Firefox 108.0 and LibreOffice 7.3.4.2 instead of with the outdated deb versions of both.
- In Xubuntu 22.04 LTS I run the following snaps; Firefox; Skype; Whatsie (WhatsApp); Caprine (Facebook Messenger) and I have absolutely no complaints.
- After an update of a snap, I detected a bug and I rolled back that update with "snap revert <snap-name>". Afterwards it worked again and that version with the bug has been blocked.

All fake-experts hate snaps, because they love bashing Canonical.

---

### Post by grahammechanical on 2022-12-15
> All fake-experts hate snaps, because they love bashing Canonical.

I agree with you entirely! I have lost interest in engaging in debates about the merits and demerits of Snap. As Mark Shuttleworth said some years ago: "Haters will hate."

A founding principle of Free and Open Source Software is the user has freedom to chose. There are other Linux distributions. I have heard that millions of people use paid for software. Extraordinary! Unbelievable! :)

Regards

---

### Post by TheFu on 2022-12-15
I use NFS for user HOME directories and only have local accounts in /home, so most users are NOT using /home/.  snapd breaks completely if the user's HOME isn't in /home/, so snaps are useless.  No other distro has limitations that require using /home/, so this is a snap-only problem that never should have been allowed to exist. There is nothing magical about "/home" being used for HOME directories.  For 40+ yrs, at least, the location spelled out in the passwd DB (local or remote NIS, NIS+, LDAP, x.500) has been used to specify where user's HOMEs are located for each individual account.

I also don't like that snaps installs when they want. That's no way to run a production server, if software can be installed and restarted without the admin's expressed permission.  Pushing it off to a specific day is better than nothing, but still doesn't fit the needs of production, enterprise, systems.

Snaps are broken for production use.  I can't believe these things haven't been solved, or do people only host cat photos and other non-critical services?  If you can't call emergency services because a snap package was just installed and broke something, that's unacceptable and a legal liability.  Canonical knows better, but snaps don't show they do.

I get that home users don't care about these little issues, but enterprises do. Basically, Canonical has created a system that cannot be used for anything critical and has been ignoring the issues for years with suggested workarounds just for Ubuntu, without regard for mixed-system environments.

I remember when Linux was about flexibility, not mandates.  I'm happy that many people find value in snaps and can understand why they do, especially if they've never looked at other options.  If it works for you, great.

I'm looking forward to Debian Bullseye Stable release in 2023, which will include a non-snap version of LXD/LXC.  Currently, that is the only reason I would have snapd on a server.  Debian understands the problems with snaps and is going to provide non-snap packages so admins will actually have control over system changes.

We each have lots of distro options. Win-win is the goal.

---

### Post by zebra2 on 2022-12-16
> **grahammechanical said:**
>  I have heard that millions of people use paid for software. Extraordinary! Unbelievable! :)

Regards
 Well yes!  Since the advent of internet based user verification the days of stealing the software is mostly gone. Paying for it is the only option.  When I was in business I had a personal policy of using registered software with my business without regard for what could be stolen from the various internet sources.  Today since I have retired there are still situations where a proprietary option is needed.  Buying a registered version is cheaper than having a resentment in the first place. A resentment is a high price to pay for a $45 software that is legally owned by someone else.

---

### Post by Tadaen_Sylvermane on 2022-12-16
> I get that home users don't care about these little issues, but enterprises do.

For home users it's not even a little issue. They don't care, totally irrelevant to them. No typical home user has any reason to have stuff outside of /home. At that point I'd argue Ubuntu is a bad choice for big business servers. I don't think snaps are mainly targeted at big business. They aren't required to use them, or Ubuntu in the first place. If it's such a big problem then they need to move instead of demanding that Ubuntu, or other companies do what they want.

The only thing that will get Canonical to change direction is if it hits them in the wallet. Thus far it hasn't. That tells me either not many enterprises are using Ubuntu or snaps, or enterprise isn't their main goal so it doesn't matter. The anti snap crowd is a very vocal minority.

I see it as the same as the Windows  / Mac on desktops, Linux on the servers. That is how many places seem to run. Same thing. Ubuntu desktop on the desktops, Debian or RedHat on the backend. Something with legendary stability, and without the problems of snaps forced on it.

---

### Post by TheFu on 2022-12-16
In 22.04, snap packages are installed by default on Ubuntu Server. Some are for critical infrastructure programs, like Linux Container management.

Nobody said that snaps were mandatory, but neither is using MS-Windows to file you taxes.

Ubuntu Core is a snap-only distro for IoT/IoS deployments. I can see where having snaps for non-critical things like a home thermostat or washing machine is actually a good thing.

I get that many people don't have issues with snaps working.  Even on systems with a local user in /home, about 80% of snaps don't work for me.  No idea why not.  When I look at the last updated date for some snaps, they are over 2 yrs old.  So we have the same issue with snap packages that we have with other packages - abandonware.

Hard-coding /home/ with no ability to override that location, or add others, is the real issue.  Flatpaks allow local overrides and flatpaks are specifically designed to be used for desktops only, not servers.

They've started shipping some packages only as snaps (lxd/firefox/chromium), further removing choices.  Firefox has a workaround.  I've gotten chromium to run outside the snap package, still using the snap for installs.  LXD is very different. It is a Canonical funded F/LOSS project that is only distributed as a snap package.  Some Debian devs have taken the source and it is currently in the Debian Testing branch, but had issues which have been reported "upstream" for use outside the snap constrained environment. Will be interesting to see if they fix the issues or not. 

I suspect we'll just be talking passed each other going any further.  Canonical made a choice.  That choice adds restrictions that never existed previously and doesn't have any method to locally override the issues with snap packages. Being flexible is a core Linux value and philosophy, is it not?

The tyranny of the masses/default is a concern here, just like it is in other areas of our lives.   [https://en.wikipedia.org/wiki/Tyranny_of_the_masses](https://en.wikipedia.org/wiki/Tyranny_of_the_masses)

---

### Post by iamjiwjr on 2022-12-16
I'm a home user. I find that, as a whole, flatpaks sill work better for my needs. And the selection is better for my app needs. But snap is getting better and better and generally works fine, as does flatpak. They both have quirks and bugs, but not many.

---

### Post by #&amp;thj^% on 2022-12-16
As a normal personal PC user, I have no use/want for snaps period.
TheFu brings some good points to consider for anything above normal everyday users, 
The Good: (**and FOR THE RECORD I'm not a fake expert nor am I Canonical hater**, quite the opposite in fact. been around for just under 20 years now, and Mark and the Crew have made some Very Nice additions to the World of Linux desktop's and Servers)

1st " Some are for critical infrastructure programs, like Linux Container management."

2nd  "I can see where having snaps for non-critical things like a home thermostat or washing machine is actually a good thing."

Now I'm just stuck trying to find any more good to them.
The Bad: (I can make this one longer but I won't)
Once again I feel exactly the same on this: 
"I remember when Linux was about flexibility, not mandates. I'm happy that many people find value in snaps and can understand why they do, especially if they've never looked at other options. If it works for you, great."
Just so I can keep my wits about me on Debian, I just went total Debian and snap free, that's MY choice and dose not need to be anyone but me here.

Some (and I'm being modest here) of the most talented Linux programmers and coder's prefer to be snap free. (They just remain silent)

---

### Post by TheFu on 2022-12-16
I don't think anyone here is a Canonical hater.  They do 1,000s of things very well.  I like that they take chances and try new things, even when I can't use those new things, provided there's a reasonable fallback position.  Most snaps have a reasonable fallback position and aren't mandatory, but a few are. It is THOSE which concern me.

Lest we forget, there are a few key goals with snap packages.
* Provide a constrained environment for higher risk problems.
* Run on any Linux system, include needed dependencies in the package.
* Automatically patch without user interaction

It is the details where I'm seeing issues.  To end-users, I can see why each of those goals seem reasonable and desirable, but there are some easy exceptions where providing local control would make snaps less of a mandate and provide flexibility for all the situations that Canonical has decided to ignore related to snaps.   After all, not everyone likes to drive a 5-door minivan, because 1-size seldom fits everyone well.

---

### Post by #&amp;thj^% on 2022-12-16
> **TheFu said:**
> I don't think anyone here is a Canonical hater.  They do 1,000s of things very well.  I like that they take chances and try new things, even when I can't use those new things, provided there's a reasonable fallback position.  Most snaps have a reasonable fallback position and aren't mandatory, but a few are. It is THOSE which concern me.


+1
> **TheFu said:**
> 
Lest we forget, there are a few key goals with snap packages.
* Provide a constrained environment for higher risk problems.
* Run on any Linux system, include needed dependencies in the package.
* Automatically patch without user interaction


+1
> **TheFu said:**
> 

It is the details where I'm seeing issues.  To end-users, I can see why each of those goals seem reasonable and desirable, but there are some easy exceptions where providing local control would make snaps less of a mandate and provide flexibility for all the situations that Canonical has decided to ignore related to snaps.   After all, not everyone likes to drive a 5-door minivan, because 1-size seldom fits everyone well.
+1 (I've kind of worn the "Testify" out now ;))

---

### Post by guiverc on 2022-12-16
> **TheFu said:**
> I use NFS for user HOME directories and only have local accounts in /home, so most users are NOT using /home/.  snapd breaks completely if the user's HOME isn't in /home/, so snaps are useless.  No other distro has limitations that require using /home/, so this is a snap-only problem that never should have been allowed to exist.

...

I'm looking forward to Debian Bullseye Stable release in 2023, which will include a non-snap version of LXD/LXC.  Currently, that is the only reason I would have snapd on a server.  Debian understands the problems with snaps and is going to provide non-snap packages so admins will actually have control over system changes.



I'm using Debian *bookworm* (ie. *testing* or 12) currently, which is what I think you meant for release in 2023 (a quick `ssh` query to my servers on *stable* show them running bullseye (11) now.

FYI: I use NFS for most of my file-storage (*so I can use different boxes*), and yes I came up against problems with the introduction of *snap* browses in 2019 (chromium first)  & my usage of directories off / which the* confined snap* packages could no longer access; I resolved that by just adding a second mount in /media/ which is accessible to *confined snap* packages (*two mounts so I could still existing scripts & not need to type the extra 6 characters when it was me as a user, and actually decided I liked that I could use different permissions for the /media mount as I really used it only with browsers or online apps*).  Most snaps can read /mnt & /media as well as inside $HOME.

---

### Post by Frogs Hair on 2022-12-16
I have had no functional or security problems with snaps, but I'm not sure if they are here to stay either. I would like to have consistency when it comes to package management and right now I use .deb , snap, and flatpak just to install the applications I like to use.

---

### Post by VMC on 2022-12-16
> **TheFu said:**
> I don't think anyone here is a Canonical hater.  They do 1,000s of things very well.  I like that they take chances and try new things, even when I can't use those new things, provided there's a reasonable fallback position.  Most snaps have a reasonable fallback position and aren't mandatory, but a few are. It is THOSE which concern me. and that, I think is where the hate comes in. I read negative comments all the time when Canonical tries something new. I didn't like Unity at the time, but it had a big following.

If it weren't from Canonical Linux would still be in the dark ages. I remember Best Buy had free Ubuntu disk available years ago. Ubuntu introduced the world to Linux on a large scale. I know its history, but Ubuntu brought it to mainstream. On a side note, I read all the time people using Distrowatch as the rating of most popular Linux distros. That in fact it just a popularity site. Google among other show real world listings, such as:
[https://www.reddit.com/r/linux/comments/n8kqc2/fixed_linux_distributions_ranked_by_google_trends/](https://www.reddit.com/r/linux/comments/n8kqc2/fixed_linux_distributions_ranked_by_google_trends/)
Even though its 2 years old, you can still get current models, and Ubuntu leads the way. So there can't be THAT much haters in the Linux world of Ubuntu.

---

### Post by mIk3_08 on 2022-12-17
Actually, I like snap. The application packages itself is cool and it will give effortless access to applications of Ubuntu to the new users of the Linux Ubuntu Operating System. It will not give them hard-time to find an applications in the world of Linux if they where new to the Operating System. And it never comes to my mind or planning to remove snap in my system. My snap in my Linux Ubuntu System is up-to-date right now. I never missed to update this snap application when its necessary. Regards and cheers.

---

### Post by mIk3_08 on 2022-12-17
> **VMC said:**
> I read negative comments all the time when Canonical tries something new. I didn't like Unity at the time, but it had a big following.
If it weren't from Canonical Linux would still be in the dark ages. I remember Best Buy had free Ubuntu disk available years ago. Ubuntu introduced the world to Linux on a large scale. I know its history, but Ubuntu brought it to mainstream.  I still remember those days and the sticker is still on the front on my door. Still alive. (see image below.) A free Ubuntu CD and a sticker sent to the users of Linux Ubuntu Operating System. That was the Linux Ubuntu 10.04 Lucid Lynx released. 
[https://i.imgur.com/RRUD2j4.jpg](https://i.imgur.com/RRUD2j4.jpg)

---

### Post by TenPlus1 on 2022-12-17
Any app that's as important as the web browser should be a native .deb package since so many users and services rely on it's usage.  Snaps may have a place but not to replace important stuff.

---

### Post by grahammechanical on 2022-12-19
> Any app that's as important as the web browser should be a native .deb  package since so many users and services rely on it's usage.

I  have the complete opposite opinion. Any application that accesses the  internet should be rigidly confined and limited as to the areas of the  OS that it can access. This is especially true of web browsers and email  clients. Over the years those two applications have been a major source  of malicious code. The Debian Package Management method (deb) and the  Redhat Package Management method (RPM) do not confine the application.

As  regards Firefox being distributed as a snap on Ubuntu 22.04 and later,  that was the decision of the Mozilla Foundation and not the Ubuntu  developers. It gives the Firefox developers control of the updating of  their application. It reduces the number of people running unpatched  versions of Firefox. We do not have to wait until Ubuntu developers  merge the upgraded Firefox into the Ubuntu repositories and then for the  user to update/upgrade the OS.

Regards

---

### Post by TheFu on 2022-12-19
> **grahammechanical said:**
>  
As  regards Firefox being distributed as a snap on Ubuntu 22.04 and later,  that was the decision of the Mozilla Foundation and not the Ubuntu  developers. It gives the Firefox developers control of the updating of  their application. It reduces the number of people running unpatched  versions of Firefox. We do not have to wait until Ubuntu developers  merge the upgraded Firefox into the Ubuntu repositories and then for the  user to update/upgrade the OS.

I agree about certain programs being high risk and needing to run confined.  I disagree about not having local control over exactly when updates happen.  Here's a guy that had to watch the world cup final on his phone because the firefox snap decided to update and in his efforts to stop that (which can't be done), he ended up with a non-bootable system.
[https://www.circusscientist.com/2022/12/18/ubuntu-snap-update-spoiled-the-world-cup/](https://www.circusscientist.com/2022/12/18/ubuntu-snap-update-spoiled-the-world-cup/)
Sure, the non-booting system was mostly self-inflicted, but running the default system should allow end-users to choose to delay snap updates for 2, 4, 8, 12, hours.  

Don't get me started about not having local control over where applications have file system access and which other programs can be integrated.

I can't believe linux programmers would forget that end-users should have power over their programs.  Something is wrong when that happens.  They've lost the Unix philosophy and need remedial education.

---

### Post by yetimon_64 on 2022-12-20
On my new laptop (from Framework) I have the Ubuntu 22.04 (Gnome) release installed for if I run into any hardware compatibility problems. This is the only reason why snapd exists on my new laptop, I would have normally "nuked it" off of my installation except for this one need.

Ubuntu is installed with just the basic requirements for running the Gnome desktop; Firefox is run from the Mozilla "tarball" download version in /opt/yetiman/firefox with integration into the desktop environment via update-alternatives and my Chromium browser is from the saiarcot895 PPA. I have my Ubuntu 22.04 install with the xubuntu-desktop package and lightdm packages added so I can use a less restricted Desktop experience. Gnome is good for setting everything up but I find Xfce to be a more usable environment; basically Xfce is much more stable and does not "freeze" all the time like Gnome does. I only keep snapd for use with the Gnome desktop. I prefer ".deb" packages over snaps.

I have voted for "No" to snaps, even though I am currently running an install with snapd in. My usual preference is to uninstall it completely. Making snaps the default has created much more work for me when installing Ubuntu though it hasn't turned me off using Ubuntu, yet. If it ever were made mandatory (impossible to uninstall) I'd probably revisit using Debian or start looking for a new distro; I hope that never happens.

---

### Post by VMC on 2022-12-20
Not sure how hardware compatibility would have anything to do with Snap. "/lib/firmware" is where I look for hardware issues.

---

### Post by yetimon_64 on 2022-12-20
> **VMC said:**
> Not sure how hardware compatibility would have anything to do with Snap. "/lib/firmware" is where I look for hardware issues.

Just for dealing with hardware issues it helps if you use a recommended installation with the framework laptop. Both Fedora (36 or 37) and Ubuntu releases 22.04 and 22.10 are recommended if hardware issues are needed to be checked out.

Snap likely isn't needed as much as a close to default install of Ubuntu 22.04 or 22.10 is suggested (hence snap is included by default).

---

### Post by Perfect Storm on 2022-12-22
I voted, no. I use flatpak instead for the few pieces I need (3 to be exactly).
In my opinion snap nor flat should be default. New users can't understand the why snap/flat are eating up their space on the HDD.

---

### Post by zebra2 on 2022-12-23
> **Perfect Storm said:**
>  New users can't understand the why snap/flat are eating up their space on the HDD.

+1 I agree with this.  New users should't have to be concerned with how much hd space is used by snaps.  They need to get back to the business of why their Windows partition won't boot any more.

---

### Post by TheFu on 2022-12-23
> **zebra2 said:**
> +1 I agree with this.  New users should't have to be concerned with how much hd space is used by snaps.  They need to get back to the business of why their Windows partition won't boot any more.

I have a chromebook running Linux with a 16GB SSD.  Ubuntu has been long deleted due to bloat. It ran Ubuntu with a stripped down install and just openbox for a few years.  20.04 doesn't fit in 16GB.  That's when snaps started being pushed by Canonical.  Not a coincidence.  I find it funny that IoT devices running Ubuntu Core can only support snap packages. An IoT device shouldn't need more than 4GB of storage ... really 1GB, but we'll give some bloat for being "new".

---

### Post by zebra2 on 2022-12-23
@TheFu
yep!  My first Ubuntu ISO download was on a CD.  The latest ISO for 22.10 is 5Gig.  Glad I have a terebyte HD. But I feel your pain. I actually started my linux journey with Puppy Linux running on a 512Meg Thumb Drive.  However now that we are where we are Snap isn't exactly the biggest space eater.  If secure boot is being used it takes circa 256M of ESP partition just to get Ubuntu installed. Hold it! I'm using legacy boot and I still needed the ESP to boot.  What's that all about.

I value your feed back but I think we are just kicking the can down the street.

Edit: If you are planning to run 23.10 you may want to get your Blue Ray on order.

---

### Post by joanne-exists on 2023-01-11
snap comes in handy on raspberry pi

---

### Post by agentl074 on 2023-01-24
Snapcraft is also gaining a lot of ground -- and most of the bugs have been worked out. The biggest thing, still, is the fresh install and Snapstore update. This can be fixed via [COLOR=#232629][FONT=ui-monospace]sudo killall snap-store && sudo snap refresh snap-store.[/FONT][/COLOR]

---

### Post by donald187 on 2023-01-29
I've decided I like snaps for applications that require version bumping to receive security updates such as Firefox, Thunderbird, and Chromium.  I was on Debian for a few years but was keeping an eye on Thunderbird in Ubuntu as well.  Eventually these version-bump applications need to be upgraded.  For example Thunderbird (e.g. from 91 to 102) or the same in the case of Firefox ESR on Debian.  This can take months at times meanwhile the cve's pile up. This included a high cve in Thunderbird in Ubuntu in the transition from 68 to 78 if I recall correctly.   Also the Chromium versions on Debian for years were generally way behind.    My understanding is that there was just one maintainer who just didn't have the time that Chromium required.  (They have a different maintainer now who is keeping it up to date.)  Snap (or Flatpak) seems to take care of these problems.

---

### Post by agentl074 on 2023-01-30
> **zebra2 said:**
> ...They need to get back to the business of why their Windows partition won't boot any more.

Personally, I can't wait to get completely rid of Windows lol, but I do understand why some would need it for certain apps. The last Windows machine we have is about to turn Ubuntu.

---

### Post by zebra2 on 2023-02-09
> **agentl074 said:**
> Personally, I can't wait to get completely rid of Windows lol, but I do understand why some would need it for certain apps. The last Windows machine we have is about to turn Ubuntu.

Couldn't agree more however!  Back in December I bought my wife a new Windows 11 15" Laptop with the intention of scraping Windows and installing Ubuntu.  With some testing I found that in no way was Ubuntu going on our new system.  I deleted everything MS that I could find on the Windows 11, disconnected and deleted the Cloud and Cloud Backup then installed all of the same Foss software on the Windows 11 system that my wife used on the Ubuntu computer.  My wife is using it every day and isn't having any problems.  I'm not sure she actually knows the difference.  I have to admit it came in handy with my tax filing. Instead of fooling around with a dual boot it is kind of nice to have a Windows machine around. Plus, it only cost $129.00 from the big box store. I actually prefer my Ubuntu 23.04 Laptop but withholding complaining about the Windows 11 machine. If I'm blessed, I say, be blessed.

---

### Post by zebra2 on 2023-02-10
I just download the current 23.10 Ubuntu ISO.  It has increased from 5.4G to 5.9G. Looks like the mama snap has spawned off another .5G of baby snaps. Pretty soon it will be fatter than fatpak.

---

### Post by deadflowr on 2023-02-10
> **zebra2 said:**
> I just download the current 23.10 Ubuntu ISO.  It has increased from 5.4G to 5.9G. Looks like the mama snap has spawned off another .5G of baby snaps. Pretty soon it will be fatter than fatpak.

You're coming to us from the future?

---

### Post by DuckHook on 2023-02-10
Users do come on this site in such a state of frustration that they post with unnecessary vehemence. Without intending to be Ubuntu "haters", they come across as such. I get that.

But we should also guard against cutting off healthy debate by reaching for labels such as "hater" with undue haste.

I'm ambivalent about snaps for what I think are good reasons, and I can hardly be accused of being an Ubuntu "hater". As a LXD addict, I am forced to use snapd. I do understand some of its advantages. But it has also been a source of maddening stress and frustration for me, none of which were necessary. It is not a well conceived or well executed subsystem.

Issues that I've run into with snapd:

[LIST]
[*]Crashed Mrs DH's computer because /var was in its own 8 GB partition. Before snaps, 8 GB for /var was more than enough. But the bloat and resource&#8209;hogging of snaps will fill up 8 GB with ridiculous speed. In Mrs DH's case, there was only one minor snap app installed. But snap will drag in a ton of junk. Most of it isn't even needed by the app—but it's dragged in "just in case". This is stupid. This is offensive. It offends one of the basic tenets of FOSS: do only what is needed and keep it stupidly simple. BTW, the solution was not trivial: expand /var partition or remap /var elsewhere. I know what to look for and how to solve such a problem. The average user would be lost and just conclude that Ubuntu is garbage.
[*]Made FF unusable. Couldn't print. Couldn't attach files from a network share. Took over half a minute to load—I thought the app was frozen. I'm told that things have gotten better since, but have they? I didn't wait around to find out: just jumped on a workaround using a PPA (thank goodness those still work, though they are a mixed blessing). Fool me once, shame on you; fool me twice…
[*]Made other apps unusable too. The Telegram and Signal snaps ran into issues so serious that, once again, I had to resort to PPAs and outside repos. Else may as well not install those apps at all. The resource piggy nature of snaps also drove me nuts there too.
[*]This just posted in another thread, so it's happening all over again with TBird: [https://ubuntuforums.org/showthread.php?t=2483755](https://ubuntuforums.org/showthread.php?t=2483755) Yet another potential hit on Ubuntu's reputation.
[*]It's been suggested that snaps are a good thing because they don't leave users any choice but to sandbox and to update, that is to say, it enforces security. While on the surface this sounds all well and good, if it is imposed on us without possibility of customization, then it becomes a bad thing. It is time that we stopped thinking of Ubuntu as a "popular" or "Average Joe" system. It isn't. It is a power user's OS. All Linux distros are. If it ceases to be flexible, or versatile, or customizable, then it ceases to be powerful. And if it surrenders its power, it will die on the open marketplace competing against the proprietary silos. That is a no&#8209;win no&#8209;brainer.
[/LIST]
It's easy to dismiss snap critics as haters, perhaps too easy. If you love snaps and they're working well for you, then good on you. But don't automatically dismiss thoughtful critics as haters. We love Ubuntu as much as you, and we are critics only because we don't want to see Ubuntu screw up a good thing.

---

### Post by zebra2 on 2023-02-10
> **deadflowr said:**
> You're coming to us from the future?

Yep, sorry about that.  I stay on the cutting edge and reinstall several times a month just to keep it clean.  The download I was referencing is actually the "pending" ISO. So it is tomorrow's version. Hence you are correct. It is from the future. 

Indecently, I reformat my /root which includes /var when I reinstall and i am never missing data when I put my apps back. The bloat in /var comes from caching and  apt/cache.  My var snap folder is next to nothing and I run all the snaps available for my program setup.

---

### Post by deadflowr on 2023-02-10
> **zebra2 said:**
> Yep, sorry about that.  I stay on the cutting edge and reinstall several times a month just to keep it clean.  The download I was referencing is actually the "pending" ISO. So it is tomorrow's version. Hence you are correct. It is from the future. 

No.
You posted a release version that won't even exist until after April.

---

### Post by zebra2 on 2023-02-10
> **deadflowr said:**
> No.
You posted a release version that won't even exist until after April.

Yep, I will go along with that also. I hope the April release is as good as it is right now.

---

### Post by donald187 on 2023-02-10
Snap Thunderbird prints just fine from here.

---

### Post by monkeybrain20122 on 2023-02-10
For those who are frustrated by Firefox snap, just unsinatll it .  

Download the tar file from [Mozilla]("https://www.mozilla.org/en-US/firefox/new/"), put it somewhere in your $HOME (some online tutorials tell you to put it in /opt. that is stupid because you then have to sudo and automatic update won't work, I don't mind it updating automatically cos if you don't trust Mozilla you may as well disable access to internet) it is a precompiled binary, extract it. Then just click firefox, that's it. When first launch it will ask you whether to make firefox the default browser, click yes and it will create a .desktop file in ~/.local/share/applications so you can use it as a launcher. It will stay if you make other browser the default later. I changed the folder name from firefoxxxx to just firefox, where xxxx is the version number, since it will get updated eventually.

Update is seamless, it is done automatically when you restart firefox (if there is an update), or you can check for update manually by going to Help > About Firefox

I don't see any reason to use a crippled version packaged by canonical, and honestly I think this gives Ubuntu a bad reputation when new users are given the impression that even Firefox doesn't work on Linux.

DuckHook has helpfully pointed out a [ppa]("https://launchpad.net/~mozillateam/+archive/ubuntu/ppa") maintained by the mozilla team. But to use it you have to change the priorities in apt or if you do sudo apt install firefox or when you update it will install the snap version, this will happen even if you purge snapd, it will just reinstall the whole snap infrastructure when you install firefox. Personally I see no need for ppa either, unless you are on a multi-user system so you want to install it globally. I just get it from Mozilla as described above.

---

### Post by DuckHook on 2023-02-10
I didn't answer the poll because there is no option that reads: Ambivalent on snap because there is both good and bad.

---

### Post by ajgreeny on 2023-02-11
> **monkeybrain20122 said:**
> For those who are frustrated by Firefox snap, just unsinatll it .  

Download the tar file from [Mozilla]("https://www.mozilla.org/en-US/firefox/new/"), put it somewhere in your $HOME (some online tutorials tell you to put it in /opt. that is stupid because you then have to sudo and automatic update won't work, I don't mind it updating automatically cos if you don't trust Mozilla you may as well disable access to internet) it is a precompiled binary, extract it. Then just click firefox, that's it. When first launch it will ask you whether to make firefox the default browser, click yes and it will create a .desktop file in ~/.local/share/applications so you can use it as a launcher. It will stay if you make other browser the default later. I changed the folder name from firefoxxxx to just firefox, where xxxx is the version number, since it will get updated eventually.

Update is seamless, it is done automatically when you restart firefox (if there is an update), or you can check for update manually by going to Help > About Firefox

I don't see any reason to use a crippled version packaged by canonical, and honestly I think this gives Ubuntu a bad reputation when new users are given the impression that even Firefox doesn't work on Linux.

DuckHook has helpfully pointed out a [ppa]("https://launchpad.net/~mozillateam/+archive/ubuntu/ppa") maintained by the mozilla team. But to use it you have to change the priorities in apt or if you do sudo apt install firefox or when you update it will install the snap version, this will happen even if you purge snapd, it will just reinstall the whole snap infrastructure when you install firefox. Personally I see no need for ppa either, unless you are on a multi-user system so you want to install it globally. I just get it from Mozilla as described above.
This is how I've been using Firefox since I installed 22.04 back in April this year.
My first start of firefox snap version took so long I thought it was crashed so tried again and ended with two windows open eventually which froze everything on the machine, an old Intel dual core using spinning rust hard disk.

The direct downloaded archive works faultlessly for me; I can not see what the differences are between it and the standard .deb version that we had before the snap.

---

### Post by VMC on 2023-02-11
**monkeybrain20122, **That's the installation I use, but I read somewhere that Mozilla created the Snap version.

---

### Post by ajgreeny on 2023-02-11
> **VMC said:**
> **monkeybrain20122, **That's the installation I use, but I read somewhere that Mozilla created the Snap version.
I am fairly certain that is correct but I still find snaps too much of a palaver with some restrictions that just annoy me, so as long as the .tar.gz archive is available I shall continue to use it.

I don't know how much space the snap uses but the .tar.gz only uses 233MB when extracted which I suspect is a lot smaller than the snap.

---

### Post by maglin2 on 2023-02-11
```
[FONT=monospace][COLOR=#000000]$ snap info firefox [/COLOR]
name:      firefox 
summary:   Mozilla Firefox web browser 
publisher: Mozilla[COLOR=#18b218]&#10003;[/COLOR]
store-url: [https://snapcraft.io/firefox](https://snapcraft.io/firefox) 
contact:   [https://support.mozilla.org/kb/file-bug-report-or-feature-request-mozilla](https://support.mozilla.org/kb/file-bug-report-or-feature-request-mozilla) 
license:   unset 
description: | 
  Firefox is a powerful, extensible web browser with support for modern web application 
  technologies. 
commands: 
  - firefox 
  - firefox.geckodriver 
tracking:     latest/stable 
refresh-date: 11 days ago, at 15:02 GMT 
channels: 
  latest/stable:    109.0.1-1    2023-01-31 (2311) 250MB - 
  latest/candidate: 110.0-1      2023-02-08 (2342) 251MB - 
  latest/beta:      110.0b9-1    2023-02-03 (2330) 189MB - 
  latest/edge:      111.0a1      2023-02-11 (2349) 197MB - 
  esr/stable:       102.7.0esr-1 2023-01-17 (2270) 183MB - 
  esr/candidate:    102.8.0esr-1 2023-02-06 (2336) 186MB - 
  esr/beta:         &#8593;                                     
  esr/edge:         &#8593;                                     
installed:          109.0.1-1               (2311) 250MB -
[/FONT]
```

Snap store says 250MB is the installed size.
I'm not sure quite what this means, since /home/user/snap/firefox folder is 229MiB, but /snap/firefox folder is 1.2 GiB (that contains 2 versions, each of which is about 620MB)

---

### Post by deadflowr on 2023-02-11
> Snap store says 250MB is the installed size.
I'm not sure quite what this means, since /home/user/snap/firefox folder is 229MiB, but /snap/firefox folder is 1.2 GiB (that contains 2 versions, each of which is about 620MB)
The 250MB size is inside /var/lib/snapd/snaps.
The /snap directory is the mount location but the actual snap packages on disk are in the /var location.

Home is what you have personally and not related to the snap packages, per se.
It contains all the configurations for the user. And I just noticed it also contains the cache data for firefox.
So that directory will vary depending on user.

---

### Post by maglin2 on 2023-02-11
> **deadflowr said:**
> The 250MB size is inside /var/lib/snapd/snaps.
The /snap directory is the mount location but the actual snap packages on disk are in the /var location.

Home is what you have personally and not related to the snap packages, per se.
It contains all the configurations for the user. And I just noticed it also contains the cache data for firefox.
So that directory will vary depending on user.

Thank you.
So it is 239.1 MiB, 250.7MB for the latest/stable version.
(I should know this stuff myself - I've been using Ubuntu for a decade)

---

### Post by DuckHook on 2023-02-13
> **maglin2 said:**
> Snap store says 250MB is the installed size.
I'm not sure quite what this means, since /home/user/snap/firefox folder is 229MiB, but /snap/firefox folder is 1.2 GiB (that contains 2 versions, each of which is about 620MB)

> **maglin2 said:**
> Thank you.
So it is 239.1 MiB, 250.7MB for the latest/stable version.
The individual snap app is not that bad. It's all the additional junk that is hauled in "just in case".

The reason that Mrs DH's computer ran out of space was not due to the app (&#8776;250 MB) but the ridiculous associated infrastructure. Among other things, it installed something called kde-core (or something like that, I now only vaguely recall) despite the fact that Mrs DH does not have kde. The -core suffix sounded terribly important, but in the course of my frustrating attempt to fix things, I nuked this 1.2 GB blob and the app ran fine without it. I can only surmise that it was an extraneous piece of bloat that this particular snap dev included "just in case".

First of all, this is lazy design. It promotes sloth and neglect. One of the major goals of Linux package design is small footprint and efficiency. When an app is installed, a package manager checks to see what libraries are needed, which libraries already exist and which additional ones need to be downloaded. The minimum is then added: enough to enable the app to run and no more. This philosophy is what has made Linux so lean and mean. It has prevented the bloat that infests proprietary OSes.

Even a snap app, designed to run in a self&#8209;contained manner and therefore not dependent on the distro's package system, ought to check for the DE. What is the point of installing kde hooks into an environment devoid of kde? It's stuff like this that gives snaps such a bad rep.

The second problem is security. Snaps are marketed as having the benefit of sandboxing. Notwithstanding that this is not a good thing when it is imposed without choice, even this limited purported benefit is undermined when useless junk is added. The more junk, the more attack surface. This is Security 101.

The third problem is more philosophical: Linux is a power user's OS. Its core followers are those who can't stand the limitations imposed on them by the proprietary vendors. We want the freedom to change things in ways that may not even be wise or safe, but are nonetheless permitted to us. Snapcraft is the antithesis of this. It is a straightjacket denying access to such freedoms. It is techno&#8209;nannyism. I'm not sure that's okay even for general users; it is definitely not okay for power users.

---

### Post by #&amp;thj^% on 2023-02-13
> **DuckHook said:**
> 
The second problem is security. Snaps are marketed as having the benefit of sandboxing. Notwithstanding that this is not a good thing when it is imposed without choice, even this limited purported benefit is undermined when useless junk is added. The more junk, the more attack surface. This is Security 101.

The third problem is more philosophical: Linux is a power user's OS. Its core followers are those who can't stand the limitations imposed on them by the proprietary vendors. We want the freedom to change things in ways that may not even be wise or safe, but are nonetheless permitted to us. Snapcraft is the antithesis of this. It is a straightjacket denying access to such freedoms. It is techno&#8209;nannyism. I'm not sure that's okay even for general users; it is definitely not okay for power users.

Once again well said...;)

---

### Post by donald187 on 2023-02-13
> **DuckHook said:**
> The individual snap app is not that bad. It's all the additional junk that is hauled in "just in case".

The reason that Mrs DH's computer ran out of space was not due to the app (&#8776;250 MB) but the ridiculous associated infrastructure. Among other things, it installed something called kde-core (or something like that, I now only vaguely recall) despite the fact that Mrs DH does not have kde. The -core suffix sounded terribly important, but in the course of my frustrating attempt to fix things, I nuked this 1.2 GB blob and the app ran fine without it. I can only surmise that it was an extraneous piece of bloat that this particular snap dev included "just in case".

First of all, this is lazy design. It promotes sloth and neglect. One of the major goals of Linux package design is small footprint and efficiency. When an app is installed, a package manager checks to see what libraries are needed, which libraries already exist and which additional ones need to be downloaded. The minimum is then added: enough to enable the app to run and no more. This philosophy is what has made Linux so lean and mean. It has prevented the bloat that infests proprietary OSes.

Even a snap app, designed to run in a self&#8209;contained manner and therefore not dependent on the distro's package system, ought to check for the DE. What is the point of installing kde hooks into an environment devoid of kde? It's stuff like this that gives snaps such a bad rep.

The second problem is security. Snaps are marketed as having the benefit of sandboxing. Notwithstanding that this is not a good thing when it is imposed without choice, even this limited purported benefit is undermined when useless junk is added. The more junk, the more attack surface. This is Security 101.

The third problem is more philosophical: Linux is a power user's OS. Its core followers are those who can't stand the limitations imposed on them by the proprietary vendors. We want the freedom to change things in ways that may not even be wise or safe, but are nonetheless permitted to us. Snapcraft is the antithesis of this. It is a straightjacket denying access to such freedoms. It is techno&#8209;nannyism. I'm not sure that's okay even for general users; it is definitely not okay for power users.
Just curious if you think Flatpak is any better.  The Debian forum members were dead set against snap.  Flatpak was acceptable *in general*, but only if what one needed was not in the repositories.

---

### Post by DuckHook on 2023-02-13
> **donald187 said:**
> Just curious if you think Flatpak is any better.
I don't use flatpaks, so I'm honestly not qualified to render any judgment in the matter. I imagine that some of my concerns about snaps would also apply to flatpaks: they could promote lazy design and larger attack surface. I gather from other forum threads that at least they allow more control by the user, so my last concern might not be as applicable.
> The Debian forum members were dead set against snap.  Flatpak was acceptable *in general*, but only if what one needed was not in the repositories.
There is one further concern that your own observation raises, and it's this: could these various self-contained package managers bring about the demise of the traditional repos? We're already seeing this with LXD, FF and Chromium. How long will it be before every app is migrated to snap (or flatpak or AppImage)? I don't need to ask what will happen to the traditional repo when that happens: they will be dropped. Obscene bloat will become the norm and the old principle of lean and mean will become obsolete.

---

### Post by donald187 on 2023-02-14
> **DuckHook said:**
> I don't use flatpaks, so I'm honestly not qualified to render any judgment in the matter. I imagine that some of my concerns about snaps would also apply to flatpaks: they could promote lazy design and larger attack surface. I gather from other forum threads that at least they allow more control by the user, so my last concern might not be as applicable.

There is one further concern that your own observation raises, and it's this: could these various self-contained package managers bring about the demise of the traditional repos? We're already seeing this with LXD, FF and Chromium. How long will it be before every app is migrated to snap (or flatpak or AppImage)? I don't need to ask what will happen to the traditional repo when that happens: they will be dropped. Obscene bloat will become the norm and the old principle of lean and mean will become obsolete.
Ok thanks.  :)

Also it would probably be more correct if I had said that the Debian forum members in general found Flatpak to be *tolerable* rather than acceptable.

---

### Post by BBQdave on 2023-02-14
> **DuckHook said:**
> There is one further concern that your own observation raises, and it's this: could these various self-contained package managers bring about the demise of the traditional repos? We're already seeing this with LXD, FF and Chromium. How long will it be before every app is migrated to snap (or flatpak or AppImage)? I don't need to ask what will happen to the traditional repo when that happens: they will be dropped. Obscene bloat will become the norm and the old principle of lean and mean will become obsolete.

I believe that is the objective, sort of. You have a stable distro with old applications that are *extended support*. Debian 11 has FireFox-ExtendedSupport. With snap or flatpak you can have current release applications. Current FireFox.

May or may not matter if FireFox is a version or two older, as long as it is secure. But it's a big difference with Darktable.deb and Darktable-snap.

Perhaps looking at snap through rose colored glasses, but I see it as a good attempt to have current release applications on stable Debian platforms.

I'm curious about bloat concerns, and I may be missing it. But my current U22.04LTS (minimal install with browser and utilities) has FF, Google Chrome, Gimp, Darktable, and Scribus. I use Google docs, sheets and other applications through Chrome. My install is under 15GB. My Google Fi Pixel phone's system is 15GB. So I perceive my Ubuntu install as normal and not bloated.

Currently, 15GB out 65GB of a SSD is used for my laptop's function. Seems reasonable :)

---

### Post by ajgreeny on 2023-02-14
> **DuckHook said:**
> <snip>
There is one further concern that your own observation raises, and it's this: could these various self-contained package managers bring about the demise of the traditional repos? We're already seeing this with LXD, FF and Chromium. How long will it be before every app is migrated to snap (or flatpak or AppImage)? I don't need to ask what will happen to the traditional repo when that happens: they will be dropped. Obscene bloat will become the norm and the old principle of lean and mean will become obsolete.
What worries me even more about this is the apparent total lack of control we users will have over our OSs should it happen.

One of the main reasons I moved from Windows XP to Ubuntu 5.04, 17 years ago, was to get away from those restrictions that did occasionally really annoy me, and don't forget that was In Windows XP which in comparison with the current Windows versions was much easier to play around with and change configurations etc etc.

I haven't seen or had to use Windows 11 but do occasionally have to use Windows 10 as a local volunteer worker and it drives me nearly insane, perhaps as a result of unfamiliarity to me, and takes me so much longer to do everything such as find any files or applications that I need to use.

---

### Post by #&amp;thj^% on 2023-02-14
> **donald187 said:**
> Ok thanks.  :)

Also it would probably be more correct if I had said that the Debian forum members in general found Flatpak to be *tolerable* rather than acceptable.

I find them very tolerable, and as far as space goes:
```
flatpak list --all
Name           Application ID                 Version Branch      Installation
Tor Browser L&#8230; &#8230;micahflee.torbrowser-launcher 0.3.6   stable      system
Mesa           &#8230;eedesktop.Platform.GL.default 22.3.4  22.08       system
Mesa (Extra)   &#8230;eedesktop.Platform.GL.default 22.3.4  22.08-extra system
nvidia-525-89&#8230; &#8230;.Platform.GL.nvidia-525-89-02         1.4         system
openh264       &#8230;freedesktop.Platform.openh264 2.1.0   2.2.0       system
KDE Applicati&#8230; org.kde.Platform                       5.15-22.08  system
kde platform &#8230; org.kde.Platform.Locale                5.15-22.08  system

```
Total Space taken:
```

du -h /var/lib/flatpak
0	/var/lib/flatpak/repo/tmp/cache/summaries
0	/var/lib/flatpak/repo/tmp/cache
0	/var/lib/flatpak/repo/tmp
0	/var/lib/flatpak/repo/extensions
0	/var/lib/flatpak/repo/state
To save space I've just shown the space used on my system.
**2.4G	/var/lib/flatpak**
```
Or for a more user readable view:
```
flatpak --columns=name,size list
Name                               Installed size
Tor Browser Launcher                31.9*MB
Mesa                               385.1*MB
Mesa (Extra)                       385.1*MB
nvidia-525-89-02                     1.9*MB
openh264                           790.0*kB
KDE Application Platform           865.7*MB


```

---

### Post by Shibblet on 2023-02-14
> **VMC said:**
> Ubuntu uses Snap [obviously]. I've read that many have already left Ubuntu just because of Snap.
I've always been curious as to the count of those opposed or not.
Tell us your opinion.

I'm not opposed to Snaps.  I'm not going to leave (K)Ubuntu because of them.

However, I would ask that they be optional.

Some packages that we have grown to use over the years (i.e. Chromium) are forced to be Snap Packages.  This wouldn't really be a problem if the Snaps were flawless.  However, they have some issues that still need to be fixed.

I understand that progress is a rough-road, and mistakes and problems along the way are natural.  But, until it's "ready for prime-time," don't force the issue.

"And that's all I got to say about that."  - Forrest Gump

---

### Post by donald187 on 2023-02-14
> **1fallen said:**
> I find them very tolerable, and as far as space goes:
```
flatpak list --all
Name           Application ID                 Version Branch      Installation
Tor Browser L… …micahflee.torbrowser-launcher 0.3.6   stable      system
Mesa           …eedesktop.Platform.GL.default 22.3.4  22.08       system
Mesa (Extra)   …eedesktop.Platform.GL.default 22.3.4  22.08-extra system
nvidia-525-89… ….Platform.GL.nvidia-525-89-02         1.4         system
openh264       …freedesktop.Platform.openh264 2.1.0   2.2.0       system
KDE Applicati… org.kde.Platform                       5.15-22.08  system
kde platform … org.kde.Platform.Locale                5.15-22.08  system

```
Total Space taken:
```

du -h /var/lib/flatpak
0    /var/lib/flatpak/repo/tmp/cache/summaries
0    /var/lib/flatpak/repo/tmp/cache
0    /var/lib/flatpak/repo/tmp
0    /var/lib/flatpak/repo/extensions
0    /var/lib/flatpak/repo/state
To save space I've just shown the space used on my system.
**2.4G    /var/lib/flatpak**
```
Or for a more user readable view:
```
flatpak --columns=name,size list
Name                               Installed size
Tor Browser Launcher                31.9*MB
Mesa                               385.1*MB
Mesa (Extra)                       385.1*MB
nvidia-525-89-02                     1.9*MB
openh264                           790.0*kB
KDE Application Platform           865.7*MB


```
I assume you like Flatpak over Snap?  Why is that?

---

### Post by #&amp;thj^% on 2023-02-14
> **donald187 said:**
> I assume you like Flatpak over Snap?  Why is that?


Just a personal prefrence ATM and that may change in the future, and that dose not mean you have to agree.
Some of my findings include, 
```
Features	Snap	Flatpak	                                                AppImage
Created By	    Canonical	RedHat, Endless Computers, Collabora	Peter Simon
Sandboxing Support	Yes	Yes	Yes
Sandboxing Mandatory	No	Yes	No
Running Without Root Access	After installation	After installation	Yes
Native Theme Support	Yes	Yes	Yes
Support for Bundled Libraries	Yes	Yes	Yes
Full App Portability		Yes	Yes
Online App Store	Yes	Yes	Yes
Multiple Parallel Installations Support	Yes (one per channel)	Yes (unlimited number)	Yes (unlimited number)
Automatic Updates	Yes	Yes	Yes (via AppImageUpdate)
App Size	Varies, usually greater than AppImage	Varies, usually greater than AppImage	Lowest app size
Applications Available	The most	The least	Medium amount
Desktop GUI Apps	Yes	Yes	Yes
Package System Services	Yes	No	No


```
Flatpak

Flatpak, previously known as xdg-app, is another distribution-independent package format developed in 2015 by Red Hat, Endless Computers, and Collabora. Its primary goal is to run apps in a secure virtual sandbox that doesn't require root privileges, thus eliminating security threats. The sandbox contains everything needed to run the software.

Flatpak was first developed for FreeDesktop, KDE, and GNOME. Later it expanded its support to Arch Linux, Debian, Fedora, Mageia, Solus, and Ubuntu. Flatpak is based on the C programming language.(This is imporant to me, I test all the above in one form or another)

The packages are available for download on the Flathub app store or via the CLI. Initially, it only supported open-source apps, but recently it has added support for proprietary software.

I hope that was fair UN-biased view, although I'm bound to have pissed someone off. :P

---

### Post by donald187 on 2023-02-14
Thanks. :)  I once read this big news.ycombinator.com debate about Flatpak.  Lots of opinions on both sides.  Very interesting.  Just pros and cons of Flatpak.  Not Snap.

---

### Post by #&amp;thj^% on 2023-02-14
> **donald187 said:**
> Thanks. :)  I once read this big news.ycombinator.com debate about Flatpak.  Lots of opinions on both sides.  Very interesting.  Just pros and cons of Flatpak.  Not Snap.
One way I overcome that is to try them and decide for my use and needs. :D

---

### Post by donald187 on 2023-02-14
> **1fallen said:**
> One way I overcome that is to try them and decide for my use and needs. :D

I generally go with the tyranny of the default.  I go with the default unless there's a need to do something else.  I just find this topic interesting.

---

### Post by DuckHook on 2023-02-14
> **BBQdave said:**
> …I see it as a good attempt to have current release applications on stable Debian platforms.
It's important that I reiterate: I'm neither a snap proponent nor opponent. I mean, I *use* it for crying out loud, so I can hardly hate it.

We are all familiar with its purported benefits: those that you have stated. Plus one that you haven't stated: sandboxing.

But here's the thing: the benefit that you highlight—app currency—was already available through PPAs and 3rd party repos. The only thing that snaps add is the sandboxing. I agree that sandboxing is not a small thing. PPAs had a tendency to break the system because they often dragged in incompatible libraries that break dpkg, whereas sandboxing  creates a separate environment that doesn't touch the host system. Moreover, because PPAs operate at a system level, a malicious PPA will corrupt your system whereas a snap won't. These are all theoretical snap pluses and I like them.

I would like to emphasize that: *I like them.*

But there is a dark side that snap proponents too often forget or dismiss. I've already listed some of them.

Here's yet another: One of the reasons that Ubuntu is so secure is because of the discipline that is imposed on app developers. Canonical does not allow just anyone to post their app in the repos. It is a curated process that requires—among other things—the the app source code. I believe (though I can't cite the source for this belief) that app authors can't post binaries. It is a pull process, not a push process. App authors can request that their apps be added, but they ***must*** contribute the source and the repo maintainers then compile the binary from that source. This process shines a very bright light into what would otherwise be a very dark corner and acts as a huge deterrent to any hanky panky. It's precisely the absence of such transparency that has turned proprietary app stores into such malware cesspools.

My fear is that the whole self-contained packaging movement will drag Linux into that same malware cesspool. When you allow app devs the freedom to do whatever they want, the natural result is pollution of the ecosystem. Yes, you get current apps from the responsible devs, but you also get rogue apps and malware from the careless or malicious ones. When there's no marshal on duty, the outlaws take over Dodge City (only the old&#8209;timers will get this reference :P). This is a problem not just with snaps, but with flatpak and AppImage too.

We can understand why distro builders find repo management such a pain and why they won't commit to app currency: it is impossibly labour&#8209;intensive. So, we end up trading currency for stability. That repo app may be several versions old, but it works, whereas the newest version may break your system. I will choose stability over currency any day, so I'm okay with repo management the way it is now. But if Ubuntu goes to the next step, where they eliminate repos altogether and just leave the ecosystem wide open to app developers (whether good, bad or ugly), then we will have lost the single most important advantage that Linux has over proprietary OSes—secure and reliable repos. That would be the death knell of Ubuntu.

There's not much that can drive me away from Ubuntu, but the loss of the repos would do it. So when you say > I believe that is the objective……I cringe. And, respectfully, I hope that you're wrong. [-o<
> …Currently, 15GB out 65GB of a SSD is used for my laptop's function. Seems reasonable :)
15 GB is not excessive by today's standards. But I still have VMs from the Trusty days that only have 8 GB of defined space *in total*. I had to grow my VMs to 16, then 32. Now, I'm committing 64. This is not a good trend. A single VM at 64 GB is not a deal breaker. 20 VMs at that sort of space commitment is very much a deal breaker.

I'm surprised that you are able to fit all of your snaps into a 15 GB footprint. I might explore that in a VM. My wrestling match with Mrs DH's snap bloat was the Telegram app. I've already posted about the kde thing. Her footprint for this one app was 7 GB. This was my own experience with other apps too, but I must admit to not pursuing matters deeply because, shortly after the start of my own misadventures, I resolved to eliminate as many apps as I could from snap in favour of traditional methods even if this required PPAs. I now only run LXD as a snap. No choice in the matter.

Oh, and BTW, I don't consider Android a good yardstick for *anything*. As a mobile OS, it is ridiculously bloated, restrictive and insecure. The penultimate nanny&#8209;tech, surpassed only by that ultimate in nanny&#8209;tech: iOS.

---

### Post by #&amp;thj^% on 2023-02-14
> **donald187 said:**
> I generally go with the tyranny of the default.  I go with the default unless there's a need to do something else.  

There is wisdom in that ;)
> **donald187 said:**
> I just find this topic interesting.
I do as well, I learn a lot about myself from my reply's......

---

### Post by DuckHook on 2023-02-14
> **ajgreeny said:**
> …it drives me nearly insane…
aj…

I'm afraid that we have normalized insanity. I've explored this theme just now with this post: [https://ubuntuforums.org/showthread.php?t=2483994&p=14130947#post14130947](https://ubuntuforums.org/showthread.php?t=2483994&p=14130947#post14130947)

I hope you get a chuckle out of it.
> I haven't seen or had to use Windows 11 but do occasionally have to use Windows 10…
I don't think you will take kindly to W11. I installed it for the first time a couple of months ago. The first outrage was right at the initial install process: it won't let you install without a MS account that forcibly ties you in to the borg collective. This freaked me out. A small rump of power users can do a web search and figure out how to disable this forcible assimilation process, but it requires firing up a power shell at the initial install stage, setting a registry flag, then a reboot (I believe). General users are out of luck.

Do you remember that awesome/controversial 1984&#8209;themed Apple commercial that ran only once during the Super Bowl some years ago? Well, it has indeed come to that.

"Resistance is Futile".

---

### Post by VMC on 2023-02-14
> **DuckHook said:**
> ...
Do you remember that awesome/controversial 1984&#8209;themed Apple commercial that ran only once during the Super Bowl some years ago? Well, it has indeed come to that.

"Resistance is Futile".Yes I remember it well!

---

### Post by BBQdave on 2023-02-14
> **DuckHook said:**
> My fear is that the whole self-contained packaging movement will drag Linux into that same malware cesspool. When you allow app devs the freedom to do whatever they want, the natural result is pollution of the ecosystem.

I hope, perhaps a false hope, that developers of the applications I use would not place malware in the system. For me, that's GNOME, FireFox, Darktable, Gimp and Scribus. And hopefully all developers of open source software are acting in good faith.

My concern with my current set up is Google Chrome. It's their repo, and I do not know how much - if any information is shared with the Ubuntu Project.

> **DuckHook said:**
> Oh, and BTW, I don't consider Android a good yardstick for *anything*. As a mobile OS, it is ridiculously bloated, restrictive and insecure. The penultimate nanny&#8209;tech, surpassed only by that ultimate in nanny&#8209;tech: iOS.

I'm up and down with the value of Google's application eco-system and of course cautious of the data they mine - stated by them, to sell me stuff. If that statement is true, I think of it as no different than turning to the sports section of the paper and seeing all the tire adds :D

I like the communication function, and calendar and organizing that Google applications provide for my family and connected friends. If however, Google applications became a problem, I would switch to other applications such as Libre Office, Thunderbird and so on.

I remember (way back) when much of what I currently do was done entirely with full Mozilla Suite and GNU applications. I could get back to that :D

---

### Post by Perfect Storm on 2023-02-14
The reason why I'm de-googling myself on my computers. Switching search engine and so on. I know it's a bit off-topic, but speaking of Borg collective by billions of Dollars companies is a horror movie. It would be naive to to trust these mastodons.

---

### Post by DuckHook on 2023-02-14
&#8593; This &#8593;

I have now completely de-Googlefied, but it was *very* hard. Now I know what those who have quit smoking go through.

---

### Post by Perfect Storm on 2023-02-14
It's not completely true. The only Google thing I have is I'm using Youtube to reach  the masses with my videos :guitar:
But that's it. I would also unsubscribe to Facebook and Instagram, but as an Author to couple of books you need to communicate with your fans and followers.

---

### Post by donald187 on 2023-02-14
> **BBQdave said:**
> I hope, perhaps a false hope, that developers of the applications I use would not place malware in the system. For me, that's GNOME, FireFox, Darktable, Gimp and Scribus. And hopefully all developers of open source software are acting in good faith.

Actually, one of the things I like about Linux is that one doesn't have to trust.  There are eyeballs looking at the code to be sure nothing bad is going on.  This is one thing I don't like about these self-contained package systems.  I don't think there is the same level of transparency.

---

### Post by DuckHook on 2023-02-14
> **BBQdave said:**
> I hope, perhaps a false hope, that developers of the applications I use would not place malware in the system.
Not a false hope at all. When source code is the only thing allowed and it's the repo maintainers that compile it, I have every confidence in the resulting binary. But how do you know that it's even the app developer who is offering that flatpak or snap app? Who is checking for identity authenticity? Supply chain integrity? No funny business?

The repo system has been tried and tested. In all the years that Canonical has been around, I believe that only one malicious app has made it past their guard dogs. In contrast, not a month goes by where Apple's or Android's app store doesn't have to take down scores of malicious apps that successfully evaded their malware detectors. That's the difference between open source and closed source.

Oops, ninja'd by donald187

It's easy to check source code yourself. Turn on the repo's source code option and just download it. Whether you or I can read it is not the point. The fact that it must be available means that a bad actor would have to be unbelievably foolish to try something underhanded.

---

### Post by BBQdave on 2023-02-15
> **DuckHook said:**
> Not a false hope at all. When source code is the only thing allowed and it's the repo maintainers that compile it, I have every confidence in the resulting binary. But how do you know that it's even the app developer who is offering that flatpak or snap app? Who is checking for identity authenticity? Supply chain integrity? No funny business?

That did catch my attention when looking at *snap* applications. It seemed one individual was sited as developer to several different *snap* packaged applications. I did not know if that was someone trusted, who is packaging for *snap*? Or someone who is a fan of a group of applications, and is packaging them for *snap*?

I would hope there are safe guards for who and what is submitted to *snap*. As in *Black Hat Joe* can not submit a *snap* package of Scribus, because *Black Hat Joe* is not part of the Scribus team.

---

### Post by DuckHook on 2023-02-15
> **BBQdave said:**
> That did catch my attention when looking at *snap* applications. It seemed one individual was sited as developer to several different *snap* packaged applications. I did not know if that was someone trusted, who is packaging for *snap*? Or someone who is a fan of a group of applications, and is packaging them for *snap*?

I would hope there are safe guards for who and what is submitted to *snap*. As in *Black Hat Joe* can not submit a *snap* package of Scribus, because *Black Hat Joe* is not part of the Scribus team.
Very good point.

The problem is that it's a grey area. The nature of FOSS is that the boundaries of who belongs to the "team" are not only vague but fluid. People come and go all the time. Some contribute intermittently. Others contribute at the edges by, say, working on translations or documentation or on the help desk. They are kinda sorta "on the team" but not one of the devs. Even if there is a gatekeeper for snaps, what criteria do they use?

This gives us insight into what the real problem is: relying on the integrity of the snap author is not a reliable solution. It is fundamentally flawed and cannot work. We need a process that ensures app integrity independently of who the snap author is.

But we already have those. They are called repos. If snaps submitted to the same regimen… where the app author can only submit source code that is then compiled by Canonical's maintainers, this would eliminate that exposure. But that would be reinventing an existing wheel, so what would be the point of snaps?

Anyways, I don't think snaps are going away, so this is an interesting but ultimately academic discussion.

---

### Post by Perfect Storm on 2023-02-15
Since when did Joe sixpack became Black hat Joe? :lolflag:

---

### Post by BBQdave on 2023-02-15
> **DuckHook said:**
> This gives us insight into what the real problem is: relying on the integrity of the snap author is not a reliable solution. It is fundamentally flawed and cannot work. We need a process that ensures app integrity independently of who the snap author is.

Still researching, but one article I came upon: [https://ubuntu.com/blog/whats-in-a-snap](https://ubuntu.com/blog/whats-in-a-snap) discusses the *snap*'s filesystem (in the contained application) and organization. The article states that you can download any *snap* and unpack it to see exactly what's inside.

[I]snap download &#8220;snap name&#8221;
unsquashfs &#8220;snap name&#8221;[/I]

So good you can see what's inside a *snap*. But still researching what the oversight is for those submitting a *snap*. If it ends up that Canonical does duplicate oversight of the *snap store* the same as .*deb repos*, then the advantage would be up to date applications (in containers) on stable LTS systems.

Snap-store and snaps seem very much still in development, though they have deployed it. I guess we're the guinea pigs :)

---

### Post by TheFu on 2023-02-15
On servers, I'm on the fence about snaps.  I love lxd and that's the only snap I'm forced to use.  It has issues, especially on servers when it auto-updates without admin approval and crashes a number of linux containers.  That shouldn't happen and generally, it doesn't.  More work needed. I'd rather have lxd without the snap package.

On desktops, I've just moved away from Ubuntu to avoid snaps.  It was just too much hassle and I got tired of fighting with the OS when it isn't necessary.  I'm testing 2 other desktop distros now. It is like a fresh breath of air in many ways, but there are some hassles too.  Nothing is perfect.  
Ran Mint Cinnamon for a few hours before switching to fvwm as the WM.  Moved my 20.04 Ubuntu "desktop" settings and files (not Gnome) over to the Mint 21.1 install.  
Spent a few hours with Xubuntu 22.04 a few days ago which is what drove me away. Found that even more hassle than 20.04. It convinced me that Ubuntu desktops aren't for me anymore.  I've been primarily on Ubuntu since 2006, so this is a pretty big change/decision.

I plan to test MXLinux for a few hours. Perhaps it will be a better fit?  I'm worried about package support with a niche release like MX. I grabbed the fluxbox version. Figure swapping that out for fvwm will be easier.  MX is based on Debian stable, but with newer versions of some major packages and MX software every few months.  As long as I have 1 desktop release that works, I can run the programs I need over remote X11 via ssh.

Neither choice is in stone yet, but I have to say the ZFS on Mint 21.1 is fast and feels good. Not having to deal with snaps is really nice, but having the option, if I choose, is nice too.  
Mint feels good and familiar, but brings only with hassles that are Linux-wide ... like the paste protection in the newer bash releases:
```
echo "set enable-bracketed-paste off # retain old select/paste behavior" > ~/.inputrc
```
or the login banner junk handled by 
```
touch ~/.hushlogin
```
Right after the Mint install, a Welcome wizard showed up with the important things to be done.  I loved that a link to the release notes for the system was right there.  There was also a Backup setup "Launch" button.  These little details matter to people new to Linux.  Canoncial should steal these ideas (if they haven't already).  I did have trouble scanning for the place to change the screen resolution ... but typing "resolution" into a search immediately offered "Display Settings".  Brilliant.  Toggling a dark theme was right there too - I don't know much about themes. The result was nice.

Sigh.  So long and thanks for all the fish, desktop Ubuntu.

BBQdave, seems like someone could create a snap downloader and converter to AppImages, so we can have local control back, without mandated updates externally controlled.

---

### Post by Perfect Storm on 2023-02-15
On Zorin OS we have both Flat and snaps enable by default, but both can easily be disabled without any fuss if the user desire.

---

### Post by BBQdave on 2023-02-15
> **TheFu said:**
> Sigh.  So long and thanks for all the fish, desktop Ubuntu.

BBQdave, seems like someone could create a snap downloader and converter to AppImages, so we can have local control back, without mandated updates externally controlled.

I appreciate all the information and insight you all are providing. I am very close to scrubbing Ubuntu and loading Debian Bullseye. I really am trying to give Ubuntu a try (again, after many years) but there are challenges and odd function. I am sincerely not trying to flame Ubuntu users, but it is not the same experience as Fedora 37 Workstation.

Gnome Software in Fedora, loads application choices quickly and defaults to the RPM. A lot of applications to explore.
Gnome Software in Ubuntu, loads blank rectangles that are populated after about 20 seconds, and then only a few choices for a given category and it defaults to snap.

I easily loaded Darktable, Gimp, and Scribus with Fedora. Had some challenges with Ubuntu, and function of those apps... is not the same as in Fedora.

That's some of the quirky functions with Ubuntu. Feels like an unfinished work in progress - with a lot of unanswered questions.

I like working with a RPM distro and a DEB distro. Similar to you TheFu, I am researching other distros to replace Ubuntu.

---

### Post by VMC on 2023-02-16
I'm not jumping the boat just yet, as I can still remove Snap and the programs I use Snap is not require.  Although, I do have other partitions using other Linux distributions, that I use from time to time, also as a fail safe **when that day comes.**

---

### Post by TheFu on 2023-02-16
> **VMC said:**
> I'm not jumping the boat just yet, as I can still remove Snap and the programs I use Snap is not require.  Although, I do have other partitions using other Linux distributions, that I use from time to time, also as a fail safe **when that day comes.**

I'm not planning to jump for servers either, just desktops.  I prefer leaner GUIs, so there's always been some dislike since Unity in 11.10 was pushed.

I can see where some people doing IoT stuff might love snap packages.  For me, it is a complete non-starter. I've had to support thousands of client workstations before and not controlling when updates occur is a non-starter for client requirements. I suppose if that doesn't matter, then snaps would remove many issues for some software companies who aren't so strong in infrastructure knowledge.

---

### Post by maglin2 on 2023-02-17
> **BBQdave said:**
> 
Gnome Software in Fedora, loads application choices quickly and defaults to the RPM. A lot of applications to explore.
Gnome Software in Ubuntu, loads blank rectangles that are populated after about 20 seconds, and then only a few choices for a given category and it defaults to snap.


I only have limited experience with it, but Discover (the KDE software app) in Kubuntu seemed to behave more as you want. It loads pretty quickly and the default source seemed to be user set (though I never tried changing it).

I have tried Fedora, and it was fine, but for me I think 5 year LTS stability (ie ubuntu gnome) will always win out.

My use case is very simple though - full disk encryption, no separate home partition. Snaps have never caused me any problem and I have masses of unused disk space, so I am pretty much unaware of their presence. Other than luckybackup and synaptic (which  are deb) I only use default install apps.

One simplification is that I have stopped using firejail with firefox since it became a snap. I may migrate to thunderbird snap soon for the same reason.

---

### Post by mikodo on 2023-02-17
I appreciate this discussion and I hope it continues, as time and things change with Snaps. I would like to have an informed decision, to stay or to not stay with Ubuntu, in the next couple of years.

---

### Post by #&amp;thj^% on 2023-02-17
> **mikodo said:**
> I appreciate this discussion and I hope it continues, as time and things change with Snaps. I would like to have an informed decision, to stay or to not stay with Ubuntu, in the next couple of years.
+1
Agreed

---

### Post by BBQdave on 2023-02-17
> **maglin2 said:**
> My use case is very simple though - full disk encryption, no separate home partition. Snaps have never caused me any problem and I have masses of unused disk space, so I am pretty much unaware of their presence. Other than luckybackup and synaptic (which  are deb) I only use default install apps.

That's what I am looking to do, keep it simple with my install too. I checked out Debian 11, nice distro, but a lot of older applications.

Ubuntu 22.04 install: Minimal (browser and utilities) + GNU Image Manipulation Program (deb)

I'll ride with this install and see how FireFox performs as a *snap* (the default install) :)

---

### Post by mikodo on 2023-02-17
> **BBQdave said:**
> That's what I am looking to do, keep it simple with my install too. I checked out Debian 11, nice distro, but a lot of older applications.


Ubuntu gets it sources from [Debian Testing]("https://wiki.debian.org/DebianTesting"). One could use that instead of a Debian Stable install, for more up to date applications. Also, if one just wants a few newer applications, possibly they are in [Debian Backports]("https://backports.debian.org/") to use to install newer versions of things, while keeping the more stable well ... Debian Stable.:)

---

### Post by ajgreeny on 2023-02-18
> **mikodo said:**
> Ubuntu gets it sources from [Debian Testing]("https://wiki.debian.org/DebianTesting"). One could use that instead of a Debian Stable install, for more up to date applications. Also, if one just wants a few newer applications, possibly they are in [Debian Backports]("https://backports.debian.org/") to use to install newer versions of things, while keeping the more stable well ... Debian Stable.:)
For quite a long time now I have been trying Debuan Unstable (sid) and slightly surprisingly to me as i expected it to be a bit flaky and crash fodder, it has been running faultlessly

I am not recommending you use that as your daily system but simply to report how well it is doing!

---

### Post by mikodo on 2023-02-18
@ aj Cool! Good to know. :)

---

### Post by DuckHook on 2023-02-18
> **maglin2 said:**
> …for me I think 5 year LTS stability (ie ubuntu gnome) will always win out…
…One simplification is that I have stopped using firejail with firefox since it became a snap. I may migrate to thunderbird snap soon for the same reason.

> **mikodo said:**
> …I would like to have an informed decision, to stay or to not stay with Ubuntu, in the next couple of years.

> **ajgreeny said:**
> For quite a long time now I have been trying Debuan Unstable (sid) and slightly surprisingly to me as i expected it to be a bit flaky and crash fodder, it has been running faultlessly…
I used to think that 5 year LTS was really important to me, but lately, I've found myself upgrading versions every new LTS release anyway, so two and a half years at most. I suppose that people running servers will find 5 years useful. Perhaps I'm skewed by the fact that I'm a member of these forums and, in order to help out, must have the latest release installed.

Given the above, moving to another distro is not hard. Even rolling releases would be fine.

But I stick with Ubuntu because it has proven itself to me. It's not so much that I owe them anything; it's that a good track record is not to be lightly dismissed.

When I compare my current experiences to those of fifteen years ago, the OS is now a lot stabler and more reliable. For example, full version network upgrades are now almost guaranteed to work for me; fifteen years ago, they were brutal and not even worth trying. But even fifteen years ago, with less stability, Ubuntu was still more reliable than the proprietary OSes. When I recall the gawd&#8209;awfulness that drove me away from Windows (first XP, then Vista being the final nail in the coffin), using Ubuntu was like waking up from a bad dream. Snaps may be irritating at times, but that's all they are: irritating. Ubuntu is still a fine distro that does 99% of its job happily with no fuss, no muss and certainly no deal&#8209;breaking failings.

It's always a good idea to stay apprised of the alternatives and, if I were to change distros, Debian would be a natural choice. But it would take a lot to force me to change (though abandoning/orphaning the repos would do it).

---

### Post by BBQdave on 2023-02-18
> **mikodo said:**
> Ubuntu gets it sources from [Debian Testing]("https://wiki.debian.org/DebianTesting"). One could use that instead of a Debian Stable install, for more up to date applications. Also, if one just wants a few newer applications, possibly they are in [Debian Backports]("https://backports.debian.org/") to use to install newer versions of things, while keeping the more stable well ... Debian Stable.:)

Thanks for this information! I definitely liked Debian 11, and my trimmed down approach to applications is a good fit.

But I also like Ubuntu :) I will keep working with Ubuntu and research Debian to get a better understanding of setup and applications.

---

### Post by VMC on 2023-02-18
> **DuckHook said:**
> ...

But I stick with Ubuntu because it has proven itself to me. It's not so much that I owe them anything; it's that a good track record is not to be lightly dismissed.Yes, indeed. Ubuntu is the default standard for me.

> **DuckHook]When I compare my current experiences to those of fifteen years ago, the OS is now a lot stabler and more reliable. For example, full version network upgrades are now almost guaranteed to work for me said:**
> I've been doing the same thing recently. I use to install the latest Ubuntu offering. Now I stick with current LTS

[quote]It's always a good idea to stay apprised of the alternatives and, if I were to change distros, Debian would be a natural choice. But it would take a lot to force me to change (though abandoning/orphaning the repos would do it).I have a couple of other distros installed to compare., nothing more right now.

---

### Post by donald187 on 2023-02-18
> **BBQdave said:**
> Thanks for this information! I definitely liked Debian 11, and my trimmed down approach to applications is a good fit.

But I also like Ubuntu :) I will keep working with Ubuntu and research Debian to get a better understanding of setup and applications.

Be a bit careful with Debian Testing.  It's the least secure of the three:  Stable, Testing, and Unstable.  Security fixes have a low priority and are often delayed.  it's not meant to be a rolling distribution like Arch.  It's a development branch.

[https://www.debian.org/security/faq#testing](https://www.debian.org/security/faq#testing)

---

### Post by mikodo on 2023-02-19
> **donald187 said:**
> Be a bit careful with Debian Testing.  It's the least secure of the three:  Stable, Testing, and Unstable.  Security fixes have a low priority and are often delayed.  it's not meant to be a rolling distribution like Arch.  It's a development branch.

[https://www.debian.org/security/faq#testing](https://www.debian.org/security/faq#testing)

Thanks for sharing this. Tis an important point.  I had forgotten it.

---

### Post by maglin2 on 2023-02-19
> **DuckHook said:**
> I used to think that 5 year LTS was really important to me, but lately, I've found myself upgrading versions every new LTS release anyway, so two and a half years at most.

I usually do the same, but it's still nice to be able to have a look at an LTS release and say 'Nah, I think I'll sit this one out' which I have with a couple of LTS releases.

---

### Post by DuckHook on 2023-02-19
> **VMC said:**
> …I have a couple of other distros installed to compare., nothing more right now.
I used to play around with a few different distros in VMs. Haven't done so for years. Now that I can do so more efficiently by using containers, I might play around with one or two again—or I might not—the urge to explore distros has really diminished in me. Maybe it's how stable Ubuntu has gotten, maybe it's how much LXD has refined my installation experience, but it's most likely just the descent into routine that comes with advancing age.

---

### Post by DuckHook on 2023-02-19
> **maglin2 said:**
> I usually do the same, but it's still nice to be able to have a look at an LTS release and say 'Nah, I think I'll sit this one out' which I have with a couple of LTS releases.
Or be forced to sit them out because Canonical orphaned something in the newer release. I have a tidy little thin server that just sips power. Trouble is that it's 32&#8209;bit, so is orphaned after Bionic. I still have 18.04 on it for that reason. I'll have to sign up for ESM on this one only, retire it, or switch to Debian. Bionic EoL is coming up soon, so I'll have to deal with it (yuk).

One of the acknowledged good things about snaps is how they allow those who value stability to stick with older LTSes and still have up&#8209;to&#8209;date apps. I do value that.

It's interesting how almost all "features" come with both a light side and a dark side. Technology is so much like: "a long time ago in a galaxy far, far away".

---

### Post by bernard010 on 2023-03-13
I like Snaps. They are containerized with all the dependencies included.
Simple to install and uninstall.Snaps have been Ubuntu's priority for quite a while now.
There are a vast amount of snaps now.   [https://snapcraft.io/](https://snapcraft.io/)  
Snaps work well with loT, Servers, like juju, lxd, maas, etc.
Desktop Ubuntu is comprised of snaps 20.04, 22.04.
Yes I actually like snaps.  
If it is not in a snap we know we can always install it the old way.:)
Snap confinement has 3 different degrees of confinement best described here:
[https://snapcraft.io/docs/snap-confinement](https://snapcraft.io/docs/snap-confinement)

---

### Post by TheFu on 2023-03-13
> **bernard010 said:**
>  
If it is not in a snap we know we can always install it the old way.:)

Really?  How can I install lxd without a snap?
My users HOME directories aren't all in /home/. Some use NFS mounts and different directories. No snap programs/packages work for those users.
Some constraints in snaps prevent access to all my NFS storage.  How do I gain access to those files for snap programs without moving where they are mounted, since lots of the systems here expect the data to be in specific directories - directories that snap packages don't allow access.

But the install of lxd without a snap would be fantastic.  So, how is that accomplished?

---

### Post by mIk3_08 on 2023-03-13
> **TheFu said:**
> But the install of lxd without a snap would be fantastic.  So, how is that accomplished? That is only for nerg and for genius. That would be a secret method for security reasons. :-D Regards and cheers.

---

### Post by mikodo on 2023-03-14
> **donald187 said:**
> I've decided I like snaps for applications that require version bumping to receive security updates such as Firefox, Thunderbird, and Chromium.  I was on Debian for a few years but was keeping an eye on Thunderbird in Ubuntu as well.  Eventually these version-bump applications need to be upgraded.  For example Thunderbird (e.g. from 91 to 102) or the same in the case of Firefox ESR on Debian.  This can take months at times meanwhile the cve's pile up. This included a high cve in Thunderbird in Ubuntu in the transition from 68 to 78 if I recall correctly.   Also the Chromium versions on Debian for years were generally way behind.    My understanding is that there was just one maintainer who just didn't have the time that Chromium required.  (They have a different maintainer now who is keeping it up to date.)  Snap (or Flatpak) seems to take care of these problems.
I am pretty sure, I am going to multi-boot Debian (maybe Stable and Sid) and Xubuntu 22.04, in a year or so. I love Mozilla Firefox. It seems the Mozilla Firefox Backports may be a solution to keep the cve's at a safer amount. Please see the link below about this. As you say, Chromium is being maintained by someone who is able to keep it up to date. Good. As for Mozilla Thunderbird, I don't use it, so I haven't looked very hard for solutions for this. It seems, one can download it themselves, and update it also. Please see the links below. 

Debian Mozilla Team, where one can choose Firefox ESR for Stable, that has Mozilla security updates:
[https://mozilla.debian.net](https://mozilla.debian.net)[URL="https://mozilla.debian.net/"]
[/URL] 
States: " ... it has the  latest security and stability fixes":  
[URL="https://support.mozilla.org/en-US/kb/switch-to-firefox-extended-support-release-esr"]https://support.mozilla.org/en-US/kb/switch-to-firefox-extended-support-release-esr
[/URL]  
Installing Thunderbird on Linux:  
[URL="https://support.mozilla.org/en-US/kb/installing-thunderbird-linux"]https://support.mozilla.org/en-US/kb/installing-thunderbird-linux
[/URL] 
 Updating Thunderbird:  
[URL="https://support.mozilla.org/en-US/kb/updating-thunderbird"]https://support.mozilla.org/en-US/kb/updating-thunderbird




[/URL]

---

### Post by mikodo on 2023-03-14
[URL="https://support.mozilla.org/en-US/kb/updating-thunderbird"].
[/URL]

---

### Post by donald187 on 2023-03-14
> **mikodo said:**
> I am pretty sure, I am going to multi-boot Debian (maybe Stable and Sid) and Xubuntu 22.04, in a year or so. I love Mozilla Firefox. It seems the Mozilla Firefox Backports may be a solution to keep the cve's at a safer amount. Please see the link below about this. As you say, Chromium is being maintained by someone who is able to keep it up to date. Good. As for Mozilla Thunderbird, I don't use it, so I haven't looked very hard for solutions for this. It seems, one can download it themselves, and update it also. Please see the links below. 

Debian Mozilla Team, where one can choose Firefox ESR for Stable, that has Mozilla security updates:
[https://mozilla.debian.net](https://mozilla.debian.net)[URL="https://mozilla.debian.net/"]
[/URL] 
States: " ... it has the  latest security and stability fixes":  
[URL="https://support.mozilla.org/en-US/kb/switch-to-firefox-extended-support-release-esr"]https://support.mozilla.org/en-US/kb/switch-to-firefox-extended-support-release-esr
[/URL]  
Installing Thunderbird on Linux:  
[URL="https://support.mozilla.org/en-US/kb/installing-thunderbird-linux"]https://support.mozilla.org/en-US/kb/installing-thunderbird-linux
[/URL] 
 Updating Thunderbird:  
[URL="https://support.mozilla.org/en-US/kb/updating-thunderbird"]https://support.mozilla.org/en-US/kb/updating-thunderbird




[/URL]

Thanks.  Debian haven't released Firefox as a Backport...

[https://packages.debian.org/search?keywords=firefox](https://packages.debian.org/search?keywords=firefox)

 ...since Firefox started using Rust which I understand is difficult to maintain (or update?) on Debian.

[URL="https://forums.debian.net/viewtopic.php?p=715665#p715665"]https://forums.debian.net/viewtopic.php?p=715665#p715665

[/URL]You'll notice that your first link says Firefox is not available.

When Firefox-esr was getting behind one time I did use the tarball from Mozilla for a while.  Then when Firefox-esr was upgraded I dutifully switched back. ;)

---

### Post by #&amp;thj^% on 2023-03-14
I need to add here, Debian testing gets new updates, which means it gets security updates. Eventually. It can (and does) take days for critical security updates to migrate from unstable to testing after stable has access to patched version.
[https://www.debian.org/security/faq.en.html#testing](https://www.debian.org/security/faq.en.html#testing)
Add a Repo:
```
 deb http://security.debian.org/debian-security bullseye-security main contrib non-free

```

---

### Post by bernard010 on 2023-03-14
> How can I install lxd without a snap?
From source, [URL="https://linuxcontainers.org/lxd/docs/master/installing/"]https://linuxcontainers.org/lxd/docs/master/installing/

[/URL]

---

### Post by nimafanniasl on 2023-03-26
As a normal PC user, I had a bad experience with snaps and new ubuntu versions in general, it isn't exciting anymore!
Canonical is still trying to get gnome like unity with extensions and themes and it's getting so heavy!

---

### Post by BBQdave on 2023-03-28
> **nimafanniasl said:**
> As a normal PC user, I had a bad experience with snaps and new ubuntu versions in general, it isn't exciting anymore!
Canonical is still trying to get gnome like unity with extensions and themes and it's getting so heavy!

You may want to check out Debian :)

Running Debian 11 with Gnome + Flathub (flatpaks) a very pleasant experience. Stable system with the latest versions of applications I use.

That said, when I upgrade to Debian 12, will keep it mostly vanilla and only pull added applications from Debian repo. My Debian machine is my daily driver and meets my needs nicely.

Fedora is interesting, in that you can pull fairly fresh applications from their repos (no need for flatpaks) and yet a stable distro.

So if you do not want Snap or Flatpak, some solid GNU/Linux distros available. If you need cutting edge fresh (even beta versions) of an application, Snap and Flatpak are great options, but it is going to add some heft to your distro.

---

### Post by ajgreeny on 2023-03-28
I have been using Debian unstable for some time simply as a test system in a virtual install using KVM.

It has been just about faultless running all that I need without any real difficulties, including Firefox downloaded and run directly from the executable in the .tar.gz download.

---

### Post by mikodo on 2023-04-02
> **ajgreeny said:**
> I have been using Debian unstable for some time simply as a test system in a virtual install using KVM.
 
I'm pretty sure I will be running both Debian Stable and Unstable, when Bookworm goes to Stable. I've run Stable before, while dual-booting with Xubuntu. I found all I did with Stable, was make it look like Xubuntu :) I symlink my Data Partition directories, (Docs etc,) to my $HOME. I'll probably do the same for Stable and Testing.  If anything goes 'Wonky' on Unstable, then I can spend time on Stable until it is fixed. Although this means configuring two installs, but I am retired now, and have the time. Three installs actually, with Xubuntu 24.04.

I was surprised to see Debian literature recommending Desktop Users use Unstable:

[https://www.debian.org/doc/manuals/debian-faq/choosing.en.html#s3.1.3](https://www.debian.org/doc/manuals/debian-faq/choosing.en.html#s3.1.3)

---

### Post by TheFu on 2023-04-02
Yesterday my Nextcloud install using a snap got an automatic update - 25.0.3 --> 25.0.4.  The main nextcloud app that I use is "News" and the update broke it.  The other nextcloud apps that I use seemed to work, but since 95% of my NC use is with News, that doesn't matter.

It took a bit of time to figure out, reverting to 25.0.3 didn't solve the problem. News still didn't work.
Looked up at the News App project page to find that v25 of Nextcloud isn't supported ... which seems strange, since it was working the last few weeks and I'm 100% positive I was on v25 of Nextcloud.  

Anyway, I needed to be on v24.x of nextcloud.

```
sudo snap revert nextcloud --channel=24/stable
```
no joy.
```
sudo snap refresh nextcloud --channel=24/stable
```
and wait for 10 minutes as everything was put back ... (I'm guessing). News was reset and working though there were about 2000 previously read articles that needed to be re-marked as read.

So the good news is that the snap system had a way for this service to be fixed.
The bad news is that the breakage was due to an upgrade I didn't explicitly request.  That is still one of the biggest issues with snaps.  NFS and HOME directory locations is the other. We need local overrides. We really do.

---

### Post by DuckHook on 2023-04-02
> **TheFu said:**
> …the update broke it…
…We need local overrides. We really do.
+1

Your story reinforces how fortunate I now feel to have rolled my own Nextcloud.

I've had to wrestle with snaps in a different way: although I only use 1 snap (because I have to) and that is for LXD, just that single platform alone has given me problems.

I share the same LXD containers across multiple boots. This is done through a workaround that TheFu might find useful for his /home directory woes: I have the whole LXD directory bind mounted to another partition. By doing so, I can bind mount the same LXD partition to each of my multiboot partitions. This allows me to share the same apps, configs and environments held within those LXD containers into every one of my multiboots which means that I don't have to install a separate suite of apps in each boot and keep them manually synchronized. This also allows me to run the latest apps because I can run containers comprised of the latest Ubuntu versions. The best of both worlds: I get the stability of an LTS in my host, but with the currency of the latest apps using containers.

The problem is that when snap automatically updates LXD, it auto&#8209;updates to the new version in whichever of my multiboots that I happen to be working on at the time. If I then switch to another boot, none of my LXD containers will run. The workaround isn't hard (just manually update the LXD snap), but it is a further illustration of TheFu's point: too much control is taken out of the hands of the user. Snaps continue to be problematic for the sort of creative edge cases that power users tend to implement.

---

### Post by TheFu on 2023-04-02
The home directly BIND mount doesn't work without changing the /etc/passwd entry too.  That's not possible in a corporate environment using LDAP.  If the passwd DB can't be trusted, then a system has even more problems than snaps.  It is unreasonable to demand all user HOME directories be under /home/{userid} - completely unreasonable.

As for the nextcloud snap - the trick seems to be to pick a working, stable, channel for each snap. Minor updates withing the same version shouldn't break anything and limiting snap updates to be on Saturdays has mostly been working for me.  It is a change and I'd rather have it default to asking me when a snap should be updated, not blindly update without a direct action, but for many people, their snap use is with browsers which we update almost weekly.

Management/upgrades with the nextcloud snap has been better and less hassle for the most part.  There are some oddities, definitely.
You and I should force our LXD setups to be in a specific, stable, channel. That should minimize disruptions. Snap does have methods to address that aspect. It is just a learning curve and something we need to learn and add to our snap setups.  Of course, it would be easier to have LXD in a snap-less environment.  Nextcloud has a more complex environment and I do appreciate that the snap is handling most of that without me having to do it manually.

---

