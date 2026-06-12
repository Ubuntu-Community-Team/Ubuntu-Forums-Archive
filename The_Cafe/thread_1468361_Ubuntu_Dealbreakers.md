---
title: "Ubuntu Dealbreakers?"
date: 2010-05-01
forum: The Cafe
---

### Post by Johnsie on 2010-05-01
What are the most common dealbreakers with Ubuntu that make people not want to adopt and how can they be resolved? Please don't post anything without suggesting show it could be resolved. I would like this topic to remain postive.


I'll start with my dealbreaker:

I want msn webcam support so I can talk with my windows friends and business contacts without having to make them switch software:
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/333675](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/333675)

I've tried amsn and found it too buggy for this purpose.



I think this can be solved by more work being put into resolving bug 333675. The next version of Ubuntu is supposed to be social so I think it make sense to work on this issue.


UPDATE: I resolved the issue on my desktops using VirtualBox in seemless mode:

[IMG]http://steeky.com/john/images/ss2.png[/IMG]

This runs without affecting the perfomance of my desktop but I think it would be a bit laggy on my netbook

I can start 'Windows' by clicking a launcher that executes the following command:

> 
VBoxManage startvm WindowsXP


(My Virtual Machine is called WindowsXP)

---

### Post by DrMelon on 2010-05-01
Emesene and Pidgin have MSN webcam support - at least, I think Pidgin does. And it works just fine.

---

### Post by jetsam on 2010-05-01
Most people run into blockades when they find some piece of software that they need but can't duplicate the functionality of without extreme effort.

There's big gaps in the software landscape; no filemaker equivalent (in ease of use and functionality), no fully working 3d cad package that can supplant autocad.  Industry standards are hard to shift; Adobe has a lock on graphic design and image processing that's only just beginning to budge.

All that is being worked on, but for people who need to get the job done, the best workaround is usually just to dual boot, or use wine or crossover, or a vm, or pay the price in learning curve to work around what they think proprietary package x has that the oss equivalent lacks.

The software lock affects specialized fields the most.  The exception is the database gap, and there are options available for that.  In terms of the average home and office, linux is already there, and I'm beginning to suspect everyone should have it in front of their TV soon...  Not that they will, but that they would benefit from it.

Most of this stuff just takes time and effort and patience.  For each household, the year of the linux desktop is whatever year someone in the home boots up linux for the first time.

---

### Post by Johnsie on 2010-05-01
I have the latest version of pdigin and the is no cam support in that that I can see. I'm looking at emesene now and it seems a little more promising... at least the icons for cam are there. Thanks for the suggestion :-)

With regard to the above post, I think adobes power days are numbered. They will continue to exist as a company, but I dont think the big two will let them continue the way they have done with flash. Adobe are now being forced to focus on Android and other forms of Linux which might actually be good for Linux... They will of course need to open up their technology though.

I guess the closed-source world is starting to implode on itself :-)

---

### Post by Johnsie on 2010-05-01
Nope the video option on Emesene didn't work either. That's sad because it looked quite promising. I hope they get it working someday. That's the only thing stopping me from using Ubuntu all the time.

---

### Post by cariboo on 2010-05-01
Does your web cam work when using cheese?

---

### Post by jkxx on 2010-05-01
The current state of the X server shipping with 10.04. Basically, you run a 3D game through wine and it will crash, provided proprietary drivers (Nvidia in this case) are installed.

Personally I'd rather hack apps in wine through desktop emulation than boot windows just to play a game but it looks really bad for someone trying to give it a spin and being greeted with an X crash.

---

### Post by Steven_S on 2010-05-01
For me personally: 

