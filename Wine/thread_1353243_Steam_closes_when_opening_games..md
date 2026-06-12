---
title: "Steam closes when opening games."
date: 2009-12-12
forum: Wine
---

### Post by Chuckler3 on 2009-12-12
I've just got my nvidia driver working properly after trouble shooting an error i kept getting while trying to play left 4 dead (failed to lock vertex buffer in CMeshDX8::LockVertexBuffer) that would kick me out of the game just after the intro movie. 

Now after opening steam and trying to open left 4 dead, it just closes steam and doesn't open left 4 dead. 

anyone run into this before or have a clue what's happening?

---

### Post by Chuckler3 on 2009-12-12
anyone?

---

### Post by Chuckler3 on 2009-12-12
bump for wisdom.

---

### Post by Sindwiller on 2009-12-12
I think that

a) you normally won't recieve an answer within 2 hours, hency why triple posting is unnecessary.

b) this thread belongs into the Wine support forum :)

---

### Post by Chuckler3 on 2009-12-12
my apologies.. everything went wrong today and i'm a little peeved.. i bought left 4 dead and it closes steam. i bought counter-strike source and it won't finish downloading. and now my screensaver isn't coming on.

just tryin to make sure i didn't just blow 35 bucks on games that don't work.

Mods: please move this if it needs to be.

---

### Post by -=hazard=- on 2009-12-12
> **Chuckler3 said:**
> my apologies.. everything went wrong today and i'm a little peeved.. i bought left 4 dead and it closes steam. i bought counter-strike source and it won't finish downloading. and now my screensaver isn't coming on.

just tryin to make sure i didn't just blow 35 bucks on games that don't work.

Mods: please move this if it needs to be.

I guess you are trying to play this games with Wine. Did you check the compatibility of this games with Wine? And even if they are compatible, did you check if there were any unexplained bugs or any problem with this games with some specific hardwares? Playing games with wine is not always as easy as it seams. I'm a fan of some different games that I cant play without wine, and even if I use wine there are some bugs that makes you just forget the game.
If you don't know, there are some nice games 100% compatible with linux, one of them is [Urban Terror]("www.urbanterror.net"), a first person shooting game, equivalent of Counter Strike.

---

### Post by Chuckler3 on 2009-12-12
i'll look into that urban terror.. actually trying to download it now. everything i could find on those two games indicated that they could be played on ubuntu. i mean, the intro movie and menu worked perfectly find in left 4 dead. something changed when i updated my graphics driver..i'm going to continue to play around with the free stuff until i can figure these problems out.. searching for the answers is proving to be rather difficult.

---

### Post by -=hazard=- on 2009-12-12
Are you trying to play on internet or singel player mode?

---

### Post by Chuckler3 on 2009-12-12
both. i'd hope that for $30 bucks it'd allow me to play online.

---

### Post by Chuckler3 on 2009-12-12
the list of other games that don't load is getting longer. I'm not sure what's going on. Urban Terror doesn't open, neither does some other pre-loaded games. left 4 dead still closes steam completely when i try to load it.

---

### Post by -=hazard=- on 2009-12-12
I think you cant from wine. Take a look on the game compatibility [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592&iTestingId=45107"). There are some optimizations explained too and user comments where might be you can find where your problem persist.

---

### Post by Chuckler3 on 2009-12-13
bump for knowledge.

---

### Post by beastrace91 on 2009-12-13
Haha bump happy much? I was out last night or else I would have posted sooner I promise ;)

What Wine version are you using and what nVidia driver version along with what gfx card?

On L4D do you get to see the menu @ all or does it dump right after the video? I personally use both these games just fine under Wine (along with many others) so hopefully we should be able to get you up and fragging soon :)

~Jeff

---

### Post by Chuckler3 on 2009-12-13
> **beastrace91 said:**
> Haha bump happy much? I was out last night or else I would have posted sooner I promise ;)

What Wine version are you using and what nVidia driver version along with what gfx card?

