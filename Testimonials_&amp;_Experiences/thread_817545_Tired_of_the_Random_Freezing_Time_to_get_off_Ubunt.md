---
title: "Tired of the Random Freezing: Time to get off Ubuntu"
date: 2008-06-03
forum: Testimonials &amp; Experiences
---

### Post by Bungo Pony on 2008-06-03
I'm seriously tired of this issue. It really sucks when you're selecting files to stick on your MP3 player, and the OS freezes for 15-20 seconds every two minutes. Rebooting doesn't help. It also doesn't seem to be a Nautilus issue, since I get it using a web browser, knotes, etc etc. It seems to be an OS issue.

This isn't a new problem either. It's followed Ubuntu from Feisty on through Gutsy, and finally into Hardy. I've been living with it for a good year. Enough is enough. It's counter-productive and frustrating.

When I get some spare time, I'll be backing up my data and moving on to PCLOS.

---

### Post by cardinals_fan on 2008-06-03
I found that the freezes were related to Compiz.  That's also why the freezing started with Feisty - that was the first release including Compiz by default.

---

### Post by zmjjmz on 2008-06-03
> **cardinals_fan said:**
> I found that the freezes were related to Compiz.  That's also why the freezing started with Feisty - that was the first release including Compiz by default.

sed s/Feisty/Gutsy/g
Anyways, I noticed it too.
Guess what.
They never happen with Compiz off.

---

### Post by aysiu on 2008-06-03
If PCLinuxOS works for you, great. Use what works for you.

---

### Post by Bungo Pony on 2008-06-03
You're right! It is Compiz! I've been keeping an eye on conky while doing other things. Compiz maxes out my CPU to 100% when it freezes.

How come nobody told me this when I bitched and complained about it in the past??!!?

The only thing that sucks is I somewhat rely on Compiz for the transparency and the zoom.

I'll be playing with Compiz later to see if I can find a specific feature that's causing the freezing. I'm HOPING it's a problem with only one feature.

Thanks for pointing it out! A compiz on/off button in my taskbar would be really helpful. Any way to make one?

---

### Post by SunnyRabbiera on 2008-06-03
Why PClinux though, its forums are ruled by arrogant snobs.
I rather use mandriva.

---

### Post by gameryoshi600 on 2008-06-03
> **Bungo Pony said:**
> You're right! It is Compiz! I've been keeping an eye on conky while doing other things. Compiz maxes out my CPU to 100% when it freezes.

How come nobody told me this when I bitched and complained about it in the past??!!?

The only thing that sucks is I somewhat rely on Compiz for the transparency and the zoom.

I'll be playing with Compiz later to see if I can find a specific feature that's causing the freezing. I'm HOPING it's a problem with only one feature.

Thanks for pointing it out! A compiz on/off button in my taskbar would be really helpful. Any way to make one?

compiz fusion icon can turn compiz off and on

---

### Post by buntunub on 2008-06-03
> **Bungo Pony said:**
> I'm seriously tired of this issue. It really sucks when you're selecting files to stick on your MP3 player, and the OS freezes for 15-20 seconds every two minutes. Rebooting doesn't help. It also doesn't seem to be a Nautilus issue, since I get it using a web browser, knotes, etc etc. It seems to be an OS issue.

This isn't a new problem either. It's followed Ubuntu from Feisty on through Gutsy, and finally into Hardy. I've been living with it for a good year. Enough is enough. It's counter-productive and frustrating.

When I get some spare time, I'll be backing up my data and moving on to PCLOS.


Compiz is unstable and buggy software. It requires fairly beefy hardware to run it properly. A while ago Beryl and Compiz merged and then everyone thought that the problems would go away and development would be streamlined and more robust, but alas, just the opposite happened. Anyway, thats the short and sweet of it. Turn off Compiz if you dont have a decent Nvidia card with at least 512M ram to boot.

---

### Post by dasunst3r on 2008-06-03
Yep... I've been dealing with that issue for the past year and a half.  It was a lot worse before nVidia fixed their drivers, though -- my computer would hard lock up and turn off/restart.

---

### Post by 23meg on 2008-06-03
[QUOTE=Bungo Pony]How come nobody told me this when I bitched and complained about it in the past??!!?[/QUOTE]

Maybe because you just bitched and complained instead of asking for help? I know I'd ignore you instead of helping.

---

### Post by Bungo Pony on 2008-06-03
> Turn off Compiz if you dont have a decent Nvidia card with at least 512M ram to boot.

Go figure, I've got both :S

> Maybe because you just bitched and complained instead of asking for help? I know I'd ignore you instead of helping.

Maybe, but I wasn't trying to be an ******* about it. I'd just mention it in existing threads. I never found anything after doing much searching both on these forums and through google. Thank god for Conky!

> Why PClinux though, its forums are ruled by arrogant snobs.

I could care less about other users. I like this forum and I wouldn't be leaving even if I did switch to PCLOS. The thing is, I've had a really good experience with that distro. When I was running Gutsy (which was a nightmare even outside the random freezing) I was doing some testing with video capture in PCLOS since I couldn't get it to work in Ubuntu. PCLOS handled it like a pro, everything compiled without any problems, and the whole distro was all around rock solid. 

Ubuntu is good for me since it actually requires a bit of work to get working, whereas everything seems to work out of the box with PCLOS. I'd recommend that distro to a noob over Ubuntu anyday. But if someone wants to get into the "meat" of Linux, I'd recommend Ubuntu.