- Problems to get folder access going in a mixed Ubuntu / Windows environment (you basically need to understand samba, permissions and mounting settings; I'm still figuring that out). 

- OpenOffice and some issues I have with it - I'm talking about printing options and quality. 

- Nautilus. I simply find it very unpractical not to have a dual-pane file manager.

- Some Windows software I need and can't use (I dual-boot as a solution). 

- Grub. 

- Restricted formats and fonts. Can't they just ask you about that upon installation, or in some kind of "getting started" interface one could go through?

I'm sure I can think of some other stuff :-)

Let's face it, it all takes searching and fiddling. Sure, Windows does too (I had forgotten how empty a fresh install of XP is), but I think I got a bit too many expectations from this whole "for humans" and "easy" thing.

---

### Post by Viva on 2010-05-01
> **Steven_S said:**
> For me personally: 

- Problems to get folder access going in a mixed Ubuntu / Windows environment (you basically need to understand samba, permissions and mounting settings; I'm still figuring that out). 

- OpenOffice and some issues I have with it - I'm talking about printing options and quality. 

- Nautilus. I simply find it very unpractical not to have a dual-pane file manager.

- Some Windows software I need and can't use (I dual-boot as a solution). 

- Grub. 

- Restricted formats and fonts. Can't they just ask you about that upon installation, or in some kind of "getting started" interface one could go through?

I'm sure I can think of some other stuff :-)

Let's face it, it all takes searching and fiddling. Sure, Windows does too (I had forgotten how empty a fresh install of XP is), but I think I got a bit too many expectations from this whole "for humans" and "easy" thing.

Nautilus does have an optional extra pane in lucid, if that is what you're looking for.

---

### Post by toupeiro on 2010-05-01
As I predicted, the biggest frustration by users I've supported or turned on to ubuntu (over 50 people) are:

1) They greatly dislike the change of menu buttons at the top of a menu.

2) They all think removing gimp to make room on a CD for broken applications like gwibber was a bad exchange.

So, this release has created more support issues for me than ALL other releases of ubuntu combined. I know a lot of people like it, from a support standpoint, I'm disappointed.

I've already replaced ubuntu with windows 7 in 2 occasions.  I'm not going to force someone to stay on an OS they don't like.  If other people who support ubuntu on peoples computers are experiencing these things, they NEED TO MAKE THEM KNOWN.  I'm less inclined to recommend ubuntu to a windows user wanting something different with this release.  For anyone who hasn't upgraded, I've had to put up some pretty significant "warnings" to people who wanted fresh installs on just how different this release is.  Differences, imo, that should have been disclosed better by the developers.

---

### Post by MrNatewood on 2010-05-01
The no. 1 issue without a doubt is Applications.

Microsoft Office 2007, Adobe Photoshop CS, AutoCAD and games.

Anyone I showed ubuntu to liked it a a lot but most people can't do without one of the above.

The day .deb Are released for those apps and given the buzz that steam is coming to linux, Ubuntu usage share would skyrocket. Unfortunately, that is the same day pigs will land on Pluto.

---

### Post by kernelles on 2010-05-01
I'm new to Ubuntu and one issue for me is the fact that all my music is on an ipod that I can no longer synchronize or download from.

I'd like to see a future version of Rythmbox come ready to do this out of the box.

---

### Post by sixthwheel on 2010-05-01
> They all think removing gimp to make room on a CD for broken applications like gwibber was a bad exchange.
I just checked, and Gimp is still in Lucid applications.

---

### Post by cmwatford on 2010-05-01
> **kernelles said:**
> I'm new to Ubuntu and one issue for me is the fact that all my music is on an ipod that I can no longer synchronize or download from.

I'd like to see a future version of Rythmbox come ready to do this out of the box.
There's an app that allows you to sync your linux box with an ipod. It's called GTKPod.

---

### Post by walker98t on 2010-05-01
A deal breaker for one person may be only a minor annoyance to someone else.

The old brown/orange theme wasn't very attractive and the new purple is really obnoxious... gag-reflex inducing, actually... but it's a simple task to change themes and colors, so I it shouldn't even come close to "deal breaker".

Pulse Audio almost reaches deal breaker status, but 30 minutes yanking it out by the roots and 45 minutes installing ALSA, and I can have functional sound.

Instant messaging text/audio/cam... what a mess. One app will let you do A but not B; one will let you do B, but not A or C, and it's always a crap shoot whether your cam will work or not. Solution, short of having multiple chat programs installed? I haven't got a clue, but I thought the much heralded Empathy was supposed to solve all those issues. I know it takes time, but was it all just hype? Like Pulse Audio?

