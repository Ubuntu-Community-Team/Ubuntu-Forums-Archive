---
title: "howe to make 1 prot work on ssh on ubuntu 10.04"
date: 2012-10-06
forum: Security
---

### Post by rzeer on 2012-10-06
Hi
 
I have Ubuntu 10.04 desktop and Ubuntu 10.04 Server
 
Howe to make 1 prot to work on ssh on dekstop and server
 
I replace the port ssh to new port , put all ip can connect to ssh in the new port
 
i want make 1 ip connect the ssh port ?
 
can any body help me ???

---

### Post by albandy on 2012-10-06
ssh user@ip -p portnumber

---

### Post by rzeer on 2012-10-06
> **albandy said:**
> ssh user@ip -p portnumber
 
 
thanks
 
but , i want to make 1 ip only work on ssh ?

---

### Post by Lars Noodén on 2012-10-06
Can you explain in more detail what it is that you want to happen?  What are you trying to do and how do you plan to use the connection?

---

### Post by rzeer on 2012-10-06
> **Lars Noodén said:**
> Can you explain in more detail what it is that you want to happen? What are you trying to do and how do you plan to use the connection?
 
 
I am open file  etc/ssh/ssh_config
 
and put line
 
LineAddress : 62.135.119.50
 
and restart the ssh
 
i cant work to ssh for any ip
 
whe i delte it , it work for any ip on ssh
 
I want make security for ssh , to work for my ip only ??

---

### Post by albandy on 2012-10-06
> **rzeer said:**
> I am open file  etc/ssh/ssh_config
 
and put line
 
LineAddress : 62.135.119.50
 
and restart the ssh
 
i cant work to ssh for any ip
 
whe i delte it , it work for any ip on ssh
 
I want make security for ssh , to work for my ip only ??


You can use ubuntu firewall to control this in an easy way:

sudo ufw enable (this enables ubuntu firewall)
sudo ufw allow from 62.135.119.50 proto tcp to any port 22

---

### Post by Lars Noodén on 2012-10-06
There is no 'LineAddress' in [sshd_config](http://manpages.ubuntu.com/manpages/precise/en/man5/ssh_config.5.html).  What you are probably looking for is [Match Address](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html) in sshd_config.  

```

Match Address *,!62.135.119.50
  ForceCommand /bin/false

Match Address 62.135.119.50

```


You could also use iptables or xinetd to restrict which address you are allowed to connect from.  Myself, I'd lean towards using iptables as described in albandy's post with UFW.

---

### Post by rzeer on 2012-10-06
> **albandy said:**
> You can use ubuntu firewall to control this in an easy way:
 
sudo ufw enable (this enables ubuntu firewall)
sudo ufw allow from 62.135.119.50 proto tcp to any port 22
 
 
thanks , and plz help me
 
for ssh want to work for my ip only , and howe to make it on ssh_config
 
for another 2 port want to work for my ip only
 
for some port want to work for any ip ?
 
can you help me plz ?

---

### Post by rzeer on 2012-10-06
> **Lars Noodén said:**
> There is no 'LineAddress' in [sshd_config]("http://manpages.ubuntu.com/manpages/precise/en/man5/ssh_config.5.html"). What you are probably looking for is [Match Address]("http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html") in sshd_config. 
 
```

Match Address *,!62.135.119.50
  ForceCommand /bin/false
 
Match Address 62.135.119.50

```
 
 
You could also use iptables or xinetd to restrict which address you are allowed to connect from. Myself, I'd lean towards using iptables as described in albandy's post with UFW.
 
 
thanks , and plz help me

for ssh want to work for my ip only , and howe to make it on ssh_config

for another 2 port want to work for my ip only

for some port want to work for any ip ?

can you help me plz ?

---

### Post by Lars Noodén on 2012-10-06
The restrictions don't come from ssh_config, so leave that be.  The restrictions can only be made on the server side.  That means using UFW as recommended above in albandy's post.  

[https://help.ubuntu.com/12.04/serverguide/firewall.html](https://help.ubuntu.com/12.04/serverguide/firewall.html)
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

To have sshd listen on additional ports, if that is what you are asking, you have to configure it in [sshd_config](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html) using the ListenAddress directive, and then open the ports in UFW as described in the two links above.


```

ListenAddress 0.0.0.0:22
ListenAddress 0.0.0.0:2022
ListenAddress 0.0.0.0:3118

```

---

