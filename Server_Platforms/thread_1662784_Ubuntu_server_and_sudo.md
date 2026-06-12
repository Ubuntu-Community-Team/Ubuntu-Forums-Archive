---
title: "Ubuntu server and sudo"
date: 2011-01-08
forum: Server Platforms
---

### Post by pmatos on 2011-01-08
Hi,

I am trying to get a user backuppc on a ubuntu server installation to be able to backup everything using tar. So I added to my sudoers file:
```
root    ALL=(ALL) ALL
backuppc ALL=(root) NOPASSWD:/bin/tar
```

However, when I try to backup /home with tar using backuppc I get permission denied:
```
$ sudo -u backuppc /bin/tar cvf /tmp/pmatos.tar /home
/bin/tar: Removing leading `/' from member names
/home/
/home/pmatos/
/bin/tar: /home/pmatos/.bash_history: Cannot open: Permission denied
/bin/tar: /home/pmatos/.lesshst: Cannot open: Permission denied
/home/pmatos/.emacs.d/
/bin/tar: /home/pmatos/.emacs.d/auto-save-list: Cannot open: Permission denied
/home/pmatos/.sudo_as_admin_successful
/bin/tar: /home/pmatos/.rnd: Cannot open: Permission denied
/bin/tar: /home/pmatos/.cache: Cannot open: Permission denied
/home/pmatos/.bash_logout
/bin/tar: /home/pmatos/.ssh: Cannot open: Permission denied
/home/pmatos/.profile
/bin/tar: /home/pmatos/Maildir: Cannot open: Permission denied
/home/pmatos/.bashrc
/bin/tar: /home/pmatos/.nano_history: Cannot open: Permission denied
/bin/tar: Exiting with failure status due to previous errors
```


Any ideas on why this happens?

---

### Post by RedSingularity on 2011-01-08
I wonder what the file permissions are in ~/home

Try this:

ls -al /home/pmatos

Post the output here.

---

### Post by pmatos on 2011-01-09
> **RedSingularity said:**
> I wonder what the file permissions are in ~/home

Try this:

ls -al /home/pmatos

Post the output here.

Hi,

```
pmatos@zeus:~$ ls -la /home/pmatos
total 60
drwxr-xr-x 6 pmatos pmatos  4096 2011-01-07 14:59 .
drwxr-xr-x 3 root   root    4096 2010-12-27 11:41 ..
-rw------- 1 pmatos pmatos 10178 2011-01-09 00:26 .bash_history
-rw-r--r-- 1 pmatos pmatos   220 2010-12-27 11:41 .bash_logout
-rw-r--r-- 1 pmatos pmatos  3103 2010-12-27 11:41 .bashrc
drwx------ 2 pmatos pmatos  4096 2010-12-27 11:42 .cache
drwxr-xr-x 3 pmatos pmatos  4096 2011-01-06 15:14 .emacs.d
-rw------- 1 pmatos pmatos    43 2011-01-07 02:17 .lesshst
drwx------ 9 pmatos pmatos  4096 2011-01-08 20:51 Maildir
-rw------- 1 pmatos pmatos     6 2011-01-08 22:14 .nano_history
-rw-r--r-- 1 pmatos pmatos   675 2010-12-27 11:41 .profile
-rw------- 1 pmatos pmatos  1024 2010-12-29 11:13 .rnd
drwx------ 2 pmatos pmatos  4096 2010-12-28 19:09 .ssh
-rw-r--r-- 1 pmatos pmatos     0 2010-12-27 16:06 .sudo_as_admin_successful
```

The strangest thing is that if I use sudo -u root for the tar instead of sudo -u backuppc it does work.

---

### Post by truant on 2011-01-09
backuppc doesn't have access to the photos directory, but root will do because root always has access.

Add backupppc to the group 'pmatos' and you should be fine.

```
sudo adduser backupppc pmatos
```

---

### Post by pmatos on 2011-01-09
> **truant said:**
> backuppc doesn't have access to the photos directory, but root will do because root always has access.

Add backupppc to the group 'pmatos' and you should be fine.

```
sudo adduser backupppc pmatos
```


Which photos directory, I have no photos directory. Moreover, the whole point was to do this with sudo through the sudoers file by allowing backuppc act as root when using /bin/tar. I don't want to add backuppc to the group 'pmatos' cause then I will hit the same problem on /home/jen where all files are jen:jen and so on and so forth for other users...

---

### Post by RedSingularity on 2011-01-09
Try this:

sudo chmod -R 744 /home/pmatos

Then try using the backuppc command again.

---

### Post by CharlesA on 2011-01-09
> **RedSingularity said:**
> Try this:

sudo chmod -R 744 /home/pmatos

Then try using the backuppc command again.

Be careful doing chown/chmod recursively (-R) as there are some files that need to have specific permissions - even in your home directory.

---

### Post by pmatos on 2011-01-09
> **CharlesA said:**
> Be careful doing chown/chmod recursively (-R) as there are some files that need to have specific permissions - even in your home directory.


Even so 744 doesn't work. 755 does but forces me to chmod/chown which is not so good. I can't understand why backuppc given that it acts as root (through sudoers file config) with /bin/tar doesn't work.

---

### Post by CharlesA on 2011-01-09
backuppc isn't the same as "root" you'd need to have it added to the group "pmatos" and change permissions to give read access to the group for it to be able to back up your stuff.

I do backups differently - I use a rsync script in a root crontab. I suppose a tar script would work the same way, but I am not sure as I don't really use tar all that much.

EDIT: I can run my rsync script manually by running it with sudo:

```
sudo ./backup.sh
```

---

### Post by truant on 2011-01-09
> **pmatos said:**
> Which photos directory, I have no photos directory. Moreover, the whole point was to do this with sudo through the sudoers file by allowing backuppc act as root when using /bin/tar. I don't want to add backuppc to the group 'pmatos' cause then I will hit the same problem on /home/jen where all files are jen:jen and so on and so forth for other users...

Sorry, not sure where I got 'photos' from.  :confused:

I didn't realise there were other users involved.

Several solutions I can see: 

- run your backup script as root instead

- add all your users to a group such as 'staff' and add backuppc to that too.

- As mentioned above, sudo your backup script so the whole thing runs as root, not just the tar bit of it.

---

### Post by RedSingularity on 2011-01-09
> **CharlesA said:**
>  I use a rsync script in a root crontab.


Same here  :)

---

### Post by koenn on 2011-01-09
> **pmatos said:**
> ... the whole point was to do this with sudo through the sudoers file by allowing backuppc act as root when using /bin/tar. ....
AFAIK, there's nothing in your script or in your sudoers file that makes the tar command run with root privileges :

- your script says "switch user to baccuppc and run /bin/tar"
- your sudoers file says that "backuppc" would _be allowed to_ switch user to root and run /bin/tar"
but there is nothing there that makes that "switch user to root" actually happen  -  and *backuppc* has insufficient access rights to tar your files 



although I could be wrong, I've never seen a sudoers file in my life and am going by what I can understand from the man page.



----
EDIT:

Apart from that, I agree with the others here: leave those sudo commands out of your script and run the entire script as root (via sudo) or from a root crontab.
Alternatively, give the backuppc account sufficient access rights (eg through groups)

---

