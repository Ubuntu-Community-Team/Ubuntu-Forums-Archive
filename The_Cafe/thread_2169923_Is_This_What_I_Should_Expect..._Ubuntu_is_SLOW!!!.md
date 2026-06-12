---
title: "Is This What I Should Expect... Ubuntu is SLOW???!!!"
date: 2013-08-24
forum: The Cafe
---

### Post by kalab2 on 2013-08-24
I just downloaded and installed Ubuntu 12.04.1
I'm coming from using a dual boot with Windows 7 & Linux Mint 15 Cinnamon.
Here's my question with a brief preface; I really like Mint, however, I know that it's based off Ubuntu so I wanted to give the real deal a try. My questions is, why is Ubuntu incredibly slow? I have to assume it was something wrong with the installation I did. I made a bootable USB per the instructions on the Ubuntu website and began install. One thing I did notice that seemed out of the ordinary is when I restarted, my computer booted into 7 without prompting me to choose an OS. Then I went to the USB, in windows, and installed it through there but it gave me a VERY basic window to install it. I restarted and Ubuntu booted.

Now, that's great, I thought. Except it's slow. Not, throw your laptop against the wall and chew it into tiny pieces slow, but slower than 7 and significantly slower than Mint. I'm really hoping someone can tell me if I did something wrong or if there is something I can do to fix the problem.

I was able to go through and do all the updating and installing of all the necessary codecs and such to get my machine doing the things I want it to (flash, java... blah blah blah) but from the beginning it was *extremely *laggy and remains as such. Please help if you can, I love the way Ubuntu with Unity works and looks but I can't deal with waiting for things as simple as the terminal and my files to open let alone the software manager or downloading packages.

Thank you!
Kalab

---

### Post by novice_penguin on 2013-08-24
Hi Kalab, I'm new too, just registered tonight actually.  I think, maybe your problem is your software is out of date?  I have 12.04.3 so I'm assuming you need to update.  sudo apt-get update should work for you? Give it a try :D

---

### Post by Werne on 2013-08-24
It may be your graphics card that 's slowing Ubuntu down, for me Ubuntu is near useless on the radeon driver. I have an XFX AMD Radeon HD 7770 which is Souther Island, Cape Verde series, basically, it's not supported by that version of the radeon driver, it supports up to Cayman/Aruba cards. But in my case, it's the combination of Compiz + radeon + graphics card that screws up, when I use GNOME 3 with Metacity/Mutter/Openbox it works fine, fire up Compiz and everything goes to hell.

On a laptop, especially if it's an older one with Intel graphics, you'd be better off with Mint or {L,X}ubuntu, Compiz is a resource hog. If you have AMD/Nvidia graphics, get the proprietary driver and if it's still slow, get something that doesn't have Compiz (or KDE).

---

### Post by Rob Sayer on 2013-08-24
I don't use ubuntu with the unity desktop anymore, but I use kubuntu 12.04 and kubuntu 13.04 on my netbook that doesn't work as well with 12.04 (a hardware support issue).

Mint 15 is based on 13.04, which is faster than 12.04 IME.  But not *that* much faster.

When I first installed ubuntu I used the unity desktop version.  There have been complaints about gnome 3 and unity and compiz (the underlying compositor) since it first came out, and frankly it was the best thing that ever happened for linux mint.  And it *is* slow.  Which is why I don't use it anymore.  But it was not slower than windows 7.

I've had mint 13 installed on my netbook for a while.  I'd never install ubuntu with the unity desktop on a 1Gb netbook, so I didn't try the cinnamon version of mint, since it's also based on gnome 3.  I did try the xfce version.  That was horrendously buggy.  Also the mate desktop, which worked fine but was *really* slow.

The thing about mint is that while it's ubuntu based, the tech support on their forums is *pitiful* compared to what you get here.  So I'm not suggesting reinstalling mint.  You could, in theory, install the cinnamon desktop on a ubuntu system.  But I would definitely not do that either.  Mint is based on 6 month old ubuntu versions.  You're just asking for weird hard to diagnose problems that you'd have a hard time getting support for.

