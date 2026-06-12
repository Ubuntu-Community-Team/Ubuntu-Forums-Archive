---
title: "Can not login - Login timed out after 60 seconds"
date: 2010-07-14
forum: Server Platforms
---

### Post by dara168 on 2010-07-14
Dear friends,

I just installed Ubuntu Server 10.04 LTS on Dell Optiplex 380.
Everything works just fine.
But this evening, when I tried to boot my server it hanged for about 3 minute with

```
Checking battery state ...
```After that come the login. After I inputed my user and password it hanged again for 1 minute than it displayed a message saying

```
Login timed out after 60 seconds.
```I tried to login again and again but end up with the same error message.

I was sure i typed the correct user and password.

I can not log into my box now.

Any help please?

---

### Post by tekkidd on 2010-07-14
Well assuming you are trying to do a remote login you might want to check that the connection is not being tied up (as in doing transfers across the network and so forth)

---

### Post by dara168 on 2010-07-15
hello,

Thank you for your reply.

No I am not login through network.

I tried to login to my server directly!

any idea?

---

### Post by kenga on 2011-08-03
The same issue. 

After reboot, unable to login to Ubuntu Server 10.04.2 LTS console, both locally and remote, for a while. On console there is an 'Login timed out after 60 seconds' error after entering password + 60 seconds, remote ssh sessions are just timing out. 

After some time (several minutes, five or more), system allows to login without any trace of problem.

The problem was more often before I've disabled pam_motd.so at pam.d.

May be this is related somehow to defaultly configured pam_winbind module.

---

### Post by ian.d.rossi on 2011-11-10
Kenga,

Did you have any success in investigating the pam_winbind module? I am having this same problem on a Virtualbox instance of 10.04 and feel strongly that it's an Ubuntu problem and not Virtualbox.

If you could share your solution, my team and I would really appreciate it.

Thanks!

Ian D. Rossi

---

