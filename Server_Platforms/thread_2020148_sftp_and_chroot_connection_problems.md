---
title: "sftp and chroot connection problems"
date: 2012-07-07
forum: Server Platforms
---

### Post by silbro on 2012-07-07
Hi everybody

I have a ubuntu 10.04.4 server running. What I wanted to do is give sftp access to /var/www/[user] so people can upload websites.

This is what I did:

1) create userx and set his home directory to /var/www/userx
2) add userx to www-data group and set that as his main group
3) I edited sshd:

```
Subsystem sftp internal-sftp

Match User userx
        ChrootDirectory %h
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```
4) the rights of the directories:

```
drwxr-xr-x  4 root     root     4096 2012-07-07 23:35 userx/

drwxrwxr-x 2 userx      www-data 4096 2012-07-07 23:22 upload/
```

When I try to connect it outputs the following error:
```

Write failed: Broken pipe
Couldn't read packet: Connection reset by peer
```

If I comment out the code written at 4) it works but the user has access or at least sees all directories.

what am I doing wrong ?

thanks for all hints :)

(this is one of many tutorials I followed [http://www.thegeekstuff.com/2012/03/chroot-sftp-setup/](http://www.thegeekstuff.com/2012/03/chroot-sftp-setup/) )

---

### Post by silbro on 2012-07-08
Ok so I just solved this problem. I guess the booze yesterday didn't help at all :)) the problem was that the directories 

```
/var 
/var/www 

```
were also needed to be owned by the user root and have the permissions 755

so I did:

```
sudo chown root:root /var /var/www
sudo chmod 755 /var /var/www
```

and it works.... so basically it's all folders above the "isolated" one that need to be owned by root and only readable by others and the group. only root can have rwx

Maybe someone else has this problem and will be able to solve it this way ;)) 

greez

---

