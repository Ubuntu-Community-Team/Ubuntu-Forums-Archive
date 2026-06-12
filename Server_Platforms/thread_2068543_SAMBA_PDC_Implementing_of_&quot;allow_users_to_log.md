---
title: "SAMBA PDC: Implementing of &quot;allow users to log on locally&quot; group policy"
date: 2012-10-09
forum: Server Platforms
---

### Post by hulk1st on 2012-10-09
Hi there,

as stated in the title, I would like to implement the group policy to allow a certain group of users to log on locally on a machine (and therefore deny another certain group of people to log on). I think on windows machines you can define a group policy, which can be applied to certain clients. The nice thing is, that I can do this on the server instead of doing it on the client machine. So I can quickly add or delete a user from the group that has access to the client machine without changing something on the client.

I tried to find a solution for this for several days now, but so far I was not able to it. Theoretically, samba 3 should be able to do this, but I'm not sure. Also I don't know wether I need to install LDAP for this...

Any ideas anyone?

Thanks in advance!

---

