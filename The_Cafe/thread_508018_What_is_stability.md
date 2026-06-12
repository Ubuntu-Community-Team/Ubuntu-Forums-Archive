---
title: "What is stability?"
date: 2007-07-23
forum: The Cafe
---

### Post by drewtown on 2007-07-23
This may seems like a silly question to some of you, but I consider myself a fairly advanced computer user and this word stability has always kind of boggled my mind.

For you is stability a certain number of days you computer/server can stay up without the need for a restart?
no unexpected crashes? (What about compiz fusion causing a GDM crash, requiring a Ctrl+alt+backspace?)
Do restarts due to updates factor into your stability index?
Does the load of the computer factor into stability?

I'm just curious of when you, the user, consider your machine to be stable.

---

### Post by Zzl1xndd on 2007-07-23
For me its about uptime without a reason to restart the Computer, Things like Beryl and Compiz (or Compiz Fusion) causing issues don't factor for me as they are Beta and I know that its my risk to take. Also Restarts from Updates dont factor in for me as that is a good reason.

---

### Post by Depressed Man on 2007-07-23
If the OS itself doesn't require a restart or reboot (except for updates). That's my definition. Unexpected crashes due to software are bound to happen for any OS. The only difference is that some OSes have better ways to kill the offending app.

---

### Post by cunawarit on 2007-07-23
It depends on how the service level agreement defines it.

---

### Post by igknighted on 2007-07-23
I'd say it is several things.  First, that programs do not crash, and if they do for some reason, the rest of the OS does not.  If a crash as serious as a Compiz crash happened on a windows box, you would need to reboot.  Not so in linux, often times you do not even need to restart X (it drops to a non-compositing WM).

Also, I can accept the occasional reboot due to an update, but even after a couple years with linux I am stunned that I can update everything I do and not need to restart.  My work computer requires constant reboots for updates (Windows), while my linux box only does when I choose to update the kernel.

A third part I would throw in is the ability to debug a crash.  If an app crashes (say FF) in linux, I can view the system logs or run it from a terminal and get output of the crash so I can diagnose what is wrong.  In windows all I can do is click to send an error report (typically a time and resource consuming activity as the system tries to recover) and hope that MS has a documented reason for the crash that might be helpful to me.

---

### Post by cunawarit on 2007-07-23
> **igknighted said:**
> If a crash as serious as a Compiz crash happened on a windows box, you would need to reboot.

Why? If explorer.exe crashes it even restarts itself.

---

### Post by igknighted on 2007-07-23
> **cunawarit said:**
> Why? If explorer.exe crashes it even restarts itself.

explorer.exe is like gnome-panel, not a WM.  If gnome-panel crashes it restarts itself too, always has as far back as I remember.  There really is no equivalent to compiz in windows, but when major windows components crash the system (even if it technically survived the crash) usually slows to a crawl until you reboot.  For that matter, during an app crashing in linux, the rest of the system is still responsive.  In windows you sit there and wait for the crash to end and recover before you can do anything.

This is not a bash-windows arguement per-se, but rather outlining my reasons why I consider GNU/Linux to be more stable.  Windows has some stability pluses as well.  It's bug reporting feature often gives you the solution to the problem (if windows has a known solution), a very handy feature.  Also, it falls back to a more basic driver for things like graphics better than most linux distributions.  Fedora is the only one that comes to mind that should a driver like NVIDIA's fail to load on boot, it will automatically drop down to the NV driver.  Most distro's would simply not load X.  I know Ubuntu has a feature planned called "failsafe mode" or something, but honestly I think the Fedora solution is much better.  That, however, is not for this discussion... the point is, Windows handles this situation better than (most) linux's.

---

### Post by stmiller on 2007-07-23
Debian stable, Redhat (commercial), Slackware, and others are famous for their rock solid stability. Start that distro on a machine and the OS will never crash.

---

### Post by Tundro Walker on 2007-07-24
> **cunawarit said:**
> Why? If explorer.exe crashes it even restarts itself.

In a topic about "stability", what you just said is very ironic.  So, an OS that restarts itself if it crashes itself is "stable"?

Ok, razzing you aside, explorer.exe is good about restarting.  You can end-task on it, and it'll come back.  But, its interaction with other programs seems to be unstable at times.  And trying to kill off a program that's blowed up...it's like trying to talk to a wall.  I honestly think the Ctrl+Alt+Del Task Manager applet is only a placebo, because I'll try to shut down a stuck program, and Windows will ignore me.  Or, on the rare case it actually DOES decide to do what I want and kill off the program, the comp is bogged down for 5 mins trying to clean up after everything.

