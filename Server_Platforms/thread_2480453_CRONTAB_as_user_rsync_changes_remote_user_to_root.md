---
title: "CRONTAB as user rsync changes remote user to root"
date: 2022-10-30
forum: Server Platforms
---

### Post by volkswagner on 2022-10-30
I'm not sure how to word the title. 

My google foo hasn't yielded any explanation.

I'm trying to "pull" a backup from a remote server.

On the server running the script, I created a script file (/bak/scripts/fusionbak):
```
rsync -arq -e "ssh -i /home/eric/.ssh/id_rsa" eric@pbx:/var/backups/fusionpbx/postgresql /bak/kvm/vmdata/fusionpbx/
```

I first tried it without "ssh -i /home/eric/.ssh/id_rsa". I added that because I thought perhaps when cron was running it was looking
for the id_rsa in /root/.ssh.

On the server pulling the backups, as user=eric I ran:
```
crontab -e
```

And added the following:
```
55 12 * * * /bak/scripts/fusionpbx
```

I can run the script as eric without sudo privileges (the backup works).

When it runs during cron I see the following in the remote server's auth.log:
```
Oct 30 12:55:01 fusionPBX CRON[16202]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 30 12:55:01 fusionPBX CRON[16202]: pam_unix(cron:session): session closed for user root

```

Why isn't an underprivileged user's cron jobs running as that user, and even though I have
specified the remote user@server in the script, why is it attempting to login as root?

Thanks in advance!

---

### Post by TheFu on 2022-10-30
Backups of files that aren't for a single user need to use root/sudo on both sides.  That means you should take steps to ensure that the "pulling" side runs as root, uses ssh-keys for that root account to connect to the remote system ... as root or root-equiv (preferred), then the rsync on the remote system runs as root.

The easy test of this without rsync is to see if
```
sudo root-equiv@remote ls /root/
```
works.  If it doesn't, then the ssh connectivity isn't setup correctly.  Use the ~/.ssh/config file to make this easier so you don't have to clutter up the command line.  Just use a different 'host' for the root-equiv connection information than the normal user account uses.

If you are going through this trouble, why not use a better backup tool that captures file metadata changes over time too?  rsync doesn't do that.  Only the last permissions/acls, user, group are retained.

If it isn't clear, the crontab used should be the local root-equiv or root account on the system doing the "pull", so that files are stored with the correct uid/gid information.  Using any other account will make the file owner the current user, which isn't likely very useful.  

The data inside the files is only 50% of what we need in a backup.

---

### Post by volkswagner on 2022-10-30
Thanks for your reply TheFu.

I think my question remains, "why is a user's crontab, trying to connect to the remote server as root".
The cron job clearly runs as the user "eric" as seen in syslog. The script that is being excecuted
specifies eric@remote. Where in the world does root get involved?

This backup job is a very small specific task. It simply copies existing .sql backups from the
remote server to the local. I can obviously push them, which may be the solution. 

I really would like to understand what I'm not learning about Crontab. 
Why in the world is root even getting involved in this scenario?

I don't want to allow root logins, nor do I want the script to require sudo privs.
Do I need to find something other than CRONTAB for the scheduling?

I can run the script as myself, crontab runs my cron jobs as me, but why is
it mangling the rsync user?

---

### Post by TheFu on 2022-10-31
Ah ... that makes much more sense.

So, some task dumps the postgres data to a text file (as the backup), then the rsync is supposed to "pull" that file from the remote system sometime later.  I hope the overall backup process honors data homogeneity requirements.  Those can really mess up a system.

Does
```
ssh  eric@pbx ls -l  /var/backups/fusionpbx/postgresql
```
Works and sees the files you wish to pull?  

