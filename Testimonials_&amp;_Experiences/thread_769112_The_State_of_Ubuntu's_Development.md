---
title: "The State of Ubuntu's Development"
date: 2008-04-26
forum: Testimonials &amp; Experiences
---

### Post by Luke has no name on 2008-04-26
Note: The term “bug” will be referred to as “error”. “Distro” and “OS” will be interchangeable. See Note(1).

*Introduction*
	Ubuntu is in the top tier of Linux distributions. Even since I started using it (6.10), a great amount of progress has been made on improving its usability and compatibility with hardware. These are important steps in allowing it to become a  mainstream workstation and server operating system. That said, the development team at Ubuntu should consider a permanent change in its development process as a way to manage its troubles with stability and error regression.

*Regression*
	Ubuntu will not be adopted as a desktop OS by end-users or businesses if they have to be consistently concerned that the product has debilitating errors. Even more so, they do not want to have to worry that a new version of the OS will have errors in programs that were stable in previous releases! See Note(2) for an informative post that makes my point. Attention needs to be paid that things DO NOT get broken that were working perfectly before! 

*Stability in software*
	Why is it that 8.04 “LTS” has such a wave of new features and new versions of software that have not been time-tested to be stable? LTS releases (meant to be exceptionally stable) should not have so many additions to its feature set. 
	For example, Firefox 3 is BETA! One of the most used programs in the distro is in the “stable” release in a relatively untested, thus unstable, state. Yes, Firefox 2 has its problems, but none that are critical or unknown. It has been time tested.	“Beta” should be nowhere in a stable release.
	OpenOffice.org 2.4 has what should be considered a critical error, where its Hebrew version displays Arabic numbers instead of decimal numbers (See Note(3) for link). Imagine the English version showing base 10 numbers half the time, base 8 the other half. Wouldn't that be a deal breaker for many users of OOo, and thus many new users of Ubuntu? That is exactly what this could be to many Hebrew users. Again, in an LTS release, OpenOffice 2.3.1 should have been used. New versions don't always mean better versions. 
	Finally, see Note(2) again for other examples of what should NOT happen in 8.04.

*Considerations for an LTS*
	One idea to prevent such a rush of higher version numbers and new gadgets from breaking a distro is to use a “STS” release as an LTS. For example, Freeze the software versions in 7.10 for use in 8.04, and work on fixing every error reported in those 6 months before the LTS release. This would allow the “beta” of the LTS to be based on an official release, with the testing and feedback of every user of the OS.  This would next apply to the 9.04 release, in preparation for the 9.10 LTS (assuming Ubuntu keeps its 6-18 month dev cycle).
	This solution may seem extreme for a distribution on the “bleeding edge”, but if Ubuntu plans to get respect in the mainstream, a balance must be found between development and stability. Currently, that balance is too far toward the former.

*Conclusion*
	Ubuntu must stop insisting on being on the bleeding edge of features and software if they want to have a “low-error” operating system. This applies even more so for LTS, and this paper is directed toward my disappointment in the QC of this LTS release. Let us briefly review my points, as they apply to any “stable” release of Ubuntu:

--Regression is unacceptable. Care should be taken that software updates and new features do not break existing functions that were stable previously.

--New software should not be included simply because it is new, quite the opposite: new software should rarely included. Firefox beta and OOo 2.4 are notable examples.

--Serious debate should take place as to how LTS releases are developed (same as normal ones, or as “error-fixed” previous releases).

I hope those in charge of Ubuntu's development take notice of these concerns. I took the time to write this paper (Yes, I wrote it on paper first) for two reasons: my respect for Ubuntu as possibly the easiest and most functional Linux OS in existence, and my sincere worry that if changes are not made in Ubuntu's development process and quality control, this terrific effort will continue to be riddled with errors, and growth of the userbase will be stifled for years.

Update (5/01/08): *Alternate ending* -  For many users, 8.04 might work without trouble. "Many" should not cut it in a release of this caliber. I believe I speak for many jaded Linux users around the net: Please devote more resources to error-correction, and for the moment, devote less time to rapid feature development. I know there will always be errors in code; I do not expect every program to pass a Hoare-logic test. Let us be reasonable, and get things working correctly, shall we?

*Notes:*
1): “Bug” does not convey the same sense of urgency that “error” does. A broken package didn't get infested with roaches, a programmer did not write correct code. Also, while Ubuntu is a distribution of Linux, it is as complete an operating system as Windows or Mac, and is thus an OS.

2)Regressions in Hardy: [http://beranger.org/index.php?page=diary&2008/04/25/08/30/01-ubuntu-8-04-quot-oliver-hardy-qu](http://beranger.org/index.php?page=diary&2008/04/25/08/30/01-ubuntu-8-04-quot-oliver-hardy-qu) This link has tons of useful information, and some links to people discussing similar points of view.

3)OpenOffice.org Hebrew debacle: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/210204](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/210204)


