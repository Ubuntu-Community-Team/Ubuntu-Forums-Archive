---
title: "Share with the community your Maverick Meerkat install/upgrade experience"
date: 2010-10-13
forum: The Cafe
---

### Post by frodon on 2010-10-13
[SIZE="3"][COLOR="Red"]*** Disclaimer for those willing to analyse this poll ***[/COLOR][/SIZE]

[SIZE="2"]- Most of users voting here are users with issues,
users with painless experience are not likely to come here. So the statistics here do not represent the reality.
- If you want to compare Maverick Meerkat release with other ubuntu releases based on this poll then here are the previous polls (the only good reference to start an analysis)[/SIZE] :

[Lucid Lynx Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=1465548")
[Karmic Koala Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=1305924")
[Jaunty Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=1133869")
[Intrepid Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=963853")
[Hardy Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=764847")
[Gusty Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=580852")

[You will find here a Summary proposed and maintained by NCLI - Click Me]("http://spreadsheets.google.com/pub?key=t0XWfWgqJpYxCGAZ1G8U-og&output=html")


The purpose of this thread is to share your experience installing/upgrading Maverick Meerkat.

Did it work flawlessly ? 
Did you get problems ? 
Did you manage to solve them ? 
if yes how ?
...
...
.

Feel free to post your experience here and please explain how you solved the problems you got, it might help other users in your case.

Thank you for contributing :KS

---

### Post by msmx5s on 2010-10-13
I can't vote on the poll. :( (voters: 0. you may not vote on this poll)

However, on my Fujitsu Siemens V5515 fresh install to 10.10, the only real issue was with the display drivers. This is a standard problem with the Sis display card. Was "quite" easily solved using the drivers on [this page.]("http://ubuntuforums.org/showthread.php?t=1548547")

I also couldn't connect to ethernet during the install, but it didn't cause any problems.

On the whole, a very stable release in my limited experience :)

I upgraded my misses's HP/Compaq Mini 1000 netbook too from 10.4, and all went well. Had a few probs (can't remember what! lol), but sorted them out, not too much trouble...

---

### Post by Kriteas on 2010-10-13
I upgraded from 10.04 UNE and most things went fine, but am having 1 major problem with the wacom stylus not working well with the leftside icons-bar and top panel. As I'm on a tablet with stylus as the only input option this is a major problem :(

---

### Post by lechien73 on 2010-10-13
I've been running Ubuntu since 9.04 on this Dell Studio 1735 laptop, and every upgrade/installation has been completely trouble-free.

I upgraded from 10.04 LTS, rather than doing a clean install.

What didn't work straight away was VMWare Player, and Sopcast.

I corrected both of these as documented here: [http://uri.tl/17](http://uri.tl/17) and here: [http://uri.tl/18](http://uri.tl/18)

I've been very happy with 10.10 so far...as I was with the previous versions.

---

### Post by CrispyCritter on 2010-10-13
I can't vote in poll either.

I ran into a kernel bug that prevented X from running (blacklisting intel_ips worked around bug); got it running by asking questions here, and posting dmesg output with the kernel OOPS.

That's the only major problem so far - fresh install.

---

### Post by frodon on 2010-10-13
> **CrispyCritter said:**
> I can't vote in poll either.Yep this is weird, trying to fix this ASAP (it seems i am able to though).

---

### Post by msmx5s on 2010-10-13
> **frodon said:**
> Yep this is weird, trying to fix this ASAP (it seems i am able to though).
It seems so lol


voters: 1. you may not vote on this poll

---

### Post by rbrick49 on 2010-10-13
absolute beautiful upgrade

---

### Post by ERIC H on 2010-10-13
Upgraded from 10.04 64-bit in about an hour yesterday and the only problem I have also existed in 10.04 on an HP 6510b. When the laptop is plugged into AC power and the lid is closed it will not suspend. Resolution is to unplug the laptop, close lid/suspend and plug back in, no biggie.

I haven't fully tested every aspect of the system and how I use it but so far there have been zero issues; Virtualbox works as before, I'm able to access all Windows shares on my network, existing printers still functioning, no slow downs or lags while using GNOME.

Also, can't vote.

---

### Post by crienoloog on 2010-10-13
Can't vote either...

latest update ; major disaster. Grub won't let me boot Ubuntu and back to first grub screen and have to resort to Windows 7. :frown:

---

### Post by pmlxuser on 2010-10-13
clean install on acer aspire one 750h, well the install was quick and smooth, liked the downloading updates while installing feature.
As usual system was usable after install but had to do the normal poulsbo fix, which in fair terms was painless, thanks to good documentation of the forums...
System works better (windows xp which come with the netbook freezed frequently, tried windows 7 worse) ubuntu flawless (well almost, freezes once in a while, but am happy)
cudos ubuntu developers and connical.

---

### Post by Elfy on 2010-10-13
Can anyone other than staff vote in here now?

---

### Post by lykwydchykyn on 2010-10-13
I tried to upgrade my workstation from a local mirror, but after fiddling with it for a while I gave up and did a "hotwire" upgrade by just changing my sources files and dist-upgrading.  It actually worked pretty well with no major issues so far, just tweaking things here and there because the old configs were invalid or something.

My laptop was smoother, apart from one of my plasma widgets crashing plasma when I logged in.  Had to do surgery on my plasma-desktop-appletsrc file to remove the bad widget.

---

### Post by kansasnoob on 2010-10-13
> **forestpiskie said:**
> Can anyone other than staff vote in here now?

Worked OK for me.

---

### Post by Elfy on 2010-10-13
> **kansasnoob said:**
> Worked OK for me.

Thank you :)

---

### Post by lechien73 on 2010-10-13
Nope...still can't vote, for some reason :confused:

---

### Post by cpmman on 2010-10-13
Voters: 3. You may not vote on this poll

---

### Post by Elfy on 2010-10-13
oddness

---

### Post by James Keating on 2010-10-13
Two upgrades: one disaster and one essential failure. 

The disaster was the NEC VersaPro VY15F laptop with an Intel 855 graphics chip. Each upgrade introduces advanced new features that further neglect this not-so-old and not-so-unusual hardware. It used to work fine. Then I got problems with suspending. 10.04 gave me the infamous five dots on a blank screen. No documented solution worked, and I had to find a new one on my own. 10.10 was an improvement in that it actually booted, but X completely failed. There was, as of yesterday, no documented solution at all, and I had to find one on my own. It turns out that Ubuntu replace my previous xorg.conf with one that doesn't work. The new kernel works better than the old standard one, but neither worked as well as a release candidate I ended up using for 10.04, which I will use as long as standard kernels give me trouble.

The essential failure is on another machine that used to have a Japanese environment and now cannot create a Japanese locale (it segfaults). This may not be the fault of the upgrade at all -- the machine kept freezing, and I seem to be the only person with this problem. I expect it will solve itself through updates and upgrades, like most problems. 

Every upgrade brings trouble and glitches. I don't really mind most. With all the different machines out there, and all the different software combinations on them, rough edges are inevitable. 

The Intel 8xx failure is inexcusable, though. It was known before 10.04 was shipped, and though I read the warning in the release notes I had no idea that I had that chip until booting failed. None of the suggested fixes worked for me. Now the next release not only is still broken, just as severely, but it is broken in a new way, completely undocumented and completely ignored in the release notes.

---

### Post by bardu on 2010-10-13
Can't vote either, however, flawless upgrade as usual.

---

### Post by s.fox on 2010-10-15
How is the voting situation looking now? 

Can anyone other than the staff vote?

---

### Post by huntspores on 2010-10-16
Hmm... I hate having been the first one to vote the last choice, but I did and I'll explain why I went back to 10.04 netbook remix.

I don't think the update went well on my HP Mini netbook, I got some sort of random glitchy merger with the 10.04 UI and the 10.10 UI.

The colored dock didn't agree with me, being new to Ubuntu I'm still rather in love with the translucent interface and like seeing as much as my three dimensional scenic wallpaper as possible.

In 10.10 I lost the control of windows and apps through the menu bar at the top, I don't know if that was a result of my failed upgrade or not. Also the new dock and interfacing with the new UI wasn't as natural and speedy as 10.04. So the menu choices at top gave rather fast and instant results.

Could I have done a fresh install of 10.10? Yes.

Could 10.10 worked if I did? I'm pretty sure.

What's preventing me? I like 10.04 for the translucence effect and the speedy top menu choices as I switch around different apps constantly. I will investigate the new 10.10 UI further.

I'm a mouse user, it seems the 10.10 UI is leaning towards the finger based icon approach of touchscreen smartphones and tablets, both which I totally detest with every fiber in my body.

Some of the world might be following the piped piper of Cupertino down the stripped down netbook iFad road, but a finger will never replace the fine detail and control a pointer provides, and no touchscreen will never replace the tactile feedback a real keyboard provides.

Sorry about the rant, :)

---

### Post by Dobbie03 on 2010-10-16
As usual I haven't struck a problem yet, works flawlessly.

---

### Post by Hippytaff on 2010-10-16
I did wubi install of 10.04 a while back and on the back of that decided to rid myself of windows on the 10.10 release (and my favourite book being Hitchikers Guide to the Galaxy helped with my decision with 101010 being 42 in binary - the meaning of life the universe and everything)

So I decided to do a full install with seperate /home partition (on the advice of serial distro upgraders) and its the best thing I've ever done to my pc!!!

thanks devs and all other staff (paid and voluntary) :-D

---

### Post by Frogs Hair on 2010-10-16
The ISO downloaded perfectly.  I had flawless installation and six days in I have no bugs report.

---

### Post by Spr0k3t on 2010-10-16
So far, this has been the most flawless upgrade and install on the computer systems I maintain/support.  Only one flaw... and that was the lircd on the mythbuntu system needing a complete reconfigure.

---

### Post by areteichi on 2010-10-16
I was able to cast my vote!

My experience has been mostly positive. I did a fresh install. I really like the tighter integration of Ubuntu One in 10.10, though I believe it still needs further improvements and fixes. One issue I did encounter was that, for my laptop chipset, there was a problem playing flash videos in fullscreen. I had to apply a minor workaround ([found on this thread]("http://ubuntuforums.org/showthread.php?t=1593363")):
[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)

Since I installed 10.10 yesterday, I'm just trying to get used to the new fonts. Not to imply that I don't like them. I certainly do. But they do look somewhat different :P

Anyway, I've been a dedicated Ubuntu user since 6.06 and I'm happy to say that this is my favorite release to date :-D
It's been a long road but this release certainly makes me feel the distance Ubuntu has traveled during the four years I have used it.

---

### Post by BlazeFire247 on 2010-10-17
I did a clean install, worked flawlessly.

---

### Post by Jay Car on 2010-10-17
With each new version since Gutsy things just kept smoothing out more and more...until Lucid. It's the only one that I've really had to struggle with.  But Meerkat - both upgrading the Lucid drive, and fresh installing it on another drive - went very well. In fact, I think the new installer is an absolute gem.

To be honest, I wish Meerkat was the LTS instead of Lucid. 

I'm just happy (and surprised!) when stuff works, and Meerkat definitely works for me.

---

### Post by kio_http on 2010-10-17
System works fine, but Kubuntu ubiquity is unable to delete a partition in manual mode (Installer crashes). Had to do partitioning with another tool (Apple Disk Utility).

---

### Post by TR82 on 2010-10-17
Painfree install from 10.04 LTS to 10.10.

Can't thank you folks enough for all your hard work :)

---

### Post by SantaFe on 2010-10-17
We need an I Voted sticker for this post! :KS  I went the upgrade route from Ubuntu 10.04 to Ubuntu 10.10.  Talk about ancient eh?   Surprisingly enough it went flawless.  No really big problems at all, well other than losing the Spinning mouse XFCE splash screen that is.  But that's evidently not a problem per say. :P

---

### Post by norm7446 on 2010-10-17
Can I vote Twice. As I upgraded Lucid on my Laptop with out a single prob and it has worked flawlessly since. 

But I cant get it onto my Desktop......

---

### Post by sille777 on 2010-10-17
upgraded....

Would not boot... had a grub error of some sort....

a quick search and found an easy fix.   Fixed Had to purge and reinstall grub from the 10.04 live cd.

now works flawless.

Yea!!!

---

### Post by m4tic on 2010-10-18
Still downloading 57%. I'm at my university, getting speeds of 1Mbps.
The RC didn't boot on any of my machines, hope this works

UPDATE: Finished download about 30min ago, will install when i get to my crib

---

### Post by pommie on 2010-10-18
Due to having a tv card unsupported in 10.04 but is supported in 10,10, I installed at the Alpha2 stage, had a few problems with the graphics card (nvidia), just used safe mode until one of the many updates fixed it :P
Other than the graphics I have had no problems :guitar:

Cheers David

---

### Post by Cam42 on 2010-10-18
Just a couple of issues with Unity.
Fresh install.

---

### Post by proyectomx on 2010-10-18
I am currently using ubuntu 10.04, and when trying to install ubuntu 10.10, my dell latitude d620 just shuts off randomly, sometimes after a few minutes, sometimes after one hour, it just shuts off.

I tried clean install and upgrade... same symptoms. Tried installing all updates and different grafics drivers for the nvidia... same symptom, just shuts off.

Even booting from usb randomly shuts off, at first I thought it was a matter of updating kernel or drivers.

There is something seriously wrong with maverick meekat.. in computers that work is faster, but this painful when it doesn't.

---

### Post by Knowle on 2010-10-18
Install -

I'm not sure if it's the Broadcom drivers fault or Additional Drivers/Hardware Drivers but it F@#$%^& sucks in this release. The only saving grace for me was that it appears the bug with Intel GMA drivers were fixed(broken since 9.04) so no more crazy screen flickering. The Ubuntu font family is very nice as well. I'll be sticking with 10.04 for a while. :\

The Broadcom STA driver doesn't work in 10.04 for me either, it installs and activates but it doesn't detect any networks. The Broadcom B43 driver installs and works. In 10.04 ONLY. In 10.10 I get a SystemError:InstallArchives() failed.

random thoughts on 10.10: The install itself worked but on my first update it broke and I had to pull up a terminal window to fix it, then finish my update. Starts up faster and the login screen was a bit cleaner looking. The Applications, Places and System buttons were cleaner looking more like browser tabs rather than boxy like the previous releases. My first update I had to pull down like 20 packages|40ish MBs of data, better than the 322 packages/278.6MBs I grabbed after I installed 10.04 LTS but whatever. Shutdown was faster as well.

edit:
For reference, this is Broadcom BCM4312 (rev 01). The laptop in question this was all tested on is a Dell 1545N that came pre-installed with Ubuntu.

---

### Post by m4tic on 2010-10-18
Can't even boot the live image, md checksums are correct. i tried on amd machine and a lenovo intel laptop same thing, even with unetbootin nothing works. glad i'm on mandriva, seems like ubuntu's racing for the sake of getting ahead at the expense of minimal testing. well this is the last time i attempt to install an operating system. mandriva has been holding up well for a while and it's only now i trully appreciate the work they've done considering their population vs ubuntu's. congrats to those who got theirs working good luck

---

### Post by BigJules on 2010-10-18
Perfect upgrade - impressive, stable, v easy on the eye, a distro to love!

---

### Post by lykwydchykyn on 2010-10-18
Well, just finished upgrading my son's computer over lunch and killed his video.  Come to find out his card is no longer supported in Maverick.  UGH.

---

### Post by 73ckn797 on 2010-10-18
Ubuntu 10.10 works great on my Toshiba Satellite laptop. Still have pop-up windows on a Java applet that only have the borders and no text and are completely transparent. All versions since 8.04 work on the laptop.

My desktop is another story. 8.10 and now 10.10 have been and are a disaster. 10.10 has constant Firefox and Open Office crashes. I have performed 3 fresh installs of 10.10. The md5's are correct on the iso file and disk checked good (was slow burned). 

I began losing scanner functionality with 9.10, 10.04 and 10.10 resulted in a complete scanner failure using xsane. I have tried multiple remedies found on the forum to no avail. Simple-scan is simply inadequate for my needs. No auto saving and multiple document scanning results in nothing worth using for my needs.

I am reverting back to 9.04 until a later version.

This has been my experience and will differ with others.

---

### Post by NCLI on 2010-10-18
Installed on my box, only to find that I'm not able to get to the desktop. I'm still working on solving the issue.

---

### Post by Cobracommand0 on 2010-10-18
Installed 10.10, had to do the Nvidia/DVI workaround to get display working (this has always been SOP installing Ubuntu on my box).  Other issues with drives not mounting, compiz/screenlets not starting/booting, and some configs not wanting to stay. Nothing really out of the ordinary as far as problems... 

Decided to go back to my 10.04 drive with everything running smoothly, though.  10.10 needs some time for updates IMO.

---

### Post by 73ckn797 on 2010-10-18
> **Cobracommand0 said:**
>   10.10 needs some time for updates IMO.

Those will likely be dealt with in 11.04. Then then there will be more issues.

---

### Post by Cobracommand0 on 2010-10-18
Such a vicious circle.. It's like running out of chips and still having cheese, then buying chips and running out of cheese, and then...

---

### Post by 73ckn797 on 2010-10-18
> **Cobracommand0 said:**
> Such a vicious circle.. It's like running out of chips and still having cheese, then buying chips and running out of cheese, and then...

Haha!! Good analogy.

---

### Post by EricLorenz on 2010-10-19
I did an 'offline' install using the alternative CD. For the *most* part...it has gone OK- and in the grand scale of things, my issues are probably low priority. BUT, to me...they are major...

1. During the install, somehow my repositories/ dependencies have gotten messed up. The major result of this was Evolution being removed by the upgrade program.  I now cannot re-install it as I am being told that there are dependencies missing/broken (search in Installation/Upgrades for 'Evolution gone' for details). I use Evolution to work with my Google Apps hosted email/calendar/contacts. While I am able to use Google directly, Evolution makes it a lot eaisier. Thiis is rocking my world. To be fair, there is someone that has been trying to help me, so far the solutions offered have not worked. I have searched and there seems to not be precedent for this issue. It seems there is either no one else having this issue/ knowledgeable enough to help solve it, or no one that cares. (The last sentence is my opinion, more than willing to correct it if shown otherwise). 

2. The upgrade also removed the Clock applet from my Applet bar. When I try to re-install it, I get  this- "The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet". Do you want to delete the applet from your configuration?" No clue behind as to what the 'problem' is! No response on the forums yet. Again, maybe not a major issue to most, but to me it is major as I got to find the Clock Applet a major convenience. 

3. For some reason, the upgrade process defaulted to always wanting to look for and check the alternative CD anytime I refresh the repositories in Synaptic or upgrade manager. I finally had to go in and uncheck it in software sources. It had never done this before.

Overall, it is running fine otherwise....but, if I cannot get these things fixed, I may have to go back to 10.04...or do a full re-install of 10.10. If I do though, I will NOT be happy.

Eric

Now overa

---

### Post by misfitpierce on 2010-10-19
Accidently hit upgraded but I did fresh install for 10.10. It worked flawlessly on Dell Inspiron 1420 which came from Dell with Ubuntu preloaded but all works perfect on the laptop on 10.10.

---

### Post by ThatBum on 2010-10-19
Clean install of 10.10 on my netbook. Worked a treat. Interesting way the installer has turned. I don't know about having an option to install restricted stuff with the rest of it. It seems...unclean, mostly because I don't see the difference between ubuntu-restricted-extras and ubuntu-restricted-addons. But meh. I'm splitting hairs.

---

### Post by AlmaTlust on 2010-10-19
Well, I had kubuntu-ppa, kubuntu-backport and kubuntu-experimental activated. The upgrade process went without problems, but after restarting all windows would show up maximized and without borders (without title bar, that is). I haven't been able to fix it yet, so will go for a clean install...

---

### Post by beew on 2010-10-19
I tried upgrade on an old laptop (not in any real use). Other than screwing up the graphic and wireless other things seem to work ok or better. The graphic because the old Nvidia-96 driver is not upgraded to support Maverick (or has not yet according to some people) so it is not Maverick's fault I suppose. The wireless card uses a broadcom legacy driver and it has not been working with encrypted AP even in Lucid, but I am getting weird errors and cannot even detect wireless ap in Maverick.

Is it normal to take 3-4 hours to upgrade? A clean install takes about 15-20 minutes. Installing all the softwares takes maybe half an hour or less if you know exactly what to install (or use an automated script). Upgrading seems to be a very delicate procedure, I am worried that some configurations may be messed up without me knowing it but will manifest as some difficult to diagnosed problems down the road. I will definitely go for a clean install next time.

---

### Post by oroberts on 2010-10-19
update disaster.
I've been through 4 other major updates. This is the only one to epic fail.

[http://ubuntuforums.org/showthread.php?p=9964549](http://ubuntuforums.org/showthread.php?p=9964549)

---

### Post by dakshsrivastava on 2010-10-19
Hey everyone..
This is my first post in the ubuntu forums.. so im sorry if i screw up the language or anything else for that matter.
I bought a new PC a few weeks back, and decided to install 10.04 LTS on it. It worked like a charm without any problems what so ever, though i had problems connecting my mobile broadband USB which was never resolved. 
I upgraded to 10.10 two days back, and though the graphics are more pleasing than ever, there were a few problems i did come across.

Note : There were no problems during upgrade process. All worked out perfectly Fine.

1) There is some problem with the sound driver. The quality of sound in movies/music when I play in rythymbox/VLC is pathetic. There are 1 sec pauses after every 3-4 seconds and the sound seems to be broken. Its impossible to watch movies at this time.
p.s. Everything works fine in XBMC media center.

2) The box where i enter text to update my status via the broadcast account (the small text box that appears on clicking the user button - next to the shutdown button) was not appearing till yesterday, now it is but its not posting anything i enter to my facebook account. the same problem persists on 10.04 LTS

3) before i sat down to write this comment, i got an error message "OPERATING SYSTEM NOT FOUND" when i switched on my laptop. Im sure im not supposed to get that message.

That rounds it up.
Even though im having the above mentioned problems.. im still happy with 10.10 :)

