---
title: "SSH access denied errors for existing SSH users"
date: 2008-05-30
forum: Server Platforms
---

### Post by tanman77 on 2008-05-30
Hi,

I seem to have trouble logging into my Ubuntu server remotely using ssh. 

This happened shortly after I did a apt-get upgrade on the server, and ssh server was upgraded. This happens to a pre-existing user that was able to log in before, but cannot and a new user.

I use the AllowHosts in ssh_config and even though I have both the usernames in there, it still has the same problem. I have yet to  see whether it can be logged in locally. 

Is there anything that I should be aware of (or looking at) in regards to this in order to resolve this particular issue? Many thanks.

regards,

Wei-Yen

---

### Post by Monicker on 2008-05-30
What kind of error message do you receive?

It might be related to the following:

[http://ubuntuforums.org/announcement.php?f=338]("http://ubuntuforums.org/announcement.php?f=338")


The host ssh keys would have been regenerated after applying the update which fixed the vulnerability.

---

### Post by tanman77 on 2008-05-30
Hi thanks for the reply Monicker. I have had a read of that and I think it closely matches the problem I am having. But I am unsure what I need to do. I just need to install that package libssl? Many thanks.

Wei-Yen

---

### Post by Monicker on 2008-05-30
You should already have libssl installed.  We really need to see the exact error message you are getting in order to determine exactly what is happening in your case.

You should also use the -vvv option to get more verbose output about why it is failing.

```
ssh -vvv username@remotemachine
```

---

### Post by popie on 2008-05-30
> The host ssh keys would have been regenerated after applying the update which fixed the vulnerability.

Can you tell me how this is done? 

I read the man page for ssh, but its clear as mud.
I know the "fingerprint" of the server I'm trying to connect to (with recently upgraded SSH) but no clue how to find the key and put it into ~/.ssh/known_hosts.

Actually, the host regenerated its keys during the update. Its the remote client that's having problems connecting, and needs to be updated with the new key. Its currently denying the connection with a "Warning Remote Host Identification Has Changed" message.

---

### Post by quelx on 2008-05-30
The key re-generation is done automatically if vulnerable host keys were found (I think they were *all* vulnerable).

Your clients need the old fingerprint purged, and ssh gives you a line number when it refuses to connect (say **:13**) where the old fingerprint is in the **~/.ssh/known_hosts** file.  ```
nano -w ~/.ssh/known_hosts
``` and browse down to the correct line number (**CTRL-C** will tell you which line the cursor is on) and delete the fingerprint (**CTRL-K** removes an entire line).  **CTRL-X** to save and exit.  When you try to reconnect to the server **ssh** will prompt you to accept the new fingerprint and save it in the **known_hosts** file.

---

### Post by popie on 2008-05-30
Thanks. I delete line 1 per your instructions, and then was able to get further. I got this warning however:

> Warning: the RSA host key for 'server2' differs from the key for the IP address '192.168.1.206'
Offending key for IP in /home/<myid>/.ssh/known_hosts:1
Are you sure you want to continue connecting (yes/no)? yes

Upon logging in again, a similar warning said that line 1 didn't match that IP, but line 4 did. So I deleted the line 1 (again). And now all is good.

Thanks again.

---

### Post by tanman77 on 2008-05-31
Hi there, 

Thanks for replying back to me. I am using a Windows Box to connect to the server. I use putty and plink, and in both incidences they say that it is" access denied". Also I created another user and included that user into sshd_config. I then restarted the sshd_config.

 I am not sure where to look....or where to start to troubleshoot this issue. Any help would be appreciated. :)

---