On L4D do you get to see the menu @ all or does it dump right after the video? I personally use both these games just fine under Wine (along with many others) so hopefully we should be able to get you up and fragging soon :)

~Jeff

nervousness has put me in a bit of a frenzy to get this running properly. thanks for the reply.

wine 1.1.34
NVIDIA-Linux-x86_64-190.42-pkg2
9800GT EE

At first, before i updated the driver, i would get into the intro video, got to the menu, upped the video settings. rebooted the game just fine.
i tried to skip the intro video and it kicked me out and gave me this error "failed to lock vertex buffer in CMeshDX8::LockVertexBuffer.

thats when i updated the video card driver to the one mentioned above. 

now when i open left 4 dead, it closes steam and acts as if i never tried to open the game.

and yes, i hope to be up and killing zombies soon.

---

### Post by beastrace91 on 2009-12-13
What did you change your video settings to (try defaulting these back if you can - so the game loads again)?

Also try setting the following registry keys: **useGLSL -> disabled** and **OffscreenRederingMode -> fbo** (If your unsure how to do this check [here](http://wiki.winehq.org/UsefulRegistryKeys))

Regards,
~Jeff

---

### Post by beastrace91 on 2009-12-13
Also after reading the L4D [AppDB entry](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592) I'm seeing all the successful listings are on Wine versions 1.1.32 and lower, maybe try turning back your Wine version some and then giving it a try (or check the link in my sig for setting up multiple Wine installs)

Regards,
~Jeff

---

### Post by Chuckler3 on 2009-12-13
i can't even open the game at this point.

Those aren't currently options in my registry when i open them and i haven't become that comfortable with this os to start adding things without checking. any way i can get an example of how to add either of those keys. the link you provided, while informative, is slightly confusing. 
i'm pretty much at the beginning. 

right click wine once i'm through hkey_current user..., software, wine.  
then add key.

---

### Post by beastrace91 on 2009-12-13
If the key you see referenced does not already exist you can add it (just make sure you use the proper key/sub-key listings given in my above link)

As for creating keys - its the same process as using the standard Windows registry editor.

Regards,
~Jeff

---

### Post by Twitch6000 on 2009-12-13
You said urban Terror isn't opening aswell this leads me to believe the problem is when you updated your nvidia driver.

I would suggest going back to the driver you were using before.

This should fix your problem.

---

### Post by beastrace91 on 2009-12-13
> **Twitch6000 said:**
> You said urban Terror isn't opening aswell this leads me to believe the problem is when you updated your nvidia driver.

Ahh I missed that bit the first time - yes please confirm that your video drivers are working properly with a native Linux game please. If it does not work then you indeed need to roll back your drivers. (or try a different version of the 190.xx that may or may not work)

Regards,
~Jeff

---

### Post by Chuckler3 on 2009-12-13
other games are opening just fine acctually.. i'm trying to find the information i used to install the last driver as i can't quite remember the entire step process. i've only got the last few inputs for terminal.

---

### Post by Ghost|BTFH on 2009-12-13
Here's some quick suggestions from someone who does have Left4Dead working just fine on WINE:

PLAN A:
1) SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS

Install the proper nVidia driver.  The "latest and greatest" doesn't always work "the best" in Linux.  I'm running version 185 and it's running smooth as silk.

2) REBOOT.

Try to play the game.  If it is still acting up, close the game and steam, try renaming your ~/(whatever)/Left 4 Dead/bin/vidcfg.bin to something else like vidcfg.binold and restart Steam and see if that fixes it.  There are some people who have an error happen over that file and removing it solves the problem.  If it does, just delete it before you play.

If it fails, go to plan B.

PLAN B:
1) Uninstall Left4Dead

2) Reinstall it.

3) Try to play it.

If you get an error as before, look up the exact error and see what is most likely causing it.  If I recall correctly, there is something inside the game's options you may want to change to make it run more smoothly and to prevent crashes.

If this option fails, try plan C.