4) (5/01/08): I want to acknowledge that my assumption of "LTS" being synonymous with "stable" is just that: an assumption. It is my belief that someone who demands support for 3 years on the same set of software is the same person who is looking for a particularly reliable environment.

**My personal issues**:In beta, I was not able to get Atheros wifi drivers working (wrapper or native). In stable: Using an ATI 3870 with binary drivers, I cannot use Compiz and play games at the same time; Compiz (non-stable software) breaks my game window. Currently, I cannot get my mic to work on my Realtek ALC882 device. Wine is giving me a lot of trouble, but I cannot fault Ubuntu for that.

---

### Post by Luke has no name on 2008-04-30
Really? No one has anything to say?

After using the distro for several days now, I have found several errors. It does not detect my mic, but it does detect my headphones. In GNOME only, I get weird glitches in full screen gaming, doesn't happen in XFCE / Fluxbox. Counter-Strike: Source will not start, as it should in Wine.

I have had a relatively smooth experience, but these are important errors.

---

### Post by MONODA on 2008-04-30
i agree that ubuntu is implementing new features too quickly and not telling the user that these are still being tested. The best example of this is compiz Fusion, it was included by default and turned on in both gutsy and hardy and is still ALPHA software and is what causes most problems posted on this forum. Ubuntu should go rolling release, it would be much easier than having to reinstall the newest version every 6  months to be able to get the new version of software. They should also be more careful in what they package with it, firefox 3 beta should not have been the default browser, it should have been epiphany or something else like that.

---

### Post by Riffer on 2008-04-30
Sorry disagree.  Every OS has growing pains with new releases in which some users experience problems.  Also every Distro has its own personality, like Debian is noted for being rock solid but behind in new features and apps. 

Ubuntu "flavour" is for being solid and having some cutting edge features, and because of that you must accept that some apps or features may not work well (or not at all) for you.  If you don't want to accept how Ubuntu does things, then perhaps another Distro would serve you better.

And yes I have had issues, FF3 kept freezing on me so I removed it and reinstalled FF2.  Other then that Hardy has been quite the enjoyable experience for me.

---

### Post by mozetti on 2008-04-30
Couple of issues with your conclusions.

LTS doesn't necessarily mean, rock solid stable. Long-Term Support is what it stands for, and what it means - 3 years of support instead of 18 months. It carries with it *additional* stabilization, polish, and translation (Ubuntu.com website). If you want rock solid stable, maybe Debian or Slack are for you. That being said, there appears to be some big issues with 8.04, to the point that I'm not upgrading yet.

You discuss the inclusion FF3 beta as a bad idea for the 8.04 LTS. But, if they are supporting it for 3 years, why would they include a browser (FF2) that is coming to the end of its life and won't receive security updates? Secondly, you say that FF3 is relatively untested (which isn't necessarily true on it's own), and is thus less stable. That's a logical fallacy - just because it's beta/less tested doesn't mean it's less stable.

You also say that if Ubuntu wants to get respect in the mainstream, it needs to balance between development and stability. Well, there's a valid point there but the bad news is your premise is flawed. Ubuntu *has* respect in the mainstream. So, if it's aleady gotten the respect on the merits of its current development and product then a change isn't necessarily warranted unless it would significantly increase its value.

Having said all that, thank you for the time and effort you've put into this. More importantly, thank you for caring enough about the distro that so many use to address some of the problems. If there's one thing I agree with you on, it's that regression is a major problem. It's something that bothered me since the first time I read one of the threads that talked about, "I upgraded to X.XX and now the <general use program> that worked on all previous versions is broken."

---

### Post by armandh on 2008-04-30
use some restraint
one does not have to install day one.
in fact if one waits until just B4 8.10 to install 8.4 = same result!
I have 3 machines running 8.04 beta or RC but the main one I am using now is 7.10 
none have problems I know of, but I did not consider 7.10 better than 7.4 until 3 months in 
[and a few areas it still isn't]
ANY ONE OF THEM BEATS VISTA

I edit to add 
until the ver. is released to the world at large not all the bugs will be discovered. 
its about 3 months from just released to just works

---

### Post by acl123 on 2008-04-30
I think the last two posts here underestimate the seriousness of some of the issues faced by users upgrading to Hardy - lockups of the worst kind that make the entire OS basically useless; numerous legacy but popular programs no longer working; the Firefox 3 fiasco, the main issue I see being that you either run FF3 without all your favorite extensions or you rollback to FF 2 and have to reinstall them all. These type of issues seem to be very wide spread (anecdotally).

---

### Post by mivo on 2008-04-30
> **acl123 said:**
> the main issue I see being that you either run FF3 without all your favorite extensions or you rollback to FF 2 and have to reinstall them all. These type of issues seem to be very wide spread (anecdotally).

"Anecdotally" meaning that only people who have a problem post about it? :) I run FF3 with the three extensions I need (Adblock Plus, Adblock Filterset.G Updater, Send to EidoGo) plus the Ubuntu one. It runs more stable than FF2, and is faster for me, at least so far. I haven't seen any high CPU usage or disk trashing  I am not saying that other people aren't having issues, since they quite obviously do, but it's not broken for everyone.

