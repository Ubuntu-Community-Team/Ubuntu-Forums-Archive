---
title: "Cron Questions"
date: 2011-08-22
forum: Server Platforms
---

### Post by Kazuki on 2011-08-22
Im having issues getting Cron to work correctly.
I am running two scripts from /bin/ folder and trying to edit files and folders in a users home directory.

the email im getting from cron is this:

mkdir: cannot create directory `/home/travis/MCServer/backupdaily/Aug_22': No such file or directory
mkdir: cannot create directory `/home/travis/MCServer/backupdaily/Aug_22+_2': No such file or directory
mkdir: cannot create directory `/home/travis/MCServer/backupdaily/Aug_22+_nether': No such file or directory
cp: cannot stat `/home/travis/MCServer/world/*': No such file or directory
cp: cannot stat `/home/travis/MCServer/survival/*': No such file or directory
cp: cannot stat `/home/travis/MCServer/world_nether/*': No such file or directory
rm: cannot remove `/home/travis/MCServer/backupdaily/Aug_20': No such file or directory
rm: cannot remove `/home/travis/MCServer/backupdaily/Aug_20+_2': No such file or directory
rm: cannot remove `/home/travis/MCServer/backupdaily/Aug_22+_nether': No such file or directory
/bin/backupdaily.sh: 18: cannot create /home/travis/MCServer/backup.log: Directory nonexistent

I tried creating crontabs for both the User and for Root and editing the crontab in /etc/ but still get the same errors.

I am new to cron so I am probably missing something about where cron has access to and where it runs from, but if someone can give me an Idea that would be great. Also not sure if this is the right forum to post in, Sorry in advance.

---

### Post by dave01945 on 2011-08-22
just a thought but is your home folder encrypted because if it is i don't think cron will be able to decrypt it without your login first

---

### Post by Kazuki on 2011-08-22
never installed encryption on this box, and never ran any encryption command for any folders.

---

### Post by blind2314 on 2011-08-22
> **Kazuki said:**
> Im having issues getting Cron to work correctly.
I am running two scripts from /bin/ folder and trying to edit files and folders in a users home directory.

the email im getting from cron is this:

mkdir: cannot create directory `/home/travis/MCServer/backupdaily/Aug_22': No such file or directory
mkdir: cannot create directory `/home/travis/MCServer/backupdaily/Aug_22+_2': No such file or directory
mkdir: cannot create directory `/home/travis/MCServer/backupdaily/Aug_22+_nether': No such file or directory
cp: cannot stat `/home/travis/MCServer/world/*': No such file or directory
cp: cannot stat `/home/travis/MCServer/survival/*': No such file or directory
cp: cannot stat `/home/travis/MCServer/world_nether/*': No such file or directory
rm: cannot remove `/home/travis/MCServer/backupdaily/Aug_20': No such file or directory
rm: cannot remove `/home/travis/MCServer/backupdaily/Aug_20+_2': No such file or directory
rm: cannot remove `/home/travis/MCServer/backupdaily/Aug_22+_nether': No such file or directory
/bin/backupdaily.sh: 18: cannot create /home/travis/MCServer/backup.log: Directory nonexistent

I tried creating crontabs for both the User and for Root and editing the crontab in /etc/ but still get the same errors.

I am new to cron so I am probably missing something about where cron has access to and where it runs from, but if someone can give me an Idea that would be great. Also not sure if this is the right forum to post in, Sorry in advance.


Show us the script you're running.

---

### Post by Kazuki on 2011-08-22
#! /bin/sh

CDate=$(date +%b_%d)
RDate=$(date -d "-2 day" +%b_%d)

mkdir /home/travis/MCServer/backupdaily/$CDate
mkdir /home/travis/MCServer/backupdaily/$CDate+_2
mkdir /home/travis/MCServer/backupdaily/$CDate+_nether

cp -r /home/travis/MCServer/world/* /home/travis/MCServer/backupdaily/$CDate/
cp -r /home/travis/MCServer/survival/* /home/travis/MCServer/backupdaily/$CDate$
cp -r /home/travis/MCServer/world_nether/* /home/travis/MCServer/backupdaily/$C$

rm -r /home/travis/MCServer/backupdaily/$RDate
rm -r /home/travis/MCServer/backupdaily/$RDate+_2
rm -r /home/travis/MCServer/backupdaily/$CDate+_nether

echo "Daily Backup Up Successful: $(date)" >> /home/travis/MCServer/backup.log

---

### Post by Kazuki on 2011-08-22
Also the script works if I run in manually.

---

### Post by SeijiSensei on 2011-08-23
Did you create the crontab entry for user travis using "crontab -e" when logged in as travis?  That will run the script as travis who presumably has permissions in /home/travis.

The other option is running the script from /etc/crontab.  There you'll need to specify the user like this:

```
1 * * * * root sh /path/to/my/script
```

Here the script is running as root, so permissions shouldn't ever be an issue.  However the backup files will be owned by root unless you include a "chown" command at the end of the script to set their ownership to travis.

---

### Post by Kazuki on 2011-08-23
I tried running crontab -e as travis, that said same error
I tried running using /etc/crontab
with these in there
0 0 * * 1 travis /bin/minecraftbackup.sh
0 0 * * * travis /bin/backupdaily.sh

Will try to run as root though in staid of Travis, will update tomorrow when i get the email.

---

### Post by hawkmage on 2011-08-23
Are you using auto mounts for either the /home/travis of /home/travis/MCServer directory?

---

### Post by awi on 2011-08-23
Try changing the first line for: 

```
#!/bin/bash
```

or running the cron task with the command

```
bash /bin/minecraftbackup.sh
```

Cron task does not have the same environment that a regular user terminal, running with bash command, you should do it.

---

### Post by hawkmage on 2011-08-23
> **awi said:**
> Try changing the first line for: 

```
#!/bin/bash
```

or running the cron task with the command

```
bash /bin/minecraftbackup.sh
```

Cron task does not have the same environment that a regular user terminal, running with bash command, you should do it.
I don't think it has anything to do with the environment.  The script is able to find the commands and it was able to resolve the variables. 

The first errors mention that mkdir can't make the directory "Aug_22" because it can't access the the directory "/home/travis/MCServer/backupdaily/".  This indicates that it is either a permissions error or the MCServer or backup daily directory doesn't exist at the time the command is executed.   I doubt that it is a permissions issue since the script was run as root.

Then the cp commands complain that it can't stat the "/home/travis/MCServer/world/*" which would indicate either the directory is empty or the directory doesn't exist.  

Also it can not create the log file /home/travis/MCServer/backup.log because the directory doesn't exist which indicates that the "MCServer" directory isn't there when the script is run through cron.

---

### Post by awi on 2011-08-24
> **hawkmage said:**
> I don't think it has anything to do with the environment.  The script is able to find the commands and it was able to resolve the variables. 

The first errors mention that mkdir can't make the directory "Aug_22" because it can't access the the directory "/home/travis/MCServer/backupdaily/".  This indicates that it is either a permissions error or the MCServer or backup daily directory doesn't exist at the time the command is executed.   I doubt that it is a permissions issue since the script was run as root.

Then the cp commands complain that it can't stat the "/home/travis/MCServer/world/*" which would indicate either the directory is empty or the directory doesn't exist.  

Also it can not create the log file /home/travis/MCServer/backup.log because the directory doesn't exist which indicates that the "MCServer" directory isn't there when the script is run through cron.

Permissions and non existent error are different:
```
user@pc:~/bin$ mkdir /root/not-here/asd
mkdir: cannot create directory `/root/not-here/asd': Permission denied
user@pc:~/bin$ mkdir /tmp/not-here/asd
mkdir: cannot create directory `/tmp/not-here/asd': No such file or directory

```


These two lines might be the problem, It is not only environment, I've had several issues porting shell scripts from FreeBSD to linux, that were solved using bash as the interpreter

```
CDate=$(date +%b_%d)
RDate=$(date -d "-2 day" +%b_%d)

```

---

### Post by toshko3 on 2011-08-24
hawkmage :!:
I think too that the directory is a mount point for something and doesn't exist on cron execution.
But he will tell us.
Kazuki, set the cron to something like 5-10 minutes from now, to see the results faster! Don't wait and make us wait till tomorrow.

---

### Post by Kazuki on 2011-08-24
Ok update, sorry busy with work and stuff. So changing to root did not help, still gave me the same errors. Will check when I get to work today about changing the bash command, pretty sure its not mounted because the user was created with the install of ubuntu, and those folders I made with the mkdir command.

Also if I try that how would I go about that. Would I change the line in the crontab file from

* * * * * command to "Bash * * * * * command"

Or change the first line of !# to something different

Or am I running the command in terminal as "bash command" to see if it works.

Thanks again for all the info :D

---

### Post by Kazuki on 2011-08-24
travis@mcsmp:~$ bash /bin/backupdaily.sh 

Works

---

### Post by Kazuki on 2011-08-24
changed sh file to

#!/bin/bash

set to run in a little.

---

### Post by Kazuki on 2011-08-24
Changing to !#/bin/bash worked
Thanks guys

---

### Post by Kazuki on 2011-08-25
So nvm for some reason it worked when I set it from 5 min when I did it, but now when i ran at 3am this morning and yesterday it said the same thing... didnt work.

I changed the backupdaily.sh first line to the !#/bin/bash thing do i need to change the SHELL= to bash in the crontab file?

---

### Post by hawkmage on 2011-08-25
Is the /home/travis/MCServer or /home/travis/MCServer/world directory an auto mount directory?

---

### Post by Kazuki on 2011-08-26
nope

---

### Post by dave01945 on 2011-08-26
if you log in as root or another user can you get to the /home/travis/MCServer directory

---

### Post by Kazuki on 2011-08-26
Only one user and only have Sudo no root login.

--------------------------------------------------------------
travis@mcsmp:~$ ls -l
total 44
drwx------  2 travis travis  4096 2011-06-09 02:29 Mail
drwxrwxrwx  9 travis travis  4096 2011-08-14 13:25 MCServer
drwxr-xr-x  8 travis travis  4096 2011-05-16 18:48 MCServer_backup
drwxr-xr-x  3 travis travis  4096 2011-04-21 02:05 MCServerTemp
drwxr-xr-x  7 travis travis  4096 2010-10-31 12:55 MCSMP
drwxr-xr-x 68 travis travis 16384 2010-09-27 20:50 mnt
drwxr-xr-x  2 travis travis  4096 2011-07-31 16:01 temp
drwxr-xr-x  2 travis travis  4096 2011-08-02 22:40 ventsrv
--------------------------------------------------------------

Fstab:

---------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/mcsmp-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=19526510-2078-4371-91f2-05dacf3282a1 /boot           ext2    defaults     $
#/dev/mapper/mcsmp-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
-------------------------------------------------------------

/etc/crontab
-------------------------------------------------------------

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=siriuskr at gmail dot com
# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --repo$
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --repo$
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --repo$
0 0 * * 1 root /bin/minecraftbackup.sh
0 0 * * * root /bin/backupdaily.sh
#
----------------------------------------------------------------

---

### Post by dave01945 on 2011-08-26
from the looking at this line in your fstab

**/dev/mapper/cryptswap1 none swap sw 0 0**