PLAN C:

1) Uninstall Steam.

2) Reinstall Steam.

3) Install L4D.

I seriously doubt you'll need to hit this level.  At this point, my best educated guess is that your video card driver is 90% of the issue.

Fix it by going with what the repos have available and quit trying to tinker with drivers before looking at other options. :)

If all else fails...

[winehq.org]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592&iTestingId=45816")

Go there, read it, learn it.

Cheers,
Ghost

---

### Post by beastrace91 on 2009-12-13
> **Ghost|BTFH said:**
> Here's some quick suggestions from someone who does have Left4Dead working just fine on WINE:

I've got L4D running just fine (Along with a PILE of other games...). 

Just as a heads up the 190.42 drivers are not the "latest and greatest" they are the latest *stable* drivers however and should work just fine (And provide better performance than the 185 drviers in the repos - Ubuntu is almost ALWAYS versions behind because they don't like to update packages)

He hasn't changed anything beyond some settings... so at worst all you have to do is default your settings - not waste all your time redownloading/installing the whole game. Just right-click on your L4D in your "my games" list and select "properties" and then have it "verify game data" to make sure all the proper files are there to run the game.

Also if you actually read the WineHq.org DB entry you linked to L4D there is nothing listed there that describes an issue like he is having with a fix... So thats not really helpful in the slightest.

Lastly - just as a double check be sure you have disabled the "steam in game community" in your Steam friends settings as this causes crashes in Wine.

Regards,
~Jeff

---

### Post by Ghost|BTFH on 2009-12-13
> **beastrace91 said:**
> He hasn't changed anything beyond some settings... so at worst all you have to do is default your settings - not waste all your time redownloading/installing the whole game. Just right-click on your L4D in your "my games" list and select "properties" and then have it "verify game data" to make sure all the proper files are there to run the game.

That's just super Jeffery.  Thanks for that information.  Could you, since you have loads of games working on there, along with Left 4 Dead, explain how he can reconfigure his settings without being able to run the game?  I'm just curious, did Steam add this feature somewhere that I'm not aware of?

He also changed the drivers...did you miss that?  That's a bit more than just "some settings."  Hmmm....could be his drivers that are the issue.

And yes, I did actually read the whole thing from winehq I posted, and as a beta tester for games, I tend to try to give people all options, just in case.  I've found that if you have one issue, sometimes other issues will arise after you've fixed it.  Other times, it's just a good idea to know what sort of issue OTHER people have had and be prepared for them.  Lastly, I felt that perhaps if he's new to gaming on WINE, he might want a very useful resource that can give him a vast amount of information (usually) very quickly.

The most logical of all issues would be his drivers, and sticking with 185 should work just fine.  I really don't think he's going to notice such amazing performance difference between 185 and 190 for him to break with the repository just to get that one level up.

But I'm sure that if he just go in and fiddle around with his game's settings, as you suggest, that he'll be just fine. </sarcasm>

Cheers,
Ghost

---

### Post by beastrace91 on 2009-12-13
> **Ghost|BTFH said:**
> Could you, since you have loads of games working on there, along with Left 4 Dead, explain how he can reconfigure his settings without being able to run the game?  I'm just curious, did Steam add this feature somewhere that I'm not aware of?

He also changed the drivers...did you miss that?  That's a bit more than just "some settings."  Hmmm....could be his drivers that are the issue.

Adjust in game settings outside of game -> **C:\Program Files\Steam\steamapps\common\left 4 dead\left4dead\cfg\autoexec.cfg** Editing this file lets you adjust any in game settings. Also adding a **-dxlevel XX** argument to the launch options of a game should default any graphics settings that may have changed.

Also if his other 3D games are working fine I'm inclined to believe the current gfx drivers are working just fine, but if he wants to try rolling them back thats fine - I was just suggesting sticking with something newer (like 190.37 for instance) instead of going all the way back to the 185 drivers in the repos

Not quite sure where the hostility/sarcasm came from there but alrighty >.<

Cheers,
~Jeff

---

### Post by Ghost|BTFH on 2009-12-13
> **beastrace91 said:**
> Not quite sure where the hostility/sarcasm came from there but alrighty >.<

Cheers,
~Jeff

It's been a long night and I'm working on about six projects at the same time.  At least you posted something I didn't know - how to edit the settings.  I presumed there had to be something in there that would tweak it, but I really had no clue where it was in L4D (Since it's worked for me right out of the box).

