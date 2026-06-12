---
title: "My Hardy Heron review and why I'll be back to Gutsy"
date: 2008-04-25
forum: Testimonials &amp; Experiences
---

### Post by Kosimo on 2008-04-25
My Hardy Heron Experience: 


**The good: **


Installation:

1, Language selection since the first step.  This is amazingly nice for millions of citizens. 

2, The option of Install Ubuntu with faster booting time. When you just want to install Ubuntu you don't need to load the entire operating system. 

3, When resizing the HD, now is totally clear witch partition is for Windows and witch one is for Ubuntu, and you can resize them by moving that small bar.  I personally love this one. 


**Experience: **

1, Booting time is much faster in my computer

2, Finally the usplash boot bug has been solved.  (At once and for all)

3, Network manager is always better and better. Now is easy to find out saved WEP or WPA/2 passwords, edit or delete them. This is very useful for people like me who changes passwords but maintains the Wireless network name.

4, Powertop works gorgeous with new Kernel. My CPU reaches C3 status at once and for all.


**The bad:**

1, can't load desktop effects anymore. (see: [this post]("http://ubuntuforums.org/showthread.php?t=764005")) 

2, Firefox is buggy for me. Today crashed more than 15 times. Honestly. 

3, My laptop is connected to AC Power, and battery is off, anyway I still get this: 

[IMG]http://kosimo.googlepages.com/nobattery.jpg[/IMG]



**The Bottom: **

1, Pulseaudio inclusion sucks. Really guys, this is horrible. Examples: 
Audacious 1.5 from repositories: When enabling the equalizer the sound is corrupt, then when moving eq bars music stops playing, then I need to change plugin and activate ALSA. But... Then the EQ effect is gone...      BMPx...  When Hardware Acceleration is enabled, sound is totally corrupted, with noises and strange behavior. Eq doesn't make any effect even if you activate it.    Zattoo...  Audio stops after 30 seconds of playing.  
....
......
........ (no comment)


[B]Conclusion
[/B]
I don't know why I'm having this problems, where the problem comes from, and I'm 100% sure that it can be solved. I have no doubt about it. But, I have no time to play with it, really. I just get some free time and I want to spend it in another way than trying to fix my computer at home. (I spend almost all my time fixing computers in my job).

I'm also sure that in some months, Hardy will become extra stable and many of this issues will be solved. For me, this are serious issues, that makes MY SYSTEM really unstable. So, what I'm going to do is going back to Gutsy and update it 'till last updates. For me, is much  more solid, and sable that the current Hardy, Audacious works perfectly, Firefox doesn't crash, Desktop effects are enabled by default, and Zattoo plays audio all the time.  

I love Ubuntu and I will give Hardy Heron another try for sure in some months and then it'll may be stable enough for me. Question is... Is Hardy really ready to be released?

Please don't attack me, this just want to be a constructive post for Ubuntu devs. Now, thanks to them I can have a rock solid Gutsy and play with it.


Thanks for reading.


A guy in love with freedom.

---

### Post by akiratheoni on 2008-04-25
As for Firefox, it IS in beta actually.

Now, I don't think I've had Firefox crash on me at all in all the times I've used the beta on Windows or Linux but every user's experience is different.

For me, Hardy's been working fine for me other than my 1680x1050 resolution. I just used my old xorg.conf from Gutsy for it.

Hardy will soon be ready for you though, don't worry. Every new OS version gets blasted and praised at the same time. It'll just take a little bit of time. No problem with staying with Gutsy, though.

---

### Post by justin whitaker on 2008-04-25
> **akiratheoni said:**
> Hardy will soon be ready for you though, don't worry. Every new OS version gets blasted and praised at the same time. It'll just take a little bit of time. No problem with staying with Gutsy, though.

I'm sorry, but that just isn't true. People are holding Ubuntu up to what they said that HH was supposed to be: the version that got Long Term Support. 

