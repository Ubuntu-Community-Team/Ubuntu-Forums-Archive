---
title: "Tribes2 + Wine Howto"
date: 2009-01-15
forum: Wine
---

### Post by toasty_ghosty on 2009-01-15
Hello

This is my first how to so please bare with me. I recently found out that Tribes 2, a personal favorite of mine back in the day, has been further developed and is free! And to make it better, it runs great in Wine! Heres how I did it:

First download it from here:

[http://www.tribesnext.com/](http://www.tribesnext.com/)

I used the torrent. It has decent speeds as well as it downloads all the files you need.

Second, make sure that Wine is updated. I am using the most current version of Wine. Older versions may run it better, but this version seems to run it well. 

Next, I moved the full downloaded directory to my home directory and executed tribes2_gsi.exe within the new file.

> wine tribes2_gsi.exe

It copies the needed files and next asks you if you would like to install it. Of course, chose yes.

After that is completed, execute the other file titled TribesNext_rc1c.exe.

> wine TribesNext_rc1c.exe

This will install the new patch.

After that is done, it should place the new game within your wine directory. Play from there.

The only issues I have had so far is one small one. The sound seems choppy at points. This may however be due to my system and not the game as it happens with all games I play over wine (Steam, WoW, etc).

Thanks.

If there are any issues feel free to ask.

---

### Post by curvedinfinity on 2009-01-15
The training works for me, but the online locks at the Garage Games intro screen.

Anyone else having a similar issue?

---

### Post by toasty_ghosty on 2009-01-15
The training/Solo play works, but not the online play? I'll try this on my other machine to see if I can replicate the error...what is it doing?

---

### Post by blueshiftoverwatch on 2009-09-19
When I go to play Tribes 2 online the WINE desktop will come up, a few seconds later the Windows CLI will come up, and display the message "File Not Found" over and over for about five seconds before closing. After which WINE won't close without kill -9ing it.

Although when viewing the list of processes running Tribes 2 is on the list despite the fact that it never shows up.

Anyone know what's going on?

---

### Post by Zeppelin! on 2010-09-02
When I take a stab at playing it (this is my favourite shooter. . .) from the menu, I get a few moments of loading and then nothing, not even a window.

So I tried running it from terminal (it seems I have to select tribes2.exe from the game data section?) and I get the following error: err:ntdll:RtlpWaitForCriticalSection section 0x6823b1b8 "?" wait timed out in thread 0026, blocked by 0000, retrying (60 sec) 

Which, looking around, I have not been able to find anything directly helpful.

---

### Post by donkyhotay on 2010-09-02
Tribes2 on linux drives me nuts, I bought the windows version back before I migrated to linux so of course I only have the windows discs rather then the linux client. After I migrated to linux they released the windows version as a free download but not the linux client. I then wined tribes2 and was able to play flawlessly until about 4-5 years ago when the official master servers went down, I haven't been able to play online since then. The special patch that's been released to allow tribes2 to play on the new fan supported master servers doesn't work well with wine and I've never been able to get it going. Could still play the solo/lan version but it'd lock up when I tried online. Admittedly it's been over a year since I tried it, maybe they've gotten the bugs worked out. If someone ever gets tribes2 to be able to run on wine with online play let me know, I wouldn't mind getting back into it again.

---

### Post by WhatTheHell? on 2010-10-31
Downloaded, ran and installed tribes2_gsi.exe.  Tested game on solo and lan, and was able to play practically flawlessly.  Downloaded, and installed TribesNext_rc1c.exe.    Ran 'Tribes 2 Online' from Applications > Wine > Programs > Dynamix > Tribes 2.  Wine window opened up but did nothing.  Any ideas?

---

