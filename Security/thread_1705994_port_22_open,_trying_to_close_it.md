---
title: "port 22 open, trying to close it"
date: 2011-03-13
forum: Security
---

### Post by fabricator4 on 2011-03-13
Hi all, my default keying popped up and asked for authentication twice today, odd since I wasn't doing anything that would require it.  I have a wifi network that does require authentication, but the wifi device on my netbook was turned off at the time.

Nothing failed to work or stopped working after I twice refused to authenticate the keyring.

I'm new to this so feeling my way...  I ran nmap:

```

sudo nmap -sS -O 127.0.0.1

```

and got: 

```

22/tcp   open   ssh

```

Looking in  /etc/services I found:

```

ssh             22/tcp                          # SSH Remote Login Protocol

```

Once I stopped freaking out, I got back to googling and tried to find out what process had the port open:

```

sudo fuser -u 22/tcp
22/tcp:         543(root)

```

I opened system monitor and could not find a process 543 so I tried:

```

sudo fuser -k 22/tcp

```

but this simply results in a new process starting which keeps port 22 open.

I deleted remote desktop off this machine as soon as I installed 10.04  as I had no intention of using it.  I have no idea what else might be keeping this port open, and at a bit of loss as to what my next step should be?

Chris

---

### Post by HermanAB on 2011-03-13
Howdy,

Port 22 is used by the Secure Shell.  I suggest that you first read up about it - the Snail book for example:
[http://www.snailbook.com/](http://www.snailbook.com/)

You can stop sshd using the services wizard.

---

### Post by The Cog on 2011-03-13
This command:
sudo lsof -i -n -P
will show you which program has opened the port. It is probably sshd which is the secure shell service. This provides remote login and file transfer. sshd is installed by the openssh-server package.

You can see what logins it has accepted with the command:
grep ssh /var/log/auth.log.

---

### Post by skraps on 2011-03-13
you can also use iptables to close the port\

```

iptables -I INPUT -p tcp -s 0/0 -d 0/0 --dport 22 -j DROP

```

---

### Post by fabricator4 on 2011-03-13
> **The Cog said:**
> 
You can see what logins it has accepted with the command:
grep ssh /var/log/auth.log.


I found in the log:
```

Mar 11 04:32:23 chris-eeepc sshd[10532]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=219.129.239.118  user=root
Mar 11 04:32:25 chris-eeepc sshd[10532]: Failed password for root from 219.129.239.118 port 50649 ssh2

```


That's one of the usual suspects for me: Chinanet. :-o


Thanks for everyone's help on this!

Chris

---