I know you wanted to keep this thread positive, so just let me say that Linux is my OS of choice, hands down, and Ubuntu is the best general purpose distribution I have found. For me, no deal breakers, just minor trials and frustrations.

---

### Post by MrNatewood on 2010-05-12
The lack of a proper Task Manager like in windows.

Now if you are in fullscreen and a game hangs you are left without much to do. Killing a process from TTY actually has *lower* success rates than Task Manager in windows, some apps sometimes just won't die, certainly not the case in windows. not to mention it is much less user-friendly to do from TTY(have to enter username and password just to kill a process).

---

### Post by earthpigg on 2010-05-12
> **MrNatewood said:**
> The lack of a proper Task Manager like in windows.

Now if you are in fullscreen and a game hangs you are left without much to do. Killing a process from TTY actually has *lower* success rates than Task Manager in windows, some apps sometimes just won't die

for example?

---

### Post by Mike BFD on 2010-05-12
> **walker98t said:**
> ...For me, no deal breakers, just minor trials and frustrations.
Same here.

Talking about CAD apps, Adobe graphics etc., we shouldn't forget they are used "at their most" only by professionals (guys who earn money for what they do with the apps). 

My vision is, Adobe (for example) still don't have Linux versions not because it just doesn't want to, but stupidly because Adobe guys don't know how to keep the software "strictly licensed" in Linux. They make apps for professionals making money on graphic works. Why should such apps be free?!
"Limited" usage of Adobe progs (of not the freshest versions) is, however, possible via Wine.

As to "common software" which may be used in literally any household or office, it's imo represented pretty well in Ubuntu (and other Linux distros as well).

---

### Post by smellyman on 2010-05-12
Fear of the unknown
 
Most people I know just use internet, email, skype etc.  An occasional document once in a blue moon.
 
Nothing would be a deal breaker.

---

### Post by everytimeref on 2010-05-12
I do wonder how many people who claim that they need photoshop actually **paid** for it.

---

### Post by NCLI on 2010-05-12
> **toupeiro said:**
> As I predicted, the biggest frustration by users I've supported or turned on to ubuntu (over 50 people) are:

1) They greatly dislike the change of menu buttons at the top of a menu.

2) They all think removing gimp to make room on a CD for broken applications like gwibber was a bad exchange.

So, this release has created more support issues for me than ALL other releases of ubuntu combined. I know a lot of people like it, from a support standpoint, I'm disappointed.

I've already replaced ubuntu with windows 7 in 2 occasions.  I'm not going to force someone to stay on an OS they don't like.  If other people who support ubuntu on peoples computers are experiencing these things, they NEED TO MAKE THEM KNOWN.  I'm less inclined to recommend ubuntu to a windows user wanting something different with this release.  For anyone who hasn't upgraded, I've had to put up some pretty significant "warnings" to people who wanted fresh installs on just how different this release is.  Differences, imo, that should have been disclosed better by the developers.

I usually respect posts like these, but your reasons for removing Ubuntu in favor of Windows are, in this case, completely ridiculous. 

1) You can change to any other theme in the Appearance menu to get rid of this "issue". A five second job, at most.

2) GIMP is till in the repos(And it wasn't removed to make space, that's a common misconception. It was removed because it didn't fit with Ubuntu's policy of having easy-to-use apps installed by default), and installing it is also a five second job, especially with the USC.

1+1=1?) Just use remastersys to remove Ambiance, Radiance and Gwibber, add GIMP, and you have a custom LiveCD to install for your users! 
Problem solved, next. :popcorn:

---

### Post by MrNatewood on 2010-05-12
> **earthpigg said:**
> for example?

open arena and enemy territory(/true combat) are the most common

---

### Post by 3rdalbum on 2010-05-12
> **MrNatewood said:**
> The lack of a proper Task Manager like in windows.

