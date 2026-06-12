---
title: "Gutsy Just Like Vista ... One Step Backwards"
date: 2007-12-18
forum: Testimonials &amp; Experiences
---

### Post by Geekkit on 2007-12-18
Here's why:

NVidia driver in Feisty worked fine ... Gutsy requires CTRL-ALT-Backspace for the new video resolution and refresh rate to take affect
Flash plugin not recognized in Gutsy - in Feisty it does (bug already filed by someone else)
In Gutsy when I go full resolution in Totem, refresh rate drops down to 55 Hz instead of the 85 Hz I had it set to - Feisty doesn't have this problem
Attempts to install restricted formats doesn't work (bug already filed by someone else)
Rythmbox icon (and other various icons) in Gutsy are a 1/5 of the size of normal desktop icons. Attempts at resizing them doesn't work unless you drag the other way (wtf?). Of course Feisty doesn't have this problem (bug already filed by someone else)
Setting up SAMBA/file sharing doesn't seem to work between the GUI and the command line in Gutsy - in Feisty, it's all command line and so it works just fine

I'm either going back to Feisty or check out Fedora ... this is ridiculous. :(

---

### Post by jayson.rowe on 2007-12-18
I haven't had any of the problems you have described personally, but one word of advice...if multimedia codecs and proprietary nvidia drivers are something you desire, know that if you try Fedora you can not get proprietary formats without stepping outside of the distro - they package nothing that's non-free or proprietary...you'd have to add a secondary repo such as Livna, RPM Forge or ATRPMS.

---

### Post by rsambuca on 2007-12-18
I haven't had any of those problems that you seem to have had.  Was this a fresh install or an upgrade?  If the latter, I would just wipe and do a fresh install.  If the former, then check your CD for defects, or just go back to Feisty.

---

### Post by MNICY on 2007-12-18
My gutsy install works much better then my fiesty install did.
Did you upgrade or do a clean install?
My attempted upgrade got messed up somehow, so i just did a clean install.

Works great.

Anyway, no shame AT ALL in going back to Feisty.

---

### Post by timcredible on 2007-12-18
sounds like you did an upgrade instead of fresh install.  you don't get those problems with a fresh install

---

### Post by lamalex on 2007-12-18
Well at least we're keeping up with MS!

---

### Post by Geekkit on 2007-12-18
Thanks for the replies. Actually this is a fresh install, that's why I'm puzzled. For me the upgrade was the one that didn't have problems.

I'm going to limp back to 7.04 later today. Some of the configuration was command line but that's never scared me off - I know that command line always works, or, if it doesn't, the feedback is there to file a bug report.

EDIT:

Additionally, here are the bug reports:
[https://bugs.launchpad.net/totem/+bug/139468](https://bugs.launchpad.net/totem/+bug/139468) <-- [gutsy] Totem fullscreen changes monitor refresh rate
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/122937](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/122937) <-- Rhythmbox desktop launcher icon appears too small
[https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/139027](https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/139027) <-- Screens & Graphics not setting correct resolution
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508) <-- Window titlebar displayed not right with compiz enabled
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/124288](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/124288) <-- [gutsy] totem-gstreamer can't handle mpeg muxed videos properly

EDIT 2:
Also, putting certain icons on a panel, after reboot, have disappeared..

---

### Post by SaiGoN DraGoN on 2007-12-18
:confused: Well; i did an upgrade of Feisty to Gutsy; there were things that did not work on Fesity like external hd support; but what really upset me it's that few days after my upgrade compiz fusion started to act weird. i uninstall it and re install it with no result and then i found out that the Nvidia driver is not working properly and there is nothing i can do about it until someone compiles a new driver or something like that. I see myself going back to Windows once in a while and it really bothers me because i though i was completely going to migrate to Linux. Well i guess i have to wait; right now i am checking some live CDs of Sabayon with the Nvidia driver working so, i guess i'll be back when Ubuntu fixes this little problem.

---

### Post by Geekkit on 2007-12-19
FYI:

I sort of have a fix for the screen resolution/refresh rate issues in Gutsy:

[LIST]
[*]Install restricted NVidia driver and use nvidia-settings applet to set screen resolution (do NOT use the System -> Preferences -> Screen Resolution. Screen Resolution simply doesn't work
[*]Remove Totem-gstreamer and replace with Totem-xine
[/LIST]

Doing this takes care of resolution issues (I'm not sure if it's both or just one or the other) but unfortunately doesn't take care of the Flash problem, icons on desktop panel, 1/5 icon sizes.

New problems now to deal with which are less important (so be aware of this):
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149615](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149615) <-- screen starts flickering in EOG when fullscreen
[https://launchpad.net/ubuntu/+source/totem/+bug/53539](https://launchpad.net/ubuntu/+source/totem/+bug/53539) <-- xine crashes when seeking fast in AVI video with windows-1250 encoding subtitles
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/138001](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/138001) <-- [gutsy] slider doesnt work properly (the slider isnt released when the mouse click is released)
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/118675](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/118675) <-- font anti-alias setup hightlights all options when closing the "details" window

Basically don't try to move the slider in Totem when viewing videos and turn off compiz when looking at image via eye of gnome if you want eye of gnome to go full screen, and check on a radio button for the font anti-alias setup highlights after it erroneously selects all four radio buttons. For me, these are less of an issue than 50 Hz refresh rate which was totally killing my eyes and so I'll stick with Gutsy.

---

### Post by wolfen69 on 2007-12-19
have you tried linux mint? the latest is based on gutsy and works a treat.

---

### Post by Geekkit on 2007-12-19
> **wolfen69 said:**
> have you tried linux mint? the latest is based on gutsy and works a treat.

Thanks wolfen69 ... I seem to have 7.10 working ... as good as it will be. The bugs that I've posted references to can be worked around. If they are in Gutsy, they'll be in Mint. One thing I'm curious about is why they continue to bundle Totem with gstreamer. I've had nothing but problems with gstreamer and always wipe it away with Totem and xine which seems to work a lot better with videos and DVDs.

Also, if you have to use the legacy Nvidia driver due to having an old vid card, there seems to be a lot of problems with the driver. I can't really blame Nvidia for it - it is old hardware. Maybe that's my gift for the new year: a new video card.

---

### Post by starcannon on 2007-12-19
First, Gutsy is nothing like Vista

Next, I'm not sure whats going on with your system, my Gutsy install was flawless, even better than Feisty (and Feisty rocked).
I install my Nvidia Drivers the same way on any fresh install with no trouble at all, and it works as expected.
I download latest stable from nvidia.com
```
cd /home/me/Downloads
sudo chmod a+x ./NVIDIA*.run
sudo /etc/init.d/gdm stop
sudo apt-get build essential
sudo ./NVIDIA*.run
cp /etc/X11/xorg.conf /home/me/Backups
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
sudo /etc/init.d/gdm start

```
At the desktop I open a terminal and ```
sudo nvidia-settings 
```
make my changes, save and exit, and everything is great.

Sorry your having troubles with it, but I have experienced Gutsy as a step forward, and it never ever came to my mind to compare it with Vista.
GL

---

### Post by wolfen69 on 2007-12-20
> **Geekkit said:**
> If they are in Gutsy, they'll be in Mint. 

not completely true. although it would stand to reason that the same problems should arise, ive seen a few posts where a simple switch to mint fixed their problem. dont ask me why, i just know that it could make a difference. it couldnt hurt to at least try the live cd.

---

### Post by kelvin spratt on 2007-12-20
Yes Mint seems to fix a lot of problems, Also try envy to install graphics drivers I had lots of problems with my ATI card, Used envy to install now OK, Totem is very poor better to get Mplayer, setup properly takes time but worth it, Kmplayer also works well just change to Mplayer plugin use basic Mplayer and extra skins, The blue skin seems to have a bug get skins from there site.

---

### Post by Z_o-s-o on 2007-12-20
No problems here on Gutsy either.

I like it better than fiesty for alot of reasons.

---

### Post by frokki on 2007-12-20
Sorry for borrowing your thread, but I'd like to have a little rant too...
Not like anyone would care, or if someone did, he'd probably just tell me to install Windows then...

I've been really disappointed in how things have gone lately with my PC. I moved from Windows to Ubuntu Linux about 9 months ago, and from Gnome to Kubuntu some 4 months ago. I really love Linux in general and certainly will never go back to Windows, but this is really starting to piss me off...

