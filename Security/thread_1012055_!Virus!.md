---
title: "?!?Virus?!?"
date: 2008-12-15
forum: Security
---

### Post by Hozza on 2008-12-15
i decided to do a virus check on my ubuntu 8.10

i am using 

ClamAV
chkrootkit
rkhunter

ClamAV is still going so ill post about that later..... (ClamGK is on 3% atm and has found a virus :sad:)

chkrootkit and rkhunter BOTH came up with [COLOR="Red"]WARNING[/COLOR]

What shall i do, has it fixed them its self or have i got to do it??
[URL="http://hozzamedia.co.uk/rkhunter.txt"]
Click to see my rkhunter.log[/URL]

please help!! :(

---

### Post by ~Mathewc~ on 2008-12-15
Hmm, i just started using ubuntu so i wouldn't know, but i assume that there wouldn't be any viruses. So i think you'd be good to go.

---

### Post by jrusso2 on 2008-12-15
> **Hozza said:**
> i decided to do a virus check on my ubuntu 8.10

i am using 

ClamAV
chkrootkit
rkhunter

ClamAV is still going so ill post about that later..... (ClamGK is on 3% atm and has found a virus :sad:)

chkrootkit and rkhunter BOTH came up with [COLOR="Red"]WARNING[/COLOR]

What shall i do, has it fixed them its self or have i got to do it??
[URL="http://hozzamedia.co.uk/rkhunter.txt"]
Click to see my rkhunter.log[/URL]

please help!! :(

You need to carefully check to make sure those are not false positives. Clam AV is notorious for false positives and the root kit detectors need to be interpreted carefully or you will do more harm then good.

---

### Post by Hozza on 2008-12-15
how do i check if they are false positives ??

---

### Post by insane_alien on 2008-12-15
the files it shows warnings for are just because it doesn't have them in its lookup table.

if you installed unhide from the repositories then it is fine.

---

### Post by DirtDawg on 2008-12-15
I would like to give you the unsolicited suggestion of trying [Avast]("http://www.avast.com/eng/avast-for-linux-workstation.html") or [AVG]("http://free.avg.com/download?prd=afl") for Linux. Both are free for personal use. ClamAV can literally take hours to complete a scan.

EDIT: I should point out neither of the aforementioned AV scanners are open source. That is very important to some people.

---

### Post by jcsteele on 2008-12-15
```
[17:57:42] System checks summary
[17:57:42] =====================
[17:57:42]
[17:57:42] File properties checks...
[17:57:42] Files checked: 127
[17:57:42] Suspect files: 2
[17:57:43]
[17:57:43] Rootkit checks...
[17:57:43] Rootkits checked : 109
[17:57:43] Possible rootkits: 0
[17:57:43]
[17:57:43] Applications checks...
[17:57:44] Applications checked: 3
[17:57:44] Suspect applications: 0
```

rkhunter only found 2 files that it found "suspect" - according to the log,
they were:

/usr/sbin/unhide
/usr/sbin/unhide-linux26

But I don't think you should be worried at all...these files are present
normally.  You probably didn't run the "$ ***sudo rkhunter --propupd*** " command
either, which would cause these problems.

All in all, unless you notice something strange happening with the machine,
everything should be fine.

---

### Post by slowth5 on 2008-12-15
Hi Hozza,  I just installed rkhunter to compare with your results, and my results are very similar to yours.  Namely, I received warnings for unhide and unhide-linux26.  When installing rkunter, I noticed unhide as a dependency, so I'd take these results with a grain of salt.

As for the virus, it's most likely a windows variant, but research the results whenever the scanner finishes.

---

### Post by hyper_ch on 2008-12-16
(1) no antivirus is needed
(2) if you chose to ignore (1) then do not scan linux binaries. Only attachments for window.s

---

### Post by azwar on 2008-12-16
Possibly it's a windows virus which reside in your hard disk. It doesn't matter if you have the windows virus because the virus cannot to anything harm to your computer, you can delete it manually from nautilus or from CLI or just ignore. 

I personally have the same problems when I scan with Avast antivirus. Most of the virus came from my windows partition and pendrive coz i'm here sharing the same computer. Due to drag and drop file to and from windows partition, I suspected that I've also do the same to  the virus.

I also suspected that some torrent file i download over the net contain the same virus. but who care, we are running the ubuntu linux.

in my personal view, virus, malware etc is not the security issues with my ubuntu. but if you're running a mail server you can scan the /var/mail for virus before they reach the windows client pc

---

### Post by Hozza on 2008-12-16
> **DirtDawg said:**
> I would like to give you the unsolicited suggestion of trying [Avast]("http://www.avast.com/eng/avast-for-linux-workstation.html") or [AVG]("http://free.avg.com/download?prd=afl") for Linux. Both are free for personal use. ClamAV can literally take hours to complete a scan.

EDIT: I should point out neither of the aforementioned AV scanners are open source. That is very important to some people.

I have AVG for linux and i use it however it never finds anything so i was unsure if it was working.....i will try avast aswell

> **jcsteele said:**
> ```
[17:57:42] System checks summary
[17:57:42] =====================
[17:57:42]
[17:57:42] File properties checks...
[17:57:42] Files checked: 127
[17:57:42] Suspect files: 2
[17:57:43]
[17:57:43] Rootkit checks...
[17:57:43] Rootkits checked : 109
[17:57:43] Possible rootkits: 0
[17:57:43]
[17:57:43] Applications checks...
[17:57:44] Applications checked: 3
[17:57:44] Suspect applications: 0
```

rkhunter only found 2 files that it found "suspect" - according to the log,
they were:

/usr/sbin/unhide
/usr/sbin/unhide-linux26

But I don't think you should be worried at all...these files are present
normally.  You probably didn't run the "$ ***sudo rkhunter --propupd*** " command
either, which would cause these problems.

All in all, unless you notice something strange happening with the machine,
everything should be fine.

thank you, but what does --propupd do??

---------

> (1) no antivirus is needed

hyper_ch i do under stand that you "dont" need AV for linux however i am soon to be starting a Server Farm of Ubuntu computers, there will be many windows files on the system so i feel it is necessary.

---

### Post by cariboo on 2008-12-16
I know this is the standard answer, but is the best way to find what options a command has:

```
man rkhunter
```

If you ever run into a command you are not sure about man is your friend.

Jim

---

### Post by slowth5 on 2008-12-16
Man pages usually are a great reference, but in the case of --propupd, I think clarification is warranted.  

Here's a good explanation:  [http://rkhunter.wiki.sourceforge.net/MPC](http://rkhunter.wiki.sourceforge.net/MPC)

Hozza, I know the Windows users will appreciate your diligence with regards to virus scanning.

---

### Post by kuradoberi121 on 2008-12-16
[img]http://www.top1gaming.com/cosplay/shaiya-1.jpg[/img] See the answer [[color=#800080]click here[/color]](http://www.top1gaming.com/coscontent-153.html).  Want to see [[color=#800080]more pics[/color]](http://www.top1gaming.com/cosplayer.php)? Show yourself  on our forum [[color=#800080]click here [/color]](http://www.top1gaming.com/forum/index.php?gid=27)**Recommend:**[[color=orange]LineAge 2 Elf [/color]](http://www.top1gaming.com/coscontent-105.html)[[color=orange]Rin Tohsaka [/color]](http://www.top1gaming.com/coscontent-83.html)

---

### Post by sergioxela on 2009-01-19
[INDENT]Call me Paranoid Android :)  but, I just scanned my computer with ClamTK and found 9 viruses, then I found this thread in this forum:
"Wireshark reveals consistent packets being sent to 78.131.193.150."
and then I remembered the economical problems the US and because of that, a big part of the world is living, so,  some companies like M$ will be so eager to get rid of the free software for many reasons, and would try to do anything to do so, because if they were actually good companies, they could start helping to get rid of poverty which is the main reason for many problems in the world, they could donate computers to poor communities. Thats way I recommend you to scan your machine with your chosen anti virus, and remember, free software tumbling down to M$.
It is ironic that a bunch of enthusiastic boys made possible what we are living this linux reality.
English is not my native language, I am sorry for the mistakes.

---

### Post by mikewhatever on 2009-01-19
Can you post the exact info on the file reported as virus by Clam. By exact, I mean the full path to file and file name.

---