I do agree that a rolling release system would be very desirable, though. As it stands now, I just do a fresh install every six months (not too much trouble with a separate home partition) and do the usual tweaks. While that is no hassle for me, I'm not entirely sure if the same is true for Joe User that Ubuntu wants to appeal to. There should be easier ways to get the new version of Evolution than to reinstall the entire OS.

Then again, if we complain, we also need to ask ourselves what we contribute to Ubuntu. Are we always filing bug reports for problems we encounter? Do we contribute code, help, translations, artwork, or even money?

In terms of community and new-user-friendliness, Ubuntu is quite unmatched. Sure I get a little frustrated if something doesn't work right away, but few other distros come quite as full-featured and work so well out of the box.

---

### Post by Luke has no name on 2008-04-30
> **mozetti said:**
> Couple of issues with your conclusions.

LTS doesn't necessarily mean, rock solid stable. Long-Term Support is what it stands for, and what it means - 3 years of support instead of 18 months. It carries with it *additional* stabilization, polish, and translation (Ubuntu.com website). If you want rock solid stable, maybe Debian or Slack are for you. That being said, there appears to be some big issues with 8.04, to the point that I'm not upgrading yet.


I understand your point, and perhaps judgment on this LTS should be withheld until the first "service pack"/point release, 8.04.1. I believe that anyone who is looking for an OS with "long term support" would be the same person who is looking for a stable environment. 

I will also look more into Debian, as I have never tried that distro. Not to say that I don't know what it's "about", and I certainly know that much of Ubuntu is born out of Debian.

> **mozetti said:**
> 
You discuss the inclusion FF3 beta as a bad idea for the 8.04 LTS. But, if they are supporting it for 3 years, why would they include a browser (FF2) that is coming to the end of its life and won't receive security updates? Secondly, you say that FF3 is relatively untested (which isn't necessarily true on it's own), and is thus less stable. That's a logical fallacy - just because it's beta/less tested doesn't mean it's less stable.


The opposite is true, as well: just because something is new doesn't mean it's better. Again, I see your point that Firefox 2 will be obsolete soon, but doesn't FF2 have automatic updates that would notify a user of the need to upgrade?

I know FF2 has its problems. I have used Firefox since 0.9.3, and have seen its evolution. I know that FF2 is a memory hog, but beyond that I have not seen any major flaw in its stability. At present, everything may seem peaches and cream for FF3, but I'd rather have the rascal we know than the angel we don't. 

> **mozetti said:**
> 
You also say that if Ubuntu wants to get respect in the mainstream, it needs to balance between development and stability. Well, there's a valid point there but the bad news is your premise is flawed. Ubuntu *has* respect in the mainstream. So, if it's aleady gotten the respect on the merits of its current development and product then a change isn't necessarily warranted unless it would significantly increase its value.


Really? How many companies have migrated to Ubuntu desktop? How many schools? My Unix class next semester will be using Ubuntu, and that's about it. I love Ubuntu (as stated) and it is making great progress toward the ends of being on the same tier of popularity as Mac and Windows. That said, it's not going to be picked up until it shows maturity in code.

> **mozetti said:**
> 
Having said all that, thank you for the time and effort you've put into this. More importantly, thank you for caring enough about the distro that so many use to address some of the problems. If there's one thing I agree with you on, it's that regression is a major problem. It's something that bothered me since the first time I read one of the threads that talked about, "I upgraded to X.XX and now the <general use program> that worked on all previous versions is broken."

At least we agree on something!

[quote=mivo]
I do agree that a rolling release system would be very desirable, though. As it stands now, I just do a fresh install every six months (not too much trouble with a separate home partition) and do the usual tweaks. While that is no hassle for me, I'm not entirely sure if the same is true for Joe User that Ubuntu wants to appeal to. There should be easier ways to get the new version of Evolution than to reinstall the entire OS.

Then again, if we complain, we also need to ask ourselves what we contribute to Ubuntu. Are we always filing bug reports for problems we encounter? Do we contribute code, help, translations, artwork, or even money?

In terms of community and new-user-friendliness, Ubuntu is quite unmatched. Sure I get a little frustrated if something doesn't work right away, but few other distros come quite as full-featured and work so well out of the box.[/quote]

Ehh... Can't you update to new versions using the update mechanism? I was also under the impression that updates were done regularly as found. If I am wrong, and wikipedia's definition of "rolling release" is correct, then perhaps that would be something to take into consideration. Again, though, Ubuntu needs to prove itself stable and "regular", and might have a better time showing that by having a normal release schedule.

