---
title: "To deb or Snap or Flatpak?"
date: 2023-03-29
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2023-03-29
I have a number of non-techie neighbours/friends I support who use Ubuntu.  For those who do not want any notifications about updates I have been looking at the three main delivery package methods.  Personally  I use deb and have a number of ideas how to make deb apps update themselves without user awareness.  I have been frustrated with both snap and flatpak, largely around the inability to be able to establish a test environment to try out different methods of background updating (e.g. not easy to get previous versions of Chromium).  My question is the long term viability of, mainly firefox and chromium/google chrome, deb packages.   I tide seems to be turning re snap - will there be a time where the deb package for an app is no longer available?  I think the answer is Yes -  "it is foolish to rely on, say, firefox or chrome debs being continually updated".   At the moment I feel snap or flatpak do not meet my requirements (100% no user involvement re updates - it all happens in the background).  How will we know when a deb package is no longer being maintained/updated and the need to switch to snap/flatpak has arrived?

---

### Post by Quarkrad on 2023-03-29
Hmm .. just found out that .deb. is debian so I guess that as long as debian is around so will the .deb updates for debian apps (I'm thinking about the popular apps).  I wonder whether Canonical would ever drop the ability to install a .deb if snaps became widely adopted?

---

### Post by BBQdave on 2023-03-29
> **Quarkrad said:**
> I have a number of non-techie neighbours/friends I support who use Ubuntu.  For those who do not want any notifications about updates...

Flatpaks and Snaps update automatically. It gives a message that applications have been updated.

I am running Debian 11 with Flatpaks, applications updated automatically, no problem. There is no official flatpak or snap for Google Chrome, though I believe someone has packaged Google Chrome for Flathub - unofficial Flatpak.

Google Chrome would be a .deb package from Google. And you would update it as you would other packages. If your DE is Gnome, Software (Gnome) handles that nicely. I would offer, if your friends can use a browser and navigate the web, they can use Software to update.

On a side note: Snap-store appears to be handling this more directly than Flathub, clear defining of the source for Snaps. So a random person can not package Google Chrome into a snap loaded into the Snap-store. Snap-store and Flathub are still developing and appear to be working toward a stable eco system of applications. With one function, provide trusted packages.

Second note: When I upgrade to Debian 12, I will not be installing flatpaks or snaps, I will use applications from Debian repos and add Google-Chrome-Stable.deb from Google. For my use, the .deb applications function fine, and updating is easy with (Gnome) software :)

---

### Post by ian-weisser on 2023-03-29
> **Quarkrad said:**
> ...those who do not want any notifications about updates...

Folks who want no notifications about updates, and do not want to learn how to maintain their systems seem like poor candidates to use Ubuntu.

They will be unhappy and they will not contribute to the Ubuntu community. Their unmaintained and insecure systems will be compromised, and their whining about their unmaintained, compromised systems will damage Ubuntu's reputation.

Learning how to maintain the system (it's easy) seems a minimal barrier to entry to an open-source operating system.

> **Quarkrad said:**
> My question is the long term viability of, mainly firefox and chromium/google chrome, deb packages.

You must look at the community that creates each of those packages. There is no single answer. Google could cease developing Chrome for Linux tomorrow, or change from deb to flatpak for distribution.  Mozilla produces its own snap packages, while volunteers produce the debs and flatpaks...but Mozilla could change their mind.

Long-term viability only comes from 1) A user community willing to learn enough about their systems to be flexible. and 2) A user community willing to contribute back to upstream open-source projects. Users unwilling to be part of #1 and/or #2 get no certainty about the future.

> **Quarkrad said:**
> How will we know when a deb package is no longer being maintained/updated and the need to switch to snap/flatpak has arrived?

Since those folks want no notifications, they probably won't know until something breaks.

> **Quarkrad said:**
> I wonder whether Canonical would ever drop the ability to install a .deb if snaps became widely adopted?

