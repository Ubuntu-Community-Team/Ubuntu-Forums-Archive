---
title: "[SOLVED] Logon Password Removal"
date: 2008-10-01
forum: Security
---

### Post by AmbiguousOutlier on 2008-10-01
My laptop broke sometime ago, when I had XP installed so I sent it off to get repaired. I didn't tell them the password to log on they just removed it. 

Can this be done in Ubuntu, just wondering how secure my data is if I lose my laptop? 

Also is it possible for someone to take out the hdd and connect it up as a slave to another computer and browse all the files, like you would with Windows?

Is there anything I can do to stop these things from happening.

Thanks
Rhys

---

### Post by Therion on 2008-10-01
> **RhysGM said:**
> My laptop broke sometime ago, when I had XP installed so I sent it off to get repaired. I didn't tell them the password to log on they just removed it. 

Can this be done in Ubuntu, just wondering how secure my data is if I lose my laptop? 

Also is it possible for someone to take out the hdd and connect it up as a slave to another computer and browse all the files, like you would with Windows?

Is there anything I can do to stop these things from happening.

Thanks
Rhys
Simply put, if someone has total physical control of your laptop, you're pretty much screwed -- assuming the person or persons REALLY want your data.  Yes, you can pop out the hard drive and move it into a different PC to access the data.  You can use hardcore encryption but anything can be "cracked" with enough time and enough dedication to the task; really good encryption just makes doing so a fools errand because of the time and resources required. 128-bit encryption doesn't make it impossible, *per se*, it just takes years of enormous computing power to hack through.

But then again, how likely is it someone stole your notebook for your DATA?  I mean, I don't know... Maybe you work for the NSA and that's a real threat.  Most likely it's your hardware they're after.

---

### Post by AmbiguousOutlier on 2008-10-01
Is it possible to hide certain videos from my girlfriend? Or keep them in a folder that requires a password to enter.

---

### Post by snowpine on 2008-10-01
Anyone with an Ubuntu live CD and physical access to your computer can see all of your files, unless you set up some sort of encryption. Try it, you'll see how easy it is. 

ps You'd be surprised how cool girls can be about certain things if you give them the chance. ;)

---

### Post by Therion on 2008-10-01
> **RhysGM said:**
> Is it possible to hide certain videos from my girlfriend? Or keep them in a folder that requires a password to enter.
Ah.  The REAL Issue.  

The answer is yes.  How PC literate is your GF?  You can simply re-name the folder **My Porn Collection** to **.My Porn Collection** (notice the ".") and the folder will be hidden.

Now, there IS an option in one of the toolbars in Nautilus for "View Hidden Folders" but maybe you just need be a liiiittle creative where you PUT .My Porn Collection for some added <cough> confidentiality.

---

### Post by snowpine on 2008-10-01
You could also move the folder to a virtual machine. :)

---

### Post by hyper_ch on 2008-10-01
if you want to protect your data against physical access (e.g. losing the notebook or someone stealing your computer) then the easiest way is to fully encrypt your system.

However if you do so, you also need to backup your data (also encrypted...). Because if there's a hardware failure... e.g. boot sector of the harddisk, then you can't access any data anymore.

---

