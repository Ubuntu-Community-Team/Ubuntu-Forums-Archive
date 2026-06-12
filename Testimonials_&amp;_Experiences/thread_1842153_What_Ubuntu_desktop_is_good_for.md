---
title: "What Ubuntu desktop is good for?"
date: 2011-09-10
forum: Testimonials &amp; Experiences
---

### Post by alexei_ on 2011-09-10
I would like to share my experience with Ubuntu Desktop running on my laptop.

I decide to give a try Ubuntu on my laptop 1 year ago. Before I was using Windows XP Home. I use mostly browser, console, screen and vim. Using cygwin in Windows was not very exciting, but it permitted me to use Windows Home Edition for years.

One year ago I assumed the Ubuntu probably will run now fine on laptop.

In short I was surprised with all issues I had during this year using Ubuntu on my laptop. My laptop is Gateway NV5378U (15.6" Laptop AMD Athlon II X2 2GHz 4GB 500GB)

The main issue -- stability. I lost count of how many times my laptop was becoming irresponsible (probably better to say hangs) and I had  to do reset.
It may be strange to hear, but I wish Ubuntu to be at least as stable as Windows XP Home was for me before.

I started with "Ubuntu 10.04 64bit" and now I have 10.10.

Looking at this forum I see quite a lot other issues which did not have.

So my question would be who is suppose to use Ubuntu desktop?
What it is good for?

Looks to me it is good for somebody who is interested in dealing with issues all the time... Then "Canonical" has to be honest and state this at the beginning.

---

### Post by overdrank on 2011-09-10
Hi and welcome, not a request for support. Another unity thread. :)
Moved to  Ubuntu Testimonials & Experiences

---

### Post by Perfect Storm on 2011-09-10
It may comes down to hardware incompatibility/poor supported hardware in your laptop. As you haven't listed what kind of instability you're talking about I can't honestly say.
I have the opposite experience with computers I have installed Ubuntu on. I rarely fix/tweak things on it other than my own curiosity made me tinkering with.

At work when we (I) switched the machines from Windows (98/XP/Vista) to Ubuntu, I rarely have any maintaining to do anymore, other than the security updates.

---

### Post by IWantFroyo on 2011-09-10
Most computers have no issues, but once in a while, there will be a computer that has problems.

Linux is wonderful for most of my hardware, but Natty and Maverick both had problems with my Toshiba T235D.

Bottom line- if something doesn't work, it's because the hardware is really cutting edge (and there wasn't time to add support yet), or the manufacturer was a meanie and put in some rare/problematic chipsets.

Also, keep in mind that Windows has more problems with computer than Linux does. They just try to hide it.

---

### Post by 3rdalbum on 2011-09-11
It's a hardware problem; you have bad RAM. It's a shame you didn't detect it while the computer was still under warranty.

Windows systems encounter fewer symptoms of bad RAM, simply because Windows grabs up to 2 GiB of RAM and doesn't use it for anything. If the bad part of your RAM is within that grabbed space, you never actually see the problem.

If you run the Phoronix Test Suite's memory benchmarks and the computer crashes during that, it's a sure-fire indicator of bad RAM.

---

### Post by rjbl on 2011-09-11
@OP

[I]The main issue -- stability. I lost count of how many times my laptop was becoming irresponsible and had had to do reset.
It may be strange to hear, but I wish Ubuntu to be at least as stable as Windows XP Home was for me before.

[/I]Can't replicate your bad experience. Never, ever, seen any GNU/Linux system showing the sort of constant instabilities that you describe. Actually I have seen rather few MS/Windows systems showing the same degrees of constant instability. Check your RAM, sounds like you have might have major problem there, you haven't been fiddling with your BIOS settings, by any chance?

rjbl

PS I just love the idea of your laptop becoming 'irresponsible'. Happens to us all from time to time; but never a hardware or OS issue - that is Users for you :)

---

