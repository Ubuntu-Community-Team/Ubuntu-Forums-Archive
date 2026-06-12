---
title: "VirtualBox: Unsupported version 11 of data unit 'vga'"
date: 2015-02-05
forum: Virtualisation
---

### Post by donpasquale on 2015-02-05
Hi there,

I am running Windows 7 in VirtualBox 4.3.10_ubuntu r93012 on Kubuntu trusty 14.04.1 LTS.

Like always I shut down the VM with "save the machine state".

After restarting the progess bar goes to 100% but then an error message occurs saying:
"Für  die virtuelle Maschine Windows7 konnte keine neue Sitzung eröffnet  werden. (= For the VM Windows7 a new session couldn't be opened.")
Unsupported version 11 of data unit 'vga' (instance #0, pass 0xffffffff) (VERR_SSM_UNSUPPORTED_DATA_UNIT_VERSION).
Fehlercode:NS_ERROR_FAILURE (0x80004005)
Komponente:Console
Interface:IConsole {8ab7c520-2442-4b66-8d74-4ff1e195d2b6}lsb_release -a

Since I am a newbie to linux I always run all the updates that are recommended by Muon ;-)

I have not made any changes to VirtualBox or the settings of the VM itself.

Many thanks in advance!

---

### Post by TheFu on 2015-02-05
Don't know the answer. Some thoughts.

Did the VM get patched and need to be rebooted?
Or did the hostOS kernel get updated so that the guest additions in the Win7 VM need to be reinstalled?

Saving the machine state is NOT shutting down. It is storing the RAM and session as it was at that instance ... sorta like hibernating.

---

### Post by dmoss on 2015-02-06
I've got the same problem after Ubuntu Studio update process that updates VirtualBox SW. 

My config:
- 1 Ubuntu Studio 14.10 HW machine
- 1 Ubuntu Server VM, runing as service (save sate at power off)

After VirtualBox SW Update and Host reboot, the guest VM cannot start with "VirtualBox: Unsupported version 11 of data unit 'vga'" error message.

I don't know the root cause, but I applied following workaround:
- stop VM, "loosing saved state"
- power on again VM

--> all have been ok from this hard VM reboot.

So, I suggest to stop by a clean power off all VM before updating VirtualBox (included in Ubuntu update process).

---

### Post by johannjanzen on 2015-02-06
> **donpasquale said:**
> Hi there,

I am running Windows 7 in VirtualBox 4.3.10_ubuntu r93012 on Kubuntu trusty 14.04.1 LTS.

Like always I shut down the VM with "save the machine state".

After restarting the progess bar goes to 100% but then an error message occurs saying:
"Für  die virtuelle Maschine Windows7 konnte keine neue Sitzung eröffnet  werden. (= For the VM Windows7 a new session couldn't be opened.")
Unsupported version 11 of data unit 'vga' (instance #0, pass 0xffffffff) (VERR_SSM_UNSUPPORTED_DATA_UNIT_VERSION).
Fehlercode:NS_ERROR_FAILURE (0x80004005)
Komponente:Console
Interface:IConsole {8ab7c520-2442-4b66-8d74-4ff1e195d2b6}lsb_release -a

Since I am a newbie to linux I always run all the updates that are recommended by Muon ;-)

I have not made any changes to VirtualBox or the settings of the VM itself.

Many thanks in advance!

Hi. Same problem here. 
> Für die virtuelle Maschine WinXP konnte keine neue Sitzung eröffnet werden.

