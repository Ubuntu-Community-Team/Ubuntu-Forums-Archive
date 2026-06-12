---
title: "UBUNTU 8.04: Big disappoinment"
date: 2008-04-25
forum: Testimonials &amp; Experiences
---

### Post by xferaa on 2008-04-25
I'm a Ubuntu user since first versions.

After testing so many distros for a long time, I was quite happy that at last there was a desktop version of Linux that would work almost without any problem and was easy to use for beginners but keeping all the power that linux can offer.

I liked a lot that most of the hardware was detected and configured properly (no more dealing with compiling drivers or kernels just for something to work) and that the system was stable enough having the latest open source software (which was the only way to move $$Windows$$ users to freedom).

Well, yesterday after installing new version, I had the feeling that I was back to those days when linux was far from a operating system for everyone and were likely to end up going into bed at 5am with a big headache after been trying to configure the system to support your latest and nice graphic card.

I found among other things this issues after installing ubuntu:

- Repositories were either not working or very slow (meaning that the installation will take a lot lot lot time to configure apt)

- System is quite slow compared to old versions (lots of unnecessary services and app's running as default from the beginning)

- Evolution server process took my CPU to 80% most of the times I started ubuntu (having to kill the process to be able to for example, surf the web)

- Firefox 3.0 (Even slower than older version, why use the beta already in a production system??? Marketing may be???)

- One of the most annoying things was that I was unable to mount NTFS partitions from external usb devices. (There is a permission issue with ntfs-3g)

- Also I activated restricted drivers for my ATI card as usual and when I restarted resolution was set to something like twice the resolution supported by my monitor (having to edit xorg config files by hand)

- Desktop image and icons will not appear randomly sometimes when you start gnome (having to log out and back again for them to appear)

- Apt-get gives an error when updating repositories because is unable to access /restricted Translation-en_US and some others, so installing an application using apt is almost impossible.


Probably, some or most of this issues happend to me or a few people only or just because of my specific hardware configuration) but I really doubt that everyone that installed ubuntu did not have to deal at least with one of the issues above (or others I did not encour)

Ubuntu team should prepare and check more the distro before releasing it and if the servers cannot handle all the load that is required for the amount of users that are going to download/install this. They should find an alternative solution or improve their networks before releasing it. I'm sure that I like many others, we wouldn't mind to donate some money for servers if needed.

So now the question is? It is worth to fix all that issues and keep using ubuntu hoping that in the future things will get better or should I go back to the good old debian?


I'd like to hear your comments :)


Thankx!

PD: Sorry for my bad english

---

### Post by Joeb454 on 2008-04-25
Sorry to hear you've had a bad experience. I've had no issues with Hardy whatsoever. It all worked "out the box" on my machines (except 1 with an Nvidia card, need to install with safe graphics mode).

For me it runs great - far better than Gutsy :)

---

### Post by Mazza558 on 2008-04-25
I agree with you on ATi - the drivers this time around are extra-awful. I have no other problems with Hardy though.

---

### Post by acelin on 2008-04-25
Sounds like you have really bad luck. I had none of these problems whatsoever.

---

### Post by K.Mandla on 2008-04-25
Moved to Experiences and Testimonials.

---

### Post by ShadowGray on 2008-04-25
The repos and apt-get problems can be explained by the fact that it's release week.  The servers are flooded... everything is going to be slow.

And every new release of every program is going to have flaws, you can't possibly predict every single condition that the program is going to be run on and what bugs you'll encounter.  At least it wasn't a mess like Vista or ME.

So, stop trolling, if you don't like ubuntu, find another distro.  Otherwise, weather through the small kinks here and there.

Plus, if you really wanted stability, why get an OS on the day of release.  Technically, the smart thing to do is to at least wait a month.

---

### Post by FuturePilot on 2008-04-25
> - Repositories were either not working or very slow (meaning that the installation will take a lot lot lot time to configure apt)

Everyone is trying to download/upgrade Ubuntu. A server can only handle so much traffic at a time.

