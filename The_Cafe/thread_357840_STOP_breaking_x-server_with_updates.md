---
title: "STOP breaking x-server with updates"
date: 2007-02-10
forum: The Cafe
---

### Post by Tucatts on 2007-02-10
OK a little rant here. Installed the most recent updates this morning and  upon the required reboot x server was broken again. I must really like Ubuntu because this has happened MANY times now. If this keeps happening it will eventually turn people off and they will just go back to windows or another distro. Can't this be checked first? The only positive about this is that it has happened to me so many times that I can fix it! Six months ago I would have just poured a cup of coffee on my machine and said the heck with all of this! HA HA. But seriously, if the Ubuntu team wants people to use this OS for their business and personal use as a primary OS please check these updates more carefully. I would rather not have to reconfigure x server every few weeks. Other than this problem Ubuntu is GREAT, works like a charm!
I think I am going to just turn off updates if possible.
Tucatts
using Dapper by the way

---

### Post by aysiu on 2007-02-10
It's intended to be fixed by Feisty in April:
[https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x](https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x)

And since it is a rant (and not a support request), I'm moving your thread to the Cafe.

---

### Post by Tucatts on 2007-02-10
AH thanks, was not sure where to put this. Don't have to rant much ha ha and will use cafe from now on.
Thanks

---

### Post by Paulr-55 on 2007-02-10
My Edgy update this morning states there are 6 updates available total 30MB download. But the list only shows 3 items totaling less than 1MB. Somethings not right here. I believe I will pass on this for now.

linux-headers-generic
linux-image-generic
language-pack-gnome-en

are the 3 showing.

---

### Post by delfick on 2007-02-10
hmmm....i update very frequently and i don't get x crashes.......

what's your system specs ??

i have

AMD Athlon 64 3500+ (in 32 bit mode)
Nvidia 6600GT PCIE
1 gig RAM
ubuntu edgy eft
gnome
beryl svn :D (irrelevant, i know :D)

---

