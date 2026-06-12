---
title: "Copied WoW from Mythbuntu to Ubuntu, won't start"
date: 2010-03-10
forum: Wine
---

### Post by Kurtosis on 2010-03-10
Last week I installed Mythbuntu, and got WoW up and running in Wine by running the wow installer and installing it from scratch in Wine.

I then found my TV card doesn't work w/ Myth, so decided to replace Mythbuntu with a clean install of Ubuntu.  I used a new hard drive for this install, set the new Ubuntu hdd to sda1 and the old Mythbuntu drive to sdb1, then copied the Warcraft folder over from my old Mythbuntu Wine directory to my new Ubuntu wine directory.

Both the [Ubuntu guide]("https://help.ubuntu.com/community/WorldofWarcraft#Alternative 1 (Copy from Windows):") and [other people]("http://ubuntuforums.org/showthread.php?t=758428") say this is all you need to do and then you can run WoW in the new installation with no problems, but it's not working for me.  

When I try to start WoW.exe by right-clicking it and selecting Open with Wine, I see a "Starting WoW.exe" button on the task bar for a few seconds, then it vanishes, but no WoW.  When I check System Monitor, I see that WoW.exe is listed, usually consuming 100% CPU or close to it.

I tried chown and chmod the copied Warcraft Folder to set it exactly equal to the owner:group and permissions of the original installed version, but no luck:

> cd ~/.wine/drive_c/Program\ Files
sudo chown -Rv kurtosis:kurtosis Warcraft
sudo chmod -R 755 Warcraft

and when that didn't work:

> [sudo chmod -R 770 Warcraft]("http://www.wowwiki.com/Wine_troubleshooting")

But still same problem.

Any idea what I'm missing here?

Edit: something else strange going on with Winetricks that may be clue:

> kurtosis@kurtosis-desktop:~$ sudo sh winetricks
[sudo] password for kurtosis: 
wine: /home/kurtosis/.wine is not owned by you
You (root) don't own /home/kurtosis/.wine. Don't run winetricks as another user!
kurtosis@kurtosis-desktop:~$ 

I installed Wine under this user (no other users on this machine), so dunno why it things .wine isn't owned by me.  :/

> kurtosis@kurtosis-desktop:~$ ls -a -l
total 6436
...
drwxr-xr-x  4 kurtosis kurtosis    4096 2010-03-09 21:58 .wine
-rw-r--r--  1 kurtosis kurtosis  142409 2010-02-02 01:52 winetricks
...

---