As for your following points, I agree. I have begun participating more in the QA area (filing reports, giving feedback) but I do not contribute money or code (yet). Ubuntu's community is terrific.

---

### Post by karellen on 2008-05-01
Luke has no name, you should send your ideas to Canonical, no on these forums
here, no matter what problem somebody has with Hardy (lockups, hardware not supported anymore and so) he'll get only "any OS has its flaws", "give it time/have patience until updates fix your problems", "you're such a whiner, it's free" and the list could go on. I refuse to accept any excuse and pseudo-explanations about regression, as there isn't any. if it works, don't break it. as simple as that

---

### Post by mivo on 2008-05-01
> **Luke has no name said:**
> Ehh... Can't you update to new versions using the update mechanism? I was also under the impression that updates were done regularly as found.

Yes and no. Ubuntu releases critical updates and crucial bug fixes for packages, but actual feature updates are rare. You'll almost always get the latest Firefox version, but you won't get a new version of Evolution or Pidgin unless it fixes a security problem or a significant stability issue. There are sites like getdeb.net where you can download more current packages, and some projects/teams release Ubuntu packages on their site too (like Deluge), but in general you get a new release (which includes thousands of applications in the respective repository) every six months that is then maintained and fixed.

A rolling release system, like used by Arch, always updates all of your applications, tools, system components as soon as they leave the "testing" stage. Arch, and similar distros, don't have actual "releases", since there is never a point where development is of a specific OS version is completed. They just occasionally release "snapshots" so that people who choose to newly run the distro don't have to download everything.

Both approaches have up and downsides.

Rolling release distros can break your system if you get something that your computer doesn't agree with. They are very bleeding edge and ideally, you should be able to fix small problems or incompatibilities yourself. The advantage is that in theory you never have to reinstall or do a major upgrade, because your system is always current. My other computer runs Arch and while it never broke since last year, there are sometimes small issues (like file conflicts) that need fixing by the user. My main work computer runs Ubuntu because I can't/don't want to run the risk that I wake up some morning, get the latest updates and then something breaks. With Ubuntu, I only have to set aside one or two day(s) twice a year to upgrade to a new version (without any pressure to do it right away). (I also love this community.)

A cyclical release has the advantage that the software is (largely) tested for compatibility with each other. So if you use Hardy and download something from the Hardy repository, you can be relatively sure that it works with everything else in Hardy. This is especially true for the parts of the actual Linux distro (the core stuff and system components). The downside is that applications aren't always the most current versions and that, if you want to stay somewhat current, you have to upgrade every x months when a new release comes out. That means either a clean install (which is made much easier by a separate /home partition) or a distro upgrade, which doesn't seem to work so well for apparently a substantial number of people. I believe the latter should be, and possibly is, one of the priorities for the Ubuntu development team. (Hardy made progress in this area.)

---

### Post by agim on 2008-05-01
If it ain't broke don't fix it. If we were all that courageous, we would probably still live in caves.
They have a bunch of new/beta software (firefox 3) BECAUSE its a long term release. Using firefox 2 in 30 months would be ridiculous, so they put it in the new release, knowing that it will grow more stable while not losing its relevance.

And yes, please, report problems to the devs, that would be spectacular. The more quickly they could fix them.

---

### Post by SteveHoffmanUK on 2008-05-01
These are one noob's experience, someone who just wants a stable GUI-based computer life. I know, I shouldn't be here.:)

Have been using Ubuntu since Dapper and have installed each new version (>Edgy>Feisty>Gutsy) and agree with Luke that error regression is a really serious problem for Ubuntu. 

In Dapper my wireless card worked out of the box; somewhere along the line (Edgy, I think) it stopped working. So I had to go the ndiswrapper route. OK, so problem solved, but why did it regress?

Got fed up and tried PCLinuxOS: sweet, GUI-friendly stability-keen distro. It got me on-line painlessly, albeit with ndiswrapper; everything fine except that virtualbox borked my desktop (panel disappeared). Probably could have fixed that, but said, hey, Hardy has just been released, so I installed Hardy dual booted with XP. (I am a bit distro-promiscuous LOL).

Got through the ndiswrapper bit and online OK, but what's this? Now I can't get more than 800x600 screen res. With Gutsy, 1024x768 was no problem. So now another regression! I am searching the forum and learning about .xorg and other things that I didn't particularly want to learn about.

Point is, I am retired, have plenty of time to mess about, and always take backups before I mess about, so no harm done. It keeps me amused and gets the grey cells working. BUT, I have to conclude that Ubuntu is never going to be a reliable solution for enterprise use because you can't impose quality control on unpaid volunteers. Ubuntu is an amazing achievement, the developers, the Ubuntu community and this forum are superb, but QC just isn't there, and the error regression I have experienced proves it as far as I'm concerned.