- Firstly the Video driver issues, like freezes/lockups and [pink screen](http://ubuntuforums.org/showthread.php?t=572057&page=5).
- Secondly a problem with [ mplayer and streaming media ](http://ubuntuforums.org/showthread.php?t=314954) just appeared out of nowhere.
- Thirdly these damn [flash problems](http://ubuntuforums.org/showthread.php?t=634551)
- Firefox crashes way more often than in previous releases (partly relating to the previous line)
- My TV-card is [f***ing with me.](http://ubuntuforums.org/showthread.php?p=3984779) Even though that's hardware related, I can point my finger at someone because it works just fine in Windows.
- Relating to this TV-thing, not being able to assign ["global shortcuts"](http://ubuntuforums.org/showthread.php?t=273281) makes my whole TV installation guite pointless.
- WLAN functionality is not that great, I had to install a third party tool to get it work like I wanted (and that tool itself doesn't work well at least on my GF's laptop, so it's a fail anyway)
- I haven't even tried compiz, because I know it would cause more problems, and I definitely hate video related ones.

This is not a typical "it's too hard and different for me" -rant.  I am quite a new user, but I have at least a little bit will power to try to find solutions myself and therefore learn something. I just wanted to say aloud that at this very moment I'm not happy with Ubuntu at all (of course happier than ever with Windows), and would like to know why it is so!

 If I had a problem with my computer half years ago, I had most likely broken something myself. However, if I have a problem with Gutsy, my noobishness doesn't have much to do with it.

Is Gutsy just a failed version?
Is Kubuntu just a failed attempt?
Am I a failed loser?
Is this just bad luck, lots of bugs appeared at the same time?
Are things going to be better in Hardy?
Would things be better in Ubuntu than Kubuntu?

---

### Post by Geekkit on 2007-12-20
> **Z_o-s-o said:**
> No problems here on Gutsy either.

I like it better than fiesty for alot of reasons.

Yes, I like it too but the bugs that I've listed (which are either new bugs introduced or ones just uncovered by Gutsy) are annoyances and IMHO set the distro back a peg due to the flaky nature of their affects. They make the desktop experience less of what Feisty offered.

On a side note, I really think that when the restricted drivers are installed, the default install should include a link to the nvidia-settings applet in the main menu and disable the default screen settings applet since it doesn't have any affect.

---

### Post by lvleph on 2007-12-20
> **timcredible said:**
> sounds like you did an upgrade instead of fresh install.  you don't get those problems with a fresh install

Then why do I have some of those problems?
Flashplugin problem, specifically. Obviously, I wasn't about to delete all my things in my Home Directory.

---

### Post by rsambuca on 2007-12-20
> **lvleph said:**
> Then why do I have some of those problems?
Flashplugin problem, specifically. Obviously, I wasn't about to delete all my things in my Home Directory.

The flash plugin problem started when adobe changed the version of flash.  Then the hashes didn't match when the file was downloaded, and things just wouldn't install.  From what I have heard, it has been fixed now.

---

### Post by Z_o-s-o on 2007-12-20
Frokki,

You've got a valid point about the firefox crashes / flash problems.

Anytime theres any flash video on a page, theres a 50/50 chance its going to turn gray and feeze at any moment.  Theres been a lot of solutions that I've tried, and nothing fixes it.

Did you upgrade from Feisty to Gutsy, or was it a fresh Gutsty install from the start?

---

### Post by Geekkit on 2007-12-20
> **rsambuca said:**
> The flash plugin problem started when adobe changed the version of flash.  Then the hashes didn't match when the file was downloaded, and things just wouldn't install.  From what I have heard, it has been fixed now.

And for me this was a minor one since a quick search on Google meant finding the newest version packaged into a Deb file. I guess I should have waited a couple more months for the dust to settle.

 Problem was I couldn't wait because I really wanted to make use of the new features in Open Office (e.g., the new redo feature), new features in GIMP (e.g., the heal tool and perspective clone), new features in Scribus (e.g., crazy PDF exporting control), and greater stability in KDEnLive (bug fixes) and all these were only in Gutsy due to library dependencies.

---

### Post by rsambuca on 2007-12-20
> **Geekkit said:**
> And for me this was a minor one since a quick search on Google meant finding the newest version packaged into a Deb file. I guess I should have waited a couple more months for the dust to settle.

 Problem was I couldn't wait because I really wanted to make use of the new features in Open Office (e.g., the new redo feature), new features in GIMP (e.g., the heal tool and perspective clone), new features in Scribus (e.g., crazy PDF exporting control), and greater stability in KDEnLive (bug fixes) and all these were only in Gutsy due to library dependencies.

If you are the type of person that really enjoys having the newest versions of programs as soon as they come out, then you will probably be a lot happier with 'Rolling Release Distro'.  These distros release packages as they come out, and as a result, you get them without having to wait the maximum of six months in Ubuntu.  The downside is that there is the occasional breakage that you have to deal with.

Some of the popular Rolling Release distros are Arch, Foresight, Gentoo, Debian Sid.

---

### Post by Geekkit on 2007-12-20
> **rsambuca said:**
> If you are the type of person that really enjoys having the newest versions of programs as soon as they come out, then you will probably be a lot happier with 'Rolling Release Distro'.  These distros release packages as they come out, and as a result, you get them without having to wait the maximum of six months in Ubuntu.  The downside is that there is the occasional breakage that you have to deal with.

Some of the popular Rolling Release distros are Arch, Foresight, Gentoo, Debian Sid.

I am and thanks for that.  :)

---

### Post by frokki on 2007-12-20
> **Z_o-s-o said:**
> Frokki,

You've got a valid point about the firefox crashes / flash problems.

Anytime theres any flash video on a page, theres a 50/50 chance its going to turn gray and feeze at any moment.  Theres been a lot of solutions that I've tried, and nothing fixes it.

Did you upgrade from Feisty to Gutsy, or was it a fresh Gutsty install from the start?My problem isn't that bad, I'd estimate the crash percentage to be around 5%. The flash problems are on my GF's clean install Kubuntu Gutsy. And yes, I also have a clean install.

---

### Post by agurk on 2007-12-20
frokki, Z_o-s-o: are you guys running version 9.0.48 version of the Adobe Flash Player plugin (type *about:plugins* in the Firefox address bar to find out) from the repo? If so, I recommend you to manually install the latest 9.0.115 version instead - the hanging problem has been significantly reduced om my machine since I upgraded.
Grab the tarball [here](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux), extract it and put the libflashplayer.so file in /usr/lib/firefox/plugins/
Hope it helps.

---

### Post by gigaferz on 2007-12-20
about flash, i did it manually too, it does help!!!

get it from the adobe site and follow instructions...

And NEVER upgrade just like that, think twice before even thinking about it, or at least try it virtual  first. unless youre kinda expeienced.

mupen64 doesnt run like it used to in feisty.... and there arent that much deb packages yet in getdeb (wich is my favorite site)

Have you ever wondered howcome most of us lasted with windows98,  2000 or xp?, probably like 2 , 5 or 6  years, wihout even thinking about upgrading or anything related. Now we just cant wait for a new release huh,,

---

### Post by Z_o-s-o on 2007-12-20
Agurk,

I'm running Flash 9.0 r115, so no dice on that being a solution.

Edit - Yes I went to Adobe's site and got the player from there and installed it that way.

---

### Post by rsambuca on 2007-12-20
> **Z_o-s-o said:**
> Agurk,

I'm running Flash 9.0 r115, so no dice on that being a solution.

Edit - Yes I went to Adobe's site and got the player from there and installed it that way.

I don't think I have had any crashes with FF and Flash sites.  Perhaps it is something else.  What is your videocard?  What driver are you using?  Are you running compiz?

---

### Post by Geekkit on 2007-12-20
Cool. Open Office envelope settings don't reset when you press the reset button. :(   .... must resist urge to use Wife's computer with working office program ...

---

### Post by kelvin spratt on 2007-12-20
Can someone please explain what you all have in common for all these problems.When I upgraded to gutsy for the first time in Ubuntu I had Graphics problems But then it was the same in other Distros as well, so I enabled restricted drivers but that was no good as the screen was to far to the left, Also glxears was very choppy so I went back to Feisty drivers that fixed that. Now ATI have released updated drivers so using Envy I installed them, Now all the compiz stuff works. But at the expense of of other things not working as they should. Solution turn it off simple as that. Had problem with latest Mplayer not working after blue skin update, removed downloaded xmmms skin problem solved. Flash went back to old version till problem solved DL latest from site problem solved. I also use Arch on 1 computer feel free to try took me a few attempts to set it up, Needs constant tweaking, very fast distro never stops updating, I also run Elive Gem, thats the machine I earn a living on runs 24hrs a day.everything works because its tried and tested that has never crashed. And also my own Distro Ununtu server based E17 set it up over a day or two between working, that has only crashed a couple of times in 2 months, I run it with 4 animated virtual desktops and animated Icons etc.I have never had Firefox crash on any machine apart from running Compiz. But I don't blame Gutsy for the drivers not working or the flash or Mplayer problems, Look on other forums and you will see the same problems and then maybe learn to fix them as I do.

---

### Post by yabbadabbadont on 2007-12-20
> **rsambuca said:**
> I don't think I have had any crashes with FF and Flash sites.  Perhaps it is something else.  What is your videocard?  What driver are you using?  Are you running compiz?

Sometimes flash will crash if you don't have the mstcorefonts installed.

---

### Post by Z_o-s-o on 2007-12-20
I've got the Nvidia restricted driver and its running a Geforce Go6150 in my laptop.

Yes I'm using compiz but it crashes with or without. If it helps at all, sometimes even browsing folders without FF running, ubuntu freezes, and resumes 3-4 seconds later.  In System Monitor you can see it as a brief spot of 100% cpu usage.

---

### Post by yabbadabbadont on 2007-12-20
Do you have the mstcorefonts installed?

---

### Post by Z_o-s-o on 2007-12-20
yes

---

### Post by yabbadabbadont on 2007-12-20
Random freezes seem to happen to quite a few Gusty Gibbon users.  :?

---

### Post by Z_o-s-o on 2007-12-20
Yeah it gets annoying.  But I think using a game in Wine makes it much much worse. If i reboot after using wine its ok for a while.

---

### Post by Z_o-s-o on 2007-12-20
To expand on that, when I'm getting these problems, system monitor shows a burst of NICE cpu cycles in the spot where it froze

---

### Post by finchx6 on 2007-12-20
I've got Gutsy running on a gateway laptop that I just recently bought off newegg for dirt cheap.  It came with Vista which results in an automatic format in my apartment...  I'm a graphics artist, so I have to at least keep xp on my main design computer but thats as far as I'll go.

From reading everyone's thoughts on this, in this particular thread, it seems like its not so much Gutsy itself as it is certain things we're adding to it.  

Currently I can't get anything having to do with flash working on this laptop, which really doesn't matter much considering that my sound card refuses to work as well.  I've gotten multiple solutions for that one and none of them seem to work.  On a plus side, my built in wireless worked right off the bat, but I had to turn off WEP on my router so that gutsy wouldn't freeze.    :confused:

Even with no sound or flash, Gutsy runs infinitely better than Vista ever dreamed of.

---

### Post by Geekkit on 2007-12-21
> **finchx6 said:**
> Currently I can't get anything having to do with flash working on this laptop

Hey finchx6:

Grab the flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb file that is referenced here:

[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

... the link to it is:
[http://ubuntuforums.org/attachment.php?attachmentid=53648&d=1198033332](http://ubuntuforums.org/attachment.php?attachmentid=53648&d=1198033332)

or here:

[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)

It's a deb file which is a self-extracting archive/installer like the windows/mac world and it installs to take care of that flash problem. Hopefully that will be one down and [ insert number here]  to go.

:)

---

### Post by RawMustard on 2007-12-21
I agree, have given Gutsy a good work over in the past 3 weeks on two different machines(A laptop and workstation) and lots of thing are broken.

For me, vlc is borked, skipping sound.
Can't play half my ogg collection in totem or exaile.  Some files play others just do nothing. mplayer works though.

New printing setup program is borked, can't find my linux compatible hp laserjet.

Had heaps of trouble getting my Nvidia card working correctly, though I still can't get TV out to work.

Flash won't install correctly in firefox.

Random freeze ups for no apparent reason.

Clean install on both machines!

Had/Have none of these problems in Feisty!  All in all, Gutsy is a piece if sh1t really.

---

### Post by Z_o-s-o on 2007-12-21
Wow that a lot of problems.

Really, everything would be OK for my laptop if it didnt have the small freeze ups and flash actually decided to work.

Print for me has been pretty smooth. I've got some old 6.06 live cds and fiesty and gutsy are head and shoulders above those.

---

