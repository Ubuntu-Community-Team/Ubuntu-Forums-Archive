---
title: "On-Line Trojan / Rootkit Scanners?"
date: 2006-03-17
forum: Server Platforms
---

### Post by Hangetsu on 2006-03-17
I know Linux is supposed to be fairly secure from the usual set of issues Windows boxes deal with, so installation of a scanning engine (AV, ASpyware, ARootkit, etc.) is not necessary.

However, if you wanted to confirm a clean machine, does anyone know if the online scanners work with Linux?  For example, TrendMicro has something called Housecall.

---

### Post by bjweeks on 2006-03-17
Nope.

---

### Post by navilon on 2006-03-17
[QUOTE=Hangetsu]I know Linux is supposed to be fairly secure from the usual set of issues Windows boxes deal with, so installation of a scanning engine (AV, ASpyware, ARootkit, etc.) is not necessary.

However, if you wanted to confirm a clean machine, does anyone know if the online scanners work with Linux?  For example, TrendMicro has something called Housecall.[/QUOTE]

Try [ClamAV]("http://www.clamav.net")

sudo apt-get install clamav

---

### Post by bjweeks on 2006-03-17
[QUOTE=navilon]Try [ClamAV]("http://www.clamav.net")

sudo apt-get install clamav[/QUOTE]

> However, if you wanted to confirm a clean machine, does anyone know if the **online** scanners work with Linux? For example, TrendMicro has something called Housecall.
...

---

### Post by Hangetsu on 2006-03-17
Well, that was clear and concise. :mrgreen:   Thank you!

So, to put a newbie Ubuntu user at ease (who was a security freak in Windows - only stayed there due to certain application requirements that don't exist anymore):

I installed outside of the standard repositories two apps - wpasupplicant and ndisgtk, namely the wpa support package and the ndiswrapper GUI.  I'd like to make sure they didn't have anything "extra" within the packages.  How can I check for keploggers or trojans on my box, to make sure they weren't installed?  Do any of the linux AVs do that (ClamAV, BitDefender, etc.)?

---

### Post by navilon on 2006-03-17
[QUOTE=bjweeks]...[/QUOTE]
I dont think you'll find any for linux, best bet is to download an AV

---

### Post by bscbrit on 2006-03-17
There is a root kit finder in the repos - called rkhunter.  It does a good job (mine runs under cron every 24 hours).  I also run clamav antivirus, not because my computer is vulnerable, but I do not want to be responsible for sending one out with my emails or whatever.  As linux is based on open source it doesn't contain adware so there is not much point in looking for it.  However, if you decide to download software from dubious sources which is not accompanied by the source code then you are on your own to a certain extent.
The usual rules of security will keep you safe - only use code from the recognised repos, don't visit sites which you know you shouldn't be visiting, don't run software if you are not 101% sure that it is what it says it is etc.
Other than that, you can sleep soundly at night knowing that the only thing that will stop you enjoying your computer is a hardware failure or when you tinker with it (and we all do - that's the fun of linux. :-D  )

---

### Post by bjweeks on 2006-03-17
only use clamav if your checking for windows viri cause if not your waisting your time cause it won't find any linux viri. Even if your paranoid there is still no point.

---

### Post by Hangetsu on 2006-03-17
If rkhunter can find keyloggers, I'm golden.  Thanks for the info!

My provider scans email for viruses (at least they are supposed to) so I'm not worried about spreading nasties.

---

### Post by bjweeks on 2006-03-17
rkhunter looks for rootkits...

---

### Post by LordHunter317 on 2006-03-19
Windows or Linux, you can't verify an installation is clean from the actual installation.  You must do it from a rescue CD.

As such, the entire idea of an online 'rootkit verifier' is rather silly.

---

### Post by beameup on 2006-05-13
Found this thread looking for info on Housecall.

[http://housecall.trendmicro.com/](http://housecall.trendmicro.com/)

If you use the " Scan individual selected folders only for malware" section, and set it to just scan your home directory, it will work. Does for me anyway.

If I try to let it scan the whole drive it scans awhile(probably the home folder) then it just sits.

---

