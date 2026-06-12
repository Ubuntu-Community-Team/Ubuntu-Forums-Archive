---
title: "[SOLVED] CCCP codeck pack made my disk drives vanish(windows2000pro)"
date: 2007-09-19
forum: Windows
---

### Post by offline on 2007-09-19
Proibably...

I downloaded cccp {Combined-Community-Codec-Pack-2007-07-22.exe}to my windows 2000pro pc(celeron1GHz). My card is NVIDIA and I had installed ffd and xvidcodecs. The day before I installed gmplayer for windows too.

Media player classic played mkv files nicely with subtitles. Then I shut down my pc and rebooted 2 days later:  a BLUE SCREEN--no passaran. It said something about Cdr4_2k.sys file causing the proble. So I rebooted in safe mode and did a search for Cdr4_2k.sys. There were 2 instances of it: in WINNT and Picasa program directory.

I uninstalled picasa and did nothing else. After rebooting in normal mode the blue screen vanished bye bye but now there were none of my disk drives(cdrw and dvdrom in side my computer folder. In device manager therewere yellow ! signs on both of them and it said that this device is not working becausewindowscould not dowload their drivers(although there was a genericmicrosoft driver name mentioned)

So I did what microsoft says:

[http://support.microsoft.com/kb/315378/en-us](http://support.microsoft.com/kb/315378/en-us)

But doing a search I realised that both instances of Cdr4_2k.sys were absent now. I deleted Cdralw2k.sys and regedited registry as instructed(first extracted all theregistry, deleted the keys in registry and merged the reg file.

nothing changed after rebooting.So then I found another MS article:

[http://support.microsoft.com/kb/315378/en-us](http://support.microsoft.com/kb/315378/en-us) and followed the instructions(but before this I uninstalled  cccp pack without any results).

The drives came back working!!

But now I can not play mkv files or use cccp . Any suggestions to be able to play them??( I have vlc but it can not play mkv files...encoded in real format.

cccp said it was probably bad timing. Doing a google search points towards roxio, which I only have in my WMP directory(recently reinstalled wmp)
Thanks.

---