---

### Post by jfreak_ on 2010-10-19
Perfect dual boot install on my dad's laptop. I am pleased to see that they have sorted out the plymouth+nvidia problems that plagued the last release. getting vcd's to play remains as big as a hassle as it was earlier.

---

### Post by cra1g321 on 2010-10-19
Everything installed perfectly and running perfectly. 

Just like it did for 10.04, 9.10, 9.04 :)

---

### Post by Spinland on 2010-10-19
Fresh install of the 64 bit version on an Alienware M17x (r1) laptop.  Quad core Q9000, Nvidia 260M vidcard, on-board Nvidia 9400M video, 8GB of RAM installed, dual 750GB hard drives.

The only real problem I encountered was the initial install went immediately to a blank screen until I disabled the hybrid SLI and the on-board graphics in BIOS.  Once the system was running entirely on the add-on 260M card the install process went fine.

I selected the options to download current stuff during install, as well as to search the install CD.  Contrary to some of the reports I read, my wireless came up without needing to connect directly to a router.  Once the installation was complete the system driver scan found the most current Nvidia driver for my card(s) and installed it without a hitch, and I was also able to re-enable the on-board card and hybrid SLI with no further issues.  Grub played nicely with the existing Windows 7 installation on the primary drive (I installed Maverick on the second drive).  

I've had an odd speed bump or two concerning the 64 bit architecture and the fact that most drivers are 32 bit, but that's largely due to my inexperience with Linux.  There are packages that help, and the --force-architecture switch to rely on, and so on.  Google is my friend.  :guitar:

---

### Post by huntspores on 2010-10-19
I wish I could vote again, 10.10 has installed/upgraded just fine on the laptops and desktop machines I have others set up on.

---

### Post by Duncan J Murray on 2010-10-19
Just one problem for me:

Slight jerkyness of special visual effects on my ageing laptop.  Although I didn't have any problems with 10.04.

Easily solved by disabling special effects.  I will wait for a later kernel to see if that fixes things.

Otherwise, it's great!

Duncan.

---

### Post by norm7446 on 2010-10-19
> **m4tic said:**
> Can't even boot the live image, md checksums are correct. i tried on amd machine and a lenovo intel laptop same thing, even with unetbootin nothing works. glad i'm on mandriva, seems like ubuntu's racing for the sake of getting ahead at the expense of minimal testing. well this is the last time i attempt to install an operating system. mandriva has been holding up well for a while and it's only now i trully appreciate the work they've done considering their population vs ubuntu's. congrats to those who got theirs working good luck

Does your lenovo laptop have ATI graphics on it. As This is what I'm blaming my lack of success with 10.10. As never had any prob's with Nvidia. But with my new system I've installed a ATi card, and now no Ubuntu.

---

### Post by beew on 2010-10-19
> **dakshsrivastava said:**
> Hey everyone..

1) There is some problem with the sound driver. The quality of sound in movies/music when I play in rythymbox/VLC is pathetic. There are 1 sec pauses after every 3-4 seconds and the sound seems to be broken. Its impossible to watch movies at this time.
p.s. Everything works fine in XBMC media center.)


This is so strange because I have the opposite experience regarding VLC.

In 10.04 when vlc plays some (not all) MP3 music it would either give out a hiccup like sound or otherwise sounding choppy and broken in the beginning of the files. This just happens in the beginning, the rest of the music is fine. This also only happens to VLC but not other music players (tried mplayer, Amorok and Banshee) 

I have Ubuntu10.04 installed in a labtop and an external hdd. I have plugged the external installation into different machines and vlc always has the same problem so it has nothing to do with the hardware, but some conflicts somewhere between the OS and vlc.I tried different workarounds found in the forum but nothing worked. It is kind of annoying so in the end I have to uninstall vlc from Lucid and use other music players.

Now with Maverick the hiccup sound and choppiness have disappeared. Vlc is as smooth as it ever can be. The other music players are good too.

---

### Post by geekwanabe on 2010-10-19
I upgraded from Lucid on my Dell Studio 1550.  Everything works perfectly.  Plus, it seems to load faster and for the first time ever, suspend actually works when I close then open my laptop back up!  How cool is that!

Thanks guys.  Again, you rock and make my computer world so much easier!

---

### Post by Blodskaal on 2010-10-20
I ran a flawless upgrade. The second time, the first time I broke the entire system, and I had to reinstall 10.04 entirely. It was my own stupid fault though. I had a separate /var partition, set up on 9.10. But the upgrade to 10.10 required almost double the amount of storage that 9.10 required. So my partition was a few 100 MiB short. In the end I messed things up badly while trying to fix that.

EDIT: I do have some issues with the X-server suddenly freezing up, about once per day, that I didn't have on 10.04, but I guess that will be smoothed out in a few minor upgrades.

---

### Post by ikt on 2010-10-20
upgraded and it went fine, least problematic upgrade yet.

---

### Post by t.rei on 2010-10-20
The upgrade was without any more trouble than any other upgrade with kernel... (reinstalling nvidia drivers...)

---

### Post by mortezamilani on 2010-10-20
I just installed Ubuntu 10.10 and nothing works properly! I'm running on HP Pavilion DV5-1299ee and HP doesn't support driver updates for linux. so I got into lots of problems.
I had problem with Memory Stick Reader, SATA port, Second Display via Serial port, USB. I figured out how to fix them.
But still I have problem with my Graphic card, Nvidia Geforce 9600M GT. I installed the driver but the computer doesn't wake up after sleep. I tried another driver suggested by ubuntu, and now, even suspending doesn't act.
But good thing is that my Wired Lan and Wireless lan work properly!

---

### Post by cariboo on 2010-10-20
> **mortezamilani said:**
> I just installed Ubuntu 10.10 and nothing works properly! I'm running on HP Pavilion DV5-1299ee and HP doesn't support driver updates for linux. so I got into lots of problems.
I had problem with Memory Stick Reader, SATA port, Second Display via Serial port, USB. I figured out how to fix them.
But still I have problem with my Graphic card, Nvidia Geforce 9600M GT. I installed the driver but the computer doesn't wake up after sleep. I tried another driver suggested by ubuntu, and now, even suspending doesn't act.
But good thing is that my Wired Lan and Wireless lan work properly!

If you are trying to get drivers from HP, that isn't going to work, all the open source drivers are included with the kernel, and only the proprietary drivers are available for outside sources. Suspend/Hibernate depends on the BIOS. We've seem systems that consist of the same hardware put together by different manufacturers, some that will suspend/hibernate and others that won't .

It would be helpful if you document what you had to do in order to get things to work.

---

### Post by tstrike on 2010-10-20
Alienware M15x - Upgraded to RC no problem... is there a GA version?

SMOOTHEST UPGRADE EVER !!!!!:popcorn: :KS

---

### Post by Darth Penguin on 2010-10-20
It's the first week I use Linux and it only took me one day to figure out how to use Ubuntu, that's how easy it is and user friendly it is. And that includes the command line in the Terminal. The install was flawless, and I repartitioned my hard drive to give it more space. I have Ubuntu and Windows XP dual-boot. I find the Windows vs Linux arguments pointless, you can have both. After installing Ubuntu I haven't used Windows at all since I use this laptop primarily for emulation. The Ubuntu Software Center makes it easy to install most of the emulators for Linux and I also think WINE is tasty, runs many PC games. I have no complaints whatsoever and am very pleased with Ubuntu.

---

### Post by caro on 2010-10-20
The upgrade itself went fine, but I have two problems so far:
1.  Sound on Rhythmbox or any player was skipping and jumping around.  Removing Pulseaudio fixed the problem.
2.  Everything launches slower and shutdown is much slower.
3.  Touchpad periodically stops responding but comes back after a few seconds.

---

### Post by ratcheer on 2010-10-20
I did the "dirty install" over my former Lucid installation. It worked very well. There were some minor issues, but all were fixed in fairly short order.

I did have a bit of a time removing the old Lucid kernels, because the package manager no longer recognized their existence in Maverick. But, once I figured it out, that was easy, too.

Tim

---

### Post by Guilden_NL on 2010-10-20
Three upgrades - 2 HP laptops, 1 custom/old desktop and all three went perfectly.  Have 1 HP netbook, 2 HP laptops, 1 custom/new very fast desktop to go but it's looking good!

Am very pleased with the legacy device support with new device support.

Wow, by far the best upgrade for me and I started with Gutsy Gibbon.  Was primarily Fedora for the previous 13 years.

---

### Post by Brent0 on 2010-10-20
Both of my installs were flawless except a weird Wifi issue that seemed to resolve itself on my netbook. I am extremely happy with 10.10. :)

---

### Post by jfbooth on 2010-10-20
Doing a network upgrade from Xubuntu 10.4 to 10.10. It is quite a bit more than 1/2 done .. shows 1 hr, 9 min remaining.

It seems to be stuck .. been sitting at the same spot for at least an hour ... maybe 2.

Terminal window in the upgrade window .. last few lines:

Removing update-grub hooks from /etc/kernel-img.conf in favour of /etc/kernel/ hooks.
Replacing config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
THEN 10 MORE FINDS
AND IT SEEMS TO BE STUCK ON THE 11TH FIND
found memtest86+ image: /boot/memtest86+.bin

and it is just sitting there.

update ... had to do something so did Ctrl C to terminate the update.  Rebooted to recovery screen.  Did a recovery of the top liste kernel.  Now get a boot showing 10.10 but no GUI .. boots to shell.  Going to have to install from scratch from Live CD.

---

### Post by srhart on 2010-10-21
I recently upgraded a server from the previous LTS (can't remember) to 10.04 and I'm just in the process of upgrading a laptop from 10.04 to 10.10.

There was a slight issue with the server upgrade (making me quite nervous) that caused the upgrade to simply lock up. I de-installed dns which wasn't needed anyway then restarted the upgrade and all finished OK.

However, that isn't why I write this.

My main problem with both of the mentioned upgrades is that several of the packages require user responses as they upgrade. This causes the process to stop. It's irritating to go back to a machine left for 2 hours only to find a question on the screen, which when answered leaves the dialogue telling me that there's another 2 hours to go, come back 2 hours later and another question.. and so on..

It would be a much better experience if the upgrade process visited all required packages requesting user questions up front, then once entered the machine could be left to finish the process unmonitored.

Anyone else agree?

---

### Post by Spinland on 2010-10-21
Second post for a second install. System was a Dell Inspiron e1505 laptop, 2GB of RAM and a single 100GB drive. Thankfully it had the Dell 1390 wireless. 

Partitioning went flawlessly, install was hitch free and the wireless worked right off the bat. Wireless Canon printer/scanner setup was a breeze thanks to having done it once already. 

Only hiccup came during system update. Something glitched and the updates halted until I did some command line stuff--easy since the upgrade app prompted me with what I needed to type. After that all was smooth sailing. 

A note if you're migrating a Firefox profile from Windows to Ubuntu: in this case some add-ons appeared to be Windows-specific and caused FF to lock up with hung scripts. I had to make a fresh profile, just import the bookmarks json, and install the old theme afresh. It might have been possible to debug and remove just the offending scripts but my route seemed quicker and cleaner.  Of course the Thunderbird mail folder came across perfectly. 

Multiple kudos to the Maverick team for an awesome job!

---

### Post by NJC on 2010-10-21
The upgrade from 10.04.1 LTS to 10.10 went smoothly - I had some temporary issues with the loss of Suspend, and F-spot now does not detect my camera. But Skype seem to retain sound settings (I mean Pulseaudio) and the font rendering is very VERY nice. I can't think of the other improvements, but overall a joy to use. Thanks to all who put their efforts into this release. 8)

---

### Post by gblues on 2010-10-21
Voted "upgrade - got many problems."

If I had taken this poll I probably would have gone with the "some problems but nothing major" but after today's kerfuffle I'm very close to writing off 10.10 for the present.

Upgrade: from 10.04 -> 10.10
System: VirtualBox (3.2.8 at the time of upgrade)
Method used: "Upgrade Distribution" from Package Manager

- Download went as well as could be expected for launch day.
- When the packages were being installed, a conflict popped up with my Samba configuration. Unfortunately, the dialog did not respond to either mouse or keyboard input. I had no other choice but to force-restart the VM.
- The half-installed upgrade obviously did not boot.
- I booted to recovery console and completed the upgrade via apt-get dist-upgrade (at least, that gave me the command I actually needed to run).
- After a reboot I had a desktop again; reinstalling guest additions partially failed due to the unrecognized X server.
- Loaded the OSE VirtualBox X driver and got my integrated mouse back.

At this point I encountered some minor problems: Seamless mode caused the title bar of the windows to disappear if 3d acceleration was enabled in the VM settings. I had the occasional crash during shutdown, but since it was during shutdown it didn't really matter.

This morning, my VM wouldn't boot at all. It gave me a message that it couldn't find my root partition! Fortunately, booting to a slightly older kernel got my VM booting again. So now I'm either stuck booting the 10.04 kernel with 10.10 and waiting for Ubuntu to release a fixed kernel (others have been hit by this problem running on real hardware so I doubt it's a VirtualBox issue), or go back to 10.04 whole kit, or another distro altogether. I haven't decided which yet.

