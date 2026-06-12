---
title: "A process that I can't kill"
date: 2007-10-27
forum: Windows
---

### Post by SNYP40A1 on 2007-10-27
On my work laptop, my company's IT recently made scan32.exe (the scandisk process) run at a level where I cannot kill it through the task manager.  When I hit the "End Process" button, I get access denied.  Is there a way to force the damn thing to die?  I acknowledge that scandisk is necessary on windows, but they have the thing setup to run every 4 days or something like that and it becomes annoying when I am using my laptop.  I leave it on all the time, so there is plenty of other opportunity to run it at night or whatever when I am not using it.

---

### Post by digital_exhaust on 2007-10-27
Are you stuck using a limited user account? If you don't have administrative privileges you won't be able to kill it... there are ways around that..... in most cases anyhow....

---

### Post by SNYP40A1 on 2007-10-27
No, I have admin privileges, I still can't kill it.  I thought about renaming the .exe next time it is not running, but even if I could do that, I probably should not.

---

### Post by LaRoza on 2007-10-28
> **SNYP40A1 said:**
> No, I have admin privileges, I still can't kill it.  I thought about renaming the .exe next time it is not running, but even if I could do that, I probably should not.

You probably shouldn't, even if you could.

You can disable service with "msconfig". (Enter in Terminal or "Run")

---

### Post by MartijnWeterings on 2007-11-05
If I need to kill a process I always open a shell and type in:

ps -A

then I search for the number of the process I like to kill and type in

sudo kill <number>

with <number> the number of the process I like to kill. I think that your problem with task manager is that you do not have administration privileges (at least you don't need them to run it).

Or maybe the process is ran by some other program and every time you kill it it is restarted. In that case you should see it come back under another id number and you need to find out which other process is running it.

---

### Post by LaRoza on 2007-11-06
> **MartijnWeterings said:**
> If I need to kill a process I always open a shell and type in:

ps -A

then I search for the number of the process I like to kill and type in

sudo kill <number>

with <number> the number of the process I like to kill. I think that your problem with task manager is that you do not have administration privileges (at least you don't need them to run it).

This is Windows, it isn't supposed to be that easy.

---

