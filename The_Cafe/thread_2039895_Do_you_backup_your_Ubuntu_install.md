---
title: "Do you backup your Ubuntu install?"
date: 2012-08-09
forum: The Cafe
---

### Post by JF382 on 2012-08-09
Do you backup your Ubuntu install? If so, how often, and what program do you use? I am looking to backup all the software, documents, themes/icons, etc so that if I ever need to re-install Ubuntu I can just get them all back very easily. Is this possible? Thanks.

---

### Post by vexorian on 2012-08-09
Yes, it is possible. Ubuntu comes with a backup app by default. It is called "deja" something, so just type "deja" in some app finder and it should find it.

You can also use more advanced tools. But since you just want to backup files and themes, I think this app is good enough.

It already backs up your home which includes your settings and documents. To backup your themes you would have to include the /usr/share/themes and /user/share/icons folders.

---

### Post by linktopower on 2012-08-09
I use APTonCD (For making a backup all the program packages I've gotten) You can find it in the Ubuntu software center, And for documents and stuff I just copy them to a flash card.

---

### Post by phrak on 2012-08-09
rsync hourly backups to an off site (located at a friends house) backup.   I host a server for him to do the same.

---

### Post by oldfred on 2012-08-09
Some like image backups, some like to backup their own data. It also depends on data value. A business has a lot of valuable data and must be backed up more often. I am a home user but some data like photos & some documents are more valuable. Those I can regenerate fairly easily in the short term, so I only copy those to a DVD every quarter or less. I run rsync for that data plus some other data to another drive more frequently.

discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

[http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[http://backintime.le-web.org/](http://backintime.le-web.org/)
[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)
[http://flyback-project.org/](http://flyback-project.org/)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

If you don't mind the command line, you can use duplicity.
If you DO mind the command line, there is a front end for duplicity; deja-dup.

Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

I posted what I back up with rsync, so I can easily reinstall.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by jonnyboysmithy on 2012-08-10
I usually backup about once or twice a month..
I just use luckybackup (front end for rsync) to copy my homefolder, but before that I get it to execute this script:
```
dd if=/dev/zero of=/tmp/disk_zero_fill.tmp bs=8M; rm -f /tmp/disk_zero_fill.tmp

# set date variable
tdy=`date +%d-%m-%Y`

gksudo dd bs=15M if=/dev/sda5 conv=sync,noerror | gzip -9 > /home/username/.System-Root-Partition-Image$tdy.img.gz
```
Works sweet as. :D

---

### Post by Primefalcon on 2012-08-10
just my home via tar and gzip

---

### Post by standingwave on 2012-08-10
> **JF382 said:**
> Do you backup your Ubuntu install? If so, how often, and what program do you use? I am looking to backup all the software, documents, themes/icons, etc so that if I ever need to re-install Ubuntu I can just get them all back very easily. Is this possible? Thanks.

No, just my home folder via rsync. My philosophy is that up-time isn't that much of a concern to me and if things got completely FUBARed I would just take the time (opportunity?) to perform a clean install. The important thing is that my data is safe.

---

### Post by jonnyboysmithy on 2012-08-10
For me its important to have both my homefolder and my system partition backed up. I have dual graphics on this system thats a pain to set up, cheers ATI you make awesome drivers .:-&
I hear the newer drivers are better, but I think I'll leave it as is I don't wanna fix it till its broke. ;)

---

### Post by Paqman on 2012-08-10
> **standingwave said:**
> No, just my home folder via rsync. My philosophy is that up-time isn't that much of a concern to me and if things got completely FUBARed I would just take the time (opportunity?) to perform a clean install. The important thing is that my data is safe.

100%. Don't see any point backing up anything outside /home. I just dropped a little wee script into /etc/cron.daily that rsyncs /home to my NAS, then I'm covered by the NAS's backup routine. Job done.

---

### Post by Jakin on 2012-08-10
I always backup HOME directory, to a thumbdrive, and it also goes into Ubuntu One. I delete the backups every month- and make a new one. 
I started doing this a long time ago, because i cannot think of a single time when i used apt-upgrade to a new version of Ubuntu, that it all went without a hitch, the system would always be very buggy (this is my experience). So i backup, that way anytime i choose to upgrade- its a clean install.

---

### Post by rewyllys on 2012-08-10
I use LuckyBackup nightly to back up my /home directory to an external hard drive connected to my desktop.

Also, I use CrashPlan to maintain a running backup of my /home directory and a couple of other important-to-me directories, all to CrashPlan's cloud storage.  

My wife's Windows desktop is backed up nightly to an external hard drive connected to her desktop.  Her desktop's C: drive is backed up continually to CrashPlan's cloud.

---

### Post by mips on 2012-08-10
I only really backup /var/cache/apt

My data is obviously backed up.

---

### Post by vexorian on 2012-08-10
^ I just wish they incorporated delta patching already.

---

### Post by cariboo on 2012-08-10
I also don't see the point in backing up your whole install. If your worried about duplicating your install use a script to list all the installed packages, or use [OneConf]("https://wiki.ubuntu.com/OneConf"), available through the Software Centre and Ubuntu-One.

To list all installed packages, run the following command in a terminal:

```
sudo dpkg --get-selections > ~/Desktop/packages
```

to install the package on a new installation:

```
sudo dpkg --set-selections < ~/Desktop/packages && sudo apt-get -u dselect-upgrade
```

---

### Post by nerdopolis on 2012-08-10
I use a script I made  to rsync to a btrfs subvolume I created on an external drive. 
After rsync completes it takes a btrfs snapshot of the subvolume for rollback.

---

### Post by BrokenKingpin on 2012-08-10
I do not backup my Ubuntu install. I store all data (documents, media files, etc.) on my home server. The data on the server is backed up though. This way I store no important data on any of my PCs, so I can reload the OS at any point without having to backup anything.

For reinstalling the OS (usually Xubuntu) I have a bash script that sets up all my applications and configures most things for me automatically. It takes me no more than 15 minutes to get all my apps installed and the OS configured the way I like it.

---

### Post by sammiev on 2012-08-10
I do a full backup every week or two to a USB HD. Only take a few min. :)

---

### Post by mips on 2012-08-11
> **vexorian said:**
> ^ I just wish they incorporated delta patching already.

Same here. Fedora is calling me with their delta rpm's.

---

### Post by Redache on 2012-08-11
I use Deja Dup to backup to Ubuntu One as the only data I have that I don't have backed up elsewhere is config/document data specific to my Ubuntu install. I keep important things like .bash* files in my Dropbox folder so I can easily copy them to new installs.

---

### Post by Easy Limits on 2012-08-11
I just back up my mail inbox and bookmarks.  Everything else is stored on a separate hard drive so if the OS crashes nothing is lost.

---

### Post by gladgrind on 2012-10-05
I run a script that runs rsync each night to back up my home directory. 

Once a week or so I run clonezilla to make an image. It takes only about 5 minutes to back up the OS - about 9 gb of the hard drive is used.

---

### Post by litiform on 2012-10-12
no. but I did create a written manual on how to configure it the same way should I need to reinstall.

---

