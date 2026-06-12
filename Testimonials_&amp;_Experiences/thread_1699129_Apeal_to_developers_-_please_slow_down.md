---
title: "Apeal to developers - please slow down"
date: 2011-03-03
forum: Testimonials &amp; Experiences
---

### Post by PetrFrish on 2011-03-03
Please slow down, test more, and embrace simplicity and robustness.

I will elaborate, but first I mention where I am

I have just made a fresh install of
 Ubuntu 10.04 LTS- the Lucid Lynx - released in April 201
after attempt to upgrade from hardy heron which crashed and  made machine unbootable. This the old old bug, still present in Lucid:

[Bug 297234] Re: Blacklist confused by additional video card
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/297234](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/297234)

In the new install, some things improved (more then two virtual desktops)
but other problems develop.

E.G.: One of the three monitors now blanks out for few seconds, at some, not all, clicks in the other monitor.

 And new bug:Cursor becoming stuck on border in multiscreen setup
[https://bugs.launchpad.net/ubuntu/+source/x2vnc/+bug/726783](https://bugs.launchpad.net/ubuntu/+source/x2vnc/+bug/726783)
appears.

The grub becomes complex and incomprehensible. In the old menu.lst I can easily change options, leave out quiet or add debug, and  see why it boots into single mode, but not all to init 5 directly. It hangs up quitely for reason unknown.

Now I cannot see or modify anything in really complex /etc/grub.d

Would it be so hard to make a LiveCD to check whether there are two graphic cards, instead of going to kernel panic? To ask, or just chose one card and make a mental note to ignore the other?

Now, not even knoppix 6 can handle two cards. Knoppix 4 could go to the console with option -b (no hardware detection). Version 6 hangs up.

The way it is going, one fears each new release, instead of looking forward to it. It feels like building higher and higher , and more and more unstable Babylon tower. 

Let's slow down and make it all more robust and transparent. Please.

---

### Post by cchhrriiss121212 on 2011-03-03
I'm not sure whether you are asking for help or not.

Regarding the 2 cards issue, can't you disable the integrated chip via BIOS? That is what I would recommend even if you weren't having trouble with it.

Yes GRUB2 is different, and in some cases worse, but Ubuntu has to adopt to the software it gets from upstream. GRUB2 is now the standard boot loader and you will have to get used it. If you read up on it, it won't seem so scary:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by PetrFrish on 2011-03-04
I am not asking for help here. I have filed bug report on the upgrade crush  [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/720655](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/720655) and so far solved that problem by fresh install.

 I cannot disable the on-board card in the BIOS. I have to physically remove the board with ATI Technologies Inc Radeon RV250 and add blacklisting. It is a bother, but it sort of works.

Here, my appeal concerns priorities and philosophy of Ubuntu:

 To have a new release perform flawlessly on wide (perhaps defined) range of hardware is more important (for growing number of users) then an added feature.

I am sure I can learn to understand new grub, but ideally, I do not really want to know about it. And I believe that on the top of current grub, there can be something like old menu.lst: one page which lists the possible boots, with titles I can edit to make sure I know which is which, and line where I can asd kernel option. Complexity, where really needed, can be hidden.


I would like to see in LiveCD with something like Knoppix 4 -b option, (no hardware detection)  which booted to console (init 1) even on myuntypical hardware. (Elimination of init 1, init 3 , init 5) stages is another example of decreased robustness.

 It feels like 'all or nothing':
either whole system with all packages boots, or, you end up with blank screen. (That, blank screen, results when I select regular boot. So, I do recovery boot, log into console, and do startx, and evrything works. But it  makes me nervous: What if, for reason unknown, one day, that too will lead to blank screen. 

In other words: What is a troubleshooting procedure when things go wrong?

So. this is a reminder, 'in the field', on other hardware then you use for testing, things do go wrong.


That said, I want to say I appreciate developers work, and am grateful for Ubuntu.

---

### Post by cchhrriiss121212 on 2011-03-04
> I am not asking for help here.
Well this is a support forum, you want this forum:
[http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)
I have requested it be moved. 

> And I believe that on the top of current grub, there can be something  like old menu.lst: one page which lists the possible boots, with titles I  can edit to make sure I know which is which, and line where I can asd  kernel option.
Like I said, Ubuntu has nothing to do with GRUB2, they don't make it, and they don't have the resources to adapt it either.
> 
 Complexity, where really needed, can be hidden.
It is hidden, most people have no need to edit GRUB. Simple changes can be done with startup manager, anything more complex requires reading the manual. 
> 
In other words: What is a troubleshooting procedure when things go wrong?
Boot from a live cd/usb and ask for help. 

On a further note, developers do not actually read these forums, for suggesting improvements try this:
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by howefield on 2011-03-04
Moved to "Ubuntu Testimonials & Experiences"

---

### Post by Jazzy_Jeff on 2011-03-04
Developers are not going to slow down. Things are changing so fast they are trying to keep up. That is the reason for the LTS versions so that you don't have to upgrade all the time or use the newest versions.

---

### Post by Simian Man on 2011-03-04
> **PetrFrish said:**
> Please slow down, test more, and embrace simplicity and robustness.
There is no one set of developers who bring you Linux.  It is a set of totally independent projects with no overarching philosophy, roadmap or structure.  Some projects, like the Kernel, do emphasize robustness and good software engineering, but most do not.  Your undirected plea for slowing down isn't going to help anything.  Your best bet is to use a stable, well-tested distribution like CentOS or Debian Stable.

> **cchhrriiss121212 said:**
> Yes GRUB2 is different, and in some cases worse, but Ubuntu has to adopt to the software it gets from upstream. GRUB2 is now the standard boot loader and you will have to get used it.
Ubuntu didn't have to adopt Grub2, and it isn't the "standard bootloader" by any means.  Many distributions still use the old grub including Fedora which is usually ahead of Ubuntu on version numbers.

---

### Post by cchhrriiss121212 on 2011-03-04
> **Simian Man said:**
> 
Ubuntu didn't have to adopt Grub2, and it isn't the "standard bootloader" by any means.  Many distributions still use the old grub including Fedora which is usually ahead of Ubuntu on version numbers.
It is the standard bootloader on Debian, which Ubuntu is based on. Ubuntu has no connection to Fedora so it is not relevant what they use.

 > Your best bet is to use a stable, well-tested distribution like CentOS or Debian Stable.

But I agree with this, Ubuntu is not the most stable Linux OS out there, and never will be as long as the number 1 goal is to attract new users.

---

### Post by Simian Man on 2011-03-04
> **cchhrriiss121212 said:**
> It is the standard bootloader on Debian, which Ubuntu is based on. Ubuntu has no connection to Fedora so it is not relevant what they use.

Debian packages both versions of Grub and Ubuntu frequently chooses to ship different defaults than Debian.  I'm just saying that Ubuntu chose to use Grub2, it wasn't forced on them by anyone.  I personally think it was a bad idea, but you're welcome to your opinion.

---

### Post by johntaylor1887 on 2011-03-04
> **PetrFrish said:**
> I am not asking for help here. I have filed bug report on the upgrade crush

That's good that you filed a bug report, but appealing to the devs here won't do any good. This is not even an officially supported forum. I suggest you stay over at launchpad if you want to affect change.

Yeah, I know some people don't like reinstalling every 3 years :rolleyes: , but "upgrading" is always iffy at best no matter what the OS is. Back up your stuff and do a clean install. In all reality, a clean install is actually faster anyway. I've heard of upgrades taking the better part of 8 hours which is ridiculous.

---

### Post by johntaylor1887 on 2011-03-04
> **cchhrriiss121212 said:**
> 
But I agree with this, Ubuntu is not the most stable Linux OS out there

Scientific proof of this? Or are you just saying this because it sounds good to prove a point? I've actually found it to be the most stable OS I've ever used, and I've literally tried just about everything imaginable.

---

### Post by cchhrriiss121212 on 2011-03-04
> **Simian Man said:**
> Debian packages both versions of Grub and Ubuntu frequently chooses to ship different defaults than Debian.  I'm just saying that Ubuntu chose to use Grub2,** it wasn't forced on them by anyone**.
Ubuntu is all about attracting new users, that means they use the newest software available. As GRUB1 is no longer being developed they are obviously going to use GRUB2 to make use of the new features it offers.
In essence it was forced on them by their own idea of what Ubuntu should be: up to date, flashy, and with all the newest features that Linux has to offer.

---

### Post by cchhrriiss121212 on 2011-03-04
> Scientific proof of this? Or are you just saying this because it sounds good to prove a point?
I do not post here to prove points, I post to offer advice that others may find helpful. I don't have any data for you, it is my personal experience as well being a commonly held opinion among other Linux users. Just take a look through the forums, and observe all the issues people have with updates breaking functionality, even with the LTS versions. 

If you want rock-solid stability, Debian stable has the best reputation.

---

### Post by Simian Man on 2011-03-04
> **cchhrriiss121212 said:**
> Ubuntu is all about attracting new users, that means they use the newest software available. As GRUB1 is no longer being developed they are obviously going to use GRUB2 to make use of the new features it offers.
In essence it was forced on them by their own idea of what Ubuntu should be: up to date, flashy, and with all the newest features that Linux has to offer.
I guess I don't see bootloaders as being flashy, exciting pieces of software.  I just want mine to work and Grub .97 works great for that.

> **johntaylor1887 said:**
> Scientific proof of this? Or are you just saying this because it sounds good to prove a point? I've actually found it to be the most stable OS I've ever used, and I've literally tried just about everything imaginable.
How could you scientifically prove something like this?  You haven't defended your justification that Ubuntu is the most stable OS either, it's just your experience.  cchhrriiss121212 and I's experience is very different, and I'm betting that most people would agree with us that Debian Stable or CentOS (my choice) are much more stable than Ubuntu.

---

### Post by mikewhatever on 2011-03-05
> **PetrFrish said:**
> Please slow down, test more, and embrace simplicity and robustness.

...

I think you are overreacting, not sure why.
New software will always introduce new bugs and sometimes fix old ones. The bugs you mentioned are actually quite minor, and the one on blacklisting graphics is arguably unrelated to Ubuntu. If those are the only bugs encountered after migrating to 10.04, I'd say you should be celebrating rather then appealing to developers.

---

### Post by johntaylor1887 on 2011-03-05
> **cchhrriiss121212 said:**
> Just take a look through the forums, and observe all the issues people have with updates breaking functionality, even with the LTS versions. 


It just *seems* like that because this forum is basically the only forum for the millions of ubuntu users to go to. If there were hundreds of ubuntu forums like there is for windows, it would seem like only a few people are having problems. If there was only one windows forum for help, there would be trillions of posts for help. Same with any OS that only had one forum. And yes, I realize there are other linux forums where ubuntu users can get help, but relatively speaking not many people post there.

After doing MANY installs of ubuntu, I still stand by my belief that ubuntu is one of the most solid OS's out there.

---

### Post by Tamlynmac on 2011-03-05
> johntaylor1887
> Scientific proof of this? Or are you just saying this because it sounds  good to prove a point? I've actually found it to be the most stable OS  I've ever used, and I've literally tried just about everything  imaginable.
> After doing MANY installs of ubuntu, I still stand by my belief that ubuntu is one of the most solid OS's out there. 	

When we state our opinion, it doesn't need to be supported - as it's  based solely on personal preference, observation and experience. You  didn't comment or state that it was a universal opinion. I think  problems occur when members make comparisons without noting that it only  represents "their" opinion. Or, their comparison somehow reflects the  opinions or beliefs of unknown others (as in the average user - what  ever that means).

I recognized immediately that your statement regarding Ubuntu being the  most stable, was your opinion. You said, "I've actually found it to be  the most stable OS  I've ever used". Which doesn't suggest that your speaking for anyone but  yourself. Nor, does it imply that you were in any way comparing one OS  to other for any other purpose than to establish your own opinion. The  number of variables associated with proof of individual opinion could be  substantial. :wink:

I also believe Ubuntu/Linux is an extremely stable platform. We've been  Ubuntu only since 7.04. Not once in all this time, have we experienced  any problems (other than those self imposed) with either stability or  security. We have tried numerous Linux distros and found Ubuntu meets  all our requirements. That's not to say, that others may find a  different distro - works better for them. Especially, considering  hardware and/or specific policies that some might find objectionable (6  month releases, etc.).

Just my $0.02

---

### Post by arunb on 2011-03-06
so is debian more stable than ubuntu ??

---

### Post by mikewhatever on 2011-03-06
Debian has several branches, but Debian stable, CentOS, ...some others I'm sure, are considered to be among the most stable distros. Please note, stable doesn't mean bugless.

---

### Post by mastablasta on 2011-03-06
well in MY opinion WIndows XP is stable. Didn't have any crashes, or registry bloat or any issues with it as others have experienced. Granted i started using it i think after SP2 came out.

I know this old system i have here works nicely in XP. Ubuntu on the other hand works nicely on one computer (so i kept it LTS) but not nice on this one. 
LTS had sound issue which a simple ALSA upgrade fixed. then came the updates which downgraded alsa again. ok to avoid this instability i decided to go with Kubuntu 10.10. tested it out live for a while first. everythign works nicely.

 I installed it. still work nice. applied some updates. still ok and stable. a week goes arround, more updates. i applied them. well well what is this. suddenly hibernate doesn't wokr as it should. computer doesn't start up sometimes screen stays dark (this is a new one i just found this wekeend). sound still works, but certain youtube videos suddenly don't work (be it in Firefox or rekonq). now i applied many patches in windows. securoty patches mostly but also some were programe updates (separte from windows patches9 and NEVER EVER have these messed up sound on the system, made you tube not viewable or made the system not go to sleep propperly. no it seems this is a built in function of Linux. to break something that works nicely for me,

as i said it is MY opinion on Ubuntu/Kubuntu stability if i would be judging the system's performance on this particular computer. I owuld also like to say they need to slow down. insetad of really fixing the bugs (there i splenty of them STILL on launchpad even after  a year or so, they spend time on developing Unity interface. or in other words those bugs are not important to them as the priority seems to be new user interface. and as someone said with new programmes also come new bugs.  what i don't udnerstand is sometimes there is a solution offered on Launchpad for the bug, but the bug stays in the system. nice.

other one (about 7 years old maybe more notebook with crapy ram, GPU and CPU) does it much better so it stayed on LTS. no issues there and it appears very stable there. it even increased the batery time from winXP. kind fo shocked me conidering many users report how their batery drains 2x as fast as on XP.

---

### Post by ikt on 2011-03-06
> **mastablasta said:**
> Granted i started using it i think after SP2 came out.


You missed out on all the fun :P

> **PetrFrish said:**
> Please slow down, test more, and embrace simplicity and robustness

You're kind of missing the underlying philosophy of linux and a lot of open source software, which is "release early, release often".

In addition the problem that you're having isn't directly related to ubuntu, sure you found the bugs while running ubuntu, and have submitted them to the ubuntu bug tracker, but that doesn't make it now Canonicals problem to deal with, in fact part of the triage process of dealing with bugs you have submitted is replicating the bugs locally, and then if necessary taking them further upstream, to the actual bug trackers of that software.

A lot of people submit bugs and think "there, work is done" but it's only the start, if nobody else has the issue, and nobody can duplicate it, it will never move on and the programmers of the software which is effected by the bugs are never aware of the issue.

---

