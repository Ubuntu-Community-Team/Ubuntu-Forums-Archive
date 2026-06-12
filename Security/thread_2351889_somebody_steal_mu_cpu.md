---
title: "somebody steal mu cpu"
date: 2017-02-07
forum: Security
---

### Post by clemare on 2017-02-07
Hi

I'm using Ubuntu server 16.04.1 LTS where I run some VM's (with virtualbox), samba and a postgresql database. A couple of weeks ago somebody get access to the server and install 3 files, (mpool, mpool.sh and zero.so). I don't know from where the hacker got the access and I need you people to figured out how he can do it. The hacer basically runs a software to do something with bitcoins, and he need all the cpu power he can get (8 cores in this machine). I have sshd running in port 22, but to access from the internet you need to use another port.
I checked /var/log/auth.log file, but there is no signal of him (he entered by third time today), I checked the incoming connections with tcptrack, but the last time this hacker install the software I was far from the console. One thing that makes me suspect is the database, because the 3 files the owner and the group is the database (postgres) and when mpool is running it runs under the postgres user. However I am not a database expert to understand how he do it.

Can anyone help me please?

---

### Post by clemare on 2017-02-07
Ok, I found it. The hacker access from the database, and somehow is capable to execute programs from the database... I didn't know that, and if there is a way to deactivate that feature, I want to know please. I closed the port from internet and see how to get better security.

---

### Post by dolic on 2017-02-09
Hi. I have exactly the same issue with my postgres since several month. I tried to find out where the software resides but couldn't even though I changed all passwords and tightend the firewall the program starts over and over and steals all ressources. So if there is something new about that, we could inform each other? That would be great. Thanks

---

### Post by dolic on 2017-02-09
Found this function in my PostgreSQL postgres/public Schema and DROP CASCADE it: sys_eval(text) and sys_eval999(text). They both created /tmp/zero.so. Hope that killed this problem.

---

### Post by ciaran-liedeman on 2017-03-17
If anyone who stumbles across this link is using docker and UFW your firewall may not be working as expected.
Due to how docker inserts iptables records and how UFW reads the config you firewall may look like its up but your container bound ports are actually open to the world.

For more information: [https://github.com/docker/docker/issues/4737](https://github.com/docker/docker/issues/4737)

---

