---
title: "Share with the community your Lucid Lynx install/upgrade experience"
date: 2010-04-29
forum: Testimonials &amp; Experiences
---

### Post by frodon on 2010-04-29
[SIZE="3"][COLOR="Red"]*** Disclaimer for those willing to analyse this poll ***[/COLOR][/SIZE]
[SIZE="2"]- Most of users voting here are users with issues,
users with painless experience are not likely to come here. So the statistics here do not represent the reality.
- If you want to compare Lucid Lynx release with other ubuntu releases based on this poll then here are the previous polls (the only good reference to start an analysis)[/SIZE] :
[Karmic Koala - Click Me]("http://ubuntuforums.org/showthread.php?t=1305924")
[Jaunty Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=1133869")
[Intrepid Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=963853")
[Hardy Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=764847")
[Gusty Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=580852")

[You will find here a Summary proposed and maintained by NCLI - Click Me]("http://spreadsheets.google.com/pub?key=t0XWfWgqJpYxCGAZ1G8U-og&output=html")


The purpose of this thread is to share your experience installing/upgrading Lucid Lynx.

Did it work flawlessly ? 
Did you get problems ? 
Did you manage to solve them ? 
if yes how ?
...
...
.

Feel free to post your experience here and think to explain how you solved the problems you got, it might help other users in your case.

Thank you for contributing :KS

---

### Post by devnuller on 2010-04-29
Congratulations to all the Ubuntu staff for an excellent upgrade package. Both my native x86 and virtual machine 9.10 to 10.04 upgrades performed flawlessly. Those were by far the easiest and cleanest Linux upgrades I have ever had the pleasure to carry out. Keep up the good work!


Regards

Dev Nuller (Unix user: 20 years, Linux user: 15years)

---

### Post by OnlyTim on 2010-04-29
Did the upgrade to 10.04 this morning. overall time was about three hours. I use both Ubuntu and KDE and the upgrade blended both seamlessly. Nothing missing, everything working as it should. Kudos to the Ubuntu folks for the easiest upgrade I've ever done!

---

### Post by Simian Man on 2010-04-29
> **frodon said:**
> Most of users voting here are users with issues,
users with painless experience are not likely to come here. So the statistics here do not represent the reality.

You could also say that most of the users here are Linux enthusiasts and are thus more likely to be able and willing to solve problems than the average user.  If a new user tries to install Linux and it fails for them, they may not even ever bother to come to the distributors forum.

I bet the poll is optimistic if anything.

---

### Post by wojox on 2010-04-29
*Install - worked but had few things to fix, nothing serious though*

Actually only one issue. I installed the mini.iso and installed ubuntu-desktop from there. Upon reboot after choosing the kernel could not get the graphics to load. So had to edit and set add "nomodeset" parameter to the kernel and then it booted and had to edit /etc/default/grub the same way so it will always work.

---

### Post by powerslave12r on 2010-04-29
***Install - worked but had few things to fix, nothing serious though***


Did a clean install from 9.10.


Version : Ubuntu 10.04 AMD64 Desktop using ext4 JFS. 
Download time: Direct download in 11 minutes odd.
Issues: Broadcom drivers (STI not available through System> Hardware). Had to connect to the internet via ethernet, then apt-get install b43-fwcutter.
Machine installed on: HP DV6400t notebook AMD Turion x2 2.0GHz, Broadcom Wireless card, dual boot with Win 7.


Done. I'm in love all over again.

---

### Post by skalra63 on 2010-04-29
So I installed it... I am a newish user, I used Karmic Kubuntu but know very little of the inner workings.

Installed it,...so far so good....try to install broadcom drivers from cd...failure....try to connect to wireless using ralink 2860 (worked flawlessly in Karmic)....keeps saying preparing to connect and asking for the "secret"...

going back to koala i think

---

### Post by drreed on 2010-04-29
[SIZE=2]A couple things happened that didn't exactly inspire confidence.

1. Got an error just before the menu's appeared on the desktop of the Live CD - something to the affect of "error - there was a problem with the installation. WQill now take you to the live desktop where you can fix the problem before continuing"

Then the desktop appeared, with the install program. Lately, my DVD-RW drive has been acting up and it may be dirty or something. I've gotten "unable to mount device" messages several times in the last few weeks.

I never saw the "test cd for errors" screen, maybe an extra "enter" key in the buffer, and that's why it went straight to the desktop on boot?

2. After the rest of the install went flawlessly, I chose not to install grub (I was installing on an empty partition for testing first) and rebooted.

It gave me a page of IO errors and hung there, suspended, until I hit the reset switch on the front panel. That's the kind of stuff you get with BSD (only they make you go to the power switch on the back, "old school" style)

Maybe it was just me, but if it's happeneing to everyone, me thinks a lot of new users might say "it's not ready".

I'm running it now, posting this, and so far so good.

[/SIZE]

---

### Post by dazcaz on 2010-04-29
Tried upgrading via the update manager and it fails to even start downloading the files.
I keep getting told to check my net connection, the same net connection that I'm using to send this :)

I'd rather upgrade than download the ISO files and do a fresh install. I can download the ISO but am resisting doing the upgrade this way.

I just hope that that it's a busy server and things will return to normal soon.

---

### Post by drreed on 2010-04-29
> **dazcaz said:**
> Tried upgrading via the update manager and it fails to even start downloading the files.
I keep getting told to check my net connection, the same net connection that I'm using to send this :)

I'd rather upgrade than download the ISO files and do a fresh install. I can download the ISO but am resisting doing the upgrade this way.

I just hope that that it's a busy server and things will return to normal soon.

I'm sure it is. The torrents are flying, took me about 10 minutes, the server version started slow, but after about 10 minutes took off, and finished in about 15 total. Every page at the site is slow, must be a few hundred thousand hitting it today - torrents are the way to go today.

---

### Post by loganfynne on 2010-04-29
I am installing Lucid Lynx onto my Dell Inspiron 1750 laptop, and everything goes smoothly in the install until I get to the keyboard layout page. Then, it gives an error when I click Forward, that says Parted Server failed, and then the installation freezes at the keyboard layout page. Is there any other way to install Lucid Lynx?

---

### Post by infamous-online on 2010-04-29
I did a clean install from Ubuntu 9.04, and so far all I have is a million I/O errors, and once I reset the machine, I'm taken to a bash shell prompt! Then I just reset my machine again, it's working wth? This is indeed strange, so let me reboot my computer again and see what happens. I'll post the results in a few. :confused:

---

### Post by NCLI on 2010-04-29
> **dazcaz said:**
> Tried upgrading via the update manager and it fails to even start downloading the files.
I keep getting told to check my net connection, the same net connection that I'm using to send this :)

I'd rather upgrade than download the ISO files and do a fresh install. I can download the ISO but am resisting doing the upgrade this way.

I just hope that that it's a busy server and things will return to normal soon.

Yep, I think the servers are dying - as usual.

No problems for me, on two clean installs. Probably because I participated in the Alpha and Beta to report the bugs I did encounter :D

---

### Post by apostra on 2010-04-29
Hello guys,

Did clean install and all worked just fine. Used manual partition, reformat my current / and home (had loads of waste things so i decided  to wipe them)

Done the update and now i install some progs like msn etc. All fine, aaaaall gooood

Ubuntu are cool, feel good!

A newbie sends many gratz and regards.

Thank you guys. Great job!  

P.S Intell Duo, GT120 graphics.

---

### Post by infamous-online on 2010-04-29
Just rebooted the machine again, and all is well. I'm still trying to figure out why I got that strange message in the first place? :confused: Oh well, it's up and running and that's what I wanted.

---

### Post by PhilGil on 2010-04-29
> **skalra63 said:**
> ....try to connect to wireless using ralink 2860 (worked flawlessly in Karmic)....keeps saying preparing to connect and asking for the "secret"...

going back to koala i think
Ralink 2860 wireless does not work in Lucid.  This is supposed to be fixed in a release update.  It's going to impact a lot of users with 1st and 2nd gen netbooks and (IMHO) should have been included in the release notes.  [https://bugs.launchpad.net/bugs/496093](https://bugs.launchpad.net/bugs/496093)

There are a couple of work-around posted in the bug report, both both require some hands-on work (installing an updated kernel or compiling/installing the Ralink driver).

--------------------------
I started with Lucid RC (clean installs on three machines) and my experience has been a bit of a mixed bag.  Two out of the three suffered from known issues (that I don't believe have been addressed yet).

EEE PC 1000h netbook: Ralink 2860 wifi driver bug, currently working fine using the patched kernel from the bug report I linked to above.

Dell GX260 desktop:  This elderly desktop suffered from frequent crashes because of a bug in the integrated graphics: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/566324](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/566324) .  Fixed by scavenging a graphics card from a spare computer.

Generic desktop, AMD 64 3400+ processor, ASUS mainboard, about 4 years old:  Lucid installed and worked bug-free on this machine.

---

### Post by lav0s on 2010-04-29
all installed but i missed something in the installer, the ability to erase all linux partitions and install, it only presented me with erase all disk, dual boot and edit partitions, i think that old option worked fine and neden't to be removed

---

### Post by Irihapeti on 2010-04-29
Clean install, one or two minor problems with Grub. If I didn't have all these other OSes on my computer, there'd be no problem at all.

@dazcaz
Another way to upgrade is to get the alternate CD. Put it in your drive and it asks you if you want to upgrade. Much quicker than over the net, and more reliable, I think - no worries about connections going down.

---

### Post by cyborg_jim on 2010-04-29
> **loganfynne said:**
> I am installing Lucid Lynx onto my Dell Inspiron 1750 laptop, and everything goes smoothly in the install until I get to the keyboard layout page. Then, it gives an error when I click Forward, that says Parted Server failed, and then the installation freezes at the keyboard layout page. Is there any other way to install Lucid Lynx?

I have a similar problem on an eee pc with the netbook remix - but I don't get any errors, it just never progresses from the keyboard layout page.

---

### Post by drunkskater on 2010-04-29
I am pretty new to Ubuntu, and I've many problems with the install of Ubuntu 10.04 :

I currently have a 32-bit Ubuntu 9.10 in dual boot with Vista. For several reasons I decided to take advantage of the release of the 10.04 version to get rid of Vista and switch to Ubuntu only... And get a 64-bit version.

I downloaded the 64-bit version of Ubuntu 10.04 from a torrent. I checked the MD5, and it was OK. I burned the ISO image thanks to Brasero and it worked all right. I wanted to check the CD, but I didn't manage to : I got a weird message : "You don't have the rights to read that disk". As I didn't know how to use the sudo command, I assumed that as everything had worked fine, and that the files seemed to be on the CD, it'd work.

I booted my computer from the CD : Nothing, only a purple screen with two small logos at the bottom of the screen. After several attempts I came to notice that if I held the "Enter" key at the right moment (note that it didn't work with other keys such as the "E" key...), I could get various options : "Try without installing", "Install", "Check CD", etc...

But none of this commands seem to work : when I select one and hit enter, nothing happens, and there's a bug. The screen remains unchanged, and nothing happens when I hit any key... After too many tries, the computer starts doing "beeep" whenever I hit a key.

As I had had problems installing Karmic Koala (I have an Acer Extensa with a 1366x768 resolution, so I got a black screen when starting the computer, unless I typed "i915.modeset=0" when starting the computer. But I fixed that bug by writing this in the GRUB), I thought it might be due to three problems :

- Problem of CD (during the burning or something)
- Problem of compatibility this the computer, due to the 1366x768 resolution, like with Karmic Koala
- Problem of compatibility with the 64-bit
- A more serious problem.

My computer is a Acer Extensa 5235. The processor is a Intel Celeron 900 : I guess it's a 64-bit processor, so that should rule out one possibilty...

But I wasn't so sure so I dowloaded the 32-bit version. I burned it very carefully (speed : x10), and everything was ok. I tried that CD : EXACTLY the same problem.

So what I did was trying that 32-bit CD on another computer with a 32-bit processor. Something really interesting happened :

- Same problem with the boot : I had to maintain the Enter key pressed. 
- But then, instead of a menu in front of a purple screen, I got a loading menu. It lasted for like 5 or 10 minutes, and then I had a message : "Install" or "Try without installing" : no other option ! That is to say, I can't check the CD, etc...
Anyway, I tried it withouth installing. I had a very long loading, and then it worked perfectly.

So I assumed the 32-bit CD was OK (althought there was that weird bug). As I had had the same bugs with it and with the 64-bit one, I assumed (although this is a huge logic error ^^) that the 64-bit was too...

And right now I don't know what to do... The second bug is minor but I find it even more bizarre than the first one. But that's the first one that's bothering me right now...
I asked help on the French Community forums several hours ago, but so far, no answers...

Thanks for your help !

PS : and sorry if I made many English mistakes... ^^

---

### Post by pauljwells on 2010-04-29
On my desktop:
Upgrade from 9.10 to 10.04 hosed both ubuntu and xp - couldn't boot anything and tried LOTS of things.
Clean install using 'side by side' got me to grub rescue
Clean install on free space got me to flashing cursor

Never had so much trouble before

On the plus side, on my netbook:
flawless clean install next to Win7 and both working perfectly :-S

---

### Post by Irihapeti on 2010-04-29
I did another install on my old Toshiba Satellite A10.

I couldn't get the live CD to boot, initially. It loaded so far and then locked up with a black screen.

It eventually booted when I pressed F6, then escape and added "i915.modeset=0 xforcevesa" to the command line.

The install itself was uneventful, but rather slow (to be expected with an old CD drive).

---

### Post by b00n on 2010-04-29
I notice during install a bunch of applications have "gone away" in 10.04, for example ekiga, tracker, and so on.  I really like being told about that, it would be better for me if there was a list of "try XYZ instead".  For example, there's a bunch of soft phones for Linux, but if there's a preferred one for Ubuntu that's where I would like to start.  Yes, I know I can keep using ekiga, etc., after it is no longer supported, but if there's one that is supported I might as well take the plunge and try it right now.

Also, assuming I like 10.04 I'll be newgrading all my computers to it... I'm on a medium-speed DSL link but it is still quite a bag of bits.  I bet there's a way I can download once and newgrade many, reusing most of the downloaded bits for each computer (they are all pretty current, so there would be not much extra each time).  That would save load on the Ubuntu servers and also speed up my progress.  Maybe it makes sense to have a click box "Will you be switching several computers to 10.04?" that burns a USB stick, etc. with the bits, then I just carry that over to the next computer and it checks there for each package before contacting Ubuntu HQ.

Somewhere between 2 hours and 2 days to go before I can try it out, I'm getting about 20kB/s right now, I hope that's because everybody else on the planet is fetching it, too :-)

---

### Post by matchett808 on 2010-04-29
Cant remember exactly how to do it, but If you d/l an install CD then you can add it into software sources me thinks....might be wrong but is maybe a start to help :)

---

### Post by sports fan Matt on 2010-04-29
The install (long ago) was pretty straightforward, no real issues, I think the only minor quirk was somehow I was in low graphics mode for a time.

---

### Post by disneyfriedhistory on 2010-04-29
Fresh installed worked great. First time since Jaunty that the video card (Radeon 7500) seems to work properly.  Runs fine with light compiz desktop settings.

---

### Post by sdt1 on 2010-04-29
Since I have Ubuntu installed on my iMac with triple-boot (OSX, Linux, and Windows Vista), I was very afraid after reading all the horror stories on the forum today about upgrading to 10.04 LTS.  I decided to bite the bullet and upgrade from 9.10 anyway. What should have been maybe just shy of a 2 hour process took_** 8 hours**_, but that was because the fetching of new files (***1345 to be exact***) took ***FOREVER***. I'm sure this was because of the overwhelmed servers. However, all is well that ends well, and I am writing to report that my fears were for not. The upgrade was flawless, and 10.04 LTS is most beautiful! _**Thank you to the Ubuntu Dev team for all your hard work**_!!!

**P.S.-** If you receive an error message during the "installing new files" phase regarding "...Network Manager could not continue", just click "OK", as it had no negative bearing on the success of the upgrade. I believe it may have been intentional as new network files were replacing old.


Cheers,

-sdt1:popcorn:

---

### Post by MobiusNZ on 2010-04-29
Did an upgrade, but my buttons are round the wrong way. That is, they are on the left-hand side as in the new style, but they go [Maximise] [Minimise] [Close],when I believe the close is meant to be on the far left. 

Easy enough to fix with gconfig though. Just thought I'd mention it.

Also I'm not sure my colour scheme is exactly correct. Light brown text on slightly darker brown for my active window is not exactly easy to read, nor is the blue hyperlinks in firefox's "awesome bar" suggestion list.

---

### Post by gsparky2004 on 2010-04-29
Just did the upgrade.  Mouse works, but keyboard doesn't.  Can't even log in, so I have no idea what else may not be working.

Based on my last upgrade (9.10) in which I had multiple problems, this is not inspiring confidence.  From the last three upgrades, Ubuntu is 1 for 3.

---

### Post by Nittalope on 2010-04-29
Upgraded from 9.10 on Acer Aspire 6530G. Everything worked smoothly. Best upgrade ever. Only a thing I think it's important to mention: when installing grub the message where you want to install it is a bit scaring... maybe a newbie would be a bit confused.
By the way: great job Ubuntu guys, the new 10.04 works and looks great!
(Still have got my little problem with the internal mic... but it already known...)

---

### Post by TBerk on 2010-04-29
Well, I did a both Upgrade AND an Install, but theres no choice for 'both'. [http://ubuntuforums.org/images/smilies/icon_razz.gif](http://ubuntuforums.org/images/smilies/icon_razz.gif)

Initially I installed 10.04 beta2 over the top of my preexisting 9.10. It pretty much clobbered 9.10 when what I had thought too accomplish was a side by side triple boot of WinXP, 9,x & 10.x. 

> ... removing conflicting system components...

Should have known better.

I ended up nuking the OS partition (from Orbit, natch) and after some housekeeping partition management/resizing, I installed version 10.04 (beta2) from the LiveCD. 

I had to add Medibuntu, Non-Free, and other repositories to get it the way I wanted it to act, but all in all it worked flawlessly.

btw, a few notable gotchas:

- I had to install GNOME ALSA Mixer to get my Creative Labs Audigy2 sound card to work (the ol' Digital/Analog JACK toggle fix)

- 27APr-29APr2010; Everybody and their brother/sister is downloading, hitting, pinging, checking, verifying, upgrading, updating, downloading from the same servers I am. Stuff is slooooow.

- ver 10.x is the 1st version to work my wifi RALink chipset card right from the get-go. (Prior to this version I couldn't both boot the LiveCD AND surf the internet, I'd have to go hardline or dualboot to Windows.)

- I *think* the 10.04 beta2 LiveCD maaaybe be the 1st one to allow my relatively older DVD-RW/CDR burner to actually burn media to completion from within Ubuntu (prior to this I've had to, you guessed it; dual boot into WinXP to burn CD/DVDs.)

Over all my Intel Dual Core P4 @ 3GHz running, 2Gig RAM memoring, IDE based HD spinning, Audigy2 sound card having, NVidia GForce FX 5200 video card displaying computer is OkaleyDokaley.

 
berk

---

### Post by shannon.jacobs on 2010-04-29
Trying to keep it simple, I started with a completely fresh install in a virtual machine (VMware Player 3.0.1). This was from a BitTorrent download burned onto a bootable CD. The installation seemed to go smoothly, though very slow in some parts where it apparently needed to download from the server. However, the result was total failure. Can't even log in. Apparently the keyboard is not connecting to anything in the VM. 

At least the mouse is working--but evidently worthless. Is there some way to activate a soft keyboard before logging in?

Not good. Can't even report the problem from inside the machine, nor collect any diagnostic information. You'd think that VMware is popular enough that they might have tested it, eh? You'd be thinking wrongly.

In the Koala upgrade, the sound cards on many machines were crippled, and it took several months before the errors started going away. I've already stopped recommending Ubuntu for new users, but at this point I'm about ready to drop it...

---

### Post by jbarnes1960 on 2010-04-29
Installed 10.04 on my duel boot laptop flawlessly. No problems.
Installed it on my duel boot desktop and Firefox won't work. I went through the forums and tried all I saw and it did not work. Ran the firefox.sh file in terminal mode and firefox ran but without flash. I can use Opera or Chrome just fine until its fixed.

WORST thing however is now when I shut down and try to boot up to XP, the computer shuts down and boots back to Ubuntu. It will not let me go back to Windows.

OK, guys. I need some help getting back to Windoze...

---

### Post by antenna on 2010-04-29
Clean install, no problems whatsoever.  All good.

---

### Post by iomtalach on 2010-04-29
Upgraded from 9.10, all good. Had to spend a lot time tinkering to get back to my nice customized desktop, but I expected that.

One question though...

What the H*** is up with the ugly 8-bit lookin nautilus? It's harshing my buzz, dammit.

---

### Post by TBerk on 2010-04-29
> **iomtalach said:**
> Upgraded from 9.10, all good. Had to spend a lot time tinkering to get back to my nice customized desktop, but I expected that.

One question though...

What the H*** is up with the ugly 8-bit lookin nautilus? It's harshing my buzz, dammit.

And wth is with this new Upper Left Hand Corner w/ the X = Close, Middle/underscore = Minimize, Right = shrink to a non-full screen window action.   Schtupid. Minimize should not be in the middle like that.


berk

---

### Post by CharlesA on 2010-04-29
> **TBerk said:**
> And wth is with this new Upper Left Hand Corner w/ the X = Close, Middle/underscore = Minimize, Right = shrink to a non-full screen window action.   Schtupid. Minimize should not be in the middle like that.


berk

Easy fix: [http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)

As for me: I'm currently trying to install Lucid and so far it's working outside of having problems with the repos not cooperating. The newest version of Webmin works with 10.04 and it seems the same stuff I had on my server when it was running 9.10 works just fine with 10.04: DHCP, Samba, SSH, Webmin, HW Raid software/management.

I haven't tried virtualbox yet, since they don't have a lucid repo yet.

---

### Post by ratcheer on 2010-04-29
I upgraded from Karmic using the Alternate CD image. I did it a couple of weeks ago to a Beta 2 image and have kept up with the updates since then.

The only real issue I have found so far is that my ALSA driver was not updated. It only took me a few minutes to fix that, manually.

For me, Lucid has been a great release. Kudos!

Tim

---

### Post by jf1991999 on 2010-04-29
Absolutely flawless install on an HP Pavilion DV6000 with 2GB ram.  Even my microphone worked in skype right out of the box.  Thanks everyone for an excellent job!!!!

---

### Post by TheLocust830 on 2010-04-29
> **TBerk said:**
> And wth is with this new Upper Left Hand Corner w/ the X = Close, Middle/underscore = Minimize, Right = shrink to a non-full screen window action.   Schtupid. Minimize should not be in the middle like that.


berk

upgrade from 9.10 went perfect, except for that. I really want those buttons back on the right side. For a moment i thought there was a terrible problem

---

### Post by iomtalach on 2010-04-29
> **iomtalach said:**
> Upgraded from 9.10, all good. Had to spend a lot time tinkering to get back to my nice customized desktop, but I expected that.

One question though...

What the H*** is up with the ugly 8-bit lookin nautilus? It's harshing my buzz, dammit.

Nebbamind, second re-boot fixed it. Of course I had to reboot because switching from one user to another locked up the screen...I'm sure that'll be patched in a bit. :) 

Dammit. I'm liking this upgrade. Now I have find something else to complain about.

---

### Post by ionFreeman on 2010-04-29
I haven't finished the upgrade yet, but it's been running about five hours. The progress bar is wacky, though. It'll say '50 minutes remaining', '13 hours', '1 hour 38 minutes' and on and on. Here's every ten seconds for a minute:
41:10 42 minutes
41:20 1 hour 7 minutes
41:30 2 hours 45 mimnutes
41:40 1 hour 11 minutes
41:50 1 hour 46 minutes
42:00 6 days 6 hours
42:10 6 days 5 hours

OK, it started converging there toward the end, but not in a good way. And this, again, is an aribtrarily selected minute 5 hours in -- it's been like this the whole time. At some point, the progress bar should give up and tell me it has no more idea than I have how this will all turn out.

---

### Post by tombepa on 2010-04-29
Guys, I am a total newbie, I will admit that. I have been toying with switching to Ubuntu for about a year and I have finally done it. I installed Karmic Koala then upgraded this morning to Lucid. I have a problem, when I shut the lid to my laptop, then open it back up, my cursor is not visible. It is there and works, I just can't see it unless I reboot. Any ideas on how to fix this?

---

### Post by CLCressman on 2010-04-29
> **jbarnes1960 said:**
> Installed 10.04 on my duel boot laptop flawlessly. No problems.
Installed it on my duel boot desktop and Firefox won't work. I went through the forums and tried all I saw and it did not work. Ran the firefox.sh file in terminal mode and firefox ran but without flash. I can use Opera or Chrome just fine until its fixed.

WORST thing however is now when I shut down and try to boot up to XP, the computer shuts down and boots back to Ubuntu. It will not let me go back to Windows.

OK, guys. I need some help getting back to Windoze...

You might try [https://answers.launchpad.net/ubuntu/+source/pm-utils/+question/108015](https://answers.launchpad.net/ubuntu/+source/pm-utils/+question/108015)

---

### Post by ionFreeman on 2010-04-29
tombepa, I have no idea. However! I recommend you start a separate thread just for that problem.

---

### Post by kakyoism on 2010-04-30
1. Install - flawless.
on HP Pavillion dv6000 Laptop.

2. Install - stuck at keyboard setup
on HP Pavillion m9340f Desktop.

Update:
#2 is solved in thread
[http://ubuntuforums.org/showthread.php?t=1466067](http://ubuntuforums.org/showthread.php?t=1466067)

---

### Post by CharlesA on 2010-04-30
Update: Finished installing stuff. Webmin installed without a problem. I was able to get Webmin configured to start/stop the DHCP and SSH server without problems, but I am having a problem getting it to start the Samba server back up. It can stop it no problem, but it is like it doesn't detect that Samba is stopped. I guess that might be due to Samba using upstart, but I don't know.

Lucid works for me (tm).

---

### Post by fh_scott on 2010-04-30
Same problem I always have -- NVidia binary driver.

Various errors - conflict with rivafb, nvidiafb

Restricted Driver Manager reported nvidia-common was activated but not currently in use.

Did a manual install of NVIDIA-Linux-x86-195.36.24-pkg1.run from NVidia's website and it came up.

---

### Post by fusa on 2010-04-30
Boot fails with 2.6.32-21 kernel, but works fine for 2.6.31-21.  Unable to install AMD's graphic drivers.

---

### Post by bellalamb on 2010-04-30
Upgraded from 9.10 via Upgrade

now when it boots I get 

error: the symbol grub_puts_ not found

grub rescue>

what do I do?

---

### Post by dazcaz on 2010-04-30
Finally got the upgrade and it looks great. Not had much of a chance to play with it yet.
One thing that is p*****g me off is that I have lost Thunderbird. Has anyone else suffered this? I don't mind re-installing it on this machine (The laptop) but I would hate to lose all my mail on the main machine when I do the upgrade on that.  There are a lot more e-mail accounts to set up on the other machine, not to mention the thousands of e-mails.
Is there a way to save my accounts just in case?

---

### Post by airydragon on 2010-04-30
Just upgraded my slicehost VPS from 32 bit karmic to lucid.  It took 5 to 10 mins. Everything is working perfect without any extra effort.

now i am looking forward to finish downloading iso image for my desktop and notebook.

Thanks to everyone who contributed...

---

### Post by Irihapeti on 2010-04-30
> **dazcaz said:**
> Finally got the upgrade and it looks great. Not had much of a chance to play with it yet.
One thing that is p*****g me off is that I have lost Thunderbird. Has anyone else suffered this? I don't mind re-installing it on this machine (The laptop) but I would hate to lose all my mail on the main machine when I do the upgrade on that.  There are a lot more e-mail accounts to set up on the other machine, not to mention the thousands of e-mails.
Is there a way to save my accounts just in case?

Backup your ~/.thunderbird folder. Or it may be ~/mozilla-thunderbird - something like that, anyway. I use the version direct from Mozilla, so it may be a bit differen.

---

### Post by dnelub on 2010-04-30
I have upgraded from ubuntu 9.10 to 10.04 but unfortunately it didnt end up well. During upgrading the electric was gone (by the way, installation took really long time) and now I am not able even to see console. 

Can someone direct me to solve this question because I dont want to format it?

thanks

---

### Post by ceefour on 2010-04-30
Using Toshiba Satellite U305-S2806, the LiveCD hangs on boot, while the two icons (keyboard + human) are showing at bottom screen. I haven't been able to resolve this problem.

Using my other Zyrex laptop, the installation process was flawless.

---

### Post by Rokyking on 2010-04-30
Did it work flawlessly? 
Actually, it did. I upgraded from 9.04 to 9.10 as I didn't have any disks to download and had Gentoo installed. Brasero kept giving me md5 errors when finalizing, I downloaded KD3 and it solved my problem and I was able to burn it. 
Did you get problems? With 10.04? Nope. 
Did you manage to solve them? ^^
if yes how? ^^



I also upgraded my Toshiba Netbook 205. As far as I can tell everything works. I have NOT tested sound though. Will report back if it is working out of the box.

---

### Post by frodon on 2010-04-30
> **dnelub said:**
> I have upgraded from ubuntu 9.10 to 10.04 but unfortunately it didnt end up well. During upgrading the electric was gone (by the way, installation took really long time) and now I am not able even to see console. 

Can someone direct me to solve this question because I dont want to format it?

thanksElectric failure during install is the worst possible thing, not sure you can recover this.

Anyway they are things you can do like booting with a liveCD and backup all your home directory (all you apps settings are there). Then re-install ubuntu and copy back your home directory, then install all the apps you had before and you should have back 90% of your settings.

---

### Post by ajnueva on 2010-04-30
Oh, my God!

I upgraded to 10.04 from 9.10 yesterday the 29th of april, and there seems to be problems with GRUB2 now. I get and error message, something like "can`t read grub_puts", and I get a promt: "grub_recovery>".

I have GRUB2, and 2 physical HDs installed:

- the fist HD was the original of my PC, with Windows Vista. It's named  sda, and has 2 partitions: sda1 (Vista), sda2 (Vista recovery)

- the second HD is sdb, with 4 partition I created months ago, when I  installed 9.10. These partitions are: sdb1 (/), sdb2 (swap), sdb3  (/home), sdb 4(fat32)

I remind there was a question the system made my during the upgrade...  To be honest, I didn't understand it properly. The system asked my  something (I don't really remember) related to the partitions. I had to  choose: sda, sda1, sda2, sdb, sdb1, sdb2, sdb3 or sdb4. I finally chose  both sda1 and sdb1, and nothing else. I presume my problem comes from  here. How can I fixed it? Help!!!!

---

### Post by thelugnut on 2010-04-30
I can't get the e-mail to work. I have tried Evolution & Thunderbird...neither send nor receive.
I have Ubuntu 9.04 installed on another partition. This is my work partition. No problems there. I carefully checked my Evolution setup on 10.04 with the working one on 9.04 to ensure I wasn't setting in an error.
I am just curious if anyone else has this problem.

Oh, this was a clean install.

---

### Post by frodon on 2010-04-30
> **ajnueva said:**
> Oh, my God!

I upgraded to 10.04 from 9.10 yesterday the 29th of april, and there seems to be problems with GRUB2 now. I get and error message, something like "can`t read grub_puts", and I get a promt: "grub_recovery>".

I have GRUB2, and 2 physical HDs installed:

- the fist HD was the original of my PC, with Windows Vista. It's named  sda, and has 2 partitions: sda1 (Vista), sda2 (Vista recovery)

- the second HD is sdb, with 4 partition I created months ago, when I  installed 9.10. These partitions are: sdb1 (/), sdb2 (swap), sdb3  (/home), sdb 4(fat32)

I remind there was a question the system made my during the upgrade...  To be honest, I didn't understand it properly. The system asked my  something (I don't really remember) related to the partitions. I had to  choose: sda, sda1, sda2, sdb, sdb1, sdb2, sdb3 or sdb4. I finally chose  both sda1 and sdb1, and nothing else. I presume my problem comes from  here. How can I fixed it? Help!!!!You might have installed GRUB on the wrong drive, nothing dramatic don't worry.

I would advice you to just re-install grub, you will find needed information there:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Are%20you%20using%20Grub%20or%20Grub%202?](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Are%20you%20using%20Grub%20or%20Grub%202?)
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by vaso_k on 2010-04-30
Tried installing amd64 version having 2 logical drives on a fake raid 0 array (MB Gigabyte 770TA-UD3) of 3 disks with windows installed on the 1st logical disc. I could not install grub from 9.10 on it, so was keen to try this new version. Normal installation disc failed completely - showing error messages when switching from graphic into text mode saying something like "error accessing sda...sdb..{raid}" over and over again. Eventually display went black and then - no signal. Restarted several times with no success. Downloaded alternate CD, it went better until committing changes in partitioner. Initially the volume was already formatted with ex4 and there was ubuntu 9.10 installed and partitioner did not like it (something like "cannot move existing files"). Then I tried erasing data on the disk, progress bar did not move for a while and I cancelled that. Deleted partition and created it again. Committing changes failed (message was not informative, just ~ cannot do it). SO, despite detecting the RAID correctly it seems to fail to handle it (9.10 actually did better).

---

### Post by bredman on 2010-04-30
I wish I could try an upgrade, but I work in a corporation behind a proxy. Bug 446552 was not fixed in Karmic, so I can't upgrade to Lucid, I must do a fresh install.

Why doesn't Ubuntu make inroads into the commercial workplace? Because of simple things like proxies...

Very unhappy :(

---

### Post by IBadget on 2010-04-30
I tried to upgrade to 10.04 from 9.10, but during the installation of the downloaded packages, I got an error message saying that Network Manager could not continue because it could not find required resources. When the upgrade was finished, upon reboot, I only got as far as the log-in sound and the laptop locked up. Even the power button was unresponsive, so I had to unplug it and let the battery run out to shut it off. I did a clean reinstallation of 9.10. I am using a Sony PCG-GRT240G Notebook.

---

### Post by b00n on 2010-04-30
nstall failed, perhaps due to server overload:

[INDENT]
The upgrade is now aborted. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-base-doc_2009-7_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-base-doc_2009-7_all.deb) Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-pictures_2009-7_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-pictures_2009-7_all.deb) Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-latex-extra_2009-7ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-latex-extra_2009-7ubuntu3_all.deb) Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-latex-extra-doc_2009-7ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-latex-extra-doc_2009-7ubuntu3_all.deb) Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-recommended_2009-7_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-recommended_2009-7_all.deb) Unable to connect to us.archive.ubuntu.com http: [IP: 146.137.96.7 80]
[/INDENT]
and so on, lots of stuff.

I assume this is due to server overload, retry is proceeding fine so far.

---

### Post by legatek on 2010-04-30
Installed 10.04 64bit beta last week on two computers:

Dell Inspiron 15n: loaded proprietary Broadcom STA wireless driver, wireless works perfectly. Wired network didn't work until I blacklisted ipv6 in /etc/modprobe.d/blacklist.conf

ASUS K52F-A1: webcam was flipped upside-down. Fixed in cheese by flipping image; fixed in skype by launching with the following command: LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype.
Other sound issues, suspend issues as reported [here]("http://ubuntuforums.org/showthread.php?t=1460790&highlight=asus+K52F")

---

### Post by mistaken on 2010-04-30
upgraded yesterday, everything was working quite fine, except Network Manager could not continue and one more error, which i dint remmember. today - mounting none on /dev :D error while mounting swap :))) and unable to login :)

---

### Post by billenbois on 2010-04-30
heres my upgrade:

- ubuntu proposes the upgrade, i click yes
- ubuntu does stuff, download packages etc
- ubuntu tells me theres package problem, i can close or report bug.. ok report bug.. after 10.. just hitting close
- ubuntu tells me it just ****ed up the upgrade and gives up.. report bug or close.. ok i hit report bug.. at this point the updater ... crashes

good job! not.

here's the root of the problem:

dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.

on any package dpkg installs

---

### Post by waldgeist_di on 2010-04-30
I followed the progress of Lucid (32 bit) on my home box (custom made with Nvidia Geforce 7900 GTX) ever since Alpha2 came out. I had some minor problems (unable to shutdown properly, some services, namely CUPS, not starting automatically) but was not bothering much about those. Tried the RC (64 bit) a few days ago on my Lenovo T61p with Nvidia Quadro FX 5??M with a painless installation.

So, I thought, let's put it on my main box (Dell Precision T5400 w/ Nvidia Quadro FX 4600), again as 64 bit version. Installation's been a nightmare! I had the same problem as somebody else in this thread with the menue of the live cd displaying but no progress after selection of "Try w/o changes". After rebooting I chose to check the cd for errors which aborted due to some uncompressing problem. So I downloaded the alternative text-based installer cd and verified both image and burned cd carefully. Installation itself was smooth and then ... my box was rendered useless. Booting takes ages, GUI is presented as a garbled flickering joke of a login screen. Loggin in works (typing blindly), I can hear the welcome sound. Screen remains flickering with no content other than that shade of grey. I switched to tty1 through -6 but didn't get the prompt (invisible). Again, loggin in blindly works, so there must be some issue with X or the driver or whatever. I even installed openssh-server blindly on tty2 to be able to do some housekeeping from another system. Uninstalling any nvidia-package did not work. I am pretty p****d right now. Using the recovery console doesn't work either as I still get nothing displayed. Booting from GRUB with nomodeset instead of quit splash brings back the log of the boot process until the login screen wants to be displayed. Then the screen craps out again. Any suggestions?

---

### Post by frodon on 2010-04-30
Switch your driver to vesa in your xorg.conf so you will be back to normal, then you will have all the time you need to fix your nvidia driver issue. If you don't need 3d games then maybe just use "nouveau" the new open source nvidia driver which is better integrated to the kernel.

---

### Post by TheSqueak on 2010-04-30
I am seriously impressed with Lucid so far.

I've been running 32-bit Karmic (Kubuntu) on my home PC for 6 months, and I haven't yet got round to upgrading that - i'll wait for the servers to settle down a bit first.

I ran a fresh install of 64-bit Kubuntu onto my work laptop (A Toshiba Tecra M10), and **everything just works**

- Wireless connects flawlessly to my home network
- The internal bluetooth adapter on the laptop works - I can send files to and from my phone, and it's set up to lock the laptop if I move the phone away from it, and unlock it when I get back - again, it just works.


My only minor issue is a media codecs one, which i'm pretty certain is just down to the codecs not being there for 64-bit mplayer, but i'm sure i'll find a workaround for it.

---

### Post by thered on 2010-04-30
Haven't voted 'cos I'm sort of in between 'Upgrade - worked but had few things to fix, nothing serious though' and 'Upgrade - got many problems that i've not been able to solve'

Upgraded both my desktop and my Acer 5738z laptop. Still looking but I know that Vuze doesn't work, not the end of the world, I'll use Transmission. 

The worse problem, which I haven't resolved is that my touchpad has stopped scrolling. This is soooooooooo annoying.

I'm also experiencing intermittent 'flickering' fo the screen on the Acer. Intel chipset.

---

### Post by bredman on 2010-04-30
Just found a way to upgrade karmic to lucid behind a proxy. I hope that this helps anybody else who is stuck behind a proxy.

Launch Synaptic Package Manager
Select Settings/Repositories
Untick everything in the "Ubuntu Software" tab.
Untick everything in the "Other Software" tab.
In the "Other Software" tab, click "Add" and enter "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main"
In the Synaptic Package Manager main screen, click "Mark All Upgrades"
In the Synaptic Package Manager main screen, click "Apply"

Sit back and watch the magic...

Note that the Synaptic repositories seem to return to default after the upgrade. If you use any non-default repositories, you will have to tick them again.

---

### Post by Jonners59 on 2010-04-30
> **billenbois said:**
> heres my upgrade:

- ubuntu proposes the upgrade, i click yes
- ubuntu does stuff, download packages etc
- ubuntu tells me theres package problem, i can close or report bug.. ok report bug.. after 10.. just hitting close
- ubuntu tells me it just ****ed up the upgrade and gives up.. report bug or close.. ok i hit report bug.. at this point the updater ... crashes

good job! not.

here's the root of the problem:

dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.

on any package dpkg installs

I had similar with one of my machines.  I don't know how to recover it.  If I install a new U OS then it wants to uninstall the old....  does that delete all my files?

Or could I install a second version and copy over key folders...?  If so how as above does not work?

This is a night mare.  I started at 4PM yesterday and worked through the night on it.

---

### Post by suryaccnamcse on 2010-04-30
I installed 10.04 LTS and it worked flawlessly, I had tested the 10.04 RC, it was a bit buggy and it took some time for the wireless to work and it had problems in some applications like gwibber. This has been ironed out in the Lucid complete version.

---

### Post by m00ndancer on 2010-04-30
> **IBadget said:**
> I tried to upgrade to 10.04 from 9.10, but during the installation of the downloaded packages, I got an error message saying that Network Manager could not continue because it could not find required resources. When the upgrade was finished, upon reboot, I only got as far as the log-in sound and the laptop locked up. Even the power button was unresponsive, so I had to unplug it and let the battery run out to shut it off. I did a clean reinstallation of 9.10. I am using a Sony PCG-GRT240G Notebook.

Same here, so I rebooted with the recovery option kernel.
Let it try to boot and then got a login prompt.
No GUI! Only a terminal. Logged in and started Gnome with the command gdm
Got the login splash, logged in as usual and it started up ok. 

Restarted and the install works now.

---

### Post by waldgeist_di on 2010-04-30
> **frodon said:**
> Switch your driver to vesa in your xorg.conf so you will be back to normal, then you will have all the time you need to fix your nvidia driver issue. If you don't need 3d games then maybe just use "nouveau" the new open source nvidia driver which is better integrated to the kernel.

I wish I could do that. But there is no way to get a console whatsoever. And hopefully you don't want to make me doing the configuration change blindly. I guess the only chance would be to use a live cd and edit xorg.conf on the system from there. Problem: Even a live cd won't start up properly, despite using nomodeset. I am at a loss.

***edit***
Ha, wait! Why would I want to take the Lucid cd? Haha, I'm gonna take an older one. I'll give it a try, FRODON, and report back.

---

### Post by greenwc on 2010-04-30
> Failed to create file system

...when attempting to install.  Attempting to install RAID1 system using Gigabyte UD3P onboard software RAID controller.  Installer detects the RAID array but when it goes to actually create and format the partition, the above error shows.

Any one else?  I found this open bug:

[Bug #568050]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/568050")

---

### Post by cludwig on 2010-04-30
Opps...  I tried to upgrade from 9.20 32 bit to 10.04, but I bricked my computer instead.  All I get is a grub rescue prompt saying the grub put is not found.  I guess I should have backed up before I started.  Thank god for live CD's!!

So I guess one place that the community needs to work on is making the grub upgrade choices a bit more intuitive.

Since I need to do a fresh install, should I be switching to 64 bit now?  Last time I tried, it didn't like my nvidia card too well.  To be fair, my nvidia card hates life in general and is difficult to get along with.

---

### Post by frodon on 2010-04-30
> **cludwig said:**
> Since I need to do a fresh install, should I be switching to 64 bit now?  Last time I tried, it didn't like my nvidia card too well.  To be fair, my nvidia card hates life in general and is difficult to get along with.you don't need to, reinstalling GRUB will take you 5 minutes with a liveCD and you will be back to normal.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by manubsu on 2010-04-30
I hope Ubuntu isn't going to turn into OpenSuSE. 

Years ago SuSE was one of the best Linux distros  on the market. It started to get buggy and wouldn't fix many of their problems. They finally went to OpenSuse which isn't very good.

It looks like Ubuntu is following this same pattern.

---

### Post by maizuddin35 on 2010-04-30
I upgrade my Ubuntu Lucid Lynx from beta version. 
At first I had it run nicely, with the compiz and effects and stuffs, it was just great. Still there is some bugs handling the beta version. ofcourse, it is a beta version.And when the time comes to upgrade to the full release,I update and upgrade everything. The process went good. But when I restart it I found that, the I cant used the compiz manager anymore, and some of the application I already installed in the beta version, cannot be used, such aptoncd, and plus, the performance is a little bit slow, I dont know why.
Right now, I'm searching a way to solve this thing.

If I dont find a way to solve this, I would just install it from the start again. Do a fresh install. I hope , I dont do that, because eveything, I install , the theme, the apps, and then again, I need to install it again. It just a waste of time for me as the internet connection at my place is not that good.

---

### Post by reidm on 2010-04-30
Warning: Do not perform an upgrade with a Bluetooth mouse attached. When the upgrade prompts to overwrite gnome defaults the bluetooth mouse is dead and plugging in a USB mouse does not work. It will not allow you to use the keyboard to switch to the window prompting a response either. Alt-Tab and all other switching options are disabled at that point. 

Fortunately I still have another hard drive with Fedora on that I am using to download the Ubuntu Alternate install CD to see if I can recover my system.

---

### Post by Silvertones on 2010-04-30
I'm scared to death to upgrade. Has the issue with grub not showing the alternate OS (Windows) been fixed? If Lucid goes to hell if i can at least access the Windows partition then fine but if it craps out the whole thing i'd be in a mess.:(

---

### Post by waldgeist_di on 2010-04-30
> **waldgeist_di said:**
> I wish I could do that. But there is no way to get a console whatsoever. And hopefully you don't want to make me doing the configuration change blindly. I guess the only chance would be to use a live cd and edit xorg.conf on the system from there. Problem: Even a live cd won't start up properly, despite using nomodeset. I am at a loss.

***edit***
Ha, wait! Why would I want to take the Lucid cd? Haha, I'm gonna take an older one. I'll give it a try, FRODON, and report back.

Well, hit a wall again. My older Intrepid cd wouldn't let me edit the xorg.conf because it didn't like the ext4 file system where my new system is living now on. I sure could eat a broom, as we germans say (translated literally :)).

Finally I managed to use the recovery console with option "nomodeset". I discovered that there is no xorg.conf, only xorg.conf.failsave. I cp'ed it to xorg.conf, since VESA is already selected in the failsave version. Now booting won't work properly since it seems that VESA requires "nomodeset" activated during boot-up which I didn't choose for the next start. It's a mess!

---

### Post by frodon on 2010-04-30
Don't give up this doesn't look like an impossible to solve issue.

If you can get the recovery console take advantage of this to install/re-install either the nvidia driver or the "nouveau" driver and select to use it through xorg.conf, check as well if you don't have any package that can be updated via apt-get.

---

### Post by slvr42 on 2010-04-30
Finished the upgrade last night on my Studio Box.  OS seems to work great though I notices not all the applications got installed.  I think it has something to do with not having versions of them in the first place.  Is there a list of every package/app that is installed with Lucid?

Web Browsing, Office, seems to work well though some of the audio apps, jack, synth, etc don't seem to like the update.  Ah well that's what I get for living on the bleeding edge.

---

### Post by pavera on 2010-04-30
both Upgrade and clean install in vmware fusion results in no keyboard support whatsoever.  Cannot log in, cannot do anything but boot to single user mode.  Seriously guys? No one tried to install this in vmware?

Also, would be nice if there was at least a notice during the boot of "press shift to configure grub" instead of having to read pages of release notes to find that little tidbit to even boot into single user mode to copy files out of my upgrade so I can actually work today...

Anyway, because the keyboard works fine in single user mode and because it works during grub configuration I know it is not a keyboard issue or even necessarily a low level kernel issue... It must be an x.org config issue or gnome config issue?  No clue where to start debugging this though...

---

### Post by PJW9779 on 2010-04-30
Just did an upgrade to Lucid on AMD-64.
Near the end of the install of the upgrades it died.
A hard reboot resulted the messages
   Mount: mounting none on /dev failed : no such device
   Chroot: can not execute /etc/apparmor/initramfs : No such file or directory

Not pleased, since this was a known bug just days ago.

---

### Post by cespinal on 2010-04-30
Flawless upgrade here. Took me 5 hours. Everything works ok and the system boots quite fast. Usplash is horrible tho :P... Screen keeps black with a white cursor blinking on the upper left for a few seconds. Then the kubuntu screen appears for a fraction of a second... goes black again, and then im greeted with the KDM... 
I believe this is completely normal...

---

### Post by aglc2005 on 2010-04-30
*Upgrade - got many problems that i've not been able to solve*

Upgraded from 9.10. I have no HID support through USB, at all. I cannot find an issue with anything, it just doesn't work. I have also tested out other USB devices, which all work, it's only HID devices. My mouse is a Logitech MX610 with my keyboard being a Logitech S520. I get confirmation flashes from the wires adapter on the keyboard so I know it is connecting, it just doesn't work. I am currently using a PS/2 keyboard to operate the computer so that I can get all my data backed up and do a fresh install (not happy about that though).

---

### Post by POI09 on 2010-04-30
> **Silvertones said:**
> I'm scared to death to upgrade. Has the issue with grub not showing the alternate OS (Windows) been fixed? If Lucid goes to hell if i can at least access the Windows partition then fine but if it craps out the whole thing i'd be in a mess.:(


All has went well for me except the boot screen is at a lower resolution that in should be making it look like crap & compiz is supposedly installed but I can't find it anywhere.Oh,and Firefox is extremely slow in loading pages.Any other browser works great.

---

### Post by wbee on 2010-04-30
Hello,

I did a fresh install,using the option to use the entire hard drive for 10.4, Desktop,i386,32 bit.

---------
 
+ The install went perfectly and all the stuff I added from the Synaptic Package Manager came down and installed properly.

-------------

- This morning,when I booted up,the process would not proceed beyond the opening Ubuntu Trademark screen. I turned off the power,tried again, and it booted properly.

- There seem to be a few minor bugs in the Gnome desktop. 

1.When I booted,the function on the bottom panel letting me choose among four desktops was missing.

 2. When I went to Firefox from the icon on the top panel,it repeated the icon on the bottom panel-on the location where the desk top's option had disappeared.

3.The speaker icon on the top panel was missing,though the volume still works fine.

But on the whole,a positive experience.

---

### Post by Samuraidog on 2010-04-30
Went well for me. I upgraded via Update Manager on both my desktop (formerly 9.10) and netbook (9.10 NBR). My desktop is a dual boot with Win XP. Win XP shows up fine when booting (even though I haven't actually used Win XP yet).  To be on the safe side, I made sure I backed up everything before the update.

---

### Post by waldgeist_di on 2010-04-30
> **frodon said:**
> Don't give up this doesn't look like an impossible to solve issue.

If you can get the recovery console take advantage of this to install/re-install either the nvidia driver or the "nouveau" driver and select to use it through xorg.conf, check as well if you don't have any package that can be updated via apt-get.

Thank you, frodon! I just read your messager *after* doing almost exactly what you proposed. I updated the system and installed nvidia-current. Restarting X with nvidia-xconfig crashed the whole system, but after cold restart everything's fine now (at least, as far as I can tell).

Nvidia-setting is reporting the current driver but the "check for hardware driver" (from third parties) reports the nvidia-current driver as being installed but not in use. I can't believe that as nvidia-settings says the driver *is* in use. Compiz seems to work, so there must be some kind of 3d acceleration.

---

### Post by itiswhatitis on 2010-04-30
I upgraded from Beta 2 to RC and now LTS.

Everything is working fine.  There were a few settings I had to change in compiz, which was not installed.  Fixed that through a quick deselect and select in Synaptic.

All other apps are working fine, and my wife's karmic laptop is still quite happy to talk to the printer on my computer.

---

### Post by waldgeist_di on 2010-04-30
> **cespinal said:**
> [...] Usplash is horrible tho :P... Screen keeps black with a white cursor blinking on the upper left for a few seconds. Then the kubuntu screen appears for a fraction of a second... goes black again, and then im greeted with the KDM... 
I believe this is completely normal...

I see the same behaviour with GNOME. But now at least I do see the screen, haha!

---

### Post by Jerubaal on 2010-04-30
Just downloaded the alternate amd64 iso in under 3 mins! (And the MD5sum matches :P)

Now I just need child-free time to install it :(

---

### Post by ratcheer on 2010-04-30
My upgrade from 9.10 to 10.04 using Alternate CD image went **great**. The only significant problem I have found, so far, is the ALSA driver did not get upgraded. It only took a few minutes to fix that, manually.

Tim

---

### Post by P4man on 2010-04-30
View the poll here:
[http://ubuntuforums.org/poll.php?do=showresults&pollid=6556](http://ubuntuforums.org/poll.php?do=showresults&pollid=6556)

Keep in mind the bias of people posting here coming here because they have a problem.

---

### Post by itachisxeyes on 2010-04-30
well i backed up everything and did a full install because i'm going from x86 to amd64 but i have not had a single problem, this is defiantly a step forward, as most Ubuntu releaces are.

---

### Post by mpjbrennan on 2010-04-30
Net upgraded from Karmic and encountered only two problems - low screen resolution and Firefox couldn't find its icon. Fixed the first by installing nVidia drivers and the second was trivial. All working perfectly now. As far as I can see all my personal settings were preserved.

I am still looking for the minimize/close icons at the top RHS of the window but I guess I'll get used to that soon.

Patrick

---

### Post by Elwro on 2010-04-30
> **mpjbrennan said:**
> Net upgraded from Karmic and encountered only two problems - low screen resolution and Firefox couldn't find its icon. Fixed the first by installing nVidia drivers and the second was trivial. All working perfectly now. As far as I can see all my personal settings were preserved.Amazingly, this is exactly my experience, too (screen res + Firefox icon). Anyway, since everything important seems to be working, I'd say the upgrade was almost flawless.

---

### Post by Ederico on 2010-04-30
My experience was a disaster, and none of my Linux systems are working right now (I have Kubuntu installed on a desktop PC, an external drive, and my laptop). They're not for the same reason, they didn't work after some upgrade. Latest to go is my laptop, the others I just left alone because I could cope and I didn't have time to waste on this stuff. Frankly, I'm terribly annoyed. I wrote about my experience and frustration in the following thread:

[http://ubuntuforums.org/showthread.php?t=1383167](http://ubuntuforums.org/showthread.php?t=1383167)

I wasted this whole morning, the afternoon now, and potentially the evening tried to get a working Kubuntu system. Just what I need when I should spend my days studying or doing something productive. GREAT! I'm sorry but a "well done" can't be forthcoming from my part, what is even most annoying is that this community doesn't appear to be so responsive in terms of help as it used to be. I've been using Linux for years now, either Ubuntu or Kubuntu, I'm starting to regret it. :(

---

### Post by ajnueva on 2010-04-30
Thanks a million, Frodon. I`ll try and I will tell you the results.

---

### Post by sports fan Matt on 2010-04-30
Mine went well as well.  There may have been a few quirks trying to get out of low graphics mode but nothing terribly bad

---

### Post by komensky on 2010-04-30
It was a dandy process.

---

### Post by ajnueva on 2010-04-30
> **frodon said:**
> You might have installed GRUB on the wrong drive, nothing dramatic don't worry.

I would advice you to just re-install grub, you will find needed information there:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Are%20you%20using%20Grub%20or%20Grub%202?](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Are%20you%20using%20Grub%20or%20Grub%202?)
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)


Thanks a million, Frodon. I'll try and I will tell you if it works.

---

### Post by prshah on 2010-04-30
> **Silvertones said:**
> I'm scared to death to upgrade.

> **itachisxeyes said:**
> did a full install because i'm going from x86 to amd64

Apparently the GRUB problem IS fixed; I say apparently because I never did have a problem (since I have no dualboot).

My upgrade went smoothly, as have my previous upgrades from Gutsy-> Hardy-> Ibex-> Jaunty-> Karmic-> and now Lucid.

However, I too am at long last going for a fresh install to take advantage of x64 features, which I think will allow me faster video processing, number crunching etc.

I am putting a new HDD and saving the old one till I transfer all the data, cause I have too much user-created content and stuff to risk.

---

### Post by Greymatter on 2010-04-30
For a noob things went well. I downloaded 10.04 to a USB stick and did a clean install. It went rapidly with no errors. Having tried a previous upgrade with the RC I was pleasantly surprised at how the clean install went.

---

### Post by Scari on 2010-04-30
I'm sorry I clicked upgrade now I think someone rushed this out, dist. upgrade window has been stuck on installing the upgrades for HOURS now saying 16 minutes left and now I'm afraid to do anything I shoulda just stayed at 9.10. Took HOURS just to get this far now it's been HOURS stuck on this screen Ubuntu and all other Linux versions thereof have been easy to install until now. I'm not happy at all :(

---

### Post by pvonbert on 2010-04-30
I upgraded from 9.10 to 10.04 on 4 computers, all different hardware w/o any problems. It even got the Grub sorted out on my main workstation flawlessly. KUDOS to all involved. At home my flaky USB Wi-Fi stopped working on the update, so I plugged in a new one (other brand), and it found it, and started it automagically.

---

### Post by reidm on 2010-04-30
> **reidm said:**
> Warning: Do not perform an upgrade with a Bluetooth mouse attached. When the upgrade prompts to overwrite gnome defaults the bluetooth mouse is dead and plugging in a USB mouse does not work. It will not allow you to use the keyboard to switch to the window prompting a response either. Alt-Tab and all other switching options are disabled at that point. 

Fortunately I still have another hard drive with Fedora on that I am using to download the Ubuntu Alternate install CD to see if I can recover my system.

After booting with the Recovery option from the install CD, I was able to complete the upgrade by running the following command:
  ```
dpkg --configure -a
```

Everything is working perfectly now. Bluetooth, Wireless, Dual displays, all working. :)

---

### Post by cuberts on 2010-04-30
> **Silvertones said:**
> I'm scared to death to upgrade. Has the issue with grub not showing the alternate OS (Windows) been fixed? If Lucid goes to hell if i can at least access the Windows partition then fine but if it craps out the whole thing i'd be in a mess.:(I will be updating it today, and none of the other updates that I have done have caused me any problems, so I hope that this one goes well too

---

### Post by kill4killin on 2010-04-30
Only issues I had were with the beta installs, all RC and release installs were flawless (definitely helped reading the release notes and changing the block size from 1MiB to 512K again since my computer is several years old :rolleyes: ).

Next up is UNR 10.04 on my EEE901 I'll report back if there are any issues.

---

### Post by leonhook on 2010-04-30
> **Scari said:**
> I'm sorry I clicked upgrade now I think someone rushed this out, dist. upgrade window has been stuck on installing the upgrades for HOURS now saying 16 minutes left and now I'm afraid to do anything I shoulda just stayed at 9.10. Took HOURS just to get this far now it's been HOURS stuck on this screen Ubuntu and all other Linux versions thereof have been easy to install until now. I'm not happy at all :(
its probably because lots of people are trying to upgrade at the same time and slowing the servers down.

i upgraded from karmic to lucid RC and then ran update manager this morning and only had about 10MB to install and took about 2 mins.
all in all my upgrade worked perfectly. Long Live Ubuntu, Die Windows. :lolflag:

---

### Post by vettie on 2010-04-30
I used the Update Manager. All went well and relatively fast. (from 9.1 to 10.4 Final)

Only issue I had was that 10.4 would not shut down via GUI not matter what button was clicked. Had to use the manual shutdown -r now command.

Booted up this morning and checked for updates and then did the shutdown to see if it was still and issue and everything worked fine.

I have not had the "slow" firefox issue that some are noting, in fact, I have had no issues once the shutdown issue "fixed itself".

Good Luck

---

### Post by jerome1232 on 2010-04-30
> **Scari said:**
> I'm sorry I clicked upgrade now I think someone rushed this out, dist. upgrade window has been stuck on installing the upgrades for HOURS now saying 16 minutes left and now I'm afraid to do anything I shoulda just stayed at 9.10. Took HOURS just to get this far now it's been HOURS stuck on this screen Ubuntu and all other Linux versions thereof have been easy to install until now. I'm not happy at all :(

Probably because the servers get slammed every time there is a distro upgrade.

Which is why (imo) it's best to torrent the alternate install iso (offloads server traffic since we are all uploading and downloading from each other) and lets you do the upgrade process quickly.

---

### Post by 98cwitr on 2010-04-30
from beta to full:
Upgrade - worked but had few things to fix, nothing serious though

---

### Post by llong0415 on 2010-04-30
I perfromed an upgrade from 9.10 to 10.04, other than a problem with a plug-in for Firefox every thing went extremely well. The plug-in was Moonlight and I uninstalled with Synaptic. I found the answer on the forums here.

---

### Post by Jordanwb on 2010-04-30
I got a computer running Server 9.10 I was going to upgrade it via "do-release-upgrade -d" or whatever, but it doesn't recognise 10.04 as an LTS so I had to change prompt to "normal". Then it wanted to download a bunch of gnome and x11 garbage. I had installed xubuntu-desktop but I had removed it because the OSS radeon drivers can't handle S-Video output properly. (Apparently "apt-get purge --auto-remove xubuntu-desktop" doesn't remove EVERYTHING xubuntu-desktop pulled in.)

So I'm downloading the ISO and doing a clean install. I hope I don't have to do a clean install on my parent's machine.

Hey I've been using Ubuntu for three years now.

---

### Post by b00n on 2010-04-30
Went from latest 9.10 to 10.04 -- aside from issues noted earlier (recommended replacements for apps going unsupported; server is overloaded):

 - a few icons do not work: emacs, firefox, maybe others
 - I have an Emacs start on login and it came up very small (maybe 1 char x 1 char)
 - Screen background went from one of the default images to white

I have only just poked at it so there may be other problems, but nothing else obviously wrong.

Wired keyboard, mouse, Ethernet; Nvidia dual-DVI board; 5+ years old Intel x86; 1xHDD, 1xCD/DVD, floppy (untested, but I don't have any floppies anymore).

Yay Ubuntu!

---

### Post by crienoloog on 2010-04-30
Got stuck half-way... I think it had something to do that I had installed a 32-bit [9.10] on a 64 machine [which was my choice] and the upgrade was confused and couldn't upgrade the 32-bit with the 64-bit which he reconned it had to install, recognizing the 64-bit machine.
Probably have to reinstall everything from scrap... damn
What should have happened that the devs should have made it an option for 64-bit machines to install either version.

---

### Post by lechien73 on 2010-04-30
Gah! Wish I could change my vote. I voted that I'd had problems with the upgrade, but it turned out to be a BIOS problem on my machine, and a BIOS update fixed it.

I wonder how many other people vote in the heat of annoyance. As the disclaimer on the first page says, the stats are probably not representative of reality.

Matt

---

### Post by katzsper on 2010-04-30
Lost my Windows XP and Windows Server 2008 R2 boot options after upgrade. Grub 1.97 beta changed to Grub 1.98 Ubuntu. Works well with unices but seems to frown at windows.:(.

---

### Post by Jordanwb on 2010-04-30
> **katzsper said:**
> Lost my Windows XP and Windows Server 2008 R2 boot options after upgrade. Grub 1.97 beta changed to Grub 1.98 Ubuntu. Works well with unices but seems to frown at windows.:(.

I think that was a bug in grub. A recent update should fix it.

---

### Post by nezurian on 2010-04-30
I am having graphical problems with lucid lynx. 

I have a Philips brilliance 200W monitor and a geforce mx440 graphic card. I downloaded the iso. and tried to install using wubi.(I tried installing it with boot too) after system reboots itself, the installation screen takes it's place in the top-left quarter of the screen, and the colors are greenish, and there are some distortioned-flashing stripes on the other parts of the screen. 

What ever, I've manage to install it. the screen was maintaining the greenish top-left quarter stuff. I've manage to change some kind of hertz and resolution - 75 hertz and 1024x768 - and my colors were back, and the screen alignment become proper. BUT. 

I am using karmic atm with a lot higher resolution (something like 1600's) using envyNG. First, I cannot install envy- and without installing it, I think ubuntu does not choose the prober driver for my monitor\graphic card. And also, I was able to install karmic "without" any kind of problems like that I experienced with lucid. I quite don't understand what's wrong, and wondering if someone experiencing this kind of problem too. 

I cannot find a solution atm, but I keep trying. If I find something, I will let you know :)

---

### Post by b00n on 2010-04-30
One more nit: I had 9.10 set up to blank the screen when idle, but not ask for login.  After newgrading to 10.04 it asks for login.  Easy to fix (System -> Preferences -> Screensver), but it looks like something accidentally stomped on some configuration bits.

---

### Post by abyteofozz on 2010-04-30
.

---

### Post by movieman on 2010-04-30
> **jerome1232 said:**
> Probably because the servers get slammed every time there is a distro upgrade.

Server performance affects download time, not upgrade time. In my case the updates downloaded in 20 minutes and installing them took over three hours.

Near the end of the install process I ran top to see what was going on, and for some reason the automounter was using around 90% of my CPU time... I've no idea what might have triggered that.

---

### Post by carlosgs91 on 2010-04-30
Hi, Ubuntu 10.04 is much more easy to use and user-friendly. I've had it since alpha 3 and I have it up to dated. The only problem I have is the touchpad in Gnome (not in Kde, login screen...) and I haven't solved it yet, but I think it has to have a easy solution, I'll find it.

In 8.04 sound didn't work and I had to do a lot of things to get it working, in 10.04 it worked since first time.

Drivers are easy to install, I bought a HP printer with scan and I thought I would have problems to get it working. I just plugged it in and then I went to print, I clicked to add printer and the setup detected my HP printer and downloaded the driver automatically. It worked without any problem. The graphic card driver (ATI Radeon) was easily installed by just going to hardware drivers. Wi-fi was also easily installed by activating it in Hardware drivers. The only thing I'd suggest would be to add all the wi-fi drivers in the CD, so if a person does not have an ethernet link he can get the Wi-Fi driver and then install the rest from the Internet.

The theme is much more better than the old one but I prefer to use Elementary themes: [http://elementary-project.com](http://elementary-project.com) I'm using Unified and I'd prefer Ubuntu to have a theme more similar to this one by default, or at least come with it, but it doesn't matter as I can change it.

Also I would recommend you to put 8-size fonts by default instead of 10. I know, you can change it, but new users should see a nice desktop environment for the first time and then customize it.

---

### Post by madHatterCutsTheChatter on 2010-04-30
mounting cd doesnt do anything.
I ran the gksu command as mentioned in the website, even that didn't work.

---

### Post by nicfallenangel on 2010-04-30
Fresh install using WUBI on both work and Home using 64-bit. No crashes, just waiting now for everyone to stop hammering the repositories so I can get Cinelerra and a few other "needed" packages.

:KS

---

### Post by jblackthorne on 2010-04-30
Thought I would add that my upgrade on a HP dv6700 laptop went flawlessly. 

Details:
I downloaded the "Alternate Install" cd, burned it, and popped it in the drive while already logged into the Karmic.  Ubuntu auto-detected the disk and presented some options, one of which was to perform a distribution upgrade.  The install was over an existing Karmic x64 install that has encrypted home directories.  

The upgrade took over 3.5 hours to complete.  Though, that is probably because I have Ubuntu Studio and a lot of aps on this machine too.  Once the install finished, the first boot went into low resolution mode.  Thus, I logged in and used the hardware applet to choose the latest Nvidia driver.  A quick reboot and all hardware and applications work perfectly.  This is my first flawless upgrade of Ubuntu ever.  To date, there has always been one issue or another that required correction.  Karmic, for example, was so bad I nearly gave up on Ubuntu and moved to Fedora.  Awesome job Ubuntu team!  10.4 is the best release experience I have personally ever had with an Ubuntu distribution.  Great work!

---

### Post by JaRRoslav on 2010-04-30
Disaster!

Upgrade 9.10 UNR --> 10.04

Toshiba NB100

- after 1st restart screen froze, had to shut down hard
- netbook-launcher disappeared for a while
- after 2nd restart netbook-launcher appeared, but when I opened something, panel disappeared (went something like invisible)
- so I tried to login to xfce4. It went fine. I added panels there. After logging to gnome, panels there were not on their places and screen froze (another forced shutdown)
- after reboot (another) i logged in gnome (another freez, some error with ICEauthority and forced shutdown)
- I managed to login to xfce4 trough recovery mode like root and set option to show login screen, but when I started my netbook and tried to choose xfce4 it tried to login but I ended in login screen

The result of this everything is that i have to log as root via recovery mode to xfce if I need something from my ext4 partition.


+ issue with two or more screens was fixed
+ screen switch button finally works

EDIT: if I login to gnome session as root via recovery console, everything is fine

EDIT: I uninstalled netbook-launcher and everything is fine :-D

---

### Post by wd5gnr on 2010-04-30
Fun fun... I decided to let it upgrade while I went to dinner. Well, that didn't work out, because it kept asking me questions. Finally it starts installing. Got a problem with apt! But it says it will keep going. Goes for a long time. 

Finally tells me too many errors, system is unstable. Too bad. Great. Finally tracked it down to a problem where the apt post install wants to read gconf (this is kubuntu; yes I filed bugs on everything I found and fixed). So a few comments and the system is able to configure itself finally.

But... somehow the NVidia drivers aren't happy. So I reinstall them. No, now the OpenGL versions are out of whack. I reinstall the driver, but on each reboot DKMS helpfully recompiles the driver and breaks OpenGL. Lucky I am good with the console and have Fluxbox installed as a backup.

Oh. And the awful Plymouth graphics with NVidia. Turns out putting a vga line in the Grub and regenerating fixes that nicely.

Unfortunately -- not the installer fault -- I decided to try to get grub to see my USB keyboard which it never did before. Something about loading USB modules in grub causes it to crash and reboot and there seems to be nothing you can do about it. Download a rescue CD. Burn it. Boot. Go comment out the USB insmods. Everyone happy again. Reboot, fix Grub, reboot again. Works. But here's the funny part -- now the USB keyboard works (I  renamed uhci.mod -- maybe that was the problem?) 

Had nepomuk working. No more. Go kill the database. Now it works. 

Virtualbox really wants hald running. Add that to rc.local. Had /proc/bus/usb mounted for VirtualBox. That causes grief on start up so removed it. VirtualBox happy.


Total time including waiting for prompts when I wasn't there? About 14 hours.

In the end, since I had up to date KDE, I'm not sure what I got out of this. Well my USB keyboard now works with grub but that was an accident. 

Also note that the new install put the keyboard notifier in my notify area. Telling it to always hide does nothing. Not a big deal.

---

### Post by eltonw on 2010-04-30
Initially, I updated, then installed the patched kernel. **This method is very, very long.**#-o
1) The servers are overloaded / busy, and 2) you have to respond to various confirmation dialogs.

[FONT="Verdana"][CENTER][COLOR="DarkGreen"]_How I installed Ubuntu LUCID LYNX 10.4 LTS (UNE):_[/COLOR][/CENTER][/FONT]

**On Asus EEE 1000 PC in Karmic, using an SD memory card.**

• Download ubuntu-10.04-netbook-i386.iso

• Download Ricardo Saveti's [COLOR="DarkRed"]patched kernel[/COLOR] from:
[http://rsalveti.net/pub/ubuntu/kernel/lucid/linux-image-2.6.32-21-generic_2.6.32-21.32rsalveti1_i386.deb]("http://rsalveti.net/pub/ubuntu/kernel/lucid/linux-image-2.6.32-21-generic_2.6.32-21.32rsalveti1_i386.deb")
     **/REM:** Copy this package to the root directory of the SD card to have it at hand, 
since I *know* I wouldn't be able to connect after initial installation.

• Use the Startup Disk Creator and burn the iso to a 2Gb SD card

• VERIFY md5sum of ISO

• Install from SD, using MANUAL partitioning (since the EEE 1000 has 2 SDDs)
sda [8 Gb] used for / with a 403 Mb swap (end of the partition)
sdb [32 Gb] used for /home
     **/REM:** both partitions formatted ext4

• After initial reboot, Lucid does not connect (*as expected*)

• Install linux-image-2.6.32-21-generic_2.6.32-21.32rsalveti1_i386.deb
     **/REM:** Wireless (WPA / WPA2) connection works!

• Launch Update Manager to download latest updates from the channel.
=D>

---

### Post by twallace on 2010-04-30
Here we go again...was all excited to give the new version 10.04 a try and hoped the resolution issues of past had been resolved. O well, wishful thinking didn't work as my laptop is once again stuck in 800 res mode!!! When o when will this ever be addressed so we can hit the mainstream???

---

### Post by 23dornot23d on 2010-04-30
Things that do not work

Grub .... all entries point to the wrong boot device now ... not sure how to fix this ,,,, 
( This is now ok for anything on drive 2 - Just for Info - only one entry points to wrong disk .... 2 instead of 0 )

Nvidia GS9300 ..... does not pick it up at all now ..... yet did in all previous versions .....
tried setting up again ..... picking new hardware and running nvidia-xconfig .... no luck.

Windows Programs CD/DVDs ..... cannot install from them .... need to make the exe ... executable in Linux
**NOT** possible on CD/DVD ..... without copying full contents of CD/DVD onto hard Drive first .... if it allows it.

Firefox ..... after watching a video ...... mouse pointer/movements selections become unstable ....... 
also did the same after using Wings3D ..... don't know if they are related problems or not .....

Still finding things out ....... so maybe more to come ...... :guitar:

---

### Post by Dubbayoo on 2010-04-30
64-bit upgrade from 9.10. Two issues both easily fixed. 

1. Had to comment out one line in /etc/fstab added for VirtualBox
2. fglrx driver didn't install cleanly; removed it and installed ATI proprietary driver.

Haven't come across any other issues yet.

---

### Post by Jordanwb on 2010-04-30
Just finished upgrading to 10.04 on my parents computer and it went very well. There were/are only two issues:

1) The Firefox icon on the desktop did not work (recreating the shortcut fixed this)
2) An error early in the boot sequence about sreadahead not starting (something like "Init: failed to start sreadahead process: failed to execute: file or directory not found")

everything-went-better-than-expected.jpg

---

### Post by parn on 2010-04-30
When I saw that upgrading through the Net was the "recommended" method :P I went download the alternative iso to avoid the jam. Past experience tells me that upgrading through overworked servers may be disastrous.. and

Very smooth update from koala -> lynx using only alternative CD. Took about 2 hours to upgrade on my Acer TravelMate 8100. Only issues I have are some minor software/application issues but that is understandable.

The ubuntu team did a great job.

---

### Post by osjak on 2010-04-30
Summary: very good experience installing.

I decided to format the drive and install from scratch, this way all dead weight programs I had installed since 9.04 would be gone. The install went smooth, had to wait a bit for those repository servers to give me my files, but that is expected on the release day. I've got a pleasant surprise - whatever drivers Ubuntu guys changed, but my microphone works now. That was my only gripe about previous Ubuntu versions, but now it all works as expected. I changed the coloring theme for controls (menus and context menus) because the default theme did not work well with Skype. Love the new dark window headers though.

Advice: USE TORRENTS to download Ubuntu images. They are fast, and don't saturate Canonical's servers.

---

### Post by oldmangamer on 2010-04-30
Tried to use live CD 64-bit for Intel Core i7-720 with nVidia GTS250. After responding to install question, no further activity. After 25 minutes I gave up.

---

### Post by POI09 on 2010-04-30
What exactly is going on with the low resolution boot screen?
It looks awful,any suggestions?

---

### Post by dadgetboy on 2010-04-30
Overall, it was pretty painless. However, while upgrading from 9.10 to 10.04 I shutdown my computer. When I booted it, the GUI was gone; but I was still able to login into a shell using Ctrl+Alt+F1; from there I ran 

```
sudo dpkg --configure -a
```

followed by

```
sudo apt-get upgrade && sudo apt-get dist-upgrade
```
.

My interruption in upgrading was fully resolved, and I am typing this using my (new, and fixed) Lucid Lynx.:P

---

### Post by georgemc on 2010-04-30
First off:  Good job, well done.

I clean installed with out any thing going wrong on 1 Dell desktop and 1 Asus A2500 laptop.  These were 9.04 and 9.10 respectively and I keep my home directories on a separate partition.  I also save my synaptic markings and was able to load every thing with out any troubles.

My 3rd clean install went well except for the NVIDIA drivers.  This I was anticipating and this is the only glitch.

Again: Well Done and Thank You to all the developers.

George

---

### Post by abickerton on 2010-04-30
On a Lenovo R60, the update via the update manager went flawlessly.

It just plain worked ... :-)

Me stunned.

---

### Post by Kaput1982 on 2010-04-30
I did a clean install, and it went great.  No problems.  I'm trying to get my applications re-installed, and that is taking forever.

Update: I was unable to install printers (the add printer button was grayed out).  After a reboot the problem went away, and all my printers are installed.

---

### Post by Johnr123 on 2010-04-30
The last two upgrades have done nothing but downgrade my user experience. I love Ubuntu for all it stands for, and for all it points to for the future--but for the average user it just isn't anywhere near there yet.

I have a descent system with hardware that was supported fine two upgrades ago. My printer worked excellent, as did my scanner, and my Logitech QuickCam Pro 9000 webcam. The next two upgrades eroded my print functions, stopped my scanner from working altogether, and downgraded my webcam to the point of uselessness (and this is a popular webcam). 

Somehow I could live with all that, but I also use my system as a local server for web site development. I have set up a perfectly functional name-based local apache2 server with php and mysql, using phpmyadmin as an interface for the databases. It has functioned flawlessly--until the upgrade to Lucid that is! 

My server is now not communicating to the Mysql databases, and I cannot get my Webmin program to open at the local address it operates on, nor can I open phpmyadmin. Apache is running fine, as is php, but without mysql all is for naught. 

Yes, I could spend a week or two troubleshooting, as I have done in the past (I'm not an expert, but I'm no slouch either), but do you know what? I am tired of all this. It reminds me of a vehicle I used to own. I loved it, but it wasn't worth the effort. I had to constantly have a tool box with me and had to pull over regularly to use it. 

And it's not just the above. I have an iomega external hard drive that was functioning perfectly on Karmic. Once I saw the problems on upgrade to Lucid, I wanted to access the backups of my system to fix the server problem--but surprise--my backup files under the iomega folder were all erased and the location of the iomega drive was moved from its previous default location. All attempts now to find those backups have failed, and the drive doesn't respond to a backup or restore command now.

As I say, I just give up. Ubuntu is a great idea; I really love the ideal. But honestly--it is still in the idea stage. It simply is nowhere near ready for mainstream use. I hate to say say it but I'm going back to Windows, or maybe I'll try Mac. 

I have better things to do with my time than reading and applying dozens of pages of conflicting advice on configuration, terminal commands, and setup procedures, just to use my computer in ways that are simple when using Windows. 

John

---

### Post by gubbe on 2010-04-30
I'm installing Lucid Lynx on a Windows 7 laptop - Acer Aspire 5920G-302G16N - and the two OS's will/should exist next to each other. However,  after I select to move forward from the screen where I choose 14GB for the 10.04 LTS/Lucid Lynx partition, I only get "resizing partition" and everything seems to stop.

Any idea what the *EASY* way forward is?
If the answer is to stick with Windows then my test of Ubuntu is done, cause then it's still not ready for mainstream.

All feedback is welcome - thanks in advance.

---

### Post by TR82 on 2010-04-30
A totally flawless upgrade.

Can't thank you enough :)

---

### Post by faflu on 2010-04-30
I've upgraded xubuntu as a virtualbox guest system. After the first restart I could not mount guest additions image - just didn't work, nothing happened. I had to install guest additions iso image from repositories, mount it manually and run installation script. Well, it worked for seamless windows and mouse integration. It doesn't work for shared folders. when I try to mount it manually using ```
sudo mount -t vboxsf michalf.BORG /home/michalf/winhouse
``` it says that 'no such device'. But now also works automounting guest additions iso image from the host. I tried with those, but no luck...
One thing more. Fore some strange reason it puts in /etc/resolv.conf nameserver's address as 195.168.1.1 instead of 192.168.1.1 ... :-(
Summary: problems, that I cannot overcome

---

### Post by mlnease on 2010-04-30
Practically flawless upgrade.  My *sole* complaint was that the new version *still* doesn't default to numlock but that was easily fixed (I've had a lot of practice).

It took a total of twelve hours or so, thanks to Comcast's blistering 0.25Mbps DSL download speed (congratulations on your Golden Poo Award, Comcast! [http://consumerist.com/2010/04/congratulations-comcast-youre-the-worst-company-in-america.html](http://consumerist.com/2010/04/congratulations-comcast-youre-the-worst-company-in-america.html) ).

Once all was downloaded and installed though, everything (except numlockx) worked perfectly right out of the box.  Most impressive.

After upgrading, I went to Salimane Adjao Moustapha's excellent tutorial at [http://theindexer.wordpress.com/2010/03/21/to-do-list-after-installing-ubuntu-10-04-aka-lucid-lynx/](http://theindexer.wordpress.com/2010/03/21/to-do-list-after-installing-ubuntu-10-04-aka-lucid-lynx/) and have been merrily tweaking ever since--thanks, SAM.

Hope your results are as good as mine.

mike

---

### Post by gaalaaant on 2010-04-30
Okay seriously need help guys.  I have Wubi in a partition and because the Update Manager Upgrade took too long (1 day 23 hours left) I downloaded and burned an upgrade cd. Now it's stuck on 30 minutes left on "installing the upgrades" and no way to cancel! HELP!

UPDATE: Okay, some of this stuff installed.  THe color scheme changed as did the top bar.  However, I still have the window open!!!

UPDATE: lsb_release -a returns  10,04 Lucid Lynx, but none of the new stuff (the me menu) came with.

---

### Post by Jimmmac1 on 2010-04-30
Hi all

Did a fresh install today and I am up an running.  A few things though.  I haven't found out how to put a different background photo on each of my 5 desktops yet.  And for some reason, my open apps don't show up anywhere to make quick switching easy.  Haven't figured that one out yet.  And this strange little toolbar keeps showing up on the right hand side of my screen. But everything is working and working well.  Good job, U-developers !

Jim Macdonald

---

### Post by theWrkncacnter on 2010-04-30
I upgraded from the amd64 alternate cd. This worked, except for a few problems.

My first mistake was selecting "install using the latest packages (highly recommended)." I had downloaded the torrent of the cd thinking I could save the ubuntu servers some bandwidth. I thought selecting "install using latest packages" would pull packages from the servers only if the package on the cd was out of date, but what it actually did was download _all_ the packages from the server. Next time I will choose to not use the network at all, and update again once the installation is finished.

The second problem I ran into occurred during the upgrade process. I had update manager pop up, and an application known as "deskbar-applet" failed repeatedly, spawning multiple bugreports. Seconds after dealing with one bug report, another from the same "deskbar-applet" would pop up. I still don't know what this applet is, or what to do with the bug report.

The third (minor) problem was, upon restarting, ubuntu couldn't find one of my partitions in fstab. I just skipped it, and commented the entries out in fstab. I think they're autodetected or something now a days.

Aside from those things, the upgrade went very well :)
The only thing remaining is to make the boot up process even faster. I'm sure with so much cruft accumulated in my system since installing feisty, there is a lot for me to clean out. :o)

---

### Post by jrbuckley on 2010-04-30
A new install of NBR on an ASUS EEE901.   It ran flawlessly from the 'live' USB stick, so I did an install on the SSD.  It is a disaster.  On boot, the Remix desktop does not appear.  Only the bar across the top was present.  When I clicked the Ubunto icon on the top left, the bar disappeared and the NBR desktop showed up.  When I start up programs, windows appear in the upper left corner, unmaximized, with no window decoration, and therefore no way of closing the windows.  With no bar across the top of the screen, there was no way of shutting down or restarting the O/S.

All these problems did not occur in the 'live' version


Anyone got any suggestions?

---

### Post by TinyDoctorTIm on 2010-04-30
[SIZE="3"][FONT="Times New Roman"]Downloading the update files took a godawful long time, but that's to be expected on the first day of a new release. The _real_ problem is Firefox causing the computer to crash. Not just the brower, either; the computer crashes entirely and has to be rebooted. Haven't seen that kind of behavior since Windows 98.

Good news: Ubuntu 10.4 accesses my floppy drive with no problem, and I never was able to get 9.10 to do that. Yes, I still keep some info on floppies, like my household budget and other stuff I don't want to lose in a hard drive failure. I'm an anachronism, I guess. 8-)[/FONT][/SIZE]

---

### Post by punjabi_tt on 2010-04-30
Hello everyone,

I upgraded my system to Ubuntu Lucid and install ATI catalyst drivers from ati website 10.4. But I have unusual problem that my monitor goes to sleep during startup and it does not wake up until I restart the system from reset button. Although I was able to start my system by going through recovery mode.

Any help is greatly appreciated.

Thanks

---

### Post by Gyanos422 on 2010-04-30
The CD did NOT work for me.

I installed 9.10 then upgraded to 10.04 with no problems, aside from the one in front of the keyboard. :P

---

### Post by WannabeFantasma on 2010-04-30
Installing went great 

After installing glitch next to Firefox button (top of screen) -> resolved by downloading graphics drivers

Couldn't mount my Data partition at first -> after reboot just fine :)

sound worked at first; after reboot it didn't; after next reboot everything just normal... :D 

now it's just awsome :) 
(too bad I can't install xbmc and that I can't find 64bit flash player)

---

### Post by keeto on 2010-04-30
I always seem to get a few things that need fixing after an upgrade, some more troubling than others.  Upgrading to Lucid produced the following crop (noticed so far):
1.  A printer that was working before, and was connected, was not working after, and there was no way to re-install it.  It turned out that CUPS was not installed.  I don't know what I did, if anything, but after a reboot it was there again.
2.  E-mail wouldn't work because it was insisting on re-authenticating SMTP.  
3.  When the screen had gone to sleep, it needed a password to wake it up,  (that one really bugged my wife, she didn't know we had a password on the computer).
4.  The oddball one that I can't fix, is that The Titlebar on each windows panel now has the Close/Minimise/Maximise buttons on the left instead of on the right.  It's only a little thing, but it seems a long way to reach.  I can find nothing in Gnome or the Gnome Configuration Editor on how to change this back to what it was before.  Can anyone help?

---

### Post by mathias j sagartz on 2010-04-30
My new installation is hiding.  I installed 10.04 (not upgraded) after having used 8.04 for a long time.  

Installation is on an old Gateway desktop dual boot with XP.  When the installation finished I clicked the restart, selected Ubuntu from the 
grub menu, and there was Ubuntu with Gnome. Everything seemed to be working great.

Restarted again and this time selected Windows from the Grub menu.  Again 
a total success.

Restarted again and selected Ubuntu from the Grub menu. After I logged in I was left with the mouse arrow on my standard background.  No Gnome desktop, just the standard background with a pointer on it.  If I right click the mouse a box with 7 menu choices appears: Create a folder, create a launcher, create a document, clean up by name, keep aligned, paste (ghosted), and change desktop.  These menu choices work.  Selecting "change desktop" brings up a window with background options.  Choosing create a document brings up a window running gedit.  However, nothing I
try will get me a desktop.  Ctrl-alt-del will bring up a box containing shutdown options and these work too.

I'd appreciate any help anyone can provide.

I've tried multiple restarts but it's always the same.  The Windows boot
continues to work fine.

I also installed lucid on a new Acer i3 laptop.  Lucid was the only option
because install disks from earlier distributions did not work with the graphics hardware -- just left me with a blank screen.  Lucid is working fine but, ironically, I had just the opposite experience from the gateway installation. This installation is also dual boot and the first time I restarted it the Grub menu did not appear.  When I restarted the system the Grub menu was there and h:(as worked well ever since.

---

### Post by alextor98682 on 2010-04-30
> **keeto said:**
> I always seem to get a few things that need fixing after an upgrade, some more troubling than others.  Upgrading to Lucid produced the following crop (noticed so far):
1.  A printer that was working before, and was connected, was not working after, and there was no way to re-install it.  It turned out that CUPS was not installed.  I don't know what I did, if anything, but after a reboot it was there again.
2.  E-mail wouldn't work because it was insisting on re-authenticating SMTP.  
3.  When the screen had gone to sleep, it needed a password to wake it up,  (that one really bugged my wife, she didn't know we had a password on the computer).
4.  The oddball one that I can't fix, is that The Titlebar on each windows panel now has the Close/Minimise/Maximise buttons on the left instead of on the right.  It's only a little thing, but it seems a long way to reach.  I can find nothing in Gnome or the Gnome Configuration Editor on how to change this back to what it was before.  Can anyone help?


I had the same issue with the titlebar all i did was just click back and forth on a new theme then back to my fav. theme. it did the trick. All went back to normal... :guitar:

---

### Post by El_Shrander on 2010-04-30
> **keeto said:**
> 4.  The oddball one that I can't fix, is that The Titlebar on each windows panel now has the Close/Minimise/Maximise buttons on the left instead of on the right.  It's only a little thing, but it seems a long way to reach.  I can find nothing in Gnome or the Gnome Configuration Editor on how to change this back to what it was before.  Can anyone help?

It's been discussed already, but I understand that no one is expected to read all the forums and blogs out there, so here is what I did: System > Preferences > Appearance > Choose a new theme > Go back to your old theme > That's it :)

My own upgrading experience has been luckily uneventful: from 9.10 to 10.4 through the Update Manager with just a couple of clicks. It took some time for everything to download, but in the end the whole system was left ready to go as fast and smooth as before.

---

### Post by starweb350 on 2010-04-30
Upgraded older Celeron P.C from 9.10 to 10.04 with automatic update from update manager screen. It took about 6 hours and it works great! I have a problem with the Linksys wireless usb adapter but this is a new piece of hardware that I am pretty sure I can get to work.

Just did a clean install of Ubuntu 10.04 on my hpmini 1000, 16G ssd,Intel Atom, etc.  I did the install from a usb flash drive that I had to make using Unebootin IN WInDOWS XP! because the usb creator that comes with Karmic would not format the usb drive.
I have found that for some reason UNEBOOTIN works better in Windows XP, i don't know why and it really bothers me.

Anyway the HPMINI 1000 clean install went great. Install is the same as 9.10. Only one issue and that is with wireless. You must use a wired connection and click on hardware drivers and it will find the broadcom drive, install drivers and you are good to go. 

Noticeably faster on the hpmini SSD
noticeably not faster on the older celeron machine.


This is my first post on the forums, I would like to thank everyone here for the awesome support.
Ubuntu Rocks!
You guys are the best.

---

### Post by asw24 on 2010-04-30
I use the amd64 version. Overall I am happy. Still a bit in doubt; I changed from 9.10 because I would like to have a LTS release. Java does not work flawless. Hibernate does not work (didn't work in 9.10 as well; does work for the 32bits version).
Overall I love Ubuntu more and more. I love the fact that the system does not freeze because of a ' background' process was started.

---

### Post by conradin on 2010-04-30
Awz hell YEAH!!! Network upgrade went slow yesterday, but its flawless.
Additionally, my dual screen extended desktop is working much better than before!

---

### Post by Orographic on 2010-04-30
I did a clean install on my spare drive, the drive that is always used for these things.

This is the message I got with the LiveCD, 'The installer encountered an unrecoverable error.' but then it booted into the desktop eventually. The iso was checked by MD5SUM and was good. Then a FSCK occured on reboot into the installation. Everything looked fine except on boot I don't see the boot splash, just a blinking cursor and then after log in, it takes 25 seconds to get to the desktop. Everything seems stable though.

Then I tried the alternate CD install instead, did a MD5SUM and tested the CD medium but the same issue exists as above, FSCK on reboot after installation and no boot splash and it takes 25 seconds to the full desktop to appear after logging in.

These same problems existed on my system in Alpha, Beta and RC of Lucid.

I don't think my system likes Plymouth. This same system runs Karmic perfectly, its rock solid with that. Ran Jaunty and Intrepid with no problems as well.

System is 945GZM-S2 Gigabyte board with intel onboard graphics.

Any ideas on getting this system to boot Lucid faster?

---

### Post by ma3382 on 2010-04-30
I upgraded from Ubuntu 9.10 Desktop to Ubuntu 10.04 LTS Desktop.

I bought this machine for personal server use less than a month ago.
Everything worked flawlessly on Ubuntu 9.10 Desktop.

NOW:
My machine is constantly at 50% IOWait according to Gnome System Monitor.

Gnome's minimize/maximize/close buttons are now displaying on the LEFT instead of on the RIGHT.

---

### Post by MetaMs on 2010-04-30
I doubt that I'm your "usual" Ubuntu user (61 Y/O female LOL) and my install of Lucid went just perfectly on my Asus eee PC 1005HA. I had been running 9.10 as a dual boot with XP for about a month.

I purchased the Netbook with XP, knowing that I had no intention of staying with that OS, and also knowing that I did not want to give Bill any more of my money. With the install of Lucid, Windows is gone completely and forever!

I love Ubuntu! My next undertaking will be to install it on my desktop. Unfortunately, I will have to keep XP on that machine for a while because I do use some software that I will have to wean myself away from. I have too many existing files in it to just make the switch. 

One program is ACD Canvas, which I will eventually replace with Gimp, Scribus and OO Draw. The other one is Sitespinner, which I use for websites (along with Joomla). Does anyone have a recommendation for a good Linux website software (html)?

Thank you to everyone who worked to make Lucid Lynx so wonderful!

---

### Post by reb68 on 2010-04-30
First I downloaded a file from "release.ubuntu.com" and burned as .iso 
when I ran it all went well until I picked the button to try the file. It asked me for a username and password. None I knew would work. So I downloaded the file from "ubuntu.com" When I choose the try pathe I again was aked for a username and password. Same result. Then I went to Upgrade Manager in my Ubuntu. It buzzed a minute and said "Could not download the release notes. Please check your internet connection"
A few weeks ago I had installed Beta 2 and ran it. It started to be problematic so I backed down and installed ver. 9.10 again. Could that be the source of the problems?
Thanks for help
****

---

### Post by merlinof2 on 2010-04-30
Have a Sony Laptop, VGN-TX650P.  Runs Ubuntu flawlessly almost every feature, including multiple monitors, wireless, bluetooth, audio, etc..
Graphic Distro Upgrade refused to run, claiming couldn't find the release notes.  So I ran the terminal based upgrade.
Ran fine, took about 2 hours over a 6Mb DSL.
System rebooted, none of my programs had any borders, and I couldn't move/resize them at all.  Ran SYSTEM>APPEARANCE and reset the theme and window controls, and now all seems fine.  It' been running for about 30 min, still looking to see if anything wound up in the weeds...

---

### Post by jimmyjones on 2010-04-30
> **dazcaz said:**
> Finally got the upgrade and it looks great. Not had much of a chance to play with it yet.
One thing that is p*****g me off is that I have lost Thunderbird. Has anyone else suffered this? I don't mind re-installing it on this machine (The laptop) but I would hate to lose all my mail on the main machine when I do the upgrade on that.  There are a lot more e-mail accounts to set up on the other machine, not to mention the thousands of e-mails.
Is there a way to save my accounts just in case?


Upgrade worked, I'm shocked but hey it should have, right.

I didn't loose Thundebird, the launcher got messed up, had to change from mozilla-thunderbird to Thunderbird, I was still running 2.??, now 3.04 is installed.

I always backup the profile directory and copy it over the new one. I moved this one from windows.

---

### Post by francesco44 on 2010-04-30
The upgrade from 9.10 to 10.4 Lucid from beta 2 was ok (almost).

Today I updated my RC Lucid on an Thinkpad X60.....BAD SURPRISE....my ordinary mouse pointer (classic arrow) has been transformed in a THICK **X**....

This is not all.....the icons regulating the windows (yes these little things which have been moved on the left-side...) HAVE COMPLETELY DISAPPEARED...VANISHED!

What should I do?

thanks to all

Piero

---

### Post by migs73 on 2010-04-30
Upgraded from Karmic to the RC of Lucid. Only problems I had were that I lost some Icons (just black boxes) for stuff in the top panel (the on/off one and firefox), just deleted them and added them again, and also I am getting the ugly fuzzy screen on boot as the screen is 'poked' to get the correct resolution. Had it before (I think it was Intrepid) and was sorted then so hopefully they can do the same. Could also be a release candidate thing, don't know. Also how do I go from RC to the proper release? I think I read it would just get patched through update manager. 
I also changed my windows buttons to the right,don't care what Mark Shuttleworth and co say it is a pain in the butt, unless you're an ex-mac bod!

---

### Post by twallace on 2010-04-30
Now I am really upset!!!!!! So in trying to fix my screen resolution I messed up by Xorg Config files so I had to do another install of 10.04. Now my laptop won't come on at all, just get my cooling fan running full blast with a blank screen!!!!!!!

HELP??????

---

### Post by r-senior on 2010-04-30
Overall, not too bad. Upgraded from 9.10 rather than doing a clean install.

Installation went smoothly (if a little slowly, even though I used the alternate CD downloaded with BitTorrent). Just a few niggles after installation:

a. No window decoration on login, but worked around that now
b. Problems with NetBeans plugins but sorted
c. Thunderbird 2.0 to 3.0 has left me with some migration headaches but that's nothing to do with Ubuntu per se.

More worryingly, I had a couple of lockups, but I think that might have been related to (a). I hope so. All's been well for the past few hours, so touch wood.

Well done to all the developers, maintainers, documenters, packagers and other contributors. It's appreciated. :-D

EDIT: I'm even getting used to the buttons on the left. ;)

---

### Post by Jadephyre on 2010-04-30
The Installation fried my goddamn Windows 7 Bootloader... good that I made a backup of all my files before trying to set up a Multiboot Environment.

Seems I'll be sticking to Products from Redmond after all... thanks for nothing.

So much for a "simple Installation".

---

### Post by jtraveller on 2010-04-30
Downloaded the alternate cd, since my network has been hic-uppy the last few days, then upgraded from karmic.
The upgrade was flawless, albeit a bit slower on the installation phase than the previous upgrades since breezy .

Had a couple minor but annoying troubles, one was the Jack sound server crashing on me every time, fixed it.

the other is the gwibber trouble, the one where it crashes and dont even stays in the background. Havent fixed it yet.

other than that, i like this new release and im going to spend a lot of quality time with it, even though i think its going to be until the next LTS that i may draw my windows-zombie friends to ubuntu...

---

### Post by DouglasAdams on 2010-04-30
i upgraded from 9.10 32-bit. everything seemed to be fine. then did the reboot to complete the upgrade and problem!
>>>>  please see attached screenshot  <<<<<
please note the following in the screenshot:

1)
top right of the open window. no close, full screen, minimize icons

2)
the lower window was the last one accessed
i.e. not bringing last accessed to the foreground

>>>>>  can't see on screenshot but it's true  <<<<<

1)
default mouse pointer, "X", does not change to the re-size one when it gets near the edge of a window

2)
when browser, or any other app, is started, it starts using only half the screen. as the app's also don't have a full screen icon, or a re-size mouse pointer, they can't be made larger.

<<<>>>  please HELP  <<<>>>
how the hell can i get rid of this rubbish and make my machine usable again?

---

### Post by suli8 on 2010-04-30
ok here is my experience!
i upgraded from karmic! download was fast,20 minutes, installation 2 hours. i had one error, which was the network manager!
it finished, i chose to install the new grub.
restart, i didnt see my vista on the list, but i dont really care cause im never gonna use it now, but somthing there went wrong!
and the resolution of the screen before the login was strange! not a big deal!
everything worked, compiz, nvidia driver...panel... i just needed to install flash, from sinaptic, the one with the ubuntu symbol.. and in the version there was written lucid, and it works on both firefox and chromium!
oh..and the network error during the installation?...i dont know...it just booted and connected to the internet....so no problem with that!
i thought it will be harder! others are having a bad luck, i know...

---

### Post by ask@refcapgroup.com on 2010-04-30
So upset to have upgraded. ATI Multi GPU support gets broken in LUCID. Worked perfectly in Karmic (aticonfig --initial=dual-head --adapter=all). Now spending countless hours struggling to downgrade back to Karmic. Try same in LUCID and you get a COMPUTER FREEZING or going to sleep.

---

### Post by yosiasz on 2010-04-30
all worked flawlessly on vmware player. webmin had problems libmd5-perl not working webmin not working.
 
otherwise nice job ! thank you!

---

### Post by chili555 on 2010-04-30
I did the upgrade through Update Manager and have no problems. It did take about 5 hours, however. Everything, so far, is flawless.

---

### Post by sussa on 2010-04-30
Yesterday I did a fresh install on my Dell Inspiron 1545 laptop, and almost everything is working fine. The sole serious problem is that my wireless card (Intel WIFI 5100) is not functioning properly. My connection either doesn't work at all or it's really, really slow. 

Up to now, I haven't been able to solve this issue

Apart from that, as I said, everything is fine.

Thanks for the job, and long live Ubuntu :)

---

### Post by uniquename999 on 2010-04-30
jrbuckley:

Your experiences with 'stuck windows' on your netbook sounds a lot like
what I encounterd in installing Ubuntu 9.04 on my Acer netbook.

One great trick: Use Alt-clkMB3 (hold Alt and click on mouse button 3, which is
usually a right-click for right-handers).  Click anywhere in the stuck window ---
preferably in the middle-right of the viewable portion of the window.

This will give you the entire, usual window menu --- with minimize, unmaximize
(restore), MOVE, resize, and close.

That might be enough to reduce your frustration level by about 50%.

----

I have documented my experiences (and 'issues' encountered) during
installs of Ubuntu (9.04 and 9.10) --- on a netbook (Acer) and two desktops.

Here is the link

[http://www.subdude-site.com/WebPages...lls_blaise.htm](http://www.subdude-site.com/WebPages...lls_blaise.htm)

You can look for the string 'window menu' or 'mb1' or 'mb2' or mb3' in this
page to get more details (and a rant) on what I have briefly outlined above.

This page is a quite long set of notes, so there is a link at the top that gives an overview.

With respect to the Acer netbook, I found Ubuntu 9.04 to be a very
responsive installation --- and the dual-processor Intel Atom CPU
seems to handle basic image processing, audio, and video apps
quite satisfactorily.

After resolving some 'stuck' windows problems and confusing
trackpad (and mouse) behavior problems (detailed in the link
above), I find Ubuntu 9.04 to be
a quite capable OS for my netbook. I am glad I did not try
Ubuntu Netbook Remix first.

---

Besides the notes on the Ubuntu Jaunty install on the Acer netbook
being of possible use (and encouragement) to netbook owners,
the notes on the page/link above should be of help to 'newbies'
as well as to others.

In particular, at the bottom of the page is a summary that gives
an overview of the applications that I have found useful and capable
and stable.

A few other topics covered:

- several things that have probably sent tens (if not 100s) of 1000s
of Linux-attempters scurrying back to MS-Windoze

- some things that Gnome/kernel/Ubuntu developers could do to
eliminate some of that scurrying

- why I prefer Gnome-Ubuntu (rather than UNR or KDE) on my netbook

- some Nautilus scripts that I have created to fill gaping holes
in the capabilities of Linux apps for BATCH image processing

- some comments on the commendable OpenShot video editor
development 'story'

- the one piece of software that forces me to keep an MS Windows
operating system on one or more of my PCs - Turbotax. (I wonder why
I never read of anyone mentioning this type of software, tax software, in
regard to needing to keep an install of MS Windows.)

- a class of users that are not served by Linux --- mechanical engineers.

That said, I have found a lot to like with Gnome-Ubuntu 9.x (Jaunty & Karmic)
--- on both netbook AND desktops.

---

### Post by uniquename999 on 2010-04-30
[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)

---

### Post by princess9987 on 2010-04-30
Hi, 

I have upgraded from Ubuntu 9.10. Everything is working fine except that the title bars of all windows have disappeared and nor are they appearing on the status bar for minimising or maximising. 

Can someone help with this issue? My computer is HP Pavillion DV6-2150us. 

Thanks,

Pritha

---

### Post by Jackelope King on 2010-04-30
I did a clean install, replacing 9.10.

Everything worked out of the box (with the exception of the usual difficulties of having to install the NVidia proprietary drivers). I was also pleasantly surprised with how easily I was able to get almost all of my old favorite programs back after installing Ubuntu Tweak.

It was also a pleasant surprise when I found the default Ambiance theme... well, likable!

Now if this works for my friend out of the box, it'll be two thumbs up.

---

### Post by aaronp on 2010-05-01
Upgrade - worked but had few things to fix, nothing serious though

PRetty much flawless upgrade process from Karmic 9.10.
Upon trying to boot, the following grub issue was encountered:

```
Entering rescue mode...
Error: the symbol 'grub_puts' not found
grub rescue> _ 
```

The simple and perfect 5 minute fix (although annoying because I know nothing about grub and still don't know the cause) was found here:

[http://www.jellykernel.org/2010/04/autres/migration-karmic-vers-lucid-symbol-grub_puts-not-found/](http://www.jellykernel.org/2010/04/autres/migration-karmic-vers-lucid-symbol-grub_puts-not-found/)

Although it's not in English so I passed it through Google Translate first: 
[http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fwww.jellykernel.org%2F2010%2F04%2Fautres%2Fmigration-karmic-vers-lucid-symbol-grub_puts-not-found%2F&sl=auto&tl=en](http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fwww.jellykernel.org%2F2010%2F04%2Fautres%2Fmigration-karmic-vers-lucid-symbol-grub_puts-not-found%2F&sl=auto&tl=en)

---

### Post by marrabld on 2010-05-01
Upgrade - worked flawlessly

Great Job, 

I am finally confident enough to direct friends to the website and encourage them to just follow then instructions.  I used to have to warn people about certain things and make excuses for others (mostly media related).

All though I am not a huge fan of the new look, I think it looks more professional than it used to.

---

### Post by JohnnyVW on 2010-05-01
I upgraded from 9.10 to 10.04 on my IBM Thinkpad R51 without issue.  I may do the desktop this weekend (also at 9.10).

---

### Post by kkfok1 on 2010-05-01
I have problem to upgrade from 8.04 to 10.04

The error that I had found in the var/log/dist-upgrade/main.log are as following :

Any advise to solve this is very much appreciated.

Thanks

2010-05-01 13:47:16,297 INFO Using config files '['./DistUpgrade.cfg.hardy']'
2010-05-01 13:47:16,297 INFO uname information: 'Linux blissful 2.6.24-27-generic #1 SMP Wed Mar 24 10:04:52 UTC 2010 i686'
2010-05-01 13:47:16,297 INFO creating state file with '['tar', '-z', '-c', '-f', '/var/log/dist-upgrade/system_state.tar.gz', '/etc/apt/sources.list', '/etc/apt/sources.list.d/', '/var/lib/dpkg/status']'
2010-05-01 13:47:16,474 INFO release-upgrader version '0.134.7' started
2010-05-01 13:47:16,729 DEBUG svg pixbuf loader failed (Error displaying image)
2010-05-01 13:47:16,729[COLOR="Blue"] ERROR html widget
Traceback (most recent call last):
  File "/tmp/tmp.blmGi13183/DistUpgradeViewGtk.py", line 404, in __init__
    import webkit[/COLOR]
ImportError: No module named webkit
2010-05-01 13:47:16,743 DEBUG Using 'DistUpgradeViewGtk' view



(some logs in between)



2010-05-01 13:47:42,392 DEBUG doUpdate() will not use the network because self.useNetwork==false
2010-05-01 13:47:42,393 DEBUG openCache()
2010-05-01 13:47:42,771 DEBUG /openCache(), new cache size 2289
2010-05-01 13:47:42,771 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2010-05-01 13:48:24,805 [COLOR="Blue"]ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'[/COLOR]
2010-05-01 13:48:24,805 DEBUG abort called
2010-05-01 13:48:24,807 DEBUG openCache()
2010-05-01 13:48:27,829 DEBUG /openCache(), new cache size 25405
2010-05-01 13:48:27,830 DEBUG enabling apt cron job

---

### Post by shmoesmith on 2010-05-01
Well removing sun java really screwed me on my financial software that I use that is java based.  the openjdk just won't seem to launch the software.  I've also encountered black screens of death when trying to switch between profiles.  Mouse and keyboard are randomly locking up.  Unpluging/replugging them seems to have no effect (they are both USB) and I have to do a hard reboot to restore functionality to them.  

Very unimpressed so far.  About to throw in the 9.10 disk, format my whole root and go back.

---

### Post by gilani_saad on 2010-05-01
Dear All;

I hope my this post will catch some replies as I am struck up with my newly installed Ubuntu 10.04 in HP Compaq 6720s. Rest all is fine but I am having some serious issues regarding my MIC and Web cam. I don't know what to do. Actually I am a newbi in the field of Linux (Ubuntu) I was a windows user previously but when I saw it working on one of my peers machine I simply fell in love with it. If someone can kindly guide me how to tackle with this problem, I’ll be obliged. 



With profound regards.

---

### Post by goldshirt9 on 2010-05-01
> **gilani_saad said:**
> Dear All;

I hope my this post will catch some replies as I am struck up with my newly installed Ubuntu 10.04 in HP Compaq 6720s. Rest all is fine but I am having some serious issues regarding my MIC and Web cam. I don't know what to do. Actually I am a newbi in the field of Linux (Ubuntu) I was a windows user previously but when I saw it working on one of my peers machine I simply fell in love with it. If someone can kindly guide me how to tackle with this problem, I’ll be obliged. 



With profound regards.

me also.
this is the only area i havent looked into.
installing a program to run my laptop webcam and mic.
other than that. worked like a treat , but i did reformat  on my laptop :P

---

### Post by gandalf2000 on 2010-05-01
Upgraded last night and it went well.  The only problem I have encountered so far is printing with my Brother printer.  Had it working fine with Karmic but can't seem to get it to work with Lucid.  The printer manager can see it on the network but when I try to print anything it says that it can't find the printer.  I did a complete removal of Brother print drivers in Synaptic then reinstalled them and it is just the same.  If I double click on the printer in the print manager and go to Policies and check Enable it looks like it is set to go but as soon as I try to print the Enable becomes unchecked.  Any ideas?

---

### Post by rigobot on 2010-05-01
Installed with no troubles, but when i tried to enable the nvidia driver v.185 i got a black screen.
The 173 version fix the ptoblem (both installed) from repos.
For more details there is a specific thread open:
[http://ubuntuforums.org/showthread.php?p=9040477](http://ubuntuforums.org/showthread.php?p=9040477)
The other things work well, I have a gigabyte ep45-ud3l with a geforce 8600gt!
Any suggestion?

---

### Post by Unicast on 2010-05-01
**Did it work flawlessly ?**
No!

**Did you get problems ?**
Yes - the intel 855GM bug. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511?comments=all)

**Did you manage to solve them ?**
Not solve, more patch up until a proper fix before available

**if yes how ?**
Had to add the kernel option "i915.modeset=1" to grub.

Not impressed that everything (for me anyway) was working in 10.04 beta2, and then they went and broke things in the RC. :(

---

### Post by schauhan on 2010-05-01
Lenovo G450 laptop. Upgrading from 9.04.

Overall the smoothest ubuntu  upgrade I've experienced to date.

I had to jump through a few hoops to get audio working on 9.04 on my laptop and was afraid the upgrade might break the audio again. But the audio is perfect.

I have a lot of apps on my system and my connection at home was a bit slow. So I left it on overnight and in the morning found download was complete and a series of dialogs waiting for my confirmation. The upgrade took about 30 mins to complete.

Everything feels a lot faster and I'm pleased! Thanks guys.

Only minor issue I've faced so far is some icons are missing from software center. The new software center is great btw.

I recommend the upgrade.

---

### Post by Amused2Death on 2010-05-01
I should have known better, feel like i have returned to windows :(

Every time i log in it then tells me a process is still running, power management to be precise. I have to click log out anyway, then i get a blank destop. After hitting several keys i eventually get my desktop back.

I stopped power management from starting but it made no difference, get the same error everytime i boot up. Turned on screen saver, just get a blank screen and it doesnt ask for password to resume. So you can hit any key to resume, but unfortunately the mouse is frozen and a reboot is required.

Turned screen saver off, and it still goes to blank screen after x-amount of time of no use, then mouse is once again frozen.

I upgraded to Karmic with no problems, just wish i had stayed with Karmic, hopefully there is a roll back button.

---

### Post by robbiemorrison on 2010-05-01
Flawless install of 10.04 desktop on a new Intel Core i5-520M chipset with QM57 on-board graphics.

Not expecting this as *LinuxUser* magazine (Germany) concluded in their April edition (translated):

[INDENT]"Linux supports chipset graphics from kernel 2.6.33, until then you need a dedicated graphics card."[/INDENT]

I opted to nuke Windows 7 and not to dual boot.  So far I have tested the LAN, WLAN, USB flash drives, remote keyboard, and fan control.

The new look is also fantastic!

In terms of experience, I have been installing and running UNIX and Linux systems for about 15 years now.  This is the first release I would unequivocally recommend to ordinary users.

The Ubuntu development and desktop teams have done an outstanding job.  Many thanks!

Hardware : Toshiba Tecra A11 11H laptop
Specs : 2.40GHz Intel Core i5-520M / 4096MiB RAM (upgraded from 2048MiB) / 250GB HDD / 1366x768
Part number : Toshiba PTSE1E-00P00FEN
Purchase date : 10-Mar-2010

Quoted article: Kottmair, Daniel. 2010. Intel "Clarkdale"-Cores i3/i5 im Test. *LinuxUser*. April p82-85. ISSN 1615-4444. website: [www.linux-user.de](www.linux-user.de).

Robbie Morrison, Berlin, Germany

---

### Post by eagle-eye on 2010-05-01
On my laptop a clean install worked perfectly first time. On my desktop PC I had problems.

I first tried installing Kubuntu but it just stuck at the splash screen. From a CD it eventually told me I had an unrecoverable error. From a USB stick it just sat on the splash screen forever.

Using the same USB stick Kubuntu installed perfectly on my laptop. I decided that I still don't like KDE 4 so I put the Ubuntu image on the USB stick and installed that on the laptop instead. Again it worked fine.

I managed to install Ubuntu on the desktop PC from the USB stick but only after a couple of failures where it stuck on the splash screen. 

On the plus side my DVB card works nicely. It wouldn't work at all under Karmic. On the minus side the desktop PC boots up very slowly compared to previous Ubuntu versions.

---

### Post by jodlajodla on 2010-05-01
Hello!
Here is my experience:
When I saw the new distribution is for download, I just went to upgrading and I click upgrade (for new distribution). Then I wait all processes and I got many problems so this upgrade doesn't work. Then I download LiveCD and delete old partition of Ubuntu 9.10 . I install 10.04 and there is no more problems. I configure all settings and restart computer. I said "Yeah! It works!" and again install one program from Synaptic. I need to restart the computer and next experiance is the Ubuntu need to start in safe graphics mode. I reset my settings of graphic driver and install it again. Now works. I need to uninstall fglrx driver, with which I have problems. I think the my Ubuntu now work.

---

### Post by johnnymenmonic on 2010-05-01
I try to upgrade to 10.04, but the installation process is very slow. The internet connection is sometimes only  2.5 B/s or even worser. Is this a server problem?

---

### Post by CoolDreamZ on 2010-05-01
Flawless upgrade from 9.10 UNE to 10.4 UNE (even the wireless worked first time!) on my Lenovo S10 Netbook

Only minor criticism is a few arcane questions when upgrading packages (e.g. GNOME and GRUB)

Well Done! Best Ubuntu upgrade experience so far and I love the new look. 

Wish GIMP was still there by default though..

---

### Post by blitzer on 2010-05-01
Flawless install.

Congratulations Ubuntu Team you deserve it.

Upgraded using the update window pressing upgrade button at the top and it took over from there.

---

### Post by ebbr.bugs on 2010-05-01
No sound within firefox.
Mplayer plugin for firefox vanished.
No volume control applet for the panel.
Did I mention there is no volume control applet for the panel?
Impossible to change the volume.
System-preferences-sound opens a ridiculous window that is 2 or 3 times taller than the height of my monitor in pixels.
Window control buttons (minimize, maximize, close) ended on the left corner of the windows. The only thing I managed to fix so far.

---

### Post by duke.tim on 2010-05-01
The new version seems good. My sound works without hacks, and my wireless (problems I've had in the past versions) I like the new installer the small changes make it seem more professional and easy. 
BUT

I now have a screen which will randomly flash for a split second (drivers?)

and the menu Launcher will light up but not open. When I get it to open my mouse stops working.

I'd rather my sound not work than the mouse...even if I can navigate with the keyboard.

---

### Post by Leischa on 2010-05-01
Doesn't work at all. I am staring at a black screen, which I assume means there's a problem with X. I have tried booting in safe mode and reconfiguring it, but have't been successful.

Fail.

I am going to retrieve my data and move to a distro that works. Ubuntu should be beyond these kinds of elementary errors by now.

---

### Post by _grv_ on 2010-05-01
Congrats to Ubuntu team,

install worked like a charm on my Sony Vaio SR140E
However Grub interchanged the names of the Vista loader and Vista recovery drives.

Also the external monitor by VGA ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/319717](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/319717)) has not been resolved... 

Ubuntu still freezes when i plug an external monitor via vga on my laptop.

Other than these two minor issues... it is awesome...

Thanks and regards
Gaurav

---

### Post by ianshortreed on 2010-05-01
Did clean install on a DELL Vostra 1000 having 2 GIG RAM with ATI Radeon EXPRESS card and when I boot after install I get a black screen with vertically arranged multi-colored lines.

Only way out is grub editing replacing ... splash quiet with nomodeset and then Control X

Once I boot into the desktop which now appears, any changes I make to Monitors throws me back to the same black screen with multi-colored lines 
 
Visual effects are set to None under Appearance

Any ideas? This looks like the end of the line for ATI cards and Ubuntu with no native ATI driver support.

---

### Post by DouglasAdams on 2010-05-01
i've followed a lot of the links about this issue and i think i've sorted things out, apparently i needed to tell 10.04 that i was human  :)
frankly, i think it's really poor that 10.04 should have been released containing this issue. certainly not something i would have expected from any Linux distro - especially Ubuntu!
in fact, it reminds me of doing a Windows install.

---

### Post by Bristol_Green on 2010-05-01
Part way through the upgrade my desktop screen turned grey but the icons remained in place. Presumably my theme had been removed. Upgrade continued OK until I did the restart. A Firefox window opened on my grey screen, immediately followed by the Firewall window which opened on top of it. Both windows were in the top left-hand corner of the screen. They had no minimize/maximize/quit buttons, and I couldn’t grab the sides or corners to resize or move them. I had to use File>Quit. Then I opened Open Office. The window opened in the centre of the screen. It too had no minimize/maximize/quit buttons. (They weren’t on the left either.)

After reading this thread (with difficulty as the window was ¼ size!) I went to System>Preferences>Appearance, selected my existing theme (which was already highlighted), and normality was restored.  It was a very scary moment!

Sound seems improved, at least on Spotify. Lots of things I haven’t checked yet.

I don’t like having to unlock the screen with my password every time I make coffee! I’m the only user here. Is there a way of disabling this feature?

---

### Post by John Bean on 2010-05-01
Clean install. Only issue was wi-fi - I couldn't get the Broadcom drivers (HP-6735s laptop) to work from the CD install, used a wired connection to download them instead. Everything else worked perfectly, far better than my previous Jaunty install.

I don't seem to be alone in this...

---

### Post by andreasdelpaso on 2010-05-01
Upgraded to 10.04 on a compaq netbook - all seems working ok but the system minimizes all applications - cant see anything since ican only glance at any window for a couple of seconds .
Thats the only problem,i keep askng for help since yesterday but no luck.....

---

### Post by shipinomore on 2010-05-01
My big concern is with the install of VMware Tools.
was done at the end of the install right after the first boot of the new system. 
Both Ubuntu and Kubuntu 10.04 fail to do this. The message on the screen says to WAIT! that it is being installed but not so.
Without this keyboard and mouse are useless.
Larry

---

### Post by navneeth on 2010-05-01
**Upgrade - worked but had few things to fix, nothing serious though**

Upgrade using the alternate installation CD, from 9.10. 

2 GB Primary memory|2 GB Swap|Pentium Dual Core E5200 - 2.4 GHz|No proprietary drivers installed. 

The whole process took a little over an hour without glitches. 

A few components of GVim were removed at the last stage. These were only two in a long list of unwanted packages which included many older versions of the kernel. Since **I did not have the option to remove by selecting the ones I did not want**, I had them all removed. It was a good time to check out the new Software Centre. Installing GVim again was a breeze.

---

### Post by StarLab on 2010-05-01
I did a fresh install on a 320GB drive. Dropped in like a dream!

Only had one issue with Compiz going dark while rotating workspaces. Unclicking the lighting option in Compiz 'general' settings solved this. 

It even picked up my wireless card - something I could never get to work properly in 9.10. 

Installation, configuration, and data restore were all done in less than 2 hours. Similar actions under Windows used to take me days to get back up to steam. 

Kinda ticked me off. I booked a whole evening off to accomplish his. I was back to work in 2 hours. lol

---

### Post by rooster78383 on 2010-05-01
Upgraded from 9.10 flawlessly on a Dell Inspiron 530 desktop. Zero issues. ThinkPad T42 clean install is next.

---

### Post by /Michael/ on 2010-05-01
I did a fresh install with an already existing /home partition. Everything went well. I had to install the Broadcom STA driver manually from my USB key (created with Unetbootin). Fortunately all the files needed were on the image. This way I could install the wireless driver without an wired ethernet connection.

I had to manually delete and recreate a keyring without password in order to connect automatically to the network after boot.

**Resume after suspend does not work!** The screen stays black and even ctrl-alt-del will not reboot the computer. All I can do is pressing the power button until the machine halts. Suspend/resume worked with ArchLinux (even there were also some problems with kernel mode setting).

---

### Post by Judge P on 2010-05-01
Well done to the Ubuntu team!

Just upgraded from 9.10 to 10.04, basically OK, just a couple of small problems.

The install hung at installing adobe flash plug-in, after 13 retries it then carried on. But the plug-in wasn't installed in Firefox. So I had to install the plug-in; got info from here [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Only other small thing was the Firefox icon on the panel was a red circle with a line through it, so removed and re-added to panel then OK.

Besides that, everything else seems fine, so thanks to the people that make it happen

Regards

JP

---

### Post by egrpioneer on 2010-05-01
Installed 10.04 LTS 64 bit, on PC w/4GB ram and 2, HDDs. HDD 1 runs XP. HDD 2 was running 10.04 beta 32 bit. So, installed 10.04 LTS 64 bit on HDD 2.
The install proceeded as expected until the re-boot, when the dreaded grub rescue prompt appeared.
I needed to use the PC, so I had to insert the XP install disk and run FIXMBR through the recovery console. The PC booted into XP, and life was good! Yesterday I changed a setting in the bios, so that HDD 2 w/ 10.04 LTS 64 bit, was given priority over the HDD w/XP. Now, the Grub menu appears as it did before the 10.04 LTS install, I can select either Ubuntu, or XP, and we're back to normal!

---

### Post by pezball on 2010-05-01
Upgraded two Ubuntu 9.10 workstations, and one Ubuntu 9.10 server.  No  major issues, just the usual and expected reconfig of a few files in  /etc.  (cron-apt and sensors3 for the server, as far as I have noticed  this far, all the rest seems to work)  :)

Whenever asked, I did  choose to go with the new versions of config files, and manually make  the needed changes later, since that approach is likely to work better  for future upgrades.  No point in keeping old style/syntax config files,  if that can cause problems when new upgrades expect to find the new  syntax.  ;)

After the upgrades I went into aptitude to see if all  packages were in order, a few packages were flagged for removal or  reinstall on one of the workstations, but not on the other.  I guess  it's because the workstation with flagged packages, has had a lot more  manual installs and removals of packages.  The other workstation is more  or less untouched since first install.

For example the package  qcad-data was removed during upgrade, while qcad stayed - some issues  with dependencies???  When I run aptitude, qcad-data was flagged for  reinstalling again, so somehow one package manager hand (upgrade) does  not know what the other hand does (aptitude).  :(
Synaptic and  aptitude do not always run hand in hand with these things too, I guess  it is because Synaptic forgets about pending changes when it's closed.   It is something that really should be taken care of.  The graphical  package manager, and the console package manager should always and  forever rely on the same data, otherwise it gives these strange and  confusing effects.  Same goes with upgrade too.  Every software used for  installing and removing packages need to use same info about what to  add/remove.  There is absolutely no reason to remove qcad-data, if it  can be upgraded instead.

The Screem web site editor is missing in  10.04.  I did not expect that, but it's really a no-issue since I can  happily use gedit for that purpose.

Another strange behaviour  with the upgrade, that i have noticed this far, is that on workstations  the avahi-daemon continues to be installed, but not on the server...  I  see no reason why it would be flagged for removal on the server, unless  it is a previously required and autoselected package which now is  considered optional for the installer...

One thing that must be  considered a bug, is that phpsysinfo complains about  /usr/share/phpsysinfo/data/distros.ini missing.  No wonder it is  missing, cos there is no data folder at all.  The system info page  works, but it does not show info about Linux dist name and version.   Hopefully an update will be available soon.


All in all, the  upgrade went a lot better than expected.  Good work!!! :popcorn:

---

### Post by ppm on 2010-05-01
I was able to do a clean installation, but not without some serious problems described [here]("http://ubuntuforums.org/showthread.php?t=1003484").

Also, I had to google to find out why I wasn't able to find Sun JDK using ```
apt-cache search <keyword>
```. The solution can be found at [Ubuntu Geek site]("http://www.ubuntugeek.com/sun-java-moved-to-the-partner-repository-in-ubuntu-10-04-lucid.html"). The openjdk is in the 'standard' repositories, but I need Sun JDK. This is not really a big issue, but things like these are just annoying.

However, I have to say that 9.10 worked just fine for me. And I hope 10.04 will do as well.

---

### Post by gemme on 2010-05-01
Upgraded, worked well. I don't understand why so many people are doing new install since:

1) Upgrade is the reccomended way by Canonical:[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

2) It's like doing format C: on Windows every time something goes bad. Ubuntu is supposed to be better!

---

### Post by JHCKX on 2010-05-01
I had trouble with Lucid Lynx beta 1 and beta 2 because of my graphics card (ATI Radeon Xpress 200M in a Packard-Bell Easynote MZ35 laptop). Beta 1 and Beta 2 froze up at the point where the language and keyboard selection screen should be displayed so I couldn't even instal them. RC went well and I'm using it now, with no other problems than the long standing issue of suspend/hibrinate not working on this laptop (same issue in 8.10, 9.04,  Ubuntu 9.10 was never stable on this laptop so I only used it as a test system).

On the other hand, I have noticed that graphics performance on Lucid Lynx is not as good as on 9.04. Just for a test, I installed "Briquolo", a 3-D breakout game. This works smoothly under 9.04 but under 10.04, the screen can't keep up with the mouse movements. 

What are other peoples experiences with graphics performance, particularly if you've got an ATI or Nvidia graphics card? And is there a good graphics benchmarking program out there?

---

### Post by gillsmithy on 2010-05-01
My first ubuntu upgrade (having defected from kde) Pretty good path from beta 1 some bugs but no hangups or outright crashes (makes a change from kde) Now a confirmed ubuntu user/fan. Thanks team.

---

### Post by evoisard on 2010-05-01
New install (replacement of an old Debian) on my Fujitsu-Siemens S Series Lifebook.

FAIL !

CD booting up to Ubuntu logo with the red progress dots, lots of CD I/Os and then black screen and nothing more. I guess it failed the X setup...

Eric

---

### Post by Greymatter on 2010-05-01
A second install, this time on a Dell Laptop. No issues at all!

---

### Post by Bristol_Green on 2010-05-01
Same problem as before after a restart. Windows are now 1/4 size and I can't move or resize them. Minimize/Maximize/Quit buttons not visible. Changing Desktop Theme didn't help this time.

It worked OK before I restarted.

The cursor is a black X when it's over the desktop.

---

### Post by Andreas1 on 2010-05-01
several issues on both my and my sister's laptop. most prominently: app store messed up packages and i had to fix them via aptitude/dpkg-reconfigure. she would never have been able to figure that out. after serious issues with both jaunty (intel video disaster) and karmic (random freezing), i promised to give ubuntu one last chance with lucid, and it's already off to a bad start.

i currently cannot with good conscience recommend ubuntu to anyone, because:
-the average user (my sister) cannot fix the unforeseeable issues that come up in ubuntu.
-the power user who can fix these issues (me) might as well use debian
-the above categories cover all potential users


the radiance theme is really nice though.

---

### Post by GuiGuy on 2010-05-01
Every Ubuntu upgrade I have ever done, and there've been a few, has been a disaster.

This on is the worst. I can't even get to recovery mode.

---

### Post by FreeTheBee on 2010-05-01
My upgrade from Karmic took a bit less than 2 hours. I had some small issues with alsa/pulseaudio, resetting volume to 0 after login or after switching to hdmi output. But that was fixed with info from the forum. 
At first I couldn't find the proper nvidia drivers but again after searching here a bit, that was fixed in a minute as well.
For the rest all seems fine, so time to explore a bit and see what is new.

---

### Post by drorlev on 2010-05-01
First and foremost, I really appreciate the efforts of the developers and helpers of the Ubuntu community. 

Saying that, the process to a boot-able Lucid Lynx was vary frustrating :cry:.

First I did an upgrade from Karmic Koala. 
The download and installation process went flawlessly. 
Unfortunately, after the restart (last stage) I got a black screen rather then a login screen...
So I tried installing from a disk, only to get the same result.

It took me a day and a half to make it work and show the login screen. 
It turned out to be the KMS-graphic card problem (I have an ATI Radeon card).

Given that this issue (with ATI, NVidia and Intel cards) is known for some time (since one of the beta versions I think) I'm sorry that there wasn't an option to deactivate KMS in a preliminary stage of the boot sequence. :confused:
It seems that it could have saved a lot of people a lot of time and frustration. 

Other then that, Lucid Lynx :guitar:

dror

---

### Post by NCMountainBoy on 2010-05-01
Install on Dell Dimension XPS B933, 512MB, 160MB EIDE drive with single partition  hung at GRUB prompt.
Used manually partitioning (20GB /Boot, 138GB /, and 2GB swap) and was able to boot up desktop.
Only other problem so far is that music CD's are not being recognized. In 9.10 RhythmBox would not
recognize music CDs but CD Player worked. Neither can find music CD in 10.04.

---

### Post by nuwave on 2010-05-01
I did a fresh install of 10.04 along side WinXp and it gave no problems at install or getting all of drivers and plugins to work.  But just yesterday afternoon I booted up and my top panel disappeared and my window manager was not responding. I found it was some compiz issue i just reinstalled and everything seems to be working again.

---

### Post by Bristol_Green on 2010-05-01
> **Bristol_Green said:**
> Same problem as before after a restart. Windows are now 1/4 size and I can't move or resize them. Minimize/Maximize/Quit buttons not visible. Changing Desktop Theme didn't help this time.

It worked OK before I restarted.

The cursor is a black X when it's over the desktop.

I've found the answer. System>Preferences>Appearance>Visual Effects defaults to None on shutdown. How do I make it stay on Normal?

---

### Post by Ethangar on 2010-05-01
Updated from 9.10 to 10.04.

Took hours but completed successfully. Rebooted fine. I had to setup the nvidia driver to enhanced? and that got my menu bars back. That was just because of compiz though. Minor detail. Everything detected and running fine. There is one error that flashes on the screen during boot about nvidia smb? It goes by to fast to read. I did find one snag though. I couldn't boot into XP anymore. Just a black screen with a cursor staring at me. I knew it was a grub error and I think that I caused it. During the upgrade it asked once about installing grub2. I likely mangled a setting there. Anyway found this link in another thread.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

That got windows up and running again with minimal hassle. All in all a great upgrade.

---

### Post by fwalderd on 2010-05-01
Just did the upgrade on my Toshiba notebook from 9.10, it took about 90 minutes including download.

After rebooting, on first sight everything works as it did before, including graphics, sound, desktop, LAN, WLAN, ....

Good Job!

Cheers, Felix

---

### Post by lessmemorelove on 2010-05-01
clean install from 9.10 to 10.04

1 hp amd 64bit dual core - saved only documents and pictures from home partition on clean install

1 n450 asus netbook - saved all of home partition on clean install

on the pc everything works as it did before except i lost printing and scanning again with my officejet. i always lose my officejet when i switch to a new ubuntu, though, so i am used to it. it is the price you pay for upgrading the day new software comes out.

on the netbook i had a few more issues. this was due to some poor documentation on "features" in ubuntu. it all works now. saving your home partition can result in weird behavior for any upgrade.

---

### Post by notquitemichael on 2010-05-01
I always find upgrading needs me to fiddle with my xorg.conf to keep my nvidia dual-screen setup, but i appreciate that you can't really blame this on ubuntu, and to lucid's credit its been the first version to have supported my configuration without needing the restricted drivers (although as I use compiz I've had to switch to the nvidia binaries.)

I've also had to self patch the grub file to allow plymouth to work with nvidia and fix gwibber's non-integer font-size issues (the bug-fix didn't seem to make it to lucid's launch packages :S )

Still can't get gwibber to add my facebook account, but looks like i'm not the only one so. Luckily i'm not all that social or well networked... :)

---

### Post by W.Elfo on 2010-05-01
I had a xp/Ubuntu 9.10 system. I have downloaded the 10.04 version & installed. It was ok until I noticed NO dual boot into XP available. Checked online & found & applied [http://ubuntuforums.org/showthread.php?t=1466169](http://ubuntuforums.org/showthread.php?t=1466169) as a solution. Now I can get into XP but not Ubuntu. 

Q. Since I can only access XP how do I undo "the Solution" or correct it (in XP) so both Ubuntu & XP are available?

I have been using Ubuntu starting with 9.04 for about a year only.

---

### Post by cludwig on 2010-05-01
Boy was I worried!!  I couldn't get my liveCD to boot.  I thought I really had bricked it.  I burned a fresh CD and all worked perfectly.  Thanks for the instructions!!

All is well now.

---

### Post by randyclark on 2010-05-01
I upgraded my Toshiba Satellite L355D from 9.10 to 10.04 . The two things I had to do to make it work were:

+ The "nomodeset" change that many have suggested

+ I had to comment out in my fstab the line that Virtualbox had added to allow mounting USB devices in Virtualbox guests. 

Both of these were neccesary for me to boot into 10.04 after upgrade. Once I made it past these two hiccups I was fine. 

Randy

---

### Post by untmdsprt on 2010-05-01
Install - got many problems that i've not been able to solve

Trackpad too jumpy when trying to type, haven't been able to find anything relating to my Macbook 2,1 to fix it.

Apple wireless keyboard still won't connect.  This the 2 battery updated one that came out recently.

Step by step instructions are needed since I'm new to everything.

---

### Post by jplinderman on 2010-05-01
I had serious (but surmountable) problems with a DVD install (at work) and an upgrade (at home).  In both cases, my screen went blank after I rebooted and made my grub selection.  I suspected NVIDIA driver problems, but I couldn't do the

System > Administration > Hardware Drivers

thing until I got a screen, and I couldn't get a screen until I installed the drivers.  I had to install a VGA card at work (already had a VGA port at home).  It worked, in both places, and the DVI ports are fine now.  Too bad there's no command line interface for NVIDIA driver installation.

I tried to post a more comprehensive reply, but it got rejected, and erased when I tried to preview it.  -- jpl

---

### Post by diffuze on 2010-05-01
Two problems after upgrading 9.10 to 10.04;

1) The resolv.conf gets wiped after each boot. 

2) The theme I use in Gnome don't show when I start my Gnome session. I have to click System --> Preferences --> Appearance for it to show up. Yes.. it's enough to just launch the Appearance app for the theme to appear..

Haven't found a fix for either yet, no show stoppers though I guess, not for me - but for a complete newbie they might be!

**Edit**: yes I use Gnome in Kubuntu. I started with Kubuntu a few years ago and when KDE hit 4.x I ditched it (hate it personally) and started to use Gnome instead. I have used the upgrade feature ever since.. that's why I'm still on Kubuntu rather than Ubuntu. Will choose Ubuntu when/if I choose to do a clean install.

---

### Post by nevyen on 2010-05-01
Downloaded and burned both 32 bit and 64 bit copies of 10.04 for my various computers. Decided to start on my main computer, the DELL with the 64 bit version. Did not work. After picking either Try Ubuntu or Install Ubuntu and hitting enter the screen would change to a blank screen with a blinking cursor. Tried all of the fixes for blinking cursors and blank screens (nomodeset, different cd drives, disconnecting hard drives, etc.) but no fix. Finally, being frustrated tried the 32 bit version and it booted into the try ubuntu mode flawlessly!

Figuring the disk was bad i tried using the 64 bit ubuntu disc on my hp laptop and it worked!

I don't understand why the 32 bit works and the 64 bit does not. I've had Windows XP 64 bit, Windows vista 64 bit and windows 7 64 bit installed w/o problems. Although I have never tried the 64 bit versions of the 9.04 and 9.10 ubuntu releases.

Any suggestions?

Dell XPS 730
Nvidia 790i ultra SLI
Intel E8400 3.00 Ghz
4 GB DDR-3 Corsair Memory
Nvidia Geforce 8800 GT
Creative SB X-Fi
Windows 7 Home Premium 64 bit

---

### Post by GrumpyBob on 2010-05-01
Upgraded a Mythbuntu box to the Lucid release candidate a wekk or so ago - very straightforward, no problems.
Upgraded a single-boot Sony notebook from Karmic to Lucid, also very straightforward, no problems.
Upgraded a dual boot Karmic/Win7 desktop PC to Lucid/Win7, very straightforward, no problems, both systems boot fine.

Another good upgrade experience for me.

Robert

---

### Post by Chindokae on 2010-05-01
In one word I'd describe this release as a catastraphuque.

I've been using and installing Linux since about 1993.  I have been an Ubuntu user since there has been an Ubuntu.  Version 9.10 (and 9.04) installed perfectly on my machine.  Version 10.04 refused to install and along the way tore up the existing 9.10 install - and I aborted at the partitioner step.  

This installer is an absolute mess.  The error posts are piling up at an unbelievable rate.  I've made my own as well. 

This was not a good effort.   The testing for 9.04 was vastly better than the testing for this.  Send it back to the showers get the next release right, like you normally do.

---

### Post by GrumpyBob on 2010-05-01
I got my facebook account set up on a previous version of gwibber, but deleted it when I realised I couldn't filter out all the stupid Farmville messages!

Just checked - the account details still work.

---

### Post by satyam on 2010-05-01
Just thought that I'd share my experience, and it has been a TERRIBLE one! I've got 2 hard disks, an old IDE and a newer SATA. The IDE had 7.10 installed, and i never removed it, just in case something like this happened. I'm typing this in 7.10. 9.10 was on the SATA disk.

Decided to upgrade from Karmic last night, and everything seemed to be going fine. I think i made a mistake when "grub" asked where to install to, and specified a partition rather than a disk. Then I got the "grub rescue > '_grub_puts' not found" message when i tried to reboot.

I thought, "OK, let's try to repair grub" . . . except that the partitions on the SATA disk are now corrupt??? I can't even mount them anymore, I get the "wrong fs type, bad option, bad superblock" message . . . what gives??? :confused: fsck.ext3 seems unable to help. And, it's not all of them that have been corrupted, because I can still mount the "Data" partition on that disk. Weird.

I was joking with a friend, "you know, I'm going to upgrade to 10.04, let's see what will break" . . . but this is ridiculous. I appreciate that the people who make Ubuntu do a lot of good work, but when stuff like this happens, I really feel to go back to the older versions. They may not have been as modern, i suppose, but at least things didn't break to smithereens.

Ah well, I still have 7.10 :)

Cheers.

---

### Post by jplinderman on 2010-05-01
It sounds like it might be related to the problems I saw (#248) since I, too, have NVIDIA cards in my Dell PCs.  But the office 64-bit install from DVD and my home
32-bit upgrade over the net *both* failed.  On the other hand, I was doing a full install and upgrade.  Do you have a VGA port you can connect to, so see if that makes any difference?  Did you hear anything that might suggest it was just the display?
-- jpl

---

### Post by DouglasAdams on 2010-05-01
> **Bristol_Green said:**
> I don&#8217;t like having to unlock the screen with my password every time I make coffee! I&#8217;m the only user here. Is there a way of disabling this feature?

system > preferences > screensaver m8

imo, the worst thing about this, which i hated too, was that "they" are now making decisions for our own good - just what i'd expect from M$ !!
hang on, this isn't M$

---

### Post by DouglasAdams on 2010-05-01
i've just noticed that Vuze does not seem to work at all.
and my browser, g/chrome which i previously left running for weeks on end, now keeps beeping at me. if ignored, the beeping seems to become continuous. funny, i don't remember installing tinnitus.
you've done a truly great job with this release guys!
gates and co must be laughing all the way to the help desk.

---

### Post by itsjustarumour on 2010-05-01
> **Simian Man said:**
> You could also say that most of the users here are Linux enthusiasts and are thus more likely to be able and willing to solve problems than the average user.  If a new user tries to install Linux and it fails for them, they may not even ever bother to come to the distributors forum.

I bet the poll is optimistic if anything.:KS

I absolutely agree.  The OP's claim is baseless and unsubstantiated.  I'd say the people who vote on this poll are more likely to be Ubuntu *fans* and experienced/technical users, who are actually *more* likely to be able to solve any problems that may arise - and have a happy end result - than the average joe-bloggs non-technical user. Most new joe-bloggs non-technical users trying Ubuntu for the first time and having problems installing it are just going to think "Ubuntu is crap" and give up right there - they're not going to come to this forum and vote.  Many of them don't even know this forum exists.

---

### Post by jjaakkol on 2010-05-01
I had several problems so in the end had to do clean install :/

[http://ubuntuforums.org/showthread.php?t=1468347](http://ubuntuforums.org/showthread.php?t=1468347)

---

### Post by daverush on 2010-05-01
Like a few other people had problems with Compiz mucking up my window manager, however the forums helped me solve it.  Looks good.:P

---

### Post by starweb350 on 2010-05-01
Hi, I'm back. A total of three computers updated to 10.04 now.

Clean install with USB drive on netbook yesterday. 
Update manager install on older celeron computer that I use for a studio (dual boot with windows xp).

AND....last night I started the update manager on our main computer
AMD quad core. Nvidia card ,msi k9n6pgm2 motherboard etc. 
I started it last night before I went to sleep and it said it was going to take 2 1/2 hours. It was done downloading when I woke up and it took another hour and half to install. It just went flawlessly! It is dual boot with windows 7 and everything is just like it was before except updated to 10.04
I am super impressed and really happy that I did not have any problems.
YAY!!!

---

### Post by DouglasAdams on 2010-05-01
> **itsjustarumour said:**
> :KS

I absolutely agree.  The OP's claim is baseless and unsubstantiated.  I'd say the people who vote on this poll are more likely to be Ubuntu *fans* and experienced/technical users, who are actually *more* likely to be able to solve any problems that may arise - and have a happy end result - than the average joe-bloggs non-technical user. Most new users trying Ubuntu for the first time and having problems installing it are just going to think "Ubuntu is crap" and give up right there - they're not going to come to this forum and vote.  Many of them don't even know this forum exists.
here, here. i absolutely agree!
i would think that the only question is can i hold on until the 2010.1 mandrake is released ...

---

### Post by Ububtubobl on 2010-05-01
I'm a 30 day user of Ubuntu and I upgraded 9.10 to 10.4 after 20 years of Windows.Took a couple of hours to upgrade almost everything seems to work (some file association issues with attachments in Firefox which were resolved) I'll no doubt tweak some things but the upgrade went fine. I used Clonezilla first to be on the safe side. I lurk in the forums to benefit from the experiences of others, and appreciate all the help even if you don't know I'm out here. Thanks to all.

---

### Post by Forbidden on 2010-05-01
Why isn't there an option in the poll for "No, Lucid bricked my system and I had to go back to Karmic?"

That's what happened to me.  I need the nvidia proprietary drivers, since I have two graphics cards running four screens.  Any time nvidia drivers are installed (from Ubuntu's own repository), my system is bricked.  Plymouth stupidity can't even boot into single user mode.  

Spending 45 minutes to install Lucid from scratch yet again, just to try some different settings isn't something I have time for.

---

### Post by byline on 2010-05-01
I did an install from the Update Manager. Seemed to go much more slowly than previous updates, a couple hours total. Had some minor problems once everything was installed: my e-mail and web browser windows were locked to the top panel, and there were no minimize/maximize buttons on any of the application windows. And the windows were all quite small. Hubby fixed all of that.

Then, when rebooting, I got an error message saying that the swap partition couldn't be loaded. Hubby tried a few different things, but didn't seem satisfied that any were effective. However, when checking via the terminal, it appears that swap *is* working. So either the error message was wrong, or something he did caused it to load. Or maybe it was a subsequent reboot that fixed it. Not sure. . . .

Other than those glitches, everything seems to be working fine. I'm hoping this upgrade magically fixes the mysterious unexpected logouts I was having occasionally with 9.10.

---

### Post by bergfly on 2010-05-01
Firstly, I cannot overstate the beauty of Clonezilla. Its a Murphy's law thing. Get a good clone prior to starting, and the upgrade goes flawlessly. Don't bother and you have issues. 

This is my 5th Kubuntu upgrade on my work Lenovo T61. Every time I have got a clone, I haven't had to use it, every time I have not, I have ended up doing a clean install...

Also, if you want to be current every six month I recommend the following partitioning. Two / partitions, one for the current and a spare for a clean install. That way you can do a clean install every time and still have access to the working old system if you have issues. Obviously you also need a /home partition that you point the latest install to. 

Having set all of this up and taken a clone, I tried the upgrade rather than a clean install and had no real issues. I'm now 3 for 5 on upgrades on this machine, so this was a good one. 

Disclaimers on this.. Firstly I did a full update on 9.10 prior to starting. 
Secondly, it took a few goes for Kpackage to finally let the upgrade commence. 
Thirdly I did put the laptop to sleep halfway through (not recommended procedure, but it had no effect)
Lastly I use Kubuntu, not Ubuntu as my default desktop, and this worked fine. Also, the upgraded gnome was a little fiddly, so I deleted all my user config files to go back to an out the box gnome desktop and it works well. It also looks nice!. Got a silverlight issue in firefox, but never use it anyway, so simply uninstalled it. 

Haven't had much time to play with it. Tried to connect my evolution client to our exchange 2007 server for a laugh and it crashed, but this a bit of a standing joke in that every release I hope and pray I can ditch windows (only outlook ties me to it) and every release go through the 30 seconds of forlorn hope...

---

### Post by yarnoiser on 2010-05-01
Sound simply does not work. I tried both the upgrade and the fresh install, nothing. I use an intel HDA sound card. None of the standard solutions worked. OSS got minimal audio, but it's quiet to the point where you really have to strain to hear it. No volume control apps will work for boosting the volume. Maybe I'll try the upgrade again in a few months, when patches or third party control apps are available, but for now, I don't see any choice but to revert to 9.10.

---

### Post by yarnoiser on 2010-05-01
Actually, scratch that, a last ditch attempt to restore audio was successful. I've posted it on a thread of mine for anyone having similar problems.

---

### Post by WasMeHere on 2010-05-01
Hello everybody,

I have been staying with hardy (because of LTS) on my main computer (desktop) with Asus M2N-VM DVI with AMD Athlon 64 X2 4400+ with 2GB RAM. I have tried but found no advantage to use 64 bits. Now I am preparing for a transition running lucid as the third boot alternative.

1. Installing ubuntu-10.04-desktop-i386 worked well on my main computer.

2. I have also tried running ubuntu-10.04-desktop-i386 live.

- in Sun Virtualbox from the iso image it worked well but the screen was limited to 800x600 pixels.

- in my daughter's IBM Thinkcentre with pentium 4, 2.66GHz it worked well. (She runs Linux Mint 6 on that computer, and my son runs Kubuntu 9.10 on a computer with the same specs. Both kids dual boot with Windows.)

- in an HP dc5100 with celeron 2.93GHz I had to switch ACPI off to avoid black screen. (That is no problem with hardy.) Anyway, then lucid was OK. (This computer is 'only for testing now'). Later on I found that it works with ACPI on if I use a newer monitor. Hardy could handle the old monitor, but obviously Lucid needs a newer one for ACPI to work.

- in an IBM Thinkpad 41 with intel centrino 1.6 GHz and 1 GB RAM it worked well.

- in a Dell Dimension 4600i with intel pentium 4, 2.8 GHz and 1.5 GB RAM it worked well, but I had to select the Sound Blaster card manually to get sound from the speakers.

3. I have not yet tried upgrading. Maybe I will do that after cloning the disk on my main computer. But I'll wait until the worst bugs in lucid will be found and fixed.
--
Final comments

- It is a little annoying that startup hangs unless I press a button to get the screen with language alternatives. (Later on I found that it is connected to problems with ACPI.)

- I am worried that memory is not cleared when applications are closed. At least that is what is reported by 'system monitor' or 'htop'.

- I have not yet tried to download and evaluate the multimedia packages. I hope that the 'Comprehensive Multimedia Howto' still works.
<http://ubuntuforums.org/showthread.php?t=766683>
Later on I could manage multimedia via an intuitive download promped by trying to run an mp4 file.

Best regards from a happy ubuntu user
Olle

---

### Post by fedexnman on 2010-05-01
been tinkering with ubuntustudio since 8.10, but really got going with it in 9.04, and loved 9.10 karmic, that being said , 10.04 has not been pleasant ](*,)( plymouth ,nvidia , ffado mixer , etc  ) so i'll stick with 9.10 karmic ( im ok with it :(),  so, ubuntu i guess ill see you in another 6 months! hope 10.10 will be better release.:lolflag:

---

### Post by wkulecz on 2010-05-01
Install was flawless (64-bit on virgin AMD quad core system with fresh out of the box hard drive) until I booted the system the first time.  The open source Nvida driver for my GeForce 210 screwed the pooch on my 1920x1200 Samsung LCD display -- stretched way too wide so I couldn't access any of the Gnome menus or the shutdown menu :(

Fortunately the "restricted drivers" icon appeard where I could activate it, so I installed the proprietary drivers and managed to mouse over enough of the shudown menu to reboot.  

Display is pretty much perfect now.

The "Software Center" is as lame for 10.04 as it was for 9.10 -- constantly nagging me to authenticate, and having horrible UI interaction with lots of "apparently dead" periods that then eventually recover.  Oh Well, I usually use symantic or apt-get any how, but this crap sure won't make me consider changing.

One thing I need seems missing in release as it was in the Beta -- Glade, its in the software center, but has no install button :(

--wally.

---

### Post by Autodave on 2010-05-01
Did one upgrade and one new install.  No problems at all on either.  Good job!

---

### Post by oldmrron on 2010-05-01
Upgrade and new installs on 2 computers, 1 Dell Inspiron laptop and a Dell Dimension desktop. The laptop completed with various errors that I was able to work through. Issues with thunderbird, kmail, synaptic, akregator, Ubuntu One etc.. Laptop is mostly functional with a few lingering issues that hopefully will be resolved soon with upcoming patches. For now I will keep track of the issues and maybe do a few Bug Reports. No big deal and the system is usable. I do like the new features and colors, way better than the old Brown stuff. :)
My desktop however is a whole other issue. This comp has 2 - 1TB drives mirrored with 9.10 and split off for the Lucid upgrade. Upgrade bombed out with so many issues and problems with grub2, etc that I ended up doing a complete new install and completely wiping the 1st drive and repartitioned. Thankfully - I have the mirror disk to recover files from. The system installed OK for the most part, with just a few workable issues. At first things seemed fairly stable and grub2 was working now. The Show-stopper for me was the install of VirtualBox, LVM2, thunderbird and bluetooth driver support for my Logitech Linovo Keyboard. Had to reinstall bluetooth after each reboot and reconfigure and reconnect the keyboard. Weird since I never had a problem with the previous version of Ubuntu! Gave up on that and connected a regular USB keyboard. After installing LVM and rebooting, I lost the LVM disks and LVOLs I just setup! WTF! OK, so I bagged that idea also and just used gparted and setup regular partitions. Now on to installing VirtualBox OSE. I wanted to use the Sun version, but alas nothing ready yet for Lucid. This was a "Virtual Nightmare" and I never was able to work through all the issues with that. Everything from kernel problems to issues with VBoxManage hanging and crashing while attempting to import my previous VMs. So back to Karmic for a while until Lucid is a bit more stable and the developers get a chance to work out a few of the kinks. It was a fun exercise though and I learned a lot more about Ubuntu, Virtual Box and LVM2. I think the dev teams did a great job bringing us Lucid so far. Looking forward to being able to use it on all of my boxes soon! Thanks guys for all of the work you've done!

---

### Post by kfrancart on 2010-05-01
Upgrade from 9.10 on Dell Dimension 9200 Desktop only upgrade is RAM and HD. Worked flawlessly.

Upgrade from 9.10 on Dell Lattitude D620 only upgrade RAM and HD. Problem with external video display not allowing to go to 1980x1200, stuck at the highest resolution of the laptop display of 1440x900. The nVidia X Server Setting app was missing from the installed drivers. It is how I always switched over to my larger screen on my desktop.

Did a manual install which removed default nVidia drivers and installed drivers per the link below and it worked as it did in 9.10. Still using the NVIDIA X Server Settings app to change to the higher resolution. Seemed like I really only needed the app. Too bad it wasn't included in the nVidia install.

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")

---

### Post by edh31 on 2010-05-01
Installed it from scratch, but after a few restarts my gnome-panel stopped working, the volume icon appears twice and replaced the network icon (I can't use it), everything on the right of the panel disappeared.


Is there a solution for this? :confused:

Thanks.

---

### Post by cabruca on 2010-05-01
> **Judge P said:**
> Well done to the Ubuntu team!

Only other small thing was the Firefox icon on the panel was a red circle with a line through it, so removed and re-added to panel then OK.

JP

I will try this solution, but the icon on menu is black too. How to fix it?

Thanks!

---

### Post by deathblossom on 2010-05-01
Well, once I got it to install, it actually went really well. Had some trouble with the LiveCD where it was stuck on the five dots screen...really needs to be some feedback there because even after going to "nomodeset", it stayed on the screen for over 15 minutes before booting into the desktop.

I was shaking in my boots that my dual-boot with Windows  7 would go fubar like a lot of people's seemed to, but I haven't had any problems. Well, there was that one where the buttons ended up on the wrong side for some reason, but that was an easy fix.

---

### Post by Naggobot on 2010-05-01
I upgraded today my Acer 5021wlmi laptop using alternate CD. I had one peculiar problem. 

**short story**
Lucid alternate upgrade stopped when the system had downloaded 1410 packages from the alternate installation CD and asked for lucid installation CD.


**long story **
I downloaded both the alternate installation image and desktop installation image from torrent. 
(try 1)
I burned the desktop installation image to CD in case the upgrade fails and I need to reinstall from scratch. 

Then I mounted the .iso image and run the update script manually as instructed here

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

Upgrade started OK and I selected for the upgrade to update through Internet also. I had hooked up a cable for this purpose, I did not trust that the wireless would work flawlessly through upgrade. 

Upgrade calculated that 1450 packages needed to be updated. System started loading the packages until up to 1410 and then it requested for me to insert the Lucid-10.04-i386 cd (image of which was already mounted). Just klicking OK did not work, so I tried inserting 10.04 installation CD (not alternative since I did not have that burnt). This of course did not work, the system just kept asking for the CD. 

(try 2)
Next I burned the alternate installation image to CD instead of just mounting the iso image directly. 

Same result, after the system had downloaded 1410 packages the installation asked for the lucid CD. I again tried inserting the official lucid installation disk and after this the system actually did something since the package download counter dropped to 1408. 

(try 3)
At this point I deducted that there has to be a bug so I decided to run the upgrade from mounted iso image again. (I selected this method since it is way faster than using actual CD) . As expected the upgrade hung at 1410 packages. Now my system was in a state where it might be beneficial to report a bug if just possible. 

So next I searched the net for how to do this for active process since just selecting report a bug from the menu did not work. After some detective work I came to conclusion that I needed to run 

```
ubuntu-bug processid
```in the terminal to make a bug report. So in order to find what the actuall process is (I suspected lucid, but was not sure) I had to cancel the upgrade once more to find out that what the active upgrade process is. I selected cancel for the CD dialog and close for the upgrade dialog. 

(try 4)
I ran the upgrade script again and when the upgrade hung I ran the ubuntu-bug command for lucid process id. Nice enough the system told me to run the command as sudo. Ok I did that, and after few seconds the system the system prompted that the source package can not be determined. :(

I decided to give up and selected once again close for the CD request dialog and close for the upgrade dialog. BUT this time I noticed that the progress indicator bar had started to proceed (it actually flashed up till the end in few seconds but my finger were faster). Naturally the upgrade was already canceled and the system reverted. Anyways this pointed for me to run the upgrade once more and just to see what might happen if I did not hesitate as usually and would give some time for the upgrade to proceed. so 

(try 5)
I started the upgrade and waited for the bar to proceed to 1399,1400,1401 (tension rising), .. 1408, (getting ready to cancel the CD dialog), 1409, 1410, 1411, 1412 

WTF? it just ran and ran until 1450

I do not know what happened but that was it, it just worked :confused:. 

After that everything was pretty much boring. I had one prompt asking for wireless driver fetching and configuring (b43-fwcutter I think) and one prompt for Grub update and that was it. I did not have to do anything else. 

Now since I did not mess everything up yet I think I will try to update to ext4. 

Happy luciding (what ever that means) for everyone :)

---

### Post by Zimmer on 2010-05-01
Ok install in about 1 hour. HP Pavillion DV6000 series 

Installed to external USB HDD  and DID NOT put GRUB on MBR as already have a Mepis install on that drive.

Sent GRUB2 to the Lucid partition (where it is still sulking) and booted in Mepis to edit the menu.lst there (GRUB 1) and create an entry for LUCID.

Re Booted and selected the Lucid entry from the Mepis GRUB menu... and here we are...  in what looks like  a pretend MacWorld  (just need to install CAIRO Dock to complete the illusion )  :)

I'm quite disturbed by the fact it  looks on first boot very much like my 9.04 install (which uses the New Wave theme with dark menus) !!

 So I may miss playing with fonts and themes and leave it as it is for a while, test the install for a month or so and decide whether or not to upgrade the day to day 9.04 on the internal drive.

---

### Post by Frantic_Earthling on 2010-05-01
Fresh install. Worked flawlessly.

I dual boot with Win Vista. For some reason, Grub did not identify Vista at first. A *sudo update-grub* immediately set things right. That was my only problem.

The restricted nVidia driver installed without problems (Ge 7600).
Compiz Fusion was up and running in no time.

I installed both my Brother DCP-750CN printer/scanner and my DS410j NAS server without a glitch and both work perfectly.

Karmic was a disaster for me:(. What a change!:)

---

### Post by R.U.Sirius on 2010-05-01
> **TinyDoctorTIm said:**
> [SIZE="3"][FONT="Times New Roman"]The _real_ problem is Firefox causing the computer to crash. Not just the brower, either; the computer crashes entirely and has to be rebooted. Haven't seen that kind of behavior since Windows 98.[/FONT][/SIZE]

i got the problem with Firefox too. it hangs and takes the whole system with it. no ctrl-alt-F1 for console, no xserver restart, nothing works. and system-monitor shows 100% cpu usage. only the off-button on my tower works
;-)
i had the same problem sporadically in karmic.

---

### Post by Tanker Bob on 2010-05-01
This was the worst upgrade experience I've ever had in Ubuntu by far. Lucid trashed my NVidia display setup before it even rebooted from the upgrade and then reordered my hard drives and reported them as corrupted rather than mounting them in their new order, bricking my system. It wouldn't boot to the GUI or in recovery mode, locking up instead. Oh, joy.

I started fixing it using SystemRestoreCD just to get Lucid to boot in recovery mode, then followed with further fixes in the Lucid recovery mode console. After getting the GUI up in basic VGA mode, it took some effort to get the video drivers loaded because of the screen limitations in VGA. After recovering my display. I finally recovered all my hard drives (there was nothing wrong with them) by manually editing /etc/fstab. It only took about three hours to get a usable system and it all works fine now, but a newbie would never have gotten there.

New, slick interfaces are a nice goal, but somebody had better be paying attention to the core functions of the operating system instead of playing with the window controls on the window title bars.

FWIW, we need another poll category for "Major problems I eventually fixed." "Few things to fix" sounds too trivial when describing serious issues that prevent the OS from booting.

---

### Post by mindstalk on 2010-05-01
Tried upgrading from 9.10, failed:

> 
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'ubuntu-desktop' is marked for removal but it is in the
removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the
'update-manager' package and include the files in /var/log/dist-upgrade/
in the bug report.


And now, after reverting, "check for updates" is broken:

> 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following
signatures couldn't be verified because the public key is not available:
NO_PUBKEY 632D16BB0C713DA6


I've been able to upgrade without major problems since whatever version was current in August 2007, though this is probably the first time I tried upgrading a few days after release.  My last upgrade, from 9.04, was only a couple of months ago. :)

---

### Post by sashby on 2010-05-01
I had to choose "Install with many problems I haven't been able to solve" because  I thought that "haven't been able to solve" was the salient point.  I'd like to comment further though...

Overall I'm _extremely_ happy with this distribution.  The installation was fairly smooth - my video even worked right out of the box, even with a new Radeon 5770 video card.  Had initial video corruption problem, but that turned out to be a defective video card and is resolved.  Upgrades install seemlessly 99+% of the time.  I got sound working without too much difficulty (more operator error I think).

HOWEVER -
I am having a problem that I can't figure out and it's major.  For no apparent reason the machine freezes completely - sometimes after a few minutes, sometimes after a few hours, and without any error messages.  Machine doesn't respond to SYSRQ commands (REISUB).

I'm still working on it - the previous distribution (9.10) seems solid on this machine, as is the 9.10 Livecd.  The 10.04 distribution and Livecd both freeze.  It could be nothing - but it's a bit frustrating trying to solve it.

From what I can see, 10.04 looks nice and seems to perform very well - but for this problem.

**SUGGESTION:**
Include an option in the survey for "had a problem or very few problems that aren't resolved."

---

### Post by the8thstar on 2010-05-01
This is by far the easiest install I ever experienced. 

I installed Lucid on both my old P4 desktop (1GB RAM, 60GB HDD, 256Mb NVidia) and on my Core Solo laptop (see sig for specs).

The reason why it was so easy is because :

1. I did a clean install instead of an upgrade
2. I have a separate /Home pratition on both computers, this way all my settings are restored when I reinstall the related programs.
3. I installed Ubuntu Tweak

Overall it's a breeze and the new UI rocks big time.

---

### Post by dragonboss on 2010-05-01
Had a flawless fresh install. The only things that caused me to frown a bit was the fact that the b43 drivers had to be downloaded, forcing me to go downstairs to access the net via Ethernet to get it to work, oh and that my backups i made were a day or two older than what i wiped, but hey thats not Ubuntu's fault now is it?:grin:

---

### Post by luvr on 2010-05-01
Fresh install on a Dell Studio 17 laptop.

*Almost* perfect; only issue was with the wireless networking interface (*Broadcom Corporation BCM4312 802.11b/g*), for which the firmware wasn't available on the system.

I didn't want to go through the hassle of connecting the laptop through ethernet (I'm not enough of an acrobat to get that done); ended up downloading the **b43-fwcutter** package on my desktop computer, and unpacking it to see which actions it would take to get the wireless interface working.

Here's what I eventually did:
[LIST]
[*]Still on the desktop, ran the following commands to download two files:
```
wget http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```
[*]Copied the two files, plus the *"b43-fwcutter"* program extracted from the package, to a USB stick, and transferred  that to the laptop.
[*]On the laptop, ran the following commands:
```
sudo ./b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo ./b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
```
[*]Rebooted the laptop (though I could probably have done some *"modprobe"* command instead). The wireless interface instantly came up (*in fact, I'm using it at this very moment*).[/LIST]

**_Tests remaining to be done: Printing_**

[INDENT]Will Lucid **finally** be able to print on my brother's HP PSC 1100/1200 series printer? Ubuntu has always refused to print on that device (except, sometimes, for the test page), but I have largely ignored the problem so far. Will open a bug report if it still doesn't work; will, then, test with a few other Linux distros (particularly, Linux Mint and Mepis) as well, to see if it's an Ubuntu or a general Linux problem.

Next, I also wonder if I can get my dad's Epson P50 (*or some such*) to work; I haven't been able to find a suitable Linux printer driver yet.

Haven't tried my own Samsung ML-1610 yet either, but I would be surprised if that didn't work, since it has been doing fine ever since Ubuntu 8.04 (when I got the printer).[/INDENT]

---

### Post by pepik on 2010-05-01
Tried upgrade on Sony Vaio PCG TR1MP (circa 2004), on restart it went through the loading screen with the red dots under the Ubuntu logo, the screen went blank and then nothing happened. Tried clean install, but on boot from DVD it goes to the same screen and dies at the same time.

I've been through a few very easy upgrades on Ubuntu without any major problems before.

---

### Post by jolyonmiller on 2010-05-01
Thought I was going to have major problems when I couldn't use the mouse properly, no maximise/minimise buttons, no window borders, couldn't drag windows and no bottom toolbar. Fiddled around and found the visual effects (Tab in Appearance) had reset to basic in the upgrade. Changed it back to normal, and all problems solved. Works like a dream, thanks to all who worked on it!

---

### Post by arsenic23 on 2010-05-01
I'm loving Lucid.
This has been my favorite install experience since Breezy.

**[COLOR="DarkRed"]Pros:[/COLOR]**
No more HAL rebooting my PC and Blackberry whenever I plug it in.  Awesome.
Pulse audio is much much more stable then Hardy.
Everything feels more responsive and folders with huge amounts of images no longer cause nautilus to lock up.
Most of my settings migrated from Hardy (manually, I did a clean install).
Photoshop appears a run in wine a little more stably.
Boots faster.
Runs the fan on my Q6600 a little slower; less noise.

**[COLOR="DarkRed"]Cons:[/COLOR]**
Some programs have stupid stupid changes in their newer versions.  I'm looking at you Amarok, Kopete, GIMP, and comix.
Tons of stupid things to uninstall.  Stupid stupid social networking.
I'm still having trouble [finding a few settings]("http://ubuntuforums.org/showthread.php?p=9213261#post9213261").

---

### Post by brucehohl on 2010-05-01
Install was Flawless!

Some 8.04 to 10.04 comparisons:

(1) GRUB to fully loaded desktop times:
    8.04  = 1:08
    10.04 = 0:33 - a 50% improvement!

(2) I really like the window close/min/max on the left. This leaves the top right free for clicking to regain focus on the clicked window.

(3) Firefox is much faster especially for Google docs and text zoom via Ctrl +/-.  OpenOffice is much faster (but hitting the Alt key still selects the File menu which is inconsistent with the behavior in the Windows version).

(4) The savage video driver was properly selected.

The overall speed improvement in 10.04 versus 8.04 is impressive. I was going to retire this 2.53 GHz CPU PC purchased in 2004 but it now performs quite reasonably. Well done Ubuntu team!

---

### Post by brydonhunter on 2010-05-01
Upgraded without any problems. System is much faster than Karmic and Karmic was fast.

I'm even getting used to the new button locations...

---

### Post by jaygo on 2010-05-01
about six hours into troubleshooting two lucid systems...

fresh install onto dmraid (six hours so far)

[LIST]
[*]since ubiquity now recognizes dmraid arrays, I thought I'd try installing with the desktop CD. The installer fails when it tries to format a partition, however. (a known bug from karmic & lucid alphas)
[*]I manually paritioned & formatted the raid array using fdisk & mkfs.ext4. Palimpset could see the partitions but couldn't format them (gave error about something else accessing them) and gparted could only see the physical drives whether the raid array was activated or not. (two hours)
[*]Ubiquity was able to complete the install now that it didn't have to format anything but it wanted to put the boot loader on sda, rather than the boot partition of the raid array. I changed it to the boot partition and have no idea if it worked as ...
[*]I find out grub2 can't boot from dmraid. The only workaround is to remove grub2 and replace it with the old grub, which will hopefully only take another hour to completion. (+two hours)
[*]following some forum posts, I've been trying to replace grub2 with grub but am getting errors & no success so far. (+two hours)
[/LIST]
upgrade from 9.10 (one hour to failure, expecting five+ hours to reinstall & restore)

[LIST]
[*]update-manager says I need 2.8GB of free space on my root partition and won't continue. I move files around and free the space up, then run it again.
[*]at some point during the installation, it throws errors up. The console shows some mentions of no space left on device. The manager says the installation failed and will now be rolled back.
[*]a few more installations continue to prompt me for input, however. Grub asks whether to keep my existing file or the new one, I answer keep since the process is rolling back the upgrade.
[*]after rebooting, grub drops to ...
[*]grub rescue>
[*]grub rescue> h
[*]grub rescue> unknown command
[*]grub rescue> help
[*]grub rescue> unknown command
[*]grub rescue> ?
[*]grub rescue> unknown command
[*](expletives). Now wiping and installing fresh from the alternate.
[/LIST]
</whining>

---

### Post by Jose Catre-Vandis on 2010-05-01
Fresh install of Xubuntu 10.04, alongside my current Xubuntu 9.10. Using the ALT CD all went well, I allowed it to install grub to the mbr as it found my 9.10 and Windows 7 installations.

Took most of the afternoon and evening to install/transfer everything, but all going fairly smoothly.

A couple of problems with thunar:

1. Can't use Detailed View due to a bug in GTK somewhere
2. Didn't automount USB sticks. Had to add hald to rc.local to fix that

Other issues/successes:
1. Nvidia proprietory driver has messed up the nice new bootsplash resolution, have to fix that
2. For the first time, audacious worked with pulseaudio out of the box
3. DVB USB stick worked out of the box after installing dvb firmwares on offer in hardware drivers
4. Used the vdpau ppa to get a couple of files, but the rest, x264, ffmpeg,mplayer etc, came from repos and mkvs and HDs working fine
5. GiMP still included in xubuntu
6. Noticed that the build-essential group of apps is not installed by default
7. boot up much quicker but the fireflies have gone :(

All very similar to karmic though with xubuntu, perhaps there is more going on under the skin, but on the surface all looks much the same (unlike the ubuntu facelift)

---

### Post by degarb on 2010-05-01
> **powerslave12r said:**
> ***Install - worked but had few things to fix, nothing serious though***


Did a clean install from 9.10.


Version : Ubuntu 10.04 AMD64 Desktop using ext4 JFS. 
Download time: Direct download in 11 minutes odd.
Issues: Broadcom drivers (STI not available through System> Hardware). Had to connect to the internet via ethernet, then apt-get install b43-fwcutter.
Machine installed on: HP DV6400t notebook AMD Turion x2 2.0GHz, Broadcom Wireless card, dual boot with Win 7.


Done. I'm in love all over again.


My machine has no ethernet cable socket.  So I would be dead in water!!!  Not to mention, not a but a half gig free on drive.  6 gig drive.

System requirements increase any?

---

### Post by joemilx on 2010-05-01
Clean install of Netbook flavor on ASUS 904HA netbook is unusable.  Screen flashes endlessly.   I had no problems with previous release.

---

### Post by techunit on 2010-05-01
Well It worked like this... Installed it and Installed Restricted Drivers.... But The Powersaving features suck... My system keeps getting pretty hot...:guitar:

---

### Post by wcorey on 2010-05-01
I manage four systems, 3 at home, one at work.
The one at work I will not upgrade.

At home..

a 32bit Dell laptop, 1GB memory single cpu
a 64 bit Dell 720 with 8GB and 450GB disk
a 64 bit Dell 9000 with 12GB memory and 4 HT cores, 750GB disk

The laptop actually upgraded cleanly, no problem.

The 720 was an upgrade, it went smoothly but the panel icon for FF broke so I deleted it from panel and created a new one. The biggest issue here was with a Thunderbird instance 2.0.24 that was upgraded. In the process the upgrade considered the version of the c++ stdlib the TB 2.0.24 used deprecated and removed it as it had removed it and upgraded to TH3.04.  Thunderbird 3.04 did not allow me to get new email due to changes in how it stored user passwords. From what I researched the best advice was uninstall TB3 and reinstall TB2. Apparently you could futz around with the TB2 config files and then reinstall TB3 or, as some users decided, just stay on TB2. Well, not only had the stdlibC++ version 5 removed it no longer existed in the repository so I couldn't go back to TB2.  Eventually it started to work but I don't know why, I had given up on it.

This machine is the cloud, cluster, storage, and Walrus controllers for my private cloud.  I had this largely working under 9.10 but removed and reinstalled the packages so, as the documentation says, it would in the post install triggers, guide me through installing and configuring each component. It did not.

The final system, Dell 9000 was (under 9.10) and is to be under 10.4 the node controller for the aforementioned private cloud. 

The Dell 720 came with RAID0 and Vista which I promptly overlaid with 9.04. It beautifully accepted the RAID 0 environment. The 9000 came with Windows 7 which 9.10 beautifully overlaid in a RAID 1 env. I thought I could simply drop U 10.4 server on top of it. Not to happen. It broken the disk such that I couldn't get back to U9.10. I couldn't even get back to Windows 7. I eventually got Win7 back and tried to go back to the U9.10 desktop..no luck. I finally removed the bios raid 1 and spent the next 2 hours trying to install server on it in a software raid environment. I believe the instructions were broken and it took several fits and starts. It did install the node controller but, as with the desktop 10.4 cloud controller, did not prompt me for anything. 

One of the steps in the node controller installation is to synch eucalyptus passwords to the cloud controller. This does not work. There is no /home/eucalyptus so there is no /home/eucalyptus/.ssh. I thought maybe I should adduser eucalyptus which took but still no /home/eucalyptus. There is, however, a /var/lib/eucalyptus that does have a .ssh to use as the -i param on the ssh-copy-id. It still does not work. So, as far as I am concerned the installation procedure is whacked. I have not found anything that corrects the instructions for adding a nc from U10.4 so I am, once again, stuck.

Is there any wonder I am not going to subject my work machine (U9.10) to this horror show? And I've been using Linux, as a developer, for years.

---

### Post by wcorey on 2010-05-01
deleted

---

### Post by jtniehof on 2010-05-01
No problems at all on the Eee 900HD. I grabbed the alternate ISO via torrent and imported the packages into apt-cacher-ng, which sped things up a lot (although any packages not in the ISO were very slow to download).

The ThinkPad R60 was much more of a pain. I couldn't get the "new version available" to show up in update-manager. It turns out .update-manager-core had wound up owned by root, thus not writeable, and update-manager won't show a new version then. (I need to file a bug on that; it should at least complain.) Obviously the download went fast since most of it was cached :). First boot didn't work for some reason; sat on "Starting up" and grinding the hard drive, then changed to a mostly black screen with red squigglies across the top. Booted into the live CD and that worked, so just tried rebooting back into the system and it worked this time.

I see there's now a checkbox for disabling the "login ready" sound; a little annoyed it doesn't honor the "no event sounds" gconf setting that disabled it in 9.10.

---

### Post by teaguzzler on 2010-05-01
Hello, I'm new to Linux, VERY new. I had koala on my laptop for about two weeks. Tonight I installed this new version. I to had a page full of IO errors, but it restarted and things seem fine. Is there something I need to  do? Thank you!!!

---

### Post by byline on 2010-05-01
> **byline said:**
> 
Then, when rebooting, I got an error message saying that the swap partition couldn't be loaded. Hubby tried a few different things, but didn't seem satisfied that any were effective. However, when checking via the terminal, it appears that swap *is* working. So either the error message was wrong, or something he did caused it to load. Or maybe it was a subsequent reboot that fixed it. Not sure. . . .
Oops, spoke too soon. We powered down during a thunderstorm today, and when we rebooted, we got the same swap partition error message, so it's still not being mounted automatically on reboot. I guess that when hubby was trying out several things earlier, he must've got it going manually. That appears to be the only lingering problem we're having with this upgrade.

---

### Post by ferd on 2010-05-01
Unmitigated disaster. Tried to download, burn and install. Failed four(4) times. Tried to upgrade. Failed. Lost seven(7) hours of my life I will never get back.  That time does not include the time required to make all the changes I need to make to optimize my computer for my use. When will I ever learn. Canonical is not capable of releasing when ready but is willing to screw users to meet an arbitrary schedule.

OK, it is more than three weeks later. I have succeeded in installing by the upgrade method. This was almost painless taking about ninety minutes. What changed? I believe I had tried to upgrade from a site  that did not have 10.04 packages so it gave me an error instead. Oh well. All is right now.

---

### Post by manzdagratiano on 2010-05-01
Okay... a few things happened - I did a clean install (I prefer that since there might have been a myriad changes in the internals since the last series), which completed in about FIVE minutes (no kidding!), just like Karmic had on my machine. However, when I reboot, I see that grub welcomes me with "error: symbol grub_puts_" not found, and dropping into rescue mode:
grub-rescue>
Now I ain't no stranger to the command line, in fact I am quite addicted to it, but I was a complete stranger to the grub command line. I muse, "Let us boot back from the USB drive and repair the grub" - I insert the USB drive and reboot, and what pops up? - it is not the `ubuntu' user environment, but the installed environment!!! - The system refuses to boot without the USB drive, and with the USB drive, it goes straight to the installed environment. I did try to fix grub by running a grub-install (using Method #1 of the Grub2 documentation - mount boot partition and install grub to it), but it did not resolve the issue - all it did was go from a grub-rescue> to a grub> prompt without the USB, and with the USB, it would again go into the installed environment. Time to try Method#2 - install grub to the MBR as instructed in the documentation... well now it installs it not to the boot partition but the root partition... on a reboot, I am now told, "the /boot device is not ready or not present, Press S to skip or M to manually install blah blah" without the USB drive. I am irritated by the fact that the USB key cannot be used to boot into the LiveCD environment. Also, the installed environment was perfect, except that now it refused to automount the USB drive - why would that be the case with Lucid?

I could stay on and fix the errors, but I was bored... so I reinstalled Karmic, and this is where I am. This is where I will stay until Lucid matures enough to not give me hassles with mundane issues like grub and automount - something like these were the reasons I left Debian after four years of loving it, since I got tired of dealing with mundane issues like wifi, graphics, automount, and so on. Ubuntu had given me that relief - with Jaunty, the only release so far that has worked spot on on my machine - wireless, graphics (nvidia), ntfs, etc etc etc. But Karmic was a disaster in the beginning, with its infinite restart loop on account of not finding nvidia and not falling back onto vesa after a fresh install (moreover the nvidia powermizer would have still plagued me had Launchpad not given me a workaround), and so is Lucid in the sense of this initial hiccup.

I have seen misery before - when I once installed Debian and all it gave me was the command prompt, and I had to painstakingly figure out entries in xorg.conf to be up and running (dpkg-reconfigure did not work enough)... I do have the stomach to do this once in a while, but I do not have the stomach to do this every time. I will never quit Ubuntu since it gives me something unique - the ease I want and the freedom of doing what I want how I want; but I guess I will refrain from the overzealousness of nuking my old install and trying the new one on the first day of the official release.

What I am going to do however, is to carefully test the new release on a virtual machine until I am satisfied I can risk the actual install - stuff like grub is unavoidable, but by this time, one might think that such essential issues would have been weeded out; I know grub2 is a new idea and will take time to be rock solid, but if it worked flawlessly on Karmic, there is NO reason it should not work on Lucid - I cannot blame the developers, since they have a lot on their hands, but I guess the phase of beta testing needs to be expanded out a lot more for such errors to plague new users.

---

### Post by gaalaaant on 2010-05-01
IF anyone is willing to help me with my issue of a wiggling screen,please feel free to at the address 

[http://ubuntuforums.org/showthread.php?t=1467678](http://ubuntuforums.org/showthread.php?t=1467678)

---

### Post by slooksterpsv on 2010-05-01
Here's my reply on the new 10.04 release:
Kubuntu: Upgrading from Beta2->RC->LTS has been great, everythings worked flawlessly.
Caveats: Package manager is better in Ubuntu, UI seems way huge on Kubuntu - I'm having trouble navigating windows - click issue with mouse and trackpad; if I click on the K Menu it pops up then if I click on something else it acts like I'm dragging something; even small ui software seems large with Kubuntu - res is 1366x768.

So I'm ditching Kubuntu and going with Ubuntu - I have it torrenting, and will let it upload at full speed after it's fully downloaded.

Ubuntu: Everything has worked perfect in it, haven't tried ATI drivers, but they worked on the Beta2 just fine, on the beta2 some apps would constantly crash - I think I read this is fixed so I'll be good either way.

Other than that, best release, IMO, ever!

Way to go Ubuntu team, you've made Linux look, feel, and run like Windows 7 - sleek, sexy, and powerful.:):KS:KS

---

### Post by Water_Spirit on 2010-05-01
Because 10.04 is LTS I decided to do some housework on my Laptop before installing, so reinstalled Windows deleting all other operating systems, then installed 10.04 Ubuntu and then installed 10.04 Kubuntu. The Triple boot is working flawlessly and all I have done is install wicd as my Network Manager. Very impressed with this release, thank you Ubuntu and those many people who are part of creating this awesome operating system.

---

### Post by karolinger on 2010-05-01
I was able to do a clean install with my mother's display because my CRT monitor goes to sleep mode after the boot screens finish loading. I'm able to use my monitor if I first boot with my mother's display and then after Ubuntu is fully loaded I change to my display.

My monitor works flawless in 9.04. In 9.10 it worked, but I couldn't change the screen resolution, so I reverted back to 9.04.

---

### Post by slooksterpsv on 2010-05-01
Brand new installation of Ubuntu 10.04 - got rid of Kubuntu as the UI (see post on page 31) was too big to use. So far, it's awesome, have some bash scripts copying my music, pictures, etc. over, installing restricted extras for flash, java, multimedia codecs, etc. going to install libdvdcss2 here shortly, change permisions on my stuff I copied over, did a sudo cp -R instead of cp -R - all in all, everything is working, nothings crashing, nothings slow, hard drive is cranking away - the only thing to make it all perfect would be for Netflix to work on Linux.

---

### Post by geodancer on 2010-05-02
This is my first upgrade and I did not enjoy it. I have Ubuntu on one HDD and Win7 on another. When I tried to boot the Win7 side, nothing happened. Fortunately, "bcbc" posted a link with instructions to use "testdisk."
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
That solved my problem.
In the poll, I gave the lowest rating for the upgrade even though I seem to have solved my major and perhaps only problem.  I did not enjoy losing one of my systems.

---

### Post by Andreas1 on 2010-05-02
> **itsjustarumour said:**
> :KS

I absolutely agree.  The OP's claim is baseless and unsubstantiated.  I'd say the people who vote on this poll are more likely to be Ubuntu *fans* and experienced/technical users, who are actually *more* likely to be able to solve any problems that may arise - and have a happy end result - than the average joe-bloggs non-technical user. Most new joe-bloggs non-technical users trying Ubuntu for the first time and having problems installing it are just going to think "Ubuntu is crap" and give up right there - they're not going to come to this forum and vote.  Many of them don't even know this forum exists.

i'm afraid there might be some truth to this. the technical users see through the problems and fix them within seconds, and the fanboys generously forgive a lot of glitches before they suddenly become haters (think i'm on the verge :-|). i voted "several minor problems", but the person i set that system up for would not have been able to fix those and the system would not have been usable for them, it doesn't matter if i fixed it within 10 seconds in a terminal.

i for one will be more careful advertising ubuntu, otherwise it will become the face of linux to the masses, and i don't think that would currently do it justice.

---

### Post by distrachi on 2010-05-02
**Selft Built AMD/ATI Desktop PC:**

Tried ubuntu-10.04-desktop-amd64 CD on my desktop PC. CD would not boot. No error message, it would just skip to booting from next boot device (HDD). Do not think it was problem with the CD as it booted when using notebook PC and passed integrity check.

I then tried ubuntu-10.04-alternate-amd64 CD and it booted fine. Install went smoothly. No problems with any of my hardware. Using proprietary ATI drivers and everything works great. Only problem is language selection does not seem to work from GDM login screen. Not a small problem but not a big problem.


**Acer Aspire Notebook PC (Intel CPU, Nvidia GPU)**

Used ubuntu-10.04-desktop-amd64 CD. Experience of somewhat opposite from above desktop. Install went perfectly, but some nontrivial problems afterwards. Very slow bootup, gives me error message about power manager not responding. Random kernel panics when using Nvidia drivers, I was able to fix this by turning off powermizer in xorg.conf. This is nvidia's problem though not Ubuntu's. Finally, suspend does not work anymore.

The suspend and slow bootup might be a deal breaker for me. If suspend worked then I don't really care about slow bootups. Or if it booted up quickly then i don't really care if suspend works or not. But having both means I'll be looking for another distro or going back to Windows. :(

---

### Post by rhawnied on 2010-05-02
I have to say that I had only a few minor (and I mean minor as in me not it :) ) issues with the upgrade.  I made sure to back up everything and crossed my fingers and ta da! ;) Good to go.

---

### Post by goldshirt9 on 2010-05-02
if i could get my laptop camera to work i'd say flawless.

there must be  a way somehow / somewhere :lolflag:

---

### Post by zatnuviz on 2010-05-02
Really good experience, i am happy with it, but there was some problems after installing it due to installation problems, at first sight it was doing it well, but after reboot, it wont load grub 2, i was able to manage this using the ubuntu 9.10 disc, because i haven't downloaded the disc just had click on update to get lucid, so i have done a grub reinstall, ( [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) ), and after it i was able to run my windows and ubuntu side by side, i must admit, lucid is faster that windows 7 in some tasks, and better at integrating social networks, so after that i get a good experience from this update, but all my buttons close, max, rest, where not there, so i check the forums for a solution, found it, and all is working well now, must say this is the best Operative system, gratz ubuntu team, i am enjoying it, but i think you guys must fix this little problems so users will be even happier

Also forgot to say that before my sound recording wasn't working, but after this upgrade all works smothly

---

### Post by crocdungee on 2010-05-02
Hi,

I have gone the upgrade route from 9.10.  Although it took several hours, the install itself went fine.:)  Just one point though - when it asked where to install GRUB, I didn't have a problem with this, but first-timer's might be confused by this.

I'm impressed with what I've seen so far, and it is all run very nicely.:)  I have encountered only two problems so far:

1. This is fairly serious.  When I have switched between users and then chosen logout I have ended up with a blank screen with no way of resolving without a reboot.  This has happened 3 times so far.

2. I have set up the new chat accounts function for Facebook google talk etc.  However, whenever I go to change my status it is greyed out.  I then had to de-select "enabled" for each account then enable it again.  For Facebook and GTalk it just shows "Disconnected - Network Error" and I can't seem to reolve this.:confused:

---

### Post by scotty64 on 2010-05-02
At first a big thank you for everybody who worked hard to get Lucid of the ground! While my main machine is still on Karmic, I installed Lucid (KUBUNTU) on my Samsung NB30 netbook:

What went well / is positive:
Booting the Kubuntu Lucid CD via external USB-drive worked without problems.
The main system installation went without any problems.
I am very impressed by the quick boot process - thanks a lot!
And thanks for bringing jackd back into main!

What could be improved:
The disk partitioning in Kubuntu. You only have the choice between complete manual partitioning or two ways of automatic partitioning that do not tell you what they will actually do (size of swap, etc ?). I suggest that the partitioner displays the partition layout before proceeding with the installation.

What did not work:
Wireless! The r8192_pci module gets loaded, but the wireless does not work. I had to blacklist that kernel module and use ndiswrapper / Realtek windows drivers in order to get wireless working.
The Samsung hotkeys. I followed [http://what-ho.posterous.com/linux-hotkey-support-on-samsung-laptops](http://what-ho.posterous.com/linux-hotkey-support-on-samsung-laptops) to get them working.

Overall experience:
Thanks for Lucid - I am enjoying it!

---

### Post by bunyip007 on 2010-05-02
well , must say my experience was frustrating to say the least , Up grade from 9.10 had mainly driver issues. Cross dependency with my ATI driver. Which i knew would have been a problem. Widely know issue with 10.04 early on. With 2 upgrade attempts , Had to re install 9.10 , found out how to actually do a real install by searching the forums. due to Screen going black on Live CD . If it wasnt for the forums , would not have got 10.04 working properly.

---

### Post by Gemba on 2010-05-02
Ditto the above post but with an Nvidia card and a LCD TV. I did an upgrade and kept getting a black screen. In the end I reinstalled out of frustration (which I haven't done for years now) and still got a black screen.

I left the black screen on while searching my laptop for solutions and much to my surprise Lucid finally booted!

After installing the restricted drivers for my Nvidia card Lucid now loads properly.

I had a few difficulties but eventually managed to install XBMC, my bluetooth keyboard and headset and open office was giving me an error message too. I'm pretty satisfied with the way everything is working now but it was the most difficult upgrade for a while.

---

### Post by kooia on 2010-05-02
Horrible... I can't get to Windows now.  I've read that it's a problem with the GRUB... 

Someone help!

[http://ubuntuforums.org/showthread.php?p=9216407#post9216407](http://ubuntuforums.org/showthread.php?p=9216407#post9216407)

---

### Post by Tom Tiger on 2010-05-02
I did the upgrade on 4 machines yesterday.

2 intel boxes (intel GPU and CPU) both worked flawlessly except on both the volume applet is missing

2 intel boxes with Radeon cards (4850 and 2400) on both compiz seized to work, one box (2400) works now with compiz the other (4850) no compiz (yet the driver is active.... desktop effects could not be enabled)

also on these the volume button is missing.

On my 2400 box the volume applet came back when switching the theme to ambiance but not on the other 3 boxes :-)

And it isn't in the add-panel list either....

For the rest, no problems with the upgrade, it went smooth and as fast as one can expect on an upgrade.

Wishlist,

-Volume applet....(or is this an oversight on my part? Help is appreciated)

-New driver for ATI to fix the Compiz problem (Luckily I'm not the only one :-))

- Conversion tool  ext3 to ext4

For the rest.... Kudos and Thanks to Ubuntu. It simply works when I need it. And that is what counts. Furthermore I love the new ambiance theme and the whole OS looks smoother and more professional. 

Would I recommend it?  Oh Yeah, it simply is good :-)

Well.. except for my little compiz snafu... but a solution will come along sooner or later.

---

### Post by silvari on 2010-05-02
Install was flawless. (Chose fresh install of Lucid into a spare partition, for / ; re-used the /home partition already being used by 9.10 )

Usage so far has been flawless. In fact it's a bit peppier than 9.10 , at least from a 'desktop-graphics-responsiveness' standpoint.

Machine:
- Intel Atom 330 Dual-Core (D945GCLF2 mobo), 2GB RAM
- WD SATA drive WDC WD3200BEVT-22ZCT0
- Hannspree HF207 LCD running 1600x900

Totally loving Lucid. Will soon be installing the Netbook Edition onto my Toshiba.

---

### Post by johann_p on 2010-05-02
Upgraded my Thinkpad T500 laptop and the uprade itself worked flawlessly. Did not use it enough to judge if anything was broken though.

I am rather disappointed  by the change of position of the minimize, maximize and close icons in the window title bar though: this is a major change of convention and usability and to do it without even telling the user why is an insult. Also, making it rather hard and hidden to change it back is something I do not like.
Does anyone know why this is forced down everyone's throat?

---

### Post by hacksaw1340 on 2010-05-02
1st machine: 

upgrade from 9.10.  All worked except ATi driver. Error Was looking for Kernel headers from previous kernel which was removed.  Failed.  reinstalled OS with 10.04.  no issues with dual displays. HD2400 ati chipset

laptop Dell d800.  

Upgrade: Worked fine..  Except, Broke,  Nvidia wake from resume.

shows old error or flashing red white screens on opening laptop screen.  added Option &#8220;NvAGP&#8221; &#8220;1&#8243; in /etc/X11/xorg.conf .  after reboot, OS would not show a logging screen. Just the start screen with 5 dots.  removed NvAGP from xorg.conf and all works except now still have resume/hibernate issues with video not working, again.

---

### Post by hacksaw1340 on 2010-05-02
> **johann_p said:**
> Upgraded my Thinkpad T500 laptop and the uprade itself worked flawlessly. Did not use it enough to judge if anything was broken though.

I am rather disappointed  by the change of position of the minimize, maximize and close icons in the window title bar though: this is a major change of convention and usability and to do it without even telling the user why is an insult. Also, making it rather hard and hidden to change it back is something I do not like.
Does anyone know why this is forced down everyone's throat?


gconf-edit  then look for metacity and change the look.   menu:minimize,maximize,close 

took me maybe ten seconds to change mine

---

### Post by BenB1 on 2010-05-02
The not serious on this end was basic preferences. I had to repartition a little bit, even that wasn't a huge issue. I had set up a home partition once before, re-installed Karmic and wiped that out. Have the home partition back now, will recall not to wipe it out next time. <chuckle> If you use a separate home partition lots of your settings and preferences ought to just carry over. Silly goober that I am just redid it all when having an issue due to power outage. The upgrade to Lucid went off well enough, though. There weren't any real troubling hitches aside from general Luser loose behind the keyboard. :) And those are nothing to worry over. Keep rockin' on.

---

### Post by jofox on 2010-05-02
I upgraded from 9.10 to 10.04 with the update manager. The whole process, including a download of over 1900 software packages, took over 4 hours.

The first thing I noticed was that the upgrade included new versions of Firefox and Thunderbird which did not support the Lightning Calender/Task Manager add-on. Consequently my calendar was wiped out and I had to reconstruct it with the Google calendar. Why did new versions of Firefox/Thunderbird have to be included in the 10.04 upgrade?

More importantly, however, is that this 'upgrade' does not recognise either my mp3player, flash memory stick, digital camera, CD reader/writer and DVD reader/writer. It also does not give me access to my second HDD which runs a version of Windows used mainly for a few Windows applications(not very keen on Wine)and scanning as neither of my scanners are recognised by Ubuntu.

I started using Ubuntu with 8.04, have taken each new upgrade when it became available and there have been little or no problems with any of the previous upgrades. This is definitely the most problematical upgrade to date as far as I am concerned.

PS - have now got access to second HDD and flash memory etc, CD/DVD drives through System-Administration-Disk Utility - when it opens properly this identifies each device and I can then manually mount each one and proceed as before with 9.10 (when they were automatically recognised and mounted). However, The Disk Utility programme doesn't always display any information in the relevant boxes. Have noticed that if I try to open Rhythmbox first this takes an unpredictably long time to open but when it does open I can then access all the info in Disk Utility. Have tried reinstalling Rhythmbox but makes no difference. The 10.04 upgrade is a good deal faster than 9.10 and I will live with this problem for the time being in the hope that updates will turn up that fix the problem.

---

### Post by Tom Tiger on 2010-05-02
Update, 

the volume applet isn't gone, see thread,

[http://ubuntuforums.org/showthread.php?t=1466309&highlight=volume+applet+lucid](http://ubuntuforums.org/showthread.php?t=1466309&highlight=volume+applet+lucid)

It's now under indicator.....  meh....

Now I just have the compiz problem.

System seems faster than 9.10 though.... on the whole, happy with the Lynx :-)

---

### Post by metalhead on 2010-05-02
The upgrade went okay until it restarted and got back to the desktop. The mouse and keyboard freeze and I have to reset the computer. This happens after 10 to 15 minutes and it doesn't matter what program I'm using. I've already posted this problem and sent a online bug report when I was last on Ubuntu within the last hour. I've ready several posts and I really hope someone comes up with a fix soon! [http://ubuntuforums.org/showthread.php?t=1469434]("http://ubuntuforums.org/showthread.php?t=1469434")

---

### Post by BenB1 on 2010-05-02
> **johann_p said:**
> Upgraded my Thinkpad T500 laptop and the uprade itself worked flawlessly. Did not use it enough to judge if anything was broken though.

I am rather disappointed  by the change of position of the minimize, maximize and close icons in the window title bar though: this is a major change of convention and usability and to do it without even telling the user why is an insult. Also, making it rather hard and hidden to change it back is something I do not like.
Does anyone know why this is forced down everyone's throat?

Not sure why it's 'forced'. But I got a real quick fix for you. Go into the Software Center. Search for Ubuntu Tweak, it has what you need to switch the title bar back to the old conventional way of the user interface. It can put the buttons back into the upper right hand corner for you. I didn't like 'em on the left either, kept getting confused. If you ever used Windows, then Ubuntu Tweak would probably be comparable to Tweak UI that was in Windows 95/98. 

So far I'm not finding anything 'borked' or broke. And I tend to be a fair to moderate power user of any operating system, and applications. Only had Lucid a day, been crunching at it, nothing is flinching so far.

---

### Post by BenB1 on 2010-05-02
<chuckle & grin> [hacksaw1340]("http://ubuntuforums.org/member.php?u=665865"), So many roads. :) I didn't think of that one, but hey it works too.

---

### Post by BenB1 on 2010-05-02
> **silvari said:**
> Install was flawless. (Chose fresh install of Lucid into a spare partition, for / ; re-used the /home partition already being used by 9.10 )

Usage so far has been flawless. In fact it's a bit peppier than 9.10 , at least from a 'desktop-graphics-responsiveness' standpoint.

"Uh huh. I thought as much, regarding the re-use of a home partition. Thanks for verifying."

---

### Post by dionysius on 2010-05-02
If there's one thing I'd recommend to people who are new to Linux or Ubuntu it's setting up a separate /home partition. It really saves so much time and hassle, so much so that I can't really notice much of a difference between Karmic and Lucid (and that's a good thing as far as I'm concerned).

Some trivial installation oddness:
At the end of install Ubuntu asked to restart the computer, but after clicking 'ok' I ended up with a black screen and the I/O error messages as has been mentioned before on this thread. Pressing 'enter' did the trick and it rebooted - but with another error message stating that the "critical temperature has been reached (90°C+)" and that it would shut down. But it didn't, instead proceeded to log in. 

Network manager had some issues with my 3G modem, but a cold reboot sorted that out (and also got rid of the temp error messages I had when rebooting to attempt to make NM recognise my 3G modem). 


No change/improvements:
After downloading and re-installing Emerald and re-configuring Compiz, window buttons are where they were before (until I re-installed Emerald I had no window decoration at all, and no buttons, which was interesting... :mrgreen: ) so no change there.

Sound works flawlessly: in Karmic I couldn't use volume control at all, had to keep it at its lowest level and use my external amplifier or sound would be distorted, but in Lucid it just works. 

My cube is still not as smooth as I'd like, but that's down to the Intel graphics and no change from Karmic so that's ok. 

All in all it went pretty well, the new log in screen looks nicer, haven't really looked at Gwibber yet (prefer prism for facebook). 

Thank you to everyone who's made it happen!

---

### Post by Danimoth on 2010-05-02
So far 2 upgrades and 2 fresh installs everything is fine. 
Also 1 upgrade from my bro, which is new to ubuntu and he managed to do it without asking me for anything(he usually asks me about details a lot), and it went smoothly. This actually impressed me.

---

### Post by hatalar205 on 2010-05-02
I have a Toshiba Laptop and a new Toshiba Netbook. Installation did well on both of them. But, on netbook (UNR is installed) boot time is sometimes very long. And there is a sound problem (since 9.04 it goes on, so not new. There is some threads about it. I can solve but I don't care much because normally its sound is too low.

Gwibber is really great. UNR 10.04.LTS's apperance is really awesome. I really like it.

It is too early to say something totally but I can say that this is the best and happiest Linux Installation experience I've ever had.

Thanks a lot developers. You are really developing something precious.

---

### Post by Amused2Death on 2010-05-02
I should apologise to those people whose dedication and work make these new distro's available.

Shouldn't bitch about something that's free that i didn't contribute to. So i'm sorry for the windows comment on page 21 of this thread.

I'm sure eventually the things that are not working well, will, and hopefully i can work out the sound issue with Diablo :P

Thanks for your efforts.

---

### Post by davidjxyz on 2010-05-02
Upgrade from Karmic to Lucid. Generally fine but the following issues:

* Problems with Intel 945GM graphics driver resulting in large black stripe at the bottom of the window. Solution was to remove all the nvidia drivers that I apparently had. Details in [this message]("http://ubuntuforums.org/showthread.php?t=1469411").

* gDesklets no longer working. Problem described in [this post]("http://ubuntuforums.org/showthread.php?t=1436753"). Solution was to re-install the previous version of gDesklets.

* Screensaver now locks by default. Solution was to turn that back off in System / Preferences / Screensaver.

---

### Post by Pjotr123 on 2010-05-02
Flawless on most of my computers. Clean install, as always.

Only on my Acer Aspire One A150 and A110 netbooks I had to do the following to enable the wireless chipset:

Applications - Accessories - Terminal
type (use copy/paste):
```

gksudo gedit /etc/modprobe.d/blacklist.conf

```

Press Enter.

Now add the following lines at the end of that text file (use copy/paste):
```

# enables the wireless chipset on the AOA 150 and 110
blacklist acer_wmi

```

Save, close and reboot. Now wireless should work.

Formerly, I had to do this in 9.04 and 9.10 as well, by the way. No big deal. :)

---

### Post by johann_p on 2010-05-02
> **hacksaw1340 said:**
> gconf-edit  then look for metacity and change the look.   menu:minimize,maximize,close 

took me maybe ten seconds to change mine

I know that also in the meantime, but it still not something that is offered to the user or even present in the appearence config dialogs.

Also, the main issue about this is why it was done in the first place and why no good reason for doing it was given whatsoever. This is about one of the most basic interactions with the GUI and you need a damned good reason to change it.

If the motivation was that they want to put something in the space that is was freed, then they need a damned good reason why not put that something into the space that so far already has been free in the left and leave those icons where they always have been and still are in other distributions.

So I am going to upgrade the remaining 3 Ubuntu computers in my family after some testing and I am going to change that stupidity back to the old behaviour.

After that a couple more work cokmputers and couple more of changing back an idiotic default. Get the picture?

---

### Post by Trailer_Lizard on 2010-05-02
Upgrade - worked but had few things to fix, nothing serious though

Had a tiny issue at the start of the upgrade where the Dist Upgrade app said there was another update program running.  Was probably the auto update check running in the background.  I simply stopped the upgrade, checked for any processes running in the background with htop and went back into the update program a few minutes later, check for any updates and then restarted the dist upgrade with no problems.

Second issue possibly more serious potentially.  Completed the download and installation, part of which was the Grub2 installation choices.  I have Win XP on SDA1 only for those times when I really do have to boot into Windows (few and far between now); and Ubuntu is on SDB1 for root, SDB3 for /home and SDB5 for swap.

I choose to compare side by side and in the end I trusted to use the maintainer's version and placed this on SDB1 rather than SDB.  I've had problems before with Grub legacy but Grub2 managed to get it right last time with 9.10 so I assumed it would be the same this time.

Even though Windows is on SDA, my main boot drive is SDB in bios.  When I rebooted I was left with this.

```

Entering rescue mode...
Error: the symbol 'grub_puts' not found
grub rescue> _

```

The same error as was experienced by [http://ubuntuforums.org/showthread.php?p=9207402&highlight=grub+rescue#post9207402](http://ubuntuforums.org/showthread.php?p=9207402&highlight=grub+rescue#post9207402)

The solution for this was found here [http://grub.enbug.org/Grub2LiveCdInstallGuide?highlight=%28live%29|%28install%29|%28cd%29|%28guide%29](http://grub.enbug.org/Grub2LiveCdInstallGuide?highlight=%28live%29|%28install%29|%28cd%29|%28guide%29)

If you just want to fix the problem, scroll down to the bottom of this article and use the commands, but make sure you use the disk Ubuntu is installed e.g. SDB1 & SDB, you can find this out by using GParted on the live CD.

The third problem was minor.  I managed to boot into Ubuntu sucessfully, and tried to start firefox which didn't start, along the same lines as this post [http://ubuntuforums.org/showthread.php?t=1469038](http://ubuntuforums.org/showthread.php?t=1469038)

The answer is simple, remove libmoon (Silverlight) in Synaptic and firefox works again.

All in all these problems are not show stoppers, but they're not the kind of things you want noobs to encounter.

---

### Post by winecurmudgeon on 2010-05-02
Clean install, mostly fine. 10.04 does boot more quickly -- so quickly, in fact, that WICD doesn't have time to make a wired connection before Thunderbird loads. And it looks good. I don't miss the brown.

A couple of points:

-- Having the same problems with the number lock not working when I did clean install of 9.04, but think I mostly have it fixed.

-- The system really doesn't like not using a password to log in. I have had minor problems with CDs not mounting and some software (Ubuntu Tweak) telling me I don't have permission to do something. After I rebooted, all was fine. I didn't have this problem with 9.04 because I used a password to sign in.

-- Hibernate doesn't always work, but I didn't expect it to.

-- The mouse has been freezing every onece in a while, which I read might be a Rhythmbox problem. I switched to Exaile, and we'll see.

--

---

### Post by lilbill on 2010-05-02
I did a fresh install of Lucid 64-bit on a dual boot system.  Downloaded the .iso via the torrent.  I have separate drives for the OSes so I planned to wipe 9.10 and install with the graphic installer.  I got the 'unrecoverable error' message and was dropped to a live-CD desktop.

From there I reran the installer and manually partitioned with a /, /home and swap partition.  Everything finished fine.  Upon initial boot I got an error on the splash screen saying that no /home was found.  Upon inspecting my fstab there was no entry so I added one (only worked after specifying with the UUID, using /dev/sdb3 failed as well).  Pretty good now.

Is anyone noticing that it takes a long time for the GNOME panels to load at startup?  My startup apps (terminal and Emacs) load quickly but the GNOME desktop panels don't load for about 20-30 seconds afterwards.

EDIT: This seems to be related to this [bug]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/539515").  The problem is that even if your system does not have a floppy disk drive, if the BIOS reports it then gvfs reports it and Ubuntu spends 30 secs. trying to mount a non-existent drive.  Disabling the FDD in the BIOS solved the problem for me and seems to be the recommended workaround for now.

Apparently, this is the cause of the installation error I received as well.

---

### Post by LADmaticCA on 2010-05-02
Clean install on my desktop and laptop. 

On the first boot after install, on the desktop, I got met with an X fail prompt. I chose low-graphics mode and all was fine from there. Really, really loving lucid on my desktop, it's soo fast.

On the laptop I had to add the *radeon.modeset=0* to disable kms, because it's causes the system to slow down. Also on the laptop, I have to load my wireless module with a custom parameter, or else I will get bad hangs when browsing. I helped test this release and knew of both these issues with the laptop, so it was really no problem for me. For a first-time user though, it would be enough to drive them away.

In conclusion, I'm loving lucid on both machines.

---

### Post by DouglasAdams on 2010-05-02
SCREAM!!
this is my third post in this thread ... or is it fourth?
found ANOTHER fault after upgrading,
all my links have vanished!
Dropbox, Zumodrive and even Unbuntu One

---

### Post by robstwd on 2010-05-02
Overall, I had a very easy clean install from 9.10 using a live CD to a system with dual boot with WinXP and a separate /home partition. No problems directly attributable to the OS upgrade at all. :)

However, as I had various configs saved to my untouched home partition, I did have to spend some (minor) time readjusting window themes etc, but most stuff just worked.
I also decided on upgrading to the latest version of Ruby (v1.9.1) and consequently have spent the last 6 hours fiddling to get some key scripts to work again! Have also spent a few hours reinstalling my preferred applications as expected and am still fiddling with a few bits & pieces.

Many thanks to the great work by the Ubuntu dev team for putting out another wonderful distribution.
cheers

---

### Post by argybee on 2010-05-02
Attempted upgrade KK to LL which ended badly. :confused:
No title bar on windows, unable to find drivers after every reboot, AWN fails, printer gone, etc. etc.)

Followed up with fresh install which worked beautifully. :)
It even seemed better than any install of any OS (and I've tried every one I could get my mitts on since PC DOS 1 in 1983.

---

### Post by ketarax on 2010-05-02
Upgraded Netbook Edition from 9.10 -> 10.04.  I'll fill in the poll with "Upgrade worked flawlessly" -- but only after I get a fix for (apparently just) one issue.

The desktop is stealing the focus/foreground from windows.  That is, if I launch anything (or there's a popup dialog etc), the window is visible for a few seconds at most, then the desktop/netbook launcher steals focus, effectively hiding the application window.

If I start a "2D" session there's no problem (except that Stellarium claims I've lost opengl -- this happens in the "3D" mode as well :/)

Pretty please?

Edit: this is on an Asus EEEpc 900.  9.10 was working splendidly (although I'd had to purge pulseaudio in favor of esd to get Spotify to play nicely under wine).

---

### Post by cpmman on 2010-05-02
My friend's Asus 900 had become infected with the MS boot loop virus after accepting a 'bonus' in Farmville.  After demonstrating 10.04 from a live cd and getting a positive reaction - even a "the buttons on the left won't bother me" (later showed how to change themes and button positions - "I can live with that - it's wonderful") installation using the install pictogram from the live cd reformatting the virus infected discs.  A post install synaptic update/upgrade demonstration later and all was well.  So far so good - cube well received and a couple of additions to Firefox (why isn't ABP included as standard?) Adobe flash and Skype.  Explanation of why an anti-virus is primarily used to protect others.

One new Ubuntu fan to add to the enlightened.

QED

---

### Post by fancypiper on 2010-05-02
I upgraded about 2 weeks before the final release and was surprised.  Almost everything worked and everything (except Apache which required a re-install) that was broken was fixed by the time Lucid was released.  I just now downloaded the install disks.

My oldest son is finally going to try Linux.:guitar:

---

### Post by jrbuckley on 2010-05-02
Thanks for the detailed reply.  I've got everything working now.  Turns out the problem was that I was reusing a /home partition from a previous distro (eb3). When I did a full reformat of both SSDs and rebuilt the partition table, everything went smoothly and 10.04 is working flawlessly, in both Gnome and une modes

---

### Post by bobnutfield on 2010-05-02
I have upgraded my netbook and main laptop so far.  Desktop still to go.  The netbook was upgraded via the Update Manager and went more or less seamless.  Did a clean install on the main laptop, and decided to finally use the ext4 filesystem.  I had previously shied away from it.  I keep a separate partition for my home directory, and even though I told the installer to NOT format the partition thinking I could "convert" to ext4 from the existing ext3.  Unfortunately, it did format the partition and I lost everything in my home directory.  Fortunately I had good backups.

So, for those who want to convert to ext4 from ext3 on a /home partition, it WILL format the partition.  Make sure you have backups of your /home directory!

On the plus side, the installation went reasonably smoothly.  I triple boot this laptop with Fedora and Slackware and use the Grub installation from Fedora to boot everything.  I do not like Grub2 and will stay with legacy grub as long as I can.  After figuring out that the UUID of the Ubuntu partition had changed, I was able to edit the menu.lst file properly and Ubuntu booted right up.  Lucid is fast, clean and attractive.  Network, network printing and all other hardware worked right away.  Graphics are better and quicker.  Boot and shutdown times are as advertised: much quicker.

Hardware:

Netbook:  Acer Aspire One, 120GB HD, upgraded via Update Manager

Main Laptop:  Toshiba Equiuum, AMD Athlon64 X2 dual core, RTL8187B network chipset, ATI X1250 built-in graphics (no longer supported by AMD with proprietory drivers, but the mesa drivers are now nearly on par with the proprietory drivers.)

Overall:  8 out of 10 for the experience.

---

### Post by floogy on 2010-05-02
I got svere unresolveable errors on upgrading my LTS/hardy to LTS/lucid lynx, due to apt-list-bugs (workaround) and dpkg/perl issue:
```

~$ sudo dpkg -i /var/cache/apt/archives/perl_5.10.1-8ubuntu2_amd64.deb     
(Reading database ... 524393 files and directories currently installed.)
Preparing to replace perl 5.10.1-8ubuntu2 (using .../perl_5.10.1-8ubuntu2_amd64.deb) ...
Unpacking replacement perl ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
Aborted
~$ sudo dpkg -i /var/cache/apt/archives/libio-stringy-perl_2.110-4_all.deb 
(Reading database ... 524391 files and directories currently installed.)
Preparing to replace libio-stringy-perl 2.110-3 (using .../libio-stringy-perl_2.110-4_all.deb) ...
Unpacking replacement libio-stringy-perl ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
Aborted
~$ sudo dpkg -i /var/cache/apt/archives/libarchive1_2.8.0-2_amd64.deb 
(Reading database ... 524391 files and directories currently installed.)
Preparing to replace libarchive1 2.2.4-1ubuntu1 (using .../libarchive1_2.8.0-2_amd64.deb) ...
Unpacking replacement libarchive1 ...
Setting up libarchive1 (2.8.0-2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
~$ sudo dpkg -i /var/cache/apt/archives/libarchive-zip-perl_1.30-2_all.deb 
(Reading database ... 524393 files and directories currently installed.)
Preparing to replace libarchive-zip-perl 1.30-2 (using .../libarchive-zip-perl_1.30-2_all.deb) ...
Unpacking replacement libarchive-zip-perl ...
dpkg: dependency problems prevent configuration of libarchive-zip-perl:
 libarchive-zip-perl depends on perl; however:
  Package perl is not installed.
 libarchive-zip-perl depends on perl (>= 5.10.1) | libcompress-raw-zlib-perl (>= 2.017); however:
  Package perl is not installed.
  Package libcompress-raw-zlib-perl is not configured yet.
dpkg: error processing libarchive-zip-perl (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libarchive-zip-perl
~$ sudo dpkg -i /var/cache/apt/archives/libcompress-raw-zlib-perl_2.023-1_amd64.deb 
(Reading database ... 524393 files and directories currently installed.)
Preparing to replace libcompress-raw-zlib-perl 2.023-1 (using .../libcompress-raw-zlib-perl_2.023-1_amd64.deb) ...
Unpacking replacement libcompress-raw-zlib-perl ...
dpkg: dependency problems prevent configuration of libcompress-raw-zlib-perl:
 libcompress-raw-zlib-perl depends on perl (>= 5.10.0-24ubuntu4); however:
  Package perl is not installed.
dpkg: error processing libcompress-raw-zlib-perl (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libcompress-raw-zlib-perl
~$ locale
LANG=de_DE.utf8@euro
LANGUAGE=de_DE.utf8@euro
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=C
~$ sudo debconf-show
/usr/bin/perl: symbol lookup error: /usr/lib/perl5/auto/Text/Iconv/Iconv.so: undefined symbol: Perl_Tstack_sp_ptr

```
[https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/573598](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/573598)
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/573696](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/573696)

This results in:
```
~$ sudo do-release-upgrade -d -m desktop
Checking for a new ubuntu release
No new release found
~$ sudo dpkg --configure -a
[...]
Processing was halted because there were too many errors.
~$ sudo apt-get -f install
[...]
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
~$ sudo apt-get dist-upgrade
[...]
E: Unmet dependencies. Try using -f.
~$ sudo aptitude full-upgrade
[...]
2937 packages upgraded, 970 newly installed, 279 to remove and 0 not upgraded.
Need to get 11.6MB/3583MB of archives. After unpacking 3305MB will be used.
The following packages have unmet dependencies:
[...]
Resolving dependencies...
open: 5312; closed: 4927; defer: 0; conflict: 77                                                                                                                   ONo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 10651; closed: 9992; defer: 0; conflict: 91                                                                                                                  .No solution found within the allotted time.  Try harder? [Y/n]n
Abandoning all efforts to resolve these dependencies.
Abort.

~$ sudo aptitude unhold cinepaint-data enblend freeglut3-dev libglut3-dev libplot-dev libxaw-headers  libxaw7-dev
Reading package lists... Done
[...]
Resolving dependencies...
E: I wasn't able to locate file for the libio-stringy-perl package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:
[...]
Score is 2412

Accept this solution? [Y/n/q/?] 
The following packages are unused and will be REMOVED:
[...]
47 packages upgraded, 15 newly installed, 24 to remove and 2955 not upgraded.
Need to get 0B/8566kB of archives. After unpacking 27.1MB will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Error!
E: I wasn't able to locate file for the libio-stringy-perl package. This might mean you need to manually fix this package.

```

```
~$ aptitude search "~ahold" | grep "^.h"
~$ 
```

Formerly the packages cinepaint-data enblend freeglut3-dev libglut3-dev libplot-dev libxaw-headers  libxaw7-dev were in the status 'hold', but I changed the status with the aptitude 'unhold' option...

I highly apreciate any help to solve the error
**dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.**

---

### Post by flarkit on 2010-05-02
Upgraded from 9.10 using the Alternate CD. I did a full update (180Mb!!) rebooted and then ran the upgrade from the CD. It started reading files off the CD, then switched over to downloading software and wound up grabbing 700Mb online! Not what I was expecting at all

So far, I'm once again disappointed by the shoddy upgrade to an existing OS installation. Compiz didn't work properly, nor did Wine and now I see that sound for Youtube clips in FF doesn't work either. The big concern is seeing FF freeze on video clips, whilst the Virtual Memory usage for "firefox-bin" ramps up to 2.5Gb. What the heck is going on?

On the positive side, pretty much everything else seems to be working fine. Hopefully Lucid Lynx will grow on me, I'd managed to get 9.10 working pretty well

---

### Post by markbabc on 2010-05-02
i upgraded yesterday on my eeepc 900 and it took about 4 hours with dl and then install but i got no errors which was great. i love the quick boot time it has but the first time i booted up my wi-fi card wasnt working but i rebooted and that got fixed. the only other problem i seem to be having is that my ipod-touch isnt being recognized but i can just ssh into it to put music on so no big deal there. other then that so far i havent had any errors and its been the smoothest install iv had yet with ubuntu.

---

### Post by dhopley on 2010-05-02
With 2.4ghz Intel Celeron , 1m RAM , 82865G Intel graphics card live CD install took 45 minutes . Worked flawlessly with manual partitioning . Thank you

---

### Post by sergiom99 on 2010-05-02
Install - got many problems that i've not been able to solve >

b/c they dropped support for custom DSDT files since KK, I have problems with power management, hibernation and such.

---

### Post by migs73 on 2010-05-02
> **shmoesmith said:**
> Well removing sun java really screwed me on my financial software that I use that is java based.  the openjdk just won't seem to launch the software.  I've also encountered black screens of death when trying to switch between profiles.  Mouse and keyboard are randomly locking up.  Unpluging/replugging them seems to have no effect (they are both USB) and I have to do a hard reboot to restore functionality to them.  

Very unimpressed so far.  About to throw in the 9.10 disk, format my whole root and go back.

I have had the same problem when switching between profiles. I also had this problem on Karmic so it did not happen with the upgrade. Not too much of a problem as I usually just log out and log in as the other user. Not much of a work around but not causing me too many issues just now.

---

### Post by old fert on 2010-05-02
I updated an old computer at my office (xubuntu test bed).  It took the better part of the day, but so far, so good.   Only one thing, it will not shut down completely, you have to unplug the computer.

I will wait a few weeks to upgrade my home and main office computers.  From reading the forums, it looks like a lot of bugs remain to be worked out.

---

### Post by freedomsramparts on 2010-05-02
I did a fresh install and it worked perfectly.  I was impressed as my previous two experiences with ubuntu were much less successful. 

I was using 9.04 (dual boot with Vista) as 9.10 would continually crash during install.  This was due to a reported bug particular to my notebook model, which was never resolved.

I took the plunge and did a clean install of 10.04 (no dual boot) and things couldn't be better. Bye-bye Windows. Well done Ubuntu team.

---

### Post by Philk on 2010-05-02
I tried the Upgrade route first, but had real problems.

I then BitTorrented the Install CD (64-bit) and had no real problems.

The one problem I did have was that Win7 would no longer boot after this install.  I do have it on a laptop, and I've decided that's the only place I'll keep Win any more.  I need it for Quicken and TurboTax and little else.  Win7 is probably the best version of Win yet, but Linux is now better, in my estimation.  I've been primarily Linux for the last several years.  I am now totally Linux on my desktop.

Kudos to the development team!

Phil

---

### Post by D3mon_Spawn on 2010-05-02
worked fine, boots fast, good job canonical! 

only problem for we was with the notification applet. my volume icon disappeared and hasn't come back.

---

### Post by terryt57 on 2010-05-02
I have very limited internet bandwidth (live in the boonies). I tried upgrading from 64 bit 9.10 to 64 bit 10.04 from the alternative install disk. When I used the option not to access the internet during the upgrade the install completely deleted the entire home directory. Luckily I have a clonezilla image to restore to 9.10. I then tried the same update only allowing internet access. It appears that the upgrade works but I get only a garbled login screen. I had the latest Nvidia drivers installed before the upgrade and I saw some errors in the message file about some Nvidia kernel stuff missing (sorry I can't now remember details). I tried changing the driver the vesa but that seems to have no affect on the issue. 

Clean install on another disk seems to work fine.

---

### Post by gwylan_du on 2010-05-02
Absolutely flawless. I was amazed. When I installed Jaunty last summer the install worked, but I had to mess around with sound quite a bit, so I was expecting the same again. I was gobsmacked that it not only worked out of the box, but better than Jaunty had.

I did take time to read the Release Notes though, and suspect that that was a good course... [http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)

---

### Post by mjbennison on 2010-05-02
OK. My turn...

Updated 9.10 (64 bit) to 10.04 (64 bit) via the release candidate version. 

Had an installation problem that it was just sitting at the splash screen doing nothing. I discovered by accident that if I hit the key 's' it would boot. Eventually found that this was due to Virtualbox and the fstab entry to support USB (see [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)). Also there appeared to be a Plymouth error that stopped the error being reported

I had a couple of dependency issues - libboost was one and I had to remove it and install the latest (didn't have any effect on the system as far as I can tell). Also melt was being reported for upgrade but couldn't due to a conflict with Openshot (removed openshot, updated melt, reinstalled openshot).

For some bizarre reason Neverball was uninstalled, but Neverputt wasn't as the common files were left behind.

Things that didn't work in 9.10 and do now:

[LIST=1]
[*]CUDA support for BOINC :)
[/LIST]
Things that did work in 9.10 and don't now:

[LIST=1]
[*]Docky crashes far too often
[*]Conky doesn't display my network settings
[*]WICD seems to start very late and therefore things that depend on network connections fail (e.g. mail notifier)
[*]No volume indicator in the panel (Gnome)
[*]No preview of music on mp3 file mouse over in Nautilus
[*]Lightning disabled as update for Thunderbird 3 is not compatible with my architecture (64 bit)
[*]The boot splash screen is shifted towards the bottom right so I have a  black border at the left and top.
[/LIST]
I have had no issues in any of my previous upgrades (from 7.04 onwards) so I'm a little disappointed with this as an LTS release - especially when things that previously worked don't.

---

### Post by Paulplex on 2010-05-02
*Install - worked but had few things to fix, nothing serious though*

All good on the whole; problems with codec support via Totem and VLC after installing MPlayer and a few other toys but where that's all I'd basically done, I reinstalled from scratch and second time around all worked as it should.

Don't like the location the window controls have been moved to, nor indeed aspects of the theme - but that's not a biggy and easy enough to put right...

---

### Post by Karl1982 on 2010-05-02
I upgraded my HP Pavilion dv6325 laptop from 9.10 to 10.04 yesterday.  I was unable to upgrade online, I suspect due to flooded repository servers.  I had no problem however downloading a set of CDs via bittorrent, so I decided to use the alternate CD to upgrade.  In retrospect, perhaps this wasn't a good idea.

The process took several hours.  After the upgrade, I found my wireless and video drivers had been disabled.  I was able to fix them the same way I do in a clean installation -- by finding a network cable, running apt-get update, and then installing the restricted drivers, although the Broadcom STA driver required me to download a few packages before it would install (this is a major problem for a clean installation).  On a side-note, I feel there should be an option during installation to allow restricted drivers if they're necessary for your system to function (such as broadcom wireless drivers).

I see the time zones were reverted back to city names instead of actual time zones.  I was very pleased to see actual time zones as choices in 9.10.  I consider having to choose a city 700 miles from where I live as my time zone to be... broken.

There's also the matter of my display themes.  The window controls were now at the top left corner instead of top right.  This was easily remedied by reapplying a theme.  However, I have been unable to figure out how to enable transparent windows, one of the major points of hype for 10.04.  I have a forum topic open on this, actually.  I've had one person tell me you turn it on with Compiz, but it seems that was poor advice.  I've heard a few people say it was delayed until something called "Lucid+1" but I have been unable to confirm this.  The window transparency was the only reason one of my coworkers wanted to upgrade, and after seeing all the problems I had here, he's going to stay at 9.10 for the time being.

The 10.04 upgrade also uninstalled xscreensaver, leaving me unable to run screensavers or lock my screen.  I imagine I can fix it by installing gnome-screensaver again, but I think it's a little absurd that you can't configure the screensavers in it.  I haven't resolved this problem yet.  I hope there is a new version of xscreensaver in the repository.

All in all... it was a long and dull experience, leaving a few key items broken, and I have yet to note any real improvements to the OS.  In my opinion, a distro upgrade should be at least as smooth, if not more so, than a Windows service pack installation.  This has a long way to go to reach that.

---

### Post by Ruazinn on 2010-05-02
Great upgrade!  Now significant problems at all.  The only insignificant problem was that on boot up in Lucid, I got the message: "An error occurred while mounting /proc/bus/usb".  This had to do with a line in /etc/fstab to get usb devices to work with VirtualBox in Karmic.  I just deleted the line and usb continues to work with VirtualBox in Lucid.

The first time I tried to upgrade, the server must've been flooded, because it failed about an hour in.  So I opened up the software sources app, had it pick the fastest server, then tried again.  About two hours later I was up and running in Lucid.

---

### Post by ngfrazier on 2010-05-02
2 of 3 computers fail to boot. On that, I would grade this release a D+/C-.

The first, is a Averatec 1020 laptop with the dreaded Intel 855m chipset. Wasted several hours trying to install/reinstall + various fixes. No go. Reinstalled 9.10 and it works.

The second, a Dell Dimension 8300 with a Radeon 9800 blanks out during loading the LiveCD. Cannot get to a desktop. Did not try a full install (I learned my lesson from the upgrade fiasco with the other laptop.) This Dell works perfectly with 9.10.

Quality control is lacking. I think Ubuntu should simply move to a rolling upgrade process like Gentoo. What is the point for a LTS release that is soo plagued with bugs? Ugh!

Love linux, but the "upgrade" process is so botched, I am learning to simply waits MONTHS after a "final" release in order to quash these show-stopping bugs. Ugh!

---

### Post by drizzt001 on 2010-05-02
*Upgrade - got many problems that i've not been able to solve*

Let me prefix this by pointing out that I'm a relative newcomer to Linux, so please be gentle.

I upgraded from 9.10 using update manager and I have been unable to boot properly since. When I switch on, the boot process seems to proceed normally until I get to the screen with the Ubuntu logo with the 5 dots below it. My screen then goes black, and my HDD light stops flickering. From that point, the only activity I get is that the cooling fan goes into overdrive for a few seconds every minute or so.

I have tried booting into recovery mode, and can get to the desktop by choosing low-graphics mode. After a while, the screen will just freeze and never unfreeze.

Just for testing purposes, I downloaded the 10.04 i386 ISO to see if I could boot into LiveCD mode, and it's doing the same thing as when I boot from HDD (black screen freeze).

My laptop is a Toshiba Satellite Pro A40, so I guess it's possible that it's just too old now to be supported, but it was working just perfectly with 9.10, and still does when I boot to 9.10 LiveCD.

---

### Post by fritzman on 2010-05-02
05/01/10 06:22:40 AM
For the past few weeks, I've been preparing myself for the almost-forced migration from Ubuntu Linux 9.04, also known as Jaunty Jackalope, to something newer.  I suppose I wouldn't really have to upgrade at all, except support from the Ubuntu community for Jaunty stops with the release of Ubuntu 10.04, also known as Lucid Lynx, on April 29, 2010.  
I've really enjoyed using Ubuntu 9.04 for nearly the past year.  All of the features and programs I use regularly are readily available via the main and community supported Ubuntu repositories, and the third-party proprietary  programs are also supported by the universal community as well, and, really, everything I want to use on my computer just work!  And they work very well!
There are a few programs which I use all the time.  Taken by themselves, just not getting one to work on Lucid Lynx might not be a deal breaker, but if I can't get it to work on Ubuntu 10.4, I just might stay with Ubuntu 9.04, Jaunty Jackalope.
Usually, a clean install will produce fewer problems than attempting an upgrade.  Although, it also means finding, downloading, and installing all the programs you currently have, whereas an upgrade leaves all your programs intact, with a few exceptions, and upgrades everything, including your programs.  So, an upgrade might be a little faster, assuming it doesn't choke and screw up everything, in which case a clean install would be faster.  Decisions.  Decisions.
Now, to upgrade from Ubuntu 9.04 to Ubuntu 10.04 needs to be done incrementally; in other words, first, upgrade from Jaunty to Karmic, then, upgrade from Karmic to Lucid. Since most of the upgrade can be done, running in the background with occasional prompts for something to be done in order to continue, I don't count this as down time.  Down time, in my estimation, is when the computer cannot be used for anything else, or my full attention is required to complete something.  So, although downloading and upgrading can take several hours to complete, my use of the computer for other things is barely bothered at all.
The first upgrade, from Jaunty to Karmic went smoothly, with just a couple of interruptions, and the required re-boot.  After logging into Karmic, I needed to re-install a couple of things, namely xscreensaver and grub.  (Yeah, I know!  I must be some sort of heretic.  Grub-pc is the greatest thing since the paper bag.  Yadda!  Yadda!  Yadda!  I prefer grub.  It's my computer.  End of conversation!)  I didn't really need to do anything else except manually edit /boot/grub/menu.lst for the new Karmic, and that, obviously, had to be done before the re-boot.  No biggie!  I've been editing grub for almost as long as I've been using Linux ….about 7 years, now.  
Oh, yeah!  I almost forgot!  The reason I had forgone the dubious pleasure of upgrading to Karmic in the first place; I have a Western Digital Passport USB 320 Gigabyte external hard drive which I use for backup of my entire system.  Karmic would recognize the /dev/sdxx differently each time the machine was rebooted.  Worse, it would also arbitrarily alter the UUID occasionally, just on that drive!  So, using the older /dev/sdxx method meant having to edit /etc/fstab with each re-boot, or contend with the icons of HAL-mounted drives cluttering up my desktop, or losing track of the drive completely sometimes if I used the default UUID method.  Never did figure that one out! I just went back to Jaunty, and skipped Karmic completely.  So, I did have to re-assign the mount points in /etc/fstab to accommodate the fickle Karmic naming joke.  No biggie!  Karmic was only going to be there just long enough to complete the upgrade to Lucid. And, as long as Lucid doesn't have this same problem, this whole endeaver will not have been in vain.
The upgrade to Lucid also went rather well, although not as smoothly as upgrading to Karmic.  For some reason, the upgrade insisted on removing an old kernel, linux-2.6.28.11, which it couldn't find.  It would choke completely, and halt the upgrade.  I honestly don't remember there ever being a  linux-2.6.28.11 kernel.  But, after several failed attempts to go on, I decided to try something a bit unorthodox.  I copied every instance I could find of the  linux-2.6.28.17 to  linux-2.6.28.11 in that same folder, i.e. /boot/*2.6.28.17* files were copied to /boot/*2.6.28.11* files, /lib/modules/ linux-2.6.28.17 kernels were copied to /lib/modules/ linux-2.6.28.11 kernels, and the same with /usr/src/.  
I tried resuming the upgrade again, and it was happy just having something named  linux-2.6.28.11 to uninstall.  After that, all went well until the reboot.  Probably because of the odd  linux-2.6.28.11 problem, my NVIDIA driver did not get installed properly, and that had to be re-installed.  
Also, Seamonkey was upgraded from 1.17 to 2.04.  That resulted in the problem of Seamonkey nagging for the master password every time I launched it, and randomly every few minutes while I was logged in.  P.I.T.A.  I did, however find the answer.  If the suggested fix of  “about: config  and changing 'signon.startup.prompt' from 'true' to 'false.' doesn't fix the problem, go to the ~/.gnome2/keyrings folder, and delete anything in it.  Reboot, and launch Seamonkey.  It will build new keys in that folder, and that annoying problem should be resolved.
I am now, quite happily running on my brand-new Lucid Lynx Ubuntu 10.04.  I think it's a keeper!

owa

---

### Post by kc600 on 2010-05-02
Upgrade - worked but had few things to fix, nothing serious though

Laptop: Like a charm, except after restart disk checking took forever. 

Desktop: Okay, except the graphics card worked in a low resolution (1024x768 max). (The card is a nVidia Corporation G72 [GeForce 7300 SE/7200 GS]) Fixed it by putting an xorg.conf (which i had removed on update to Karmic or Jaunty, i don't remember) back in place. The xorg.conf contains only this:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by fs3rp4 on 2010-05-02
I installed in two Dell 1525. One fresh install and another was upgraded. Both worked perfect.

Best Ubuntu distro ever.

---

### Post by swudee on 2010-05-02
My results have been mixed.
Three upgrades so far.
First from Hardy, I ran into problems with X with the infamous Intel 845 ? I think it is chipset causing it to have a black screen with white lines flashing in and out in the top 3rd of the screen, Now it goes to a file system check and is unable to sort itself out, have left it running for a couple of hours and it gets 70% and starts again.

Second, again from Hardy, Downloaded the packages, then had an issue with Open Office and aborted the install. Un-met dependencies I think.
I uninstalled OO.o and all went well, apart from Google Earth. It opens up fine, but the earth has disappeared, the window is completely black.

Third, from Jaunty, It started ok, but I had a work related call and had to switch to the Windows computer so I could log into one of our Linux servers!!!, yeah that sucks, the html interface is ie only, when I switched back I had no keyboard/mouse, so when it stopped waiting for input for the boot loader, I had to give it a hard reboot, and no, plugging in a usb mouse didn't work either, it wouldn't recognize that either. Of course it didn't boot, I ran up a live cd and tried to install grub, which at least gave me a grub command prompt, but not able to find the hard drive, I am able to boot with the right commands, but it errors when reinstalling grub, and grub still doesn't boot.

Still my 64 bit laptop to go.

---

### Post by bapoumba on 2010-05-02
Had kept a Sony Vaio VGN-C2S 13" with Hardy to test the upgrade LST > LST.

Upgraded with upgrade-manager for the first time ever. Had one issue with flashplugin, solved with these steps from this bug: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841)
I did not look if there was some other solution, as the link was the top one from the error message and worked.
The install error did not bring up any reboot or other problem. I fixed it after the second reboot.

Everything else is fine.

Edit: another acer laptop was upgraded from Karmic to beta without any problem.

All these computers are over 2 years old.

---

### Post by evertmantel on 2010-05-02
I had some errors during the upgrade; these could be corrected after the upgrade by doing an update with the update manager. Then used the janitor to clean up all the junk.

Firefox did not start at all. I solved this by de-installing it and then re-install it again. 
So far, no other issues popped up. I have the feeling it is all just a little more snappy than with 9.10!

A more critical remark: The upgrade took a very long time: almost 3 hours from starting until finishing. 

proudly using Ubuntu 10.04-64-bit now.

---

### Post by stefano94 on 2010-05-02
Heyy,

Made a clean install with netbookremix on a netbook (no ****, i'm seriuz) and it went pretty ok. The only issue is that wifi doesn't work cause of the chip in the networkcard, but that's a matter of drivers, gonna fix it later. And I also made an attempt to install 10.04 on a partition next to a win7 partition, a normal desktop btw. But the thing is, during the installation teh partition manager doesn't see my hdd. I've tried several things, but I can't find the solution. I'm already asking for help on the dutch ubuntu forums, so if anyone recognizes my problem, plz send me a message! Maybe I also will start a topic here, but first I'm going to try an alternate installation.

Cheers

---

### Post by MacDuff on 2010-05-02
Tried 10.04 on two laptops and one desktop.  Two were upgrades to 9.10 and the other was a clean installation.

For the most part the experience was excellent, best yet, BUT there is a major problem with Kontact and that is essential to me.

Akonadi seems to be the culprit here. With all three machines after the installation of Kontact, I received Akonadi error messages when Kontact was first started.  After re-booting, the error messages disappear and Kontact seems to work but I cannot associate the imported address book with the kmail portion of the Kontact.

When trying to create new email, there is no apparent way to pull the email address from the address book.  

On previous versions of Kontact, when entering a few characters of the addressee's name, a list of matching names would appear to allow selection of the correct one.  That does not occur in 10.04 and I cannot find a way to enter an address other than copy/paste. 

Has anyone else encountered this?  
If so, is there a solution?

---

### Post by tommark on 2010-05-02
Upgrade went very well, except now I have to x out a pop-up screen that insists on telling me that I need to log in to a keyring 'default". Nothing seems to be affected by this pop-up, and it finally goes away after 6 or 7 x-outs. Just annoying. How do I get rid of it?
Thank you
As I watched the verbose screen during the upgrade I was made aware of how many things were being updated/graded. I need to say here that I am extremely impressed by whoever the team is that created this upgrade. Each of us millions of users has a computer that is different in several ways from every other computer. The UU team has managed to please nearly all of us - otherwise the servers would be down because of despair.
CONGRATULATIONS!!! from a recent Win to Ubuntu convert.  And Thank You!!!

---

### Post by asw24 on 2010-05-02
I already highlighted the things that went wrong/don't work in a few other posts. BUT :guitar:
overall I am just very happy with Ubuntu. I am still struggling with two programs and a pieze of hardware (lide100 canon scanner) that still reply upon MS software. For the rest: Ubuntu is just as computer OS should be: mulittasking without background proccesses getting the overhand; networking with other PCs. 
Great job! The PC I upgraded is the one used by me (hobby PC; i7-920 processor) My wifes machine I will not change from 9.10 though. Maybe in three months time, She needs a computer for her work.

Thanks for all the work. Next project will be an Android device.....

---

### Post by danbar on 2010-05-02
My first problem is that everything was working fine. I switched off my laptop. When after doing some errands in the city came back and switched on again, firefox did not open. As an emergency I installed chrome of google.  What happened to firefox?

---

### Post by blegs38552 on 2010-05-02
Just upgraded to Ubuntu 10.4. Installed well (not a Wubi install). I previously had 9.04. I hosed all partitions for Ubuntu (my primary is Win 7 - please don't shoot me). Had problems setting Windows to the default O/S, putting it on top of the grub2 menu (I'm still not a big fan of grub2) and changing menu colors. Finally had to resort to editing grub.cfg y running sudo gedit and opening the file (no matter what they say about not editing the file directly). Did a few changes and saved, rebooted and all was well. Next step - use my Acronis backup program on Win 7 to create an image backup for this, just in case... (and we know there will probably e a "just in case"). Hopefully, I will be able to restore this, when "Just in case" happens.

I have an Epson Artisan 810 All-In-One networked device. Was able to print "right out of the box". Tried scanning using Simple Scan. It shows my device but when I try to scan, I get an "unable to communicate with the scanner" message. Tried installing XSANE with the same result. In both cases, the device's control panel was only half displayed and was flashing on and off. I had to power down and power back up to regain functionality. I will be posting this as a separate thread.

One note - I was never able to install the beta for 10.4, so this is a good thing.

We're getting there, but Win 7 is still my primary O/S for mission critical business.

---

### Post by tetrafuran on 2010-05-02
updating UNR on Acer Aspire 1 took about 20 hours or something. I started in noon and it got completed sometime in the middle of the night or during next morning. Who knows. In any case the SSD of my laptop is really slow and the person who designed should have his wage lowerd.

The new interface takes some time getting used to. Pretty much everything has changed - even the x button moved from the right corner. Apparently windows 7 has had some influence, since programs are icons instead of boxes in the panel. I don't like the fact that the bottom bar has disappeared. I could see my 4 virtual desktops in there even if it took some of my precious screen space. Now the top bar is totally cluttered up with... well, pretty much everything.

So far everything seems to work though. Can't really complain. New stuff is generally cool, but sometimes a bit confusing... at first.

---

### Post by jerome1232 on 2010-05-02
Botom bar shouldn't have disapeared.

---

### Post by jelofson on 2010-05-02
Fresh install over 9.10 along side Vista (blah). 
No problems
1) Wired internet works
2) ATI X1300 with compiz out of the box
3) Monitor resolution perfect
4) sound seems fine. Haven't tried much.

Other comments.

1) tried the buttons on left. Couldn't handle it. Switched to New Wave theme and mashed it together with ambience. I found it really hard to deal with the buttons on the left, but I did give it a try. Looked totally messed up and unbalanced too.

2) Ubuntu One music store in Euros and I am in Canada. Would be nice to see local currency. Haven't tried to purchase anything. Neat concept though. The fact that they are synced to each PC is a nice touch. Of course, you are "kind of" locked in with Ubuntu, though.  

3) Resize handles on the left and right of windows is way too small. I can barely grab them. Also inconsistencies as to when a resize handle is present in the bottom right corner or not.

4) I like the new theme in general. I like the icons, the colors, the fonts, branding etc. As I mentioned, I don't like the wacky button position. On the new background image, the bright orangy-pink spot near the top creates a funny optical illusion where the top panel looks bent. This might just be me :)

5) I don't see Ubuntu One in the places menu. Thought it used to be there. I liked it there better than the new me menu thing. 

6) I don't do the whole broadcast thing (twitter, et al) so I dont' use those. However, I would imagine it's a great thing for those who do.

7) I find the software centre appealing. Visually and functionally. Featured apps a nice touch, especially since Gimp was removed from the default install. 

8) I find it crazy fast. Boot is very fast and just general computing is very fast.

8) I have a MS webcam vx-1000 maybe? Video seems to work now, but the mic doesn't. I should have gotten UVC cam...Live and learn.


Save for the buttons (sorry, I can't help harp about them), this is an excellent Distro. Best yet, I think.

---

### Post by jflaker on 2010-05-02
There are a few dialogues that come up during the upgrade..but probably not for everyone though...I wonder if things breaking have to do with people answering some of the questions wrong because they don't understand what they mean.

---

### Post by Benchrest on 2010-05-02
I've been running Ubuntu since 5.04 . It seems each release has been a bit more difficult.
9.10 I could not get to work so I went back to 9.04.  I downloaded 10.04 desktop 32 bit i386, checked the  MD5SUM correct. Burned the CD as usual as recommended. I tried to boot the live CD on my HP dv6000 laptop and got a screen with hieroglyphics across the top. English on the main part of the screen but could not click on anything. Seemed to be multiple screens overlaid. I then tried on my desktop and it went directly to console. Using F6 I was able to try check disk on both machines and it would run a short time and then quit without a message. 
I re-burned the CD and got the same symptoms.
I finally was able to get to preferences/monitor. I found to select an item I had to click on a spot 5 inches to the left of the item I want to select. I changed the resolution and now it was readable. But why no display on my desktop? I am hesitant to move forward. It was strictly luck that I figured out the resolution problem. It was at a very high resolution it seemed, If I recall previous releases had a low resolution default.
Perhaps I should try another download even though MD5SUM was correct.

---

### Post by canerunner on 2010-05-02
I've upgraded two now. One is a Quad core AMD64 desktop, and the other is a Lenovo X60s laptop. Both upgraded with no issues, although the download time for the first was slow due to the server load at the time. 

I installed the x86-64 bit version on the desktop, and the x86 version on the laptop.

Both worked perfectly, and I haven't found anything yet that doesn't work at least as well as it did in 9.10.

Great job on the new LTS release, and thanks for all the hard work!!!!

---

### Post by stegouin on 2010-05-02
Ran the upgrade 2 days ago, from 9.10... a few errors were displayed along the way... something about network applet and GRUB I believe.

Upgrade completed successfully... rebooted... was now missing my slave ext4 hdd and external firewire ntfs hdd... fstab revealed no mount points for those.

I edited my fstab to include them back in, reboot again, back online.

I've also noticed my DVD+RW drive is not mounted either, so I'll have to look into that as well.

Other than that, pretty smooth. I am running a full Ubuntu desktop... no dualboot with Windoze or other...so I guess one less headache.

One great thing... I bought a new Samsung laser printer (CLX-3175)... simply plug and play... Ubuntu picked it up right away, pointed me to the right driver, a couple of clicks and voila... printer online.

Big improvement over my last Canon MP4210... what a pain that was (had to download drivers from Canon Asia, corrupted CUPs along the way etc...)

I was thinking perhaps of burning an installation CD of Lucid Lynx, and doing a full re-install... thinking perhaps it would install more cleanly?

In any case, looking good so far. Good job Ubuntu dev team and Canonical.

FYI... running a 7 year old pc, Pentium 4, 2.4 GHZ, 1GB Ram.. Intel Mobo, ATI 7500 All IN Wonder Radeon TV tuner card etc...

---

### Post by Joherrer on 2010-05-02
Installation run (several hours, overnight) and finished with a fully working opsys.
All my devices work fine.
My only concern is about the three buttons that used to be on the upper right of each window.
They are now at the left side, mirrored with the previous position.
Is that a bug, a joke or a new point of view?
:o
Sorry, I forgot to say... 
I use Ubuntu in my home made desktop, with a MSI motherboard, AMD processor, Nvidia GE Force7300.

---

### Post by linfidel on 2010-05-02
This was the first time I had major problems after installing or upgrading over about 5 versions.  I was unable to solve the problems, and had to reinstall from scratch.

The install stopped responding at the point of asking me what to do about my old menu.lst file.  It would not respond to mouse or keyboard, and then the screen went blank.  I have a theory about why, but I don't know if it's really feasible:  I have 2 computers sharing a monitor/keyboard/mouse, and I quit using the kvm switch due to problems.  I have a USB switcher for the mouse/keyboard via a button, and I switch video via the analog/digital inputs on my monitor.  So, while Ubuntu was installing, I switched over to the other system for a while.  I'm thinking the installer decided I had no keyboard or mouse, so it didn't install drivers, and when I tried to interact, it simply didn't know I was there, and the screensaver kicked in making the screen go blank.  

Anyway, I was forced to reboot, and it wouldn't get very far, no matter what I tried.  I was getting kernel panics, and didn't really know what was needed, and couldn't find any information about the errors.

I installed fresh, got everything working in about a day, then had another slight problem which is now under control, so I'm pretty happy except for having to repopulate MySQL for my test web sites.  But that's OK, as I really need to learn how to do that.

---

### Post by linfidel on 2010-05-02
> **Joherrer said:**
> Installation run (several hours, overnight) and finished with a fully working opsys.
All my devices work fine.
My only concern is about the three buttons that used to be on the upper right of each window.
They are now at the left side, mirrored with the previous position.
Is that a bug, a joke or a new point of view?
:oNo, a google search will show its reasoning, and also the solutions for changing it, if you want.  I changed it, but then put it back after deciding I should bite the bullet and get used to it.

Too bad I also use Windows, but maybe this will keep my brain exercised. :)

You can find good directions here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by AzT3K on 2010-05-02
Dual boot is broken and still not fixed, I had to manually edit my grub.cfg file to get my windows back, obviously it took quite a bit of trouble shooting to come to that conclusion.

but that issue should be well known by now...

Every distribution upgrade I've ever done, since apodting ubuntu at Intrepid, has broken at least one of the computers i work with. My conclusion:

UPDATING UBUNTU IS NOT SAFE AND SHOULD NOT BE ATTEMPTED BY THE FAINT OF HEART....

Seems the grub dual boot issue was a known one that either didn't get sorted or was only partially addressed, I realy think the 6 monthly release cycle is too tight or too much is trying to be done and its with out a doubt an area where ubuntu falls down as a consumer operating system.

I think that quality releases should be the focus rather than quantity. I dont care if it comes a week late, id rather be patient than disappointed.

---

### Post by panachippara on 2010-05-02
Yes the installation worked perfect for me. I upgraded from version 9.10 because sound was not working earlier. After upgrade everything inlcuding sound is working on my Macbook Pro (2.53GHz processor(Intel core i5), 8GB RAM, 500GB HDD, NVDIA GeForce GT330M, 15 inch display).

---

### Post by Gregz on 2010-05-02
Upgrade - worked but had few things to fix, nothing serious though


The upgrade went just fine, I started with the beta a week before release, A few little upgrades since and all seems fine.

I do have to note flash does not work on a few websites, like pogo.com, wife plays bingo there. lol, will not load flash for some reason, every other site works great????

I must say from what I've seen so far GREAT 


:popcorn:

---

### Post by friv_livs on 2010-05-02
Supports all hardware on Gateway M1625 laptop. Even the physical wireless switch is recognized.

I had to reinstall pitivi to stop it complaining. 

This is what koala should have been.

---

### Post by Dafau on 2010-05-02
Hello all,

Yesterday I upgraded from 9.10 to 10.04 and I got an error during installation, after choosing to update the Grub to the new one. It passed this point, Ubuntu works and looks gr8. The problem is although the new Grub recognises my other OSes (Vista, Vista Recovery Utility, Windows XP) the laptop won't boot any of these. Still looking for a way to fix this, the files are there, maybe somebody can point to what I did/went wrong. It seems that those partitions are seen as Windows 7 instead of Vista and XP. :( Headaches!

---

### Post by kubunut on 2010-05-02
Upgraded from 9.10.

The upgrade failed like 3 times couldn't get some package. Had to reboot to continue upgrade. Then couldn't get it to load KDE. Tried to install Nvidia drivers and got some kind of error about gcc and kernel mismatch. Had to reinstall Opera.

Tried using the nv driver didn't work so I tried the Nouveau driver that ended up getting me in to KDE. Then I just settled for using the Hardware Drivers program to install the almost latest nvidia driver. Bit of a pain....

Now I noticed my loading Kubuntu screen looks low res (bad), when I used the nouveau driver it looked really nice....what's the deal there ?

Overall pretty decent upgrade seems much quicker than Karmic.

---

### Post by rickvan67 on 2010-05-02
Day 3 since I installed Lucid on a brand new AMD Athlon quad core.  It is working flawlessly, this version of Ubuntu rocks!  :guitar:

---

### Post by lusid on 2010-05-03
Live CD failed to load.  No video.  It looks like a common failure mode for this release.  I see a lot of people with some variant of "no video after install/upgrade".  9.04 worked, 9.10 mostly worked, 10.4 is DOA.  

Hardware is an HP8440W with a NVidia Quadro FX 380M.

I gave my ubuntu partition space back to windows and put ubuntu in a VM, where it actually runs, but no GL support, so no compiz, so no AWN dock.  Its a shame, 10.4 looks better in 2d than 9.10 looked in 3d.  Better luck in October.

---

### Post by bcastalia on 2010-05-03
Upgrade from Ubuntu 9.10 to 10.04 using Upgrade Manager.

System: Core i7 on Gigabyte EX58-UD5 with dual nVidia GeForce9800 GT graphics cards.

The system was fully functional and very stable w/ 9.10. The system is mostly functional and somewhat unstable with 10.04. The upgrade process itself was uneventful; the results were rather disappointing.

* During the boot sequence the message -

init: ureadahead man process (nnnn) terminated with status 51.

- appears. Curiously, the message in /var/log/boot.log is slightly different -

init: ureadahead-other main process (nnnn) terminated with status 4

- but whatever the consequences of this problem are it is not apparent.

* The nVidia driver, working fine with 9.10, failed to work at all with 10.04. A thankfully prompt reply to my question on launchpad (which directed me to an Ubuntu Forms thread:_ _[http://ubuntuforums.org/showthread.php?t=1467074)]("http://ubuntuforums.org/showthread.php?t=1467074") finally got that worked out just as I was preparing to retreat back to 9.10.

* The Enlightenment (e16) window manager, which I have been using for many years, started up OK, but no menus worked at all. Since this meant that nothing could be done the only way out was a reboot. Restarting with a default session of KUbuntu, and then un-installing and re-installing e16 and its siblings fixed this problem.

* The thunderbird email application was upgraded from 2.x to 3.04. This left many add-ons non-functional, including the important Lightning calendar capability. GUI events in the application produce the inscrutable message -

LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so [libxul.so: cannot open shared object file: No such file or directory]

- though the IcedTeaPlugin.so file is in fact present at the specified pathname. The application appears to be working correctly, however, so either this is a bogus error message or something non-fatal is wrong. There were several other problems with the new version of thunderbird that I was eventually able to overcome. It seems that this application upgrade was rushed out too soon.

* Some, but not all, user configurable settings were lost in the upgrade. This will be a rather annoying hassle to redo. It would be good if user settings were kept separate from application defaults and, where this is not feasible, it would help if the old settings were saved and the changes brought to the attention of the person doing the upgrade (and I don't mean by having to painstakingly wade through log files).

* The Qt installation was upgraded from 4.5 to 4.6. That's fine, but the upgrade damaged some of the underlying machinery: Whenever an application based on the Qt framework runs it complains -

QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/castalia/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address.
IBusInputContext::createInputContext: no connection to ibus-daemon

There is no ~/.config/ibus/bus. Reinstalling ibus-qt4 did not fix the problem.

The Qt assistant application ran the first time, but now when it is run the GUI flashes on the screen and then disappears though the processes is still running (it must be killed).
Reinstalling libqt4-assistant did not fix the problem.

* The /var/run/motd file (/etc/motd is a link to this file) was blown away and not updated. This was corrected by running /etc/init.d/motd_update as root.

More problems continue to crop up as I use the upgraded Ubuntu 10.04 OS. The impression is of a major upgrade that was rushed out too quickly without paying attention to the details (where the devil lives). This is letting the users debug the software; a policy that rapidly undermines the reputation of a product and those who are responsible for it. My previous experience with Ubuntu has been very good, so I am convinced that the folks responsible for Lucid Lynx can do better. I remain hopeful that fixes to the rather messy situation will be forthcoming....

---

### Post by bergfly on 2010-05-03
After a great laptop upgrade, I gave a go on my home desktop. 

Issues, none a show stopper, but for the less experienced user, this requires attention.

Firstly, I use Kubuntu, and have been using Wicd for a couple of versions as KDE 4 decided we didn't need static IP's for the longest time. 
Networking was completely broken when I rebooted. Wicd was half installed, gnome network manager completely missing in action, and the plasma/kde stuff a mess. Took some CLI antics to bring up the eth0 to get something to work so I could apt-get a solution. Breaking networking is almost worst than breaking X!

Couple that with the known Nvidia issues (again.. How many upgrades is this that have not worked for Nvidia) and it was a mess. The Nvidia issue was really sweet in that once I locked up the system playing, Ctrl-Alt-F2 put me to an out of range indication on my monitor... 


All working now, but for an install that was less tweaked than my laptop, I am a little surprised.

One good thing, they finally got rid of that hard drive checking tool that spent six months telling me that HD failure was imminent on a perfectly good Seagate drive. Thanks for that folks, I'm giving gnome another go now.

---

### Post by slooksterpsv on 2010-05-03
Not sure if I posted this, and I apologize if I already did, but I cannot even start the installation on my big computer - quad core amd phenom 9600, gigabyte mobo, 2GB RAM, ATI Radeon 4850, - Ubuntu 10.04 x64 Lucid Lynx.

I'm not sure why, the terminal is very very small like it's running the terminal in 1280x1024 - for console mode. I'll try the alternative here soon, but right now I'm doing dual-vista installs, one for just Microsoft and Microsoft Development products (even running MSE on it) the other for Gaming, and that - I barely use my big computer, so I'm not at a loss with it, but I have games I've only started - Red Faction Guerilla, Mass Effect 2, GTA 4 - all of which I start playing then don't - oh and Assassins Creed.

Should try them or some of them  under Linux see how they run.

---

### Post by paterijk on 2010-05-03
Problem with the boot splash screen (just a black screen with random color spots until login screen) ... see my description here: 

[http://ubuntuforums.org/showthread.php?p=9221087&posted=1#post9221087]("http://ubuntuforums.org/showthread.php?p=9221087&posted=1#post9221087")

---

### Post by razor62 on 2010-05-03
Did a clean install from Karmic to Lucid.  Did not have any issues with the sony viao fj270.  Just realized all the work I did on Karmic went down the tubes.  Will seriously think about keeping up with the Jones in the future. Albeit, I dig lucid very much and will stay with it from here on out. I did use the Perfectbuntu 5 scrip from Robbie Ferguson [http://perfectbuntu.category5.tv/](http://perfectbuntu.category5.tv/)  @ category5.com to load all the media codects and move the min max button back.  Worked great saved alot of time. :D

---

### Post by ollesbrorsa on 2010-05-03
Fresh install to second hard drive. Ended up with grub rescue prompt as many apparently have. Have three hard drives, no windows install. Decided to move install to first hard drive. No dice.

Have tried Super grub disk, reinstall of grub2 via grub2 wiki and a couple of links that have made the rounds when similar problems have been described here at ubuntuforums. Still got dumped at the grub rescue prompt... Curiously grub2 reports sdb as hd0!?

Long story short I disconnected second and third hard drive and did a fresh install with only one disk connected. Problem solved. Other disks are now connected and the system is working fine. 

min, max, close buttons are going back to the right as soon as I get over the lucid aversion lingering from the install fiasco.

My eeepc 1000he will not see 10.04 until [bug #496093]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093") is fixed.

Hey, at least boot times are shorter...
/ollesbrorsa

---

### Post by MightyMouse on 2010-05-03
Have done an upgrade yesterday on my Desktop via update-manager. No serious problems during the update but then the never ending story: wireless, wirelss, wireless..................................

If there is one thing that makes me sometimes think if it is worth to try a new version at all it's that I know for sure that I will have to spent hours trying to fix the wireless. And unfortunately somehow every upgrade makes sure that whatever tweak worked last time will not work any more! I have about 4 or 5 different adapters in various computers/Laptops and every time it's like playing roulette to see which ones might be recognized and work out of the box. Over the years this has definitely improved, but I might find this just annoying, many newbie finds this an obstacle that makes them go back to Window$ (Not that stuff works there 'all' the time and everything is 'flawless' by the way).

I don't want to complain since everyone should be appreciative of all the work that goes into Ubuntu and we all get this for free, but at the end of the day I think people get very reluctant to try a new release once they have a stable system.

And one other problem is that the Forums are by now so overloaded with requests that the majority never even gets an answer. If you want to keep you message on the first page you pretty much have to 'bump' your own message every hour and that can't be the way to go. So even if you would like to spent time on solving your problems it's getting dam difficult to even find the right thread.

But no hard feelings, have been a Ubuntu fan for a long time and even so I might have been tempted to check out other distros I can say that there were non that came with no problems whatsoever!

So at the end of the day thanks for the effort and let's work on the problems together, after all this is Linux for the people.

MightyMouse

---

### Post by MadMax2 on 2010-05-03
Worked on Desktop but hung on laptop.
I tried to install from the CD. It did the dots and then threw in the towel.
Memory 480.7 MB
Intel Pentium M Processor 1500Mhz.
9.04.

 description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation

Am upgrading but wanted a clean install.

Solved:
> Solution 2

Yes, I think you may be right about it being a graphics card problem. I think you may have the same problem that I did on my beat-up old Toshiba Satellite A10.

So, here is what should work:

At the very first screen, the one with just the rectangle (it&#8217;s meant to be a keyboard) and a human figure, press any key - spacebar will do.

Then choose your language.

Then make sure you have &#8220;Try Ubuntu without any changes&#8221; selected, and then press F6

Add this to the end of the command line:

    i915.modeset=0 xforcevesa

Then press enter and it should boot successfully.
[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)


---

### Post by pharma on 2010-05-03
Did an upgrade on HP laptop - dv 6000 series.  Triple boot Karmic, Jaunty, Vista (Just in case) - now triple booting Karmic, Lucid and Vista.

Worked flawlessly - almost - volume applet disappeared but reinstated it through startup applications.

2 installs to dual boot desktops.

No 1 - Jaunty, XP home - now triple booting Jaunty, Lucid and XP home.  Wouldn't install Grub2 (errors at restart) but fortunately left Grub1.  Manually added Lucid to Grub1 menu.lst - check out Grub2, cfg for Lucid installation and transfer boot information.

Will have to manually change Grub1 on kernel upgrades - not brave enough to try and install Grub2, yet.

No 2 - Karmic, XP professional - no real problems - just need to "sudo update-grub".  Now triple booting Karmic, Lucid and XP professional

Impressed with Lucid, fast and most of the software I will ever need

Well done to the Ubuntu team and community

---

### Post by jonerich on 2010-05-03
> **devnuller said:**
> Congratulations to all the Ubuntu staff for an excellent upgrade package. Both my native x86 and virtual machine 9.10 to 10.04 upgrades performed flawlessly. Those were by far the easiest and cleanest Linux upgrades I have ever had the pleasure to carry out. Keep up the good work!


Regards

Dev Nuller (Unix user: 20 years, Linux user: 15years)


I dont know what your talking about!!!!! i should have left well enough alone and never attemped to upgrade( so i blame myself )from 9.10 triple boot osx ubuntu and windoz thats was working flawlessly im glad i didnt touch my netbook it bricked my whole computer tried fresh install also Had no choice as recovery didnt work either and no luck there ether.Lucid is the word all right staring at a black screen while the lynx runs off with all your data customizations and configs.going back to 9.10


amd 2,2
2 gig ram
1tb
nvidia 220 1gb ddr3

---

### Post by uncleV on 2010-05-03
Upgraded, worked flawlessly.


At least till now.
And I now what[COLOR=Black] [jonerich]("http://ubuntuforums.org/member.php?u=948730")[/COLOR] is talking about

---

### Post by omalley82 on 2010-05-03
works very well on dell studio 1737. :D

---

### Post by anupcshan on 2010-05-03
Did a clean install on my new Dell Studio 15 laptop. Works really well :D
Kudos to the Ubuntu team!

---

### Post by TangyFM on 2010-05-03
This was on a Toshiba Satellite Pro SP4600, 750MHz cpu, 192MB RAM.

Tried 2 different ISO downloads, and the whole thing hung for over an hour, checksums were fine. Then reading this forum found I should have used the alternative CD, which I did.

Another hour later and a black screen full of script, and it hangs again.

Back to 9.10 !

---

### Post by Dangerous Curves on 2010-05-03
Upgraded both my laptop & desktop from 9.10 using update manager.  I do have 1 problem.  If I reboot, the visual effects resets to none.  I have to reenable it to get the borders.  This is happening on both systems.  Any way to fix or do I just deal with it?

---

### Post by TunaCanTommy on 2010-05-03
I did an upgrade from Karmic to Lucid (Alpha 2). Then, after Lucid final release I decided to do a clean install.

My system is a desktop - AMD Athlon CPU, 2GB Ram, and an Nvidia 6200 (NV4A) graphics card.

I first tried an install from a CD after I downloaded and burned the ISO. I booted to the "live-CD" and tried to partition my hard-drive. 
The install kept "locking-up" when the GParted started to do the partitioning.

Built a USB thumb-drive and tried again . .  no luck kept locking-up.

Put in a "SystemRescue CD" and successfully partioned the hard disk.

Booted off the USB drive and started the install . . . again a "lock-up" when the partitioner started. Tried several times. In all I probably tried to do a clean install 8 or 9 times, all failed when the partitioning started.  I was ready to go out an buy a new hard drive.

Then I thought . .  "Why is the system locking-up ? ?"  Could it be because I was "over-clocking" the system ? ?

I went to the BIOS and set everything to "Optimal Settings" . . . restarted the install and BOOM . . success!

Went very smoothly, no problems (after I turned off all the "over-clocking" I'd done).  So, if you're having problems with your install, check to see if you've set over-clocking parameters a little too high . . . that might be the problem.

BTW  - after some research here's how I partitioned (ext4) my 120GB Seagate: /boot=146MB, /=5GB, SWAP=1.8GB, /home=all remaining.

I'm now running a clean install of 10.04, I dual-boot to Window XP Home Edition running on a the second disk (80GB) with a second data partition (ext3) for backing up Linux stuff.

---

### Post by soccerush10 on 2010-05-03
I have a major issue:

Fresh install of Lucid Lynx ( Ubuntu 10.04 ) 64-bit gives me a weird screen w/ an odd vertical pattern on it.  The OS booted perfectly right after installation, but after a reboot all I get is that odd vertical pattern.

I reinstalled using another install CD, I even performed a check on the install CD and on my HDD to make sure that both were Error-free, but I got the same result.

Can anyone help?!!?:confused::confused::confused:

---

### Post by srivo on 2010-05-03
Upgrade last night,

Work fine I have a few minor thing to fix but nothing serious. AWN 0.4 didn't restart, I need to reconfigure it! Probably not relate to ubuntu. The same thing has happen on my Arch Linux laptop. I also have to reinstall the medibuntu and freenx repository. Not so bad at all!

In the upgrade process the system ask me a couple of question I wasn't very sure what to answer. But it restarted perfectly.

I personnaly like the new look!

---

### Post by CryptSphinx on 2010-05-03
Upgrade , ran smoothly , 

amarok is crashing after starting and thunderbird is segfaulting.

have only spent about 15mins investigating problem (headed to work)
but probably easy fixes.

I think in both cases its some addon / custom script thats causing the problem.

---

### Post by Windy Peaks on 2010-05-03
First and foremost, thank You very much to those who made 10.04 happen.

I have a funny upgrade issue here.
I first upgraded My 64bit desktop and it went flawlessly, took close to two and half hours but it did upgrade.

Now this is where I need the Ladies and Gentlemen help, on My toshiba A200 32bit laptop when I get to the upgrade screen and select Upgrade, I enter my password and watch the process get to the third party software must be disabled screen.
I select close and and the selecting some channel options start running then bang it all stops and and says that there is a error during update and that it 
"failed to fetch http://archive.canonical.con/ubuntu/dists/lucid/partner/binary-i386/Packages.gz"

Also it "could not fetch http://archive.canonical.com/ubuntu/dists/partner/source/Source.gz"

then it tells me that I might have a internet connection problem, which I am sure I don't. I even disabled my ufw firewall in the hopes that it was the problem.
Any thoughts would be greatly appreciated as I don't want to reinstall my Ubuntu and lose everything in the process.
Thanks 
Windy

---

### Post by P4man on 2010-05-03
those sources are incorrect. Did you type them in manually? there is no

[http://archive.canonical.co](http://archive.canonical.co)[COLOR="DarkRed"]**n**[/COLOR]/

that should be com.
Im not sure if you just typed that address wrong in this post or if its setup wrong on your machine though. Let us know

btw, the second one is also incorrect. There is no distribution in there (like lucid). Can you post the contents of /etc/apt/sources.list ?

---

### Post by jstalnak on 2010-05-03
Sadly, for the second time a Ubuntu upgrade has caused an issue. The last time, when I  upgraded to 9.04, I lot the USB subsystem -- keyboard and mouse stopped responded in the middle of the upgrade and knowing no other I used the power button to restart the computer. This was very bad in the middle of an upgrade. It took two days to fix.

This time the exactly same thing happened. As the upgrade was proceeding mouse and keyboard worked, but at some point they stopped working. There was no power to the keyboard and though the laser of the mouse was powered, the cursor itself was inoperative. But happily a coworker suggested that I attempt to ssh into the box which I *could* do from another computer. Not only that, I could run x11vnc and from the remote computer I DID have both keyboard and mouse function. I was able to complete the install and restart successfully.

Unfortunately, though I did have keyboard function at the beginning of the boot process (I had to select a display) once I get to the login screen I no longer have keyboard/mouse function. So this was not a painless upgrade and it will continue to be painful as I now have to troubleshoot, and hopefully fix, inoperative keyboard/mouse.

---

### Post by prshah on 2010-05-03
> **soccerush10 said:**
> after a reboot all I get is that odd vertical pattern.
Can anyone help?

Please start a fresh thread to catch more eyeballs; can you post a (camera) screenshot? Can you also include your system specs / model etc?

---

### Post by dangmc on 2010-05-03
I'd like to say that my experience has been kind of mixed. Installation was painless and I'm certainly impressed by the speed. I also upgraded my hardware prior to installation so uncertain as to what extent speed boost is due to x64. My biggest concern is lack of microphone capability. I've tried several suggested fixes after researching this issue with no luck. Audio sound quality is excellent with severely limited adjustment possible from both alsa and pulseaudio controls. My new Asus mobo (P7P55D-E seems to include a new built in soundcard listed as VIA vt 1828s in product data. This is shown in my system as a VIA ID 4441. Via doesn't provide any support for this card-they state they provided a limited set of drivers to Asus for this series who then adds their own input. (only for windoze-no linux support) This is a major issue for me since rebooting to windows just to use the microphone is a real pain in the a$$! Any suggestions will be appreciated.

I finally found this: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/574504?comments=all](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/574504?comments=all)

I now have a working microphone. Three days ago I did a fresh reinstallation due to many small irritations. Now I only have a few minor bugs which is to be expected with any new dist.

---

### Post by james.whanger on 2010-05-03
Only one problem, but have not yet been able to resolve it:

I installed Ubuntu 10.04 from a Live USB onto an HP Mini 1030nr. The bcmwl wireless driver is not installing. 

I've tried a number of solutions that worked with 9.10, such as trying to install using the Deb package installer to grab packages and drivers from the Live USB drive. 

However, I ran into a problem with two dependencies for bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb: both g++-4.4_4.4.3-4ubuntu5_i386.deb AND libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb list each other as dependencies. Thus, it won't install either. 

After setting a CD repository, both the Deb package installer and Synaptic package installer tries to grab the dependencies from a Live CD, but it does not automatically recognize the Live USB as the Live CD image. 

I need a way to set the Live USB as the Live CD repository for either the Deb installer or the Synaptic installer.

---

### Post by rg_stephens on 2010-05-03
Upgrade from 9.10 didn't work. I had no keyboard, and other problems. Fresh install worked flawlessly (HP tc4200).

I convinced my wife to try dual booting XP and Ubuntu (HP Pavilion zt3000). Ubuntu runs great, but the grub does not give an option to boot XP :confused:  When I did the install, I selected "Import Accounts" not knowing that it would fill up the partition and make Ubuntu unbootable. It's fixed now.

---

### Post by Audiosears on 2010-05-03
Folks,

We've been running the x86 server edition since 6.04 Dapper, and have upgraded through every disto since on the same box.  Would eventually like to do a clean install on a new server, but this machine has served pretty well for 4 years now.

Most previous distro upgrades broke something, notably Samba and Xorg most frequently, though upgrade from 9.10 to 10.04 had no issues.

Also, since Samba and Apache have updated in those past few years, as well as how fstab and menu.lst work, those config files suffered a bit and had to be rewritten as the combining feature didn't end up working well for us.  Glad to see that was no issue here - only my apache config needed to be kept as is.

Only thing I would concentrate on improving would be the way the upgrade process works - the updater doesn't allow you to download all the upgraded files without actually beginning the process - for those of us with standalone production servers, it would help save time if we could d/l all the files near the end of the workday e/o yet committing to the upgrade process.  This would help save some time in keeping the server's services going normally right up until the upgrade process is started.  Would also help in case an issue came up during installation, and update files could simply still be there for next try.

Overall, update experience always improves a bit with every distro - fantastic job! :D

---

### Post by oldguysrule on 2010-05-03
With much trepidation I did a clean install on my 4 year old system running 9.10. I had just installed a new Nvidia G210 graphics card as I have had trouble booting live CD's with the on board graphics since 8.10.
To maka a long story short - everything went great. No issues so far and 10.4LTS with my new graphics card (low end as it mat be) is blazingly fast.
Thanks to all involved for another great release.

---

### Post by Georgia boy on 2010-05-03
Did a bit-torrent download. Created a Live CD. Remembered to do the "Try without" first. Checked it out, did a print job to make sure printer worked with Lucid. Then did a complete eraser/install. When it got done installing I removed CD and tried to do the restart. It just sat there doing nothing. Had to do a force shut down. While doing that got a whole screen of errors, didn't have time to read them. I then turned the computer back on keeping fingers crossed. Got to log in screen and it worked good. Did have some minor issues setting up ThunderBird and Evolution but finally got them to work. Had to install SMplayer and VLC because Movieplayer wants to do a search for plugins. Will do that this weekend. So far other things are working real good. Guess I'll find out later if anything else acts up. 

There are a couple of things I can't figure yet. One is with TB automatically downloading mail into the system instead of letting you go and get it. 

Other is with FireFox not showing the clear history like with Hardy on closing FireFox.

Other than that, I'm happy so far. Windows is now gone for good.:D

Tom

---

### Post by linfidel on 2010-05-03
I tried upgrading an old Dell Inspiron 8500 laptop with NVidia 4200 card.  Pretty much a total disaster.  Video very bad, and it crashes a lot.  Live CD had similar video problems.

Also, there was a Windows XP partition, with a GRUB entry, and the upgrade left that out.  I was able to add it in easily, though.  Fortunately, I still had the old grub, so I knew how.

Karmic ran perfectly on this machine.

---

### Post by cor2y on 2010-05-03
FIrst time in a long while that a clean install of ubuntu did not work flawlessly for me.
There were a few minor problems that came up, one was with grub2 installing itself automatically on /dev/sda instead of /dev/sdc which is the boot drive instead of /dev/sda, had to fix that with a reinstall since installing grub2 to /dev/sdc via the live cd didnt work.
Another was with audio output for some reason it was set to 'None' and i had to manually fix that.
Thats the two problems i ran into on ONE machine.
On my offline secondary machine i couldnt get 10.04 to install at all, complaints range from the disc/burnt cd is no good to the harddrive does not exist it may be hardware failure of some sort since when i check the disc for errors its says its good.

---

### Post by MadScotty on 2010-05-03
I'm having some serious issues that are really starting to frustrate me...apparently the issue is somewhere between my hard drive and GRUB.  (9.10 worked fine)

If anybody's willing to give me a hand, I'd much appreciate it:

[http://ubuntuforums.org/showthread.php?t=1470861]("http://ubuntuforums.org/showthread.php?t=1470861")

---

### Post by Zenith88 on 2010-05-03
I was expecting to get the same kernel as in the release notes - 2-6-32, but am still on 31. Manually installed 2-6-32 and no X anymore.

Also had to manually add desktop menu and all applets.

But what was most frustrating, was that after reading a message that after clicking the button the upgrade will take many hours, clicking Upgrade and going to bed, I came in the morning just to see that it had a question dialogue open for replacing a config file... Ended up sitting for hours in front of the computer, clicking the 'replace' buttons. The developers of the upgrade package should have thought better.

---

### Post by johnshore on 2010-05-03
*Upgrade - worked but had few things to fix, nothing serious though*.

Using Dell Inspiron 350, dual booting with Windows Vista.

Upgraded to Lucid Lynx last night.

- Came up with an error message saying installation failed!

- However, boots to Lucid which seems to be working ok, EXCEPT

- halts on boot with error message:
"An error occured while mounting /proc/bus/usb
Press S to skip mounting or M for manual recovery."

Pressing S completes boot and all seems to work ok, including usb devices (this includes usb on Sun Virtual Box).  Unless there's an easy fix I'll put up with the nag screen and hope it will go away with a later update.

- I notice the usual Galeon-common failure notice is still there.  I had hoped it would go away with this upgrade.

---

### Post by gatorbrit on 2010-05-03
Upgraded from 9.10 on both my toshiba satellite laptop and my dell optiplex desktop.   Pretty much flawless in both cases.

---

### Post by union two levers on 2010-05-03
Well much better experience than with karmic on my compaq evo n1015v laptop, karmic installed from cd but i just got a blank screen with a blinking cursor and of course there was the no sound and other issues after an upgrade to karmic so i reverted back to trusty old jaunty.
so far happy with lucid except for not being able to install my wifes favourite bejeweled from cd ( jeweled is not in the same league), i have tried other .exe type cds and can't install any of them, can't get permissions to accept them...this is very annoying.Apart from that everything seems ok so far.
Also tried xubuntu on a desktop which was another story altogether...tried two cds both of which would boot on my laptop but on the desktop the installation would just die at the final stage of the install, setup on the desktop seemed very slow..so i tried to upgrade and 12 hours, yes 12 hours later it finally upgraded but so far it seems ok apart from the gnome panel which started misbehaving and losing things but i have sort of fixed it but can't work out how to add firefox to it yet.oh the desktop has a 733mhz celeron processor and 256 mb of memory

---

### Post by kkady32 on 2010-05-03
after upgrade or fresh install,lucid will not boot
amd64 with nvidia ge 9500 gt

---

### Post by arborhil on 2010-05-03
My upgrade from 9.1 to 10.4 on an Acer netbook (I'm not using the netbook version, but the full version) went smoothly.  I goofed in the beginning, by not getting my old 9.1 system completely up to date before I started, so I stopped the upgrade, restored my disk image, then completely updated 9.1 before I started the upgrade.  The only hitch I encountered was something about the network applet.  It said I couldn't go any further.  I hit "OK" and then the upgrade continued.  After rebooting the network applet was back again.  I had to re-install my Firefox applet too for some reason.  But that was all!  I'm really glad the upgrade worked so well.  I'm going to keep 10.4 and not upgrade any more.

I do have one question though.  After the upgrade, I am using 700MB more of disk space than before the upgrade.  I wonder if that's normal? :confused:

---

### Post by mhbell on 2010-05-03
None of the beta's worked and neither did the release on a compaq presario desktop computer with AMD 64 cpu 2 gigabyte ram and 360 GB HD grafics is a Nvidia 6150 LE built in Monitor is a Visio HDtv 26 inch. I keep getting a blank screen or a no signal once in awhile I can get the first screen and when I tell it to run with out making changes to my system it starts and then the screen shuts down with no signal and then starts up again then it goes to sleep and I get a blank screen. I know that it has finished booting up because I get the boot sound when it is supposed to show the desktop but all I get is a blank screen. It is a graphics problem Monitor or graphics card. I don't know which. 9:10 is working flawlessly for me, but I want a LTR Don't know what to do have tried all of the help codes noapic, ect.
MH:
confused:

---

### Post by kkady32 on 2010-05-03
> **mhbell said:**
> None of the beta's worked and neither did the release on a compaq presario desktop computer with AMD 64 cpu 2 gigabyte ram and 360 GB HD grafics is a Nvidia 6150 LE built in Monitor is a Visio HDtv 26 inch. I keep getting a blank screen or a no signal once in awhile I can get the first screen and when I tell it to run with out making changes to my system it starts and then the screen shuts down with no signal and then starts up again then it goes to sleep and I get a blank screen. I know that it has finished booting up because I get the boot sound when it is supposed to show the desktop but all I get is a blank screen. It is a graphics problem Monitor or graphics card. I don't know which. 9:10 is working flawlessly for me, but I want a LTR Don't know what to do have tried all of the help codes noapic, ect.
MH:
confused:
hi,try this,maybe work:[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

1. Boot from the Ubuntu 9.10 CD
2. Mount the internal HD and look for /etc/X11/xorg.conf - its missing!
3. Copy a new “known good” xorg.conf file to the HD (I had to use sudo cp … otherwise I got permission problems)
4. System boots fine.

---

### Post by ttanev on 2010-05-03
I have a major  issue /[link]("http://ubuntuforums.org/showthread.php?t=1466758#5")/ with my girlfriend's notebook - Asus m51tr /x56tr/, after  upgrade brightness controls makes the core0 to stay at constant 100%  load and the computer becomes non-responsive at all. With the liveCD  option works like charm, but the upgrade isn't. Will have to reinstall a  clean Lucid system, too bad for all the configurations and applications  /hamachi, games, etc. /

---

### Post by byline on 2010-05-03
> **johnshore said:**
> 

- However, boots to Lucid which seems to be working ok, EXCEPT

- halts on boot with error message:
"An error occured while mounting /proc/bus/usb
Press S to skip mounting or M for manual recovery."
We get a similar error message on booting, except that it has to do with our swap partition not being mounted automatically. We hit "S" and boot-up continues to the login, whereupon everything in our system seems to be working fine. We then manually mount the swap partition by opening a terminal and entering: sudo swapon -a /dev/sda1

Not perfect, but not a major problem either.

---

### Post by RevNomad on 2010-05-03
Although, to be honest, there may be only one problem. Xubuntu cannot find a monitor so I got nothing.

This was a net upgrade of Xubuntu. Currently my laptop is useful only as a paperweight. I'm downloading Xubuntu but would appreciate any advice on getting my display back without a complete reinstall.

---

### Post by reiki on 2010-05-03
Honestly, I expected to have trouble installing Lucid, however that expectation proved to be false.

I don't do upgrades any more. I just install clean. I copy my /home contents to an eSATA drive, wipe out my previous partitions, and reinstall from scratch
Onto my Dell Zino HD I installed the amd64. My machine uses an ATI HD4330 in an MXM slot (like a laptop) and it seems to be working fine. Using the stock radeon driver and not the proprietary fglrx driver. Desktops effects working. 

First thing I installed was Ubuntu Restricted Extras. Went to Adobe's site to test Flash. It works. Tested on YouTube to make sure sound was there in Flash.... yup. All set. Started Firefox and then shut it down. Renamed .mozilla to original.mozilla and then copied over the .mozilla from my saved /home. Done deal. All my bookmarks and cookies and everything are there. 

I did NOT like the new Thunderbird. So I set up Evolution and I really like it. The ONLY thing that doesn't work on my machine is the rear sound jack. The front one works fine, but the rear one is just dead. It has something to do with the Conexant (Hermosa) sound card. I wasn't able to get it working in Karmic either. 

Logitech Wireless Keyboard and Mouse... works out of the box.

Acer 22" monitor. Detected properly and running at optimum resolution out of the box.

I can switch video over to my HDMI output and that carries video and sound out to my 42" plasma. (Awesome but gotta only do it when the wife ain't there or she can't watch Desperate housewives and stuff).

the ZinoHD is about 8" square and 3-and-a-half inches tall. As nearly silent as I think is possible. Runs a bit on the warm side, but so do a lot of small form factor boxes. Still within parameters of the chips so it's all good.

So maybe I'm blessed... and maybe I just jinxed myself by saying that and something will blow up tonight when I get home. But right now... I'm pretty pleased with Lucid.

---

### Post by Ryazanov on 2010-05-03
First upgraded over 9.10 upgraded from 9.04... Got problem with video driver which gradually degraded. Ended up with low graphics mode and unable to uninstall proprietary drivers. 
Got fed up :) Copied all data to external HDD. Proceeded with clean install of 10.04 x86_64. All went well except broadcom WiFi adapter did not work at all. Had to connect via ethernet to install proprietary driver. Finally quality of graphics adapter was so high, that I did not need proprietary one this time. Spent all day installing software and moving data. Bravo! This release is so much better!! I even can watch my movies with best ever quality in Ubuntu! Another step off Windows! One little thing is absence of Thunderbird Lightning extension for 64 at the moment. Found previous version compiled by one user. Happy so far! Thanks a lot to developers team!

Hardware HP 6735s laptop
AMD Turion x2 64
video Ati Radeon Mobility HD3200
wireless Broadcom adapter
dual boot with Windows7 RC 64

---

### Post by Wolf-Ekkehard on 2010-05-03
Kubuntu update ran flawlessly - everything seemed to work out-of-the-box just fine - Lucid looked like a very worthy LTS candidate.  Then I wanted to start doing my work again.  Tried to open KDevelop - gone!!  WTF - my main tool for developing software gone?  And no mentioning of that in the release notes so I could have been warned? 

Of course, after looking around, I found some postings that mention this grave omission during beta which also gave launchpad links to deb packages that were supposed to install the kdevelop and kdevelop-data packages - none of them even installed on my machine!

kdevplatform1-libs install fine, but why on earth is the old KDevelop not included in 10.04 if the new one isn't ready (if that's the reason)?

I can understand software having bugs - every software of non-trivial size has them.  But knowingly omitting an essential tool for SW development in a major LTS release and not even mentioning it in the release notes is beyond of what I can possibly understand - unless of course I am the only one developing software under Kubuntu.

Not a happy camper at all

---

### Post by cspence on 2010-05-03
On my home machine the upgrade went just fine. On my work machine, there are issues with nis, and autofs that I haven't been able to resolve, yet. I haven't yet asked for help, either.

(I see a big gap between "worked but had few things to fix, nothing serious though" and "got many problems that i've not been able to solve". Maybe I'm too picky.)

---

### Post by Halah on 2010-05-03
> **frodon said:**
> You might have installed GRUB on the wrong drive, nothing dramatic don't worry.

I would advice you to just re-install grub, you will find needed information there:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Are%20you%20using%20Grub%20or%20Grub%202?](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Are%20you%20using%20Grub%20or%20Grub%202?)
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
This is exactly what happened to my desktop and this fix worked perfectly, thank you.  My laptop upgrade went off without a hitch, which is strangely pleasing as that's the one that usually gives me fits.

---

### Post by umart on 2010-05-03
first,i installed carmic which worked OKon my amd64 athlon system.seen the screenshots of lucid and tried to upgrade.first it could not upgrade,gave me error of an non canonical software.backed up my documents,performed full clean install of carmic with format,because i didn't have blank CD at the moment.could't not boot,gave me the "gave up waiting for device.." error. 

got to drugstore in 2 o'clok after midnight,got an blank CD,downloaded the .iso of lucid and burned it,performed the full clean install with format and same thing happened.after some time it came to me to type "return". it worked,but could not find the drivers for nvidia card.gave up,installed carmic again.this is the problems with ubuntu,wich would be OK if the ubuntu didn't mess up my win xp sp3.

i'm an audio producer,and i've got into ubuntu to free win from regular browsing and emailing.i've got the dual-boot of an win xp sp3 and ubuntu.carmic worked fine.win was on one 80 gb wdc drive and ubuntu is on maxtor 80 gb drive.tried to install clean of an dualboot,because i prefer the BIOS boot menu (i simply press f8 and choose which drive to boot).when i performed the clean instal of lucid i've disconnected the wdc drive which have win on it.i mess up with lucid,and when i gave up i've connected the wdc drive,and tried to boot the win.it could't boot,it said "error:the drive blah-blah-blah could not be found" new column grub rescue/.i've had about 7000 dollars worth of an software on win.i try to salvage win installation with my win cd and recovery console,but no sucsess 'till now.i'll continue to try to salvage it,i've been about 2-3 h working on it 'till now.thinking to press charges,but i live in serbia,so i doubt it will bring anything good to me.

sorry for my bad english.

---

### Post by jd4x4 on 2010-05-03
Who wrote the poll questions?? I'm somewhere between
  - worked but had few things to fix, nothing serious though
 and
  - got many problems that i've not been able to solve

Upgrade from 8.04 to 10.04 and no sound card was detected. I managed to fix it by manually installing it, but not an easy task for a newb.

---

### Post by Jonners59 on 2010-05-03
Figures speak volumes.  I only voted once but have a couple of machines I am upgrading...  Neither worked, though I am writing to you via one with 10.4:

It seems no one is covering off the issues people are having, which seem to be quite related around Grub install and config, as well as graphics card.  I found on one of my machines the same problem that many have found and on a recovery I found in the log graphics resolution issues, so booted in low graphics and it booted up, though screen was un-usable (don't know why the default has to be so off the mark).  Following that the reboot worked fine.

My main issue now is that I have a machine that shows my OS options in Grub, but if I select Vista it will not start, it just returns to the menu selection again.  I would also like to be able to change the order of the options.

Any help?  I have raised threads but non of the experts seem to be responding to any of the crys for help!

---

### Post by keithwill on 2010-05-03
Mine was total nightmare.  Thought upgrade ran ok, but then realised grub bootloader not correct and lost access to both ubunutu and windows.  Reinstalling Ubuntu did not resolve it.

To make matters worse, it then prevented me from installing further or reinmstalling 9.10.  i have had to reinstall windows, reinstall ubuntu, restore backups.

---

### Post by M0LIT on 2010-05-03
Well I bit the bullet and installed a clean version of 10.0.4 32Bit onto my Gateway ML3108B laptop. All has gone well except for tty1 which appears to have a display issue, the screen constantly appears to flicker/jump. I have never had this problem on 9.04 or 9.10. Anyone else have this problem or a solution?

---

### Post by Ethangar on 2010-05-03
That was odd. I did a proper restart to make sure that XP was running again. While I was there I looked up a couple settings and went to transfer them back to ubuntu. Restart and let it boot up linux. I was confronted with the ubuntu screen saying that it was checking all my disks for errors and that it could take a while. It finished and booted fine but I thought it was odd.

---

### Post by quixote on 2010-05-03
Today was the big day when I upgraded my real, working, production 64-bit computer with nvidia graphics.  The critical need detector did NOT go off. :D  The upgrade worked flawlessly.  Flash, sound, java, and a hundred other bits and pieces all worked with no backchat.  Great job!

Now for the niggles:  I'm with johann-p (comment #323) and about a thousand other comments I've seen:  it was super-dumb to change the position of the window buttons for no reason that has ever been explained to us users.  Dumb.  D. U. M. B.  That is not treating your users with respect.  This is linux.  No matter how much you (i.e. some mythical person controlling Ubuntu) may want to look like Apple, for God's sake don't even dream of *being* like Apple.

Just to reiterate the fix that others have mentioned already: ubuntu-tweaks (installable with synaptic) is said to have a one-click way of doing it.  Or open a terminal, type "gconf-editor" (that program is also installable with synaptic).  Under "apps", then "metacity" then "general", right-click on "button layout".  Choose "Edit" and change to ```
:minimize,maximize,close
``` to revert to old position at top right.  The position of the colon is the key.

Niggles #2 and #3.  Give me separate system tray icons for battery, volume, and so on.  Do not "disappear" the volume icon!  (What ARE you folks smoking?)  Do not group it with some mail notification I don't want or need that takes up way too much space.  

(For those equally irked: you get battery and volume back by adding "Indicator Applet" to the panel.)

Irritating as those pimples are on this outstanding upgrade, the rest of it is absolutely A++.

---

### Post by P4man on 2010-05-03
> **Ethangar said:**
> That was odd. I did a proper restart to make sure that XP was running again. While I was there I looked up a couple settings and went to transfer them back to ubuntu. Restart and let it boot up linux. I was confronted with the ubuntu screen saying that it was checking all my disks for errors and that it could take a while. It finished and booted fine but I thought it was odd.

Even if you never improperly restart, ubuntu will check your filesystems every x mounts. x being 30 by default I think (its configurable). The counter for that is in the filesystem itselve, so even if you only just upgraded it might just have reached that number.

---

### Post by P4man on 2010-05-03
> **quixote said:**
> 
Now for the niggles:  I'm with johann-p (comment #323) and about a thousand other comments I've seen:  it was super-dumb to change the position of the window buttons for no reason that has ever been explained to us users.  Dumb.  D. U. M. B.  That is not treating your users with respect.  This is linux.  No matter how much you (i.e. some mythical person controlling Ubuntu) may want to look like Apple, for God's sake don't even dream of *being* like Apple.

There is a reason, it has nothing to do with being like apple the company (although it does take a page out of OS-Xs UI):
[http://www.markshuttleworth.com/archives/333](http://www.markshuttleworth.com/archives/333)

---

### Post by bdig85 on 2010-05-03
Hello everyone! I wanted to share my experience with the latest Ubuntu upgrade. I was a little scared because I had never upgraded Ubuntu. This is the first time a release came around when I had Ubuntu installed on a computer (a Samsung N310 netbook). I debated doing a clean install vs. an upgrade, but due to my dual boot situation, I decided to go ahead and try an upgrade first. Thankfully, everything went perfectly. It took quite a while to complete (about 5 hours) but once it was done, everything was in place and worked just as it had before. I'm loving this release! I already installed it on my main computer as well. A job well done! :D

---

### Post by Ethangar on 2010-05-03
> **P4man said:**
> Even if you never improperly restart, ubuntu will check your filesystems every x mounts. x being 30 by default I think (its configurable). The counter for that is in the filesystem itselve, so even if you only just upgraded it might just have reached that number.

Good to know. Thankyou.

---

### Post by pirexeee on 2010-05-03
Hi,

I updated Karmic Koala NBR to 10.04, via the update capability of Koala.

After the update I've noticed:
- Takes more time to boot then before (know it appears a black/wite message before the login, with some errors)
- All the windows are minimized automatically after about 2 secs of open it

Any suggestions/help?

Best regards and great job!!

---

### Post by eotakos on 2010-05-03
Hello everyone, congrats to the Ubuntu team for putting together another LTS,  congrats to all of you for your new OS.

I was thinking about which category I should vote for, because I was certainly not upgrading, but rather not-so-fresh installing keeping the /home from the previous install (separate partition). That was the one thing... the other thing was that my previous installation was the last LTS (8.04). 

So, in these last two years I guess there have been quite a few changes in the config files and directories in the home folders, which resulted in having kind of messed up menus. The funniest of all mis-functions being, hitting Places->Home Folder, which started Rhythmbox (like if someone new I wasn't getting along very well with that program....). Note that this problem didn't exist for new test-users I created.

Doing a little bit of searching, I found out that it was a minor issue some faced when upgrading to 8.10. The proposed solutions I found weren't any helpful, but deleting the .local folder sure fixed the problem (I noticed that this folder didn't exist at all in the test-account home directory.

Anyway, I don't consider this to be an installation issue, so I voted for flawless installation (did I ruin your poll?? :D - I hope not). Besides an OS installation lasting 15 minutes!? who would believe it :-)

---

### Post by sille777 on 2010-05-03
I upgraded this weekend from 9.10 to 10.04. I upgraded using update manager.

The upgrade process reported an error with network manager, but continued to upgrade. upon finishing and reboot, everything seems to be running perfectly normal and no apparent errors with my network manager.  (I did vote for flawless upgrade in the poll despite the issue I listed above, since I really did not have to fix anything.)

The process took about 2 hours after it downloaded all it needed.  

Looks good and running great.  I also quickly found the how to: to move the min-max-close buttons to the right (which is where I prefer and am used to them being)

---

### Post by man_bash on 2010-05-03
Upgrade itself worked OK with a few dropped packages and restarts - took 4 tries to do. I blame it on the wireless, but that's all I have...

Done this on a netbook, and I got UNR again, and I never liked the UNR to begin with. Now I don't have the second panel, the one I have is useless, and I cannot add the second panel, nor remove anything from the 1-st one, and that is after disabling UNR first, and then uninstalling the packages with synaptic. Right clicking on empty space on the top panel gives me "Help" and "Properties", as well as _grayed out_ "Add to panel", "Add new panel", and something else. I only have about 3 pixels of it to click on, right under and to the left of wireless display. Looks a bit too Mac-ish in icons though. Will probably revert back to Karmic on a netbook at least. I will give it a second shot on a desktop, but I'm gonna use another partition for it though.

Looks absolutely stunning out of the box so to say, possible to backport some of those themes and graphics into Karmic :D

---

### Post by Bobulous on 2010-05-03
I had two problems (upgrading from 9.10 to 10.04):

1) The notification icon was a big, red no-entry sign complaining about the /etc/apt/apt.conf.d/99synaptic and a Permission Denied error. I think I've fixed this by making the 99synaptic file readable to all users. The content of the file is extremely tame, but if anyone knows of a reason why this file should not be readable to all, let me know.

2) The window borders are missing most times the machine boots. The only way I know how to get the borders back is to go into System -> Preferences -> Appearance, then change the visual effects from "None" to "Normal" (or vice versa), after which the window trimming magically reappear. So Compiz is likely to be at fault, but I don't know how to fix this permanently. Any ideas?

---

### Post by abrianb on 2010-05-03
Very smooth upgrade.
 Much better than the last one.
My Brother MFC240c scanned using Xsane, without opening a terminal and going to work.(the first upgrade for that) ((simple scan also worked and the scan looked better, crisper and had a more accurate color representation than xsane))

---

### Post by OldGoat58 on 2010-05-03
Well, I'm reasonably certain that the problems I'm experiencing are directly related to the fact that I am computer illiterate, but here goes.

Followed the instructions from Ubuntu.org on upgrading from Karmic Koala to Lucid Lynx.  I had already burned an installation CD but decided against doing a "FRESH" install as opposed to the upgrade option offered through Update Manager.

It took forever.  Well, OK, maybe not forever, but I took a nap and woke up an hour and fifteen later and it still wasn't finished.  Once it did finish the first issue was it wouldn't boot.  It got hung up on the splash screen.  (Unresolved)  Still happening.  Have to do a HARD shut down and then it normally works.

Second  issue was with playing games at POGO.com, for which I posted for help in the "General" section of Ubuntu Forums.  After reading a load of stuff I went in through "Synaptic Package Manager" and removed the IcedTea Plugin from my package.  My games at POGO then loaded and played without incident.  :o)

The other problem I have is that "Evolution" just spontaneously closes without warning or any input from me.  If my computer sits idle for say 45 minutes, which is not uncommon at work or at home, and I come back to it Evolution has either already closed or when I maximize the window and attempt to reply, forward, or get mail it just closes.

I am NOT extremely savvy when it comes to CLI operating systems such as Ubuntu Linux, since ALL my experience prior to Karmic was with Mr. Gates products.  I am not going to give up on Ubuntu, as I've been enjoying the learning process since October last year!  If the problems persist I will try to figure out where my mail files reside on my hard drive, copy them to my external USB HDD, and then flop the good old CD in the drive and boot and install from the CD.

If push comes to shove I'll go back to Karmic as I was completely satisfied with that release and it functioned flawlessly.  The Great Ubuntu Powers asked us to share and share I did.  I like the feel for Lucid, and I think I could probably get my family to change, but I won't do that until I figure out the glitches.

Thanks for reading!
Mike
Fairless Hills, PA

---

### Post by nucleuskore on 2010-05-03
On my desktop I attempted a clean install (as I always do), and took three hours of fiddling around to get past the out of sync display and install. This was due to the built in NVidia graphics card. Published my [workaround](http://ubuntuforums.org/showthread.php?t=1463294&page=2) on the forums.

On my netbook eeepc 1000H my wireless card (rt2860) does not connect to WPA or WPA2 networks. Hopefully a fix will be out soon :(

On my wife's Acer AS5732Z-4867 wireless network reception was weak and frequently disconnecting; fixed it by installing **linux-backports-modules-wireless-2.6.32-31-generic**

---

### Post by manzdagratiano on 2010-05-03
> **eotakos said:**
> Besides an OS installation lasting 15 minutes!? who would believe it :-)
I do believe it - for it took 10 minutes on mine! Karmic had taken FIVE!

---

### Post by jim97321 on 2010-05-03
Mostly it went well.

However, I found that when I download "qcad" it is not visible in the menu (usually under Graphics), so I don't know where to find it.  It worked well in 9.10 and earlier Ubuntu.


I would like the "UTC=no" line to be set in /etc/defaults/rcS, that way I don't have to change it manually each install on my thumbdrive... that way the clock is not changed when I boot the system as Windows.

Thank you for the new LTS.

---

### Post by cthlhu1987 on 2010-05-03
I upgraded from 9.10 to 10.04 via the Update Manager. all works fine, I had to fix the minimize,maximize & close buttons (They were after the upgrade on the left side... Who the hell had this "smart" design idea?!). And the Software Center and the Gnome MPlayer frontend looked better in the 9.10 version, too. I've seen no real problems (Applications that stopped working or similar stuff), it was a less abrupt change than from 9.04 or 8.10.
Dear Ubuntu Team, thank you... This release proofs one thing once again:

---

### Post by jcoles on 2010-05-03
After I got it installed, it looked good. 

But the install disk is flaky, and that will stop some people in their tracks. (Yes, I ran the CD check. No errors.)

If you hit ESC or cursor keys during start up, you see error messages. Hitting ESC at the right time brings up a text menu which includes Try, Install, Check Disk, etc. Hitting the wrong key at the wrong time leaves you hanging blind (black screen). It's quite unstable.

Throughout the installation there are black screen periods that make the system look dead. I discovered by accident that the install might recover if given enough time. The user needs to be kept informed at all times. There should always be some evidence of life, even if it is only an incrementing timer or set of dots. Trying to use graphics too early in the install process is risky. A basic text mode is the most reliable.

If you are really patient and never touch the keyboard during startup, you eventually get a graphical menu with just Try and Install options. Is there any documentation about keypresses you can use during install? 

Installing into VirtualBox OSE is very slow and the flakiness is made worse by severe lags in responding to user input. The install seems to work, but when you boot the new install, the window changes shape three times but remains black. It seems dead, but after about 10 minutes, Ubuntu starts. It's rather sluggish, though.

As a user, I would rather see fewer releases, better tested and more stable. Non-technical Ubuntu users (are there any?) are best advised not to attempt any upgrades unless the upgrade has functionality they really need.  

In spite of the installation difficulties, what I have seen of installed Lucid (on hardware, not VirtualBox) is good so far.

---

### Post by jcwmoore on 2010-05-03
the upgrade hosed my server, rather than deal with the grub issues i just nuked the virtual hard disks that are my server, reloaded them from back up and tried again, second time with the upgrade, (installing grub to all disks and partitions) work fine.  now i just need to recover the last few weeks of content as the back ups have aged a little.  the nice thing about a VM is that it becomes a magic retry "button" when you need it most.

---

### Post by bousozoku on 2010-05-03
For the most part, the upgrade from 9.10 was flawless.  There was a mention of a problem with network configuration, but it apparently wasn't a problem as networking is fine, as far as I can tell.

I had been upgrading from 7.04 and had increasingly encountered problems.  After 9.10, I had to re-partition the drive so I started over with a fresh installation.  I'm guessing this added to the stability of the upgrade.

This is the first Linux-based operating system version that I believe is good enough for grandma--any grandma, anywhere in the world.

I'm looking forward to the updated GNOME desktop environment in the near future but good work on Ubuntu 10.04.

---

### Post by Windy Peaks on 2010-05-03
No I did not type it manually, I just misspelled it when I wrote it above.
I am not on My A200 laptop right now but I will copy and contents of the aboved mentioned file when I get a chance.

Actually I am using My daughters eeepc, which strangely enough was just fawlessly upgraded to 10.04. So I'm 2 for 3 on the upgrade front.
Thanks for the replie and I'll post it as soon as I can.

Windy

---

### Post by quixote on 2010-05-03
Very interesting post you linked to, P4man.  (This is in ref to [this comment]("http://ubuntuforums.org/showpost.php?p=9230194&postcount=456") earlier.)  I agree 100% that vertical space should stop being wasted.  I agree with almost everything there.  What I didn't see was anything about why it was essential to move the buttons to the left.  Even in the drawings, he still has them all on the right.  

Besides, my point is really that if there's a good reason, users shouldn't have to hunt for it to find out.  And if there isn't a reason, if it's just someone's preference, **they should have made it a simple right-click option to position the buttons however the user likes**.

---

### Post by musicman10489 on 2010-05-03
I upgraded from 9.10 and it couldn't have been smoother. No issues or anything. I am incredibly satisfied :]

---

### Post by manzdagratiano on 2010-05-03
> **manzdagratiano said:**
> 
What I am going to do however, is to carefully test the new release on a virtual machine until I am satisfied I can risk the actual install

What I am also going to do is to flood Launchpad with bug reports and participate in weeding them out. Out of all the GNU/Linux distributions, Ubuntu is the only one that has what it takes to be `Linux for the masses', and I am going to see it through! Had it not been for Ubuntu, GNU/Linux would still be an underground cult-like phenomenon for the elite and the enlightened.

---

### Post by Windy Peaks on 2010-05-04
Here is the file You asked about, does it help ???

root@toshiba:/etc/apt# cat sources.list
# added by the release upgrader
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.2)]/ karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic restricted main #Added by software-properties
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) karmic main restricted multiverse
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) karmic-updates main restricted multiverse
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) karmic universe
deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [https://archive.canonical.com/ubuntu](https://archive.canonical.com/ubuntu) karmic partner
deb-src [https://archive.canonical.com/ubuntu](https://archive.canonical.com/ubuntu) karmic partner

deb [https://help.ubuntu.com/community/medibuntu/ubuntu](https://help.ubuntu.com/community/medibuntu/ubuntu) karmic main

Thanks for Your help with this.

Windy

---

### Post by bearbigears on 2010-05-04
As always I do a clean install of each new release. I had no problems as usual, I enjoy Ubuntu more than ever.

---

### Post by Windy Peaks on 2010-05-04
this is what the message says once the upgrade gives up.



W:Failed to fetch [https://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](https://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  couldn't connect to host
, W:Failed to fetch [https://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz](https://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz)  couldn't connect to host
, E:Some index files failed to download, they have been ignored, or old ones used instead.

thought it might help

---

### Post by iu34 on 2010-05-04
Upgrade/install, I did both. Upgrade first, then clean install.

The only problem I had was a slow internet connection, but I got it fixed by using the internal wireless adapter instead of an external one(linksys wusb54G version 4). Possible driver issue perhaps?

Other than that, it's been great! I'm really loving Gwibber, especially from the MeMenu.

---

### Post by jimpofic on 2010-05-04
Hear, hear.  Complete disaster - wouldn't boot after upgrade and then after 5-6 hours of trying, still no success in doing a new install.  The disk partitioner has crashed multiple times, requiring me to start over.  I did get through the entire installation process once - machine wouldn't boot afterward.  All in all, my worst experience with linux yet - and I started with Debian 7 years ago.  This sucks.

---

### Post by quequotion on 2010-05-04
I have a special case:

1. I've tried upgrading online, but my connection is through a ssh tunnel and there simply isn't any effective means of socksifying the whole upgrade process without breaking something.

2. I've tried upgrading offline, using the alternate CD, but that breaks down and says I have held broken packages, which is not true.

3. The thought of doing a clean install gives me the shakes. I swore after my wretched and disgusting karmic upgrade experience that I would never again format my hard disks for a linux install.

It looks like I'm most of the way there with the offline upgrade, but I can't make any progress unless I can get a list of the conflicting packages... I imagine this is a list of lucid packages that conflict with my massively back-ported, ppa pumped karmic installation.

Is it possible to convince Ubuntu to upgrade *with* third-party repositories?

I'm going to try adding a pin to lucid packages to make sure they can override karmic packages with higher version numbers.

---

### Post by Peter Bell on 2010-05-04
Used Update Manager to upgrade my Shuttle X200 from Karmic to Lucid.

Upgrade process went smoothly, but still wondering about the list of Apps which were removed during the Update!

Problems encountered:

Firefox icon vanished ... quickly recovered.
Window furniture had migrated to the left ... soon found and reinstated the familiar theme.
AutoFS no longer starts up automatically at boot.  This was working fine under Karmic - now I have to start it manually.  How can I fix this?
Returning from screensaver demands a password entry.  How can I disable this?

However, nothing major, but I would like AutoFS back!

---

### Post by rhardie on 2010-05-04
Was not able to install.  The system began loading, a splash screen was visible for a bit, then a white square within the screen and the system locked up.

I don't have time to figure it out.  I switched my laptop over to Windows 7 from Ubuntu because of usability issues such as wireless drivers, business applications that were not available and regressions when Ubuntu upgraded.

I don't have time to fix broken things inside my computer....as much as I like Ubuntu....but I gotta work out in the main stream world where things work pretty consistently.

I think that if a person buys a computer pre-installed with Linux and it has been thoroughly tested for stability prior to the system's release to the public, then the main stream user can do just fine using Ubuntu Linux.  I would fit into that category of consumer, i.e. I don't want to fix anything (anymore); I just want it to work so I can work or play.

I continue to like Ubuntu and would recommend it to my family and friends - pre-installed with NO updates allowed (Like Dell appears to do).

I continue to think that Linux is fundamentally a better OS than MS Windows; things just aren't there "yet" for me.

---

### Post by asuastrophysics on 2010-05-04
That upgrade could not have gone worse...wait, no it could always be worse...I guess someone could have come in my room and took a hammer to my hard drive.

I'm stuck with a completely malfunctioning computer that's spewing errors nobody on the planet seems to understand, meanwhile 250GB of 3 years worth of valuable data is being held captive inside it. I'm seriously considering going back to windows. I just happen to like windows better, I think. At least when I do an "anytime upgrade", there isn't a 1 in 2 chance that my computer will never start again and I'll have to reformat and reinstall the entire OS. With Ubuntu, you seriously need a backup hard drive, if not for regular data backup, then to save your stuff from updated destruction, everytime canonical decides you need an "update".

This is my opinion on Linux stability: It's absolutely rock-solid and stable on some particular sets of hardware. If you don't own that hardware, then it's an absolute eternal living hell. If I wanted to buy hardware for the specific reason of owning a stable OS, I would've bought a mac. ATI will never work well with linux, and neither will my chipset. ever.

...So yeah I guess I'm saying that the update didn't go well. ;-)

---

### Post by ~cyrus~ on 2010-05-04
Upgraded a desktop to 10.04 and the process went along just fine. Flawless actually :popcorn:

---

### Post by uRock on 2010-05-04
> **fritzman said:**
> 05/01/10 06:22:40 AM
For the past few weeks, I've been preparing myself for the almost-forced migration from Ubuntu Linux 9.04, also known as Jaunty Jackalope, to something newer.  I suppose I wouldn't really have to upgrade at all, except support from the Ubuntu community for Jaunty stops with the release of Ubuntu 10.04, also known as Lucid Lynx, on April 29, 2010. 
No, it is supported for 6 more months. Intrepid its the one that just lost its support.

---

### Post by rhm on 2010-05-04
I did a Windows Vista dual-boot upgrade from Karmic and a Windows 7 dual-boot Live CD clean install today, both currently up and running perfectly.

The upgrade from Karmic was painless, although it took all afternoon and the better part of the evening to download, install and clean up. This is on a HP Pavilion dv2000 AMD64, with nVidia graphics card. Everything important worked flawlessly.

The only glitch was that it added an underscore to the name of a FAT32 drive I use to share documents between Windows and Linux; It is called *common* but now mounts as *common_*. This caused a problem because (for some reason I can no longer remember) I keep my Firefox profiles there and when I tried to start it, it complained about being already running. I fixed this by adding the underscore to the profile path in the *profile.ini* file of FFox. Initially I thought it could have happened because I neglected to unmount the drive during the *restart* part of the upgrade. Now I'm just perplexed about it. Fortunately that is the extent of the problem. Any clues as to what this is are appreciated.

The clean install was for a Dell Vostro 1500 AMD64, also painless except for a minor wireless issue. This was solved by plugging the laptop to the router and activating (and thus downloading) the proper Broadcom drivers. Easy as pie.

I'm particularly proud of the clean install because it is for my mother (she handled the installation) and so far she is loving it. She already had a bad Ubuntu experience with Feisty so she was initially reluctant about trying to move away from Windows, as much as she hates it. After the install and initial setup for multimedia, etc. she seems very pleased with her new OS and has already found ways to do everything she does in windows. Plus, her system is in Spanish (she doesn't speak English all that well) and the Spanish support is AMAZING! The best software translations I have ever seen.

Overall, both the upgrade and the Live CD install were superb. Thank you for this amazing piece of work.

---

### Post by Peter Bell on 2010-05-04
> **Peter Bell said:**
> AutoFS no longer starts up automatically at boot.  This was working fine under Karmic - now I have to start it manually.  How can I fix this?

Right, I've kludged this ... by modifying autofs.conf - I removed the netdevice gubbins from the 'start on' condition.  Now it just says:
     'start on filesystem'
I guess that this may well break something, but at least autofs starts up automatically at boot time now. :)

> Returning from screensaver demands a password entry.  How can I disable this?

... and I found this in the screen saver configuration. :redface:

---

### Post by Yorkiede on 2010-05-04
worked perfectly - the only problem I have now is that Evolution closes itself sometimes and needs to be re-opened.

---

### Post by homebrewn on 2010-05-04
Just completed the upgrade from 8.04 to 10.04, the only issue was flashnonfreeplugin. Found the solution on the forums and quickly fixed it. This is my first post, just wanted to thank everyone for the help they provide.

---

### Post by prabath_fun on 2010-05-04
Hi,
   I tried only with live CD with huge happiness. Because, I love Ubuntu so much and it is LTS version as well.

   But, boots till language screen, if I try to install or live boot hangs after boot screen (Ubuntu with animated dots) and there after no mouse or keyboard actions. 
   Only once live booted and after some times system hanged. I was happy by seeing 5.1 surround support on video playback without any work around as like in Ubuntu 9.10. But, that happiness lost with in few minutes as system hanged. There after no booting at all...
   
   So, went back with Ubuntu 9.10.

---

### Post by Windy Peaks on 2010-05-04
Good point, this is the first time I tried to upgrade this laptop I always did fresh installs myself. But I think there is something to this laptops setup, I justed tried to respond to a program crash and the crash report did not go through for the first time on this computer.
Thanks for the help.
Windy

---

### Post by manuti on 2010-05-04
**Upgrade** from 9.10, **all OK on a HP 550** core 2 duo with express card SSD 16Gb for separate /home partition.

---

### Post by EpoxyRepair on 2010-05-04
I've encountered the problem with autofs not working as well. For some reason if I actually mount a file via fstab then autofs seems to start up quite well. Otherwise I need to su to root
and run 'nohup rpc.statd -Fd &' 

I'll try your fix to the startup script instead.

I actually think this worked straight after the upgrade, so it's either intermittant or I broke it trying to get virtualbox to work

---

### Post by conryf on 2010-05-04
I've been with ubuntu since Hardy 8.04 and have installed or upgraded every distro since then and always had minor to major trouble. Usually upgrading turned into a forced fresh install. 

However I can say without a doubt Ubuntu 10.04 was the best experience yet. I had a small problem with internet speed that was easily solved. Excellent work guys!

---

### Post by wgarider on 2010-05-04
This was the first time I used the upgrade feature - I upgraded 2 machines to 10.04 and did one clean install. Elapsed time for the upgrades was about 3 - 4 hours each.

I have a fairly complex configuration (lots of virtualization 'stuff'); my wife's PC was simpler and quicker. Both machines appear to have upgraded seamlessly; I've only verified about half of my apps but there's nothing missing and everything seems to be working as it should. 

I also would offer Kudos to the Ubuntu team for the easiest upgrade I've ever done!

---

### Post by Crio on 2010-05-04
I've made two upgrades:

1) Server Edition upgraded from previous LTS -> smooth upgrade, but on reboot I run into problem due to unavailable entries in fstab.  It took about four reboots to notice message about "keep waiting,press S to skip mountng, or M for manual recovery" on splash screen, because the message tend to dissapear quickly (either with time or on key-pressed - don't know) and does not come back. Then some time was spent to investigate cryptic "ureadahead terminated with status 4" message, before the true reason came out. No fun. 

2) Toshiba L40 Notebook - one problem was that AWN manager lost all settings and did not want to run at startup (solved by removing check in AWN properties, removing entry in Startup Applications, restarting and setting check in AWN properties again); another - support for RTL8187B Wireless Adapter have been, apparently, improved and it now pays attention to RFon/RFoff hardware switch and corresponding Fn key, which were completely ignored before. Of course, I forgot about them long ago and of course they were in a wrong state. :) Took some time to figure it out, but it is my fault entirely.

P.S.: Now I've discovered that the first trouble is actually described in Release Notes. Should have read them before upgrade, not after!

---

### Post by yyyc186 on 2010-05-04
This should not have been released with the grub_puts_ error that effects everyone with more than one disk drive.

bad bad bad bad bad bad bad

I'm still not running.  None of the recovery methods listed here seem to work when you have 3 disk drives.

---

### Post by kellemes on 2010-05-04
Clean Install, as always.
No serious issues.

---

### Post by AnneTanne on 2010-05-04
Did a fresh install...

I have been experiencing sound issues in the majority of distro's/versions I tried until now.
Only the very first Linux-distro I ever tried (Suse 7.something), and 9.10 give me sound and not sound-problems.  

It has even happened that I had sound via headphones (and none via speakers) in one version, and no sound at all in the next, so I was pretty sure that 10.04 would be giving problems too.
But guess: flawless sound, and even better (i.e. louder) than in the previous release.  In 9.10 I couldn't hear my music anymore when going to the other side of the room, but now I can even go to the kitchen...

I fear I'm gonna stick with 10.04 for a long time... To afraid to loose this!   (If I could get Banshee to work properly, I would really be a happy girl! I don't like Rhytmbox, and find Amarok a little clumsy, but those do work)

---

### Post by vagrale13 on 2010-05-04
4 clean install and 1 upgrade from karmic, without problem!
Everything went fine!! =D>

I vote *Install - worked flaulessly* because we have one choice! :roll:

The only problem I have encountered so far is with the *agp ATI *:confused:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413/)

---

### Post by johanbove on 2010-05-04
The first post, i had troubles with the LIVE CD;[INDENT][I]Thus far cannot get the LIVE CD to boot; stuck at the animated dots splash screen as other users. Probably has to do with the IDE controller I have hooked up extra in my comp...

Am thinking of trying a clean install once I figure out how to reinstall all the (dev) apps in the least time consuming way. Have my files on a separate /home drive, but still it would be good to have some sort of script to install everything in one go.[/I] [I]

For now am going to stick with 9.10 for a while; it took me a couple of weeks to get that release going in the end [/I] *:-)*
[/INDENT]*Wanted to change my experience post with the upgrade;*

I got the CD to work by writing it on the lowest speed, so I could load Lynx and check it out on my old comp. Everything worked great and so I decided to go for the upgrade from 9.10. It took a few hours to finish, but after a reboot the Lynx was purring on my machine!

Just want to congratulate the upgrade team for the great work! Using Lynx for a day now, and i'm simply amazed by the new features and speed increase on my system. Great job!

One detail though, did you really have to move the buttons to the left of the window? I mean, it's probably great for left handed people, but simple statistics apply that most people are right handed. Additionally the window scroll-bar is on the right of the screen, hence buttons should be close to the scroll bar... Good thing it's easy to switch the themes.

---

### Post by Jonners59 on 2010-05-04
> **yyyc186 said:**
> This should not have been released with the grub_puts_ error that effects everyone with more than one disk drive.

bad bad bad bad bad bad bad

I'm still not running.  None of the recovery methods listed here seem to work when you have 3 disk drives.

I agree.  I have three threads out about this plus others within this thread.  There seem to be so many users with the same issue or related.  There needs to be a new clear thread led by our "experts" with a fix.  So many getting lost and wasting time.  It's OK for geeks who love to play, they are probably getting off on this but for the rest of humanity and those we are trying to win away from Windows this just re-enforces the don't touch brigade!!!!:confused:

[http://ubuntuforums.org/showthread.php?t=1467211](http://ubuntuforums.org/showthread.php?t=1467211)

[http://ubuntuforums.org/showthread.php?t=1467225](http://ubuntuforums.org/showthread.php?t=1467225)

[http://ubuntuforums.org/showthread.php?t=1466166](http://ubuntuforums.org/showthread.php?t=1466166)

---

### Post by flyfishingphil on 2010-05-04
Only problem noted so far is the slow down while using Firefox. It may jump from page to page, like following a thread in Ubuntu, then suddenly slow down with "looking for Ubuntu", loading Ubuntu" and, finally, "Done" showing up in lower left corner of page. Have seen this on nearly every site I have checked, even getting to my Yahoo homepage, checking email(s) or returning to my home page from elsewhere.

Also, don't know if it's site related or Firefox related, but just noticed that, at the top right of this page, it shows: You last visited: 16 Hours Ago at 03:33 PM. I was in and out of here several times yesterday evening and had already been here once before this morning.:confused:

---

### Post by byline on 2010-05-04
> **jcoles said:**
> Non-technical Ubuntu users (are there any?)
Raises hand. Hubby is the Linux tech; I'm just a user.

---

### Post by chejrw on 2010-05-04
I tried upgrading from 8.04 LTS and am having some major problems.

I started a thread by so far no views or replies.  Maybe this will bring some attention to it: [http://ubuntuforums.org/showthread.php?t=1472451](http://ubuntuforums.org/showthread.php?t=1472451)

I've had good luck with Ubuntu upgrades previously, this is very frustrating this time around though.

---

### Post by byline on 2010-05-04
> **quixote said:**
> Niggles #2 and #3.  Give me separate system tray icons for battery, volume, and so on.  Do not "disappear" the volume icon!  (What ARE you folks smoking?)  Do not group it with some mail notification I don't want or need that takes up way too much space.
This reminds me: Every morning on boot-up, I get this window asking me to choose a mailbox. We use Thunderbird, yet it isn't listed among the options I can select, and there doesn't appear to be any way of adding it to the list. Also, there doesn't seem to be any way of discontinuing this notification option every time I reboot. Any suggestions?

It's not a real problem, just more of an annoyance.

---

### Post by cthlhu1987 on 2010-05-04
>  Last edited by cariboo907; 12 Hours Ago at 11:37 PM.. Reason: Removed derogatory image  
What kind of Linux forum is this taht forbids jokes about Windows or Microsoft?! <...>

---

### Post by biffnix on 2010-05-04
Man, what a pain. The upgrade from Karmic to Lucid killed mySQL so hard I still can't resurrect it.  Nothing seems to work, and no one seems to have any solutions!  AAAARGH!

---

### Post by uRock on 2010-05-04
> **cthlhu1987 said:**
> What kind of Linux forum is this taht forbids jokes about Windows or Microsoft?!
This forum isn't for bashing other OSes.

---

### Post by bhold on 2010-05-04
Install - worked but had a few things to fix.

My current 10.04 problem is annoying but not a show-stopper for me. I can't access Windows shares through Nautilus. Workaround is to install smbfs and use mount.cifs to mount the share. Also, for some reason I have no name resolution for my Windows system so I need to specify the ip address in the mount.cifs syntax. 

I'm approaching the 10.04 release same as always - installed in its own partition and will continue to run 9.10 while I gradually phase into 10.04. And eventually after some 10.04 patches and enlightment from the forums 10.04 will become my main system.

---

### Post by KingYaba on 2010-05-04
In a nutshell? Garbage. 

Hibernate and Suspend don't work. They totally trashed my system. The display now only uses the top-right corner of my LCD screen. Restarting the computer, starting gnome, redoing driver, isn't working. Worse is I can't even connect to the internet when booted in 10.04. I had a feeling I should have kept chuggin' with 9.10 and I should have trusted my gut. I totally wasted four hours last night installing and reconfiguring my system. :x:mad:

---

### Post by FoxMcCloudwp on 2010-05-04
I'm using quite an old PC, 2.6Ghz CPU, 480MB Ram, 40GB HDD. integrated GPU. It was very sluggish with it's default OS (Windows XP) I've been using Ubuntu on it since version 9.04, it has worked great, very stable, and very fast for being 7 years old :) 

I installed a fresh copy of 10.04 last Friday, it has worked great, the speed is incredible, Quake Live/ movies/music run fantastic. Also, I love the cream colored "Radiance" theme :)

---

### Post by thirdspace on 2010-05-04
Fresh install on old (Athlon XP 2000 CPU) PC. Reformat whole drive, autopartition, all defaults. Result: install reported success. On reboot, grub2 loads kernel, kernel cannot find root filesystem, drops into busybox shell. Repeat install, different CDRW media, custom partition (separate /, /home, ext3 not 4). Same result.

Install Karmic on exact same hardware, same options. Result: boots kind of slowly, but once booted, runs fine. Installed all Karmic updates to date, rebooted, still fine. Well actually, there is the small matter that I have to install a hand-crafted xorg.conf to get a reasonable monitor resolution, but that's a story for another day.

---

### Post by qhaz on 2010-05-04
> **biffnix said:**
> Man, what a pain. The upgrade from Karmic to Lucid killed mySQL so hard I still can't resurrect it.  Nothing seems to work, and no one seems to have any solutions!  AAAARGH!
Ditto biffnix . . . I found that I needed to reinstall mysql-server after the upgrade, and even now it's still broken.  When trying to access Gallery2 I get this error message "Deprecated: Assigning the return value of new by reference is deprecated in /usr/share/gallery2/bootstrap.inc on line 43" No images load and the font size is all screwed up!  Arrrg!

---

### Post by Rebelli0us on 2010-05-04
I think that the poll should include questions for those of us that gave Lurid Lucy 10.04 a test-drive and decided not to upgrade.

I didn't notice any differences from Karmic Kate, so if the changes are mostly under the hood maybe the upgrade should be just done quietly through the Update Manager.

---

### Post by Bobulous on 2010-05-04
Actually, despite my earlier posting, I've hit several other problems.

For reasons beyond me, trying to access Synaptic Package Manager suddenly started to ask for the administrator password (such that my own password would no longer work). This has never happened before, and after a reboot it's reverted to simply asking for my password. I've no idea why the sudden change in behaviour.

Thunderbird suddenly forgot what software to use for viewing http links, even though it worked fine for two or three reboots after upgrading to 10.04. Easy enough to fix, but it worries me when software suddenly forgets settings without good reason.

Netbeans suddenly stopped working, but that was easy to fix by installing the OpenJDK package and telling Netbeans to use OpenJDK (now that 10.04 has dropped the Sun JDK).

And I've still not been able to stop the window manager from failing to start each time I login. So I'm still going to System -> Preferences -> Appearance to toggle the Compiz settings (which seems to force the window manager to restart, and causes window borders to appear).

---

### Post by Elwro on 2010-05-04
Unfortunately, my initial positive view of the upgrade also ended when I realised that my system lost the ability to print :( It happily reports a job well done in the upper-right corner and deletes it from the queue, but the printer remains oblivious of any attempts of contact on part of my computer. No solution so far; on that particular computer I have to print from Windows.

---

### Post by rebeltaz on 2010-05-04
I don't understand the "I did a clean install from 9.10" or what ever version statements. A 'clean' install, to me anyway, means that you installed Ubuntu on a blank formatted drive. An install 'from' any other version, again to me, means that you did an upgrade from your existing version to the new 10.4...

Anyway, I digress... I **upgraded** my 9.10 to 10.4 last night (after agonizing over whether to do a 'clean' install and go with a dual-boot setup or just upgrade the straight Linux setup I was using) going through the Upgrade function of the GUI Update Manager and everything worked perfectly. I didn't have a single problem with the upgrade itself or using it afterwards. I don't know how a 'clean' install would have gone, but I'll probably do that on one of my other systems later.

Just a thank you....

---

### Post by Wolf-Ekkehard on 2010-05-04
Spoke too soon when I thought the missing KDevelop was the only problem.

Here are a few more that I encountered upgrading from Kubuntu 9.10 to 10.04 on a 32-bit i686 architecture, and this is how I fixed (most of) them (for those that run into the same problems with Kubuntu):

[LIST]qtoctave from distro requires version 3.2.0 or better of octave, the one in the distro, however, is only 3.0.5 - I'll fix that tonight by building the latest stable octave package from source - I guess the repository needs to be updated to make the two packages compatible.
[/LIST]

[LIST]Kontact's address book had a mysql problem that would prevent it from handling my existing (or any) address book.  To fix this I had to install the full mysql server ("sudo apt-get install mysql-server").
[/LIST]
[LIST]KPackageKit appears to be broken in Lucid, so the regular KDE GUI procedure (i.e. clicking on the deb package) didn't work.  I used the CLI "sudo dpkg -i <packae name>" instead, which worked fine.
[/LIST]
[LIST]The flashplayer in Firefox didn't play sound.  I followed
[http://ubuntuforums.org/showthread.php?t=1137803&highlight=libflashsupport](http://ubuntuforums.org/showthread.php?t=1137803&highlight=libflashsupport) without problems, which fixed it for me (I double-checked the effects of the rm commands mentioned there - they were safe for me)
[/LIST]
[LIST]To get KDevelop back, I did the following:

got and installed kdevelop-data_4.0.0-0ubuntu1_all.deb from
https://launchpad.net/ubuntu/lucid/<architecture>/kdevelop-data/4:4.0.0-0ubuntu1

got and installed kdevplatform1-libs_1.0.0-0ubuntu1_i386.deb from
https://launchpad.net/ubuntu/lucid/<architecture>/kdevplatform1-libs/1.0.0-0ubuntu1

got and installed libsublime1_1.0.0-0ubuntu1_i386.deb from
https://launchpad.net/ubuntu/lucid/<architecture>/libsublime1/1.0.0-0ubuntu1

got and installed lcov_1.7-1_all.deb from
https://launchpad.net/ubuntu/lucid/<architecture>/lcov/1.7-1

got and installed kdevelop_4.0.0-0ubuntu1_i386.deb from
https://launchpad.net/ubuntu/lucid/<architecture>/kdevelop/4:4.0.0-0ubuntu1

where <architecture> can be one of the following:
amd64
i386
armel
ia64
powerpc
sparc

Obviously, I only tried i386 for my own architecture
[/LIST]

After that, Lucid ran flawlessly for me, except for KPackageKit which still doesn't work, but there is a trivial CLI workaround mentioned above.

Again, a deliberately missing major package for doing real work is very irritating, the rest for me was minor and not a big deal at all - all in all a great release for everything else!

BTW, I run a dual-boot with XP residing on its own disk - grub didn't give me any grief, and both XP and Lucid boot without problems.

---

### Post by keepitsimpleengr on 2010-05-04
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/435136](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/435136)
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/575498](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/575498)
[https://bugs.launchpad.net/ubuntu/+source/cron/+bug/508083](https://bugs.launchpad.net/ubuntu/+source/cron/+bug/508083)
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/575502](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/575502)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/575503](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/575503)
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/435136](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/435136)

18 broken packages

Window manager crashes regularly.

No audio, sound manager does nothing.

awn no longer works.

compiz too hinky to use.

no consoles, only screen garbage.

wine crashes system.

backing up 9.10 was an excellent idea.

---

### Post by kfcSmitty on 2010-05-04
So far I've noticed

- USB stick requires sudo to copy.
- CD/DVD Drives do not mount on their own
- nano enabled logging and started giving errors

I'm sure there'll be more, but I haven't had time to play around at all.

---

### Post by accodata on 2010-05-04
Pogo Games
Hi

I have had a great experience with upgrading to ubuntu 10.4, just 1 problem, I can't get pogo games to play!
Has anyone got an idea on how I can fix this please?

with thanks


Accodata
:popcorn:

---

### Post by Peter Bell on 2010-05-04
I'm beginning to become a little frustrated by the 'low res video' problem!

It has happened four or five times since I upgraded two days ago.

The machine always boots up okay, recognises my monitor, and makes the appropriate 1280x1024 selection.

Then, some time later (it always happens when I'm away from the keyboard), when I wake the machine from the screensaver, I'm told that the monitor is unrecognised and a low-res mode has been selected.  The strange thing is that it's still running 1280x1024, but very slowly - similar to the performance when a previous update (was it Jaunty?) lost the ability to select an appropriate driver for my Intel 945 Graphics controller.

The other thing that happens at the same time as the 'low res video' is that running applications (certainly FireFox - I don't often leave other apps open) have vanished ... almost as though the machine has rebooted itself (but it hasn't - I can see this from the logfile for a background server process).

Is there a separate thread discussing this problem?  Is the cause known?  Is a fix forthcoming?

---

### Post by RayAYang on 2010-05-05
My Logitech Webcam Pro 9000 stopped working. Completely. The System->Preferences->Hardware Information no longer recognizes it. It's now marked as unknown (0x0809) in the USB device section.   How does one go back to 9.10? Or if I didn't backup, am I just screwed?

---

### Post by uRock on 2010-05-05
If your data is not in the /home partition, then you need to back it all up then reinstall Karmic. If you have the separate /home, then you can just install Karmic.

---

### Post by g-raf on 2010-05-05
I have two serious problems:

1) At startup, there's no option to hit ESC and choose which kernel i want - i need to use the realtime kernel, so this is a problem i haven't been able to fix. Please post a reply at the following thread if you have any suggestions for me: [http://ubuntuforums.org/showthread.php?p=9239501#post9239501](http://ubuntuforums.org/showthread.php?p=9239501#post9239501)

2) SCIM isn't working. When trying to load SCIM (it used to load automatically at startup), i get this:

Smart Common Input Method 1.4.9

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Failed to load x11 FrontEnd module.
SCIM has exited abnormally.

So I can't log into my e-mail since it's in korean.

Other than those two problems, 10.04 has been great. I even got fglrx working, which surprised me.

---

### Post by Levy1234 on 2010-05-05
I chose to do upgrades rather than new installs on three machines from Karmic to Lucid.  They all went flawlessly, but there was one post install oddity.  I decided to run computer janitor on one of my machines in lucid after the upgrade and it wiped out several things including my virtual box,  which seemed to work perfectly after the upgrade, before computer janitor killed them.  I use the version from sun rather than the version from the synaptic since the Sun version works with USB and, it seems, the synaptic version does not.  Unfortunately, Sun does not yet have a versions of virtual box for Lucid.  Oh well, there went my carefully updated and lovingly nurtured  version of Windows XP that I was running in Virtual Box!

---

### Post by 37fleetwood on 2010-05-05
well, this is the first time I've had any problems, usually it upgrades flawlessly, maybe I'll try back when everything calms down and a few bugs have been worked out. at least it didn't rape my 9.10.
[IMG]http://i39.tinypic.com/14nmcsg.jpg[/IMG]

---

### Post by int02h on 2010-05-05
Its a desaster. Horde groupware crashes down. I dont know what to do. Asking google for this, but just found broken webpages with same failure....



**Deprecated**:  Assigning the return value of new by reference is  deprecated in **/usr/share/php/Log.php** on line **168**

**Deprecated**:  Assigning the return value of new by reference is  deprecated in **/usr/share/horde3/lib/Horde/Notification.php** on  line **64**

**Deprecated**:  Assigning the return value of new by reference is  deprecated in **/usr/share/horde3/lib/Horde/Perms.php** on line **455**

**Deprecated**:  Assigning the return value of new by reference is  deprecated in **/usr/share/horde3/lib/Horde/Perms.php** on line **462**

**Deprecated**:  Assigning the return value of new by reference is  deprecated in **/usr/share/horde3/lib/Horde/Perms/datatree.php** on  line **82**

**Deprecated**:  Assigning the return value of new by reference is  deprecated in **/usr/share/horde3/lib/Horde/Prefs.php** on line **847**

---

### Post by infracom on 2010-05-05
I'm fairly new to Ubuntu but previously had 9.10 running for a few weeks. I upgraded to 10.04 without any problem although it did seem to take an age to perform the upgrade. I put this down to the fact that the internet connection is by a Homeplug device into my router and this can sometimes be rather slow.  A couple of times I was asked well into the upgrade to confirm I wanted to proceed. These particular questions seemed unnecessary and meant I could not just leave the upgrade running while I was out.  

This machine is used mainly for BBC iplayer so I don't have comments on how other applications perform on it. It also dual boots into Windows XP and the dual boot continues to work without a problem. Another post describes my installation, not upgrade, experiences on a different machine.

---

### Post by papikondalu on 2010-05-05
Upgraded two laptops to Lucid Lynx. Very minor issues remained!


1) On both systems, the window buttons (close, minimize, etc) were moved to the left by default. I had to go and select another theme and go back to the theme of my choice to get it back to the right side. I don't know why the left side was made as default !
2) On one of the systems, the synce-trayicon refuses to be shown in the notification area. I gave up after trying few times.

Other than that, I did not see any problems in upgrade. However, I did not see any improvements in speed either !

Overall a good upgrade experience.

---

### Post by infracom on 2010-05-05
I'm fairly new to Ubuntu but upgraded from 9.10 to 10.04 on one machine and installed fresh on another. Machine was a Dell Dimension E521 running Vista Business. I was doing the install from a LiveCD I had burned from the downloaded ISO. I intended to dual boot but was a bit wary of screwing up Windows boot loader so when I installed 10.04 I did not install Grub2 to the hard disk but told it to install to a USB stick. This seemed to work OK but when I tried to boot from the USB I kept getting some message about Grub error. It did not stay on the screen long enough to read. And yes, the machine previously booted 9.10 from the USB stick without any problem. So i thought that maybe Grub did not like having Ubuntu on the hard drive but Grub itself on the USB so I deleted the hard drive Ubuntu partition,  repeated the installation but put everything on the USB stick. I got the same (or similar) error when I booted from USB.

So I bit the bullet and installed yet again, to hard drive for both 10.04 and Grub 2. This time Grub 2 seemed OK, I got the expected Grub boot menu and could dual boot into either Vista or Ubuntu. But there does seem to be an intermittent problem. Since then I have booted many times and sometimes the machine freezes when booting into Ubuntu. This only happens after doing a "restart" (shutdown -r) from Ubuntu, not from power up. After the restart and selecting Ubuntu from the Grub screen the display goes white blank and stays like that. No keyboard sequence has any effect. the only way out is to power off the machine. then the boot works OK. This never happens booting into Vista, only into Ubuntu and only sometimes. 

Boot seems very quick when it works and for the most part I like what I see. Everything seems to work so far. BUT like many others I find the movement of the close/minimise/maximise buttons to the left side a real pain. It has become second nature to go to top right for these, which is where they still are on everything else except Ubuntu 10.04.

---

### Post by hellblazer on 2010-05-05
Upgraded with only three minor problems:
1) Firefox's icon changed to something random, but I have a custom installation of FF so I can't be too upset about that, besides it took about 5 seconds to fix
2) The volume control disappeared from the notification area. I read about other users having the same issue before I did the upgrade so I could find a solution for that rather easily, but this was very annoying.
3) I had to re-install mySQL and postgreSQL for some weird reason, but I didn't lose any data and the re-install update the versions of both

Except for that and compared to the previous graphics issues when upgrading this was a walk in the park. My dual screen setup works fine with nVidia drivers installed correctly. My customized theme was left intact and unaffected. Except for the databases, all my software works as expected even wine!

Overall, well done I'd say!

---

### Post by WishMaster on 2010-05-05
Booting from USB on Acer TravelMate 661:

Booting just stops at a given point. Black screen. Nothing to do,  can't even open a terminal (Alt+F1)!
    Do you think Ubuntu mentions some issues on their homepage?  Nooooo...     !
    It had to boot in VirtualBox to see some error logs. The logs  mention something about 'ureadahead', but the Ubuntu Bugtracker says  that it is an error... It displays 'ureadahead', but is has nothing to  do with it...
    After searching and searching and searching, I found out it might  have something to do with the graphics card     (Intel i855GM).
    
    Thanks to this [post]("http://ubuntuforums.org/showpost.php?p=9214364&postcount=52"), I got Ubuntu to boot: 
    -      press Tab on the 'menu' when Ubuntu boots,
    - you now see the booting parameters. Remove the 'quiet splash --'  at the end of the line and type '[COLOR=Red]i915.modeset=1[/COLOR]'.
    - Yeey: Ubuntu finally boots as it should !
    - install ubuntu to HDD.          On reboot, the system will not boot, again the issue of the black  screen.
      Now for he **next problem**: we need to put the  'i915.modeset=1' in the bootingsequence. Pretty ******ING ******  there is no way to boot into a terminal...
      Basically, we need to [disbable the gdm]("https://lists.ubuntu.com/archives/ubuntu-users/2005-December/061132.html"). 
      Let's reboot into VirtualBox... When the Ubuntu desktop shows in  VirtualBox, open a terminal:
      - > cd  /media/<whatever_your_HDD_is>/etc/X11 (I had something like  /media/3AR4184BFT-54FDEGH/etc/X11)
      - > sudo mv default-display-manager  default-display-manager_bak(make a backup)
      - > cd /home/ubuntu/Desktop      - > gedit default-display-manager When  gedit (=texteditor) opens: just save it as an empty file.
      - > sudo cp default-display-manager  /media/<whatever_your_HDD_is>/etc/X11      - now reboot. After a while, the booting seems to 'hang'. No worries,  this is normal since we just disabled the gdm.
      - press Alt+F1 to open a terminal.
      - you can now login in the commandline.
      - [When]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") logged in: > echo options i915 modeset=1 | sudo tee  /etc/modprobe.d/i915-kms.conf
      sudo update-initramfs -u       We have put the 'i915 modeset' in the bootingparameters now!       
      We have only one last thing to do: re-enabled the gdm: > sudo cp /etc/X11/default-display-manager_bak       /etc/X11/default-display-manager      Now you should be able to boot normally :-)



Booting on desktop fails completely. Ubuntu fails to recognize the DVI connection to the monitor..

---

### Post by amosct3 on 2010-05-05
I have tried with both the netbook and desktop verion by downloading the CD and tried an upgrade from 9.10.  All reboot and I get the Ubuntu logo and then a blank screen.  I have to do a hard power off.

I have an old Fujitsu S6120 that ran 9.10 fine so i did not expect any problems.

---

### Post by Charliemong on 2010-05-05
Well my first post. Upgraded from Ubuntu 9 to 10.40. Managed to totally brick the install. So will be doing a fresh install from a CD. But the upgrade process was smooth and would have worked i think? I Choose to keep my old Grub i think and it did not boot into the OS after the upgrade. Oh well we live and learn. Just got the Linux bug last year so still pretty mucha noob to this.:p

---

### Post by kellemes on 2010-05-05
> **Charliemong said:**
> Well my first post. Upgraded from Ubuntu 9 to 10.40. Managed to totally brick the install. So will be doing a fresh install from a CD. But the upgrade process was smooth and would have worked i think? I Choose to keep my old Grub i think and it did not boot into the OS after the upgrade. Oh well we live and learn. Just got the Linux bug last year so still pretty mucha noob to this.:p

Great attitude..

---

### Post by Jerubaal on 2010-05-05
**Upgrade using Alternate x86: **
I didn't include the online updates as part of the upgrade, which confused things to begin with, as other software such as gpodder didn't work anymore. However, once I ran the partial upgrade, such things worked fine.

The main issue still to fix is on startup where it has problems mounting all my partitions. I'm assuming I need to edit my fstab and probably change partion IDs as I've done when adding drives. However, I am planning on a big reorganisation and reducing the number of partitions. I had created a /boot partition, but I've found conflicting advice on whether this is worthwhile - maybe it is no longer helpful? 

**Clean install with desktop AMD64:**
All went smoothly, but the lack of proper Adobe Flash support means 64bit sadly stays unused for the time being.

---

### Post by ve3tru on 2010-05-05
I think you guys have done a nice job, but...
The install went well (clean install 64bit) had to hard wire to the internet and download my broadcom driver. Wireless didn't work out of the box no real biggie. That stuff could be a real nightmare for a newbe tho. Still getting this annoying flickering across the screen, it seems I'm not the only one either. Tried some of the fixes out there, but they don't work, waiting for a fix. Just updated everything and still no fix, its a little annoying; no biggie tho.

---

### Post by shebaw on 2010-05-05
I can't setup dual montiors and I can't manage to decrease my fan's noise. Other than that, it was a pleasant experience.

---

### Post by uRock on 2010-05-05
> **Jerubaal said:**
> **Upgrade using Alternate x86: **
I didn't include the online updates as part of the upgrade, which confused things to begin with, as other software such as gpodder didn't work anymore. However, once I ran the partial upgrade, such things worked fine.

The main issue still to fix is on startup where it has problems mounting all my partitions. I'm assuming I need to edit my fstab and probably change partion IDs as I've done when adding drives. However, I am planning on a big reorganisation and reducing the number of partitions. I had created a /boot partition, but I've found conflicting advice on whether this is worthwhile - maybe it is no longer helpful? 

**Clean install with desktop AMD64:**
All went smoothly, but the lack of proper Adobe Flash support means 64bit sadly stays unused for the time being.
There is a nice thread with a howto for installing 64bit flash that even has an app you can install that will remove the bad versions and install the right ones with just two clicks. [http://ubuntuforums.org/showthread.php?t=1414595](http://ubuntuforums.org/showthread.php?t=1414595)

---

### Post by denchriste@yahoo.com on 2010-05-05
Hello
upgraded 32 bit and 64 bit machines, the 32 bit went well cept had an ext32 146 gig partition had to break in half to get past the partitoning part ... the 64 bit made it bout half way and then died... had to do complete install of 10.4,, had no indication of what happened.. the 64 bit quit responding.. the new install went easy enuff,,just lost all me data..but luckily did backup before upgrade attempt.. very important,, also.. the reason for the upgrade- slow, 2-6 mb transfer from usb drives is still on the 64 bit ubuntu.. 32 bit seems to transfer at 26 to 32 mb but 64 bit still only doing 2 to 6 mb... same hardware from one machine to another.. something wrong with the 64 bit ubuntu... was hoping that was fixed... think will try a diff 64 bit flavor and see what happens...
still like linux better than windows... just some wrinkles is all..

---

### Post by alexc2 on 2010-05-05
Hello everybody...
I just did the upgrade from 9.10 to 10.04 yesterday... and I noticed that after the upgrade, the vsftpd service is really slow! It takes almost 30 seconds to connect (when it succeed)...
It should work without any changes, does it? 
Is there a way to improve the performance? 

thanks in advance.
AlexC2

---

### Post by uRock on 2010-05-05
There really needs to be an option in the installer to to automatically create the /, /home and swap partitions, so that people don't loose data with future upgrades and installs.

---

### Post by resthavener on 2010-05-05
Two problems:

1.  Having trouble with mouse cursor - can't customise (could be a show stopper for visually handicapped).  This seems to have happened after RC was released (that was OK at least in 64 bit).
2.  Firefox - I'm in UK and localisation did not flow through to search engines.  Got US Google, Amazon,ebay.  Finally found an add on which enables you to add new search sites (in my case UK sites) but it took about 30 minutes research - irritating and beyond many fellow newbies

---

### Post by bredman on 2010-05-05
Upgraded my wife from XP to Lucid.

Overall, very successful. The social networking is a real hit.

Some minor problems...

- The window controls on the left caused my wife to emit a high-pitched whining noise. This was fixed by moving the window controls to the right, and the whining noise stopped immediately.

- The darkness of ambiance was casting a shadow over our relationship, but radiance has brightened things up considerably.

For those interested in the computer: Dell Inspiron 2200, standard install plus b43-cutter to get WiFi working.

Windows XP (with its 300+ viruses) is now a distant memory.

---

### Post by rebeltaz on 2010-05-05
> **37fleetwood said:**
> well, this is the first time I've had any problems, usually it upgrades flawlessly, maybe I'll try back when everything calms down and a few bugs have been worked out. at least it didn't rape my 9.10.
[IMG]http://i39.tinypic.com/14nmcsg.jpg[/IMG]

Wow! I am subscribed to this thread, so when I got an email saying that there was a new message, I clicked on the link. When it opened in Chrome, it automatically went to this post centered on the screen.

It took me a few seconds to realize that the screenshot was just that, a screenshot, and not a message from my OS! Had me worried for a second....
:lolflag:

---

### Post by JayRobert on 2010-05-05
I did a fresh install as opposed to an upgrade from ubuntu studio Karmic, since I needed to shrink some partitions anyway.  Overall, the install went OK, but there are several annoyances:

1.  No volume control on the panel.  Really?  For an OS packaged with everything you need for creating audio and video, I can't understand this.  If it was an oversight, it's maybe excusable (though I have to say, why didn't you just copy it over from Karmic???  Was it broke?  If not, why are you trying to "fix" it?).  If it was intentional, I have to say it was a very poor decision.  But maybe for some people volume is a setting that they adjust once on install and then just leave it the same for months at a time.

2.  In Karmic, the UUIDs for encrypted volumes were displayed at each password prompt for unlocking, which permitted different passwords for different volumes / directories.  In Lucid, this has been changed to a box with a little lock icon and no indication of which encrypted volume is being unlocked, which practically forces you to use only one password regardless of how many encrypted volumes you have.

If your question in response to this is, "Why do you need different passwords for each volume?", you are not paranoid enough.  Why not just leave encryption out entirely then? Why was it necessary to change it from the way it worked in Karmic?  Without the relatively easy to set up encrypted LVM RAID in Ubuntu, I would not have tried it in the first place.  It's a great feature, but not well-documented or supported generally.  The change from Karmic is inexplicable.

3.  The boot splash graphics are jacked up, rendered at what looks like VGA or maybe SVGA, but this is minor, since it reverts to the correct settings once logged in.

Overall, I still like ubuntu studio much more than I thought I would when I first tried it in January.  Hopefully these annoyances will be fixed in future updates, especially the volume control.  That's pretty basic.  I mean, how do you expect to win people over from Windows when you tell them they need to go find an app so they can control their volume from the panel???

---

### Post by uRock on 2010-05-05
> **JayRobert said:**
> I did a fresh install as opposed to an upgrade from ubuntu studio Karmic, since I needed to shrink some partitions anyway.  Overall, the install went OK, but there are several annoyances:

1.  No volume control on the panel.  Really?  For an OS packaged with everything you need for creating audio and video, I can't understand this.  If it was an oversight, it's maybe excusable (though I have to say, why didn't you just copy it over from Karmic???  Was it broke?  If not, why are you trying to "fix" it?).  If it was intentional, I have to say it was a very poor decision.  But maybe for some people volume is a setting that they adjust once on install and then just leave it the same for months at a time.

2.  In Karmic, the UUIDs for encrypted volumes were displayed at each password prompt for unlocking, which permitted different passwords for different volumes / directories.  In Lucid, this has been changed to a box with a little lock icon and no indication of which encrypted volume is being unlocked, which practically forces you to use only one password regardless of how many encrypted volumes you have.

If your question in response to this is, "Why do you need different passwords for each volume?", you are not paranoid enough.  Why not just leave encryption out entirely then? Why was it necessary to change it from the way it worked in Karmic?  Without the relatively easy to set up encrypted LVM RAID in Ubuntu, I would not have tried it in the first place.  It's a great feature, but not well-documented or supported generally.  The change from Karmic is inexplicable.

3.  The boot splash graphics are jacked up, rendered at what looks like VGA or maybe SVGA, but this is minor, since it reverts to the correct settings once logged in.

Overall, I still like ubuntu studio much more than I thought I would when I first tried it in January.  Hopefully these annoyances will be fixed in future updates, especially the volume control.  That's pretty basic.  I mean, how do you expect to win people over from Windows when you tell them they need to go find an app so they can control their volume from the panel???
I think they removed it because each application is supposed to have its own volume control. In 10.10 there will be a volume control amongst other things in the upper right hand corner of the window.

---

### Post by JayRobert on 2010-05-05
> **uRock said:**
> I think they removed it because each application is supposed to have its own volume control. In 10.10 there will be a volume control amongst other things in the upper right hand corner of the window.

True, each app does, but some don't work so well - e.g., sometimes volume on YouTube vids is locked, etc.  Plus, even old mixing boards, with all their sliders and knobs, always had a master volume control.  It's really the same concept - sometimes you just want to adjust the volume from one place.

So this proposed 10.10 volume control - will this be a master control and back on the panel, or something in the upper right for each app?

Also, do you know where I can find an app to put on the panel for a fix right now?

Thanks in advance!

---

### Post by cpmman on 2010-05-05
After several normal successful installs of 10.04 to various machine configurations a friend asked me if it would install to her 512Mb XP Dell.  She did not want dual boot or wubi so I said the only alternative is to try to see if Virtualbox would work with some misgivings about memory availability.  A session of redundant program removal Ccleaner and Speedupmypc followed by a defrag and chkdsk and all was set.

Sun Virtualbox duly installed on XP and a swift fresh install of a 10.04 beta I had handy followed by a not-very-swift update using the 238Mb it would let me have.  Everything worked fine and I took snapshots at each stage to ensure a swift return to working if problems occurred.  Guest additions fell over when trying to update the kernel and the computer completely locked up - not responding to alt/sysrq b so a three-pin reset followed.  On normal booting again we restarted the VM 10.04 and tried Guest Additions again - worked perfectly this time and we had full screen and non-captive mouse + usb.

It was after this that the problem occurred.  The next reboot of the real machine had the option of choosing between XP and ubuntu!  Whilst a quick edit of the boot.ini file on XP solved the problem for the user it left me wondering at what stage does the virtual world of Virtualbox start encroaching on the virtual world of XP and could this extend at some stage to the real world of people?! :lolflag:

---

### Post by g-raf on 2010-05-05
> **g-raf said:**
> I have two serious problems:

1) At startup, there's no option to hit ESC and choose which kernel i want - i need to use the realtime kernel, so this is a problem i haven't been able to fix. Please post a reply at the following thread if you have any suggestions for me: [http://ubuntuforums.org/showthread.php?p=9239501#post9239501](http://ubuntuforums.org/showthread.php?p=9239501#post9239501)

2) SCIM isn't working. When trying to load SCIM (it used to load automatically at startup), i get this:

Smart Common Input Method 1.4.9

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
Failed to load x11 FrontEnd module.
SCIM has exited abnormally.

So I can't log into my e-mail since it's in korean.

Other than those two problems, 10.04 has been great. I even got fglrx working, which surprised me.

Nevermind!!! I got these two simple problems fixed like no problem:

1) I should've read about the new Grub stuff (holding down shift to get the menu as opposed to hitting ESC)

2) I just needed to configure the SCIM Input Method Setup in System>Preferences. No problem, everything works great with 10.04 and it's fabulous.

---

### Post by PhilB on 2010-05-05
Worst distro ever.

The first two iso's I downloaded would not boot. The third did.
I did my usual clean instal (which I prefer to do very year rather than upgrade, on a 250GB drive by keeping my 240GB home partitions and installing / and swap on the remaining 10GB. It asked for and kept all my personal settings.
When the install was finished, I booted and found that I had 16GB of space available in my home partition-all empty.
However, checking with the disk utility I still had 250GB mounted as home. 
Currently checking the disks and hoping to rectify the situation, if this doesnt work I only hope that I can get Karmic back up and running.

Apart from the busybox problems a few years back have never had any major issues with Ubuntu, but at the moment I am really pissed off with it.

Well, five hours later I have a basic Lucid system running. Found my original home partition buried deep in the file system as a separate sub folder (?). Luckily most of my browser/newsgroup settings could be copied over to the new home folder, but playing safe and starting from scratch with new desk top config files etc. Still got a long way to go to get it back to how I want it.
A bit happier than I was earlier, but I have had an Ubuntu desktop since Breezy, and this is by far the worst install experience for me.

---

### Post by acii on 2010-05-05
I upgraded a few days ago.

Had to fiddle with a busy cursor problem; VirtualBox (Windows XP) seemed to take another step backwards and some memory problems with a few apps. Today there were a bunch of updates (kernel update to 2.6.32-22 among them).

Today Ubuntu runs like I've never seen it behave before. VirtualBox is back to where it used to be and far better..eminently usable. Nautilus seems 200% improved. Many other improvements too numerous to mention. A speedy and attractive OS.

This is good....really good work.

Thanks to everyone involved for the effort (and apparently listening).

---

### Post by uRock on 2010-05-05
> **JayRobert said:**
> True, each app does, but some don't work so well - e.g., sometimes volume on YouTube vids is locked, etc.  Plus, even old mixing boards, with all their sliders and knobs, always had a master volume control.  It's really the same concept - sometimes you just want to adjust the volume from one place.

So this proposed 10.10 volume control - will this be a master control and back on the panel, or something in the upper right for each app?

Also, do you know where I can find an app to put on the panel for a fix right now?

Thanks in advance!
I went through the menus to System> Preferences> and dragged and dropped it onto the bottom panel. It will open the sound preferences applet when you click on it.(Not quite the same as just clicking and sliding like on previous versions.)

In 10.10 there will be a volume control on every window, I think that it will be for controlling the sound on just the app in the Window, but Mark's blog doesn't specify.

---

### Post by ggsinclair on 2010-05-05
Have always been a big fan of Ubuntu and I have never had problems upgrading before but am having the following issues:


[LIST]
[*]Boot time is slow - I suspect that this is a hardware issue but havent been able to get to the bottom of it yet. Need to find out where boot issues are saved.
[*]CD burner has stopped working properly - cant rip or burn using any software.
[*]Applets on taskbar either disappear or merge which is annoying.
[/LIST]
Not the biggest issues in the world I know but I am used to seamless upgrades so am a little disappointed.

That said Ubuntu still rocks and is infinitely better than Windoze.;)

---

### Post by marcusjames on 2010-05-05
[SIZE=2]I installed Lynx ok. But then I reinstalled ubuntu 9.04. Both installs are meant to share the same /home directory. This causes ubuntu 9.04 to crash to a black screen on boot. I didn't see any screen asking the user to take ownership of the common /home. Secondly on previous test installs I noticed that if swap isn't set the installer will install a new one even if there is one already. I can't find how to use Konqueror as a root user. And I can't open kate as root either. I wouldnt need to at all if the grub 2 didnt over write my grub form another OS. All manner of windows effects don't seem to be working. On my grub boot screen all ubuntu installs start with the words ubuntu generic or similar.........there is no useful label.......I also notice that the default method of alerting a new user to the existence of the non free codecs is to wait till he fires up konq - which he might never do. To complete my misery this text input box types in a miniscule font which is virtually unreadable to me. Altering the setting makes no difference. Am I happy ? No. [/SIZE]

---

### Post by cthlhu1987 on 2010-05-05
Does anyone know, where the KPDF in Lucid has gone? :confused: :confused:

---

### Post by Wolf-Ekkehard on 2010-05-05
Use Okular instead of Kpdf - works fine for me.

---

### Post by KinKiac on 2010-05-05
I actually searched for this thread just so i could post a positive experience.  I hate seeing all the negative feedback with no positive feedback so i thought id try to balance it out a bit.  My install worked flawlessly.  No sound issues, no video issues, compiz works fine, no CPU maxed out issues.  It just worked.  I have been using Ubuntu since 9.04 just came out and this has been the quickest and most painless install yet.  Although i credit at least some of that to the fact that Im not a noob anymore, well sort of, lol.  I had my desktop up and running and looking the way i like it within 2 hours.  

The initial install only took like 20 minutes and the rest of the time was spent just loading video drivers and then configuring compiz, installing flash for online video, installing gstreamer etc etc.  Also, with regards to the number one complaint I have seen, that being the buttons moved to the left, lol, I have no complaints at all, even though I prefer my buttons on the right.  I thought I would have to change it all but I like using emerald for my window decorator and when I selected trueglass and then edited a few settings for color and size of the title bar etc, I looked up and noticed it already moved the buttons for me.  So for me anyway, the whole button thing is a total non-issue for me since I didnt have to do anything I wouldnt have already done to get them back to the right.  No editing of config files or reading up on the most efficient solution, just set everything up the way i nromally do and hey what do you know, the buttons are on the right, YAY.  

My final words - Great job guys, keep it up, I cant wait for 10.10!!

---

### Post by Wolf-Ekkehard on 2010-05-05
Now everything is working again - sigh - except one thing:  How is samba supposed to be stopped / started / restarted / reloaded / status-checked?  The file /etc/init.d/samba is gone, so neither the "service" command nor the manual approach using this script will work.  Is this just a bug (in which case I simply recover the file from my backup) or is there a new/better way to administer that service?  Anybody knows?

---

### Post by uRock on 2010-05-05
> **Wolf-Ekkehard said:**
> Now everything is working again - sigh - except one thing:  How is samba supposed to be stopped / started / restarted / reloaded / status-checked?  The file /etc/init.d/samba is gone, so neither the "service" command nor the manual approach using this script will work.  Is this just a bug (in which case I simply recover the file from my backup) or is there a new/better way to administer that service?  Anybody knows?
To get help with this, you might want to start a new thread. People with knowledge in that area are not likely to post here or read the posts here.

---

### Post by Zenith88 on 2010-05-05
I lost the ability to click links in the Thunderbird emails and open them in Firefox browser, which worked fine prior to the upgrade.

When URL is clicked, nothing happens. When 'open link in browser' selected from popup menu, nothing happens. Choosing Help from Help menu - nothing happens.

Either default browser registration is broken, or it's a problem with Thunderbird, either way I see a poorly tested release.

---

### Post by oxo2oxo on 2010-05-05
Did an upgrade on a Philips box without a hitch. 

Have been trying to do a clean install on a dell D400 laptop and install gets part way through and then just stops. Have burnt an alternative disk and still the same problem. No problem on the laptop with 9.10

---

### Post by phaile on 2010-05-05
During the install process I was able to access the web (clicked on the link to this very site from the last install window). Between the installer finishing and booting up again something happened to my network interface - it doesn't work in Ubuntu, but more distressingly it doesn't work in Windows any more. 

Anyone else had this?

---

### Post by njsharp on 2010-05-05
I always only INSTALL not upgrade, and sadly clicked the survey's lowest install button, but I really needed to click "got ONE OR TWO (not many) problems that I haven't been able to solve".  Lucid so far seems very good WHEN IT WORKS. 

In particular I have had a lovely time on my Dell Dimension 9150 with NVIDIA 7300, especially now I have AT LAST understood MythTV enough to get it working really well.  I haven't booted WXP+WME for days now, and might just never do that again!

I have had a slightly ordinary time with a Gigabyte GA-K8N51GMF board talking to a 1024x768 LCD since the install really wanted to use 640x350 which is just a TRIFLE exiguous given that it is smaller than some of the install screens, so I couldn't see the FORWARD button!  F6+nomodeset fixed that for the install, and I managed to see enough of SYSTEM PREFERENCES MONITORS to get to 1024x768.  The onboard GPU is NVIDIA C51G (GeForce 6100) rev a2, and I have yet to try the proprietary driver for that.  The login screen still looks like 640x350

I have had a failure with my Toshiba Satellite A10 which uses this GPU:
Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
and there seem lots of problems with that in Lucid.  I think they are well enough known for me to skip a repeat here.  I wonder though if this problem will be fixed nicely for installing, since the bad code is on the install disk, and would presumably need an install time work around (currently F6 then replace quiet and splash by i915.modest=0 xforcevesa) and a boot up time work around to get to the point where the installation could be mended by an Update Manager run so all future boots would be good.  Hmmm!  A re-spin isssue needed?

So despite having to choose the bottom button on the survey, I'm quite pleased with Lucid, and look forward to a fix for the Intel 855M GPU.

Thanks to all the contributors!

---

### Post by The Question on 2010-05-05
Unfortunately, 10.04 is a dud for me.

I tried to upgrade and it crashed while doing so, making system unbootable.  So then I installed an old version and tried downloading the ISO and installing from CD.  It crashed several times doing that but worked on the third try.  Probably should have abandoned it at that point, but I thought if it got through the install it would be fine.  But it crashed constantly with a "getpwuid_r failed due to unknown user id" and then for some reason Nautilus would not recognize either the CD drive or the DVD drive, making copying data impossible.

I still have it on one partition and maybe if it becomes usable with some updates I will be able to switch to it.

Looks real pretty. :)  Funny how outdated 8.10 looks now.

---

### Post by cthlhu1987 on 2010-05-05
> **Wolf-Ekkehard said:**
> Use Okular instead of Kpdf - works fine for me.
Thx, works fine and convinient like kpdf. Thx, u rul :)

---

### Post by garry.donnelly on 2010-05-05
Worked like a charm.  Upgraded a desktop, installed one fresh and installed a server.  Had a little problem with non-free-flash and media-tomb packages during the upgrade but it was easily resolved.  I even took screen shots along the way to show other how easy it is to install the new Ubuntu Server.  Posted the slide show in [30 Screenshots to Install Ubuntu 10.04 Lucid Lynx Server]("http://www.greatwhiteit.com/web/guest/technology-blog/-/blogs/thirty-screenshots-to-install-ubuntu-10-04-lucid-lynx-server")

---

### Post by eagle-eye on 2010-05-05
> **JayRobert said:**
> 

Also, do you know where I can find an app to put on the panel for a fix right now?

Thanks in advance!

Go to System, Preferences, Startup Applications

Click on Add

Give it a name

In the command field type **gnome-volume-control-applet**

Job done.

---

### Post by AlexanderDGreat on 2010-05-05
@biffnix - have you read the release notes? I saw something about the mysql version there, pls. take a look.

---

### Post by Pepe Lebuntu on 2010-05-05
Pretty horrible to be honest. I am a STRONG advocate for linux, and for ubuntu specifically. I was SOOO looking forward to Lynx, but have been disappointed rather badly. Here's the three major things I'm a little ticked off about:

1. I was really looking forward to the desktop integration with social networking. In reality though, this function always goes to offline mode, and needs to be "woken up" by going to the envelope and opening "chat". Also, the feed from Facebook and Twitter is very sporadic, and if I was relying on it to send me every comment put up by a friend (which is what I expected it would do), I would think all my friends were basically dead.
2. I was really looking forward to the new music store, as this would allow me to be able to get the same music my Apple friends can get so easily. Then I go into the store and there is very, very little selection of any real music of note - I look up Coldplay = nup, for example. This is despite 7Digital, our provider, actually having all those titles.
3. Seriously, just give in to Sun and use Java. Yes we have to sign a license agreement, but OpenJDK is a nightmare of epic proportions. It's no good having Firefox if it doesn't load, or it crashes, etc. And since a vast majority of our stuff on Firefox uses Java, and OpenJDK is terrible, then Firefox crashes. I had to reinstall several times until I discovered this was the problem. 

So yeah, disappointed.

---

### Post by DrJohn999 on 2010-05-05
Upgrade from 9.10 x64 desktop went very well -- no glitches, crashes, etc. Two problems thus far, tho--

Sound is a little messed up. The system volume control doesn't work the same as before; it changes all sorts of settings on the mixer panel. I can't figure out what happened, but am attempting to put it right.

The Pitivi editor cannot open most of my avi files although Kino opens them without a hitch.

Not too bad!

---

### Post by JayRobert on 2010-05-06
> **eagle-eye said:**
> Go to System, Preferences, Startup Applications

Click on Add

Give it a name

In the command field type **gnome-volume-control-applet**

Job done.

Thanks for helping a n00b, and you too, uRock.  You both rock!

Next I'll tackle this flash thing.  FF is forgetting tabs since I tried Carlee's installer, and closes instead of minimizing.

Let's see, do I regret wiping XP off my disk?  Most annoying problem solved in 1/2 a day, and no Windows 7 launch parties to attend with [MS marketing geeks]("http://www.youtube.com/watch?v=1cX4t5-YpHQ").  Um, no, I don't regret it.

---

### Post by kenodlum on 2010-05-06
I use an old Dell Dimension 3000, a simple PC based around Intel chip set.  9.10 installed perfectly and 10.04 upgraded perfectly.
A bit boring really :lolflag:

---

### Post by CoolDreamZ on 2010-05-06
After a great experience upgrading my Lenovo S10 from 9.10 UNR to 10.04 UNR I have had a disastrous upgrade from 8.04 to 10.04 on my main desktop.

Four serious issues:

1. A network connection is required during installation as the package installer attempted to upgrade the mscorefonts packages. I say "attempted" because the wireless network connection failed during the upgrade process. Despite the lack of a network connection the installer repeatedly tried to download font packages for what must have been about 2 hours!

2. The package flashplugin-nonfree ended up in a broken state which I gave up trying to resolve

3. The RTL8187 wireless connection ended up "unmanaged" and I was not able to connect. I solved this problem with help from the forums only to find...

4. The RTL8187 would not work with WPA2 security, repeatedly asking for the password

I have given up trying to solve the network issue. I tried Linux Mint 9 RC1 live CD and the RTL8187 connection works perfectly, this is a mystery to me as it appears the same underlying kernel, driver module & network manager are used! I think I will wait for Mint 9....

From reading the forums on the RTL8187 issue it is incredible to see that this problem was also present in 9.10. Getting networking right should be one of the top priorities of any distro, without a network connection it is extremely difficult to resolve all the other smaller issues that need fixing.

---

### Post by VHans on 2010-05-06
> **frodon said:**
> [SIZE="3"]
The purpose of this thread is to share your experience installing/upgrading Lucid Lynx.



On my desktop (amd64) I am having problems with the nVidia drivers. I spent countless hours trying to solve them but I still get some weird errors and problems.

On my laptop (i386) Skype doesn't work anymore. Yesterday I tried all night to fix it. PulseAudio keeps getting in the way.

This upgrade makes me believe I can't afford using Ubuntu anymore. The time needed to fix problems is getting too much for me, I have real work to do during the day and I want to spend my evenings with my family.

I am looking for another distro now and I hope to find a solution that makes my computers productive again (suggestions welcome!)

I really liked Ubuntu but I don't recommend it anymore to customers, friends, family and I will stop using it myself.

---

### Post by dargaud on 2010-05-06
Well, quite a bunch of problems, mostly solved:
- during boot got random colored garbage and a lockup. Pressing random keys I discovered that [s] will skip a stuck driver (good to know), then removing vga options and logo from kernel options helped see what was going on.
- had to remove ureadahead which was locking up the boot
- had to remove the line "none /proc/bus/usb usbfs devgid=124,devmode=664 0 0" from the /etc/fstab as it was locking up the boot (I had nothing custom in my fstab). I don't know what it was for or if I should replace it with something else. 
- had to remove libnjb5 which was causing plenty of udev warnings during boot
- had to redo the nvidia settings and configuration twice before I got a proper screen.

After that I had a running OS, but:
- mysql was running but not working. Had to issue a password reset for my user. Thankfully I still remembered the sql root passwd: *UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='username';*
FLUSH PRIVILEGES;
- Gallery2 would display some 'php deprecated error'. Changing the php.ini to *error_reporting = E_ALL & ~E_NOTICE & ~E_DEPRECATED* solved it by shoving it under the rug.
- x11vnc keeps repainting the screen. I haven't [solved that yet]("http://ubuntuforums.org/showthread.php?p=9247210#post9247210").
- There were a bunch of other minor stuff I already forgot...

---

### Post by Herman on 2010-05-06
Lucid Lynx is the best Ubuntu yet!

I installed it a few times in my newest computer first, that one has a quad core CPU and an OCZ Vertex SSD and Lucid Lynx can boot in it in 3.03 seconds according to bootchart. Everything works.

My other computer is my multiple boot computer and that's the one with four hard drives, and I dedicated one whole hard drive to Lucid Lynx in that one, and that one will probably be my main operating system. I was worried a little bit for a while when I realised the sound wasn't working, but it started working all of a sudden for some strange reason when I clicked the volume slider in 'sound preferences'. 

Lucid Lynx also works great in my old PC Chips 'Book PC', with a 400 MHz processor and 512 MB of RAM. I installed Lucid Lynx a few times in that one to get an installation how-to made.

I installed Lucid in my EeePC as well, replacing Karmic Koala and it's working great in that too, everything works perfectly.

Quite a lot of friends are giving me their computers to install Lucid Lynx in too, some have had earlier versions of Ubuntu and others have tried out Ubuntu in the Live CD and have decided they want Lucid installed.
I've just finished installing in a big dual core desktop belonging to one friend, it had sound problems in Karmic, but the sound worked fine in Hardy. Anyway, much to my relief, the sound in that computer is working perfectly in Lucid, as well all everything else I tested.

I just finished another netbook install and I have a laptop to do tomorrow or over the weekend, and probably by the time the weekend gets here there will be more on my 'to-do'  list. :)

Lucid Lynx seems to be a great success out here in the Australian outback, all smiles so far and no complaints at all.

Well done devs and all involved in rolling out Ubuntu Lucid Lynx!
You people are the greatest! 

Regards, Herman :)

EDIT: Everyone likes the Ubuntu Software Center and I think Ubuntu One will be a big hit with a number of people too, given a little time for people to get to know it.
I was surprised how easy it was for me to install qgis this time too.

---

### Post by tomski on 2010-05-06
seems like this is becoming a trend for me

upgraded from karmic & well

first
was prompted with grub recue prompt found solution after 3 hours worth of google searches (why couldnt the grub upgrade get the correct settings from the old menu.lst???)
second (still stuck on this)
my display has failed to initialise, i saw the new purple (YUCK) splash screen for 2 seconds and the monitor turned off, hit ctrl+alt+F1 got a prompt & now i guess i have to re-learn everything again as it appears i no longer have xorg & it wont configure itself & im totally stuck & have embarresed myself by telling the owner of this pc that ubuntu is great & really easy to use!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

now i have to work around this issue & am considering giving up entierly on ubuntu as the only upgrade i have not had issue with was feisty>gutsy since then i have had to re-learn near on everything i had previously learnt

yes i know using linux is a learning curve but why do i have to going back to what feels like square one when you guy's make such detremental changes that what i knew previously no longer applies to ubuntu????

---

### Post by Kernel_Sanders on 2010-05-06
[COLOR=black][FONT=Verdana]Install of 10.04 went great. Downloaded image at work in 5min. burnt CD in 10min. installed in 40min. no problems. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Auto detected my wireless and connected no problems. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Found the drivers for my graphics card first time and installed. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]The new look is great.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]And best of all is the lightning fast boot up time.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Great work all :p[/FONT][/COLOR]

---

### Post by forestG on 2010-05-06
Hi! I upgraded from ubuntu 9.10 to ubuntu 10.04 and I have an Acer Aspire 5920G. All things work fine except for the media player keys on the left which is OK and the touchpad which is quite annoying.The touchpad does not work at all. Anyone who knows the solution to that problem? Any help would be deeply appreciated as I am a newbie to Ubuntu and Linux in general.

---

### Post by Merkaba_ZA on 2010-05-06
Overall this was probably the most impressive install of Ubuntu both from a design and usability standpoint that I've done yet.  I got it set up and sorted out all my custom repositories and programs in just about an hour. I'm loving the new look and design as well and hopefully it will see a few more adopters who can see that Linux is not marketed towards 'geeks' ;)

My only hassle was in the Me Menu breaking when I installed Pidgin. I don't use IM much from home any more so I've decided to just stick to Empathy for now even though I'm still sad to see it has no metacontacts support.

---

### Post by javisan60 on 2010-05-06
Friends, first Congratulations for the new 10.4 .

I have made 3 installations from 9.10 to 10.04 no flaws
One from 8.04 lts to 10.04 lts,  have to solve the problems, it only works on Gnome fail proof start.  But no data lost.

It says before the login page, that can not mount /proc/bus/usb then a message if (s)skipps of (m) modiffy, if (s) and started in gnome safe mode it runs without problem

If a user selects normal starts the computer stops working and congelate everything, just reset button worked.

Any suggestions?

Thank you....):P

---

### Post by radiomog on 2010-05-06
I have 6 computers running Ubuntu... 

I've upgraded the following:

 x64 desktop running 9.10 to 10.04 w/o any problems
x86 P4 panasonic laptop, again, 9.10 to 10.04 w/o any problems

installed 10.04 on a PE 1850 w/o any problems

my Lenovo T400 dual boot 9.10(x64)/Xp had issues at the reboot just after the upgrade process finished (started thread in I&Y).


on the machines that 10.04 is working on, seems to be better than 9.10, even my panasonic runs better. I was having some audio / video performance issues with it and gambled doing the upgrade on...


I have an even older P3 running the previous LTS (8.04(?)).. but I don't think there is any reason to upgrade that at all.

I like Ubuntu, usually there are initial upgrade issues whenever a new version is released and I typically wait a week or two for the bugs to be ironed out.. didn't do that this time and got bit (~)... mad? no, just not "happy" that it didn't work (upgrade) on the one computer the way it did on the others...and that would be the one computer I REALLY need things to be working on.  I won't kick y'all to the curb over this, honest ;)

---

### Post by phyre-x on 2010-05-06
Worse upgrade I've experienced in ubuntu sing 5.04 and then I had very little experience on ubuntu. Today its supposed to be better but this is woeful (for me). For the first time in ~ 5 years I am considering leaving ubuntu for a different distro. 

Sony Laptop VGN-FW41E, Screen Brightness doesnt work, bluetooth will not add new device or connect to existing ones, gnome-do crashes frequently at start up consuming 100% of both CPU cores, banshee uses 100% of a CPU core while playing tracks, no notification popup appear (volume change, track change) for banshee, start up is SLOWER and ugly compared to 9.10, boot screen process is less smooth, graphics card is incorrectly identified, new icon set looks out of place, new theme is generally poor, banshee task bar icon has non-transparent background, simple compiz config settings are rubbish.

I think there is more but thats all I have observed in the past hour or two since upgrading. Where is the revert button? Karmic was far superior for me and had NO problems on install which I couldn't fix with a simple search of the forums, which I've tried. 

Is it still possible to download 9.10 release ISO? I get the feeling that Ubuntu is no longer the OS of choice. Working on facebook gimicks when the overall OS is lacking quality.

---

### Post by grnorris on 2010-05-06
[http://ubuntuforums.org/showthread.php?p=9236571#post9236571](http://ubuntuforums.org/showthread.php?p=9236571#post9236571)

The link is to a thread I made (I've linked to it a few times) with my upgrade experience and how I fixed the most major issues.  I'm still working on a few things and I'm starting to try some of the new features.  I noticed that KVM wasn't installed by default like I heard it was supposed to be.  I also noticed that a lot of my programs were removed, I'm just about finished reinstalling the ones I really want.  Some of the programs were obsolete but, it also deleted Wine, PlayOnLinux, ATI Proprietary drivers, and many of my games.

On the bright side Thunderbird finally has a 3.0 release in the repository (I installed 3 manually because it was having issues syncing with Windows).

Currently working on some mount and GUI issues.  Think the mount issues might have been resolved by editing fstab and removing my EHDD from it, that's probably a temporary solution though.

---

### Post by robertcoulson on 2010-05-06
When I upgraded to 10.04, I could not boot XP, but a gentleman named BCBC had a fix...It worked perfectly...But still had quirks with 10.04, so I used Gparted to clear a big free space and did a fresh install..Everything works great now.
Robert

---

### Post by marcusjames on 2010-05-06
The big one for me is that mounting the home as /home during an install isn't working. The mess, frustration and trouble that in turn causes is endless. The software simply isnt useable or installable except in a limited set of circumstances. But Linux it ain't'. That is the end of my ubuntu experience. Good bye.

---

### Post by uRock on 2010-05-06
> **marcusjames said:**
> The big one for me is that mounting the home as /home during an install isn't working. The mess, frustration and trouble that in turn causes is endless. The software simply isnt useable or installable except in a limited set of circumstances. But Linux it ain't'. That is the end of my ubuntu experience. Good bye.
Sounds like you had a bad ISO burn, but have fun on your other distro.

---

### Post by thirdspace on 2010-05-06
> **thirdspace said:**
> Fresh install on old (Athlon XP 2000 CPU) PC. Reformat whole drive, autopartition, all defaults. Result: install reported success. On reboot, grub2 loads kernel, kernel cannot find root filesystem, drops into busybox shell. Repeat install, different CDRW media, custom partition (separate /, /home, ext3 not 4). Same result.

Install Karmic on exact same hardware, same options. Result: boots kind of slowly, but once booted, runs fine. Installed all Karmic updates to date, rebooted, still fine. Well actually, there is the small matter that I have to install a hand-crafted xorg.conf to get a reasonable monitor resolution, but that's a story for another day.

Decided to try a different jumper option on the hard drive. karmic boots much faster with the change. installed lucid yet again, now it boots very quickly. Now I want to make it display a grub menu for a few seconds instead of launching instantly into the default OS. How nice they decided we would all help test grub v2 before it is finished! Oh, and now shutdown freezes without powering off the machine (worked OK at first). On my system the bootup sequence is uglier than ever (Savage S3 GPU).

---

### Post by uRock on 2010-05-06
> **thirdspace said:**
> Decided to try a different jumper option on the hard drive. karmic boots much faster with the change. installed lucid yet again, now it boots very quickly. Now I want to make it display a grub menu for a few seconds instead of launching instantly into the default OS. How nice they decided we would all help test grub v2 before it is finished! Oh, and now shutdown freezes without powering off the machine (worked OK at first). On my system the bootup sequence is uglier than ever (Savage S3 GPU).
Grub two was running fine on Karmic.

---

### Post by hagfish on 2010-05-06
Firstly, let me say - *wow* - this release is the best yet. Here's how the upgrade went down for me.

**Background:**
I've been using Linux since Mandrake 9.0. Linux moved from second fiddle to primary OS on my family PC with Dapper Drake. That was on an AMD Athlon 1GHz chip, 512MB of RAM, a 30GB drive, and a Radeon 9000 card. Since then, I have clicked "Distribution upgrade" each time. These days, the system is an AMD X2-4600+, 2GB DDR-400, a mix of SATA and PATA drives, and an nVidia 9600GT. The machine has been a bit of a sandbox over the years, and quite a bit of cruft had built up. Time for a fresh install!

**Things that made it a bit harder for me:**
A mix of SATA and PATA drives - they keep popping up in different places
Decision to go with the AMD-64 bit release. It's 2010 for chrissakes! Adobe - I'm lookin' at you..

**Process:**
I kept my /home partition, and moved /home/me to /home/me-bak so I would get a minty-clean /me directory with the new install. The install went quickly and flawlessly. Formatted the / partition, nominated (but didn't format) the /home partition, and away it went.

On first boot, the graphics card drivers went in. No probs. I tried to run an MP3. As I recall, I was asked if I wanted to install the ubuntu-restricted-extras package. In it went. After a reboot, I had mp3/DVD/foo playback.

Installed Pidgin and Thunderbird. I started copying my stuff across from the /home/me-bak folder. E-mail went into its new ~/.mozilla-thunderbird/<gobblydygook> folder, chat settings and logs went into ~/.purple. No probs. Everything detected, indexed, and good to go.

In went wine, then google-earth, skype, steam. I had to "chmod +x google-earth.bin" - don't remember that from last time.

I showed Rhythmbox where I keep my Music, and reloaded my podcasts and playlists. The playlist file took a bit of finding in my /home/me-bak folder. I was looking under ~/.gnome2/rhythmbox, but it was under ~/.local/share/rhythmbox.

I thought, "better install the printer". I went to the Printer app, and lo - my trusty Brother 2040 was already there - installed, configured, and online. Try doing that in XP!

The SD card from my camera launched F-Spot. Photos imported without a hitch. Picasa picked them up immediately. Result.

[http://www.picnik.com/](http://www.picnik.com/) is working again - yay.

**Problems:**
Because of my mix of PATA and SATA drives, the letters would change from boot to boot. Sometimes, my media drive was at /dev/sda4, sometimes it was /dev/sdc4. In order to have it mount at /media/av every time, I ran "sudo blkid", and used the resulting UUID in /etc/fstab, rather than using "/dev/sda4" and hoping. This should only affect people who are not afraid to pop the side off their case and wrestle with ribbon cable.

My only worry with the 64-bit version was Flash support. It seemed to be going fine (no problems with the Bionicles website!) but Club Penguin wouldn't work. I did the following (from [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407):](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407):)
In a terminal, type "gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer"
Add: export GDK_NATIVE_WINDOWS=1 before the last line of text
That did the trick. That could have been a show-stopper - gotta feed those puffles!

Removing the Evolution envelope icon from the notification area took the volume control slider with it. I added gnome-volume-control to the Startup Items, and the slider is back.

**Conclusion:**
I was in and out of the terminal "cp -ra"-ing and vi-ing happily. I pretty-much either knew what I was doing, or knew what to google. If I had used a single big blank SATA drive (or kept my existing /home/me folder) and used the 32-bit release, I believe I would have had no problems whatsoever. The only gotcha would have been making windows installers executable. It's still not for the faint-hearted, but it's *much* easier and quicker than reinstalling XP - no hardware drivers to track down on dusty old CDs/websites. Fast boot times, perfect stability thus far. Happy camper :)

---

### Post by TimelessRogue on 2010-05-06
[FONT=Comic Sans MS]Interesting ... all these install and boot  problems.  I've installed and been using Lucid as my primary OS on my  64-bit HP Pavilion dv7 laptop since the Lucid beta became available [/FONT](Karmic  and Winlose 7 Ultimate on other partitions as "back-ups").  There were  no problems with installation (including grub) and I have not  encountered any in it's daily use.  Granted I've only been "trialing" it  as a normal "entry level" (entry level for each new upgrade, that is)  user would but have not tried any particularly exotic programs such as  games and such.  But ... everything that would be used by the regular  day-to-day user, including suggested hardware driver upgrades   (particularly the ATI/AMD proprietary FGLRX graphics driver) and  wireless,  just worked "out of the box" so to speak.  Am I not doing  this "trial" thing right?

Yes, there are a couple of things such as Flash that are problematic, but nothing that is absolutely necessary for everyday use ...

That said, I will be installing Lucid on an older 32-bit Dell desktop  later this week and will come back with any problems I encounter ... as  well as any solutions to those problems ... provided I come up with any,  that is ...

And ... I am very much looking forward to beta releases of Maverick when  they become available.  I _really_ get a kick out of hanging out  here at the "edge of the known universe" ...

PS:  Oh, and I almost forgot.  I used both methods of upgrading:  a fresh .iso download install on a new partition and via the "in-line" method of altering my /etc/apt/sources.list to reflect Lucid to replace Karmic on an existing Karmic partition.  Both worked ...

---

### Post by uRock on 2010-05-06
> **TimelessRogue said:**
> [FONT=Comic Sans MS]Interesting ... all these install and boot  problems.  I've installed and been using Lucid as my primary OS on my  64-bit HP Pavilion dv7 laptop since the Lucid beta became available [/FONT](Karmic  and Winlose 7 Ultimate on other partitions as "back-ups").  There were  no problems with installation (including grub) and I have not  encountered any in it's daily use.  Granted I've only been "trialing" it  as a normal "entry level" (entry level for each new upgrade, that is)  user would but have not tried any particularly exotic programs such as  games and such.  But ... everything that would be used by the regular  day-to-day user, including suggested hardware driver upgrades   (particularly the ATI/AMD proprietary FGLRX graphics driver) and  wireless,  just worked "out of the box" so to speak.  Am I not doing  this "trial" thing right?

Yes, there are a couple of things such as Flash that are problematic, but nothing that is absolutely necessary for everyday use ...

That said, I will be installing Lucid on an older 32-bit Dell desktop  later this week and will come back with any problems I encounter ... as  well as any solutions to those problems ... provided I come up with any,  that is ...

And ... I am very much looking forward to beta releases of Maverick when  they become available.  I _really_ get a kick out of hanging out  here at the "edge of the known universe" ...
The Beta install image is different from the final release. Apparently it got worse instead of better.

---

### Post by tjfitz on 2010-05-06
I have a brand new, Toshiba Satellite L505 that came with Windows 7.  I just finished installing Xubuntu from the x64 livecd, and all I get is a page full of hex codes and gibberish (errors?).  It's the same thing that I got when I first booted from the livecd without specifying any boot parameters.  To get the livecd to boot, I hit f6 and selected the first three options (I think they disabled acpi, apic, and lapic).

---

### Post by cabomix on 2010-05-06
I noticed that in all my upgrades from Karmic to Lucid, I had to remove and reinstall Rhythmbox through the new Ubuntu Software Center, to make it work; other wise it crashes upon launch. Iphone connection works out of the box once Rhythmbox is fixed.;)
I LOVE IT!

---

### Post by cato58 on 2010-05-06
I have been using Ubuntu since 7.10.  Never, ever had a problem loading Ubuntu until now.  The upgrades to 10.04 left me in a login loop that I can't resolve.  I reloaded 9.04 and am now using that, but I am finding myself with software that I can no longer update as I am on an outdated system.

This is all very frustrating - I am now looking for other alternatives to Ubuntu.

---

### Post by uRock on 2010-05-06
> **cato58 said:**
> I have been using Ubuntu since 7.10.  Never, ever had a problem loading Ubuntu until now.  The upgrades to 10.04 left me in a login loop that I can't resolve.  I reloaded 9.04 and am now using that, but I am finding myself with software that I can no longer update as I am on an outdated system.

This is all very frustrating - I am now looking for other alternatives to Ubuntu.
Probably should have waited a few more weeks. You can easily install newer software from source.

---

### Post by dBuster on 2010-05-06
I have a fresh install of lucid on a netbook for the wife, however I need to get lucid to behave like my jaunty does in regards to the keyring, no prompting for password!  

Anyone have an idea on how to accomplish this on a netbook version of lucid???

---

### Post by granric on 2010-05-06
Upgrading from Karmic on a HP Pavilion notebook in dual boot w/ Win7: smooth and fast installation, very minor glitches (cups-pdf needed reinstall, as well as flash plugin for mozilla).

++ for the good work done!

rick

---

### Post by johnnyhop on 2010-05-06
First tried an upgrade, it worked after the initial reboot, with one detected bug, no dropdown menu when right clicking on the desktop.  Then went to the Maryland Ubuntu LoCo team release party and upon returning home went to boot up and when attempting to log into KDE got an error message something to the effect of--unable to write to a directory in /tmp.  HMMM Being clueless on how to resolve this opted to do a clean install.  After resolving the many issues with Thunderbird 3.0.4 which made it so nerve racking that I installed Evolution to see if it could import Thunderbird, realizing Kmail wouldn't import T'bird.  Evolution worked well but I was left without the history from Thunderbird.  The issues with Thunderbird were many, messages not showing in the preview plane and dropdown menus without text, the same problems I'd experienced in the Alpha and Beta.  Curiously the full functionally of Thunderbird was restored when swapping the nearly decade old Radeon 7200 display adapter with a more recent Radeon 9550 I'd recently gotten as a hand me down.  Another artifact since the Lucid clean install, a one to two second flash of lime green whenever an application was being opened went away with the display adapter change.

Another comment, I'm grateful for the return of different images on different desktops which I hadn't seen since KDE 3.5 (Hardy--8.04).  Also included with the "Different activity for each desktop" setting is the choice of different icons for each desktop but regardless of which desktop is selected, the "Add to Desktop" selection will only put icons on desktop one.  Dragging the icons from Dolphin to the other desktops is a workaround. =P~

---

### Post by Mattevt on 2010-05-07
I tried to upgrade from 9.10. It seemed to be going well, but when my computer restart I recieved an error message at the login screen...something about usb, I forgot. Then, when I logged in, I had no panels, and I couldn't create one either. I searched the internet for a little while, but none of the solutions worked for me. I made sure everything was backed up and I just did a fresh install (from a torrent)...no complaints from that point.

---

### Post by northwestuntu on 2010-05-07
did a fresh install like always.  install went great and the new system is great!  very very happy with the new version.

thanks ubuntu team :p

---

### Post by ysNoi on 2010-05-07
Did a fresh install...! Everything went fine...! Mabuhay Ubuntu...

---

### Post by cviorel on 2010-05-07
Installation on my ThinkPad T61 worked without any glitches.
Running "**sudo aptitude install smart-notifier**" will crash the X server. Reported the bug ([https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/562456](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/562456)) but no workaround until now.
After installing **thinkfinger-tools**, the fingerprint works, but (in X windows) you need to hit "**Enter**" after doing a scan.
This bug was not present in Karmic.

---

### Post by klemes on 2010-05-07
Clean installation for me went as expected,meaning without major glitches.
I had of course to install some packages after installation for my wireless being able to operate but I consider this not to be  a nuisance at all.
Oh and of course I was affected by the Plymouth bug(plynouth screen not showing at all) but that was easily rectified following the guide in '10.4 known bugs & workarounds' thread.
Other than that no major video card or other incidents ,compiz working out of the box as it should be,but occasionally after the first login I find the window decorations missing which is easily settled by logging in again or reloading the window manager(compiz).
All in all I am very excited about the new release especially after the nightmares I had experienced with the revious release and I am thinking I will be keeping it indefinately,at least that's how I am feeling right now about it.

---

### Post by vajras on 2010-05-07
Initially, all 3 SATA HD's refused to be seen and the install failed until they were all disconnected and i was only able to install on the IDE drive solely (i've tried!).

Additionally, Lucid will not mount either the floppy nor the second DVD drive - it will only see the CD drive & not the DVD either separately or together.

Additionally, my Logitech MS700 randomly has had its buttons reassigned after booting (scroll = size and forward/back = search) however, this could be caused by a conflict with the (newer) Firefox as a reinstall of FF fixes this - i've reinstalled FF twice today and once yesterday.

Additionally, the boot process is now considerably slower.

All in all - and in comparison to v9.10 - this has not been a good experience.

---

### Post by eagle-eye on 2010-05-07
> **eagle-eye said:**
> Go to System, Preferences, Startup Applications

Click on Add

Give it a name

In the command field type **gnome-volume-control-applet**

Job done.

Hmm.  Just did today's updates. After a reboot I had 2 volume applets on the panel.

Removed my one from Startup, rebooted and ended up with no volume applets!

---

### Post by eagle-eye on 2010-05-07
Sorry, scrub that. Operator error.  :biggrin:

---

### Post by arak on 2010-05-07
Was running 8.04 dual xp boot with Virtualbox in lenux and xp also in linux.  Wanted everything to look the same as in 8.04

Problem mounting drives and a USB fix I had installed in 8.04 for VirtualBox.  Went in to fstab and # out the lines for the USB and empty drives.  Booting problem solved.

Problem with panels.  Fixed color and added "indicator" which gave me a volume control.

Problem with audio streaming in Firefox.  Installed Adobe Flash from repository.  Still didn't work.  Uninstalled Adobe and went to Adobe website and installed Flash for 8.04+.deb.  It now works.

Couldn't get skype to work.  Uninstalled Skype and installed later beta version from Skype website.  After turning up mike volume and making sure Skype was on Pulse audio, it worked.
 
Virtualbox--grayed out printer.  Went to users and groups and made sure "lp" was checked.  It worked.

Lost some of my email addresses in Thunderbird.  Fortunately had a file with most of the addresses and those that weren't in my addressbook, I got form my emails which were satisfactorily put in the new Thunderbird.

This is a work in progress and I hope that I have fixed all the problems.

---

### Post by QKC on 2010-05-07
Dear All,
I have just upgrade to 10.04 from 9.10. After the upgrade, the cursor better described as invisible since if I move the mouse around icons will highlight when I believe the "invisible" mouse is over them. I am able to click on them though.Sometime it become invisible again. Attach is some information of my system. Hopefully someone can help me solve the problem 




# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1024 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


Thank you 
JQ

---

### Post by irishbreakfast on 2010-05-07
Did a clean desktop install and worked perfectly. This time I moved from Dual Boot (ubuntu/vista) to Tri-Boot (ubuntu/vista/play are for any another distro). Again, all well.  Thanks to all who contributed!

---

### Post by grnorris on 2010-05-07
> **Irihapeti said:**
> Clean install, one or two minor problems with Grub. If I didn't have all these other OSes on my computer, there'd be no problem at all.

@dazcaz
Another way to upgrade is to get the alternate CD. Put it in your drive and it asks you if you want to upgrade. Much quicker than over the net, and more reliable, I think - no worries about connections going down.

I used the alternate CD's method and I think everything is back up and running properly now.  That's after 3 days of working on it the first stuck completely offline.  Search my threads, I created one about my experience.

Curious, as this was the first time I actually upgraded Ubuntu I used what seemed to be the safest method (other than trying the net upgrade since I'm stuck offline more often than not).  I've seen other's mention installing via the live CD so I'm curious as to whether I could do that without losing my current configuration (aside from truly outdated stuff).

I also think it would be nice if there was a bit more/better documentation on upgrading perhaps with a list of (or a link to a list of) Wireless and Graphics cards that might suffer.  At this point I'm not sure if my wireless card was actually broken or if I just had to delete the old configurations.  (I installed the most recent stable release through a shared ethernet line, then still had to delete the old configurations).

---

### Post by Tom Tiger on 2010-05-07
> **Tom Tiger said:**
> I did the upgrade on 4 machines yesterday.

2 intel boxes (intel GPU and CPU) both worked flawlessly except on both the volume applet is missing

2 intel boxes with Radeon cards (4850 and 2400) on both compiz seized to work, one box (2400) works now with compiz the other (4850) no compiz (yet the driver is active.... desktop effects could not be enabled)

also on these the volume button is missing.

On my 2400 box the volume applet came back when switching the theme to ambiance but not on the other 3 boxes :-)

And it isn't in the add-panel list either....

For the rest, no problems with the upgrade, it went smooth and as fast as one can expect on an upgrade.

Wishlist,

-Volume applet....(or is this an oversight on my part? Help is appreciated)

-New driver for ATI to fix the Compiz problem (Luckily I'm not the only one :-))

- Conversion tool  ext3 to ext4

For the rest.... Kudos and Thanks to Ubuntu. It simply works when I need it. And that is what counts. Furthermore I love the new ambiance theme and the whole OS looks smoother and more professional. 

Would I recommend it?  Oh Yeah, it simply is good :-)

Well.. except for my little compiz snafu... but a solution will come along sooner or later.

Update,  problem with compiz fixed, when I was reading a few docs and forums I found out that my ati radeon 4850 had no longer any 3D support with the new driver.... ouch... (r700 chip has only 2d support, even with fglrx)

So I took the easy way out.... I replaced the 4850 with a Nvidia GT250, all problems solved.  Compiz works now flawlessly, speed of the system seems to be up.

So couldn't wait for a driver :-) Just replaced the hardware.

Only thing left is now my wishlist, a ext3 to ext4 tool thingy (seems to be in the works and there is a workaround)

---

### Post by bilalakhtar on 2010-05-07
Awesome upgrade! This was the first time I did an upgrade, and it was FLAWLESS! Watch out Macrohard Bhindoze, Ubuntu is gonna kick you out of the arena.

---

### Post by Scooter_X on 2010-05-07
Tried installing fresh to my ubuntu partition. I dual boot. Dang that hosed me. The whole grub issue. So, I just hopped off the fence and down onto the ubuntu side of things and now quit running windows. Gotta' find a way to run Steam games (wine runs them, but SLOW) and I'll be a happy camper. But the install itself ran smoooothly when I didn't have to worry about dual booting anymore.

---

### Post by rhyz on 2010-05-07
GOOD:
New look is great,
Boot good,
Right click iso and mount nice :),
(im not sure what else there is?)

BAD:
Buttons on left :/ (although im getting used to it)
NETWORK MANAGER !!! (no wifi as password doesn't seem to be accepted)

Overall good but need wifi fix FAST!!!

Well done on finally changing looks :) and everything else!!!!!

Rhys

PS. problems during install,
Used alternate, Didnt know how to select items to be installed just need some instructions to say: Press space to select and deselect options.

Grub found windows xp i accepted that was all other os' but not there when boot, Easy fix of ```
sudo update-grub
```

---

### Post by nicolastroche on 2010-05-07
I installed ubuntu netbook and it goes well, with some errors in the installation but with problems after it finished. But my computer is near the minimun requeriments and i try to install xubuntu and I get a big problem. It ask me for user and password before starting to install. I try with a lot of combinations, like "ubuntu" for user and pass, only for the user and blank password, and the same options for "xubuntu", "root" and the user I have in netbook, but nothing works. So now, I'm using Windows 7 to write this and try to get an answer to install xubuntu. I see the boot is faster than other versions, and I like it, but if I cant install, what can I do? I check the MD5 and the write and everything is ok, but it just dont work.

---

### Post by verlyn13 on 2010-05-07
The upgrade took forever, screwed up the automatic mounting of my partitions, and gave several errors during installation.  Also screwed up my customized grub2 config.

It did manage to successfully keep most of my custom desktop settings.

With that said, i just did a clean install which went smoothly, except now there is no eth0 option in my network adapters. (writing from jolicloud on netbook)

Overall pretty annoying so far.

---

### Post by jloflin on 2010-05-07
On one machine, Intel dual core, upgraded with no problems.

On the other machine, AMD quad core, I upgraded, but most of my apps disappeared, and I couldn't get away from an ugly, huge pointer. So I did a fresh install, not formatting my home directory, which is on a seperate partition. The install went well. I still had to reinstall a number of apps, which took about 3 hours total, but now everything seems to be fine.

---

### Post by tomdkat on 2010-05-07
I upgraded to 10.04 from 9.10 last Sunday and overall the upgrade went smoothly.

My current issues are:
[list]
[*]Nautilus takes longer than "usual" to start after a cold boot.
[*]The Firefox icon in the GNOME panel disappeared and was replaced with a red circle with a line through it.  I have already resolved this.
[*]When I print to my USB connected Brother HL-2040 laser printer, I can print only ONE page and then subsequent pages don't print until I reboot.
[/list]
Outside of that, everything is working just fine.  :)

Peace...

---

### Post by augusto.sisa on 2010-05-07
Hi.

Last night I upgrade from 8.04 to 10.04 (I prefer LTS releases), almost without problems. Just I get three problems.

1) flashplugin was no upgraded by the software. The problem has no been solved, but it will be easy to reinstall after all.

2) nvidiadriver was no upgraded by the software in a DELL Latitude D630 (I not sure but I think  that it's a Quadro NVS 135M). The problem has no been solved, but I think it will be easy to reinstall after my check if Nvidia has a new driver. However, I could use my laptop with the ubuntu driver.

3) Finally,after all the package installation and try to report the problems showed, I get a fatal error that say me that Ubuntu was in a unusable state (That was true) so I had to reboot my machine with the on/off button.  

After reboot Ubuntu 10.01 works fine for me. I'm checking that right now, but I detect that fan turn on and off more often that ever It just past few seconds on and turn off an so on. 

So I turn off my machine and I'm looking for a reason I think that I will bet a small temperature range for turn on/off the fan but I don't know where to change or if I can change that.

Augusto

---

### Post by adnans on 2010-05-07
Upgraded from 9.10.  Worked great for 2 days.  After rebooting this morning, I was greeted with the blank screen of doom.  After spending a few hours trying to resolve the issue, I'm reinstalling 9.10 as I type this.

---

### Post by taihlo on 2010-05-07
Both upgrades of my 9.04 and 9.10 went smoothly albeit slowly.  The only issue was the immediate need to de-mac the button location (for my own sanity)

:guitar:

---

### Post by Stray Wolf on 2010-05-07
I upgraded first, but misplaced the GRUB.  So, I used my KarmicLiveCD to make LucidLiveCD and installed from it.  I expected to make as many file mods as I had to in Karmic.  Everything has worked out of the box flawlessly!  I'm in awe...

---

### Post by confused_user on 2010-05-07
I upgraded from 9.10 to 10.04 on an advent4213.

as with everyone else, flash player did not get upgraded and i had to install it manually from the flash website.  Not good.

My machine does not sleep or hibernate when closing the lid.  

Cooling fan is on all the time,it never idle's.  flattens the battery really fast.

At least 3 times now the network manager has failed to detect any wifi networks and i have had to reboot the machine.  that never happened on 9.04

Experimenting with the UI was in my opinion counter productive enterprise.

A) there was nothing wrong with it in the first place

B) you must have the option to move the buttons back to the place they have always been.  there is a hack i know but it's a total waste of every bodies time

My netbook takes twice as long to boot as it did with 9.10

the new splash screen is tacky and unattractive, i will now waste more time returning it to the much nicer 9.10 splash, if i can.

Have not got round to checking anything else yet but so far i'm not very happy with it, slow, clunky and tacky looking.

---

### Post by lashram on 2010-05-07
I upgraded from Karmic 9.10 to Lucid 10.04 by using the update-manager -d option and my upgrade went very smoothly. I did not have any issues downloading the needed packages nor any issues with the install. All of my components worked right from the moment I upgraded. My computer was even at the correct or native resolution without installing additional drivers or using hacks. I had to download the proprietory drivers for my modem but that was for the sake of having it installed I rarely or hardly never use my built in modem because I use wireless high speed connection. But everything went great with my upgrade. :guitar:

---

### Post by wm_brant on 2010-05-07
I did a double upgrade today - 9.04 -> 9.10 to -> 10.04.   Everything worked perfectly. 

I was not on 9.10 because I had been affected with the problems with  Network-Manager and DSL in 9.10.  While I eventually got that issue  fixed, I never tried the 9.10 again until today.

Woo-Hoo!!!  :KS:KS:KS:KS:KS

---

### Post by Whizzospace on 2010-05-07
I am just floored at how well this version works. I have never seen a PC boot this fast. Haven't benchmarked, but perception is that Lynx flies! I've used Hardy 8.04 LTS the past couple of years, dual booting with XP, but Lynx has convinced me to dump Microsoft entirely on the desktop.

Clean install with "new" (stock surplus) 2004 vintage hardware:

Intel 875PBZ w/P4 2.4
4 GB RAM
Nvidia 6200 AGP8x 256MB
500GB SATA (my first non-EIDE)

I just pulled my old Win XP files over via USB drive. Video codecs, data file formats, all working as advertised. Even pulled my Outlook pst file into Evolution without a hiccup.

No ripples, just smooth.

---

### Post by Muskegman on 2010-05-07
Hello everyone, I decided to go with the upgrade from update manager, I was a bit apprehensive at first because i have only done clean installs on previous versions of ubuntu and never actually done an upgrade.

Anyway everything went flawlessly, a smooth transition with no problems at all whatsoever. All my apps and settings, even my desktop icons were all there after the upgrade. 

I really have absolutley nothing negative to say at all, everything works perfectly :)

Great job Canonical and ubuntu, I am very impressed \\:D/

---

### Post by texla on 2010-05-07
Really, really like Lucid - It looks great and moves very quickly around the net!  Only troubles  in my install were 
1.  that I had to find out about using OpenDNS in order to get net speed from super slow to super fast.  
2. than after yesterday's updates, I lost all internet access because my user was kicked off of the item "network connection by modem".  I just had to go into Users and Groups and reenable it.  All and all, Lucid has been very cool so far- I like the Broadcast box, too!

Oh yeah, my coming from Karmic Studio was a bit bumpy, too.  I couldn't use the separate Home partition at all, the two kernels weren't jiving I guess.  But I started all over with a new Home and used the forum to find out all about using the older Realtime kernel with Lucid and enabling just what I need for Studio from scratch and so far it looks good - I would love to see a Lucid Studio release though that kicked as much tail as the Karmic one did right from the install!

all and all though, I am crazy about Lucid and thanks a lot to all who made this as great as it is!  :guitar:

---

### Post by inoh on 2010-05-07
been using karmic for a few months a little over six months now.   used lucid live cd on my girlfriends laptop while mine was in shop.  was upset that the lucid live cd was faster than my installed karmic, though i realised this the the latest and greatest.  installed last night after getting my laptop back from bestbuy.  pushing the performance as hard as i can to see if i can cause a freeze/crash like i did in karmic.  so far everything is perfect and noticably faster though i havent tried encoding any videos yet.  only two small annoyances: firefox icon in top panel has been replaced with a red no smoking type of circle; repositories were unresolved first two time i checked for updates.

great job on this release.  everything should work this good. especially if its not open source.

---

### Post by schenier on 2010-05-07
I couldn't wait to get this upgrade and in all I am happy. But when I tried to use VirtualBox, it couldn't see any of the USB devices anymore. It is very important for me to be able to use it for WinXP (unfortunately) and some USB devices (ipod touch). I know that Ubuntu can now see ipod, but I still need iTunes.

What did I do wrong? I have the latest VirtualBox.

---

### Post by Melindrea on 2010-05-07
I **LOVE** Lucid Lynx. I had some issues to get it to install, and now I've spent some time getting all the stuff that I need to install down.

However. I have a Creative SoundBlaster soundcard. I knew when I installed Ubuntu (Hardy Heron) that there would be some issues with getting it to work. Eventually, all my sound died. Today, I have working sound. Out of the box. It works perfectly.

---

### Post by uRock on 2010-05-07
> **schenier said:**
> I couldn't wait to get this upgrade and in all I am happy. But when I tried to use VirtualBox, it couldn't see any of the USB devices anymore. It is very important for me to be able to use it for WinXP (unfortunately) and some USB devices (ipod touch). I know that Ubuntu can now see ipod, but I still need iTunes.

What did I do wrong? I have the latest VirtualBox.

You may want to start a new thread on this, so that the right people see it.

---

### Post by shantiq on 2010-05-07
[COLOR=Blue][B]well it would be excellent but for one thing


[/B][/COLOR][CENTER][COLOR=Blue]** it tells me     **[/COLOR][COLOR=DarkRed]**your window manager does not support the show desktop button, or you are not running a window manager**[/COLOR]


[/CENTER]

[COLOR=Blue][B]

any ideas how to fix that?    thanks in advance     shan[/B][B]


at the moment i cannot minimize or widen my windows[/B][/COLOR]  
[COLOR=Blue][B]
i upgraded from karmic through update manager[/B][/COLOR]

---

### Post by jfleming9232 on 2010-05-07
Just did a fresh install from live cd.  So far, so good.  Just need to add a couple of programs.  Kudos to all involved for a painless way to enjoy UBUNTU!

---

### Post by richardh9936 on 2010-05-07
My upgrade on my Toshiba Tecra A4 worked flawlessly.  

I like the new typefaces and styling in the interface.  I always use xcalib -ia -alter to invert the colours, and I'm very pleased with the results.  Progress bars come out a lovely turquoise.

Richard.

---

### Post by grashdur on 2010-05-07
I was only able to upgrade my laptop to Lucid Lynx (minor problems, all resolved except that display problems prevent switching between accounts--have to log out each time). With my main computer I found it's still not possible to use a USB headset with Skype in the current version of Ubuntu -- since I rely on Skype I had to revert again to Jaunty Jackalope and to Skype version 2.0. 

With Karmic Koala half a year ago I talked a lot on the Forums, and based on suggestions from others I tried 8 different fixes, none of which worked. The problems were identical this time with Lucid Lynx, so I didn't try to work on it any further. 

I haven't found any place to report this bug. I hope it will eventually get fixed. I'd really like to upgrade.

---

### Post by Zanven on 2010-05-07
I am a newer user to Linux and installed from Xubuntu Karmic. It seems to work great. The only thing I didn't like was more cosmetic and convenience related was I didn't like the new Add/Remove programs menu.

---

### Post by ResidentBio on 2010-05-07
I have experience all sorts of problems

First i could not install from an usb. Parted server was looking into my usb key as if i was gonna installed there. Since it encountered some issues with the partition then THE WHOLE installation process stop. 

Well i found a clean cd and installed. Not before dealing with a blank screen, i had to change of dvi port in my 5870 so i could get image. Then installation went smooth

Then upon login i configured my wireless keyboard and mouse mx5500. I seemed to be okay, but today i logged to find out that it freezes at login because of my bluetooth it seenms.

Now, i don't give up easly, but this is too much. A regular user would just stick to others OS. Who wants to find out that suddenly pc stop working from one day to another having dealed with hours of test to fix other issues

---

### Post by munky99999 on 2010-05-07
upgrade karmic to lucid:

-Took a long time.
-I absolutely hate the theme change in moving the minimize-max-exit to the left side. Happy with the colours. Changing back to the original theme busted that also. Set to another to reclaim proper position of said items.

-notification tray items that have transparent backgrounds now appear as white boxes. Annoying.com called they want their bug back. [http://ubuntuforums.org/showthread.php?t=1427968&highlight=notification+tray](http://ubuntuforums.org/showthread.php?t=1427968&highlight=notification+tray)

-Something called akonadi was installed. Dont know what it is. Vaguely remember it from slackware; I uninstalled that. But it's still there in the app menu. Bugged up. Probably just need to login-logout or restart.

-When restarting and what have you. Normally black screens are purple now.


Other then that. Things seem peachy.

---

### Post by flayme on 2010-05-08
Went ok no problems going from karmic to lucid.  took a while but that's ok.  Like the new deep maroonish/purple theme/screen.  Was hoping that the evolution to exchange problem that I had been experiencing would be fixed but no change on that front.  All together - Thumbs up!

---

### Post by RgnKjnVA on 2010-05-08
I've been using Ubuntu since Gutsy so I feel for those having problems with Lucid but personally I have to say that this is by far the best experience I've had with Ubuntu. I'm running two Dells, a Latitude D610 laptop and a Dimension 4500. After a clean install it was the first build where everything (more or less) just worked! 

First I'm impressed with the speed that has been acheived. Boots up very fast, restarts in just under a minute on this old hardware. Applications run very quickly, even GIMP loads quickly. WHAAAAAT? The Nvidia monitor on the Dimension fired right up, no BS with crazy drivers! I got my external audio interface (Tascam US-122) working on the first try. Speaking of audio, it seems PulseAudio has been tamed, I'm able to stream audio from a media player AND stream music videos in Firefox AT THE SAME TIME if I like. Nothing hangs or crashes! DVDs played right out of the box for me. Printer (HP D5100) was found and driver identified without me having to do a thing. I thought I had a serious problem for a couple minutes until I read online that openssh-server isn't installed natively. That was a quick fix and I was retrieving back-up data to easily restore my stuff. Whew! I tried tethering with my Moto Droid and it worked on the first try, no rooting! I love that and it will come in very handy for any upcoming trip my family is taking. Icing on the cake is that I genuinely LIKE the new default UI, it's dark enough to appeal to me but very functional and more mature than previous versions IMO.

The gotchas were few and all but two have been resolved. Amarok was refusing to play mp3s as it typically does after an install but they played fine in Rhythmbox. Once I realized Global Keys control RB and I took the time to learn how to play and store my inet radio playlist in Rhythmbox, I uninstalled Amarok. It's a great player but always a little too high maintenance with python scripts that ran amok. 

Bluetooth; I would love to know how many hours I tried to get this working in previous builds to have to settle for half-assed functionality that sent PulseaAudio into a tailspin when disconnected. At first I was disappointed to see very similar behavior right out of the box with the native Bluetooth Manager Applet unti I installed Blueman which is what had sort of worked for me before. To my amazement BT with Blueman JUST WORKS! I connect to my headset and music just plays, turn them off and the audio goes back to my laptop speakers. I'm also able to move files back and forth between my Droid over BT. I'm getting weepy just thinking about it. How long I suffered to finally savor blissful functionality. I'm sure there's some techie or political reason Blueman isn't installed natively but it needs to be IMO. BT Mgr Applet is like a tease.

One odd issue I'm having is that the Smart Folders in Thunderbird 3 no longer work. I don't see any email listed in them but I still see mail in the individual account folders. Not that big of deal since I'd just started getting used to the Smart Folder configuration but kind of a strange thing. I copied my TBird profile straight from my backup data so I suspect something internal isn't referenced properly or something. Regardless, I don't count this as a serious problem but would like to get Smart Folders working again.

The only big problem that persists is a lack of 1280x1024 support for my laptop despite the max display parameters reported to be larger than that. Despite this, I am finally thrilled with Ubuntu with Lucid.

---

### Post by boublik on 2010-05-08
I tested the beta version from CD to see if it picks up my hardware properly and it did. So I installed it and did some updates later on and all is working just fine.

---

### Post by Edho on 2010-05-08
Did a new install of Lucid on my laptop Asus, 1.5 year old.

Computer becomes very hot.
Switching itself off because overheating, when playing a movie.

Every new boot i had to install the printer again.

I gave up.

Installed now Ubuntu 9.04.(Jaunty)
Works very good.

Update manager says 9.10 available for upgrading?

Is it necessary ?
Is it safe to do that ?


Thank You.

Eddy

---

### Post by Teroc on 2010-05-08
Upgraded from 9.10 without any problems. But then, my graphics are now not working correctly. I can't even play a SD video, firefox is running very slow, boxee is unsupported...
But, my new keyboard  works now, yay !

---

### Post by paydaydaddy on 2010-05-08
I use Kubuntu. I originally had planned to do a clean install just for making the change to ext4. This (older) machine would not boot from the live cd so I decided to upgrade. After the upgrade, upon first boot, I had a brief moment of excitement as it looked as though things were just going to work. The desktop loaded and seemed to have an exceptional clarity. But, alas, all was not well. It was pretty to look at, but while the mouse cursor would track as expected, clicks would produce no response. Keyboard, likewise, was unresponsive. Had to do a hard shutdown with the power button. Tried to reboot and this time had system hang just after Kubuntu splash screen (this was the behavior of the live cd also). Did a hard reboot and this time reverted to an earlier kernel. Booted into the OS and made a few of the usual tweeks (video driver, restricted extras, medibuntu, etc.). Things seem to be working okay at this point. I still have a few things untested, but expect that any minor details can be taken care of. This machine is an AMD XP 2800+ cpu on a Samsung KT880 motherboard(mfg date 2004), SATA hard drive, cheap geforce graphics card, onboard sound, ps2 mouse and keyboard, and 1440 x 900 lcd monitor. I suspect that some part(s) of this system is no longer supported under the latest linux kernel.

---

### Post by mrsray on 2010-05-08
well, I upgraded from ubuntu 9.10 last nite thru the update manager.

all went well except the grub dual boot that I got the fix for here
[http://ubuntuforums.org/showthread.php?p=9259268#post9259268](http://ubuntuforums.org/showthread.php?p=9259268#post9259268)

vista would not start but it was a real easy fix

so far I am pleased with my upgrade, it seems like I'll be enjoying this.

---

### Post by s_raiguel on 2010-05-08
Having learned with Karmic that an "upgrade" can mean a non-working or crippled system, this time I removed my system disk and popped in a spare HD for a fresh install of 64-bit Lucid. The install went smoothly, but it was "back to the future" with several issues that I'd had, and had gotten fixed, with Karmic now rising from the grave to re-appear in Lucid: unreadable menus with black lettering on a dark background; Skype video that doesn't work (nor does my old workaround fix the problem anymore); Firefox that doesn't save passwords, even when the box is checked. All these were were issues before, and now, here they are all over again. Some things just never change. And, now, this new issue: neither IOQuake3 nor OpenArea read their botfiles properly, producing empty areas. All minor issues, to be sure, but enough to make me yank the Lucid disk out and re-insert the Karmic disk and use my old, trusty system until fixes come out. While I appreciate the hard work done by Ubuntu developers, I really think they need to relax their 04/10 release schedule and give themselves the time to get it right, rather than rushing to release a beta two times a year thats more like an alpha-and-a-half.

---

### Post by texla on 2010-05-08
> **shantiq said:**
> [COLOR=Blue][B]well it would be excellent but for one thing


[/B][/COLOR][CENTER][COLOR=Blue]** it tells me     **[/COLOR][COLOR=DarkRed]**your window manager does not support the show desktop button, or you are not running a window manager**[/COLOR]


[/CENTER]

[COLOR=Blue][B]

any ideas how to fix that?    thanks in advance     shan[/B][B]


at the moment i cannot minimize or widen my windows[/B][/COLOR]  
[COLOR=Blue][B]
i upgraded from karmic through update manager[/B][/COLOR]
My problem with this was only solved with a fresh install on a new Home partition - my Karmic Studio Home partition didn't work well with Lucid and caused the same problem you have with the windows.  Don't know if that's the case for you (or if you even have a separate Home partition) and of course you may want to start another thread on this, too - but that's how I solved it.

---

### Post by uRock on 2010-05-08
> **s_raiguel said:**
> Having learned with Karmic that an "upgrade" can mean a non-working or crippled system, this time I removed my system disk and popped in a spare HD for a fresh install of 64-bit Lucid. The install went smoothly, but it was "back to the future" with several issues that I'd had, and had gotten fixed, with Karmic now rising from the grave to re-appear in Lucid: unreadable menus with black lettering on a dark background; Skype video that doesn't work (nor does my old workaround fix the problem anymore); Firefox that doesn't save passwords, even when the box is checked. All these were were issues before, and now, here they are all over again. Some things just never change. And, now, this new issue: neither IOQuake3 nor OpenArea read their botfiles properly, producing empty areas. All minor issues, to be sure, but enough to make me yank the Lucid disk out and re-insert the Karmic disk and use my old, trusty system until fixes come out. While I appreciate the hard work done by Ubuntu developers, I really think they need to relax their 04/10 release schedule and give themselves the time to get it right, rather than rushing to release a beta two times a year thats more like an alpha-and-a-half.
Sounds like you had a bad ISO.

---

### Post by ocram83 on 2010-05-08
I am upgrading on my laptop Dell inspiron 1525 
I am having lots of troubles with audio (as always happened to me so far with this pc... (nut it seems I am the only one...)
I will need help soon...

everything else is gr8!

---

### Post by fluxley on 2010-05-08
hi
totally new to using an os other than windows, installed 9.10 about 3 weeks ago and everything worked perfect, very happy.
trying to upgrade to 10.04 and cant get the internet to stay connected.
though im keen to learn, im not experienced with fixing this sort of thing, so for now im going back to 9.10.
if 10.04 had been my first experience of ubuntu i think i would of just not bothered.

---

### Post by Endolith on 2010-05-08
Looks like this release is [just as bad as all the rest]("http://www.endolith.com/wordpress/2009/06/24/ubuntu-isnt-getting-any-better/").  

I guess I'll wait a few months to upgrade.  I'm sick of the issues I'm having with Karmic, and probably some of them are fixed in Lucid, but it looks like Lucid brings plenty of its own that I'll also be pissed off about.  

I think I'm gonna pay for Windows or OS X with my next computer. I have the money, and Ubuntu has used up all of my patience.

---

### Post by alegallo on 2010-05-08
I voted for a flawless install, and it was it on my PC.

I have a SATA HD with Karmic and XP, and an EIDE one where I installed Lucid.
I studied the matter for a while, and decided to disconnect the SATA one, install Lucid and THEN apply a GRUB update, to avoid all possible problems.

It worked just fine, my Lucid started as a charm and is faster than Karmic in the bootup, which I actually expected.
I made some customisation, installed the nVidia drivers and a couple more things, everything was fine.

Although I did not use it more than a couple of hours, the overall impression is as good as Hardy was, a sound, reliable though friendly distro, a good LTS.

Thumbs up for me ;)

---

### Post by discostoo on 2010-05-08
The installer freezes for me after setting my time zone. Well, it doesn't freeze... it just spins the little "please wait" cursor forever.

I tried messing with various kernel options, etc, but setting things like nomodeset just makes it freeze even earlier, and flash my caps lock and scroll lock buttons.

Hooray for stable releases! I guess it's back to Karmic or Arch (which isn't stable, but at least it installs and boots).

---

### Post by Off Topic on 2010-05-08
Clean install on a Sony Vaio,  flawless.  Couldnt have been easier and it behaves better and faster then the XP install that was on it.

Dual boot on an Acer Aspire netbook.  Had a few hiccups when resizing the Win7 partition but for the most part a smooth install and again better performance then windows.

Reinstalling on Acer desktop right now.

---

### Post by oldspammer on 2010-05-08
I posted in a different thread after I landed there after a Google search of this site...

[http://ubuntuforums.org/showthread.php?p=9263817#post9263817](http://ubuntuforums.org/showthread.php?p=9263817#post9263817) 

I had about 4 problems.

/etc/fstab had a reference to mounting several devices that were not powered up or connected any more, and this forced me to enter 'S' to skip each one, otherwise the system would sit there stupidly and not boot up quickly (or at all?).  For further details see above linked thread.

Warm booting a few times, the Serial MS Intellimouse would not work.  For further details see above linked thread.

Power saver mode for hard disk drives during a warm boot initiated by root via shutdown -h now command caused my BIOS to hang during SATA bus device scan.  So during such a boot, a wake up SATA (or whatever) command should be sent to the sleeping hardware so that the BIOS does not hang during reboot.  See above linked thread.

IP address changes during the upgrade were changed live sometime during the 6 hours of processing, disconnecting my Samba shares unexpectedly, instead of waiting until after the reboot.  The /etc/network/interfaces file was changed unnecessarily, so I had to revert it back to its original version.  For further details see above linked thread.

---

### Post by EliotB on 2010-05-08
I didn't read the 67 pages of replies, this may have already been mentioned.
The poll is missing at least one item "The upgrade had serious problems, but I eventually managed to fix them"

* failed first time (something to do with pam)
* required forcible removal of flashplugin-nonfree
* at end of upgrade, apport wanted to report install problems on many many packages.
* on logout, gdm crashed, requiring hard reboot

---

### Post by I Shooter on 2010-05-08
I have been trying to get 10.04 to install for the past week with no luck. When I put in the type of key board. I get an error message of could not start device/dev/mapper/asr_pictures-nosuch file or directory. I tried an up grade and was asked did I want it to clean up files? I said yes and that was the end of that. It took out some thing that it needed to work because it didn't work after that. I reinstalled 9.04 and that is what I am using now. Any one have any ideas or fixes?

---

### Post by Stevo261 on 2010-05-08
Hi all.

Hope this is the best place to post this as my upgrade from karrmic to Lucid has not gone well. The wizard seemed to run fine, only stopping to confirm a couple of files that would be replaced one showing no changes and another which had a lot of difference and said not changing was the default so I went with that, and opted to keep the original. I know I should have, but I didn't note the file name. When it came time to reboot the system, it hangs at the boot loader, with my screen displaying only the words "Starting up..." This feels familiar, I have had a similar problem before though I don't recall how I fixed it. Guess I will boot a live CD and look at the bootloader i(s it menu.lst?) or something.

Any ideas folks?

---

### Post by uRock on 2010-05-08
> **Stevo261 said:**
> Hi all.

Hope this is the best place to post this as my upgrade from karrmic to Lucid has not gone well. The wizard seemed to run fine, only stopping to confirm a couple of files that would be replaced one showing no changes and another which had a lot of difference and said not changing was the default so I went with that, and opted to keep the original. I know I should have, but I didn't note the file name. When it came time to reboot the system, it hangs at the boot loader, with my screen displaying only the words "Starting up..." This feels familiar, I have had a similar problem before though I don't recall how I fixed it. Guess I will boot a live CD and look at the bootloader i(s it menu.lst?) or something.

Any ideas folks?
You'll probably need to reinstall grub if the grub screen doesn't appear.

---

### Post by Bobby2626 on 2010-05-08
I tried to install versions of 10.04 on three different computers that had previously run Ubuntu successfully, but on all three computers it did not work.  After putting the disc in the screens went blank.  These are all computers with nvidia video cards, which Ubuntu did not provide the right drivers for  On one level I don't feel as though I have any right to complain about a free product, but since Ubuntu makes a lot of claims about how good its software is, I'll complain.  Anyway, Opensuse works well on these computers.

---

### Post by uRock on 2010-05-08
> **Bobby2626 said:**
> I tried to install versions of 10.04 on three different computers that had previously run Ubuntu successfully, but on all three computers it did not work.  After putting the disc in the screens went blank.  These are all computers with nvidia video cards, which Ubuntu did not provide the right drivers for  On one level I don't feel as though I have any right to complain about a free product, but since Ubuntu makes a lot of claims about how good its software is, I'll complain.  Anyway, Opensuse works well on these computers.
Did it cross your mind that you may have had a bad ISO or a bad burn?

---

### Post by dizzykittystudios on 2010-05-09
I attempted to upgrade from the previous Ubuntu (from within Ubuntu's Update Manager).  The way the instructions were written regarding updating the GRUB, it made it sound like it was necessary to update it on all hard drives, which I did.  

Once the upgrade completed, Ubuntu was working, but I was not able to get into Windows XP anymore.  I tried a suggestion which involved I tried a suggestion that I found in the forums of running fixmbr from my Windows XP cd.  That only made things worse.  Now my computer just gives me a blank black screen after the BIOS screen.

I posted in the forums asking for help.  I will post here if I am able to get some help and fix the problem.  However, if I'm not able to get help I may have to reformat and start all over.  In that case, I will definitely never install Ubuntu again (the one up side though is that I'm able to backup my data from a live Ubuntu session--but I had hundreds of gigabytes of music production software that will take a very long time to reinstall).

---

### Post by Concrete Pants on 2010-05-09
I first of all tried to upgrade... this ended badly, there were no window borders and everything overlapped each other, it was terrible!

Fortunately a fresh install fixed this and now it works flawlessly! It is fantastic

---

### Post by dizzykittystudios on 2010-05-09
Just want to mention that bcbc helped me get back into Windows XP by running fixboot from the WinXP cd.

---

### Post by uRock on 2010-05-09
> **dizzykittystudios said:**
> Just want to mention that bcbc helped me get back into Windows XP by running fixboot from the WinXP cd.
.....

---

### Post by AlexanderDGreat on 2010-05-09
> Just want to mention that bcbc helped me get back into Windows XP by running fixboot from the WinXP cd.

..........

---

### Post by Off Topic on 2010-05-09
Only beef Im having is with the dual monitors on my main comp.

---

### Post by jonnykash on 2010-05-09
I was so excited for the new 10.04 LTS release to come out, that as soon as it did, I started upgrading all of my laptops, and completely removed Windows XP from my desktop and started a fresh install of Lucid. The reason I was so excited was because Karmic Koala was such a great release. Everything worked on all my computers the way it was supposed to, so I assumed Lucid would be just as good or better. Well, you know what happens when you assume... The new GRUB took several minutes to load from ext4 on computers that started much more quickly before. A bunch of included drivers got dropped in Lucid, envy-ng no longer works in Lucid, because they switched to the shitty open source drivers by default. The most annoying part though was the now very controversial move of the window buttons to the left side. Yes, I know it's just a change of one line of code to move it back to the right, and there are a bunch of scripts floating around the internet to do it for you, but I felt that Karmic was so perfect and I didn't have to go through as much crap, so I cancelled what upgrades I could cancel and restored them back to Karmic. Sadly my Macbook, which was very nicely set up before had already finished the upgrade, so I had to reinstall Karmic on that and follow all my previous procedures to get the programs I wanted, and I did a fresh install of Karmic on my desktop and have everything working that I want. I'll admit, I'm no Linux guru. I've only been messing with it in my free time for about a year and a half now, but I know a nice, easy to set up operating system when I see it, and Karmic in my opinion is the best. It's too bad that wasn't the LTS. I will keep using Karmic. If I need support, I will Google or look on here for answers; it's what I've always done anyway. I've been trying different Ubuntu distributions since late '08 and I finally found one that impressed me enough to replace every Windows installation in my home, and it happens to be 9.10. Someone once said to me "the thing about Linux is, you have to find a distribution and version that works for you and NEVER upgrade, because they're constantly changing ****". I see what he means now.

---

### Post by Saul.Lima on 2010-05-09
Clean Install works perfectly, but with last updates can't boot Ubuntu 10.04. On my notebook the system stop in the Grub's "bash-like" screen.

I reinstall the system ans all works well. When I upgrade the system again, the same problem return. How can I boot on my system again?

---

### Post by plaidcounty on 2010-05-09
I Quad boot with Snow/Ubuntu/7/XP and installed grub2 to the ubuntu partition. Now all it says when rEFIt loads the partition is "Error Loading Operating System" I can't remember if I had this problem when I installed Karmic but this is really irritating and can't figure out how to get lucid to boot without messing up my Windows boot systems.

---

### Post by Whizzospace on 2010-05-09
> **Whizzospace said:**
> I am just floored at how well this version works.

Spoke too soon, as a glitch appeared. I was losing audio after a couple of minutes, any time I tried Flash streaming video. Changed my Nvidia driver from 'newest' to 'recommended,' reinstalled Flash. No change. Finally I disabled my old AC97 standard analog audio card and ran off the on-board audio. Works fine, except being in mono only.

---

### Post by basilf on 2010-05-09
At first it installed flawlessly, then the upgrade notice to kernel-image-2.6.32-22-generic #%#$%% everything. Why?

---

### Post by nastytales on 2010-05-09
Installed fine, but window icons on the left, but fixed that after digging about, had to turn off screen savers because of lock ups, evolution still had the usual can not empty deleted mail, fixed now, again by digging around. Overall a good release if you really understand how the software works, but still needs some fixes, not for the casual user

---

### Post by Xanthomryr on 2010-05-09
The only thing not working, after the upgrade from 9.10 to 10.04 on my desktop, was that I needed to reenable the desktop effects every time I logged out or rebooted.

[https://bugs.launchpad.net/ubuntu/+bug/563161](https://bugs.launchpad.net/ubuntu/+bug/563161)

The servers in our company upgraded also without problems.

Good work Canonical. :)

---

### Post by theotherotherguy on 2010-05-09
Kbuntu flavored like I like it. I've used, J, and K, Now L. I opted to install from scratch as I made bad decisions about swap when I was a beginning linux user, and the experience has been good.

I'm liking it! I think you did a little better in getting things together on Lucid (not too surprising being an LTS release and all)

Using a dell inspiron e1505 I had to install packages to get my wireless up and running, still having video playback issues, but I believe I should have those resolved shortly. It's performing better than Karmic did, and it looks better! I even tried a live of the original GNOME version and wasn't unimpressed (KDE seems to fit me for some reason though)

All in all, assuming my video woes are as temporary as I believe them to be it's going to be a smooth ride.

EDIT: Issues-schmissues, the AVI I was using to test was corrupt, that'll do it every time... gotta remember to make sure my backups aren't corrupted before relying on them. A clean AVI yielded flawless playback.

---

### Post by innmari on 2010-05-09
I was surprised that it took 2+ hours to upgrade from 9.10, but other than that I felt it was a smooth process. Am running multiple OSes, and had to answer a question regarding Grub when upgrading; the suggested option worked fine :).
Some programs no longer supported (no biggie).
Desktop background picture disappeared (defaulted to grey).
Booting takes m-u-c-h longer than before :confused:. (Dual core working; memory hogged at 1.3 Gb after startup...!!)

---

### Post by guano on 2010-05-09
I did a fresh install of Ubuntu x64 on my new production machine:
Intel i7
12 GB RAM
NVIDIA GTS250 1 GB
HD SATA 1 TB
Monitor 24" LCD/TV Full HD

Everything worked perfectly from start. Really nice! 

This week I will install on a netbook, post results later.

---

### Post by buddha001 on 2010-05-09
Upgraded Kubuntu from 9.10 to Lucid 10.04 LTS. Upgrade completed in under 2 hours, rebooted and most everything just worked out of the box.

Couple annoyances/complaints:

1. All my CPAN installed Perl modules were removed without any good notification, so had so spend some time reinstalling those. Once reinstalled, everything that depended on them worked fine.

2. Amarok crashes with Podcast updates/downloads, per [bug #230932]("https://bugs.kde.org/show_bug.cgi?id=230932"). Hopefully, Kubuntu will upgrade to Amarok 2.3.1 quickly once released.

Cheers to the entire team for the smooth process.

---

### Post by maury on 2010-05-09
I did a clean install and only had one problem. I wanted to change my Screen resolution after Installing the N-vidia driver. I could change the resolution but it would not save the change to the xorg config in the x11 folder so that if I rebooted it would return back to the default highest resolution. I had to fix the problem manually. It isn't an Ubuntu problem per say. It is a glitch in the Updated N-vidia driver.

---

### Post by Ntr0s on 2010-05-09
Upgraded from 9.04 to 10.04 LTS, 64 bit.

I ran into a few problems after upgrading from 9.04:

- bootsplash corruption - could not fix

- grub menu incorrect, could not boot into any OS. - reinstall of grub did not work.

- extremely long boot time - 120+ seconds.

- Clean install, well the problems above did occur with a clean installation, but I was able to get into a functioning desktop before those components failed again.  Also, oening any application also took at least 15-20 seconds, compared to the 2-3 seconds in ubuntu 9.04.

I rolled back to 9.04 64 bit last night.  Rock solid, I love it.

My first attempt at 10.04 was last night, I've only run a couple of searches on solutions.  What I did find was possible incompatibilities with the NVIDIA drivers and the ext4 filesystem.

---

### Post by jerome1232 on 2010-05-09
That really sounds like something just went wrong with your install (other than plymouth and nvidia not getting along)

My boot times were reduced a good amount (switching from ext3 to ext4) and the system feels solid and fast.

---

### Post by erikthedrink on 2010-05-09
I upgraded from 9.10 to 10.04 on Tuesday.  On Thursday morning, I did a shutdown.  On Thursday night, I started up and realized I had no active wired connection.  I tried the usual -- setting and turning off of both the modem and computer.  I do not use a router. No luck yet.

---

### Post by uRock on 2010-05-09
> **erikthedrink said:**
> I upgraded from 9.10 to 10.04 on Tuesday.  On Thursday morning, I did a shutdown.  On Thursday night, I started up and realized I had no active wired connection.  I tried the usual -- setting and turning off of both the modem and computer.  I do not use a router. No luck yet.
Starting a help thread in the Installation & Upgrades sub-forum will get you faster help. When you post there, it would be helpful to include the output of the following terminal command. ```
ifconfig
```

---

### Post by Danjatron on 2010-05-09
I can only access grub since I've upgraded, which I don't really know how to use. If I allow my computer to boot normally, the screen displays only the wallpaper, and I have no access to files, applications or the terminal. If possible, would someone tell me how downgrade back to 9.10?

---

### Post by Will4 on 2010-05-09
I tried a clean install. 
I could only get to see the "Try Ubuntu" Desktop but never got to install the Lucid. I can't go further with installation. Just keeps running for ever at the loading ubuntu screen and after about 1 hour just reboots and runs again another "forever". 
I have tried to install it ACPI=off, TEXT MODE, and so forth. Also tried by going through "Try Ubuntu" and then Alt+F12 to type ubiquity --no-migration-assistant. But NOTHING, NADA, RIAN. 
It is very sad for me as i want to try it. Otherwise i keep working with my Jaunty, very customized and running super well.

---

### Post by ortichi on 2010-05-09
Performed clean install og Lucid 64 bits in a box previously running Hardy 32bits. Formatted drive to ext4.

All went well except a very nasty bug for wireless connection. Main issue is that the connection, previously running @ 10 Mb in Hardy, now can only get 1-2 Mb. Moreover, connection is lost repeatedly and sometimes loading sites is dropped by ANY browser. Tried all the proposed solutions (disabling iPv6, openDNS, etc). Some people are reporting an improvement in this area after latest update, but not in my case. 

Unable to find solution so far.

---

### Post by wavesound on 2010-05-09
> **geodancer said:**
> This is my first upgrade and I did not enjoy it. I have Ubuntu on one HDD and Win7 on another. When I tried to boot the Win7 side, nothing happened. Fortunately, "bcbc" posted a link with instructions to use "testdisk."
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
That solved my problem.
In the poll, I gave the lowest rating for the upgrade even though I seem to have solved my major and perhaps only problem.  I did not enjoy losing one of my systems.

HI
Thought I'd try the upgrade..
Now I'm stuck at the grub rescue prompt!!
I cant even boot my other disk,
I've had to mess with grub before but the rescue thing doesn't seem to accept any commands.
Not impressed at all.

Bob

---

### Post by Kir_B on 2010-05-09
My upgrade went fairly well, with a few exceptions, that I don't think absolute noobies would have known how to deal with.

My first reboot wound up in low graphics mode, which meant that I needed to let Xorg reconfigure it's configuration file. Once that was done and I got to my desktop, I discovered that the upgrade was only partially upgraded. When I fired up the update manager, it told me that I needed to do a partial upgrade, which I then did. It then told me that edubuntu-artwork was causing some problems, resulting in a crash report (I think it told me before the reboot, but I couldn't file the report at that time for some reason), which I then promptly filed. I then went to synaptic to try to remove it, as I really don't need it and don't even know how I ended up having it. I first tried to remove it with no success, then tried to reinstall it, also with no success.???

Next up, was to see if everything I had installed pre-upgrade was still there. Almost everything was still in place with a few very minor exceptions. After finding a few things missing (as I'd expected), I went back to the synaptic to reinstall the missing items, but every time I do an install or uninstall of a package I encounter errors related to the edubuntu-artwork package. I've just tried to uninstall the edubuntu-artwork package again, but to no avail and I just hope they get the fix out soon, as I now know that it's a known bug ([Bug #554585]("https://bugs.launchpad.net/ubuntu/+source/edubuntu-artwork/+bug/554585")).

One of the other issues that I'm facing is every time I log in, I'm given the following message: "Could not apply the stored configuration for monitors. X-server does not support size requested." It doesn't appear to be effecting my currently selected resolution (1280x1024), so it's more of an annoyance than anything else. I'm guessing that this is related to the fact that canonical is trying to push the open source drivers for our nvidia cards on us. 

The other problem I (and others) are having, is that I don't have any boot up splash screen. After doing a bit of research, I've found that this is not at all uncommon amongst those of us using the proprietary drivers for our video cards, as the boot up plymouth splash works fine for people not using the proprietary drivers, or those that are using the nouveu drivers (open source). Hopefully they reverse the decision to use a splash that won't work with the proprietary drivers, as I don't think the first impressions are very good for people thinking about escaping the clutches of the monopolistic windoze O.S.. It's not a very attractive boot up process at this point. I know that there is a fix of some sort, but I'm a little reluctant to do it until I see how it works for people in the long run.

---

### Post by Lia-chan on 2010-05-09
Well, I have tried to install Lucid several times in the same new machine. It has finished the installation, for certains values of "install". And those problems I had experimented in Karmic as well.

The LiveCDs don't boot well, the Alternate Install CD doesn't detect my Ethernet card (a card who is on board, connected, and fully functional), and when the installation ends the after reboot land me in command line, no boot splash. I can login, but not start X. 
And to think I erased my install of Karmic because of the sound issues and I thought that Lucid would have solved them.

---

### Post by InfectionZero on 2010-05-09
Wow, I had so many concerns with updating to 10.04 as I run a dual boot with Win7. Bravo as I had absolutely no issues and the only thing I needed to fix was the wall paper! :guitar:

---

### Post by Rollodog on 2010-05-09
I installed from the cd after the install I could not see the desktop, nothing but black. I reinstalled karnic and did the network upgrade. Everything is fine now. But why no graphical desktop after a fresh install.

---

### Post by JoKeR123 on 2010-05-09
Installed just fine. Worked for a while, but after installing new updates, restarted the computer, and can't turn it back on. Posted thread but can't find it...

---

### Post by IdahoBackwoods on 2010-05-10
Did an upgrade from 64-bit Karmic 9.10 to 64-bit Lucid 10.04, on a Toshiba P305. So far, everything is working fine except for Flash in Mozilla browsers.  For example, YouTube videos don't play.

---

### Post by codyduncan on 2010-05-10
I did a fresh install on an HP Pavilion ZV6000 laptop.  It worked fairly well.  I cannot use suspend or hibernate, I have sound issues with my USB interface, and cannot use advanced desktop effects.

I tried a fresh install on a Toshiba Satellite A15-S157 notebook using the alternate install disc (the Desktop install wouldn't work, as is usually the case with me) which had previously run Hardy with only one (major) problem using WPA encryption on wireless.  After a seemingly successful 10.04 install, the machine simply would not boot into the login.  I would get the Ubuntu splash screen, but then nothing but black.  Next time I tried, I was taken into a disk error checking phase, which detected errors, but when I tried to fix them, it only rechecked, and did nothing except restart upon finding what it had already found.  I figured Hardy ran well enough, so I re-fresh-installed Hardy, and attempted to upgrade from there.  After that, I met the same black screen, so now I am back to Hardy on this machine because it works.  That is what this is about, after all, isn't it?

---

### Post by uRock on 2010-05-10
> **Lia-chan said:**
> Well, I have tried to install Lucid several times in the same new machine. It has finished the installation, for certains values of "install". And those problems I had experimented in Karmic as well.

The LiveCDs don't boot well, the Alternate Install CD doesn't detect my Ethernet card (a card who is on board, connected, and fully functional), and when the installation ends the after reboot land me in command line, no boot splash. I can login, but not start X. 
And to think I erased my install of Karmic because of the sound issues and I thought that Lucid would have solved them.
Sounds like your CD/DVD ROM is fading or the source you used for burning the image is to blame.
> **Rollodog said:**
> I installed from the cd after the install I could not see the desktop, nothing but black. I reinstalled karnic and did the network upgrade. Everything is fine now. But why no graphical desktop after a fresh install.
Same as above?

---

### Post by Stevo261 on 2010-05-10
> **uRock said:**
> You'll probably need to reinstall grub if the grub screen doesn't appear.

Thanks uRock, :guitar:  I'll give it a go. :)

---

### Post by rusty0101 on 2010-05-10
Upgrades through [alt-f2] 'gksudo update-manager -d' worked fine on home workstations.

Install from cd on home workstations OK except for a couple of app issues that are essentially 'still broken and unchanged from earlier versions of ubuntu.'

Two systems that I've run into problems that I consider should never have happened.

First major issue - cd installer.

I have control over one system that is behind a firewall. Apparently the module update-manager calls to do a major version update doesn't understand how to use any of the proxies that are configured for apt or web access.

As a result I ended up having to download and install from a CD image.

When selecting partitions to use and manage, the partition manager apparently properly detects the partition type, and allows you to say that you want to convert a detected ext3 partition to an ext4 partition, and does not 'check' the 'format this partition' box. It then does not warn the user that doing this conversion _will_ format the partition, and verify that this is the course of action you want to take. I would have said _no_ and stated that I wanted the file system to remain as ext3 if I had known that was the expected result. As it was I'm out any not-backed up data from that system. This is not particularly critical in my case, but very much undesired behavior.

This was to be an LTS - LTS upgrade, but since I couldn't 'upgrade' over the net that doesn't matter, it became an LTS install.

Second bad and ongoing experience.

LTS-LTS upgrade.

At home I have a server that I updated via a gui console 'update-manager -d' experience. I have two services that I consider 'critical' running on this platform. Apache and Jabberd. Both 'upgrades' are broken in one way or another when they should not be. 

Some brilliant security dude[tte] decided that mods-available/php5.conf should by default disable php in userdir. Considering that this is where my blog is running from along with several pages that I use pretty much continuously are php pages in my userdir on this server, I have to admit that I am not amused. Personally I suspect this is more of a decision at the Apache level than at the Ubuntu level, but since Ubuntu is where I have experienced the issue, the upgrade gets the blame. 

As to the issue with Jabberd, Apparently there is zero interest in capturing the configuration information from earlier jabberd installations when upgrading to jabberd14. It did not import or capture the domain that was set up for it. As an ongoing issue, s2s is failing with some jabberd servers that were working without any problems under previous releases. I get why google's jabberd server works flawlessly with the jabberd14 stock install once the 'localhost' entries in jabber.xml are all fixed (along with the /etc/default/jabber.xml changes needed to get user's to be able to talk to the server) but with the number of ubuntu users on identi.ca I'm really surprised that messages from [email]updates@identi.ca[/email] through jabber.identi.ca are not getting through to my jabber server. All communications in both directions end up with errors in /var/log/jabberd/error.log that look like:

```

20100510T05:27:13: [notice] (s2s.jabber.beresourceful.net): connected to identi.ca (unencrypted, no cert, auth=db, stream=XMPP1.0, compression=none)
20100510T05:27:54: [notice] (identi.ca): bouncing a packet to update@identi.ca from rusty@jabber.beresourceful.net/baghera: Server connect timeout while sent out dialback request: 174.142.114.111:5269: Connected

```


I suspect that there is somewhere a note stuck to a monitor that says 'to fix this add a 'host' entry like '...' to your jabber.xml file in the <...> </...> section. But I'm not seeing it on ubuntuforums.org, which I find kind of sad.

---

### Post by tipiglen on 2010-05-10
Upgrade left unattended.  Returned to find question about grub modifications and frozen screen.

Hard reset needed.  Then complete failure to boot.  Eventually got a root terminal (on a four step back kernel), and did dpkg --configure -a

Got an apparent completion of upgrade, but with almost instant screen freeze and dead keyboard and touchpad.  Hard reset.

recovery boot and into root terminal.  cannot get update-manager to work - "cannot start display"  ETC ETC ETC.

Saw a warning about runtime java not being installed and that I should delete some openoffice file, but cannot find any <dot>openoffice directory.  Where is it?


Grrrrr!

---

### Post by christhegoth on 2010-05-10
Upgrading from Hardy?  Yup, no problem.  Update manager sorts it no problem.

Installing from a disk as a new install?  Zero success rate on my 2 machines.  It collapses at Casper for disk check as well.

I've downloaded 2 iso versions, and done 2 burns. I got nothing.  It's completely un-usable.

I did get success on a more modern laptop with a friend, so I can only assume it's a driver issue.  Hardy has no trouble on my machines, so it should be easy enough to fix.

---

### Post by Andreab67 on 2010-05-10
Can u help enabling compiz on VMWare Fusion?

See thread below:

[http://ubuntuforums.org/showthread.php?t=1478087](http://ubuntuforums.org/showthread.php?t=1478087)

Thanks

AndreaB67:popcorn:

---

### Post by ashokranade on 2010-05-10
Upgradation for Ubuntu from Karmic Koala to 10.04 went smoothly. My grub page shows window XP but when i do 'enter' a cursor in a blank screen appears and continues. I donot know how to fix this problem

---

### Post by iofanster on 2010-05-10
I upgraded from 9.10. The upgrade process itself was as usually fast & simple. The most interesting began after reboot.))
First, I got a issue when /etc/fstab contained a string for /proc/bus/usb. So I got a screen to fix it manually. But as I had no idea what exactly caused the issue. I had to investigate hard before relaized what I should comment in. 
Second, I got blank screen at both kernels. I checked Xorg.0.log & saw there :(EE) intel(0): [drm] failed to set drm interface version.
(EE) intel(0): Failed to become DRM master.
(II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"
(EE) intel(0): failed to get resources: Bad file descriptor
(EE) intel(0): Kernel modesetting setup failed
(II) UnloadModule: "intel"
(EE) Screen(s) found, but none have a usable configuration.
This made my crazy for a day. I fixed it only removed intel video driver. The point is I got X with no pbs when started it from recovery console at previose trouble!
Now seems it's ok.

---

### Post by Tragos on 2010-05-10
So far I have upgraded three desktop computers from Karmic and one server from Hardy LTS without problems. However, on Asus Eeepc 901 the upgrade from Hardy didn't go so well.

First I couldn't connect to Ethernet or Wi-Fi. Installing a newer (non-LTS) kernel from Mainline PPA fixed this, but Ad-Hoc Wi-Fi connections don't seem to work. On Hardy I have used Ad-Hoc with an Android phone for wireless tethering while travelling.

Also on Hardy I used to shrink /usr directory with SquashFS so the whole installation would fit in a 3GB partition on the 4GB SSD drive. One GB is taken by nLited Windows XP. The 2.6.33 kernel from Mainline doesn't seem to have support for unionfs (or aufs), so I can't add an overlay to the squashed, readonly directory. I'm now forced to keep /usr on the second, slower SSD along with /home. I have tried unionfs-fuse, but couldn't get it to work on boot.

Suspend was not working either. Logs showed this was caused by PulseAudio and unsuccessful release of audio modules. Quick fix was to "chmod -r" the sound related scripts in /usr/lib/pm-utils/sleep.d so they won't run and fail.

There are also some other problems which I haven't been able to solve. Apt-get segfaults often with libc6 error and fsck takes over 20 minutes after an unclean reboot. Netbook-launcher disappears from the screen every now and then, although the process is still running.

I'm still going to give Lucid Lynx one more try and perform a clean install. If I'm still not happy with it, I'm going to install Debian Lenny on the netbook.

---

### Post by Phrea on 2010-05-10
I voted "Install - worked flawlessly".
Did two complete fresh installs on two computers, and apart from some really minor things that are hardly worth mentioning, it all went very very smooth.
Awesome job !

---

### Post by Moriarty123456 on 2010-05-10
Upgrade from 9.10 = Black screen of death

Burned CD = Black screen of death.

Sort it.

---

### Post by uRock on 2010-05-10
> **Moriarty123456 said:**
> Upgrade from 9.10 = Black screen of death

Burned CD = Black screen of death.

Sort it.
Bad CD? Or maybe you need to run the installer in safe graphics mode.

---

### Post by johanbove on 2010-05-10
> **Moriarty123456 said:**
> Upgrade from 9.10 = Black screen of death

Burned CD = Black screen of death.

Sort it.

A bit more information would be nice; can't give much assistance on this.
Did you try burning the CD at a lower speed? That fixed my problem.

---

### Post by wavesound on 2010-05-10
OK
Using super boot disk I managed to get my 64studio to boot.
But not the Lucid upgrade So I can at least get my Data.
I think I'm back with Grub and not Grub 2 though.

I tried to change disks in Bios but get file missing error in grub.
This must be a show stopper for users surely.
Cheers
Bob

Update:
Got it working using super grub disk and then realised I had to select chainload grub2
seems a bit of a mess to me

---

### Post by HarshReality on 2010-05-10
Well, did an upgrade but hate cruft so went back and did a clean install.. everything worked but had to do the work around to get nvidia drivers loaded and now have all 3 screens going.

40G Intel X25V and a 500G Seagate SATA 2 buth split 50/50 for lin/win OS on SSD and programs and user data on SATA. Boot time is 10.07 sec

[IMG]http://only-harshreality.com/postimages/hr-lucid-lucid-20100510-1.png[/IMG]

---

### Post by DogMatix on 2010-05-10
I updated my Acer T180 desktop 'flawless'. Any problematic changes caused by outdated packages, were well documented, and were easy to solve.

I wubi installed my Acer Aspire ZG8 netbook inside XP and this was 'flawless' and has been no problem since.

---

### Post by openBA on 2010-05-10
There is a list of problems of fresh install on Thinkpad R51 with Radeon M 9200 (RV250):
- wrong resolution on dual monitor setup. Display/xrandr resolution change crashes X
- suspend to RAM/Disk is not waking-up
- Firefox/NoScript crashes X
- Firefox/Google Search sometimes crashes X

With the solution proposed here
[https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/545096/comments/5](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/545096/comments/5)
all problems are solved! Only drawback is, that Compiz is not working anymore.

It seems, that open radeon KMS driver is not handling older ATI Radeon cards properly. Switching to older driver helps, but some newer functionalities are then not there.

---

### Post by crackham on 2010-05-10
Upgraded my work box, no issues all good.
Upgraded my laptop, MAJOR problems with older ATI video card, dual monitor setup is broken, wireless connections no longer work.. 
VERY BAD EXPERIENCE..

Oh, not a Linux noob, and this is the worst "upgrade" to an LTS I have ever seen.

---

### Post by tipiglen on 2010-05-10
> Upgraded my laptop, MAJOR problems with older ATI video card, dual monitor setup is broken, wireless connections no longer work..

Sounds familiar.  I can get it (ancient laptop) working by booting into recovery and choosing failsafe (low graphics).

Then I get a perfectly working machine with perfect resolution and working wireless/ethernet....

Thinking of editing grub to opt for recovery as default

---

### Post by Goatrancer on 2010-05-10
I had to post some questions and get help to get my speakers and mic working.
I recently discovered to my horror that the current netbook edition prevents me from adding and removing things from the panel. I guess that doest count as an installation problem though since it appears to have been intentional.

In general it seems nice but I was perfectly happy with my Karmic netbook remix, I had everything working and I could actually edit my panel. I doubt I will use the social mediat integration features of Lucid and I really miss editing my panel, so there wasn't really any reason for me to upgrade. Next time I will be more careful about installing a freshly released version.

---

### Post by cpa_baraboo on 2010-05-10
Upgrade from 9.10 to 10.04.

After all files downloaded and installed, I got a popup during GRUB upgrade to select the device to install to.  I tried my boot partition but it failed.  I was able to go back and try selecting different partitions.  I tried them all and none worked.  I WAS, however, able to select the drive devices /dev/sda and /dev/sdb.  After selecting them the upgrade completed successfully and I was told to reboot.

However, when I usually see a list of kernels to choose from, I only see a black screen.  Apparently the grub update failed and I now have no way to boot the system.

:confused:

---

### Post by de Bacon on 2010-05-10
**The install worked, though with serious problems, no GUI is serious to me**

> 
Actually only one issue. I installed the mini.iso and installed ubuntu-desktop from there. Upon reboot after choosing the kernel could not get the graphics to load. So had to edit and set add "nomodeset" parameter to the kernel and then it booted and had to edit /etc/default/grub the same way so it will always work.

I had the same experience as the quote above.  I consider this a serious issue, being ignorant, were I a little less persistent and desirous of the system I'd have quit.  If I were a little more ignorant, I wouldn't have had the ability to figure it out nor found my way to the fix.  

Thus I would believe a true beginner with an equal hardware set and little computer experience would have been unsuccessful (my opinion).

I was unable to make the upgrade work at all, wouldn't start at all, thus had to reload fresh :(

I am still happy though :) It goes again!

---

### Post by HotPepperMan on 2010-05-10
My experience? Where on earth do I begin. 

I have been a long term user of Linux and this has to be THE single worst experience I have had (and am still having). Looking at the comments in the forums and elsewhere it is clear there is a serious problem with Lucid and dual boot and people are still experiencing it.

Why on earth is there no solution being provided and proposed by Canonical?

I have to use Windows for work and, like many, have a machine that did not come with recovery disks. The many proposed 'solutions' either refer to earlier versions and do not apply, or they contain potentially destructive commands. There are a host of new users who are perhaps investigating Ubnutu for the first time who are going to be left with a machine that will not allow them to return to their primary OS.

This is bad for the Ubuntu community.

Canonical where are you when needed. One would think there was nothing wrong. Indeed there is! How many people have a machine that did not come with recovery disks or, as in my case, are no longer able to access their recovery partition?

I personally am exceedingly annoyed.

---

### Post by Niniel on 2010-05-10
Wow, I'm about to join the ranks of the disgruntled whiners and naysayers... who would have thought...

Ok, let's get it out:

This is the biggest crap ever. The worst Ubuntu of all times. A total and utter disaster. Unworthy of the name "Ubuntu".

There, I did it. 

I took 2 approaches - 1) online update from 9.04 to 9.10 to 10.04. It still worked after 9.10, but for 10.04, the system would freeze at the login screen. Well, not entirely, the clock kept on running. But mouse and keyboard were completely unresponsive. The only way out was a hard reset.
2) I put a live CD on a USB stick with unetbootin and that didn't turn out any better - the system would boot, but once I started to actually click on something, like the Install icon, the system would freeze up again. Every time.

I guess my hardware has become too old for Ubuntu (2.4 GHz Pentium 4 M, Ati Radeon Mobility 9600, Broadcomm WiFi chip...). What a shame.
At least I backed up my 9.04 installation this time. 9.10 had already annoyed me with all-too-frequent system freezes, but not even being able to install the system, that is something new.

Well, maybe something can be done. Fortunately, this wasn't my first experience with Ubuntu. But it looks like I may be stuck at 9.04 forever.

Oh well.

---

### Post by junio_buntu on 2010-05-10
Hi,

I am new to Linux, I was using ubuntu 9.04 & 9.10. Recently I upgraded to 10.04, while doing it I was asked for a **partial upgrade**. I accepted.

And now I am messed up. Its a worst experience.

I cant see mouse pointer (displayed as 'X'). No maximise, minimise & close buttons on windows. Cant maximise any window. When I click on "show desktop button", it says "**Your window manager does not support the show desktop button, or you are  not running a window manager**". Complete display is messed up. 

I sorted it out, by changing the visual effects to "Normal" from "None" in "Appearance preferences". But it is temporary.(plz see the attached for screen shot)

Every time I reboot, I need to do this.

Can some one fix this, and provide me a permanent solution.

Thanks in advance.

---

### Post by epp on 2010-05-10
Due to a video issue, it required a reinstallation of the software.  Rather than install 7.04 and then 8.04 LTS to 10.04 LTS, I downloaded the 10.04 image.  

This turned out to be nothing but trouble.

Some "migration assistant" crashed, rebooted, got a black screen, keyboard didn't work, rebooted again.  Went through the 7 steps, it formatted the hard drive, then the window showing that progress closed.  Video then disappeared a total of four times, displaying nothing but either a black screen or the desktop background image, before it went black again and ultimately displayed the login screen, with no accounts to choose from.

---

### Post by tipiglen on 2010-05-10
Niniel
> 2.4 GHz Pentium 4 M, Ati Radeon Mobility 9600, 
I suspect it's the radeon.  I got the same symptoms - any keypress causes a freeze.

Try recovery boot and choose "failsafe" graphics.  

Works for me, but it's a crap solution

GRRRRR!

---

### Post by bondo101 on 2010-05-10
I installed 9.10 then it asked me if i wanted to upgrade to 10.40 said yes . I love it it is a lot easier than 8.04. there i had to work thru it but now everything is easier and faster . Can't believe its an old parts machine i put a new mobo in with a 2 core amd and a gig of memory. The programs fly un believeable.I used Mandrake years ago but now licid rocks my world alittle more knoweledge and bye bye windows. Thankyou for your time.

---

### Post by ruehara on 2010-05-10
> **HotPepperMan said:**
> My experience? Where on earth do I begin. 



[QUOTE]I have to use Windows for work and, like many, have a machine that did not come with recovery disks. The many proposed 'solutions' either refer to earlier versions and do not apply, or they contain potentially destructive commands. There are a host of new users who are perhaps investigating Ubnutu for the first time who are going to be left with a machine that will not allow them to return to their primary OS.

I also have to use Windows for work and dislike any dual boot "solutions". I'd strongly suggest that you commit your PC to Linux and install Sun's VirtualBox for your Windows apps. This gives you a fully functional Windows (or almost any OS) computer running in a window on your Linux host. Much simpler, much more powerful and much, much more usable. Any Windows apps I need to run are launched in the Windows window and work just like they are running on a dedicated Windows box, while still allowing you to use a fully functional Linux box. It's like having two computers serving one shared screen.

---

### Post by proggy on 2010-05-10
0nly thing i have to say with only 14% upgarde with no problems at all , upgrade needs to be improved

---

### Post by jetsam on 2010-05-10
> **proggy said:**
> 0nly thing i have to say with only 14% upgarde with no problems at all , upgrade needs to be improved

The poll is not a random sampling.  Forum visitors tend to be people that are either regular forumites or people coming here looking for solutions, so it's reasonable to assume that the poll weighs heavily towards people with problems.  

The only general conclusion I've come to is that there seem to be a lot more grub issues this release than any I remember.  Unbootable systems are real trouble for any level of user, and they incline people towards giving up.   

But you're right: there's always stuff to be improved, and flawless upgrades are an ideal to  strive for.

---

### Post by proggy on 2010-05-10
Ubuntu I love ,Grub maybe not so much.

---

### Post by OPENyourmind on 2010-05-10
I am having the same problem since my upgrade. I had to use the on screen keyboard to login. When I checked the keyboard settings it showed I had a keyboard so I am unsure what the problem may be. Please post any suggestions.

---

### Post by raven on 2010-05-10
man !!! where do I start
I used to be surprised when people were not able to install older Ubuntu
as I was all the time successful sometime with some tweaking, but not with lucid 

with lucid, I'm one of them and let me tell you it is frustrating
and I'm an Ubuntu user since hoary

I will explain and maybe somebody can help

2 x500GB sata
using alternate desktop
I want to make my whole system in raid1
I partition as follows
boot=5GB
root=30GB
swap=3GB
home=462GB
on both drives, when I partition I select to use each partition as raid volume
than go to create raid volume and pair each partition to its twin on the other drive
than select  mounting point of each raid device as above, boot flag is on
no errors at all
system continue installing flawlessly

at one point I'm asked to chose if i want to have a raid fail option
[COLOR=Red]1- to start system with degraded raid,
2- halt system when degraded raid[/COLOR]
**[COLOR=Black]I tried both options and none worked,[/COLOR]**

another option to chose is to encrypt home directory and I chose YES

and in the end there is the option to install GRUB
and I see that it is installing on both drives /dev/sda and /dev/sdb

all go with no errors
take out my installation disk. reboot
and system fall on consol1 with initramfs prompt
if I go back to GDM, I see the error 
"there is a serious error with /home"
press F to fix, I to ignore, S to skip mounting,
none of the options fixed anything


anyone having the same issue ???

---

### Post by friendwilder on 2010-05-10
I have an Emachines precharged with XP Home, I created the Linux Live USB Creator, after trying with the Unetbootin USB, both with the UNE Ubuntu. 

The Live session runs well on both (Unetbootin and Linux Live USB Creator), but installing inside the Live Session DOES NOT WORK!!!!

After restarting the netbook, shows the grub, I chose Ubuntu, after that a screen with a cursor in the upper left side blinking.

I have done this three times, I will try installing without being inside the Live Session?

What do you think?

Another guy with same problem?#-o

---

### Post by rajendrag on 2010-05-10
Yesterday I tried to do a fresh install of Ubuntu 10.04 on my fujitsu Siemens Amilo D1845 laptop and it was a failure. In the first trial, the touch pad and mouse were not recognized so I had to reboot. In the second trial, touchpad and mouse was recognized but it was not possible to use keyboard. Therefore, I could not setup an account for installation to proceed. I did another try and the same problems persisted. On the fourth trial keyboard started working and I tried to select a keyboard layout during the setup by typing some letters. I only pressed letter "a" once and it automatically filled all the available space with many "a". Thereafter the computer hang up with no activity. I had no choice but to go back to Ubuntu 9.04 since 9.10 has some problems on my laptop.

---

### Post by uRock on 2010-05-10
> **rajendrag said:**
> Yesterday I tried to do a fresh install of Ubuntu 10.04 on my fujitsu Siemens Amilo D1845 laptop and it was a failure. In the first trial, the touch pad and mouse were not recognized so I had to reboot. In the second trial, touchpad and mouse was recognized but it was not possible to use keyboard. Therefore, I could not setup an account for installation to proceed. I did another try and the same problems persisted. On the fourth trial keyboard started working and I tried to select a keyboard layout during the setup by typing some letters. I only pressed letter "a" once and it automatically filled all the available space with many "a". Thereafter the computer hang up with no activity. I had no choice but to go back to Ubuntu 9.04 since 9.10 has some problems on my laptop.
I hope you will try again in a few months. When I run into problems like you did, I redownload the ISO and burn it slower to make sure I have a good ISO disk.

---

### Post by eaglemob on 2010-05-10
Hi all !!
I had problems with installing ubuntu on a i7 975 cpu with motherboard GA-X58A-UD3R.

The reason why , is because i didn't read the bios section on the manual.
This Bios have a option called "HPET", that means "High Precision Event Timer".

That Bios wen you go on that options and yo choose to "Default=Enable", you expect to get the best from it.
That is wrong !! the "Default* from HPET makes you run at 32 bits.

The bios info and setup about HPET is situated at "PC HEALTH STATUS* , that i found a bad place to be.

Anyway the 2th is the "HPET MODE*. there you need to change to 64 BITS.

My mistakes were. i changed to default .. formated .... installed 64 bits (on a formated 32 bits structure)..wrong

So with this i just want to say.RTFM :)
Windows 7 i still have a problem with the Ati radeon hd 5870 .. somehow doesn't want to give me the score on the scale 1,0 to 7,9  .Amd driver stops.. (well this is not win7 forums :))

P.S .. this is running on I7 975, 12GB DDR3 1600, 2X1 TB (both master) 1 TB WIN7, 1 TB UBT 10.04  . With no problems so far. And no problems with GRUB !! even after updates/upgrades.


Cya all.

---

### Post by CompSciSTL on 2010-05-11
I'm currently trying to upgrade to 10.04, but I'm experiencing a problem.  Currently I am encountering the following error message when trying to upgrade:

"An unresolvable problem occurred while calculating the upgrade:  The package 'ubuntu-desktop' is marked for removal but it is in the removal blacklist."

The message directed me to /var/log/dist-upgrade.  I looked at the apt.log file and I discovered the following at the end of the file:

"Investigating ubuntu-desktop
Package ubuntu-desktop has broken Depends on libsdl1.2debian-pulseaudio
  Considering libsdl1.2debian-pulseaudio 2 as a solution to ubuntu-desktop 0
  Re-Instated libsdl1.2debian-pulseaudio
  Re-Instated ubuntu-desktop
Investigating libsdl1.2debian-alsa
Package libsdl1.2debian-alsa has broken Conflicts on libsdl1.2debian-pulseaudio
  Considering libsdl1.2debian-pulseaudio 2 as a solution to libsdl1.2debian-alsa 10
  Added libsdl1.2debian-pulseaudio to the remove list
  Fixing libsdl1.2debian-alsa via keep of libsdl1.2debian-pulseaudio
Investigating ubuntu-desktop
Package ubuntu-desktop has broken Depends on libsdl1.2debian-pulseaudio
  Considering libsdl1.2debian-pulseaudio 2 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change libsdl1.2debian-pulseaudio"

Could there be some sort of issue with the sound driver(s) which is preventing the upgrade?

---

### Post by kellyhardinguk on 2010-05-11
Upgraded from 9.10 Netbook Remix on my Aspire One ZG5 to Lucid.

All seemed to go ok, except when I log in I get no netbook launcher and no icons at the top and only a xterm coming up (only because it was set in my startup apps).

Otherwise all seems ok, but this problem makes it sadly unusable atm. Will likely do a fresh install shortly once I've prepared a suitable USB stick to recover any files on hdd so I can wipe and start afresh.

---

### Post by sakusa on 2010-05-11
Loved the seamless and painless install experience - looks and works great so far. Well done Ubuntu team!

---

### Post by garethinbendigo on 2010-05-11
Coming from a working Fedora 12 I formatted the entire disk then installed Ubuntu 10.04. After rebooting nothing works period. No menu list, no splash image, nothing other than a limited grub cmd window.
I havent been able to fix my issues.

Gareth

---

### Post by ktechman on 2010-05-11
Did a fresh install after a Karmic partition resize on a Toshiba Satellite A305-S6864 with an ATI graphics card, funny thing though I had in the past fought getting dual monitors and compiz with the proprietary driver this time I used the stock driver and everything worked flawlessly even Open Office presenter view. No problems with plymouth just one aside though grub 2 identified the Vista partition as the recovery partition a simple fix with a name change in the "/etc/grub.d/30_os-prober" file and all is normal but I would hardly call that an issue. I should also say that fresh installs on two P4s and a  AMD K8 and an M3A also went without incident the only disappointment I had was that Brasero Would not burn a disk on the K8 I should get more votes than 1. After trying to upgrade from Gutsy to Hardy I opted for the fresh install.  Windows with all of their millions in revenue can't pull off a flawless upgrade something usually goes wrong. 


Ktechman

---

### Post by taro4cycle on 2010-05-11
I just installed Lucid Lynx yesterday, after building my computer. Ubuntu is so cool. I've had experience with CentOS as well as Gnome/KDE from about 10 years ago, but LL blows everything away.

---

### Post by thegeneftw on 2010-05-11
I am an Ubuntu user for the very first time. There was problems with getting the wireless working that took me some time to figure out. I have an HP dv4 laptop with a broadcom 4312 built in wireless adapter. Using WEP encryption for the wireless security (which I realize is not suggested due to how easy it is to break) caused the wireless to not reconnect automatically after suspend. I resolved the problem, after trying a few help options that I found on support pages without avail, by simply switching to WPA wireless encryption. Other than the wireless problem, my experience so far with Ubuntu has been great! I'm in tech support, so I will be able to actively spread the word about Ubuntu and all its advantages.

---

### Post by Jonners59 on 2010-05-11
> **jetsam said:**
> The poll is not a random sampling.  Forum visitors tend to be people that are either regular forumites or people coming here looking for solutions, so it's reasonable to assume that the poll weighs heavily towards people with problems.  

The only general conclusion I've come to is that there seem to be a lot more grub issues this release than any I remember.  Unbootable systems are real trouble for any level of user, and they incline people towards giving up.   

But you're right: there's always stuff to be improved, and flawless upgrades are an ideal to  strive for.

I would disagree.  It tends to be those that WANT Ubuntu to work for them and are keen, rather than those, normal users that were trying it out and it failed or otherwise, and may well have just walked away or got on with it.

That said, I agree with your target - aim for flawless, even if it may be unattainable.

I have installed on a coupler of machines, so many times and read much of the issues people have had, the issues seem in the main to be linked to just a few critical items.

1. GRUB2
2. Resolution
3. Keyboard and or mouse recognition in build mode
4. Inability to install on multi Hard drive installations, which is probably linked to GRUB2
5. Upgrade - so many, including mine succeeded on install, but then failed after the upgrade... especially 1, 2 & 4.  There is defiantly an issue there.
And the new Security levels, which I can understand, but what I can't is the lack of providing simple device for users to make changes so they can take control of THEIR machine.

As angry and frustrated as I am with this new build, I still believe in Ubuntu....  Just wish there had been more thought about the quality of the 1st launch rather than bowing to pressures to deliver a new product in April, as one of the developers put it to me, who still has his bit incomplete!

---

### Post by HotPepperMan on 2010-05-11
Horrible experience. Totally screwed up my Vista install. It is clear from other posts that installing Lucid on a dual boot machine is not advisable as you will not be able to get your other system back.

Thanks a bunch Canonical for totally failing to provide a timely solution. I have, after many years of using Ubuntu, realised that you have overloaded the system and are clearly not concerned at the debacle which is this release. Despite recognising and 'fixing' what was clearly a major issue Lucid was pushed out. A simple read of the forums and elsewhere will show how many people have been badly affected by the failure of the dev team to issue a product that is stable. Lucid certainly is NOT.

---

### Post by HotPepperMan on 2010-05-11
Well that is an option if you  have sufficient ram. I have already this in the past with mixed results and a variety of stability problems (mainly from Vista). Unfortunately my present installation is now completely screwed thanks to this atrocious release.

---

### Post by Amused2Death on 2010-05-11
I ended up having to blow away the Lucid upgrade and reinstall everything. Sadly this did not fix my problems, especially the one telling me about power management as i login :(

I said in an earlier post i shouldnt bitch about something thats free and that i didnt contribute to, that still holds but i do wonder about developers who fix things that aren't broken.

I refer to things like the moving of the close/max/min buttons, email tied in with messaging. No offense meant, but its starting to feel like bloatware, the very reason i left the Evil Empire.

Well i'm off to find a copy of Karmic, it worked perfectly and thats all i need.

---

### Post by t.h.w. on 2010-05-11
Hi!
I have already posted my experience elsewhere on the forum (follow link: [http://ubuntuforums.org/showthread.php?t=1474394](http://ubuntuforums.org/showthread.php?t=1474394), but this seems a good place to post my experience:

I wanted to make a fresh install, so I used the alternate install-cd, so I could keep my /home folder.

After installing a black screen appeared after the splah screen.
After installing it in nomodeset, I got to the prompt, but wasn't able to start the GUI (X-server).

I gave up, made a fresh install of Karmoc, also using the alternate-cd (when partitioning: keep existing data on /home) and am happy with it.

NOTE: On my netbook, I have upgraded from Karmic to Lucid via the update-manager, and this worked ok!

Greetz!

---

### Post by TheLarch on 2010-05-11
Sorry, I didn't read all the previous posts, but I already did a few google searches and my issues aren't being discussed.

My situation:

Upgrade - worked but had few things to fix, nothing serious though

They aren't serious, but they are major annoyances, nevertheless.

Firefox and Vuze stopped working after the upgrade.

When launching Firefox, I get: Attempting to load the system libmoon 
Segmentation fault

I already tried reinstalling firefox and anything that remotely could have any connection to libmoon, but the problem remains.

As for Vuze, I get: /usr/bin/vuze: Unable to locate swt in /usr/share/java

Again, all my Java libs seem to be installed and in place (I reinstalled a few as well). Does anyone know the name of the package swt should be in?

Thanks to all who can shed some light on these issues.

On the plus side, some audio apps started working when they weren't before (Rhythmbox and Soundbird).

---

### Post by inversecow on 2010-05-11
> **frodon said:**
> 
The purpose of this thread is to share your experience installing/upgrading Lucid Lynx.

Did it work flawlessly ? 
Did you get problems ? 
Did you manage to solve them ? 
if yes how ?
...
...
.

Feel free to post your experience here and think to explain how you solved the problems you got, it might help other users in your case.


0.) Thanks for the new release, aside from a compatibility issue with my graphics sub-system, all is golden.

1.) Did it work flawlessly ?
  -No, I suffered from video issues on my Compaq Presario M2000 after performing a live upgrade (my graphics chipset was blacklisted in KMS in the new release).

2.) Did you get problems ? 
  -Yes, my graphics chipset was blacklisted in KMS, so I would boot, *maybe* see the boot splash (screen with the dots), and then it would hang (blank screen, no "red alert" sounds or the like).
  -This issue has been detailed in [THIS]("http://ubuntuforums.org/showthread.php?t=1468244") thread (some have not been so lucky as I).

3.) Did you manage to solve them ? 
  -Yes, after some stumbling about the internet.

  a.) if yes how ?
    -To the credit of the community & the DEVs, I found a reasonable fix [HERE]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") (executed "Workaround A: Re-enable KMS" from a local Recovery:root console, reboot, no problems).

---

### Post by Electraglider on 2010-05-11
Gateway MT6452 laptop with ATI radeon xpress 200m graphics card and 2GB RAM. Upgrade via update manager went without a hitch although it took quite some time since that method doesn't use the torrents. Upon reboot I recieved the "unable to start usbfs" error as others have reported. Commented the line out of my fstab file and all works flawlessly.

I am now just waiting for improvements to the open source ATI video driver so GoogleEarth will once again work. Otherwise I am extremely pleased with the results.

Thank you Ubuntu team for a job well done. Pay no attention to those having issues with their installs. Whatever their problems is not the fault of Ubuntu.

Except for the early days of Fiesty Fawn, when I first started using Ubuntu, I have not had any more problems than I ever had with Windows.

---

### Post by TCWriter on 2010-05-11
I upgraded both my Dell laptops without a single issue, but my desktop remains a problem. 

Despite an upgrade and several clean installs, my Nvidia equipped desktop is still experiencing random freezes. I messed with the Nvidia video drivers (I believe this is a video-related issue) but the problem remained, and right now I'm running the plane-Jane Nouveau drivers (no desktop effects). 

That may or may not be solving the problem (we'll wait and see), though I've invested a ton of time just getting this far.

I like Lucid, though if I can't get it running consistently, I may install a 9.10 partition while the problem is solved.

---

### Post by mister_playboy on 2010-05-11
I did a clean install of Kubuntu 10.04 and had zero issues with the install.  Currently I'm having some trouble with seg faults in Dolphin and crashes in Opera, but it's nothing too terrible. :popcorn:

---

### Post by cyclemutton on 2010-05-11
> **ggsinclair said:**
> 
[LIST]
[*]CD burner has stopped working properly - cant rip or burn using any software.
[/LIST]


Is there a fix for the CD Burner problem yet? It is rather annoying, and not conducive to mass take up.:mad:

---

### Post by tipiglen on 2010-05-11
I strongly second this arrangement.

> I'd strongly suggest that you commit your PC to Linux and install Sun's VirtualBox for your Windows apps. This gives you a fully functional Windows (or almost any OS) computer running in a window on your Linux host. Much simpler, much more powerful and much, much more usable. Any Windows apps I need to run are launched in the Windows window and work just like they are running on a dedicated Windows box,
You can easily have both systems running simultaneously as I do on an asus netbook with 2Gb RAM.  I suspect that with any less RAM, there may be performance issues, but not for me.

I'm currently running a lucid virtual machine inside a karmic host with absolutely no problems, and on any day I want windoze, I simply boot up an xp virtual machine and use photoshop (the only thing I sometimes want windoze for, because of photomerge)  The windoze virtual machine does thank me for allowing it 9ooMb RAM, while the Lucid is perfectly happy with 512.

You can copy and paste between the host and guest(s), and access/share files, etc.  For this (and general ease of use, you should install the "guest additions" (also free from Sun)

Go for it!

---

### Post by nickmhalliday on 2010-05-11
Hi upgraded from Karmic to Lynx took about an hour or so very straightforward only issue was installing driver for Dell 1450 wireless stuff once i found answer on one of the forums here it took 30 secs to resolve. Loving the fast start up time.

---

### Post by lrcaballero on 2010-05-11
excelent JOB!!! to the Ubuntu team for such a great OS 10.04 LTS.
Thank you!!!!

You guys ROCK~~~:guitar:

Luis

---

### Post by uRock on 2010-05-11
Just installed Warty! It installed flawlessly!

---

### Post by bdw on 2010-05-11
I had upgraded my desktop system from Karmic to Lucid this past weekend and while the upgrade process itself went OK there were a few issues that crept up that were easily resolved

1. New kernel didn't install.  This was because the "frontend" process had hung when the kernel was installed so /boot/grub/menu.lst was not updated

2. I use KDE as my desktop of choice and my panel that is always on the bottom of the screen was removed and I had to readd it and the widgets that I had before

3. Splash screen didn't appear when booting up, and the virtual consoles were dark screens.  I searched the forum and found that the framebuffer needed to be enabled, after doing that I could see the splash screen and the text on the virtual consoles

4.  This was operator error on my part here - I said "yes" to the screen that removed obsolete software and IcePodder wouldn't work as python2.5 was removed.  I reinstalled python2.4 from karmic updates and that was resolved

5. Handbreak 0.9.4 doesn't work with Gnome 2.3 - I installed the snapshot builds from a PPA and that was resolved

Other than that, no show stoppers or other broken apps at this time, I absolutely love the fast start up times and Amarok 2.3! :guitar:

---

### Post by archerba on 2010-05-11
Other than having to do a quick search for the nomodeset graphics workaround for my Dell E1505 laptop, the upgrade from v9.10 was as easy as usual.  Thanks for all the hard work that went into this release.

---

### Post by atr_hugo on 2010-05-11
Sound issue with all browsers - the fixes in the forums have yet to work for me - this was a major catastrophe of an install. Wish'd I'da stuck with 9 (and due to other problems - a HUNG upgrade - that's no longer possible).

---

### Post by xblinker8 on 2010-05-12
Lucid Lynx is cool but I failed to do a clean install of Desktop 10.04 LTS (32-bit) on one of my notebooks (Fujitsu Lifebook S6130) as it's having Intel 855 VGA chipset [symptom: installation screen goes black after the bootflash]. Hoping for fix in upcoming versions, Thks.

If there is any workaround apart from [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
do PM/Guide me. Thks.

---

### Post by zandman on 2010-05-12
Intention was to do an upgrade, but finally it became a complete re-installation. Since there is a back-up of all the old data there's no data loss, it just takes a lot of time to get it all back to where i like it to be. :sad:
Root cause: the kvm-switch and switching to the other connected PC a few times during the upgrade. At the moment i saw the mouse pointer on my screen not move while i was moving the mouse i knew i was in trouble (since it had happened once before....). ](*,)
No way to get the PC to accept input (adding keyboard and mouse, both USB and PS2 type) so the only thing left was to push the reset-button.
Solution: always make sure that next time, before starting an upgrade, there's a keyboard and mouse directly connected to the PC.

---

### Post by xyzt on 2010-05-12
Nah. Tried the CD and though the console ping works, Firefox doesn't connect. I have been having this problem with all my computers and it is *NOT* ipv6 addressing. The last version that worked was 9.04. I overconfidently installed 9.10 as upgrade, just to get a paperweight on my desk and having to downgrade. I'll wait for a release that works.

---

### Post by isoToxin on 2010-05-12
I just upgraded from 9.10 to 10.04 on my old fujitsu laptop.  Well, I say upgraded, I actually just reformatted the / partition and did a fresh install.  I kept all my data in the /home partition though.  This laptop dual boots to XP, so I didn't want to trash everything on the drive and start from scratch.  

It didn't go smoothly at first because of the intel 955 graphics which just goes to a blank screen shortly after boot.  After using the workaround on the wiki, I was up and running pretty quickly.  Everything seems fine, and I like the new GNOME/interface.  Great!

---

### Post by julio_cortez on 2010-05-12
I've first done a distribution upgrade from 9.10 which took more or less 3 hours, to find that I had been locked out the door and I had nothing more than a bash to work with.
I managed to get fglrx removed and reinstalled, and everything went fine from taht moment on except from that issue in which compositing would reset (and disable itself) at any startup.

Thinking it was my fault, I then decided to get rid of it and re-install it straight away, and I managed to get it up and running in something like half an hour or even less, having no trouble at all (apart from that compositing issue that anyway is fglrx's own fault).

Very easy to install to be honest, even doing manual partitioning isn't hard at all. And GRUB recognized and properly listed my W7 partition at startup without a problem.

---

### Post by almufadado on 2010-05-12
I finally decided to upgrade when I discovered that it can be done by the update manager, which was not clear at first.

In my system it took less than the estimated time.

In Portuguese there is an error in the translation, as it say "erro ao descarregar" when no errors were found, according to the log.

EBOX firewall created some errors caused by /tmp/orbit-root directory permissions, solved by allowing other to read/write.

Networks are okay ! 

The dual monitor configuration (extended) with the Nvidia driver seems to have worked better than before in the 9.04 version.

"Places" works better and some mounting problems I had with ntfs partitions and drives seems to have be solved. 

A problem to open the cdrom drive with the drive button still persists. It does not open at first (seems to want to open making the noise) and only opens at the second or third try.

Good job ! Well done Ubuntu !
Congratulations !!

---

### Post by roti_xavier on 2010-05-12
Hmm! :(. I have been using Linux since 8.04. Then migrated to 8.10 & 9.04 from a fresh CD installation. Then updated from 9.04 to 9.10 using the updated manager which took about 23 hours to complete. But this time I'm unable to see 'new update available for download' in the updated manager inspite of running the check/reload about 20 times even with changing the servers.  The other problem I'm facing is the older version of kernel keep showing in the grub boot menu. The list is just increasing with every kernel updated. There about 9-12 options in the updated list. Is there a way to uninstall the older versions of the kernel without ruining my system???

Thank you.

Xavier Francis

---

### Post by uRock on 2010-05-12
> **roti_xavier said:**
> Hmm! :(. I have been using Linux since 8.04. Then migrated to 8.10 & 9.04 from a fresh CD installation. Then updated from 9.04 to 9.10 using the updated manager which took about 23 hours to complete. But this time I'm unable to see 'new update available for download' in the updated manager inspite of running the check/reload about 20 times even with changing the servers.  The other problem I'm facing is the older version of kernel keep showing in the grub boot menu. The list is just increasing with every kernel updated. There about 9-12 options in the updated list. Is there a way to uninstall the older versions of the kernel without ruining my system???

Thank you.

Xavier Francis
Use Synaptic to remove the old kernels.

---

### Post by texpat on 2010-05-12
Upgraded one machine from Jaunty which went smooth as silk. This is a work machine, though, so its a rather lean, streamlined job with not so many programs.

Decided to do a clean install on my 2nd machine after some hiccups with synaptic, slow boot times and so on. Not too surprised, though, since that machine was a bit like a Turkish bazaar. A bazillion programs, residual installs and daemon megaparties being held in the RAM. So far so good, although it sometimes hangs on startup.

I've also got a laptop that's running 9.10, ticking over nicely, so I'm going to leave it alone for now.

So, as far as I'm concerned, ubuntu has been a pretty cool experience.

---

### Post by BlacqWolf on 2010-05-12
i installed desktop on my laptop and then netbook. love them both:P

but in netbook, i installed the same drivers that i did in desktop, and i cannot enable any video effects.

but from the way its grayed out, is it just completely disabled in netbook?

---

### Post by Guitar John on 2010-05-12
Xubuntu 9.10 > Xubuntu 10.04

I was going to do a clean install.  I decided, pretty much on a whim to upgrade instead.  A couple of minor things to fix.  I had to go into Synaptic and re-install the Adobe Adobe Flash Player plugin installer. 

As far as I can see so far, everything works like it should.

---

### Post by sowelie on 2010-05-12
The install worked flawlessly both on my laptop and my desktop.  Lucid is much faster and seems to be much more well put together.  You guys are doing a great job and have come a long way since I first started using Ubuntu.  It is safe to say, gaming aside, Ubuntu is my operating system of choice.

---

### Post by markeet on 2010-05-12
Did the upgrade after a full update manager update to 9.x.   

Update seemed to work fine, accepted the 'delete unused packages?' option, then after the restart I only get a dead black screen.  Hung...   Hard reboot and same thing happens. 

Pretty disappointed.

---

### Post by mrsray on 2010-05-12
> **ashokranade said:**
> Upgradation for Ubuntu from Karmic Koala to 10.04 went smoothly. My grub page shows window XP but when i do 'enter' a cursor in a blank screen appears and continues. I donot know how to fix this problem

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I'm assuming you mean your XP dual boot option on grub

try the sourceforge.net fix, it worked for me with the dual boot problem you have

good luck

> **HotPepperMan said:**
> Horrible experience. Totally screwed up my Vista install. It is clear from other posts that installing Lucid on a dual boot machine is not advisable as you will not be able to get your other system back.


HotPepperMan, did you try the above fix?

I have vista dual boot with lucid and that fix was all I needed.

---

### Post by EamonSloane on 2010-05-12
I did an upgrade to hold me over until I have time to back up my stuff and do a clean install.
It went pretty well.  I mean, I didn't have to perform any arcane rituals to get it to work, so that's good.  I really like the new look.

Really, the only problem I'm having is that my trackpad is now acting very strangely, like the response resolution is distorted.  It's as if the trackpad thinks it's a square, when it is actually a rectangle, so that the cursor moves much faster horizontally than it does vertically, which is really annoying, and I'm not sure why that would happen.

---

### Post by Docaltmed on 2010-05-12
Upgrade was a train wreck. After 10 hours of spinning disk, I called a halt to things. Of course the disk was trash, so I did a fresh install of Lucid which took about 1 hour, then restored the home directory. That made everything go all wanky, so I swapped out for a new home directory and copied data over manually.

Still have key problems: System hangs on shutdown, I have to manually turn it off. Several applications which formerly worked, when re-installed, do not. Printing seems to have taken a big step backwards. Can only print one copy of any file containing images, I have no idea why, but it sucks when I need 40 copies.

Restoring Evolution data gave me the fantods, but I finally got it done.

On the plus side, I can use Firefox again because the fonts aren't all screwed up anymore. Boot time is way faster. I like OOo 3.2 much better.

---

### Post by dondiego2 on 2010-05-12
I did the upgrade from 9.04.  It worked pretty good after fixing a few minor things.  It could be my imagination but 10.04 appears to be much faster than 9.04.  So far I am very happy:)

---

### Post by Kirahvi on 2010-05-12
Clean install and it worked flawlessly !!! I had been using 9.10 karmic before and it worked beautiful too, except that I had to strugle with my ati drivers for a while (yes, I am a noob :D)

I have little experience with other linux distros (Windows user...) but 10.04 is by far the best OS I have ever used (easy and so customizable)

I love Ubuntu but now only I could get my webcam to work with cheese :D:D

---

### Post by amites on 2010-05-12
I got a bit impatient and ran the upgrade on my development machine before testing on another - all the common programs went through just fine

where I've been running into issues with with development specific software such as mysql-server and running firefox -p (for profiles)

WINE no longer crashes pulse audio when launching and a few other things improved

if you are an everyday user then you should be in good shape - developers be ready to lose a couple days to get back to fully functional

---

### Post by chelmite2 on 2010-05-12
I tried both ways: Upgrading and Installing. Both fail. (I have a a Dell Latitude E6500: Intel dual X86-64.)

1. Upgrading from Karmic to Lynx.  It got to the point where I got a pink cosmic screen with some fuzzy white dots and a cursor that I could move around. There's no window manager or panels or login screen. I could use the consoles to log in as root and start up a window manager. However I couldn't get firefox, synaptic, or apt-get to work.

2. I gave up after a week and tried a fresh install. I now get that pink cosmic screen, but no window manager, no panels, no login.
I do have the consoles, but I'm logged in as user ubuntu with my real disks mounted under /target, so I can't get REAL work done.

I am REALLY STUCK and my manager is seriously questioning the whole free software path that I've been advocating.

Any help would be appreciated.

---

### Post by chelmite2 on 2010-05-12
The poll allows me to vote only once, but I tried both Install and Upgrade. Neither works.

---

### Post by chelmite2 on 2010-05-12
User ubuntu's .xsession-errors contains:
(polkit-gnome-authentication-agent-1:16215): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:16215): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** (nm-applet:16213): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:16213): DEBUG: old state indicates that this was not a disconnect 0

(gnome-power-manager:16221): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.0/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0xb77b50'
/usr/bin/compiz (core) - Fatal: Software rendering detected.
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :1.0
Initializing nautilus-gdu extension
evolution-alarm-notify-Message: Setting timeout for 10076 1273708800 1273698724
evolution-alarm-notify-Message:  Wed May 12 17:00:00 2010

evolution-alarm-notify-Message:  Wed May 12 14:12:04 2010

** (update-notifier:16331): DEBUG: Skipping reboot required
ubiquity
ubiquity-dm
Cannot connect to backend, is it busy?
com.ubuntu.DeviceDriver.PermissionDeniedByPolicy: com.ubuntu.DeviceDriver.PermissionDeniedByPolicy: com.ubuntu.devicedriver.info

---

### Post by kevinatkins on 2010-05-12
This has been the greatest release yet...

I have upgraded and installed on a variety of machines, including old desktops and laptops, through to fairly recent multi-core machines and it's been 100% fine.. no problems whatsoever.... Even the alpha / beta releases were pretty solid.. Seriously impressive work..

---

### Post by clauswk on 2010-05-12
Only had one problem upgrading from 9.10 to 10.04: a RAID drive and change of /dev/mapper name, see

[http://ubuntuforums.org/showthread.php?t=1481703](http://ubuntuforums.org/showthread.php?t=1481703)


WUBI works great on my HP workstation

Good job, Ubuntu teams!

Claus

---

### Post by BenJaDov on 2010-05-12
Up front - I am not very conversant with Ubuntu, or Linux. I have many years managing mainframe shops - and now in retirement waste too much time with the 'wee' boxes. It is relevant that one of the multiple 'wee' boxes I have on the floor has more memory - and storage - than the multi-million dollar iron I once herded into doing what the user needed.

Having said all that - - - 

I ran 9.04 and 9.10 with little or no problems. Over time I figured out how to get 9.10 to do most near everything I wanted accomplished on the Ubuntu system. My first attempt to upgrade my 9.10 came a cropper and I discontinued a CD based upgrade when the instructions mentioned an online upgrade - - - The install appeared to go well - reboot did not - it took several tries before I finally confabbled which one of the boot options got me to the upgrade to 10.04 with all the 9.10 options intact.

Being a glutton for abuse - I shut down and removed the removable SATA drive that held the 'operational' 10.04 OS and loaded an available 1TB SATA in the same bay. I then proceeded to do a clean install of Mythbuntu on that drive. Again, the install looked good - the boot is not to be found. I have spent many hours wandering around here trying to find a workable solution - to date none has surfaced.

An early poster conjectured that new to Ubuntu folk would surrender early and leave never to return. I will assure all of you that is a unbearably enticing alternative. However, all those years with operators, and analysts, and programmers, et al has probably addled the memory banks and erased that 'enough of this horse flop - let's go watch the grass grow' alternative.

I am not sure that I would make the transition attempt had I known on the 30th of April what I know now. And there you have it!

---

### Post by daemoncat on 2010-05-12
Install - got many problems that i've not been able to solve.

Actually, it's fatal. I have an ati radeon x700 pro pcie card. Apparently, the x-server for Ubuntu 9.x and above will not support this card.

What is truly annoying is that the live cd test drive works fine. Do an install and it's solid lock up if I try for a gui. >:-( GRRRR!!

What is most annoying and in my opinion unforgivable, is that there is NO disclaimer or warning what-so-ever!! You just install and happily reboot to ... nothing. No warning that some very high-powered and very common video cards will not ever again work with Ubuntu without some pretty messy kludges. I'm so thoroughly disgusted that I'm not even in the least motivated to try them. :-P

Maybe I'll slap on Ubuntu 8.x, or not. I used to think Ubuntu was a real "Linux for the masses". Now, it's Linux if you have the newest hardware. Heck, even Windows 7 works on radeon x700's! WHAT HAPPENED???

---

### Post by dtfinch on 2010-05-12
Built my new computer today. Wanted to have a mirrored raid, but apparently Lucid Lynx is one of those very rare Linux distros with an installer that supports neither mdraid nor dmraid.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/568050](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/568050)

Posting this from the Live CD.

---

### Post by Bluxer on 2010-05-12
Hi, i am quite new here.
i have a problem. I dual booted my windows 7 with Ubunto 10.04 and it  said it successfully installed.
I booted the ubuntu and it freezes on th Ubuntu image with the message( i  didn't copy the message). i rebooted and freezes again on an image  after the Ubuntu Image.So itried recovery mode and it worked. i always  use recovery mode to use ubuntu. Pls help, this is my first time with  ubuntu. thanks...
Sorry for my english.

---

### Post by goatgonads on 2010-05-12
Fix flash native support, you can hardly surf the Internet without it, after that, windows 7 network support. The longer you use linux, the easier it is to forget how hard it is for first time users to fix what may seem like small issues to an experienced user. W7 has been around for 2 years now, yet samba is a &**&^ to print a document to a W7 printer. I would use Ubuntu for my printer server, but it runs my Magicjack, which again... does not work under linux without running a virtual client. I realize that this is not the linux communities wrong doing, but the provider's wrong. None the less, if Windowz is ever going to be beaten, we need to come together to provide solutions. Printer sharing not working for windows 7 out of the box is laughable at best for the linux community, we can do better, it has been in RC for nearly a year.

---

### Post by quequotion on 2010-05-13
> **quequotion said:**
> I have a special case:

1. I've tried upgrading online, but my connection is through a ssh tunnel and there simply isn't any effective means of socksifying the whole upgrade process without breaking something.

2. I've tried upgrading offline, using the alternate CD, but that breaks down and says I have held broken packages, which is not true.

3. The thought of doing a clean install gives me the shakes. I swore after my wretched and disgusting karmic upgrade experience that I would never again format my hard disks for a linux install.

It looks like I'm most of the way there with the offline upgrade, but I can't make any progress unless I can get a list of the conflicting packages... I imagine this is a list of lucid packages that conflict with my massively back-ported, ppa pumped karmic installation.

Is it possible to convince Ubuntu to upgrade *with* third-party repositories?

I'm going to try adding a pin to lucid packages to make sure they can override karmic packages with higher version numbers.Scratch that, I'm doing it the Debian way.

Changed all my sources to Lucid, by hand, and doing```
sudo socksify apt-get dist-upgrade
```

So I'll come back the day after tomorow, when this:```
1871 upgraded, 171 newly installed, 21 downgraded, 17 to remove and 0 not upgraded.
Need to get 1,603MB/1,603MB of archives.
```finishes downloading via my iPhone.

---

### Post by ZeDeun on 2010-05-13
Hi,

Well I think you, developers had made a good job. Upgrade from 9.1 did work fine.
But, I experienced problem with akonadi, loosing my address book !!!! Big issue for me.

I tried to fix it following the wiki (don't remenber where it is but somewhere in kde.org).
It did not solve anyhting. Worse : I am not able any more to lunch kontact, kaddressbook or kamail or korganizer. Really big issue for me.

The funny thing is that I get information saying that I had received some mails, which shows that somehow kmail is working I guess. But it is impossible to open it!

Really disappointing and a bit upset by the situation.

However, I can lunch it from xfce.... so the problem is not (?) o kubuntu side.

---

### Post by theneoindian on 2010-05-13
Upgraded fine ... But now , the Update Manager acts weird .. It aks for a Partial Upgrade and as i see it , tries to upgrade the entire distro once again ... Please help in the following thread : 

[http://ubuntuforums.org/showthread.php?p=9291158](http://ubuntuforums.org/showthread.php?p=9291158)

---

### Post by ansuman on 2010-05-13
Hi,

I am using Ubuntu 9.10 ("Karmic Koala") and I want to upgrade it to Ubuntu 10.04 LTS ("Lucid  Lynx"). I am following the instruction which is written in the web site. But alas! there is no option shown  for upgrading. The screen short is attached with the massage. Please help me.

Thanks

---

### Post by Kulgan on 2010-05-13
Fresh install over Karmic/W7 dual boot on a Dell Studio (1735). Upgrade was close to flawless, only problem being that wireless drivers were initially not available through Jockey. Applying updates and rebooting solved this, however. 

I'm also very impressed with the graphics drivers. They worked out of the box, and with the installation of ubuntu-restricted-extras I was able to play most media without having to fiddle with display settings as I have had to in the past. 

Only downside is that the computer seems to be running at very hight temperatures, meaning more noise from fans. Oddly enough, however, I have noticed no fall in battery performance since this problem started (after installing Karmic). 

As a minor disappointment, I do not agree with the changes which have been made in the theme. However, changing the theme to Dust and putting the window buttons back on the right with gconf-editor gives me a desktop I enjoy using. And I'm very impressed with the wallpapers included in this release!

This was without a doubt the best installation experience I have had with Ubuntu (ie best OS install ever!) since getting to know Ubuntu Hoary.

---

### Post by Xyldor on 2010-05-13
What a disappointment.....again !

Every time I have upgraded Ubuntu there have been items which would not compile/install and other applications which, although previously working, now have problems.
This time the sound system was degraded. The left front speaker in my 5.1 sound system now stutters abominably and I still haven't managed to fix that yet.
Firefox (windows version run under wine) now freezes when used with the websites which need Flash (The whole reason for using the windows version being that the native linux version has a bug which prevents the latest Flash player working)
And during upgrade Fakeroot installation failed resulting in the install aborting before cleaning up after itself.
I also lost the ability to boot into linux and had to manually reinstall grub2.
I still haven't got my windows XP partition back yet.

For those of us who regard the operating system as just a necessary part of a computer system which allows us to run applications, and would rather not spend hours (or days/weeks) tweeking the OS, then this upgrade is very disappointing. I'm sure that it will keep the geeks amused for hours, but if we want Windows users to switch to linux then linux needs to be easy to upgrade.

---

### Post by roti_xavier on 2010-05-13
> **ansuman said:**
> Hi,

I am using Ubuntu 9.10 ("Karmic Koala") and I want to upgrade it to Ubuntu 10.04 LTS ("Lucid  Lynx"). I am following the instruction which is written in the web site. But alas! there is no option shown  for upgrading. The screen short is attached with the massage. Please help me.

Thanks


Hmm! I'm facing the same problem. Can someone help please???

Thank you!
Moved from Windows to Ubuntu. Sort of like Ubuntu now.

---

### Post by garymokha on 2010-05-13
I had wubi before.. when i upgraded from 9.10 to 10.04, it broke the grub.. nd after booting i got the grub rescue prompt..
besides this, there were always some problem or the other in wubi after every upgrade, so i finally decided to chuck wubi and i installed 10.04 on a complete partition.
But the installation wasn't easy, i got stuck at the partition and my laptop hanged when i let the installation setup my partitions automatically, i rebooted and selected the partitions manually.
Now i have a dedicated partition to ubuntu.

Lessons learnt:
1. Do not upgrade without checking the forums for any problems with the new kernel or distribution upgrade.
2. Use a separate partition for your data.
3. Developers NEVER test upgrades on wubi.
4. Ubuntu is free, don't expect it to be hassle/bug-free.

---

### Post by Bigneil on 2010-05-13
My Upgrade has gone badly. Normally i would burn cd then do clean install but, my laptop has no cd/dvd drive and broken USB slots. 

So i decided to upgrade via update manager, To be honest i did expect a few bugs or teething troubles. Howerver, the problem i have is a black screen.   When starting the laptop i get as far as a split second of the Ubuntu splash screen then nothing........ just NOTHING!  

I am not going to let this put me off, i will take out the hard drive and do a clean install on it with an external caddy using my desk top PC.


Oh yea, My laptop is Dell Latitude D400. and i was upgrading from 9.04.

---

### Post by quequotion on 2010-05-13
> **quequotion said:**
> Scratch that, I'm doing it the Debian way.

Changed all my sources to Lucid, by hand, and doing```
sudo socksify apt-get dist-upgrade
```

So I'll come back the day after tomorow, when this:```
1871 upgraded, 171 newly installed, 21 downgraded, 17 to remove and 0 not upgraded.
Need to get 1,603MB/1,603MB of archives.
```finishes downloading via my iPhone.

While I'm still waiting for my download to finish, I had a novel idea... As much as I appreciate the Ubuntu Development Team's enthusiasm for making Ubuntu better, leaner, and meaner every six months... Perhaps we could *delay* the next release? at least until it has been installed and run for a month, **after the release freeze** by a few hundred amateur testers? We could call it the "Aunt Suzie Run" or the "Girlfriend Challenge" and exclusively test the operating system on people who have no idea.

---

### Post by pete_m on 2010-05-13
i'm an EEE PC planning an imminent move to Ubuntu Lucid  ( and Maverick & Debian Sid perhaps? ) . .

i've put some work into my existing  install based on 9.10 karmic  nbr2 and am very happy with the results - full credit and thanks to all

i've uploaded some screenshots. . .[http://www.youtube.com/watch?v=YoI4wRVVjBs](http://www.youtube.com/watch?v=YoI4wRVVjBs)

i'm therefore hoping to be able to upgrade my machine rather than do a  fresh install, tho i have by now got .iso's of my present install and  backups( dumps ) of gconf.

i found this thread . .[http://ubuntuforums.org/showthread.php?t=1461159](http://ubuntuforums.org/showthread.php?t=1461159)
 suggesting  that there may be WIFI problems with Lucid  for   some users. i don't know if these had been fixed before the release . . 
from launchpad .  .[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093)
check out post 53 . .

in any event i suspect i may find some wrinkles on the way

so i've posted a fresh thread [http://ubuntuforums.org/showthread.php?t=1482077](http://ubuntuforums.org/showthread.php?t=1482077) about this process  in case fellow  programmers may be interested & to see if others have experience to  share or guidance to offer . .

looking forward to being able to report on a smooth ugrade when i take the plunge . .

P..S. writing this in EB4 booted from a  USB stck made in 9.10 - all  good tho' couldn't get the stick to function with persistent storage. .

---

### Post by Zimmer on 2010-05-13
Re Printing.
Anyone else NOT seeing CUPS loaded at boot time?

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/554172](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/554172)

Work around..
Start cups service from terminal

> sudo service cups restart

---

### Post by David Ker on 2010-05-13
I've given up on Ubuntu several times but this version has really impressed me. I hoped that I might get everything set up without once using Terminal. I almost made it!

I've now done a dedicated install. Transitioning from WUBI was not painless.

The only major issue I still have is problems with standby/hibernate. I thought a dedicated install would solve that but it still is giving me trouble.

I logged my experiences on my twitter lingamish #ubuntu10

---

### Post by map445 on 2010-05-13
Hello,

I upgraded from Ubuntu 9.10 and everything went well.  It took about three hours (Slow DSL) to download and install.  It takes a bit longer to get started at sign in but, after the desktop is started, my programs start up much faster.  Very happy with the upgrade, thank you and well done, Ubuntu Team.

     Mark

---

### Post by pdlethbridge on 2010-05-13
So far, it has been a problem. I tested the cd and the results were okay, but it kept giving me errors on the install. Something about an unrecoverable error.

---

### Post by Jedah on 2010-05-13
I have recently upgraded to Kubuntu 10.04 Lucid and everything worked as expected, EXCEPT the SFTP support of Konqueror and Dolphin. In all my previous installations (8.04 -> 9.10), if you setup your ssh configuration properly the sftp://somehost/ was working without any further customization. Right now I can connect with ssh without a problem, but Konqueror returns this message:

The requested operation could not be completed
Connection to Server Refused
Details of the Request:
URL: sftp://[user]@[host]:[port]/[path] **These are for reference
Protocol: sftp
Date and Time: Thursday, May 13, 2010 11:28 pm
Additional Information: Failed to resolve hostname = (Name or service not known)
Description:
The server [host] refused to allow this computer to make a connection.

Every other network program has no problem to find the [host]. Anyone stumbled into this?

---

### Post by bayvista on 2010-05-13
Upgraded from Karmic - no problem. However, can only use one user. If I try to switch users, I get the dreaded BSOD. For those unfamiliar with Windows, this means 'black screen of death' and involves a reboot to fix. Seems that Ubuntu is catching Windows bugs!!

---

### Post by Garry_L on 2010-05-13
I have had, & still have, problems.

I am a GUI user.  I can run command-line, but I only know & understand a few commands, so I can only run other commands when I find them on the forum (etc.) or someone tells me what to do.  So, in many ways, I am a newby with Ubuntu, in spite of lots of usage.

I have been using Ubuntu for over 4 years now, usually upgrading a month or so after a new release.  However, since I had an easy upgrade to 9.10 last year, I decided to upgrade ~ 1 week after release (07/05/10).  I downloaded the alternate CD, as I have been able to pass that on to friends with even less download capability than me.

The install went reasonably well.  I did not take the option to include updates at the same time.

I did accept to allow the upgrade tool to delete all suggested files (I don't know what most of them were for, but I was happy to get rid of a lot of old kernels, etc.).  This deletion may have been the reason for my subsequent problems.

When I booted & had problems, I thought that the missing updates would help, so allowed those to be installed (this was later, after I managed to boot using fail-safe).  It didn't solve the problems.  2 are listed below:

1. Now when I boot using the current kernel, I get the following:

When it reaches the login screen, I get either of the following:
. A locked screen with no mouse or keyboard capability.  So I press & hold the start button for 6 seconds to stop the PC.
. The screen is not initially locked, but after I select my user & try to enter my password, It either locks up as above or it keeps looping through saying the user/PW combination is not valid (sometimes filling the PW line with dots).

Once, it worked perfectly!?

So, from then on, I booted using the fail-safe mode.

I now know that I have a 5-year-old ATI graphics card.  However, at one stage during the boot, it said to configure an NVidia graphics driver.  This didn't help.

Hardware Driver didn't help, as it merely comments "No proprietary drivers are in use on this system".

I tried to work out what was wrong with the graphics driver, & soon  realised that it was set up for the wrong card type.

After lots of searching files, I thought fglrx might be the solution, & downloaded that (even though  ATI said that the legacy cards support stopped over 1 year ago).  It didn't help.

I then noticed that there was no /etc/x11/xorg.conf, only backups & failsafe.

So I copied failsafe to xorg.conf, & changed the driver to "radeon".  This didn't help.

I did try the "reconfigure graphics" option that comes up when using  the fail-safe mode.

I think that this latest step may have helped to provide high-resolution graphics, at least.

2. On Tuesday, when I booted (using  the fail-safe mode, I could not get any network connection.  My first thought was that the problem was in the modem (or possibly the separate router).  However, when I checked my other PC (Mythbuntu 9.10), it could access the Internet.

Furthermore, The icon on the top left was for the wireless connection, not the cable connection.  My router has wireless, but my PC doesn't.

I did lots of searching using my other PC, but with no success.

However, when I booted up on Thursday (I needed a break from looking at these problems for 5 days!), the network started properly...

I hate this random/intermittent aspect of problems.

As you can see, the network is also available today.

Anyway, after this morning's change to create /etc/x11/xorg.conf & include fbdev as the device driver, my non-fail-safe mode may work...

Regards, Garry.

---

### Post by apostate on 2010-05-14
OK,

This isn't usually my cup of tea but I'm going to just say some things about 10.4, code-named White Elephant. It sucks. I'm sorry fans, but it isn't good. I've been using *Buntu since around 7.04 I think, and this release is a dog.

Evolution? Broken. Tomcat. Broken. Windows-button layout fiasco adds no value but irritates the hell out of me. Windicators that seem to have consumed the dev teams attention for months and GIVE NO VALUE! They are NOT an improvement over the notification area. I understand the idea was to relieve the "inconsistency" of the notification icons....but WTF? Combining the classic notification icons with the Indicator crapplet just looks worse. And the "features"...wow. Clicking the Rhythmbox icon forces the user to now click the the windicator and choose "Show Rhythmbox" off a menu? Why would I click Rhythmbox for the first time this session if I didn't want to show it? What else would I want it to do? Maybe I want to pick some songs? I hope newbies were able to figure out when they were clicking away on Rhythmbox that it really *was* launching. And I liked being able to hover over the old notification icon and see the track info...but the Apple...erm--I mean Ubuntu team decided I didn't need that feature anyway and removed it. And there is a windicator for the file-transfer window that also has a left-click menu....WITH ONE OPTION! Show the damn dialog. Duh. 

Oh, and try deleting more than one file consecutively by highlighting them and hitting the *Delete* key. Fail. Nobody noticed that? 

Or how about the dialog that allows the user to change the interface preferences of Canonical, to reflect those of the users. They removed it. Thanks.  You know, I happen to think that having the text next to the icons looks more or less...shitty in the vast majority of apps and I liked it the way it was. But of course, there is no interface tweak so minor that Canonical can't obsess over it and then spin it as some sort of "improvement" and then make it next to impossible to change.

And if you are more interested in using this thing to run Enterprise-grade development apps rather than noodling with Indicators, you may be in for a shock. The sqldeveloper-package installer is broken because of an error on one line they still haven't fixed. It depends on a non-existent package. So if you aren't pretty UNIX savvy...no Sqldeveloper for you. The package is useless.  The Tomcat server package is so mangled as to be unusable because somebody just can't seem to leave the file-structure alone, so there go two of my most important use cases for a computer: browsing Oracle databases at work and building Java apps.

But it doesn't matter, because it is agony trying to hit the databases at work anyway now that a change in the driver architecture has rendered Juniper-Network Connect unusable on 10.4 without a crude hack that will break with every kernel update. I know, this isn't Ubuntu's fault-- it's the vendor, yadda yadda. Odd, that excuse never seemed to work for Microsoft. I've spent the last few weeks trying to mitigate all this stuff while telling myself how wonderful Lucid is...but it isn't. I get to fix plenty of broken UNIX machines at work where I get paid for it, the last thing I want to do is have to put 20 hours a week into my "Just Works! (TM)" Ubuntu desktop to keep it from being a total fail. I could install the apps I need from the tarballs and configure them myself. I could search this forum for hacks to get the out-of-box **** to work they way it is supposed to, but that is not what I call a "great" distro. It's just a distro.
 

The best thing about 10.4 is that it somehow, inexplicably, broke by Windows bootloader. Yep. It worked in 9.10...now it doesn't. I don't know why, I don't care. I am downloading OpenSuse 11.2, redoing my Win 7 and then I'm out. This outfit has gotten lost somewhere in the wilderness of UI Facism and color-schemes, and has turned out what may be the purplest...but crappiest Linux distro since Mandriva 2006. 

Sorry. Not drinking the Kool-Aid.

---

### Post by PugTheBlack on 2010-05-14
Got my new Lenovo W510 a few weeks ago and installed Ubuntu 9.10 x64 on it - while waiting for 10.04 to be released, using the wireless backport the setup was painless and the system ran smoothly. 

Updated to 10.04 using update-manager, and the upgrade worked just fine aswell... 

Got some extra RAM and changed HD on the machine and decided to do a fresh install using the Alternate installer, and again the install and setup was smooth. 

Have run into some problems after installing though, especially with my Wireless card disconnecting, and also getting my Juniper Network Connect VPN set up. 

The wireless card does seem to be working a bit better now that I installed the wireless backport on 10.04, and changed from NetworkManager to Wicd, but it still disconnects from time to time... I will look into what someone mentioned in another forum post that a BIOS CPU setting might influence the card, but since Im using the machine for virtualization Im not really happy about switching off virtualization options... 

The Juniper Network Connect problem was solved using  [the Mad Scientist's Guide]("http://mad-scientist.net/juniper.html"), and is now working as it should.

All in all I like this new version of Ubuntu, though it does seem to have some kinks it still needs to work out :-) 

-M-

---

### Post by Thespian on 2010-05-14
So, verdict on 8.04->10.04 upgrade on my laptop, pretty darn sweet.  

One problem I had to search forums for, and not sure which fix worked, because 
after it seemed like none of them did, I found a loose usb connector, 
re-seated it, and it started working.  

 Minor problems and fixes (and some improvements right off the bat) :
 
  Had to re-enter my WPA2 password for wifi.  Once enetered, it worked 
flawlessly, but not sure why it lost that during upgrade.  

  Default colors are darker, but I like them.  Screen seems sharper, may 
be due to upgrade or better configured-by-default video drivers (nvidia).  
Pure UI "look" a slight improvement.  

  My virtual desktops went from my prefered 2x2 arrangement to 4x1.  This 
was easily reset with a click on properties.  

  My volume control widget vanished from my dock at the top of the screen. 
 One click and drag from the system pull down, and it was back in place.  

  Openvpn / sound / printing (over wireless) and virtualbox all worked as 
before, with no weirdnesses.  
 
I needed to re- apt-get "miro" (formerly the "democracy" video plyer) though   
all my subscriptions were intact, as well as mydownloaded videos.  again, not sure why it vanished.
 
Biggest, and only "real" problem was with aumounting of my USB 1TB Western Digital "MyBook" drive.  In  Hardy, just plugging it in had the "hal" subsystem automount it, and the 3    
partitions on it, two ext3 and one NTFS.  Tried it after the uprade, and      
nothing.  Disk powered on, saw a message in /var/log/messages but nothing in   
/dev and nothing in /media.  Tried a bunch of solutions other folks posted on 
the ubntu forums, with no luck.  Tried booting in to windows, and windows     
couldn't recognize the disk!  Freaked out a bit, then noticed the micro USB   
plug on the back of the drive was loose.  In enough to power it up when       
plugged in, but loose enough to cause problems.  Fixed that, and windows was  
fine with the NTFS volume.  Went back in to Ubuntu, and all disks now             
automounted, so I don't know which of the earlier fixes I tried actually fixed the     
problem, or if I just had the same sympotm as othrs, caused by a loose usb    
cable.
 
Once resolved, the only other minor nit was that in Hardy, the ext3 file      
systems on that USB disk were always mounted as /media/disk and /media/disk-1 
and now they were being mounted as /media/<ugly hex string UUID>
 
Was able to fix that just by giving them both a lable.  They now mount as     
/media/<lable> just like the NTFS one does.
 
On the plus side, the system seems faster, the newer versions of thunderbird  
and firefox are nice (yeah, I know I don't need an OS upgrade for that) and   
the one bit of pleasing new functionality is that the SD card reader on my    
laptop (HP Compaq 8710p) is now natively supported, which never worked under Hardy no matter what I tried.
 
So all in all, pretty painless for a two year and 2 major revision jump in    
technology for an "upgrade" rather than  fresh install.  Good job on the LTS->LTS upgrade folks.

Thespian

---

### Post by Silvertones on 2010-05-14
I did an upgrade from the Alt CD. A perfectly great running Karmic is now a BSOD. I totally removed it and am back to Windows. This is totally unacceptable.

---

### Post by uncle_meatloaf on 2010-05-14
I was happily using Ubuntu 9.10 when my update manager informed me that 10.04 was available. 
Since the ugrades from 8.04->9.04->9.10 went well, I decided to upgrade to 10.04.
At this point, I feel like I've made a BIG mistake.
Although the upgrade appears to have worked, and I've received 2 sets of updates since the install, I still have a few unresolved problems with 10.04 that were not there in 9.10.

[LIST=1]
[*]My background picture "hides" my attached USB sticks, until I hover over them with the cursor. (Minor Inconvenience)
[*]The window manager keeps crashing, leaving me with open apps that I am unable to open/close/move/resize or move front/back. Logout/Login only workaround at this time. (Major Problem #1, and the reason I joined this forum)
[*]OpenOffice spreadsheet app, which I use constantly, shows corrupted characters, slow re-calcs for new input data, and blotchy blocks of screen garbage when manipulating comments. I does not appear to be corrupting the actual data, because flipping between sheets helps to clear up the screen corruption. I believe it may be related to, and symptomatic of, problem "2." , above. (Major Problem #2)
[/LIST]
Additional Info: After the window manager crashes, and I've closed/quit apps from their "File" menus, they still appear in the task bar, and the "busy" cursor (spinning-dots-in-a-circle thingy) is running when hovering over my background picture.

If these problems cannot be resolved, then I need to know if I can re-install 9.10 over 10.04, without losing the files in my home directory. As things are, 10.04 is not stable enough for me to continue using it on a regular basis.

---

### Post by jetsam on 2010-05-14
> **uncle_meatloaf said:**
> I was happily using Ubuntu 9.10 when my update manager informed me that 10.04 was available. 
Since the ugrades from 8.04->9.04->9.10 went well, I decided to upgrade to 10.04.
At this point, I feel like I've made a BIG mistake.
Although the upgrade appears to have worked, and I've received 2 sets of updates since the install, I still have a few unresolved problems with 10.04 that were not there in 9.10.

[LIST=1]
[*]My background picture "hides" my attached USB sticks, until I hover over them with the cursor. (Minor Inconvenience)
[*]The window manager keeps crashing, leaving me with open apps that I am unable to open/close/move/resize or move front/back. Logout/Login only workaround at this time. (Major Problem #1, and the reason I joined this forum)
[*]OpenOffice spreadsheet app, which I use constantly, shows corrupted characters, slow re-calcs for new input data, and blotchy blocks of screen garbage when manipulating comments. I does not appear to be corrupting the actual data, because flipping between sheets helps to clear up the screen corruption. I believe it may be related to, and symptomatic of, problem "2." , above. (Major Problem #2)
[/LIST]
Additional Info: After the window manager crashes, and I've closed/quit apps from their "File" menus, they still appear in the task bar, and the "busy" cursor (spinning-dots-in-a-circle thingy) is running when hovering over my background picture.

If these problems cannot be resolved, then I need to know if I can re-install 9.10 over 10.04, without losing the files in my home directory. As things are, 10.04 is not stable enough for me to continue using it on a regular basis.

Most problems can be resolved given much time and patience and a steady backup plan.  

I'd suggest you consider doing the downgrade to save yourself grief, and maybe start by reposting your post in Installation and Upgrades or General Help for help doing the downgrade safely.

---

### Post by alienprdkt on 2010-05-14
Boy has Ubuntu came along way since I first worked with it in Ubuntu 7.04 (Feisty Fawn) release.

Love the new look and feel, despite the problem I had with grub2 during the upgrade from Karmic to Lynx. But it was an easy chroot from Live cd and grub-install fix.

Do wish that some minor things get fixed me and alot of people I have noticed have had issues (I had them in Karmic as well) with fstab not mounting all drives, but when you run mount -a after booting it mounts them, when this just reads fstab and does what should have been done in the boot procedure. Well this mount -a worked to get one of my addition drives to mount. The others I had to use the mount -t (followed by the same thing that mounted one of my drives in fstab) and write these mounts to a custom script to kick off during the boot process and a umount to run during shutdown.

I hope that Ubunutu isn't going to remove certain necessaries just to speed up some boot processes. This will result in a lot of users going elsewhere I am sure. I really like Ubuntu has been my favorite Linux distro for a few years now, please don't start messing up now. 

Other then these few minor problems (hope it stays at a minor) Love the new version, Fast & Stable! Uses less resources when idling and under stress. Keep up the good work!

---

### Post by BudT on 2010-05-14
Just installed 10.04 LTS on my Gateway M275 laptop. I had to follow this advice to get the live CD to boot: 

[http://ubuntuforums.org/showthread.php?p=9239795#post9239795](http://ubuntuforums.org/showthread.php?p=9239795#post9239795)

but once booted I was able to install no worries. This laptop is a tablet, but I have no need for the tablet functionality so I don't think I'll pursue the drivers for that. Everything else appears to be working fine at this point.

Bud

---

### Post by jstalnak on 2010-05-14
Upgrade worked very well on my HP Dv4 1222nr laptop!! Only issue was getting the grub upgrade done -- for some reason the dialog box for selecting which partition to put grub on would not accept a click via mouse cursor. I had to use the keyboard (tab, space bar) to navigate the dialog box successfully. Once that was done, I was fine after removing the /proc/bus/usb entry in /etc/fstab.  Wish my desktop had been this easy.

---

### Post by witeshark17 on 2010-05-14
Edit: On a Dell Insiron which had 9.04 from the factory.
Installed by Update Manager today. Went flawlessly! Download speed was around 290 kb/s and the installation was extremely smooth! :KS

---

### Post by urugTON on 2010-05-14
Installed 10.04 today.  Took about 3 hours with CD download, burn and so on.  Biggest amount of time was spent with updating software after 10.04 was installed.

I had a few problems finding things, but no worse than with any release since 9.04.  (Yes I'm still slow at closing a window.  The "X" seems to be in the wrong spot :P).

I have a Dell D610 - an older laptop - 512MB memory, 20GB hard drive.  Graphics is Intel 915GM.  Wireless is Intel PRO/Wireless 2200BG.  Everything came up without a problem.

I did a fresh install because I don't trust upgrades.  There were no problems.  

I'm dual booting with 9.10.  That's my plan B, but plan A seems to be working fine.  

I do not feel any performance boost over 9.10, if anything it might be more sluggish.  OTOH, this is not a very powerful machine and has a really old (circa 2000) hard drive.  I will note that I'm seeing more use of swap than I have seen on either of the two earlier releases on this machine.  Right now I'm using 55% of my 512MB.  There's 120 MB of swap allocated.  I don't remember seeing any swap allocated before today.

About all I do on this machine is surf the web, occasionally read documents and write a few simple documents.  For what I'm doing, the performance is just fine.  FWIW, this machine originally had XP.  The Ubuntu upgrade was an incredible performance boost. 

Everything seems to work.  I have a whole one hour on the beast, but 10.04 came up just as smoothly as the 9.04 and 9.10 installations.

At the moment I am a very happy camper with this new release.  My complements to those who pulled off another release.

---

### Post by edempco on 2010-05-14
I have more than one installation and all of them have lock up problems because of ATI video cards. Would have liked to be able to vote for each machine. Upgrade and new install both lock up.

---

### Post by visual_decoy on 2010-05-15
Just finished upgrading from 9.10 to 10.04 on Thinkpad T400 dual boot with windows 7. ATI mobility radeon hd 3400. Intel wireless WiFi Link 5300.
I uninstalled the proprietary ATI driver prior to the upgrade, and reinstalled afterwards.
Very happy with the results so far.

---

### Post by Kung! on 2010-05-15
I installed 10.04 about a week ago.  I've got a variation of the Toshiba Satellite L500D, with an AMD Athlon M320 (I believe it is), 2Gb of RAM, 250GB hard drive (since upgraded to 500GB), ATI Radeon 4200, etc.

I had more than a few problems; it is now running well, but in truth the reason it's running now is because I've been working with Linux for a few years and am an IT guy, and as my father once said, "I'm like a bulldog....I don't stop till it's fixed."

1.  Originally could not even boot into the GUI.  That was solved fairly easily by adding the command "acpi=off" to the arguments.

2.  Utilizing the standard video drivers works; utilizing the 'specific' hardware drivers for my card breaks everything.  Still working on that one, but being as it works fine with generic drivers, it's not a show stopper.

3.  Sound SUCKED.  Long story short, uninstalling Pulseaudio (and therefore forcing it to use ALSA, I believe) fixed that problem.

I also had problems with wireless, but for some reason, UNLIKE many others here, I simply had to download the RTL8192SE drivers from Realtek, make/make install them, and then run the other requisite commands.  Now it either recognizes the networks, or joins them if I've told it to.

There have been some other small things, but nothing big at all - nothing a simple Google/search within this forum hasn't solved.

---

### Post by puccio on 2010-05-15
I upgraded from 9.10 to 10.4 and I have this terribly annoying problem with my wireless card:

[http://ubuntuforums.org/showthread.php?t=1483904]("http://ubuntuforums.org/showthread.php?t=1483904")

three times only today (first day of the upgrade) and it gets disconnected from the Access Point. Trying to reconnect using the tool Wicd (the one I have always used) gives no successs. A complete reboot instead fixes it, which is of course not acceptable.

**So up to now I'm NOT satisfied of this upgrade.**

---

### Post by greenerpole on 2010-05-15
I installed Ubuntu 10.04 yesterday night. 
A couple of minutes after inserting the cd, I could contemplate the install purple screen. Unfortunately, an error message appeared a few seconds later ("unrecoverable error...") inviting me to try to complete the installation from the live cd session. 
And indeed, the live cd loaded and the installation completed with no trouble after that.
 
I really appreciate the smoothness of the desktop and acknowledge that developers achieved what is probably the best Ubuntu release so far (i started ubuntu with breezy). 
However, if i have been a first-time user, i would surely have given up after the first error message. 

Just a detail. TVTime, the software I use to watch tv on my computer, did not work out of the box (crashes all the time). However, installing the latest version solved the issue: 
[https://launchpad.net/~whoopie79/+archive/testing/+files/tvtime_1.0.2-5ubuntu2.1_i386.deb](https://launchpad.net/~whoopie79/+archive/testing/+files/tvtime_1.0.2-5ubuntu2.1_i386.deb)

Many thanks to all developers and forum contributers!

---

### Post by willyclaes on 2010-05-15
I updated from 9.04 to 9.10 without any problems, and the update to Lucid Lynx also went well. Except now I can't enable desktop effects. All the options are there, some people had the same problems but their options for desktop effects where gray or they received an error message, but I don't even get an error message. Its driving me nuts:(. 

But apart from that everything worked out of the box. Kudos for the ubuntu development team.

---

### Post by shinglebrook on 2010-05-15
Toshiba NB100 netbook works OK - I had 9.10 UNR on it and upgraded to 10.04. Everything on this machine works as expected except all my favourites icons disappeared. I do not use Evolution mail on this machine.

My main machine (quad core Q6850 extreme on Asus P5W DH Deluxe mbd, 4Gb RAM, ATI Radeon X1600 running 2 monitors on DVI, 6 hard drives triple booting Win XP, Win7 & Ubuntu) did an in-place upgrade but GRUB did not install properly leaving the machine unbootable. Recovering from that was interesting as I did not have a 10.04 CD to reinstall GRUB from. I eventually used a 9.10 live CD to download the 10.04 CD then reinstalled GRUB. Now boots OK. When I originally installed 9.10 all the drives and other OS were correctly detected and it just worked.
Ongoing problems with this system are:
1. Evolution keeps randomly shutting down. Did not do this on 9.10.
2. Slower boot than 9.10. I run Compiz fusion with Emerald themes. Getting to a blank desktop is quicker than 9.10 but there is then a delay of approx. 30 seconds before the panels appear and the desktop is usable.
3. Sometimes icons for installed software do not appear on the menus. I installed Marble & the icon did not appear. Went to edit the menu but it was already there. Had to remove & re-add the icon then it was OK. Similarly some drives sometimes take a long time to appear in the places menu. Did not happen in 9.10.

My test server (basically old scrap I play about with) is an AMD Athlon 2600+ with 2GB RAM and an ATI Radeon MX440 AGP graphics card. I did a clean install of 10.04 LTS server edition. The live CD boots OK, install completes but on reboot my monitor says "input not supported". Don't even get the GRUB menu. System appears to be working apart from the display as logging in then halting the system works from the keyboard if you can guess correctly when to start as the display is totally blank.
Not fixed this one yet. Have re-installed 9.10 as this works correctly. Reading the forums indicates there is a problem with MX440 graphics cards and the drivers in 10.04.

Bit of a mixed bag then really.

PS - download speed is OK. I get 2.3 Mb/sec average for the CD download - a bit less than 5 minutes for the entire download.

---

### Post by dyno7351 on 2010-05-15
My computer is a P4 3GHz, 2 gig ram with a 7600GS Nvidia graphics card. I upgraded from 9.10 to 10.04 LTS 32 bit. The process took about an hour. Unfortunately it was not problem free.

After the reboot, the gnome window manager fails to start. I can start it manually using gnome-wm&. I tried sudo apt-get install gnome-session ubuntu-desktop into a terminal window followed by a reboot without success.

I do see an error in the daemon log:
gnome-session[1352]: WARNING: Could not launch application '10e3c217e564d6d4cf126422946943887600000017030024.desktop': Unable to start application: Failed to execute child process "/usr/bin/compiz.real" (No such file or directory)

/usr/bin/compiz.real does not exist but /usr/bin/compiz does. 
I have no idea where the ".....".desktop application comes from, so at this point I's a bit frustrated.

I generally do not do the upgrade option in update-manager just for this reason as I have never had any success with this hardware. Next time I will know better.

---

### Post by blucat on 2010-05-15
I decided to do a fresh install of the 64 bit instead of an upgrade.  So I wiped all the hidden files on my home partition and proceeded.  The only problem I had was with booting the live cd.  Sometimes I got a splash screen with two icons at the bottom that stayed that way forever, or else it would finally get past that screen but it also bypassed the keyboard setup and boot option screens altogether.  When the later happened the final result was a black screen with some error message about a network error.  Thinking that maybe the alternate install disk would free me of the problem, I started downloading it.  While it was downloading I decided to do a Google search.  I found that when the splash screen appears I could hit F6 to get to the keyboard layout.  Hitting F6 again I entered a "nomodeset" option to the command line.  It then booted normally. I installed the OS and everything seemed to be OK.  
I haven't had a great amount of time to play with it but everything seems to be working normally.  It detected my HP network printer and even my ancient AGFA scanner.  
I believe the source of my problem was my ATI HD4200 graphics, although once installed it notified my of the proprietary ATI drivers and they installed without a problem. 

:-\"

---

### Post by karatedog on 2010-05-15
*Upgrade - got many problems that i've not been able to solve*

The update was flawless, however I have some problem. I'm a Hungarian user but I used US locale and Hungarian keyboard.
Now my locale is FUBAR. It is "en_US.UTF-8" and almost all starting applications freak out, that they can't find it and must fall back to "C" locale. This error was present during the upgrade procedure.
This is no wonder as the proper locale now on my machine is "en_US.utf8", which - being a folder name - can cause errors if not properly set.
If I manually modify LC_ALL and LANG somethings modifies it back to the wrong one (I haven't investigated it thoroughly, yet)
I'm using heavily accented characters, like "&#337;&#369;éáí", which seem fine up until the point I receive or send letters with attachments that contain one of these characters, at which point Thunderbird cannot find the attached file.

---

### Post by jlunse on 2010-05-15
Installed Ubuntu first time ever om my computer and it works just fine:)

Today, I also installed Ubuntu on my daughters computer. She is currently doing her homework using Openoffice Writer for the first time in Ubuntu. She think it looks cool.

Ipod mini together with Rhythmbox and her mobile phone seems to work fine too. Installed Flash player in the browser and she could watch her favorite TV-shows.

Finally after so many years with different MS OS, started with Windows 2.0 and it ended with Win XP - but now starts a new era, hopefully forever **[COLOR="Red"]going 100% Ubuntu[/COLOR]** in my home:)

//Jlunse

---

### Post by Guitar John on 2010-05-15
After [upgrading]("http://ubuntuforums.org/showthread.php?p=9286708#post9286708"), I decided to switch from Xfce to Gnome using [this method]("http://www.psychocats.net/ubuntu/puregnome").  Don't ask, long story.

I noticed a trend toward being more Mac-like in regards to themes.  I compiled my own using a combination of Clearlooks and Dust.  I didn't feel like getting used to the left-handed themes just yet.  

Overall I like Lucid, but there are definately some things to adjust to.

---

### Post by Unicast on 2010-05-15
Got fed up of the bugs in Lucid, esp with the abysmal support for the 855GM graphics.

My top panel where the time, networking icon etc etc are would regularly jumble itself up and on occasions would have to press Ctl-Alt-Del to get to the shutdown option.

Very poor.

Have reverted to Karmic - so much better.

---

### Post by treebadger on 2010-05-15
I'd accumulated a lot of trial-and-error rubbish using Jaunty &  Karmic and wanted to switch from 32-bit to 64-bit, so did a fresh  install... 

I had a lot of hassle getting anywhere to start with and burned 4  separate copies of the live cd before I could get past known problems,  but when I eventually got Lucid installed it worked perfectly.

I liked Jaunty a lot, Karmic was okay, Lucid seems, so far, excellent.

---

### Post by byline on 2010-05-15
> **uncle_meatloaf said:**
> OpenOffice spreadsheet app, which I use constantly, shows corrupted characters, slow re-calcs for new input data, and blotchy blocks of screen garbage when manipulating comments.
I've noticed that in my OpenOffice word-processing files, everything works fine except that the toolbar dropdown menus look splotchy. Any ideas as to what's going on there?

> **apostate said:**
> Oh, and try deleting more than one file  consecutively by highlighting them and hitting the *Delete* key. Fail.  Nobody noticed that?
FWIW, I haven't had this problem. I can delete as many files as I like.

---

### Post by scrapmetal on 2010-05-15
Not so good so far, on main machines.
Failed Live update, servers?, feed torrents -all...helps.

1.
Virgin Computer, out of box. Wiped hard drive.
Have installed alternative 32 bit Kubuntu 10.04 on machine below. (only fault noticed, so far forum type runs of screen - "different" ) 
After loading Ubuntu 8.04 LTS 32bit (worked fine),
Loaded XP pro - SP2 (it is having massive trouble with sound, net access etc. "Expected that")
Hard drive allocation, 25% Ubuntu,  25% XP, 50% Kbuntu, 

IBM - Lenovo
Product: ThinkCentre M52 9210-KME

Motherboard:
CPU: Intel: Celron 2660 Mh
Support Chip set: Intel
RAM: 512Mb DDR2 CAS:4-4-4-12 ,Single Bit (64), Slot 0, BRAND: hynix semiconductor, Made In: Korea [note; can get 1Gb sticks]
Video Card: Rage
Hard Drive: 80Gb Identification?:

Site info: [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4UFUYK](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4UFUYK)

2.
Main Machines:
On 1 main (modern AMD - Asus - Geil (matched pairs 4-4-4-16 ) 4 GB, have dropped to 2 checking RAM, swapped DVD units 1 SATA, + 1 Pioneer 16 Cache. 3 x 500 GB's 1x 320 WD + other stuff ) 
Machine. Live CD runs in 32 bit Ubuntu and Kubuntu.
64 bit, no luck.
Checksums Ok. No over clock etc.
Will keep trying, Grub - Grub2 etc. A few bugs to sort out yet.
 10.04 looks fantastic in all forms.
Well done, to all :-)

---

### Post by Pablo W on 2010-05-15
Hi. I tried to get answers to my issues searching through previous posts before posting a message, but I could not find them, so here we come:

I upgraded through the update manager from Ubuntu 9.10 in an HP mini 5101.
Problems found so far are:

Gnome panel: From the two panels I had in the previous version (one in the upper part of the screen, the other to the right), only 1 survived the upgrade to Lucid. I have tried to create a new panel, to no avail. If I go to System, panel, nothing happens. If right click in the existing panel, all options are deactivated. :confused:

Prism: same as Gnome panel: It used to work flawlessly in Ubuntu 9.1, now I cannot make it run. If I click on Internet, Prism, nothing happens. Besides, I have lost all my links to Prism applications because they were all in the missing gnome panel) :( 

Videos in Firefox: From a perfect performance in Ubuntu 9.10, the situation in Lucid is that I cannot see videos. When I try to play videos in sites such as youtube or BBC News I get the following error message: "Cannot play media.You do not have the correct version of the flash player". I have checked in Firefox (Tools, contents manager). I have the three options installed (Gnash SWF Player, Adobe Flash player, and a third one). If I download the player from the adobe website, I get a message announcing that there is a conflict with players already installed. :confused:

Being almost wholly illiterate in Linux, In could not solve any of these issues.  I will keep trying and report back in case of success. Help is very appreciated.

Cheers.

---

### Post by marbss on 2010-05-15
After 4 days of using ubuntu 10.04 LTS on my old IBM x40 thinkpad... Today I gave up and reinstalled ubuntu 9.10.  

I was able to do a clean install and get 10.04 working using tips from
[http://ubuntuforums.org/showthread.php?t=1475128](http://ubuntuforums.org/showthread.php?t=1475128) and
[http://www.divideandconquer.se/2010/04/30/thinkpad-x40-with-ubuntu-10-04-lucid-lynx/](http://www.divideandconquer.se/2010/04/30/thinkpad-x40-with-ubuntu-10-04-lucid-lynx/)

The clean installation experience on my ibm x40 thinkpad was disappointing because I had to use the alternate installation cd and some workarounds to get the video card working (see the links above).  

I then installed Opera web browser and the "restricted extras" from the Ubuntu Software Centre.  I was excited about the fast boot times and the pretty new Mac-like user interface....  but I then frequently had my computer freeze and lockup when browsing the web.  I don't know if this is an Opera bug or a Ubuntu bug.  Whatever the case... I did not want to spend anymore time figuring out the issue.  I'm back to 9.10 and stable and happy.  

Back in 9.10, it looks like Gwibber and the game Gbrainy are available via the Ubuntu Software Centre and the new video editor I won't use.  So I'll stick with 9.10.  No need to move to 10.04 for me.

---

### Post by bigtom71 on 2010-05-16
Just upgraded my Dell Inspiron 1525n from 8.04 to 10.04 and everything is working fine. Wireless card worked right out of box, Had to follow multimedia guide to get DVD player to function. Only real problem is that there seems to be a bug in firefox about closing when opening certain sites but for the most part a real painless upgrade.

---

### Post by ZizzerZuz on 2010-05-16
Flawlessly ... with a small disclaimer.

Desktop is running well.  Everything I would expect to work is.  The touch screen responds, just incorrectly.  I'll tackle that soon.

I've also loaded Server on another box and I'm having a bit of a learning curve on that one.

Waiting for the boss OK my department moving to Ubuntu desktop.  The prototype is built.

ZizzerZuz

---

### Post by Manganic on 2010-05-16
Here's what's stupid:

I have 4 computers, on which I am running Ubuntu.

First is the one I'm currently using to type this message  AMD 1.1GHz, 1 Gig RAM, and 100GB Hard drive.  Old Nvidea card.  Was running Karmic Koala, no problems.  Upgraded to Lynx with no problems.  Running fine.  No 3D acceleration available, but no worries.  Not a big deal.

Second is a computer I'm using to run as a server, dual core CPU and gobs of hard drive space.  It had Karmic Koala Server, and upgraded to Lucid Lynx Server.  No problems.  

Third is a laptop, 200GB hard drive, ATI 7600 Xpress graphics, dual core CPU, but nothing special.  Running emerald, compiz (with desktop cube and full 3D acceleration) Upgraded to Lynx, after workaround of ATI blank screen problem, worked fine.

Fourth is a quad-core CPU, dual 250GB hard drives striped RAID configuration, loads of RAM, TWO ATI RadeonHD 4850 graphics cards, three monitors.  Was running Windows Vista with Ubuntu WUBI Karmic Koala, but nothing that I wanted to keep.  Downloaded and burned ISO of Lucid Lynx.  Install: error with RAID.  No matter, install Karmic and upgrade (successful.)  No blank screen problem either.  Install fglrx ATI drivers and catalyst.  Screens lock on UBUNTU splash screen.  No success, reinstall Karmic and try again.  Upgrade GRUB and Apply ATI workaround.  Re-connect bluetooth keyboard and mouse.  Install Open-source ATI Radeon HD drivers and modify XORG.conf accordingly.  Screen locks.  Enter recovery mode, edit xorg.conf, screen works, but bluetooth keyboard and mouse no longer work.  Plug in USB keyboard and mouse.  Neither work.  re-enter recovery mode.  sudo dpkg-reconfigure xserver-xorg.  No xorg.conf file generated.  No solution can be found online.  Swear.  Beat head on desk.  Reinstall karmic...

I don't understand why my most powerful system is giving me the most grief, but at this rate, I'm going to upgrade - yes, I said upgrade - to Karmic Koala.

---

### Post by MikeSteele on 2010-05-16
The upgrade worked fine, and didn't take all that long.  My complaint is the top line in many programs turned black with white letters.  You click "File", "Edit" or whatever, and you get black pulldowns where you can no longer see the dividing lines between groups of options.

I initially thought this was a Firefox 3.6.3 problem, so I whined on their forum.  Some guy there said it was Ubuntu's fault and I should come here (or go find a different "theme", whatever THAT is).  A bit later, I started Open Office, and by George, it exhibited exactly the same problem!

If anyone has any suggestions, let me know!

-Mike

---

### Post by ThePinkWitch on 2010-05-16
I had Karmic installed and it was working reasonably well except the internet sometimes took ten minutes or more to connect. Update manager wanted to update to 10.04 so I let it. After the upgrade my machine was extremely slow and when I closed a window it left parts of the window behind and bits of flame from the effects were left on the screen. It was a disaster. When I shut the computer down the screen would get a whole lot of coloured lines just before it shut down. I thought it must be a problem with the update so I downloaded the ISO and burnt it and reinstalled. Unfortunately it still does the same thing. I'm thinking of just putting Karmic back on.

---

### Post by Enginer on 2010-05-16
I have NEVER been able to download a Ubuntu iso and install.   EVERY time the install stalls at some percentage less than 100%.  Almost makes you want to weep.

HOWEVER, I have an old 6.06 LTS disk that came with the Gagne book "Moving to Ubuntu Linux" that ALWAYS installs perfectly.

10.04LTS is now happily sitting on my new harddrive on an Althon ECS MB (with glue-on chip - an el cheapo) working like a champ.

I have tried Debien and two or three other distributions, every Ubuntu, and the live CDs work fine.  The install always fails.  Only sequential upgrades from 6.06 works.

Why?

---

### Post by jvector on 2010-05-16
Well, I had the same issues that several people have reported where you get an unresponsive black screen just after the splash screen at boot. This happened on all of:
[LIST=1]
[*]Network upgrade of Xubuntu from 9.10 to 10.04
[*]Fresh install of Xubuntu 10.04 from downloaded image into new partition
[*]Network upgrade of regular Ubuntu 9.10 to 10.04 (after doing fresh install of U9.10: I figured it might be more thoroughly debugged than Xubuntu)
[/LIST]

Tried several kernel boot option workarounds that did not help: nomodeset, noapic nolapic, acpi=off.

Did lspci|grep VGA, discovered I have Intel 82852 graphics and that 10.04 has a known issue with that.

Boot with kernel option i915.modeset=1, get to a low-res desktop with no window decorations hence no drag, resize, min/max/close buttons. I suspect that may have been due to an earlier boot into recovery low-res X, combined with a setting to skip login and go direct to desktop.

From low-res desktop, force logout to get to login screen, select failsafe X session, login. It Works!! :guitar:

Create /etc/modprobe.d/i915-kms.conf saying "options i915 modeset=1", sudo update-initramfs -u .

Reboot, no kernel option required, desktop and windows behave as they should :KS (... so far...)

---

### Post by Nightstrike2009 on 2010-05-16
Hated Ubuntu 9.10 too many serious bugs, also killed my net connection, Ubuntu 9.04 worked with no issues. 

Ubuntu 10.04LTS is the best release I have experienced yet (Started at 7.04 and up until then rated 9.04) minor issue with moving window gadgets to left side but new "notifications" planned for rightside so at least their is method in the madness (Until they implement them we have "gconf-editor" righthand fix anyhow so no serious issues).

Glad they lost the "Muddy" theme to that was depressing, nice move on that one black & Purple is much better. :-)

---

### Post by Drycola on 2010-05-16
It was a good experience after all, although I've installed it on a fancy modern tablet!
Everything worked out-of-the-box, except for the 'calibration' of the touchscreen (although it killed me for several days before getting it done!), otherwise nothing essential needed tweaking or so..
In General: Lucid Lynx is a well finished edition, with a better theme and no post-installation headache!
Thanks, UBUNTU developers :D

---

### Post by bpack on 2010-05-16
Well my install was relatively painless and it even detected my ATI mobility 3650 which has been the bane of countless other distros. Coming from Linux Mint 8 (great distro for beginners) I still have a problem that was present in Mint. My Intel 5100 A/G/N Wifi link card detects networks, but can't connect to them. (In particular ad-hoc networks with my Epson wifi printer. 
Otherwise, I'm quite impressed.

---

### Post by warpasylum on 2010-05-16
Installed Lucid a couple days ago to my desktop and put the remix on my netbook as well. No issues here. I was pleasantly surprised @ the speed of the boot sequence. No issues to speak of yet.:guitar:

---

### Post by ekoerner on 2010-05-16
I downloaded 10.04 and burned the CD without problems.

Installed on an 6 years old IBM Thinkcentre (3GHz Pentium 4, 1.5GB memory, ATI Radeon 3650 AGP graphics card, 80GB hard drive with 9.10 in another partition, XP and another 9.10 on a separate disk). 

Installation went smooth and fast. After the restart I got Grub starting the new 10.04 installation. Then nothing, just a blank screen. Powered down and started again. This time, after the Grub loader, I got a few weird looking screens, but Ubuntu came up. Not sure whether this is an Ubuntu problem, periodically I see XP hanging up at about the same stage, meaning the initial VGA mode works fine, but switching to the enhanced screen management fails. Reboot usually resolves the problem. However I have never seen this with Ubuntu, which I have been using since the 8.10 release.

I activated the ATI driver, then none of my restarts hung.

Next I was looking for a way to move the windows control buttons to the right. I expected to find something under preferences, but did not. Had to look it up in the 10.04 documentation. Then I wanted to unlock the root user and assign a password. In the previous releases I used the user control section under administration. I did not find this option anymore, had to do it from the terminal using "sudo passwd root".

I will continue to work with 10.04 on my computer before I put it on my wife's laptop. For her I have to make sure it looks and functions the same way as 9.10.

Ewald Koerner

---

### Post by jasonMB on 2010-05-16
Logged into Ubuntu for the first time in some weeks, and was advised there was an update available.   I went ahead and accepted it and followed all the recommendations, and that's where the problem started.

As much as I hate Windows, I have to use it for school since .NET framework isn't compatible with Ubuntu and my school programs use it.  Needless to say, when I rebooted and got to my multiboot menu, I selected WindowsXP and nothing happened.  So I rebooted and tried again, same thing nothing happened.

Not too happy with either program right now.....

---

### Post by halversondm on 2010-05-16
I have a home built, P4 3.0 GhZ, 1.5 GB RAM and three hard drives.  I have a SATA that dual-boots Windows 7 and XP.  The other IDE drives are for Linux.  I'm using 9.10 currently on the 20 Gig drive.  The computer is about 5 years old.

I went with the upgrade first.  At some point it locked up.  I couldn't get past the Grub screen.  I would say that it was about 85% complete.  I had no mouse support at this point.  I'm not sure if I had keyboard support or not.

I then downloaded the CD install version.  When I loaded it the first time, I didn't have the traditional text based menu to pick Live CD or install.  No options.  It just skipped right over that part.  When I got to the GUI for the install, I had no mouse support.  Thinking that I had an issue with the disc, I tossed it.

I downloaded the DVD install version.  I was thinking that the byte count for the CD was too close to the max of the CD.  So I burned the DVD and loaded it.  This time I had the text based menu.  I was able to use this and get into the GUI for the installation.  Again, though no mouse support.  I was able to install though without the mouse by using the keyboard.  However, when I restarted, I wasn't able to login because I couldn't find a way to select my name and type in my password.  After that, I was going to start researching what I had to do to get mouse support back.  I restarted the machine and tried to select the boot of Windows XP through the Windows 7 boot loader.  When I selected the earlier version of windows, the computer restarted.  At this point, I gave up.  I restarted with the 9.10 CD and reloaded that.  As the saying goes, if it ain't broke, don't fix it.  I'll stick with 9.10 until I get some answers or 10.10 comes around.

---

### Post by quequotion on 2010-05-17
Pleased to report a nearly complete success using the Debian method.

I wrote a little how-to:

[http://ubuntuforums.org/showthread.php?p=9312857#post9312857](http://ubuntuforums.org/showthread.php?p=9312857#post9312857)

---

### Post by consindo on 2010-05-17
No ethernet networking. It has worked on feisty, hardy, intrepid, jaunty & karmic but not on lucid. Ubuntu should really have a week or two after they do the RC to fix all these issues and not at the last minute (cough grub cough).

---

### Post by beeno on 2010-05-17
It was the best Linux installation I have ever done!

It installed in (with no exaggeration) about 10 minutes on both of my PCs using the USB stick. It runs near flawlessly, 20x more stable than any previous release of Ubuntu and is much quicker too.

Also, the new interface is amazing, I think it's the first time that installing emerald was not the first thing on my to do list.

It's simply amazing, if Ubuntu keeps progressing at this rate, it's a sure fire to finally bring Linux out of the dark ages and finally get some support from major software companies that refuse to write for Linux at this point in time.

---

### Post by Flangeman on 2010-05-17
Downloaded and installed clean.

Then restart to try XP on a separate hard drive - nothing, the XP is on the selection list for Grub but when its selected the machine re-boots to the Grub screen...

I use Skype to keep in contact with parents who are on the other side of the world, not been able to talk to them via Skype for a week - not impressed.

---

### Post by quequotion on 2010-05-17
> **Flangeman said:**
> Downloaded and installed clean.

Then restart to try XP on a separate hard drive - nothing, the XP is on the selection list for Grub but when its selected the machine re-boots to the Grub screen...

I use Skype to keep in contact with parents who are on the other side of the world, not been able to talk to them via Skype for a week - not impressed.

There is a Linux version of skype!

+1 I also have parents other side of the world. You talk to them every *week*?

---

### Post by abhay.abcd on 2010-05-17
I installed the OS on a P4 2.8 ghz processor with 512 RAM A dual boot with Win XP . 

It is connected to a 24 inch LCD monitor from Sun Microsystems with a resolution of 1920- 1200 and intel onboard graphics

The problem I am facing is when I open more than 3 applications the X windows has some problem and I get vertical black and white lines on the monitor . It works fine when I restart. 

I would be happy if this problem is solved , I cud then use ubuntu as my primary OS :(

---

### Post by steyr22 on 2010-05-17
Unable to Install at all!

Have downloaded the ISO 4 times, burnt to disk 5 times (data validation shows all is well) - 5 times coz I reduced the burn speed to try to get a good copy.

Install gets to 43% copying new files (every time - on any disk I have) and then has an I/O error that causes the install to crash and close down (opens in Live CD Desktop).  Got System Log - so will try to find cause of problem.

Ubuntu 9.10 had no sound at all (never did fix that - even with all the help off the Internet - eventually just reinstalled Ubuntu 9.04) and now Ubuntu 10.04 won't install at all ! 

Going back to Ubuntu 9.04 (and may stay there!! )

---

### Post by ubalderdash on 2010-05-17
Since the Hardy Heron I've had lots of problems when upgrading to the latest versions.

Consequently I reserved my weekend for the expected problems and launched the upgrade with trepidation! Two hours later I was out enjoying the sunshine quite dumbfounded as to how quickly and how smoothly the upgrade had gone. NO PROBLEMS OR DIFFICULTIES AT ALL !!!

WELL DONE TO ALL THOSE WHO MADE THAT POSSIBLE

---

### Post by RainKap on 2010-05-17
I tried the upgrade route, which went fairly well, but I'm afraid that for now I shall revert to Karmic. The wrinkle with "error mounting /proc/bus/usb" at startup was easily solved by editing /etc/fstab, but the lack of a reliable wireless connection is a killer. I've tried the various suggestions on threads in the forum to deal with my Atheros AR5001, but none was successful.

I'll keep an eye out for any further suggestions for getting wireless working, but when I've posted this the Karmic alternate AMD64 CD will be going into the CD drive on my laptop!

Ian

---

### Post by jetsam on 2010-05-17
I do admire your persistance with a troubled wireless card, Ian, but you could just swap the card for one that works.  Ask on Networking and Wireless if you want some advice on which to get.  Also, chili555 there if he isn't to busy will likely take your case and maybe make short work of it, or possibly guide you through a long and winding trail of unknown duration to a probable solution to your problem.  

Personally, I've always fixed wireless by using ethernet.

---

### Post by -harvi- on 2010-05-17
10.04 working almost 'out of box' i just need to copmile today-realesed kernel 2.6.34 to get switchable Gpu working and i could say bye-bye to Vista for good :)

---

### Post by lippsmasta on 2010-05-17
My Dell XPS 1530 and my Media center worked with minimal issues. And i am loving many of the new features (iphone sync) and the upstart goodness. The only issue I'm having at this point is geting Lucid to work with by IBM X40. I seem to be unable to start GDM even though i have gone through the [workarounds]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") that others with IBM X40s are reporting work for them. Right now I have reinstalled Karmic until a little more progress is made. I that being said i am itching to upgrade but I am willing to wait for this bug to get fixed.

---

### Post by kooia on 2010-05-17
I installed it, and I first was going completely crazy.  I couldn't access my windows, the grub was had a bug.  Here's how I fixed it.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by kamiokande on 2010-05-17
I did 2 fresh installs on my laptops - one is a Dell Inspiron B130 (32-bit version) and the other is an Acer Aspire 1810T (64-bit version).

Both of the installs worked flawlessly (except for maybe some Skype internal mic issues).

10.04 looks beautiful! I like the default theme.

---

### Post by Lince88 on 2010-05-17
I did upgrade. I have some problems and i cannot fix it. I'm new. I lost my title bars in all the programs and other problems with graphic

---

### Post by libssd on 2010-05-17
Ubuntu 9.04 was my introduction to Linux, and was very satisfactory and stable from the beginning, running in a 32gb partition on an Acer AA1 D150. The Jaunty experience was so positive that I tried Karmic when it became available, but it dropped internet connection every time I switched from battery to line power, so I went back to 9.04. Also, I had significant problems with ext4 filesystem when I attempted to install Karmic on an 8gb SDHC card; ext3 was fine.

Last week, I decided to give Lucid a try. My usual practice is to create a USB installer from the ISO image, remove the HDD, and do a test install to an 8gb SDHC card. This time, I became complacent, and left the HDD in. Even though I was installing on the SDHC card, toward the end of the install process, I noticed that it said it was updating grub, which worried me. When the install finished, neither the SDHC card nor the HDD would boot -- just a black screen. I could probably have recovered with just a reinstall of 9.04, on the HDD, but I panicked and reinstalled both Windows XP and 9.04, a process that took several days to get my configs back to where they were prior to the disaster. At least I now have two squeaky clean installations -- learning a **lot** in the process!

During this time I found out about remastersys, and now have system recovery capability from both an external DVD drive and a USB thumb drive. I don't think I'm going to touch Lucid for a while, and if I do, it will be with the HDD removed. In my opinion, a recovery utility like remastersys should be part of the standard Ubuntu distribution -- it's far too easy to go from a stable system to a mess, with no easy way back.

**Lesson learned:** have *tested* recoverable system backups, and remove the HDD before launching experiments with new software.

---

### Post by libssd on 2010-05-17
> **MikeSteele said:**
> The upgrade worked fine, and didn't take all that long.  My complaint is the top line in many programs turned black with white letters.  You click "File", "Edit" or whatever, and you get black pulldowns where you can no longer see the dividing lines between groups of options.

I initially thought this was a Firefox 3.6.3 problem, so I whined on their forum.  Some guy there said it was Ubuntu's fault and I should come here (or go find a different "theme", whatever THAT is).  A bit later, I started Open Office, and by George, it exhibited exactly the same problem!

If anyone has any suggestions, let me know!

-Mike
Have you tried changing to a different theme? (I'm assuming that gnome works the same way in Lucid). Preferences > Appearance, then choose a theme. I'm fond of the Clearlooks theme with Human icons.

---

### Post by ike2702 on 2010-05-17
Still trying to get it working.
 
I've tried three different legacy motherboards (asus, biostar and one that didn't even have a name), 3 different old harddisks, 6 different old cdrom drives. Building from scratch. CPU is 1300MHz Duron. Memory is new, two sticks of 512, PC133. CD's were 8x, 20x, 40x, 40x, 55x old IDE drives sitting around.
HD's are 8G, 15G, 20G, old IDE harddrives sitting around.
 
I am typically able to press Ctrl-Alt F4 or F5 to get to a command prompt, where I issue the DMESG command and get info about:
 
Bus IO error
SQUASHFS unable to xxxx
 
Errors indicated CD, but was able to run the 9.10 test cd and indicated no problems.
I burned 8-10 copies of the 10.04 disk, last at 2X with complete verify, and they indicated it was fine. I checked the checksums, md5, all fine.
 
I'm trying to build old and slow systems, and suspect some kernel IO errors in 10.04 causing these problems. Getting ready to reformat, again, and try 9.10 on them.
Very sad that 10.04 is not working for me. :mad:
 
I was able to build a higher end box AMD X2+ 5000, from scratch, and get it working with few problems. Had IO problems with one of the two DVD's on that systems, could only get 10.04 to work installaling from one of them. 
 
Again, indicates to me there is some timing issue in a kernel IO file, just a thought, going back to 9.10. Let me know when you find the bug and fix. I'll try again.
 
vr
Ike
 
ps.  I have just finished reading about 300 posts, and my gut feel is the wierd anomalies during install of 10.04 are due to a timing issue in the io section of the kernel.

---

### Post by adamsiddhi on 2010-05-18
I am having a problem virtualizing Ubuntu 10.04 32 bit on Virtual Box 3.1.8 on Vista Home Premium 64 bit. Ubuntu stalls on the purple load screen. Very frustrating. Tried many times but fails every time. 

More details at [**[COLOR="Indigo"]my post here[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1486726")

I hope you can help.

Regards,
Adam

---

### Post by kafkaian on 2010-05-18
I'm one of the 38.5% (according to the above poll and as of current timestamp) who couldn't get this working as upgrade or install. This upgrade has been ghastly for me and is the worst since I first starting using Ubuntu with Dapper. I thought by having legacy hardware (a 2005/6 box),all the issues would have been ironed out for this incarnation. 

[Aside - And why have I almost never been able to print colours particularly well in Ubuntu?]

I was desperate for a new LTS version since Karmic proved an unreliable previous upgrade - whether it be poor/no performance with a Canon printer (frustrating having to export to another OS), poor graphics or just unable to work on certain apps where previous distros worked perfectly. So Lucid couldn't come soon enough for me....I thought it couldn't get any worse at least. How wrong I was eh?!!!!!

I know some might say, "Ubuntu is freeware. What do you expect? Stop moaning", but if this is attempting to be a mainstream alternative to other proprietary OSs, then it simply has to work out of the box. When you've got toothache, a business to run and issues surrounding death in the family, the prospect of having to deal with 'geekware' just becomes daunting.

I have had the same issues as others; i.e. I can log in and onto a Desktop with moveable cursor, but icons never get populated and taskbars flicker with no apps. At least I can turn off with a flick of the power button.

Thank goodness for small mercies!!!!!!

---

### Post by pvossen on 2010-05-18
My one problem that has been a nuisance is the change
to open java and icedtea. Icedtea is not running
my java programs. That makes things difficult for me.

Patrick

---

### Post by L8erG8er on 2010-05-18
I have not read each and every post to know who has already written about this, but Lucid absolutely refuses to work with Nvidia drivers.  I don't mean to sound ungrateful (since Ubuntu is being provided without charge), but if you can't use it, what good is it?

I've been using nothing but Ubuntu since 6.06 on my home machine, so I consider myself a loyal Linux user.  But over time, it has become apparent that if I wish to use newer, improved applications, I have to keep upgrading to newer versions of Ubuntu.  Unfortunately, it seems that Canonical, in their zeal to make Lucid more out-of-the-box user friendly, have broken quite a few things.  And since for many people like me, who have Nvidia graphics cards, without the Nvidia proprietary drivers, X is useless.

So it seems that Canonical is currently engaged in a self-defeating cycle.  They want people (Windows users) to adopt Linux as their primary operating system, but they are actually making it harder with each release to flawlessly install Ubuntu without having to tweak the system to get it to work the way it should.

I just don't think I can take this anymore.  Looks like I'm about ready to go back to a proprietary, closed system which works every time you turn it on, and live quietly in my ignorant existence.  Sorry for the rant, but Lucid is bad.  Don't know how else to say it.

---

### Post by L8erG8er on 2010-05-18
By the way, in regards to my rant above, I have read enough posts in this thread to see that a LOT of people have had problems installing and/or using Lucid.

When the polls show that [U]no one[U] had any problems installing or using a version of Ubuntu, then the OS is ready for new Linux users.

A run-of-the-mill former Windows user is NOT going to go through what we long-time Linux user go through to make these installs work right.

---

### Post by aphatak on 2010-05-18
I installed Lucid Lynx on 4 machines, and had a different experience in each case.  Here is a summary -
1) HP tablet: Flawless. The OS installed itself with no help from me at all.  If only it could rotate the screen on its own like Windows, and had as good handwriting recognition ... (well, I can dream, can't I?!?)
2) Home theater PC: Almost as good. Had the usual hiccup with dual screens - I needed to unplug the second screen till the proprietary NVidia driver was installed.  But that is nothing new, it has happened to me with *all* the previous versions (starting with 8.04), so I can't really say I was surprised.
3) Desktop PC: had a couple of bad moments here. The disk on which I was setting Lucid Lynx up had a partition of type 'fd' (Linux RAID autodetect), and Lynx didn't like it.  It wanted the RAID to be ready before it booted, but mdadm couldn't start RAID before boot!  Once I had figured it out (perhaps I was being more stupid than usual), it worked.  Incidentally, this PC has a RADEON-based video card, did not need proprietary drivers, and could install and boot with two screens plugged in, no sweat.
4) Wife's desktop PC: This was the last install, because I wanted to have confidence before I touched Her Majesty's PC (she doesn't take prisoners).  And of course, this gave me a hard time.  The keyboard and mouse froze solid, and the only way out was to show the machine who was boss - hard re-set.  After frantic searches for a fix, and trying things out, the problem vanished, just before I was thinking of resorting to chanting mantras and doing a couple of yoga poses.  The PC is working without freezing up (fingers crossed), but I am not sure if it was because of something I did / did not do.
All the four PCs already had Linux running on them before the Lynx install.  However, I am paranoid, and rather than have the new install screw up existing set-ups, I did a fresh install of the OS and all the software in a new partition.  I was wise, wasn't I - it made sense in three out of four instances?

---

### Post by libssd on 2010-05-18
> **L8erG8er said:**
> By the way, in regards to my rant above, I have read enough posts in this thread to see that a LOT of people have had problems installing and/or using Lucid.

When the polls show that [U]no one[U] had any problems installing or using a version of Ubuntu, then the OS is ready for new Linux users.

A run-of-the-mill former Windows user is NOT going to go through what we long-time Linux user go through to make these installs work right.
You have hit the nail on the head. My first experience with Ubuntu was with 9.04, which worked so well from the get-go that I thought Ubuntu was the next big thing, and I became something of an evangelist. I'm still on 9.04 because, as you say, Karmic was worse (for me), and I couldn't get Lucid to work at all with a clean install (and there is no way, I'm going to risk the upgrade route). At this point, I don't even know what Lucid looks like, or if I can tweak it to my preferences, which has been one of the fun things about 9.04. I'm not a typical Windows user, so I've been able to figure out how to install newer versions (FF 3.6, OO 3.2, Chrome) of apps that I use frequently. I was eager to try 10.4 because it was labeled as a "long term support" release, but at the moment, I don't need no stinking support because 9.4 is running (as far as I can see) perfectly for me. 

This really is a significant issue for the future of Ubuntu; I had high hopes that Ubuntu would become the "consumer" version of Linux, but it seems to be moving in the wrong direction. Obviously, from the survey and posts here, many others are having wonderful experiences with 10.4, but overall, they are in the minority. I looked at the surveys for other releases, and 10.4 appears to be having more than its share of problems.

I decided to check my reasoning by summing the "flawless" and "nothing serious" votes from Hardy onward. The trend was encouraging until Karmic (and explains why I am still on Jaunty:

**Hardy** [4296 votes]
11.06%
12.06%
13.06%
14.06%
**50.24%**

**Intrepid** [1962 votes]
9.99%
21.10%
11.11%
13.46%
**55.66%**

**Jaunty** [2061 votes]
17.18%
23.19%
13.34%
13.44%
**67.15%**

**Karmic** [4326 votes]
15.72%
19.37%
15.44%
13.29%
**63.82%**

**Lucid** [2077 votes as of 20100518]
13.67%
22.87%
13.91%
11.07%
**61.52%**

---

### Post by L8erG8er on 2010-05-18
Libssd:

Exactly.  I have been hyping Ubuntu to everyone.  But as it stands right now, I can no longer support the Ubuntu experience.  Things are getting a little too much like Microsoft around here, especially concerning things like taking away xorg.conf, putting Synaptic in the background...I could go on and on.  Lucid is just plain self-destructive, and I really do hate to say that.

---

### Post by ashwinrao on 2010-05-18
I was wondering why 60-80 MB of updates are available after I installed a latest version. It will be much pain when you are having slow internet connection (32Kbps) and takes ages to complete those upgrades. I went for re installation instead of upgrading from 9.10 only becoz of this slow internet connection. I also wonder the amount of data needs to upgrade the version (850MB) is more than the amount of data (700 MB) new installation. However, finally I have upgraded to 10.04. :guitar:

---

### Post by ashwinrao on 2010-05-18
Why my signature still displays 'Ubuntu 9.10 Karmic Koala' in forum?:confused:

---

### Post by Zenith88 on 2010-05-18
With upgrade to 10 I lost the ability to record DVDs.
Accursed upgrade. I am screwed.

One burner (LG) is now completely toast. It does not even read. I blame K3B for doing something to it with calibration, which it never did before. It calibrated, started burning and not working since.

Installed Lite On and it now treats DVD+R as DVD+RW and tries to format them.

DO YOU GUYS EVER TEST YOUR RELEASES???

Guess not, you just code, compile and release.

---

### Post by StingMP9 on 2010-05-18
I am having the same problem now in 10.04 as when I upgraded 9.04 to 9.10. It is this...eventually you lose the ability to add more software. You can Get Software and install, but everything fails at 90% or earlier. 90% is installed in cases like Camora but the app fails to capture an image. 

However I was a new user at 9.04 and am fairly inexperienced. What am I doing wrong

---

### Post by Randy Schilling on 2010-05-18
I tried to upgrade from ubuntu 8.04 to 10.04.  The process terminated with the following message: "The upgrade is now aborted.  Your system could be in an unstable state.  A recovery will run now (dpkg --configure -a)".  I tried to boot 
to my ubuntu disk. The grub boot loader showed several options, several version 10.04 kernels (no 8.04 kernels) and corresponding recovery options.  I tried a normal boot and it locked up in the first screen following the boot loader.  I did not try a recovery option.  Instead, I selected the Windows option from the grub menu; this so I could could get this message off ASAP.  
 
I am in dire need of help.  I am a linux novice but I was doing very well learning about ubuntu and linux from the book by Kier Thomas.  I worked through almost all 700 or so pages and now I wish I had never tried this upgrade.
 
I am running a pentium D cpu at 3ghz and 5gb ram.  It has two 150gb hard disks, one I call my ubuntu side, the other my windows side.  
 
I decided to learn linux at my son's behest.  After a virus infection and costly recovery, my windows side has not been the same.  It is disgustingly slow and it continues to slow down.  All I did was click on a picture of Rihanna and kaboom, infected!
 
The upgrade was interrupted by messages of the form "Sorry, the packgage "x" failed to instal or upgrade" where 
x=gwibber2.30.0.1-0ubuntu1, 
libimobiledevice00.9.7-1ubuntu1, 
evolution-couchdb0.4.5-0ubuntu1, rtkit, 
libgpod40.7.93-0ubuntu1, 
python-desktopcouch-records0.6.4-0ubuntu3, 
libgpod-common0.7.93-0ubuntu1,
rhythmbox-plugins0.12.8-0ubuntu4, 
couchdb-bin, 
python-speechd0.6.8~unofficial~N2-0ubuntu3, 
nVidia-gix-new, 
python-desktopcouch0.6.4-ubuntu3, 
gvfs-backends1.6.0+git20100414-0ubuntu1, 
gwibber-service2.30.0.1-0ubuntu1,
rhythymbox-ubuntuone-music-store0.0.9-0ubuntu1, 
gnome-orca-2.30.0ubuntu3, 
desktopcouch0.6.4-0ubuntu3, 
speech-dispatcher.
 
What do I do from here?  Install 8.04 or 9.04 or 10.04 from scratch?  
Can I get back up and running with ubuntu without loosing the important 
documents on my ubuntu side?
 
Any help will be most graciously appreciated.  
Regards - Randy ([EMAIL="rchilling@comcast.net"]rchilling@comcast.net[/EMAIL])

---

### Post by jetsam on 2010-05-18
Hi Randy.  Panic!!!

Just kidding.  Relax first of all.   And turn of the dubious computer.

What I would do: pull the plug.  Pull the ethernet cable.  Pull the box out and put it on a table.  Hit the power button two or three times to ground the system.  Touch a heating vent.  Get a screw driver, and pull the hard drive.  

Then I'd go buy a new one and also an external hard drive enclosure for the old one.  Then I'd install Puppy linux.

Any ubuntu boot disk will do.  Put the new hard drive in.  Install Ubuntu.  Find a version that works with minimal tweaking on your part.

Two days later, put the old hard disk into the new external enclosere, plug it into to your new and better computer, and save your data.

That's what I would do.

---

### Post by LuigiAntoniol on 2010-05-18
I would have preferred to upgrade from 9.10, but by the time I realised what was happening, I was well on the way to installing 10.4.

Very impressed with the speed of installation, boot up and shut down.

Well done, Canonical / Ubuntu team.

---

### Post by MCBaker on 2010-05-18
I am new at this.  I was using Hardy Heron off-line, it had not been updated for several years.  Got online, and one set of directions said that once you update your present version, you can jump to Lucid.  So I tried that.  Did not work.  Asked a few questions in the forums, and decided to do it step-by-step, Found out how to change my settings for a step-by-step upgrade, and proceeded.  Very time-consuming, but apart from the need for a new nvidia driver, I have not had any problems.

Could my luck have something to do with the decision to ugrade step-by-step?  Are unresolved dependency problems between versions part of the overall problem?

---

### Post by Wolf-Ekkehard on 2010-05-18
> **StingMP9 said:**
> I am having the same problem now in 10.04 as when I upgraded 9.04 to 9.10. It is this...eventually you lose the ability to add more software. You can Get Software and install, but everything fails at 90% or earlier. 90% is installed in cases like Camora but the app fails to capture an image. 

However I was a new user at 9.04 and am fairly inexperienced. What am I doing wrong

Hard to say with this info.  Open a command window and type```
df
```

See if you have enough disk space.

---

### Post by cor2y on 2010-05-18
On the second pc i installed lucid on i lost my wireless usb adapter which was natively identified in 9.10 but thanks to a tutorial on the forums i was able to get it working.

---

### Post by Musicologynut85 on 2010-05-18
Upgrade-Fail

I've been running Karmic, and I've tried to upgrade three times to Lucid. The first time was from my old system, the other two were from clean installs of Karmic (I have a karmic CD on-hand).

I keep getting caught-up at the same point: I'll reboot at the end of the upgrade and it will take me to the new Ubuntu splash screen, and then it wigs out and I'm left at a black screen with nothing.

It is a real pain to work with, especially all the acrobatics I had to go through to get my tablet working, and now I'm either going to have to go through them again with a clean Karmic install, or I'm going to have to fiddle around with the back-end of the Lucid boot-up... and then figure out how to get my tablet configurations working again in Lucid.

Fun...

---

### Post by ubunterooster on 2010-05-18
well I have 4computers and jumped in on the alpha with some of them, so to say I had no problems at all...

---

### Post by dazndom on 2010-05-18
YABBA DABBA DO !!!!!

congratulations are in order excellent easy upgrade on my HP  machine.
Also from disc on a 10 yr old benq machine, NO  PROBLEMS at ALL. Infact i now have 3d graphics on this old beast, skype works easy, no drama with webcam or mic.

BUT i never had any drama going from 8.10 to 9.04 to 9.10,

ONYA Ubuntu crew, love ya work  :guitar:
rockin

---

### Post by Maupertus on 2010-05-19
I had a couple of small problems, though hardly due to Ubuntu, mainly a problem with my graphics card, which is a ATi 2600HD AGP card, which is pretty exotic so even though I would like to complain, I won't ;)

More serious problem was with the mounting of my second HD and the detection of my dvd player and dvd burner, but those were easily fixed.

---

### Post by rax_m on 2010-05-19
Hi 

I just installed Lucid on a brand new Sony Vaio VPCF117. The install worked and I could log in, however I have a few issues: 

- Nvidia driver with Lucid did not work (I downloaded the driver from Nvidia and installed manually)
- Sound currently does not work (but apparently the latest Alsa should sort that out)
- I believe that the mic does not work (haven't tested myself yet)

Other than that all seems ok for now. 

This link seems good for documenting all the issues with this laptop range:
[http://code.google.com/p/vaio-f11-linux/](http://code.google.com/p/vaio-f11-linux/)

---

### Post by Pott on 2010-05-19
Going from Karmic to Lucid with a clean install. Put the .iso on a USB stick with Unetbootin, the live session works a treat but it doesn't seem to want to go past the keyboard choice screen on the installation...

It's a laptop with no USB hardware plugged in. Just the USB key with Lucid in it. It was formatted to FAT32 by yours truly before and then I used Unetbootin to put it in.

---

### Post by Dracona on 2010-05-19
I upgraded from the beta release. the main problem i had was sometimes when i rebooted the computer, i would loose the close/minimize buttons on all windows. sometimes i would have to reboot a couple times until i got the buttons back. never looked into fixing it since i was going to do a fresh install of 10.04LTS

a couple days ago, i did a fresh install of Ubuntu 10.04 LTS, so now i am dual booting 10.04 with xp pro ( sorry, im not happy about it either).
after the fresh install, I installed the updates, enabled restricted video drivers and codecs. 
Have had no problems with the install or video drivers. everything is working great. now if Itunes would get on the band wagon and play nice with ubuntu, i could get rid of the virus..... i mean windows xp pro.

Be safe everyone

Dracona

---

### Post by lizzie2 on 2010-05-19
Clean install

Installation from disk went as always with no problems, there are problems with set up, but each time their are less.

#1 Major problem, can not scan. 
Brother DCP-150C Printer/Scanner – Printing working - Scanner not.
Epsom Perfection 1260 Photo – Not scanning

#2 Medium Plug in Camera - Canon PowerShot A480 – Brings up Image viewer – No Prompt.

#3  Minor Hidden files – On 8.04
With 8.04 Folder/ You ticked the box to show and when you closed the folder they were hidden automatily, on 10.04 the do not, you have to untick the box.

#4 Minor Evolution / Contacts – When a name is open, it opens to the note page instead of the First page.

#5 Last, at the moment, but not least. I am getting a hard time from my wife as ¨Same Gnome¨ (Ball game) is missing. Please help !! LOL

Thanks to every one who has worked so hard on this, past, present & future.

Les

---

### Post by StingMP9 on 2010-05-19
> **Wolf-Ekkehard said:**
> Hard to say with this info.  Open a command window and type```
df
```

See if you have enough disk space.
It's nothing that simple. I have 40 Gb of free space

---

### Post by Dracona on 2010-05-19
> **lizzie2 said:**
> Clean install


#5 Last, at the moment, but not least. I am getting a hard time from my wife as ¨Same Gnome¨ (Ball game) is missing. Please help !! LOL



You can install the package from Karmic: [http://mirrors.kernel.org/ubuntu/poo...untu1_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb")

I found this in the ubuntu forumes, was posted by user "AnRa"

here is the link to the post 
[http://ubuntuforums.org/showthread.php?t=1468302](http://ubuntuforums.org/showthread.php?t=1468302)

might be worth reading, some people have said to install the game Same Gnome, they had to remove Gnome games. 


Be Safe everyone

Dracona

---

### Post by spezticle on 2010-05-19
the actual install process worked completely fine and flawlessly.

---

### Post by Beowulf.1000 on 2010-05-19
Upgrade was nothing but destructive, i have spent all day now reinstalling 10.4 fresh off a CD, and the problem is that GRUB does not recognize my Windows 7 disc. I had 9.10 installed and working great. Nothing but headaches with 10.4; installs fine but can't dual boot.

---

### Post by joshklewis on 2010-05-19
I have actually not had too many problems with the upgrade from Karmic to Lucid. I had a flawless clean install (did it clean because I had been wanting to clean up some disk space anyway). My main problems are not with Lucid, but with switching from Karmic 32 bit to Lucid 64 bit. I have had some problems getting some things to work int he 64 bit environment. As for Lucid itself, I love it and am glad I went ahead and spent the 7 hours downloading Lucid on the day of its release.

---

### Post by lizzie2 on 2010-05-19
[QUOTE=Dracona;9325594]You can install the package from Karmic: [http://mirrors.kernel.org/ubuntu/poo...untu1_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb")

I found this in the ubuntu forumes, was posted by user "AnRa"

Thanks Dracona,
Saved my live,might sleep indoors instead of the shed tonight LOL
Les

---

### Post by Manganic on 2010-05-19
> **Beowulf.1000 said:**
> Upgrade was nothing but destructive, i have spent all day now reinstalling 10.4 fresh off a CD, and the problem is that GRUB does not recognize my Windows 7 disc. I had 9.10 installed and working great. Nothing but headaches with 10.4; installs fine but can't dual boot.

I did away with dual booting in favour of running Windows in a VirtualBox.

The big issue I'm having is with my multi-head set up (3 monitors, 2 ATI 4850 Radeon HD cards)  all three screens come on, but when I roll the mouse to the screen on the second card, my system locks up.

I've been messing around with xorg and kms and everything for two weeks now...  Grrrr.

On *all* my other PCs, 10.04 LTS is beautiful.  But when it messes up, it messes up royally.

---

### Post by Dracona on 2010-05-19
> 




Saved my live,might sleep indoors instead of the shed tonight LOL



HHEHEHE Glad to help, i know what its like when the wife is not happy.

---

### Post by Beowulf.1000 on 2010-05-19
> **Manganic said:**
> I did away with dual booting in favour of running Windows in a VirtualBox.....

I tried virtualbox and vmware when I had a quadcore, it was unsatisfactory for my needs-- video editing, music composition with Sibelius and Komplete 6, Movie Magic Screenwriter. I absolutely need dual boot for video editing Windows (Sony Vegas Pro), there simply is NOTHING that compares in linux. Music-- I had Sibelius working, and also Movie Magic Screenwriter (Celtx is inadequate).

I just upgraded to a hexacore (six core) cpu a couple of weeks ago, so I am going to give virtualbox another go and see if the boost in cpu power makes music composing doable in linux (and no i am not going down the path of Rosegarden and JACK in linux, fricken NIGHTMARE to figure out how to configure, so user unfriendly it is not ready for the masses). I love linux, but it is just not ready for certain apps in a user friendly install and use fashion-- music composition and orchestration with high  end virtual instrument samples, and video editing for anything other than home and youtube movies.

---

### Post by kevdog1983 on 2010-05-19
Upgraded from 9.10 Jaunty to 10.04 Lucid. No problems at first with the upgrade itself or so I thought. After the 2hr download completed on my 15Mb cable connection, it installed just fine no errors that I noticed. Clicked reboot and now unless I go into recovery mode and select run in low graphics mode (one time only) it will not boot, it gets to the Purple Unbuntu splash screen for a second or two then goes blank no errors only blinking cursor for about 30sec to a min, then goes blank and nothing. I let it sit for almost an hour hoping it was just being really slow for 1st boot, hard killed it and tried several things but it only seems to able to boot in low graphics mode. I have a rather old system but have never had any issues with previous releases. 

System info.

HP Pavilion 752w
Intel Pentium 4 Processor 2.4Ghz I think don't remember for sure
ATI Raideon (3200) 8Mb AGP Graphics card again the exact model is a guess I have had this machine for a long time and don't remember for sure.
637MB ram DDR...

---

### Post by klutzie on 2010-05-19
Hi all..

my first post on this forum - so bit nervous. give me a poke if this isn't in the right place.

have to break the bad news though. 10.04 didn't work for me. Previously had Kubuntu 9.10 koala on it. nice furry animals. worked fine.

Then thought I had enough of dual-booting with Windows, so decided to create bootable cd with 10.04. The booktup detected the cd, but just blacks out after that - none of the usual installation screens (like asking for language, setting keyboard, etc etc).

That killed the notebook. So restored back to 8.04 Hardy (Unbuntu now) from cd. Worked fine - up and running in 30mins. Then did an upgrade to 10.04 Ubuntu....and that killed my machine to. Upgrade completed, it restarted and blacked out again..this time complaining about a kernel.

Any ideas anyone?

---

### Post by JohnVLang on 2010-05-19
Hi All,

I've had good and bad experiences with 10.04...

The good, firstly, i did a step up on my no-name laptop from 8.10 to 9.04 to 9.10 and finally to 10.04 one after the other (i had gone from 8.04 to 8.10 months ago and had left it at that)... Anyway, that all went very well. I've even set up a VM with VirtualBox using the ISO and all went very well.

Now the ugly - i'm in Australia, my mother is in England - last year when she visited i installed 8.04 on her laptop (she had continual problems with Windows 2000). All was good with 8.04, decided that an upgrade to the latest LTS was the way to go for her (also wanted the ability to install Skype and screen sharing software to better support her)... BUT, after talking her through the online upgrade she wasn't able to log on with her usual user and password!!! Could not get to the command prompt with ctrl+alt+F1 either... did a complete re-install after booting to Live CD (i had to send her one in the post) and still couldn't log on, keeps saying "authentication failed"... tried a couple of re-installs setting up different user/password combos but nothing has worked, always comes back with "authentication failed" and can't get to command line with ctrl+alt+F1... So, i'm off to the forums to post in the hopes of a resolution, it's dirving both myself and my mother to tears - try doing command line stuff over the phone with a complete novice!!! :confused:

---

### Post by Ben Branch on 2010-05-19
Could not get 10.04 to work; an apparently common problem with older laptops is the keyboard and mouse freezing. Here's what happened to me:

1) upgrade from 9.10 (which was an upgrade from 8.10 and 8.04); kbd and mouse froze partway through the upgrade.
2) try to install 10.04 from scratch; kbd and mouse freeze during the 'what's your name?' screen, very early in the process.
3) repeat 2) with same effects.
4) install 9.10 without any problems.
5) upgrade the 'clean' 9.10 to 10.04. Install went to completion, but after restart and launching terminal, kbd & mouse froze.

I'm going back to 9.10 until this is thoroughly understood and fixed!

Will post specifics on my hardware later. It's a vanilla (no-name) laptop purchased Sept. 2004. It was working like a champ with 9.10

---

### Post by cookingrock on 2010-05-20
I tried the Upgrade but it started tweaking out. I eventually stopped it and did a full-on clean installation. (Everything important was backed up on an external drive).

Everything's been running fine since then.

---

### Post by frodon on 2010-05-20
I upgraded my desktop last week, it has been quick and flawless.

I just had some minor things to change like button position, put back some apps shortcuts, reboot to get quake wars running again.

So flawless upgrade for me, will see if it goes the same with my laptop on hardy heron.

---

### Post by tehowe on 2010-05-20
On my Acer 1410, which they've made for about a year now, Wubi Lynx worked perfectly.

Great, that means it's time to move Windows off to one side by installing Ubuntu Studio Lynx for a dual-boot, right?

**No network card found.**

Zounds. Since I assume Wubi doesn't boot anything in Windows other than its native OS picker, I've no idea how that could even happen, yet it has, another Ubuntu gotcha.

I really don't want to have to reimage my drive to get back to my Wubi install, so hopefully that's easy to fix. 

In the meantime, Wubi, please crack that 30Gb limit. Thank you.

---

### Post by adamsiddhi on 2010-05-20
I video documented my problem with installing it in Virtualbox here:

[COLOR="Red"][http://www.youtube.com/watch?v=XMbbm5E_0Xw]("http://www.youtube.com/watch?v=XMbbm5E_0Xw")[/COLOR]

---

### Post by peap on 2010-05-20
Tried yesterday with a clean lynx 32bit server install using usb (grub install fails) and a cd (software install fails). My first time to experience such major problems during install.
I'm installing to a VIA EPIA SN, same setup has been running 8.04 and 9.04 without any major difficulties like this one.

Will give it another go today and I'm sure I can get it up and running but my vote in this thread unfortunately must be "install, many unsolved problems".

---

### Post by dez93_2000 on 2010-05-20
loved the few-clicks upgrade. took about 11 hours to download because my network speed died.

problems:

1. didn't recognise my wireless usb adapter. Had to lug my machine doownstairs to the router and do the ndiswrapper solution which worked fine. Not a huge problem but a bit of a pain - why not include the ndiswrapper download file (ndisgtk) in the install? I know you don't wanna include everything, but surely things which - if lacking - will prevent internet access should be included?

2. Grub: somehow must have screwed up the grub install and now it won't let me boot to windows - just get a flashing cursor. Done some preliminary investigation and others have had the problem so i imagine it's solvable, but it's a shame there was no option to "duplicate existing grub configuration".

---

### Post by reiki on 2010-05-20
Sony Vaio BX540B - no issues!
This is an older laptop that my son uses for school work. He had XP on it and it was infected with viruses, malware, etc and was to the point of being unusable. I had tried Ubuntu on this laptop several version ago and there were things that didn't work.

Booted the Lucid desktop CD from USB flash drive, told it to erase the disk and use the whole thing. Done deal. First thing I did after the install was to install Ubuntu Restricted Extras. Flash works, sound works, wireless works.... the only thing I found that wasn't working were the special function key combinations (hit the Fn key plus the F5 key to decrease sound.... etc), but my son tells me those weren't working under Windows either.... so who knows.

Anyways, he now has a laptop he can use to do homework, surfing, email, and I think he's going to install TweetDeck.

10.04 does it again. So far I'm 100% satisfied.

---

### Post by genseng on 2010-05-20
Hey,

I started with Intrepid - love Ubuntu....

But Lucid has been anything but, and now I am more homicidal than lucid.

I have two Ubuntu boxes, both upgraded, but nothing worked....

Downloaded 10.4 as a torrent and tried to wipe and install, seemed to work, but then the update manger poped up, 9 (nine) hours later I killed it.

Today I downloaded 10.4 from a mirror, same thing, update lasted for 12 (twelve) before I killed it. WTF, that update went thru all the human language packages, then started on some off-world ones, I think -- each one taking several hours to load.

Three days with nothing makes me want to spew somem language.

Oops, was i suppose to ask a question here: WTF!!!

---

### Post by Manganic on 2010-05-20
> **Beowulf.1000 said:**
> I tried virtualbox and vmware when I had a quadcore, it was unsatisfactory for my needs-- video editing, music composition with Sibelius and Komplete 6, Movie Magic Screenwriter. I absolutely need dual boot for video editing Windows (Sony Vegas Pro), there simply is NOTHING that compares in linux. Music-- I had Sibelius working, and also Movie Magic Screenwriter (Celtx is inadequate).

I just upgraded to a hexacore (six core) cpu a couple of weeks ago, so I am going to give virtualbox another go and see if the boost in cpu power makes music composing doable in linux (and no i am not going down the path of Rosegarden and JACK in linux, fricken NIGHTMARE to figure out how to configure, so user unfriendly it is not ready for the masses). I love linux, but it is just not ready for certain apps in a user friendly install and use fashion-- music composition and orchestration with high  end virtual instrument samples, and video editing for anything other than home and youtube movies.

I don't know what level of editing you're at (home production vs profession production) however I've used Kino for some linux-based video editing, and ManDVD is likely to be the package that burns them (I like the ability to burn PAL format from an NTSC-based machine) and it seems to work well enough to suit my purposes.  

I run Vista in a VB on my dual-core laptop under 10.04LTS because I need the flexibility provided by MS Outlook (I have several user-defined fields in my work-based stuff that can't seem to import over into Thunderbird, Evolution, or any of the other cloud-based projects out there) as well as the ability to edit, save and send .PDF forms.  (When I edit and send in Ubuntu, the changes aren't visible on a windows machine.)

For video and music editing at a higher-end level, I might just say, "heck with it" and go with an iMac.

---

### Post by Manganic on 2010-05-20
Well I'm done with messing around with it.  Last night, I disconnected my third monitor from my second ATI video card, and ran with it as-is.  I was able to get the dual-monitor desktop working fine, installed Compiz, and now have eye candy.

(The third monitor ended up as a flatpanel monitor for my network server, so at least it didn't go to waste)

Ironically, The Lynx is also running smoothly and happily on my quad-core CPU machine under KMS, which surprised the heck out of me.

So while I like the stability and flexibility of Ubuntu in general -- which, compared to anything built by MicroSnot, is far superior -- I'm very disappointed at the level of difficulty in getting things configured on a system like mine.  How difficult is it to get KMS to figure out that there are TWO video cards with three screens attached?  

I don't expect Ubuntu to be plug-and-pray, but I do expect, given how easy it was to configure and run with three screens on Karmic Koala, that Lucid Lynx would be an improvement.  Sadly, it seems to be a bit of a step backward in that area.  No doubt there are aspects of the OS that are huge improvements, however as I see it, when one releases an upgrade, it builds upon what is already working.  It's crazy to improve half the system, but break critical pieces of it while doing so.

I'm going to run with Lucid Lynx, since I prefer to be with the most recent version, however I have to say this latest release is NOT the best version of Ubuntu I've seen.  I think the Hardy through to Karmic editions outshine Lucid.

---

### Post by afrodeity on 2010-05-20
For me it was a 17 hour download followed by an 8hour install process in which I was confronted with a various questions which made little sense. The config diffs were seriously taxing on the eye, and without a help option, or code dictionary at hand, I was unable to discern where the differences were and what the results would be, so I chose rightly or wrongly to replace most of the configs which were suggested over the default, which in hindsite might have given me a better system.

After my initial enthusiasm on finding that my sopcast player worked thanks to removing a dev version of VLC and replacing with goldeneye, I am a little dismayed by the following issues:

Extremely slow boot times in post caused by ureadahead (or not) which means a lengthy process of problem solving with no immediate outcome.

[http://www.flickr.com/photos/14887361@N05/4624611874](http://www.flickr.com/photos/14887361@N05/4624611874)

Another boot issue: Fixing the butt ugly plymouth with over the counter medicine was a bit of a kick in the pants quite frankly. Thought the core devs would have figured this out by now, we all not on high-end machines and we all not going to have the same experiences. The reason why some of the fixes are now sitting on mainstream corporate software sites, and not here in the forums or on launchpad being launched as fixes is because some of the devs either sold their fixes to publishers or neglected to put them into the install process a week after LTS official launch.

Big ouch, Nautilus is worse off for me. I wish I could just swop it out and put something in its place, but having a scriptable desktop does takes some of the pain out of menial tasks.

I was therefore more than a little perturbed to find the install removed nautilus additions without bothering to ask me, and provided little or not choice in configuration.

The trouble as I see it, is that there is a big gap in interpretting code and giving users choices when they need them. How are we expected to simply read off diff code if there are is no criteria for analysing such differences, and no other machine connected to the internet?

Common evolutionary paths means a lot of the divergence and hybridity in the community is part of a known set which should be understood and analysed by an installer. at least an intelligent one.

The really weird and far out systems, have my sympathy. Extreme computing has its downside.

But is it too extreme to expect a better Nautilus? One which doesn't quit every time I click on a file? 

I want my old nautilus back, at least it was functional in karmic

Now all I have is a desktop without a working nautilus, lucid there in name only.

[http://www.flickr.com/photos/14887361@N05/4624055717/]("http://www.flickr.com/photos/14887361@N05/4624055717/")

The over-minimalised practically useless nautilus in lucid which has a serious problem, come on its just a window without any real functionality. I have tried removing and reinstalling but no luck yet. Big ouch.

---

### Post by CHFFriday on 2010-05-20
Five machine all work great!

One machine did not as it has the Intel chip set problem.

GREAT PRODUCT!!!

CHFFriday

---

### Post by Beowulf.1000 on 2010-05-20
Short films, ultimate goal indie feature film, so Kino and such just are left in the dust compared to high end NLE editors like Vegas, Final Cut, Avid. Try editing two hours of HD video with filters, 20 tracks, in Kino, etc.-- just not possible.  However, today I was able to install Sony VEGAS PRO 8 in virtualbox, and it seems to work, even full screen 1920x1080 inside of linux, amazing. Same with Sony ACID Pro.

---

### Post by mlnease on 2010-05-20
Hello All,

I already posted my nearly flawless results on my Ubuntu-only Dell Optiplex; still working great.

I'm now upgrading my SO's machine from Hardy to Lucid and I've run into a couple of problems.  It's a bit complicated; hope it's OK to post them here.

Problem 1:  My SO's machine is--or was--set up to dual boot XP and Hardy.  When she decided she wanted an upgrade, she downloaded the .iso and installed it, thinking that she was upgrading.  Aside from some serious graphic problems with this installation, it didn't--of course--import any of her data.  She thought she'd lost her old settings and a few unbacked up files but instead she'd installed--apparently--Lucid alongside Hardy *and* XP.  Attached is what her GRUB screen looks like now.

I am entirely ignorant of partitions so I decided to first do a proper upgrade via update-manager --devel-release, which has been going fine for the last fifteen hours by way of Comcast's blistering 0.24 Mbps cable DSL.  With a little over an hour to go, I ran across this, while researching how to get rid of the extra (and faulty) Lucid:

"Warning: Ubuntu Desktop edition installer no longer allows a  custom installation of GRUB, and it now uses GRUB2 (which allows very  little customization). DO NOT USE the Lucid Lynx Desktop edition if you  use a boot partition, use multiple OS (more than 2), or chainload  bootloaders. The Ubuntu installer will overwrite your Master Boot Record  and you will later be forced to recreate it manually. This is a serious  flaw in both Karmic Koala and Lucid Lynx. Use the Ubuntu Server edition  instead (and then later add the ubuntu-desktop).  GRUB2 has caused major problems in installation -- be sure to  research the issue before upgrading to Lucid Lynx."

 [http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

Problem 2:  So now I have the problem of "multiple OS (more than 2)" and am researching the issue before finishing the upgrade.  What I would like to do, of course, is delete the unwanted Lucid(s?) and use the space(?) for the proper Hardy-Lucid upgrade.  Assuming I'm able to delete? uninstall? the superflous Lucids, should I go ahead with the upgrade despite the 'serious flaw' with GRUB2?  I am at a loss as to how to proceed.  Any advice would be greatly appreciated.

Thanks in Advance,

mike

---

### Post by CSInDevelopment on 2010-05-20
I have has a perfect experience with ubuntu, and I am shocked that it even has OUT OF THE BOX ipod touch newest firmware support


its amazing

---

### Post by dallasmayor on 2010-05-20
Hello everybody.

I'm not used to this Drupal based forum layout, so I hope this lands where I expect it to, LOL.

I would highly discourage the Hardy>Lucid upgrade. Grub-PC, a variant of Grub2 is a lesser concern, the problem you will likely have is that the installer isn't going to update the scripts and configs properly.

Hardy to Lucid is a HUGE leap in infrastructure change. Knowing that and saying that is one thing, but I haven't tried it. Might work perfectly but I would not count it. Having said that I have had good luck upgrading version to next version, but that's a completely different scenario. You have to understand the quantum changes from release to release.

Unless you are a glutton for punishment, the best advise would be to not even do a fresh install until midterm into the release cycle. Don't misunderstand, I love Ubuntu but it's initial releases are ALWAYS buggy. My point of view is based on the fact that I work with a lot of computers. The BUGS tend to go away by themselves. You simply can't fix what you can't fix if you catch my drift.

Enough rambling, I made my point best I can. Good luck and let us know how it goes should you make the plunge. Grub-pc is another issue altogether but as long as your not using a multi disk config I don't think you will have a problem. If you have a multi disk config, may god help you. 

Scott

---

### Post by gulmer on 2010-05-20
Upgraded to Lucid Lynx through the Update Manager on our Dell machine, Dimension 4550.Total time was 2.5 hours which included tweaking with compiz, and AWN, otherwise it went smoothly,no complaints. Tomorrow will be our AMD 64 to upgrade. :P

---

### Post by phoenixpb on 2010-05-20
I have tried to upgrade from 9.10 to 10.04 was a disaster
Blank screen at boot with cursor blinking

Fresh Installation from live cd indeed was a success. (i have previously backuped my system with clonezilla to be sure hehe)

as you can see all is working perfectly compiz, virtualbox and so on.

See the picture. As you can see windows xp is installing in a virtualbox :)

[http://ftpb.free.fr/images/Ubuntu_lucid_lynx.jpg](http://ftpb.free.fr/images/Ubuntu_lucid_lynx.jpg)

Ho sorry my system

Athlon 1.7 ghz
1.5 gigs of memory
Hdd 60 gigs + external hdd 750 gigs usb 2
nvidia geforce 4 MX 64 meg of ram

---

### Post by Manganic on 2010-05-20
A number of people have mentioned the Blank Screen of Death(tm) upon bootup of Lucid Lynx either from upgrading or a fresh install from the Live CD.

This is most likely due to an issue with Lucid's default Kernel Mode Setting (KMS) either not properly detecting your video settings or being unable to work with the active driver.

I know that there are solutions posted in these forums (I've posted one myself) but I can't link to them as I'm writing this message from my Blackberry and don't have the links memorized.

A couple of basic suggestions are to rename xorg.conf (if it exists) before upgrading to ensure no conflicts are present and make sure you have one of the basic graphics drivers (ATI, NVidea, VESA, for example) active.  Other than that, after install, go into GRUB and change the command line to add "nomodeset" or "radeon.modeset=0" or "918.modeset=0" (not sure on the last one so double-check it) to turn KMS off.

A quick google of my username (manganic) and "nomodeset single" should get you to the thread with my workaround in it.

---

### Post by njnickols on 2010-05-21
i have never booted anything other than what comes installed when i by a computer. i am seriously thinking about dumping windows 7 and loading Ubuntu for fun. i dont want to lose my files i already have and i want to use my microsoft office (I AM A STUDENT AND NEED MY FILES AND MS OFFICE).. is there any way i get to keep my files and my office?

---

### Post by jezjones on 2010-05-21
I have been using Linux and particularly Ubuntu for quite a while (since Debian 3.0). I am just going to state the problems i have had.

This time around has been a little more flakey than previous upgrades i'm afraid. I had a Grub problem with 9.04 which meant it could not find the UUID of my main installation and so died at Grub. This prompted a format and then clean install.

The live CD of 10.04 was quite slow, but it worked and i managed to recover my data (email really) before then wiping and doing a clean install.

Here is the issues;-

Sound - worked then stopped working (just one boot up the controls were gone and no sound came from anywhere), now fixed with the removal of pulse (this is a standard issue with ubuntu since 8.04).
still have an issue with going to system->prefs->sound, its just hangs waiting for sound system.

Video - Nvidia card but unstable video and no openGL until attention given to correct driver - the standard install looked pretty grim.

USB sticks cannot read, get permission denied errors.

Battery meter seems wildly inaccurate, claims 7 hours then dies in 2.

Shutdown seems to only log me out to the GDM login screen, then i must shutdown from a command line to get it to happen... is this a permission thing?

Hardware is a Dell studio XPS laptop, its quite high spec and being Dell pretty standard components, it ran 9.04 fine and I have gone through the compatibility check.

Overall impression of this upgrade, not great. I don't honestly think i can rely on this laptop for my work which is a bad sign as i need to work more than i need to tinker getting ubuntu working.

I appreciate the efforts of the various developers and the ubuntu team who put this together, but sound and video seem to be issues in every release, yet cloud computing is more important to get into the next LTS.
Yes that is a selfish view, but how long do we have to live with 27 competing sound systems and a mexican stale mate on binary video drivers?

jez

---

### Post by pelgrim on 2010-05-21
2 pc's and a laptop: upgrade from prefious version, went fine
1 pc, upgrade resulted in hard disk failure, boot sector is beyond repair,
tried all kind of ubuntu and (forgive me) windows installs)
1 pc with dual boot, win xp in first partion, ubuntu 9.10 in second
 after upgrade, can't start xp anymore, results in black screen.
 grub "looks" ok.

I had the worst cases with upgrading since I started with ubuntu 6.06

---

### Post by juky on 2010-05-21
Upgraded from 9.10. It took 90 minutes both to download around 750 megs of packages and install them (on old Fujitsu-Siemens E8010 notebook with Intel integrated graphics). 

After reboot, could not get into GUI ("ubuntu" logo shows for 1-2 seconds and then nothing). After browsing the forum, find a workaround by permanently editing ```
/etc/default/grub
``` by adding "i915.modeset=1" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash", so it looks like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
```

Saved the file and then ```
sudo update-grub
```.

Original post:

[http://ubuntuforums.org/showpost.php?p=9171045&postcount=11](http://ubuntuforums.org/showpost.php?p=9171045&postcount=11)

Hope it will help someone.

Cheers,
juky

---

### Post by jxh on 2010-05-21
After upgrade to Lucid Lynx I have 2 problems that I cannot resolve.  I spent a day looking over various suggestions nothing has worked.

I have Zend Studio 7.1.2 installed if that is a clue.

Prior to the upgrade using 9.10 (things all ran fine).

My 2 problems.
I can no longer run any app with mysql in my web browser.  This is a very serious problem.
From my apache2 error log.

[INDENT]PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/mysql.so' - libmysqlclient_r.so.15: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/mcrypt.so' - /usr/lib/php5/ext/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/mcrypt.so' - /usr/lib/php5/ext/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/mysql.so' - libmysqlclient_r.so.15: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/mysqli.so' - libmysqlclient_r.so.15: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/ext/pdo_mysql.so' - libmysqlclient_r.so.15: cannot open shared object file: No such file or directory in Unknown on line 0
[Fri May 21 08:03:34 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.2.10-2ubuntu6 with Suhosin-Patch configured -- resuming normal operations
[/INDENT]

If I try and run the Synaptic Package Manager:
/usr/sbin/synaptic: error while loading shared libraries: libxapian.so.15: cannot open shared object file: No such file or directory


Thanks anyone who can help

---

### Post by alterpinguin on 2010-05-21
install worked nice - no special problems,
except one time there was no device.map build from grub
and the grub-menu was not loaded. It looks like "update-grub"
does not create a missing device.map, i had to call explicit
for grub-mkdevicemap.
Still not working is the shutdown with poweroff for kernel 2.6.32-22-generic
and it does not work for the live-version 10.04 booted from the install-cd too. Older ubuntu 9.04 had, and still has no problems to poweroff(its on a seperate partition).
dvbstream refused to run, when started with atd (at a special time for recording) when i was logged in as another user at the schedule-time and i am shure this never happened with ubuntu 9.04 version too. It looks like it depends on the load-level at this time but it was not started as a batch(with settings dont run at load-level >1.5)
(... and i have still to check-out "ubuntu-one" and the new emphaty, still using old versions like pidgin)
Import from old evolution calendar and mail-settings worked without probs.

---

### Post by jkuzenka on 2010-05-21
:confused:  I ran the upgrade last night with Update Manager (upgrade button) upgrading ubuntu from 9.10 to 10.04.  It is stuck on error message **"rpmdb: Program version 4.8 doesn't match environment version 4.7"** found in this thread:
 
[http://ubuntuforums.org/showthread.php?t=1489702](http://ubuntuforums.org/showthread.php?t=1489702)
 
I haven't found any answers searching this forum or gotten any replies yet on how to work around this.
 
I am currently thinking either to just reboot Ubuntu to see what happens or download 10.04 doing a clean install over 9.10.
 
I could just go back to 9.10 but, wanted to upgrade to 10.04.
 
Let me know if anyone has any answers for this issue.  This is my first upgrade with Ubuntu.
 
Thanks,
~Josh

---

### Post by KeesM on 2010-05-21
Did do both an upgrade (on older Dell laptop) and a fresh install (64-bit on desktop); had no major problems with either of them (apart from having close button etc on the top-left of windows ;-)  and Flash playback not always working :-( , now solved). Was a bit scary to switch to 64-bit (was btw the reason to do a clean install, and not an upgrade); however did not find any serious issues.

What did give problems was my initial attempt to install UbuntuStudio 64-bit with ext4. Either the real-time or ext4 was an issue, as installation took hours, and even then did not result in a correct system. Did play safe, and stayed with plain Ubuntu and ext3...

Like the new purple theme!

Thanks, Ubuntu team! :D

---

### Post by KeesM on 2010-05-21
> **njnickols said:**
> i have never booted anything other than what comes installed when i by a computer. i am seriously thinking about dumping windows 7 and loading Ubuntu for fun. i dont want to lose my files i already have and i want to use my microsoft office (I AM A STUDENT AND NEED MY FILES AND MS OFFICE).. is there any way i get to keep my files and my office?

You could start with a 'dual-boot system, where you initially keep your Windows 7 and can select during boot whether to start Windows or Ubuntu? Worked great for me, and gave me confidence that OpenOffice was a fairly suitable replacement for Microsoft Office.

Or, as an (maybe even better) alternative, start with running Ubuntu in a virtual machine (in that case you can run them both at the same time as long as you don't expect great 3D performance in Ubuntu, and share/move files between the two).

---

### Post by kjb34 on 2010-05-21
I just upgraded my system and there have been no problems so far.

---

### Post by jkuzenka on 2010-05-21
> **Re: Share with the community your Lucid Lynx  install/upgrade experience**
 		:confused:  I ran the upgrade last  night with Update Manager (upgrade button) upgrading ubuntu from 9.10 to  10.04.  It is stuck on error message **"rpmdb: Program version 4.8  doesn't match environment version 4.7"** found in this thread:
 
[http://ubuntuforums.org/showthread.php?t=1489702](http://ubuntuforums.org/showthread.php?t=1489702)
 
I haven't found any answers searching this forum or gotten any replies  yet on how to work around this.
 
I am currently thinking either to just reboot Ubuntu to see what happens  or download 10.04 doing a clean install over 9.10.
 
I could just go back to 9.10 but, wanted to upgrade to 10.04.
 
Let me know if anyone has any answers for this issue.  This is my first  upgrade with Ubuntu.
 
Thanks,
~Josh 	


New Update.  Just rebooted my PC and was able to successfully logon to version 10.04.  Even though I got an error applications seem to work so far.

Just wanted everyone to know problem resolved... :):P

~Josh

---

### Post by john8791 on 2010-05-21
Not great so far.  The first time I installed from the CD it hung up at 68%.  I re-partitioned, etc and installed successfully 2nd time.

Current problem is that it won't connect to my Linksys with WPA2.  I disabled security and am running update manager as we speak.  I found a post that said the RALINK drivers are broke with the Lucid Kernel.  I find that disappointing for a major release like this.  In my younger days I used to enjoy compiling kernels and messing with modules.  Now i just want things to work.  Not impressed so far.  Sorry.

---

### Post by ubun2warrior on 2010-05-21
i did afresh install and it was quiet fast. I have one problem with 10.04. i have created two users. and when i switch between them(without logging out from one and logging into the other)the screen goes black (sort off) and hangs i have to turn of the power supply finally.

---

### Post by jfreak_ on 2010-05-22
upgrade works perfectly, but can't do a fresh install now. just can't get to the live environment

---

### Post by StarDate2008 on 2010-05-22
I upgraded my dual boot (Win XP & Karmic Koala) 2 weeks ago.
after upgrade.
Desktop computer wouldn't finish booting up.
stuck in initramfs 
also took much longer to boot up, than with Karmic.
almost like it was testing each hard drive and finding them too slow to respond, then timing out w. an error msg during boot up process.  Karmic didn't do this.
Couldn't figure out how to get PC to finish booting, just hit enter, that brought up an Initramfs prompt.  I keyed in exit and hit enter, that exited me out of initramfs script and continued on w. boot.  finally desktop came up.  Then when I clicked on Firefox, I discovered javascript wasn't showing certain backgrounds and some buttons for example on my godaddy hosting screen.
If I had it to do all over, I would not have upgraded to Lucid yet.  Should have stayed w. Karmic which I loved.

Installed Lucid on a 2nd desktop.  Screen resolution problem (cant go to 1024 x 768   only 800 x 600 and even on lower setting, bottom STATUS line of screen is off the screen, you can only read 1/2 of it.  and mouse problem, have to click ABOVE each button or link.  Reinstalled Karmic, and these problems went away.

Guess I cant complain though, since I got Karmic and Lucid for free.  I do intend to pay them full Microsoft windows price, when I can afford it.  Thanks for creating a secure OS.
Falls Church, VA

---

### Post by cmagiera on 2010-05-22
I recently upgraded from 9.10 to 10.04.  I love the feel of the Ubuntu format; however, I have experienced a few issues.  One isn't that major it is concerning OpenAstro.org, but I think that's because of the python formatting.  The other is a little more discerning.  After upgrading, I found my sound card not to be working.  Of course, I have a SB Live! EMU10k1.  I've noticed a lot of people had issues with this particular pci board in earlier Ubuntu releases, but I have not seen anything posted so far about 10.04.  Could anyone direct me where I can find some help?

---

### Post by Son of William on 2010-05-22
I was running 9.10 but had tried so many modifications that things were getting unstable (not sure the failures were scrubbed fully and properly), so I decided to go with a fresh install of Lucid 10.04.

It worked on first boot. A couple of bugs I had conquered in 9.10 came up again and I had to relearn the fixes for them  (example: Firefox slowness fixed by switch to OpenDNS).

I still can't get my network shares working again.  It is very difficult to get Ubuntu on a Windows 7 workgroup.

In addition, I had become used to several modifications and the switch back to the defaults (especially the new right corner window button placement) was unacceptable.  Ubuntu Tweak was invaluable for getting things back/closer to how I liked them.

I am going to do more research on how to save configuration settings before my next upgrade.  It would be nice if there was one place to do this (there may be such a place - I just don't know where it is).

---

### Post by therabyte on 2010-05-22
I had a lot of problems when upgrading from 8.04 to 9.10, but the upgrade from 9.10 to 10.04 was painless!!!

I only had a minor problem with sound which was easily fixed.

Gratz to the Lucid Lynx Team!

---

### Post by cwsnyder on 2010-05-22
First, I should state that I am back in Karmic.  My attempt (today) to run the Live CD convinced me not to install at this time.  I am looking for guidance on how to file a bug properly to reflect my problems. I have a custom /etc/X11/xorg.conf file because my 17" Etronix LCD monitor does not report its resolution properly, which has caused problems in the past.

When I attempted to boot into Lucid, it took me 2 tries at downloading, then burning the CD from the i86 32-bit ISO file.  The first trial (from Canonical's mirror) froze with an error message saying the install failed and would attempt to boot into the desktop.  I hadn't even started the install process, just attempted to boot the CD.  I tried this twice with the same result.

The second trial (from the more local Michigan mirror), after I had burned the new CD, I hit the Esc key to see if the messages would tell me of problems.  I was able to get to the screen where it asked if I wanted to install Lucid or try without changing my installation (Live CD mode).  I went with the trial Live mode.  When I got to the desktop after answering the intervening questions, my ATI Radeon Xpress 200 (RC410 on the motherboard) gave me my Ubuntu normal 800x600 screen (I mentioned that my 1280x1024 LCD monitor EDID doesn't report properly).

Also not functioning (although when I went into the controls, the hardware was listed) was the sound card, an ATI Technologies IXP SB4x0 High Definition Audio Controller (according to lshw from Karmic) from the motherboard.  Windows lists it as a Realtek sound system, and I had used a RealtekAudioLinuxPkg_5.13.tar.bz2 package to update and fix my sound system for Karmic.  Sound from inputs and outputs was muted.

My most serious failure was my motherboard Realtek Ethernet wired port (lshw lists it as RTL-8139/8139C/8139C+) was no longer recognized.  I had had problems with sound and video in other releases and distributions, but Ubuntu had worked with my RTL-8139 port since Feisty (7.04)!

After the results of that attempt, I decided to abort the installation attempt until I could report the bugs and get some real help.

---

### Post by danLinux on 2010-05-22
I have a bad (really bad!) situation with the video card on HP Pavilion dv9320 laptop.
The screen is totally blank, since I have attempted to upgrade the Nvidia drivers, after a new 10.04 install (multiboot with grub: ubuntu 10.04+vista home)

I have extracted the hard drive and memory chips (these components work fine on another laptop) and then powered up the problem laptop (with no HD and with/without mem chips) - and nothing shows on the screen.

I am (still) enthusiastic about Linux in general, but cannot yet accept that after so many years of using Windows, the first time I totally lock myself out of a computer is after updating Linux drivers...:(

Is there anything that can be done to find out if the video is fried or what the problem is?
Where should I look for any solution to this?

---

### Post by Manganic on 2010-05-22
> **danLinux said:**
> I have a bad (really bad!) situation with the video card on HP Pavilion dv9320 laptop.
The screen is totally blank, since I have attempted to upgrade the Nvidia drivers, after a new 10.04 install (multiboot with grub: ubuntu 10.04+vista home)

I have extracted the hard drive and memory chips (these components work fine on another laptop) and then powered up the problem laptop (with no HD and with/without mem chips) - and nothing shows on the screen.

I am (still) enthusiastic about Linux in general, but cannot yet accept that after so many years of using Windows, the first time I totally lock myself out of a computer is after updating Linux drivers...:(

Is there anything that can be done to find out if the video is fried or what the problem is?
Where should I look for any solution to this?

If it's a clean (fresh) install from the 10.04 liveCD, when you boot, hold down the left SHIFT key to enter the GRUB.  Then, choose the Kernel you want to boot, but hit "e" to edit the command line.  Backspace over "quiet splash" and replace it with "nomodeset single"  Hit "enter" and then hit "x" to boot.  

That --SHOULD-- get you into Ubuntu for a one-off, by disabling the Kernel Mode Select (KMS) which tries to load and configure your video based upon what the Kernel thinks is the right settings.  I use ATI graphics, and had a similar problem.  

If that works, then you will need to edit your grub settings to disable KMS permanently.

---

### Post by danLinux on 2010-05-22
> **Manganic said:**
> when you boot, hold down the left SHIFT key to enter the GRUB.  Then, choose the Kernel you want to boot (etc)

That doesn't work, as the screen is totally blank. The external monitor shows no signal either.
There is a known problem with HP Pavilion laptops overheating, and killing video and wifi chips, but why did the video die exactly when upgrading Nvidia drivers in Ubuntu 10.04?
Who knows... 
I'll probably end up sending the laptop in for repairs and then wait until Nvidia drivers are better deciphered before installing again on that laptop.

---

### Post by Manganic on 2010-05-22
> **danLinux said:**
> That doesn't work, as the screen is totally blank. The external monitor shows no signal either.
There is a known problem with HP Pavilion laptops overheating, and killing video and wifi chips, but why did the video die exactly when upgrading Nvidia drivers in Ubuntu 10.04?
Who knows... 
I'll probably end up sending the laptop in for repairs and then wait until Nvidia drivers are better deciphered before installing again on that laptop.

Let me make sure I'm understanding - you get nothing at all.  No BIOS screen, no "press DEL to enter setup," nothing?

If that's the case, you're hooped.

---

### Post by jetsam on 2010-05-22
> If that's the case, you're hooped.

What is this thing called "hooped?"

---

### Post by Manganic on 2010-05-22
> **jetsam said:**
> What is this thing called "hooped?"

[http://www.urbandictionary.com/define.php?term=hooped]("http://www.urbandictionary.com/define.php?term=hooped")

---

### Post by jetsam on 2010-05-22
1. 	hooped 	
	
buy hooped mugs, tshirts and magnets
caught in a situation that has no obvious solution
We are kind of hooped because the guy to interview you doesn't come in to work for another two hours.

---

### Post by Manganic on 2010-05-22
> **jetsam said:**
> 1. 	hooped 	
	
buy hooped mugs, tshirts and magnets
caught in a situation that has no obvious solution
We are kind of hooped because the guy to interview you doesn't come in to work for another two hours.

I was more thinking along the lines of #2 in the definition, but having no obvious solution works too.

---

### Post by jetsam on 2010-05-22
YeaaaaaHHH...  sig that!

---

### Post by SlidingHorn on 2010-05-23
I have to say that I'm more and more impressed with *buntu every day.  I run Xubuntu on my laptop (old Toshiba Portege) and Ubuntu on my desktop -- both of which dual booted with XP.

Each one only has XP for a single reason:

Laptop - I have Act! for my job, and I have yet to find a comparable CRM program to replace it.  I have installed SugarCRM on my VPS, but it just doesn't compare at this point.  (that, and I kinda peeved off a couple of the regulars on the support forum when I was a bit cranky and I don't believe they're gonna want to help me again any time soon, lol)

Desktop - I can't use my girlfriend's Netflix account on Ubuntu yet :(  *sad trombon(ist)* lol

The upgrades to Lucid were absolutely flawless on both machines.  I have a wireless issue w/ the laptop, but that has never been functional under Ubuntu.  I hope to get that resolved (you can take a crack at it @ the link in my sig) soon.  Overall, I'm extremely pleased with Ubuntu and all it has to offer:

[INDENT]-a safe, stable, and secure OS

-all the quality, free (and not pirated -- not that I would do such a thing.......) software you could need or want

-quite simply, the best community-based support forum in existence. (I would venture to say that I doubt I needed to add the "community-based" qualifier)[/INDENT]

It's a wonder to me why it's not more popular than it already is.

---

### Post by emma00 on 2010-05-23
It worked pretty good but only my desktop appears late after upgrading it i don't know about that i think have to report a bug otherwise its awesome always n thanks to all the ubuntu community for bringing this up i wish i can help also but am not good in programming:popcorn:

---

### Post by Ossil on 2010-05-23
So far I have had 3 problems, luckily all of them are solved now.

I did an upgrade from 9.10, which worked fine.

First and biggest problem was display resolution. In 9.10 it used to be 1600x1200, but after upgrade it dropped to 1024x768 (or 1280x1024, I don't remember anymore).

After playing a while with different kind of xorg.conf and installing and removing nvidia binary drivers I managed to get 3600x1200 resolution which I lowered to 1600x1200.

Sorry for not having more details, it was quite hectic and annoying debug process.

At the same time I struggled with language troubles, for that I filed a bug report:
[https://bugs.launchpad.net/ubuntu/+bug/584468](https://bugs.launchpad.net/ubuntu/+bug/584468)
Very annoying as well.

Latest and smallest problem was automatic removal of Sun kava and replacement with OpenJDK. OpenJDK might be "quite ok" but apprently it doesn't work always (ie. gosupermodel.com games), which is good enough reason for me to get rid of it.

---

### Post by rcbell on 2010-05-23
I had graphic-freeze issues with Radeon HD 3200.  See my post at:
[INDENT][http://ubuntuforums.org/showthread.php?t=1491345](http://ubuntuforums.org/showthread.php?t=1491345)
[/INDENT]However, once I added the boot option,
[INDENT]    "radeon.modeset=0"
[/INDENT] I was able to move past it. 

This was a tough one to figure out, because the only other posts I found having to do with graphics/freeze was very specific about that it only happens when running on battery power, but mine occurred with the power cord plugged in. 

Craig

---

### Post by foreverNewbie on 2010-05-23
I've just started the installation process and still don't have it installed (CD I got isn't recognized).  

I am going to see this through so hopefully i'll learn something along the way.

---

### Post by SpectralDesign on 2010-05-23
Upgrade: many problems that are, as yet, unresolved.

Firstly, let me say that I really do love Ubuntu... I've been using it for years and years.  Additionally, before I get to the problems I do want to point out that for the first time ever (be it an upgrade or a clean install) I have completed the process with functional wireless -- every install or upgrade in the past I had to go through one problem or another to get my wireless working (Broadcom Corporation BCM4311 802.11b/g WLAN, fwiw).  Whoohoo!  Kudos!

Now, on to the issues:

external media, be it my external (currently NTFS) hardrive, or a USB memory stick, iPod, or a camera -- Fail.  Unable to get these mounted now, where prior to the upgrade they would all automount. (Making changes to Nautilus in gconf-editor hasn't helped).

Picasa doesn't work anymore :(
/usr/bin/picasa: line 139: 16967 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175: 17063 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\

I did do a remove and install of it to see if that would help, to no avail.

EDIT: found this "workaround" in the forum:
sudo sysctl -w vm.mmap_min_addr=0

Now Picasa seems to be working okay!  I think Google owns this, or maybe Wine, so that it lets the kernel chose the memory map instead of forcing it's own agenda?  Meh.

I'm a bit bummed... if I get time in the next month I may do a clean install for s&g...

At any rate, thanks Canonical, thanks community, thanks Linus, et. al.

---

### Post by n0+4c|u3 on 2010-05-24
I installed 10.04 netbook remix on my Acer Aspire One last night.
It was a completely flawless install. Everything right down to the Atheros wireless worked out of the box.
I got that wild hair feeling in my nether regions and decided to install the netbook remix on an old p3 desktop with an Nvidia fx 5500 video card.
It went mostly flawless except for the screen resolution and the wireless card I forget to install before installing Lucid

First the wireless card went in, rebooted and the realtec based card came right up.
All I had to do was enter the network password and I was on my way.
Next I refreshed the sources and downloaded the proprietary Nvidia driver, then I was able to set my  screen resolution @1680x1050

That was the extent of my troubles. it was much more painless than I expected.
I rather like the netbook remix interface, everything is right up front and easy to find.
Thanks for the hard work guys!

---

### Post by GEZEN Foundation on 2010-05-24
I upgraded from 9.01 to 9.04 to Ubuntu 10.04 on all 3 of our machines: 1 Desktop, 1 Dell Vostro 1000 laptop, 1 HP 500 laptop.

Upgrade seems to work fine on the Desktop. HP500 laptop was upgraded but functionality was unstable or some things weren't usable anymore. (Scanner, network, USB Headset unusable)

You can read the whole story detailed here: [http://ubuntuforums.org/showthread.php?p=9292260#post9292260](http://ubuntuforums.org/showthread.php?p=9292260#post9292260)


Some solutions were;

buy a new scanner
buy commercial scanner software 'Vuescan'
buy analog headsets
clean installs on laptops Ubuntu 10.04 + 1 run of updates (within 2 days apart)

Unsolved:
Wireless networking/internet on both laptops: can find networks but can't connect

Ubuntu loses preferences after shutdown of laptops ( ethernet fall-out, MAC-address lost + disabling of trackpad for double-clicking re-enabled automatically)

A I wrote in the post of the stated link: I propose a new error reporting scheme for Ubuntureleases and specified hardware. Making it more ease for programmers and users to figure out what causes the problems and what changes can be made to software (if possible) to solve them.

Another thing that might help is to reorganise the posting structure of this forum or the search engine within, using tags for Ubuntu-version,hardware-elements,software,issues,etc

---

### Post by Robertjm on 2010-05-24
In the past whenever I updated my desktop computer I'd wipe all partitions except for /home. However, I decided to chance it and give the Distro Upgrade path a whirl. 

Took over three hours to do the upgrade, but I'm calling it a "Flawless" upgrade!! Only a couple of odd things that had to be fixed.

Move the buttons from left to right
Add back Notification icons on panel (volume, bluetooth and mail)
Modify and reactivate third party repos in Synaptic.

Also, I have volume set to mute, but there's still a "drum roll" sound if I hit the wrong buttons prior to actually logging into Gnome, albeit it's not nearly as loud as if I had the volume actually up.

Still have problems mounting my CD/DVD burner, but it's a problem that existed prior to the upgrade which I hadn't spent much time trying to fix.

After logging into Lucid, I get the backdrop, but it seems that it takes a while for the desktop icons, and panel to appear compared to Karmic.

Still, overall, I'm pretty happy with the upgrade process!

---

### Post by juky on 2010-05-24
> **juky said:**
> Upgraded from 9.10. It took 90 minutes both to download around 750 megs of packages and install them (on old Fujitsu-Siemens E8010 notebook with Intel integrated graphics). 

After reboot, could not get into GUI ("ubuntu" logo shows for 1-2 seconds and then nothing). After browsing the forum, find a workaround by permanently editing ```
/etc/default/grub
``` by adding "i915.modeset=1" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash", so it looks like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
```

Saved the file and then ```
sudo update-grub
```.

Original post:

[http://ubuntuforums.org/showpost.php?p=9171045&postcount=11](http://ubuntuforums.org/showpost.php?p=9171045&postcount=11)

Hope it will help someone.

Cheers,
juky

If anyone rans into similar problem, please click "this affects me too" here:

[https://bugs.launchpad.net/ubuntu/+bug/572868](https://bugs.launchpad.net/ubuntu/+bug/572868)

and here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/568779](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/568779)

Thanks,
juky

---

### Post by demios on 2010-05-24
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9348511](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9348511)

couldn't even boot the liveCD, even trying all of the fixes found on the forums. I'm going to see if I can get it to work, but I'll maybe just stick to karmic or try out fedora.

---

### Post by aj_the_first on 2010-05-24
> **frodon said:**
> [SIZE="3"][COLOR="Red"]*** Disclaimer for those willing to analyse this poll ***[/COLOR][/SIZE]
[SIZE="2"]- Most of users voting here are users with issues,
users with painless experience are not likely to come here. So the statistics here do not represent the reality.


Nice.  I wish I could just assume away that my own statistics poll represented a worse form of reality.

Someone already said it: if they are on Ubuntu forums, then they are doing well for themselves on computers, and they likely are fans of ubuntu and can solve some problems.  The poll is most likely optimistic, not full of problem-reporters as you assume.  I would say take the poll at face value and have a happy compromise.
But you can assume what you want.  I guess it is nice to have a pretty picture of reality, it just isn't useful for the Ubuntu users that you are here to help.

I have had many problems on one of my machines (an MSI laptop), the sound still doesn't work, and after all the usual fixes, I suspect it never will.  Wine is terminally broken, as are most of the flash aps that I use.  I am just going to have to switch to Windows on this machine since I have never gotten a version of Ubuntu to be predictable, stable, or even very functional on it.
My Toshiba works flawlessly.  I've had some problems in the past on it when ATI dropped support for my vid card and the open source wasn't ready yet, but since 9.10 it has been great, and the upgrade to 10.04 was even better...  except for that asinine min/max/close buttons on the left.  I was so angry to see that.  I can't believe that a someone would change a format that they have been using since 2004.  It really shows a complete lack of business sense.  the desktop can be modified.  If people want to modify, let them, but don't change defaults between OS releases.

---

### Post by Silvertones on 2010-05-24
My first upgrade went south because I didn't read the release notes so I reinstalled Karmic.
I did the upgrade today from the Alternate CD and it was flawless. All I needed to do is add the "nomodeset" to the boot line. Then I did the NVdia upgrades from sys/admin/hardware. Then the other updates.
My network is running without touching it, dialup works everything.:)
Nice work.

---

### Post by Robertjm on 2010-05-24
Then WHY waste your time with the poll part of this thread? Just post the "Share with..." part and not ask for a poll. 

> **frodon said:**
> [SIZE="3"][COLOR="Red"]*** Disclaimer for those willing to analyse this poll ***[/COLOR][/SIZE]
Most of users voting here are users with issues,
users with painless experience are not likely to come here. So the statistics here do not represent the reality...

---

### Post by scrapmetal on 2010-05-25
Casting one vote for many installs, for many people.
Excellent.
Thanks to all involved.

---

### Post by fancypiper on 2010-05-25
I just upgraded a Mirus Inspiration E09E16 netbook from Ubuntu 9.04 to Ubuntu 10.04.  It took a couple of days to upgrade, but everything went smoothly!

I was amazed!  I had fewer tweaks/configurations to make than for my tower (about a month's time difference)!

Thumbs up

---

### Post by Simon Cropper on 2010-05-25
Hi,

1. Upgraded from 9.10 using Package Update Manager -- slow process using ADSL but finished in 1-2 hours
2. Disappointed that update did not run unassisted, it does require user imput on ocassion and will stop. You need to be around to hit return occasionally. 
3. Update found a hard disk with old bootable XP drive and installed a menu at GRUB asking what I wanted to boot into. Did not want or ask for it to do this. took a lot of mucking around to get the menu to go away (mainly searching for details -- pretty quick once you knew what you are doing)
4. nvidia twin screens now work in TwinSpan. Although screen 1 will not load up the first time that you reboot after any configurational change, e.g. changing alsa-base or loading a new sound card.
5. sound card issues (quiet output) not fixed in 10.4 - installed a new sound card but output volume set at 100% on boot. It can be changed during a session but returns to 100% on reboot.
6. machine boot time actually slower on this machine compared to 9.10, other machines i have loaded 10.4 onto have just worked fine and boot like lightning, but my main machine takes 1-2 minutes longer. Runs fine however once the computer settles.
7. Samba connections were broken after update. Needed to unshare drives (which could not be seen), then reinstall samba, and load up the share drives. then worked fine.
8. PDF-CUPS also did not work after install of 10.4 - again just reinstalled and it worked.

Aside from this the upgrade went well.

UPDATE: Cleaned out my application menu, i.e. deleted unwanted programs, and this caused the system to come down. Gnome panel disappeared and the entire system became unstable. Was only able to log on a another user -- so created a new 'me' and then spent half a day setting up everything again. NOT HAPPY AT ALL. Lucid also does not appear to work well with No Machine anymore - or not very well at least: I know that this is not a supported package but without a peer-to-peer remote desktop alternative that is supported that does not run like a snail I have to use this package. I also removed the nVidia Driver. Not sure if this also caused the system (Gnome Panel) and other things to destabilize. Like some of the others on this forum, constant mini-fixes, wear you down.

Following each reboot I watch the screen in trepidation hoping everything loads up.

Simon

---

### Post by atirox on 2010-05-25
Well, every time i try to install it, it crashes, almost exactly a minute or two after boot. I've tried Wubi, and tried partitioning the drive and installing via boot from CD. I'm starting to think its my computer... The only recent change is the 1GB stick of DDR PC-3200, even though the system is supposed to use PC-2700. However, i'm not sure that its the problem, as Windows doesn't have a problem using it, and i've been stress testing the module with Prime95, which hasn't turned up any errors. I suppose i'll have to run Memtest x86 when i have some time...

---

### Post by paks.dreamer on 2010-05-25
Cleanest, easiest install yet.

I dual boot ubuntu and win 7 (in that order) using the grub 2 loader
/home folder was in a separate partition (best move I ever made)
backed up my package list, so I wouldn't have to manually install apps

I did a fresh install (not an upgrade) and all my preferences and settings were reinstated with absolutely no issue, including wallpaper, bookmarks, you name it.

I thought putting min/max/close on the left was the most ridiculous thing I've ever seen, but then I realised it's near the program menus, and I probably have no reason to linger my mouse on the right side besides habit.  So I'm going to give it a shot and see if I adapt -- possibly not, as I game in windows, and that could get confusing.   I can always customise if I don't like it. :]

I'm very impressed.  Cheers for the great work.

[SIZE=1]~Paks.[/SIZE]

---

### Post by clayd62 on 2010-05-25
I was converting an Dell XPS 140 from XP to Lucid 10.04. The computer had a failed CD/DVD drive, so live CD wouldn’t work.  It took many hours of trying multiple live CDs to decide it was the drive, not my copies of the live CD.  I attempted to install from a USB thumb drive, but the install would hang up on the “choose keyboard type” screen.  Once I got the CD/DVD drive fixed, I was able get the laptop installed without further issues.

Then the real work started.  Media install using the forum how to:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

This took several hours, now I’ve got DVDs playing, MP3s playing.  I’m a pretty happy camper.

THEN, I discovered that firefox will not load web pages.  After several days looking through the forum and thinking that Lucid did not support DSL (there are several forum threads regarding this), I decided that I had network connectivity and the issue was with firefox.  A quick search got me here:
[http://ubuntuforums.org/showthread.php?t=1476688&highlight=firefox+internet](http://ubuntuforums.org/showthread.php?t=1476688&highlight=firefox+internet)

(thread item #2) I tried to disable ipv6 by editing /etc/sysctl.conf, but that did not correct issue with Firefox.
(thread item #12) I then toggled my network.dns.disableIPv6 in firefox and that got the firefox web browser working like a champ.

I also disabled ipv6 on firefox in another laptop that is running 8.04 and now the browsing speed in 10 times faster.  By the way, on my 8.04 machine when 9.04 was officially released, I attempted to upgrade but when firefox quit working I reverted back to 8.04.

Even knowing that linux isn’t Windows or Apple OSX, setting up a Ubuntu machine takes a lot of persistence.  The beginner’s guide is excellent; when I have issues (like the firefox issue) I find myself spending several hours searching the forums and reading deep into each forum’s threads to resolve the issue.

---

### Post by LakesidePark on 2010-05-25
Had problem with Broadcom BCM 57788 ethernet driver dying during DHCP detection on an Dell Inspiron 580.  The solution was to:


[LIST=1]
[*]control-alt-f2 to a command screen
[*]modprobe -r tg3
[*]modprobe tg3
[*]control-alt-f1 back to install screen
[*]continue install
[/LIST]

---

### Post by Metrop021 on 2010-05-25
All right so i was upgrading from 9.10. i was thinking about using 10.04 seriously on my main desktop since i have been using a smaller linux distro (puppy linux) on my old laptop and i was really starting to like it/get used to the entire linux environment. 

I went ahead and ran the upgrade but for some reason i forget it didn't work flawlessly so since i didn't have any serious information saved on it i just went ahead and used the live cd to just install 10.04 over the other partition. For some reason my bios would kick out the cd while i was shutting down after installing, and my screen got flooded with a load of read errors. then when i booted 10.04 there were a lot of problems installing packages and everything, i never saw errors like this in 9.10 so i figured it was because of the random cd eject.

So then i found an old 2 gig sd card, used the live-cd to make it a boot flash drive, and reinstalled 10.04 using the sd card instead of the cd. the install then worked flawlessly, and i was able to use wine/find linux equivalents of any software and games i played. so about after 2 weeks of using linux i felt it was time to just give linux the entire hdd (I have a lot of media (mainly music) and i wanted linux to have easy access to it all, without mounting the windows partition). so I deleted my windows partition and copied my linux partition into the space it used to be (you can't just expand it because of the way the side by side install sets up partitions). got into a hiccup with grub but i posted a topic here before i went to bed and in the morning had responses that helped me fix the problem. then i went ahead and grew my linux partition to the full drive and now everything is working well. very pleased :)

---

### Post by Fire_Master on 2010-05-25
The upgrade from version 9.10 was flawlessly. It takes some time to be completed.
But after the installation I have all the time system crashes. This never happened before.

I have a P5P800SE motherboard, a 3.06 GHz Celeron processor, 512 MB of memory and ubuntu is installed under windows XP professional version 2002 and service pack 3.

If somebody has an answer I will be glad to hear it. Otherwise I move back to version 9.10

---

### Post by Callius on 2010-05-26
Installed fresh from 10.04 live-cd onto my second (of four) hard drive.

It ate my Windows Vista MBR.
My Wireless (RTL8187) won't work for more than a few minutes, and even then it's limited to one "stream" at a time (I guess, I don't know how to explain it... if one piece of software is using the wireless another one can't at all).

So, here I am, back in Windows land.

---

### Post by alibro on 2010-05-26
I have two Fujitsu Siemens Laptops, a S7010 and an E8010. They are quite old (around 5 years) but have worked perfectly with previous versions of Ubuntu. I tried 10.04 last week but cannot get it to install. The CD will boot to the Ubuntu symbol with little dots below it but then the screen goes blank and nothing more happens and I have to power the laptop off. I tried installing 9.10 and upgrading to 10.04 but after a reboot I get the same blank screen. I guess I will have to stick with 9.10 :(

---

### Post by davyzhu on 2010-05-26
Install Ubuntu 10.04 on my laptop from official CD.

Installation and boot up successfully. But a few problems remains.

1. **Desktop random freeze/hang. **
I have encountered the same problem in 9.10. I guess it is caused by Intel graphic driver. Unlike in 9.10, freeze in 10.04 is not so often (twice an hour, 15s each time, and CPU is idle), so I have a rest when desktop hang :)

2. **Boot time longer than 9.04. **
I use bootchart to log the boot time. In 9.04, it's about 30s, and in 10.04, about 40s.

My HP laptop(3 years) info:
CPU: Intel P 2G 
RAM: 1G
GPU: Intel 915

Hope Ubuntu better :)

---

### Post by Dmjthomas on 2010-05-26
Ever since upgrading to Lucid Lynx, I can not burn DVDs or CDs. In Karmic I was able to easily. 

For a while I thought it was the type of DVD-R and CD-Rs I was using, but I went back to the ones that I knew had worked before and they don't work now. Slightly annoying, but I'm sure a fix is out there.

---

### Post by Zsola on 2010-05-26
Upgrade went flawlessly.. about 1 and a half hour from start to finish.
What is strange, that ubuntu now loads slower than the previous... and the loading ubuntu logo is disappeared from startup, but present at shutdown...

---

### Post by iceback on 2010-05-26
Dell GX260 desktop: Upgrade from 9.10 to 10.04lts went smoothly enough, but I lose sight of the cursor after the login screen.  Can control-click to find the current position and can see things arm (to use an old X term) as I mouse over but this makes most things rather difficult.  Haven't seen a clear response to this yet.

---

### Post by juky on 2010-05-27
> **alibro said:**
> I have two Fujitsu Siemens Laptops, a S7010 and an E8010. They are quite old (around 5 years) but have worked perfectly with previous versions of Ubuntu. I tried 10.04 last week but cannot get it to install. The CD will boot to the Ubuntu symbol with little dots below it but then the screen goes blank and nothing more happens and I have to power the laptop off. I tried installing 9.10 and upgrading to 10.04 but after a reboot I get the same blank screen. I guess I will have to stick with 9.10 :(

I have the same E8010 Notebook. You have issues with Intel Graphics. Check here: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

possible temporary solution here:
[http://ubuntuforums.org/showthread.php?t=1472054&page=8](http://ubuntuforums.org/showthread.php?t=1472054&page=8)

and here the launchpad bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511?comments=all)

Basically, the initial solution is to modify grub menu and add "i915.modeset=1" after "quiet splash". Then you can install new version. And after make changes permanent.

Or, you can download and install from live-CD of Ubuntu 10.04 with updated Intel-drivers and 855gm-patched kernel-modules here:

[http://glasen-hardt.de/?p=568](http://glasen-hardt.de/?p=568)

Hope it helps.

Cheers and good luck,
juky

---

### Post by Pott on 2010-05-27
I tried everything I could think of to get the install to not get stuck at the keyboard choice. To no avail. It simply will not install on my PC and I have no idea why. I didn't get any issues whatsoever with Jaunty nor Karmic.

---

### Post by punchdrunkgrunt on 2010-05-27
Upgraded from Kubuntu 9.10 to 10.04. No showstopping problems but about 101 minor bugs that are gradually wearing me down. I have the added disadvantage of using Kubuntu, so I'm getting all the new KDE 4.4 bugs as well as the regular *buntu ones.
I get the impression that none of the devs at Canonical or KDE are familiar with the phrase "If it ain't broken, don't fix it." A bunch of things that worked fine with 9.10 are buggered in 10.04. Example: Plymouth - about 50% of shutdowns and 20% of boots result in the system hanging; and like almost everyone else using proprietary drivers it looks like crap. What was wrong with the old bootsplash?
On the plus side my computer is noticeably faster in many areas, but I'd be willing to take a small performance hit in the interests of stability and ease of use.
I can only hope it all gets sorted before 10.10 rolls around.
:(

---

### Post by rey1321 on 2010-05-28
[SIZE="3"][B]Thinking seriously of going back to WINDOW$
I'm a ubuntu user since 2006, and I'm ready to give up to Bill Gate$:(, why?, cause since I've been using ubuntu=headache, every distro upgrade breaks my system and I have to spent lots of time fixing problems in every upgrade, Lucid Lynx is a _TOTAL MESS_, I've seen hundreds and hundreds of people complaining about it.
nvidia driver doesn't work any more. I can't auto mount my mp3 player any more, my sound system is broken, and the list of problem is growing in this forum.

So, RIP to Ubuntu (ITS ALREADY DEAD), I'm glad that I still have my WINDOW$ XP PROFE$IONAl, BUT AT LEAST I CAN USE MY COMPUTER.[/B][/SIZE]

---

### Post by irv on 2010-05-28
So far I have installed Lucid Lynx 10.04 on a Desktop and a Laptop. The desktop is a no name, with XP professional. It is a Pentium 4 - 1.4 Ghz with 1 Gig of memory and a 120 Gig Hard drive.  (bought it at a yard sale for 25 cents). The Laptop is running Win7 and is a Dell Inspiron 1521 AMD Turion(tm) 64 X2 Mobile Techology TL-58 - 4 Gig of memory and a 350 Gig hard drive. 
I installed Ubuntu along side both WinXP and Win7. Both installs when with out a hitch. The install took a little over an hour on the Desktop (and that included updating OS and software with the install of other packages.) The Laptop install took less then an hour for the same installs. I also needed to plug in the network cable to the laptop because my wireless card is not supported in the install. I need it to install a driver for it.
Very simple process: Plug in the network cable goto System> Administrator >Hardware Drivers. It searches for the hardware and give me an option of two drivers. I used the Broadcom STA Wireless driver. It installed it and I unplugged the network cable and it found my network and made the connection. 
I am sitting in a coffee shop right now, and the wireless just found all the networks in this area and allows me to pick the one I wanted. And after doing this it just connects. 
So far I have found no problem with either of these installs.
In a nutshell, I found 10.04 better then any of the other version of Ubuntu that came out. The few problems I had in the past were not that bad when I think back. 
9.04 did have an issue with my wireless card also and I needed to use a windows driver to get it to work, but there was a great howto out here to help with that.
I would have to say that Ubuntu is getting better with each release. We must remember that with all the different hardware out here you are bound to have some problems with any OS you install. The big difference with Ubuntu is there is always help for those who want to look for it.
I guess if I had one small complaint it would be I have problems searching in the forum for answers to a problem, I use Google to find it, and it take me to the forum for the answer in the end anyway. Maybe it is just me.
That's it! Great stuff Guys and Gals, keep up the good work.
A great OS and getting better.

From a forever user of Ubuntu.

---

### Post by jfl on 2010-05-28
**Kudos to the Ubuntu team !**

Did an on-line upgrade from 9.10 to 10.4 on 2 Lenovo Laptops.
It went like a charm !!!
I always make sure I have the latest updates, close all the apps, reboot and start the upgrade.
I also make sure I have an "alt" CD, just in case.

---

### Post by linfidel on 2010-05-28
I decided to try again with my Dell laptop, which had severe video problems previously.  I had figured out how to fix that problem with a setting in my xorg.conf file, so I did the upgrade.  

At first, it sucked; no multiple desktops, no titlebars, and a lot of the basic keyboard shortcut keys were not only non-functional, but were totally missing from the keyboard shortcut utility (like the run app, run terminal, etc).

I finally decided to change the theme to the new default, Ambiance, from the one used for 9.1, and all my problems immediately disappeared!  Even the multiple desktops came back.

Now, everything works well, and I'm happy.

---

### Post by mrpenguin on 2010-05-28
10.04 sucks *** !!! wish i never did the upgrade, my high speed internet slowed down so much you would think i am on dail up ... my wireless 3GS dont work anymore as well

---

### Post by 73ckn797 on 2010-05-28
My initial fresh install of Lucid went flawless. I was very excited about Lucid and even started a thread about it. It has been after several updates recently that things have gone wrong. I have reinstalled Karmic since there were no problems on 3 computers it was running on before and is now working perfectly.

I did not feel like pursuing the fixes to correct bad updates and broken packages in Lucid. I suspect there are problems in the repo's causing failures to access needed items during updates.

I updated on 2 occasions and since then Firefox would not show dialog on pop-ups at times, I am not talking about ads but information windows or confirmation windows. 

There were broken packages or failure to retrieve items during updates and then Synaptic would not load at all even after restarting the system.

I do not seek an answer to correct these issues. 

I will wait a while until things stabilize with Lucid. That has been my experience and may differ from others.

For myself, Karmic has been the most stable.

---

### Post by consindo on 2010-05-28
> **rey1321 said:**
> [SIZE="3"][B]Thinking seriously of going back to WINDOW$
I'm a ubuntu user since 2006, and I'm ready to give up to Bill Gates:( [/B][/SIZE]

I'm pretty sure that Bill Gates left Microsoft.

---

### Post by ozite on 2010-05-29
I upgraded from 9.10 to 10.04 flawlessly.  Amazingly MythTV still works and nothing was broken.

---

### Post by rods87 on 2010-05-29
Had dual boot Asus netbook with 9.xx and XP.  Performed upgrade to 10.04 that worked but had Grub error messages Mount: mounting none on /dev...... and Chroot: cannot execute /etc/apparmor..... eventually it would boot and operate OK.  Also, Grub menu did not show correct kernel version and would not accept any edits.  Tried a bunch of things to fix the errors but nothing worked.
 
Since I did not have much to lose, I did a clean install of 10.04.  All is well, no error messages, boots faster and has been smooth sailing!

---

### Post by RgnKjnVA on 2010-05-29
> **rods87 said:**
> Had dual boot Asus netbook with 9.xx and XP.  Performed upgrade to 10.04 that worked but had Grub error messages Mount: mounting none on /dev...... and Chroot: cannot execute /etc/apparmor..... eventually it would boot and operate OK.  Also, Grub menu did not show correct kernel version and would not accept any edits.  Tried a bunch of things to fix the errors but nothing worked.
 
Since I did not have much to lose, I did a clean install of 10.04.  All is well, no error messages, boots faster and has been smooth sailing!

I've heard that a fresh install is a different animal and for the first time I did one with 10.04 for my best install experience to date. It seems a fresh install cannot be recommended highly enough.

---

### Post by Frantic_Earthling on 2010-05-29
Installed 10.04 on an Asus UL20A.

Everything works, including suspend/hibernate, with the exception of:

- Screen brightness function key does not work, along with the LCD brightness applet which does not either. Clicking on it with a mouse makes the brightness cursor disappear, though the UP and DOWN cursor keys seem to have a limited effect - no gradual dimming, though, only "low" and "high".

- The screen flickers very briefly once in a while, not often enough to make the laptop unusable, but it is annoying all the same.

---

### Post by sad1sm0 on 2010-05-29
*Upgrade - got many problems that i've not been able to solve*

I usually do a fresh install instead of upgrading, but I heard good things so I figured I'd give it a try.  I don't think I'll ever do that again.  It took way longer than a straight install does in my  experience, and at the end of the day, I was left without some really important programs (MySQL Server and Client both uninstalled on the upgrade--thankfully only the applications, not the data as well--is this because of the Oracle situation or is this normal?)  I had to re-enable my restricted NVidia drivers, no biggy there, but I still don't have x server working correctly.  Immediately after the upgrade I started getting an error whenever I logged in:
```

X Server does not support the size requested

```
  I can't find it in my logs to get a more elaborate explanation.  I've tried removing the xorg.conf file (I've heard this is moot since the new X server isn't using xorg.conf anymore, but who knows) and creating a new one using the NVidia gui, but no go.  Another problem that I am attributing to this is that my virtual terminals (F2-F6 usually) are blank, although I can still log in and use the terminal, just no output.  My Gnome session is on F8 which is odd to me also, but which place each is on doesn't really matter so long as I can use them (Which I can't at the moment other than gnome).  Also, instead of getting splash screens for boot and shutdown, I was getting ugly blocks of color.  Finally, my ability to handle multiple x sessions seems to be crippled as well.  If I lock my screen and have another user login to their account, all is well until they log out and it's time for x to give me back my terminal, it just hangs on a blank screen (can't remember if the screen drops the signal completely or if it's just a black screen, but either way, I can't log back into my own session which is important.

UPDATE:
I have since downgraded to an older NVidia driver which got rid of the posted error, but I have completely lost all of my Virtual Terminals other than my gnome session now (no more ctrl-alt-f2, f3, etc).  I still can't seem to have 2 users signed into gnome simultaneously, and I get a lot of new quirky issues.  Instead of the ugly colored blocks and bars where a splash screen belongs, I get no output at all, (Screen goes into standby).  Overall, I don't see any changes that are an improvement, and although I'm not sure whether this is an x issue or an NVidia issue, these issues are major drawbacks to the upgrade to Lucid.  Again, I did perform the upgrade as opposed to the fresh install like I normally do.

---

### Post by viralmongoose on 2010-05-30
Upgrade did not work, twice. 

Fresh Install worked fine.

---

### Post by gmc on 2010-05-30
> **Frantic_Earthling said:**
> Installed 10.04 on an Asus UL20A.

Everything works, including suspend/hibernate, with the exception of:

- Screen brightness function key does not work, along with the LCD brightness applet which does not either. Clicking on it with a mouse makes the brightness cursor disappear, though the UP and DOWN cursor keys seem to have a limited effect - no gradual dimming, though, only "low" and "high".

- The screen flickers very briefly once in a while, not often enough to make the laptop unusable, but it is annoying all the same.


Put "GRUB_CMDLINE_LINUX_DEFAULT="**acpi_backlight=vendor** quiet splash" in /etc/default/grub control file, issue an "sudo upgrade-grub2" and reboot. That should fix your problem with controlling the screen brightness

G.

re-edited to fix typo :-)

---

### Post by irv on 2010-05-30
> **Frantic_Earthling said:**
> Installed 10.04 on an Asus UL20A.

Everything works, including suspend/hibernate, with the exception of:

- Screen brightness function key does not work, along with the LCD brightness applet which does not either. Clicking on it with a mouse makes the brightness cursor disappear, though the UP and DOWN cursor keys seem to have a limited effect - no gradual dimming, though, only "low" and "high".

- The screen flickers very briefly once in a while, not often enough to make the laptop unusable, but it is annoying all the same.

I found the same problem after doing a clean install of 10.04. I think it has to be reported as a bug. This will happen if I close the cover of my laptop, and if I am outside, I can't even see the screen to fix it. The only fix I found is to open the power manager, and even though the brightness is set to 100%, I need to just move it and the screen goes bright again. By the way I have a Dell Inspiron 1521.

---

### Post by irv on 2010-05-30
> **gmc said:**
> Put "GRUB_CMDLINE_LINUX_DEFAULT="**acpi_backlight=vendor** quiet splash" in /etc/defaults/grub control file, issue an "sudo upgrade-grub2" and reboot. That should fix your problem with controlling the screen brightness

G.
Thanks for the tip. It worked, but you had one typeo, the grub is in /etc/default/grub, just drop the "s" on defaults. I also had to cd to /usr/bin to run the "sudo upgrade-grub2."
After rebooting this fixed the problem.

---

### Post by Lisimelis on 2010-05-30
I did an upgrade from 9.10 yesterday and was surprised once more from the speed and efficiency of the upgrade package. The biggest surprise came when i restarted!!!! In my old Toshiba satellite with 256Ram the previous version booted at 2m 15 seconds, with 10.04 in 1m 15s it was already up and running and connected to the net. BIG BRAVO UBUNTU from Thessaloniki Greece. This old laptop is revived!!!!

---

### Post by e.farrell on 2010-05-30
Congratulations to the Ubuntu Developers and Community on a great product.

Installed Lucid yesterday and after one or two small problems everything works perfectly. (The forums solved  any problems I had)

I had tried previous Ubuntu versions but always found some little things that didn't quite work(wireless, display resolution) so went back to Windows. Lucid just worked and is a superb operating system.

best wishes
Enda.

---

### Post by Janeleaper on 2010-05-30
I'd had problems with 9.10 on both our households Dell computers.  Probably I'd upgraded too many times without doing a fresh install, but 9.10 was buggy and unstable on both machines.  

One machine eventually failed to boot and I had a nervous time restoring the system and retrieving my documents.  I did a fresh install of 9.10 on this machine and then upgraded to 10.04.

That went very smoothly, and I'm very happy with Lucid.  No problems with hardware compatibility (printer and webcam), and  I like Lucid's looks.  In fact, I can't find anything to complain about!

---

### Post by circletide on 2010-05-30
I've been an Ubuntu user since 8.04. My upgrade experience on a Thinkpad T60, Intel Core Duo,T2500 @ 2.00GHz:


[LIST]
[*]Two and a half hours to upgrade, install, clean up, etc.
[*]First restart: complete hang immediately following kernel command line, followed by odd corrupted graphics (similar to: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568031](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568031)).
[*]Hard restart (pressing button down) would then enable me to load Ubuntu successfully. This had to be done every time the computer was shut down. On restart, the computer did not hang.
[*]Followed the advice on above bug report; would then load at least, but very slowly with odd resolution on splash screen and login.
[*]First instance of trying to use the internet - Firefox wouldn't load. Tried starting in safe mode and removing all add-ons. Still nothing - just a white flash when the icon was clicked. Eventually found this which corresponded to my error messages: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/563036](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/563036) . Uninstalled libmoon - firefox worked.
[*]Tried to alter appearance under System > Preference > Appearance. Received error message if I tried anything other than Desktop Effects: none.
[*]Tried to use the new Broadcast accounts feature. After several instances of the program freezing when trying to connect to Facebook, I managed to add a couple of accounts.
[*]Tried to sign up for Ubuntu One. The option to add computer did not display; this solved it: [https://wiki.ubuntu.com/UbuntuOne/FAQ](https://wiki.ubuntu.com/UbuntuOne/FAQ)
[*]Tried to play some music. Songbird (from previous install) loaded but would not play sound. Tried Rhythmbox - very impressed with look and feel, but still no sound. Looked for volume applet to try and check mute settings - applet was not there. Retrieved applet with 'Add to Panel' > 'Indicator Panel' - no hardware recognised.
[/LIST]
At this point having tried and failed to start the computer, access the internet, use any integrated web features or get any sound from my machine I figured a clean install would be best. This took an extra 4 hours or so to back up my data, burn a disc and install.

Install experience: great. Basically worked out of the box: managed to import my Thunderbird and Mozilla profiles without any difficulty, mail and web fine, started using rhythmbox with sound (a huge improvement over Songbird), signed up to Ubuntu One, all applications working great.

This has been my most disappointing Ubuntu experience so far - completely draining and frustrating. I know my way round the terminal a bit, but this amount of effort to get a desktop that **just works** is unacceptable - especially when i had so few problems with 9.10. The ironic thing is that if I had simply clean installed, I'd be saying how great the platform is. It's a shame that such a great OS is marred by such initial problems in the upgrade - I'm sure it will put many off. I'll still be an Ubuntu advocate, but there's no way I'm ever upgrading again - clean install for me every time.

---

### Post by WinRiddance on 2010-05-30
**Installed Lucid 4 times so far, ****on 4 different machines**, three of which were laptop computers. Two of the laptops have dual displays. None of the computers was more than 2.5 years old and two of the computers are dual-booting with WinXP. Oh, and three of them were upgrades from 9.10 Karmic via the update manager while the last computer was a direct fresh install after formatting the partition to ext4 file format. 64bit on three of the machines, 32bit on the other one.

I wouldn't go as far as to say that the installations/upgrades went flawlessly, but they involved _less problems than I've encountered on many Windows machines_ in the past. A little quirkiness here and there with a simple fix that can usually be found pretty quickly online. Overall **I'd rate Lucid Lynx a 9 out of 10** and my upgrade/install experience an easy 9 or even a 9.5


**If you're gong to use Lucid**, download the newest ISO image and don't use one from 3 or 4 weeks ago. Make sure the partition for it is **formatted in ext4** which is the new file system that should be used by default. Make sure your CD drive is bootable and copy the ISO on a regular blank **CD** as opposed to a DVD disk. Don't forget to use ISO mastering software since most generic CD burning apps won't be able to burn an ISO image properly.

If you're a "die-hard gamer who's addicted" to Windows games only, you may want to reconsider using Ubuntu 10.04 (or any version of Ubuntu) since 3D chip manufacturers are still experiencing quite a few problems with Linux compatibility and 3D game engines. I don't use the term "addicted" lightly because I personally know some, and have noticed additional people online who are prevented from making a switch for that reason alone ... oh, no, what about my precious windows games that I can't live without ... ??? Well, **there are close to 500 games** available in the Ubuntu software Center and if you search google for Linux Games you'll find hundreds more, including many 3D shooters, RPG, and so on.

If gaming is not an issue, **Ubuntu 10.04 Lucid is an OS that I would recommend to absolutely anyone** _from child to senior citizen_ (my 75 year old mom is getting her Ubuntu soon too - she's been with Windows and MS Office for clsoe to 10 years now). Many people seem to forget that Windows had more than it's share of problems for many years, to include zillions of installation/driver/hardware issues. Ubuntu is no different, but in my opinion solutions to Ubuntu problems can be found much easier if you're willing to be a little patient, and if need be, roll up your shirtsleeves just a little. That's my 2 cents worth ...

---

### Post by Lelouch Yagami on 2010-05-30
the only major problem im having is that compiz isnt working right. it will not turn on for anything. it was working on both ubuntu 9 and linux mint before i installed 10.04 to take over completely and now it wont let me use compiz effects at all i cant even use wobbly windows please help

---

### Post by irv on 2010-05-30
> **Lelouch Yagami said:**
> the only major problem im having is that compiz isnt working right. it will not turn on for anything. it was working on both ubuntu 9 and linux mint before i installed 10.04 to take over completely and now it wont let me use compiz effects at all i cant even use wobbly windows please help

Before it worked for me on my desktop, I had to load third party driver from System> Administration> Hardware Drivers. I also had to load Compiz Config setting Manager.

---

### Post by iceback on 2010-05-30
Well don't worry about the 'invisible cursor' any more.  None of the kernels available (all the way back to .26 though they all claim to be 10.04LTS) will boot (though the old Windows XP still works properly, suggesting the hardware is generally ok)

wtf

---

### Post by bmilner on 2010-05-30
Upgrade left me with a non-functioning computer as was the case with the last one, Was getting boot IO errors. Found solution on net, because fstab referred to non-existant hd, boot hung before getting console. Burnt rescue disc and removed offending fstab line and boot went further, was missing some package dependency and that fixed more boot/init issues (forgot which one it was). Mouse is non-functional sometimes until i switch to console and then back to gui.


Summary, Upgrade - serious problems, some solved some not.

---

### Post by etdsbastar on 2010-05-30
many thinks to be changed or upgraded, such as i am experiencing problems with vlc, its hanging or suddenly exiting while playing anything.

Same bug with Rythmbox,

Problems with Hybernate, system working slower for upto 10-15 minutes after waking up from hibernation.

---

### Post by sdbrogan on 2010-05-30
On a Dell mini netbook - installed easily with no problems at all.  On a desktop with Sempron 3000+ CPU &  GeForde 5500 graphics card, won't work at all - freezes within seconds of booting up.  Still think one of the advantages of Windows is that it seems to install on pretty much anything.

---

### Post by davoudi on 2010-05-30
Everything works well except the graphic card, nvidida GeForce 310M.

---

### Post by iceback on 2010-05-30
If you're having trouble, what chance do I have?  rjs

---

### Post by irv on 2010-05-31
Have you ever been going to a website and then get a error saying the page did not load? Or have you ever downloaded a file to fine it was corrupted? I can answer yes in both cases. Well, think about it, when you are doing a upgrade over the Internet, there is always the change of something going wrong. Doesn't installing or upgrading from a CD sound more logical then trusting an Internet connection?
I find that when I install from the CD everything (or just about everything go well), but when I do upgrades over the Internet I sometimes have problems.
I guess the big question I have here is with all the things I see happening here in this thread could some of them be the fault of a corrupt file or something going wrong with the upgrade over the Internet? 
Just a little food for thought.

---

### Post by cusinndzl on 2010-05-31
I had an almost perfect server upgrade. The only problem I had with the server upgrade was related to my IRC server. The desktop version had slight problems with a few applications. Overall the upgrade was great.

---

### Post by irv on 2010-05-31
> **cusinndzl said:**
> I had an almost perfect server upgrade. The only problem I had with the server upgrade was related to my IRC server. The desktop version had slight problems with a few applications. Overall the upgrade was great.
My server install went perfect. But just prior to the release of 10.04 we had a transformer blow in my area and destroyed my server. I had to replace the motherboard, memory, power supply, hard drive. Basically a complete rebuild. So I just install 10.04 Desktop version and loaded all the server software, reset my configuration files and was up and running in a couple of hours.

---

### Post by tanmays on 2010-05-31
Did a clean install and dual booting with Windows 7.

Had some problem Installing because of faulty ISO file. Downloaded the ISO from a torrent and the installation completed like a charm.

Now, Ubuntu 10.04 is my mail OS with occasional Windows use (mostly for some wicked websites which require exclusive use of IE)

Kudos to the Ubuntu Team for making linux so user friendly.

---

### Post by donaldt on 2010-05-31
Update manager, with no bit torrent, box selected "10.04 LTS is available" and my Internet upgrade worked without problems.  Time 1.5 hours.  Lost my favorite background photo but all worked well.

Dual boot with Grub 2 still opens windows XP pro from the grub menu.  I don't know if I have the latest ext4 files system, but whatever is there works good enough for me.

Perhaps waiting 30 days helped, but I am pleased with the outcome.

donaldt

---

### Post by TechnoCog on 2010-05-31
Install was easy using the update manager, got some weird message about missing parts, however it hasnt seemed to make any major problems.

I'm running on an Acer timeline 4810TZ, in Karmic I had to use the work around to switch to the low power GPU thats now gone, so my battery life has gone form 8 hours down to 3, thats a major issue for me as I was considering a full change from my dual boot with win 7 purely to Ubuntu but not now.

Also its running a lot hotter.

---

### Post by mpolito1969 on 2010-05-31
I upgraded from version 9.10 as the UMTS connection didn't worked properly in that version. With 10.04 it didn't work at all.

I asked for support on this forum one month ago ([http://ubuntuforums.org/showthread.php?p=9345908#post9345908](http://ubuntuforums.org/showthread.php?p=9345908#post9345908)) I didn't get any reply yet. I asked for "meta" support ("where can I find some support?"), you can see by yourself how many replies I got: [http://ubuntuforums.org/showthread.php?p=9266274#post9266274](http://ubuntuforums.org/showthread.php?p=9266274#post9266274) (OK... don't waste your time, it's zero again).

I reported a bug on launchpad ([https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/576599](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/576599)) which up to now (three weeks) has not been taken into consideration.

I wrote to the modem-manager mailing list, got a suggestion but didn't solve the problem.

I wrote on Ubuntugeek and got one suggestion: reinstall everything from scratch. I did it, now UMTS connection works perfectly but Firefox is completely dumb. I can listen to mp3, I can watch mpeg movie but I can't find a way to listen to Youtube video (for instance). I followed the suggestion I found here [http://ubuntuforums.org/showpost.php?p=4928900](http://ubuntuforums.org/showpost.php?p=4928900) but when I run "pavucontrol" all what I get is an everlasting rotating wheel...

No need to say I'm very disappointed.

Ciao,
Max

P.S.
BREAKING NEWS: I made a reboot, now Ubuntu is aligned with Firefox: completely dumb. In [http://ubuntuforums.org/showpost.php?p=4928900](http://ubuntuforums.org/showpost.php?p=4928900) there is something wrong with Ubuntu 10.04.

I wonder if I will ever get out of this nightmare...

---

### Post by irv on 2010-05-31
> I can listen to mp3, I can watch mpeg movie but I can't find a way to listen to Youtube video (for instance).
mpolito1969, did you load the codecs.
[ATTACH]158956[/ATTACH]

---

### Post by mpolito1969 on 2010-05-31
> **irv said:**
> mpolito1969, did you load the codecs.
[ATTACH]158956[/ATTACH]

I can't find that codec:
[IMG]http://img217.imageshack.us/img217/2333/screenshotsynapticpacka.png[/IMG]

---

### Post by fancypiper on 2010-05-31
Lots of people are unaware of the [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683) and/or [What To Do After A Fresh Ubuntu Install: A Script For Ubuntu 10.04 Lucid Lynx](http://www.webupd8.org/2010/04/what-to-do-after-fresh-ubuntu-install.html).

I believe these two guides would solve 98% of the problems.

---

### Post by irv on 2010-05-31
good post fancypiper, and I like you signature.

---

### Post by dr4c4n on 2010-05-31
upgrade went alright, albiet a little long, problem though: any cds or dvds I put in my drive do not automount unless I reboot the machine. Does anyone have a fix for this?

---

### Post by lenovot400 on 2010-05-31
I use a Lenovo T400,  and I upgraded from 9.10 to 10.04. 

The upgrade has been a total catastrophe for me. I can only start using the Kernel 2.6.31 recovery mode and somehow my thunderbird installation is gone. Until now I am unable to figure out how to start without recovery mode. I used essentially every troubleshooting option and it still does not work.

If I could undo the upgrade I would.

---

### Post by josephe on 2010-05-31
Hi All
 
Did the upgrade about 2 weeks ago. System seemed ok apart from loosing my object docker (apple lookalike launchpad) and my Evolution mail client seemed gone, until I dug into Internet Apps (I think) and found the Evolution Client. Luckily when I launched this I found all my mail. I thought, great, But then...
 
A few days ago, for some reason when I boot (by the way I dual boot Ubuntu and Windows 7) and choose Ubuntu I get an error message something about not being able to find /boot. I leave it and after some time (probably a minute or two) the machine boots and seems ok.
 
Help? 
 
My machine is a Dell Inspiron 1520 (about 3 yrs old)
 
Thanks
 
Joseph

---

### Post by dr4c4n on 2010-06-01
> **dr4c4n said:**
> upgrade went alright, albiet a little long, problem though: any cds or dvds I put in my drive do not automount unless I reboot the machine. Does anyone have a fix for this?

New issue created a bug report for this, if anyone else is having difficulties, automount only works after reboot, and randomly decides to umount at different time intervals, for dvds. See bug report here: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/588121](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/588121)

I have tried to fix as per bug report #546992. However still no luck.. :)

---

### Post by mpolito1969 on 2010-06-01
> **fancypiper said:**
> Lots of people are unaware of the [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683) and/or [What To Do After A Fresh Ubuntu Install: A Script For Ubuntu 10.04 Lucid Lynx](http://www.webupd8.org/2010/04/what-to-do-after-fresh-ubuntu-install.html).

I believe these two guides would solve 98% of the problems.

Fancypiper, with all due respect, the first thing you read on the Ubuntu site is:

"Super-fast and great-looking, Ubuntu is a secure, intuitive operating system that powers desktops, servers, netbooks and laptops. Ubuntu is, and always will be, absolutely free."

Is "intuitive operating system" correct for something that requires so much troubleshooting after a fresh installation on a three years old laptop (this is to say that I'm not using some sort of very innovative hardware)?

I'm sorry to be so argumentative, but it's really disappointing when you have a problem and you don't find solutions (UMTS) or you find three hundred tutorials/posts each of them suggesting something different for the same problem (audio problems in Firefox), and you have to apply 98% of those suggestion without even knowing what you are doing to your sustem.

Ciao,
Max

---

### Post by killer62491 on 2010-06-01
yeah im having trouble getting the dvd-r i wrote the .iso file to to mount. whenever i try to mount it in a terminal, i get this code: 

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

any idea whats up....? i'm running karmic presently, this is the first time i've had any problems with it (karmic, that is). any help is greatly appreciated!!

EDIT: also, please pm me if possible with help....

---

### Post by irv on 2010-06-01
> **josephe said:**
> Hi All
 
Did the upgrade about 2 weeks ago. System seemed ok apart from loosing my object docker (apple lookalike launchpad) and my Evolution mail client seemed gone, until I dug into Internet Apps (I think) and found the Evolution Client. Luckily when I launched this I found all my mail. I thought, great, But then...
 
A few days ago, for some reason when I boot (by the way I dual boot Ubuntu and Windows 7) and choose Ubuntu I get an error message something about not being able to find /boot. I leave it and after some time (probably a minute or two) the machine boots and seems ok.
 
Help? 
 
My machine is a Dell Inspiron 1520 (about 3 yrs old)

 
Thanks
 
Joseph
I have almost the same setup. I have a Dell Inspiron 1521 with Ubuntu and Windows 7. I have one swap drive with Ubuntu 9.1 and Vista. I took this drive out and put in a new drive, Installed Windows 7 and a clean install of Ubuntu from a CD. Everything works, The only thing I had to do was install a third party driver for my wireless. I am not sure what is causing your problem but I would start by looking in log files to see if you can find something there.

---

### Post by Contra75 on 2010-06-01
Almost 40% failure of Lucid installs, including me on my Dell 700m laptop, after "upgrade" from Karmic.

What a shame!!! It should have never been released. :oops::evil::arrow:

I will be (very reluctantly) going back to Windows.

---

### Post by lordyosch on 2010-06-01
Made the switch this afternoon (week off work so no stress if it broke my PC!).

All systems functioning normally as far as I can tell.


Happy days.

Jay

---

### Post by adamsiddhi on 2010-06-01
I tried installing Ubuntu 10.04 64 bit today and it failed miserably. Not only that but I damaged my Vista OS which took a long time to repair. Thank god for the auto repairing software built in. 

I have described my installation woes in detail over here: 

[[COLOR="Indigo"]**http://superuser.com/questions/147854/problem-installing-ubuntu-10-04-64-bit-side-by-side-with-vista-by-using-a-bootabl**[/COLOR]]("http://superuser.com/questions/147854/problem-installing-ubuntu-10-04-64-bit-side-by-side-with-vista-by-using-a-bootabl")

If you are wise in the ways of the Ubuntu 10.04 installation process then I would love for you to check this problem out. Seems like it is a rare one. 

Thanks,
Adam

---

### Post by tekkidd on 2010-06-01
Did a fresh install of 10.04. 

No major issues other than the ugly boot screen which took me about 30 min to fix.

---

### Post by jetgraphics on 2010-06-01
Attempted to do clean install of ubuntu-10.04-server-amd64.
Problem: after install, and reboot, screen goes black. Monitors show "no  signal" warning.

CPU: Phenom 9600
MB: ASROCK A780GMH/128M (AMD 780G chipset)
RAM: 4 GB DDR2-800
Video Adapter: ATI (AMD) Radeon HD 2600 XT

Is this a common bug with AMD/ATI video chipsets?

---

### Post by ausmuso on 2010-06-02
OK, I broke my own rule about not upgrading more than once every 1-2 years. I had Karmic humming perfectly on two machines. However, with all the hype about Lucid I just had to have a go and updated one. I used a combination of DVD and internet.

The upgrade went fine, Including wireless internet etc.. I had just two minor niggles:
1. The Firefox icon had disappeared from my desktop. I soon retrieved that.
2. The screensaver/powersave combination malfunctioned. That got fixed by downloading some updates.

Concusion: works fine, just as well as Karmic on the other machine.

Is Lucid a real improvement on Karmic? Not sure. The exit/scale buttons on the Gnome application windows have migrated from the top right-hand to left-hand corner. This should be progress?

Will I upgrade my other machine? Not for the time being. I'm too busy using it!

---

### Post by wavesound on 2010-06-02
> **circletide said:**
> 
This has been my most disappointing Ubuntu experience so far - completely draining and frustrating. I know my way round the terminal a bit, but this amount of effort to get a desktop that **just works** is unacceptable - especially when i had so few problems with 9.10. The ironic thing is that if I had simply clean installed, I'd be saying how great the platform is. It's a shame that such a great OS is marred by such initial problems in the upgrade - I'm sure it will put many off. I'll still be an Ubuntu advocate, but there's no way I'm ever upgrading again - clean install for me every time.

Yep I have finally come to this conclusion myself.
Must do a clean install.
I have no sound on here and as you know it all worked before.
How do they take a working sound system and hose it?
I could understand a clean install not seeing the sound card but an upgrade is a working system!:confused:

Cheers
Bob

---

### Post by irv on 2010-06-02
> **wavesound said:**
> Yep I have finally come to this conclusion myself.
Must do a clean install.
I have no sound on here and as you know it all worked before.
How do they take a working sound system and hose it?
I could understand a clean install not seeing the sound card but an upgrade is a working system!:confused:

Cheers
Bob

I have been following this thread since the day I found it. After reading through 105 pages of posts and seeing all the problem many have had with the upgrade, I think I might have an answer to why things seem to get broken.
We must remember that this is an open source OS and being such there are third party driver that can not be included in the install or upgrade. I believe because of this fact part of the blame lies with the hardware manufactures who do not support their products with Linux drivers. Until they do we may never get around this problem. Microsoft has hardware companies eating out of there hand. I believe it has something to do with money.

---

### Post by bondo101 on 2010-06-02
Dual boot with karmic and lucid . I bought a distro on a cd on line, split the 120 gig i'm using into half , Karmic on one side and lucid on the other. karmic worked flawlessly for the past 2 months. Lucid works fine also seems to be a littlebit of a  memory hog. I only have 2 gigs of mem with a amd dual core 3800 cpu. so far for lucid its the mail that's giving me problems , might be the server. any way why are so many users fighting with the distros. the problems i have are very minimual. I don't get it Whats up lucid ?
hang in there everybody its works i know, but not with the upgrade over the internet its terrible get the cd.:KS:popcorn:

---

### Post by liniaal on 2010-06-02
I always have a full install, as i just seem to have better experiences with it. I use a really old IBM T42 laptop. Until this release, almost every ubuntu release made a change for the better. Not this time :(. LiveCD experience is very good, boots from the cd in less than a minute. After install & reboot: no network, not cable nor wifi, no sound, big logs because of a fd0 device not ready or not found, not even able to start to graphics/gdm at once (i come to terminal login and then i can 'startx'). I am very disappointed and at the moment, have not the faintiest idea about what i could do about my uber failed installation.. I'm typing this back on the livecd. Ideas anyone, or need for details? Any help is appreciated and you can expect me to pay your next cup of coffee when you're around. Not all negative though, I do love the new theme/skin and top menus etc.
But this installation is unworkable :|

Edit: is the ext4 implementation or so different in this release? it would explain a lot because i DO use my old /home partition (just new username because elseway it would not install)

---

### Post by Black Trench Coat on 2010-06-02
[http://larrymulcahy.blogspot.com/2010/05/ubuntu-1004-lts.html](http://larrymulcahy.blogspot.com/2010/05/ubuntu-1004-lts.html)

---

### Post by jeffreyldavidson on 2010-06-02
I could never get it to install - Toshiba L505 Intel. I guess I have to wait until 10.10 to see if the kernel is matured to be able to install.

---

### Post by mantorpcity on 2010-06-02
Upgraded from 9.10, took 8 hours total. Observations, my PC still freezes every now and then and refuses to respond for a minute or so. Should a 2.53 pentium 4 with 2GB Ram not be enough?
Looking thru the features everyone mentions the me menu, why on earth isn't it called that? Indicator Applet isn't exactly a dead ringer for Me Menu.
Also not crazy about the minimize maximize switcheroo, but I'll leave it for a while to see if I can get used to it.
Oh and my volume switch disappeared, but an applet reappeared when I added my indicator applet.
Pulse audio seems better than in Karmic, doesn't stop playing or gets as choppy as quickly as before.
Overall, glad I did it.

---

### Post by mpolito1969 on 2010-06-03
> **irv said:**
> I have been following this thread since the day I found it. After reading through 105 pages of posts and seeing all the problem many have had with the upgrade, I think I might have an answer to why things seem to get broken.
We must remember that this is an open source OS and being such there are third party driver that can not be included in the install or upgrade. I believe because of this fact part of the blame lies with the hardware manufactures who do not support their products with Linux drivers. Until they do we may never get around this problem. Microsoft has hardware companies eating out of there hand. I believe it has something to do with money.

Sorry but I strongly disagree with this.

Many posts are about problems that happened AFTER the upgrade, the hardware has not been changed during the upgrade process, the blame is not to be put on HW manufacturers. They have their share or responsibility in other Linux problems but when it comes to a software upgrade I can hardly see what they could be held responsible for.

HW that worked BEFORE the upgrade should keep working AFTER it.

I had a UMTS modem that didn't work well in 9.10 but it worked, after the upgrade it stopped working. Another problem I have is about Firefox no more playing audio from Youtube (and I've seen there are lots of post about this) this is not a hardware related problem either, as I always listened audio from Youtube before the upgrade, with the same HW I have now.

I think the best way to get out of this situation is raising the priority to support and lowering it on new SW development. For 2-3 weeks at least developers should be asked to devote more time to community support and less time to development.

Ciao,
Max

---

### Post by wavesound on 2010-06-03
> **mpolito1969 said:**
> Sorry but I strongly disagree with this.

Many posts are about problems that happened AFTER the upgrade, the hardware has not been changed during the upgrade process, the blame is not to be put on HW manufacturers. They have their share or responsibility in other Linux problems but when it comes to a software upgrade I can hardly see what they could be held responsible for.

HW that worked BEFORE the upgrade should keep working AFTER it.

I had a UMTS modem that didn't work well in 9.10 but it worked, after the upgrade it stopped working. Another problem I have is about Firefox no more playing audio from Youtube (and I've seen there are lots of post about this) this is not a hardware related problem either, as I always listened audio from Youtube before the upgrade, with the same HW I have now.

I think the best way to get out of this situation is raising the priority to support and lowering it on new SW development. For 2-3 weeks at least developers should be asked to devote more time to community support and less time to development.

Ciao,
Max

HI 
I agree if the hardware has been working for years , My delta card is fully supported in 64studio, this is a problem with the OS itself.

At the moment Totem has no sound or Firefox yet I can now listen to Spotify no problem.

This is sloppy development, and a lack of leadership or care.

The main problem I see here is lack of an answer, It seems if it doesn't work that's tough and your on your own.

Also on such a high profile OS as Ubuntu now is, this demeans all of Linux putting us back into the realms of tech heads only.:(

Ubuntu has raised the profile of Linux in general but this can be used by our detractors in a negative way to spread more FUD.

Cheers
Bob

---

### Post by KwukDuck on 2010-06-03
New install on Asus EEEPC 1000H

Works okay, some issues though:

- Wireless WPA+WPA2 disconnects after a minute of connection (requiers reboot to get connected again at all)
- A lot of random desktop freezes (kernel keys also not working then), what i heard it's related to the kernel having issues with the i9xx chipsets.

Using a custom kernel to solve the Wireless issue but it doesn't fix the stability issue, also i don't like to use custom kernels, at all!

Other then that i'm a very happy user.

---

### Post by sai koushik on 2010-06-03
hi all ,
i want to install ubuntu 10.04 on my studio in dual boot mode.

i tried to install , it installed , but after restrting from second time onwards blank screen is coming and boot options are not coming ,

i tried for 4 times but unsuccessful , i did below steps

-my hdd is 320 so i seperated 200(for win 7) , 50 (for personal ) , 40 unallocated for linux

-inserted ubuntu 10.04 rc1 cd

- in fourth step when selecting disk , i selected manual option(3rd)
- and i selected 40GB unallocated and formatted to ext4 and selected as root and install
- after reboot in boot options i can see 4 options i selected win 7 and from win7 i restarted
- after that black screen coming , boot options are not coming


can anybody help me please ?

---

### Post by pike747 on 2010-06-03
Began with Lucid beta and it has been working very well. Some issues but most are solved. Exceeded my expectations, a lot.

---

### Post by KaYnemO on 2010-06-03
Upgraded from Karmic - few unsolvable problems: 3945 loses wifi and won't reconnect (needs a manual shutdown for the module to bring up the network) also no more automatic connection with wimax external modem - only through terminal. Otherwise seems to be running somehow :)

---

### Post by irv on 2010-06-03
> **mpolito1969 said:**
> Sorry but I strongly disagree with this.

Many posts are about problems that happened AFTER the upgrade, the hardware has not been changed during the upgrade process, the blame is not to be put on HW manufacturers. They have their share or responsibility in other Linux problems but when it comes to a software upgrade I can hardly see what they could be held responsible for.

HW that worked BEFORE the upgrade should keep working AFTER it.

I had a UMTS modem that didn't work well in 9.10 but it worked, after the upgrade it stopped working. Another problem I have is about Firefox no more playing audio from Youtube (and I've seen there are lots of post about this) this is not a hardware related problem either, as I always listened audio from Youtube before the upgrade, with the same HW I have now.

I think the best way to get out of this situation is raising the priority to support and lowering it on new SW development. For 2-3 weeks at least developers should be asked to devote more time to community support and less time to development.

Ciao,
Max

	Here is what I am trying to say. My wireless card is not supported in Ubuntu. After every upgrade I had to Installing Windows driver using ndisgtk (ndiswrapper graphical interface). After the upgrade I had to repeat the process or my network did not work. (In other words it got broken by the upgrade). This happens with video, sound wireless cards, etc. This is the point I was trying to make. Not all the problem are HW many are SW also. HW is still a big problem.

	(Just for the record I didn't have to use ndiswrapper this install. It was made easier by being able to install using Hardware Drivers from the System > Administration menu. It just found it and install it.) 
	Another big problem is SW developers do not develop SW on ever platform out here so some SW will not run right with all systems without being tested first. I believe there is not enough testing going on before releasing new upgrades. There are to many bugs in the new releases. Grant you will never get them all, but it seems there are way to many with ever release. Maybe they are being released way to fast. (Just like Vista was pushed out way to soon and I was stuck with it until the release of Win7). But in the case of Microsoft it was just a way to get more money out of me.
OK I will get off my soapbox.

---

### Post by SilverWolf240 on 2010-06-03
I did a clean install of Ubuntu 10.04, and the only problem that I had was the Zebra stripe freeze, which I was able to solve quite easily.

---

### Post by PEZGUN on 2010-06-03
I started this sytem on Jaunty Jackalope, had no problems to speak of, upgraded to Karmic Koala about a month before Lucid Lynx came out and had only a few additional issues - the most serious of which was setting up the display.  I had to manually modify the xconfig file to use the "ati" driver, create appropriate 1440x900/60Hz mode line with GTK and put it n the modes section, then things went well.

I upgraded to Lucid Lynx about a week after it was released.  Even more issues than before, but not impossible.  The correct video was retained but some new unusable modes got added.  Also, everything in the Alsa Mixer was set to "muted" and volumes set at 0%  for some reason.  Once I fixed that, I had audio again.  The final issue is that any music CD player application will at first play, then skip, then jump to the next track.  It sounds as though the buffering might be turned off at the device handler level but I don't know how to activate it.  I've got an update running right now, maybe it's fixed already!

Not to worry, I realized that I went to each release at a point earlier in it's lifespan than the release before, so with less time in development, it's reasonable to expect more fixes needed.  My system still won't pass all the "System Testing" checks, but at least it's now comfortably useable again.

Pez

---

### Post by rediron on 2010-06-03
Long time Ubuntu user, first try Lucid:  I put in a new hard drive in the first sata plug and installed Lucid _64.  It was a really nice install, with prompts being few and strait forward.  It did manage to see all my other hard drives, some with OSs, some without, incorporated the old OSs into the grub menu.  Pretty smart!

Then i did the first package update.   I don't know what happened after that, exactly.   The system ends up at "grub rescue> out of disk" prompt.

I was able to boot to the live cd and look at things.  It appears that there are new grub directories and files in my other non-Lucid drives. 

I notice that when I boot to the live cd, the /dev/sd(x) numbering of the drives changes between reboots.   All I have to do is to select 'reboot' from the gnome menu and when it comes back up the drives are in a different order.  What part of Linux decides the those device names ?  By the time grub loads the Kernel image, the device names for hard drives are set because the Kernel knows where to get modules, swap space, look for inittab, etc...  I wonder if it is the Kernel that builds the device tree in /dev ?  Or maybe it builds the rest of it after grub sets up the hard drives.  

Anyhoo,  a big --==** THANK YOU **==-- to the Ubuntu team for the awesomeness.  For even though the over effect was a dead system, I think it is a problem that is in the realm of grub 2 and not something the Ubuntu team can/should fix.  I wish I knew where to start helping.  The week I had Lucid up was sweet.  I really want to try again, use it, help out, show off to guests.  

I look forward to trying Lucid 32/64/Studio when I can.  Thanks again Ubuntu!

---

### Post by parovelb on 2010-06-03
Hola!
I am a beginner linux ubuntu lover and I was used to karmic. Recentl upgraded to Lucid. I get a black screen after boot for kernel 2.32xxx. The kernel 2.31xxx works fine running on a Dell Latitude D400 notebook. 

However I surely prefer an Ubuntu black screen without response than a "windows welcome" ;)

---

### Post by undrline on 2010-06-04
Installed LUbuntu from USB formatted with Lucid minimal image, then upgraded to Ubuntu Lucid Desktop via Synaptic.

**sound** - [solved]("http://ubuntuforums.org/showthread.php?p=9444100#post9444100") by changing settings
**printer** - [solved]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html") by following directions on manufacturer's website
**drives**, [still haven't solved]("http://ubuntuforums.org/showthread.php?t=1515074") why they either won't mount or won't see any media
**scanner**, [still haven't solved]("http://ubuntuforums.org/showthread.php?t=1515896")
**windows software**, [haven't solved]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2505") how to run Paint Shop Pro properly under Wine
**remote access** - solved how to rdp into the machine; someday I'll figure out VNC
**shared directories** - solved bits and pieces, still figuring out permissions issues, and to see shares on windows machines
**digital camera** - copied files off of, but haven't figured out how to  delete files from the device
**webcam** - haven't attempted yet
**fax** - haven't attempted yet

---

### Post by DouglasAdams on 2010-06-04
ubuntu 10.04 live won't even boot on my sons old tosh lappy, it starts fine, i get all the dots then eventually the screen goes blank and it just stops. the cd is fine and the drive. i'm sure that it's a screen driver problem.
seems like i will need to install 9.10 (live runs fine) then do a dreaded upgrade and watch it fall flat on it's arras.

---

### Post by srkirk on 2010-06-04
Did a fresh install of 64-bit Lucid on a Dell Optiplex 960, and am getting random lockups and spontaneous reboots.

I reported the problem here:

[https://answers.launchpad.net/ubuntu/+question/113306](https://answers.launchpad.net/ubuntu/+question/113306)

and on the Dell Linux wiki, but have had no reply as yet. I would really appreciate some insight and advice on solving this problem.

---

### Post by irv on 2010-06-04
> **srkirk said:**
> Did a fresh install of 64-bit Lucid on a Dell Optiplex 960, and am getting random lockups and spontaneous reboots.

I reported the problem here:

[https://answers.launchpad.net/ubuntu/+question/113306](https://answers.launchpad.net/ubuntu/+question/113306)

and on the Dell Linux wiki, but have had no reply as yet. I would really appreciate some insight and advice on solving this problem.

I tried the 64-bit on another version and had problems so I re-installed the 32-bit and had better luck. I really don't have a need to run 64-bit because I don't have high specs on my laptop. If you continue to have problems try the 32-bit Ubuntu.

---

### Post by DouglasAdams on 2010-06-05
clearly people who install to more than one machine, have more than one story to tell. don't you think they should get also get more than vote too?

---

### Post by irv on 2010-06-05
> **DouglasAdams said:**
> clearly people who install to more than one machine, have more than one story to tell. don't you think they should get also get more than vote too?

The polling system on this forum only allows one vote (one voice). Maybe our voting system in the world should be setup like this. I know I would love to see it in America. (to much voter fraud).
Oh, maybe I shouldn't get so political. Sorry.

---

### Post by Amol Parithosh on 2010-06-05
I've been using Ubuntu 10.4 LTS for a week now. Its impeccable. Works well with my machine (Toshiba Satellite L300). 

I have three words for Windows.., Rest In Peace (R.I.P) :) 

Cheers,
Amol,
Bangalore, India

---

### Post by genesisleighton883BC on 2010-06-05
I had 10.04 on my brand new, customized Presario CQ61 for a week and a half and it started freezing up when it was just on the battery. Then, seventy pages of hard work later, I accidentally clicked on something by the power/login/logout menu and now I can't even log in, it goes to the purple screen but it wont even show the login window. :mad:

Short of going back to 9.04 I don't know how to get it to function. But that would delete seventy pages of my work plus school assignments and custom wallies. :(

Any help would be very, very appreciated. 

- Genesis

---

### Post by aeb1 on 2010-06-05
The Averatec upgrade reintroduced the same video bug I fixed before the upgrade.

Since this was a dual boot ( XPpro ) system, I'll wait until the bug is really fixed this time.

I HAVE used the ubuntu LIVE! CD to fix an existing 8.04 system.

The key is to use sudo su in a terminal window and the CL to edit the problem out ( or add ) if necessary.

---

### Post by TheBikeGuy on 2010-06-05
My upgrade on my desktop couldn't have went any better. My laptop was another story. I tried first upgrading and then a clean install. Both were the same result, everything seemed to be going fine. When the system rebooted after install it took a long time to load. Once it loaded the screen was complete gibberish and once the hard drive activity stopped no key combinations seemed to effect it. It was just locked up. I just reinstalled 9.10, which I never had a problem with to start with. I've been using Ubuntu a little less than a year and I'll admit I know almost nothing about it other than just using it. My laptop is a bone stock Dell Inspiron 8200, with a 2.0 Pentium M, 512 MB of ram and Radeon 9000 video adapter. If anyone has any ideas, cool. If not I'm  happy with 9.10.

---

### Post by JohnnyVW on 2010-06-05
I decided to upgrade the server from 9.04 to 10.04 LTS today.  So...  I had to go through 9.10 first. 

The 9.04 to 9.10 upgrade went flawlessly.  The upgrade from 9.10 to 10.04, not so much.  

Something glitched with mysql during the upgrade.

I used:
```

sudo apt-get update
sudo apt-get upgrade
sudo do-release-upgrade

```

I had to cancel the process and hope that it continued.  It did.

So, I had the server up, running 10.04, happily running boinc and sharing my printers, but no mysql.  After uninstalling and purging a few times, I scoured the 'Net.  One little command did it.  I found it on this forum!

```

sudo /usr/bin/mysqlrepair

```

Taaadaaaa!  I re-booted and mysql was running.

Now, PHP was screwy.  I run Jinzora and when I loaded it from my desktop, I got pages and pages of errors.  

When I was uninstalling/purging, I had PHP5 in the command too.  So, everything went to default in /etc/php5/apache2/php.ini.  Since Jinzora has some buggy PHP code in there, I forgot about turning off error reporting. 

All is good.  I can't get over how fast 10.04 server boots!

---

### Post by bweinel on 2010-06-06
Well my experiences with 10.04 LTS have been for the most part good. I have done at least 5~6 upgrades and a couple of new installs with 10.04 LTS. Most worked... here's the details: 

I have upgraded 9.04 to 10.04 server on three different boxes (all AMD64 systems) with little to no problems. Ity was an all together painless experience. 

The desktop upgrades were a bit more painful. Installed Kubuntu 10.04 LTS on a dual processor Opteron desktop and had issues with the soundcard. Still working on those... but I suspect its a card/slot/pci related issue as it doesn't work on first boot... but consistently works after a reboot.

Installed Kubuntu 10.04 LTS on a Intel D850 MB with onboard ATI Radeon hardware and had big trouble with the Xorg server not seeing the keyboard or mouse. After days of working on it, I found that the problem was in the default kernel (2.6.32) and had to install the mainline ubuntu kernel (2.6.34) to fix it. 

Installed two new 10.04 LTS installs on AMD Athlon hardware with no issues at all. Everything worked out of the box...

All things considered, installer issues are getting to be a lot less prevalent than they were a few years back. A pretty good testament to the developers hard work. ...my hats off to them. 

cheers, Bill

---

### Post by alain_sat on 2010-06-06
I'm also a Linux fanatic and trying to run everything via Ubuntu.
I want to thank the community for the help but must admit it's easier to use the Redmond products.

Having troubles with the Win7 boot (is solved thanks to the community) after update of the netbook remix on my Asus N10.

I struggle now the hole week end with this bloody Nvidia driver.
Everything works well untill I open a window.
Let's take evolution for example.
It just disapears after 1 second behind the desktop.
I'm stuck, so anyone having a solution....

I made a fresh install next to the old one.
I asked to copy my Evolution and Firefox documents, it didn't.
So I have a fresh installation but without my data.

I tried low graphics mode but didnt help.
I'll make a separate thread for this.

---

### Post by Breambutt on 2010-06-06
Hardy seemed to like my gear better for some reason, which is kinda strange given that most of it now has proper support in the recent kernels yet work not-as-well or not at all.

Man the irons!

---

### Post by mahela007 on 2010-06-06
regardless of whether this poll represents the actual situation, IMHO , ubuntu still has a lot to polish up in it's install procedure. For example, when I was upgrading to 10.04, the installer told me to install grub on all disks. However, the wording was very easy to misinterpret an I (and apparently many others) unknowingly overwrote the windows boot sector. Fortunately, I found a solution right here on the forums.. but this simply cannot happen if Ubuntu is going to be a competitive OS.

---

### Post by polybius on 2010-06-06
Your work is stored in some file on disk, right?  Just use a live cd to access the disk and copy your file to a USB stick, or ftp it or email it somewhere to save a copy.  Then you can worry about what went wrong with your installation.

If you're careful, you should be able to do a fresh installation without losing any user data.  It's not recommended that you do this---in fact you should backup any user data before doing a new install.  But the fact remains that if you do an install of either 10.04 or an older version, most likely all your user files will be intact.  Then you won't actually need the copy you made as suggested in the previous paragraph.

---

### Post by jtravnick on 2010-06-06
Did a fresh install on my laptop Acer Aspire 5517. Dual booting with windows7 for now as I was not sure how the broadcom wireless would work. Was pleasantly surprised when it worked after loading the propitiatory drivers. So far everything I have checked works fine.

Ubuntu seams to load faster than windows though haven't actually timed it yet I do know the wireless connects faster as does my browser. 

Just wish I had given Ubuntu a larger partition instead of splitting the drive in halve.

---

### Post by wavesound on 2010-06-06
> **genesisleighton883BC said:**
> I had 10.04 on my brand new, customized Presario CQ61 for a week and a half and it started freezing up when it was just on the battery. Then, seventy pages of hard work later, I accidentally clicked on something by the power/login/logout menu and now I can't even log in, it goes to the purple screen but it wont even show the login window. :mad:

Short of going back to 9.04 I don't know how to get it to function. But that would delete seventy pages of my work plus school assignments and custom wallies. :(

Any help would be very, very appreciated. 

- Genesis

HI
Try a live CD first and then backup your stuff to a USB/borrowed hard drive/anything you can copy to.
The stuff is still there!

CHeers
Bob

---

### Post by movieman on 2010-06-06
> **JohnnyVW said:**
> Something glitched with mysql during the upgrade.

Same here when upgrading my MythTV server; everything else worked but mysql was a disaster... the whole system locked up while it was configuring and I had to hit the power button to shut it down, then everything was screwed. I managed to get most of it working with dpkg --configure -a, but mysql couldn't read the user database... fortunately I'd made a complete dump of all databases beforehand just in case so I was able to delete all the database files and reload them.

Edit: sensors have stopped working too... I've gained core temperature readings which are completely bogus, and lost voltage and chip temperature readings.

---

### Post by irv on 2010-06-06
I guess I have come to the end of upgrades for Ubuntu on the laptop I use at the chapel for the sound system. I don't understand why the CD will not load to the install or the live OS. I tried two different CD, and by the way they both work in to other PC's. But goes as far as the UBUNTU logo and after a short while goes to a blank screen and just sits there. After 15 to 20 minutes I just pop the CD out and restart the PC. I am at 9.04 and was going to do a clean install, but now it looks like I am just going to upgrade to 9.1 and stay there. There is really no reason why this CD should not work. Here is the screen shot of the System Monitor.
[ATTACH]159572[/ATTACH]
I am afraid to upgrade to 10.04 doing a upgrade from the package manager because of all the problem I have seen with the upgrade from 9.1. If I can't do a clean install or even get the live CD to work I am afraid I will just screwup the laptop and have to go back to 9.1 anyway.

---

### Post by ackley on 2010-06-06
It was awful. I like to do fresh installs whenever a new release is, well, released. I back up everything to my server & format the drive. Well, I got as far as the backing up.

Threw the cd in the drive & got a purple screen that wouldn't go any further. Booted with "nomodeset" & got it to install. Once installed, it wouldn't boot without anything than nomodeset. Doing this killed my usage of the drivers for my video card. I *finally* got it installed after using Arch for a few months & this was on a smaller partition. I got my nvidia drivers working...kinda. Still no 3d, but the module loads. Dunno how that works. Also in Gnome, I don't have a network manager.

What I finally ended up doing was downloading the minimal iso & using that to install then manually installed the packages I needed. (ubuntu-desktop, kubuntu-desktop, etc)

Overall, the absolute worst experience with Ubuntu ever. I've used, or at least tested, every version of Ubuntu since it's 4.10 release. Didn't care for the text installer then, but it had the best hardware detection for my limited Linux knowledge.

It seems the culprit for my issue is the Nouveau driver. Fedora 13 gives me the same issue. I would like to see Ubuntu make it an option to use Nouveau instead of using it by default.

---

### Post by aceprry on 2010-06-07
The upgrade from karmic worked very well.  I was afraid of losing windows in the boot up like others had in this thread.  So I prepared for it by downloading testdisk and saved some instructions for restoring the dual boot setup.  It was unnecessary because I was able to boot into windows7 after the upgrade.  Had a minor issue with flash not showing up in Chrome, but I was able to fix that by reinstalling the flash packages.  everything looks great, and most importantly, works great.

The karmic install was originally an upgrade over jaunty, which was an even better experience, absolutely no probs whatsoever with that one.

BTW, this was done a couple of days ago on my Dell Vostro laptop.

---

### Post by alain_sat on 2010-06-07
> **alain_sat said:**
> I'm also a Linux fanatic and trying to run everything via Ubuntu.
I want to thank the community for the help but must admit it's easier to use the Redmond products.

Having troubles with the Win7 boot (is solved thanks to the community) after update of the netbook remix on my Asus N10.

I struggle now the hole week end with this bloody Nvidia driver.
Everything works well untill I open a window.
Let's take evolution for example.
It just disapears after 1 second behind the desktop.
I'm stuck, so anyone having a solution....

I made a fresh install next to the old one.
I asked to copy my Evolution and Firefox documents, it didn't.
So I have a fresh installation but without my data.

I tried low graphics mode but didnt help.
I'll make a separate thread for this.

Nobody knows how to repair the old installation so that the programs remain on the screen longer than a second or to copy my Evolution mail and Firefox settings from the old installation to the new one?

---

### Post by jetgraphics on 2010-06-07
> **jetgraphics said:**
> Attempted to do clean install of ubuntu-10.04-server-amd64.
Problem: after install, and reboot, screen goes black. Monitors show "no  signal" warning.

CPU: Phenom 9600
MB: ASROCK A780GMH/128M (AMD 780G chipset)
RAM: 4 GB DDR2-800
Video Adapter: ATI (AMD) Radeon HD 2600 XT

Is this a common bug with AMD/ATI video chipsets?

Update: Good install of Ubuntu 10.4 LTS (64 bit) Desktop, in a dual boot system (Win XP 32).
AMD Phenom 9600, ASROCK A780GMH/128M, 4 GB DDR2 RAM,  Radeon HD 2600 XT


Hindsight:
Attempts at installing 64 bit versions of Linux have met with failure /  bugs / frustration.

One machine - AMD Athlon 64 X2, BIOSTAR TFORCE TA780G, 4 GB DDR2 RAM,  AMIBIOS: V02.61 - would only load 32 bit PCLINUXOS.
Bad / buggy 64 bit installations:
Fedora 12 (after install, crash, blank screen)
Mandriva 2009.1 (flaky KDE4) 
Ubuntu 9.10 
Kubuntu 9.10
Bad / Buggy 32 bit:
Fedora 12

Other machine - AMD Phenom 9600, ASROCK A780GMH/128M, 4 GB DDR2 RAM,  Radeon HD 2600 XT
Bad / Failed 64 bit installations:
Ubuntu Server 10.4 (After complete install, and reboot, blank screen  diplay - warning message "no signal")
Mandriva 2010.1 (Could not get Samba working, nor load driver for HD  2600XT)

Has anyone else experienced success / problem with AMD 780G chipsets?
Or am I just exceptionally "lucky"?
Or is AMD/ATI cursed by Tux?

---

### Post by irv on 2010-06-07
> **irv said:**
> I guess I have come to the end of upgrades for Ubuntu on the laptop I use at the chapel for the sound system. I don't understand why the CD will not load to the install or the live OS. I tried two different CD, and by the way they both work in to other PC's. But goes as far as the UBUNTU logo and after a short while goes to a blank screen and just sits there. After 15 to 20 minutes I just pop the CD out and restart the PC. I am at 9.04 and was going to do a clean install, but now it looks like I am just going to upgrade to 9.1 and stay there. There is really no reason why this CD should not work. Here is the screen shot of the System Monitor.
[ATTACH]159572[/ATTACH]
I am afraid to upgrade to 10.04 doing a upgrade from the package manager because of all the problem I have seen with the upgrade from 9.1. If I can't do a clean install or even get the live CD to work I am afraid I will just screwup the laptop and have to go back to 9.1 anyway.

Well, I gave it a try anyway. I thought I would start from 9.04 (clean install with no other software loaded.) Did the updates then upgraded to 9.1 and did the updates, then tried the upgrade to 10.4. Everything went well until that point. Just before the install finish the laptop froze up. I finally had to power it off and of course it booted to a black screen with no activity on the hard drive. So I went back to 9.04 fresh install and moved up to 9.1. This took many hours and that is where it is going to stay. If the Ubuntu CD doesn't allow it to boot on a system, then it is not compatible with it.
I sure hope the next release will work on this laptop. I have used Ubuntu on it for many years now and would like to have the latest and greatest on it till it dies.

---

### Post by d_e_monat on 2010-06-07
Not bad but a few problems.  (Upgrade from Karmic 64bit)

The window buttons switched to the left. (Fixed) :guitar:

The volume control missing from panel. (Fixed) :guitar:

During boot I get a message that "/boot is not accessible, press..."  I press "s" to skip and the boot continues with no problem :confused:

My system is a little complicated (I like to experiment) but here are the specs.:

AMD 939 2gHz, Asus A8V-MX, 2 IDE hd, 2 SATA hd in hardware raid0 (2Tb), Nvidia AGP video card.  I need to use pci=nomsi on kernel line to boot.

The /boot and grub partition are on an IDE drive.  I never was able to get the RAID array to work for booting with grub :mad:  I also have separate partitions for /home. /usr, /tmp, /var

---

### Post by irv on 2010-06-07
From what I can tell after hitting the [ESC] when booting the 10.04 cd. The reason it will not boot is because of my CPU: It give me a CPU error.
[ATTACH]159654[/ATTACH]
As you can see from the attachment I have a Intel Pentium M Processor 1.7GHz. If this is the case, why doesn't Ubuntu support it. Has anyone else installed on a Intel Pentium mobile chip? I would think this is a widely use in older laptops. 
I am still wondering why it won't boot in this one system?

---

### Post by ronparent on 2010-06-07
I've installed 10.04 64 bit desktop on three amd64 compters as well as the latest Mint on two. The installs went well on the two boxes without raid. I installed to the raid0 with some glitches, now all solved. The install on the raid initially failled with a fatal grub error. I fixrd initially by reinstalling the grub2 to a non-raid sata drive. I have finally found the trick for it and installed the mbr to the raid0 root array symbolic link found in /dev/mapper. That box is fast and responsive.

My problem is still with the inconsistent handling of 'fakeraid' between sucessive distros. For instance, gparted will not currently work with the raid drive at all. Good news is that the raid drives are now automatically mountable in nautilus. 

I avoided most graphics problems because I had to upgrade all my video drives to be fully supported in Win7. My main problem was that my  latest box would not install until I disconnected one monitor. The distro graphics drivers would not otherwise permit anything but a black screen. The ATI driver works perfectly! There is no driver for my printer so I have to use win7 for any printing.

Otherwise am still evaluating.

---

### Post by whoboo on 2010-06-08
I wanted to upgrade but couldn't, for reasons not understood having to do with repository stuff.
So I installed new ubuntu in dual boot with old ubuntu.
Installed OK on my old e-machine.
Then I decided to hibernate.
Hung.  Turned off power.
Now the ethernet card is disabled on boot and I cannot get to network. Even if I ifconfig the card.   Also, shutdown hangs like hibernate did.

I have no clue how to fix this.

Fortunately, old ubuntu still comes up and gets to network or I wouldn't be here.

Unfortunately, cd rw won't write and printer won't print since upgrade from u8.

Next upgrade I guess I'll lose monitor or keyboard.  Or maybe both.  Then I'll just have the nifty ubuntu sounds.

I hope somebody reads this.

---

### Post by iflanery on 2010-06-08
I wanted to upgrade last night, but Karmic wouldn't let me for some reason, probably owing to the presence of KDE3 on my system and some broken repositories... or something.

So..... I decided to do a clean install. This went alright for the most part, but I'm pretty sure I made a mistake during the installation as I didn't set a mount point for my /home partition (the data is still *there*, fortunately), and as a result, it now shows up under /media/, followed by one long alpha-numeric string... anyone know how to fix that?

Other than that, the problems I've encountered are the typical problems I've always faced after a clean install: getting all the plugins installed, etc., etc.

My system is a Dell Inspiron 530N, 250GB HDD, 1GB of RAM, nVidia GeForce 8300 GS, with a 1.3 Ghz Intel 4 processor.

---

### Post by sanderd17 on 2010-06-08
The install worked almost flawlessly. The only problem was that ubuntu didn't recognize my mint theme and gave me a windoze-95-like theme instead. I've used mint for one release and used the same home directory.

When I chose my own theme, it was solved.

---

### Post by irv on 2010-06-08
> **iflanery said:**
> I wanted to upgrade last night, but Karmic wouldn't let me for some reason, probably owing to the presence of KDE3 on my system and some broken repositories... or something.

So..... I decided to do a clean install. This went alright for the most part, but I'm pretty sure I made a mistake during the installation as I didn't set a mount point for my /home partition (the data is still *there*, fortunately), and as a result, it now shows up under /media/, followed by one long alpha-numeric string... anyone know how to fix that?

Other than that, the problems I've encountered are the typical problems I've always faced after a clean install: getting all the plugins installed, etc., etc.

My system is a Dell Inspiron 530N, 250GB HDD, 1GB of RAM, nVidia GeForce 8300 GS, with a 1.3 Ghz Intel 4 processor.

I am sure if you start a new thread about you home mount point someone will be able to help you. I have a thought on how to fix it, but I am not sure I am 100% right, so I will keep it to my self and not screw up you system any more.

---

### Post by Robot007 on 2010-06-08
Did an upgrade on one laptop (32 bit 9.10 to 10.04) and it worked flawlessly. However, on my other laptop I did a clean install to dual boot with windows 7 and after a few restarts was no longer able to boot into either. I fixed that by formatting the partition and putting 9.10 on that partition. But someone recently told me that the original 10.04 iso (which I used) had a bug that made it do that, but now it's fixed. Can anyone confirm/deny that?

---

### Post by kfh on 2010-06-08
I attempted both an upgrade and fresh installation of lucid lynx desktop on a compaq cq60 laptop having an external keyboard and monitor after the most recent karmic "update" overwrote my network settings and re-activated the blasted network-manager.

DHCP networking worked after the upgrade, and, although I wanted to run with a static IP address, I got sidetracked by a monitor-resolution restriction of  800x640  when the displays were mirrored.  If I set the monitors for having different content, the resolution was adjustable over the full range of resolutions, but the gnome control bar on the top of the display was only available on the laptop's display.  Googling this issue resulted in suggestions to edit the Xorg.conf.  

Editing a config file to set display resolutions for dual monitors just doesn't qualify as a feature of a "Just works" OS.

The fresh install of lynx didn't work any better, and, rather then spend another several hours fixing monitor-resolution and static networking, I decided to go back to rhel5.  The rhel5 install took about 1.5 hours with networking and display resolution working.  I was even able to get openoffice installed.

I'm really sorry that the ubuntu desktop developers decided to make desktop administration so tedious for desktop users.  And updates should NEVER overwrite network settings.


> **frodon said:**
> [SIZE=3][COLOR=Red]*** Disclaimer for those willing to analyse this poll ***[/COLOR][/SIZE]
[SIZE=2]- Most of users voting here are users with issues,
users with painless experience are not likely to come here. So the statistics here do not represent the reality.
- If you want to compare Lucid Lynx release with other ubuntu releases based on this poll then here are the previous polls (the only good reference to start an analysis)[/SIZE] :
[Karmic Koala - Click Me]("http://ubuntuforums.org/showthread.php?t=1305924")
[Jaunty Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=1133869")
[Intrepid Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=963853")
[Hardy Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=764847")
[Gusty Poll - Click Me]("http://ubuntuforums.org/showthread.php?t=580852")

[You will find here a Summary proposed and maintained by NCLI - Click Me]("http://spreadsheets.google.com/pub?key=t0XWfWgqJpYxCGAZ1G8U-og&output=html")


The purpose of this thread is to share your experience installing/upgrading Lucid Lynx.

Did it work flawlessly ? 
Did you get problems ? 
Did you manage to solve them ? 
if yes how ?
...
...
.

Feel free to post your experience here and think to explain how you solved the problems you got, it might help other users in your case.

Thank you for contributing :KS

---

### Post by markMDW on 2010-06-08
Install of 10.04 was very difficult on my Intel Core i5 machine, apparently because of the default video driver causing the machine to become severly unstable.  Anyhow, I managed a workaround and have the Ubuntu recommended restricted propritary video driver installed and everything is just perfect, now.
 
 Thanks to everyone how posted with helpful hints.  Those tips all combined helped with the fix!  read all about my experience here:
 
[http://ubuntuforums.org/showthread.php?t=1488088](http://ubuntuforums.org/showthread.php?t=1488088)

---

### Post by chuck4200 on 2010-06-08
Beware of upgrade process if you have Multiple HDD and partitions.

Hosed my dual boot XP system on an upgrade through 9.x to 10.x.  I would strongly advise installing from a Live CD.  I have/had two HDD's with multiple partitions on each.  The install of upgraded files appeared to be fine, although I could not test it.  Would not reboot.

Probably occurred with GRUB2 asking what HDD/partitions to installi on the right partition or drive.   Quite a few problem posts regarding this installation feature/problem.

Lost the Boot.ini, could not fix using the lilio -M routine, or the XP Recovery Console fixboot/fixmbr suggestions.  Testdisk did not work for me with Live CD - only testdisk_static will install/run and gives you only a log file, no option screens.

If you have a standalone Linux box, or a dedicated drive it might work better as many have reported.

---

### Post by iflanery on 2010-06-08
> **irv said:**
> I am sure if you start a new thread about you home mount point someone will be able to help you. I have a thought on how to fix it, but I am not sure I am 100% right, so I will keep it to my self and not screw up you system any more.

Got it. New thread is [here]("http://ubuntuforums.org/showthread.php?t=1504502").

Any advice you have would be appreciated, though.

---

### Post by mollyj on 2010-06-08
Since I do not usually upgrade every time there's a new version I have been using the last LTS package (8.04) for a couple of years. Along comes 10.04 and this is also a LTS and so I decided to try an update. I dutifully backed up my user files and then tried to install Lucid (10.04) from a live CD. The live CD ran and, because I have an Elonex webbook(and this has a perenial problem with the screen driver) I was using an external monitor. I clicked on install and waited; I answered the questions and since I thougt that I had nothing to lose I installed to a clean harddrive. After churning away for sometime the whole system appeared to have finished ( I didn't stay around to watch for the hour or so that it took). I turned off the machine, remobved the usb CDROM and turned everything on again...... result...... nothing; no boot no disc activity just a par of blank screens. Undaunted I reconnected the CDROM and tried the live CD again. This time it asked me for a username and password but refused to accept the one that I had used on the install and so it wouldn't get any further. I tried lots of different things... passwords.... switching off and on.... unplugging varios bits. No - joy.
Finally I fished out an old magazine disc that had 9.10 on and managed to install this however this reported that 10.04 was already there. Out of curiosity I accessed the 10.04 partition but found that it only contained a single folder. I decided to cut my losses.... I'd spent the best part of a day installing etc. I reinstalled 9.10 using the whole drive  as as far as I could tell the half drive allocated to 10.04 was useless to me and I then managed, with the help of Alan Bell of the Webbook Blog to get the screen on my Elonex working. I would like to upgrade to the LTS version but I'm wary ... Once bitten twice shy as it were. Any advice would be welcome.... Was it just a bad live disc (the machine didn't complain) or is there a fundamentaly problem with the quirky hardware of the Elonex and 10.04?

---

### Post by r m h on 2010-06-08
Not impressed - the most problematic release of Ubuntu to come out of Canonical in 4 years.  My length of experience with Ubuntu is only 4 years old.

Fresh install on a 32-bit P4 3.6GHz machine with new EIDE disk fails miserably.

ubuntu-10.04-desktop-i386.iso burned to CD.

ISO md5sums match published values in MD5SUMS from [http://ubuntu.osuosl.org/releases/lucid/](http://ubuntu.osuosl.org/releases/lucid/)

CD creation (under Ubuntu) tells me it succeeds.

Booting from the install CD fails with the following informative results:

A Window entitled "installation failed" which contains the text "The installer encountered an unrecoverable error.  A desktop session will now be run so that you may investigate the problem or try installing again." appears with an "OK" button.

When I click the OK button, I see a very brief display of text on the blank black screen, one piece of that text appears to be "getpwuid failed due to unknown userid (0)" 

Then when the desktop appears, nautilus keeps crashing.  

My fresh install experience is total garbage.


I have already upgraded (apt-get dist-update) 4 laptops, 4 servers, and 4 workstations to Ubuntu 10.04.  One server and one laptop scrambled their boot process and didn't build the right grub files (menu.lst and grub.conf didn't reconcile).  The goofy thing here is that the machines that scrambled their boot process were virtually identical (h/w and s/w) to other ones that went fine.

All of these machines are single boot, and only booted a completely up-to-date Karmic Koala (9.10) release prior to the upgrade.

A 77% installation/upgrade rate (to a bootable 10.04) is not impressive at all.  The 10 machines that did successfully boot had assorted other issues that I have resolved, so I will call them successes.

This is the absolute worst release of Ubuntu in the past 4 years that I have had experience with.  I do not expect this poor quality from Canonical based on past experience.

So, the question is, have you lost your process?  or, what happened?

I left Red Hat Linux/Fedora after 11+ years for a similar reason.

---

### Post by KLStringer on 2010-06-08
Been slogging away at this for 3-4 weeks now and still can't get 10.04 to work. I've searched high and low with no solution to be found. If anyone has any suggestions here's my issue and thread.

[http://ubuntuforums.org/showthread.php?t=1487227](http://ubuntuforums.org/showthread.php?t=1487227)

---

### Post by Istrebitel on 2010-06-09
Was migrating from windows (an experienced windows user, had some knowledge on linux, but not much, mostly outdated - red hat examinations)

Installed Kubuntu

Problems i received and fixed somehow:
1) Wasnt so obvious i need to install proprietary drivers for window effects to work. Wasnt obvious drivers were already in the "hardware" menu, so i tried to go after nvidia website and had problems installing them, in the end it resolved
2) Wasnt so obvious i need to download a theme in different places then choose it everywhere (in color scheme, in plasma, in window decoration...)
3) Wasnt able to play dvds - had to switch numerous players until i stumbled across the post in multimedia forums - later i was told a new way exists, kubuntu-restricted-extras, but there was no clue to it
4) No normal image editing software. Okay, gimp is for pros. But i want to be able to draw lines, cut image parts, and so on! Something paint-like MUST be in the default graphic applications list. 

Problems i never got to fix and why i left Kubuntu:
1) Ntfs mounting requires password. Cant be fixed even recompiling ntfs-3g with internal FUSE. Dolphin keeps prompting. Automount on startup pops numerous prompts. It all fails. Kubuntu is NOT ntfs drive-friendly!
2) Network manager is a dreaded monster. IT WILL NOT REMEMBER THE SETTINGS! It always defaults to auto eth 0 you cant configure (you can in Ubuntu!). Always will use DHCP no matter what. I hate it so much
3) Ibus is not working. Moreover, system expects it to be there and spits errors but it isnt there!
4) creative x-fi titanium not working surround. looks like its a common problem though

Installed Ubuntu

So far feels much better than Kubuntu. Almost no problems 

Didnt figure out how to yet:
1) Fix the drop down menus from not appearing if i switch them too fast (i turned on compiz effects like beam up etc)
2) automount ntfs drives at runtime (not at boottime - i know about /etc/fstab, it wont help, one of my external scsi drives "boots" for about 20 seconds for the first time)
3) Still no solution for creative x-fi but i dont think i will ever find one

---

### Post by Tholley on 2010-06-09
I have to admit, I was scared to do an upgrade, I was prepared for the worse since I had a nightmare of a time upgrading from Jaunty to Karmic (mostly due to Grub2 problems), so I figured I would finally try an upgrade, and if I had any issues, I would just do a clean install. It went without a hitch! I was actually unsure if it even had done the upgrade since everything still looked the same. All my Compiz and Emerald setting were still intact, I couldn't see any difference. I was actually disappointed a little that there was no fanfare after the upgrade. I had to choose a new desktop wallpaper since my cherries from Karmic were no longer there, but other than that, very uneventful.
 
Now I have another newer machine triple booting Jaunty/WinXP/Win7, well I was anyway... last night I upgraded from Jauntu to Karmic, (while keeping my fingers crossed, and en route to upgrading to Lucid) and that went without a hitch either.
Of course now I find out the source of my worries (upgrading from Grub to Grub2), was premature since upgrading does not automatically change Grub, but gives you the option to test Grub2 by chain-loading it. I'll find out tonight if Grub2 will work on my system, and if so, then pull the trigger on Lucid.

---

### Post by TheTank on 2010-06-10
I chose 'Upgrade - got many problems that i've not been able to solve'

On my work machine I went from 9.04 to 9.10 pretty without much issues.
But then the leap to 10.4 went badly.
Might be related to hand-compiled stuff. Dunno.
I had to completely reinstall. Luckily I had an extra drive handy.

But my Jaunty@home is staying the way it is until I have a free weekend for this adventure.

One thing that scares me is Grub2 because I have optimizations in my grub (journalling tweaks) I have yet to figure out for Grub2.

---

### Post by Trapper on 2010-06-10
We've opted out of U 10.04 here. It's just disappointing, overall. At first we chose to remain with 9.10 but ultimately switched to Fedora 13. It's what we were hoping U 10.04 would be. :mad:

---

### Post by wavesound on 2010-06-10
> **r m h said:**
> snip

This is the absolute worst release of Ubuntu in the past 4 years that I have had experience with.  I do not expect this poor quality from Canonical based on past experience.

So, the question is, have you lost your process?  or, what happened?

I left Red Hat Linux/Fedora after 11+ years for a similar reason.


Hi 
I to had moved over from Fedora to Ubuntu.
Seems  to be a regular thing these days.
They build a great following with quality software then seem to lose site of the basics.

I did an upgrade of a working system which then hosed my Grub.
A live CD later I managed to get it to boot but no sound now.
Worse thing is they don't seem to count sound as important now!!
Might as well say dont bother with the internet!

Cheers
Bob

---

### Post by Trapper on 2010-06-10
> **wavesound said:**
> 
A live CD later I managed to get it to boot but no sound now.
Worse thing is they don't seem to count sound as important now!!


Check to see if your sound is simply muted. I found in my installs that it was. I also found that the internet connection was there but had to be enabled, or enabled for all users, or enabled at startup.

---

### Post by Tholley on 2010-06-10
>  
Now I have another newer machine triple booting Jaunty/WinXP/Win7, well I was anyway... last night I upgraded from Jauntu to Karmic, (while keeping my fingers crossed, and en route to upgrading to Lucid) and that went without a hitch either.
Of course now I find out the source of my worries (upgrading from Grub to Grub2), was premature since upgrading does not automatically change Grub, but gives you the option to test Grub2 by chain-loading it. I'll find out tonight if Grub2 will work on my system, and if so, then pull the trigger on Lucid

 
I was unable to chainload Grub2, even after editing the root to uuid, when I would type b for boot, it would just go to a command prompt. Then on reboot, the uuid would be gone and root back. So I followed the instructions from here, [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and reinstalled Grub2 thinking I could still chainload it to test it, but it actually installed it as default, but it all worked after several reboots, so then I went ahead and removed Grub Legacy, and now with Grub2 working, I'll give Lucid upgrade a go tonight.

---

### Post by byline on 2010-06-10
Since upgrading from Ubuntu 9.10 to 10.04 on April 30 (via Update  Manager), with a few minor exceptions, pretty much everything has been  working the way it should. However, earlier this week, when I plugged in my Sony MP3  player to add a few more tracks, the device is not automatically  opening up on my desktop. Also, on the MP3 player itself, when I plug it  in, before there was an exclamation point inside the circle; as long as  that was there, it wasn't safe to disconnect it. Now the exclamation  point is not showing up.

Everything else -- printer, scanner, photo card reader, etc. -- is  working properly under 10.04. Oddly enough, the MP3 player worked fine under 9.10, and in fact still works as it should on my husband's laptop, on which he has installed 9.10. He has searched for solutions to this problem with the MP3 player, to no avail.

A couple of other problems have persisted since the upgrade to 10.04,  and neither hubby nor I have found permanent solutions to either: The swap partition is  not automatically mounted on boot-up, so I have to do that manually by  typing **sudo swapon -a /dev/sda1** in the terminal. And then every  time I boot up, I get a mail notification window asking me to choose a  mailbox. Thunderbird is the e-mail program that we use, but it's not one  of the options offered. So I have to close that window every time I  boot up; there doesn't seem to be any way of permanently disabling it.  Not a biggie, but annoying.

I think we may end up reinstalling 9.10 on our main computer, as I don't see any noticeable  improvements with 10.04, yet I've actually lost some functionality.  Besides the issue with the MP3 player, the swap partition *should*  be mounted automatically on boot-up . . . yet it's not. And I *should*  be able to completely disable that mailbox notification window on  boot-up . . . yet I can't. And there don't seem to be any solutions for  any of these things.

Of course, these are relatively minor issues compared with what other  folks have gone through, but it's still annoying that what should have  been an improvement is actually a step backward.

---

### Post by wavesound on 2010-06-10
> **Trapper said:**
> Check to see if your sound is simply muted. I found in my installs that it was. I also found that the internet connection was there but had to be enabled, or enabled for all users, or enabled at startup.

Hi
I seem to have no alsa at all on the system now (have tried re-installing it)

There is no volume controls to mute and selecting pulse from the menue fails saying unable to connect.

This is with a fully supported sound card
Audiophile 9624 which has always worked.

Seems these cards will not be supported in the new Ubuntu's.
Alsa used to like them.

Thing is I got spotify to works a few times, so the system is all there ready.  :guitar:

---

### Post by WinterRain on 2010-06-10
> **byline said:**
> Since upgrading from Ubuntu 9.10 to 10.04 on April 30 (via Update  Manager)

That is the problem. Upgrades in ubuntu are notorious for going bad. Try a clean install of 10.04 and update immediately.

---

### Post by byline on 2010-06-10
> **WinterRain said:**
> That is the problem. Upgrades in ubuntu are notorious for going bad. Try a clean install of 10.04 and update immediately.
Sorry, I'm not really sure what a "clean install" is. (Linux is my husband's baby, and he's done most of the work. I'm just the user.)

Given some of the horror stories I've seen others post, I'm also a wee bit reluctant to change anything, as pretty much everything works the way it's supposed to, with just these few minor glitches. "If it (mostly) ain't broke, don't fix it.":confused:

---

### Post by emarkay on 2010-06-10
One must never get so "locked" in to an OS that they must "upgrade" it instead of being able to  "reinstall" - come on now, we all know that even in Linux there are things forgotten, kludged or otherwise overlooked that may rear their head in the most inappropriate times.

One does not put a fuel injected 2010 LS4 engine into a Model T; or even into a 1965 Impala without addressing every possible issue; do you know how to get the high pressure return line to the ambient pressure open fuel tank or how to interface the analog coolant gauge synched to the digital bitstream?  Unless you are one who "wrote the book", buy a new car; or in otherwords, reinstall! 

As for me, it's as good as it's gonna get - I am sticking with Lucid LTS (and my Rear Wheel Drive old Chevy!)

---

### Post by byline on 2010-06-10
OK, hubby was able to work out solutions to all three of my complaints:

- deleted rhythmbox utilities and removed rhythmbox from the panel.  Plugged in the Walkman and, voila, a folder opened with the Walkman's contents!
- to keep the mail notifier from opening every time you log in: System Preferences, Startup Applications, uncheck "Mail Notifier", Close
- to automatically set the swap partition as /dev/sda1, use sudo gedit to have /etc/rc.local end with:
swapon -a /dev/sda1
exit 0
So I guess I'll stay with 10.04 after all!:guitar:

---

### Post by DouglasAdams on 2010-06-11
i did a clean install, totally reformatted and re-repartitioned the hd for Linux on my sons Tosh, previously Win XP Pro, lappy.
Live cd ran fine; install went fine; the sun was shining and everything in the world was perfect. then came the reboot at the end of the install. seemed to be going ok; ubuntu flash screen; first row of dots; started to go the other way then went back then stopped.
tried to reboot a few times but exactly the same, first row of dots fine then one dot and back.
i'm guessing it's a screen driver problem, which is sad as the lappy is a few years old so i would have thought it would be ok.
new install of 9.10 went fine.
when is 10.10 out?

---

### Post by irv on 2010-06-11
You asked: > when is 10.10 out?
It come out October 2010. 10/2010. The version number is the release date.

---

### Post by rastro123 on 2010-06-11
Im not really impressed with lucid at all, and have returned to jaunty. I first came to linux with intrepid, went to jaunty, and then tried koala. Koala was no good as I only have wireless, I installed it and was stuffed from the word go- no wireless working, so went back to jaunty. I installed lucid about a week ago, went to a friends house with a cable connection and got the wireless working. Prob 1- no password asked for on boot up. Prob 2- cant get rid of the evolution icon at the top of the screen without losing the volume control also (very peculiar!) Prob 3- Many times the pc just hangs. Prob 4- in lucid when I put my icon over the battery symbol it does not tell me how much time left, in jaunty it does this. Prob 5- 3 times I changed the desktop to kubuntu and the wireless stopped working. I removed it but the wireless would not come back. So ....after reinstalling lucid 3 times, I give up on it and go back to the jaunty distribution. I just made a new partition on my drive so that I can install and try out a different linux distro and acustomise myself to it, before I use it as the main system. Seems sad to me that the developers are going backwards and not forwards in their ''improvements'' Jaunty is great, but what do I do when support is finished and there are no more updates?

---

### Post by jfl on 2010-06-11
I have already upgraded 2 Lenovo laptops without a hitch; having the /home directory in a separate partition helps.
Yesterday was the final test, upgrading the main office computer; I knew I would have 4 days if something went wrong.
As usual, I did all suggested updates, re-booted, checked for updates again and re-booted.
Then I started the update to 10.4 around noon, and fixed  lunch.
Around 1:30, thunder in the distance (common in S. Florida), started to worry. Power failure are common here and my UPS is only good for 10-15 minutes.
But the download went well, started the install, asked for the usual questions, around 2:30, final re-boot ... 10.4 was there.:p
Everything worked except a few Perl programs I had written; they could not find Perl modules they needed to run; re-installed the modules from CPAN and around 3:15 the machine was fully operational.

BTW it is a "home made" based on a Celeron, 512Mb memory, 2 SATA HD,
1 IDE HD and 2 DVD. Grub boots Ubuntu or W2K (needed to run Quickbooks).

So, I'd give it ***** 5 stars. The Perl glitch was probably because I installed the modules in the wrong place.

My advice to anybody starting any kind of upgrade or re-install is to record IN WRITING the partition layout.
In my case I had 13 partitions.
If you have to re-install from the alt CD and you don't want to clobber your data, apps, other OS, etc. You'll be glad you did.

---

### Post by Tholley on 2010-06-11
I upgraded my second machine last night, both from the upgrade button, and all went perfect! 
 
I will agree with some others that I'm not overly impressed with Lucid. For some reason I kind of liked Jaunty the best also.
 
I did notice that I was able to right click on a file and it gave me the option to "Move To" and "Copy To" that I don't thnk was there before and I like WAY better than cutting and then drilling into the folders to paste.

---

### Post by FirstByté on 2010-06-11
As from previous experiences of upgrades... Worst of 'em all, Jaunty>>Karmic upgrade taught me never to rush into an upgrade provided the present was still up and running.

After waiting for about 4weeks of Lucid release, I joined the wagon. I liked it right from the LiveCD. However, some 'BASIC' functionalities and features that worked flawlessly on Karmic 9.10, just seem to be blown in Lucid 10.04. Which makes me often wonder why the X.04s are the LTS and not the X.10s.

What broke in 9.10 Karmic >> 10.04 Lucid upgrade
-----------------------------------------------

* Built-in Mic [http://ubuntuforums.org/showthread.php?t=1491824](http://ubuntuforums.org/showthread.php?t=1491824)
** Firefox dictionary/spell check no more*. aspell works with Pidgin etc. (suspected Firefox related)
** US_Intrnl Keyboard ceases to show punctuations whenever typing mails in GMail* (suspected Fifefox related)
Removed feature:
* Mouse-over Volume Control for RhythmBox Icon on System-tray
* 60 Seconds countdown on 'Shutdown' button pressed [Remembered a few members requesting it be removed :( ]

These features sometimes make me feel paranoid. Aside these, I have no major issues [yet]. I barely push my X to the boundaries, so little bugs may be noticed.

---

### Post by FirstByté on 2010-06-11
> **byline said:**
> OK, hubby was able to work out solutions to all three of my complaints:

- deleted rhythmbox utilities and removed rhythmbox from the panel.  Plugged in the Walkman and, voila, a folder opened with the Walkman's contents!
- to keep the mail notifier from opening every time you log in: System Preferences, Startup Applications, uncheck "Mail Notifier", Close
- to automatically set the swap partition as /dev/sda1, use sudo gedit to have /etc/rc.local end with:
swapon -a /dev/sda1
exit 0
So I guess I'll stay with 10.04 after all!:guitar:

You are most welcome on board. I look forward to the XX.10 though, they often more stable releases than XX.04s

---

### Post by giddyup306 on 2010-06-11
I have been using Ubuntu since Intrepid, and this has been by far the most problematic version yet!  I had the best luck with Jaunty, but Karmic had the safely remove hardware option.  Since Lucid is a "LTS" version I figured that I would be trouble free for 3 years...

The first thing that was more of an annoyance was that the min. max., and close buttons were all on the left side.  I remember a poll here where something like 75% of the people didn't like it.  I was hoping that the Beta version would have gotten rid of it, but they didn't.  It's not that big of a deal to switch, but it was annoying having all the other tabs like in Firefox on the right, and windows in VB on the right as well.

The volume button at the top of the panel went MIA.  It won't automount external hard drives.  Won't auto recognise CDs or DVDs.  Firefox seems to loose connectivity for no reason.  This might be a wireless issue in Lucid itself.  There was a thread on it a day or so ago.  I had to recompile the Virtual Box Kernel so that it would load.  After doing so I had to reconfig everything! Now it gives me some BS that this version is not suitable for production use... It also messed with my Compiz settings (which is nothing new).  After burning a disc it says to eject it manually. 

I was hoping that updates would fix some of these problems, but they only caused more. After doing some updates everything I download is "locked".  If Transmission is running and I try to use it it says that there is already one instance of it running.  I have to close it and then click on whatever I want to download. The most annoying is that I have to hit a bunch of keys on the keyboard to get Lucid itself to load.  It has something to do with my nvidia card.  I though I had it fixed, but I was wrong. 

I've been trying to backup for a long time because I have a lot of tweaking done, and a fresh install is out of the question.  I tried the old sudo dd if=/dev/sda1 of=/dev/sdg1 trick and now not only can I not load off of the USB drive, but windows and Linux don't even recognise the drive!  I tried clonezilla, and it locks up half way.

Sorry but the "typical Windows user" doesn't want to have to deal with this.  With any other distro I've been able to fix minor things, but this has been nothing but a headache since day one!  My brain is about ready to explode from doing all the research, and not finding any solutions!

Don't get me wrong Ubuntu is still way better than windows.  I need to get a laptop for work, and I think I'm going to buy one of those Ubuntu laptops and three years of support!

---

### Post by byline on 2010-06-11
> **FirstByté said:**
> You are most welcome on board. I look forward to the XX.10 though, they often more stable releases than XX.04s
Thanks! Live and learn. I think next time, I'll follow the advice of you and many others, and wait until a later version of an upgrade, when many of these issues have been settled.

---

### Post by KLStringer on 2010-06-11
> **KLStringer said:**
> Been slogging away at this for 3-4 weeks now and still can't get 10.04 to work. I've searched high and low with no solution to be found. If anyone has any suggestions here's my issue and thread.

[http://ubuntuforums.org/showthread.php?t=1487227](http://ubuntuforums.org/showthread.php?t=1487227)


Found the answer to my issue in this thread

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7744000](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7744000)

Thank you to [Brachus12]("http://ubuntuforums.org/member.php?u=1093677") for finding and pointing me to it.

---

### Post by cipher_lx on 2010-06-12
I've performed fresh installation of Lucid Lynx on external USB HDD and it installed like a charm!

However, I've one question? I installed the notebook version and I'm not able to figure out how to get classic drop-down menu instead of on-screen panel for accessing programs?

I know in previous version we were able to use Desktop-switcher. 

Any help is appreciated?

---

### Post by fancypiper on 2010-06-12
Well, I did a full re-install so that I could compare the two situations.  I much prefer the upgrade over the re-install, although it worked well in both cases.

I had more difficulty with the install, trying to remember my favorite programs and the ppas that I needed, as well as remembering my fairly complex 5 hard drive mixed SATA and IDE partitioning scheme.

My conclusion: choose the upgrade over the install for both speed and ease.

YMMV

---

### Post by eggdeng on 2010-06-12
Generally quite pleased with Lucid. My graphics card had problems with KMS but I was able to install using the nomodeset option. The bundled Radeon driver works well and Intel HDA audio finally works out of the box. In general everything works except for suspend.
I have been using Ubuntu since 5.04, Hoary Hedgehog, and like others, find the recent apeing of Apple off-putting. Linux has strengths and beauties of its own that other OSs cannot aspire to and there is no need to pretend otherwise.
Full review in sig.

---

### Post by camorri on 2010-06-12
I installed 10.04 with Unetbootin. The install was fast, easily the fastest install of linux distro I have used. 

The hardware - HP Mini 210-1080CA. 1 Gig of ram, N450 processor, and 160 gig disk.
 
I picked this distro because of the support community, I thought I would need. All the hardware worked out of the box. For the record, here is lspci.

```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Atheros Communications AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

Problems. One of the reasons I blew away Win-7,   it would not talk to my samba servers. I installed Samba on the Mini. Installing it was easy, however, getting it working took some research. I ran into the inability to log in to the shares, even though I could see the. 

The fix - [http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/](http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/)

Followed this blog, now sharing works. 

No problem with my Nikon digicam. Plugged it in, transfered pics. Nice.

Printing - Had to go to Brothers site to get the driver for my Brother HL-2040. Printing works now. Configured it with [http://localhost:631](http://localhost:631).   

Plugged in an external USB mouse, it works along side the touch pad. Nice.

It took some reading to find out how to switch to the Gnome desktop. Nothing wrong here, just my lack of knowledge with Ubuntu.

I bought a 6 cell battery, I have used it  for 3 hours, still have 68% left. I'm happy with that. 

I bought this machine as a traveling system. Light weight, powerful enough to do everything I want on the road. 

Happy with the hardware, and Ubuntu. :guitar:

---

### Post by spamless on 2010-06-12
The poll conspicuously is missing an important category:

[INDENT][COLOR="DarkRed"]got many problems that I've nevertheless been able to solve (but it wasn't easy)[/COLOR][/INDENT]

Also, do you ***have*** to leave the English first-person pronoun small-case?  How amateurish!

I've now installed Lucid four times, including a netbook version most recently.  My suggested response as above is what I would pick for half of the experiences.

---

### Post by malkdude on 2010-06-12
I upgraded from karmic, and I had a few problems with Gnome ubuntu lucid lynx. At first, the windows borders did not appear at all, so it was impossible for me to close windows (at least with a mouse). I had to use

metacity --replace

command for a while and then, after a week or so, it magically worked (probably because the Ubuntu developers worked on it, and put a few patches in the repos, God bless them ):P).

Then I decided to give KDE a try for the first time in my life. I had problems with the laptop logging out by itself, and taking me back to the log in menu, and also issues with the graphics drives. I saw sometimes scrambled colors. It turned out both these issues were related to the graphics driver, so I had to do some tweaking. In particular I reverted to XAA acceleration method, and I disabled the render acceleration (before that I also had to tell ubuntu to create an xorg.conf file, since the designers decided to let KMS due the job automatically, but it's still buggy on some systems like mine, with the infamous ATI xpress 200m card...)

Another issue I had with Kubuntu lucid was the suspend/resume. My workaround for that was to disable it using Power Management. The problem I have is that when the computer suspends to RAM (ie sleeps) or when it hibernates, it doesn't wake up properly. When it wakes, the keyboard works fine, but the mouse stays at the top left corner of the screen, and doesn't respond. I believe this is a bug in pm-utils, and it's still there, but I just decided to disable suspend instead of trying to figure out how to make suspend work (for now).

So for now, I have 2 working desktops, GNOME and KDE, but I have to say that the suspend is still buggy for me in KDE as I described above (I forgot whether suspend works for GNOME). I can now forget about bugs, and do some work :). Peace! :guitar:

---

### Post by byline on 2010-06-13
A question my husband asked, as he's the one who's had to fix the little glitches that have popped up with 10.04: Why this upgrade had to reset the user's default panel settings I cannot  fathom.  Just creates a lot of work for everyone to get things back to  working as they had been before.

---

### Post by JayKay3000 on 2010-06-13
No problems this time. Even the wireless worked fine. 

I prefer clean installs and that was just flawless. 10.04 on my pc was the same.

---

### Post by wolf_3d on 2010-06-14
Clean install after previously using 9.10 KK. Easy installation and still yet to find a serious issue having now used it since Apr 30th. *thumps up*

---

### Post by cb5online on 2010-06-14
The install went well. Had to manually faff about with partitions but this was only due to previous amendments I made with linux mint / windows / dos. Install went fine. Slightly frustrated that the audio visual codecs don't come with the release (linux mint packs them in as default) but that's easy (ish) to fix - only, I don't have the internet at home, and I have to generate a package list and take this to my local internet café and manually download each package and then install each one by one when I get back... works though.
One major bugbear though
NVIDIA
God's teeth
It transpires lucid lynx incorporates as part of initrd.img (i think) the Nouveaux (faux NVidia device driver) driver and as such this might be responsible for why none of the nvidia / linux device drivers sucessfully install. One nearly did - but after checking, it did nothing but install a dud link to my 'system' menu and stopped a few games working...
So i'm yet to fix this but might try tonight after work
 
Wish me luck *crosses fingers* ;-)

---

### Post by tdyboc on 2010-06-14
Originally messed around with Karmic (server), got it installed and functional on my AMD Phenom II X2 Black Edition with 64bit.  Upgrading to 10.04 failed, after reboot it would not function.  Scraped that and started with 10.04 server.
 
Now, I use hardware RAID5 from an LSI MegaRAID 150-6 controller with 6 500GB drives.  Created my 2 arrays partitioned using LVM and the installer sees them as well as I can expect I think.  The install process begins and does its thing but when it gets to GRUB install I cannot install GRUB at all.  I want to place GRUB/2 into the /boot partition but it fails.  The /boot partition is the first primary partition on the first array sized and 500MB and it says its a type 83 partition from every way I look at it so it should be vaild and usable.
 
I then had to install without a bootloader to try and come back and fix it manually and I have not had enough time to devote to that work, yet.  One thing I did notice was that upon entering rescue mode the system complains that the /boot partition contains no partition table, strange.  Attempted to mount the /boot partition and once complete there are no files there.  There are files on several of the other file systems /usr, /var etc.  Disturbs me that /boot was not used/worked during the installation if that is in fact true.  I am going to attempt to try the MBR method but I suspect that to will also fail.
 
Past experience with other distros and this same hardware worked without issue.  Why does Ubuntu struggle so?  I'll continue with my installation attempts to see where I end up.  Will post here with additional findings or troubles.
 
Any advise appreciated.

---

### Post by tdyboc on 2010-06-14
Originally messed around with Karmic (server), got it installed and functional on my AMD Phenom II X2 Black Edition with 64bit.  Upgrading to 10.04 failed, after reboot it would not function.  Scraped that and started with 10.04 server.
 
Now, I use hardware RAID5 from an LSI MegaRAID 150-6 controller with 6 500GB drives.  Created my 2 arrays partitioned using LVM and the installer sees them as well as I can expect I think.  The install process begins and does its thing but when it gets to GRUB install I cannot install GRUB at all.  I want to place GRUB/2 into the /boot partition but it fails.  The /boot partition is the first primary partition on the first array sized and 500MB and it says its a type 83 partition from every way I look at it so it should be vaild and usable.
 
I then had to install without a bootloader to try and come back and fix it manually and I have not had enough time to devote to that work, yet.  One thing I did notice was that upon entering rescue mode the system complains that the /boot partition contains no partition table, strange.  Attempted to mount the /boot partition and once complete there are no files there.  There are files on several of the other file systems /usr, /var etc.  Disturbs me that /boot was not used/worked during the installation if that is in fact true.  I am going to attempt to try the MBR method but I suspect that to will also fail.
 
Past experience with other distros and this same hardware worked without issue.  Why does Ubuntu struggle so?  I'll continue with my installation attempts to see where I end up.  Will post here with additional findings or troubles.
 
Any advise appreciated.

---

### Post by cb5online on 2010-06-14
What happens when you use rescue mode to update GRUB through the menu? On mine (granted, nowhere near as complex as your setup) that did the trick when I deleted the first partition to get rid of window$ and took the mbr out with it... wouldn't reboot but does now
Also is /boot within a LVM partition? Could this mean that GRUB needs a non-LVM partition to boot from? Hence why, although it's looking at /boot like it's been told to, it can't read it, because LVM support hasn't been loaded at that stage?
Might be talking complete balls but just following my own train of thought... ;)

---

### Post by tdyboc on 2010-06-14
Yeah, I thought about this after writing the statement, I might have /boot set as LVM but I am almost positive I don't.  I have to look later this evening.  I have always done a /boot partition in the traditional fashion.  I just found it odd nonetheless it had no files in it ;-)

---

### Post by Benchrest on 2010-06-14
Overall very pleased! I had a few problems. The installation disk started in 1280x800 which my laptop is, but wrapped very badly and hard to find where to select. Finally got it to 1024x768 and all was well. Thought I would do the same after install, but on first boot the screen was so scrambled I had know idea where it was. could not see to login. Found a post to use nomodeset with grub2. Found that was very easy to edit on startup.  After I got a proprietary driver installed I was able to use 1280x800 again. Wireless worked great after I got the broadcom driver installed. easier than 9.04 . Most of my issues were not with Lynx but with getting my applications set up again.  disappointed that Sunbird was dropped from the repositories but I got it installed from the Mozilla site with a little help. Let this run a few days and then do my wifes.

Oh I moved the buttons to the right.  Either that or have the wife throw something at me. Seriously, users who are just users don't want to have to learn something new after using one way for ever without there being some benefit. 

Also switched from 64 bit to 32 bit on my laptop. Occasionally I have problems where an application is available for 32 bit but not 64 bit. Still Lynx boots a bit faster and starts applications a bit faster than Jaunty.

I hate the "are you sure message" when I shut down. I found Ubuntu Tweaks allows turning it off. Also not getting notified of updates. On research I found the answer and went to put it in my notes for next upgrade and it was already there

Have discovered bug 585008 . Keyboard locks up if press the disable laptop touchpad. There is a temporary workaround by using ctrl alt f2/ ctrl alt f7. did not occur on 9.04

---

### Post by Che69 on 2010-06-15
Thanx !!! Upgrade worked perfect... had some fault messages, but didn't have to do anything to them. OO I had to install fresh, but nothing seems to be broken. Cheers =D>

Computer seems to run smoother and looks a little bit nicer... only thing I need to get used to is the program-exit-switch on the LEFT now. 8-[

I was quite afraid something bad would happen, 'couse this is my work PC and I'm the only one at office with Linux... so called lonely rider / rebel... :-\" I would have been in deep s**t if something would have happened to my work data.
So I'm very happy everything  worked so fine !

:guitar:

---

### Post by irv on 2010-06-15
> Che69: Computer seems to run smoother and looks a little bit nicer... only thing I need to get used to is the program-exit-switch on the LEFT now. 
You can install Ubuntu Tweak and use it to customize a lot of Ubuntu including the position of the navigation button on the top of the windows. Check out this video on youtube.
[http://www.youtube.com/watch?v=HWZqtLXkRQQ]("http://www.youtube.com/watch?v=HWZqtLXkRQQ")

---

### Post by WatchingThePain on 2010-06-16
I upgraded from the great Jaunty to karmic. Karmic seemed buggy so upgraded to Lucid Lynx. Upgrades worked flawlessly.
Anyway..10.04 is nice, fast. Changed Gnome for KDE..looks good, works well except for ye old flashplayer problem.

It's a shame really since I often watch youtube but at present cannot do so at all. I'm AMD64 hence the problem.

Past experience tells me to wait as an update will fix this. I wish they would hurry up because to me it is an important issue. Loads of ppl have amd64 and need flashplayer to work.
Apparently it is something to do with Adobe.

Maybe I can try running 32 bit flash in this but I can't be arsed right now.

Indeed Jaunty had this problem at first (also amd64) but updates fixed it.

End of rant.

---

### Post by irv on 2010-06-16
> **WatchingThePain said:**
> I upgraded from the great Jaunty to karmic. Karmic seemed buggy so upgraded to Lucid Lynx. Upgrades worked flawlessly.
Anyway..10.04 is nice, fast. Changed Gnome for KDE..looks good, works well except for ye old flashplayer problem.

It's a shame really since I often watch youtube but at present cannot do so at all. I'm AMD64 hence the problem.

Past experience tells me to wait as an update will fix this. I wish they would hurry up because to me it is an important issue. Loads of ppl have amd64 and need flashplayer to work.
Apparently it is something to do with Adobe.

Maybe I can try running 32 bit flash in this but I can't be arsed right now.

Indeed Jaunty had this problem at first (also amd64) but updates fixed it.

End of rant.

I'm running the 32bit, and loaded the 32codec's, can't you load the 64codec's so you can do videos? How about the restricted extras, did you load them?

---

### Post by WatchingThePain on 2010-06-16
Yes, restricted extras done..that used to work but no joy.
Codecs..the evil that men do.
I don't care anymore. Jiggery poker from me will not do this.

---

### Post by WatchingThePain on 2010-06-16
update..it works now. Made sure I had restricted-extras then removes gnash and swfdec. Leaving me with a pretty perfect OS. One other thing I noticed in KDE is the fonts are not as smooth as gnome. Which I think used MS fonts.

So yes..pretty flawless upgrading. Glad to see that.
Well done.

---

### Post by pme 72 on 2010-06-16
I did a clean install on Saturday of the 32 bit version of Lucid Lynx. I voted incorrectly though, I voted flawless update when it was a flawless install. My apologies, I was a little over eager to share my enthusiasm. 

My system presented no hurtles for the install, one hard drive, hard wired to the internet, ATI open source drivers for a Radeon x1550 graphics card and no other operating systems. Flash and all the codecs installed with no issues. DVD movies play with VLC media player, Hulu works, YouTube works, Rhythmbox plays my music files, Evolution recognized my backup file, Gnucash recognized my backup file, Compiz works and suspend works. My backup device was an 8GB USB flash drive and it worked. 

The Radeon x1550 struggled a little with one of the more demanding courses from SuperTuxKart so I used that as an excuse to see if a Radeon HD4550 had open source 3D support. On 9.10 the HD4550 worked beautifully with the fglrx drivers, I could even play Second Life. The open source drivers had great 2D performance but just about no 3D so I ended up using the x1550. With Lucid the HD4550 has much improved 3D performance, even better than the x1550. SuperTuxKart plays with no issues. Glxgears went from 266 in 9.10 to around 1400 in 10.04. Great work from the open source driver developers!

Wonderful install, thank you Ubuntu Team for your hard work. The system is quick and responsive and has a nice refreshing new clean appearance. Karmic 64 bit worked great for me and I was expecting a big let down. I am impressed, thank you again.

System specs:
Compaq Presario desktop
AMD 64 3500+ processor
3 GB ram
ATI graphic card

---

### Post by joncrndl on 2010-06-16
[B][SIZE=2]The new kernel video architecture can be a REAL show stopper and puzzler when it strikes.  If one has an older version of Ubuntu to try then the real head scratching starts.  I seen a lot of questions on  the forum that point to this issue.  It does not as rare as hoped.  A blank screen is no way to introduce Linux to a new user. :confused:  Defaulting to a 800x600 display would at least give some information from which to dig out of a hole.  
[/SIZE][/B]

**Working  around bugs in the new kernel video architecture**

 Ubuntu 10.04 LTS enables the new  kernel-mode-setting (KMS) technology by default on most common video  chipsets.  While this is a major step forward for the graphics  architecture in Ubuntu, in some rare cases KMS[COLOR=Red] **will prevent your video  output from working correctly, or from working at al**l.[/COLOR]  If you need to  disable KMS, you can do so by booting with the nomodeset  option.  You can also save this setting so that it's applied at every  boot by adding it to your grub config (for GRUB 2: edit /etc/default/grub and add nomodeset  to GRUB_CMDLINE_LINUX, then run sudo update-grub; for GRUB 1: edit /boot/grub/menu.lst and add nomodeset  to the line beginning with # kopt=, then run sudo update-grub).  ([533784]("https://bugs.launchpad.net/bugs/533784"), [541501]("https://bugs.launchpad.net/bugs/541501"))
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture")

BTW - this did work for me. :)   Normally, I don't read release notes, but after spinning on this to get Ubuntu working on a friends HP Pavilion a1510n with Nvidia chip set, I do have Ubuntu 10.04 working mostly.  There is still one error about the screen which keeps the Nvidia kernel from loading. :(

Once I figured out how to get past the KMS issue, the install went very well.  The import of files and setting from the Windows XP disk went very well.

---

### Post by SWT_nux on 2010-06-16
so far not bad.
i have a couple of desktops, one file server, 2 laptops and one new netbook all running buntu or dual booting with windoze. everything was working great, even the old laptop with the broadcom 4300 wifi seemed easier. the newer laptop with the rlt8900 wifi went smooth and i was really giddy. then i tried installing unr on my new netbook and suddenly remember why i still dual boot. had to compile a driver for the atheros 2427 wifi chip. i thought by 2010 wifi driver issues would be a thing of the past.
when stuff like this happens, all those folks that i have converted to buntu from windoze slowing start falling off the wagon.

still great os, still rips my bread when ever i try to spread it!!!

---

### Post by getjondy on 2010-06-17
this was my first experience installing and dealing with ubuntu and it worked extreamly easy for me, i even setup a dual boot with win7 installing each OS in a separate hard drive and using grub as my booter as a final touch i install burg to make my boot screen look just awesome.. it cant get better than this!!

---

### Post by PoopyTheJ on 2010-06-17
Horrific. I've never had a more unreliable OS. Freezes, failure to boot, lost home partition, infinite boot/login screen. I'm done with 10.04, I may try 10.10 but I'll never use 10.04 again.

---

### Post by irv on 2010-06-17
> **PoopyTheJ said:**
> Horrific. I've never had a more unreliable OS. Freezes, failure to boot, lost home partition, infinite boot/login screen. I'm done with 10.04, I may try 10.10 but I'll never use 10.04 again.

What did you try to install/upgrade it on? Are you booting with more then one OS? You didn't give us much information.

---

### Post by fancypiper on 2010-06-17
When is this thread due to be closed? Ubuntu 10.10 is available now.

---

### Post by irv on 2010-06-17
> **fancypiper said:**
> When is this thread due to be closed? Ubuntu 10.10 is available now.

But only in the bata release. It doesn't officially come out until Oct. 2010. 10/10. The version/date number.

---

### Post by Chame_Wizard on 2010-06-18
Clean installed Lubuntu Lucif Lynx on a Pentium 3 and a P4 with 512 MiB,both are working good.

---

### Post by papibe on 2010-06-22
First of all, Lucid is great! :p  Right now I have working: dual head, vdpau, mplayer, no tearing, compiz, a cube on each screen, and dual boot.

Here's come the ugly: installation was a magnificent royal pain in the butt ](*,). This is why, and how I fixed it.

Grub didn't recognize my Vista partition, so (1) I couldn't import any settings, and (2) I lost the ability to boot windows. I tried to update grub, but it still did not work. After I run the famous "Boot Info Script", I realized that at least my partition was there, but also learned that my problem will require a much longer path to solve it.

[INDENT]BTW, this was a great help: [http://ubuntuforums.org/showthread.php?t=1492566]("http://ubuntuforums.org/showthread.php?t=1492566")[/INDENT]

So I went ahead and use my Vista recovery DVD, repair the mbr(?) block, and hey! I recovered Vista; only to loose grub and Ubuntu.

After that, I had to recover grub from the Ubuntu live CD, and finally got grub back.
[INDENT]This explain it pretty well: [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")[/INDENT]

Now dual boot works, with the caveat that the option for Vista grub calls it "Windows Recovery Partition"... oh well, may I'll fix that later.

Any how, thanks to wilee-nilee and "ranch hand" for your contributions in that thread.
Regards.

---

### Post by jesuisbenjamin on 2010-06-24
Hi there!

Thanks for making Ubuntu a reality: i'm glad to use it and glad i can participate in my own humble way.

Installation went well, it was fluid, fast and clear. Usage is great too, it's faster, cleaner, user-friendly. I love it.

Now the disappointing part is principally customisation (esp. Gnome). One of the most silly thing i have come across is the "Indicator Applet" which groups volume control with mail and broadcast, and rythmbox. Another instance is the me-menu which is inseparable from the shut-down menu. The most irritating thing is i cannot change it in 2 or 3 clicks. Another thing is simply customising the theme sound at login (i just never like the theme of Ubuntu) which appeared to be impossible in the sound preferences!

Overall it's great really i just think however the Gnome-panel should be taken more seriously and be fully (but simply) customisable. It is, after all, one of the main tools of the interface. I'd rather have no cube-desktop at all (which i am not using anyway, but any super-cool special effect) than a mail-icon stuck to my volume control.

I hope this feedback makes sense.
B.

---

### Post by Kixtosh on 2010-06-26
Well, I can't really complain. I thought I would have to install Puppy on the HDD of my old Portégé 3790CT. It has a maximum allowed 256MB of RAM, and the CPU is a Mobile PIII 700. I wiped Karmic and installed Lucid Lynx _Xubuntu_. 

Just about everything seems to work, including my obscure wireless-b PC Card. FireFox was slow, though, so I added the LXDE mega-package. This gained me 10-15 seconds on startup times, now down to 55-65 seconds. Chromium web browser gained a few extra seconds to start in about 8 seconds the first time, about 3 seconds every other time (during the same session). There's no real need to consider Puppy much at this point.

_Only issues_: hibernation works, but it doesn't save much time. Standby does not work (I get a blank screen with a flashing dash "-"), and I have to force a shut down to restart. Screen saver does not work either, so I had to disable it.

_Conclusion_: For my old Portégé laptop, Xubuntu 10.04 & LXDE is a clean, stable system for a secondary laptop that can surf the web and edit documents. So far, so good!

---

### Post by SaintDanBert on 2010-06-26
Installed to a Lenovo ThinkPad X61-tablet. Most of the "laptop" features worked out-of-box, while most of the "tablet" features did not work at all or have serious troubles.

Troubles with audio and video codecs vs. whatever comes from the net as well as "commercial" CD and DVD content.

Many of the "tablet" troubles involve the 2nd (external) display, digitizer, touch pointer, stylus pointer, keyboard, and various buttons. The event-drive, dynamic configuration of X11 does well enough that "laptop" use works well enough. Beyond that there is little joy and even less documentation.

~~~ 0;-Dan

---

### Post by libssd on 2010-06-26
I need to update my post of May 18 (#879), as I have successfully installed 10.04 since then, and I like it very much, especially the startup/shutdown speed. It appears that most of those who have had problems with 10.04 have had them with video cards or with grub2. I was in the latter camp. 

While I certainly understand Canonical's desire to tout Ubuntu ("It's fast, easy and used by millions") there really need to be more "read me first" caveats. If you have only one computer, and the Ubuntu installation process hoses it, you are not likely to want to have anything further to do with Ubuntu. I was fortunate that I have two computers, so I could find what grub error 15 meant, and how to fix it. 

The PDF guide, *Getting Started with Ubuntu*, needs to be much more accessible (I stumbled on it by accident; previously had no inkling of its existence). When a new guide is released, it really needs to place more emphasis preparation (including having a restorable backup) before installation, such as Keir Thomas provides in his excellent *Ubuntu Pocket Guide*. There seem to be quite a few Vista and Windows 7 users who have had disastrous first encounters with Ubuntu, which is unfortunate both for them, and for the Ubuntu community.

I'm still very enthusiastic about Ubuntu, but too many people in the Linux movement have an attitude of, "Well, you should have thought about that before you tried to install." If risks are involved (and they obviously are), we need to be upfront with people, and encourage them to make backups, and be prepared for possible glitches. "Fast and easy" doesn't cut it when your computer no longer works.

---

### Post by laithk50 on 2010-06-27
10.04 is amazing!
I installed it on my net book (Asus Eee PC 1005PE) and its running like a charm...I had to fix the screen brightness function keys, but that was all spelled out at the ubuntu hardware compatibility page. I also installed Jupiter (for powersave and monitor out) and now all is well.

On my dad's old toshiba I used an upgrade but had to add some "i915_modeset=1" line to get it to boot...again after that it was flawless!

On my desktop I had the same problem with an nvidia card and fixed it too. (this computer's jacksense is also shot since forever, but seeing as its the only computer I did not check for ubuntu compatibility, I find the price of buying some speakers with headphone jacks acceptable)

On all of them I installed crossover office 9 (finally integrated) and Office 2007 (working on 2010)...sadly, I do need it...I DO!

Overall, I love Ubuntu 10.04!
Btw, my sisters now like ubuntu too because of the aesthitic things (one of them likes the new kde interface, the other likes the me menu)...my dad likes it since its his business computer and a LTS release was what he was looking for.:p

Ubuntu Rocks!:guitar:

---

### Post by prshah on 2010-06-28
> **laithk50 said:**
> I used an upgrade but had to add some "i915_modeset=1" line to get it to boot...

...and now you have lost video. Go on, try it; vlc, totem, etc; gdm will shutdown whenever you try to play back any video. Flash videos in firefox will work well; as long as you don't try to full screen them.

---

### Post by kirbyparufo on 2010-06-29
I installed Ubuntu 10.04 on a friend's Windows XP loaded with malware to the point that it was almost useless. Rather than send it in to get it fixed, he gave it to me. Having recently acquired a netbook with XP installed myself, I had no need for a second XP. Rather than throw out the thing, I decided to install Ubuntu on. Installing with a burnt CD was a chore. I got to the installation screen, told the thing to install, and nothing happened. I got an error and was taken to an Ubuntu desktop screen where there was an installer and installed through there.
 
After installation, almost everything works fine. I have two problems. One of which I will probably be able to resolve at my earliest convenience (I'm taking a vacation and have no access to the Ubuntu in question until tomorrow). The system thinks there is a floppy drive, but there isn't. After scanning my BIOS like a hawk, I found no references to a floppy drive whatsoever. I was able to disable the appearance of having a floppy through fstab, though one still appears in the disk utility (though I'm working on removing that too). Nothing about this problem has affected the performance of the system.
 
My second problem has to do with mounting USB drives. No matter what I do, USB drives are mounted as root and in and undesired location (USB0 in the media folder) as long as the "automatically mount and [COLOR=black]unmount USB Mass[/COLOR] Storage Devices" file from the Ubuntu software center is installed, making my USB drives unusable. I can manually mount/unmount/safely remove the drives via the Disk Utility program. I've asked for help, but I'm still unable to fix this issue:
 
[http://ubuntuforums.org/showthread.php?t=1516591](http://ubuntuforums.org/showthread.php?t=1516591)

---

### Post by woodzie on 2010-06-29
I don't usually comment or post on forums for no reason, but this deserves it.  I've been using Linux for over a decade now, and even though I've always enjoyed it (even when things not working got pretty annoying and time-consuming), with this latest release it really feels like a bona-fide proper operating system.  

I installed a fresh copy of 8.10 a while back, upgrading to 9.04, and then to 10.04, and the upgrade experience was painless.  Compared to upgrading Windows, it's miles ahead - and the system is FASTER now than it was after two in-place upgrades - amazing!

I even get less "tech support" calls from my wife, now that I've installed it on her computer.

Excellent job. Keep up the good work guys!

Cheers,
Darryl

---

### Post by cthlhu1987 on 2010-06-30
> **woodzie said:**
> I don't usually comment or post on forums for no reason, but this deserves it.  I've been using Linux for over a decade now, and even though I've always enjoyed it (even when things not working got pretty annoying and time-consuming), with this latest release it really feels like a bona-fide proper operating system.  
I installed a fresh copy of 8.10 a while back, upgrading to 9.04, and then to 10.04, and the upgrade experience was painless.  Compared to upgrading Windows, it's miles ahead - and the system is FASTER now than it was after two in-place upgrades - amazing!
I even get less "tech support" calls from my wife, now that I've installed it on her computer.
Excellent job. Keep up the good work guys!
Cheers,
Darryl
My first Linux was Ubuntu 8.04 on my Laptop (that, which I'm using now)... Good ol' times... I installed it to use it as an normal OS (not only to use it as a livecd to download drivers for Windoze), when I accidentally killed my Windoze installation (With some "optimizer" to optimze it for gaming... Actually I optimzed it for not working X() and needed an os right now. So I installed it first on an usb stick (and installing Linux on that stick wasn't healthy for the stick, some weeks or months after the install it started to show up fs errors), and, after I started to like it, I installed it on my hd. Now I do all the work under Linux and boot Windoze just to work with my ol Nokia phone or watch tv via my new dvb-t-usb-stick.

---

### Post by Azatos on 2010-07-01
I had two installation experience's with ubuntu,  At first I installed 10.04 on a clean installation and experienced numerous problems slow boot times, and some problems with root access like I didn't have admin access.  I eventually downgraded about a week-ago to 9.10 and decided to try it again.  For some reason it was flawless no boot garbage or slow loading times, no issues whatsoever.

---

### Post by byline on 2010-07-05
> **byline said:**
> OK, hubby was able to work out solutions to all three of my complaints:

- deleted rhythmbox utilities and removed rhythmbox from the panel.  Plugged in the Walkman and, voila, a folder opened with the Walkman's contents!
- to keep the mail notifier from opening every time you log in: System Preferences, Startup Applications, uncheck "Mail Notifier", Close
- to automatically set the swap partition as /dev/sda1, use sudo gedit to have /etc/rc.local end with:
swapon -a /dev/sda1
exit 0
So I guess I'll stay with 10.04 after all!:guitar:
Solving problem of using swap partition automatically.

The previously described solution, of adding a swapon command to  /etc/rc.local was actually more of a workaround than an actual solution.

Here's what hubby has figured out: the cause of this issue is that  /dev/sda1 is an old swap partition that was formatted a few years ago  and (apparently) does not contain a UUID in the superblock which Ubuntu  10.04 now requires in /etc/fstab.   No listing of a UUID link to  /dev/sda1 (ls -l /dev/disk/by-uuid) and trying to use sudo tune2fs -U  random /dev/sda1 indicated a UUID could not just be added.

So under System, Administration used Disk Utility to reformat /dev/sda1  and now (tada!) there's a symlink to /dev/sda1 in /dev/deisk/by-uuid.   Copied the symlink name into the entry for /dev/sda1 in /etc/fstab (sudo  gedit /etc/fstab) and after a cold  reboot swap was automatically used.

---

### Post by kamlapati on 2010-07-05
I have used Linux at home for nearly a decade, moving from Red Hat to SuSe before finding Ubuntu in around 2006. I've had no reason to change since then.

My previous system, an ASUS M3A78-EM based homebrew, had been upgraded several times and was running 9.10. It upgraded to 10.04 with no problems. However, I noticed that it would never boot the live 10.04 CD.

This weekend I upgraded my motherboard to an ASUS M4A89GTD PRO. Oops, no go. Black screen, monitor in power saving mode. Won't boot. Won't recover. No terminal mode. Nothing. 

The alternate install completed the whole process. Then wouldn't boot. Same result as above! Wow, that was a waste of time, and it overwrote a working install to boot! Ouch!

After weighing the alternatives, I'm now running Fedora 13 on my new box. I would rather run Ubuntu, and I will switch as soon as the bugs with the kernel and the video drivers are fixed. (BTW, I mean fixed on the live CD, I can't do some partial install at this point in hope of something to come.)

I was really hoping for a stable LTS. This is extremely disappointing.

---

### Post by DarinVR on 2010-07-06
I've tried Linux once every couple three years for the last 10-15 years or so.  I've always had trouble getting hardware to work right or there was a shortcoming with what software was available.  When I saw an article discussing the new Ubuntu release I figured I'd give it another whirl.  Wow! so much has improved.  I played around with it for about a week before deciding to go ahead and make it the primary OS on my main machine. I'm still learning a whole lot and in fact these forums have been the main source of information as I've been setting things up this past week.  All I can say is that so far so good.  I've had very few issues...and those I have had were easily addressed out here via a search. 

I chose the 64-bit variant and installed it on an Intel based machine.  Specs:

Asus P5KC MB
Intel Q6600 Quad Core @ 2.4GHz
8GB RAM (800MHz)
Nvidia GTX 260 Graphics
LG-DVD-RW
LG-BD-RW
HD1 - 1TB Windows 7 Home Premium 64-bit
HD2 - 500GB Ubuntu 10.04 64-bit
Creative X-Fi Fatility Platinum Sound Card
1TB USB attached WD-MyBook External Attached

I went ahead and did a fresh install of Windows 7 followed by a fresh install of Ubuntu.  I had zero errors during the install of Lucid Lynx and all I had to do after it booted up the first time was add the 3D Graphics Drivers.  100% of my hardware was found and usable out of the box.

The only issues I ran into were with Adobe Flash and Adobe Air.  I use a Macbook Pro when I'm mobile and I've grown fond of TweetDeck.  After reading through the forums out here I was able to get Adobe Air installed and finally get TweetDeck running...no offense Gwibber.  I also had some trouble with being confused on whether or not to use the 64bit version of Flash.  After installing that, most stuff worked but Hulu stopped working.  When I switched back to the 32bit version Hulu worked again.  My troubles wouldn't have been troubles if I didn't insist on being able to use the Hulu Desktop application.  Finally I found on this forum how to fully clean out the old installation of Flash and put it all back together.  In the end, everything works including Hulu Desktop.  When I want to play games its as simple as a reboot into Windows where the only thing loaded are games.  I'll tackle Wine someday but its not that big of a deal to me to have both OS's loaded.

I have used Gimp for a long time on the PC so there isn't much of a change there for my serious Photos and as for snapshots and what have you I've been using Picasa for quite a while as well.  Both are up and running here in Linux.  Probably the thing I will have to adjust most to is not having iTunes on my main PC.  I have it on my laptop but still it'd be nice.  Rhythm Box is "ok" but its not iTunes.  

Frankly, there isn't much beyond gaming that I cannot do in this environment so I'm sticking with it for the foreseeable future.  I'm enjoying the challenges of learning something new and fresh.  So far I would have to give this a resounding positive experience.  This is my first post out here so to all of those who have contributed to these forums, I thank you.  The information out here is outstanding.  I look forward to your continued assistance as I get deeper into this OS.  

Regards,

---

### Post by BlazeFire247 on 2010-07-06
I used Wubi once again, and the installation worked flawlessly. I used to have several problems installing before, but for Lucid Lynx, it works perfectly with no errors at all.

---

### Post by FlameReaper on 2010-07-06
Newcomer here, running a Windows Vista Ultimate x64 / Ubuntu 10.04 64-bit... although I upgraded to Lucid a few months ago. I jumped from Jaunty, and although I had upgraded to Karmic it didn't get to live long because I found out Lucid was already out by the time I decided to upgrade.

Installation was a breeze, and one of the things I liked after coming over from Jaunty is of course a desktop that looks much more sweeter (sorry for being a GUI lover though, hard to live without those :P), and that my Wacom tablet is now supported out-of-the-box. Nice.

Although this updates have its hiccups, like driver issues - the first time I encountered issues with it all I did was reinstall the driver completely, and there was once I messed up Ubuntu that I didn't know what to do except a reinstall (using Wubi). I quickly learned my lesson since then... but for the graphics issue (my laptop was using NVIDIA GeForce 7000M / nForce 610M as integrated graphics)... I somehow got around with it. Now I'm using KDE as my window manager, and somehow using it really helps me fix my graphics issue (too lazy to explain here), and I'm liking it very much.

... Now all I need is a larger hard disk for this laptop... if I can get one. I'm currently running Ubuntu with a very tight check on disk space usage, using only 7GBs for all of it. And numbers are still ticking down...

---

### Post by KEE on 2010-07-06
this thing is suppose to be cooler then a brass monkey balls, however its dog poop because it takes too much ram. also nvidia 120m driver is not working right either...this OS is a fail!! 
```
inops@ops:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3529       1179       2350          0         80        480
-/+ buffers/cache:        618       2911
Swap:         4251          0       4251

```

---

### Post by irv on 2010-07-07
I have 10.04 running on my laptop since the release date and have had no problems. Last Monday I read about installing in via Windows and I have never tried an install like this so I thought I would give it a shot. (I didn't really need to install it seeing I have a dual boot system with Win7 but only wanted to try the install.) I was in a coffee shop when I tried it so I did have the install there and the last half when I got home. It installed flawless. I had to plug in a network cable when I got home because I need it to install a driver for my wireless card, but I don't consider that a problem. I need to do this anytime I install Windows also. I was going to remove it, but I am not short of RAM so I will just leave it installed for now and will wait until 10.10 is released when I plan to Install Win7 and 10.10 fresh.
I find this release or Ubuntu the best so far.

---

### Post by blackspyder on 2010-07-07
I upgraded via internet from 8.10 to 9.10 flawlessly, the internet upgrade failed (think my connection cut off) halfway through the 9.10 upgrade and left my system in a boot cycle. Luckily, I practiced what I've preached for so long (Since Fedora "Core" 4) and downloaded a CD .iso and burned it before starting the process. Outside of a few iPod sync, Xbox360 and windows networking snags. No major issues.

---

### Post by baguahsing on 2010-07-08
Brand new user of linux and Ubuntu. I'm a week old user. I installed the 10.04 netbook remix on a Toshiba satellite pro 6100 with a 1.6Ghz P4, 40Gb hard drive, and 256Mb memory. Since the install I have upgraded my memory to 1Gb, a definite improvement. Here are my issues:
 
1. Built in wireless will not connect. I bought an Asus usb-n10 wireless adaptor and am trying to build the driver. a work in progress
 
2. cdrom does not auto mount when media is inserted
 
3. Replaced aging battery with a new one. Now the battery indicator says I'm critical low but the led on the laptop is green.
 
Considering the age of the laptop these are minor issues. This is my learning platform since I inherited this laptop from work. I've wanted to try linux for a while but did not want to do a dual boot on my desktop computer which I built from scratch. If I "blow up" this laptop playing around with linux, no big loss. The goals are to learn linux, learn terminal, and possibly develop on a small scale. Ultimate goal - divorce windows totally including wine. That will be hard since some aspects of cell phones, ipods, and other electronics firmware / software updates can only be done in windows. I'm don't know how linux is on gaming (Sims 3). TTFN

---

### Post by nudge on 2010-07-08
I got 10.04 to load ok but, have problems.  Openoffice will not print labels, part of the program is missing and the OO people say I need to load another version of OO.  Sometime 10.04 will not allow me to read a travel drive.  Sometime 10.04 will not shut down. The survey shows 18% with problems. Thats too high.  Instead of all the eye candy the effort should go to making the 18% happy.   Thanks for effort to date, I'll never go back to MicroS.

---

### Post by MarilenCorciovei on 2010-07-09
[Installed on Dell Latitude D829]("http://www.len.ro/2010/05/ubuntu-lucid-lynx/"), everything worked ok except for vertical panels which do not work, notifications are drawn outside the screen. A bit annoying but otherwise perfect.

---

### Post by MadCookie on 2010-07-09
There was a tiny tiny issue....i got a lot of text when I shut down from the install giving some kind of error, but I have installed Ubuntu before, and I hit enter and rebootet. Apart from that, everything works fine.

---

### Post by aikiwolfie on 2010-07-18
Something that is beginning to bug me is losing my Thunderbird Lightning calender. It has important dates I need to check. I might even consider downgrading. I've used Thunderbird since before I migrated over to Linux. Losing Lightning support is a major blow.

---

### Post by ubalderdash on 2010-07-18
> **aikiwolfie said:**
> Something that is beginning to bug me is losing my Thunderbird Lightning calender. It has important dates I need to check. I might even consider downgrading. I've used Thunderbird since before I migrated over to Linux. Losing Lightning support is a major blow.

It would seem that the Lucid Lynx has many such problems. I gave up on Thunderbird and switched to Evolution. However, after a long and laborious migration I discovered that the latter is constantly failing tasks and making double copies of all my mail. The calender scheduler looks good but has a bad habit of losing entries !

Fortunately I have a laptop running Windows and Office Outlook, which is a more reliable solution.

---

### Post by Silvertones on 2010-07-18
My Lucid install has not hiccuped once since install. I don't lose my Lightning.

---

### Post by quixote on 2010-07-18
You can get a version of Lightning to work with the new Thunderbird, but for some reason mozilla doesn't have it yet.  Go here: [http://stage.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/](http://stage.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/) If you have a 32-bit version you want the i686 subdirectory.  If 64-bit, go to the contribs subdirectory and to the 64-bit version from there.  

It took me forever to find that after my Thunderbird was suddenly upgraded to 3 without even asking me whether I wanted to lose all my extensions!  Stupidest thing they ever did.  I'm like you about how essential Lightning is.  (Also Header-Tools, which I still haven't managed to get working!)

---

### Post by matera_the_mad on 2010-07-18
The poll has nothing that fits my situation (that's normal for me!).

I finally devoted a morning to letting Ubuntu do its thing. The upgrade went just fine, everything seems to be working. EXCEPT. [SIZE=5][COLOR=Red]The reversed window buttons are driving me bugfug.[/COLOR][/SIZE]
Is this really the new default, or is something screwed up? I mean, does everybody have the close/min/max buttons in the upper left now?  I can't find any option to get the window control buttons back on the right side where they belong. It is HELL, it's like a bad dream and I can't wake up.

Edited to add:
The solution was disgustingly simple -- I changed window themes. Completely. Just a minor change didn't do anything to switch button back to normal. But why did it get bollixed up in the first place? Thank goodness that was all that got messed up.

---

### Post by quixote on 2010-07-18
Yup, that's how it strikes almost everybody.  To fix: open a terminal, type "gconf-editor" (without quotes), In the window that comes up, go to apps > metacity > general, and right-click on button-layout. Select edit.  Change it to menu:minimize, maximize, close to get the old behavior.  The ":" separates what goes at the left from what goes at the right.  

I agree 100%.  They should have made it a simple right-click option to change it back.

(Just saw your edit.  Yup, changing themes to clearlooks will get the old behavior back too.  The gconf-editor thing works if you want some other theme, though.)

---

### Post by beerguzzler on 2010-08-18
Installed 64 bit flawlessly and running very happy as my mythtv media centre.

Same cannot be said for the 2 32bit pcs I have in the house.

PC1 - Having been merrily syncing my Windows mobile without any issues for the last 2 years, the same sound and stable SYNCE method just does not work (for me at least) in Lucid.

I receive Segmentation faults on numerous applications including trying to run any Administrative tools. Did read somewhere that that's probably the video drivers. Tried using both the 96 and 173 NVIDIA proprietary ones and also the latest build from NVIDIA, but I still have lots of Segmentation faults and system freezes.

Firefox (ok not Ubuntu's fault) is just a complete joke now. Crashes every time, no matter if I create a new profile and have no add ons. Run it again from Terminal to figure out what may be causing it and all I see is the Segmentation fault again.

3 times now I've reinstalled, even formatted the / and /boot partitions and still can't get a stable instance.

PC2 - Just doesn't work. Full stop. Boots up ok and after couple mins the thing just completely freezes.

So, thanks for a very stable 64 bit main system. 32 bit - well bye bye for now Ubuntu, I'm off to try another flavour.

---

### Post by DouglasAdams on 2010-08-18
i have posted previously in this thread about the horrendous experience i had when i "upgraded" (using update manager).

latest:

1)
i have given up trying to get any sounds out of my machine and i still can't print from O.O
i need to make a pdf and print that.
interestingly, my kids laptops (both still on 9.10) now have exactly the same problem yet all test prints, etc, are fine.

2)
i have had a number of "stops". e,g, lockups or system buzzer sounding. not as frequent as blue screens of death with an average windoze machine but i had none with 9.10 (totally new hardware at that point).

roll on october!

---

### Post by GenBattle on 2010-08-18
There's no option for both upgrade and install problems.

I've already posted in this forum outlining my problems, but my experience boiled down to a lack of good hardware support.

I first tried upgrading, but after the upgrade Ubuntu would report that various components of my ATi driver where missing. I reinstalled the driver several times but still got the same issue. 

Eventually i gave up, and resigned myself to a full install. My next problem was that when i tried to boot off the installation CD/USB, halfway through startup my computer screen would start turning itself off and on in a periodic pattern. Another video driver issue. Awesome.

So after trying both the x86 and x86_64 versions of the live cd, booting from both CD and USB and trying various boot options, i was still having no luck. So i resorted to trying to sort out my messed up upgrade. Eventually i resolved the issue by installing the driver from the repository (which still complained about missing files), then uninstalling it and reinstalling my original driver (from AMD's website).

Not really an upgrade or install issue, but i've also had problems with the Ubuntu driver for my network card bricking the network interface (doesn't respond in windows or GNU/Linux) until you do a hard reset. More recently my Ubuntu install is reporting a ureadahead exit with status 4 on boot, which i can't seem to find a fix for.

---

### Post by su-37 on 2010-08-18
Worked beautifully for me.

---

### Post by ssulaco on 2010-08-19
> **quixote said:**
>   To fix: open a terminal, type "gconf-editor" (without quotes), In the window that comes up, go to apps > metacity > general, and right-click on button-layout. Select edit.  Change it to menu:minimize, maximize, close to get the old behavior.  The ":" separates what goes at the left from what goes at the right.  

GUI
[http://www.omgubuntu.co.uk/2010/03/easy-gui-window-button-switcher-for.html](http://www.omgubuntu.co.uk/2010/03/easy-gui-window-button-switcher-for.html)

---

### Post by dargaud on 2010-08-23
I had some issues when upgrading to LL on my custom box at home, but since we are also going Linux-only at work, I installed it on my brand-new and maxed out Dell Latitude E6410. Almost flawless. I installed from the alternate CD because of the requirement for encrypted disks at work.

I just had to use nomodeset on boot (and keep it in grub). The webcam works with some apps (skype) but not with others. I can't find if there's actually a microphone on this PC. The smart card reader is not recognised but I don't even know what it would be used for (reading credit card chips ?)

---

### Post by DouglasAdams on 2010-08-23
small point. as 10.04.1 has been released would it be worth mentioning in the future which release the poster is referring to?

---

### Post by furiousjason on 2010-08-23
I installed Lucid Lynx a couple weeks ago. It worked flawlessly. Only problems I have had were not from the install but from things I wanted to do in Lucid like have drives mapped when booting up. Any other trouble I had I searched this site or google (which usually always linked to this site) for fixes or posted in the forums the trouble I had and plenty of users helped.

EDIT: I am unable to vote though!

---

### Post by SamSnood on 2010-09-10
Installed lucid on my laptop, worked flawlessly and a back-up machine, which had a problem with flash, Flashaid fixed the problem.  Decided to fresh install on my main computer that had 9.04 on it.  Had a flash problem again corrected by flashaid, and a freeze problem that appeared to be when the screensaver kicked in.  Changing to visual effects - none seems to have corrected that. Also can receive email but not send in thunderbird. Evolution works but I don't really like the program. 8.04 was so much more stable and problem free.

---

