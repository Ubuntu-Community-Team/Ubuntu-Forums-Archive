---
title: "Ok to have obm running as root?"
date: 2008-06-08
forum: Server Platforms
---

### Post by SumnerBoy on 2008-06-08
Hi - I am running obm to manage my offsite backups to PerfectBackup.co.uk. It is currently being run as a cron job (daily) as root and all the configuration files are in /root/.obm.

I am trying to tidy up my server and improve security etc and thought obm should really be running as something other than root. Has anyone tried/done this or have any suggestions?

I have taken the first step and moved the config and log files to /var/local/obm and updated the RunBackupSet.sh to point to this location (instead of /root/.obm).

I have still got the cron job running as root and just noticed that a /.obm/ipc folder was still created in /root. Any ideas how to stop this happening?

I am newish to Linux - is it SOP to run backup type scripts as root - in order to have sufficient access to your files for the backup process? Or should I change the job to run as a low-privilege user in order to maintain security?

Any help or tips more than welcome!

---

### Post by abhiroopb on 2008-06-08
I use obm as well, I actually couldn't figure out how to get cron to run it. Lets say I want to do an offsite backup daily automatically. Right now even if I set up a schedule in the OBM nothing happens unless I run it at the right time.

Could you please explain how to set up an automatic schedule to backup.

---

### Post by SumnerBoy on 2008-06-08
I just create a cron job to run daily at 3am. You just call RunBackupSet.sh and pass in the backup set name as the first command line parameter.

[CODE]sh /usr/local/obm/bin/RunBackupSet.sh tui > /dev/null/[CODE] 

As I stated in my OP - I am currently running this task as root.

---

### Post by thanh_hien73 on 2009-01-19
> **SumnerBoy said:**
> I just create a cron job to run daily at 3am. You just call RunBackupSet.sh and pass in the backup set name as the first command line parameter.

[CODE]sh /usr/local/obm/bin/RunBackupSet.sh tui > /dev/null/[CODE] 

As I stated in my OP - I am currently running this task as root.
I just how to install OBM. I installed in but still not running. when i put the address it error:
Database error: cannot use database obm
MySQL Error: 1049 (Unknown database 'obm')
Session halted.
help me.

---

### Post by thanh_hien73 on 2009-01-19
OBM you are not running? I installed that is not forever. How do I remove everything about OBM, I remove it but still

---

