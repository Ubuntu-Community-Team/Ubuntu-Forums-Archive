---
title: "very odd security risk"
date: 2007-01-07
forum: Server Platforms
---

### Post by dynamicres on 2007-01-07
i had just installed a new box and after i got a whole ton of apps installed and running, SOMETHING started randomly typing out an internet address on WHATEVEr window i had currently up...
here is a screenshot
[http://www.uploadfile.info/uploads/6365955f03.png](http://www.uploadfile.info/uploads/6365955f03.png)

i installed and ran chkrootkit
found nothing.
i uninstalled VNC. still happened.
could someone shed some light on how to rid this virus/spyware/bug?
like, would a online virus scan work? i havent been able to get the right pugins to run trendsofts yet. ill keep at it.

---

### Post by maxamillion on 2007-01-07
do you have firestarter running? if not, install it, run it and monitor inbound connections. but it looks like you have a compromised system and should probably backup data and reformat just to be on the safe side

---

### Post by Mike'sHardLinux on 2007-01-07
Did you install software not in the repos?

I think you can use netstat on the commandline to see the active connections. It might give you some more insight into what's going on.

---

### Post by enopepsoo on 2007-01-07
what software do you have installed to download MOVIEZ?  I could imagine if you did a direct port forward and bypassed your firewall that whatever app that is could have been compromised. :rolleyes:

---

### Post by kebes on 2007-01-07
In the screenshot it looks like it's an attempt to get you to download "rxbot.exe" from "miwebsite.com". (I'm assuming the "r" at the beginning and the "c" before rxbot were your typing mixing with the output?) rxbot.exe is a Windows worm, and "miwebsite.com" doesn't look like a site that has any real content on it. Just a parked domain.

It seems weird that someone compromising a Linux machine would try to get it to download a Windows worm. Perhaps some cross-platform app is compromised. (I see firefox running in the screenshot... could it be some sort of clipboard-injection from malicious website code? Does the weirdness persist if firefox is closed?)

---

### Post by dynamicres on 2007-01-07
LOL! na the 2 hard drives you see are directly from my main system and are in this box as backup, im using it as a backup server above all, and a small web/game server.
so i have only installed appropriate apps that i know of.
the only thing i can think of that might of compremised anything would have to be tightvnc.
and as soon as this started happening, i removed that program. 
but it still happns =/
odd thing also i should add is that it even started typing in the web site on my LOGIN to the box!!

and yes it will sit there and type stuff out so yes the R and C etc. are me interupting.


as for :
Does the weirdness persist if firefox is closed?
i will be testing that now.

---

### Post by dynamicres on 2007-01-07
OOh, i installed the virus scanner that is under applications/ add/remove.
and it came up with a few infected files from my windows backup i was running.
which would explain why it was trying to run a windows virus?

and i have antivirus running on my windwows box which makes me wonder why its still on the HD... 
for reference, ive never had this happen on my windows box.

virus name =
W32/Netsky.c@MM
and 
w32/Magistr.a@MM

which brings up another issue...
is my backup method vulnerable?
i had a program called cobain 7 
which backed stuff up thru FTP on a schedual.
i set a user for the FTP for this process.

UPDATE**
yes it still happens while running the virus scan and with no firefox open.

oh and ill try to get firestarter  running as soon as the virus check is done, thanks max.

---

