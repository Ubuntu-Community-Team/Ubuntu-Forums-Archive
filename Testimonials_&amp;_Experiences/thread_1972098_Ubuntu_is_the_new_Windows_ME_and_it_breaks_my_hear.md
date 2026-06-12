---
title: "Ubuntu is the new Windows ME and it breaks my heart."
date: 2012-05-03
forum: Testimonials &amp; Experiences
---

### Post by nomadhar on 2012-05-03
this is a heartfelt plea to Cannonical to get back to basics.

when i first started using Ubuntu, it was fast, stable and secure.  now i can't use it for longer than 15 minutes without a freeze or crash.

Cannonical, you have forgotten the primary rule of open source: do one  thing well.  the attempts to be like MacOSX and Windows 7 are killing  what used to be a decent version of Linux.  Ubuntu is trying to do too  much, and doing much of it very poorly. the 10 series seems to be the  last fully functional version of Ubuntu, i guess ever again.

i'm sorry to say that i now spend much more time on my Windows 7  partition because it is far more stable than Ubuntu.  unlike Ubuntu, it  just works.  i cannot tell you how painful it is for me to make these  statements.  i had been migrating many people i know over to Ubuntu from  Windows; i cannot in good faith do that any longer.  i am seriously  considering getting rid of my Ubuntu partition and going back to good  old Slackware for my everyday computer.

the screen locks up for no reason all the time, forcing a reboot.

it will mysteriously do an instantaneous logout and go back to the login screen.

the Evolution calendar is totally broken and attempts to look at any appointments results in it showing me the year 1900.

Software Center is a slow, bloated piece of refuse now.  why do you keep adding to it?

the internet is mostly unusable.  Firefox is barely functional and Chrome installs but does not run when i try to use it.

any attempts to watch any media or video online result in massive slowdown, choppyness and eventual freeze.

it abuses my CPU and load is often nearing 100% on my dual core system.

there are so many errors i cannot be bothered to try to detangle them all.

for all the people that post complicated fixes for various things, remember this: isn't Ubuntu supposed to be the easy and friendly version of Linux?  i am an experienced programmer that has run major Linux servers using Slackware and Fedora, and the current Ubuntu utterly confounds me.

i'm using 11.10 right now, and from what i can see, 12.04 is worse and seems to be fundamentally broken.  i have seen so many threads around about broken installs and wrecked partitions, it is like looking at threads about Windows ME.

Cannonical developers, please please please stop trying to make Ubuntu 'pretty' and start trying to make it stable again.

---

### Post by mips on 2012-05-03
> **nomadhar said:**
> 
it will mysteriously do an instantaneous logout and go back to the login screen.

I had that happen to me yesterday and this is on a Xubuntu base install with openbox.

---

### Post by nothingspecial on 2012-05-03
*Thread moved to **Ubuntu Testimonials & Experiences**.*

---

### Post by Docaltmed on 2012-05-03
There are *always* scads of complaints around upgrade time. You might want to try doing a fresh install, that can help eliminate problems sometimes.

Alternatively, you could triage your issues and post them as threads in the support fora and get some solutions. That always works for me.

---

### Post by philinux on 2012-05-03
> **nomadhar said:**
> this is a heartfelt plea to Cannonical to get back to basics.

when i first started using Ubuntu, it was fast, stable and secure.  now i can't use it for longer than 15 minutes without a freeze or crash.

Cannonical, you have forgotten the primary rule of open source: do one  thing well.  the attempts to be like MacOSX and Windows 7 are killing  what used to be a decent version of Linux.  Ubuntu is trying to do too  much, and doing much of it very poorly. the 10 series seems to be the  last fully functional version of Ubuntu, i guess ever again.

i'm sorry to say that i now spend much more time on my Windows 7  partition because it is far more stable than Ubuntu.  unlike Ubuntu, it  just works.  i cannot tell you how painful it is for me to make these  statements.  i had been migrating many people i know over to Ubuntu from  Windows; i cannot in good faith do that any longer.  i am seriously  considering getting rid of my Ubuntu partition and going back to good  old Slackware for my everyday computer.

the screen locks up for no reason all the time, forcing a reboot.

it will mysteriously do an instantaneous logout and go back to the login screen.

the Evolution calendar is totally broken and attempts to look at any appointments results in it showing me the year 1900.

Software Center is a slow, bloated piece of refuse now.  why do you keep adding to it?

the internet is mostly unusable.  Firefox is barely functional and Chrome installs but does not run when i try to use it.

any attempts to watch any media or video online result in massive slowdown, choppyness and eventual freeze.