As mentioned, it's hard to say without knowing what kind of hardware you're running.  It's true amd drivers don't work well with ubuntu versions after 12.04.1, but mint 15 is 13.04 based and you didn't seem to have problems.  I yanked the unity desktop version on my 4Gb i3 based laptop because I found the graphics performance was poor.  I definitely would use a different desktop for less than 4Gb.  I tried xfce for a while but have settled on kubuntu (kde).

---

### Post by Jonathan Andrew Upton on 2013-08-24
Hi there,

It could be that the amount of RAM used in the computer is not enough for both of the operating systems to cope with when functioning. It could also be that the amount of spaced used up on the hard drive is near the limit; there are two operating systems running on one computer at the same time, remember. If I were you, I would stick to only having one operating system on the computer in future, or upgrade the RAM or install a bigger hard disk drive into the computer.

Hope it gets sorted out soon.

Jonathan

---

### Post by ibjsb4 on 2013-08-24
Want to get compiz out of the picture.  Add gnome-classic (no effects) to your ubuntu install.  That will use 'metacity' as a window manager.  And how much ram do you have?

---

### Post by Rob Sayer on 2013-08-25
I also tried gnome classic, no effects, and didn't find it fast enough either.  Better than unity but not nearly as fast as xfce or kde tweaked for speed.

That was on a 4Gb i3 based laptop.  I agree we  need to see some hardware specs here.  But I still think if it ran mint 15 (13.04 based) OK it should run unity without that much of a speed difference.

---

### Post by mJayk on 2013-08-25
> **Rob Sayer said:**
>   But I still think if it ran mint 15 (13.04 based) OK it should run unity without that much of a speed difference.


Thats just not true unity can be alot more intensive, and will can run terribly with bad drivers. As opposed to the default mint gui which tends to be fine. Sounds like a hardware / driver issue to me.

---

### Post by d-cosner on 2013-08-25
Sounds like maybe graphics drivers. Installing Preload may also help. I have preload installed on one of my computers and it fixed things up in a fairly short amount of time.

---

### Post by startas on 2013-08-25
Actually, unity is the fastest de in linux, it is at the same level as xfce and other useless des, except that unity isnt from 80's and has vsync and other basic technologies from the 21 century. gnome 3 and kde also has these basic features, but these de are very slow and full of crap. Second, you should even compare so old 12.04 with such a beast as windows 7 ;) even current development versions of 13.10 isnt in par with windows 7/8 in speed. And there is pretty big chance (as always), that something is broken (as usual).

---

### Post by oldrocker99 on 2013-08-25
> **startas said:**
> Actually, unity is the fastest de in linux, it is at the same level as xfce and other useless des, except that unity isnt from 80's and has vsync and other basic technologies from the 21 century. gnome 3 and kde also has these basic features, but these de are very slow and full of crap. Second, you should even compare so old 12.04 with such a beast as windows 7 ;) even current development versions of 13.10 isnt in par with windows 7/8 in speed. And there is pretty big chance (as always), that something is broken (as usual).

Are you trying to start a flame war? Calling ANY Linux slower than Windows is a great way to do it. Another great way is to call any DE than Unity "slow and full of crap."

---

### Post by Werne on 2013-08-25
> **startas said:**
> Actually, unity is the fastest de in linux, it  is at the same level as xfce and other useless des, except that unity  isnt from 80's and has vsync and other basic technologies from the 21  century. gnome 3 and kde also has these basic features, but these de are  very slow and full of crap. Second, you should even compare so old  12.04 with such a beast as windows 7 :wink:  even current development versions of 13.10 isnt in par with windows 7/8  in speed. And there is pretty big chance (as always), that something is  broken (as usual).