---

### Post by armandh on 2008-05-01
> **acl123 said:**
> I think the last two posts here underestimate the seriousness of some of the issues faced by users upgrading to Hardy - lockups of the worst kind that make the entire OS basically useless; numerous legacy but popular programs no longer working; the Firefox 3 fiasco, the main issue I see being that you either run FF3 without all your favorite extensions or you rollback to FF 2 and have to reinstall them all. These type of issues seem to be very wide spread (anecdotally).


I am unqualified to even speculate as I never use the upgrade.
I have always done a fresh install. maybe this is a hangover from my win 3.1/95/98/xp upgrade experiences where all kinds of junk migrated. it sounds like similar grief.

---

### Post by chewearn on 2008-05-01
Let's be realistic and see from each other's perspective.  I quote Steve to illustrate a different point of view.  Hopefully, we get more action and less talk.

> **SteveHoffmanUK said:**
> Have been using Ubuntu since Dapper and have installed each new version (>Edgy>Feisty>Gutsy) and agree with Luke that error regression is a really serious problem for Ubuntu. 

In Dapper my wireless card worked out of the box; somewhere along the line (Edgy, I think) it stopped working. So I had to go the ndiswrapper route. OK, so problem solved, but why did it regress?
*...edit...*
Got through the ndiswrapper bit and online OK, but what's this? Now I can't get more than 800x600 screen res. With Gutsy, 1024x768 was no problem. So now another regression! I am searching the forum and learning about .xorg and other things that I didn't particularly want to learn about.

On one hand, regression is a big problem.  On the other hand, have you joined the ubuntu QC team to test your hardware?  If not, then who are you waiting for to test those hardware?  How are they going to ensure thing are working on hardware that they might not have?

If you can't find the time, then are you contributing cash for someone to do this for you?


> BUT, I have to conclude that Ubuntu is never going to be a reliable solution for enterprise use because you can't impose quality control on unpaid volunteers. Ubuntu is an amazing achievement, the developers, the Ubuntu community and this forum are superb, but QC just isn't there, and the error regression I have experienced proves it as far as I'm concerned.For enterprise, companies know to pay Canonical for support.  Your argument does not apply.

---

### Post by mivo on 2008-05-01
> **AstalaVista said:**
> On the other hand, have you joined the ubuntu QC team to test your hardware?  If not, then who are you waiting for to test those hardware? [...] If you can't find the time, then are you contributing cash for someone to do this for you?

I basically agree with your point, and said as much above, but there is one problem: The fact that Ubuntu is marketed as a new-user-friendly Linux system for the desktop that everyone without in-depth knowledge of hardware and software can use.

I'm pretty much torn on the issue, since on one hand I agree that Ubuntu is a community project, but on the other hand I understand that the target audience of Ubuntu does not have the knowledge, skill or, perhaps more importantly, the time and desire to take care of "fixing problems". 

It is of course a problem if your hardware is supported now and suddenly after the next upgrade it no longer works. Someone **did** change or remove the code that caused Steve's wireless to break after Dapper, and it was **that** person's responsibility to make sure that **their** change does not break something for other users. It wasn't Steve's task to do this because he couldn't even possibly know that his wireless would not work in the next release. It worked for him until a new version was released. It's not realistic to expect everyone to alpha and beta test new releases, and it's even recommended against by the Ubuntu team.

The issue is complex and there isn't a really good solution that works for everyone. Ubuntu wants to be seen as a "Linux distro for everyone", and yes, that means that it's necessary to put in extra effort and extra resources to address the needs of even those users who aren't interested in tweaking their OS and making basic functionality work. The devs of a distro like ArchLinux can expect that, because it's offered as an expert distro. Ubuntu isn't.

(And to be fair, Ubuntu succeeds at this goal more than any other Linux distro.)

---

### Post by chewearn on 2008-05-01
Ok, having re-read my post, I find myself sounding harsh, which was not my intention.

What I'm saying is this.  When things are not working for you, you can:

1. Test your hardware in alpha and beta release; make sure the developers know about your issue and help them solve it.

We must appreciate the difficulty of developers who have to reverse-engineer hardware, which came from companies who don't provide support for linux.  If the developers don't have a sample of the hardware in testing, they can unknowingly change things that will break it.  You can't blame them for this.


2. You can also say "meh" and accept that your hardware no longer works.  Next time, buy a hardware from companies that actively participate in linux development.


3. Revert back to the older distro version which works.  This might mean you get less of other things, like never better software.


4. Ask for assistance in forum nicely.  We are more than willing to help, if we got the means and knowledge.


5. Write a complaint to this forum, which incidentally, very few developers are actually participating in.

This last option, of course, serve very little purpose.

---

