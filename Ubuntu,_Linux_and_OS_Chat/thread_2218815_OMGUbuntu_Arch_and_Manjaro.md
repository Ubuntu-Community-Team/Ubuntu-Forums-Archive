---
title: "OMGUbuntu Arch and Manjaro"
date: 2014-04-22
forum: Ubuntu, Linux and OS Chat
---

### Post by slooksterpsv on 2014-04-22
OMGUbuntu posted an article on Arch Linux. While I've heard quite a bit about it, and had a few people tell me to switch to it, I didn't feel like completely customizing everything, compiling everything, etc. I think Arch does AURs where it does everything automatically for you... I'll look that up.

Anyways, back to my story, well I read the article and felt like taking a new challenge into the Arch area. I've used Slackware and that was a paint to have to compile everything pretty much. Great for customizing, but if you need a system ready to go, Ubuntu outshines it. Well Arch looked pretty slick. Rolling release, downloading AURs to get non-official items installed (Google Chrome *cough cough*), up-to-date repositories. It sounds great!

Well... I didn't want to do CLI as I wanted to browse in case I had questions or needed help, so I looked into Manjaro which I've been hearing more and more about lately. Pretty much a pre-packaged Arch install with GUI installer (granted I had to use the CLI to install for EFI, go figure right?, but the GUI was in a terminal so its all good), codecs, everything I could want.

First boot. Bam! I'm like whoa when did my computer get so speedy quick.
Well in Ubuntu 14.04 I have an issue where I have very slow network speeds with my WiFi, like I can boot, try to load up a site and it act like we're in the dial-up ages. I tried a few things to fix that, nothing really worked, tried compiling the driver and loading it, that didn't help. I decided well if WiFi is still bad in Arch I'll look into getting a more compatible dongle (not what I want to do, but still). Arch loads up, I connect to WiFi, and the speed, it's not as fast as Windows (interference), but it's a lot stronger than Ubuntu. The kernel for manjaro is 3.10.30-1 (I think 3.14 is out and Ubuntu is on 3.13). It could be a kernel issue for the WiFi as 13.10 was great.

The installation experience. I got a little paranoid:
1. GUI wouldn't let me continue unless I chose an EFI drive nor would it let me select where to install the Bootloader, so I canceled the GUI.
2. CLI was a little spooky when it was accessing my EFI partition, so I, before doing this, did a dd of my /dev/sda2 and a cp -Rn of the EFI drive.
3. It went through, and Manjaro wasn't in the list for my EFI. Great, just great!
I luckily had Ubuntu 14.04 on another partition so I booted up and created the entry, moved it to the top and updated grub, it didn't save so I booted into grub, created the entry and used my app to modify the entries. Well this sparked another idea for my EFI Boot Order - label modification (now I know how to do it).

Let's continue onto what I've noticed about Arch/Manjaro:

After install I have over 500MB of updates - its a rolling-release, I was expecting 900, but hey I'll take 500 =P
Codecs right out the package (like Mint)
Graphics drivers right from live cd - I had a vesa issue booting normal, used non-free and it loaded my AMD driver
XFCE is using Whisker menu, it's all clean and organized
HiDPI must be enabled. I was using Ubuntu-Gnome and it felt like I was using a 1366x768 screen on my 1600x900 display. Manjaro booted and I have a lot more real-estate for my screen. I feel like I can more prominently multi-task

Downfalls:

I'm only on my first 2 hours of Manjaro so yes it's exciting, new, fun, and making me giddy like a school girl, but in all seriousness, I need more of a challenge to test my Linux skills. Modifying my brightness via terminal, perfect. Didnt know how to, now I do.

Any one else with experience with Arch or Manjaro? Questions such as UEFI or that?

Let me know =D

---

### Post by sffvba[e0rt on 2014-04-22
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by Jordan_Cameron on 2014-04-22
I have actually switched from my own Arch install to ubuntu 14.04.  I loved the AUR, and the rolling release, but for my production machine that I use for University Studies needed to be more solid, and able to get up and running quickly.

I sum it up like this: If new code is your "crack", then Arch is for you.  But if stability, rock solid and out of the box setup is your "crack", then *buntu and Mint are for you.

---

### Post by mips on 2014-04-22
I just want to mention one thing, Manjaro is not Arch. 

Yes it's based on Arch but they have their own repos and a few unique utils like MHWD for example. 
Don't go asking for support in the Arch forums with things related to Manjaro, sure read the Arch wiki & forums as there is a lot of info there as well if you need anything in addition to the Manjaro forums & wiki.

