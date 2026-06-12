---
title: "how to mount ecryptfs upon login"
date: 2011-03-08
forum: Security
---

### Post by gnopak on 2011-03-08
I need to mount ecryptfs filesystem upon login. I am aware of ecryptfs-setup-private script, but it does not automount for remote ssh logins (console logins). I followed the /usr/share/doc/ecryptfs-utils/README.gz instructions:


mkdir /home/milos/s /home/milos/.s
sudo su
mount -t ecryptfs /home/milos/.s /home/milos/s

When prompted for password by the mount line above I entered the login password for milos.

I copied the ecryptfs line from mtab into /etc/fstab adding noauto, user as options.

then, still as root, I performed
umount /home/milos/s

and as user milos, I run ecryptfs-manager utility and added the milos login password to the keyring.

Then I performed 
mount -i /home/milos/s

This worked perfectly. Then I tried  
umount /home/milos/s 
mount -i /home/milos/s

and I got mount: No such file or directory
with the following lines in /var/log/messages
Mar  8 17:14:02 prudek kernel: [64650.034640] process_request_key_err: No key
Mar  8 17:14:02 prudek kernel: [64650.034646] One or more global auth toks could not properly register; rc = [-2]

and a simple
mount  /home/milos/s
results in "Error attempting to evaluate mount options: [-22] Invalid argument"

Interestingly, I can:
mount  /home/milos/s
just fine, with the following message in /var/log/messages:
Mar  8 17:18:08 prudek kernel: [64896.251343] ecryptfs_parse_options: eCryptfs: unrecognized option [noauto]

What am I doing wrong?

---

### Post by gnopak on 2011-03-08
This is interesting: any time I run "sudo mount  /home/milos/s" I am prompted for Passphrase, and I get two questions:
Enable plaintext passthrough (y/n)
Enable filename encryption (y/n) 

Do these three prompts prevent non-interactive login? Even root cannot use "sudo mount -i /home/milos/s" ...

---

### Post by bodhi.zazen on 2011-03-08
When you log in via ssh, ls home.

There is a readme file ;)

As a user (not root and not with sudo) you run ecrypt-mount-home (or similar).

You then cd into your decrypted home directory.

---

### Post by gnopak on 2011-03-08
> **bodhi.zazen said:**
> 

You then cd into your decrypted home directory.

Actually I found that ecryptfs-setup-private works fine. I probably used it incorrectly the first time. The ~/Private directory gets automounted upon console login. So I am satisfied, but curious. In which file is the mount command that does this job? It is not in ~/.bashrc

---

### Post by bodhi.zazen on 2011-03-08
> **gnopak said:**
> Actually I found that ecryptfs-setup-private works fine. I probably used it incorrectly the first time. The ~/Private directory gets automounted upon console login. So I am satisfied, but curious. In which file is the mount command that does this job? It is not in ~/.bashrc

I am not sure, my guess would be it is in the pam modules somewhere.

---

### Post by gnopak on 2011-03-09
> **bodhi.zazen said:**
> I am not sure, my guess would be it is in the pam modules somewhere.

Thank you for your tip. dpkg -L ecryptfs-utils show only one file installed in pam, /usr/share/pam-configs/ecryptfs-utils:
Name: eCryptfs Key/Mount Management
Default: yes
Priority: 0
Auth-Type: Additional
Auth-Final:
        optional        pam_ecryptfs.so unwrap
Session-Type: Additional
Session-Final:
        optional        pam_ecryptfs.so unwrap
Password-Type: Additional
Password-Final:
        optional        pam_ecryptfs.so

Does this file provide automounting? it does not reference ecryptfs-mount-private...

---

### Post by Krissie on 2011-06-20
Hi everybody, 

I think there is a similar problem on my Ubuntu box. After upgrading to the latest Natty 11.04 version the auto-mounting of the encrypted part of my home directory does not work anymore. 

ls -la shows this 
```

total 40
drwx------ 8 kriss kriss 4096 2011-06-20 15:02 .
drwxr-xr-x 4 root  root  4096 2011-02-08 20:54 ..
lrwxrwxrwx 1 kriss kriss   56 2011-02-08 20:54 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
-rw------- 1 kriss kriss 1084 2011-06-18 00:55 .bash_history
drwx------ 2 kriss kriss 4096 2011-05-03 20:14 .cache
drwx------ 3 kriss kriss 4096 2011-05-07 00:09 .config
lrwxrwxrwx 1 kriss kriss   31 2011-02-08 20:54 .ecryptfs -> /home/.ecryptfs/kriss/.ecryptfs
drwxr-xr-x 7 kriss kriss 4096 2011-05-30 00:59 Maildir
drwx------ 3 kriss kriss 4096 2011-05-07 00:09 .pki
lrwxrwxrwx 1 kriss kriss   30 2011-02-08 20:54 .Private -> /home/.ecryptfs/kriss/.Private
lrwxrwxrwx 1 kriss kriss   52 2011-02-08 20:54 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
drwx------ 2 kriss kriss 4096 2011-02-11 19:25 .ssh
-rw-r--r-- 1 kriss kriss    0 2011-06-12 00:01 .sudo_as_admin_successful
drwx------ 2 kriss kriss 4096 2011-05-03 20:14 .unison
-rw------- 1 kriss kriss   50 2011-06-20 14:50 .Xauthority

```and the .ecryptfs directory contains the auto-mount file:
```
total 20
drwx------ 2 kriss kriss 4096 2011-02-08 20:54 .
drwxr-xr-x 4 kriss kriss 4096 2011-02-08 20:54 ..
-rw-r--r-- 1 kriss kriss    0 2011-02-08 20:54 auto-mount
-rw-r--r-- 1 kriss kriss    0 2011-02-08 20:54 auto-umount
-rw------- 1 kriss kriss   12 2011-02-08 20:54 Private.mnt
-rw------- 1 kriss kriss   34 2011-02-08 20:54 Private.sig
-rw------- 1 kriss root    48 2011-02-08 20:54 wrapped-passphrase

```If I run the command ecryptfs-mount-private manually it works nicely, but the automatic mounting on login is gone and I have no idea where to search to get it running again. Any help is very appreciated.

Kriss

---