### Post by lhtown on 2008-05-01
Luke has no name,
I don't exactly agree with everything you are saying, but I do believe that Ubuntu as a project has some major problems.

The Hardy release has been Ubuntu's Vista. Ubuntu is still going strong, but it risks becoming irrelevant as time goes on.

After starting with Debian, I have been using Ubuntu since Warty and every release has been a significant improvement although gutsy wasn't quite what I expected. We were all expecting another Dapper with Hardy, and we didn't get it.

In my case, I have had data loss in two cases, (one of them just burning a CD) which I have never had before. Firefox 3 crashes very frequently, usability is still questionable with some simple things being left undone, my printer that configured easily with Gutsy didn't do it with Hardy. All of that with only a few days of use. Besides all that, it seems slower, particularly when copying files. On the bright side, it is pretty.

I have been a big fan of Ubuntu for a long time. With Gutsy, I had some misgivings, but with Hardy, I am off to find a new distribution. If we were talking about an LTS +1, I might be more understanding, but at this point, I am ready to try almost anything but Ubuntu. I hope the Ubuntu leadership gets it back on track.

It looks like I will settle on pclinuxos.

---

### Post by berlinbrown on 2008-05-02
It sucks.  The whole experience is degrading and people are praising Ubuntu as the second coming without even testing it.    That is what pisses me off, all of these editors trying to push it as some great operating system.

It is the worst, software experience I have ever had.  Even worse than DOS.  Win95?  Win98, no way.  I never had problems with Win98.

Gutsy was horrible.  Heron is unusable.  There are some things that I just ignore like my sound going off and on.  I gave up on that one.

Right now, I am lucky enough to post this article.  I am sure firefox will crash on me.

I know you guys have a tough job; this is a major undertaking, but it isn't the first tough job that has been conquered.  If we can send a person to the moon; I hope we can create an operating system where most of the core software isn't crap.

---

### Post by mivo on 2008-05-02
> **berlinbrown said:**
> Gutsy was horrible.  Heron is unusable.  There are some things that I just ignore like my sound going off and on.  I gave up on that one.

Well, the thing is, I used Gutsy every day for 12-14 hours, without problems (once I had it running, that is; there were issues with the latest Nvidia cards and my Abit motherboard), and I have used Hardy for a few days now, also without any crashes, freezes, data loss, etc. It performs well for me and is stable. I'm not saying that you are not having these troubles, because every new release seems to cause problems for some people (then again, it's no different with any other OS), but blanket statements like "it's unusable" are not justified. I mean, almost all of us here are not affiliated with Ubuntu. There's no company line to follow, so if we say it works for us, that can be believed. :)

As for your sound problems, try this: Go into *System -> Prefereces -> Sound*, and change "auto detect" to Alsa. This is likely to fix the problems. If you use VLC and still have sound issues, or only one application can use sound at the same time, see my post in [this thread]("http://ubuntuforums.org/showthread.php?t=776755"). It may also be necessary to uninstall PulseAudio, though I did not have to do that to address the sound stuttering.

---

### Post by berlinbrown on 2008-05-02
Thanks for the sound fix.  Actually, I didn't try that yet.

---

### Post by mivo on 2008-05-02
Let us know if it helped. My sound worked, but in VLC I got "clicking" noises when playing MP3s, which was, of course, rather undesirable. :) I also had the trouble that once my Java application used the sound device, other programs were muted. Using alsa-oss (aoss) fixed that. I'm not entirely sure why PulseAudio was included in Hardy, but at least it's easy to work around.

I think a lot of the problems we see are more related to Linux in general than to Ubuntu in particular. The advantage of a commecial OS is definitely that there is only one team (loosely spoken) that works on the OS, so that makes quality assurance much easier -- or at least better structured. Linux has countless cooks, and it's hard to coordinate everything and communication is bound to suffer. Then there's the issue with Windows-centric hardware and the closed binary drivers as well as the manufacturters' refusal to release at least proper documentation for their stuff. It's a bit of an uphill battle. Everything considered, Linux developers all over the world are doing a fantastic job, especially since there is usually no money involved.

I've tried quite a few distros, as I'm sure you did as well, and in the end I always conclude that Ubuntu is the best choice for me, in spite of the flaws. I also can't see myself going back to Windows. Not that I ever had any real trouble with it (used it since '91, I think, after six or seven years of CP/M and TOS/GEM), except when XP forced me to buy a new ISDN modem when it came out as there were no drivers for my old one, but I'd feel too restricted and "closed in". I like the Linux way of things. Macs are beautiful systems, especially the new iMacs, but I'd not want to tie myself to the hardware and OS from just one manufacturer. Choice is important.

---

### Post by Luke has no name on 2008-05-02
> **mivo said:**
> 

