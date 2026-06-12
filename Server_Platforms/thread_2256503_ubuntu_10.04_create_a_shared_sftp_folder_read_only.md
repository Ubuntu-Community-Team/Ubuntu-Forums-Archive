---
title: "ubuntu 10.04 create a shared sftp folder read only"
date: 2014-12-13
forum: Server Platforms
---

### Post by markosjal on 2014-12-13
I have an ubuntu 10.04 server. I want to create a shared space accessible as read only by multiple uusers over sftp.

users should not be able to see anything other than the shared read only folder and preferrably not be able to get a shell. it must be read only

How can I do this?

---

### Post by Lars Noodén on 2014-12-13
(The end is nearing for 10.04 Lucid as you know...)

But the way you can do what you are asking is to use openssh-server and set [ChrootDirectory](http://manpages.ubuntu.com/manpages/lucid/en/man5/sshd_config.5.html) for that group of users using a Match statement.  For example, make a group "sftponly" and put the users who are to be prevented shell access in that group.  Then make a directory owned by user "root" and group "root", say /home/sftp, and put your files there, again owned by root:root.  Then your file /etc/ssh/sshd_config could contain something like this:

```

...
Subsystem sftp internal-sftp
...
Match Group sftponly
        ChrootDirectory /home/sftp
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

If you are working remotely, make sure you have another way in so you don't get locked out if you make a mistake.

---

### Post by markosjal on 2014-12-13
that "no other way in" is what makes me nervous. SSH is all I have , no other access

---

### Post by Lars Noodén on 2014-12-13
Maybe I'm just overcautious today.  

One option is that you can launch sshd manually, separately on a different port, then connect to that.  

```

sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.orig
sudo /usr/sbin/sshd -p 2223 -f /etc/ssh/sshd_config.orig

```

Then once you are connected on that other port, 2223 above, you can work with configuring the main sshd.  

```

sudo service ssh restart 

```

Don't use [pkill](http://manpages.ubuntu.com/manpages/lucid/en/man1/pkill.1.html) or you will zap the extra sshd instance you are running to stay connected in the event of an emergency.

---

### Post by TheFu on 2014-12-14
> **markosjal said:**
> that "no other way in" is what makes me nervous. SSH is all I have , no other access

Test with a testusr, not your main userid?

---

