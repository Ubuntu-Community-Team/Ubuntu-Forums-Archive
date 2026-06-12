---
title: "monitor ssh trafic only"
date: 2009-11-28
forum: Security
---

### Post by Sin@Sin-Sacrifice on 2009-11-28
It's really the only service I use but it's open to the internet so I can connect when I'm out. I have a pretty good password but even still I would like to monitor when people attempt to sign in. Is there any easier way to do this than having to go through all of [this]("http://ubuntuforums.org/newthread.php?do=newthread&f=338")? I have looked around for an ssh log or something of the sort but everything points back to that thread. Thanks in advance.

---

### Post by Yoann Juet on 2009-11-28
> **Sin@Sin-Sacrifice said:**
> I would like to monitor when people attempt to sign in.

/var/log/auth.log

It's usually a good idea to protect the ssh service from dictionary and brute force attacks. fail2ban tool (as well as sshblock, sshguard...) parses system log files to detect such behavior then interacts with iptables to block the attacker.

---

### Post by The Cog on 2009-11-29
Other good advice is:

Move the ssh service to a high port rather than 22 (maybe above 10000)- most password guessing bots only try port 22.

Configure ssh to use key-based authentication instead of password based.

---

### Post by Lars Noodén on 2009-11-29
> **Sin@Sin-Sacrifice said:**
> It's really the only service I use but it's open to the internet so I can connect when I'm out. I have a pretty good password but even still I would like to monitor when people attempt to sign in. Is there any easier way to do this than having to go through all of [this]("http://ubuntuforums.org/newthread.php?do=newthread&f=338")? I have looked around for an ssh log or something of the sort but everything points back to that thread. Thanks in advance.

One way is xinetd, which can use the **log_on_success** directive and can make a separate log for just sshd.  

```
 
service **ssh**
{
	socket_type     = stream
	protocol        = tcp
	wait            = no
	user            = root
	server          = /usr/sbin/sshd
	server_args     = **-i**
	per_source      = UNLIMITED
	log_on_success  = **USERID HOST DURATION**
}

```

Prohibiting remote root access is important, as is requiring key-based authentication.  

```

     PermitRootLogin **no**
     PasswordAuthentication **no**

```

---

### Post by Sin@Sin-Sacrifice on 2009-11-29
Thanks guys. Lots of help. I don't use port 22 and it is key based... well both acutally but nothing is impossible to crack. I just want to watch over it. About the brute force attacks... I wonder how long it would take to brute force a password over 20 characters long.

---

### Post by EJeanmaire on 2009-11-30
> **Sin@Sin-Sacrifice said:**
> Thanks guys. Lots of help. I don't use port 22 and it is key based... well both acutally but nothing is impossible to crack. I just want to watch over it. About the brute force attacks... I wonder how long it would take to brute force a password over 20 characters long.

you can watch failed attempts at /var/log/btmp (use the 'lastb' command to read the log as its a binary file).  

As for the 20 character password, depends on the encryption algorithm, and depends if you mean a password that is 0-20 char in length.  Exactly 20 characters (and the attacker knowing this) is far less secure.

---

