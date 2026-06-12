---
title: "Wine update seems to have caused all Windows applications to stop working."
date: 2009-01-04
forum: Wine
---

### Post by kaldor on 2009-01-04
Up until a Wine update today, I was playing Quake II, Quake III, Jedi Outcast, and other stuff perfectly. I updated Wine earlier today, and ever since, no program will run in Wine. How can I fix this? 

Update: In fact, Wine is not working at all. I tried to open configure Wine, and nothing happened. What is going on?

---

### Post by hikaricore on 2009-01-04
You should first try and downgrade to the version you were previously using by downloading the version before the one you updated to from the winehq website.

See if that resolves the issue.

Also, you are aware that every release of Quake has a native Linux client right?
There's no need to run them under WINE unless you're having troubles with the native version.

---

### Post by kaldor on 2009-01-04
I am aware of the Linux versions, but for whatever reason, they would never run properly so I used Wine.

Also, how do I downgrade without removing? I did not use the winehq site, I used the Update manager because it found the update. I tried to use Force Version, but the previous versions are not listed; only the latest. What to do now?

---

### Post by kaldor on 2009-01-04
Still need to fix this, can anyone help?

---

### Post by kaldor on 2009-01-04
No one is available to help? :(

---

### Post by kaldor on 2009-01-04
Really in need of answers.. how can I downgrade Wine when the previous versions are not showing up in synaptic?

---

### Post by kaldor on 2009-01-04
Solved: I uninstalled Wine and got the previous version from winehq.

Warning to everyone who reads this: Wine 1.1.12 for Hardy Heron failed horribly on me, you are better off sticking with 1.1.10

---

### Post by Meow27 on 2009-01-04
one: DONT MULTI POST, ITS ANNOYING, JUST AS ANNOYING AS THE WAY IM TYPING RIGHT NOW!!!!!

second: why not wine 1.1.11? (are you using [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)  ?   i dont know... but i didnt have problems with the intrepid builds on hardy :/) im a very big 1.1.10 hater :P

---

### Post by jimjutte on 2009-01-04
Meow27, 

Can I take it that you are happy with 1.1.11? I have just installed .12 and it isn't doing anything for me, but this is the first time I'm trying Wine... so for all I know, it is just inexperience.

Cheers

---

### Post by Meow27 on 2009-01-04
in .10, the shortcuts are installed in the submenu, "other>shortcut" instead of the submenu Wine> Orgrams >program folder>shortcut

thats the main reason :/

---

### Post by jimjutte on 2009-01-05
Thanks. It doesn't really mean anything to me yet. I've just installed .11 and haven't use Wine yet. I'm hopeful however that this will function smoothly... time will tell ;)

Quick question... can you explain why Wine doesn't see all the folders on the C drive... even when they should not (in theory) be hidden?

---

### Post by jrusso2 on 2009-01-05
WINE is so poor, Windows 2000 is platinum trying to get word and excel to work is bad though.

Can't get the registration to even stick.

---

### Post by hikaricore on 2009-01-05
Some of you, who will remain nameless... should stop threadjacking.

Very few replies have anything at all to do with the OP's issue.

---

### Post by jimjutte on 2009-01-05
If you mean me, that is not exactly true. NONE of the applications that I have tried yet with .12, are working. At least with .11 I seem to have gotten Wine to install itself properly. Now... to get it to work.

---

### Post by caithness on 2009-01-05
I was having the same problem as OP and was trying to manually install the old version and getting all kinds of problems. I hadn't seen the page that was linked to, and using that I fixed it very fast, thanks for that link.

---

### Post by hikaricore on 2009-01-05
> wine: Call from 0x7b8456d0 to unimplemented function ntoskrnl.exe.KeInitializeSemaphore, aborting
wine: Unimplemented function ntoskrnl.exe.KeInitializeSemaphore called at address 0x7b8456d0 (thread 0024), starting debugger...
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart.

This does seem to be a bug in 1.1.12 package for Intrepid possibly others.

Downgrading to the [1.1.11]("http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.11~winehq0~ubuntu~8.10-0ubuntu1_i386.deb") fixed this for me.
Strangely enough my flatmate's system has no trouble with the 1.1.12 package...  I'm wondering if this could relate to something left behind by an old version?

---

### Post by david_kt on 2009-01-06
> **hikaricore said:**
> This does seem to be a bug in 1.1.12 package for Intrepid possibly others.

Downgrading to the [1.1.11]("http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.11~winehq0~ubuntu~8.10-0ubuntu1_i386.deb") fixed this for me.
Strangely enough my flatmate's system has no trouble with the 1.1.12 package...  I'm wondering if this could relate to something left behind by an old version?

Looks like this 2 threads need to be made sticky:
[http://ubuntuforums.org/showthread.php?t=944949](http://ubuntuforums.org/showthread.php?t=944949)
[http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)

so that nobody will face problem anymore when upgrading wine.

DK

---

### Post by mackilll on 2009-01-06
Up until now, all wine updates work for me.

But now it just f. everything UP, it crash all my programs.

They just lose there mind..!!???

But people come on !!!!:confused:

If  I have to go down to wine 1.1.11, This will delete the .wine folder completely...so all programs, settings, saved games, etc. in it will be gone

A lot of work ... VERY very inresponsable 

And don't bother use the testing as a iscuse, it was a big mistake of wine developers.

---

### Post by david_kt on 2009-01-07
> **mackilll said:**
> 
If  I have to go down to wine 1.1.11, This will delete the .wine folder completely...so all programs, settings, saved games, etc. in it will be gone

A lot of work ... VERY very inresponsable 


No, if you just uninstall wine 1.1.12 and install wine 1.1.11, all should still be there, nothing change.

If you still not sure, you could copy as backup all .wine directory content, EXCLUDE dosdevices directory. And if .wine directory disappear, you could copy from the backup.

DK

---

### Post by hikaricore on 2009-01-07
> **mackilll said:**
> 
A lot of work ... VERY very inresponsable 

And don't bother use the testing as a iscuse, it was a big mistake of wine developers.

I'm sure the people who work on the WINE project for free, including those who package it for you, are very very sorry to inconvenience you...

But all sarcasm and flames aside, if you want a stable build stick with the one in our repos.  By using the winehq releases you're essentially beta testing.

As david said above me, downgrading to 1.1.11 will not erase everything, if it does you're doing something terribly wrong.

---