Noone cares if Ubuntu screws the pooch on a 6th monther...you can always wait for the next edition and see if the developers get around to fixing the bugs. 

On an LTS version, however, one expects it to be dead solid. Think of 6.06. and the following 6.06.1. How stable and solid were they? Ok, now look at the issues that everone seems to be having with Hardy. See a problem?

Now Canonical created this issue themselves. Noone said that they should call the next version an LTS version, and noone said that they should add new applications to an LTS version. This was all self imposed.

Frankly, if I were a corporation looking for a Linux solution, I would not be considering Ubuntu at this point. I don't want to make a pitch for Linux by saying "just give it a bit of time." That is a cop out. 

This version should have been dead stable, reliable, and provide users that wanted a no-brainer/no-risk desktop for the next 3 years. 

They didn't get it. 

Now, I say this while running HH, and it has no issues with my hardware. I just think Canonical shot themselves in the foot.

---

### Post by yaknowwat on 2008-04-25
Your Firefox Crashes are more than likely from flash and pulseaudio not working together.

I personally like pulse audio WITH its management addons. such as devicechooser manager volume control etc.
Though i noticed in hardy they didn't include the pulseaudio device chooser by default (IMO one of  the key features of pulseaudio as it allows easy control over sound streams)

I don't know why they didn't in Hardy but they should have included NSPluginWrapper by default on 32 bit versions, this would increase firefox's stability (firefox 3 beta is far stabler than 2 by default its just plugin issues around it.) as flash or any other plugin would crash a npviewer (NSpluginWrapper viewer) instead of firefox, same would go for other addons.


As for Desktop effects the way xorg.conf is done now is slightly different so i suggested reconfiguring xorg-server in order for it to enable the correct drivers. (i had to reconfigure xorg-server to install restricted drivers).

---

### Post by tc101 on 2008-04-25
> Frankly, if I were a corporation looking for a Linux solution, I would not be considering Ubuntu at this point. 

What would you be considering?

---

### Post by akiratheoni on 2008-04-25
> **justin whitaker said:**
> I'm sorry, but that just isn't true. People are holding Ubuntu up to what they said that HH was supposed to be: the version that got Long Term Support. 

Noone cares if Ubuntu screws the pooch on a 6th monther...you can always wait for the next edition and see if the developers get around to fixing the bugs. 

On an LTS version, however, one expects it to be dead solid. Think of 6.06. and the following 6.06.1. How stable and solid were they? Ok, now look at the issues that everone seems to be having with Hardy. See a problem?

Now Canonical created this issue themselves. Noone said that they should call the next version an LTS version, and noone said that they should add new applications to an LTS version. This was all self imposed.

Frankly, if I were a corporation looking for a Linux solution, I would not be considering Ubuntu at this point. I don't want to make a pitch for Linux by saying "just give it a bit of time." That is a cop out. 

This version should have been dead stable, reliable, and provide users that wanted a no-brainer/no-risk desktop for the next 3 years. 

They didn't get it. 

Now, I say this while running HH, and it has no issues with my hardware. I just think Canonical shot themselves in the foot.

So it's supposed to be perfect from the get-go, huh? The final release hasn't even been out for two full days and you're already complaining and saying it should have been perfect... makes me wonder exactly how much criticism Vista got in its first day.

I'm kind of surprised. Am I the only person who goes into Hardy and doesn't expect anything to work? Then everything works (or most of it) and I'm happy. It's all about the pessimism :P Then you're never disappointed.

---

### Post by thisllub on 2008-04-25
I agree about Firefox 3. 
It doesn't work at all for me.

I upgraded so maybe removing the folder and starting again would be a good option but why would I bother? I installed Firefox 2 and use that.

It seems that Ubuntu is going the route of "more is never enough".
I tried Mint and hated it for just that reason.

It would be a shame to see any Linux turn into a Windows like resource pig but I fear that is what is happening to Ubuntu.