### Post by jasonrisenburg on 2011-09-11
I have used Ubuntu sine 2007. The only time I have had stability problems is when I caused them by using a unstable beta program or trying to "make it" what I want ans erasing the grub.... that was a funny night. As for who should use Ubuntu, what does Ubuntu mean and is it right for you. If not windows 7 is a pretty good os and well mac is good to. I do prefer Ubuntu over them simply for the fact that I can make it what ever I want it to be. Look how I want it to looks and after I break it, I will put it back together and start over. I wish you best in all that you do computer wise, and hope you find what linux means to you.

---

### Post by stalkingwolf on 2011-09-11
It could be as simple as the 64 bit system.  I have read many accounts of issues with the 64 bit systems windows included.

I have used Ubuntu on laptops since at least8.04 with only one persistant issue and that was a hardware issue. 

I have installed it on everything from an everex (graphics card issue) to a 7"asus EEE several HPs, afew Dell's, a 10" EEE and an ibm.

I guess i have been lucky, sound has always worked, occasionally i had to add a graphics driver.

as an aside i have 5 computer that i run, my bench system and my desktop are customs, my wifes is an emachines that we bought for the monitor, ( it was a windows machine that would hardly boot when we bought it. paid 75.00 for the entire system with printer.
removed 225 viruses and it works beautifully. bought it for the 19"HD monitor.)  an IBMT42p and a 10 eee.  the only ones unity will work on is the laptops.

---

### Post by alexei_ on 2011-09-11
Thanks for all your replies.

While using 10.04 the main issue was with "stand by" -- system used to hang during return from "stand by". For me "stand by" is a key feature. I was not the only person affected by this -- there was big thread about this issue. By now I do not observe the issues any more. The main thing I learned from this -- Ubuntu is not doing enough testing. As a result many users get affected...

After upgrading to 10.10 I start seeing another issue. After playing several of "mts" (high definition videos from my camera) something is happening that totem or vlc can not play any video. Some time later usually the system hangs -- black screen with no ability to do anything other then reset (Ctrl-Alt-F[1-7] -- is not working also). Sometimes I the system hangs with garbage on the screen (horizontal lines with alternating colors). This could be hardware or driver... Is there any log file I can use to troubleshoot this?

BTW, I heard some people prefer to re-install Ubuntu for each release, because release upgrade often does not work well.

Playing "mts" is another issue. Yes, "AMD Athlon II X2 2GHz" is not very strong, but Windows 7 with default player plays them almost perfectly on this hardware. Sometimes totem/vlc is able to play "mts" OK... but often image gets semi-frozen... the impression is that hardware is not powerful enough... but how Windows 7 does it?

I also have to say my laptop is not the only Ubuntu machine I am using. With those the main issues were during upgrade to next release. I had issues with some libs which were deprecated in next Ubuntu version. So I had to do research how to make things working. Another frustration was UI changes. Ubuntu upgrade was not "bothering" to give an option to keep my existing UI settings... again I have to search forums in order to get my UI back. So now I avoid upgrading release if possible...

However for my desktop (build in 2004) I had issues even during regular update. Several times after upgrade the system could not start with updated kernel. Good for me was that I could change kernel version during boot time when I was near that computer... but this would be a huge problem when I manage this computer remotely... 

 The main reason to upgrade release is to get new version of software which I do not like to compile myself (probably I will have to start doing this because even latest Ubuntu release is often missing newest versions)... 

BTW, for me to upgrade to 11.04 I need to re-size a partition -- I wish I could guess needed size before... If I understand correctly existing size of partition would work fine in 11.04, only during release upgrade additional space is needed... Why Ubuntu can not use a different partition?

Regarding release every 6 months. My experience shows to me that Ubuntu is trying to do things too fast without appropriate testing.

With issues described above can we expect non-technical person to become Ubuntu user?

---

### Post by stalkingwolf on 2011-09-12
i have 3 very non technical people in my family that use it quite happily.

---

### Post by walt.smith1960 on 2011-09-12
> **IWantFroyo said:**
> Most computers have no issues, but once in a while, there will be a computer that has problems.

Linux is wonderful for most of my hardware, but Natty and Maverick both had problems with my Toshiba T235D.

Bottom line- if something doesn't work, it's because the hardware is really cutting edge (and there wasn't time to add support yet), or the manufacturer was a meanie and put in some rare/problematic **cheap **chipsets.

Also, keep in mind that Windows has more problems with computer than Linux does. They just try to hide it.

"manufacturer was a meanie and put in some rare/problematic **cheap **chipsets."  Same mindset as WinModems.  Manufacturer: "But if I use the oddball all-in-one chipset, I can save $5/machine"

---

### Post by XubuRoxMySox on 2011-09-12
I have "distro-hopped" (trying a new Linux distro) dozens of times off and on looking for the perfect mixture for me, that would run on my hardware, be easy for the kids who share this computer to use without coaching, that would be stable, safe, not subject to being broken regularly by updates, etc etc.

From the "kiddie distros" for "ordinary desktop users" (whatever that is supposed to mean) like Ubuntu and PCLinuxOS to "advanced" geeky ones (like Slackware and Crunchbang), it boils down to three things for me: **Hardware**, **repositories**, and **support**.

**[COLOR="Blue"]In all three areas, there is absolutely nothing that surpasses the Ubuntu family (Lubu, Xubu, Kubu, and their derivatives).[/COLOR]** Ubuntu can be as geeky and difficult as the most tech-savvy nerd wants it to be (with a minimal install); as light and fast as any low-spec computer needs; or as super-simple and kid-friendly as any member of the family needs. Hardware support is unrivaled. And support? From the paid support from Canonical to this awesome community, it too is unrivaled.

Of course it has it's downsides, as with any Linux distro that uses the one-size-fits-most approach. But it doesn't *have* to be a one-size-fits-all thing. It can be what you make it - you don't have to "take what you are given and learn to like it." Like um, certain proprietary OSes.

For stability issues I stick with the LTS releases, at least for as long as I'm down to one single 'puter that is "mission critical." I select only security updates. I remove cruft and heavy applications I have no use for. Troublesome software (PulseAudio and Brasero in my case) is removed and/or replaced (ALSA, Xfburn in my example). It takes a bit of trial-and-error to discover what works best for you and your hardware. Give yourself time to make those discoveries at your own pace.

And one other li'l thing I've learned along the way: **Keep a record of what you did and why.** It helps me avoid repeating some mistakes and forgetting why I needed this or that, or why I dumped this-or-that in favor of the other thing.

Take your time, relax, and try to make it fun. You just might discover an "inner geek" inside!

---

### Post by wolfen69 on 2011-09-14
> **alexei_ said:**
> 
Looks to me it is good for somebody who is interested in dealing with issues all the time...

If that was the case most of the time, no one would use it. I've had almost no issues after 7 years on many different computers. I've actually had many more problems using windows.

---

### Post by mastablasta on 2011-09-15
> **stalkingwolf said:**
> i have 3 very non technical people in my family that use it quite happily.
 
 
well if somoene else fixed all the starting issues (instea dof me doing all the search and asking arround) and the issues still remaining on my maschine i would also be using it quite happilly.

---

### Post by armandh on 2011-09-15
I just set up my daughters old stand-by laptop
dual boot XP-sp3 and Ubuntu 10.10

the oem xp had finally filled with cra# and was unusable

both work, Ubuntu took half the time and came with lots more
[lots more useful stuff as opposed to bloat ware]

---

### Post by cheesennacho on 2011-09-16
I've been bouncing from distro to distro for 4 months now and ubuntu is the only one that works flawlessly out of the box for me. I have found ways to get what needs to be done one way or another that I used to do in mswindows, which is what makes linux in general exciting to me. The other products have become just plain boring, so when I started experimenting with Ubuntu it felt good to shaky shaky and get rid of the cobwebs. 

My other machine is a mac, haven't had a windows box for long time

---

### Post by Sef on 2011-09-17
off-topic. Locked.

---

