---
title: "Grand Theft Auto"
date: 2009-05-20
forum: Wine
---

### Post by oh n0es on 2009-05-20
Just downloaded this game (legally) from the Rockstar [website]("http://www.rockstargames.com/classics/?id=1"). Installation went fine, but upon trying to run the game through Wine, I encountered the following error;
MGL Fatal Error!
Error 268.473
Cannot find a suitable display mode.

After a bit of searching, I believe that this is a problem with running the game under Wine, and not with my PC.

Does anybody know if this can be fixed?

EDIT: Well, I probably should have checked first, but the Wine AppDB has all versions listed as Garbage. Oh well, GTA 2 got a gold so I'll give that a try.

---

### Post by asdfoo on 2009-05-20
> **oh n0es said:**
> Just downloaded this game (legally) from the Rockstar [website]("http://www.rockstargames.com/classics/?id=1"). Installation went fine, but upon trying to run the game through Wine, I encountered the following error;
MGL Fatal Error!
Error 268.473
Cannot find a suitable display mode.

After a bit of searching, I believe that this is a problem with running the game under Wine, and not with my PC.

Does anybody know if this can be fixed?

EDIT: Well, I probably should have checked first, but the Wine AppDB has all versions listed as Garbage. Oh well, GTA 2 got a gold so I'll give that a try.

apps complaining about display modes usually means that your X server doesn't support the resolution the app is requesting, you can test this by enabling virtual desktop in winecfg so it runs windowed

---

### Post by oh n0es on 2009-05-21
I tried running it in Virtual Desktop, and received the same error.

And now trying to run GTA2, I receive this error: Videomode 16x16x16 is not available.

---

### Post by asdfoo on 2009-05-21
could be a display depth issue then, Wine can't change the display depth of the X server (X has to restart to pick a different depth), Wine tries to fake it, but if the app asks the right questions it can figure it out.

---

### Post by pastaluver on 2009-07-06
I know this is an old thread kinda.I am having the same problem....

Awhile ago I bought the classic GTA game from amazon. I installed it on my Windows computer and it worked fine.I could actually play it. Then I reformatted my computer and tried to install the game again. When I go to play it I get the follow:

MGL Fatal Error! 
Error 268.473 Cannot find a suitable display mode

Not sure why this would be happening considering it had worked previously before reformatting. I tried doing a google search for tips on how to fix but none were helpful. Any ideas on how to get it working again? Step by step instructions would be helpful.

---

### Post by RealG187 on 2009-07-07
> **pastaluver said:**
> I know this is an old thread kinda.I am having the same problem....

Awhile ago I bought the classic GTA game from amazon. I installed it on my Windows computer and it worked fine.I could actually play it. Then I reformatted my computer and tried to install the game again. When I go to play it I get the follow:

MGL Fatal Error! 
Error 268.473 Cannot find a suitable display mode

Not sure why this would be happening considering it had worked previously before reformatting. I tried doing a google search for tips on how to fix but none were helpful. Any ideas on how to get it working again? Step by step instructions would be helpful.
It probably doesn't work because you are using wine...

---

### Post by pastaluver on 2009-07-08
:(  How do I get wine off completely then?

---

### Post by RealG187 on 2009-07-08
> **pastaluver said:**
> :(  How do I get wine off completely then?You don't have to remove wine.

I am not sure if there is a way to make it run in Ubuntu without Wine. Wine will not run any Windows program and that sucks. It would be cool is Wine ran every Windows program without issue.

You can try installing Windows in a VM, but the game might not run because VMs don't have full graphics...

---

### Post by Max Uglee on 2009-07-08
Sometimes running things in compatibility mode for an earlier version of windows helps.  I have had to do it for a program or two but I can't think of which ones off of the top of my head.  I think GTA 1 came out around the windows 98 era so I would try that and maybe win2k mode as well.  Also Virtualbox is a VM and it has (limited) hardware acceleration that you can enable.  It is in the repos.  Let me know if you decide to go that route and need some help.

---

### Post by RealG187 on 2009-07-08
I think you can download the proprietary one too, it might have more hardware acceleration...

---

