---
title: "WoW installer won't work"
date: 2010-12-12
forum: Wine
---

### Post by Kruger2147 on 2010-12-12
So I just downloaded the WoW free trial Installer. From the stuff I read, I needed to add a few things then WoW should work fine and dandy. At first it was, but then I had to restart my computer cuz of an update finish. After I rebooted, the WoW installer wont work. If I open it up, and click install it just says "waiting for files to close" and wont do anything. I figure its some glitch cuz its already partially installed.
 - I can't get into my C: drive to remove the files, how do I do this?

OR

When I click play, and let the updater take care if the installation, the window just closes and nothing else happens. 

How do I fix this so I can finish installing it, update it and play?

---

### Post by Tweak42 on 2010-12-13
What version of wine, 3d accelerator and drivers are you using?

Default location wine puts all the programs is /home/<username>/.wine , you should find the "C: drive" in there.  The . makes it hidden at the command line and in Nautilus file manager but it is there.  Open your home directory in Nautilus and hit Ctrl-H to unhide all the . files and you should see it.  You can rename the .wine directory to be deleted later just in case.  Running the "Configure Wine" will create a new .wine directory if it's not there.  Then you can start another clean install.  

Some guides that might help:
[http://www.wowpedia.org/Wine_troubleshooting](http://www.wowpedia.org/Wine_troubleshooting)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549)

Because it's hanging at first time launch, it might be something with the config.wtf file, you may need to either create one or edit manually.

---

### Post by Kruger2147 on 2010-12-14
Thank you. I'm installing a virtual machine for some other programs I have. I'll just install WoW on that.

---

### Post by cwwilson721 on 2010-12-14
Do a search for the issue in this forum (it has been asked/answered MANY times)

The answer has to do with ports.

Next time, search first

---

