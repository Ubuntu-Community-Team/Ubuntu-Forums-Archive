---
title: "Possible rootkit?"
date: 2009-12-30
forum: Security
---

### Post by bradch on 2009-12-30
Sorry if this is too long but lots of info. Running 8.10 dual boot(wubi) with vista. Acer aspire 5735z. Firefox lost my bookmarks and won't let me go back a page or download. Installed epiphany and when I try to start it I get cannot start failed to create /home/brad/.gnome2/epiphany. Also trying to shut down ubuntu, the shutdown on the dropdown menu does not work. Pushing the power button gives me the option to shut down and that works. Started having trouble after trying to rip a dvd with k9copy and dvdrip. I enabled the medibuntu repo and libdvdcss and a couple of other dvdread things. I tried uninstalling and disabling medibuntu but didn't help. Also ripping the dvd didn't work so I thought maybe that did something to my system. I've been using ubuntu for a year but still new to it. Thanks for any help.

---

### Post by cariboo on 2009-12-30
It sounds like you have changed the permissions of your home directory. Open an applications-->Accessories-->Terminal and type:

```
cd /home
```

then at the prompt type:

```
sudo chmod -R 700 *
```

this will change the permissions of you home directory to read/write by you only. Note you should get an error saying that you can't change the permission of .gvfs.

---

### Post by bradch on 2009-12-30
I tried this and the return response was as you said. I tried to access my vista partition and instead of the usual password request it says System policy prevents mounting internal media. An application is attempting to perform an action that requires privileges.It then has a box for my password and under details has application listed as  /usr/bin/gnome-mount and then action listed as org.freedesktop.hal.storage.mounted-fixed. This isn't what came up before. It just ask for my root password before and showed nothing else.

---

### Post by bradch on 2009-12-30
Also when I try to create a folder or do anything else I am told I have no space. I know I have at least 13 gigs free on this partition.

---

### Post by bradch on 2009-12-30
Now the dropdown menu for applications is gone.Whatever this is it is getting worse.I want to back up my files to my external hdd but I'm afraid I might corrupt it. I don't know if this is something malicious or if I just really screwed something up.

---

### Post by cariboo on 2009-12-30
> **bradch said:**
> I tried this and the return response was as you said. I tried to access my vista partition and instead of the usual password request it says System policy prevents mounting internal media. An application is attempting to perform an action that requires privileges.It then has a box for my password and under details has application listed as  /usr/bin/gnome-mount and then action listed as org.freedesktop.hal.storage.mounted-fixed. This isn't what came up before. It just ask for my root password before and showed nothing else.

That is normal, depending on what version you are using.

As for the Menu problem, right click on the top panel and select **Add to panel** and select **Menu bar** and add it to the panel.

---

### Post by bradch on 2009-12-31
The menu bar is still there. Just the drop down for applications won't drop down. The dropdowns for places and system still work.I recently moved some files from my windows partition to my ubuntu partition, could this have caused any problems?

---

### Post by cariboo on 2009-12-31
What happens if you replace the current Menu Bar with a new one. Moving files from one partition to another should have no affect on you Ubuntu installation.

---

### Post by bradch on 2009-12-31
A new menu bar acts the same. No drop down on applications

---

### Post by bradch on 2009-12-31
If I launch firefox from the terminal it works like it should. Does this help? This makes me think you were right about me changing my permissions. How can I fix that?

---

### Post by bradch on 2009-12-31
OK I'm an idiot. Trying to fix permissions I set everything to 700. Now I can't even boot up ubuntu. It wants user and password. Nothing works.Trying to access through windows and a puppy live cd but no luck so far.I think having installed with wubi is messing this up.Anyone have any suggestions?

---

### Post by cariboo on 2010-01-01
My instructions were to just set the permissions for your home directory, not the whole directory tree. You can try fixing the problem, as most directories have a permission of 755, but it may be easier and quicker to reinstall in your case.

---

### Post by bradch on 2010-01-01
I managed to reset so I can start ubuntu. Just finished backing up my files.Got an iso of 9.10 I'm going to try installing without wubi this time. Thanks for the help.

---

