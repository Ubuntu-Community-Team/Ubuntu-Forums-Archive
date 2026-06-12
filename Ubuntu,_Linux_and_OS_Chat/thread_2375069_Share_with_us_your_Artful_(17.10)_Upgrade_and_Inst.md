---
title: "Share with us your Artful (17.10) Upgrade and Installation Experiences"
date: 2017-10-21
forum: Ubuntu, Linux and OS Chat
---

### Post by cariboo on 2017-10-21
It's that time again, Artful (17.10) was released October 19, 2017 Please tell us about your experience upgrading, or doing a fresh install of Arful Aardvark.

Keep in mind that this thread is only for your experience, if you are having problems, please create a thread in the support forums.

Poll and thread for the previous release:



[https://ubuntuforums.org/showthread.php?t=2359321](https://ubuntuforums.org/showthread.php?t=2359321)

**Note:** I increased the expiry date to 180 days.

---

### Post by ventrical on 2017-10-21
> **cariboo said:**
> It's that time again, Zesty (17.04) was released April 13, 2017 Please tell us about your experience upgrading, or doing a fresh install of Zesty Zapus.

Keep in mind that this thread is only for your experience, if you are having problems, please create a thread in the support forums.

Poll and thread for the previous release:



[https://ubuntuforums.org/showthread.php?t=2359321](https://ubuntuforums.org/showthread.php?t=2359321)

Uhh  cariboo.. the topic header says 'artful' and you have zesty zapus in content?

Don't you mean experience with artful?

---

### Post by cariboo on 2017-10-21
> **ventrical said:**
> Uhh  cariboo.. the topic header says 'artful' and you have zesty zapus in content?

Don't you mean experience with artful?

I was still editing the post.

---

### Post by ventrical on 2017-10-21
> **cariboo said:**
> I was still editing the post.

Oh:)

---

### Post by sudodus on 2017-10-21
Ubuntu persistent live works in my 64-bit computers.

Lubuntu persistent live 32-bit persistent live (made with mkusb) works in
- my old Dell Dimension 4600 with Pentium 4 from 2004
- in an old IBM Thinkpad T42 with Pentium M (using the boot option forcepae)
- even in UEFI mode in my relatively new Dell Latitude E7240 with Intel Core i5 4200U

Lubuntu 64-bit installed in an SSD connected via a USB 3 adapter works in my 64-bit computers

---

### Post by Frogs Hair on 2017-10-21
Clean installation worked well .

---

### Post by ventrical on 2017-10-21
A most difficult testing cycle. Intel based  desktops worked very well for the most part but there were still issues with wayland and plymouth which seemed to get resolved on the ISO  on Oct.18th.

nVidia based graphics were just awful to get up and going all through the cycyle.

I can say I really like the finished product of "dry" gnome3 with wayland and/or xorg but I honesty don't like the fannaggling around of how  many , many xapps will not work on wayland, hence jockey back to xorg.

1. It is a power session and has potential to be a work horse.
2. Once bit , twice shy .. a trepedation to install apps for fear of breaking gdm or plymouth or wayland.
3. Excellent on the network and firefox friendly.
4. The panel is a honest effort to provide accessibility.
5. A+++ for devs because I know they really worked hard on it.. especially Jeremy.
5. A+++ for U+1 testers because I know our team hammered the smitherines out of it and many migraines later we have somthing we can all be proud     of. :)

Regards..

---

