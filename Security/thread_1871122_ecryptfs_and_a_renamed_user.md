---
title: "ecryptfs and a renamed user"
date: 2011-10-28
forum: Security
---

### Post by cong06 on 2011-10-28
I'm in over my head.

My primary user for my desktop had an encrypted home folder (still does I hope):
/home/name/

I decided to rename the user:
```
usermod -l newname name
usermod -m -d /home/newname name
```
Now it has the new folder.
Unfortunately mounting didn't work at first. I had some issues with the symlinks that ecrypt wanted, being in the right location. I've fixed all that now though:
```

newname@pogo:~$ ls -al .
lrwxrwxrwx  1 newname name   56 2011-10-28 10:52 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
lrwxrwxrwx  1 newname name   39 2011-10-28 10:51 .ecryptfs -> /home/.ecryptfs/newname/.ecryptfs/
lrwxrwxrwx  1 newname name   38 2011-10-28 10:52 .Private -> /home/.ecryptfs/newname/.Private/
lrwxrwxrwx  1 newname name   52 2011-10-28 10:52 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt

```
Now whenever I run:
```

newname@pogo:~$ ecryptfs-mount-private 
Enter your login passphrase:
Inserted auth tok with sig [secret] into the user session keyring
Cannot chdir into mountpoint.

```

However I'm able to unlock it. If I run "ecryptfs-recover-private":
```
newname@pogo:~$ sudo su -
[sudo] password for newname: 
root@pogo:~# ecryptfs-recover-private 
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/home/.ecryptfs/newname/.Private].
Try to recover this directory? [Y/n]: 
INFO: Enter your LOGIN passphrase...
Passphrase: 
Inserted auth tok with sig [ac4c027fa81efcae] into the user session keyring
INFO: Success!  Private data mounted read-only at [/tmp/ecryptfs.IJ0U9nL7/private].
root@pogo:~# ls -al /tmp/ecryptfs.IJ0U9nL7/private/
total 14368
drwxr-xr-x 47 newname name    16384 2011-10-27 16:58 .
drwx------  3 root         root      4096 2011-10-28 11:15 ..
drwx------  3 newname name     4096 2011-09-07 09:00 .adobe
drwx------  2 newname name     4096 2011-10-26 10:10 .aptitude
-rw-------  1 newname name    10244 2011-10-28 09:42 .bash_history
-rw-r--r--  1 newname name      220 2011-09-06 15:30 .bash_logout
-rw-r--r--  1 newname name     4584 2011-10-27 15:15 .bashrc
-rw-r--r--  1 newname name     4587 2011-10-19 10:41 .bashrc~
-rw-r--r--  1 newname name     3349 2011-09-06 16:47 .bashrc.org
drwxr-xr-x  3 newname name     4096 2011-10-26 09:43 bin
drwx------ 15 newname name     4096 2011-10-26 09:09 .cache

```
So as you can see, it's being decrypted.

Does anyone know what the error means "Cannot chdir into mountpoint."? There's no documentation online about this at all. I have all the proper permissions...

---

### Post by kmolnar on 2011-11-18
I have this exact problem, right down to the solution steps I attempted. =)
And absolutely no idea why it's not working. =(

I've recovered partially like so:
```

# ecryptfs-recover-private
# mv /home/username /home/usernameOLD
# mkdir /home/username
# rsync -avR /tmp/ecryptfs.XXXXXXXX /home/username

```

But this leaves me with an unencrypted home directory, which is not exactly ideal.

---

### Post by kmolnar on 2011-11-18
Although I should point out that in addition to changing the user name and home directory, you'll want to use groupmod unless you're intentionally leaving the group name alone, so that it matches the username.

---

### Post by cong06 on 2011-11-18
Oh, I'm sorry. I should have replied to this.

I forgot to write my fix immediately, but it had to do with the files in the folder:
/home/.ecryptfs/user/.ecryptfs/

```

$ cat /home/.ecryptfs/user/.ecryptfs/Private.mnt
/home/user

```
Make sure that that file is pointing to the correct folder. If it isn't you'll have to open it (gedit, you know the drill)

I think that's all I had forgotten...

If that doesn't fix it, let me know and I'll scan over my config at work on Monday.

---

### Post by kmolnar on 2011-11-19
Thank you! Editing that file fixed the problem. This should go into the HowTo on moving user homes around.

---

