---
title: "A few simple beginner questions"
date: 2017-10-29
forum: Ubuntu, Linux and OS Chat
---

### Post by chrislw324 on 2017-10-29
I'm new to using Ubuntu and Linux in general. I have a few questions I hope I can get answered. Thanks in advance!

1. I downloaded Ubuntu 16.04, but now there is a new version out (17.01). How do I upgrade to the latest? Do i have to manually upgrade somehow?

2. What exactly is a linux repository? I understand it is where all sorts of software you can download for linux resides, but is it kinda like the apple app store or the google play store? If I want to see and browse all the software in the repository, where can I do that?

3. I have Ubuntu dual booted with windows 10, and I've found that after loading Ubuntu, the next time I load Windows 10 and log in, the clock will be wrong. It will be four hours ahead. Has anyone experienced this problem and know how to fix it?

---

### Post by coffeecat on 2017-10-29
Welcome to the forum!

> **chrislw324 said:**
> 1. I downloaded Ubuntu 16.04, but now there is a new version out (17.01). How do I upgrade to the latest? Do i have to manually upgrade somehow?

I suggest you stay where you are for the time being. Ubuntu issues a new release every 6 months, but only every two years are they what are known as long-term support (LTS) releases. The numbering system for Ubuntu releases is year-month, so your 16.04 version was first released in April 2016. It is an LTS, and will be supported for 5 years from April 2016. The intermediate releases are supported for nine months only - since 16.04 there have been 16.10 (now out of support), 17.04 (support ends January 2018), and the recently released 17.10 (not 17.01) which will be supported only until July 2018. 16.04 will be supported - that is, updates and security patches - until April 2021. The next LTS will be released next April - 18.04.

As a newcomer you will probably be better off with the increased stability and long-term support of an LTS. The main drawback is that most repository apps will not be upgraded to newer releases - they will just have bug and security patches - with the exception of web browsers such as Firefox, for which you will always get the latest release. There are solutions to that, but I'll keep it simple for now.

> **chrislw324 said:**
> 2. What exactly is a linux repository? I understand it is where all sorts of software you can download for linux resides, but is it kinda like the apple app store or the google play store? If I want to see and browse all the software in the repository, where can I do that?

Here's a good start for Ubuntu:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Open the Software Centre. It looks a little bit like an app store and it's fairly easy to browse around. 

Some people might recommend you install the package manager Synaptic. I use it myself. It's a more powerful GUI app for installing and updating software, but you really have to know the package name you want. It's a bit off-putting for some newcomers. 

> **chrislw324 said:**
> 3. I have Ubuntu dual booted with windows 10, and I've found that after loading Ubuntu, the next time I load Windows 10 and log in, the clock will be wrong. It will be four hours ahead. Has anyone experienced this problem and know how to fix it?

I have one suggestion, which may or may not be correct. If your Windows is set to Eastern Time, assuming you are in the States, and your Ubuntu to London time, that might account for it. Click on the cogwheel icon top right of screen -> System Settings -> Time & Date. If it's showing the wrong location for you, simply click on where you are on the world map there.

---

### Post by verymadpip on 2017-10-29
Hi there.
Just my opinion:

1. Stick with the LTS (Long Term Support) release, which you have. (16.04 - that's the year & month of release by the way, so 17.10 is October 2017 release).
    LTS releases have 5 or 3 years support depending on which *buntu you are using.  Releases between LTSs only have 9 months support.
    The next LTS release is 18.04, then 20.04, etc.

2.  Yep.  The repos are kind of like an app store.  Search for Gnome Software from the dash or click the icon in the launcher that looks a bit like a capital 'A' on a shopping bag.

3.  Can't help with this one I'm afraid.

Dang, I'm just too slow for this game.

---

### Post by Bucky Ball on 2017-10-29
Welcome. 

1. You do not need to upgrade at all, particularly if everything is working fine and you're happy. The latest is not always the greatest. 16.04 LTS is a long-term support release, supported for five years from release until 2021, stable and a great place to start. 17.04, and now 17.10, are interim releases which are supported for nine months. You are fine where you are, nothing to panic about. Many of us only use the LTS releases (next is 18.04 LTS due next April). While a five year release has the chance to become very stable, interim releases can sometimes be a bit wobbly and will have some teething problems. By the time things have become stable it may be time to upgrade to the next release.

If you don't want to be upgrading to a new release every six months and taking the chance you are going to need to take some time out to crush a few bugs or if it is very important that your machine does not experience downtime (this applies particularly to production machines, servers, etc.), then LTS it is.  

2. The non-technical explanation: think of it like a big bucket full of software! Ubuntu has it's own 'official' repositories, but anyone can create a repository to contain and share their software. Someone else will give a fuller explanation before long.

3. Licensed, legitimate version of Windows? I have had the same issue happen myself a few years ago and don't remember how I fixed. What time do you have set in the BIOS and where is Windows getting it's time from? The net or ...?

(I have asked staff to more your thread to a support area as this is a chat area, not for support. Good luck. ;))

---

### Post by chrislw324 on 2017-10-29
Yes. It is a legitimate version of Windows. 
I'm pretty sure my time zone setting on Ubuntu is correct for me, but won't be able to doublecheck until I get Ubuntu back.
I had a non-related problem with windows and the support people walked me through reinstalling it. It fixed the problem, but now the option to boot Ubuntu is gone. So now I need to research fixing that..

---

### Post by vasa1 on 2017-10-29
Please ask support questions in the appropriate support sub-forum, _not_ in Chat. Also, please ask about one issue per question. In other words, don't club several questions together. The result may be quite confusing to other members of the forum.

And, it would be very nice of you to ensure that each thread has a title that informs the reader of the thread title and helps those who use search engines to find help on the same issue.

In the body of your question, please provide all information you think is relevant so that people can help you quickly rather than just guess.

For more, please see [Suggestions on how to get your support questions answered as quickly as possible]("https://ubuntuforums.org/showthread.php?t=1422475")

---