> - Evolution server process took my CPU to 80% most of the times I started ubuntu (having to kill the process to be able to for example, surf the web)
Bug
[https://bugs.launchpad.net/bugs/151536]("https://bugs.launchpad.net/bugs/151536")

> - Firefox 3.0 (Even slower than older version, why use the beta already in a production system??? Marketing may be???)
Probably so they wouldn't have to support Firefox 2 after it hits EOL which was what happened with Dapper and Firefox 1.5

> - One of the most annoying things was that I was unable to mount NTFS partitions from external usb devices. (There is a permission issue with ntfs-3g)
Have you tried ntfs-config?

> - Apt-get gives an error when updating repositories because is unable to access /restricted Translation-en_US and some others, so installing an application using apt is almost impossible.
Receiving errors from Translation-en_US is normal.

People seem to forget that a freshly released OS is bound to have bugs. This happens after every Ubuntu release. It will stabilize. Give it a while.

---

### Post by xferaa on 2008-04-25
What about speed issues? You didn't say anything about that.

---

### Post by FuturePilot on 2008-04-25
I haven't noticed any speed issues. If anything it's faster.

---

### Post by eptech1 on 2008-04-25
For me, who has also been around from around the beginning of Ubuntu, this is a very solid release.  I had to plug in wired to download b43-fwcutter, then after a reboot you was up and going wirelessly.  Then I had to install nvidia driver using restricted device manager, and its speed has been great.  The one complaint I have is the speed of downloads, as I got it ready for rails development, but it was release day, if I didn't expect that, I wouldn't have had my  head on straight.  

All in all, I haven't had any issues.  It definitely sounds like at least part of it is hardware related, and it's unfortunate that you've had such a tough go of things thus far.

---

### Post by VipeR_11 on 2008-04-25
I have problems too!

In my case, I was downloading in full speed everything runs smooth.
Well….until the restart.
The bug report manager was showing about 20 windows and none of them was closing (cause the error occurs again and again). I think some of the software I had in 7.10 was incompatible but then the new version had to notify me to remove them or at least letting me know..
So what I did? Just hit reset and went back to windows XP :confused:

Before that though, because I had a lot of troubles with my ATI card (as usual with new ATI cards under Linux) I tried to enable the restricted drivers and restart. Here we go like the old times no signal once again. I fixed it but then the 20+ error reports appear again (I hate this report thing reminds me of windows lol).

I will do a fresh install and hope this time everything will go smooth…!

But I've noticed some really funny staff. I have only used Ubuntu 7.10 (my 1st Linux OS so far) and something I found annoying was having to different option for graphic setting (1 to set screen resolution and one that includes screen resolution + drivers setting). So I was wondering, what’s the point of the screen resolution option menu (since we have it in a tab next to driver’s option under display setting menu).
So guess what in 8.04 instead of moving the screen resolution (was odd and useless) they moved the display settings option lol (I didn’t check if it was hidden and I had to make it appear, but it wasn’t there by default and not even under under control centre).


I hope in your next update guys to have in mind users already running the software, and make their life easier instead of difficult. I have never seen soooo many error windows in my life. I have used Mac OS version 10 and later, windows 95se/98/98se/ME/XP up to sp2 and I have never ever received so many errors.
What we want is an OS easy to use without errors and avoid the troubles of the past caused by windows. I want to avoid error messages and slow OS and of course not to format my drive to put the new version (as we used to do in windows).

---

### Post by ljrossi on 2008-04-27
I install 8.04 expeting to have a solution to power managment.
Not only it was not solved , that i get the new following troubles.

1)Sound, only one software can capture de resuorce, for example I cant hear music meanwhile i try to make a skype.
2) Numpad keyboard is not working !! (the bloqnum key works ok , leds on off)
3) Again Nvidia graphics cards has troubles with some aplication
4) O my god Firefox 3 , nice, but i cant use many of my Ad ons , not what im suposed to do. Cant use anymore "Foxmarks Syncronize" or "Read It later" ones or my favorites add ons. Didnt "Ubuntu" know that ? 

Regards

---

### Post by elmezeni on 2008-04-27
Hello to all of you

   I have installed Ubuntu 8.04 on my Toshiba Satellite Pro A200 1MI and this is my first Linux OS. It's work nice from the start. It has working internet connection but it seems that it needs some tuning because my download speed is now 20kB/s instead of 110kB/s which I had in win xp. Can someone help me where to start, and what can it be because I'm totally new in Linux world.

---

### Post by VipeR_11 on 2008-04-27
> **VipeR_11 said:**
> I have problems too!

In my case, I was downloading in full speed everything runs smooth.
Well&#8230;.until the restart.
The bug report manager was showing about 20 windows and none of them was closing (cause the error occurs again and again). I think some of the software I had in 7.10 was incompatible but then the new version had to notify me to remove them or at least letting me know..
So what I did? Just hit reset and went back to windows XP :confused:

Before that though, because I had a lot of troubles with my ATI card (as usual with new ATI cards under Linux) I tried to enable the restricted drivers and restart. Here we go like the old times no signal once again. I fixed it but then the 20+ error reports appear again (I hate this report thing reminds me of windows lol).

