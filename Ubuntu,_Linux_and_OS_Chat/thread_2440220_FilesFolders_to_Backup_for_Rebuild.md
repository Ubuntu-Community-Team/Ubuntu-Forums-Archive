---
title: "Files/Folders to Backup for Rebuild"
date: 2020-04-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2020-04-07
Just had to re-install 18.04 - which is a shame because 20.04 is coming up.  Re-install not too bad because I have separate / and /home.  What files/folders, or info saved, is advised to get the re-build as close as possible to the original in terms of installed apps and configs over and above the standard install?  I guess this is also a backup question as well.

---

### Post by oldfred on 2020-04-07
If a standard desktop user /home.
You can export a list of installed apps and restore those apps.
If you edit system configuration, those would be in /etc. I edit grub config, but just copy that into /home so that backup includes it.
Then if you have installed any server type apps, web, data base, etc those would normally be in / (root) but a server admin should know how to back those up.

If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[https://ubuntuforums.org/showthread.php?t=2311501](https://ubuntuforums.org/showthread.php?t=2311501)
[https://ubuntuforums.org/showthread.php?t=2419993](https://ubuntuforums.org/showthread.php?t=2419993)

I am just a retired desktop user. And do not follow TheFu's very good recommendations. But use rsync to copy to second drive, rsync to copy to multiple flash drives, copy most critical data to DVD(s) periodically and sneakernet my data from two total different locations several times a year. Planning on converting some of my backup from rsync  to rdiff.

Sample rdiff file by TheFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
Summary report from rdiff & use variables, example
[https://ubuntuforums.org/showthread.php?t=2422831](https://ubuntuforums.org/showthread.php?t=2422831)
[http://rdiff-backup.nongnu.org/examples.html](http://rdiff-backup.nongnu.org/examples.html)

Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) & 
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

### Post by Quarkrad on 2020-04-07
Wow - thank you; a very comprehensive answer.  I too am looking at moving from rsync to rdiff - it seems easy at first but the devil is in the detail!

---

