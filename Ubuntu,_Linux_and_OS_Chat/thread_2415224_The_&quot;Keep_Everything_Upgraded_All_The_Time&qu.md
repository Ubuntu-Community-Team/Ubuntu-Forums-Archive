---
title: "The &quot;Keep Everything Upgraded All The Time&quot; craze is annoying"
date: 2019-03-22
forum: Ubuntu, Linux and OS Chat
---

### Post by SagaciousKJB on 2019-03-22
I get so annoyed with this.  Everyone acts like if you use a version of software below the current release, hackers are going to break into your computer and kidnap your mother or something.  Half the time the updates only cover extremely minor bugs, that only happen in extremely specific use cases.  Meanwhile, the upgrade process ends up breaking stable, usable systems and in most instances is basically a case of "Don't fix what isn't broken."  Then when you need to go out and figure out how to revert to the old, stable software, instead of helping you, you just get a bunch of "security experts" lecturing you on keeping your software updated.

I feel like people have good intentions, they don't want the internet to be full of outdated devices with unpatched security holes, but in some ways it's pretty counter-productive.  I am just trying to get an older version of a software package installed, and the development group responsible for it basically won't help me and are instead urging that I not only upgrade to their latest software, but update my OS too. (And who knows how much that might break). Instead I'm just going to use their old software on an old OS too.  Gee that sure helped make the internet safer.

The funny thing is they didn't even have their facts straight.  They said 16.04 is EOL when it's not until 2021.  It's as if people just see bigger numbers and think, "Oh well that must be better!"  There's no consideration given to hardware limitations, or to what other safety they have in place.  It's like they just assume that every computer user doesn't want to upgrade because they're merely lazy, and that they're all patched straight into the internet with a cable modem and no firewall.

Anyway just had to complain because I'm getting really tired of it.

---

### Post by TheFu on 2019-03-22
Some excellent points.  