I will do a fresh install and hope this time everything will go smooth&#8230;!

But I've noticed some really funny staff. I have only used Ubuntu 7.10 (my 1st Linux OS so far) and something I found annoying was having to different option for graphic setting (1 to set screen resolution and one that includes screen resolution + drivers setting). So I was wondering, what&#8217;s the point of the screen resolution option menu (since we have it in a tab next to driver&#8217;s option under display setting menu).
So guess what in 8.04 instead of moving the screen resolution (was odd and useless) they moved the display settings option lol (I didn&#8217;t check if it was hidden and I had to make it appear, but it wasn&#8217;t there by default and not even under under control centre).


I hope in your next update guys to have in mind users already running the software, and make their life easier instead of difficult. I have never seen soooo many error windows in my life. I have used Mac OS version 10 and later, windows 95se/98/98se/ME/XP up to sp2 and I have never ever received so many errors.
What we want is an OS easy to use without errors and avoid the troubles of the past caused by windows. I want to avoid error messages and slow OS and of course not to format my drive to put the new version (as we used to do in windows).


Here I am again!
I just installed again 8.04 this time from scratch.

Now it works well, my keyboard problems (i have them under 7.10) solved graphics and desktop issues too. Only few minor problem but i gess everything going to be even better in next version.

8.04 look much better than 7.10 but a bit more RAM hangry though. It doesn't seem to me faster but not slower either.

So Developers please next time don't make as (even if we are few) to need a reinstall from scratch instead of just upgrading.

It's not Very stable i guess because it's new release but as far as i remember 7.10 was VERY stable from day one...!

There are some bugs as ussual when is new version.
- when i store my session next time i restart i have no monitor signal!!
But if I press ctrl+alt + backspace in the login screen it comes back!
- Also some programs freezes, i never experienced a program to freeze since i moved to linux from the 1st day ubuntu 7.10 came out.

---

### Post by tovento on 2008-04-28
> **elmezeni said:**
> Hello to all of you

   I have installed Ubuntu 8.04 on my Toshiba Satellite Pro A200 1MI and this is my first Linux OS. It's work nice from the start. It has working internet connection but it seems that it needs some tuning because my download speed is now 20kB/s instead of 110kB/s which I had in win xp. Can someone help me where to start, and what can it be because I'm totally new in Linux world.

I have had a similar issue with my wireless in Linux vs XP.  In XP, my speed was up to 1000 kB/s, in Linux I've only managed to get 450 kB/sec.  Not sure what the issue is to be honest.  Apparently there are sometimes things one can play with in the router which will help out.

As for Hardy, I'm trying Linux again after a few years hiatus.  I was trying the last version a little when Hardy beta came out.  I was having some issues with my vid card (ATI) in terms of choppy video, and a few other small functions.  So, I decided to try Hardy and do a system wipe.  Things worked so much better out of the box for me.  No more of the same issues with the ATI drivers, etc.  One problem I had was with slow transfers to my USB key drive.  After one of the updates during the beta stage, that issue was fixed.  The one complaint I've had so far has been Firefox 3.  Yes, things worked initially (though not all plugins).  As time went on, the plugins started being updated to be compatible with FF3.  I was using FF3B4, and was content with the workings.  Hardy final was released, and I did all the recommended system upgrades.  That also installed FF3B5.  WOW...what issues.  The application would go grey constantly, become non-responsive for a few seconds, everything was slow.  I had enough this weekend, uninstalled FF3, and installed FF2.  It may not look as pretty, and web pages don't render as nicely as in FF3, but it works, it's fast, and no big complaints.

Some things are definitely a step forward in this edition of Ubuntu...some things still have issues, but I can't completely complain about FF3: it's in beta.  I would have assumed that FF3 would go full release by the time Ubuntu went full, but I guess that's not the case.  Ubuntu should have shipped with FF2, or give the option on which one to install.  If FF3 continues to have the same issues, I'll stick with FF2 for as long as I can.

---

### Post by verm69 on 2008-04-28
I did the upgrade yesterday, and have had a few problems...

- I cannont mount a secondary linux partition with my vm on it. Just ask's for authentication and then freezes the system

- had trouble mounting my NTFS partiion, but the NTFS config mentioned previously fixed that

- When ever i tried to sudo anything in console, it said it couldn't resolve my PC's name. had to edit the host file in tty2 to fix it since i couldn't open gedit with sudo or su

- I can see windows shares, but when i go into folders nothing is there when i know they're full of other folders... but in some i can see folders. Comes up saying it couldn't show the contents because of an "invalid arguement"

- After installing LikeWise open and joining my domain, it says "no log on server" or that i'm not allowed when i log onto my box locally...

- can't even make a shortcut to home on my desktop... at least not as easy as i could in 7.10

other wise it's okay... i was very impressed with 7.10 with it's usability and stability, i didn't have one problem... but i'm not so impressed with 8.04 since i have "alt + ctrl + Backspace" all the time due to constant problems...

I'm sure a fresh install will probably fix it, but i've done so much work to it to get it where it is, and because i'm in a buisness enviroment, i can't spend the time nessisary to get it up to speed again.

i love ubuntu and won't go back to windows (only reason i run a vm windows box is so i can edit Active directory), but i'm not impressed with the problems i've been having since upgrading...


ANY help would be great too :)

