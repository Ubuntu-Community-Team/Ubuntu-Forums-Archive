---
title: "desktop but not menus after Hardy install"
date: 2009-06-03
forum: System76 Support
---

### Post by OldDirtyTurtle on 2009-06-03
Hi,

I did a clean install of Hardy yesterday.  Upon completion, I ran the update manager and at the reboot, I get logged on, but no menu bars.  I did another clean install, and this time after running software updates, installing the System76 drivers, etc., I can operate.  I moved my backed up files back to to my home partition and off I went.

Now this morning when I fired up, log on, the same thing happens.  I see my background image, I see a folder that I put on my desktop, but I don't have menu bars.  

Any ideas?  This is my primary work computer and I'm losing quite a bit of productivity at a time when our nonprofit can't be farting around much.

???

---

### Post by thomasaaron on 2009-06-03
Did you transfer *all* of the files from your home directory? Even hidden ones like .gnome or .gnome2? If so, this could be the problem.

To get you up and running as quickly as possible, try to create a new user on your computer. Since you don't have menu's we'll do it from Recovery Mode.

To boot into recovery mode, restart your machine and press the "Esc" key when you see the grub countdown (i.e. grub...3...2...1...). This will bring you to a list of available kernels. Highlight the first line that has "Recovery Mode" in its title and press enter. You will then be presented with a GUI that offers you a list of options. Select "Drop to Root Shell Prompt."

To create a new user, run these commands...
```
adduser <newUserName>  #For example: adduser tommy
```

Follow the prompts to enter the new password, et. al.

Then...
```
assuser <newUserName> admin  #For example: adduser tommy admin
```

Now you can boot into your system and log in with the new username and password.

Then go to System > Admin > Users and Group and click the "Unlock" button and enter your new password. Then highlight your new user and click the Properties button. Then click the privileges tab. Make sure ALL of the checkboxes have been selected. Click OK. 

Log out and log back in as the new user. Do you have your menus, etc...?

Now, you can transfer JUST your important files over to the new user.

---

### Post by OldDirtyTurtle on 2009-06-03
Thanks Thomas, but no dice.  

And I did a fresh install of Jaunty over my old Intrepid - I made a mistake in my original post.

I did as you said and the new account is the same as the old one.  I see the default Jaunty background image but no menus.  I can right-click and get the standard Create Folder, Create...  blah, blah, blah.  But that's it.

When I backed up my original data from my old /home I only took my documents, music, and pictures folders and put them on an external hard drive.  Then when I moved them back to /home I dragged and dropped the contents into the corresponding folders on the jaunty /home folders.

Any other ideas?

---

### Post by thomasaaron on 2009-06-03
Strange.

Try pressing Alt-F2. In the resulting box, type: gnome-display-properties and press Run.
Do you have the proper resolution?

Press Alt-F2 and run: gnome-appearance-properties
Go to Visual Effects and set them to none. Does that give you your panels?

Press Alt-F2 and run: /usr/bin/jockey-gtk
Is your nVidia driver enabled?

---

### Post by OldDirtyTurtle on 2009-06-03
Alt-F2 produces nothing.  Hmm...

---

### Post by OldDirtyTurtle on 2009-06-03
My problem is covered here:

[http://ubuntuforums.org/showthread.php?t=797229](http://ubuntuforums.org/showthread.php?t=797229)

I'm confused about the solutions.  I did uninstall evolution in both rounds yesterday. 

Is that it?  It's easy enough to do a clean install and just leave evolution installed.

I'm not out anything by doing another clean install.

---

### Post by thomasaaron on 2009-06-03
I've not heard of evolution causing that before.

Interestingly, though, I just switched over to Thunderbird today, as it supports 2-way synching with gmail.

Try renaming your evolution folder...

Boot into the recovery mode terminal and run these commands...

mv /home/<yourUserName>/.evolution /home/<username>/.evolution.backup
reboot -h now

Do your panels come back?

If not, I don't think it's evolution.

---

### Post by OldDirtyTurtle on 2009-06-03
I assumed it was an evolution-linked problem based on the other thread.  Folks with my symptoms were had consistently removed evolution (and I'm assuming all related installations).  

I did a clean installation and am now back up and running.  I've been through several shutdown/restart cycles and no issues so far.  I'll keep this thread and come back if something goes awry again.

I've been on Thunderbird for quite some time.  I love the lightning calendar extension.  Be sure to follow the recommended settings on Gmail for pretty flawless and seamless syncing.

Thanks for our help!  Hope I don't need it on this issue any more!  :D

---

