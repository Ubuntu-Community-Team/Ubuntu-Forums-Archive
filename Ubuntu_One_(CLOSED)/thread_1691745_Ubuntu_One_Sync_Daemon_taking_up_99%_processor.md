---
title: "Ubuntu One Sync Daemon taking up 99% processor"
date: 2011-02-20
forum: Ubuntu One (CLOSED)
---

### Post by outleradam on 2011-02-20
Ubuntu One Sync Daemon is taking up nearly 100% of my processor.  I kill the process, and then it comes back later with the same thing.   Every time I reboot, I have to kill the process and then again when my computer keeps bogging down.   Ubuntu One is not synchronizing.  It is stuck in some sort of loop.   How do I fix it?  I don't know much about Ubuntu One.

---

### Post by Souptik on 2011-02-20
> **outleradam said:**
> Ubuntu One Sync Daemon is taking up nearly 100% of my processor.  I kill the process, and then it comes back later with the same thing.   Every time I reboot, I have to kill the process and then again when my computer keeps bogging down.   Ubuntu One is not synchronizing.  It is stuck in some sort of loop.   How do I fix it?  I don't know much about Ubuntu One.


I have the same problem and have posted about it minus the processor bit which unfortunately I have not noticed.... Can anyone solve our problem ?????:(

---

### Post by Iowan on 2011-02-20
Moved to Ubuntu One subforum.

---

### Post by Docaltmed on 2011-02-28
I have had the same problem on 3 different platforms. Unfortunately, the only way I could stop it was by entirely removing Ubuntu One from my computer.

---

### Post by outleradam on 2011-03-02
Any support here? 

Just remember, Team Ubuntu One,  the modern day use of the word "virus" is  any software installed without permission or knowledge of capabilities and causes undesired actions on a host computer.   This newer version of the 1990's "3mhz virus" comes pre-installed on every Ubuntu computer.  **Way to go!**

---

### Post by gotamangoflavouredrat on 2011-03-11
Just removed "Ubuntu One", its fine to hit 100% now and then on a desktop, with extra fans its does not over heat
On a laptop , leave the laptop alone for a hour and it drains the battery, luckily the machine overheats and shuts down before the battery is fully drained.

At least giving the process a lower priority does not freeze the machine while using it.

---

### Post by duanedesign on 2011-03-14
> **outleradam said:**
> Ubuntu One Sync Daemon is taking up nearly 100% of my processor.  I kill the process, and then it comes back later with the same thing.   Every time I reboot, I have to kill the process and then again when my computer keeps bogging down.   Ubuntu One is not synchronizing.  It is stuck in some sort of loop.   How do I fix it?  I don't know much about Ubuntu One.

Do you have anything in this file?:

~/.cache/ubuntuone/log/syncdaemon-exceptions.log

---

### Post by outleradam on 2011-03-15
no, nothing.  Do I have to reinstall ubuntu-one to have something there?   I uninstalled it because it worked for other people.  I mean, if it's a log, it should have something there after I uninstall right?

---

### Post by eljc2 on 2011-07-16
I had a problem with the ubuntuone sync daemon using up more and more memory and pushing my CPU speed to 100%. It was using so much memory, that even File Manager was crawling, so I couldn't get in to any files.

Here is what I did that solved the problem for me. You might like to try.

1) Go to System > Preferences > Startup Applications, then untick UbuntuOne
2) Restart. After restart, the sync daemon shouldn't be running.
3) Backup the files you have recently synced to a safe location
4) Delete the files or folders set to sync that have been added or modified before you started having problems.
5) Login to the ubuntuone dashboard at [https://one.ubuntu.com/](https://one.ubuntu.com/), then delete the same files and folders as in step 4.
6) Go to System > Preferences > Synaptic Package Manager, and put in 'ubuntuone' in the search box at the top. Look for girl1.2-ubuntuone-1.0 and mark it for installation. Install it.
7) Go back to System > Preferences > Startup Applications and retick UbuntuOne
8) Go to System Preferences > Ubuntu One. At this stage, my CPU maxed out for a few seconds, then it returned to normal and Ubuntu One said. 'File Sync is up to date'.
9) As a final check, I created a new OpenOffice word file in a synced folder. This was uploaded OK and the problem was solved.

Unfortunately, instead of unticking Ubuntu One in step 1, I actually deleted it from the list of startup applications. This means that I couldn't retick it in step 7 and I have to start Ubuntu One manually each time I boot. If anyone knows how to get it back on the list, please let me know.

---

### Post by eljc2 on 2011-07-16
Got the last bit solved by going to System > Preferences > Startup Applications, clicking 'Add' and then finally pasting this into the command box: /bin/sh -c '[ -d "$HOME/Ubuntu One" ] && ubuntuone-launch'

---

### Post by duanedesign on 2011-07-18
This could be caused by trying to sync files owned by root. This has been fixed in newer clients but might affect people running older Ubuntu One Clients.

I recommend if you need support for Ubuntu One the best place is to contact [Ubuntu One Customer Support directly]("https://one.ubuntu.com/support/contact/").

You can get more detailed logs to help in troubleshooting issues by doing the following:

1. Open Applications->Accessories->Terminal and run:
```
echo -e "[logging]\nlevel = DEBUG" > ~/.config/ubuntuone/logging.conf; u1sdtool -q; u1sdtool -c
```

2. Copy files into your ~/Ubuntu One folder and let it run for awhile to collect information.

3. Open your home folder

4. Click the View->Show Hidden Files menu option

5. Open the .cache/ubuntuone/ folder

6. Right click on the log/ folder and select "Compress"

7. Click OK and you should have a file named "log.tar.gz" in the .cache/ubuntuone folder, move this file to your Desktop since it's in a hidden folder which can be hard to find in the next step

8. You can attach the log.tar.gz archive to a bug report or an email to [EMAIL="ubuntuone-support@canonical.com"]U1 support[/EMAIL].

respectfully,
duanedesign

---

### Post by Yumi on 2011-07-21
Thank you for this threat. I have now found which program sucked the power out of my batteries. Disabled File sync and now batteriew last much longer.

Another annoying thing - I work for a short time on the notebook and when I want to switch off Ubuntu One informs me that "some files are still syncing". I have to leave it until ----

Synchronizing takes forever. Always uploading huge files over a slow connection, this is logical. Would it be possible only to synchronize the changes to a file instead of uploading the whole Gigabites every time?

Michael

---

### Post by ozzyprv on 2012-06-04
Only this sis the trick for me....

```
sudo apt-get --purge remove .*ubuntuone.* .*couch.*
```

... I tried un-installing (it was uninstalled) and checking the startup app's (it wasn't there either). Yet the demon was coming back after each re-start.

---

