---
title: "Ubuntu One for restoring OS settings (packages installed, app settings)"
date: 2011-03-25
forum: Ubuntu One (CLOSED)
---

### Post by andrei_1 on 2011-03-25
It would be great if the Ubuntu One integration with the Ubuntu operating system could be enhanced so that ultimately one could restore an OS almost entirely.

This is useful when changing your computer or after restoring after a hard drive crash etc.

I'm thinking it could back up things like:

* General OS settings (appearance, themes, panels etc.)

* The packages installed (later a tool could apt-get install those on the new system)

* The application settings (things like ~/.wine/, ~/.audacity, ~/.amule etc.) because really, almost all Linux programs are "portable" by default

Your thoughts?

---

### Post by oldfred on 2011-03-25
I do not use Ubuntu One, but do what you suggest.

I have a rsync task. But I include running these and whenever I manually edit a system file in /etc I copy it into /home. My /home only has the hidden configuration files & some misc files as most of my data is in /data(EXT3) or /shared (NTFS) partitios which I separately backup. My /home is only about 1GB with most of that .wine (Picasa).

cp /etc/apt/sources.list ~/Documents/LinuxDocs/CurrentSys/sources.list.backup
dpkg --get-selections > ~/Documents/LinuxDocs/CurrentSys/ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script055.sh

---

### Post by andrei_1 on 2011-03-26
> **oldfred said:**
> I do not use Ubuntu One, but do what you suggest.

I have a rsync task. But I include running these and whenever I manually edit a system file in /etc I copy it into /home. My /home only has the hidden configuration files & some misc files as most of my data is in /data(EXT3) or /shared (NTFS) partitios which I separately backup. My /home is only about 1GB with most of that .wine (Picasa).

cp /etc/apt/sources.list ~/Documents/LinuxDocs/CurrentSys/sources.list.backup
dpkg --get-selections > ~/Documents/LinuxDocs/CurrentSys/ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script055.sh

I'm also doing this, but with Jungle Disk instead. After a reinstall I just restore most ~/.dirs and other dirs like /etc/ /var/. However, I have to be careful about this, as restoring a file I should not may render the system unusable. 

I just thought that Ubuntu might do this more safely especially for lower level settings (startup apps, installed packages, Gnome panels, firewall settings etc.)

---

### Post by Lkm on 2011-07-02
Hello, I'm relatively new, how does one go about restoring their settings from the hidden folders in home?
I have a backup copy of my home folder on a separate partition, can I use this to restore my settings on a fresh install?

---

### Post by andrei_1 on 2011-07-02
> **Lkm said:**
> Hello, I'm relatively new, how does one go about restoring their settings from the hidden folders in home?
I have a backup copy of my home folder on a separate partition, can I use this to restore my settings on a fresh install?

Use a file manager to just drag them from the backup location to your home dir (from the command line it might be trickier for newbies because * globbing will not match hidden - starting with a dot - files).

To be safer, you could use rsync -ax /home/myuser/ /my/backup/dir/ (to backup). You can figure out I guess the command to restore. cp also has a parameter to preserve attributes though I'd recommend rsync.

---

### Post by duanedesign on 2011-07-06
> **andrei_1 said:**
> It would be great if the Ubuntu One integration with the Ubuntu operating system could be enhanced so that ultimately one could restore an OS almost entirely.

This is useful when changing your computer or after restoring after a hard drive crash etc.

I'm thinking it could back up things like:

* General OS settings (appearance, themes, panels etc.)

* The packages installed (later a tool could apt-get install those on the new system)

* The application settings (things like ~/.wine/, ~/.audacity, ~/.amule etc.) because really, almost all Linux programs are "portable" by default

Your thoughts?

I have built an application that backs up your dot config files using Ubuntu One/CouchDB. It also saves a list of installed applications. The project is called[ Stipple]("https://launchpad.net/stipple"). I have not made a deb file yet but you can download the source and run the app with the command: 

```
python main.py

```

---