I think a lot of the problems we see are more related to Linux in general than to Ubuntu in particular. The advantage of a commecial OS is definitely that there is only one team (loosely spoken) that works on the OS, so that makes quality assurance much easier -- or at least better structured. Linux has countless cooks, and it's hard to coordinate everything and communication is bound to suffer. Then there's the issue with Windows-centric hardware and the closed binary drivers as well as the manufacturters' refusal to release at least proper documentation for their stuff. It's a bit of an uphill battle. Everything considered, Linux developers all over the world are doing a fantastic job, especially since there is usually no money involved.


Again, I understand, and appreciate the feedback. It is absolutely true that these are hard working people, and perhaps over the summer I will have time to truly contribute to the project. I don't want to bail on Ubuntu for having problems, I want to help find and fix them.

 As Ubuntu and any other distro is a collection of entirely separate software projects, I know it's tough to get them to interact flawlessly. That is why it is important to have an effective process of QC to make sure errors are found and dealt with, and that new software packages are not thrown in for the hell of it. (Pulseaudio?)

---

### Post by mivo on 2008-05-02
I read up a bit on PulseAudio in an attempt to understand why it was included. It actually makes sense to support it, especially in the long run, and simplifies things, also in the long run. I think I can see why they added it, though I agree that a LTS release is probably not the best version to change a larger system component in (considering that visual changes were pushed back to 8.10).

