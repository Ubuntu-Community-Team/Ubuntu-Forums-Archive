---
title: "Spore install help needed"
date: 2011-02-27
forum: Wine
---

### Post by DaSkinna on 2011-02-27
I've just upgraded to 10.04 LTS so far I've noticed a big difference.. anyway I've tried to install spore, it installed fine but upon launching the program it comes up with a dialog box saying "the program SporeApp.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience. this can be caused by a problem in the program or a deficiency in wine, you may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application" 
i have looked on this site and found nothing useful there, if there is anyone else who has had this problem could you help me in sorting it out cause its an awesome game, thanks

p.s. im fairly new to ubuntu so talk to me as if im a complete idiot and know nothing :L

---

### Post by cogadh on 2011-02-27
Are you running the game in the manner indicated on AppDB? The game will never work unless it is launched correctly.

---

### Post by DaSkinna on 2011-02-27
yes i have tried all things on the site and i still get the same message :/

---

### Post by cogadh on 2011-02-27
What is Wine's actual error output (the stuff output to the terminal)?

---

### Post by DaSkinna on 2011-02-27
im not sure if terminal is open, if it is then its not showing itsself, but the only thing that comes up is "the program SporeApp.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience. this can be caused by a problem in the program or a deficiency in wine, you may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application" and thats in a dialouge box simmilar in looks to a windows error prompt

---

### Post by cogadh on 2011-02-27
If the terminal is not open, then you are not running the game as described in the AppDB how to:

> The easiest way to play Spore without problems in Wine:

[LIST]
[*]Make sure youre using wine version 1.1.26 or greater.
[*]Start Spore using the -safe flag, e.g. 
```
wine Sporebin/Sporebin.exe -safe
```
[*]If you have problems: In the Settings menu, in Graphics, set the Lighting to the lowest possible quality. This is a useful workaround for almost all in-game crashes.
[*]Also: Turning off shadows allows paint mode to work properly. 
[*]Enjoy.
[/LIST]
If you experience problems:
[LIST]
[*]Make sure the current working directory you run this from is the SPORE folder, not the Sporebin folder - it'll spin forever looking for the data folder otherwise.
[*]If it hangs on start-up then try to rename DMCmdPortalClient.dll(also a problem on Windows):
```
mv Sporebin/DMCmdPortalClient.dll Sporebin/DMCmdPortalClient.dll.bak
```
[*]Make sure you're passing the -safe flag.
[*]If you are using PulseAudio: this is not officially supported by Wine, but some users have reported success using the ESD or OSS audio driver instead of the ALSA driver. This is configurable in winecfg. It is recommended that you do not use PulseAudio with Wine. [/LIST]
You need to do that first before we can even begin to figure out if you are really having an actual problem.

---

