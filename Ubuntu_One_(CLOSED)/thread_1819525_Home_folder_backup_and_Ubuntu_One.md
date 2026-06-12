---
title: "Home folder backup and Ubuntu One"
date: 2011-08-06
forum: Ubuntu One (CLOSED)
---

### Post by EgoGratis on 2011-08-06
Hi. Can somebody explain this to me?

> If you have uploaded files to your Ubuntu One cloud storage and are now setting up a new computer or re-installing your operating system, it's important to not copy over the following folder from a backup copy you may have saved: ~/.local/share/ubuntuone

As long as you do not copy that folder over, you are safe to setup Ubuntu One on your computer as you normally would following the setup instructions.

The danger of copying ~/.local/share/ubuntuone from a backup to your new computer and then setting up Ubuntu One is that your files will be deleted. The Ubuntu One client will look for information about your local files in ~/.local/share/ubuntuone, see that there were files on the system and see that those folders are empty. Once you setup Ubuntu One, the client will tell the server to delete all the files from the server.

[https://wiki.ubuntu.com/UbuntuOne/FAQ/SettingUpAnExistingAccount](https://wiki.ubuntu.com/UbuntuOne/FAQ/SettingUpAnExistingAccount)

So if i do Deja Dup backup of my home folder after i setup my Ubuntu One account and later after i used Ubuntu One a lot do a clean install of Ubuntu or upgrade Ubuntu to new version and restore the home folder from Deja Dup backup.

Then when i log in to my Ubuntu One account it is possible some files will be deleted on the server?

---