Unsupported version 11 of data unit 'vga' (instance #0, pass 0xffffffff) (VERR_SSM_UNSUPPORTED_DATA_UNIT_VERSION).

Fehlercode:NS_ERROR_FAILURE (0x80004005)
Komponente:Console
Interface:IConsole {8ab7c520-2442-4b66-8d74-4ff1e195d2b6}


I only used Window XP in VirtualBox. I shut down the ubuntu-server remotely and asked to "save the machine state", but after the next start I experienced the same problem as above. And I think, before a reboot, there was also a system-update of the kernel...

Using Ubuntu 14.04.1 LTS (kernel 3.13.0-45-generic and VirtualBox 4.3.10_Ubuntu r93012

Post #3 from dmos worked for me, although I lost the data of some open programs...

---

### Post by donpasquale on 2015-02-08
Thanks a lot to all of you for the quick replies!

Since I'm a newbie I'm not really sure how VB works, so please allow me a maybe stupid question, just to make sure that I go it right.

Unfortunately I haven't done any  snapshots since installation which was months ago.

Does VB always safe changes (f.e. installed software, Configuration changes,...) to  the last snapshot (in my case the first one only) and the "saved  state" only keeps the data of the RAM, so to say, like a session that's  lost when I reboot?

Or will I lose the software installed and the  configurations made sinces the last snapshot I discard the  saved state?

Kind regards

---

### Post by TheFu on 2015-02-08
**Almost always** is the answer. There are exceptions.

[http://www.virtualbox.org/manual/ch01.html#snapshots](http://www.virtualbox.org/manual/ch01.html#snapshots) from the official documentation.  Best to read that since there are intricacies that could be important.

Nothing is lost at reboot for snapshots.
[http://www.virtualbox.org/manual/ch01.html#idp52379840](http://www.virtualbox.org/manual/ch01.html#idp52379840) - is the page for **saving state.**  Think of saved state as "standby" - it is RAM, not disk.

---

### Post by donpasquale on 2015-02-23
Thanks so far to everybody.

Unfortunately the problem has not been solved yet.

Going back to my one and only saving state causes the same error.

Rebooting the machine without saving state leads to the primary installation where all software installations and configurations that have followed are lost...

---

### Post by Jan Greeff on 2015-02-26
donpasquale, I had the same problem, updated vbox here and problem solved: [http://ubuntuhandbook.org/index.php/2014/11/virtualbox-4-3-20-released-upgrade-in-ubuntu/](http://ubuntuhandbook.org/index.php/2014/11/virtualbox-4-3-20-released-upgrade-in-ubuntu/)

---

### Post by SeijiSensei on 2015-02-26
That page describes the method of [using the official Oracle repositories for VirtualBox]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions"). I've always found that a better method than using the version of VirtualBox distributed by Ubuntu itself.  Plus you get the added benefit that your VB installation updates to the most recent release automatically.

---

### Post by JKyleOKC on 2015-03-04
Posts #3 and #9 have the proper solution to this recurring problem. Several times I've forgotten to power down one or more VMs here, that were in saved state, before allowing VBox to update via the Oracle PPA, and found them unable to start afterward. In every case, destroying the saved image made them available again. Since I do make it a practice to save any work in progress before closing a VM into saved state, all data was safe in the virtual disk files. It's always possible with today's operating systems that the data could still be in a buffer rather than moving to the virtual disk, but my experience indicates that VDI files get written to far more rapidly than do physical drives.

Losing software installations and upgrades as mentioned in post #7 has not happened here; that sounds as if the lost material needed a reboot after installation, that had not occurred. Once written to the virtual disk, everything should be independent of "saved state." The saved state, according to most descriptions I've found, is actually in a totally separate file, much like the hibernation file used by host systems.

I do make it standard practice to "save state" rather than closing down any VM that I use often. However I try to be certain that all are powered off before making any changes to VBox itself.

---

### Post by donpasquale on 2015-03-17
Hi Guys,

sorry for the late reply, I was on vacancies.

Thanks for your support all of you!

@[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195"): I did as you suggested. Trying to start the VM now I get (at about 98%):
"For the VM windows7 a new session couldn't be opened (my translation)
Für die virtuelle Maschine Windows7 konnte keine neue Sitzung eröffnet werden.
No error info.
Fehlercode:NS_ERROR_CALL_FAILED (0x800706BE)
Komponente:ProgressProxy
Interface:IProgress {c20238e4-3221-4d3f-8891-81ce92d9f913}

@[**[COLOR=#000000]JKyleOKC[/COLOR]**]("http://ubuntuforums.org/member.php?u=374258"): I definitely made several reboots in the meantime. I installed AVM Antivirus first, then rebooted, then installed MS Office, rebooted etc.

Any further ideas?

---