---

### Post by rMatey on 2010-10-21
Pretty good experience.  Two upgrades with different experiences.
Dell B120 laptop 32-bit Update Manager upgrade to 10.10.  Everything worked flawlessly.
Self-built desktop 64 bit thru Update Manager.  Some problems experienced with a bunch of 0-bit files in system folder.  Memory was also spiking, but no real cause noted.  System Monitor showed a lot of similar named processes that were always sleeping, but no files were attached to the process ( tracked to the 0-bit files)
  I think I tracked it to several aborted backup processes that might have been mashed-up in the upgrade process.  Downloaded the 64-bit ISO and now everything is fine.  No process zombies or trash.  Memory footprint is low.

:P

---

### Post by cariboo on 2010-10-21
> This morning, my VM wouldn't boot at all. It gave me a message that it couldn't find my root partition! Fortunately, booting to a slightly older kernel got my VM booting again. So now I'm either stuck booting the 10.04 kernel with 10.10 and waiting for Ubuntu to release a fixed kernel (others have been hit by this problem running on real hardware so I doubt it's a VirtualBox issue), or go back to 10.04 whole kit, or another distro altogether. I haven't decided which yet.

It is a virtualbox issue, I would suggest you upgrade to 3.8.10, available  [here]("http://www.virtualbox.org/wiki/Linux_Downloads"), and try again, I had several failure with the 3.8.2, before installing the latest. One of the big things is that 3.8.2's guest additions aren't compatible with Xorg 1.9.

---

### Post by quequotion on 2010-10-22
I had minimal problems with upgrade--most of them caused by me.

I upgraded in an unusual way so as to keep (available) PPA repositories active and update from the bleeding edge of Lucid to the bleeding edge of Maverick in one go.

This method caused a few dependency riddles (mostly sorted out with apt and dpkg) and also a few over-the-edge packages to be installed (specifically from the **compiz**, **network-manager**, and **ipheth** PPAs)*.

All of the problems I experienced were already posted here and there in the forums or launchpad and most of them had a solution or a workaround already.

Only snes9x-gtk won't work like it used to. I can't figure out why, but it doesn't want to output video at all.

I have replaced it with bsnes which is working much better than it used to. (even "Accuracy" mode runs on my pc at a pretty reasonable speed)

This was my best install/upgrade since beta Intrepid.

Thank you very much ubuntu-release, ubuntu-dev, ubuntu-bugs, et all!





* PPA issues:
Compiz has undergone some kind of abi change and the repository has only a few of the new packages at the moment.

The network-manager version in the ppa is waiting for isc-dhcp-client to be packaged and isn't compatible with dhcp3-client, which means *it will kill all your network interfaces*.

iPheth may still have a bug that tries to create a wwan interface (which does not work). This is fixed upstream (a developer responded to my post like lightning, much respect!) but I don't know when it will be repackaged in the ppa.

Many other PPAs have no packages for Maverick at the moment, although their Lucid branches exceed the Maverick versions. There are always a few PPAs that become redundant after upgrades but I'm hoping a few will come up with new packages soon, like pulseaudio-equalizer, notify-osd-config, etc. The versions I kept from Lucid are still working

---

### Post by grimreaperwithalawnmower on 2010-10-22
Actual process of runnning the upgrade was, as ever, without issue.

Usual NVIDIA issues for me.  After eventually getting everything sorted with karmic/lucid, I'd hoped this issue had gone away, but to no avail!

Basically, GDM wasn't displaying & booting to console, despite saying that GDM was already running.  Managed to get in in recovery mode, download the latest NVIDA GeForce 7100 nForce360i driver, restart, remove all NVIDIA drivers and reinstall latest version.  Started GDM and all seems well.  Successfully rebooted just as well.

Booting to Windows Vista is fine - thankfully GRUB is behaving itself for me now.

Slightly more faff than I would have liked, but having learned from previous expereinces, this upgrade was minimally stressful.

---

### Post by GoldNugget on 2010-10-23
I upgraded from Lucid to Maverick and it went beautifully. I am using an Intel D945GC motherboard and Nvidia graphics card. My HP Printer and Acer scanner didn't respond at first but a restart got them running fine. I like the Simple Scan application which really simplifies quick jobs.

All my settings and customizations returned perfectly and it feels comfortable and familiar yet also new and faster. 

I know some people are against upgrades but I generally have good luck with them. I don't dual boot and I try to stick to standard packages although I do have some custom scripts and drivers which all came through the upgrade working fine. (Installer asked me if I wished to keep the old versions, which I did.) 

My Nvidia GeForce 9600 GT card didn't require a driver reinstall, config file editing or tweaking of any kind, Compiz and TV out worked OOtB.

I have had good luck with upgrades but this one seemed the best so far. Great work Ubuntu and OSS developers.

---

### Post by jleach on 2010-10-23
Tried to upgrade from Lucid to Maverick but I am afraid the machine was very slow, crashed repeatedly esp using Chrome and just froze at various times.  I changed the kernel to RC which did improve things, but as I use this computer for work, I have gone back to Lucid, which worked like a dream.  I appreciate that there is a difference between the normal and long term editions, as the latter will have been tested far more, but having installed various editions of Ubuntu over the years, this is the first time I have had a problem.

Samsung NC10 2Gb RAM using netbook edition

Jonathan
UK

---

### Post by ugm6hr on 2010-10-23
Dell Mini 9, fresh install.
Just 1 issue, so not quite flawless.... But very easily solved:
[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

---

### Post by eltonw on 2010-10-23
I have already voted. 

I notice that when I cold or warm boot the machine *[COLOR="Red"][netbook][/COLOR]* [FONT="Trebuchet MS"]The keyring confirmation dialog now comes up* [COLOR="Olive"]twice[/COLOR]*[/FONT]. 
By that I mean: I successfully enter the keyring password, then _[COLOR="Sienna"]**the dialog comes up a second time**[/COLOR]_ and I have to enter the keyring password once again, *before* I can get to the desktop (already visible).

is this a bug or additional security?

... just wondering...

---

### Post by Praxicoide on 2010-10-24
I did a fresh Xubuntu install, with a separate /home directory that I kept, as always (since 6.10, I think). Everything went smoothly. It's been a while since I've had such a flawless installation, without any fuss with the graphic card (which got blacklisted the last time) or anything else.

My only problem is that the Parole Media Player browser plugin is not working, even though it was working fine with 10.04, and 9.10. I wish I knew what the problem was, but it's really not that  big of a deal. I guess I'll have to install the gecko plugin or VLC or something else if I can't solve it. Pity.

I also installed 10.10 for a friend on a PPC computer (an iBook G4). This was an update, since the CD would not boot for whatever reason. Everything went well. I'm checking everything and I'm surprised to find zero problems. The partner repository seems to be gone for PPC, which I guess sucks. The restricted-extras package is installed, however, and stuff like Java or mp3s play fine. (No flash, just Gnash, but that's always been the case for PPC.)

Overall two very positive experiences.

---

### Post by tbplayer on 2010-10-24
I'm in the "Install - worked but had few things to fix, nothing serious though" group. Did a fresh install using a clean drive on my Athlon XP 2400 box with 2GB RAM. I originally did this just to check out the latest Ubuntu - I've been running Mandriva on my home server for a couple of years and touting it as the easiest distro to install. But Ubuntu 10.10 is at least as easy, and probably a faster install. Very smooth and quick. Detected most of my hardware so I had sound and the correct video settings right away. I had to modify the smb.conf before I could access my home Window network, but then I was able to quickly and easily install a shared network HP printer. Performance is very good - even with Gnome it's better than Windows 7 on the same box. So far my only disappointment is no support for my HP scanner. Everything else is working well - I installed Opera for my browser and I'm trying out the included version of Evolution (I usually use Thunderbird and haven't used Evolution for several versions). I also installed all of the updates with no issues. I'm quite pleased and will be using this Ubuntu box as one of my Internet computers.

---

### Post by pionium on 2010-10-24
hi

I tried upgrading from previous LTS, but the upgrade was interrupted and Im left with a broken upgrade. Not that it matters, I thought, because I can just do a clean install. However, as with my netbook, the installer halts on the first screen. :(

Not having enough free time to figure this out at the moment probably means I will leave it for a while.

so long and thanks for the fish

---

### Post by note32 on 2010-10-24
kubuntu 10.10 is working fantastic, installed and everything just worked perfect
:KS

---

### Post by Netscannur on 2010-10-24
Everything appears to be functioning after upgrade from 10.04, but I'm unable to adjust my screen resolution up to where it was previously.  I think it's an issue with Intel 945 chipsets not being supported, but haven't had any luck fixing it.

Other than that, 10.10 looks awesome and works well, thanks guys!

---

### Post by Sonybuntu on 2010-10-24
I did a fresh-RC install. Other than the ATI drivers, nothing else was wrong.

---

### Post by Cobikegeek on 2010-10-24
I performed a fresh install with no problems at all. More polished installation process than previous versions. The shutdown/restart closing screen reverts to text mode, which is less than elegant, but boot and shutdown is very quick. I'm not wild about the default purple/pink color scheme, but that is easy to change.

Only issue I've had is the cd copy function in Brasero and Gnomebaker fails. Brasero error claims that Cdrdao plugin is an old version, even though it is the latest version. I finally resorted to installing K3B, arguably the best KDE app, but it requires lot of KDE overhead on an otherwise gnome desktop.

I also installed Xubuntu 10.10 on my netbook with no problems. Almost as good as Ubuntu, but lacking in gnome's customization tools.

---

### Post by Dr. C on 2010-10-24
The system an older P4 3.0 GHz, with 1.5 GB RAM, Nvidia 7600 GS 512 MB AGP Graphics, 250 GB IDE hard drive and yes a 3,5in floppy drive. Fresh installation. By the way this is not the first time that hardware that does work, will work in a subsequent version of Ubuntu.

The good: 
Maverick Installed without any problems and recognized a TOSHIBA USB sound device that did not work with previous versions 7.xx and 8.xx of Ubuntu. Nouveau graphics works great. 

The bad:
Installation of the Nvidia propriety drivers fails. After reboot one gets a terminal screen. This is really an Nvidia and not an Ubuntu problem since the drivers in question are proprietary. 

The ugly:
Floppy drive support. This has been a mess in Ubuntu for a while. In an attempt to solve problems with computers with floppy controllers and no floppy drives, floppy drive support has been broken. In lucid this could be fixed by locking in to a previous version of udisks. This option is not possible in maverick. I did get a work around in this thread, [http://ubuntuforums.org/showthread.php?t=1599639]("http://ubuntuforums.org/showthread.php?t=1599639"), that solved partially the problem, but the fix is not a full solution. Cannot this be solved by disabling floppy drive support by default and then making floppy drive support an installable option, if a fix for the bug cannot be found?

---

### Post by cejack on 2010-10-24
Two installs from 10.04 to 10.10.  Both working.

I would like another voting checkbox that allows you to choose: "Upgrade - worked but had a lot of things to fix, some of them pretty serious..."  This would be the checkbox I would tick off for the laptop.  The desktop install was easier and would qualify for the "Upgrade - worked but had few things to fix, nothing serious though" voting category.  

One is Shuttle X27 atom processor desktop box.  Just kind of a back-up system with dual boot Win7 and Ubuntu.  Actually leave it in Ubuntu as the hardware seems to work better on it and the video is better on it and is more responsive than Windows 7.  Other is Acer Extensa 4630Z laptop. 

_Pros_

Printer installation from previous desktop edition comes in flawlessly.  Driver installation with new update facility in printers makes Windows look like a joke.  Way easier to install printers in Ubuntu.  Keep up the good work with sensing network printers and local printers and drivers.  Really awesome job on the printer drivers.  

Been real happy about Compiz working with the Intel integrated graphics.  This seemed to be a big problem in the 9.X releases of Ubuntu. The old days of only working well on Nvidia dedicated GPU systems appears to be gone.  Good job on this.  Will have to install 10.10 on some of my ATI graphics systems and see if ATI problems have been solved.  No comment on that so far.  

No actual problem using the upgrade.  In fact couldn't boot on on the Shuttle system using the install CD burned from ISO.  Seemed to be some kind of video problem there.  Couldn't find a solution to this problem so that is why I went with upgrade as opposed to clean install.

My desktop came in pretty clean on the laptop upgrade.  Not much problem with the Screenlets and what not...

[IMG]https://files.me.com/cejack/njdjth[/IMG]

_Cons_

1.  Wireless was a major pain in the !@#$!$.  Had to download RaLink RT2860 drivers.  Won't bore you with the details but it involved a pretty detailed fix.  No big deal here as I ultimately got this up and running.  But it is obvious that adding wireless drivers for Ubuntu is much more involved than Windows 7.  

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

2.  VMware Workstation did not come through cleanly on the new kernel and would not run after the 10.04 to 10.10 upgrade.  Needed recompile via this script:

[http://www.apleben.com/2010/10/vmware-workstation-7-1-patch-for-linux-kernel-2-6-35/](http://www.apleben.com/2010/10/vmware-workstation-7-1-patch-for-linux-kernel-2-6-35/)

Please note that I had to run this script with root privileges from the root folder.  Not exactly well documented even on the web page that presented the fixed script.  

3.  Google Chromium and/or Google Chrome will require you to remove libmoon library or install newer pre-release version 3 library from Novell Moonlight page.  

[http://www.go-mono.com/moonlight/prerelease.aspx](http://www.go-mono.com/moonlight/prerelease.aspx)

You will get Chrome/Chromium crashes / inadvertent closing behavior while surfing until you apply this fix.  Did not impact Opera or Firefox.  

Totally had me stumped on this one.  Some nice recent posts on these forums helped me figure this Google Chromium/Chrome problem out.  

My particular problems should be pretty common and you think that the upgrade crew would address this stuff if they did some decent testing.  However, not too bad overall all things considered and those with sufficient knowledge can figure this out. 

For me the installation CD was a problem.  If I had done a clean installation and re-installed the applications from scratch I probably wouldn't have had the VMware or Chromium/Chrome problems.  Probably would have still had the wireless drivers issue.  

Using an Acer Extensa 4630Z.  Best $389 I've ever spent on a notebook.  The hardware is pretty good with upgrades to Windows and Ubuntu.  

Oh, I do like the new Grub with its Boot Manager. Not new to 10.10 but new since 10.04 and seems a bit more friendly with multiple boot installations.  Have less problems with Grub than Windows boot manager.   

My recommendation is to stick with 10.04 LTS if you don't want to have as many issues and don't have time for any BS.  If you like to spend a little time on these forums fixing things, then go with 10.10.  Then you know you are running the latest and greatest and it kind of gives you a warm fuzzy feeling.

---

### Post by LexLux on 2010-10-25
Upgraded from 10.04 to 10.10 and had NO PROBLEMS. 

I only got a message repeatedly: "process 16982: arguments to dbus move error () were incorrect, assertion "dest) ==NULL || !dbus_eror_is_set ((dest))" failed in file dbus-errors.c line 280 This is normally a bug in some application using the D-BUS library."

Cheers and happy

---

### Post by EriCr on 2010-10-25
Hi all,

I have dipped in and out of Ubuntu over the last 2-3 years. I installed Ubuntu 10.10 - the Maverick Meerkat asa dula boot option on two laptops here at home. Both went flawlessly.

Laptop one: Acer 6935G Intel Centrino2 4Gb ram 320Gb HDD Bluray, Wifi & Blutooth Nvidia 9600 MGT video card.
Had to download restricted driver but it was seamless.

Laptop two: Toshiba Equium A100 147 same result 100% painless:popcorn:

Both lappies have Win7 installed and living happily a a dual boot.

Laptop two is my 16 year old daughters and she loves the Maverick Meerkat.Her only question was will my IPOD work, what about Itunes - Yes and Yes.:guitar:

Only issue I am having in printing. I managed to get my HP photosmart D7460 working 1st time on bluetooth but the wifi/network option is installing but prints getting held. I started with HPLIP but then heard about CUPS - much better.:KS

---

### Post by tfbiii on 2010-10-25
Installing 10.10 Edubuntu on a gateway M275 tablet and things have been less than smooth...

First attempt from DVD the installer crashed toward the end, I would say 90% through. Same thing happened ont he second attempt as well.

I then manually partitioned the HD, and I was able to get to 100% and a successful reboot and login. Sytem appeared to be using the HD 100% of the time for about the first 2hours after reboot and log in. It would also take very long pauses as if it we processing something (10-30 seconds before menus would pull down)

Being a LONG term Windows user, I started trying to convert my WinTel troubleshooting into Linux Troubleshooting. Found the system monitor and it showed all resources well within limits, 1.8 ghz cpu spiking to about 30-40%, 1GB RAM at 25%, and 4GB of swap not even being used.

Ran the system Test and it seems sound drivers are beat, a driver issue would make sense and could easily cause system-wide issues. ATA seems solid. DVD playback bites.

Broadcom WiFI drivers were a "secure" download and install, but seem to not be working. Tells me "firmware" is missing.

I then tried the System Update - it downloaded about 78 patches and seemed to hang while unpacking a linux patch (of course I did not write the name down). I let it sit on that over night and then force rebooted it this AM when it was still at the same screen. I then sat looking at the Ubuntu loading screen for about an hour and left it that way as I went to work.

Less than stellar.

I know this is not new harware, but it's solid and the only issue I had on the Windows side was finding the right WiFI driver since Gateway sold support for these systems to a company that folded a few years later.

I am trying to go the Edubuntu route to give my son something moire than a DVD player with a pen.

Anyway, that's where I stand right now, I am pretty sure I will be running the install one more time when I get home and another problem will just make me choose a different Distro.

Fred

---

### Post by rabiddingo on 2010-10-25
I did one upgrade on my Acer, one fresh install on a laptop and then one dual installation with Windows. All of them worked easily and well.

---

### Post by pseudocube on 2010-10-26
Did an upgrade on my Dell Dimension 3000, my resolution was all messed up. :P I made a thread [here]("http://ubuntuforums.org/showthread.php?t=1583825"). I did a fresh 10.04 install when I couldn't fix it, and a couple days ago I downloaded the .iso and burned it to a disk. I tested it out, and since the resolution was still screwed up, I didn't install.

Another issue I don't know still exists, but did when I tried the beta: in Supertux2, objects flicker rapidly, and when I move Tux it gets worse to the point that I can't see what I'm doing.

I hope these issues will be sorted out. :)

---

### Post by nlsthzn on 2010-10-26
Was fully intending on sticking to 10.04, until I borked something with playonlinux trying to get Starcraft 2 to work, decided to re-install and try out 10.10 while I am doing it... and wow, it is very polished, I am very impressed!

---

### Post by Hooman on 2010-10-26
I did a fresh install with my x201i, but I still have something I can't fix now.
[I can't enter gdm!]("http://ubuntuforums.org/showthread.php?t=1603727")

---

### Post by alanmoore78 on 2010-10-26
I tried to upgrade a 10.04 Wubi install to a straight 10.10, and needless to say, it did NOT work.  So I bit my pride and lost my bookmarks/cookies and went with a straight install.  All my important stuff was saved in my Windows partition anyway.  Oh, and I lost a parts list for a computer I wanted to build so, heaven forbid, I have to do that again, that's so much fun...

10.10 install went 98% flawlessly.  I did have a small issue with the Software Center where it didn't want to install non-Canonical things like Skype and Adobe plugins/Reader/AIR.  After the reboot Update Manager wanted to do, all of that worked fine.  The only minor issue I'm having now is I can't click on SOME dropdown boxes with my mouse.  This isn't much of a problem because I generally use the keyboard and tab through when entering forms anyway.  But say, on the wattage calculator on NewEgg, I can't open the dropdown box to see different choices for the processor or video card or whatever.  This may be a CHROME issue.  I haven't even tried it in Firefox yet, nor have I tried to look for a solution.  It isn't bothersome enough to bother me.

Here's my only complaint.  I was on Groupon looking at a deal and I clicked the Map link and it took me to Bing.  Bing proceeded to persecute me in a popover window about not being on a Windows computer with Silverlight.  They told me to COME BACK when I was on a Windows computer.  From here out I will simply highlight addresses, search in Google, click the Maps link and let it find it for me.  That was so rude!  OMG, like, totally!

I also took the opportunity of having a non-toddler abused Live CD on hand to install 10.10 onto my daughter's severely* beat-up eMachines laptop.  The poor thing ran Vista Home Basic with 1GB of memory and a single core Athlon 2650e.  IMO, Home Basic is more or less a trial version of Windows.  It's slow, it won't let you do anything, and everything you do on it makes you want to upgrade to Premium.  Cold booting into a desktop took EIGHT MINUTES.  It took another 6-7 minutes for Yahoo and all that to show up, let me click on Chrome, and bring up Google.com which is PATHETIC.  I used to have a 600MHz Celeron with 256MB of RAM running XP Pro that was faster than that.  With 10.10 installed the same process takes 2 minutes and 15 seconds.  That's THIRTEEN MINUTES shaved off the time to boot and get a webpage up.  Unbelieveable!

When we finish painting our living room, I'm putting 10.10 on my son's eMachines desktop.  Another used $200 computer, but this one I spent $25 on eBay and gave it a 4450B processor, so it's quite a bit faster.  It has XP Home now and as fast as it is, I bet it'll be faster in Ubuntu and his flash games will be better and it won't take so long to boot, either.  With 3GB of memory and 160GB of hard drive space, his only bottleneck now will be the graphics card (6150SE integrated, ew) so I'm watching CL and eBay for a PCI 8400GS/9400GT/9500GT or something.  Most video cards these days are Express x16 but this computer has only PCI and PCI Express x1.

Next on the Microsoft chopping block is this eight-year-old Dell GX260 sitting next to me.  It's got a whopping 1.8GHz single core P4, 2000SP4, 2GB of RAM (the only part of the computer worth keeping IMO), a wheezing 20GB HD, and a CD-ROM.  Wow.  But I bet it'll run great on 10.10 and maybe it will make a good HTPC with say, Mythbuntu and a big huge hard drive?  My wife would LOVE a way to record all the episodes of NCIS that keep coming on Sleuth, USA, and CBS.  It might be cheaper to spend $80 on this computer for a hard drive and some cables than to spend $150+ to get all the season box sets.

I have an old Mac IIsi in the closet but I think it deserves to keep System 7 on it.  On floppies, even.  With a monochrome display.  

*the right hinge is loose and it is missing over 1/3 of the keys on the keyboard...it's THAT bad but when you spent $200+ on a used laptop and the 11-year old doesn't take care of it, you make her use it like it is 'til she appreciates what she has...then we'll get her something nicer, dual-core, no missing keys, etc...

---

### Post by haretic on 2010-10-27
I have used many flavors of unix / linux over the years and came to stick with Ubuntu on my personal systems. Currently I own a Dell M65 (running win7) a Dell Lat D630 (U 10.10 now:) ) and an older Tosh Satellite had 8.04 now needs new HD. 

A nicety since my upgrade today is that the graphics have vastly improved. The images are much clearer and vivid than  previous releases, system is noticeably quicker processing and moving around.  Just want to say great job guys this release has been a good move for me.

:KS:popcorn:

---

### Post by jackdale on 2010-10-27
New install (had problems with 10.04 due to messing up upgrade from 9.10 - user error - so I decided to start fresh).  No problems at all.

My network card works faster than b4 and now much faster than with my W7 partition (which i sometimes have 2 use 4 work)

boot & shutdown are now even faster and leaves OS X 10.6.4 for dead on similar hardware specs.

Very happy
:)

---

### Post by ophie99 on 2010-10-27
Ubuntu worked great but it hosed my grub for the windows partition. It was only bad because I needed that for work. 

As far as I could tell the 8 series bootloader was better but overall I'm really enjoying MM

Here's the link that I used to fix the grub /windows/xp/vista chainloader for Ubuntu 10.10 friends- hope it helps

[http://grub.enbug.org/ChainLoadWindows](http://grub.enbug.org/ChainLoadWindows)

---

### Post by wolfe on 2010-10-27
Unable to use 10.10 as I am affected by this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

Also, my i7 at 4Ghz feels incredibly slow with 10.10.  I'll be sitting this release out.

---

### Post by thelaw on 2010-10-27
Was running Hardy but installed 10.10 "fresh" - well, pulled the old hard drive and put in a new one:

Dell Latitude D505.

1) Would only boot to a "grub" screen - a re-install took care of this.
2) Unable to control video - setting xorg.conf to "intel" sort of fixed this - still it is buggy but it is documented as such
3) Wireless doesn't connect using WEP (haven't tried anything else, yet)
4) Cisco VPN client will not install
5) 'patch' command does not work (required for above Cisco VPN Client install).  Running 'patch mydiff.diff' just hangs
6) Rebooting causes desktop effects to stop and I always have to reset the display.  I am using dual monitors - well, a big desktop monitor plugged into the docking station as a cloned screen
7) Clicking on links in Firefox sometimes I have to 'F5' for the link to work
8) mail-notification for Evolution does not work.  Installed another mail-notification program but was unable to configure unless booting to a gnome desktop (I use KDE)
9) booting to laptop without second monitor requires booting to root prompt and copying a backup xorg.conf and rebooting