Granted, this is my computer at work, though.  When I was using Windows at home, I had it tweaked enough to where it was pretty responsive.  So, this could just be a case of lame IT at my work (or over-aggressive anti-virus/spyware that wants to log every flippin activity taking place).  But, the fact that you need to tweak Windows quite a bit to make it responsive...that's lame in and of itself.

---

### Post by cunawarit on 2007-07-24
> **Tundro Walker said:**
> So, an OS that restarts itself if it crashes itself is "stable"?

Clearly not, an OS that crashed often even if it recovered nicely would be unstable. And it isn't ironic, because it was said in the context of a Compiz crash.

---

### Post by igknighted on 2007-07-24
> **cunawarit said:**
> Clearly not, an OS that crashed often even if it recovered nicely would be unstable. And it isn't ironic, because it was said in the context of a Compiz crash.

Funny that a beta quality piece of software is a reasonable comparison to a main component of the dominant operating system :-/

---

### Post by Tundro Walker on 2007-07-24
> **cunawarit said:**
> Clearly not, an OS that crashed often even if it recovered nicely would be unstable. And it isn't ironic, because it was said in the context of a Compiz crash.

Yes, but it wouldn't have been as funny unless I misquoted you and used it out of context...:)

---

### Post by happy-and-lost on 2007-07-24
Stability is the ability of software not to crash, even when pushed hard. This is why, to me, Debian Etch is not stable, as the KDE on Etch will a'splode at the lightest touch,

---

### Post by cunawarit on 2007-07-24
> **igknighted said:**
> Funny that a beta quality piece of software is a reasonable comparison to a main component of the dominant operating system :-/

God almighty, I'm not going to defend explorer.exe because it doesn't deserve it... 

However the comparison is nothing to do with one being a final release and the other being a beta product. It is to do with both being user interface components. 

As for Compiz, I have tried it but not enough to say anything other than the fact that I think the wobbly plugin is absolutelly fantastic!!! And that particular plugin poops all over Aqua and Aero.

---

### Post by igknighted on 2007-07-24
> **cunawarit said:**
> God almighty, I'm not going to defend explorer.exe because it doesn't deserve it... 

However the comparison is nothing to do with one being a final release and the other being a beta product. It is to do with both being user interface components. 

As for Compiz, I have tried it but not enough to say anything other than the fact that I think the wobbly plugin is absolutelly fantastic!!! And that particular plugin poops all over Aqua and Aero.

Relax, i was making a joke.  I just found it really funny that I compared Compiz (pretty much held was one of the least stable programs in lnux) to a primary component in windows and the discussion went on without batting an eye.  I would have expected 80 "but compiz is beta" posts

Ironically just before I typed this explorer did crash, and came back as it should.

