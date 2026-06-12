---
title: "Issues with 13.04"
date: 2013-04-15
forum: Ubuntu Development Version
---

### Post by ryanvade on 2013-04-15
Well. I am <snip>. I installed 13.04 and I can't do anything with it.  

First  off, I installed firefox-nightly, preload, unity tweak, gnome tweak  tool, ubuntu tweak, bumblebee and ccsm. That is all the programs I installed. I  have completely Updated the system.  

Now, the issues:

1. I can't change the wallpaper.  It is stuck on a Silver/White color. According to system settings it is correct. 
2. System Settings changed.  At first it had Ubuntu tweak, Appearance, etc. Now it is missing items. 
3. About Computer says this version of ubuntu is 3.8.0
4. Ubuntu tweak won't start. 
5. Unity tweak settings are not permanent. 
6. Half of the programs I have installed crash. 
7. Software center won't start. 
8. I can't change the unity "Panel". The Power Settings "Battery Monitor" is missing. 
9. Ubuntu One keeps starting at login. I have repeatedly checked "Do not start at start up"
10. Unity keeps crashing. 
11. Compiz is not installed at default.  It is now even more buggy. 
12. File Permission are wrong. 
13.  I can't change themes. 
14. I can't change Icons. 
15. During start up, grub was not completely installed. I had to install it later. 


I tried removing the programs I installed except firefox-nightly and Bumblebee. It did not help. I reinstalled and did not install the programs and got the same effects. I am a moderator at 2 different Linux forums, I cannot honestly recommend this to anyone unless SERIOUS fixes are released.

---

### Post by dino99 on 2013-04-15
a few things you need to understand:
- if you take the risk to play with the latest bleeding edge packages, then you need to be able to find what is wrong. To help you, the first places to glance at are the logs, then browse the u+1 forum (some of your issues have been already discussed, and workarounds have been found)
- what you have installed is not supported as u+1 : gnome 3.8 is not the stock raring
- before beeing able to be a "moderator", you also need to be first a "confirmed" user.

---

### Post by grahammechanical on 2013-04-15
I am shocked that a 'moderator' would use swear words.

Compiz is installed by default. It is the compositor/window manager. Without Compiz Unity would not work. What are not installed by default are seriously powerful (can break things) utilities such as Compiz Configuration Settings Manager and Unity Tweak and Ubuntu tweak and other such tools.

Why are these not installed by default? Because from the beginning it was intended that Ubuntu be Linux for ordinary people. Now, here is a strange thing. When I search the Ubuntu Software Centre for Ubuntu Tweak it is not there. We have Unity tweak in the repositories but not Ubuntu tweak. How did you install Ubuntu tweak? Is it compatible with Ubuntu 13.04? Is this why your system is so messed up. In fact there is not a version of Ubuntu Tweak for Raring Ringtail. The last version was for Quantal.

I also note that Unity Tweak is at version 0.0.4. So, it is still very much under development. And we are told: Canonical does not provide updates for Unity Tweak Tool. These kind of things are community software and Ubuntu cannot be held responsible for their failures. There is a reason why some things are not installed by default. They have a large potential to break the OS.

Anyway, congratulations, you finally found what you were looking for. Something to complain about.

Would a genuine moderator please move this thread to the section called Ubuntu, Linux and OS chat.

---

### Post by cariboo on 2013-04-15
I'd suggest we wait to see if the op actually comes back to explain how he did what he claims to have done, or if this is just a complaint that isn't looking to solve any problems.

---

### Post by mcellius on 2013-04-15
Ryanvade,

I also installed Ubuntu 13.04 on my laptop (I assume you put yours on a laptop because you say you're missing the power indicator), and I have had exactly none of the problems you're experiencing.  You report so many problems that it appears that something must be seriously wrong.  Have you checked to make sure that the 13.04 ISO you downloaded doesn't have errors?  What sort of machine did you install it on, and what sort of hardware is in it?  My own experience has been that 13.04 has been extremely stable and solid, and has had very few errors (even though it's still in testing), and many others report the same; there has to be a reason why your experience has been so different and so far out of the norm.

---

