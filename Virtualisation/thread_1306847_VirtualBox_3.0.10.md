---
title: "VirtualBox 3.0.10"
date: 2009-10-30
forum: Virtualisation
---

### Post by Fraser1987 on 2009-10-30
Hi,

I've just this second installed VirtualBox 3.0.10 and tried to install Windows XP Professional SP3. I got the following message but I'm not sure what is wrong.

A critical error has occurd while running the virtual machine and the machine execution has been stopped.

For help, please see the Community section on [http://www.virtualbox.org](http://www.virtualbox.org) or your support contract. Please provide the contents of the log file VBox.log and the image file VBox.png, which you can find in the /home/<user>/.virtualbox/machines/Windows XP Professional sP3/logs directory, as well as the description of what you were doing when this error happend.Note that you can also access the above files by selecting Show Log from the Machine menu of the main VirtualBox window.

Press OK if you want to power off the virtual machine or press ignore if you want to leave it as it is for debugging. Please note debugging requires special knowledge and tools, so it is recommended ot press OK now.

<Ignore> <OK>

------------------------------------------------------------

Ideas?.

---

### Post by howefield on 2009-10-30
That's a bit unfair, isn't it ? ;)

You deny anyone here the information that the the people at Virtualbox would want to see, and you expect some help.  :)

Given the paucity of your details, I'd search the internet for - A critical error has occurd while running the virtual machine virtualbox - and see what turns up, after I'd posted in the virtualbox support sections.

FWIW, I'm currently installing 9.10 along with the new Virtualbox, if I get the same error, I'll let you know.

---

### Post by Meow27 on 2009-10-31
from what i hear. the newest version 3.0.10 deletes your VMs.... ppl recommend using 3.0.8

---

### Post by rliegh on 2009-11-01
> **Meow27 said:**
> from what i hear. the newest version 3.0.10 deletes your VMs.... ppl recommend using 3.0.8
If that's true, I can't find any source for it -can you point out where people are saying this? 

If this is true, it would be a good thing to point out to the VB devs (who -as far as I'm aware- aren't aware of this).

I'm using 3.0.10 on 09.10/i386 and have no problems so far....

---

### Post by niteshifter on 2009-11-01
Hi,

I posted [this]("http://ubuntuforums.org/showthread.php?t=1304280") 3 days ago. The update didn't delete the VMs, it rendered them useless - they crashed right after starting. There's a link to virtualbox forums in that post - wasn't just me having problems. 

Specifically that was VirtualBox 3.0.10 r54077 that was broken. It was replaced by 3.0.10 r54097 (within a day) which should work - according to the folks on the virtualbox forums. I haven't tried it, I'm keeping my install locked at 3.0.8 until 3.1.xx comes out ;)

---

### Post by Fraser1987 on 2009-11-01
I got this working. I just enabled SCSI Logic after enabling the SATA controller in the options... w/e. Sorry for not being specific right now I'm just testing out wine. XP works great in VirtualBox now. :D

---