---

### Post by jurialmunkey on 2010-10-27
My ethernet wouldn't work properly after an upgrade to 10.10. No Samba shares. Network manager reported no available connections. There was a connection, however, as I was able to access a very limited amount of webpages (which was entirely random, I was able to access google about 1 in 6 times I tried after logging in).

It turns out that the upgrade installs connman, which conflicts with the already installed network manager (which is finally in a state which works well on my system). So I had to remove connman and, after a reboot, everything worked fine.

I also had a problem with the gtk2 rgba module preventing nautilus from displaying the wallpaper.

The network issue is a BIG deal. It was entirely frustrating as I wasn't able to access the net to fix my problems. Although not nearly as bad, it reminded me of the time I updated to XP SP3 and was sent into an endless reboot cycle. Anything that involves going to another computer to try and find a fix for is an utter nightmare. 

Nonetheless, I only had those two problems. At least my NVIDIA and X-FI cards don't cause me any headaches any more.

---

### Post by Rei Malebario on 2010-10-28
When I upgraded from Karmic to Lucid, it went so badly, I ended up backing everything up and installing Ludic from scratch.

This upgrade went flawlessly. It was brilliant.

---

### Post by nlsthzn on 2010-10-28
> **Rei Malebario said:**
> When I upgraded from Karmic to Lucid, it went so badly, I ended up backing everything up and installing Ludic from scratch.

This upgrade went flawlessly. It was brilliant.

....and then you decided to install Maverick because that is what this thread is all about :p

---

### Post by Lancro on 2010-10-28
I upgraded from 10.04 wubi to 10.10 wubi and then I converted wubi in partition install, and everithing is ok but 2 translations issues, but I can understand them, they are in english that isnt my native languaje, but my built in web camera microphone starts working, thats why I made the upgrade, I saw it working on a live usb stick, the splash screen when ubuntu is loading, the previus one to the login screen, is not working as well, it only puts "Ubuntu 10.10" in plain text, and it displays the apache2 start command, at shutdown the same, commands, but it works fine, so Im happy with the upgrade.

---

### Post by janpol on 2010-10-28
Installed Maverick desktop edition (64 bits) on my desktop and netbook edition on my Asus eee and both worked flawlessly. 

I also plugged an Edimax USB wifi adapter and worked right out of the box :D

---

### Post by mvblair on 2010-10-28
I detailed some of [my problems upgrading here](http://ubuntuforums.org/showthread.php?t=1607117) (I incorrectly wrote that I upgraded to 10.04, but I really tried for 10.10, I think). Long story short: when my computer restarted after the upgrade, my screen wasn't getting a signal or wasn't getting any pictures. I guess some people wrote that there are work-arounds, but I'm not good enough with computers to do start messing around with that GRUB stuff. Maybe in a few weeks I'll try again. For now, I just said "to heck with it" and reinstalled 9.04, losing all my data that wasn't on my key drive.

---

### Post by Caliga82 on 2010-10-28
Before i start to lament, let me say that i DO like (K)ubuntu, but  installing 10.10 really was a little bit frustrating from a user  experience point of view. The last thing now was to look for an  appropriate place to post this, and I'm not really sure I found it.  (Because I'd appreciate if some of the Natty Devs would read this)
I actually switched from Gentoo about a year ago because I was tired of doing everything by hand...

**Installation** (Kubuntu 10.10)
First thing that annoyed my was that my **internet connection** was not detected. Not too surprising actually, as i don't use **DHCP**.  However PLEASE let me help you out if you can't detect it! Let me give  you the IP of my router (which is simply 192.168.0.1) and let me set my  own.

Next step: **partitioning**
Why does it ponder for a  few seconds on everything that I change in the partitioning layout? I  had an empty SSD which i partitioned and set some mount points. It was  incredibly **slow**.
I also had a HDD with existing partitions.  (reiser, ext, swap) When i set a mount point for my existing partitions,  wouldn't it be nice if that dialog would **suggest** to mount it with the file system that was **correctly detected** before?

**Missing components**
Installation itself went smooth. Then, first time on the desktop, i was informed that some components (**localization** and probably updates?) could not be installed because I had no **internet** connection. Yay! So I had to keep this dialog open to not forget the steps I need to do after configuring my internet.

Configuring **internet**
I actually think the **network manager** has been improved, but it still has its annoyances.
When I set my IP and that of my router PLEASE don't bother me to open the **wallet**!  There is nothing secret about that data! And because I made that  mistake in past (had to enter my password every time to open the  internet connection), I looked hard for a way to avoid that. After some  time I discovered the setting "**save passwords in file** (unencrypted)". Well, as said, there is no password, it's just an IP!
Also,  I don't consider it the most elegant method that internet only connects  when I log in to the desktop. I noticed the checkbox "**system connection**"  (Systemverbindung) which was grayed out. There was no hint what it does  or how to activate it. But I guess it's what I would want. I actually  event tried to sudo the system settings, but it stayed gray.  Nevertheless, I was online...

**Missing components**, part II
I  could then go back to that message and install the missing  localization. After that I had to enable it manually in the system  settings. All that just because i can't configure the network during  installation!

**Installing my default set of applications**

**Thunderbird/Lightning**:  As I had copied my profile from the previous installation, TB noticed  that I probably want the Lightning plugin and tried to install it, but  failed as before, because there still is no official build for 64 bit  available. Please! Just put it in the repository.

**Amarok/Phonon/mp3**
It's so nice that **Amarok** now actually tells you why it can't play. At least if you notice the small popup that blames **phonon** and then goes away. Why does it not have a **FIXME**-button?  I forgot what the other backend was, so I had to google for it and then  install it. Well, Amarok stayed silent. More googling... Oh, I still  miss the **mp3** support... more installing... Finally it works. Please make it simpler.

**DragonPlayer/VLC**
As **DragonPlayer**  still is the default app, I expected some improvements. Put a DVD in.  Fail. As before, DragonPlayer doesn't play anything and doesn't even  bother to tell you why.
Installed VLC. Fail, but at least not silent. Googled the error message. Oh, I don't have **DeCSS**. Didn't I install **restricted extras**? Oh, it's not part of that... well... Ok, works.
Should give DragonPlayer one more try. Fail. It's just **useless**.
But  VLC has its problems, too. After I watched a DVD for more than an hour,  it had bloated 3,8GB of my memory and started swapping so heavily that I  could not kill it before the OOM(?) killed my X session. Also, VLC  often drops a few seconds (reproducable). I used to blame it on my  drive, but DragonPlayer doesn't have that problem if only you manage to  make it work. Would you please make DVD-playing less cumbersome?

**Cups/Adobe reader**
By now it should be obvious that I want unfree stuff like **mp3** and **acroreader**.  Why is it so complicated? Why can I not enable that during  installation? Had to google again to find out that I have to enable a  package source. Why I need acroreader? Because it prints my pdf's the  way I expect it. And it handles forms. (Also I like the tabs actually :)  )
Then I set up my printer. Acroread could not print. Why? Exactly  the same issue as in the previous Kubuntu releases: Long standing bug  that writes a wrong line (JobSheets) in the printers.conf when the  printer is installed.

**Booting**
**startupmanager** is a really nice package, but probably nobody knows about it. Could be  integrated in the system settings or the installation process. Who wants  to wait 10 seconds?

I admit the problems could be more severe. But flawless looks different to me.

---

### Post by seenthelite on 2010-10-29
Installed Kubuntu for a mate, and was pleasantly surprised with the detection of the Broadcom Wireless card, no extra downloading just put the wpa key in and it's working. Everything seems fine. Ubuntu just gets better to install and use with each release.  :)

---