### Post by mc4man on 2013-04-15
It appears you installed the ubuntu-gnome image & then upgraded to gnome-3.8 in some fashion (gnome3 ppa(s)?
Hard to say because you've left that info out.
If you're using the ppa(s) then likely you updated from them incompletely (use sudo apt-get dist-upgrade

If intending to use gnome-shell, gnome-3.8 in 13.04 from ppa's I wouldn't bother with compiz/unity, not a good deal atm.
Plus you mentioned 'preload', could also be a factor.

I'd dump that install & either go the ubuntu-gnome image/gnome3 ppa's route or install from the 13.04 daily & use unity/compiz
Your  'issue' with grub is also not normal.

---

### Post by ryanvade on 2013-04-15
woah, slow down guys. I did not mean to start anything.  As for the cuss words, I did not think THAT was a curse. Sorry. I would have corrected if no one else did. THANK YOU cariboo907

As for my stuff.  I checked the MD5SUM of the image after download. Ubuntu tweak is from tualatrix next. I did not add any extra GNOME ppa's.  There is a list of all the ppas on my system attached to this post. (including MATE. But that is not installed yet. ) I have not changed any settings in Unity tweak. I installed ccsm (sorry. I meant ccsm in my first post) for desktop cube and wobbly windows. Those are the only changes I made there. No other system settings are changed.  Very weird for me. I never had these kinds of issues with other Ubuntu Beta releases. Alpha yes, beta no.  I am not looking for answers. I am really checking to see if anyone else has these issues. Apparently not.  I do know at least 3 others with the same issues.  Not exactly an isolated problem, but not wide spread. 

I installed KDE 4.10.2 and that works GREAT!!! It must be Unity.  I will remove the tweak tools and see what happens.    Sorry to have started anything. 

ryanvade


*NOTE 
For some reason there was a double posting. Sorry. I can't remove the other post. [ATTACH]241426[/ATTACH]

---

### Post by mcellius on 2013-04-15
I have been using Unity exclusively since testing 13.04 (right after 12.10 was released) and have rarely had any problems with it.  I'm not denying the problems you've had, but for me it's been about as stable as could be.  Since the MD5SUM of your download checks out, there must be something different about your hardware: what do you have?  Mine is an off-the-shelf Dell Studio 1535, no hardware changes at all.

---

### Post by ryanvade on 2013-04-15
mcellius, I am using an HP DV6T-7000 CTO.  I5-2450m, 6GB ram, Intel HD 3000, Nvidia GT 630m. Dual Boot with Windows 7, UEFI, GRUB installed to Linux partition. EasyBCD added 13.04 to Windows boot manager. 

To all. I really did not mean to make anyone angry. I just wanted to give my opinion and show what issues I am having. [ryanvade @ Oz Unity Forums]("https://www.ultimateeditionoz.com/forum/viewtopic.php?f=199&t=5133")

---

### Post by kuvanito on 2013-04-15
> **mcellius said:**
> I have been using Unity exclusively since testing 13.04 (right after 12.10 was released) and have rarely had any problems with it.  I'm not denying the problems you've had, but for me it's been about as stable as could be.  Since the MD5SUM of your download checks out, there must be something different about your hardware: what do you have?  Mine is an off-the-shelf Dell Studio 1535, no hardware changes at all.

i am with you there except for skype any version and my INTEL pc (no window buttons) regardless of any work around

---

### Post by cariboo on 2013-04-15
Removed the first double post as the op added info to the second.

---

### Post by mc4man on 2013-04-15
> **ryanvade said:**
>  I did not add any extra GNOME ppa's.  There is a list of all the ppas on my system attached to this post.     Sorry to have started anything. 

ryanvade


> **ryanvade said:**
> Well. I am <snip>. I installed 13.04 and I can't do anything with it.  

First  off, I installed firefox-nightly, preload, unity tweak, gnome tweak  tool, ubuntu tweak, bumblebee and ccsm. That is all the programs I installed. I  have completely Updated the system.  

Now, the issues:

3. About Computer says this version of ubuntu is 3.8.0
10. Unity keeps crashing. 
11. Compiz is not installed at default.  It is now even more buggy. 

No big deal & glad you did a re-install & found something that works.
What was & remains curious about your orig. post are the 3 points above, particularly #3. I don't see anyway that an ubuntu install without the gnome3 ppa(s) would report  3.8.0, though it will after upgrading from those ppa's
#10 would be not unexpected if upgrading **Ubuntu 13.04 **to the gnome3 ppa(s), especially if not done completely.
#11 makes no sense unless you mean either ccsm, or you used the ubuntu-gnome image

The attached list of ppa's does show gnome3 ppa enabled - 
"ppa.launchpad.net/gnome3-team/gnome3/ubuntu raring"

---

### Post by ryanvade on 2013-04-15
I noticed the 3.8 repos too.  very odd.  I reinstalled and they were back.  odd.  I removed them during a reinstall. Everything seems to be fine now. I just don't understand how those repos got there. I will everyone know to remove those repos if they decide to install standard ubuntu 13.04.  Very strange....

Again, I do apologize for what I said. I reinstalled some 20+ times before I noticed the Gnome-3 repos. I was being stupid. 
Thanks all.

---

### Post by mcellius on 2013-04-15
I don't think you were being stupid, and I think we can all see how what happened would be very frustrating.  On the other hand, you should know that what happened to you isn't something that many other people have seen, and I had certainly never heard of it.  It is a pre-release version so bugs are to be expected, but this one really does seem odd.  I'm glad you were able to solve it.

---

### Post by VinDSL on 2013-04-15
As a side note...

It **IS** possible to run Unity 7 on top of Gnome 3.8.  I do it all the time, but there's a trick to it.

[LIST=1]
[*]Start a GS session
[*]Don't allow Nautilus to manage the desktop
[*]Open a terminal window and replace GS with Unity
[/LIST]

Simple pimple! ;)

