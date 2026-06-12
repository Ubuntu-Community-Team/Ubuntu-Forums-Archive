---
title: "NFS won't allow write"
date: 2007-07-03
forum: Server Platforms
---

### Post by EnterDaMatrix on 2007-07-03
Here is my exports file:

```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#

/media/files 192.168.2.55 (rw,sync)
```

It won't allow me to write to the share from the client. I can only read.

---

### Post by punx45 on 2007-07-03
if your user ID on the client and server are different (which is likely the case), this might help:   

[http://www.die.net/doc/linux/man/man5/exports.5.html](http://www.die.net/doc/linux/man/man5/exports.5.html) - check the section on user ID mapping.

also check the permissions of the directories on the server side.   even if you export a directory as rw, i believe the permissions of said directory take precedence.  

use permissions in concert with ID mapping to get the control you desire.   if you are the only one accessing the NFS share, it might be just as easy to enable all levels of write access to the directory with chmod.

---

### Post by EnterDaMatrix on 2007-07-03
I don't know how to do the permissions. Heres my ls -l on that directory. I tried giving 777 to each but it still wont work. It's weird cause this was working great until recently, and I'm not sure what I did.

Heres the ls -l:

```
drwxrwxrwx  5 justin justin  4096 2007-07-02 20:29 downloads
drwxrwxrwx  2 root   root   49152 2007-03-02 11:16 lost+found
drwxrwxrwx  4 justin justin  4096 2007-04-08 12:55 Movies
drwxrwxrwx  8 justin justin  4096 2007-04-25 16:43 Music
drwxrwxrwx  5 justin justin  4096 2007-03-03 23:11 Software
drwxrwxrwx 11 justin justin  4096 2007-06-24 21:25 TV

```

My user name on the server and the client is justin in both cases. I think I might have made a mistake by giving privileges to lost+found. Anyway there it is.

---

### Post by punx45 on 2007-07-03
hmm..   i wish I had shell access to my system at home from here at work!

as you have it now, all the directories are universally read/write.  (chmod-ed to 777) 

maybe try adding all_squash to the parameter list.  e.g.```
/media/files 192.168.2.55 (rw,sync,all_squash)
```

try restarting nfsd too.   should be ```
/etc/init.d/nfsd restart
```

hopefully im not leading you on a wild goose chase :)

i will check my /etc/exports when i get home later tonight


this is what i have:```
/media/mediaserver/ 192.168.1.0/255.255.255.0(rw,async,insecure,all_squash,)
```

---

### Post by punx45 on 2007-07-03
or it could simply be the space:   
change ```
/media/files 192.168.2.55 (rw,sync)
```
to
```
/media/files 192.168.2.55(rw,sync)
```

---

### Post by EnterDaMatrix on 2007-07-04
I couldn't restart nfsd, and when I looked in the init.d directory, there was only nfs-common and nfs-kernel server. I restarted both of those and suffered the same results. In the end I rebooted the server and now it works. I have it set up with the same exports options as you. Thank you very much. I guess it was just a weird problem.

---

### Post by punx45 on 2007-07-05
sounds good.  but do note that I have my share set to 'async' rather than 'sync'.   

as you can see from the exports man page, async is riskier.   just so you know.

> *async*
    This option allows the NFS server to violate the NFS protocol and reply to requests before any changes made by that request have been committed to stable storage (e.g. disc drive).   Using this option usually improves performance, but at the cost that an unclean server restart (i.e. a crash) can cause data to be lost or corrupted. 
*sync*
    Reply to requests only after the changes have been committed to stable storage (see async above).


And I just feel that I should disclose that when I put that exports together I didn't fully understand what I was doing, so it might not be the best solution, so I encourage you to learn more about NFS and apply that knowledge to your situation.   (and dont get mad at me if something breaks :-) )

---

### Post by EnterDaMatrix on 2007-07-05
I tried both and didn't notice any speed problems. I tested transfer speed and it is exactly as fast using sync. I used to use async and switched when I was trying to fix my problem. I'll stick with sync because data loss would be very bad (all my media is here, not backed up). Do you know of any free or cheap online service that would back up like 500GB of media?

---

### Post by punx45 on 2007-07-05
I dont know of any online backup hosts.    500GB is an immense amount to store online, especially since upload speeds are so slow.   It is likely to be very expensive as well.   You would probably be better off investing in another HDD and backing up to it, or using a RAID scheme that mirrors.

---

### Post by EnterDaMatrix on 2007-07-05
That's what I figured. A lot is lossless CDs and DVDs so I can back those up pretty easily, anyway I think we're wasting the space on this board, but thanks for the excellent advice.

---