### Post by Erik1984 on 2017-10-21
One serious issue (still not a 'dealbreaker' as the upgrade seems to be successful): [https://bugs.launchpad.net/ubuntu/+source/cracklib2/+bug/1725116](https://bugs.launchpad.net/ubuntu/+source/cracklib2/+bug/1725116) Furthermore the network and volume indicator appeared twice in the panel. Fixed by disabling Volume Control in Startup Applications. The desktop now looks identical to 17.04 :D

---

### Post by SantaFe on 2017-10-21
Me, I got an error about the ttf-mscorefonts-installer.

> [INDENT] ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
 0% [Working]
0% [Working]
0% [Working]
 Err:1 [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
  Redirection from https to  'http://downloads.sourceforge.net/mirrorproblem?failedmirror=gigenet.dl.sourceforge.net'  is forbidden
 0% [Working]
 E: Failed to fetch [https://gigenet.dl.sourceforge.net/project/corefonts/the](https://gigenet.dl.sourceforge.net/project/corefonts/the)  fonts/final/arial32.exe  Redirection from https to  'http://downloads.sourceforge.net/mirrorproblem?failedmirror=gigenet.dl.sourceforge.net'  is forbidden
E: Download Failed
flashplugin-installer: processing...
[/INDENT]


Then of course every so often I'd get a pop up window asking if I wanted to try again.  Since the MS fonts were already installed, I just removed the package in Synaptic & will try it again later if they fix this.  Otherwise it was flawless.;)

---

### Post by cariboo on 2017-10-21
I just did a fresh install, setup Dash to Dock, Weather, and Random Wallpaper extensions, using the nouveau drivers everything works as it should. I did notice I have a mouse pointer on my main screen, while mousing around my second screen. I never ran into this while testing, but then I used the same installation all through the development cycle.

---

### Post by monkeybrain20122 on 2017-10-21
Did a clean install (keep /home) over 17.04 in one of my laptops. Spent most time on unity, it works very well (thanks to the effort of the testing team) except can't logout (both with GDM and lightdm), but this is a bug even in 17.04. Checked out gnome session on xorg and installed some extensions, works ok (not as bad as I thought from experience with Fedora) but not nearly as smooth as unity, feel constricting and animation a bit jerky. 

Other than the DE hasn't done much yet. there seems to be some issues with installing things with python-pip

---

### Post by wheatpenny2 on 2017-10-21
When I finally got it to install it worked flawlessly, but I had a rather strange thing happen with my first 3 attempts at installing it. First time it only allotted 9 GB (on a 1 TB drive) for the dual-boot setup. Second time, same thing. Third time there was no dual-boot option (just an option to erase the HD and install Ubuntu).  Then I tried turning the computer off completely and restarted it, and this time it worked exactly like it was supposed to (I have my HD partitioned in 2 equal-sized partitions, 1/2 of it to Windows 10 and half to Ubuntu).
Since installing it, I have had no problems so far.

---

### Post by litlesam on 2017-10-21
Clean install on kde - perfect
Clean install on Xubuntu - perfect
Clean install on Ubuntu ( 2 months back ) - still working perfect with no install issues at the time.

---

### Post by Perfect Storm on 2017-10-21
Clean install. Works perfect, my computer specs are in my signature. Though I can only log in Xorg not Wayland, but that's a known fact regarding restricted Nvidia driver.

---

### Post by Xian on 2017-10-21
Did an apt-get upgrade from an existing Ubuntu Gnome installation. 

Had no issues save the ones presented by Wayland.

---

### Post by yoshii on 2017-10-22
Fresh install of Xubuntu on an old HP EliteBook with both NVIDIA and Intel hardware components.  
Pretty much everything went OK.  Only issue was needing to be in user home directory when installing WINE-staging.  
Other than that, mostly no significant issues.  My config/prefs backups from Zesty transferred well.  

I was able to remove all the junk I didn't want and install other stuff I do like.  
gDebi doesn't seem to work though.  :(

---

### Post by Rocky_Bennett on 2017-10-24
I did a fresh install of 17.10 on to a little 250 gb SSD and everything is working perfectly. No problems with the install and no problems with the OS.

I am just having fun setting it up now.

---

### Post by olav.adapt.dk on 2017-10-27
I'm not happy 

**Upgrade**
Took a long time. Particularly since Grub config was recreated between each removal of previous entries. It would have saved me 20 mins or so if it hat done it once in the end.

**Terminal**
Copying from the terminal does not work. Neither:
 - Ctrl+Shift+C
 - Edit -> Copy

Have tried different clipboard managers and also no clipboard-manager with reboots in between - still no dice.

[B]27" monitor 2560x1440
[/B]The hack that made the monitor work with this resolution so far does not work and Ubuntu does not support it out of the box.
- I used xrandr to create a new, add and set a mode calculated with cvt
- Can't be bothered to type it here and copy from terminal does not work - jikes

So far I have:
- stopped using sudo to run the script.
- added: export DISPLAY=:0.0
- changed displayname from HDMI-1 to XWAYLAND1

I still get:
  - xrandr configure crtc 1 failed
And then (probably a symptom of the same problem):
 - X Error of failed request: BadName (named color or font does not exist)

Googling for answers does not turn up pertinent answers since (X)Wayland is still new mainstream technology.

My machine is a Lenovo X201i laptop with Intel Integrated Graphics. Drivers used to come with Ubuntu.

Updating has incurred many hours of wasted time and a poorer user-experience for me.

---

### Post by techguru30 on 2017-10-28
I was able to do clean install of Ubuntu 17.10 Artful Aardvark with no issues on my Gateway SX2855-UR20P.

---

### Post by chrisw22 on 2017-10-28
My install for the most part was flawless. After the reboot however things changed a bit. After the first reboot things worked fine (system always booted into sleep mode WTF) and no sound and overall the entire OS was very slow (video drivers??). Trouble was video and HDMI drivers. I found out after the fact that HDMI/video etc etc was not supported. My fault I should have read the release notes (I assume that must have been in there)  I am eagerly awaiting another try with Ubuntu 18.04.

---

### Post by jpberes on 2017-10-30
I did switch from Linux Mint 18.2 XFCE towards Xubuntu 17.10, complete blank install and I'm super happy for the results.
I can only say 'Good work Guys and Girls' ... Hereby an overview how my system does look like and this from scratch installed and achieved in 2h of time ;-)
[ATTACH=CONFIG]277346[/ATTACH]

---

### Post by johnbond777 on 2017-10-31
I blew away 16.04.1 and installed 17.10 clean.  My problems arose as soon as I started to download packages.  Synaptic fails terribly while trying to open.  Wireshark failed, and so did a few more items in the Ubuntu Software application.

Been searching to see if anyone else tried Synaptic on 17.10.  This is supposed to be a test machine to let me try out some tricks to bridge our developer's network from the corporate network... but I seem to be hitting a lot of walls.

---

### Post by Perfect Storm on 2017-11-01
Regarding Synaptic: [https://ubuntuforums.org/showthread.php?t=2375077](https://ubuntuforums.org/showthread.php?t=2375077)

---

### Post by ulysses77 on 2017-11-02
Worked, had things to patch though. A lot of display and graphical bugs, but hey, they'll patch it up over time.

---

### Post by ktat on 2017-11-02
Can't say I'm overly happy with the upgrade overall.

On the plus side:
Now when my bluetooth speaker connects, the sound settings are adjusted automatically
The layout is a little less cluttered on the desktop
Mouse sensitivity is better

Negatives:
Shotwell not responding well (particularly, can't use two fingers to zoom in/out)
super+f used to be a shortcut to file search, this has gone
When laptop wakes from suspend mouse is frozen
keep getting asked for my email password on startup
Need to select my profile at login (don't know why visitor is the default on this)
Wacom tablet isn't working as it used to

I have a Dell Inspiron 15 running an intel i7-7500U CPU with Ubuntu 17.10

---

### Post by hh1488 on 2017-11-02
My HP Spectre x360 laptop is pretty much un usable logging on in wayland. The desktop freezes if I try drag and drop a file or folder, Bluetooth and wifi does not work and in settings quite a few toggle buttons dont work, they go orange and do not slide to the right and perform their functions.

---

### Post by uRock on 2017-11-03
I upgraded from 7.04 to 7.10 and it went flawlessly on an older Asus laptop. I have a few complaints about some of the design decisions, but the software works and that is what matters most.

---

### Post by sudodus on 2017-11-03
@uRock,

Gutsy Gibbon was my first Ubuntu version ;-)

---

### Post by uRock on 2017-11-05
> **sudodus said:**
> @uRock,

Gutsy Gibbon was my first Ubuntu version ;-)

That's cool! I started with Jaunty Jackalope. Loved it.

---

### Post by sudodus on 2017-11-05
You didn't notice the typing error: that you upgraded to 7.10 :-)

---

### Post by #&amp;thj^% on 2017-11-05
Ha! Got ya all beat...Started with Ubuntu 5.04 (Hoary Hedgehog) :)
Except for uRock.

---

### Post by gallowglass on 2017-11-06
New-to-Early-Intermediate user. I felt it was important to try out what the desktop was going to be like post-Unity, so while I didn't need any particular feature of Artful, I upgraded (I let the installer write over my Xenial install because I have good backups). I have to say, I want to go back already.

The install went quite nicely. The interface is a little different, and I'm working on getting used to that. 
> Putting the buttons in the window's title bar was a very novel move, but it completely forgets about flow, leaving me confused when I get to the bottom of a page.
> I told the Dock to Always Hide, and I think I misinterpreted the intention of the setting. I couldn't access the Dock at all afterward, and I had to install GNOME Tweak to get it to appear. However, the Dock section does not show up in the Settings screen, so the Dock behavior can't be changed, it's just take-it-or-leave-it. Also, in Tweak, when I clicked on the Extensions > Dock option, it offered to let me "install" it. Sure, I thought, if I haven't got full function, why not? The install button pulled up the Software application pointed at... well, nothing. Bizarre.
 > In the Applications screen, which I've been using set to All to start applications, the scroll up and down the list is WAY too sensitive, and a slight move on the touchpad throws you from the top page of the list to the bottom, making accessing anything between the two pages a skill challenge. The answer is to use the PgUp and PgDown buttons instead of the touchpad, but... really?
> Two applications I really got into under Unity, guake and Cairo-Dock, simply don't work. I'm sure it's a product of switching from Unity to pure GNOME, but I'd been using these two programs to get around - as a matter of fact, I barely used the Dock's search function at all in Xenial. Again, it's understandable that they haven't caught up to GNOME yet, but... it's a major drawback as I relied on both and not on the Unity interface nearly as much.

So for the moment I'm quite unimpressed. I'll also freely admit that I liked the aesthetics a lot better in Xenial (the default login screen in Artful is just ugly). I'm a little afraid to play with things now, the Dock being such an odd experience.

Now, I'm determined to give this an honest trial so I'm knuckling down to use Artful for at least a week before I give up. Since I won't get to play with this computer much again until late in the week, I'll skip those days in my count. I'll see if I make some breakthroughs and can post about things late-to-end of week.

---

### Post by uRock on 2017-11-10
> **sudodus said:**
> You didn't notice the typing error: that you upgraded to 7.10 :-)

I can't Facepalm hard enough....

---

### Post by Jason80513 on 2017-11-10
I did an upgrade from the version that System 76 had installed on the system (17.04) - one of the first run of the new style Galagos. Everything seemed to work, but the Wayland Gnome desktop was disabled, or wouldn't work, or something. It was weird. So I ended up with a nuke-and-pave to 17.10. 

Pretty flawless. And the work you guys have done to make everything familiar - much appreciated! 

This is really well done - really usable. There are noticeable improvements over 17.04 (even using the Gnome desktop). Kudos!

---

### Post by Gottier on 2017-12-17
I installed Ubuntu 17.10 in a VM last night. I needed to test out some code in PHP 7.2, and decided to use 17.10 because I wanted to check out the new Gnome desktop.

I was able to accomplish my testing, but while I was setting up and performing the tests, I noticed a few things:

1) Apache restarts were so fast I almost thought something was wrong.
2) I've never really liked Gnome, and Ubuntu has made some tweaks, but I'm not satisfied.
3) Some of the Firefox page loads seemed glitchy. It wasn't a smooth transition that I'm used to.
4) I'm used to having menu bars at the top of my window, and there were none in some cases.
5) I will probably use a different flavor of Ubuntu, or perhaps Debian. As odd as it may sound to some of you, I like Unity, and feel let down. I first started in with Ubuntu over 10 years ago, and when Unity was introduced it made it feel way more stable to me. Unity made it feel like it wasn't a broken toy operating system. Gnome makes me want to cuss, and I'm not one who normally does that.
6) Why should I need an extension just for a suspend button? Oh, I guess I can use Alt ... but why? For the amount of times that I shut down vs suspend, it should be the other way around.
7) I'm hoping that there will still be some big tweaks to Gnome before 18.04, or I'll be jumping ship.

