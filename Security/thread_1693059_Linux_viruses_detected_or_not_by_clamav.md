---
title: "Linux viruses detected or not by clamav"
date: 2011-02-22
forum: Security
---

### Post by gdiloren on 2011-02-22
Is clamav ONLY for windows viruses or will it be good to detect some well known linux viruses (although many say there are no linux viruses!!!...:D) .

---

### Post by HermanAB on 2011-02-22
Howdy,

Here is a Linux virus scanner for you.  Save the file in /usr/local/bin and make it executable then run it and enjoy:

```
#! /bin/bash
echo Linux virus scanner version 1.3.3.4, GPL, 2011.
sleep 10
echo Scanning...
sleep 5
echo Computing...
sleep 10
echo Deep thinking...
sleep 20
echo Almost done...
sleep 5
echo Wait for it!
sleep 10
echo Drum roll...
sleep 5
echo No viruses found!
sleep 5
exit 0
```

Have fun!

---

### Post by oldsoundguy on 2011-02-22
> **gdiloren said:**
> Is clamav ONLY for windows viruses or will it be good to detect some well known linux viruses (although many say there are no linux viruses!!!...:D) .

And many are absolutely correct.  No Linux virus out there that has not already been addressed by the developers.

And remember .. Only YOU can install a virus on to your computer since NOTHING installs with a single click.

---

### Post by uRock on 2011-02-22
ClamAV does look for Linux viruses, but it is really a waste of time being that those same viruses are obsolete. 

When Linux viruses are first found, vulnerable code is patched immediately. This is why keeping an up to date system is more important than running AV.


Regards,
uRock

PS, nice code HermanAB

---

### Post by Joe of loath on 2011-02-22
> **HermanAB said:**
> Howdy,

Here is a Linux virus scanner for you.  Save the file in /usr/local/bin and make it executable then run it and enjoy:

```
#! /bin/bash
echo Linux virus scanner version 1.3.3.4, GPL, 2011.
sleep 10
echo Scanning...
sleep 5
echo Computing...
sleep 10
echo Deep thinking...
sleep 20
echo Almost done...
sleep 5
echo Wait for it!
sleep 10
echo Drum roll...
sleep 5
echo No viruses found!
sleep 5
exit 0
```

Have fun!

:lol: nice

---

### Post by brydonhunter on 2011-02-22
```
#! /bin/bash
echo Linux virus scanner version 1.3.3.4, GPL, 2011.
sleep 10
echo Scanning...
sleep 5
echo Computing...
sleep 10
echo Deep thinking...
sleep 20
echo Almost done...
sleep 5
echo Wait for it!
sleep 10
echo Drum roll...
sleep 5
echo No viruses found!
sleep 5
exit 0
```

I think I'm infected !!!

---

### Post by wormyblackburny on 2011-02-22
> **HermanAB said:**
> Howdy,

Here is a Linux virus scanner for you.  Save the file in /usr/local/bin and make it executable then run it and enjoy:

```
#! /bin/bash
echo Linux virus scanner version 1.3.3.4, GPL, 2011.
sleep 10
echo Scanning...
sleep 5
echo Computing...
sleep 10
echo Deep thinking...
sleep 20
echo Almost done...
sleep 5
echo Wait for it!
sleep 10
echo Drum roll...
sleep 5
echo No viruses found!
sleep 5
exit 0
```Have fun!

Beautiful!

---

### Post by Koffeehaus on 2011-02-22
> **HermanAB said:**
> Howdy,

Here is a Linux virus scanner for you.  Save the file in /usr/local/bin and make it executable then run it and enjoy:

```
#! /bin/bash
echo Linux virus scanner version 1.3.3.4, GPL, 2011.
sleep 10
echo Scanning...
sleep 5
echo Computing...
sleep 10
echo Deep thinking...
sleep 20
echo Almost done...
sleep 5
echo Wait for it!
sleep 10
echo Drum roll...
sleep 5
echo No viruses found!
sleep 5
exit 0
```Have fun!



Dude! That is cruel! Hahaha. It's like those ladies' pills when every once in a while you take an empty placebo pill purely for consistency reasons. A rather odd association, but still...

---

### Post by The Cog on 2011-02-22
In a less sarcastic vein, I'm sure that if there ever are any well-known Linux viruses, then clamav will look for them. However, there are none at the moment. I don't know if clamav looks for any Linux viruses at all to be honest. I don't think any have ever been seen outside of labs. 

With Linux, viruses aren't really your top problem. Logging in to insecure services like VNC and SSH, SQL injection attacks and maybe browser exploits are more of a worry. Unauthorised VNC and SSH logins (poor passwords) continue to be the main problems people want help with here. You can of course use clamav or other AV to scan files that you pass between yourself and windows users, to make sure you don't pass them on.

Windows users come here pretty-much every day and ask what AV to use to protect Linux. I guess they don't believe that viruses really aren't an issue - it's just taken as the norm. That's why you see some sarcastic answers.

---

