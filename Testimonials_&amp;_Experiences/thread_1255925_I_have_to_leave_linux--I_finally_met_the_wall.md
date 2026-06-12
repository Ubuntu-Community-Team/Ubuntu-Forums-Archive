---
title: "I have to leave linux--I finally met the wall"
date: 2009-09-02
forum: Testimonials &amp; Experiences
---

### Post by viking_maniac on 2009-09-02
This is a sad moment. I've used a lot of time on Ubuntu Linux up to this point of testing and learning, and everything was ready for the main/master install this morning. But suddenly,. it can't be installed anymore. And nothing has changed on my system either.
 
Every time Grub is about to be installed at the end of the install process, I get a fatal error message telling me that Grub could not be installed. Now I've tried everything. I've tried to fix the MBR with a Windows system DVD, other utilities, and even tried to setup and partition the HD using the Ubuntu installer itself. Nothing helps. I've tried everything reasonable that a computer engineer with 20 years of experience would've tried, since I am one, at least on Windows NT/XP/Vista/Server, but no luck. It's almost supernatural. I even tested the install CD, and it's fine. My HD is fine too. So is my hardware.
 
I guess this was the final drop. Linux contains more problem solving and hill climbing than enjoyment and down sliding. I don't expect only the latter in life, but I don't appreciate too much of the first either. Though, I did like Ubuntu and the freedom, safety and opportunities it delivered me for a while. But I don't have the time or motivation to run a system that is such instable and unpredictable, and use an over-ratio of time to do things that one should not have needed to do in 2009 and which I don't need to do on the Windows platform, especially not on the server platform. I guess I've been spoiled by a system that just *works* as in always. These negatives have been my general impression and experience with most freeware, though. When things are too good to be true, they mostly are.
 
I want to thank everyone who have helped me during my time here and I want to compliment this great community. *Greets!*

---

### Post by wandalalakers on 2009-09-02
> **viking_maniac said:**
> This is a sad moment. I've used a lot of time on Ubuntu Linux up to this point of testing and learning, and everything was ready for the main/master install this morning. But suddenly,. it can't be installed anymore. And nothing has changed on my system either.
 
Every time Grub is about to be installed at the end of the install process, I get a fatal error message telling me that Grub could not be installed. Now I've tried everything. I've tried to fix the MBR with a Windows system DVD, other utilities, and even tried to setup and partition the HD using the Ubuntu installer itself. Nothing helps. I've tried everything reasonable that a computer engineer with 20 years of experience would've tried, since I am one, at least on Windows NT/XP/Vista/Server, but no luck. It's almost supernatural. I even tested the install CD, and it's fine. My HD is fine too. So is my hardware.
 
I guess this was the final drop. Linux contains more problem solving and hill climbing than enjoyment and down sliding. I don't expect only the latter in life, but I don't appreciate too much of the first either. Though, I did like Ubuntu and the freedom, safety and opportunities it delivered me for a while. But I don't have the time or motivation to run a system that is such instable and unpredictable, and use an over-ratio of time to do things that one should not have needed to do in 2009 and which I don't need to do on the Windows platform, especially not on the server platform. I guess I've been spoiled by a system that just *works* as in always. These negatives have been my general impression and experience with most freeware, though. When things are too good to be true, they mostly are.
 
I want to thank everyone who have helped me during my time here and I want to compliment this great community. *Greets!*

What version of 'buntu are you trying to install?  8.04, 8.10, 9.04, etc.
Try installing 8.04 is you are trying to install 8.10 or 9.04.
What video card, motherboard, chipset, cpu, etc. do you have?

---

### Post by prshah on 2009-09-02
> **viking_maniac said:**
>  
Every time Grub is about to be installed at the end of the install process, I get a fatal error message telling me that Grub could not be installed. 

I don't know if OP will ever get to read this, but for other vistors facing a similar problem, I'd suggest checking that the BIOS option for virus protection is turned off. The exact wording of the option varies, but will be similar to:

boot sector protection
virus protection
write protect sector 0 

...and so on.

---

### Post by Methuselah on 2009-09-02
That's a shame.
Installing != using though.
How have you found it unstable when you weren't able to install it?

Anyway, if Windows is the best choice for your applications and hardware by all means go that route.
Good luck with your further endeavors!

---

### Post by 3rdalbum on 2009-09-02
Although I am disappointed for you in that GRUB doesn't install, it's stretching it a bit to say that "Linux contains more problem solving and hill climbing than enjoyment and down sliding". As you've probably gathered, GRUB should always install; I've never seen it NOT install. In the highly-likely event that Ubuntu installs correctly, it's all downhill sliding.

And this sentence: "But I don't have the time or motivation to run a system that is such instable and unpredictable, and use an over-ratio of time to do things that one should not have needed to do in 2009 and which I don't need to do on the Windows platform, especially not on the server platform."

Linux is anything but "instable" or "unpredictable". It wouldn't be the most popular operating system for high-availability, time-is-money computing otherwise. I don't know what "should not have needed to do in 2009" that you've come across in Linux but most of the time it's just a misconception:

"OMG! You have to use the command-line to install Flash Player! It took me 5 hours of Googling to find out how!"

"No, just install the 'flashplugin-nonfree' package in Synaptic, it takes two minutes."

---

### Post by stefangr1 on 2009-09-02
I recently spend half a day on getting and usb-wifi device working on windows-xp, WITHOUT SUCCESS. In Ubuntu it worked after just connecting the usb cable. Should my reaction be to leave windows entirely because of that?

And for the freeware: there's at least not a lot of malware available for linux, and besides that both for windows and for linux available software ranges from barely functional to excellent. The big difference is though that for linux the community plays an important role in the selection of software, whereas you have to find out everything for yourself in windows.

---

### Post by PaulReaver on 2009-09-02
stupid question

have you tried lilo?

I find that half the fun in linux is fixing it when it goes wrong.

---

### Post by mdsmedia on 2009-09-02
Given that I've used Ubuntu as my main operating system for 4 years, installed it on 4 machines without a problem, never had a problem with Grub not installing, I'd say that you have a problem with your install disk.

I'm no expert, but I think it's either that or hardware incompatibility.

Given that you've spent so much time with Ubuntu, I'm a little surprised that you can't get it to install now. Somehow that doesn't make much sense.

If you really want to use a system which takes more maintenance than actual use, I can recommend an OS that gives no end of maintenance worries. It's called Windows.

Ubuntu/Linux isn't perfect, but for me it's so much easier and more maintenance free than Windows that I fail to see what your problem is. That is, since you've given so little detail.

Given that you're such a Windows expert, and that you've been a member here for...ohh...2 months....how long did it take you to work out the chinks in your Windows knowledge?

---

### Post by automaton26 on 2009-09-02
Your GRUB problem must be quite specific but solveable - the BIOS virus protection mentioned sounds like a strong possibility.

Or how about the last post here:
[http://ubuntuforums.org/archive/index.php/t-53102.html]("http://ubuntuforums.org/archive/index.php/t-53102.html").
It sounds like you might want to try removing all partitions on the disk completely, *before* trying an install.

Anyway, as an ex-Windows user, I can recommend taking a break if things seem insurmountable. I successfully returned to kubuntu on the second attempt, after a later version came out, and I had a brand new PC to try it on :)

It's well worth the investment of learning a different OS, but I still dual-boot because of games and certain devices.

---

### Post by ukripper on 2009-09-02
GNU/Linux protected ](*,)<------behind Fire**WALL**

---

### Post by PaulReaver on 2009-09-02
"Given that you're such a Windows expert, and that you've been a member here for...ohh...2 months"
Whats your point?

I've only been on the ubuntu forums for 6 months
Does that mean i can't use Ubuntu? Certainly not.
I started using linux on gentoo. ubuntu is a piece of p!ss. 
but not for everyone.


So you've been using Ubuntu since Breezy? well done. it seems to have worked out for. Congratulations.  It does'nt work out for everyone.

---

### Post by kerry_s on 2009-09-02
> Every time Grub is about to be installed at the end of the install process, I get a fatal error message telling me that Grub could not be installed.

by any chance did you use ext4 & grub2 ?

---

### Post by mdsmedia on 2009-09-02
> **PaulReaver said:**
> "Given that you're such a Windows expert, and that you've been a member here for...ohh...2 months"
Whats your point?

I've only been on the ubuntu forums for 6 months
Does that mean i can't use Ubuntu? Certainly not.
I started using linux on gentoo. ubuntu is a piece of p!ss. 
but not for everyone.


So you've been using Ubuntu since Breezy? well done. it seems to have worked out for. Congratulations.  It does'nt work out for everyone.
Sorry, but your OP gave very little detail. I could only use the fact that you'd been a member of the forums since June.

You indicated that you'd spent a lot of time on Ubuntu, yet you had trouble installing Ubuntu. To me that was a contradiction.

I could only speak from MY experience. I never actually used Breezy. I started with Hoary and upgraded to Dapper.

Your OP indicated that you'd spent a lot of time and only had problems. I only wanted to share my experience as being very positive.

My reply was simply contra to yours. I've had few problems. You've had problems. Your OP simply stated, from your point of view, facts. Mine did too.

---

### Post by viking_maniac on 2009-09-28
Hello, I'm back! :D

I don't know what went wrong, but it sure disappointed me! I may have done something wrong back then, but I seriously don't know what since nothing was changed. But now it suddenly worked! I re-downloaded 9.04 and burned a new disc. I'll give it another go--and I apologize for being such a crybaby. lol.

---

### Post by GodLikeCreature on 2009-09-28
I have installed ubuntu in more than 10 PCs now, from relatively old laptops to very current workstations, always successfully in the first go.

I did have an issue when installing intrepid because my HD was old, so I had to choose one specific GRUB option and add old IDE support, but that was about it.

The ubuntu installer has always worked flawlessly.  I admit I have had my share of issues, mostly around Wireless cards support, but nothing installation related.

