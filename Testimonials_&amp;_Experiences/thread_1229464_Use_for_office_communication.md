---
title: "Use for office communication"
date: 2009-08-02
forum: Testimonials &amp; Experiences
---

### Post by LimCore on 2009-08-02
Hello,

I am using Linux for many years now, and since around 2 years I was using Ubuntu for VoIP communication.

**It would seem that Linux does not yet support sound fully.**

As for me, following problems (Ubuntu 9.04 on a PC)
[LIST]
[*] Sound is muted or dies when I switch users (VT-7, VT-9) (as in [bug 309724]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/309724"))
[*] Sound doesn't work for Skype, there is a huge delay (around 10 seconds)
[/LIST]

On my other computers
[LIST]
[*] 64bit Laptop - sound works fully
[*] 32bit Laptop - sound input was distorted and almost unusable, never fixed it
[*] Some older PC - sound input never worked in Linux
[*] Other PC - sound input worked, but after wasting hours on finding proper driver options
[/LIST]
So its around 50/50 for me.

About my coworkers and business partners:
[LIST]
[*] Some PC - sound works, but almost every time user needs to reboot to use Skype
[*] Other PC, and mac book - it seems it was working sometimes, but few times using Skype was not possible
[*] I can note that at ONE time linux won with windows here - sound blaster live24 bit was working horribly in windows, while it worked fine in linux.
[*] Sound output appears to be working more out-of-the-box then in windows
[*] Other guys are using MacOs / Windows (and sounds works ideally)
[*] (2007/2008) a bit older information: few fellow developers tried using Linux, and they sound experience was usually that it had trouble with sound (esp. input)
[/LIST]

On top on that, for every user - always you have to know to go to kmix/mixer, and play (sometimes a lot!) with the settings untill you get sound input working at all.

You can note that **Skype is 3rd party application**, but the problem seems to be in the system, if sound I/O is working in linux, then it also works in Skype (sometimes you have to switch in Skype to use Pulse).

Overall, sound NEVER worked fully out-of-the-box, always you have to know there is a need to go to sound mixer, enable some hidden settings and change them.

Other then that. sound works, but often with some problems, and sometimes it fully does not work.


Therefore I would say, **Ubuntu is not ready for Desktop in terms of providing working sound I/O**.

Steps to improve it, apart from sound drivers etc, could be to provide an application that:
[LIST=1]
[*] sets up default input levels 
[*] allow quick testing of I/O (including input etc)
[*] automatically tries other drivers settings
[*] mail a bug report + hw report if nothing worked
[*] recommends what audio cards are known to work
[/LIST]

---

### Post by LimCore on 2009-08-02
p.s.

If you selected pool **option 1 - EVERYTHING**, then please write did you really tested if sound playback for user A on VT-7, and for user B on VT-9 (alt+ctrl+F9) works at the SAME TIME.

So on desktop A you play music, then you go to desktop B and use Skype there, and the music from A is still playing.

If yet then please comment in [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/309724](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/309724) if it works for you, and system version / hardware.

---

### Post by Tamlynmac on 2009-08-02
Why is this poll necessary? :confused:

I can personally identify multiple hardware and driver issues with Windows, Ubuntu and other OS's. All of which negatively impacted video and/or audio functionality. Based on your statement "**Ubuntu is not ready for Desktop in terms of providing working sound I/O**." then Windows (or any other OS I've used) isn't ready either. When put into perspective, I've not found any OS that supports all available "video and audio hardware" or "software packages".

It's so discouraging, you struggle with Skype on Ubuntu and my poor neighbor can't find XP drivers for his onboard audio. Almost makes one wonder why we even bother with computers. ](*,)

My only word of advise is to use what works and meets your needs. We have been using Ubuntu/Linux for three years and to date it's met all our requirements and expectations. Of course we don't use Skype and only purchase Linux compatible hardware (which tends to minimizes driver issues).

---

### Post by LimCore on 2009-08-03
> **Tamlynmac said:**
> Why is this poll necessary? :confused:

To find out more or less the scope of this problem.