---

### Post by PJs Ronin on 2013-04-15
> **VinDSL said:**
> As a side note...

It **IS** possible to run Unity 7 on top of Gnome 3.8.  I do it all the time, but there's a trick to it.

[LIST=1]
[*]Start a GS session
[*]Don't allow Nautilus to manage the desktop
[*]**Open a terminal window and replace GS with Unity**
[/LIST]

Simple pimple! ;)
You could explain this for those of us who are slow on the uptake (read: noob)?

---

### Post by mc4man on 2013-04-16
> **ryanvade said:**
> I noticed the 3.8 repos too.  very odd.  I reinstalled and they were back.  odd.  I removed them during a reinstall. Everything seems to be fine now. I just don't understand how those repos got there. I will everyone know to remove those repos if they decide to install standard ubuntu 13.04.  Very strange....
 I reinstalled some 20+ times before I noticed the Gnome-3 repos. 

Can't see any ppa being 'self/auto/whatever' enabled in a fresh 13.04 or fresh any version install.
So if you didn't directly then I'd look at ubuntu-tweak

---

### Post by cariboo on 2013-04-16
The other thing to keep in mind is that ppas can't be added without entering your password, unless you are running as root at the time, in which case almost anything can be installed without you knowing it.

---

### Post by VinDSL on 2013-04-16
> **PJs Ronin said:**
> You could explain this [...]
Sure...

I'm logged into a Gnome-shell 3.8 session, right now.


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-16-apr-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-16-apr-2013-1.png")[/INDENT]


Make sure that the file manager is NOT handling the desktop (disable in gnome-tweak-tool)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-16-apr-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-16-apr-2013-2.png")[/INDENT]



Open a terminal window and type:  
```
unity --replace &
```

At some point, while Unity is loading, the dialog will stop.  When that happens, close the terminal, and the process will complete.


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-16-apr-2013-3(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-16-apr-2013-3.png")[/INDENT]



That's it...

---

### Post by ryanvade on 2013-04-16
> **cariboo907 said:**
> The other thing to keep in mind is that ppas can't be added without entering your password, unless you are running as root at the time, in which case almost anything can be installed without you knowing it.


To add a ppa the user has to be in the sudoers file.  Yes I know.  For some reason it is in the original image.  The ppa is active when running live. I really don't know why.

---

### Post by cariboo on 2013-04-16
> **ryanvade said:**
> To add a ppa the user has to be in the sudoers file.  Yes I know.  For some reason it is in the original image.  The ppa is active when running live. I really don't know why.

Where are you getting your iso from? This is the preferred place to download the Ubuntu iso from:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

For Ubuntu Gnome get it from here:

[http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/)

---

### Post by ping-wu on 2013-04-16
> **mcellius said:**
> Ryanvade,

My own experience has been that 13.04 has been extremely stable and solid, and has had very few errors (even though it's still in testing), and many others report the same

Ditto here.  I have 13.04 beta2 (updated) running side-by-side 12.04.2LTS (also updated).  Even though 13.04 is only beta, it appears to be even more stable than 12.04.2 LTS.

---

### Post by ping-wu on 2013-04-16
> **ryanvade said:**
>  I was being stupid.

I have to take issue with your comment.  You are NOT stupid.  We appreciate your taking time to report your experience.  That's how we grow.

---

### Post by ryanvade on 2013-04-16
[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

---

### Post by mc4man on 2013-04-16
> **ryanvade said:**
>   For some reason it is in the original image.  The ppa is active **when running live**. I really don't know why.
No, not possible
screen, beta2 live session

---

### Post by ryanvade on 2013-04-16
Well I did not add it. I did not install any new software during live system. And when I looked at the software sources in Update Manager it showed the Gnome-3 repos. It is really no big deal now though.

---