I'd disagree about the driver most likely not being the issue just because other games work fine - I've had oddball stuff like this happen many times - it's one of the reasons I stick with the repository drivers - one solid base to start off everything else with.

Sorry about the hostility, I'm just tired.  If you can get him back to a stable game, good deal.  I'm going to finish up my projects and lay off the caffeine so I don't bite anyone else's head off.

Cheers,
Ghost

---

### Post by Chuckler3 on 2009-12-14
thanks for all of the information. i actually went in and looked at the hardware driver installed for my graphics card and it says 185.. i was under the impression that the file i loaded in previously was for 190 though. confused.. obviously i know how to apply the driver in the gui, but the one i downloaded from the terminal i don't believe i have running right now. how do i "apply" it?

screensaver isn't working either at this point.

judging by the fact that the only screensavers that work are the 2D ones, i'm curious what trouble shooting a lacking 3D driver is like

the current driver it's saying is 185.18.36

---

### Post by beastrace91 on 2009-12-14
Do other 3D games run that are native to Linux? (Urban Terror is a good one to try for this). If not then indeed your drivers are not working properly. To install the 190.42 drivers you downloaded from the nVidia site you want to remove the current ones you have from hardware drivers and then follow the instructions listed [here](https://help.ubuntu.com/community/NvidiaManual) for installing the new ones.

Regards,
~Jeff

---

### Post by -=hazard=- on 2009-12-14
It's not possible that the latest repository drivers aren't working properly and the nVidia latest release would. Maybe he just need to reinstall the repositories one (after making a good clean).

---

### Post by Chuckler3 on 2009-12-25
> **beastrace91 said:**
> Do other 3D games run that are native to Linux? (Urban Terror is a good one to try for this). If not then indeed your drivers are not working properly. To install the 190.42 drivers you downloaded from the nVidia site you want to remove the current ones you have from hardware drivers and then follow the instructions listed [here]("https://help.ubuntu.com/community/NvidiaManual") for installing the new ones.

Regards,
~Jeff

the instructions found through that link are impossible to follow. here is why.

the first step is to backup the xorg file.. i keep getting error messages.

"sudo apt-get install build-essential linux-headers-`uname -r`" - this comes up with an error.
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
E: Couldn't find package linux-headers-uname -r"

When i open this in the editor to "disable it" i get nothing in the window that opens.
"gksudo gedit /etc/default/linux-restricted-modules-common"

I haven't found a way to input this in order to load the driver without it cutting the order in half.
"cd /path/to/installer
sudo chmod +x NVIDIA*"

Before i attempted all of this. i used the driver install tool to uninstall and reinstall the current 185 driver and i still can't open 3D games, screensavers, and left 4 dead still closes steam.

sorry it took so long to get around to posting this up, but it's been hectic. 

thanks for your time.

---

### Post by Chuckler3 on 2009-12-26
just keeping it alive.

---

### Post by Chuckler3 on 2009-12-27
bump

---

### Post by Chuckler3 on 2009-12-28
double bump.

---

### Post by Chuckler3 on 2009-12-29
daily bump.

still trying to figure this out.

as if this wasn't bad enough, i still haven't figured out how to get my ipod to show up as anything other than a camera on my new desktop. doesn't show up in rhythmbox gtkpod manager or exaile.

---

### Post by Chuckler3 on 2009-12-30
ttt

---

### Post by Chuckler3 on 2010-01-01
bump

---

### Post by Chuckler3 on 2010-01-02
help

---