> compiz fusion icon can turn compiz off and on
Cool, I'll be adding it to the taskbar!

Thanks all for your help! I really didn't feel like re-installing software and restoring backups anyway :)

---

### Post by Bubba64 on 2008-06-03
I don't think compiz is the only component of freezing I have never used compiz due to low ram and have had freezing in Hardy but I have a old think pad with a boinked hard drive for me it is probably hardware. If the Freeze problem had a definitive answer it would have been fixed, I suspect that a lot of it is unsupported driver problems. On my ancient desktop with no compiz used Hardy runs great with only 256 ram but it has a 1.7 g hard drive

---

### Post by ukripper on 2008-06-04
i really have no idea what is causing this freeze on your system. 


But if i were you I would first try to compile and install the latest kernel from [www.kernel.org](www.kernel.org)  to analyse this problem and then might consider to move to some other distro.


Make sure you backup first.
There is very easy howTo to install new kernel (kernelCheck app)if you haven't come across it,try this link - [http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563)

---

### Post by wdaniels on 2008-06-04
A lot of people seem to be reporting improved performance with today's kernel update, so maybe that will help? Are you on 26.6.24-18 yet?

---

### Post by Buzzdee on 2008-06-04
I had a similar problem. Give this a try:

Go into Nautilus' preferences, 'Preview' Tab and put 'Preview sound files' to 'never'. That did it for me ;)

---

### Post by stchman on 2008-06-04
> **Bungo Pony said:**
> You're right! It is Compiz! I've been keeping an eye on conky while doing other things. Compiz maxes out my CPU to 100% when it freezes.

How come nobody told me this when I bitched and complained about it in the past??!!?

The only thing that sucks is I somewhat rely on Compiz for the transparency and the zoom.

I'll be playing with Compiz later to see if I can find a specific feature that's causing the freezing. I'm HOPING it's a problem with only one feature.

Thanks for pointing it out! A compiz on/off button in my taskbar would be really helpful. Any way to make one?

I personally have never had this problem.  You can turn Compiz off for just when you want to transfer MP3 files to your player and turn it back on when done.

---

### Post by wootah on 2008-06-04
> **Bungo Pony said:**
> You're right! It is Compiz! I've been keeping an eye on conky while doing other things. Compiz maxes out my CPU to 100% when it freezes.

How come nobody told me this when I bitched and complained about it in the past??!!?

The only thing that sucks is I somewhat rely on Compiz for the transparency and the zoom.

I'll be playing with Compiz later to see if I can find a specific feature that's causing the freezing. I'm HOPING it's a problem with only one feature.

T**hanks for pointing it out! A compiz on/off button in my taskbar would be really helpful. Any way to make one?**

I know with *screenlets*, you can get a screenlet with a menu that has a compiz on-off button. Check out screenlets in the repos (I think) and the app is at: [http://www.gnome-look.org/content/show.php/FusionSwitch+screenlet?content=80091](http://www.gnome-look.org/content/show.php/FusionSwitch+screenlet?content=80091)

---

### Post by Bungo Pony on 2008-06-04
The problem isn't with the actual copying of files, it was selecting the files. And that's not the only time it randomly freezes either.

I installed the Compiz icon, and I may look into the screenlets.

Speaking of screenlets, does anybody know a good one that lets you know when there's mail in your POP account? I've tried all the ones in gdesklets which are mostly crap. There was one that worked really well (can't remember the name), but it doesn't work in Hardy.

Maybe I should start a new thread for that subject, since that's how I got into the compiz / freezing mess ;)

---

### Post by MONODA on 2008-06-04
> I found that the freezes were related to Compiz. That's also why the freezing started with Feisty - that was the first release including Compiz by default.
yep compiz has caused problems for many and has been regarded as unstable, it drags users into ubuntu but causes them to run off in a few days. I liked how in feisty there was a warning that thing wouldnt work perfectly, there should be something like that in future releases too and it shouldnt be on by default. @23meg, considering that you are a developer you can probably answer this for me, why wasnt a warning included in hardy? it is the source of many problems in many cases. I am just curious. NOTE: I am not being sarcastic or making fun.

---

### Post by Jimmy9pints on 2008-06-17
Just to add my voice to this, I also had problems with Ubuntu freezing due to improper Nvidia drivers and Compiz. Even with the improper drivers if I turned Compiz off, everything was fine (but looked boring).

I plan to stick with Ubuntu for sure, but certainly at the start it was really hard with the whole system freezing up every few minutes. My friends were questioning my sanity when I had changed over from Windows to this regularly-freezing OS that they'd never heard of. 

Compiz is indeed the source of many people's problems on Ubuntu, so I question the wisdom of including it as standard.

---

### Post by Sealbhach on 2008-06-17
I had a whole series of freezes last night when I tried out some screenlets. Every time I try to use screenlets I get problems.

I haven't installed the latest updates yet, maybe they'll help.



.

---

### Post by ukripper on 2008-06-17
> **Sealbhach said:**
> I had a whole series of freezes last night when I tried out some screenlets. Every time I try to use screenlets I get problems.

I haven't installed the latest updates yet, maybe they'll help.



.
you should use latest updates and then see if it does.

If it still does then probably you may want to use kernel 24-19 generic from proposed updates. This has fixed for many users.

---

