---
title: "Starcraft Patching Probs [Wine]"
date: 2006-03-28
forum: Wine
---

### Post by gaberade on 2006-03-28
Hoooo kay. I'm having some difficulties here. I've got starcraft and broodwars up and running. Smoothly at that. Problems I'm having is connecting to Battlenet and patching. When I do so the screen goes blank and I only see the text saying "Searching for fastest Battle.net Server" and "Cancel" Then I get a long readout in my console and wine shuts down.

The read out is:
wine: Unhandled page fault on write access to 0x7d4dc000 at address 0x7e510480 (thread 0014), starting debugger...
WineDbg starting on pid 0x13
Unhandled exception: page fault on write access to 0x7d4dc000 in 32-bit code (0x7e510480).

Register Dump [bunches of text]
Stack Dump [bunches of text]
Backtrace [bunches of text]
Modules [bunches of text]

Threads:
process  tid      prio (all id:s are in hex)
00000013 (D) C:\Program Files\Starcraft\StarCraft.exe
        0000001c    2
        0000001b    0
        0000001a   15
        00000019   15
        00000017    0
        00000016    0
        00000015    1
        00000014    0 <==
        0000000c
        0000000d    0
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  70 (X_PolyFillRectangle)
  Resource id in failed request:  0x0
  Serial number of failed request:  105
  Current serial number in output stream:  142

Now, I only really care about connection to Battle.net to get the patches. So when this didn't work I figured I'd  grab the patches from blizzard and apply them that way. Grabbed the patches, but when I try to use them with wine I get a short error message and nothing happens.
The message:
Warning: could not find DOS drive for current working directory '/home/gaberade/Desktop', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\SC-113f.exe": Module not found

I think this might have to do with the path of my fake c drive, but I'm only 2 days old with Ubuntu.

Anyone care to enlighten me? :D

---

### Post by shinygerbil on 2006-03-28
You might try making sure you're in the same directory as the patches, and run them from the commandline. It seems to make a difference with a lot of executables...

It's also quite possible you have conflicting versions of wine installed - it seems to be quite picky about these things. I had a similar problem; I deleted the '.wine' directory from my home folder, then ran wine again, and it made all things complete (after configuring, of course :) ).

Hope this helps

Steve

---

### Post by gaberade on 2006-03-28
Well I uninstalled wine, and then at the command line i removed the /.wine folder.
Installed wine with the apt get command and winecfg'd again. Worked PERFECTLY. Still a black screen and all with battle-net, but the patches applied fine. Thanks so much!

---

### Post by blackant on 2006-04-11
Did you apply the patch of broodware?

---

### Post by Toxicity999 on 2006-04-11
*Broodwar...

and Battle.net seems to work fine in WIII for me anyway... in .11 are oyu using .11? before it's release I heard quite a bit about bnet hell so if your not, consider upgrading.... also I compiled my version with the MMap patch specifically for WoW.... not sure if that really has any meaning to this but it could be possible for my success...

---

### Post by JAF_temp on 2007-08-09
Hi,

I just installed Ubuntu Feisty on my Dell 6400. Now i want to play SC.

I already installed SC and BW, no problem with that, but I'm having same problem with Bnet... black screen appears... i already patched both, actual version 1.15.0 :confused:

thanks for your help!!!

---

