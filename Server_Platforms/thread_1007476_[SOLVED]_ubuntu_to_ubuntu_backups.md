---
title: "[SOLVED] ubuntu to ubuntu backups"
date: 2008-12-10
forum: Server Platforms
---

### Post by Dryfter on 2008-12-10
Both computers are running 8.10 server. and I can read and write to both share's so I'm pretty sure it's not a permissions issue.  It's an, "I don't know wtf I'm doing issue". hahaha

What I'm trying to do is transfer a folder from one machine to the other.

//Server1/Share to //Server2/Sharebackup

I've tried using rsync. it backs up to my local directory and just keeps looping.

"sudo rsync -av --progress --delete /home/share \\server2\sharebackup" Is the command i'm using.

Not really sure what I'm doing. I do have webmin running.  If there is an easier way to do this i'm all for it.

---

### Post by hrod beraht on 2008-12-10
> **Dryfter said:**
> Both computers are running 8.10 server. and I can read and write to both share's so I'm pretty sure it's not a permissions issue.
"sudo rsync -av --progress --delete /home/share \\server2\sharebackup" Is the command i'm using.

When you say you can read and write to both shares, how do you mean you are doing it? That is, what protocol are you using for the shares, NFS, Samba, SSHFS?

Since you are using '\\' to address the backup location, it's obviously not mounted, so rsync likely just isn't seeing it. Which brings me back to the first question of what protocol are you using for the shares?

I'm going to guess you are using Samba (no particular reason for that guess :D ). So the easiest way to do it via rsync (which is awesome) is to mount the server 2 backup to the first machine under somewhere like /media, as in:
```
sudo mount -t cifs //Server2/Sharebackup /media/Server2
```

And then do the rsync:
```
sudo rsync -av --progress --delete /home/share /media/Server2
```

And then unmount Server2:
```
sudo umount /media/Server2
```

Bob

---

### Post by Dryfter on 2008-12-10
Yes, you were correct about me using Samba. the first machine is also accessed by Windows users. (which is why i'm using samba)

Tried to do the first step, but I got an error.

"mount error: can not change directory into mount target /media/Server2

Do the Share's on Server 2 have to be Browesable? Because right now they aren't.

---

### Post by hrod beraht on 2008-12-10
> **Dryfter said:**
> Tried to do the first step, but I got an error.

"mount error: can not change directory into mount target /media/Server2

The directory has to exist before you can mount it. So if you haven't created it yet, do a:
```
sudo mkdir /media/Server2
```
Or whatever name you want to use.

Bob

---

### Post by Dryfter on 2008-12-11
Alright! Makes sense that the directory has to be there before I mount something to it. 
Now i'm getting a:
CIFS VFS: Error connection to IPv4 socket.
CIFS VFS: cifs_mount failed w/return code =-512

^It tells me that after I type in the password (I'm assuming for the remote system), and it just sits there so I ctrl+C'd and it threw me that error.

Can you believe I've set up 3 Ubuntu servers? hahaha

---

### Post by Dryfter on 2008-12-11
Never mind.  I got it!

I had to change //Server2/share to //x.x.x.x/share and then I did end up having to change the permissions on Server 2.

My next question is if I want this to be automated. is there an easy way to do it to where I don't have to type my password in? (if I need to make a new thread I will just tell me)

Edit:
And I think I just changed all the permissions on my home folder. Haha, wow I suck at this :).
I did a chmod 777 on it. I think I ment to do something else.  But I don't really know what.  Nothing REALLY important is there, but I would like to get back to those...

---

### Post by hrod beraht on 2008-12-11
> **Dryfter said:**
> I had to change //Server2/share to //x.x.x.x/share...
If you would prefer to use the short-hand computer name rather than it's IP address, just put that information in the /etc/hosts file. For example:
```
192.168.1.150 Server2
```
That will mean that you can then refer to //Server2/share and the computer will use the /etc/hosts file to translate *Server2* into *192.168.1.150* (or whatever IP address you assigned to Server2). If you haven't assigned a static IP address, you should, otherwise you take the chance that after every reboot that DHCP will assign it a different random address. That's not usually a problem with a desktop computer because other computers aren't specifically trying to address it. But with a server, other computer are specifically trying to address it, and so a static address makes things much easier.

> **Dryfter said:**
> And I think I just changed all the permissions on my home folder. Haha, wow I suck at this :).
I did a chmod 777 on it. I think I ment to do something else.  But I don't really know what.  Nothing REALLY important is there, but I would like to get back to those...

The default permissions are, I believe, 755. But that may not be ideal as it gives others the ability to read your home folder. I personally have my home folder permissions set at 700, meaning that I, as the owner, have full read/write permissions, but nobody else has any, i.e. the folder is private.

Bob

---

### Post by Dryfter on 2008-12-11
> **hrod beraht said:**
> If you would prefer to use the short-hand computer name rather than it's IP address, just put that information in the /etc/hosts file. For example:
```
192.168.1.150 Server2
```
That will mean that you can then refer to //Server2/share and the computer will use the /etc/hosts file to translate *Server2* into *192.168.1.150* (or whatever IP address you assigned to Server2). **[B][COLOR="Red"]If you haven't assigned a static IP address, you should, otherwise you take the chance that after every reboot that DHCP will assign it a different random address.[/COLOR]**[/B] That's not usually a problem with a desktop computer because other computers aren't specifically trying to address it. But with a server, other computer are specifically trying to address it, and so a static address makes things much easier.



The default permissions are, I believe, 755. But that may not be ideal as it gives others the ability to read your home folder. I personally have my home folder permissions set at 700, meaning that I, as the owner, have full read/write permissions, but nobody else has any, i.e. the folder is private.

Bob

[COLOR="Red"]Yup, already did that.  I'm not THAT new at this :lolflag:[/COLOR]

The permission info should be in a wiki article some where.  I wasn't able to find what in the world all the numbers mean anywhere. Then again, I'm probably not using the right termination when googling.  Thanks for the info! and the help!

Any idea on an easy way to make this automatic?

---