Now if you are in fullscreen and a game hangs you are left without much to do. Killing a process from TTY actually has *lower* success rates than Task Manager in windows, some apps sometimes just won't die

Kill them with -9:

kill 22137 -9

or in Top, after you press K and type the PID, it asks you what signal to send. The default is 15, change it to 9, and the program will instantly die.

To answer this thread's question, the dealbreaker seems to be Microsoft Office. Yes, Openoffice.org does 100% of what 95% of people use it for, but if your child is being taught MS Office and expected to hand in their assignment in MS Office format, you can't switch in Openoffice.org.  Of course, this is a problem with those schools (ESPECIALLY the ones who teach them Office 2003!!!) but as a parent you have to make sure that your child is not disadvantaged.

---

### Post by 98cwitr on 2010-05-12
no deal breakers here...im fully converted :)

---

### Post by MrNatewood on 2010-05-12
> **3rdalbum said:**
> Kill them with -9:

kill 22137 -9

or in Top, after you press K and type the PID, it asks you what signal to send. The default is 15, change it to 9, and the program will instantly die.

Thats exactly what I mean... it shouldn't be that complicated.
so This is what I have to do to kill a process:
1.ctrl-alt-F1
2.username
3.password
4.top(have to get the ID)
5.enter ID
6.choose signal 9

Sorry, thats freaking insane.

---

### Post by pookiebear on 2010-05-12
not quite dealbreakers, but annoyances that are close:

Sound... one of my laptops the mic does not work in half the linuxs I have tried. (I distro hop weekly) or the sound is auto-unmuted after 10 seconds of muting it.

Gimp. It is really good, but not photoshop good.

File associations sometimes take an act of war to get moved to a different program after the default program is uninstalled. Need to add this as a program to the preferences somewhere so that it is not a text file I have to hunt down. 

Firefox is super slow with rendering. Across all the distros I have tried on multiple computers on any version 3 and after. I can put 2 identical hardware computers side by side. wired. one with linux and one with windows. The windows firefox will load a page almost twice as fast. So I use chrome even though it does not have the add-ons that I like... yet.

ATI video and Broadcom wireless. But that is not any distros fault. They need to pump out some real drivers and quit with the whining. 


Take all that with a grain of salt. I work from home as a Microsoft Engineer. And I run lubuntu as my OS of choice right now at home.

---

### Post by handy on 2010-05-12
> **MrNatewood said:**
> Thats exactly what I mean... it shouldn't be that complicated.
so This is what I have to do to kill a process:
1.ctrl-alt-F1
2.username
3.password
4.top(have to get the ID)
5.enter ID
6.choose signal 9

Sorry, thats freaking insane.

You could install htop, which will streamline the process some.

---

### Post by ubunterooster on 2010-05-12
> **3rdalbum said:**
> To answer this thread's question, the dealbreaker seems to be Microsoft Office. Yes, Openoffice.org does 100% of what 95% of people use it for, but if your child is being taught MS Office and expected to hand in their assignment in MS Office format, you can't switch in Openoffice.org.  Of course, this is a problem with those schools (ESPECIALLY the ones who teach them Office 2003!!!) but as a parent you have to make sure that your child is not disadvantaged. Can't you just save them as MS office files?  

Dealbreaker is most don't know what an operating system is

---

### Post by rg4w on 2010-05-12
> **jetsam said:**
> There's big gaps in the software landscape; no filemaker equivalent (in ease of use and functionality)
Funny you should mention that:  I have a modest DB engine and UI I've been using for my own business, and have been toying with the idea of fleshing it out into a product. I've enjoyed FMP in the past, and would model some of the UI on it.  I've played with Open Office, and as much as I like the rest of the suite the DB part just doesn't gel for me.