That out of the way carry on and have fun ;)

---

### Post by slooksterpsv on 2014-04-22
As far as I can tell I still get all the rolling-release updates like Arch does though right?

Yeah it's smooth. Audio issue, had multiple times, fixed. I'll have to give Ubuntu another go around don't get me wrong. I may have to try a pure Arch install and see how that goes.

---

### Post by mips on 2014-04-22
> **slooksterpsv said:**
> As far as I can tell I still get all the rolling-release updates like Arch does though right?


Yes but they are delayed and sometimes some packages are held back for stability reasons. 

It goes like this Arch Stable Repos-->Manjaro Unstable-->Manjaro Testing-->Manjaro Stable

---

### Post by lykwydchykyn on 2014-04-22
I switched to Arch on my laptop when I got it a few months back.  It's an ordeal to get things going initially, but once it's setup you're set, and it's not like you're going to be reinstalling every six months (*cough*).  I've had good experiences and plenty of fun so far, but honestly I wouldn't want to manage Arch on a system that I wasn't using daily.  My servers are staying with Debian and my family machines are sticking with *buntu.

Haven't yet had to deal with a machine with UEFI, though.  My laptop was a Dell that shipped with Ubuntu so they had it in BIOS mode.

---

### Post by monkeybrain20122 on 2014-04-22
I have a partition running Manjaro, it was very fast starting up and with all the codecs already installed (even flash with hardware acceleration enabled, resulting in crashing everywhere. :)) But a few weeks later package managing system was broken after an update..  It is easy to set up, fast and easy to use but feels a bit unfinished and volatile,--arch probably will be more so,-- I won't use it for a production system, not for now. I was in the process of setting up Arch but get interrupted with other things, will get back to it in a few weeks.

---

### Post by monkeybrain20122 on 2014-04-22
> **lykwydchykyn said:**
> I switched to Arch on my laptop when I got it a few months back.  It's an ordeal to get things going initially, but once it's setup you're set, and it's not like you're going to be reinstalling every six months (*cough*)..

Well you don't have to re install every 6 months, support period is 9. It is 5 yrs if you use LTS. But Ubuntu is so easy to install and setup that you can do it many times during the time you set up arch once. :)

---

### Post by lykwydchykyn on 2014-04-22
> **monkeybrain20122 said:**
> Well you don't have to re install every 6 months, support period is 9. It is 5 yrs if you use LTS. But Ubuntu is so easy to install and setup that you can do it many times during the time you set up arch once. :)

Just an innocent tongue-in-cheek jab, since the "accepted wisdom" at this forum is that only a complete reinstall will do (I've always just upgraded myself).  Ubuntu is quick to install *if you stick close to the default setup*.  Part of the reason that I switched to Arch was that my preferred setup involved installing a bunch of packages from Universe, a bunch of PPAs, some things backported with apt-src, and about half a dozen things that I had to install from upstream source using checkinstall or dpkg-buildpackage ('cause sometimes one worked but not the other).  

At that point Arch makes more sense, but only at that point.

---

### Post by monkeybrain20122 on 2014-04-22
> **lykwydchykyn said:**
> Just an innocent tongue-in-cheek jab, since the "accepted wisdom" at this forum is that only a complete reinstall will do (I've always just upgraded myself).  Ubuntu is quick to install *if you stick close to the default setup*.  Part of the reason that I switched to Arch was that my preferred setup involved installing a bunch of packages from Universe, a bunch of PPAs, some things backported with apt-src, and about half a dozen things that I had to install from upstream source using checkinstall or dpkg-buildpackage ('cause sometimes one worked but not the other).  

At that point Arch makes more sense, but only at that point.

You need to stick to default set up only if you 'upgrade'. I never 'upgrade' so I meant a clean install. 

My setup is very far from default. clean install is fast if you have a separate /home. Fast to get the thing up and running and reinstalling applications from ppas. So with less than an hour I can get things back to where it was, more or less, with the exceptions of applications that I compiled, system settings tweaks etc. Those will take longer to recover (which 'upgrade' would destroy anyway if it works at all,--by 'works' I mean not completely breaking the system)

But now I do something else. 

I never get new OS on release day, always wait about 3 months for bug fixes. I install the new OS in an external drive, check in may be twice a week to run updates and do some tweaking, compiling, adding ppas, editing config files etc, Since it is not mission critical I can experiment a bit, no pressure, no rush. In 3 months I would have a perfectly tweaked and customized system ready to go. When I have to upgrade I just wipe my internal drive, clone the external and restore it over, no nasty surprises, no new tweaking required, everything is good to go as is. There is no gap between transition. :)

