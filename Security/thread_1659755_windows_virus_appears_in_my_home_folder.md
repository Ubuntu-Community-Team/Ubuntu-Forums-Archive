---
title: "windows virus appears in my home folder"
date: 2011-01-04
forum: Security
---

### Post by superpisto on 2011-01-04
Lately, I've found 2-3 times an .exe file with a random name in my /home, and another data file with a random name as well. I'm a user of wine, but none of the programs that I use seems to be the cause.
Last time it happened I sent it to virustotal.com, and this is the result: [http://www.virustotal.com/file-scan/report.html?id=779f9bb28c800b6ab18de2b88ccc7b0ca08b79cd99dc42214dbeb219b46bc5cb-1294161817](http://www.virustotal.com/file-scan/report.html?id=779f9bb28c800b6ab18de2b88ccc7b0ca08b79cd99dc42214dbeb219b46bc5cb-1294161817)
So, this is clearly a virus.
The two files show "nobody" in the proprietary field and "none" as group.
What can I do to track down the cause?
Also, telepathy-butterfly likes to hog 100% of CPU lately, and all I can do is killing it: is someone exploiting a vulnerability? if so, why the hell would he drop a win32 virus?

thanks.

---

### Post by uRock on 2011-01-04
I just uninstalled telepathy-butterfly via Synaptic Package Manager after reading what it does and everything that I use that is related to MSN still works properly. That said, I think you should uninstall it as well, being that it is giving you problems.

If uninstalling causes something else to not work, then you can easily reinstall it.

---

### Post by superpisto on 2011-01-04
> **uRock said:**
> I just uninstalled telepathy-butterfly via Synaptic Package Manager after reading what it does and everything that I use that is related to MSN still works properly. That said, I think you should uninstall it as well, being that it is giving you problems.

If uninstalling causes something else to not work, then you can easily reinstall it.
ok.

no ideas about the virus problem?

---

### Post by uRock on 2011-01-04
> **superpisto said:**
> ok.

no ideas about the virus problem?
When you delete them, do they reappear or are they just popping up out of nowhere? While they may have an effect on your Wine applications, I doubt they can hurt anything else. If you do not mind me asking, what programs do you run in Wine?

---

### Post by superpisto on 2011-01-04
they stay deleted for a while, but it's happened at least twice that I found other exe with different random names after deleting them.

my wine applications are ida pro disassembler, windbg debugger, emule, foobar2000 as far as I can retell.

---

### Post by bodhi.zazen on 2011-01-04
From the looks of it your wine installation was infected.

I would advise you delete ~/.wine (note this will remove all installed applications and any data in ~/.wine) and re-install your wine apps.

Run an antivirus scan on any removable devices or shared directories.

As long as you are not running wine as root you should then be fine.

I also advise you remove the link in ~/.wine to your home directory and anywhere outside of ~/.wine.

~/.wine/dosdevices 

I do not allow wine to access anything outside of .wine, or if needed temp access only to cdrom / an iso for installation.

---

### Post by superpisto on 2011-01-04
I wonder how my installation could have been infected.
Fortunately, I'm almost sure I've never run wine with sudo.
> **bodhi.zazen said:**
> I do not allow wine to access anything outside of .wine, or if needed temp access only to cdrom / an iso for installation.
This looks wise, how can I setup wine to do that, and possibly select a limited list of path that it's allowed to read and write?

---

### Post by msandoy on 2011-01-04
Run winecfg in a terminal, go to drive setup, and remove all items pointing to anywhere else than ~/.wine/c_drive.

---

### Post by nitrogensixteen on 2011-01-05
My guess is that you have a pirated version of IDA Pro as it is so damn expensive and that the source was kind enough to include a virus.

---

### Post by superpisto on 2011-01-05
you might be right. But I use the same IDA version in my windows installation, and I've had no problems there.

---

### Post by DodgeV83 on 2011-01-28
> **superpisto said:**
> you might be right. But I use the same IDA version in my windows installation, and I've had no problems there.

...that you know of.  The smart viruses don't advertise their presence.

---

### Post by superpisto on 2011-01-28
of course. but being not the dumbest pc user and having an antivirus and since no symptoms have appeared so far, I believe that IDA is not the cause.

Btw. I uninstalled wine, and some daemons like samba and ssh. if they appear again, I'll run here again.

---

### Post by Jive Turkey on 2011-01-29
I imagine it wouldn't be too difficult to create an apparmor profile that would let you know when wine tries to write outside of ~/.wine.  

It could very well be that you aren't seeing any problems on your windows OS because the app in question installs a rootkit under windows and manages to run unobtrusively doing god-knows-what in the background.  You might find evidence of this by running a packet capture app on another machine while running windows.  Another approach could be to search for some of these randomly named executables on your windows partition from linux.  Antivirus applications won't always recognize new or polymorphic virii/malwares.  I don't have a link to the video but I saw a demonstration once where the presenter showed how trivial it was to take a known trojan (that ws detectable by all antivirus vendors over 5 years prior) and make it undetectable in a hex editor.

Nobody mentioned in this thread that there are drive by javascript exploits that can drop binaries into your user's home folder.  apparmor and the noscript plugin for firefox can help you avoid this too.

---

### Post by superpisto on 2011-01-30
I'm going  to check out this apparmor.

A rootkit is a piece of kernel, and on windows x64 it should block any installation of kernel stuff without signature, right?

---

### Post by OpSecShellshock on 2011-01-30
> **superpisto said:**
> I'm going  to check out this apparmor.

A rootkit is a piece of kernel, and on windows x64 it should block any installation of kernel stuff without signature, right?

Not exactly. A rootkit is a tool used to hide the fact of an already-compromised system from the system itself. If such a thing has been successfully introduced, then it's already too late to block it, and whatever it's trying to hide can't be removed without rebuilding the system. A 64-bit installation in and of itself won't necessarily prevent modification of low-level processes.

---

