---
title: "Switching to CentOS"
date: 2012-07-09
forum: Server Platforms
---

### Post by bbqroast on 2012-07-09
Hey, some issues regarding encryption and the JVM on Ubuntu has resulted in me deciding to switch to CentOS. I'm running Ubuntu Server 11.

How do you recommend I make the switch, I have the following things set up:
Minecraft Server.
MySQL.
Apache + PHP.
And want to preserve the data from all of them? Is there a way I can make a complete backup of my Ubuntu install onto my TB hard disk (I have physical access to the server).

Alternatively if someone can tell me a really easy way of decrypting my home folder then I might stay (or to create a new user with a decrypted user DIR), the JVM issues are almost livable- not being able to access the hard disk when I am not online has caused many more issues for MC (not entirely Ubuntu's fault, MC has crappy code- nothing I can do about it sadly).

---

### Post by SeijiSensei on 2012-07-10
A few things about CentOS:

Apache/PHP configuration is a bit different.  RedHat/CentOS do not use the sites-available/sites-enabled approach of Debian/Ubuntu.  The default web directory is /var/www/html.

As for migrating MySQL, I strongly recommend using mysqldump to make a plain-text dump of all your databases.  Trying to migrate the binary image in /var/lib/mysql can work in some cases, but a plain-text dump will always work.

Perhaps you should consider migrating to [Debian]("http://www.debian.org/") rather than CentOS since Ubuntu is based on the former with similar filesystem organization.

To make a complete filesystem backup, use rsync.  Create an empty mount point with "sudo mkdir /mnt/temp", then mount the external to that location.  Now run rsync like this:

```

cd /
sudo rsync -a . /mnt/temp --exclude=proc/ --exclude=sys/ --exclude=mnt/temp

```

The first two exclusions concern transient filesystems like /proc that are created anew by the kernel on each boot.  Exclude /mnt/temp to avoid backing up the backup.

If you want to watch the backup take place use "-av" instead of just "-a".  In "verbose" mode rsync displays a list of all the files it's transferring on the terminal.

---

### Post by LHammonds on 2012-07-10
Why do you have anything touching the home directory?
 
I have a Minecraft (Craftbukkit) server setup on an Ubuntu server and it works perfectly. I have Java and CraftBukkit installed and running under /opt
 
Not sure it would be helpful but here is [my thread on how to setup a Minecraft server]("http://forums.bukkit.org/threads/how-to-setup-a-custom-craftbukkit-server-1-2-5-r1-0.69825/").  It mentions setting up a 10.04 server but I am running it on 12.04 now with no problems.
 
LHammonds

---

### Post by bbqroast on 2012-07-10
So let me get this clear? I've selected some option dure in the install process to encrypt something (most likely my user DIR). If I run my server in the "/opt/" directory it won't be encrypted? That's great news!

I'll try it out :).

Also, I probably won't use CentOS for now. I decided to use it on recommendation from numerous people, but Ubuntu looks a lot simpler and I have far more experience using it. I'm copying everything to /opt/ now. It takes a while, a couple of GB of backups. I probably won't use RAMDisk, Anvil kind of cut out the need for it (and I don't have a lot of RAM anyway).

Damn, didn't work. The second I logged out the online map/backup stopped working (and spewed IO errors).

---

### Post by LHammonds on 2012-07-11
> **bbqroast said:**
> So let me get this clear? I've selected some option dure in the install process to encrypt something (most likely my user DIR). If I run my server in the "/opt/" directory it won't be encrypted? That's great news!

Yes, the home directory can be encrypted and should not affect (encrypt) files outside the home folders.  However, I am not sure if you can simply copy/move files already encrypted in the home folder to someplace outside the home folder.  I have not done that.
 
> **bbqroast said:**
> I'm copying everything to /opt/ now. It takes a while, a couple of GB of backups. I probably won't use RAMDisk, Anvil kind of cut out the need for it (and I don't have a lot of RAM anyway).
 
Damn, didn't work. The second I logged out the online map/backup stopped working (and spewed IO errors).
Simply moving folders may not work.  There may be references to running it from the original home folder location.
 
What I would do would be to uninstall Java from home, and re-install it to the /opt folder.  Then install a fresh copy of craftbukkit (the version you are using) into /opt and make sure a base install will work.  If it works, backup this installation as a base install.  Then start the process of restoring your files to the new area.
 
LHammonds

---

### Post by bbqroast on 2012-07-11
> **LHammonds said:**
> Yes, the home directory can be encrypted and should not affect (encrypt) files outside the home folders.  However, I am not sure if you can simply copy/move files already encrypted in the home folder to someplace outside the home folder.  I have not done that.
 

Simply moving folders may not work.  There may be references to running it from the original home folder location.
 
What I would do would be to uninstall Java from home, and re-install it to the /opt folder.  Then install a fresh copy of craftbukkit (the version you are using) into /opt and make sure a base install will work.  If it works, backup this installation as a base install.  Then start the process of restoring your files to the new area.
 
LHammonds
Seeing as I'm upgrading to LTS 12, I might as well just do a reinstall. I'll install Java in the /opt dir this time as well. Following your tutorial to the letter :).

---

### Post by bbqroast on 2012-08-03
Did just that, it all works great now.

---

### Post by LHammonds on 2012-08-04
> **bbqroast said:**
> Did just that, it all works great now.
Congrats.  I'm waiting for a CraftBukkit version to be released that supports 1.3.1 before I upgrade my client...even then, I probably will wait a bit longer until all my favorite CB mods have been updated to work with the new system.

Version 1.3.1 is a major overhaul and will take time for everyone to make updates/changes for it.

LHammonds

---

