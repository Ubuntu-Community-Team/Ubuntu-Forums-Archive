---
title: "ubuntu studio or ubuntu desktop"
date: 2009-10-13
forum: Ubuntu Studio
---

### Post by s.dalas on 2009-10-13
hi people,

i am going to build a powerfull desktop for recording professional sound. i have made my decision on hardware. 

What i need to know right now is this:
Ubuntu studio 9.04 supports real time kernel.
Does Ubuntu desktop 9.04 support real time kernel?? Cause if this happen i am going to put on desktop version and set up the programs i need.

Maybe is a silly question but... 

Thanks in advance,
Stelios

---

### Post by kayosiii on 2009-10-13
The realtime kernel in 9.04 really isn't worth the effort. The stock kernel in 9.04 is almost as good as a realtime kernel (it's one of the best stock kernels). 

9.10 is due out in a few weeks and has and so far I have had much more success with the realtime kernel in it.

As for Ubuntu Studio VS Ubuntu.. Theoretically it shouldn't make a great deal of difference Except that there might be a few less steps of Configuration to get the system the way you want it starting with studio. I use Kubuntu + Realtime Kernel (so I don't have much direct experience with either).

---

### Post by s.dalas on 2009-10-15
> **kayosiii said:**
>  I use Kubuntu + Realtime Kernel (so I don't have much direct experience with either).

maybe i sound stupid, but in the above sentence you mean that you have put the real time kernel in kubuntu or that kubuntu have real time kernel by default (so and ubuntui guess)

---

### Post by c00kie55 on 2009-10-15
ubuntustudio comes with realtime kernel on most others you have to install the realtime kernel but in most cases its real easy just install linux-rt from synoptic

just remember to set the realtime in /etc/security/limits.conf 
i like thoes settings even thoe i think someone once said memlock unlimited aint safe ??

@audio - rtprio 99
@audio - nice -19
@audio - memlock unlimited

i have some grapihis probs with the ubuntustudio theme that i dont have in the desktop theme and i also like the menus in desktop most

---

### Post by s.dalas on 2009-10-15
ok i admit i cant understand the settings...
but i understand that i can put the real time kernel easy from synaptic.

will this make the pc run better for professional sound recording with ardour?? or should i leave the default kernel in ubuntu desktop?

i admit that i trust ubuntu desktop more...

---

### Post by c00kie55 on 2009-10-15
yes i think so.. guess thats one of the reasons way they made it (rt-kernel)
if you think it sounds hard i would go for the studio version as some off the setting is automatic set for you and lots off audio programs is also installed by default

if you dont set the setting you want have realtime 

its easy do a

sudo gedit /etc/security/limits.conf

apply tihs at bottom of page 

@audio - rtprio 99
@audio - nice -19
@audio - memlock unlimited
 
now save and close

next add your self to audio grup by 

sudo adduser (your name) audio 

witout the () thing and thats should be it

---

### Post by s.dalas on 2009-10-15
i dont have any problem to set them by my self. i just dont understand what are these doing.

i dont trust studio though... so you advice me to install desktop version and install the rt kernel by my self.

can i make 2 users? one to log in to rt kernel and the other to login to default desktop kernel - so i can see if there is any difference?

Thanks again,
Stelios

---

### Post by snowpine on 2009-10-15
Hi Stelios, if you install the real time kernel (sudo apt-get install linux-rt) it will appear on your Grub boot menu. You can choose between the rt and generic kernel each time you boot up the computer. That is the best way I know to compare them.

---

### Post by s.dalas on 2009-10-15
> **snowpine said:**
> Hi Stelios, if you install the real time kernel (sudo apt-get install linux-rt) it will appear on your Grub boot menu. You can choose between the rt and generic kernel each time you boot up the computer. That is the best way I know to compare them.

ok thanks a lot. i will keep the 2 kernels in my grub menu so i can check for differences. By the way have you notice anything between them? i care about recording sound in a studio

Thanks again

---

### Post by snowpine on 2009-10-15
> **s.dalas said:**
> ok thanks a lot. i will keep the 2 kernels in my grub menu so i can check for differences. By the way have you notice anything between them? i care about recording sound in a studio

Thanks again

Last time I tried the rt kernel, it was unstable on my hardware (an old pentium 4 desktop). I would get occasional freezes when switching between apps. The generic kernel was fine for my purposes (recording no more than 2 tracks at a time). I am getting a new computer today and will have to try both to see which works better on the new hardware.

---

### Post by s.dalas on 2009-10-15
ok thanks a lot. 
i am waiting some of the parts for the new pc. then i will try them too. so post back if you want for any observations. 

Stelios

---

### Post by c00kie55 on 2009-10-15
guess the setting is how much off cpu ,harddisk and ram power the user group audio is allowed to use 

i think its working real good (real-time) but i migth depend alot on hardware i mean if you got a proff sound-card it might not be as importen as on build in and cheap soundcards 
on my notebook using intel hdaudio its seams as a world in difference but I had allot off freezes in jaunty this probely varies from computer to computer 

in my case it improved latency by 3 times or more

---

### Post by s.dalas on 2009-10-15
i am setting up the new pc now. yes i have a prof sound card. (outside of the box). i can configure it now using JACK on desktop 9.04. 

in the new pc i am going to put desktop version and install the rt kernel just to see if there is any different. 

i have to make a new group of user "audio" for ex? or i can leave it as it is and just choose between them in grub? if the second choice is possible, i have to make the settings you mention??

Thanks again,
Stelios

---

### Post by Stochastic on 2009-10-15
> **s.dalas said:**
> i dont trust studio though... 

S.Dalas, I'd really love to hear why it is you don't trust Ubuntu Studio.  It'd be great to address those concerns.

---

### Post by s.dalas on 2009-10-15
cause i read and hear that they have hardware compatibility problems, less support than desktop edition and less updates (security, bug fix and other).

i haven't try them. this is what i read and hear around. and there are a lot of these comments, in addition to the most positives for the desktop version...

and by the way can you express your opinion about my problem, cause as an ubuntu member you have a better way of view

Thanks in advance,
Stelios

---

### Post by Stochastic on 2009-10-15
I'd like to try and address your concerns one by one.
**hardware compatibility:** This shouldn't be true, but unfortunately I've seen the odd bug where something works in Ubuntu but doesn't work on Ubuntu Studio.  This could be due to a number of reasons, it could be an issues with the RT kernel compatibility, it could be a problem with their settings, it could be an issue stemming from the install procedure (alternate installer VS graphical installer), lastly it could be a missing library that comes pre-installed with the ubuntu-desktop meta package.
**less support:** Well Ubuntu Studio is a smaller community than the Ubuntu community.  It is however still Ubuntu - same data in the packages, same software download point, etc... so Ubuntu support applies equally to Ubuntu Studio as it does to Ubuntu (there's just a few configuration changes like the RT kernel).  You will, however, find that more musicians and artists using Ubuntu will be running Ubuntu Studio, and thus one could argue that for these purposes Ubuntu Studio actually has ***more support*** than Ubuntu as community members will recommend programs like Ubuntu Studio Controls in their troubleshooting.
**fewer security updates** This is essentially false.  Ubuntu and Ubuntu Studio come from the same repository of software.  That repository is updated with security updates and your computer notifies you when these updates are ready.  The linux-rt package that supplies the RT kernel does recieve less updates than the linux kernel simply because there's a smaller team working behind it.  But in most cases security updates are of other applications than the kernel.  Even then, it's the same linux-rt package in an Ubuntu install with the RT kernel as it is in an Ubuntu Studio install with the RT kernel.  Ubuntu Studio software receives the same security updates that Ubuntu does.

It sounds like a bit of FUD is beginning to circulate about Ubuntu Studio.  I'd just like to nip that in the butt before it becomes widely accepted.

Essentially what Ubuntu Studio comes down to (from a user-end perspective) is a set of multimedia applications, an RT kernel (if the audio meta is installed), a couple minor tweaks under the hood for multimedia, and the Ubuntu Studio Controls application, all loaded ontop the core Ubuntu operating system.  In fact, you can easily install Ubuntu Studio ontop of Ubuntu by following these instructions: [https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy) (they apply to all current Ubuntu versions).

What I recommend is to install Ubuntu Studio on any multimedia production system (I'm slightly biased here as a member of the Ubuntu Studio team).  I personally install the [ubuntu-desktop]("apt:ubuntu-desktop") package in most of my Ubuntu Studio installs simply because I use the same OS for both studio and personal work, and there are a number of packages in the ubuntu-desktop meta that I find very useful.

If you're just starting to install right now, I'd recommend installing Karmic Koala (or doing so once it's released on October 29th).  The RT kernel in 9.10 is an official RT release from upstream, which gives it quite a bit of stability. There are also a lot of software upgrades in Karmic that people have been asking for (Ardour, and Denemo for example).

Whichever install method you choose, I would also recommend installing both the vanilla and the RT kernels. This way if you find a bug/problem/etc.. with one, you can always reboot into the other to see if it's a kernel-specific issue and get on with your work.

Okay, I've typed enough for today.

Hope this helps.

---

### Post by s.dalas on 2009-10-15
your "guide" and your opinions are very useful and i will spend a few minutes before making up my dicision as far i modding the new pc. 

when i was talking for security updates i was talking exactly about this > The linux-rt package that supplies the RT kernel does recieve less updates than the linux kernel simply because there's a smaller team working behind it. and we must always think that the rt kernel is what we most want in a multimedia production system.

for the other 2 as you spoke yourself i was in way right, cause of all these infos and opinions anyone can find.

When you say this > I personally install the ubuntu-desktop package in most of my Ubuntu Studio installs simply because I use the same OS for both studio and personal work, and there are a number of packages in the ubuntu-desktop meta that I find very useful. you mean you install the desktop version inside the studio (like we install kde in a gnome version?) ? and if yes you have the opinion of the kernel choice - rt for studio and generic for desktop?

Thanks again,
Stelios

---

### Post by trulan on 2009-10-15
+1 for going with the 9.10 Karmic RT kernel.  (Still in the testing phase, soon to be officially released!)  I get noticeably better performance on it than on any previous kernels I have used.

It depends on what you want to do as to whether the generic kernel or the rt kernel will be your best option.  The big difference between the two kernels, in my experience, is latency, or how long it takes for a sound to go into your computer, be processed, and return through the headphones/speakers.  I use a Presonus Firepod as my audio interface.  My PC is an AMD64 running at 2.4ghz.  I can cut my stable running latency roughly in half with the rt kernel.  The difference for me is maybe 6 or 7 milliseconds, so as kayosii said the generic kernel does pretty good.  For any serious work, where low latency is important, I strongly recommend at least seriously testing the rt kernel.

+1 for Ubuntu Studio as well, mostly based on looks.  I think its black-oriented theme looks much more professional than Ubuntu's standard browns.  But it is quite easy to install standard Ubuntu, add a few metapackages via Synaptic, and have essentially the same system as a fresh Ubuntu Studio install - in other words, turn regular Ubuntu into Ubuntu Studio.

As far as the desktop goes, Ubuntu Studio and regular Ubuntu both use the Gnome desktop, so they are the same except for some settings, all of which can be tweaked by the user to his own liking.   Or, the Studio metapackages can be installed on top of KDE (Kubuntu) or XFCE (Xubuntu), if you prefer those desktop environments.  But Gnome is the standard.

And thanks to Stochastic and all the Ubuntu Studio team for the great work!!

---

### Post by s.dalas on 2009-10-16
Thank you all of you. i am going to install both of them in different partitions, test them and finally keep the best one for me.
i will post my experience back.

Thanks again all of you for your help,
Stelios

---

### Post by Stochastic on 2009-10-16
I should post that security is important for the linux-rt package, and if any security bug is released/fixed during the life cycle of a particular release that affects the linux-rt package administrators of that bug will release an updated RT kernel.  Most security fixed that are released are of other programs (particularly networking applications & libraries).  The linux-rt package is part of the Ubuntu repository and thus the people monitoring kernels in Ubuntu keep an eye on the RT version too (not just the Ubuntu Studio team).

S.Dalas, I'm glad you're trying them both - you'll learn more that way.  I think you'll find them much more similar than you're making them out to be.  By installing the other kernel, other theme, and other programs in one install, it becomes the other.

Oh, and that [ubuntu-desktop]("apt:ubuntu-desktop") package that is a link in my last post will install that package if you click it from an Ubuntu (or Ubuntu Studio) version of Firefox. (but it's alot of software, take a look here [http://packages.ubuntu.com/karmic/ubuntu-desktop](http://packages.ubuntu.com/karmic/ubuntu-desktop) for info on what that will install).

---

