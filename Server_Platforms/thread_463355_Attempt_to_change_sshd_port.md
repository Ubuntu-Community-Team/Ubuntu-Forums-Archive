---
title: "Attempt to change sshd port"
date: 2007-06-03
forum: Server Platforms
---

### Post by gogo242 on 2007-06-03
At one time I had sshd listening on a non default port....but now whenever I change the port line in my sshd_config I get the following error when I try to login:  "No Address associated with nodename"

And when I do a sudo netstat -tupl I can see sshd listening to the port I specified.  But I can't connect remotely...and ideas?

Also in my auth.log everytime I try to connect remotely via ssh I get an entry that says this...
> Jun  3 16:18:48 ubuntu sshd[4285]: Server listening on 192.168.2.20 port 2242.
Jun  3 16:18:50 ubuntu sshd[4285]: Received signal 15; terminating.


---

### Post by gogo242 on 2007-06-05
bump

---

### Post by MJN on 2007-06-05
What SSH client command are you using? Can you connect via IP address (no name)? Where are you connecting from?

Mathew

---

### Post by Znupi on 2007-06-05
Are you trying to connect from behind a firewall?

---

### Post by gogo242 on 2007-06-05
> **MJN said:**
> What SSH client command are you using? Can you connect via IP address (no name)? Where are you connecting from?

Mathew

I'm trying to connect from another computer I own on the same local network.  If I set the port in sshd_config to 22 and type "ssh username@ipaddress" it connects perfectly.  If I change the port in sshd_config to 2242 and type "ssh username@ipaddress:2242" I get this error..."No address associated with nodename"

And I've tried connecting using hostname and ip address, no joy for either with a non-default port.

---

### Post by gogo242 on 2007-06-05
> **Znupi said:**
> Are you trying to connect from behind a firewall?

No

---

### Post by MJN on 2007-06-06
> **gogo242 said:**
> If I change the port in sshd_config to 2242 and type "ssh username@ipaddress:2242" I get this error..."No address associated with nodename".

Drop the colon and use **-p 2242**!

Mathew

---

### Post by Znupi on 2007-06-06
Indeed, the right command is
```

ssh username@ipaddress -p 2242

```

---

### Post by gogo242 on 2007-06-06
:grin:  Man I love you guys.  Thanks!

I don't remember having to use that -p flag ever!

---

### Post by MJN on 2007-06-06
You might want to 'hard code' the port for that host in your **/etc/ssh/ssh_config** file:
 
```

Host <the server's hostname>
Port 2242

```
 
Make sure it appears at the end so as not to effect the default port for any other SSH connections.
 
Mathew

---

