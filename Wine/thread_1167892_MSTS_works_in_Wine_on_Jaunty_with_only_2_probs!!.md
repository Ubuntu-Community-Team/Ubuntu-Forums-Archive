---
title: "MSTS works in Wine on Jaunty with only 2 probs!!"
date: 2009-05-23
forum: Wine
---

### Post by b@sh_n3rd on 2009-05-23
Hi, Today I successively installed MSTS a.k.a Microsoft Train Simulator, on Wine. I installed it using PlayOnLinux 3.5. My wine version is, 1.0.1

Train  Simulator worked perfect I can say but with ONLY *two* problems...wow? so little? I'm amazed...Well, first of all, MSTS works on Full Screen, BUT, when I exit, it causes X to crash, so I use it in windowed mode, (Wine emulated desktop). I was able to drive an Acela Express in North East Corridor on a test run...very smooth...I think better than XP too.

However, here are the probs...When loading, I get a white screen...that is upon starting the sim and loading an activity...nothing serious. Everything on the main menu works normal...The two difficult probs are;

1. The cab in the locomotive doesn't show the track properly as it's supposed to
2. The 3D graphics are missing textures

That's about it...I'll post screenshots later on, I wanted to reinstall Wine, so I've gotta reinstall MSTS as well...I think the texture problem has to do with DirectX? I was able to install 9 yesterday, but now it doesn't seem to get installed as it did...(I was idiot enough to remove the stupid thing...can kick myself for that...how can I nuke wine off? that might help coz it's not working as well as it was anyway, like, the registry doesn't clear uninstalled programs)

PS: How do I "delete" the menu shortcuts under "Other" that get created upon installation? I hid em, but when I hit delete it doesn't get deleted...annoying...

---

### Post by cogadh on 2009-05-23
First off, don't install DirectX in Wine, it already has its own DirectX that is functional enough and if you install DX, it can break Wine. If a game requires a particular DirectX DLL, then you can copy that from Windows and override it in Wine, rather than risk breaking Wine with the full DirectX install.

If you want to "nuke" your Wine installation and start over, you just need to delete the /home/<yourusername>/.wine directory. That deletes everything you have installed and restores Wine to its default settings/configuration.

As for the shortcuts, you can only get rid of them using the menu editor, but don't delete them, since by doing that, they won't come back, even if you re-install the application. Instead, just uncheck them so that they are no longer shown, but you can get them back if you need them.

Lastly, since you seem to be focusing on getting games to work, you might want to consider moving up to the latest version of Wine. The 1.0.1 version is what is called the "stable" version, in that it does not recieve any major updates or changes in attempt to provide consistent performance for everyday use. However, since 1.0.1 was released, Wine has been significantly updated, especially in regards to gaming. The current version as of this past Friday is 1.1.22, but at the moment the most current Ubuntu package is 1.1.21. You can find out about getting the latest Wine here:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by b@sh_n3rd on 2009-05-23
Hi...I was doing a bit of research on the wine app db and even that states a newer version of wine...so I was just thinkin of installing the latest version...thanks for that link dude..i owe u one :D

---

### Post by b@sh_n3rd on 2009-05-24
Right, so I tried MSTS on Wine 1.1.22 and there's not much of a difference..Slight improvements and where ever the texture's missing is now black instead of white. I've got a couple of screenshots of MSTS.

The first two (#2 and #3)screenshots show the bugs on one trainset and what it should be like is shown by the last two. For example, the first one of a cab shows what it looks like on that loco. and the 3rd shows the cab on a different loco. as it should be like. Same for 2 and 4. The first one shows the Main Menu of MSTS.

---

### Post by longtom on 2010-05-05
Sorry for resurrecting...taking a chance here.

@b@sh_n3rd

have you ever succeeded in your quest.  I am a MSTS player myself, which is one of the very few reasons I still use XP.

I also use some peripheral programs to edit textures, load additional routes etc.

Maybe we can share some thoughts?

---