it abuses my CPU and load is often nearing 100% on my dual core system.

there are so many errors i cannot be bothered to try to detangle them all.

for all the people that post complicated fixes for various things, remember this: isn't Ubuntu supposed to be the easy and friendly version of Linux?  i am an experienced programmer that has run major Linux servers using Slackware and Fedora, and the current Ubuntu utterly confounds me.

i'm using 11.10 right now, and from what i can see, 12.04 is worse and seems to be fundamentally broken.  i have seen so many threads around about broken installs and wrecked partitions, it is like looking at threads about Windows ME.

Cannonical developers, please please please stop trying to make Ubuntu 'pretty' and start trying to make it stable again.

I'm sorry but the developers don't often frequent the forums.

Either raise a bug report on Launchpad. Or take a look here. 1 and a half days left.

 [http://iloveubuntu.net/ubuntu-open-week-may-2nd-4th-2012-opened-ask-mark-shuttleworth-may-1st-2012](http://iloveubuntu.net/ubuntu-open-week-may-2nd-4th-2012-opened-ask-mark-shuttleworth-may-1st-2012)

---

### Post by kurt18947 on 2012-05-03
nomadhar, I'm sorry to hear you've had such a poor experience.  It sounds like you're having problems with more than the desktop.  What kind of machine are you running?  If not at least a dual core processor,  you might try Xubuntu or Lubuntu.  They seem to work better on less powerful machines.  Mint is another nice alternative; I have the 32 bit version running on a 10 year old notebook and it's working well considering the age of the machine.  Mint doesn't run Unity, it's more 'traditional'.

The other thing I would do if I were you is try a live install, either CD or USB.  I think CD is more certain to boot on nearly any machine, USB is faster.  If you tried an upgrade, that could have something to do with your problem.  Upgrades don't have the greatest history and are why clean installs are generally recommended.

---

### Post by nerdopolis on 2012-05-03
> **nomadhar said:**
> 
it will mysteriously do an instantaneous logout and go back to the login screen.
.

This! This happens to me since last year, but what's weirder is if I log into a TTY it "fixes" it...

I was never able to get to the bottom of it, as it creates no apport logs, or last I checked in any logs...

Are you on an Intel card?

---

### Post by snowpine on 2012-05-03
Slackware is a good choice if you're looking for a very stable distro. :)

---

### Post by 3rdalbum on 2012-05-03
Most of the "errors" you report are basically one problem: High CPU use.

Ubuntu is not a high CPU-using system by nature, but there may be a bug that's causing a program to abuse the CPU and keep it at 100% usage. You can find out what program using System Monitor.

As for "12.04 is the new Windows ME!", well, no it isn't. There are always complaints around release time, but for 12.04 I've heard shockingly few complaints about instability or inability to use. Windows ME was unstable for almost everybody. 12.04 is unstable for almost nobody.

The key to everything is bug reports: If you have a problem, report it to the developers using Launchpad and you've got a chance of it being fixed. If it doesn't get reported, and no developers run into your specific problem, there's almost no chance of it being fixed. That's partly why people volunteer to test pre-release versions of Ubuntu; partly to help report bugs to make sure the final release is solid.

---

### Post by Version Dependency on 2012-05-03
> **3rdalbum said:**
> As for "12.04 is the new Windows ME!", well, no it isn't. There are always complaints around release time, but for 12.04 I've heard shockingly few complaints about instability or inability to use. Windows ME was unstable for almost everybody. 12.04 is unstable for almost nobody.

The OP has not used 12.04.  He is on 11.10 but he assumes 12.04 will be even worse: 

[I]"...from what i can see, 12.04 is worse and seems to be fundamentally broken."

[/I]Not a good assumption, me thinks.  The LTS releases are much more stable.  Just because you see alot of threads right now about people having problems installing 12.04, well....of course.  First, 12.04 just came out and everybody and their grandmother is upgrading.  Second, the people posting in the support forums are the people that, well...need support.  I've installed 12.04 on five machines without any issues at all.

---

### Post by CharlesA on 2012-05-03
12.04 has been stable for me so far.

I did a clean install instead of upgrading, so I could start with a clean slate.

The only issue I have run into so far is that "halt" alone will not power off the machine like it did in lucid.

---

### Post by TBABill on 2012-05-03
Like others have mentioned, this sounds a lot like a faulty install, whether from packages that had errors during download or that were corrupted during the install. My first instinct in such a troubled system experience would be a fresh install from a newly downloaded ISO, or at least a new CD/DVD/USB from a known good md5sum iso.

---

### Post by nomadhar on 2012-05-03
system specs of the test rig. also, this 11.10 is a clean install.

HP tx-2513cl laptop

-Computer-
Processor        : 2x AMD Turion(tm) X2 Dual-Core Mobile RM-70 (2.0GHz)
Memory        : 3796MB
Operating System        : Ubuntu 11.10

-Display-
Resolution        : 1280x800 pixels
OpenGL Renderer        : ATI Radeon HD 3200 Graphics
X11 Vendor        : The X.Org Foundation

-Multimedia-
Audio Adapter        : HDA-Intel - HDA ATI SB

-SCSI Disks-
ATA WDC WD3200BEKT-6
Optiarc DVD RW AD-7561S
Generic- Multi-Card

while it is an older computer, it is most definitely not underpowered.  Windows 7 runs flawlessly.

some advice i've seen is to disable Unity and Compiz.  i thought these were part of the point of using Ubuntu.  if i want to run vanilla Gnome, i will just use Slackware.

---

### Post by QIII on 2012-05-03
I understand that you are frustrated.  I would be.

But you need to take care not to assume that your experiences are  universally observed by the entire community.  If they were, nobody  would be using it.

Oneric worked fine for me in every way. Precise is even better.  So  good, in fact, that I have been using it as my primary since the second  Alpha.

Your CPU spike, as mentioned, may be the root of many of your problems.   This is NOT a normal condition.  That would be the first thing to  investigate.  Something is wrong on your machine (notice I did not say "something wrong with your machine"), not with Ubuntu in  general.  Since you are using Oneiric on a laptop, the solution may actually already have been discussed -- and solved -- several times.  I've seen a number of posts like that.

Your hardware looks just fine.

Disabling Unity and Compiz would be problem avoidance, not a solution.  That is not a good course of action, so I agree with you there.

What would do us all some good here is for you to install htop, get your CPU maxed out and copy and paste the results of htop and an explanation of your problem in a new thread in a help forum -- written as a request for help rather than as a rant.

And, FWIW, it is my opinion that reinstalling fresh is an action of last resort.  Rather that taking the "Blast off and nuke 'em from orbit" approach, I think it best to try to fix a problem first.  The whole community (you included) learns that way.

---

### Post by beansdad on 2012-05-03
I too have been having problems like these. I reverted to 10.10 as neither 11.04 or 11.10 would allow me to use the computer for any sensible amount of time i.e. extremely slow to do anything at all.
I was hoping 12.04 would be better and, for speed, it definitely is, but I get many "system problem" messages, lightning calendar goes blank when I align my desktop and laptop (directly, not through the Cloud or whatever). My virtual harddrive file for Virtualbox has mysteriously disappeared!
This is all after five attempts at a clean installation! I've tried reading the forums but found nothing to help, the requests to submit a report do not seem to work (computer simply sits there as if gathering info without ever achieving anything). Some of the bug reports seem to be written in a language I cannot understand because it is far too technical and I am only a user with about 30 years experience.
I am now seriously looking for an alternative to Ubuntu having wasted an inordinate amount of time and effort trying to get the last 3 releases to work and failed.

Can anyone suggest a system that works at a reasonable speed without all the errors?

---

### Post by philinux on 2012-05-03
> **beansdad said:**
> I too have been having problems like these. I reverted to 10.10 as neither 11.04 or 11.10 would allow me to use the computer for any sensible amount of time i.e. extremely slow to do anything at all.
I was hoping 12.04 would be better and, for speed, it definitely is, but I get many "system problem" messages, lightning calendar goes blank when I align my desktop and laptop (directly, not through the Cloud or whatever). My virtual harddrive file for Virtualbox has mysteriously disappeared!
This is all after five attempts at a clean installation! I've tried reading the forums but found nothing to help, the requests to submit a report do not seem to work (computer simply sits there as if gathering info without ever achieving anything). Some of the bug reports seem to be written in a language I cannot understand because it is far too technical and I am only a user with about 30 years experience.
I am now seriously looking for an alternative to Ubuntu having wasted an inordinate amount of time and effort trying to get the last 3 releases to work and failed.

Can anyone suggest a system that works at a reasonable speed without all the errors?

Post a thread with an appropriate title in general help forum which includes your full system specs.

---

### Post by FormatSeize on 2012-05-03
> **nomadhar said:**
> system specs of the test rig. also, this 11.10 is a clean install.

-Computer-
Processor        : 2x AMD Turion(tm) X2 Dual-Core Mobile RM-70 (2.0GHz)
Memory        : 3796MB
Operating System        : Ubuntu 11.10
Well, I don't want to offend anyone here or anything, but 11.10 was pretty bad. I didn't have too many problems with it, but I've read a lot about how problematic it was. I personally found it nothing to really talk about, and I never bothered with it enough to attempt to fix all the problems that would arise if I did use it all the time.

In my gaming machine with Win 7, there's an AMD quad-core processor. For whatever reason, AMD's APU doesn't like my GPU, causing crashes at times. If my friend were standing over my shoulder now, he would tell me to post something along the lines of "do you cook an egg on that AMD processor?". He has some issue with them, but I've come to like mine when it works and my computer doesn't crash. 

Win 7 is pretty good, though. It took a long time for me to admit that, but that's probably part of the reason why you have to pay for it (in most cases). 

I think you should at least try a fresh install of 12.04. LTSs are generally more stable upon release, and it's a lot more stable for me than 11.xx. It's running on a Pentium-D processor, 4 Gb of memory, Gateway GT5445 (that's old). But I've had no problems, things look good, and there's not many things to try to fix like other times I've upgraded in the past.

---

### Post by nomadhar on 2012-05-04
i appreciate the advice from all the replies.  10.04 just worked so well, i was so happy with it even for my own machine (i typically ran Slackware on my machines in the past).  having all these issues after moving to 11.10 from a verified MD5 checksum DVD was an utter shock.  there are so many problems that i cannot detangle them to figure which issue is causing which problem, and i am an experienced programmer that enjoys compiling Linux kernels.  i think i will just wipe this partition and start over with Slackware, maybe give Ubuntu another go when it is sane again.

my underlying issue is that i do not feel that i can recommend Ubuntu as a Windows or MacOSX replacement anymore.  i had been migrating people and clients over to Ubuntu as an open-source advocate, but the extreme unstable nature of 11.XX and 12.04 is forcing me to look for other options.

i liked Ubuntu because it had provided a user friendly out-of-the-box experience.  in the past, i simply gave a burned DVD to non-technical unexperienced Windows users and they could install it without my help.  Ubuntu had helped me to convince lots of people to migrate to open source.

then 11 came along.  i had to roll people back to 10.04 from 11.XX because some clicked the upgrade option and fragged their machines.  my personal attempt to test 12.04 on another rig was an absolute nightmare: installer issues, then login issues, then stability issues, then throwing my hands up and installing Slackware. ](*,)

12.04 is supposed to be a LTS release, but even Mark Shuttleworth admitted that Unity/Compiz is only 2/3 of where they want it to be in the official chat 2 days ago.  why make such an unfinished product the default UI for a release that should be stable?  surely more time should be spent testing and refining it.  i've already had people telling me that they had no problems with 12.04, but every single person that said that is an experienced Linux user.  i am trying to reach out to the larger PC user crowd, who are mostly unwilling to read technical instruction FAQs or go on forums.  these users will definitely never touch a terminal.

Cannonical seems to have forgotten the golden rule of open source: do one thing well.  Ubuntu seems to be attempting to emulate Windows 7 and MacOSX and do everything.  there seems to be a growing case of 'inmates running the asylum' again:
[http://books.google.ie/books/about/The_Inmates_Are_Running_the_Asylum.html?id=04cFCVXC_AUC](http://books.google.ie/books/about/The_Inmates_Are_Running_the_Asylum.html?id=04cFCVXC_AUC)

i think Cannonical needs some sort of non-technical average user consortium; i think a number of my issues (that others share) would never have appeared.  Unity/Compiz was made the default far too early.  while i dislike Flash, the Compiz and Unity's interference with it drives average users away.  Software Center has become extremely sluggish; again, a favorite element for the people i know.  the requirement for following a detailed FAQ just to install 12.04 definitely pushes users away.

---

### Post by nothingspecial on 2012-05-04
> The forum membership, staff included, are volunteers. Most are ordinary users. This is not the place to address concerns to Canonical, the Ubuntu design team or the developers, nor is it the place for bug reports.

This is not the place for full-scale debate or vigorous discussion, but feedback to the original poster is welcome.

Staff may close a thread before this time if it strays from these guidelines

Should you wish to provide feedback and ideas to the developer or designer teams, or to report bugs, here are some useful links:

[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)
[http://design.canonical.com/2011/11/...touch-with-us/](http://design.canonical.com/2011/11/...touch-with-us/)
[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

[http://ubuntuforums.org/showthread.php?t=1921679](http://ubuntuforums.org/showthread.php?t=1921679)

---