---

### Post by jbysmith on 2008-04-28
Overall I really like 8.04, but for me the disappointment comes with the feeling that 8.04 was rushed to meet a deadline.  Certainly not bashing the Ubuntu guys, as it's still a great distro.  But I'm the type of person who prefers a release when it's ready, not by what the calendar says.  

The repo speed issue is a given of course; a bajillion people hitting the servers will do that.  FireFox V3.. no surprise there, first thing I did was remove it for V2 as I knew some of my "must have" addons don't play nicely with V3 yet.  But, at least on my hardware, it's having some serious stability issues.  Random lockups mostly (some severe enough to require a hard reset), some other bugs here and there that are just annoying.  

For now, I'm back in 7.10.  (Go back to Windows? Pfft I'd rather get an Etch-A-Sketch first.. faster reboots and probably more productive) Compiled Wine and Compiz Fusion from source just to have the latest.  The rest is "current enough" for me to work with.  It's all good.  

Figure a few weeks should be enough time for the developers to nail down the more serious problems and then I'll give 8.04 another go. Wish my system was in the majority that's running it perfectly.. but that's geek life for you.  Can't wait to give it another spin down the road.

---

### Post by wolfen69 on 2008-04-28
> **jbysmith said:**
> Go back to Windows? Pfft I'd rather get an Etch-A-Sketch first.. 

one of the funniest one-liners ive heard in a while. i might use that in my sig. of course, attributed to you.

---

### Post by shearn89 on 2008-04-30
To the guys asking support questions - its easiest and quicker to post your own support thread in the relevant section of the forum. To the guys who've "been with ubuntu from the early days", i'm surprised that you've never been on the forums before to ask a question (as demonstrated by the post count of ~2 and the join date of eg, Nov 2007).
?

@wolfen69 - rofl...

---

### Post by magnus0 on 2008-04-30
I just switched back to Ubuntu when the new version came out, after being in windoza for 2 months. Everything was great, there were no problems at all installing Ubuntu. But Firefox 3 is really slow and unstable. It just 'goes gray' randomly when I visit pages.

---

### Post by RainCT on 2008-04-30
> **magnus0 said:**
> I just switched back to Ubuntu when the new version came out, after being in windoza for 2 months. Everything was great, there were no problems at all installing Ubuntu. But Firefox 3 is really slow and unstable. It just 'goes gray' randomly when I visit pages.

There still is Firefox 2 in the repositories. However, I don't think that this your problems come from Firefox, it's more probable that the Flash plugin causes them.

---

### Post by sports fan Matt on 2008-04-30
I simply just cant read these "big dissappointment" threads any longer.  It honestly seems like some but not all, with x posts even though they say "Ive been a ubuntu user since X".  Then why wouldnt take the time to post and see if you can get the issues straightened out?.  

I realize that some are going to have similar issues and thats cool, but lets be real.  Its alot easier to state things like:

I have an issue with Driver X not working, What do you suggest I try?  

Sorry, but inho, it seems like sometimes people just dont want to take the time to ask for help for things rather then ranting?  Am i off base here?

---

### Post by 3rdalbum on 2008-04-30
I ran the live CD on my own computer, and installed it on a new computer for someone else. There were certainly no speed or monitor resolution issues, even though the new computer has fairly weak components and integrated ATI graphics. I didn't try NTFS partitions.

I did notice that I needed fewer workarounds, two monitors I tried were fully detected out-of-the-box, and the speed of the system is just as good as previous versions.

---

### Post by magnus0 on 2008-04-30
> **RainCT said:**
> There still is Firefox 2 in the repositories. However, I don't think that this your problems come from Firefox, it's more probable that the Flash plugin causes them.

No, it just crashes on random pages. Especially, when opening a lot of tabs.

---

