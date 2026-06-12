---
title: "create user by running script through browser"
date: 2013-09-05
forum: Server Platforms
---

### Post by kptsuresh on 2013-09-05
We have 1000 clients running ubuntu 13.04 OS in an institute, (cloned all using clonezilla), and created two users 
1. user1 (sudoer) 2. user2 (limited).
 we have given password for the user2 only to restrict the users not to  use sudoer related commands in their systems. Now we have got the  problem in user2 i.e. earlier implemented user quotas in user2 and gave  wrong size for the user2, so unable to store any single file.
So I request you to guide me is there any way to create another user in  those systems without giving sudoer password(user1), like executing any  shell program from firefox browser with sudoer/root privileges. 

Thank you.

---

### Post by CharlesA on 2013-09-05
Do you know how the quotas were assigned initially? I haven't used quotas on my home or work server, so I'm not really sure how you modify them, but that would probably be the best thing to do.

---

### Post by TheFu on 2013-09-05
I'd follow CharlesA;s advice, but to create new users ...
* useradd
* mkdir for the HOME
* chown for the HOME
* passwd to set an initial password
That should be it.

But, if you have 1000 clients, you really should be using something like Salt or Puppet or **Ansible** to manage them all.  Doing the same thing across 1000 systems with ansible is simple,

---

