---
title: "How are you going to upgrade to Maverick Meerkat?"
date: 2010-10-02
forum: The Cafe
---

### Post by slooksterpsv on 2010-10-02
I'm just wondering how everyone is going to upgrade to Maverick Meerkat?

Reformat and install, Upgrade, Not going to, going to wait then reformat or going to wait then upgrade?

Personally I'm planning on doing an upgrade from Update Manager when it comes out.

---

### Post by lisati on 2010-10-02
Well... my server is currently busying itself with an upgrade from 9.04 to 9.10. Assuming nothing gets horribly broken in the process (I've spotted a couple of warnings that might warrant attention later) I'll probably look at (eventually) updating to 10.04 LTS. No offense intended to the Meerkat team but I might wait a bit before checking it out.

Edit/update, 2 hours later: so far so good; a minor glitch with hald segfaulting and restarting during the update (seemed to cure itself on reboot) and another with pulseaudio (I have a gui installed for times when I'm too lazy to figure something out using SSH, also easily fixed by removing pulseaudio, who needs sound on a server?), everything else seems to check out OK so far.

---

### Post by slooksterpsv on 2010-10-02
> **lisati said:**
> Well... my server is currently busying itself with an upgrade from 9.04 to 9.10. Assuming nothing gets horribly broken in the process (I've spotted a couple of warnings that might warrant attention later) I'll probably look at (eventually) updating to 10.04 LTS. No offense intended to the Meerkat team but I might wait a bit before checking it out.

I can't say as I blame ya, I've had my OS have tons of things not work from doing an upgrade. I don't want to have to burn an ISO, download my x amount of programs I use and have to transfer over 120GB worth of data back to the HDD, as I don't put my home folder on it's own partition.

---

### Post by cariboo on 2010-10-02
Servers are a totally different animal from the desktop. My server is currently running karmic, I will update to Lucid when support runs out on Karmic.

What I usually do is once a final version is released, is do a fresh install of the current version, the do a second fresh install on an other hard drive to prepare for the next version. The current version is used in case the testing version becomes unusable.

There isn't much difference between a current version and a testing version until after [UDS]("https://wiki.ubuntu.com/UDS-N"), so it just sits there until something starts happening.

---

### Post by zer010 on 2010-10-02
Reformatting and installing has been the only way that I've ever done it. I've read too many "horror posts" about any other way of upgrading.
Myself, I will probably make the move to 10.10 a month or so after it's release. Any sooner than that, it seems there are still a lot of bugs. Fortunately, the majority of them get spotted and fixed pretty quickly. As far as I'm concerned, Ubuntu has been spectacular about quickly resolving issues.

---

### Post by 3rdalbum on 2010-10-02
> **slooksterpsv said:**
> I can't say as I blame ya, I've had my OS have tons of things not work from doing an upgrade. I don't want to have to burn an ISO, download my x amount of programs I use and have to transfer over 120GB worth of data back to the HDD, as I don't put my home folder on it's own partition.

Well, if you use the Manual partitioning in the Ubuntu installer and don't tell it to format / (just install Ubuntu over-the-top) your /home will be preserved even though it's on the same partition.

---

### Post by Ewingo401 on 2010-10-02
I usually do a clean install with each LTS release and upgrade to each subsequent release until the next LTS.  If you're not using any PPA's or any other repos aside from the defaults, then you should have no trouble with upgrading.

---

### Post by Bachstelze on 2010-10-02
None of the above, I did a good ol'

```
echo "s/lucid/maverick/g\nw" | sudo ed /etc/apt/sources.list && sudo apt-get update && sudo apt-get dist-upgrade
```

Kids, don't do this at home.

---

### Post by Dustin2128 on 2010-10-02
I usually only grab LTS releases for machine's I've already converted, I'm too lazy to do it every 6 months. I might have gotten 11.04 if they had gone with the suggestion to name it neurotic newt... so much potential...

---

### Post by Legendary_Bibo on 2010-10-02
I'm not upgrading. Lucid works perfectly, and I have things set up how I like them, why would I risk screwing that up?

---

### Post by xjesse on 2010-10-02
From the reviews I've read and the videos I've watched I see absolutely no need to upgrade. The Ubuntu Software Center looks a disaster! I am not a fan of having to open it simply to install a .deb file. 

I've used Ubuntu since the 6.06 days but I may be considering jumping ship from the looks of this release as well as the next.

GNOME 3? G[NO]ME thanks.

---

### Post by oldos2er on 2010-10-02
You left out the option "I'm already running 10.10".

---

### Post by cap10Ibraim on 2010-10-02
my first distro was 9.10 
from 9.10 to 10.04 I did a clean install , so now i'll try the update manager and deal with the issues

---

### Post by witeshark17 on 2010-10-02
I will upgrade at some point, but 10.04 is sweet enough that I'm in no hurry. :popcorn:

---

### Post by Dustin2128 on 2010-10-02
> **Legendary_Bibo said:**
> I'm not upgrading. Lucid works perfectly, and I have things set up how I like them, why would I risk screwing that up?
I had the same thing with hardy on my desktop, the reason why I was eventually forced to upgrade is that some of the later karmic and lucid packages just weren't working (repositories didn't contain dependencies or contained outdated versions). I probably could've updated the repositories, but it was all just much more difficult than updating. In retrospect I really didn't need to, my desktop now runs more slowly than in the hardy days and I used a wired network anyway. I'm probably swapping to (p-something) penguin on the laptop though (12.04, next LTS release), if the requirements don't quadruple (again).

---

### Post by Khakilang on 2010-10-03
I upgrade from 9.10 to 10.04 and everything works well except for some minor bugs and later do a clean install. I think it is best to do a clean install. I may download 10.10 and test it on other computer.

---

### Post by andymorton on 2010-10-03
I've never had any problems upgrading through update manager so I've done it that way again. Everything is solid. 

andy

---

### Post by Elfy on 2010-10-03
I did a clean install - but without a format to see if it did in fact keep the /home and it did.

---

### Post by NCLI on 2010-10-03
I've already upgraded two PCs using Update Manager, so I'm probably going to do the same for the rest as well.

---

### Post by pwnst*r on 2010-10-03
I do clean installs, but this is why it's confusing for new users.  They should just be able to upgrade, not pointed in the direction of a reformat.

---

### Post by lxlv01 on 2010-10-03
I am not upgrading because I have fresh installs of Lucid, but if i do I have a strong prejudice for clean install. however, to be fair, I have upgraded a small installation on a computer my parents use, since 9.04 to 9.10 then to 10.04 in June with no issues at all. It may be just luck but after this I trust update manager much more.

---

### Post by Frogs Hair on 2010-10-03
I had a bad upgrade experience , but it was likely my fault for not removing ppa's an third party software . I'm still a little gun-shy , but may try an upgrade on 11.04. Installing an operating system that is ready for the general public should not be a nightmare nor should it take weeks or months to get it working properly.

---

### Post by PaulW2U on 2010-10-03
I've no need to upgrade as I'm already running the pre-release and have been doing so since alpha 2. But if I was going to replace a previous version with Maverick I would definitely re-install taking care to preserve most of my /home partition.

---

### Post by FuturePilot on 2010-10-03
Upgrade. Never had a problem with upgrading. Done it on many computers for years.

---

### Post by wolf_3d on 2010-10-03
Not upgrading at this time. I like what they've done to it, though. I might look at 11.04 but I'm more likely to see what the next LTS brings.

---

### Post by MrNatewood on 2010-10-03
I will reformat in order to rid of all the junk I accumilated

---

### Post by madhi19 on 2010-10-03
I was still using Jaunty until last Friday but I was ready to move on. I had a Lucid partition that I never really used so that where I put Maverick in. I spent most of Saturday setting things up picking a new theme and rebuilding Firefox the way I like it that sort of things. DesktopNova is a pretty good replacement for Wallpaper-tray by the way! No trouble at least nothing I could not handle myself. So far so good I will keep my old jaunty for a while until am sure the crap will not hit the fan. 
This is how my new desktop look right now.
[IMG]http://ubuntuforums.org/picture.php?albumid=1351&pictureid=6794[/IMG]

---

### Post by Nightstrike2009 on 2010-10-03
I always do a clean install from a freshly burned iso disc image burned to cd.  

I am far to impatient to wait for final versions sometimes and it helps to clean install new versions to clear all the "experimental" apps ive tried out LOL.

Then I use terminal to reinstall all my favourite apps via the internet.

---

### Post by slooksterpsv on 2010-10-03
> **Frogs Hair said:**
> I had a bad upgrade experience , but it **was likely my fault for not removing ppa's an third party software .** I'm still a little gun-shy , but may try an upgrade on 11.04. Installing an operating system that is ready for the general public should not be a nightmare nor should it take weeks or months to get it working properly.

Wait what? I didn't remove my PPA's or 3rd party software, I think it disabled them for me. I have Maverick 10.10 RC running great (even with ati drivers - hehe that was tricky). So yeah... checking sources.list now... hmmm ppa's are still there.

---

### Post by JDShu on 2010-10-03
Upgrading works perfectly for me, but I'm happy with Lucid right now. Probably won't upgrade until at least the next LTS - 1

---

### Post by wojox on 2010-10-03
Reformat, that's the only way to do it. Wouldn't say it's the only way, but it's what I prefer.

---

### Post by Cavsfan on 2010-10-05
I upgraded yesterday and it went perfectly! And I didn't loose anything! I was going to stick with the LTS, but just 
could not help myself. I was not about the do a clean install so I would have stuck with Lucid until I seen someone
mention that they did an upgrade and it went smoothly. I didn't loose any thing! Not even a cookie on Firefox! 
:guitar:

---

### Post by paulde1983 on 2010-10-05
I wont be upgrading to 10.10 just yet I have only just switched from an aging install of Windows XP to lucid I tried the update manager to have a go at the release candidate and broke my install :(. 
I had to do a complete reformat and install lucid again, think it was Nvidia 173 drivers did not work as no desktop effects.

---

### Post by slooksterpsv on 2010-10-05
> **paulde1983 said:**
> I wont be upgrading to 10.10 just yet I have only just switched from an aging install of Windows XP to lucid I tried the update manager to have a go at the release candidate and broke my install :(. 
I had to do a complete reformat and install lucid again, think it was Nvidia 173 drivers did not work as no desktop effects.

I'm sorry to hear that, yeah the graphics are a pain to get working in RC right now. I lucky had made a backup of my Xorg file and now have graphics acceleration with the 10.9 driver in Ubuntu 10.10 64-bit RC. Lucid is still amazing.

---

### Post by Cavsfan on 2010-10-05
> **paulde1983 said:**
> I wont be upgrading to 10.10 just yet I have only just switched from an aging install of Windows XP to lucid I tried the update manager to have a go at the release candidate and broke my install :(. 
I had to do a complete reformat and install lucid again, think it was Nvidia 173 drivers did not work as no desktop effects.

That's ironic, I have installed NVIDIA Driver Version: 260.19.06 and the upgrade went well from Lucid to Maverick! 
I have an nVidia Geforce 9800 GT. I didn't loose anything.

---

