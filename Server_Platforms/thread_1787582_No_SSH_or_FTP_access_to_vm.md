---
title: "No SSH or FTP access to vm"
date: 2011-06-21
forum: Server Platforms
---

### Post by bigmonmulgrew on 2011-06-21
HI I was following some instructions on how to setup and limit FTP access to a server.
Doing this on a VPC both guest and host are ubuntu server 11.04
guest is a LAMP
anyway part of the guide I was following said to add the code below to the file /etc/ssh/sshd_config
```
Subsystem sftp internal-sftp

Match Group webadmins
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp
```

Since doing this I now cant access the vpc at all. I dont have ssh access or ftp access. I can still access the website thats hosted on the server.
So any ideas how I get access to fix this problem.

If you want full details of what I was up to look [here]("http://ubuntuforums.org/showthread.php?t=1785402"). but ultimately it was the step above that messed things up.

---

### Post by Lars Noodén on 2011-06-21
You will need to access it via a user that is not a member of "webadmins".  All users of that group will get locked into a chroot jail upon successful login.

---

### Post by bigmonmulgrew on 2011-06-21
I'm not even given the chance to log in. For example while using putty to ssh I get the message
Network Error: Connection refused

---

### Post by bigmonmulgrew on 2011-06-21
I've only added one user to this group, the one I created to try this out.
I cant access the vpc with any user.

---

### Post by Lars Noodén on 2011-06-21
> **bigmonmulgrew said:**
> I'm not even given the chance to log in. For example while using putty to ssh I get the message
Network Error: Connection refused

sshd may not be running.  

What about 
```

pgrep -l sshd

```

If sshd is not running then you want to do a little debugging on one screen while you try to log in on the other:

```

/usr/sbin/sshd -Dd

```

---

### Post by bigmonmulgrew on 2011-06-21
I currently cant acces the VPCs terminal either

---

### Post by Lars Noodén on 2011-06-21
> **bigmonmulgrew said:**
> I currently cant acces the VPCs terminal either

Which one are you using?  Qemu or VirtualBox?

---

### Post by bigmonmulgrew on 2011-06-21
qemu, i think

---

### Post by bigmonmulgrew on 2011-06-21
I'm starting to think that my only option is to start from scratch and rebuild the vm. This wont be a problem for my website but I had done a lot of configuration changes since the last backup

---