rsync uses ssh by default with the ssh-keys as expected in the ssh order.
If the local username and the remote username are the same (uid doesn't matter, just the username), then there's no need to specify it.
```
ssh pbx ls -l  /var/backups/fusionpbx/postgresql
```
should work.
also, the remote userid can be checked with 
```
ssh pbx id
```

The identity file is the default, so it doesn't need to be specified.  Might be worth changing away from RSA, BTW.  In the last few years, the default order of preferred ssh-keys has changed, so it would be good to either specify the exact file you want in the ~/.ssh/config for the connection or stick with the defaults.  I'm a big user of the ~/.ssh/config file, since all ssh-based connections use it and honor the settings it has based on the 'host' specified.  As for ssh keys, we switched from RSA to ed25519 about 5 yrs ago.  This shouldn't matter, unless the RSA key length is too short and has been deprecated.

---

### Post by LHammonds on 2022-11-02
I use NFS shares on the remote servers and configure them so that only the backup server can reach in and pull the data off of it.

For sensitive data and database exports, I make sure the export script archives and encrypts the data before placing it in the NFS share for pick up so the data is protected at rest and transit.

Make sure you utilize log files in your scripts even if the only thing you record is just when it starts and completes.  It helps troubleshooting...such as the script being executed multiple times at the exact same time (such as the schedule being created under different/unexpected accounts) or just to make sure it is running when it should.   Example:

```

LogFile="/var/log/myapp.log"
printf "`date +%Y-%m-%d_%H:%M:%S` [INFO] Script started.\n" >> ${LogFile}
### Main part of your code here ###
printf "`date +%Y-%m-%d_%H:%M:%S` [INFO] Script completed.\n" >> ${LogFile}

```

Here is an example of what I did for a [backup server for 20.04]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=283").

As for managing crontab, there are a few ways to initiate schedules.  You can control them using "crontab -e -u <userid>" (which is [what I do]("https://hammondslegacy.com/forum/viewtopic.php?p=1010#p1010")) or by creating files in /etc/cron.hourly/ or /etc/cron.daily/ or /etc/cron.weekly or /etc/cron.monthly and so on.

Other considerations when using crontab is relative pathing.  The crontab environment is reduced and things such as "paths" in the shell may not exist in crontab.  So scripts that have "rsync" as a command may not work because it cannot find "rsync" in the folder where the crontab is being called from.  You should use a full path when calling the script and everything in the script....try to avoid using any relative paths to avoid that issue.  A simple workaround (which is typically frowned upon is to add the same path searching in shell to crontab.  Example:

```

#############################################################
## Name    : Crontab.root
## Author  : LHammonds
## Version : 1.2
## Date    : 2022-05-31
## Purpose : Crontab Schedule for root user
###################### CHANGE LOG ###########################
## DATE       VER WHO WHAT WAS CHANGED
## ---------- --- --- ---------------------------------------
## 2012-05-20 1.0 LTH Created schedule.
#############################################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# Crontab SYNTAX:
#       __________ Minute (0-59)
#      / _________ Hour (0-23)
#     / /  _______ Day Of Month (1-31)
#    / /  /   ____ MONth (1-12)
#   / /  /   /   _ Day Of Week (0-7) (Sun = 0 or 7)
#  / /  /   /   /  -------------------------------------------------------------
# m h dom mon dow  command <arguments> > /dev/null 2>&1
#
# Backup database server
#
#0 23 * * * /var/scripts/prod/db-backup.sh > /dev/null 2>&1

```

Having the path in the crontab file will allow the scripts to work if you do not put the full path to every command (such as rsync, printf, etc.)  But again, it is typically not recommended in best practices (but I still cheat).

EDIT: Oops, falling asleep in my chair.  Good night.

LHammonds

---

### Post by volkswagner on 2022-11-04
Thanks, LHammonds and TheFu.

Now I know why nobody could tell me why a user's crontab was executing/changing the user as root.
Well, it wasn't and it doesn't.

Looking at LHammonds one-liner in crontab made me think (why not post output to a file so
I can get more info, since syslog had next to nothing).

After writing the output to a file, I found my error... "file not found". What?!
I looked at the script path many times and never picked up on my typo.

With the correct path to the script, my cron job runs as expected.

Cheers!

---

### Post by LHammonds on 2022-11-05
> **volkswagner said:**
> With the correct path to the script, my cron job runs as expected.
Awesome!  Don't forget to edit the thread and mark as solved.

---

