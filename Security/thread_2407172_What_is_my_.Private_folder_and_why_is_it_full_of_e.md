---
title: "What is my .Private folder and why is it full of encrypted files?!"
date: 2018-11-30
forum: Security
---

### Post by goemonburo on 2018-11-30
I just found that my home dir is full and there's a folder I don't recognize:  .Private, filled with encrypted files.  Is this normal?  Have I been hacked?  If so, from what and how should I go about removing this?

I've recently upgraded to Ubuntu 18.04LTS, which was a relatively seamless joy.  Really hoping this is just some new folder option and I haven't noticed it before.

Thanks for any/all help!

---

### Post by oldfred on 2018-11-30
You have an encrypted /home. 
You should remember that is how you installed & you have to give passphrase everything you boot.

Post these:
sudo parted -l
df -h

Ubuntu, I believe has discontinued a separate encrypted /home as part of install, but it should work with upgrade.
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)
> The installer no longer offers the encrypted home option using  ecryptfs-utils. It is recommended to use full-disk encryption instead  for this release. ([1756840]("https://bugs.launchpad.net/bugs/1756840")) 
It now uses only LVM withfull drive encryption. 
Users have the option of encrypting files, folders or partitions on their own.

---

### Post by goemonburo on 2018-11-30
Okay, so the real question is that when I do df, I see that this .Private folder seems to be filling my entire home dir.

/home/myuser/.Private ....0 space left.

How do I clear/clean this so that I can use the disk?

And thank you, yes, I remember seeing something about not being able to do the encrypted home option.  If I look, it indeed is a symlink to /home/.encryptfs/myuser/.Private  

What are my options?  I really don't want to have to reinstall, gack, that would be such a pain.

---

### Post by oldfred on 2018-11-30
Have you unencrypted it and then checked size?
Otherwise you may need lots of housecleaning.

If you cannot boot:
       Includes chroot. /home encryption:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

### Post by goemonburo on 2018-11-30
I have hard rebooted fine, several times actually.  And when I reboot, it shows my hard drive home with 85 percent of dir space used.

However, now that I've left the system on a few hours, it's already (with nothing that I'm aware of running) at only 87 percent.  I normally leave the system on for days or weeks, so I can easily see that by the time I wake up tomorrow, this ".Private" directory will have filled my home dir to the point of instability and I'll be unable to use the computer until I reboot.

As far as "unencrypting" I'm not sure what you mean.  When I boot, before I can do anything else (even login) I have to unencrypt the disk.  Then it chugs through to a login screen and I log in as whichever user I choose.  Then it chugs a bit more and the desktop shows up.  When I open a terminal and "df" I see the available space on the various disks and mountpoints.  

What disturbs me is that this ".Private" folder just grows and grows.  Can I proactively delete its contents?  What is filling it with files?  Are these logs?  

I haven't lost any data, but when the /home/myuser directory is at 100 % of course things get wonky.  My worry is that SOMETHING (virus?!) is filling up this space like crazy.  I have a 3TB hard drive, so 85 percent should last me for months or years.  Instead, it's filling after a day or so.

The links you posted seem to be for when the home directory has been deleted or can't be accessed.  I can access it fine, but something's filling up my home directory with files that I don't know and don't understand.

---

### Post by oldfred on 2018-11-30
What brand/model system?
Start with a good backup of all your data.

A lot of this may be system, not user data.
       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

 Caution deborphan will delete anything you manually installed. See comment: 
     
From /home run this:
       sudo du -hc --max-depth=1 
Then change to largest folder and run again.
Keep drilling down to see if one large file or folder is issue.

Also these may show something:
      
 #check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
sudo -H nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.
sudo du -ahx / | sort -rh | head -20

---