---

### Post by Koori23 on 2008-04-25
I myself am half way tempted to revert back to 6.06.1. I haven't made up my mind yet though. 

Well, that usplash bug you spoke of, still occurs and has occurred ever since 6.06. 

console-kit-daemon what the heck is that? Why do I have a million of them and why is it that when I kill all instances of it, my computer functions normally?

---

### Post by Mazza558 on 2008-04-25
The LTS is simply that - Long Term Support. Where does it say "VSLTS" or "Very Stable Long Term Support"? Dapper was a very stable release because it was delayed 2 months to fix the bugs left before release. I do think, however, 8.04 should have become 8.06, as there are still a few bugs that ruin the experience for some.

---

### Post by Onyros on 2008-04-25
> **tc101 said:**
> What would you be considering?Debian? That's as solid as they come. A few packages outdated, but when Debian releases something labeled as stable, you can count on it.

I still haven't upgraded the laptop I have that's still running Ubuntu, the other times around I always upgraded early but now I just don't have the time to correct all the problems it always encompasses. And that's coming from someone who uses Arch, primarily! I remember helping a few people out that had problems with Feisty --> Gutsy's upgrade, including a few unbootable boxes resulting from a kernel update.

Pulse Audio and Firefox 3 (while still in BETA) as default in what's supposed to be a LTS release is questionable, to say the least. And don't give me that "it'll be corrected when 8.04.1 comes out". Hardy IS supposed to be the LTS release, so people are expecting it to be rock solid. There are a few choices for defaults I can't agree with, like compositing enabled by default, Tracker, etc.

When Gutsy came out, it brought a few problems of its own with it. Many problems, if we read back just 6 months ago in these very boards. So this is a 6 month cycle. Every 6 months we have people whose upgrades went horribly, and then some other people dismissing that and saying that it's the best release ever :P

I suppport Ubuntu totally. I think its contribution to Linux and the entire FOSS community are invaluable. But with all the choice we have around, it wouldn't be my first choice right now. I keep it installed more as matter of curiosity, because I've found something which suits me better somewhere else. Doesn't mean Ubuntu is worse, it's just different, its philosophy is different. Setting it up is one of the easiest things around, the forums are just incredible means of problem resolution... but every 6 months that balance is challenged.

Unfortunately, upgrades aren't as seamless as one would expect, many new features are added and it's hard to predict how it would all work out on every type of hardware combinations possible. That's where I question the defaults' choice, they should be more focused on stability rather than on innovation (again, especially when we're talking about an LTS release).

There are alternatives. Ubuntu isn't = Linux. ;)

BTW, I'm with Mazza. It wouldn't hurt anyone if it were 8.06 and much more polished than it (supposedly) is.

---

### Post by M_Alex on 2008-04-25
Well, i have to say that I toyed around with Edgy, returned to Windows XP, and then I tried out gutsy, and it stayed on my laptop. ATM i'm seriously thinking about returning to gutsy. I do actually think that i rushed it and got Hardy to fast, its too buggy for my taste. The sad thing is that although these are not bugs which totally render the system unusable, they are really irritating. Sorta like the feeling I got when using vista (I confess that I like XP quite alot). I do believe that Hardy will be fully operational one day, but I'm really thinking of going back to gutsy until that happens. Ironic considering the motto of Hardy (you know, the "you'll never go back" one.

BTW: Firefox kept crashing and blocking the system all the time. Luckily firefox 2 is available in the repositories, so i just switched it :)

---

### Post by K.Mandla on 2008-04-25
Moved to Testimonials and Experiences.

---

### Post by K.Mandla on 2008-04-25
Thread moved to Testimonials and Experiences.

---

### Post by K.Mandla on 2008-04-25
Weird double post. :???:

---

### Post by madjr on 2008-04-25
some fat bugs:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/198453](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/198453)

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/185209](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/185209)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188226](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188226)

---