---

### Post by electrosteam on 2017-12-19
I run Lubuntu on an old Dell 5150 laptop, started up with a clean install of 17.04 32 bit.
Did an upgrade to 17.10 32 bit, and can not see any obvious differences.
I was having system freeze problems, and now after about 6 days of operation with 17.10 I have not suffered a freeze - hoping.
John.

---

### Post by raphaell2 on 2018-01-06
Not sure if this counts as an installation experience, but there's one small difference between Xenial an Artful where I find the change in Artful a bit annoying: Under Xubuntu, you can add an Xfce applet to your main panel that shows system load - cpu, memory, and swap use. In Xenial, that applet has a mouseover function where if you move the mouse to a part of that applet, you're shown data about the thing monitored by that part of the applet. Under Artful, that mouseover has apparently been removed, or at least it doesn't work. I prefer the Xenial version with the mouseover.

---

### Post by marciomj on 2018-01-10
I have an old Dell E6550 that I use as a Ubuntu testbench. Don't have any special program or file there, beside a couple of VirtualBox VMs.

I've made a clean install of 16.04, and I'm doing upgrades since then.

I've had some trouble from 16.10 to 17.04 (that were solved with some updates), but from 17.04 to 17.10 it was flawless (until now, at least :D)

P.S.: my main system is still running 16.04.

---