it looks like you have an encrypted home directory most likely setup during the initial install this line indicates an encrypted swap which is only needed and setup with an encrypted home

with the encrypted home crontab will not have access to those directories while you are not logged in exactly why you are getting errors that say directory not found and why it worked previously when your was logged in

if you type this in your home directory we will be able to confirm this by looking for a specific directory

```
ls -a
```

or you can type 

```
mount|grep ecryptfs
```

hopefully this will fix your problem :)

---

### Post by SeijiSensei on 2011-08-26
```
/dev/mapper/cryptswap1 none **swap** sw 0 0
```

That's an encrypted swap area on an LVM volume.

---

### Post by dave01945 on 2011-08-26
> **SeijiSensei said:**
> 

That's an encrypted swap area on an LVM volume.

i understand that but why would the OP have an encrypted swap setup if he doesn't have an encrypted home directory and the encrypted home would explain the error messages the OP has been recieving

---

### Post by Kazuki on 2011-08-27
Thanks you :D

so it does look like its encrypted, I didnt do the initial setup of the box, did not know he encrypted the box when he did it.

travis@mcsmp:~$ ls -a
.              .ecryptfs        MCSMP           .selected_editor
..             .fontconfig      mnt             .ssh
.bash_history  .irssi           .mysql_history  .sudo_as_admin_successful
.bash_logout   Mail             .nano_history   temp
.bashrc        MCServer         .ncftp          ventsrv
.cache         MCServer_backup  .Private        .vim
.config        MCServerTemp     .profile        .viminfo
travis@mcsmp:~$

can I use this: mount|grep ecryptfs 
In the script to get it to work?

---

### Post by dave01945 on 2011-08-27
i believe the only way to make it work is to either move the files into a directory not in your home or you can disable the encrypted home but moving the files id probably the easier option

---

