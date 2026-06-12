---
title: "I give up!"
date: 2013-07-06
forum: Ubuntu, Linux and OS Chat
---

### Post by mikodo on 2013-07-06
I have been reading the threads like the ones below, and as a casual user of 5 year experience with computers, I really am afraid for my beloved Xubuntu.

So, I am going to hedge my bets and install different distros with Xfce DE's, to become familiar with them, before things start changing/breaking (if they do).

[https://bugs.launchpad.net/mir/+bug/1149581](https://bugs.launchpad.net/mir/+bug/1149581)

[http://ubuntuforums.org/showthread.php?t=2127165](http://ubuntuforums.org/showthread.php?t=2127165)

[http://ubuntuforums.org/showthread.php?t=2158180](http://ubuntuforums.org/showthread.php?t=2158180)

There have been many other related subjective articles/blogs/threads I have read, too. Those are only examples.

I'm not reading them anymore, though doing so has been enlightening. I am going to use my limited time with my computer learning other things. I don't like worrying.

We'll see what washes out in the wash.

Plan:

Two new drives.

SSD = for booting and installing different distros, root installs.

Larger Platter = for data partition to symlink with the root/mnt/ installs.

'tis going to be fun!

---

### Post by MadmanRB on 2013-07-06
I would not worry about Mir, for Xubuntu I doubet it will effect aanything.
Same with Kubuntu.
Ubuntu itself will still probably ship x, Mir will take some time to adopt.

---

### Post by EgoGratis on 2013-07-06
> So, I am going to hedge my bets and install different distros with Xfce  DE's, to become familiar with them, before things start  changing/breaking (if they do).

Or wait to actually see some braking and then act. That could be sane strategy IMO too.

---

### Post by MadmanRB on 2013-07-06
Mir has not even become out of the door yet either, like I said I doubt it will break anything right off.

---

### Post by Elfy on 2013-07-07
> **mikodo said:**
> I have been reading the threads like the ones below, and as a casual user of 5 year experience with computers, I really am afraid for my beloved Xubuntu.

So, I am going to hedge my bets and install different distros with Xfce DE's, to become familiar with them, before things start changing/breaking (if they do).

[https://bugs.launchpad.net/mir/+bug/1149581](https://bugs.launchpad.net/mir/+bug/1149581)

[http://ubuntuforums.org/showthread.php?t=2127165](http://ubuntuforums.org/showthread.php?t=2127165)

[http://ubuntuforums.org/showthread.php?t=2158180](http://ubuntuforums.org/showthread.php?t=2158180)

There have been many other related subjective articles/blogs/threads I have read, too. Those are only examples.

I'm not reading them anymore, though doing so has been enlightening. I am going to use my limited time with my computer learning other things. I don't like worrying.

We'll see what washes out in the wash.

Try going to the next Xubuntu dev meeting - see what get's talked about there, jono is coming at the beginning to discuss Mir.

[https://lists.ubuntu.com/archives/xubuntu-devel/2013-July/009043.html](https://lists.ubuntu.com/archives/xubuntu-devel/2013-July/009043.html)

It gets logged as well - so you can catch up later if you can't make it

---

### Post by mJayk on 2013-07-07
Nothing wrong with, and probably most sane, learning more than one distro.  Ubuntu is brilliant at getting people into linux but there is much more out there to play with.

---

### Post by Erik1984 on 2013-07-07
> **EgoGratis said:**
> Or wait to actually see some braking and then act. That could be sane strategy IMO too.

Exactly. I see the same with Kubuntu. There are a lot of politics and drama involved in the current discussion which could make you think your desktop is going to explode any minute now ;) But for everyday users it's not that *buntu will suddenly stop working tomorrow. Just see from version to version if it still works. 

@mikodo 
Your profile says you are running 12.04 so you should be safe untill april 2017 :P

---

### Post by monkeybrain2012 on 2013-07-07
I totally understand though I like Unity, so I have more reasons to worry than you do (xubuntu is probably not going to switch to Mir anytime soon) The roadmap is kind of crazy from what I see now. They are going to default to xmir and with x fallback (hopefully it works!) in 13.10 and remove x fallback in 14.04 LTS. 

I hope the roadmap is just for setting goals and rallying the troops and they will be more pragmatic and sane at actual release time instead of forcing something half baked on a LTS and killing Ubuntu's dispaly and reputations. That happened  before, they promised feature x  in release y and  then there was no x when y came out, they  deferred it to release y + 1 and then y + 2 because they couldn't get x in good working shape. If that could happen with something relatively trivial like  scopes and lenses it would be more likely to happen with something vastly more complicated like the display server.

If 13.10 doesn't work out my fallback is 12.04 (it is kept very up to date with the newest kernel and software from ppa and self compiled) and/or Fedora, which I have gotten to be very comfortable with and can do most things I do in Ubuntu if with a little more work.

---

### Post by Tamlynmac on 2013-07-07
> mikodo

I must agree with mJayk.
 > Ubuntu is brilliant at getting people into linux but there is much more out there to play with.

I've continued testing other XFCE distros, looking for stability and  compatibility since first installing Xubuntu (won't discuss my opinions  here, as I have no desire to debate them). The three listed below have  all exhibited OOTB stability and functionality on all the systems I've  tried - including the desktops. The only issue I ran into was with  wifi in Vector Linux which was related to driver installation. But did  get it working. Due to the varying levels of experience in the circle of  users that rely on my assistance, I prefer Saline. But, I suggest one  try numerous candidates before limiting their focus to any particular  distro.

[SalixOS]("http://www.salixos.org/wiki/index.php/Home")
[SalineOS]("http://www.salineos.com/")
[VectorLinux]("http://www.vectorlinux.com/")

One of, if not the best part of Linux IMHO is - choice.

 Good Luck

---

### Post by mikodo on 2013-07-07
> **Euroman said:**
> 
Your profile says you are running 12.04 so you should be safe untill april 2017 :P
Thank you everyone, for the responses and advice. 

It is a thorny subject on the display issue. I spent a little time on #xubuntu-devel talking with some of the devs. So, upstream Xfce is not leaving Xorg. It appears to remain undecided, if Xubuntu will use XMIR (or presumably, stay with Xorg for now). 

@ elfy  This next [#ubuntu-devel meeting]("https://wiki.ubuntu.com/Xubuntu/Meetings") with Jono Bacon, is promised to be interesting. Thanks, for the tip.

@ Euroman  Xubuntu 12.04 LTS is for 3 years, as they deviated from the other flavors. (FYI) Maybe Xubuntu will stay with X11 with Xubuntu 13.10 & 14.04 LTS, which would give it at least another 3 more years of X11 after that, if not 5 more years this time. I read on Kubuntu Forums, that they are going with X11 on 13.10 and 14.04 LTS and then hope to use Wayland, after that.

---

### Post by Elfy on 2013-07-08
> **mikodo said:**
> ...
@ elfy  This next [#ubuntu-devel meeting]("https://wiki.ubuntu.com/Xubuntu/Meetings") with Jono Bacon, is promised to be interesting. Thanks, for the tip.
...

From my logs I see you now know as much as we do :)

---

### Post by Erik1984 on 2013-07-08
> **mikodo said:**
> Thank you everyone, for the responses and advice. 

It is a thorny subject on the display issue. I spent a little time on #xubuntu-devel talking with some of the devs. So, upstream Xfce is not leaving Xorg. It appears to remain undecided, if Xubuntu will use XMIR (or presumably, stay with Xorg for now). 

@ elfy  This next [#ubuntu-devel meeting]("https://wiki.ubuntu.com/Xubuntu/Meetings") with Jono Bacon, is promised to be interesting. Thanks, for the tip.

@ Euroman  Xubuntu 12.04 LTS is for 3 years, as they deviated from the other flavors. (FYI) Maybe Xubuntu will stay with X11 with Xubuntu 13.10 & 14.04 LTS, which would give it at least another 3 more years of X11 after that, if not 5 more years this time. I read on Kubuntu Forums, that they are going with X11 on 13.10 and 14.04 LTS and then hope to use Wayland, after that.

I forgot about the 3 years for some derivatives. But still I consider this a 'problem' for the long term.

---

### Post by buzzingrobot on 2013-07-08
Don't worry about the pudding until it's out of the oven. :)

And, you don't need to eat the pudding unless you want to.

Nothing needs to happen to the software on your machine unless you allow it.

---

### Post by Tamlynmac on 2013-07-08
> buzzingrobot
Don't worry about the pudding until it's out of the oven.

I  would disagree with this philosophy, preferring to be informed and  aware of what's available. Not to mention what would work for both my  user requirements and systems should the need arise.

I believe  all Linux users should investigate alternative distros and software periodically. A number of apps I use aren't installed OOTB and finding  those that best meet my needs/demands required some effort. Plus, new  Linux software is released regularly and without testing I may miss an  opportunity.  

 Historically, the wait & see mentality has rarely (if ever) benefited me.

---

### Post by buzzingrobot on 2013-07-09
> **Tamlynmac said:**
> I  would disagree with this philosophy, preferring to be informed and  aware of what's available...


Sure, stay informed, but knowing that Canonical is working on Mir or that other people are working on Wayland doesn't mean anyone needs to change the software they're using *now*.

I've used Linux for almost 20 years and long ago decided that changing what I do now because someone else plans to change a piece of that  software, some time in the future, is not necessary. 

Mir may turn out to be amazing, Or, awful. Probably somewhere in between, like most software.  Ditto Wayland.  X might be overhauled.  A fourth contender might show up.  Who knows? None of it has happened yet.

When Canonical releases Ubuntu with Mir, I'll boot a live image and take a look. I'll read credible unbiased evaluations (assuming I can find any). If I think it's the best choice for me, I'll install it. If not, I'll stay with what I have until something better comes along.

---

### Post by cortman on 2013-07-09
Try Debian. There is a slightly larger learning curve depending on your hardware, but I've always had great luck with it (even installing extra, non-free firmware required by my wireless card during the installation was a complete breeze). Debian is less crufty as well and far more stable. The main disadvantage I see is that you won't get as late package versions as you would with Ubuntu unless you run unstable.

---

### Post by mikodo on 2013-07-09
> **cortman said:**
> Try Debian. There is a slightly larger learning curve depending on your hardware, but I've always had great luck with it (even installing extra, non-free firmware required by my wireless card during the installation was a complete breeze). Debian is less crufty as well and far more stable. The main disadvantage I see is that you won't get as late package versions as you would with Ubuntu unless you run unstable.
I have Wheezy installed with Xfce. I like it.

I am going to install others and then pick a select few to maintain and learn about.  For me, Debian is a given.

Thanks.

---

### Post by mikodo on 2013-07-09
> **Tamlynmac said:**
> I must agree with mJayk.
 

I've continued testing other XFCE distros, looking for stability and  compatibility since first installing Xubuntu (won't discuss my opinions  here, as I have no desire to debate them). The three listed below have  all exhibited OOTB stability and functionality on all the systems I've  tried - including the desktops. The only issue I ran into was with  wifi in Vector Linux which was related to driver installation. But did  get it working. Due to the varying levels of experience in the circle of  users that rely on my assistance, I prefer Saline. But, I suggest one  try numerous candidates before limiting their focus to any particular  distro.

[SalixOS]("http://www.salixos.org/wiki/index.php/Home")
[SalineOS]("http://www.salineos.com/")
[VectorLinux]("http://www.vectorlinux.com/")

One of, if not the best part of Linux IMHO is - choice.

 Good Luck
Thanks, for the tips. I'll be installing those to try out.

---

### Post by su:bhatta on 2013-07-10
> **cortman said:**
> Try Debian. There is a slightly larger learning curve depending on your hardware, but I've always had great luck with it (even installing extra, non-free firmware required by my wireless card during the installation was a complete breeze). Debian is less crufty as well and far more stable. The main disadvantage I see is that you won't get as late package versions as you would with Ubuntu unless you run unstable.

I would +42 that anyday... Debian +Xfce works gr8.....

---

### Post by mastablasta on 2013-07-10
> **cortman said:**
>  Debian is less crufty as well and far more stable. The main disadvantage I see is that you won't get as late package versions as you would with Ubuntu unless you run unstable.

Debian 7.0 doens't have so much older packages. i would say it is on par with ubutnu 12.04. maybe a few are a bit older but mostly it's arround there. someitmes stability is more important that fancy new programmes. 

also Chrunchbang (debian based) makes it very easy to install and offers a few newer packages via scripts after install is done.

---

### Post by cortman on 2013-07-10
> **mikodo said:**
> 
I am going to install others and then pick a select few to maintain and learn about.

Can't +1 this enough- good luck. :)

---

### Post by vasa1 on 2013-07-10
> **Elfy said:**
> Try going to the next Xubuntu dev meeting - see what get's talked about there, jono is coming at the beginning to discuss Mir.

[https://lists.ubuntu.com/archives/xubuntu-devel/2013-July/009043.html](https://lists.ubuntu.com/archives/xubuntu-devel/2013-July/009043.html)

It gets logged as well - so you can catch up later if you can't make it

Is the log made available automatically or does some have to do it? It isn't [here]("http://ubottu.com/meetingology/logs/xubuntu-devel/2013/") at this moment.

---

### Post by mikodo on 2013-07-11
> **vasa1 said:**
> Is the log made available automatically or does some have to do it? It isn't [here]("http://ubottu.com/meetingology/logs/xubuntu-devel/2013/") at this moment.
The meeting isn't for another 9 hours, at the time of my writing this. I assume it will be logged and listed on the page you linked, after it is over.

---

### Post by vasa1 on 2013-07-11
> **mikodo said:**
> The meeting isn't for another 9 hours, at the time of my writing this. I assume it will be logged and listed on the page you linked, after it is over.
Oops! Thanks for that! BTW, do you know how can we access the meeting live using a browser?

---

### Post by Elfy on 2013-07-11
Logs for all logged ubuntu channels are always here [http://irclogs.ubuntu.com](http://irclogs.ubuntu.com)

The logs for some projects and meetings are sometimes kept on wiki's - our meeting will be there afterwards, note that I'm not saying immediately ;)

You can use freenode webchat to get to the channel 

[http://webchat.freenode.net/?channels=xubuntu-devel](http://webchat.freenode.net/?channels=xubuntu-devel)

---

### Post by Elfy on 2013-07-11
[http://irclogs.ubuntu.com/2013/07/11/%23xubuntu-devel.html#t15:01](http://irclogs.ubuntu.com/2013/07/11/%23xubuntu-devel.html#t15:01)

[http://ubottu.com/meetingology/logs/xubuntu-devel/2013/xubuntu-devel.2013-07-11-15.00.html](http://ubottu.com/meetingology/logs/xubuntu-devel/2013/xubuntu-devel.2013-07-11-15.00.html)

---

### Post by vasa1 on 2013-07-11
Nice meeting :)

---

### Post by mikodo on 2013-07-11
> **Elfy said:**
> [http://irclogs.ubuntu.com/2013/07/11/%23xubuntu-devel.html#t15:01](http://irclogs.ubuntu.com/2013/07/11/%23xubuntu-devel.html#t15:01)

[http://ubottu.com/meetingology/logs/xubuntu-devel/2013/xubuntu-devel.2013-07-11-15.00.html](http://ubottu.com/meetingology/logs/xubuntu-devel/2013/xubuntu-devel.2013-07-11-15.00.html)
^^These are easier to read. Thanks.

---

### Post by slickymaster on 2013-07-11
> **vasa1 said:**
> Nice meeting :)

+1
Indeed.

---

### Post by Elfy on 2013-07-12
> **vasa1 said:**
> Nice meeting :)

> **mikodo said:**
> ^^These are easier to read. Thanks.

Thanks :)

---

### Post by mr john on 2013-07-12
As mentioned above, Mir is going to be in the next Ubuntu. There will be fallback for X though if it doesn't work on people's computers. It's going to happen sooner than some people think.

---

### Post by mips on 2013-07-12
> **mr john said:**
> As mentioned above, Mir is going to be in the next Ubuntu. There will be fallback for X though if it doesn't work on people's computers. It's going to happen sooner than some people think.

It's going to be disastrous for some of the ubuntu derivatives as upstream is not ready or interested in it.

---

### Post by monkeybrain2012 on 2013-07-12
> **mr john said:**
> As mentioned above, Mir is going to be in the next Ubuntu. There will be fallback for X though if it doesn't work on people's computers. It's going to happen sooner than some people think.

Provided the fallback works.

---