### Post by slimdog360 on 2007-02-10
Im glad the mods took my advice when I told them to tell people of this, this morning. It broke mine in half then flushed it down the toilet. Long story short, Im installing gentoo now, its been going for about 3 or 4 hours and about 1/10th of the way done.
[http://ubuntuforums.org/showthread.php?t=357551]("http://ubuntuforums.org/showthread.php?t=357551")

---

### Post by Tucatts on 2007-02-10
P4 2.5
1.75 gig ram
Gforce 5500 nvidia

Only real problem I have with Ubuntu.Looks like Fiesty in April may fix this. Have tried Edgy and liked that fine, just have Dapper on my primary machine but will replace with Fiesty I am sure.

---

### Post by RandomJoe on 2007-02-10
I only had X get broken once, a few months back - just happened to be a couple of days after my parents finally decided to try Ubuntu...!  That was fun, explaining over the phone to my dad what he had to do - which he had to write down, then hang up because they are still on dialup!  Fortunately it worked.

This time, I'm glad I'm lazy.  Hadn't hit the update icon in a few days, then saw the threads about all the problems.  This morning (a few minutes ago, in fact) I finally ran Synaptic and did a Refresh, then checked the updates and everything went well.  This was on two systems - one 6.06 one 6.10.  Both use nVidia, but I just use the binary driver in the repo.

It does worry me to see this sort of major show-stopper appear, just wondering if there is even a "test farm" where devs try out releases before going live or it's just seat of the pants...! ;)  (Yeah, I know, kind of hard to have a test farm for a widely distributed group!)  For me personally, it's just a PITA - I've been around Linux too long for anything to really shut me down, but imagining what newcomers must go through...! :o

---

### Post by delfick on 2007-02-10
hmmm, maybe we need a quality assurance team :D

(though not one has thorough as the MTA:SA one.....so long before releases (though it's worth the lack of bugs in the end :D) 
([http://www.mtasa.com/](http://www.mtasa.com/).... hmm, that site's changed a lot since i was last there :p)

---

### Post by OffHand on 2007-02-10
Bulletproof probably will not make it into Feisty due to the delay of the new Xorg.
Furthermore it's logically you will need to re-install the driver if you do a kernel upgrade.
This is not a bug. 

Tip: Always leave a Nvidia driver installer in your /home so you can easily fix it with 
```
sudo sh NVIDIA-Linux-x86-1.0-xxxx-pkg1.run
```

If you do not remember the full name use tab for auto completion.

sudo sh NV<tab>

---

### Post by macogw on 2007-02-10
No updates ever broke X for me (not the August Dapper one that got a bunch of people, not the Edgy one a few months ago that got a bunch of people, and nothing on Feisty either).  Know why?  I use open source video drivers.  It's not Ubuntu's fault ATi and nVidia put out crap binary drivers that break if they touch a new kernel, but if they don't put out the new kernel, people will whine "my new hardware is supported in Fedora, but not in Ubuntu, why don't you guys catch up on the drivers?" and the answer is that the drivers are in the new kernel that they're afraid to release.  Bulletproof is for Feisty+1.  The new Xorg isn't coming out til like June or something.

By the way, to protect against these issues in future (at least I assume that's why), I've heard that from now on there will be a constant unstable branch for Ubuntu, the way Debian has.  I have a partition for "unstable," so I'll be staying on that pretty much for good.  I do have a stable partition, but I never boot into it.  Hopefully having some people running bleeding edge all the time will be enough to give early warning of binary blob + new kernel = oh crap.

---

### Post by FuturePilot on 2007-02-10
I don't understand this. I've heard that kernel updates break the Nvidia driver and therefore breaks X. But I have the Nvidia driver installed and I updated the kernel yesterday and nothing broke. Can someone explain this?

---

### Post by macogw on 2007-02-10
FuturePilot, do you have the open source or binary driver, and for which card do you have it? I'm fairly sure there are multiple binary drivers dependent upon which card you have.  There's also people using beta drivers so they can use Beryl, and they're more likely to have graphics problems.

---

### Post by Brunellus on 2007-02-10
> **macogw said:**
> FuturePilot, do you have the open source or binary driver, and for which card do you have it? I'm fairly sure there are multiple binary drivers dependent upon which card you have.  There's also people using beta drivers so they can use Beryl, and they're more likely to have graphics problems.
. . . which is why I keep insisting that people who run Beryl should accept occasional X breakage without whining.  Beta software--drivers, x servers, compositing managers-- BREAKS.  It is as much a fact of life as death and taxes.

---

### Post by FuturePilot on 2007-02-10
> **macogw said:**
> FuturePilot, do you have the open source or binary driver, and for which card do you have it? I'm fairly sure there are multiple binary drivers dependent upon which card you have.  There's also people using beta drivers so they can use Beryl, and they're more likely to have graphics problems.I have the binary driver for the GeForce 6600 card. And I am running Beryl too.

---

### Post by macogw on 2007-02-10
Maybe people with a different card than you are the ones getting the breakage *shrug*

---

### Post by seijuro on 2007-02-10
I use the binary nvidia driver in the repos and I have not had X break even once in the two years I've been running Ubuntu same for my wife's computer.

---

### Post by PriceChild on 2007-02-10
[SIZE=4][COLOR=Red][B]If you install 3rd party applications/drivers/packages/squirrels outside of the Ubuntu repositories then don't blame Ubuntu for your problems!

[/B][SIZE=2][COLOR=Black]The guide you followed should have explained to you that installing the nvidia drivers would require them to be reinstalled every time the kernel changed. If it didn't then go moan at them.

Ubuntu support everything in the repositories. If you decide to step outside the protection and support we offer then please don't blame us... we'll still try and help if you're polite :)

Pricey
[/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by Brunellus on 2007-02-10
> **PriceChild said:**
> [SIZE=4][COLOR=Red][B]If you install 3rd party applications/drivers/packages/squirrels outside of the Ubuntu repositories then don't blame Ubuntu for your problems!

[/B][SIZE=2][COLOR=Black]The guide you followed should have explained to you that installing the nvidia drivers would require them to be reinstalled every time the kernel changed. If it didn't then go moan at them.

Ubuntu support everything in the repositories. If you decide to step outside the protection and support we offer then please don't blame us... we'll still try and help if you're polite :)

Pricey
[/COLOR][/SIZE][/COLOR][/SIZE]
Testify, brotha.

---

### Post by Tucatts on 2007-02-10
Ok, hear you. However,, I have been polite and simply tried to  say that as someone new to linux and really trying to learn I was a bit frustrated with the x server problem I was having. Now, if there is a better way to install my nvidia drivers that Ubuntu will like and that will not result in a broken x server so much please let me know. I can uninstall the current drivers and install the correct drivers. Where do I find this? When you are new to this sometimes you really do have to have things spelled out to you. I do save the instructions though and never have to ask twice about the same thing.As I have stated I think Ubuntu is great and one of the best things about the whole process is this forum.
Thanks

---

### Post by PriceChild on 2007-02-10
Just install nvidia-glx from the repositories instead of using 3rd party versions then?

---

### Post by Tucatts on 2007-02-10
You mean from synaptic package manager?

---

### Post by PriceChild on 2007-02-10
That would be the one.

---

### Post by Tucatts on 2007-02-10
Roger that Price child, many thanks for the help.

---

### Post by Sunflower1970 on 2007-02-10
I have three different installs of Ubuntu. two on one computer (one's my test system) and then one that's set up as our main computer at home. I did one upgrade last night, had a bit of trouble with the nvidia drivers, but solved it...somehow--it was 2:30am in the morining when I got it to work fine...not even sure how I did it...I'll do it on my test system, but I'm spooked to do the update on my main computer.

Should I uninstall all nvidia drivers first, then do the upgrade? Then reinstall them after it's done...? I want to avoid as many problems as possible

---

### Post by HotFoot on 2007-02-10
I'm also having a problem since I updated my kernel to the *7.11 version (running Edgy Eft).  My xserver was broken, so I loaded into safe mode and ran:

dpkg-reconfigure xserver-xorg

Once I did that and rebooted, xserver would load, but I had no video acceleration.  Even scrolling through webpages laggs.  To see if 3D acceleration was working, I typed:

glxinfo | grep rendering

The output of which is:

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Then, I went into the Synaptic Package Manager and highlighted the nvidia-glx binary and marked it for re-installation.  This process completed sucessfully, after which I restarted my xserver via alt+ctrl+backspace.  Still, I had no video acceleration, so I ran:

sudo nvidia-glx-config enable

Then I restarted the xserver again.  Still, I have no video acceleration and the output of "glxinfo | grep rendering" reamains unchanged.  Is there something I'm doing wrong?

---

### Post by shining on 2007-02-10
> **HotFoot said:**
> I'm also having a problem since I updated my kernel to the *7.11 version (running Edgy Eft).  My xserver was broken, so I loaded into safe mode and ran:

dpkg-reconfigure xserver-xorg

Once I did that and rebooted, xserver would load, but I had no video acceleration.  Even scrolling through webpages laggs.  To see if 3D acceleration was working, I typed:

glxinfo | grep rendering

The output of which is:

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Then, I went into the Synaptic Package Manager and highlighted the nvidia-glx binary and marked it for re-installation.  This process completed sucessfully, after which I restarted my xserver via alt+ctrl+backspace.  Still, I had no video acceleration, so I ran:

sudo nvidia-glx-config enable

Then I restarted the xserver again.  Still, I have no video acceleration and the output of "glxinfo | grep rendering" reamains unchanged.  Is there something I'm doing wrong?

When you reconfigured xserver-xorg, did you enable glx in the Modules section ?
Check the /etc/X11/xorg.conf, and see if you've a line with 
Load "glx"
in the Module section

---

### Post by C-A on 2007-02-10
Is support for nvidia cards in the official repositories adequate?

---

### Post by HotFoot on 2007-02-10
Hi shining,

Thanks for the reply.  Yes, the line

Load "glx"

is in the xorg.conf file, along with several other modules.

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

---

### Post by jdhore on 2007-02-10
i use Edgy as well and i'm so afraid to do these 10 or so updates from the past week or so for fear of it either messing up my grub, adding another 2 entries to my already huge menu.lst, giving me some problem with the nvidia-glx drivers or having an issue...seriously...Ubuntu has a team of developers and a lot of people who are ok with breaking their system every once and a while...i think there should be like a Ubuntu...thing like edgy-unstable so the people that might want to take the plunge with new updates can find out problems before the people who really don't know what they're doing and don't want to bork their installs...people want Ubuntu to replace windows...well, whenever i've done a windows update, it's NEVER messed anything up in my OS and i think Ubuntu needs to have semi-bulletproof updates as well...or at least get a team to test the updates before you push them live

---

### Post by marcus2004 on 2007-02-10
As someone said eariler in the thread new kernels will cause you to need to reinstall your nvidia drivers. The easiest way I found was to download envy from:
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
And run the deb file and it will set up envy script which you can run and it will reinstall nvidia drivers and correct your settings. If you are left with nothing but the prompt just log in and:

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb
```

Then 
```
sudo dpkg -i envy_0.8.1-0ubuntu6_all.deb 
```
remember you can just sudo dpkg -i envy and then tab to print out the rest.

Then it will install envy. 
Then:
```
envy
```
And it will install the drivers and configure everything for you.

I have done this 5 or 6 times so far and it works great. 

And don't be upset if you have 3rd party drivers / software installed and things don't work right. 

PS. This is my first explaination with codes so hope it looks right and helps.

---

### Post by HotFoot on 2007-02-10
Heh... I do remember when I installed SP2 for Windows my computer was basically unusable.  Figuring out how to fix that problem was... fun (sarcasm).  But yeah, it's happened once.  User-friendliness still has a way to go with any Linux distribution, but things don't happen overnight.

---

### Post by HotFoot on 2007-02-10
Marcus 2004,

What configuration are you using?  I mean which kernel and what video card.  I just followed your instructions for installing envy.  It seemed to install okay, but when I ran it (and selected "1" to install the nvidia drivers), it took me to a blank screen with a cursor blinking in the top-left.  I left the computer for several minutes and when I came back, it was still at this screen.  I rebooted, and none of my settings seem to have been changed.  I still have no 3D acceleration and moving objects causes a lot of lag.

---

### Post by C-A on 2007-02-10
I installed my current nvidia driver with envy.

In order to update to the new kernal, would this work? :

un-install current driver with envy
install the ubuntu supported stuff
update to the new kernel
un-install the ubuntu supported stuff
reinstall nvidia driver with envy

---

### Post by FuturePilot on 2007-02-10
Would installing the Nvidia driver from Automatix make a difference to whether X breaks with kernel updates?

---

### Post by Tucatts on 2007-02-10
Ok, trying this again. I went to synaptic package manager and indeed found nvidia-glx. I installed this then ran the code to eable it in terminal and nothing seemed to happen. No nvidia drivers there. I uninstalled and reinstalled and still no effect. Must be leaving out a step .
SO went back to envy. ctl-alt-F1 and login. Put in sudo envy and reinstalled the nvidia drivers, no problem I am up and running fine. OK so for now I am just gonna live with it. I know how to reconfigure X ( dpkg-reconfigure xserver-xorg startx) and I can reinstall the drivers with sudo envy. SO I guess I have learned something, but still would be nice to not have this sort of hanging out there everytime I do a update. Of course this is kinda linux 101 and can't learn it if can't fix it ha ha. 
Kinda like how I learned to build or rather assemble my computers, last three machines I built myself. Got my training from my first machine years ago, a MMX166 with 16mb of ram and a 1 (ONE) gig hard drive. It was a train wreck from the start and I literally replaced everything in it but the case. Well, after awhile the mystery behind this stuff went away and I found out that man this is just assembling parts! Guess linux will be the same. 
Thanks for the help everyone.

---

### Post by HotFoot on 2007-02-10
After trying several times to get envy working, it seems something must be very wrong with my installation.  I can't even run envy with option 5 (restart the x-server).  I can restart my x-server with the alt+ctrl+backspace keys, however.

I've tried booting into the 7.10 kernel, but my 3D acceleration is gone there as well.  I suppose this has to do with all the settings/drivers being overwritten.  I've tried running envy with the old kernel, and still it doesn't work.  It now seems I've lost all 3D capabilities.  It doesn't make sense.  I should at least be able to revert to my old settings and do what I was doing yesterday.  Is something wrong with the nvidia-glx drivers now?

---

### Post by Sunflower1970 on 2007-02-10
> **FuturePilot said:**
> Would installing the Nvidia driver from Automatix make a difference to whether X breaks with kernel updates?

I used automatix originally to download the nVidia drivers, but when I saw the problems people were having with this new update, I uninstalled them, and then downloaded the updates. I then installed envy, and rebooted. Got myself to a command line, used envy, reinstalled the nvidia stuff, then in my xorg.conf file had to change nvidia to nv using nano, and then got to the desktop. I did this last night (ooo around 2:30am or so) so I'm now trying it out on another system I have to see if this will work for me a second time.

---

### Post by Tucatts on 2007-02-10
Future Pilot
 I have never tried installing the drivers with automatix with dapper. I did try it with edgy and it did work but not the first time. second try was the charm.

---

### Post by FuturePilot on 2007-02-10
Well that's what I did. I installed the driver through Automatix and I updated the kernel and nothing broke. But I did notice that there was another update along with the kernel. It was a nvidia-glx update. I'm not sure but I think if you installed the drivers through Automatix you won't break X with a kernel update.

---

### Post by marcus2004 on 2007-02-10
> **HotFoot said:**
> Marcus 2004,

What configuration are you using?  I mean which kernel and what video card.  I just followed your instructions for installing envy.  It seemed to install okay, but when I ran it (and selected "1" to install the nvidia drivers), it took me to a blank screen with a cursor blinking in the top-left.  I left the computer for several minutes and when I came back, it was still at this screen.  I rebooted, and none of my settings seem to have been changed.  I still have no 3D acceleration and moving objects causes a lot of lag.
I using Edgy but that shouldn't matter. I am using a geforce 6600gt so nvidia drivers. If you run envy in the terminal you can go to on the login screen it will not work. Try starting up in recovery mode and then try envy again. 
I usually install the newest kernel and it breaks the x-server and then I follow the process outlined. Hope that helps.

---

### Post by HotFoot on 2007-02-10
Well, I seem to have made some progress.  For whatever reason, the "linux-restricted-modules-2.6.7-11-generic hadn't installed (though I had the 2.6.7-10-generic ones).  I followed some instructions I found online and removed the "nvidia-glx" package, then installed the 2.6.7-11-generic restricted modules and then installed the "nvidia-glx" package again.  The online notes said that if you install the nvidia-glx package first, it won't be the correct version.

Next I tried running "sudo nvidia-glx-configure enable", only to get an all-too-familiar error message.  However, I noticed a little note onine that the above command is obsolete in Edgy.  The line you're supposed to use now is "sudo nvidia-xconfig".  Running this seemed to work, and then I hit alt+ctrl+backspace to restart X...

X failed, telling me I had a mismatch between the nvidia kernel module (1.0-8776) and the X module (1.0-9746).  I booted into recovery mode and ran "dpkg-reconfigure xserver-xorg" and went through the settings, choosing "nv" as the video card type.  Then I rebooted into normal mode.

Now the output of "glxinfo | grep rendering" is still not "yes", but at least there is no lag when I move objects around.  It was getting pretty annoying when the system would lag just scrolling through a web page.  Now to see about that 3D acceleration...

Oh yeah, and that website with the instructins I was following (not sure why this isn't linked from the ubuntu online documentation regarding video cards): [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Sunflower1970 on 2007-02-10
Two out of three of my updates worked. One painful but working very well now...one a lot easier than I thought, and the third..well, it was only a test system and I'm reinstalling Edgy now and gonna try again to update. :lolflag: 

For some odd reason, when I tried to run Envy on my main computer that has an nVidia 7600GT card in it, that the card wasn't supported...(?) So, I'm using Automatix again to get my 3D going, again. (Later on this coming week, I'm going to figure out how to use Beryl for the fun of id :D)

Is it me, or does it seem this last update made things boot up a bit faster....?

---

### Post by HotFoot on 2007-02-10
> **marcus2004 said:**
> If you run envy in the terminal you can go to on the login screen it will not work. Try starting up in recovery mode and then try envy again.

I followed your instructions and ran envy under recovery mode.  It certainly did at least most of what it's supposed to do.  It seems I'm now using something other than nvidia-glx to run my video card.  I think this is progress...

X is working, but I still do not have 3D acceleration.  I loaded the game TORCS and it immediately pins one of my cores to 100%.  Also, texture compression under OpenGL is not available.  The output of "glxinfo | grep rendering" is now "direct rendering: No".  I feel like I'm one step away from everything just working.  What might it be?

---

### Post by C-A on 2007-02-10
> **C-A said:**
> I installed my current nvidia driver with envy.

In order to update to the new kernal, would this work? :

un-install current driver with envy
install the ubuntu supported stuff
update to the new kernel
un-install the ubuntu supported stuff
reinstall nvidia driver with envy

I upgraded to the new kernel, rebooted my system, and as expected xserver crashed. I ran envy to un-install my current nvidia driver and then ran it again to install the nvidia driver. Now I have the updated kernel, nvidia driver installed, and xserver working thanks to the fine work by Alberto Milon.

---

### Post by HotFoot on 2007-02-11
Heh... well, the problem has been solved.  Envy works as advertised.  What I needed to do was uninstall the nvidia drivers before installing nvidia drivers again (both steps done with envy).  After re-starting the x server, everything works.  Beryl window manager is happy too.  Thanks for all the help.

---

### Post by leeyee on 2007-02-11
It has been good enough that the forum had given a notice on the index about the crash from updating. Ubuntu is the first distro that gives its most confused issues on the forum index. We should be patient and appreciate efforts from contributors. :)

---

### Post by macogw on 2007-02-11
ok people on #ubuntuforums say i'm wrong about the binary drivers being kinda "idk whatll happen" and that its the you installed it from elsewhere, so tough cookies! thing cuz the ones in the repos are tested beforehand

---

### Post by eduardoeltortuga on 2007-02-11
I'm SO confused! I installed Ubuntu Ultimate with a dual boot to XP. I got my Nvidia Geforce GT 6600 to FINALLY work after three days of searching Google and Ubuntu forums. I even figured out how to get my creative soundblaster card to work. I was SO proud. I even got Beryl to stop crashing after MORE searching (I used Automatrix Bleeder). It was BEAUTIFUL man! I was king for a couple of days! I was  Linux dude. I could finally scream "I don't do windows!" Then, I did an update to Ubuntu. "Failed to start  the x server" I tried to reconfigure, but to no avail! I tried to reinstall nvidia drivers, but alas, 0 upgraded, 0 newly installed, 0 to remove and one not upgraded is the message from this DAMN text screen! Can't even get to the GUI anymore. Can't figure out how to get new drivers from this text mode. I refuse to reinstall Ubuntu again!


Ubuntu to all, and to all a goodnight

---

### Post by nab on 2007-02-11
Hi,

ok, yesterday everything was working just fine. 
Working on toshiba m30x under 6.06 this is the first time x-server broke down or stalled after updating.

Well, unfortunatelly I'm not very firm in linux and connecting over an WPA secured wlan. I somehow I can't get this in recovery mode working  ...

ok, I really like ubuntu. It is way more stable than windows on my setup. But today I should work and not fixing first windows (I didn't care to repair it the last 3 month) to be able to access the internet und find an solution and secondly fix ubuntu.

just my 5 cents,
Nikolaus

---

### Post by marcus2004 on 2007-02-11
> **HotFoot said:**
> Heh... well, the problem has been solved.  Envy works as advertised.  What I needed to do was uninstall the nvidia drivers before installing nvidia drivers again (both steps done with envy).  After re-starting the x server, everything works.  Beryl window manager is happy too.  Thanks for all the help.

That is great. Glad that it worked out for you.

---

### Post by HotFoot on 2007-02-11
So just today I get the automatic updates for the restricted modules for the 2.6.7-11-generic kernel.  Thing is I've seen a lot of people ragging on those who complain after using 3rd party drivers that get broken with new kernel updates.  Before I was using the drivers according to the ubuntu documentation, taken from the repository.  That's what broke because when this last update was done, the kernel came out a day before the restricted modules.  Now I'm using envy to get 3rd party drivers because it turns out that's easier.

---

### Post by FuturePilot on 2007-02-11
I still don't get why nothing broke for me. Not that I wanted anything to break or I'm complaining:lolflag: 
Could it really be that nothing broke because I used the drivers from Automatix?

---

### Post by mistypotato on 2007-02-11
FuturePilot,

I have basically the same config you have and I'm going to Mondo my harddrive B4 I update so I can easily get back if anything goes wrong.  I also used Automatix to instal nVidia drivers so it will be interesting to see if I have the success with the updates you did.

This Linux Newbie did the smartest thing ever by becoming acquainted with MONDOARCHIVE very early on.   I have used it to "right" things many times and never have to "reinstall"..just replace with a few mouse clicks and viola!  I'm back in business...from where I was...NOT from the begining!   Now I do a Mondo only after I add new features or right before major updates like the one's available now.

Anyway, ever since the day I started using MondArchive, I've been a VERY happy Ubuntu camper.

I'll post the results after I Mondo and then install the updates.

MP

---

### Post by macogw on 2007-02-11
> **eduardoeltortuga said:**
> I'm SO confused! I installed Ubuntu Ultimate with a dual boot to XP. I got my Nvidia Geforce GT 6600 to FINALLY work after three days of searching Google and Ubuntu forums. I even figured out how to get my creative soundblaster card to work. I was SO proud. I even got Beryl to stop crashing after MORE searching (I used Automatrix Bleeder). It was BEAUTIFUL man! I was king for a couple of days! I was  Linux dude. I could finally scream "I don't do windows!" Then, I did an update to Ubuntu. "Failed to start  the x server" I tried to reconfigure, but to no avail! I tried to reinstall nvidia drivers, but alas, 0 upgraded, 0 newly installed, 0 to remove and one not upgraded is the message from this DAMN text screen! Can't even get to the GUI anymore. Can't figure out how to get new drivers from this text mode. I refuse to reinstall Ubuntu again!


Ubuntu to all, and to all a goodnight
uhh....wtf is "Ubuntu Ultimate"?&#12288;The only OS with an "Ultimate" is Vista, and I think that was delayed...

By the way, Beryl crashes aren't uncommon.  Don't be surprised if it crashes more in the future.  It's in "testing" mode, and you are apparently testing it to tell them it doesn't work.  Or rather, if it keeps crashing, you should tell them it doesn't work.

---

### Post by FyreBrand on 2007-02-11
> **macogw said:**
> uhh....wtf is "Ubuntu Ultimate"?&#12288;The only OS with an "Ultimate" is Vista, and I think that was delayed...

By the way, Beryl crashes aren't uncommon.  Don't be surprised if it crashes more in the future.  It's in "testing" mode, and you are apparently testing it to tell them it doesn't work.  Or rather, if it keeps crashing, you should tell them it doesn't work.I've upgraded with no problems.  I'm using Edgy, an Nvidia 6800XT, and Beryl with Emerald.

There are still 3 packages being held back.  It makes sense to me not to try and force an upgrade on those until whatever gets sorted out.

I use the ubuntu.beryl-project repos and have almost no trouble with them.  I don't install experimental plug-ins because this is my home production machine.  Sometimes I get a few quirks, but overall it's been pretty stable.

I have the beryl nvidia repos enable, but I noticed this last update to nvidia-glx 9xxx came from the ubuntu repos so I can only assume that ubuntu motu's have updated the nvidia driver.  So no X breakage for me.

A good thing to keep in mind, for those who are disappointed, is that just because an update is available doesn't mean it needs to be installed right away.  This is especially true, for me at least, with kernel and xorg updates.  Didn't a few wise people recommend some popcorn?

---

### Post by Migs on 2007-02-11
I am sorry if I sound negative but I really can't understand why people complain.

First of all and like mentioned before, the usage of binary drivers outside the standard repository's can cause problems when updating your kernel. It's almost logical that after a kernel update X won't start because the nvidia/ati driver is being hooked in kernel, when updating the kernel this hook will be lost causing that dreadful blue X screen. 

Second, if U you use binary drivers please don't copy/paste those commands from howto's in your terminal. Try to understand what is happening when you enter those commands , so when it gets broken you can fix it. Otherwise don't use it! 

Just a simple reinstall of your driver would have fixed all your problems.

---

### Post by FuturePilot on 2007-02-11
> **FyreBrand said:**
> 

I have the beryl nvidia repos enable, but I noticed this last update to nvidia-glx 9xxx came from the ubuntu repos so I can only assume that ubuntu motu's have updated the nvidia driver.  So no X breakage for me.
That's what happened with me. I got a nvidia-glx update along with the kernel, so I'm guessing that's why nothing broke.

---

### Post by HotFoot on 2007-02-11
> **Migs said:**
> I am sorry if I sound negative but I really can't understand why people complain.

First of all and like mentioned before, the usage of binary drivers outside the standard repository's can cause problems when updating your kernel. It's almost logical that after a kernel update X won't start because the nvidia/ati driver is being hooked in kernel, when updating the kernel this hook will be lost causing that dreadful blue X screen. 

Second, if U you use binary drivers please don't copy/paste those commands from howto's in your terminal. Try to understand what is happening when you enter those commands , so when it gets broken you can fix it. Otherwise don't use it! 

Just a simple reinstall of your driver would have fixed all your problems.

I'm not sure if you're responding to me, but everything I did up to the point of the kernel update was according to the ubuntu documentation.  I used the restricted modules to install the nvidia-glx driver.  When x-server crashed after the kernel update, I was able to understand that.  With a little help I got it working again using the instructions from ubuntu documentation.  I did, as you suggest, reinstal the nvidia-glx drivers, but this didn't work.  I spent all day trying to follow the official ubuntu instructions.

Eventually I gave up and now I'm using 3rd party drivers.  The next kernel update, I'll know better what to do, but the point here is that I was having so much difficulty even though I was trying to do things the ubuntu way.  I won't be complaining next time since from now on I'll be doing things with envy.

Oh, and another plug from a new envy fan: someone I've met at another forum was able to get drivers for his 8800 gtx card working by using envy, though it wasn't possible for him to get his card working with the repository drivers.  I was quite impressed to hear about that.

---

### Post by neighborlee on 2007-02-11
> **Migs said:**
> I am sorry if I sound negative but I really can't understand why people complain.

First of all and like mentioned before, the usage of binary drivers outside the standard repository's can cause problems when updating your kernel. It's almost logical that after a kernel update X won't start because the nvidia/ati driver is being hooked in kernel, when updating the kernel this hook will be lost causing that dreadful blue X screen. 

Second, if U you use binary drivers please don't copy/paste those commands from howto's in your terminal. Try to understand what is happening when you enter those commands , so when it gets broken you can fix it. Otherwise don't use it! 

Just a simple reinstall of your driver would have fixed all your problems.

well ,,and take this with grain of salt as im hardly a windows expert < haha yeah sure>..how does windows avoid this calamity when it updates things and avoids breaking a currently installed nvidia or ati driver ?..do they accept pros and cons of this procedure and linux does in other ways like this instance ?

cheers
nl

---

### Post by Polygon on 2007-02-11
with nvidia, are there default drivers that ubuntu uses if the nvidia drivers are not installed/ cause i know with my ati card, when i first install ubuntu, the resolution is all small and things are sow, but i still get a GUI (because it is not using the ati drivers but some default ones). The same thing with windows, when you first install it, the resolution is all crappy and things are slow until you install the correct drivers

so i guess why cant this be a feature in ubuntu? if a kernel update somehow messes up the installed ati / nvidia drivers, why cant ubuntu just fall back on some default drivers that will obviously lower the resolution and make everything slow, but at least keep the GUI working? (until the drivers get fixed by whatever person runs the computer)

---

### Post by rev_b on 2007-02-11
This will happen every time a new kernel is available on the repositories. It's not Ubuntu's fault, it's how linux driver model works. If it's not available on the kernel (as "nv" driver is), binary drivers have to be recompiled for each kernel.

It's not only Nvidia drivers, for instance, I had to reconfigure VMWare server for the new kernel release.

So, in order to not break X on a kernel update, either you install nvidia drivers available on the repositories (nvidia-glx), they will be automatically updated when a new kernel is out, or have the binary Nvidia drivers at hand (at your -/ directory, for instance) and be prepared to get a X error, get back to a console and do $ sudo sh NV*.bin to recompile and reinstall Nvidia driver to the new kernel. I don't see how that's hard, as if you have Nvidia binary drivers installed you did that before, as they wouldn't even install with X running...

And yes, fail-safe X would be preferable.

---

### Post by macogw on 2007-02-11
> **neighborlee said:**
> well ,,and take this with grain of salt as im hardly a windows expert < haha yeah sure>..how does windows avoid this calamity when it updates things and avoids breaking a currently installed nvidia or ati driver ?..do they accept pros and cons of this procedure and linux does in other ways like this instance ?

cheers
nl

Windows doesn't put whole new kernels in its updates, now does it?

---

### Post by FuturePilot on 2007-02-11
Now I'm even more confused. Isn't nvidia-glx the same as the binary drivers? That's what I'm using and Beryl seem to handle fine and I even see the Nvidia splash screen when I boot..:confused:

---

### Post by macogw on 2007-02-11
FuturePilot, but those are the in-repos binary drivers, not the "found them online somewhere" ones.  Ubuntu supports whatever's in the repos, but not stuff floating around online.

---

### Post by FuturePilot on 2007-02-11
Oh I see. But then if there are ones in the repos, why go online and find one yourself? Are they better or something?

---

### Post by macogw on 2007-02-11
The ones in the repos don't support every card known to man, so some people have to find them elsewhere.

---

### Post by FuturePilot on 2007-02-11
Ok now I see. Thank you, you've cleared everything up for me and now I now why nothing broke, it was because I'm using the ones from the repos. It all makes sense now.:KS

---

### Post by FyreBrand on 2007-02-11
> **FuturePilot said:**
> Oh I see. But then if there are ones in the repos, why go online and find one yourself? Are they better or something?The drivers in the repositories are not always the latest versions.  If a newer driver version has better support for newer features people my download them or install them from other repos.  It's nice that the driver has been updated in the official Ubuntu repo.

---

### Post by BrooksOfSheffield on 2007-02-11
Running NVidia 6200 LE AGP, Edgy, beta drivers + beryl. 

Used Synaptic to upgrade.  Rebooted.  X broken.  From terminal did apt-get upgrade, voila, new beta driver installed.  Rebooted again.  X works fine.

No complaints here.  If I was happy with Metacity, maybe I wouldn't have to do anything special...  but it's worth the work.  (And maybe the extra thought required).

Heh.  I mean, I spent an entire afternoon figuring out the proper modeline to get rid of overscan on my LCD television so I could do away with a regular monitor.

---

### Post by rev_b on 2007-02-11
With the Nvidia latest drivers you get also Nvidia X Server settings, a very useful control panel where you can configure twinview, color correction, Antialiasing / Anosotropic settings, and even overclock the video card with the right words in xorg.conf ;)

This

[img]http://img507.imageshack.us/img507/6342/nvidiact8.jpg[/img]

is reason enough to install drivers from [www.nvidia.com](www.nvidia.com)

---

### Post by cookfromfrozen on 2007-02-13
> **OffHand said:**
> Furthermore it's logically you will need to re-install the driver if you do a kernel upgrade.

What an arrogant statement.   Logical to who?  There is no notification whatsoever after the updates install that you will need to reinstall your graphics driver.  How is the typical user who has just installed Linux for the first time supposed to know that?  Then they reboot and their X server is broken or 3D acceleration is borked.

Updates are being pushed out without any thought. Was the latest kernel update even to fix a security issue?  If not, all this recent breakage has been for nothing, again.

As you can see, I feel very strongly about this and I haven't even had my system badly broken by these updates yet.  I just get upset when I see someone innocently updating their system, then having to post about it here when their system busts.

---

### Post by Brunellus on 2007-02-13
> **cookfromfrozen said:**
> What an arrogant statement.   Logical to who?  There is no notification whatsoever after the updates install that you will need to reinstall your graphics driver.  How is the typical user who has just installed Linux for the first time supposed to know that?  Then they reboot and their X server is broken or 3D acceleration is borked.

Updates are being pushed out without any thought. Was the latest kernel update even to fix a security issue?  If not, all this recent breakage has been for nothing, again.

As you can see, I feel very strongly about this and I haven't even had my system badly broken by these updates yet.  I just get upset when I see someone innocently updating their system, then having to post about it here when their system busts.
the only kernel modules Ubuntu is obliged to maintain are the ones in the core distribution, installable via the nvidia-glx package.  

Anything else, you're on your own.  If it breaks, you get to keep both pieces.

---

### Post by neighborlee on 2007-02-13
> **macogw said:**
> Windows doesn't put whole new kernels in its updates, now does it?

I have no idea..I just know i've never seen windows updates break my system like poor unsuspecting ubuntu users as of late..maybe that is what separates paid from oss SHRUG

cheers
nl

---

### Post by neighborlee on 2007-02-13
> **Brunellus said:**
> the only kernel modules Ubuntu is obliged to maintain are the ones in the core distribution, installable via the nvidia-glx package.  

Anything else, you're on your own.  If it breaks, you get to keep both pieces.

..ic,if it breaks you get to keep both pieces..I wonder, do you speak for ubuntu making wide sweeping statements of such ilk, when people genuinely seem to be looking for answers to linux problems ?..;)

cheers
nl

---

### Post by Brunellus on 2007-02-13
> **neighborlee said:**
> ..ic,if it breaks you get to keep both pieces..I wonder, do you speak for ubuntu making wide sweeping statements of such ilk, when people genuinely seem to be looking for answers to linux problems ?..;)

cheers
nl
I'm sorry if that sounds gruff.  But that's that.  Things that are NOT in the ubuntu distribution are OUTSIDE of ubuntu's control, and they CANNOT be held liable for them.

If you wanted to run the fancy new nvidia drivers from Nvidia's own tarballs--well, more power to you.  Now you have Beryl and all the desktop bling you can possibly want.  But if a kernel update breaks compatibility--well, sorry.  Ubuntu devs tested and approved that update against modules in the distribution--not against some arbitrarily recent nvidia release.

---

### Post by neighborlee on 2007-02-13
> **cookfromfrozen said:**
> What an arrogant statement.   Logical to who?  There is no notification whatsoever after the updates install that you will need to reinstall your graphics driver.  How is the typical user who has just installed Linux for the first time supposed to know that?  Then they reboot and their X server is broken or 3D acceleration is borked.

Updates are being pushed out without any thought. Was the latest kernel update even to fix a security issue?  If not, all this recent breakage has been for nothing, again.

As you can see, I feel very strongly about this and I haven't even had my system badly broken by these updates yet.  I just get upset when I see someone innocently updating their system, then having to post about it here when their system busts.

true that is indeed a good point..some notification would indeed be helpful...for the first time in quite sometime I was unable to use nvidia drivers ( synaptic method,,and btw having to use CLI to enable them is imnsho ridiculous )  and had to resort to ctrl-alt-F1 > envy, which thankfully worked great albeit I admit to not liking that 'route' due to not being able to tell someone new to linux to try that..its fine for us geekoids, but some people are going to find nearest hard object and hurl at me for suggesting it <wink>

speaking of which what did the update fix kernel wize, if it was security releated thats great but maybe in future a warning could be given for usres or 3d accel. cards...I realize you dont have to do it, but it might go a long ways towards end user's view of ubuntu.

cheers
nl

---

### Post by fuscia on 2007-02-13
are the updates ok, today?

---

### Post by PriceChild on 2007-02-13
> **fuscia said:**
> are the updates ok, today?They've always been ok... just make sure you recompile any modules you've installed yourself.

---

### Post by HomerSimpson748 on 2007-02-13
I know I might catch some heck for this... but I usually wait a couple days to download and install updates... just so I don't wind up with a broken system.

---

### Post by spockrock on 2007-02-13
maybe I should ask in the repo section, but is there a repo the has updated LRM-2.6.17-11 with the nvidia 9746 driver?

I know I can use the nvidia installer from their site.....or envy, but I would prefer, to use a nvidia-glx package and lrm.  Now I am not complaining, but just wondering, if there is one yet.  Right now I am using tseliots repo and the lrm package for the new kernel is not available.

---

### Post by cookfromfrozen on 2007-02-13
> **PriceChild said:**
> They've always been ok... just make sure you recompile any modules you've installed yourself.
xorg-driver-fglrx is in the repos and is supposed to be handled by the updates.  Yet on my system the latest update to that package breaks 3D acceleration.  I've never compiled any drivers or used any kernel modules that don't come with stock Ubuntu.

"They've always been ok" is probably the viewpoint of the people managing the updates..if they imagine there isn't a problem, hopefully it will go away.

---

### Post by rev_b on 2007-02-13
> **HomerSimpson748 said:**
> I know I might catch some heck for this... but I usually wait a couple days to download and install updates... just so I don't wind up with a broken system.

... but if you're using 3rd party drivers, it will whenever you install a new kernel. So waiting isn't actually an option.

There's nothing wrong with ubuntu repos updates, it's just how these binary drivers work.

---

### Post by prizrak on 2007-02-13
I'm using Feisty and get updates pretty much every day (this is beta after all) and haven't had anything broken (other than Beryl a couple of times with Beryl's own updates) yet. Been using it since Herd2 came out (can't remember when that was). Perhaps the nVidia driver is screwing you up? Dapper still has the old one in the repos, the new one seems to have fixed certain issues (like Xorg 7.1 support).

---

### Post by FyreBrand on 2007-02-13
> **neighborlee said:**
> true that is indeed a good point..some notification would indeed be helpful...for the first time in quite sometime I was unable to use nvidia drivers ( synaptic method,,and btw having to use CLI to enable them is imnsho ridiculous )  and had to resort to ctrl-alt-F1 > envy, which thankfully worked great albeit I admit to not liking that 'route' due to not being able to tell someone new to linux to try that..its fine for us geekoids, but some people are going to find nearest hard object and hurl at me for suggesting it <wink>

speaking of which what did the update fix kernel wize, if it was security releated thats great but maybe in future a warning could be given for usres or 3d accel. cards...I realize you dont have to do it, but it might go a long ways towards end user's view of ubuntu.

cheers
nlThe first thing to consider is that just because an update is available doesn't mean that it needs to be installed immediately.  When I update the Windows or Linux boxes I prepare for it.  I backup my data and pay attention to what's being updated.  I also consider whether this is a necessary update or not.

It sounds like the nvidia driver install problem was on your end because nvidia-glx updated with the kernel update (using the nvidia driver in the repos) and the nvidia driver has been available.

Every guide I've seen that explains how to install binary drivers with 3d accel warns the user that they will need to reinstall the video driver on a kernel update.  Again this comes back to preparing for an update by understanding what is going to happen before getting click happy with the OK button.

99% of the software on the machines I maintain are installed from Ubuntu repositories.  I rarely have any trouble with updates.  Most of the time, if I have a problem, it's because I've tinkered with something and the breakage is my fault.

---

### Post by neighborlee on 2007-02-13
> **FyreBrand said:**
> The first thing to consider is that just because an update is available doesn't mean that it needs to be installed immediately.  When I update the Windows or Linux boxes I prepare for it.  I backup my data and pay attention to what's being updated.  I also consider whether this is a necessary update or not.

It sounds like the nvidia driver install problem was on your end because nvidia-glx updated with the kernel update (using the nvidia driver in the repos) and the nvidia driver has been available.

Every guide I've seen that explains how to install binary drivers with 3d accel warns the user that they will need to reinstall the video driver on a kernel update.  Again this comes back to preparing for an update by understanding what is going to happen before getting click happy with the OK button.

99% of the software on the machines I maintain are installed from Ubuntu repositories.  I rarely have any trouble with updates.  Most of the time, if I have a problem, it's because I've tinkered with something and the breakage is my fault.

heh well..except for the fact that this was a brand new install , and clearly was before the fix was released...I installed nvidia-glx,,ran sudo nvidia-glx-config enable as per the directions and rebooted and no x...and I had to fix xorg.conf to go from there..

cheers
nl

---

### Post by flyingbrass on 2007-02-13
> **FyreBrand said:**
> Every guide I've seen that explains how to install binary drivers with 3d accel warns the user that they will need to reinstall the video driver on a kernel update.

That depends.  If you're using Ubuntu's packages and have linux-restricted-modules-386 (or 686) installed (in Dapper -- not sure if it's named differently in Edgy), the package is supposed to pull in the most current restricted modules package.  Along with xorg-driver-fglrx or nvidia's driver, upgrading should never be a problem.  No extra user actions are necessary.  

Problems can arise when Ubuntu fails to upload the newest restricted modules at the same time as a new kernel.  Or they otherwise mess things up, as apparently happened in this recent update.  In my case, the restricted modules metapackage wouldn't have upgraded with a normal apt-get upgrade.  It and a few similar important packages required a dist-upgrade, and then still didn't set things up correctly. 

So, if you're using video drivers from Ubuntu's repo's, you should never have to take any extra steps when the kernel changes.  If you've installed from source, you'll have to reinstall every time.

---

### Post by macogw on 2007-02-13
flyingbrass, the updates are put on one server first and then depending on the speed of the other servers, they pull the updates to themselves, but if they are in heavy use at the time, they don't get the updates from the main servers as quickly, and it can be a while before all of the updated packages get to all of the mirrors even though they're all put on the central server at the same time.  thats why sometimes it says some packages are being held back or are broken--the mirror you're downloading from hasn't received all the info from the main server yet [according to people on the ubuntu+1 irc channel where i was wondering why the new kernel was being held back in my feisty updates]

hey prizrak, given that there's only 3 bugs listed on feisty, does that mean what we're running is actually seeming to be *more* stable than the stable releases?

---

### Post by Brunellus on 2007-02-13
> **macogw said:**
> flyingbrass, the updates are put on one server first and then depending on the speed of the other servers, they pull the updates to themselves, but if they are in heavy use at the time, they don't get the updates from the main servers as quickly, and it can be a while before all of the updated packages get to all of the mirrors even though they're all put on the central server at the same time.  thats why sometimes it says some packages are being held back or are broken--the mirror you're downloading from hasn't received all the info from the main server yet [according to people on the ubuntu+1 irc channel where i was wondering why the new kernel was being held back in my feisty updates]

hey prizrak, given that there's only 3 bugs listed on feisty, does that mean what we're running is actually seeming to be *more* stable than the stable releases?
no, the feisty bug listing may have something more to do with the fact that nobody's gotten around to posting any yet?

---

### Post by flyingbrass on 2007-02-13
> flyingbrass, the updates are put on one server first and then depending on the speed of the other servers, they pull the updates to themselves, but if they are in heavy use at the time, they don't get the updates from the main servers as quickly, and it can be a while before all of the updated packages get to all of the mirrors even though they're all put on the central server at the same time.
True, but in the past restricted modules have at times been delayed far longer than propagation alone can explain.

That wasn't why my packages were being held.  I update manually, and this was done days after the updates were released.  Further, when I saw a plain upgrade was going to leave packages behind, I instead did a dist-upgrade, which got everything.  I don't know how the graphical updater thing works.  Perhaps it does the equivalent of a dist-upgrade.  Doesn't really matter, as there are reports of both methods failing to work properly.

Ubuntu really needs to do something about this.  They break X far too frequently.  Before any hot-headed fans start shouting that it's all due to proprietary drivers, read my previous post again.  If users install ATI or Nvidia drivers using the versions in Ubuntu's repo's and with the restricted modules metapackage, updates should never screw the drivers.  The only exception is, as you indicate, a short delay while everything propagates.  That possible delay is one of the reasons why I prefer to update manually, only hitting "y" after making sure nothing important will get left behind.

I'm concerned that new users don't understand the difference between Ubuntu's versions of the drivers and drivers installed from source.  Some wrongly blame Ubuntu when Ubuntu isn't at fault, and others fail to blame Ubuntu when Ubuntu is responsible.  

I notice in reading the recent problems that Envy is often being recommended as a "fix."  However, I doubt many newbies realize that they'll have to use Envy or the driver company's installer every time after a kernel change from then on.  They may incorrectly blame Ubuntu next time the kernel changes.

---

### Post by ndefontenay on 2007-02-13
I've updated my OS this week end and lost X.
I didn't know how to fix it so I re installed the whole thing.
I asked on how to fix it on the forum afterwards.
I've updated it again 2 days ago but performed a reboot only today (My friend wanted to see something on windows YIIIIIIK).
When I came back on Linux it failed.
I used the command line I've learned by heart to be sure I could fix it: dpkg-reconfigure xserver-xorg

I got so complexe questions I had to answer, that I have not been able to get it to work with this. (It really requires a good preparation first)

I finally restored my very first xorg.conf the one before I started playing with dpkg-reconfigure.

I rebooted Xserver (ctrl+alt+backspace) and it worked.
My mouse was freezed. I just unplugged it and plugged it again.

Everything is working fine.

To make a long story short, apparently a reboot of Xserver should solve the problem after an update.

If not, run dpkg-reconfigure, fail it. Then restore your original xorg.conf and reboot Xserver (This looks like voodoo to me though. Solution1 should work)

---

### Post by macogw on 2007-02-13
> **Brunellus said:**
> no, the feisty bug listing may have something more to do with the fact that nobody's gotten around to posting any yet?

i reported 3 bugs on it.  Two were fixed within a day.  One is still remaining.  The Tomboy applet is hanging up the gnome panels (so I removed the applet).  The other two bugs were the updater and running dbus stuff.  Everything else works fine though.  Even Beryl works fine!  It kept core dumping on Edgy.  Feisty is actually being very well-behaved for me.  Herd 4's about to come out, and given how often I've been getting updates (127 last night, at least 20 each of the last few days), they've got to be fixing some stuff up.  I don't know why, but it's being pretty stable.

Tilda and Beryl are not playing nicely though :(

---

### Post by Johnathon on 2007-02-14
We've had mutliple problems. At the moment, I'm booting with the old Kernal, and am quite close to just removing the new one. Mainly, because I'm using the nvidia driver in restricted-modules, and restricted-modules seem not to be updated. 

I can't really run dpkg-reconfigure on it, because I'm using a custom dual-monitor setup, and don't really want to lose all of my settings.

My box has now been broken twice by ubuntu updates, nothing to do with other drivers, or repositories not updating themselves quickly enough, pure Official Repo errors.

---

### Post by Samu on 2007-02-14
Hi,

I am not using nvidia and my X seem broken too. I use Kubuntu 6.06 and Radeon X300. After the last updates (several days without restarting the computer) it fails to run KDE. I have automatic login and now it gets stuck into the login screen. I have tried to run it with the old kernel without success. But I don't know really the reason of the failure. Any idea where the problem could be? Any idea of how to fix it without Internet access? Anyone with the same problem? I don't remember having installed critical drivers or modules from outside the official repositories.

Thx

---

### Post by flyingbrass on 2007-02-14
In Dapper I got fglrx working again by reinstalling linux-restricted-modules-2.6.15-28-686 (I'm using the 686 kernel) and xorg-driver-fglrx.

---

### Post by Samu on 2007-02-14
> **Samu said:**
> But I don't know really the reason of the failure. Any idea where the problem could be? 

I run a dpkg-reconfigure for the xorg server just to find that it was quite similar to the old one I had, but I started X anywa to try it, being root, and logged me smoothly into kde. But after restarting the computer it got again stuck into the login screen with the normal user. But again, logging into console, from there sudo -i and startx allows me to start kde as root. Again, I cannot figure the reason. For me all of this is just weird. I hope it is a clue for someone more experienced willing to give me a hand. The good thing is that now I am able to connect to the Internet from my own computer and can download upgrades/downgrades easily.

I tried to install (not reinstall) the fglrx to see if something different would happen, but nothing. I am still stuck into the described behaviour. Then, I think, I have X and KDE able to run, but anywhere in the way for the normal user to login something is screwed up. And, again, I cannot figure what. Any hint? Something to try out?

Thx

---

### Post by mistypotato on 2007-02-14
> **mistypotato said:**
> 
I'll post the results after I Mondo and then install the updates.
MP

[SIZE="3"]Well I backed up with Mondo then did the updates.....sorry folks....smooth as silk.   No errors, no problems.  

Not sure why many are having trouble :confused:

I'm pretty much a Linux dummy...I just do what people say works...and usually it does.

I have an nVidia card and used Automatix to install drivers for it.  I've installed a bunch of stuff (even stuff I probably shouldn't) so my Linux install is now this big fat overloaded goat...but it still hums along merrily...no complaints....I really like it :KS 

Hey I know what it is.... I do a complete MONDO backup before I update my system.  Next time I won't backup my system first and I'll guarantee the update will toast my install :) 

Kidding aside.... I'm VERY impressed with ubuntu.   it's been the best Linux install ever (I tried Red Hat once) and has totally restored my faith in Linux .  I can only imagine the fun I'll have with it as I learn how to really work with the Unix underpinnings.   VERY happy camper.

[/SIZE]

---

### Post by justin whitaker on 2007-02-14
I think envy is pretty rocking, and should be made an official package.

---