3 people voted so far for the EVERYTHING option, yet noone written if he really tested for 2 desktop users AT ONCE using audio, and on what hardware/system - to debug this bug I linked to.


> **Tamlynmac said:**
> then Windows (or any other OS I've used) isn't ready either.

The end result is following: from around 5 windows, 2 mac os x, 5 linux computers (in recent work and personal use of me and friends), there are 3-4 cases of "oh I can't use skype" or "wait, I have to reboot to have audio working" - all of which are Linux (Ubuntu).

About the hardware, this would help a lot, but I think more can be done on software side to help, as some wizard application, better error reporting, etc. 
And there are also software-only bugs like my multiply users bug.

---

### Post by cariboo on 2009-08-03
> 3 people voted so far for the EVERYTHING option, yet noone written if he really tested for 2 desktop users AT ONCE using audio, and on what hardware/system - to debug this bug I linked to.

You aren't seeing any one else with your problem, as it is unusual for most people to have two users running on the same computer at the same time. If this is truly a problem and not something you are doing to reinforce your argument, I would suggest you file a bug.

PS: I had more problems with Skype on windows than I do on Ubuntu. Windows and Skype refuse to detect my webcam's microphone, so if I wanted to use Skype in Windows I have to drag out a headset in order to use it.

---

### Post by Tamlynmac on 2009-08-03
> LimCore
The end result is following: from around 5 windows, 2 mac os x, 5 linux computers (in recent work and personal use of me and friends), there are 3-4 cases of "oh I can't use skype" or "wait, I have to reboot to have audio working" - all of which are Linux (Ubuntu).

About the hardware, this would help a lot, but I think more can be done on software side to help, as some wizard application, better error reporting, etc. 
And there are also software-only bugs like my multiply users bug.     I understand. Very similar to all those individuals that all share the same motherboard with my neighbor and can't locate audio drivers for XP.

As I said, all OS's have some issues. You apparently have found one in Ubuntu with respect to Skype (obviously cariboo907 has not experienced this issue) . My neighbor has found one in Windows. Polling the issue is IMHO foolish unless you plan on becoming involved in problem resolution. I'll assume that is your intent.

Keep in mind that Ubuntu/Linux is FOSS and if we find issues, I believe it's our responsibility to get involved in problem resolution. There are multiple ways to get involved. I'm certain you have investigated and have already decided which course of action is best for you. For example, becoming involved in writing the software wizard your referring to or writing the help documents, etc.

Please don't go down the path of entitlement (as some do). Remember that (IMHO) all of us have a responsibility to get involved, if we make use of FOSS apps. To often, those that rant and complain refuse to get involved in the community and only wish to demean the products. Which is (IMHO) fundamentally flawed and lacking in integrity.

Good Luck and I look forward to reading about your direct involvement with this project and how you participated in solving the problem. By doing so, you will definitely be contributing to the community. Benefiting the community and becoming a responsible participating member, certainly gains my respect.

---

### Post by LimCore on 2009-08-04
> **cariboo907 said:**
> You aren't seeing any one else with your problem, as it is unusual for most people to have two users running on the same computer at the same time. If this is truly a problem and not something you are doing to reinforce your argument, I would suggest you file a bug.


The bug is reported long ago, I linked to it in the first post here.

Skype now working is just one thing, usually  skype doesn't work if overall sound I/O doesn't work.

And it would seem on 9.04 most computers (all?) have this problem that sound does not work with 2 users logged in (to desktop) at same time.

---

### Post by LimCore on 2009-08-04
For the multipe desktop USERS at ONCE playback prolbem:



Ok the solution (to have sound from all users at once, if you are logged in several desktop sessions at once) is:

(on ubuntu 9.04 - tested on amd64)

1) edit as root /etc/default/pulseaudio
and set there:
PULSEAUDIO_SYSTEM_START=1

2) add all users that use sound to groups: pulse-access and pulse-rt

3) restart computer

I also did remove /home/*/.pulse* and added to group pulse also - but this was probably not needed and a bad idea

---

