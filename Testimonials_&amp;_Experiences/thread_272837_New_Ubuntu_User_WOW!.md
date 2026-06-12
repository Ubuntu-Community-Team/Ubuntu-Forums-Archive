---
title: "New Ubuntu User: WOW!"
date: 2006-10-07
forum: Testimonials &amp; Experiences
---

### Post by russell.h on 2006-10-07
I first became interested in Linux because my highschool robotics club, which I was president of and lead programmer for at the time was considering building a robot based around a small computer running linux.

In order to prepare for that project I began investigating various distributions. The most knowledgeable IT guy in our school district had SuSE running on a few servers, including one he was maintaining for robotics, so I decided to go with that. As a windows user I found it fairly easy to install, but had constant difficulties with drivers and networking.

When we actually went to build the robot our Linux expert suggested Slackware as a nice light and versatile distribution. I never really used it much, since I fairly promptly fried the motherboard, but my general impression was that it was not for the faint of heart, or generally for anyone who didnt want to spend 2/3 of their life manually configuring their graphics drivers, etc.

So since christmas I have been back to running windows mainly, with a SuSE machine off somewhere in the basement hosting some files, and generally wasting electricity.

Now all of a sudden I got the idea that I want to start using Linux again. Just a few hours ago now I downloaded Ubuntu 6.06.1 x86 desktop, a 30 minute bittorrent download. I especially liked the fact that it all fit on once CD. If I recall SuSE was 6 CDs which had to be constantly swapped out during install.

So after a fairly painless install (all the pain was caused by the motherboard, nothing related to Ubuntu at all) I had Ubuntu running. While it was installing I was installing a new printer on my windows network. So, while I dont expect to be doing much printing from the linux box, I figured I would just see what it takes to make it see my printer. In short, it took about 30 seconds, most of which I spent waiting for the little old hard drive to spool up.

Wow! Then I discovered that I could actually browse my shared windows files without having to configure any sambas or anything. Just point and click!

This is far and away the best experience I have ever had with any distro (thus far SuSE, slackware, and a brief stint with debian).

I was just so blown away by the ease of use that I figured I should go tell someone about it. Of course I guess I'm not telling anyone here anything new, but seriously [SIZE="3"]Ubuntu Rules!![/SIZE]

---

### Post by lemonsCC on 2006-10-07
Welcome to the club!

Umm 6 CDs for SuSE????  Are they insane 4.2 gigs!!!

---

### Post by Jiraiya_sama on 2006-10-07
congratulations russel, you should however consider upgrading to ubuntu 6.10 edgy eft when it comes out in the next few weeks. It's even easier to run than dapper, and has a lot of new features.

---

### Post by russell.h on 2006-10-07
I just checked, with SuSE you can either download 6 CDs (which for some reason are not all even close to 700mb), one 2.9GB DVD, or do a net installation which is basically the same thing as Ubuntu does. At the time I was paying $5/gig for every GB over 5 per month, and since I was looking at putting it on several computers I went with the full download.

Still, the Ubuntu installation was way easier, and its nice being able to use the installation cd as a live cd. 

I just set up the graphics drivers (nvidia-glx-legacy). Since the graphics card is so old I had all kinds of trouble doing this with SuSE, and it turned out that in the end I had to completely redo it all whenever any update affected graphics. With Ubuntu I did end up having to manually edit xorg.conf for some reason, but the whole procedure took me about 2 minutes, as compared to half an hour in SuSE.

When 6.10 comes out is there a way to just update without having to totally reinstall?

---

### Post by GStubbs43 on 2006-10-07
> **russell.h said:**
> 

When 6.10 comes out is there a way to just update without having to totally reinstall?

Yup, ```
sudo aptitude update && sudo aptitude dist-upgrade
``` should do it I believe. :mrgreen:

---

### Post by Jiraiya_sama on 2006-10-07
he would need to alter his repos too wouldn't he?

> With Ubuntu I did end up having to manually edit xorg.conf for some reason, but the whole procedure took me about 2 minutes, as compared to half an hour in SuSE.

I don't know if it works with nvidia-glx-legacy but generally all you need to do to set up the xserver is type ```
sudo nvidia-xconfig
``` into the command line.

---

### Post by livingtarget on 2006-10-08
> **russell.h said:**
> Just a few hours ago now I downloaded Ubuntu 6.06.1 x86 desktop, a 30 minute bittorrent download. I especially liked the fact that it all fit on once CD. If I recall SuSE was 6 CDs which had to be constantly swapped out during install.

Yes this is a factor that's pretty good. When I first got into linux I was running RedHat, then RedHat became Fedora. So after a while I wanted to upgrade.

I download 3 discs of Fedora and decided to download the single Ubuntu disc as well just in case. Fedora has 3 cd's and your base install usually has a dozen or so programs that I just want to throw out of the window. So I ditched Fedora, slammed in the Ubuntu disc and that was the end of that. Uncomplicated bliss.

The factors that initially held me back from Ubuntu were: text install (pre-dapper) and the fact that it was the new kid on the block. It surely couldn't be that good? WRONG! :) It's great.

---