### Post by karellen on 2008-04-26
> I'm kind of surprised. Am I the only person who goes into Hardy and doesn't expect anything to work? Then everything works (or most of it) and I'm happy. It's all about the pessimism :P Then you're never disappointed.
if you expect nothing, or almost nothing, to work on an OS, why use it in the first place? why introduce new feature when old bugs haven't been solved yet? lots of why...

---

### Post by berlinbrown on 2008-05-01
I haven't gone over everything; but FF is crashing on me all the time.

Take over windows?  Yea right.  Maybe next year.

---

### Post by StormTrooperVII on 2008-05-27
For the audacious problem, I found that sudo apt-get remove audacious and then dpkg -i audacious 1.4.6 solved a lot of problems for me.  What was happening with 1.5 for me was that one song would play nicely, and then the player wouldn't play anything else after that.  i have yet to have problems with 1.4.6.  Note that you need the 1.4.5 version of the plugins too (not a typo, there is no 1.4.6 of the plugins).  I can't find the old versions now, but I did a few weeks ago, and I dont know if its been fixed in a new audacious release.  Anyway, good luck

---

### Post by Kosimo on 2008-05-27
> **StormTrooperVII said:**
> For the audacious problem, I found that sudo apt-get remove audacious and then dpkg -i audacious 1.4.6 solved a lot of problems for me.  What was happening with 1.5 for me was that one song would play nicely, and then the player wouldn't play anything else after that.  i have yet to have problems with 1.4.6.  Note that you need the 1.4.5 version of the plugins too (not a typo, there is no 1.4.6 of the plugins).  I can't find the old versions now, but I did a few weeks ago, and I dont know if its been fixed in a new audacious release.  Anyway, good luck

All audacious problems I had in Hardy are solved already. We had an audacious update a week ago or so, and that solved all problems with crashes and eq

---

### Post by stchman on 2008-05-28
I have Hardy installed on 3 different PCs and it is very stable.  No lock ups at all.

Firefox 3 is far better than Firefox 2.

Keep up the excellent work Ubuntu.

---

### Post by webcoded612 on 2008-05-28
> **Kosimo said:**
> My Hardy Heron Experience: 


**The good: **


Installation:

1, Language selection since the first step.  This is amazingly nice for millions of citizens. 

2, The option of Install Ubuntu with faster booting time. When you just want to install Ubuntu you don't need to load the entire operating system. 

3, When resizing the HD, now is totally clear witch partition is for Windows and witch one is for Ubuntu, and you can resize them by moving that small bar.  I personally love this one. 


**Experience: **

1, Booting time is much faster in my computer

2, Finally the usplash boot bug has been solved.  (At once and for all)

3, Network manager is always better and better. Now is easy to find out saved WEP or WPA/2 passwords, edit or delete them. This is very useful for people like me who changes passwords but maintains the Wireless network name.

4, Powertop works gorgeous with new Kernel. My CPU reaches C3 status at once and for all.


**The bad:**

1, can't load desktop effects anymore. (see: [this post]("http://ubuntuforums.org/showthread.php?t=764005")) 

2, Firefox is buggy for me. Today crashed more than 15 times. Honestly. 

3, My laptop is connected to AC Power, and battery is off, anyway I still get this: 

[IMG]http://kosimo.googlepages.com/nobattery.jpg[/IMG]



**The Bottom: **

1, Pulseaudio inclusion sucks. Really guys, this is horrible. Examples: 
Audacious 1.5 from repositories: When enabling the equalizer the sound is corrupt, then when moving eq bars music stops playing, then I need to change plugin and activate ALSA. But... Then the EQ effect is gone...      BMPx...  When Hardware Acceleration is enabled, sound is totally corrupted, with noises and strange behavior. Eq doesn't make any effect even if you activate it.    Zattoo...  Audio stops after 30 seconds of playing.  
....
......
........ (no comment)