Is that so? Fascinating! I'd like to hear more about that.

I'd especially like to hear about what substance have you been using before making this post, cause that seems far more interesting, something that induces those kind of hallucinations probably isn't on the market yet.:D

Now, while you get your facts straight, let me explain what Unity is. Half of Unity is Compiz (visuals, window manager), a resource-heavy 3D desktop compositor that can bog down even a modern system and make it squeal for mercy. Sure it runs fast, on an i5 3570K, 8GB system RAM and Radeon 7770, but on a Core 2 Duo E4500, 2GB system RAM and Radeon 4350 it makes the PC slow. And GNOME 3, the one "full of crap" is the other half of Unity (programs).;)

KDE is also a resource-heavy desktop environment that offers a greater extent of modifications and options than Unity/GNOME. I was never a big fan of it though, but I do like some things about it.

VSync you're mentioning, it is available in Xorg's radeon/noveau/intel drivers and fglrx/Nvidia propriatery drivers. Incompetence to actually activate VSync or RTFM is another thing entirely.:roll:

"Old 12.04" was released in 2012, Windows 7 was released in 2009 and Windows 8 was released 6 months after Ubuntu 12.04, so I fail to see how 12.04 is old. I also fail to see how a year and a half makes it old, if that's the case, then Win7 is a dinosaur and Win8 is old too. So unless Microsoft went back in time to release 7, Ubuntu 12.04 is 3 years ahead of Windows 7.

As for Windows 7/8 speed, Windows is fast, but only on new machines. Faster? Yes, when using default FLOSS drivers on Linux, fglrx performs worse on Linux but Nvidia drivers are on-par with Windows'. Go run Windows without AMD/Nvidia drivers and see how that works out for you, Linux's FLOSS drivers can at least be further tweaked. Not to mention that Windows 7/8, compared to {L,X}ubuntu, Debian LXDE/XFCE or even Mint Cinnamon, is slow as sloth. You do not measure boot time or game performance to decide how an OS performs, you measure reaction time, responsiveness, CPU cycle usage, GPU usage, etc.;)

And the best part of the post was when you compared Windows 7/8, which you praise oh so highly, to an unfinished development version of Ubuntu that is scheduled to be released in two months. You can't judge an OS by going and using a cutting-edge developmental version that is not yet even released. If you want speed and stability, go use Debian Wheezy. If you want "latest and greatest", use Arch or Gentoo.

If you prefer Windows, use it, love it, sleep with it, make out with it, marry it, <snip> it, nobody cares. Just don't cram your ideals down people's throats cause, surprisingly enough, people don't like that.:o



Now if you'll excuse me, I shall retreat and wait for my punishment by the moderation team for not being able to just shut the hell up and move on.):P

Note for mods: Don't be gentle, I can take it.:cool:

---

### Post by jaedin2 on 2013-08-25
Dual booting can cause problems with the speed of ubuntu and any other OS on your computer. Also, I highly recommend the x32 bit versions of linux, they are better optimized to run faster. Of course, you might just need to break it in a little bit.

---

### Post by ibjsb4 on 2013-08-25
> **jaedin2 said:**
> Dual booting can cause problems with the speed of ubuntu and any other OS on your computer. Also, I highly recommend the x32 bit versions of linux, they are better optimized to run faster. Of course, you might just need to break it in a little bit.

Sounds like time to get my boots on, its getting pretty deep around here.

---

### Post by tgalati4 on 2013-08-25
And that ain't mud on your boots partner.

---

### Post by d-cosner on 2013-08-25
Werne, I absolutely love what you wrote! Weather you get in trouble with the mods or not I think you expressed what all of us were thinking**.  **:lolflag: You gave me a good laugh too! Thanks![**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1786950")

---

### Post by cariboo on 2013-08-25
This thread doesn't belong here, moved to the Cafe, as it isn't a support question any more.

**Edit** Closed for 24 hours to let the participants settle down a bit.

---

