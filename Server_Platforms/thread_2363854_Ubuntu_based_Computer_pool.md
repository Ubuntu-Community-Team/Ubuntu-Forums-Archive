---
title: "Ubuntu based Computer pool"
date: 2017-06-15
forum: Server Platforms
---

### Post by aprox on 2017-06-15
Dear all,

possibly, this question is rather simple and I merely need a hint. I am trying to establish a computer pool with about 10 PCs in our university institute. I want to manage some software (OSGeo) and data within this pool, possibly from a central server. Students are supposed to have their personal accounts within this pool, being able to start their account from any PC, launch the software and use the data. Hence, I am more or less looking for something similar to a Win NT solution, but based on Ubuntu.

What would be the best solution?

Many thanks in advance and sorry if my question is misplaced or overly simple

---

### Post by SeijiSensei on 2017-06-15
The [Linux Terminal Server Project]("http://www.ltsp.org/") enables you to set up diskless workstations and run applications stored on Linux or Windows servers.  I see there is a [demonstration of LTSP that comes with the Edubuntu flavor]("http://edubuntu.org/documentation/ltsp-live").  LTSP is not bound to Edubuntu; you can use it with any Ubuntu flavor, or indeed any Linux distribution.

---

### Post by Tadaen_Sylvermane on 2017-06-15
+1 to LTSP. Use it at home to pxe boot media centers. Simplifies management big time. I have it also set to boot a usable desktop as well if needed. Very easy to configure and easily scalable.

---

### Post by TheFu on 2017-06-18
Welcome to the forums.

I can't say that I understand the question, but if you want to setup 10 Unix systems with 10-10,000 users and allow different people to walk up, sit down and have each computer be "their own" based on login, then a combination of NIS+ and NFS is what I'd use.  Actually, NIS+ servers only run on Solaris, so you need some sort of LDAP+PAM to handle the things that NIS+ would handle - netgroups, userids, groups, passwords, POSIX fields, hosts, and a few other things.  Ubuntu doesn't easily serve this stuff, but as a client, it works well.  For the server, I'd setup a CentOS machine with FreeIPA as a replacement for NIS+.

Setting up NFS to mount HOME directories is pretty easy.

As for managing software across all the systems, this has been something trivially scripted for 40 yrs. These days, people seem to prefer using a DevOps tool like Ansible, Chef, Puppet, or one of the others.  I use Ansible for less than 500 systems because it has the lowest complexity and is easy to get started for someone with just a few years of Unix admin skills.

Should also point out that there isn't any GUI to make this stuff happen. That isn't the Unix way. There are how-to guides, however.

I don't know anything about LTSP, so cannot say whether it is a better solution for your needs or now. With 2 well-respected commenters recommending it, I'd definitely take a look.

---