### Post by HermanAB on 2011-02-23
The thing is that in a Windows environment, there is a strong financial interest in only fixing the band-aid (releasing a new AV version and charging millions of customers) and never fixing the actual problem (the Windows vulnerability).  Therefore, there are thousands of different viruses using the same old exploits to get into systems.

On Linux, when an exploit is found, the root of the problem is fixed almost immediately, thus closing the door on the exploits, since there is no financial incentive in prolonging the problem.

---

### Post by tjwoosta on 2011-02-23
I dont for a second believe that there are absolutely no viruses in the wild for linux, they're just very very rare and even more rarely discovered. 

I think being based on open source software has a lot to do with the stats, and being less popular im sure also has an influence. 

With windows people usually download precompiled binaries of closed source software from all over the place, often from random semi trustable websites who usually dont even offer integrity verification. When they do its manual verification and most users dont even know what its for, let alone how to use it.

With linux each distrobution has dedicated repositories that compile the sortware themselves from open source code availible for all to see and automatic integrity verification is standard.

---

### Post by The Cog on 2011-02-23
> **tjwoosta said:**
> I dont for a second believe that there are absolutely no viruses in the wild for linux, they're just very very rare and even more rarely discovered.
The original posts were about "well known" linux viruses. I don't know if there are any Linux viruses in the wild at the moment - I suspect not but I don't know. I'm fairly sure there are no well known ones.

I do suspect there may be a terminology issue. Windows folk tend to call everything a virus, from trojan PFD files to browser cookies. 

A few weeks ago, someone demonstrated an exploit that used a flaw in a PDF thumbnail generating program to take control of a Linux PC just by putting a USB stick in. The demo was performed in a presentation at a conference. A fix to the flaw was released very soon after - I can't remember if it was actually the following day or the day after that. An update to my PC from the Ubuntu repositories fixing the flaw arrived a day or two after that. Now there's a reason that viruses don't flourish on Linux that I haven't seen before. It's a combination of very rapid fix times and widespread patch application. Now, a virus could have been created using that flaw, possibly, though I don't think one was. It wouldn't have had long to spread before pretty-much all Linux boxes became immune, so it would have no chance of becoming a *well known* virus in the same way that many windows viruses are.

You may have heard about the above vulnerability. It was mentioned in lots of computer related media, and the usual Windows fanboy crowd gathered to jeer. But the thing is, this was newsworthy! Dog bites man - boring, happens all the time. Man bites dog is worth writing about.

There are almost certainly 0-day (meaning not publicly known) expliots of Linux as well as windows. But anti-malware code can't look for those. Once they become known about, the weaknesses get patched real quick so any virus based on that flaw can't spread. Unless it can spread rapidly before it gets discovered it will never become well known.

I really don't think there are any *known* Linux viruses spreading in the wild at the moment. And they're all any AV product can search for.

---

### Post by HermanAB on 2011-02-23
Well, I have been using UNIX since 1985 and Linux since 1998.  I have installed and configured thousands of machines and I have never encountered a virus.  If you find one, please forward it to me, since I would love to stuff it and mount it on the wall above the fireplace...

---

### Post by SeijiSensei on 2011-02-23
Running "sigtool --list-sigs | grep -i linux | sort" brings up these:

```
Backdoor.Linux.Small
Backdoor.Linux.Small-1
Backdoor.Linux.Suki.A
DDoS.Linux.Fork
DoS.Linux.Blitz
DoS.Linux.Chass
DoS.Linux.Forkbomb
DoS.Linux.Octopus
Dropper.Worm.Linux.Coptic
Exploit.Linux.Da2.B
Exploit.Linux.Local
Exploit.Linux.Lupii
Exploit.Linux.Lupii-2
Exploit.Linux.MySQL.20b4
Exploit.Linux.Pine.v456.Sorbo
Exploit.Linux.Race.C
Exploit.Linux.Race.H
Exploit.Linux.rpc
Exploit.Linux.RPC.A
Exploit.Linux.RPC.B
Exploit.Linux.RPC.C
Exploit.Linux.RPC.D
Exploit.Linux.RPC.E
Exploit.Linux.Small.V
Exploit.Linux.WU-FTPD.v262.WOOoouHappy
Exploit.Shellcode.Linux
Exploit.Shellcode.Linux-1
Exploit.Shellcode.Linux-Gen-1
Linux.Adm.Sh
Linux.Adm.Src
Linux.Adoreworm
Linux.Alaeda.A
Linux.Bish.A
Linux.Bliss.a
Linux.Brk.B
Linux.Brundle
Linux.Brundle-1
Linux.Cassini.1618
Linux.Caveat
Linux.Dido-478
Linux.Dido.478.elf
Linux.Diesel.969.elf
Linux.ELF.Compagnion
Linux.ELF.Zap
Linux.Evil.A
Linux.Fecto.A
Linux.Gildo
Linux.Godog.A
Linux.Godog.C
Linux.GodogWorm
Linux.Kagob.A
Linux.Kagob.B
Linux.LIME
Linux.LionCleaner
Linux.Lionworm
Linux.Lionworm-1
Linux.LionWorm.9
Linux.Mandrag.666
Linux.ManPage
Linux.Manpages
Linux.Nel.A
Linux.Neox.A
Linux.Nibom.A
Linux.NuxBee
Linux.Nuxbee.1403
Linux.Orig
Linux.Osf.3974
Linux.Osf.8759
Linux.Ovets.A
Linux.Ovets.B
Linux.QNX.Probe.B
Linux.Quasi
Linux.Radix16
Linux.Ranfy
Linux.Ranfy-1
Linux.RcrGood.556
Linux.Rootkit
Linux.Rootkit-1
Linux.Rootkit-10
Linux.Rootkit-11
Linux.Rootkit-12
Linux.Rootkit-13
Linux.Rootkit-14
Linux.Rootkit-15
Linux.Rootkit-16
Linux.Rootkit-17
Linux.Rootkit-18
Linux.Rootkit-19
Linux.Rootkit-2
Linux.Rootkit-20
Linux.Rootkit-21
Linux.Rootkit-22
Linux.Rootkit-23
Linux.Rootkit-24
Linux.Rootkit-25
Linux.Rootkit-3
Linux.Rootkit-4
Linux.Rootkit-5
Linux.Rootkit-6
Linux.Rootkit-7
Linux.Rootkit-8
Linux.Rootkit-9
Linux.Rst.A
Linux.RST.B
Linux.RST.B-1
Linux.Sickabs.15488
Linux.Siilov
Linux.Siilov.5916
Linux.Silvio.A
Linux.Silvio.B
Linux.Slapper-A
Linux.Slapper.B.src
Linux.Staog
Linux.Svat.A
Linux.Svat.B
Linux.Svat.C
Linux.Telf.8000
Linux.Telf.9812
Linux.Telf.A
Linux.Telf.B
Linux.Telf.C
Linux.Thebe
LINUX.Vit.4096
Linux.Winter-343
Linux.x.cworm
Linux.Xone.A
Linux.ZipWorm.elf
PolyEngine.Linux.LIME
PUA.Tool.ProcHider.Linux
Trojan.Linux.Attack
Trojan.Linux.BO.002
Trojan.Linux.BO.121.B-cli
Trojan.Linux.Cyrax.A
Trojan.Linux.LocalJ
Trojan.Linux.Rain
Trojan.Linux.Rohack.A
Trojan.Linux.Rootin.A
Trojan.Linux.Rootin.C
Trojan.Linux.Rootkit.A
Trojan.Linux.Rootkit.C
Trojan.Linux.Rootkit.I
Trojan.Linux.RST.b
Trojan.Linux.Small.I
Trojan.Linux.SSHD
Trojan.Linux.SSHScan
Trojan.Linux.SSHScan-1
Trojan.Linux.SucKIT
Trojan.Linux.Sysniff
Trojan.Linux.UDP
Troj.Linux.Rootkit-A
VirTool.Linux.Elfwrsec.A
VirTool.Linux.Infect
VirTool.Linux.Mmap.443
Worm.Linux.Cheese
Worm.Linux.Coptic
Worm.Linux.Coptic-1
Worm.Linux.Hijack
Worm.Linux.Mworm
Worm.Linux.Ramen
Worm.Linux.Ramen-1
Worm.Linux.Ramen.B
Worm.Linux.Ramen.C
Worm.Linux.Slapper.A
```

[Too bad the vBulletin "spoiler" tag is disabled.  It would help make postings like this less massive.]

That seems like a lot of Linux viruses, but it's still only 163 signatures out of a total of 903,678!

---

### Post by oldsoundguy on 2011-02-23
and all on that list were patched within hours of discovery and most never made it into the wild. (a lot of that crap in the list above is "proof of concept" stuff that was done in a lab and never got out of the lab!)

Added FACT.  You can NOT install a virus of ANY kind in Linux with the simple act of clicking on a link or a picture.  THAT was the primary problem in Windows until they emulated Linux with the "mother may I" screen. 
In Linux you have to INTENTIONALLY install as you WILL be asked for your password and what you want to do with the file!
As long as you use repositories , unless you are dumber than a ditch, no way malware can get into your Linux based OS.

I have a very good friend that programs for some major companies .. and will not work on any OS that does not have an X in it .. hates Windows with a passion beyond reason and refuses to fix them (says that until MS hardens the system against the chair occupant, that is the way he will continue to work). That fact is in his contract.
Makes good bucks .. enough that he owns a nice sized horse ranch in the Sierra Nevadas and phones in most of his work!

---

### Post by SeijiSensei on 2011-02-23
> **oldsoundguy said:**
> and all on that list were patched within hours of discovery and most never made it into the wild. (a lot of that crap in the list above is "proof of concept" stuff that was done in a lab and never got out of the lab!)

I wasn't suggesting that they were, or were not, a threat.  I was answering the OP's question of whether ClamAV recognized "Linux viruses."  The answer to that question is yes.  Having used Linux daily for over a dozen years now, I know from experience none of these are a real threat for the reasons you give.

Oh, and I forgot that the [noparse][code][/noparse] tag scrolls, though I still like the option of hiding chunks of text with the [noparse][spoiler][/noparse] tag.

---