One final thought: I totally agree, compiz is slick.  I am still running beryl and not the new compiz-fusion (I haven't had the motivation to learn the new one yet), but if you have the hardware to run it, its worth it.  Wow, totally off topic now :)

---

### Post by forrestcupp on 2007-07-24
Let me just start by saying that I like Linux better than Windows, and I'm not a Windows fan.

But I don't think people are being realistic about stability.  Maybe some people make claims without actually having much experience with Windows.  Maybe some people just hate Windows so much that they make extremely biased and unrealistic claims.

Again, I like Ubuntu better than Windows, but I've had **a lot** more crashes in Ubuntu than I ever did in XP.  In Ubuntu I've had crashes that required ctrl-alt-backspace, I've had crashes that required a hard shutoff by holding in my power button, and I've had crashes where X was trashed and I had to start to a command line and fix it.

In XP I had crashes, but some only required a ctrl-alt-del and not a reboot.  I didn't have anywhere near the crashes that everyone claims Windows has.  And the BSOD doesn't really happen nearly as much as it did under previous versions of Windows.

I realize that a lot of my crashes in Ubuntu may have been my fault, but that's true for Windows, too.  In my experience, it is not true that Linux handles crashes any better than Windows.

Remember, I like Linux better, but I'm just trying to be realistic here.

---

### Post by igknighted on 2007-07-24
> **forrestcupp said:**
> Let me just start by saying that I like Linux better than Windows, and I'm not a Windows fan.

But I don't think people are being realistic about stability.  Maybe some people make claims without actually having much experience with Windows.  Maybe some people just hate Windows so much that they make extremely biased and unrealistic claims.

Again, I like Ubuntu better than Windows, but I've had **a lot** more crashes in Ubuntu than I ever did in XP.  In Ubuntu I've had crashes that required ctrl-alt-backspace, I've had crashes that required a hard shutoff by holding in my power button, and I've had crashes where X was trashed and I had to start to a command line and fix it.

In XP I had crashes, but some only required a ctrl-alt-del and not a reboot.  I didn't have anywhere near the crashes that everyone claims Windows has.  And the BSOD doesn't really happen nearly as much as it did under previous versions of Windows.

I realize that a lot of my crashes in Ubuntu may have been my fault, but that's true for Windows, too.  In my experience, it is not true that Linux handles crashes any better than Windows.

Remember, I like Linux better, but I'm just trying to be realistic here.

Interesting.  I try to keep as rational a view as possible (I don't use windows unless I have to, but I don't hate it by any means... it just isn't my cup of tea), but my experience has been the exact opposite.  In linux, I have never had a non hardware-related (as in the hardware physically malfunctioned) crash that killed the whole OS.  In windows a crash (for me) regularly takes down the whole system.  Granted, when windows apps crash for me it tends to be games that are hogging a lot of system resources and if i were to leave it long enough it might come back, but who has the time?

In short, the modular nature of linux, IMHO, is more stable.  This may or may not hold true in reality, as it depends on hardware support.  But a linux system is undeniably more stable in that pieces can crash and not even effect the rest of the system at all.  While at times windows can recover from key crashes, it almost always bogs down the system.  In linux if an app crashes you click around it and keep working and when its done you can debug it.

---

### Post by dca on 2007-07-24
In the old days, the MS kernel (win95, 98, NT) tied in with everything, hardware, applications that are running, etc.  Most times when an app crashed it would bring down the whole system requiring a forced shutdown (holding down power button).  Now a days w/ Windows (2000, XP, server) it's a little easier recovering from a faulting app.  *nix systems on the other hand have had the ability to close/restart the faulting app only.  Somewhere in there is where the 'stability' thing ties in I believe.  I will not argue the current stability of say RHEL5 versus Windows Server 2003 on and enterprise/mission critical class server...

---

### Post by marco123 on 2007-07-24
Stability to me is being able to leave your computer on downloading for 8 months straight.  I like the fact that I can do this in Linux. (Last time I used windows it went mental on me after 2 weeks! :)  )

---

### Post by forrestcupp on 2007-07-24
> **igknighted said:**
> Interesting.  I try to keep as rational a view as possible (I don't use windows unless I have to, but I don't hate it by any means... it just isn't my cup of tea), but my experience has been the exact opposite.  

I guess everyone has their own experience.  I have had longer uptimes with XP than I have had with Linux.  I really believe that today, kernel for kernel, the stability is pretty comparable.  MS has done a lot of work in that area.  It's usually other 3rd party things that cause problems.

Let's face it, about everything we run in Linux is beta.  And it's freely and easily available to the masses.  Not only that, it's pushed on the masses.  Just look at Compiz in Feisty, and better yet, Compiz/Fusion in Gutsy.  In the Microsoft world, it's not so easy to just get and run a beta version of the new OS.  I'm not saying it's wrong to run beta stuff; I'm just saying it's the way of the Linux world, and Linux crashes.

---

### Post by cunawarit on 2007-07-24
> **forrestcupp said:**
> But I don't think people are being realistic about stability.

Let me just start by saying that I am not an Ubuntu user, I am a Debian user. 

And agreed, I find some people&#8217;s ideas and experiences of Windows bizarre, as they are simply things I have never experience. My current XP machine has not ever blue screened, and I&#8217;ve had it for one and a half years, it did however not start once. It is a little too soon to comment on Vista, I&#8217;ve only been using it for a week and a bit.

Debian too has been fantastic so far, I don&#8217;t use it much for work, but I do use it as a home desktop and it is great, it has been rock solid. 

Much like Vista, my experience with Ubuntu has been too brief to comment.

> **igknighted]Granted, when windows apps crash for me it tends to be games that are hogging a lot of system resources and if I were to leave it long enough it might come back, but who has the time?[/quote]

There may lay the difference, I don&#8217 said:**
> Let's face it, about everything we run in Linux is beta.

I disagree, one of the things I like about Debian if you use the stable repository there is more reassurance that what you are installing has been tested thoroughly. I&#8217;d rather have the Debian team do the testing than trust the supplier/developer entirely.

---

### Post by igknighted on 2007-07-24
> **forrestcupp said:**
> I guess everyone has their own experience.  I have had longer uptimes with XP than I have had with Linux.  I really believe that today, kernel for kernel, the stability is pretty comparable.  MS has done a lot of work in that area.  It's usually other 3rd party things that cause problems.

Let's face it, about everything we run in Linux is beta.  And it's freely and easily available to the masses.  Not only that, it's pushed on the masses.  Just look at Compiz in Feisty, and better yet, Compiz/Fusion in Gutsy.  In the Microsoft world, it's not so easy to just get and run a beta version of the new OS.  I'm not saying it's wrong to run beta stuff; I'm just saying it's the way of the Linux world, and Linux crashes.

Thats not a fair statement about GNU/Linux as a whole.  Ubuntu is based on Debian Testing, so yes, the packages will be newer and not quite as stable.  But what about RHEL?  Or Debian?  Or Slack?  Slack only dropped the 2.4 series kernel as default in the just released Slack 12 IIRC.  This is a conscious decision by a user to go with the most current software.  GNU/Linux as a whole is not "all beta software", not even close.

I think the only reason that linux does not present as far more stable is the lack of quality hardware drivers in many desktop situations.  Mind you this is a serious issue.  People don't care why it doesn't work, just that it doesn't.  However, it is easier to write a quality driver (if you are the HW manufacturer) than it is to re-write a kernel to increase stability.

So fundamentally, I believe that linux is more stable, but in reality I agree with you that the end user experience will end up with approximately equal stability (or more accurately, there will be a spread of people, some finding linux far more stable if their hardware is fully supported and others with unsupported HW finding windows to be far more stable)

---

### Post by init1 on 2007-07-24
> **drewtown said:**
> This may seems like a silly question to some of you, but I consider myself a fairly advanced computer user and this word stability has always kind of boggled my mind.

For you is stability a certain number of days you computer/server can stay up without the need for a restart?
no unexpected crashes? (What about compiz fusion causing a GDM crash, requiring a Ctrl+alt+backspace?)
Do restarts due to updates factor into your stability index?
Does the load of the computer factor into stability?

I'm just curious of when you, the user, consider your machine to be stable.
For me, a stable OS doesn't crash, or do weird things. Ubuntu is by far the most stable OS I have ever used. Nothing comes close.

---

### Post by forrestcupp on 2007-07-24
> **igknighted said:**
> Thats not a fair statement about GNU/Linux as a whole.  Ubuntu is based on Debian Testing, so yes, the packages will be newer and not quite as stable.That's true.  I based what I said off of my experience with Ubuntu and Sabayon, not off of Linux as a whole.  But remember that Ubuntu is the most popular distro, especially for new people.

> I think the only reason that linux does not present as far more stable is the lack of quality hardware drivers in many desktop situations.  Mind you this is a serious issue.  People don't care why it doesn't work, just that it doesn't.  However, it is easier to write a quality driver (if you are the HW manufacturer) than it is to re-write a kernel to increase stability.

I have always thought that Linux developers (especially kernel devs) are awesome.  In Windows world, they just write their OS and all of the hardware manufacturers write their own drivers based on what they created.  In Linux, we pretty much have to reverse engineer everything to get hardware to work without much help from the manufacturers who know how their hardware works.

---

### Post by drewtown on 2007-07-24
I didn't mean for this to turn into a Windows Vs Linux debate but it is kind of interesting.

I have a Windows Laptop running XP Pro and a desktop running ubunt 7.04 and I wouldn't say one is more stable than the other.  I see my laptop becoming sluggish more often but it always manages to recover back to it's normal state.  My Ubuntu box has been up for 15 days with compiz fusion, amarok, pidgin, azureus, ssh/vnc running all the time and some light browsing so I can't say I've tested it extensively but it seems to be moderately stable to me right now.

I like the comments about how in *nix systems a program crash shouldn't take down your whole system (unless it's CF destroying X).  I would venture a guess that most people on these forums that consider themselves moderately advanced or advanced computer users their stability problems come from old/unsupported hardware or they are dinking with the system and trying to change something.  I would also say that most OS is going to be stable enough for most users, especially if you shut down your computer at night like you should.

---

### Post by forrestcupp on 2007-07-24
> **drewtown said:**
> 
I like the comments about how in *nix systems a program crash shouldn't take down your whole system (unless it's CF destroying X).

I've had Super Tux crash my computer to the point of having to do a hard power down.  I have a lot of trouble with Super Tux, and it's my son's favorite game.  It's probably a compatibility issue with Compiz/Fusion and previously Beryl.

---