Some versions of 16.04 ARE EOL.  Ubuntu Server and Ubuntu Desktop (Unity) have 5 yrs of support, but  not all others do. Specific kernels have lost support. [https://wiki.ubuntu.com/Kernel/Support#A16.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/Support#A16.04.x_Ubuntu_Kernel_Support)  Many 3rd party packages didn't have any support from the day of installation.  Use the **ubuntu-support-status** command to see what Canonical thinks are supported packages.  This doesn't track the support states for outside packages.  

New is the enemy of stable.  That has always been true.

---

### Post by freemedia2018 on 2019-03-22
Refreshing take on this. Similar (recent) thread exists elsewhere called  "Getting off the software upgrade treadmill" and that one is about a  Slackware user who says the same.

> **TheFu said:**
> New is the enemy of stable.

Oh, I like that. I still believe in updates, but I think the OP has a point.

---

### Post by Tadaen_Sylvermane on 2019-03-22
Im very much on the keep updated bandwagon. That being said I do agree. I'm finding that my current server on 16.04 can't be upgraded to 18.04. I'm slowly coming to terms with it. And I admit maybe I'm to hardcore about keeping updated.

Your post definitely is making me think about it. Well said.

---

### Post by thenailedone on 2019-03-24
Good thing Debian has got you covered then.

---

### Post by Tadaen_Sylvermane on 2019-03-25
> **thenailedone said:**
> Good thing Debian has got you covered then.

I wish Debian would have me covered. I've been to hell and back trying to get Kodi to work properly. AMD hardware = pita. YMMV.

---

### Post by thenailedone on 2019-03-26
> **Tadaen_Sylvermane said:**
> I wish Debian would have me covered. I've been to hell and back trying to get Kodi to work properly. AMD hardware = pita. YMMV.

Sucks... bet and stuck with nvidia many years ago.

---

### Post by mastablasta on 2019-03-27
snap brought the option to install old software on new machine. hopefully that will get us somewhere.

i too am upset with all this. for example i have a perfectly good 14.04 working and setup and i have to upgrade it with a fresh install to 18.04 after i found out that i actually can not do the upgrade. aside from performing the fresh install, the windows 7 residing on the other side of the disk could also pose a problem. 

next is the wine i fooled around with lately. i used the playonlinux, but quickly found out their scripts actually do not work. fine with me i will use it's GUI to do the "manual install", i thought. so time to load two platinum edition games (Morrowind and Oblivion). none of them worked. i installed Morrowind to 14.04 once before with little to no issues. and then i searched the internet and searched. official pages, UESP wiki, Wine appdb... and i ofund out many people have reported similar issues. what once worked without any errors now throws out a bunch of them and there are no real fixes or workarounds. would it be nice if i could just use the old version in an easy way and install there? or if they have to move forward with better product to at least insure backwards compatibility. 

also IMO platinum rating should be reserved for the likes of Torchlight where you just install and play. not for items where you need to install this and that and disable this and that...

---

### Post by LastDino on 2019-03-28
Couldn't agree more. I've a very peculiar problem with Windows office (hope its alright to mention here), I like to snap my watchlist from NEST trader to office excel so I can do further calculations on it, but this process is not working as flawlessly as it was working on office 2007. Some compatibility issues and MS shifting to different methods, but now that 2007 has reached end of life two years ago, it has left us wanting  for solutions elsewhere. We have tried on 2010 and further versions on various times, and the live update sheet breaks on every reboot of NEST

All this could've been avoided if 2007 was left untouched, and I don't really use anything other than this on it.

---

### Post by jdeca57 on 2019-03-28
It all depends.

On the one side programmers make (unwanted) changes and then they try to convince the users that these changes were worth it and that they should be adapted. Personally I don't see much differences in versions of LibreOffice but then that's because I don't use much of it. And I guess for most people the MS Office of 2007 or earlier is completely satisfying. I still use mc and that's ancient but it's the most productive software I know in text mode. So here change is bad.

And then there is software where changes matter and a good example is the Gimp that still undergoes meaningful and useful changes. Changes that make drawing or editing easier. You didn't ask these changes but you are glad they came. 

Lastly, and also very important are updates for security reasons. Browsers change monthly but then again there is always a new flaw.  Actually kernel updates may also be in this category, but not always because it's also a question of new hardware and an existing system doesn't need that.

So the problem is more that one doesn't know in what category an upgrade is situated but except for the first I'm happy with changes that improve my system or make it safer.

---

### Post by mörgæs on 2019-03-28
People who question the reason behind security updates should take a look here:
[https://usn.ubuntu.com/](https://usn.ubuntu.com/)

Reading just a month's worth of security notes should make you want to update everything, every time.  

If people want to stick to the familiar look and feel (and I certainly understand that) there are still distros like Lubuntu where security bugs are fixed but most everything else is kept as it is.

---

### Post by mastablasta on 2019-03-29
security patches themselves are usually not an issue. 

much bigger problem (for the user) are various "feature upgrades". they can improve the user experience or make it worse. sometimes it is just different. but the issue is when they change the experience to such a point that the original features of the app are actually no longer accessible or no longer work. 

eg replacing menu interface with ribbon is not necessary and can at best cause minor annoyance or not. depending on the workflow of individual. a much bigger issue is if you suddenly can't open the old files.

or having a Unity interface or not is not that important as long as you can continue to run the apps on the OS of choice.

---

### Post by dacha on 2019-03-29
The source of all these security updates is simple: developers use too much C/C++. Studies have consistently found that something like 70% of all security issues were due to memory bugs. In my professional and personal software development, I have favoured high-level memory-safe garbage collected languages whenever possible for the last 15 years: Java, C#, Node.js, bash, Python, Go, etc. which are not only safer and more secure, but faster and far more pleasant to develop in. Yet other software developers seem to live in denial of the problem. These days you have Rust, which is pretty much on par with C in terms of performance, yet much more secure. Adoption? Minimal.

As for the many updates that add new features, again, I think it's developer culture, as well as the gap between development and packaging that Linux distros introduce.

There is no fundamental reason that makes large frequent updates necessary. Secure languages could minimize security updates, and a stable branch could be maintained and new features added only occasionally. Updates could also use binary delta compression to greatly save space and speed up download times, and a good concurrent package database with fast indexes instead of the ultra-slow file-locked setup used by Apt. Wasn't there a Slashdot article recently about how outdated and buggy Debian's build system is?

---

### Post by QIII on 2019-03-29
70% of bugs related to memory?  How many bugs per 100k lines of code in each language?  Without that, any conclusion drawn about a particular language is void.

I own a software company.  While we use a number of languages and use Microsoft technology, including C#, quite a bit, I will say from my experience that languages with GC often result in sloppy, careless code because people get used to the babysitting.

High-level languages are great for on-time deliverables.  Not so great for elegant and efficient solutions.

---

### Post by thenailedone on 2019-03-29
Show me the new stuff (and tomorrow's stuff now!)

---

### Post by dacha on 2019-03-29
> **QIII said:**
> 70% of bugs related to memory?  How many bugs per 100k lines of code in each language?  Without that, any conclusion drawn about a particular language is void.

Here are some of those articles:
[https://it.slashdot.org/story/19/02/11/2019247/microsoft-70-percent-of-all-security-bugs-are-memory-safety-issues](https://it.slashdot.org/story/19/02/11/2019247/microsoft-70-percent-of-all-security-bugs-are-memory-safety-issues)
[https://motherboard.vice.com/en_us/article/a3mgxb/the-internet-has-a-huge-cc-problem-and-developers-dont-want-to-deal-with-it](https://motherboard.vice.com/en_us/article/a3mgxb/the-internet-has-a-huge-cc-problem-and-developers-dont-want-to-deal-with-it)

> **QIII said:**
>  High-level languages are great for on-time deliverables. Not so great for elegant and efficient solutions. 

The state of the art in C/C++ development is anything but elegant and efficient. Compared to say Java, compilers are still full of quirks, linker errors are a nightmare to solve, build time is horrendous, debugging painful, cross platform binary portability nonexistent, tooling/factoring relatively poor, and they require constant maintenance (eg. porting to x64/ARM, building with new versions of compilers and operating systems, security updates).

In my experience, when people have good experiences with C/C++ projects, those projects are either small or new.

---

### Post by QIII on 2019-03-29
First citation:  > Around 70 percent of all the vulnerabilities in **Microsoft products **  The emphasis is mine.

As for your second citation, it still does not relate bugs per line of code -- thus it cannot be used to compare C/C++ to other languages.  Lacking that, one cannot draw a conclusion about whether it is the developer or the language that is at fault.  Is a vulnerability more or less likely per 100k lines of code than Foobar++?

> In my experience, when people have good experiences with C/C++ projects, those projects are either small or new.

Like Linux?  Your experience is a sample size of one.  Although we humans are all tempted to do so, making hasty generalizations does not often lead to valid conclusions.

The vulnerabilities of C/C++ are quite well known and those who write and review code should know well enough to watch for them.  I agree that this should be rectified.  I would not be unhappy to see a new C++ revision specifically for that purpose.

Java is "safe" (stack corruption, pointers and buffer overflow are not an issue) but it is not necessarily more "secure".  Safety and security are different concepts in the context of software.  While we believe right now that the JVM sandbox escape issue we learned about so disasterously in the October of Java Horror is fixed, we don't know what the next vulnerability might be because of the whole notion of the JVM.  Is it secure?  Would you provide a guarantee to your customers that it is?

Don't get me wrong.  C# and Java are where the good money is made these days and I am a businessman.  So that's where I go.  I'm neither extolling the virtues of any particular language nor disparaging any.  I think most of the "Foobar is a terrible language" is a bit of unnecessary brand loyalty that lends itself very well to partial "proofs" that are neither fully factual nor defensible by rigorous logical exercise.

The language, be it Foobar++ or another, is not really a factor in the "Keep Everything Upgraded" cycle.  That would happen anyway as independent developers worked to get new functionality out, fix security issues that can plague any software written in any language, and respond to user trends and demands.  The Wild West that is the Open Source Community is not going to magically agree on a policy of scheduled releases of all versions across the board on the second Tuesday of each sixth week of every thirteenth month of every leap year.

THAT is the source of the constant upgrade cycle.  If we don't like it, we need to petition the community to schedule all releases on my wedding anniversary just because it's a date I remember.

---

### Post by SagaciousKJB on 2019-03-30
> **mörgæs said:**
> People who question the reason behind security updates should take a look here:
[https://usn.ubuntu.com/](https://usn.ubuntu.com/)


I think security researchers and software developers in particular seem to have a great imagination when it comes to determining what bugs are actually imminently dangerous--they have to in order to find them.  Most of those bugs have probably gone on unexploited and undiscovered until they were found by a researcher in source, not by a hacker exploiting their binaries.  There have been cases of serious privilege-escalation bugs existing in kernel sources for decades without ever being exploited before they were found.  I'm not saying a user shouldn't upgrade to better security whenever possible, but there seems to be this impression that such security problems are just imminent attacks waiting to happen, when in reality that's a pretty big stretch.  If a user assumes that every security related patch is more important than productivity, they're going to spend a lot of time updating and re-configuring their system versus actually using it.

It's not often the security updates that break things, anyway.  They typically arrive in back ports that are compatible with current versions of installed software and so don't break or change anything at an interface level.  The ability to fix flaws and problems while maintaining the user's working experience is obviously there, but it seems like a lot of the times developers just want users to play guinea pig to try out new features, or they adopt new ways of doing things for reasons that seem great to the developers, but pay no dividends to the users who have to re-learn how to configure a system they've been maintaining the same way for years. The latter is the type of upgrade which I despise.  If I could come up with my own quip, I'd say progress is the bane of productivity.

I think it would be great if more developers had kind of a "guiding hand" into the new.  For example, the ffmpeg project has been trying to transition to avconv for years, but they didn't just leave older ffmpeg users high and dry by changing the interface and leaving them to figure it out.  Instead they support the legacy ffmpeg syntax while gently reminding of the new avconv way.  On the other hand, avconc adoption is still dragging way behind ffmpeg use, so I have to wonder if most software writers are prioritizing adoption rates over usability.

---

### Post by mastablasta on 2019-04-01
> **SagaciousKJB said:**
>  I'm not saying a user shouldn't upgrade to better security whenever possible, but there seems to be this impression that such security problems are just imminent attacks waiting to happen, when in reality that's a pretty big stretch.  If a user assumes that every security related patch is more important than productivity, they're going to spend a lot of time updating and re-configuring their system versus actually using it.


my server (hosted) got hacked due to this way of thinking:
[LIST]
[*]security issue went public on Thursday
[*]patch was out on Friday, but i decided to perform updates on Saturday.
[*]I actually did the updated on Sunday morning, because i had a few errands on Saturday.
[/LIST]

about two weeks later i got a notice form host saying they closed access to my server due to spamming of others. i immediately requested backups to be restored. but it turns out the server was hacked on Saturday or Friday evening, since the two weeks backups they had were also infected.

so when the bug report (security hole) was out, the server got hacked and infected with malware in two days. took me another two weeks to restore it from my old personal backups. i learned my lesson, installed security software and created my own automated backups. also i learned to uninstall any service i wasn't using, because ironically the server got hacked though a plugin i had installed but was not using it.

---

### Post by monkeybrain20122 on 2019-04-01
> **mastablasta said:**
> security patches themselves are usually not an issue. 

much bigger problem (for the user) are various "feature upgrades". they can improve the user experience or make it worse..


But there is no feature upgrades in Ubuntu unless you go out of your way to get them (e.g ppa, snap or flatpak) I think the biggest insanity is that you have to upgrade the OS just to get a few up to date software. Upgrading the OS is more risky than anything you can do by installing "unstable" software (esp if it doesn't involve system components), since the worst that can happen is you have to resinstall the OS, but that is exactly what you are doing already if you upgrade your OS (on the other note: "upgrade" is usually more problematic than clean install, but that is another topic)

One time an xorg upgrade from official channel  almost killed my system. Ironically it was a "bug fix" that introduced more bugs, I ended up having to upgrade to an "untrusted" version from a ppa to restore my system. Go figure.

---

### Post by mastablasta on 2019-04-02
> **monkeybrain20122 said:**
> But there is no feature upgrades in Ubuntu unless you go out of your way to get them (e.g ppa, snap or flatpak) I think the biggest insanity is that you have to upgrade the OS just to get a few up to date software. Upgrading the OS is more risky than anything you can do by installing "unstable" software (esp if it doesn't involve system components), since the worst that can happen is you have to resinstall the OS, but that is exactly what you are doing already if you upgrade your OS (on the other note: "upgrade" is usually more problematic than clean install, but that is another topic)

One time an xorg upgrade from official channel  almost killed my system. Ironically it was a "bug fix" that introduced more bugs, I ended up having to upgrade to an "untrusted" version from a ppa to restore my system. Go figure.


actually there are plenty feature upgrades and fixes, that are not security patches. especially in the beginning of LTS. 

i had have security patches done automatically on server and for feature patches i get a notice on email. once i get that i run the update. at this point it will give me a short release note i can read and then decide to patch or not. there was plenty of these notes in beginning. so i know there are feature upgrades. you might not see them but they are there. even for non gui apps and various drivers.

system upgrade is a whole other beast. they should be less frequent and they should really be smooth. unfortunately Kubuntu lost Cannonical support so now it has 3 year cycle for LTS and also upgrade from 14.04 to 16.04 is still broken after all these years. these upgrades are really desctructive.

for those on longer LTS scheme, snaps should solve the issue.

---