I agree with other posters that this is very strange, and perhaps related to your own machine rather than anything else.

Having said so, if Windows works for you, I would install Ubuntu using Wubi.  Not Ideal, but I think that could get around your problem perhaps.

Good luck

---

### Post by Bucky Ball on 2009-09-28
Install 8.04 LTS if you want stability.

---

### Post by Thorndog on 2009-09-28
> **3rdalbum said:**
> 

"No, just install the 'flashplugin-nonfree' package in Synaptic, it takes two minutes."

I am running quad processor so 64 bit. The flashplugin-nonfree did me no good whatsoever on my 9.04 install!!!!. A lot of sites kill firefox now if you don't have flash 10 so the forums and 3 hours or so is what it took me to get it sorted, and I am not daft. 
Started using computers on a pet and clearly remember how great windows 1.0 seemed.
Still, I just installed 9.04 on three radically different machines , took me quite a while in all honesty but I like it. It fixed my 2 linpus acer netbooks neither of which would talk to networking any more. Big bonus that was. Worked straight away after install complete of the 9.10 netbook remix. Awesome job from the team that put that together!!!!
Just for the record, Windows does NOT always work right out of the box, it can take a day or more to get a machine going especially if you have problems with the drivers or wireless. Go find the latest ones etc.
I just setup dual boot on a Dell machine and the XP install is shutting the wireless off and on and stopping the system dead every 10 seconds for a few seconds. Pretty much unuseable and not the first time I've installed xp.
Sad to see someone give up on Ubuntu though.

---

### Post by Thorndog on 2009-09-28
> **viking_maniac said:**
> Hello, I'm back! :D

I don't know what went wrong, but it sure disappointed me! I may have done something wrong back then, but I seriously don't know what since nothing was changed. But now it suddenly worked! I re-downloaded 9.04 and burned a new disc. I'll give it another go--and I apologize for being such a crybaby. lol.

Yippeee!!
So you didn't *really* give up then. It's tough to give up.
Probably corrupt on the download. Did you do the checksum thing on the download and your live cd.

---

### Post by HappyFeet on 2009-09-28
> **viking_maniac said:**
> Hello, I'm back! :D

I don't know what went wrong, but it sure disappointed me! I may have done something wrong back then, but I seriously don't know what since nothing was changed. But now it suddenly worked! I re-downloaded 9.04 and burned a new disc. I'll give it another go--and I apologize for being such a crybaby. lol.
Unlike a lot of people, you were man enough to admit you were wrong. I give you props for that. JUST DON'T LET IT HAPPEN AGAIN! ;)

---

### Post by m4tic on 2009-09-29
Instead of installing a fresh new version, why not upgrade it from via update manager, it works well

---

### Post by stalkingwolf on 2009-09-29
> You indicated that you'd spent a lot of time on Ubuntu, yet you had trouble installing Ubuntu. To me that was a contradiction.


Not really.  I have done probably a hundred installs since 6.10.  Occasionally I still have install problems.  In almost every instance
I have traced the problem to 1) screwed up CDs,2) dirty or malfunctioning
cd-roms, 3) cd rom not playing with a certain brand of media,4) bad download
or 5) terminal error in the primary input device.

On one recent occasion i could not get the wireless to work either with 8.10 or 9.04.  installed 8.04 everything was fine.  A couple weeks ago I decided to give that laptop to a friend for school.  I did a fresh install for her.  I decided WTF ill try 9.04 again.    Ill be damned everything worked picked up and connected with both the internal and external wireless.

What changed ?  No Idea, it just worked.  I can take yes for an answer.

---

### Post by Bucky Ball on 2009-09-29
> **stalkingwolf said:**
> 

What changed ?  No Idea, it just worked.  I can take yes for an answer.

What changed is Jaunty is still being worked on and things get fixed and break. See what happens after the next update.

---

### Post by HappyFeet on 2009-09-29
> **Thorndog said:**
> I am running quad processor so 64 bit. The flashplugin-nonfree did me no good whatsoever on my 9.04 install!!!!. A lot of sites kill firefox now if you don't have flash 10 so the forums and 3 hours or so is what it took me to get it sorted, and I am not daft. 

It's actually very easy to do.

Go [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") and download the 64bit flash file. Right click and **extract here**. Then copy the resulting **libflashplayer.so** file. Then go to your home folder and do **Ctrl-H**. You will now see the hidden folders that start with a dot. Open the **.mozilla** folder and create a new folder called **plugins**. Paste the **libflashplayer.so** file there. Close out and restart firefox.

Works every time. I know it can be frustrating, but don't blame the OS when it's your lack of knowledge holding you back.

---

### Post by stalkingwolf on 2009-10-01
> What changed is Jaunty is still being worked on and things get fixed and break. See what happens after the next update.
__________________

actually no i used the very same CD.  have only made one copy so far.

---

### Post by running_rabbit07 on 2009-10-01
Whenever I find myself at a wall with no doors, I just put a hole in it and keep going forward.

---

