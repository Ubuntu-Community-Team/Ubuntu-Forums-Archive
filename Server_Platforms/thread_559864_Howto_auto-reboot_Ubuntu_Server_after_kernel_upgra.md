---
title: "Howto auto-reboot Ubuntu Server after kernel upgrade"
date: 2007-09-25
forum: Server Platforms
---

### Post by ruibernardo on 2007-09-25
With today kernel upgrade I've search on the forum, once again, for an automatic way to restart my headless server when a kernel update occurs. Since I've not found any, I've done some homework.

Some considerations:[INDENT] * you might not want to reboot automatically after a kernel upgrade if you're very far from where the server is and it doesn't boot up again. Change the script so it sends you a mail instead of automatic reboot.
[/INDENT][INDENT] * this will only reboot the server with a kernel update. To make this work, you must have a clean /var/cache/apt/archives directory (where apt-get stores the archives it downloads and installs). If you like to keep a copy of the files you have there, copy them now. If you want to keep a copy of the future *.deb files downloads, change the scripts so they copy them to another directory before the clean-up. To clean it now run "sudo apt-get clean".
[/INDENT]This is very basic, but it was the way I've found to do this. A script is run on root crontab every day do make the update/upgrade/dist-upgrade (nothing new here). After all the APT work, it searches for any file named linux-image*.* (the new kernel deb packages). If it finds them, it calls another script that cleans the cache directory and reboots. Even if it doesn't find any linux-image*.* file, it cleans it (just to be sure that it's empty next time). Here they are:

/usr/local/bin/cron_upgrade (update/upgrade/dist-upgrade/search/clean script)

```
#/bin/bash
# Update, upgrade and dist-upgrade and check if reboot is 
required: /usr/local/bin/cron_update
# Must be exected by root or by root crontab.
/usr/bin/apt-get update
/usr/bin/apt-get upgrade
/usr/bin/apt-get dist-upgrade
/usr/bin/find /var/cache/apt/archives/linux-image* -exec /usr/local/bin/clean_and_reboot {} \;
/usr/bin/apt-get clean
```/usr/local/bin/clean_and_reboot (clean and reboot script)
```
#/bin/bash
# Clean APT cache and reboot: /usr/local/bin/clean_and_reboot
# Must be exected by root or by root crontab.
/usr/bin/apt-get clean
/sbin/reboot
```Don't forget to "chmod +x" them. Edit the root crontab:

sudo crontab -e

Call the script at the time you want (here at 07:00 every day):

```
 00 07 * * * /usr/local/bin/cron_upgrade
```Any suggestions and/or corrections are welcome :)

---

### Post by runemaste644 on 2007-11-17
Well, with kexec, rebooting is no longer necessary. I do not know how to use it correctly, though.

---

