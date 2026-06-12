---
title: "GTK themes work for some applications?"
date: 2010-06-01
forum: System76 Support
---

### Post by PsychoDevon on 2010-06-01
I tried to reinstall Ubuntu 10.04 after a problem I had with metacity that I was unable to fix. Now, after reinstalling, I had numerous package problems that now for the mean time are fixed.

Now, I have a somewhat odd problem with GTK themes.

Whenever I log in, I see a Windows 2000-esque basic GTK theme with tango icons all over the place for a split second. Then, panels use the actual theme, and some applications do. But, other applications don't. I can't really explain this, but this is what it looks like:

[IMG]http://i48.tinypic.com/ra2po0.jpg[/IMG]

I'm pretty sure this is due to a package problem that happened with my package problems while I was fixing it. My system is all upgraded & updated, and it still doesn't fix it. What do I do to fix this?

---

### Post by thomasaaron on 2010-06-01
I'm not sure if I fully understand your problem, but I *think* I do.

Go to System > Prefs > Appearance > Theme. Click the "Customize" button. Then, under the "Controls" tab, select "Ambiance." It looks like you have "Dust Sand" selected.

---

### Post by PsychoDevon on 2010-06-01
umm, that is NOT my problem whatsoever. I have tried enabling every theme I have installed, and Radiance controls were still selected in that screen. Couldn't you see I had Synaptic open displaying it correctly, meanwhile nautilus still has ****ups?

---

### Post by thomasaaron on 2010-06-01
Please be respectful on the forums. I'm trying to help you.

Can you give us a little more background on what configurations you've made, themes you've installed, etc... on your 10.04 installation.

I'm not able to duplicate this on a fresh install of 10.04.

When you installed, did you transfer your old hidden folders from your home directory into your new installation of 10.04?

---

### Post by PsychoDevon on 2010-06-02
I'm not being disrespectful, I'm just saying.

And no, I did not. I just installed Linux Mint 9, and it does the same thing.

No, I did not, because I didn't really have anything to transfer.

---

### Post by jbelmonte on 2010-06-02
Hi Devon,

Which System76 model do you have?

---

### Post by cbecker78 on 2010-06-02
try this: 

-go to your home folder, 
-use "control+H" to reveal hidden files
-backup your .config file by copying it to the desktop or some other directory
-delete the .config file in your home directory
-reboot your computer
-apply whatever theme you like and see if it looks proper
-go about recustomization

---if that doesn't work, just go and delete the new .config file in your home directory, copy the one you backed up back to the home directory, and reboot again- and then you should be right back where you started.  note, whereever you copied the .config file to, you won't be able to see it unless you navigate there in your file manager and reveal hidden files.

---

### Post by PsychoDevon on 2010-06-02
> **jbelmonte said:**
> Hi Devon,

Which System76 model do you have?

Um, I do not own a System76 computer. I have no idea why it is in this section-I posted this thread in General Support.

---

### Post by PsychoDevon on 2010-06-02
> **cbecker78 said:**
> try this: 

-go to your home folder, 
-use "control+H" to reveal hidden files
-backup your .config file by copying it to the desktop or some other directory
-delete the .config file in your home directory
-reboot your computer
-apply whatever theme you like and see if it looks proper
-go about recustomization

---if that doesn't work, just go and delete the new .config file in your home directory, copy the one you backed up back to the home directory, and reboot again- and then you should be right back where you started.  note, whereever you copied the .config file to, you won't be able to see it unless you navigate there in your file manager and reveal hidden files.


This did not work.

---

### Post by PsychoDevon on 2010-06-02
I found a fix-this didn't work in Ubuntu 10.04, but apparently it works in Linux Mint 9.

Whenever I opened Synaptic in Ubuntu, it told me to run "dpkg --configure -a". I did so several times after errors, and it never worked. But, i just did in Mint, rebooted, and everything is back to normal.

---

### Post by cbecker78 on 2010-06-03
> **PsychoDevon said:**
> I found a fix-this didn't work in Ubuntu 10.04, but apparently it works in Linux Mint 9.

Whenever I opened Synaptic in Ubuntu, it told me to run "dpkg --configure -a". I did so several times after errors, and it never worked. But, i just did in Mint, rebooted, and everything is back to normal.

Might want to mark this post as solved then.  YOu can find that option above in the thread tools.  Glad you got something to work.

---