Some links of interest:
[Why you should care about PulseAudio]("http://www.linux.com/feature/119926")
[What's Cooking in PulseAudio's glitch-free Branch]("http://0pointer.de/blog/projects/pulse-glitch-free.html")
[Dreams of Audio Unity]("http://www.osnews.com/permalink?308961") (Karl's comment)

---

### Post by zoubidoo on 2008-05-06
Executive summary:
   Hardy Heron is still in beta.  Postpone upgrade.

As someone pointed out in an earlier post, LTS means long-term support.  I had misunderstood, I took it to mean "a rock-solid system suitable for professional use".  The current release is frankly still in beta stage.

I have been hit with a handful of regressions and have hardware that is no longer usable.

It seems that since Edgy the number of critical bugs found in each release has increased and stability has dropped.  Dapper was an excellent release.  From an outsider's point of view it seems that since Dapper there has been a change of leadership and development goals.

Hardy Heron may shine in a while, but I would recommend users wait a certain period before moving to Hardy while the *real* beta testing is done.

In the meantime, I have stopped recommending ubuntu to friends and family because of the embarrassment with all the problems.

---

### Post by Joeb454 on 2008-05-06
It's a shame you've had a poor Hardy experience - However I know of many people who have Hardy running perfectly (myself included) with little or no effort. And claim it is faster and more stable than any Ubuntu release they have tried.

Either way - you are not *forced* to upgrade. Ubuntu 7.04 is still supported until October, and Ubuntu 7.10 is supported until April 2009, what's stopping you using those releases?

---

### Post by zoubidoo on 2008-05-06
Much of the problem may be related to the LTS label.  I (and apparently many others) take it to mean stable.  Evidently we're wrong.

The upgrade from 7.10 was with the hope of getting rid of the bugs in that release.

So what is the ubuntu stable release?  Hardy certainly does not qualify.  If stability means old LTS releases then perhaps users like myself should go back to Dapper and we should be recommending Dapper to non-expert users.

Perhaps the stable release should be called **Ubuntu gold**
  [http://en.wikipedia.org/wiki/Software_release_life_cycle](http://en.wikipedia.org/wiki/Software_release_life_cycle)

---

### Post by Joeb454 on 2008-05-06
All releases are intended to be stable. LTS literally means "you get support for longer"

I've found Hardy to be very stable. If you prefer to use Gutsy (7.10) then go ahead :) I can totally understand why some people are. My server still runs Gutsy :)

---

### Post by karellen on 2008-05-06
if it's not stable, why release it?...:confused:
"still in beta" it's no excuse for something advertised to "just work"

---

### Post by 23meg on 2008-05-06
It's not an excuse; it's someone's opinion.

---

### Post by agim on 2008-05-06
Its so funny when people compliment ubuntu's usability and readiness, and then say that they should worry about stability first. 
They moved so fast because they are willing to take chances and be on the bleeding edge, if they worried only about stability now they would be usurped in a couple of years by the new bleeding edge desktop distro.

---

### Post by radtek on 2008-05-08
6.10 was rock solid. I didn't like 7.10 because it appears unstable and I got away from it as soon as I could. No end of the problems. But... 8.04 has worked very well... particularly on my lappy. Firefox3 beta and adblock causes problems- the same as in FF2 in 7.10. I'm very pleased with Hardy in anycase. No adblocky for the time being... Go team Ubuntu!

---

### Post by mivo on 2008-05-08
FF3 and AdblockPlus works fine for me in 8.04, but it also worked in 7.10 and FF2 for me. I couldn't surf the web without Adblock. ;)

---

### Post by randomnick on 2008-05-08
A picture says a thousand words....so here ya go:)

[IMG]http://i59.photobucket.com/albums/g306/staceychandler/castaway.jpg[/IMG]
My apologies to Richard, lol.

---

### Post by YokoZar on 2008-07-07
> **Luke has no name said:**
> Counter-Strike: Source will not start, as it should in Wine.

I have had a relatively smooth experience, but these are important errors.Did CS work for you in Gutsy?

I ask this because regressions are much bigger problems than normal bugs, especially normal bugs with upstream software.

That said, there's a good chance your issue has been fixed upstream anyway; have you tried Wine 1.0?  Wine 1.0 will (soon) be released through hardy-updates in much the same way as FireFox 3 final was when it came out.  See here for more: [http://ubuntuforums.org/showthread.php?t=852534](http://ubuntuforums.org/showthread.php?t=852534)

---

### Post by gmatht on 2008-07-07
> **karellen said:**
> I refuse to accept any excuse and pseudo-explanations about regression, as there isn't any. if it works, don't break it. as simple as that

If you really believe that then don't replace Gutsy with Hardy. Problem solved. Or you could use a distro that is founded on that principle, like Debian Stable...

However although Debian Stable has less regressions, I found it to have more bugs. Newer versions of software have lots of bug fixes, so you hold on to an old version because it kind of works and newer versions might break something, you'll miss out on a lot of bug fixes as well as new features.

But if avoiding regressions is that important to you Debian stable is definitely a option. The choice is yours.

---

### Post by stalkingwolf on 2008-07-08
This was the deal breaker for me.  
In 7.04 i get several choices for resolution settings including 1024x768 My choice, and a couple higher ones.

In 7.10 I get 3 choices with 1024 being the highest.

With the live CD of 8.04 I again get several among them
1024.  When installed however I get 2 choices 800x600 and
600x480.  

How in the name of Mary and Martha are you supposed to test
hardware when the results are different from the live media and the
installed (from the same media)version?

---

### Post by mdsmedia on 2008-07-08
> **karellen said:**
> if it's not stable, why release it?...:confused:
"still in beta" it's no excuse for something advertised to "just work"So, Vista should never have been released? I could agree there, but then, XP was growing very long in the tooth.

How the h*** do you know it's 100% stable until people have tried it with every known piece of hardware? All the recommendations to wait until it's stable and there are no bugs mean that if YOUR hardware hasn't been tried, you may still experience bugs.

If you want 100% stable, why use Ubuntu? Because you want to use the latest packages which don't come with guaranteed stable releases.

As for why Firefox 3 was used instead of 2, apart from support for 2 being on its last legs at Mozilla, FF3 was very close to final release when Hardy was released. Ubuntu, by policy, does not release new versions when they are released by the developers. I'm still using 1.5.x.x in Dapper. What would you rather? Have 2.x released with Hardy and supported for 3 years, or have the much awaited FF3 included and supported for 3 years in Hardy?

LTS does not mean "based on Debian Stable" so don't expect it to be 100% stable. It's very stable for most users. There are problems, but Hardy will still be supported for 3 years.

Rolling releases work with other distros. If you like that idea, use another distro. Ubuntu's policy is not to release rolling updates. The software that comes with the release will be supported through the life of the release. I won't offer an opinion on that except that it's Ubuntu's policy. It's a compromise between stability and cutting edge. If you want cutting edge, use a distro which offers cutting edge, but don't expect stability. if you want stability, use a distro which offers stability, but don't expect cutting edge. If you don't like the 6 month release cycle, use the 12 month old release.

---

### Post by SteveHoffmanUK on 2008-07-08
Sorry to say that regression caused me to abandon Ubuntu in favour of PCLinuxOS Gnome, which follows a rolling philosophy and which, for most people's equipment, "just works". However, I have noted one version regression with it as well - my particular wireless PCI card was not recognised in its most recent release but was in an earlier one.

So no distro is immune from regression, it seems, and therefore mdsmedia's advice is realistic and practical. In effect it's "different strokes for different folks". Don't expect perfection because even Linux is an imperfect world. I ditched Ubuntu for something that works for me now, but that doesn't mean that I won't try it again later.

---

### Post by stalkingwolf on 2008-07-11
Ok I just got a Compaq nc8000.  After several hours of fighting
with windows errors, I was going to dual boot because I need
IE at work. I said to hell with it.

I slapped in the 8.04 livecd.  Everything seems to work even the
internal wifi!,and ati graphics card.

1 hour later it is installed , all my addons except ies4linux
are working.  I'm good.
An hour later Ies4linux still wont work. hell with it. I installed
safari in wine 10 min. its working.  20 min. of tweaking my selected JLH picture and Jennifer Love Hewitt now resides on 
my desktop.  I'm really good now.  And my work laptop is windows free!!!!!

still working on the desktop thing.

---

