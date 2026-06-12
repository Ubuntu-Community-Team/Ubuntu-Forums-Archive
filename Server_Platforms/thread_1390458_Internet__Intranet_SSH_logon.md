---
title: "Internet / Intranet SSH logon"
date: 2010-01-25
forum: Server Platforms
---

### Post by m3bik on 2010-01-25
I'm running an Ubuntu 8.10 Server. I have an account that I use from my intranet to access the server. I want to make that account only accessible over an intranet connection and set up a separate account for me to use over an internet connection. 

Basically allow any connection from 192.168.*.* to use one account, and all other connections can only use another specific account to access the server. The want for this is because I have a basic username and password for my account, but I know that by making a public SSH connection possible, I need* to use a really strong (stronger than my basic) password. I don't want to have to use a really strong password if I'm accessing remotely...that's why I'm looking into this option. Is this possible?

Thanks.

---

### Post by BkkBonanza on 2010-01-25
You can use the AllowUsers directive in /etc/ssh/sshd_config.

AllowUsers joe
AllowUsers fred@192.168.0.*

or if your network is named properly then,

AllowUsers joe
AllowUsers fred@mynetwork

---

### Post by Lars Noodén on 2010-01-26
As BkkBonaza  points out, [sshd_config](http://manpages.ubuntu.com/manpages/karmic/en/man5/sshd_config.5.html) is the place to start looking.  Changes to who's allowed to access the server are more manageable when the access is granted to a group rather than an individual user.  

But to provide different settings based on network of origin, you can use the **Match** directive. e.g.

```

Match Address 192.168.0.0/16, Group extranet
   MaxAuthTries 0

```

---