This is answerable: In the Ubuntu Summit 2022, Mark Shuttleworh (owner of Canonical, and SABDFL of Ubuntu) clearly and unambiguously stated his intent to remain close to Debian. This is in line with years (decades!) of interviews and public statements by him expressing [I]exactly the same intent.

[/I]At the same time, Ubuntu Core systems cannot install deb packages at all on the base system...but that's a special product, not an indication of future intent for all flavors of Ubuntu.

---

### Post by BBQdave on 2023-03-29
> **ian-weisser said:**
> ...In the Ubuntu Summit 2022, Mark Shuttleworh (owner of Canonical, and SABDFL of Ubuntu) clearly and unambiguously stated his intent to remain close to Debian. This is in line with years (decades!) of interviews and public statements by him expressing *exactly the same intent.*

@ian-weisser your entire post is well said. +1

That is an interesting statement by Mark Shuttleworth. I figured application development was headed toward snaps, with the financial service component added. As in, payment to devs through small fee or donation button.

I can understand a LTS distro with snaps, stable distro and donation option when you load the latest GIMP-snap.

---

### Post by #&amp;thj^% on 2023-03-29
> **ian-weisser said:**
> Folks who want no notifications about updates, and do not want to learn how to maintain their systems seem like poor candidates to use Ubuntu.
May I add here as a aged/seasoned experienced user, I prefer not to see the notifications, but manually daily (or more) keep my system updated and out of harms way.
Do agree and support your whole concept of being notified though...(as long as i have the choice, and I do for now)
> **ian-weisser said:**
> 
They will be unhappy and they will not contribute to the Ubuntu community. Their unmaintained and insecure systems will be compromised, and their whining about their unmaintained, compromised systems will damage Ubuntu's reputation.
I have to watch my wording here, but I so agree on this.
> **ian-weisser said:**
> 
Learning how to maintain the system (it's easy) seems a minimal barrier to entry to an open-source operating system.
Speaks volumes>>>+1

> **ian-weisser said:**
> Long-term viability only comes from 1) A user community willing to learn enough about their systems to be flexible. and 2) A user community willing to contribute back to upstream open-source projects. Users unwilling to be part of #1 and/or #2 get no certainty about the future.
spot on.
> **ian-weisser said:**
> 
Since those folks want no notifications, they probably won't know until something breaks.
We see our share of that in all the sub-forums...:(

---

### Post by Quarkrad on 2023-03-29
Although I agree with what has been said it is a pity.  Personally I love ubuntu/linux because it provides me with a whole new world of learning, challenges and pleasure.  However, I have to be careful with my words here because I do want to offend, be sexist, or aged, or against anybody.  A few of the people I support are not young in years, mentally challenged in terms of learning new technology and to a degree frightened of 'all these new things'.  These people certainly do not fit the profile that some people, (disparagingly in my opinion) describe the typical 'linux use'.  E.g. linux is not for the masses - just for the geeks. (These are NOT my words).

So why did I move then to ubuntu?  Their Windows environment was constantly being hacked and although it was no issue for me to fix or rebuild I could see that ubuntu was going to be easier for them.  They love ubuntu but see it as a tool rather than something to maintain or a community to join.  The snap 13 days to upgrade message is confusing and for these Desktop people not helpful.

That being said, and agreeing with most of what you have said, it is a pity that ubuntu, with all it's flexibility, cannot cater for these people.  With all it's faults, for some people, Windows (in terms of app updates) just works with no user input.

---

### Post by #&amp;thj^% on 2023-03-29
> **Quarkrad said:**
>  it is a pity that ubuntu, with all it's flexibility, cannot cater for these people.  With all it's faults, for some people, Windows (in terms of app updates) just works with no user input.
Would this work for them:[https://www.cyberciti.biz/faq/how-to-set-up-automatic-updates-for-ubuntu-linux-18-04/](https://www.cyberciti.biz/faq/how-to-set-up-automatic-updates-for-ubuntu-linux-18-04/)
You could receive emails to monitor the progress or any miss-haps

---

### Post by BBQdave on 2023-03-29
> **1fallen said:**
> Would this work for them:[https://www.cyberciti.biz/faq/how-to-set-up-automatic-updates-for-ubuntu-linux-18-04/](https://www.cyberciti.biz/faq/how-to-set-up-automatic-updates-for-ubuntu-linux-18-04/)
You could receive emails to monitor the progress or any miss-haps

I was thinking somewhat on similar lines. Though not as direct of support.

Not the best security practice, but checking in every couple of weeks or monthly, and updating their systems. Given the described limited interaction by the user with the system, I would guess just a few applications are being used. Most patches are performance related.

I still question how difficult would it be to hit the update button in (Gnome) Software :) An opportunity for the user to have more independence with their system.

---

### Post by ian-weisser on 2023-03-29
> **Quarkrad said:**
> A few of the people I support are not young in years, mentally challenged in terms of learning new technology and to a degree frightened of 'all these new things'. 

Sure, been there also.

It's understandable that stock Ubuntu out-of-the-box, intended for a more general audience, might not automatically be the best fit. Just like a new automobile has the seats and mirrors and radio settings not-quite-right for you, minor changes to settings are easy enough to make Ubuntu very welcoming and safe for most folks. Just like learning which side the petrol tank door is on and what the dashboard lights mean, folks must learn a minimal amount if they want to get anywhere.

Updates without notifications is trivially simple using debs. Unattended Upgrades does it for security fixes, and it's very simple to add bugfixes. It's changing one line. Stay away from non-Ubuntu sources, which tends to rule out Chrome, though it can also be added to Unattended Upgrades (more difficult).

I supported a set of elder folks for about seven years using Ubuntu. All they wanted was the web browser; everything was through that. They asked me to hide the other applications on the dock. They asked me to set up autologin. They were sensible enough keep sensitive information offline, so I agreed. About three years on I upgraded them to the next LTS. That's all. They never needed any more help than that, and my fancy remote-desktop reverse-ssh support backdoor was never used.

Were I doing it today, I would edit Unattended Upgrades settings to include bugfixes, stick to the default Firefox browser snap, teach them the simple quit-and-refresh drill to keep the snap up-to-date, and mark my calendar for October 2024 for LTS release-upgrade. Optionally might consider setting Firefox to be more strict. And then go back to sleep until they phone with a question.

---

### Post by Quarkrad on 2023-03-30
Thank you - I have been experimenting with unattended upgrades hence me looking at the 'future' of deb compared to snap/flatpak - your comments are reassuring.  Both these people live within 5 minutes walk so 'support' is not an issue.

---

### Post by monkeybrain20122 on 2023-03-30
> **BBQdave said:**
> Flatpaks and Snaps update automatically.

I don't know about snap since I have removed it, but flatpak doesn't update automatically on 22.04 (i think some kind of bugs with gnome software). It did on 20.04 but always followed with some warnings. This is through the software store but the gnome store is forever broken for one or another reason. I am looking for a gui "app store" for flatpak apps for non tech users I might want to set up Ubuntu for. I found [this]("https://github.com/vinifmor/bauh#installation") and another one on gitlab but can't find the link now. Will test this out. I am not sure if it does automatic update though I don't see that as a big problem as long as there is an easy way to update.

@OP
security updates and be configured to install automatically. I don't think flatpak updates are security updates.

---

### Post by BBQdave on 2023-03-30
> **monkeybrain20122 said:**
> I don't know about snap since I have removed it, but flatpak doesn't update automatically on 22.04...

Yes, I should have been more clear: Ubuntu 22.04 -Snap updated automatically, Fedora 37 -Flatpak updated automatically, and Debian 11 -Flatpak updated automatically.

Although Snap would be part of the (auto update) solution for the OP, but Google Chrome (third party .deb) would be through (Gnome) Software. So given the information of the users the OP is trying to support, install the few applications they use with Snap and teach them how to update Chrome (clicking the update button in Software) and all should be good.

So basically the users would just click the update button in (Gnome) Software when an update notification appeared :)

---

### Post by Quarkrad on 2023-03-31
Again thank you for your suggestions. (@monkeybrain20122 - re gui for flatpak; have you looked at FLATHUB?).  Currently the users do 'just click on the update button' but they are of a condition that they keep forgetting what I say, or look at the reminder piece of paper on their desk, so phone me because a message has appeared on their Desktop.  I am currently looking at installed deb packages and including google chrome to be part of the unattended-upgrade process.  Also, I can manually forced unattended upgrade to happen as part of my  backup script that runs when they shutdown daily.

---

### Post by kurt18947 on 2023-03-31
I have a couple flatpaks installed on otherwise stock 22.04. Everything updates as expected. I do get a notice that snap updates are due but I haven't had to manually intervene in the process. I do power down at night when I think of it. I have at least 2 accounts - the original and a user account. If it wouldn't be too complex, make sure the "software updater" icon is prominent on the "housekeeping" account and not on the user account. If the user is able to understand and cope with a "housekeeping" and a "daily user account" that may work.

---

### Post by monkeybrain20122 on 2023-04-01
Come to think of it I am not getting flatpak updates automatically maybe because I have disabled updates from the gnome software store. It is annoying that it automatically restarts after any inconsequential little deb update. It is annoying like Windows.

---

### Post by PHerrmann on 2023-04-15
Hi everybody,
I would like to add a comment concerning Handbrake.
Current deb version is 1.2.2. This version allows you to read commercial encrypted DVDs as libdvdcss is installed with Handbrake.
When I tried to upgrade Handbrake, last version available is 1.6.1, but is only available through flatpak install. I followed instructions and version 1.6.1 is used via cli [FONT=system][FONT=arial]: [FONT=system]flatpak run fr.handbrake.ghb[FONT=arial][/FONT]
[/FONT][/FONT][/FONT]Handbrake 1.6.1 behave nicely, except that it is unable to read commercial encrypted DVDs.
Maybe I missed something, but I reinstalled deb version and I use this one to read commercial DVDs. I verified that Handbrake flatpak version still doesn't read commercial DVDs after libdvdcss is reinstalled.

---

### Post by NormanFLinux on 2024-03-23
It depends. Some flatpak packages are broken or don't run well; install deb. A close to immutable system is the ideal state. Notice I didn't say immutable because in real life compromises will always have to be made.

---

### Post by VMC on 2024-03-23
I only use [makemkv]("https://www.makemkv.com/") and have never had issue with commercial DVDs. I gave up Handbrake years ago. It was slow and confusing.

---

### Post by ian-weisser on 2024-03-24
> **PHerrmann said:**
> 
I would like to add a comment concerning Handbrake.
Current deb version is 1.2.2.


Let's offer a bit of a correction about the "current deb version"...

1.2.2 = Debian oldoldstable. Not available in any supported release of Ubuntu.
1.3.1 = Debian oldstable and Ubuntu 20.04 LTS
1.5.1 = Ubuntu 22.04 LTS
1.6.1 = Debian stable
1.7.2 = Debian testing and Ubuntu 24.04

---

### Post by monkeybrain20122 on 2024-03-26
So I have installed Ubuntu for someone new to Linux and need a gui tool to manage flatpak (gnome-software is broken) , I found [bauh]("https://github.com/vinifmor/bauh"), it is quite nice. It has a unified interface to search for,  install and upgrade flatpak, snap and  appimages (though it only can find appimage published in Appimage-Hub, so for example Krita is not there) 

Bauh is  itself can be downloaded as  an appimage.

---