Two hitches:
1. It works really well for the scale I designed it for (I've had good tests with just over 100k records, which is far more than I need) but has some slowdowns if you go too far beyond that. FMP's no speed demon but in good hands it can handle millions of records, and mine can't.

2. I'm fond of eating, and a truly usable product wouldn't offer much in the way of consulting opportunities to recoup costs.  So unless I find free money I'd probably have to seek compensation through the old-world path of license fees.  It wouldn't have to be much (I was thinking about US$50), but something to justify the time.  I'd prefer to deliver it for free, but no matter how much free code I write my rent stays the same. :)

Would such a package still be useful for you?

---

### Post by screaminj3sus on 2010-05-12
Video Drivers

---

### Post by donkyhotay on 2010-05-12
> **3rdalbum said:**
> To answer this thread's question, the dealbreaker seems to be Microsoft Office. Yes, Openoffice.org does 100% of what 95% of people use it for, but if your child is being taught MS Office and expected to hand in their assignment in MS Office format, you can't switch in Openoffice.org.  Of course, this is a problem with those schools (ESPECIALLY the ones who teach them Office 2003!!!) but as a parent you have to make sure that your child is not disadvantaged.

As mentioned previously just save in MS office format. Most educators don't know what open office is and have just memorized "their" version of MSoffice. I've had many teachers in college that said we *must* use MSoffice and I even had one teacher specifically state we can't use open office under any circumstances. I just made certain with those instructors to simply save as a MSoffice compatible file and they never knew that all the work I did was with open office. I usually got this more often with classes that weren't computer related (english, writing, etc.) while my computer instructors (that actually know something about it) generally wouldn't care and some of them would even recommend using open office. I agree this is primarily a failure of the educators not knowing enough about computers, but there isn't much that can be done except let them know about it and of course show your kids how to save as MSoffice format.

---

### Post by Johnsie on 2010-05-12
I've overcome my dealbreaker on my desktop at home and at work. My computers are newish so I can run Windows in VirtualBox without it affecting the performance of Linux:

[IMG]http://steeky.com/john/images/ss2.png[/IMG]

I use the closed source version from the website rather than the version in the repositories. The one on the website is more up-to-date and has more features (like USB)

Sadly I don't think this will work on my Atom n270 netbook because I dont think it will be able to handle running two operating systems at once.

---

### Post by jetsam on 2010-05-12
> **rg4w said:**
> Funny you should mention that:  I have a modest DB engine and UI I've been using for my own business, and have been toying with the idea of fleshing it out into a product. I've enjoyed FMP in the past, and would model some of the UI on it.  I've played with Open Office, and as much as I like the rest of the suite the DB part just doesn't gel for me.

Two hitches:
1. It works really well for the scale I designed it for (I've had good tests with just over 100k records, which is far more than I need) but has some slowdowns if you go too far beyond that. FMP's no speed demon but in good hands it can handle millions of records, and mine can't.

2. I'm fond of eating, and a truly usable product wouldn't offer much in the way of consulting opportunities to recoup costs.  So unless I find free money I'd probably have to seek compensation through the old-world path of license fees.  It wouldn't have to be much (I was thinking about US$50), but something to justify the time.  I'd prefer to deliver it for free, but no matter how much free code I write my rent stays the same. :)

Would such a package still be useful for you?

I'd be really interested in seeing the approach you took.  

Reason #2 is a pickle, though, isn't it?  It's really the crux of the matter; the people with the competency to do a good FM replacement also tend to be or want to be database consultants!  It's true at every scale.  Sun didn't neglect Open Office base for nearly a decade just because they didn't "get around" to making it truly work well...  

I hold simmering hopes for Kexi and for Dabo, and I occasionally like to catch up with developments, but I've learned not to keep those hopes too high because all these projects tend to stall with time.  

I'd encourage you to release what you have truly open source and truly free.  You might get developer interest, and maybe it could turn into something great...

As for my own needs, I use Filemaker and like the product a great deal.  The vendor lock-in grates, but I can live with it.  Long term I know that a good open source solution will come around some day.

I tend to go far afield when looking for the long term way out.  Exist engine and Gambas plus plus front end?  I mean-- given that the Sage people can glue 90 different higher math packages together with Python, it seems like a good solution should be out there if only the right pieces were put together...

---

### Post by mickie.kext on 2010-05-12
> **Mike BFD said:**
> Same here.

Talking about CAD apps, Adobe graphics etc., we shouldn't forget they are used "at their most" only by professionals (guys who earn money for what they do with the apps). 

**My vision is, Adobe (for example) still don't have Linux versions not because it just doesn't want to, but stupidly because Adobe guys don't know how to keep the software "strictly licensed" in Linux.** They make apps for professionals making money on graphic works. Why should such apps be free?!
"Limited" usage of Adobe progs (of not the freshest versions) is, however, possible via Wine.

As to "common software" which may be used in literally any household or office, it's imo represented pretty well in Ubuntu (and other Linux distros as well).
Really? They do not know how to slap EULA for Linux version and have no problems doing that for Mac and Windows version? 

They do not want to make Linux port because Microsoft and Apple are pressuring them not to do so. Nobody forces ISVs to opensource anything they do not want, I do not know why you imply that those "programs should not be free". I happen to thing that it should but that is not the point. Point is that lots of ISVs who make professional already ported their stuff, and nobody have problem "keeping stuff strictly licensed". 

Examples: 

[SDFX Houdini]("http://www.sidefx.com/") 
[The Foundry Nuke]("http://www.thefoundry.co.uk/")

[Autodesk Maya]("http://usa.autodesk.com/adsk/servlet/pc/index?siteID=123112&id=13577897")
[Autodesk Softimage]("http://usa.autodesk.com/adsk/servlet/pc/index?siteID=123112&id=13571168")

I am to lazy to link but there is tons of other. They knew how to license it. I guess Adobe can ask them how they done it:P.

---

### Post by RiceMonster on 2010-05-12
> **mickie.kext said:**
> They do not want to make Linux port because Microsoft and Apple are pressuring them not to do so.

Or, they do not see value in, or expect any profit from developing and supporting a Linux version.

---

### Post by mickie.kext on 2010-05-12
> **RiceMonster said:**
> Or, they do not see value in, or expect any profit from developing and supporting a Linux version.

Yeah, really no value. Biggest Hollywood movies are done on Linux, every big movie studio have at least some Linux workloads, and companies like Alias, Softimage (now Autodes) and SDFX are supporting Linux since 1999. I happen to have worked with some photo and 3D studios, so that shill line does not fool me. Adobe could port at least Photoshop, Premiere and After Effects, and would make huge business sense to do that. But Apple would probably kick them from their walled garden so it is a no go. Apple acquired Shake, it was making money and had Linux port, but they killed it only to integrate it in Final Cut which is OS X only.

As for AutoCAD, Autodesk is pretty close with Microsoft, and their Linux support for Maya and Softimage was tradition of companies they acquired. They would be cutting their profits if they stopped linux port, but if they port any new software, Microsoft would get all upset.

---

### Post by RiceMonster on 2010-05-12
Shill line? Give me a break. You know, I sort of *wish* Microsoft payed me to say that. What an easy job that would be.

I should have known you wouldn't be worth my time. To avoid going againt the CoC or causing a distruption, I'm not going to waste my time refuting any of your arguments.

---

### Post by mickie.kext on 2010-05-12
> **RiceMonster said:**
> Shill line? Give me a break. You know, I sort of *wish* Microsoft payed me to say that. What an easy job that would be.

I should have known you wouldn't be worth my time. To avoid going againt the CoC or causing a distruption, I'm not going to waste my time refuting any of your arguments.

I did not implied you are shill, just that "there is no market" sentence is easily thrown around but it is nothing more than a shill line in most cases. Which do not mean that one saying it is a shill. When some people repeat it to much, some other tend to pick up as it is truth. No offence intended.

---

### Post by 3rdalbum on 2010-05-12
> **donkyhotay said:**
> As mentioned previously just save in MS office format.

There's two issues here. Firstly, the kids are meant to be following their book step-by-step to perform certain tasks in MS Office. As long as Openoffice.org doesn't have an identical interface to MS Office, this can't be done.

And the second issue is that OOo's MS Office format compatibility is not flawless - and I'd hate to see a child lose marks in an assessment because OOo hasn't properly exported a graph or something.

These aren't criticisms of Openoffice.org, but just sad realities. The solution is to get the schools to teach Openoffice.org, which would solve some other problems too (such as parents having to shell out two hundred bucks for software for a class, and then finding out that the school is still teaching Office 2003 rather than the Office 2007 that they've bought).

---

### Post by smellyman on 2010-05-13
> **3rdalbum said:**
> There's two issues here. Firstly, the kids are meant to be following their book step-by-step to perform certain tasks in MS Office. As long as Openoffice.org doesn't have an identical interface to MS Office, this can't be done.
 
And the second issue is that OOo's MS Office format compatibility is not flawless - and I'd hate to see a child lose marks in an assessment because OOo hasn't properly exported a graph or something.
 
These aren't criticisms of Openoffice.org, but just sad realities. The solution is to get the schools to teach Openoffice.org, which would solve some other problems too (such as parents having to shell out two hundred bucks for software for a class, and then finding out that the school is still teaching Office 2003 rather than the Office 2007 that they've bought).
 
