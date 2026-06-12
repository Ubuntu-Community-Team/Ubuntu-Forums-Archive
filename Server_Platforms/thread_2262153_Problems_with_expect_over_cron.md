---
title: "Problems with expect over cron"
date: 2015-01-23
forum: Server Platforms
---

### Post by burge84 on 2015-01-23
Hi,

first off I'm new to this forum and therefore hope im posting this in the correct place if not have patience and a moderator surely will move me.
I have googled and searched for 2 days now without finding the answer so be nice =P

OS/Dist: Ubuntu desktop 14.04 (If memory does'nt fail me)

[B]My issue

[/B]Im trying to set up a scheduled transfers of files to a SFTP-server using cron

```


#!/bin/bash


/usr/bin/expect<<EOD
set timeout 40
spawn /usr/bin/sftp sp110@10.32.1.10
expect "*password:"
send "SP110!\r"
expect "sftp>*"
send "put /home/simon/scripts/python/transmission/SP/SP_upgrade_script/startup_script/*\r"
expect "sftp>*"


send "bye\r"
EOD



```

The script works fine until i try running it over cron
I've seen this behaviour prevoiusly when using expect making me slove it in other ways.

I've had similar scripts where the bash-parts run but the expect-parts fail so the issue is only when running expect over cron

I'm placing my expect inside a bash-script as the plan is to do some manouvers after the script is run

[B]
My Crontab (BOLD is the script in question)
[/B]```
# /etc/crontab: system-wide crontab# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.


SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin


# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
35 11   * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
21 11   * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
01 1    10 * *  root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#40 12   *  * *  root    /etc/cronjobs/test.sh
40 12   *  * *  root    /etc/cronjobs/TN_Inventory_check.sh
40 12   *  * *  root    /etc/cronjobs/Ceragon_Inventory_check.sh
07  10   *  * *  root   /home/simon/scripts/bashscripts/exportupload.sh


01 0    13  * *  root    python /home/simon/scripts/python/transmission/traffic_node/diff_corr/Diff_Corr_Sthlm_RevBF.py
10 0    14  * *  root    python /home/simon/scripts/python/transmission/traffic_node/diff_corr/Diff_Corr_GBG_RevBF.py
10 0    15  * *  root    python /home/simon/scripts/python/transmission/traffic_node/diff_corr/Diff_Corr_MLM_RevBF.py
10 0    16  * *  root    python /home/simon/scripts/python/transmission/traffic_node/diff_corr/Diff_Corr_CPH_RevBF.py
10 0    17  * *  root    python /home/simon/scripts/python/transmission/traffic_node/diff_corr/Diff_Corr_Jylland_RevBF.py






#Ceragon
08  15   *  * *  root   /home/simon/scripts/bashscripts/ceragon_backup_upload.sh


#Ceragon Monthly
12  14  14  * *  root    python /home/simon/scripts/python/transmission/ceragon/configuration_backup/Ceragon_Configuration_Backup_Local_revAG.py




#SP-Scripts
*/5  *  *  * *  root    python /home/simon/scripts/python/transmission/SP/SP_upgrade_script/SP_Upgrade_script_RevAE.py
#*/1  * *  * *  root    /home/simon/scripts/python/transmission/SP/SP_upgrade_script/SP_folder_creation/SP_folder_creation_start.sh
*/1  *  *  * *  root    /home/simon/scripts/bashscripts/sp_upgrade_backup_script_moval.sh
***/1  *  *  * *  root    /home/simon/scripts/bashscripts/sp_startup_script_upload.sh**





```

Im guessing the problem is crontab not knowing the path of expect or similar but I dont know how to fix it.

---

### Post by ian-weisser on 2015-01-23
If it's cron not knowing the full path of expect, then use the full path of expect in your script.

Personally, I would use ssh keys for an automated system instead of expect. I don't want scripts broadcasting my password all over.

Hmmm. That's not your crontab. That is root's crontab. One presumes that you have good reason for all those root jobs.
A simple FTP upload, for example, of a user-level file should be done as a user, not as root.
A good practice for picky people (like me) is to move custom root cron jobs to a separate /etc/cron.d/ file, and user jobs to their user crontab.

---

### Post by Lars Noodén on 2015-01-23
sftp also works with keys and in an automated batch mode.  The [-b option](http://manpages.ubuntu.com/manpages/trusty/en/man1/sftp.1.html) allows batch mode and is how it can be automated.  You can read from stdin like below, or else set up a separate file with the batch commands.

```

echo 'put /home/simon/scripts/python/transmission/SP/SP_upgrade_script/startup_script/*' | sftp -b - -i /home/simon/.ssh/key_sp110_rsa sp110@10.32.1.10

```

You can also read batch commands from a file.

If you would like to lock it down further, which might be a good idea, then you can modify the public key over on sp110@10.32.1.10 to only work with SFTP by prepending it with a forced command:

```

command="internal-sftp" ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC9Qlg...

```

Though, *authorized_keys* ought to be set up read-only for that user in that case.  That's easy but a few more steps.

---

### Post by SeijiSensei on 2015-01-23
I suggest using rsync for this task rather than SFTP.  It uses ssh as its shell, so all the transfers are encrypted.  It's also very easy to script.  A command like:
```

cd /; rsync -av . /path/to/backup/directory

```
is really all you need to back up the entire filesystem.  After the initial transfer, rsync will only copy over new or changed files.

---

