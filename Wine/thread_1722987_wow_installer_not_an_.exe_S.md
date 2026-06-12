---
title: "wow installer not an .exe? :S"
date: 2011-04-06
forum: Wine
---

### Post by key! on 2011-04-06
I downloaded the game client for World of Warcraft and after attempting to open it with Wine I got this

The file '/home/kevin/Downloads/WoW-4.0.0-WOW-enGB-Installer.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Obviously I downloaded it from battle.net so it's obviously the right thing?

I have the disk for the last expansion... I tried installing it last night (it worked I got all the way through it and while downloading the patch data I launched it and it would play the opening cutscene then crash. I unilstalled it. I can't seem to install it from the disk again)

Halp meh! I only got ubuntu yesterday o.o should I just plain reinstall ubuntu?

---

### Post by PCNetSpec on 2011-04-06
```
chmod +x /path/to/file/filename.exe
```

Or, right click the .exe, select "Properties", select the "permissions" tab, put a tick in "Allow executing file as program"... "Close".

Now double-click the .exe

---

### Post by key! on 2011-04-06
Ok, I did that, but now Wine just is "starting" then closes, no window pops up or anything.

Just tried off the disk again and it's saying I don't have enough harddrive space, which is interesting since I have 80GB free.

GAH!

I'm downloading the wow trail off of wine tricks now, but I'm pretty sure it's not going to work since it's the US version (I'm EU, but I'm figuring, nothing else is working why not)

---

### Post by key! on 2011-04-06
Oh also, I'm using Ubuntu 10.10 & Wine 2.2

---

### Post by key! on 2011-04-06
One more thing, this came up after I checked the executable thing

 No installer data could be found. If this problem persists, please contact Blizzard Technical Support.

---

### Post by Dupointx on 2011-04-06
> **key! said:**
> I downloaded the game client for World of Warcraft and after attempting to open it with Wine I got this

The file '/home/kevin/Downloads/WoW-4.0.0-WOW-enGB-Installer.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Obviously I downloaded it from battle.net so it's obviously the right thing?

I have the disk for the last expansion... I tried installing it last night (it worked I got all the way through it and while downloading the patch data I launched it and it would play the opening cutscene then crash. I unilstalled it. I can't seem to install it from the disk again)

Halp meh! I only got ubuntu yesterday o.o should I just plain reinstall ubuntu?

First, there's nothing wrong with Ubuntu.

Second, you're going to have to work to get WoW to run. I wish WINE was a cake walk, but it's going to take a lot of trial and error.

The best resource is the [WoW page on winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549"). There's plenty of help on that page to get WoW running, but it will be challenging. You may even have to use the terminal to get things working right.

I had a friend who is a little bit more advanced than me help me install WoW last fall, and we ended up having to un-hide the contents of the Wrath DvD just to start the install. Then after taking all day to install, I couldn't get it to recognize my mouse. so I was just sitting there at the screen to log-in with no way to do anything. I just gave up at that point, I knew that it was going to be more trouble than it was worth. Plus I dual-boot, so Windows right there, ready to play WoW.

The last time I got WoW working on Linux it took a lot of tweaking with WINE config. Even the stuff that wouldn't matter made a difference. Sound, user permissions, just about everything.

As far as using the download install application thing. It's not going to work. It just doesn't for some reason. Need to use the DvD.

---

### Post by key! on 2011-04-06
Really, really random.
I came off my computer for a while, the CPU was getting a little hot, and I just came back on and the WoW icon was on the desktop. I double click and it's downloading as if nothing happened. It's downloading from the start (I think I mentioned I uninstalled it in the first post so that's nothing strange really).

Thanks for your reassuring words! I'm gonna leave this to down the whole thing before I try anything again.

---

### Post by cwwilson721 on 2011-04-06
It will take awhile...

12+GB for first download, then a patch or two...

But, to help out:
[LIST]
[*]Disable Compiz. I use the Compiz Fusion Icon.
[*]Use the latest proprietary drivers for you card/chip.
[*]Append '-opengl' to the end of the launch command (This will also have WoW write the correct 'SET GFXApi' setting in config.wtf).
[*]If you do get it running, run on lowest settings first, then tweak individual sliders a bit at a time until you get a good balance between 'eyecandy' and FPS
[*]Update your wine install to v1.3. Just Google "wine 1.3 PPA" to find instructions, if needed
[*]If you have a older Ati/AMD card/chip, you may not be able to play. The open source 3D drivers you are forced to use are not up to the task yet yet. They are a TREMENDOUS effort, but just aren't quite 'there' yet.
[*]If you have a non-Sandy Bridge Intel video chip, the odds of it working at all are slim to none, and if you DO get it to run, the experience will be horrendous. If you do have Sandy Bridge, let us know how it works. OpenGL is supposed to rock on these new Intel processors.
[*]If you end up with stuttery video when playing, try disabling sound. That sounds odd, but there was, at one time, issues with certain sound cards/chips and odd WoW video behavior. 
[/LIST]

Just a short list.

---

### Post by mendhak on 2011-04-08
I don't know if you've seen this yet, but there's also a pretty good guide on getting WoW on Ubuntu here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Dlambert on 2011-04-08
Try [playonlinux]("http://www.playonlinux.com/en")

---