I can appreciate the Arch way, but the setting up is so painful that it had better be rolling,  I doubt that anyone would want to do that every 6 months. :)

---

### Post by slooksterpsv on 2014-04-23
Arch isn't bad. I didn't mind the setup, I learned quite a bit more about the CLI for installing Linux and seeing how much really pours into getting everything ready to go. The thing I liked about Manjaro vs Arch is it already looking nice, GUI for AURs, and ease of installation. Now on Manjaro I have an issue with one package not downloading to install to be able to update the system where Arch is was servers weren't connecting too well. Either way I'm back on Manjaro and will try arch another day. I can see why people use either of them - fast, clean, simple not overloaded with "bloatware"

---

### Post by malspa on 2014-04-23
I installed Bridge Linux and ArchBang here last year. I chose them over Manjaro because both use the Arch repos -- they're still considered "not Arch," and you won't get help with them at the Arch forums, but they're closer to Arch than Manjaro is. After a few months, I liked Bridge and ArchBang so much that I went ahead and installed Arch. I still have all three installations going great here.

Yes, Arch takes some work to install and set up, but if you're okay with that and you're willing to do some reading and can follow instructions, it's well worth it. The Arch wiki is awesome, and pacman, the package manager, is great to use. You end up with a system that includes only packages that you want, not a bunch of other stuff.

The article mentioned in this thread's first post is a good read: [http://www.omgubuntu.co.uk/2014/04/arch-shangri-la-ubuntu-power-users?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2014/04/arch-shangri-la-ubuntu-power-users?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by mips on 2014-04-23
> **slooksterpsv said:**
> Now on Manjaro I have an issue with one package not downloading to install to be able to update the system...

Could you provide details wrt the error ie output of pacman or yaourt from cli please and I'll try and help.

---

### Post by slooksterpsv on 2014-04-23
It keeps doing the operation taking too long. I implemented my own fix for it:

Go to /var/cache/pacman/pkg and find a server with the package you need e.g.:
sudo wget -c [http://the.mirror.site/arch/extra/os/x86_64/some-file-package-1-2-3-4.tar.xz](http://the.mirror.site/arch/extra/os/x86_64/some-file-package-1-2-3-4.tar.xz)

Then run: sudo pacman -Su or sudo pacman -S <packagename>

And it will install.

---

### Post by mips on 2014-04-23
[https://wiki.manjaro.org/index.php/Rankmirrors_to_Set_the_Fastest_Download_Server](https://wiki.manjaro.org/index.php/Rankmirrors_to_Set_the_Fastest_Download_Server)
[https://wiki.manjaro.org/index.php/Change_to_a_Different_Download_Server](https://wiki.manjaro.org/index.php/Change_to_a_Different_Download_Server)

---

### Post by slooksterpsv on 2014-04-23
I think its my network connection, it happens all the time. I've tried those steps and even used the reflector app to try and fix it as well.

---

### Post by buzzingrobot on 2014-04-23
I've used Arch a bit, but I quickly realized the DIY nature of the thing didn't payoff in any way I found meaningful. In the end, it's a good, efficient distribution with access to a lot of software.  But, it's certainly not the only one. You will get new code soon after release, although if you don't make the effort to regularly check the site and/or subscribe to mailing lists, you are liable to update your way into troible

Someone who finds that downside acceptable in return for early access to new stuff should also look at Fedora Rawhide, too.

If someone  just wants the newer software and has no interest in fussing with Arch's care and feeding, Manjaro is a very good alternative.

---

### Post by slooksterpsv on 2014-04-23
I've had a few things I've had to work out, and it'll help when working with others here on the forums. Like I had to create a modprobe for my alsa configuration for pulseaudio to even playback audio - and use amixer to toggle mute (why it goes on mute, no clue).

Wireless networking via terminal. - This has always been a pain, but this wifi-menu app is awesome! I wonder if I can install it in Ubuntu. Hmm... I'm back to testing out conky scripts. There's just a variety of fun things where I have a more finite control of what newer software I want/need besides PPAs.

Yeah there's quite a bit, I'm learning.

---

### Post by PondPuppy on 2014-04-24
Yes to "Manjaro is not Arch" -- it's a based-on-Arch distro. On the Slackware side, Salix is a similarly user-friendly based-on distro. I use both now and then, and they're both stable and pretty snappy on old hardware.

---