[B]Conclusion
[/B]
I don't know why I'm having this problems, where the problem comes from, and I'm 100% sure that it can be solved. I have no doubt about it. But, I have no time to play with it, really. I just get some free time and I want to spend it in another way than trying to fix my computer at home. (I spend almost all my time fixing computers in my job).

I'm also sure that in some months, Hardy will become extra stable and many of this issues will be solved. For me, this are serious issues, that makes MY SYSTEM really unstable. So, what I'm going to do is going back to Gutsy and update it 'till last updates. For me, is much  more solid, and sable that the current Hardy, Audacious works perfectly, Firefox doesn't crash, Desktop effects are enabled by default, and Zattoo plays audio all the time.  

I love Ubuntu and I will give Hardy Heron another try for sure in some months and then it'll may be stable enough for me. Question is... Is Hardy really ready to be released?

Please don't attack me, this just want to be a constructive post for Ubuntu devs. Now, thanks to them I can have a rock solid Gutsy and play with it.


Thanks for reading.


A guy in love with freedom.

This is the most intelligent, honest, clear experience with Ubuntu I've ever read.  You criticized without being mean, praised without being gushy, and didn't mention M$ once.  

Very nice.  And if anybody attacks you, they're retarded and just like to complain.  

Excellent review.  Good luck with Hardy next time you give it a shot.  :)

---

### Post by webcoded612 on 2008-05-28
> **akiratheoni said:**
> So it's supposed to be perfect from the get-go, huh? The final release hasn't even been out for two full days and you're already complaining and saying it should have been perfect... makes me wonder exactly how much criticism Vista got in its first day.

I'm kind of surprised. Am I the only person who goes into Hardy and doesn't expect anything to work? Then everything works (or most of it) and I'm happy. It's all about the pessimism :P Then you're never disappointed.

Nothing is perfect from the go.  Win XP, probably the best OS Microsoft has ever released, was junk for the first six months.  It takes time to tweak and fine tune everything to make it all as broadly compatible as possible.  

As for the pessimism, that has kind of been my approach, too.  I was on a the phone with a non-Linux savvy friend while I was installing HH, telling him all about the manual configuration of xorg I'd have to do because for whatever reason Ubuntu couldn't manage to get a ATI Radeon X1300 graphic card working.  He's saying things like "Wow", and "Sheesh" and then my PC reboots for that first login, and it worked!  I was so stunned I almost went back to Windows, thinking my PC might be possessed, or that I was dreaming.  :P

I'm making a joke of it, I know, but in truth I had all the commands written down and step by step instructions to fix xorg from the off.  Since I expected the worst I was pleasantly surprised that it worked.  Had I expected it to work, I wouldn't be writing about the experience right now, would I?  I'd have forgotten about it.  

Pessimism can be your friend, if you let it.  :P

---

### Post by Sinkingships7 on 2008-05-28
> **webcoded612 said:**
> This is the most intelligent, honest, clear experience with Ubuntu I've ever read.  You criticized without being mean, praised without being gushy, and didn't mention M$ once.  

Very nice.  And if anybody attacks you, they're retarded and just like to complain.  

Excellent review.  Good luck with Hardy next time you give it a shot.  :)

Seconded.

---

### Post by jarvis13 on 2008-05-28
I am also extremely dissapointed with Hardy. Including Beta software in a LTS release is just dumbfounding for me. Lots of Audio problems, lots of crashes with Firefox and it's extra bloaty. The faster boot time is much appreciated, but it doesn't make up for all the faults I've had with it so far...both upgrading from Gutsy and installing fresh. I've used Ubuntu since Breezy then upgraded to Dapper which was rock solid and stable from the start...and this is just disappointing. 
I'll probably be switching to a new distro soon. I'll give Ubuntu another shot with 8.10. I really hope Intrepid is extremely stable (even if that means *GASP* being less bleeding edge by default!) and they'll cut down on some of the bloat.

---