Do they have specific MS office courses in school nowadays?

---

### Post by McRat on 2010-05-13
What I see based on 10 days:

People expect to throw a generic O/S like Ubuntu on a customized OEM Windows System and have everything work perfect immediately.  Those WinTel boxes had the OS and drivers custom fitted before shipping.

Here's a little test.  Take a bunch of spare PC parts with no drivers.  Slap them togther.  Grab a old HDD with uh, hmmm..  WinME on it.  Now try to load a fresh copy of Win XP, Vista or 7.  See how many weeks it takes to get it running right.  Oh, make sure it dual boots while you are there.  Right.

I took new computers with no drivers, and pretty much got everything we need to do roughed out in a week with Ubuntu 32.  No where NEAR as hard as it is to adapt Windows to a machine that it wasn't designed specifically for.  The Ubuntu machine I'm typing from was a Win7 Crashaholic.  Brand new Clone, but wouldn't run Win7.

But I'm not expecting a desktop computer to:

Replace my phone.
Replace my camera.
Replace my TV.
Replace my radio.
Replace meeting friends in person.

And even if there were a Microsoft Virtual Sex application, I'd probably not use that either.  So for me, the only dealbreaker is stability.  If it crashes more often than XP, then it's a no-go.  So far, it takes a lot of abuse without shuddering.  No crashes yet.  But I did crash an XP Dell tonight:

IE8 was looking at a 5.8ghz wireless bridge for me.  Then it started to freak out.  I hit CNTL-ALT-DEL and saw IE8 was using 1,600,000,000 bytes of RAM.  Holy Memory Hole Batman!!!  I couldn't get it to shut off, so I had to kill the power.  

To make it a fair comparison, you would need to sell Ubuntu preinstalled on a tuned computer with MFR co-op on driver design to optimize for that box.

---

### Post by quinnten83 on 2010-05-13
> **everytimeref said:**
> I do wonder how many people who claim that they need photoshop actually **paid** for it.

Or actually *really* _NEED_ it.

---

### Post by quinnten83 on 2010-05-13
> **MrNatewood said:**
> Thats exactly what I mean... it shouldn't be that complicated.
so This is what I have to do to kill a process:
1.ctrl-alt-F1
2.username
3.password
4.top(have to get the ID)
5.enter ID
6.choose signal 9

Sorry, thats freaking insane.

how about alt+F2 > type xkill, point to misbehaving app?
Does that not work?

---

### Post by MrNatewood on 2010-05-13
> **quinnten83 said:**
> how about alt+F2 > type xkill, point to misbehaving app?
Does that not work?

Not when you are playing a game in fullscreen... No GNOME key combination works when playing in fullscreen.

---

### Post by smellyman on 2010-05-13
I just make a keyboard shortcut to open system monitor (ctrl + *)  Does that not work in full screen?

---

### Post by MrNatewood on 2010-05-13
> **smellyman said:**
> I just make a keyboard shortcut to open system monitor (ctrl + *)  Does that not work in full screen?

Nope

---