### Post by tbuser on 2010-10-29
I upgraded one machine and decided thereafter to fresh install. Most features worked out of the box with CF-29 Toughbooks. I liked the fact that the hot-keys just worked. Touchscreen worked but needed a tweak. Had an issue with models with 855GM chip sets. The touch-pad pointer disappeared. Fixed that. 
To save re-typing and associated errors look at my thread [http://forum.notebookreview.com/panasonic/524581-ubuntu-10-10-toughbook-version.html](http://forum.notebookreview.com/panasonic/524581-ubuntu-10-10-toughbook-version.html).

---

### Post by darkhelmetchris on 2010-10-29
For my situation, I chose a fresh install of Maverick Meerkat 10.10 instead of an upgrade, formatting my "/" partition and keeping my "/home" partition in tact.  This made it very close to an upgrade, but giving me a clean OS partition.

The only trouble I had was that metacity didn't start automatically, and I had to remove the metacity.desktop file in my user profile.  After that, things were very nice.

---

### Post by gtardini on 2010-10-29
To be fair: I had only ONE problem, but this proved a knock out: the X-server. Despite several suggestions from this and other fora, it never worked. 10.04 was ok, instead, although in low graphics mode. In principle I like automatic upgrades, but I hope THAT aspect (xorg & c) will never be "upgraded" to the Maverick default.

---

### Post by KaYnemO on 2010-10-29
Upgrade from 10.04 Worked flaswlessly

---

### Post by cwwilson721 on 2010-10-29
I did a 'upgrade' via the Desktop-64bit iso. Ran the Startup Disk Creator to make my 8GB USB stick Live, and booted that.

I chose the "specify partitions" option during install, and selected my current 10.04 '/' partition to install to. After it was done, the system rebooted, and it worked fine.

Just like a 'clean install' I had to install my Nvidia drivers, update the system, and add-in my old software (wine, Skype, etc). Not formatting the drive saved my '/home', and all the settings I've had. 

So far, no issues at all. Total install/update/configure/reinstall of packages/goofing off was ~1 hr (slow internet...sigh)

---

### Post by cwwilson721 on 2010-10-29
> **Caliga82 said:**
> [COLOR="Red"]First thing that annoyed my was that my **internet connection** was not detected. Not too surprising actually, as i don't use **DHCP**.  However PLEASE let me help you out if you can't detect it! Let me give  you the IP of my router (which is simply 192.168.0.1) and let me set my  own.[/COLOR]Actually, if you would have booted into the Live system first ("Try Ubuntu 10.10"), you could have set the network connection manually. (Rt click the NetworkManager icon, edit connections, choose your connection, and edit). 

After editing that, run Firefox, and make sure it works (Or open a terminal, and 'ping [www.google.com](www.google.com)'). If the network doesn't work after that, you may have to rt click the NetworkManager again, uncheck "Enable Networking", then do it again to enable it. Retest network, make sure it's working.

THEN start the install by double clicking the "Install" icon on the desktop.

You would have avoided a ton of hassles.

---

### Post by Primefalcon on 2010-10-29
I did both, on separate machines, had no problems with either at all

---

### Post by wilsonpenha on 2010-10-29
I've upgraded from 10.04 to 10.10, I thought it went OK, but today I got a partial upgrade and asked me to removed unused things, then after reboot the system my nightmare got over me, my machine seems very, very, very slow, like it was a K6 II, it is taking pure much time to do anything, like type this comment , keyborad take a life to respond, anything I try just take a life to happen, now for example I am waiting for 10 minutes to my lotus notes to open, I wish to not have done this upgrade, I trusted bcz. 10.04 is fast like 10,10 is slow, I have done a lot things over my 10.04 64 bits, to make all my sttufs to work, and now I have to reinstall everything, it is sucks.

Anyone got 10.10 slow as I did?
How did you fix it?
There is anyway to fix?
Only a reinstall would fix it?
Can I truts to reinstall 10.10 over itself, would that keep what I have installed at all?

Or the only things I can do is to turn back to 10.04 from the begin.

Pls help.

---

### Post by Quadunit404 on 2010-10-29
Upgrade - Terrible. Screwed up my computer and made it nearly impossible to use right. It's the whole reason why I came here in the first place. A reinstall fixed everything fortunately.

And of course I backed up everything first, who wouldn't? :wink:

---

### Post by Thebear on 2010-10-30
have an Asus eee 1201hab previously running windows cp and ubuntu 10.04 through wubi.  tryed to upgrade through wubi, grub would not load. Tried to load install maverick through wubi - managed to get opening page but no mouse or keyboard to input commands. 
finally did fresh install with live Cd sacrificing windows - taking a chance that my printer would work with maverick as well as my logitech USB headset.  so I must have missed somehting in the set up but Gnome mnaager does not run, only the password key, so I can't choose unity.  So mow have maverick meerkat without unit and can't use my logitech headset and there seems to be no good driver for my Canon mp 250 printer. 

Can someone refer me to a thread that may help.

---

### Post by GeeLo on 2010-10-30
Bare metal install of 10.10 went great on my Pentium 3, a faster response them I thought in regards to gnome. I've posted about this system before, it has a 10 GB hard drive 450MHZ Pentium 3 cpu and only 256MB of ram. Very impressed with Ubuntu 10.10 on that system.

Upgrade from 10.4 to 10.10 went well on my single core 1.7 Ghz Athon with 2 GB of ram and 160 GB sata hard drive, however I lost the graphic acceleration. I have a NVidia Geforce FX 5200 x8 AGP card that was using the 096 nvidia driver. Funny thing is that I can use the 173 Nvidia driver and "have" graphic acceleration, but the resolutions are max at 640x480. I cannot set a fixed monitor modes in xorg.conf file because the new xorg server gives an error that I cannot do so. I know there is some sort of driver "mod" out there, but I think I'll revert back to 10.04 LTS.. for now.

I'm "not" upset because of this. I am very happy with the support of the community and the drive of all of the open source folks who have made Ubuntu a very great looking distro. I also heard that Nvidia is trying to update the Nvida 096 driver so it will work again.. and that would be a great holiday gift to me and other folks that have run into this issue.

---

### Post by Techdude27 on 2010-10-30
Upgraded Laptop from 10.04 ("Lucid Lynx")  to 10.10 ("Maverick Meerkat")  went smoothly only problem encountered was with Virtual Box 3.2.8 - Windows 7 Virtual Machine missing USB Support. Problem was quickly corrected by removing VB 3.2.8 and installing latest version of VB  3.2.10 for Ubuntu 10.10.

Toshiba Tecra M5 -    Intel Core 2 Duo T7200 / 2 GHz -  2GB Ram -  80 GB HD

---

### Post by thebarisaxkid on 2010-10-30
The only problem I am currently having is random freezes.  I have noticed that it keeps happening when I am viewing a youtube video for a prolonged amount of time, but it may not necessarily mean that it is a problem with the O.S.  It is more likely that it is a problem with flash.  I am currently trying out "Square Flashplayer" instead of the one that comes with the Ubuntu-restricted-extras package.  The only problem I have now is figuring out how to "attach" this plugin to chrome.  But then again, it could be a problem with the OS.

Link to my thread about this:
[http://ubuntuforums.org/showthread.php?t=1608972](http://ubuntuforums.org/showthread.php?t=1608972)

---

### Post by Ray Mac on 2010-10-31
I did a clean install on a new 1.5TB WD green drive (WD15EARS). I first used a bootable WDIDLE3 disk to turn off the auto head parking. Next, I installed Ubuntu 10.10 using the 32 bit desktop disk. When I rebooted, I was greeted with the usual blinking cursor. I then used RESCATUX to install grub2.   

  The disk starts at sector 2048 so that problem was fixed.

dd if=/dev/zero of=/tmp/output.img bs=8k count=256k  shows a speed of just under 100mb/s which is about the max I can expect with this motherboard.

---

### Post by xpod on 2010-10-31
This particular round of upgrades, when i got round to them a few days ago, had been my first where i`ve not already had the development version running on the second drive in my Desktop for at least a month beforehand. In fact, i have to admit that this upgrade has been the first that came & went with me being just too busy to even realize that 10.10 time was here. :oops:

Needless to say that all 5 upgrades that needed done went without a hitch. The main drive in my Desktop has been going through the upgrade procedure now since about 8.10 without any major issues.

Just one of the lucky ones, obviously.:)

---

### Post by masinger53 on 2010-10-31
I did the synaptic upgrade (dialog saying new version available, etc.); everything appeared to be fine initially, but I didn't really test thoroughly.  

Current issues:

No sound - have no clue why, as it "just worked" in Lucid, and everything appears to be fine, e.g., device is there, etc.

Laptop goes into hibernation whenever I plug/unplug the power - new behavior never before seen.  Have had Ubuntu dual-booting on this lappy since Dapper.  I should have just done a fresh install, but hey, this is Ubuntu, right?  It should just work =)

Chrome is funky - can't get flashplayer to run, even after doing a manual with the tarball.

Same issue for Firefox.

Contemplating a re-partition & fresh install or possible rollback to 10.04 LTS.

---

### Post by masinger53 on 2010-11-01
Update on issues:

Sound works in some things, but not others -- e.g., system sounds -- have no clue what changed, other than Flashplayer (see below).  

Still have no idea on the hibernation issue, but haven't researched it.

Flashplayer fixed:  Was poking around in Synaptic & decided to try to install it from there.  For some reason, this worked and it is now functioning in both Chrome & Firefox.

New issue found:

GRUB has disappeared the optical drive (again) -- this is a known, albeit obscure, issue with some BIOS/optical drive combinations and GRUB.  Had previously used the workaround of installing LiLO, but to my great surprise, I was able to use GRUB again with fresh install of 10.04.  So it seems it's broken again in 10.10.

---

### Post by ebbr.bugs on 2010-11-01
external usb storage devices stopped working.
seriously considering windows 7 after the last few upgrades have all been disappointments.

---

### Post by DanLeto on 2010-11-01
The install went just fine the problem arose when I tried to boot into Windows XP and it wouldn't work, for some reason Ubuntu changed /dev/sda*/ to /dev/sde*/ :(

---

### Post by extremejosh on 2010-11-02
I did a fresh install and so far i love it everything works fin for me just have a little graphics driver problems to work out but im sure i get it all in order soon

---

### Post by Nightstrike2009 on 2010-11-02
I upgraded from 10.04 to Ubuntu 10.10 and wish i hadn't bothered on first appearance musc more stylish and smarter even though minor tweaks apparent, massive video problems with it (Even caused me to leave linux completely for a brief period, seeking an alt. distro before returning to Ubuntu).

I now dual boot windows and Ubuntu once more and have returned to Ubuntu 10.04, I should have known better really as in my experience the x.10 releases are "flaky prototypes" of what to come in the next "stable" x.04 release. :-(

PS: I also recieved "Missing hal file" error when trying to dual boot 10.10 with windows xp on boot choice loader.

---

### Post by Damcevski on 2010-11-02
Since 10.04 worked very well, I upgraded to the premature 10.10 ..
Bad idea. [-X The system was constantly rebooting on resume after standby (worked-around anyway), got random scattered audio and video playback, heavy load figures and impossible flash support ..

.. finally, a fresh install got me back to 10.04 LTS

Use Ubuntu, careful with the upgrades  :wink:

---

### Post by The Flying Penguin on 2010-11-02
I downloaded 10.10 and made a live usb stick using 10.04's startup disc creator. From the time I restarted my Asus ul30vt to the time I was booting into a working desktop was around 8 1/2 minutes. I have never installed an OS so fast in my life. Windows, eat your heart out :P

The trackpad didn't work perfect out of the box but I was able to get it working in minutes using the guide in the ul30 owner thread on this very board.

I installed it on my Fujitsu P1610 tablet too. Everything except the touchscreen and related buttons works perfectly right out of the box. Tablets can be rather finicky though so I can't hold the fact I have to manually get these things working against Ubuntu.

Those are the only two machines I"ve installed it on. I think I'll keep the rest of my machines on Lucid since its LTS.

---

### Post by vicmate on 2010-11-02
Hi Ubuntu Users,

I recently bought an Asus EeePC 1000H, one of those tiny netbooks, well it came with windows xp and it really sucked, the pc was slow and kept giving me the freeze so I did a complete format and fresh install of Ubuntu Netbook Edition. Lucky I had  spare 2gb usb stick lying around, these things don't have cd/dvd drives.

Everything seems to be working fine, I changed a few things tho.
Replaced Evolution mail with Thunderbird
Replaced Movie Player with VLC Media Player
Installed Gimp, Filezilla, XAMPP 1.7.3a, firestarter and Wine.

That's pretty much it and now it runs like a dream.

Thanks

---

### Post by infamous-online on 2010-11-03
Sorry for being so late about my experience, as usual the install went perfectly, it just took a bit longer to install but other than that, no complaints. :guitar:

---

### Post by KingYaba on 2010-11-03
No hitch at all. Best install ever.

Desktop
955 Phenom II X4
770 motherboard
HD 4770 
...

---

### Post by themarker0 on 2010-11-03
I'm a skeptic. I hate updating too. My dads words, if its not broken, don't fix it, don't touch it, don't even plug it in!" and my laptop ran 9.04 perfectly. Now though it started to act up, and i thought why try another distro, Ubuntu is working. 10.10 worked perfectly. I can't ask for better out of the box support! I have more troubles installing windows on it then Ubuntu 10-10! 

Thanks devs, support, and everyone else who has helped Ubuntu. Makes my life easier! Its a perfect ten!

---

### Post by slr107 on 2010-11-04
Installed yesterday, everything seems to be working fine. This is my first linux experience and so far I am enjoying it. Didn't realize there was so much free software out there. My only issues with the install was it didn't install alongside of XP, it deleted it, but I am sure I screwed that one up. And the other was me using a capital letter on the username line, which I think is what led to me deleting XP.

---

### Post by Sean Moran on 2010-11-04
I really liked the new installation routine, for the way it started copying files and THEN asked me the questions.  That was a great improvement!

Also, Meerkat seeems to recognise broadband wifi aircards much more smoothly than Karmic does, but I'm yet to really test that out properly, so all I can say is that there 'seems' to be some development there.

The big gripe that keeps me on Karmic is the same bug as Lucid, on the panel.  Two sections of the panel, the indicator, and the window list, have both got the same drama when I try to "unLock to Panel" and "Move" in that the space available for the right-click has shrunk from around 24x4 on Karmic to 4x2 or somewhere in that region on both Lucid and Maverick. 

It's a simple bug, I realise, but it would be nice to sort it out by the next release.

---

### Post by KernelKludge on 2010-11-04
I'm planning to upgrade my 10.04 home and work systems this weekend. Definitely looking forward to it. However, I have a significant user story to share that compares fresh installs of 10.04 vs. 10.10.

I was asked a couple days ago by a coworker to help install Ubuntu on his brand new Dell desktop. To set your expectations, this user is familiar with Unix on the level of using vi to develop embedded systems software, but less so on managing his own Linux system. I happened to still have a 10.04 CD lying around from months ago and offered the LTS version with the advice that 10.10 was already out. He took the CD with thanks. With encouragement and oversight resizing and moving his corporate Windows partitions, the 10.04 install went smoothly since enough healthy curiosity encouraged him to click the "Advanced" button at the end of the install and he correctly configured the installer for our company HTTP proxy. The 10.04 install was perfect.

The next day he asked about upgrading to 10.10 and I showed him how to enable the upgrade button in the LTS's Update Manager. Unfortunately physical disaster occurred and power was lost during a critical point in the upgrade. The machine booted but was effectively unusable. "No problem," I declared, since he had virtually no investment in the system to this point. I downloaded and burned the 10.10 desktop ISO for him.

The 10.10 installer booted right up but complained about an inability to get to the Internet. Obviously the network proxy wasn't set — unfortunate that wasn't handled. We quit the installer. I checked Network Manager and it confirmed the Ethernet device had a DHCP address. The network proxy was easily remedied and Firefox was able to get to Google. We restarted the installer which again complained about Internet access. I pressed on hoping for the "Advanced" button of previous installers. But not proxy configuration was discovered. FAILURE IMMINENT.

The machine came up on first boot but, predictably, APT was unable to hop the corporate web proxy to get to the repositories. Now I've really been drawn into this poor user's nightmare as I guide him through configuring the cryptic syntax of /etc/apt/apt.conf which he transcribes from his Windows IM client. Fortunately that was the only stumbling block and the system works great. But the user's early impression of Ubuntu is rather poor and would doubtless be far worse were I not available.

The point is that installers are a critical first impression. Don't even suggest expert mode to the crowd this affects the most. Ubuntu is finding wild success beyond the home user where network security is a little more complex, but nothing beyond what Ubuntu has handled in the past.

[LIST=1]
[*] Hiding common network access configuration (HTTP proxy in this case) behind an "Advanced" button is maybe not such a great idea where new users are involved. But at least it was possible previous to 10.10. Bravo.

[*] Invalid complaints (the network worked fine) about problems without providing even trivial remediations (e.g. configure network proxies) creates a bad first impression.

[*] Installing Ubuntu without the ability to identify and install updates and install new, desired packages is a REGRESSION.
[/LIST]

Otherwise, the 10.10 installation is a welcome evolution, particularly starting the package installation before the user has even finished entering configuration information. Kudos.

---

### Post by Merlino on 2010-11-06
I've installed ubuntu 10.10 64-bit on a new laptop. When I got to the screen with the username selection I couldn't figure why the forward button would still remain locked. Then I discovered that although the username was checked with a green "v" it couldn't include upper-case letters. I think that this very misleading even if it's a small issue, please fix the green sign appearing near an invalid camp.

---

### Post by TCHebb on 2010-11-07
I was running Lucid, but I decided to do a clean Maverick install. My disk is encrypted LVM, but I didn't have an alternate CD, so I had to install lvm2 and then run cryptsetup in a chroot. Ignoring that, I thought the install was very smooth and polished.

---

### Post by Nightstrike2009 on 2010-11-07
I was happy with 10.04, but curiousity got the better of me and I upgraded to 10.10 which on first appearance was like a smarter, version of 10.04 but with minor visual upgrades,10.10 installed fine I found the installer an improvement and more intuitive than the old one. Then like other x.10 releases the cracks began to show and I decieded to downgrade back to 10.04LTS. 

Then I heard the 11.04 Unity DE news (on top of the previous Windicator fiasco) which boiled my urine considerably and have now left entirely for Linux Mint 9 (Ubuntu 10.04 based).

Anyhow back on subject 10.10 introduces new ideas and generally appears smarter, but after a while appears to be "partially finished" like other x.10 releases and the bugs rear their ugly heads, basically I prefer 10.04LTS's stability. :-)

---

### Post by lightningfox on 2010-11-07
I removed Ubuntu 10.04 64 bit from my laptop and installed Ubuntu 10.10 64 bit.   

So far everything seems to work except my laptop's integrated camera.


My laptop is a Samsung R580.

---

### Post by kyphos on 2010-11-10
A clean install of 10.10 hangs at "Configuring Hardware...".  Have not been able to get past this roadblock.  Bug reported (#670003). 

[http://ubuntuforums.org/showthread.php?t=1611252](http://ubuntuforums.org/showthread.php?t=1611252)

---

### Post by Old Codger on 2010-11-10
Upgrading from 10.04 Lucid Lynx to 10.10 Maverick Meerkat went fairly smoothly on my MacBook, and I've managed to iron out a few minor kinks like iSight, which has plagued other Mac users. Perhaps the reason the upgrade went well was because the laptop is now in its fourth year.

In contrast, I've had problems with 10.04 and 10.10 on my fairly new iMac. At one point I had 10.04 working just fine and just how I wanted it, save getting the magic mouse to work properly. But when I tried to upgrade to 10.10 the system froze after I shut down and rebooted. As a result I had to reinstall 10.04, but have experienced the same problem after I installed the recommended updates from Update Manager. In fact, I've reinstalled 10.04 several times to see if I could find a way around the problem. Ironically, the last two times I reinstalled, I found that things--like sound--which worked fine before no longer worked--even after I checked the settings and synced them to those on my MacBook.

Since then, I also installed Open SUSE on the iMac to see if it work any better than Ubuntu. The answer is not really. Consequently, I'm beginning to think that Linux is not the best alternative if you're using a [COLOR="Red"]***new***[/COLOR] Mac. To be honest, OSX works perfectly and is very, very stable. I can't say that for either Ubuntu or Open SUSE--at least not as far as my iMac is concerned. There are too many bugs, it seems, and too many tweaks needed to get either flavor of Linux to work. I've spent too many hours trying to learn Linux better and feel strongly that the time could have been invested better doing other things. For the time being, I'll stick with OSX on the iMac and enjoy Ubuntu 10.10 on the MacBook.

---

### Post by 62chevy on 2010-11-11
Installing 10.10 was a night mare. I was installing to virtualbox so maybe that made a difference thou Debian testing (Squeeze) installed just fine to a vm. The installer is the biggest problem no options, none nada zero. I lost track of how many time I had to reinstall because the installer would load all the files but during configure it would freeze. using the live disk to try and fix it was a waist because it never got apt configured. I did get 10.10 to install by clicking off of the only two options, install updates and and the non-free stuff.

The first successful install crashed after doing the updates. The second time I installed the guest additions first then the updates and everything seamed fine.

I've been using Meerkat for about four days now and love the way it looks and feels. Great job!

I left Meerkat running for two days without any problem. Firefox is probably one of the better tests for stability so I left that running over night and sure enough it froze X or made it very sluggish to the point were nothing else would load. I could use the menus and mouse and it would act like a terminal was going to come up but never did. It happened two nights in a row.

I could never recommend Ubuntu to the faint of heart. Mostly because of the installer but also stability is an issue.

I have run Debian testing for years with only an occasional problems.

---

### Post by PGHammer on 2010-11-11
> **rbrick49 said:**
> absolute beautiful upgrade

In my case (as is typical), I clean-installed.

There is a difference this time around, though - this install is all-SATA (Samsung SH-223B optical drive source, Maxtor 6LS200 hard drive destination) and there is a wireless-N USB stick in da mix (Tenda WG311U).  The stick worked from the jump (live media boot detected the stick), which means I did NOT need the (included with the stick) Linux drivers.  So far, the only hardware I have that *isn't* supported right off the bat is my old webcam (Logitech QuickCam Communicate STX).

---

### Post by Cant on 2010-11-12
My upgrade experience was just fine. Everything after that, however, has been a disaster. The only noticeable difference was slight changes to the login screen and a ****ton of random crashes. The computer has randomly frozen at times, Banshee Media Player freezes often when I want to resize a 720p video, increase bass in the equalizer or simply edit the preferences and I remember one particular occasion when the screen went gray. Just out of nowhere-grayscreen. I have had to forcibly shut down the laptop by unplugging it and removing the battery on multiple occasions. Did I mention that the X server crashes randomly? I wish I had never "upgraded" from the ridiculously reliable Ubuntu 10.04.

[/vent]

---

### Post by The Flying Penguin on 2010-11-12
I installed Maverick on another computer the other day. My friend has a Dell X300 (it used to be mine until I sold it to him) and I had installed 9.10 for him a few months ago. Sadly, 10.04 would not work because of an Intel video issue that resulted in a blank screen when you tried to boot into it after installing. I know are ways around it but I didn't have the time to monkey with that for him.

Anyway, he brought it over the other day and I installed Maverick onto it from a thumb drive. The install went flawlessly. Wireless didn't work out of the box but loading the firmware from b43-fwcutter got it working. Best of all, there is no blank screen! Hats off to the Ubuntu team for fixing this issue in the new release.

I didn't get to play around with it much but 10.10 actually seems to run faster on his laptop then 9.10 did. Menus drop down instantly and programs load much quicker. Maybe it's just me but it seems to run extremely well for a laptop with just a Pentium M 1.2GHz, 640MB RAM, and integrated graphics. Since he only has a 40GB hdd its particularly beneficial that virtually all the programs he needs are already installed.

Based how much he liked 9.10 after only a few months of usage, I have a feeling he is going to be in love with 10.10. He was considering having me remove the XP partition when I installed Maverick for him but had me leave it on "Just in case".

Keep up the amazing work Ubuntu devs! Every new version seems to be a notable improvement from the last! I tell everyone about your lovely distro every opportunity I get.

---

### Post by Razor54 on 2010-11-14
I did a clean install on one of my home built desktops, flawless install.  I'm very pleased with 10.10.

On the down side, my old Compaq Presario R4000 was frustrating trying to install the wireless Broadcom legacy firmware and drivers.  I was not able to get the wireless card to work.  Reverted back to XP Pro and wireless works just fine.  BCM device 4320, (legacy), does not seem to be supported in 10.10  LOL talk about legacy, Win XP Pro.

---

### Post by toolmania1 on 2010-11-15
My install was flawless.  I came from a Windows environment that I used for years.  I was really impressed with Ubuntu 10 10.  I started on Fedora a few weeks ago which I liked also.  But, Ubuntu seems a little more user friendly.
 
Also, as I am learning through this and other forums / sites, I messed up and deleted dhclient3 from a false positive when I ran chkrootkit.  So, I had no internet.  Well, I was not stuck.  I put in the live cd and had the internet so I could research.  2 thumbs up to Ubuntu for the ingenious idea :-).

---

### Post by guru Hari on 2010-11-15
Hello. I tried to uninstall Kubuntu using[ code]("http://www.psychocats.net/ubuntu/puregnome") that advice. After I can't boot Ubuntu. I just have Ubuntu 10.10 screen and it stops there.

---

### Post by dstrout on 2010-11-15
I chose the "Install, lots of problems" option, not because I'm having *lots* of problems, just one very stubborn one I'm still working on fixing.

---

### Post by SpyderBite on 2010-11-15
Only issue I'm having since upgrading is that all my Adobe Air apps stopped working. Haven't figured out how to fix it cause I forgot how I fixed the problem after the last upgrade. XD

---

### Post by Sven6210 on 2010-11-16
No problem at all on my EeePC 900a. Then I tried to update my EeeBox B202 which is a kind of media centre in the living room. After the update the EeeBox had problems playing videos. After several minutes the video player closed and it kept closing, even after updates etc.

The strange thing: The same videos played well on my EeePC 900a and I never had is crashing or anything comparable.

Even though the hardware of the EeePc and EeeBox is rather similar I had this problem and I just decided to stick with 10.04 LTS on the EeeBox - and I will probably leave it this way until the launch of the next LTS version as everything works as I expect it for a machine in the living room. Ubuntu 10.04 banned Windows XP which I have been using before - but never wanted it back.

---

### Post by eodrobot on 2010-11-17
I was keen to try Meerkat - I had no joy with 10.04 - for me a backward step after 9.10.  I wish I'd stayed with 9.10 and now have gone right off spending time giving Linux a chance as a pure - no other system OS.

In defence I have Linux Mint 8 as a dual boot on an old IBM Lenovo ( a joy with compiz and docks for fun )

I have a travelling Samsung netbook with win 7 - I daren't molest that with  ~Ubuntu - might have 6 months ago.


On my main grown up PC. Several distros reside safely inside Virtual Box along with a 'Lite' version of Win XP (excellent NLiteOs)  but the limitations are there.

Another, work, laptop, unfortunately has Sis video drivers and this makes 9.10 display crap - upgrading to 10.04 took a day and I had to fanny about with Win XP CD to repair the MBR so I had anything. Tried wubi in the end and got 10.04 running after 3 tries. Then had to suffer the 'interference' screen and long boot up. Left that to settle for 3 months - seemed OK but wasn't happy with it mainly due to drivers for display problem 800 x 600 being the best res available - like viewing the screen through a magnifying glass - forever panning the sliders up, down, left right.

I have an old 128 Mb pendrive with D-SL which works and Puppy on another  1 Gb drive.
So I'm neither 100% newbie nor geek but if it was a Windows problem I'd solve it with Google or call into a local PC repair guy. I don't feel I need that service on Windows but do need on call gurus for Ubuntu who seem to view problems as challenges not irritations.

As you can see I'm not short of hardware ( how do single PC owners get by if they lose their broadband / OS?)

Still giving 10.10 a try - on the Sis laptop -but cannot get it to install either with wubi or from Live CD - even Linux Mint 9 stops (so I daren't try upgraing LM8 on the IBM). I've cloned / backed up the windows disk now and when I have an hour(s) might try a clean Linux only install to an empty hard drive.

Am I optimistic? Guess what - after my 10.10 experience I'm in no rush. Took years to get Linux into any sort of battle ready GUI shape - Ubuntu screwed it for me in two distro releases within 6 months.

---

### Post by debd on 2010-11-17
I was too bored with win xp. so I decided to have a linux OS and got myslf Ubuntu 10.10
loved it at the first sight. main problem I faced was with my Nvidia GPU driver..set it to the res. that I use  in win...the display is fine except that the txts show a litl hazy..not xactly prominent.
else... evrythings great.

---

### Post by Yougo on 2010-11-18
i upgraded last week from lucid. i intended to stick to LTS this time, but little things like sound menu goodness were starting to itch :P

...Hi, i'm yougo, and i'm an upgrade-addict. there. i said it.

while i did get my sound menu goodness, my plymouth broke -again-. the fix i used for lucid doesn't work anymore. i've been all the way through the intarwebs and back, clicked through all the stupid websites that just blindly copy eachothers BS and did all the things that were supposed to get my NVIDIA Gforce and Plymouth to like eachother, but no game :'( **if there's anyone, anywhere, at all, who can tell me anything new or usefull, please, with a cherry on top.**

otherwise, 10.10=good stuff so far

---

### Post by Evil-Ernie on 2010-11-19
Got my Maverick Meercat disc yesterday and put it on my machine that had Karmic on.
 
First attempt failed due to a disc read/write error, second attempt worked perfectly.
 
I am impressed that it recognised me plugging in my 3G phone via USB straight away, I usually have to do some minimal poking around to get it up an running but from the get-go it was found. Same goes for other USB peripherals I have like my DJ control surface and DVB reciever.
 
It's still early days yet but 'out-of-the-box' this release is the most complete yet and I'm loving using Meercat :)

---

### Post by weasel fierce on 2010-11-19
Upgraded and worked flawlessly

---

### Post by ellyka112 on 2010-11-21
> **rbrick49 said:**
> absolute beautiful upgrade
I haven't fully tested every aspect of the system and how I use it but  so far there have been zero issues; Virtualbox works as before, I'm able  to access all Windows shares on my network, existing printers still  functioning, no slow downs or lags while using GNOME.

---

### Post by wkavinsky on 2010-11-22
Upgrading from Lucid left me with a few issues to sort out, unfortunately, I eventually gave up on my upgraded system, **but** I then clean installed, and it was easily the best install experience I've ever had. Post install, had the usual joking around with proprietary drivers, but that's to be expected, and was, otherwise, a flawless experience. Just a shame I can't vote twice!

Oh yeah, the as-yet-unfixed QT4 typo issue (that only affects Maverick) was quite annoying, and damn near impossible to track down the fix for, but once the patch is installed as standard or found during the update process, then Maverick will be by far the best installation of Linux I've used in these past 15 years.

---

### Post by dustinmoorman on 2010-11-23
I'm on a Gateway MX3414 and the install went flawless! (and they have been getting better and better since the past!)

---

### Post by santq on 2010-11-24
After upgrading I had a problem with fglrx (black border issue), but I've installed it manually so I can't really blame Ubuntu for that and I answered *Upgrade - worked flawlessly*.

I was very happy to notice my sound problems - buggy volume slider and one sound driver reserving the whole sound card - are actually gone. Seems like after using Linux for one year, everything important finally works like it should. Thanks to every contributor for your hard work! :)

---

### Post by shy_guest on 2010-11-24
I tried to upgrade, but the upgrade froze in the middle and after several hours waiting I killed it. I ended up with no Grub & a black screen.

Then I booted Partied Magic on a USB key to,wipe the partition & then reinstalled from a CD which went fine..

---

### Post by shy_guest on 2010-11-24
I'd also say that the _**poll needs rethinking**_.

People who have problems with the upgrade are likely to do what I did & install. It's not necessarily an either/or question.

So why it is impossible in the poll to reply to both upgrade and install experiences ?

Perhaps there should be 2 separate polls.

---

### Post by AbeJarano on 2010-11-29
I posted a negative vote, there was no choice for few problems or 1 problem unsolvable, so.   I had two problems.  One is the standard difficulty OSes have with recognizing a high resolution monitor, but I notices when I installed the proprietary drivers it went smoother than before.  I didn't have to edit xorg.conf ;).  But when the 10.10 booted for the first time it started giving errors with most drives in fstab (from 9.10).  It said something like ERROR your drive UUID=xxx... could not be mounted because it is not ready yet or it's missing.  Well I do have missing hot plugs but I've never seen errors during boot.  After fixing the video problem I rebooted and tried "sudo mount -a" and everything on board was mounted.  THe problem has remained though.  THese are SATA2 drives, mostly Windows, one EXT3.  All are AHCI in the BIOS.

THanks, it's nice.

---

### Post by sadohert on 2010-11-30
Thought I'd come back here to report a very positive upgrade experience.  I was still stuck back on 9.04 and was totally dreading this experience, but the package upgrades had finally ran out and there was some other software I needed upgrades for (not to mention the look-and-feel upgrades that I wanted).

I did each incremental upgrade over the course of the day on Sunday with basically no issues (so far).  Some of the services I count on are: NX NoMachine, VirtualBox, medatomb, samba, exim4.  A number of the packages had maintainer config files in "/etc/" that were updated, so I had some conflict warnings that I had to decide on.  For example,  the base /etc/mediatomb/config.xml had changed, and I had made significant changes to it.  The upgrade process warning me about this and I had the option to overwrite with teh new one, or keep my old one.  In any case where I was prompted like this I believe the file I chose NOT to take was still stored in its usual location, but with the *.dpkg-new (or *.dpkg-old) file extension.

The only snags I've had so far were a bunch of stale VirtualBox artifacts that prevented it from starting up, and the permissions on the mediatomb config file were set wrong.  I expect other little issues to still crop up, but I doubt they'll be major.

---

### Post by fatharraxman on 2010-11-30
wonderfully upgraded
:P

---

### Post by julio_cortez on 2010-11-30
I've tried the upgrade on my old machine and for some reason it wouldn't load a graphic environment, again.
It happened exactly like the last time I upgraded, but now fortunately I knew what to do.

Planning upgrade of my main PC tonight, I'll let you know ;)

---

### Post by szczecinmeister on 2010-11-30
Did it work flawlessly ? No
Did you get problems ? Yes
Did you manage to solve them ? No
if yes how ?
 
I installed the desktop beta on a usb drive and it was complaining  about not being able to find the syslinux kernel(?) basically it couldn't load it as a boot device.

I figured it was something wrong with the way I put it on the usb drive, so I used a later  non-beta version and it got to the loading screen - GREAT - but ran into more problems. I could do the scans - and did them they were all fine. Then I went to install it and it didn't install - it just came up with a huge amount of text on the screen. I could use commands like ls, but I was at a loss.

So again, I figured it was the installer, so I downloaded the netbook edition just last night, and now  it's at "SYSLINUX 3.82 2009-06-09 EBIOS Copyright (C) 1994-2009 H. Peter  Anvin et al" and the cursor just flashes.

This was my experience.

~~ Background knowledge ~~
It might help to know...
This is on an Asus 1001px
It had lucid lynx installed. I attempted to use the recovery partition to put windows XP back on, and it seemed to work, brought up symantec ghost etc. Next thing I know grub is confused and I'm left with a netbook-sized doorstop. By confused I mean "error: unknown filesystem. <linebreak> grub rescue> _"

---

### Post by cariboo on 2010-11-30
If you are looking for support, please start a thread in the support forums, this thread is just for experiences.

---

### Post by jamesbrown on 2010-12-01
FGLRX with radeon 4870 after 10.10 upgrade is extremely FUBAR. I have not been able to resolve this so far.

---

### Post by HappySmack on 2010-12-02
DELL Optiplex GX270. 

 Fresh install of 10.10, immediately when the official torrent was posted, worked without a hitch. The only issue was, that I could not get more than 2 bluetooth devices to work at a time. I have to remove one to install another.

 Now as far as the upgrade, expect graphics issues. I _Lost All Desktop Effects_. I have been on a relentless quest for about a week to resolve this. Compiz worked on a fresh install but now doesn't. I tried to downgrade the driver for the Intel 82865G and that would not work (even when I tried to force it). Tried to reconfigure X, no resolution there either. Compiz-icon won't run. BUT, if I try 'compiz --replace' from terminal, I do get some limited effects. I would like to also mention, compiz-check script states all is well and 'glxinfo | grep rendering' responds with yes. Hoping it's just a Xorg.conf issue.

 All in all, works great (just no desktop effects, ANYMORE  :frown:)

---

### Post by Old Codger on 2010-12-03
As I've already posted, upgrading from 10.04 to 10.10 on my MacBook was easy and that I only had to tweak a few things to have things work the way I wanted.

However, upgrading to 10.10 on my iMac has caused numerous headaches, but I persevered. After successfully updating software with Update manager, I then upgraded to Maverick Meerkat online. After rebooting, the system froze as before. This time, I shut down and rebooted using recovery mode and everything works fine there--except it's in the recovery mode.

Since I'm still a noob, I'm still on the down side of the learning curve. I'm sure that there's a simple fix to get 10.10 to boot properly and appreciate advice.

---

### Post by jjpcexpert on 2010-12-03
I installed from CD but from a personal data POV, it's an upgrade. No cdromupgrade.

---

### Post by jjpcexpert on 2010-12-03
> **HappySmack said:**
> DELL Optiplex GX270. 

 Fresh install of 10.10, immediately when the official torrent was posted, worked without a hitch. The only issue was, that I could not get more than 2 bluetooth devices to work at a time. I have to remove one to install another.

 Now as far as the upgrade, expect graphics issues. I _Lost All Desktop Effects_. I have been on a relentless quest for about a week to resolve this. Compiz worked on a fresh install but now doesn't. I tried to downgrade the driver for the Intel 82865G and that would not work (even when I tried to force it). Tried to reconfigure X, no resolution there either. Compiz-icon won't run. BUT, if I try 'compiz --replace' from terminal, I do get some limited effects. I would like to also mention, compiz-check script states all is well and 'glxinfo | grep rendering' responds with yes. Hoping it's just a Xorg.conf issue.

 All in all, works great (just no desktop effects, ANYMORE  :frown:)

Maybe you accidentally disable effects and you forgot.

---

### Post by kryssix on 2010-12-03
Upgraded from 10.04 fine and dandy, just have the "executable bit" issue when trying to run a WINE .exe on another partition.

---

### Post by tehchibipanda on 2010-12-03
All in all, I say it's great. I just can't seem to shut down the computer. Other than that though, no problems!

---

### Post by femi_ko on 2010-12-03
to setup
  clear-all
  set-default-shape turtles "bug"
  ;; randomly distribute wood chips
  ask patches
  [ if random-float 100 < density
    [ set pcolor yellow ] ]
  ;; randomly distribute termites
  create-turtles number [
    set color white
    setxy random-xcor random-ycor
    set size 5  ;; easier to see
  ]
end

to go  ;; turtle procedure
  search-for-chip
  find-new-pile
  put-down-chip
end

to search-for-chip  ;; turtle procedure -- "picks up chip" by turning orange
  ifelse pcolor = yellow
  [ set pcolor black
    set color orange
    fd 20 ]
  [ wiggle
    search-for-chip ]
end

to find-new-pile  ;; turtle procedure -- look for yellow patches
  if pcolor != yellow
  [ wiggle
    find-new-pile ]
end

to put-down-chip  ;; turtle procedure -- finds empty spot & drops chip
  ifelse pcolor = black
  [ set pcolor yellow
    set color white
    get-away ]
  [ rt random 360
    fd 1
    put-down-chip ]
end

to get-away  ;; turtle procedure -- escape from yellow piles
  rt random 360
  fd 20
  if pcolor != black
    [ get-away ]
end

to wiggle ; turtle procedure
  fd 1
  rt random 50
  lt random 50
end


; Copyright 1997 Uri Wilensky. All rights reserved.
; The full copyright notice is in the Information tab.

---

### Post by Fourcultures on 2010-12-03
Two online updates from 10.04 to 10.10:

1) Toshiba Satellite A100 notebook. Perfect update. Very happy.

2) Toshiba NB200 netbook. freezes unless user provides input via trackpad or keyboard. It seems to be a [known bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/638434") which also affects some other types of computer. Possible fix only results in draining the battery faster, so not really a fix at all. Very annoying (but I quite like Unity).

I have three other PCs to maintain - 1 notebook, one netbook and one desktop. Am hesitating to update to 10.10 now due to (2).

---

### Post by Duncan J Murray on 2010-12-04
Hmm I posted earlier that I was pleased with my fresh install of 10.10 over 10.04, but that I had some compiz problems.  To rectify slow and jerky windows, I switched off compiz, but since then, have been unable to re-enable it.  I have finally managed to do this, but compiz is still jerky, and I kinda miss it!

Thinking about rolling back to 10.04 to satisfy compiz-urges.

---

### Post by homeuser1 on 2010-12-04
Dell Latitude D600 laptop. Clean install from CD.

Had three green checks for space, ac power and internet connections to start.  While retrieving files (26 or 62), the installation just froze. Ever since, I have not been able to connect to the internet.

---

### Post by Fourcultures on 2010-12-04
Update re. post #188 : problem fixed. Am now v happy with 10.10. 
[http://ubuntuforums.org/showthread.php?p=10199447#post10199447](http://ubuntuforums.org/showthread.php?p=10199447#post10199447)

---

### Post by sn0m on 2010-12-05
Customised EasyNote MH45, ie wireless card is intel pro. Upgraded fine apart from mplayer seem to take 50% of processing power when downloading Internet radio for me. But not bovered for the time being.
Ta
Koli

---

### Post by illuminate42 on 2010-12-06
Mixed results for me.

Clean install on my old desktop PC worked beautifully and dual boots Win 2K no problem. Compaq Presario 2100 laptop ran 10.04 no problem and 10.10 live CD was fine but can't get it to run when installed on the hard disk. Not found a solution yet!

---

### Post by Fourcultures on 2010-12-07
Update to post #188 - fixed the freezing problem on my Toshiba NB200 fairly straightforwardly. No further problems. Am finding 10.10 great to use. I really like Unity.

---

### Post by Amused2Death on 2010-12-08
Upgrade went fine, much better than the last.. which surprised me as i run satanic over the top. I have not as yet upgraded satanic.

1 problem i have i have not been able to fix.... java seems to be flawed, and a reinstall did not fix that.

This means that browser games, like evony etc will not load. nor will any java scripts on other web pages.

anyone with a clue, or an outstretched finger pointing in the right direction would be appreciated.


Ok, it wasnt java it was flash.... found a thread about flash, so i installed flash aid and ran it, fixed my problem immediately.......

So i need to change my vote to flawless ...... and apologise :)

---

### Post by witeshark17 on 2010-12-08
Upgraded flawlessly. Love the new look, very creative! :KS:popcorn:

---

### Post by 1492 on 2010-12-09
I upgraded from 10.04 to 10.10 and now my built in wireless adapter works and I do not have to rely on a USB adapter anymore. Screen resolution is messed up a bit, though...

**EDIT: **Screen resolution problem fixed, nevermind.

---

### Post by Khakilang on 2010-12-09
I have sold my hard disk which contain 10.04 LTS and install 10.10 on my other 80GB hard disk. Did all the necessary updates and everything works flawlessly.

---

### Post by uRock on 2010-12-09
Just did a clean upgrade of 10.10 on my production machine. I like the ability to throw in the Fluendo packaging during the install. Flash works like a charm. The font looks great! During the install I changed from 32bit to 64bit without any issues, hence the reason I said flash was working great.

It was well worth the wait.

---

### Post by tonypg on 2010-12-12
Having a problem with this install.

[http://ubuntuforums.org/showthread.php?t=1644052](http://ubuntuforums.org/showthread.php?t=1644052)

Any help would be appreciated.

---

### Post by code_linux on 2010-12-14
Just upgraded from 10.04, ran into "grub _xputs" problem, solved using posts on this forum. 
However, an amusing find: Menu>System>About Ubuntu says, "You are using **Ubuntu 11.04 - the Natty Narwhal** - released in April 2011 and supported until October 2012."!!!
(Nothing serious here, but I thought I should share it.)
All other places it says **maverick**, such sources list, etc.

---

### Post by if4124l on 2010-12-14
When I was using 10.04, I installed kubuntu, upgraded, then uninstalled it. At this point Virtualbox don't work. Then I installed Jolicloud(because Vbox don't work), which messed up with grub. Then I decided to format everything(10.10, Jolicloud, and two swap partitions) and reinstalled 10.10. Since then I haven't run into any problems, except some display glitches which was immediately fixed by installing Nvidia driver.

---

### Post by tkzv on 2010-12-14
I am using "netbook remix". The problems during the upgrade were:


[LIST=1]
[*]Aptitude connection settings are not well suited for poor connections. Timeouts are too long, retries are too few. Aptitude downloaded ~100M of DEBs for about a week (I had to restart it manually 3-5 times a day). Correctly tuned wget downloaded the rest 400M in 2 days.
[*]The application for upgrading with one click is completely unsuitable for poor connections. Every time an update broke, it took several minutes to restore the old state, then start the upgrade, then ask for confirmation several times, then fetch the necessary applications again. A "Retry" button would have been very useful. As well as "Don't ask again" checkboxes. I ended up updating via Aptitude and fetching the DEBs with wget.
[*]Lack of space was a problem, but perhaps the easiest one. Can Ubuntu use deltas?
[*]After the update Firefox completely ignores the old settings. History, cookies, bookmarks, add-ons are gone. Looks like ~/.mozilla directory was deleted during the update.
[*]Non-English fonts disappeared from the console (I mean the one accessible from X by Ctrl-Alt-F*). What package is responsible for them now?
[*]Unity desktop in its present state is completely unusable. Menu is unavailable, there's no way to add anything to the top bar, the side bar takes about 1/10th of the already small screen and is also irremovable and unchangeable. There are 4 icons there: Cheese, Firefox, Workspace switcher, and Trash bin. The latter also seems the only way to open Nautilus and run any other application :)
[/LIST]

What cretin decided that Unity is ready to replace anything on desktop?

---

### Post by weasel fierce on 2010-12-14
> **tkzv said:**
> 

What cretin decided that Unity is ready to replace anything on desktop?

Given that 10.10 doesn't have unity as its default desktop, I'd wager nobody yet

---

### Post by uRock on 2010-12-14
> **tkzv said:**
> I am using "netbook remix". The problems during the upgrade were:


[LIST=1]
[*]Aptitude connection settings are not well suited for poor connections. Timeouts are too long, retries are too few. Aptitude downloaded ~100M of DEBs for about a week (I had to restart it manually 3-5 times a day). Correctly tuned wget downloaded the rest 400M in 2 days.
[/LIST]
Try apt-get. See next comment.> The application for upgrading with one click is completely unsuitable for poor connections. Every time an update broke, it took several minutes to restore the old state, then start the upgrade, then ask for confirmation several times, then fetch the necessary applications again. A "Retry" button would have been very useful. As well as "Don't ask again" checkboxes. I ended up updating via Aptitude and fetching the DEBs with wget.You just answered your own problem. If you have a bad connection, then download the alternate installer and use it to start the upgrade or, better yet, just do a clean install.> Lack of space was a problem, but perhaps the easiest one. Can Ubuntu use deltas?Use bigger partitions or do a clean install.> After the update Firefox completely ignores the old settings. History, cookies, bookmarks, add-ons are gone. Looks like ~/.mozilla directory was deleted during the update.Hence the reason for back ups.> Non-English fonts disappeared from the console (I mean the one accessible from X by Ctrl-Alt-F*). What package is responsible for them now?
Unity desktop in its present state is completely unusable. Menu is unavailable, there's no way to add anything to the top bar, the side bar takes about 1/10th of the already small screen and is also irremovable and unchangeable. There are 4 icons there: Cheese, Firefox, Workspace switcher, and Trash bin. The latter also seems the only way to open Nautilus and run any other application :)Unity looks and works great on my Netbook. If you don't like it, then select the standard Gnome desktop at the login screen.

---

### Post by apemax on 2010-12-14
well installing 10.10 (minimal install cd) on my Hi-Grade 8615 went fairly well. no problems at all that i can remember. however it's not going well trying to install it on my IBM R40e using the same method. see here:

[http://ubuntuforums.org/showthread.php?t=1645196](http://ubuntuforums.org/showthread.php?t=1645196)

---

### Post by ningke on 2010-12-16
I saw the same thing (natty narwhal) in "about ubuntu"

---

### Post by wbee on 2010-12-17
Hello,

Having always done clean installs in the past,I copied stuff I did not want to lose,and did the upgrade.

The update was flawless,but allow me these comments.

--Next time I update,I'll get the "alternate" as a torrent,using Transmission. The download took hours and hours and hours.

--Even after "cleaning up",I ran Bleachbit and took out another two thousand files.

--I thank Canonical and Debian for their efforts and the fine operating system. That said,I wonder if a one year cycle might make more sense than a six months cycle?

--((edit) I'm going now to change the information in the left column.:-)

---

### Post by Frogs Hair on 2010-12-17
Two months and seven days of use from a clean installation and absolutely nothing negative to report . 10.10 runs extremely well with my hardware.

---

### Post by revtds on 2010-12-18
I have been runing Lucid for some time, and decided to upgrade to Maverick.  I ran the install, and it seemed to work well, until rebooting, when I got a black screen after the splash.

While upgrading, it gave me an error about fglrx not playing nice, in that it would not uninstall.  I tried to do the same thing in recovery mode, and it would not.  Took most of it out, not all.  I re-installed, then attempted to uninstall, same error same problem.

Did that twice more, no change. Rebooted three times, it finally booted up and ran.  Why, I don't know as I am still a noob at this, or feel like it.

Everything seems to be running well, peripherals, modules, etc.

Today I ran Computer Janitor, and it told me I had 30 some outdated, unsupported OpenOffice files/modules that could be removed.  When I told it to remove them, it wiped out my entire installation of OO that was upgraded with 10.10.

I am extremely grateful for this, as I have printing to do before Sunday AM, and will now begin to re-install, or re-upgrade or something, in order to get a working copy of OO on my system.

To say that this s**ks is so far below grade for what I am feeling, wondering why a cleanup system would utterly remove OO from my system, claiming all of the files/modules were outdated or unsupported.

I am so happy now!!!!!!!!

---

### Post by Austin25 on 2010-12-18
I haven't yet. When I do, I'm gonna go for Kubuntu, though.

---

### Post by Dusenberg on 2010-12-30
Clean install of 10.10 netbook on an old Asus eeePC 701 from USB stick went flawlessly - everything worked! 

I don't like the unity interface but you can simply switch over to the normal gnome desktop so I'm v happy.

---

### Post by Mr_Leo on 2010-12-30
upgraded from 10.04 on my dual core, 64-bit machine. Upgrade went smoothly; most things work well. only problem I noticed after a few days was with miro. Now, with miro, downloading torrents starts slow, then freezes, displaying "starting up". there is a bug report on launchpad, [bug 668615]("https://bugs.launchpad.net/ubuntu/+source/miro/+bug/668615"), but for now my miro is broken.

---

### Post by emtjr928 on 2010-12-31
Upgraded from 10.04. Went smoothly and everything worked as before.

---

### Post by SnickerSnack on 2010-12-31
The only complaint I have is that it took so long.  Big update this one.

---

### Post by Tiler on 2011-01-01
Dell Dimension 5100 3GHz, 64 bit, 3GB, Upgraded Nvidia video card.  This machine was sitting around after a couple of failed Mythbuntu attempts (hardware issues). This install was basically for fun and the browsing pleasure for The Mrs. and me on the main family TV.  It's also going to serve as our DVD player.

This 64 bit install was so uneventful, I think the only thing I have to say about it is that it seemed to be painfully long. (twss-heh).  My experience seems to have mirrored Tom's Hardware although different machines.

Other than that, I had a small issue of getting wireless working

solved here:

[https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455)

Also, I had to uninstall and reinstall the sound to get it working.  Santa brought us a bluetooth keyboard with tracpad from Thinkgeek and all is good.

Four out of five stars, Ubuntu team.

---

### Post by Kalimol on 2011-01-01
Upgraded from 10.04 on an Eee S101, 2G RAM. It was excruciatingly long as always, but I encountered no problems and had enhanced support for my Eee SHE waiting for me, which meant in practical terms that my processor's low-power mode is actually useable now. Wireless on waking from suspend encountered a problem that required a pair of scripts to be added, but this problem was present in 10.04, too. My tweaked Synaptics trackpad driver had to be reinstalled, but this went without a hitch.

Generally, I've submitted to anticipating problems with my WiFi card and Compiz specifically every time I've upgraded or installed on any system, and those things didn't happen, so it was the most painless upgrade I've had. I've also never been remotely as happy with an OS.

---

### Post by gfe on 2011-01-05
I was running 9.04 on an older Pentium 4 desktop and couldn't run some software I wanted, and couldn't get updates to 9.04 anyway, so I decided to take the plunge to 10.10. I of course made backups of all my data and made a list of the software I wanted to reinstall.

The installation of 10.10 went flawlessly. I installed "on top of" my old installation, and I was delighted to find out that many of my configurations and some other data were still valid. I reinstalled Opera and Thunderbird and some other software and found that all my configurations, addresses and bookmarks for those were intact as well. I did have to manually search for a couple icons to make my menus look pretty, but compared to what I was expecting, that was terrific.

The only problem that I had is that in my startup menu (I dual-boot with Windows XP for the sole purpose of watching Netflix) some old kernels were still listed (so many that XP was on the second screen) and I couldn't figure out a proper way to remove them even with tools designed for the purpose (they were no longer listed in Synaptic or anywhere). So I simply deleted the directories with the old kernels and did a grub update and crossed my fingers, and the problem was fixed.

I was expecting some difficulty in jumping three versions and was prepared to wipe the hard drive clean if necessary. But I couldn't have asked for a better upgrade experience.

---

### Post by witeshark17 on 2011-01-05
Wow, that's very interesting and impressive! :popcorn::KS

---

### Post by dhopley on 2011-01-05
Hi ,
Fresh install on old Intel 2.8 ghz Celeron , 1G ram , Intel graphics card worked flawlessly and together with the major update manager run after the initial restart it took about two hours . Don't really use Compiz and Gnome Desktop instated OK . 13 year old Lexmark LZ11 printer also OK .

---

### Post by durandetto on 2011-01-08
This is currently an ongoing nightmare for me tried 3 different downloads with different write speeds and get 3 different problems/ errors.  About to give up and go back to windows.

---

### Post by GrahamM on 2011-01-09
I at first ran the Live CD on my laptop - Wifi kept switching on & off. Decided to do an install on usb external HD. Went OK but still problem with wifi

Main project was to do a clean install on my 1Gb Athlon based desktop. This machine had previously had 8.1 installed which worked fine until HD failed.

An unable to get 10.10 to install. Have got as far as install but it just sits and gets nowhere. Did once get to point where install slide show appeared and I even had a wifi link. But install hung up there with CD spinner instead of mouse arrow.

Even burned new CD on same machine just in case drive didn't like CD burned on laptop, but that did not help.

Getting close to giving up :(

---

### Post by Mat11 on 2011-02-23
Meerkat has to be the worse Operating system to install.I have a Fujitsu laptop 1718i which was originally updated from vista (hate to mention that rubbish rip off) to Karmic 9.10 which was a struggle at best but i managed it. I would give my experience fo that a 7 out of 10 although i had to reboot the computer sometimes three times to start it.Recently i ran the 10.10 disc i long waited for about 13 times and wasted hours just to get to the partitian screen where after many previous and varied complex messages. The one i have now is no root file system is defined. I never wanted to start to fiddle with the partitian part in the first place because all i wanted to do was completely overwrite and format my hard drive.I would consider my self someone who has swapped out two hard drives in the past one got XP being an easy install and the other Karmic which seemed a bit trying. Finding Meekat like its name sake more or less impossible, my laptop has also decided to grey out some of its features in its start up Bios ie the reset feature.
Sometimes i get a squashHFS error:unable to read metadata cache entry.Other times i get the message (process:304):GLIB-Warning**:getpwuid-r():failed due to unknown user id (0) -- think i have already overcome this one by pressing F2 and entering the bios password.Have also noticed a problem in the terminal i see odd output lines which i never saw in the previous Karmic operating system sometimes mentioning Pulse audio.
Should i abandon my WD500gb hard drive which is fairly new or do you know the answer ? Have a totally cocked machine at the moment.
Hope you can help -- really need it.
 
Matt11

---

### Post by Mat11 on 2011-02-23
Forgot to mention i have another problem when the meekat CD starts to boot even though the wireless Lan is switched off in the bios start up ,the CD during the beginning boot process turns the wireless network light on and i have noticed a strange terminal line mentioning wifi network had switched on.Why is this happening when i'm wired in ?

---

### Post by Hollyecho_Montgomery on 2011-02-28
I have found that Boxee does not work, or come up in 10.10
Kubuntu 10.10 has to have internet connections set manual for each connection:
ie:
IP:   192.168.1.XXX  (wired does NOT work at all - only wireless)
        255.255.255.0
        192.168.XX.XX
DNS  199.224.XX.XXX
         199.224.XXX.XXX  (for example only)

Only when the wireless (again wired does not work) will it connect.

While when I connect as GNU - everything connects perfectly, every time. (just having DHCP automatic settings)

Hated to see that Boxee does not work (even with the new or changed nvivia drivers), spent more than 4 days on code after code after code.  Just black screen, then disappears no error message.

Hollyecho Montgomery
[email]pure.ubuntu@gmail.com[/email]

---

### Post by Ctrl-Alt-F1 on 2011-02-28
I had some stability issues when I tried it immediately after release.  I never found out what was causing those because I switched back to using the LTS briefly and in the interim the problem has been fixed.  :D

---

### Post by n00b512 on 2011-03-02
I did a fresh install, using alt cd.  It worked pretty well except for one sticky point.  Since I was wanting full disk encryption & had a dual boot system I had to manually partition.  When I put 100 Mb as the size for /boot it reserved some bytes or something so that it only showed 96 Mb free.  I didn't give it much thought but after it finished copying files and setting up users it gave me an installer failed error with no explanation what the problem was.  After a lot of head scratching and googling I finally figured it out and made my /boot partition a little bigger and all was well.

---

### Post by Mat11 on 2011-03-03
All is well i just used another install CD from Ubuntu user magazine and hey presto no problems, went as smooth as anything OH yes.The original problem was just a faulty Desktop CD sent to me in the post.Hardly saw much on the CD except very very faint scratches and micro dot marks about two of them.

Must say thanks to all for your amazing support it was very helpful.

---

### Post by xXOtherPeoplesWasteXx on 2011-03-03
Problem free install, so lacking of problems that I went back and just reformatted entire HD (INCLUDING WINDOWS and RECOVERY Partitions)

Thanks for all the support and awesomocity

Now Running dual-boot ubuntu 10.10 next to Linux-mint 10

LOVE IT!

---

### Post by Lee E on 2011-03-03
I was one of those who "jumped right in" and now am stuck in the mud (or rather grub) like you. The gui came up fine after the initial install but after I accepted the updates, grub> has a hold on me. Oh well, to the tech forums I go.

---

### Post by FlameReaper on 2011-03-11
Just decided to jump on the MM bandwagon, ironically a few more weeks before Natty is released. Well, maybe I'll do the same for the next releases as well.

Even with the alternate CD upgrade things were pretty going slow for me since I decided to upgrade everything on the spot. Well, some hiccups happened and, KDM and Compiz suddenly refuses to let me run them for some odd reason. But meh, it's all solved now and 10.10 is now official in my machine. Sweet experience.

Oh, by the way, I'm running on Liquorix kernels even before the upgrade. I don't know what I should enjoy from it since I decided to try it out for some kicks, but if there's anything significant I'd love to know and enjoy it.

---

### Post by rabinnh on 2011-03-22
I've been doing distribution upgrades since 8.04.  Just upgraded to Meerkat.  Never had a problem before, but now X crashes every 30 seconds or so.  Reinstalling the NVidia drivers makes no difference (they are the same drivers I was using with 10.04).  Changed the X config file back as well, but still crashing.

Looks like I am hosed after 3 years

---

### Post by johntaylor1887 on 2011-03-22
> **rabinnh said:**
> I've been doing distribution upgrades since 8.04.  Just upgraded to Meerkat.  Never had a problem before, but now X crashes every 30 seconds or so.  Reinstalling the NVidia drivers makes no difference (they are the same drivers I was using with 10.04).  Changed the X config file back as well, but still crashing.

Looks like I am hosed after 3 years

The law of averages caught up with you. Clean install FTW.

---

### Post by rabinnh on 2011-03-22
A clean install is not an option.  This is a workstation with tons of in process work.

I may have solved the problem.  I Googled everything in sight and it seems that there might be a bug in the version of X11 shipped with Meerkat. I use x11vnc (as do many others).  I added the "-noxrecord" option to the startup line and I have been working for 5 minutes now without a crash.

Had I reinstalled the same software, I would have gained nothing

---

### Post by dehager on 2011-03-29
[SIZE=2]Worked well and could not be happier!!![/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]The goal was to have a Netbook running Ubuntu so I could access internet, e-mail and video chat while traveling. I also needed to use Google Earth and transfer GPS waypoints with my Garmin 60CSx. I decided to purchase a Toshiba NB505-N508 with 2G of memory after researching Netbooks. The only issues I found while researching was loss of battery power while shut down on early NB505 Netbooks and Wi-Fi drivers not installed, nothing of any major importance with the newer NB505-N508 Netbooks. Before wiping the Windows 7 Starter from the drive I ran Belarc Advisor under Windows and printed out the hardware information. The Wi-Fi was listed as a Realtek RTL8188CE Wireless LAN 802.11n.

USB Flash Drives were created using the Universal USB Installer and the drive was wiped with DBAN “Darick’s Boot and Nuke”. After connecting the Netbook to the internet using the Ethernet port Ubuntu 10.10 Netbook was installed using the USB flash drive and updates were installed. At this point I did not have Wi-Fi working and installed the Realtek driver update as listed below, once installed the wireless appeared and worked without issue. No issues were found with discharging batteries while turned off.

Google Earth 6, Google Talk and Skype installed and worked without issues. I was disappointed that Google Earth 6 did not have GPS support but I can use GPSBabbel to save my waypoints and import the .gpx file into Google Earth. I was not able to get Empathy working with video using my Gmail account but I am confident that the community will eventually get the bugs worked out.

With a little up front research all went well and I am now the proud owner of a fully functioning Netbook running Ubuntu 10.10. I am grateful to all who contribute their time and expertise supporting the Ubuntu community. I have no complaints with the Toshiba NB505-N508 running Netbook 10.10 and the minor issues encountered were easy to overcome. I am sure that future updates and bug fixes will add to the functionally of the software. 

I am sure that there are many ways to install and configure Ubuntu. This is how I, with very little experience using Ubuntu configured my Netbook… Again, thanks to all!

**_Installing the Realtek Wi-Fi drivers:_**
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms

**_Installing Google Talk:_**
Downloaded the application through my Gmail account by clicking on the “Install voice and video chat” link and installed with Ubuntu Software Center. Using Gmail in Firefox I was able to connect to a Windows XP work station using Gmail video chat with no issues.

**_Installing Skype:_**
Click, click with Ubuntu Software Center. I was able to connect to Skype users with no issues.

**_Installing Google Earth:_**
sudo apt-get install lsb-core (lsb-core package must be installed)
sudo apt-get install gdebi-core (this is how I chose to install the .deb package)

sudo apt-get install googleearth-package
sudo make-googleearth-package --force
sudo gdebi <*package name*>.deb[/SIZE]

---

### Post by Olivier 22 on 2011-04-02
I recently installed ubuntu 10.10 without a hitch on this machine, however it wouldn't install on 4 older machines. I'm guessing hardware issues. This seems to be common from what I've read on line about it.
This machine is pretty new.

I like  how stable this OS is compared to Windows. I'm thinking of putting it on a laptop. There appears to be a lot of free programs out there.

I'm not able to use my Linksky  wireless adapter for some reason and the  my Ethernet card has done some strange things.
 I haven't read much about  any security issues. I have it firewalled. I guess I'll have to read up on it.
It seems that viruses are non existent and with Windows it seems like no matter what I did or which virus program I used  I always ended up with several viruses a year and would have to reinstall everything.

 So far my experience has been good:razz:

---

### Post by el_koraco on 2011-04-02
emachines e442. amd v140 cpu, aetherow wireless, radeon hd4200 gpu, 2gb ddr3 ram, came with linpus linux preinstalled (boots into the command line, i have no idea how they expected to attract any new users with that). maverick has been 100 percent effective out of the box.

---

### Post by Wavebourn on 2011-04-20
I had some Kamasutra with Ubuntu 10.10 and HP Mini 210 1000. It has no CD drive, so I decided to try a pendrive. On the phase "Preparing to install" it stuck. I searched the net and found lots of weirds suggestions. I did all of them, starting from "seems to be reasonable somehow" to "absolutely weird", but nothing helped, until I realized that ubiquity somehow did not know sometimes which drive is hard, which is flash...
Then I tried to install Centos 5.6 on the same machine, and after installing manually boot loader and GRUB to the proper place it come alive, but I liked more Ubuntu notebook interface and functionality: skype even though statically linked requires dynamic libraries that are not available on current CentOs...
So, today I borrowed an external DVD drive, and continued Kamasutra with Maverick Meerkat... It successfully went through "Preparing to Install", but I stuck on user-create script. It won't allow me to go forward! I had almost to reverse-engineer the thingy until realized that it did not like capital letters in usernames!
However, it sounds weird, but it is as it is...
Looks like the installation went through... But not without further surprises: casper ejected cd-rom and then started complaining about IO errors. Oh-oh, how come! :D
So, it should be rebooted now...
Let me go and see, if my daughter will have a nice notebook instead of that crappy Windows 7 toy for mentally retarding she broke somehow...

It works!

Thank you for the software! :popcorn:

---

### Post by Linux_junkie on 2011-04-20
Installed from fresh Xubuntu 10.10 on a desktop dell pc with 256MB of RAM and 40GB hard disk.  I no issues about the install.

Before settling with Xubuntu I also tried Ubuntu 10.10 and once again no issues with the install but was a bit slow which was why I changed to Xubuntu.

---

### Post by alliance1975 on 2011-04-29
It seems the newer the version the worse it gets. Most of the problems stem from my ATI 200m xpress video card in  my HP laptop. Earlier versions eliminated Google Earth from use. The latest new install just gives black screens and crashes. Very disappointed. My wife's new laptop with Win 7 is working very nicely.

---

### Post by jpuk on 2011-05-01
Upgrade seems ok so far, though there was one gotcha.

I was running the 10.10 netbook version and by default after installation & re-boot it logged in using the Ubuntu netbook UI which led to an empty screen with just the desktop backdrop to show the graphics were working.

Re-booted selected Ubuntu as UI option and everything sprang to life with unity etc side bar.

---

### Post by augusto_sf on 2011-05-06
After the update from 10.10 earlier this week, I was happy with the new system but suddenly the screen went blurry and I can't read anything anymore! I have spent countless hours trying new screen resolution, new configuration, reading manuals, help pages, etc. It has been very disappointing! I think my only option is to re-install Ubuntu 10.10.

Cheers,

Augusto

---

