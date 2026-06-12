---
title: "[SOLVED] Accessing SSH via custom port"
date: 2007-09-02
forum: Server Platforms
---

### Post by p_quarles on 2007-09-02
I have an SSH server set up and running fine on a high port with key-based authentication. I.e., my questions are not about OpenSSH software itself, but other ways of connecting to the daemon.

1) /etc/fstab: I have a line (currently commented out, as it's not working) that tries to mount an sshfs share on the server:
```
user@10.0.0.X:/home/user /media/servername fuse defaults 0 0
```
How do I tell it to use the custom port? Is there syntax I can add to this line, or do I need to customize fuse or the ssh client? 

NB: mounting the drive manually works just fine, and this isn't really a big problem. I'm throwing this question in mainly because it's closely related to the next one.

2) rsync: I can't for the life of me figure out how to get this to work aside from configuring sshd_config on the remote machine to listen on port 22. I really don't want to have to restart the ssh server and change the iptables rules every time I run a backup. I tried adding 
```
--port=*xxxx*
``` to the rsync command, but this accomplishes nothing: I am still told that connecting on port 22 failed. 

Also, I should note that the backup destination folders are in an encrypted loopback device. Meaning that, no, I cannot specify the already mounted remote drive as the target directory (though I suppose I could mount the loopback device using sshfs, if necessary). 

Thanks in advance.

---

### Post by HermanAB on 2007-09-02
The listener port(s) is configured in /etc/ssh/sshd_config.  You can make SSH listen on multiple ports by listing them underneath each other:
Port 22
Port 2222

Remember to restart sshd to make the change take effect:
$ sudo service sshd restart

Then you can log on using:
$ ssh user@server -p 2222

Cheers,

Herman

---

### Post by p_quarles on 2007-09-02
Thanks for the reply, but that doesn't answer either of my actual questions.

---

### Post by HermanAB on 2007-09-02
Well, once the server is configured, then you can configure the client in /etc/ssh/ssh_config in a similar way and set the default port to use by the ssh client:
Port 2222

SSH and rsync over ssh will then use port 2222.

Cheers,

H.

---

### Post by p_quarles on 2007-09-02
The server has been configured for a while :)

Anyway, thanks. That should solve the problem. I can't believe I overlooked that.:redface:

EDIT: I'm going to reboot and see if the network drive mounts. If it does, I'll mark this thread solved.

---

### Post by p_quarles on 2007-09-02
Okay, partial success. After changing the SSH client's settings to go to the custom port, rsync works correctly. The sshfs share still refuses to automatically mount at startup, though. 

Like I said, rsync was the priority, and the other problem is more of a nuisance, but if anyone can see what I'm doing wrong . . .

---

### Post by bodhi.zazen on 2007-09-03
Might I suggest a more descriptive title ? I had no idea you were  asking about sshfs :twisted: 

At any rate ,  you might find these links helpful : 


[http://www.john-hunt.com/linux/2006/10/30/fixing-fuse-for-auto-mounting-in-your-fstab-via-sshfs/](http://www.john-hunt.com/linux/2006/10/30/fixing-fuse-for-auto-mounting-in-your-fstab-via-sshfs/)

[http://www.debuntu.org/2006/04/27/39-mounting-a-fuse-filesystem-form-etcfstab](http://www.debuntu.org/2006/04/27/39-mounting-a-fuse-filesystem-form-etcfstab)

---

### Post by p_quarles on 2007-09-03
> **bodhi.zazen said:**
> Might I suggest a more descriptive title ?
Yeah, I was trying to come up with something a header that included both problems, but it is kind of misleading. 

Those links will give me a few more things to try. Thanks.

EDIT: Still not working. I loaded up the mount.fuse script from the first link, played around with the fstab line (adding the uid,gid lines for my account), and it doesn't seem to be doing anything.

---

### Post by p_quarles on 2007-09-03
I was doing something *completely* unrelated when I stumbled upon the cause of the problem with sshfs: apparently the Gnome session manager had taken the fstab information and turned it up into a startup command. 

About a month ago I changed the software the server was running on (I guess I neglected to mention this in the initial message). While doing this, I assigned the server a different static IP address. The session manager command (which I didn't realize existed until I stumbled upon it) was mounting a drive on a nonexistent machine *after *the system had mounted the drive (reading from fstab) on the server. I.e., the remote address had changed, but the local mount point was the same. Gah.

If it had ever occurred to me to simply boot into safe mode, I would have figured this out a lot sooner. And, yes, I will let that be a lesson to me.](*,)

---

