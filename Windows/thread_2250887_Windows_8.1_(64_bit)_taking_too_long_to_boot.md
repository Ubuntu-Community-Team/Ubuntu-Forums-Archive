---
title: "Windows 8.1 (64 bit) taking too long to boot"
date: 2014-10-31
forum: Windows
---

### Post by john205 on 2014-10-31
Windows 8.1 has decided to take forever to boot after I decided to put my gaming PC into sleep mode (not the hybrid sleep, just the normal suspend to RAM sleep) That worked okay, nothing appeared to get very angry. When I woke the machine, the windows splash screen came up like it was in safe mode. I clicked to bring the form up, and it bluescreened in about a second. I didn't catch the error code, nor did I think to look. Then it said the updates failed, but I hadn't even run updates that day.

**Problem: **The disk activity light is constantly on (Haha, yeah. I got it fixed), save the one time it goes out for a moment. The drive on which Windows resides does thrash around for about 10-15 seconds then I can no longer hear it with the case open. (I have 5 drives; 4 SATA and one IDE with a USB adapter). But the disk activity light still shows a very large amount of activity. I've yet to try the one-by-one method.

I came up with a workaround that worked for maybe, three days: I would boot to safe mode, which worked the same boot time as before the crash. Then I would restart using the power button on the login screen. It would boot just fine after that.

Eventually safe mode started taking very long as well. The first time Safemode did this I hit the reset switch (haven't used it since) and went around in windows 7 (which boots perfectly without fail, so it's a software issue) looking for causes. Hard drives checked out fine, so I don't think that is the problem.

[B]What I tried (and didn't work):
[/B]Turn off hot swapping for SATA (turned them all on for something I did a while back)
Turned on fast boot (BIOS said something about it not supporting windows logo, never really turned it on)
Turned off early anti-malware software
Deleted pagefile.sys and hiberfile.sys (moved them to the USB IDE drive, ended up moving them back because it made W8.1 much angrier :P)
Using the windows cd to repair it (bluescreened saying my computer needed repaired. Not really helpful at all)
using command prompt from both OSs, and the windows 8 repair thing)
Almost every other thing I could think of
----

Now I haven't had the time or the patience to track down services and whatnot to disable them. Also, don't tell me to try uninstalling stuff to make it faster, until I verify that it's a program that I installed doing this. 

I haven't installed or uninstalled anything prior to the crash.
Lesson learned: Don't use standard sleep mode. Make sure you're using hybrid, which worked fine for me.

I'll check back when I get home.

---

### Post by john205 on 2014-10-31
[Removed whining]

---

### Post by john205 on 2014-11-03
Well I found a workaround. If my windows 7 hard drive is unplugged before boot, it boots in 15 seconds. The drive is not failing; windows 7 works fine as well on it.

Now a new question, Why, of all things, is windows 7 slowing down windows 8, even being on another drive?

---

### Post by bashiergui on 2014-11-08
> Then it said the updates failed, but I hadn't even run updates that day.Win8.1 is configured by default to check for updates automatically. > But the disk activity light still shows a very large amount of activity.If you have office 365 installed it will constantly sync with onedrive (or whatever MS's cloud is called.) It also might be installing/checking for updates automatically.> Well I found a workaround. If my windows 7 hard drive is unplugged before boot, it boots in 15 seconds. The drive is not failing; windows 7 works fine as well on it.
Now a new question, Why, of all things, is windows 7 slowing down windows 8, even being on another driveWhat is the boot sequence set to in the BIOS? Sounds like perhaps the BIOS is confused on which to choose. Might be interesting to see if Win8.1 checks for other Windows OS's as it boots, but that would require general reverse engineering and/or general poking around.

---

