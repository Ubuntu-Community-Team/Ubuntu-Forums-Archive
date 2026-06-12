---
title: "WoW updating under WINE"
date: 2010-06-04
forum: Wine
---

### Post by Beastlicker on 2010-06-04
Hello. Over the course of the past week, I decided to freshly install Ubuntu 10.04 over my previous version. On the old version, WoW ran fine and normal under WINE. But, when I installed WINE on 10.04 and installed WoW, problems began to occur.

The game was downloaded and installed perfectly. That went fast and smoothly. But then, after I installed it, I go to launch and get this error:

"The program Launcher.exe has encountered a serious problem and needs to close," and then WINE goes to tell me it is either a deficiency with WINE or a problem with Launcher.exe.

I ran the Blizzard repair tool and It fixed about 26mb of files it looked like. After that, I was able to at least download the patch. When it goes to actually update to the patch that was downloaded, it either crashes, or the updater says that it is unable to update. 

Has anyone else ran into this problem?

---

### Post by pedro_orange on 2010-06-04
Try running WoW.exe, not the launcher. 

Also, when running things do it from the terminal 

```
wine 'path/to/program.exe'
```

And if there's a problem you will see it, rather than just a GUI error.

Hope this helps.

---

### Post by devildog3543 on 2010-06-04
I did have the problem of the patches crashing, what I ended up doing is just downloading the patches through a third party and putting them in thew .wine/wow directory, set their permissions to execute and just ran them from that directory and it seemed to work great.

Another thing with doing it that way is if you just run the launcher.exe not the wow.exe fro the directory with the patches in there wow wont try to download the patches because it will see they are already there and run them ! 

Hope that helps

---

### Post by Beastlicker on 2010-06-04
I am able to download the patch fine and everything. It all happens when the update begins to occur. In Terminal, I receive this error message.

```
err:ntdll:RtlpWaitForCriticalSection section 0x5d6598 "?" wait timed out in thread 0034, blocked by 008a, retrying (60 sec)

```

And it repeats itself every 60 seconds. I am very confused as to why this was happening. I even tried reinstalling Ubuntu just to see if it was an OS problem. It was not.

---

### Post by david.burlingame on 2010-06-05
I had a similar issue after reinstalling WoW due to the patching process.  After each patch you are prompted with a button that says "reset"

If you click that button the program launcher.exe starts.  This program changes the permissions on the World of Warcraft folder at ( ~/.wine/drive_c/Program Files/World of Warcraft) effectively preventing the user from view the files. 

The solution I used was in a terminal change directory to ~/.wine/drive_c/Program Files/
the run
$sudo chmod 750 "World of Warcraft"

I had to repeat this each time a patch successfully installed and I clicked the reset button.  After the 2nd patch I stopped clicking the reset button and just closed the program.  Then restarted the application with wine Wow.exe



Now I need to find out why the Wow UI no longer sees the in-game icons eventually leading to a crash and debug in wine.  I appears a few others are having a similar issue.

---

### Post by creatox on 2010-09-14
david!! that was excatly what i needed.  I've been running wow for all of 3 days now and just hit 1st update.  that fixed it right away.
heres the script i'm using from now on


killall WoW.exe
killall Launcher.exe 
sudo chmod 750 ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft

---

