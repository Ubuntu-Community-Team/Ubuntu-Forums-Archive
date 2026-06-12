---
title: "The end of my Linux journey..for now at least."
date: 2007-04-26
forum: Testimonials &amp; Experiences
---

### Post by fugufish on 2007-04-26
Having been in IT for many years and a PC enthusiast since the 80's I had often kicked around the idea  to try out Linux.  About a month ago I read a great article called 30 days with Linux and decided to give Ubuntu 6.10 a try.
[http://consumer.hardocp.com/article.html?art=MTI5OCwxLCxoY29uc3VtZXI=](http://consumer.hardocp.com/article.html?art=MTI5OCwxLCxoY29uc3VtZXI=)

I installed Edgy on several test boxes ranging from brand new HP dual core towers to an older P4 2.4 we built with spare parts laying around the shop. The installs went well generally but I was struck by seemingly simple things that didn't work right out of the gate. I.E. my mouse thumb buttons didn't work with Firefox while browsing. I don't mind tweaking and I spent hours scouring various foums until I found out the right settings to "hack" into xorg.conf. I learned a valuable lesson about backing that file up before changing anything as one wrong setting will brick your x server. Another thing that didn't work correctly was screen resolution. You would think that a modern OS would correctly detect your LCD monitor's capabilities and allow a standard resolution of 1280X1024. But no, more hacking of the xorg.conf file to add the desired resolutions. Then there is the lack of .mp3 and DVD playback support. I understand that their are legal reasons why these things  aren't  included "out-of-the-box" and they can all be added in but if the Linux community hopes to lure more people away from XP/Vista, this isn't the way to go about it. It simply takes too much time to get Linux to the same level of usability as a standard XP install. I found that the solutions to most problems involved entering long, arcane strings of information  into a terminal window. 

I continued playing with Edgy and got beryl working on my old GF4 Ti4200 card with the Nvidia "legacy" drivers.(what a joy to install those from a command line) I got embedded .wmv support working and pretty much had Edgy working the way I needed it to. Still, I didn't really "need" linux. I used it for browsing, music, IM and email.

Then I '"upgraded" to Feisty and it all went downhill. I used the official upgrade method. Waited 6 hours and
after the reboot was left with a broken x-server. Some incompatibility with the default legacy driver and my old graphics card. I backed up my data and wiped the HD and installed fresh from a Live CD.
It was then that I discovered the LiteOn CD player bug which caused the system to hang for 5 minutes and boot with a non working optical drive. Pretty big bug. I found the workaround and added "irqpoll" to some
file somewhere. Booted into Feisty but could not get 1280X1024 resolution, again. Then the desktop started freezing every couple of minutes. (worked fine with XP so not a hardware problem).

That was it for me. Fixmbr, delete the Linux partition and walk away. At least for now...

---

### Post by newlinux on 2007-04-26
We hope you come back. There are many advantages to Linux that XP can't do as well. You also might want to look into other distros if you want codecs installed by default. But I'll be the first to admit Linux isn't for everybody. Neither is XP. Just wish more people took the time to properly evaluate and use both -> I think this would lead to more Linux users.

---

### Post by Eric Layne on 2007-04-26
Sorry to hear that fugufish. It sounds like people are having many different problems for a myriad of different reasons, and patience can only be stretched so thin.

Better luck next time.

---

### Post by detroit/zero on 2007-04-26
My upgrade from Edgy to Feisty was less than stellar as well. I backed up all my desirables to about 7 DVDs and did a fresh install. After months of fighting Edgy to get my nVidia card to work, I made patchwork of about 6 different install methods for nVidia restricted drivers and got it up and running. (FYI: System>Administration>Restricted Drivers doesn't do the trick..)

I got all my data back on my drive, nVidia works,  unimpressed with the Desktop Effects performance I've since installed Beryl and am happy as a lark with the whole experience.

I can't say I've enjoyed the endless hours of pecking away at a keyboard and scouring forums looking for answers like you say but, in retrospect, I've learned a lot along the way and after years and years of being stuck in Windows, I've finally got the system I want.
[B]
And it didn't cost me a dime.[/B]

I'm looking at my Beryl Cube and I can't believe that people with XP (and Vista) will pay hard earned money for the "privilege" of *skinning their desktop*.

I read an article a while back about why Windows users find it hard to make the transition to a Linux system. It said that "power users" often had the more difficult time, because there's a *Windows way* of doing things, and a *Linux way* of doing things. Power users often get very frustrated when the methods they know and use are no longer useful.

I've hit that roadblock many times, and almost pulled out my XP system restore disks and started over with that nightmare. But then I remembered.. I'm trying to do it the *Windows way*; that's why it's not working!

I'll take editing configuration files to get exactly what I want over paying someone for software that doesn't perform as expected/advertised in the first place.

---

### Post by pmenefee on 2007-04-26
I have an old (3 or 4 years) computer that's not terribly out of date and I thought I would move from XP to Linux.
Installed Ubuntu, upgraded to 7.04, the fawn, and things (most) seem to work.  I'm not a hobby code writer, so that doesn't interest me.......I just want it to work.  I'm 63, and certainly not into all the terminal code, but not a total green guy either.

Bottom line is, it works for me.  My computer in the house is still XP, but in my workshop I get to play with Linux.

Except for............the wireless problems that I see all over the board.  I can connect and send and receive without any problem whatsoever until I try to secure my home network, and no configuration will work.  I am currently unplugging my Linksys router to keep from broadcasting 24/7 when I'm not active.  Surely, there is a better answer, but that may take a few months.

Keep working guys, it's working!

---

### Post by dabbner on 2007-05-01
I experienced some issues with 7.04 as well.  What we all have to keep in perspective is that a 2-3 week old release is never totally ready.  I own an IT consulting company, and I can tell you that several months into it, we are still not selling Vista to our customers.  Our standard party line is "wait for the application developers to catch up and wait for MS to get their first big patch or service pack out before we decide how to proceed."

We all know that most companies will eventually embrace Vista (and many others will just have it forced upon them).  Even XP, which is now a great OS was total junk prior to SP1.  Ubuntu is no different.  A proven distro will offer fewer features, but more stability.  A fresh, still wet behind the ears release will be more visually stimulating, and will offer a variety of cool new bells and whistles.  

Everyone has to decide what is for them.  I currently run 1 OSX Mac Mini, 1 Vista PC, and Ubuntu on my home desktop and work laptop.  I also have a 2003 R2 and a Ubuntu 6.06LTS server in "production" at home to learn with.  

I first touched Ubuntu at 5.10, and it wasn't ready.  Now 7.04 is a HUGE improvement.  I hope you will give it another try at a later date.  The improvements are amazing, and coming quickly.

---

### Post by rygar on 2007-05-01
i just installed ubuntu for the first time a few days ago.  while i agree with you on some points, especially driver related issues (screen resolution and whatnot), did you really think mp3 support was an issue?

ubuntu automatically detected and read my ntfs partitions (the reverse of which cannot be said for windows), so i could access my mp3s.  i double clicked on one and it tried to open in movie player, but a pop-up came up and said 'this codec is not installed, do you want to install it?' and i clicked yes.

while some modifications seem to be a pain to someone who's not linux-savvy like myself, i found many issues (like mp3 support) as simple as clicking a button.

certainly, i wouldn't recommend linux for everyone--or anyone, for that matter, who is not computer savvy.  while the ubuntu distribution is pretty user friendly, you're almost predestined to do some troubleshooting right off the bat to get everything working the way you like it.  i feel this intimidates a lot of computer illiterates who dont want to deal with such nuisances.  there's still a long way to go before any linux distribution can compete with windows or mac in terms of catering to the common user.

---

### Post by Goombie on 2007-05-02
I agree with rygar; some modifications can be a pain (for me, getting my wireless card working), but overall Ubuntu seems to be one of the most user-friendly Linux distros out there. It's similar enough to Windows that I don't feel totally lost, yet with handy new features that make things more fun. While some things don't work quite right out of the box (the extra buttons on my mouse, for example), almost all the other components in my PC do. I'm also fortunate in that I have enough hard drive space to keep Windows XP, Linux, and my personal files on separate partitions, which makes file management a lot easier. So, I hope that you'll try Linux again sometime. It's not perfect yet, but nothing is. It's getting closer, though. :)

---

### Post by Ptero-4 on 2007-05-02
Too bad that you got scared by a bunch of M$C`s refusing to run linux (M$C`s are designed to refuse running linux). I hope next time around you get yourself a true PC (Apple or System76 boxen are PC`s) and try linux again, I tell you run linux on a real PC and you won`t look back at windoze anyome (I run feisty on an Apple eMac PPC).

---

### Post by krdt on 2007-05-02
I've been very lucky with Ubuntu so far.   As a long-term user of machines back to well before DOS (remember the days of PET-Apple-Tandy at home and a PDP-11/Elliot-900 mainframe running an entire University on punchcard input or ASR-33 teletype input/output) I've tried most things over the years, including just about every version of DOS/Windows but never got into Mac/Apples.

I've run most of the Linux distributions including Mandrake, Gentoo, RedHat/Fedora, Debian and Ubuntu is certainly one of the friendliest and easiest to work with and install.  Last year, Edgy installed flawlessly on my generic Intel/Asus system, recognizing both soundcards correctly, setting the widescreen resolution without hassles and happily connecting to my HP printer-scanner.  It took very little time to get it up and running on my network, and it recognized Windows drives and machines easily.  Nvidia drivers loaded easily, as did a bunch of amateur radio programs via checkinstall.  I don't run wireless, but the wired network worked flawlessly.  So did my Pentax SLR digital camera using UFRaw and Gimp.

When Feisty came out, I upgraded via the Internet with very few problems.  I did have to change the xorg.conf back to use the nv driver rather than nvidia temporarily, then use the restricted driver manager to reload it, and I did have to make Grub use the -generic rather than -386 kernel as default, but that was pretty painless.  There were no other major issues, and all of the added software including the amateur radio programs and camera raw software for photography upgraded automatically and work well.

With VMware's free VMPlayer running XP Pro SP2 as a virtual machine, the few Win XP programs I need/use are easily available, including access into work's Windows programs via their Citrix interface portal.

This is in stark comparison to my experience with my wife's new machine.  She went out on her own and bought a cheap Vista Home package deal (ouch!). Setting it up, getting it to talk to even the other Windows machines on the network, let alone Samba, and to use other printers was a nightmare of non-existent or hard to find drivers, and it still doesn't fully work with everything properly after messing for over a week.

Ubuntu team, if this release is this good this early in its lifespan, you did a GREAT job!.

---

### Post by indigoshift on 2007-05-02
> **detroit/zero said:**
> But then I remembered.. I'm trying to do it the *Windows way*; that's why it's not working!

That's the golden rule, right there.

You know, I've always had bad luck with upgrades as well.  I've upgraded three "steps" on two different machines, and it always breaks something to the point where I have to just scrap it and install the latest version fresh.

As for wireless...other than a weird glitch last week (which affected both my and my wife's laptops) where I couldn't get an IP from my router, it's always worked perfectly for me.

If you're tired of it, just be done with it for awhile, man.  Nothing bad will come of that.  By the time the bug bites you in the *** again (and it will  ;) ), there'll be a new version ready to download/burn, and that's always a fun thing to discover.

---

### Post by regomodo on 2007-05-02
> **detroit/zero said:**
> My upgrade from Edgy to Feisty was less than stellar as well. I backed up all my desirables to about 7 DVDs and did a fresh install. After months of fighting Edgy to get my nVidia card to work, I made patchwork of about 6 different install methods for nVidia restricted drivers and got it up and running. (FYI: System>Administration>Restricted Drivers doesn't do the trick..)

I got all my data back on my drive, nVidia works,  unimpressed with the Desktop Effects performance I've since installed Beryl and am happy as a lark with the whole experience.

I can't say I've enjoyed the endless hours of pecking away at a keyboard and scouring forums looking for answers like you say but, in retrospect, I've learned a lot along the way and after years and years of being stuck in Windows, I've finally got the system I want.
[B]
And it didn't cost me a dime.[/B]

I'm looking at my Beryl Cube and I can't believe that people with XP (and Vista) will pay hard earned money for the "privilege" of *skinning their desktop*.

I read an article a while back about why Windows users find it hard to make the transition to a Linux system. It said that "power users" often had the more difficult time, because there's a *Windows way* of doing things, and a *Linux way* of doing things. Power users often get very frustrated when the methods they know and use are no longer useful.

I've hit that roadblock many times, and almost pulled out my XP system restore disks and started over with that nightmare. But then I remembered.. I'm trying to do it the *Windows way*; that's why it's not working!

I'll take editing configuration files to get exactly what I want over paying someone for software that doesn't perform as expected/advertised in the first place.

Yeah, i didn't like the desktop effects. At first it didn't configure the xorg correct. I sorted that out. Then i noticed how slow it was to switch between apps and click on buttons. I'm using an oc'd 6800gt for petes sake!

Switched to Beryl. Boy was that a lot easier to install than in Edgy! 

I too tried Ubuntu for a while and got so farkin stressed out with it so i wiped it from my hdd. Came back to it a few days later with the gained knowledge and got most stuff sorted within 1.5hours. Granted, a total beginner wouldn't know how to do most of the stuff i did, and shouldn't.

Can't speak about Feisty tbh. I upgraded and all went swimmingly.

Still not got everything sorted on it that i need, thats why i'm typing from XP

---

### Post by RandySavage on 2007-05-03
> **fugufish said:**
> Having been in IT for many years and a PC enthusiast since the 80's I had often kicked around the idea  to try out Linux.  About a month ago I read a great article called 30 days with Linux and decided to give Ubuntu 6.10 a try.
[http://consumer.hardocp.com/article.html?art=MTI5OCwxLCxoY29uc3VtZXI=](http://consumer.hardocp.com/article.html?art=MTI5OCwxLCxoY29uc3VtZXI=)

I installed Edgy on several test boxes ranging from brand new HP dual core towers to an older P4 2.4 we built with spare parts laying around the shop. The installs went well generally but I was struck by seemingly simple things that didn't work right out of the gate. I.E. my mouse thumb buttons didn't work with Firefox while browsing. I don't mind tweaking and I spent hours scouring various foums until I found out the right settings to "hack" into xorg.conf. I learned a valuable lesson about backing that file up before changing anything as one wrong setting will brick your x server. Another thing that didn't work correctly was screen resolution. You would think that a modern OS would correctly detect your LCD monitor's capabilities and allow a standard resolution of 1280X1024. But no, more hacking of the xorg.conf file to add the desired resolutions. Then there is the lack of .mp3 and DVD playback support. I understand that their are legal reasons why these things  aren't  included "out-of-the-box" and they can all be added in but if the Linux community hopes to lure more people away from XP/Vista, this isn't the way to go about it. It simply takes too much time to get Linux to the same level of usability as a standard XP install. I found that the solutions to most problems involved entering long, arcane strings of information  into a terminal window. 

I continued playing with Edgy and got beryl working on my old GF4 Ti4200 card with the Nvidia "legacy" drivers.(what a joy to install those from a command line) I got embedded .wmv support working and pretty much had Edgy working the way I needed it to. Still, I didn't really "need" linux. I used it for browsing, music, IM and email.

Then I '"upgraded" to Feisty and it all went downhill. I used the official upgrade method. Waited 6 hours and
after the reboot was left with a broken x-server. Some incompatibility with the default legacy driver and my old graphics card. I backed up my data and wiped the HD and installed fresh from a Live CD.
It was then that I discovered the LiteOn CD player bug which caused the system to hang for 5 minutes and boot with a non working optical drive. Pretty big bug. I found the workaround and added "irqpoll" to some
file somewhere. Booted into Feisty but could not get 1280X1024 resolution, again. Then the desktop started freezing every couple of minutes. (worked fine with XP so not a hardware problem).

That was it for me. Fixmbr, delete the Linux partition and walk away. At least for now...

I liken Linux to a Ferrari and Windows to a Toyota.  

Linux is fast.  Linux is sexy.  Linux will do all kinds of cool things to amaze your friends and impress the chicks.  Linux is also cranky, high-maintenance, has an enormous learning curve, and if not treated just right will leave you stranded on the side of the information highway.  It's hard to start Linux and all adjustment to its workings are done by hand.  When it runs, it runs great, but keeping it in top shape can take an big investment of time..

If all you're trying to do is get to work to get something done, that old Toyota will do just fine.  Better, in fact, than the Ferrari.  It'll require less maintenance, runs on regular unleaded, and things like valve-lash and brake adjustments are handled automatically.  The Toyota spends far more time on the road than in the shop.  Its not going to turn many heads, it will definitely be boring, you won't get anywhere in record time, but you will get there.

---

