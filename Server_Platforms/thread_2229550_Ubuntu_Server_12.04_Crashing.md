---
title: "Ubuntu Server 12.04 Crashing"
date: 2014-06-13
forum: Server Platforms
---

### Post by k0koS on 2014-06-13
Hello,

Last days i am facing the above problem.
I am running a ubuntu server 12.04. In the server run Nginx, Mysql, and Liferay6.1.

Every day when i go to login to my system using ssh, when i enter username, password and login to system.
I get these messages:
You are required to change your password immediately (password aged)
WARNING! Your password has expired
You must change password now and login again
Changing password for root.
(current) UNIX password:

And blocking there. I cannot change password, i cannot do nothing. Server need restart to work again, and to login again.
I check if there is any password or Account Expiration date, but all say

Password expires                                        : never
Password inactive                                       : never
Account expires                                         : never

Have any ideas how to fix it;

Thank you,
Konstantinos

---

### Post by TheFu on 2014-06-13
My first guess is that your machine is hacked and owned.  Time to start doing some auditing of your offsite logs and odd changes in the daily backups.  I suspect your login program has been replaced and the first time you entered the root password, it was all over.  

The prompts appear highly suspicious to me - it isn't like you should be logging in as root anyway.

This might help understand what you are up against:  [http://draios.com/fishing-for-hackers/](http://draios.com/fishing-for-hackers/)

Of course, it could be something simple like the disk is corrupt and mounted read-only. Fix the corruption.

---

### Post by k0koS on 2014-06-14
Thank you for your reply.

The Access on the machine is only via Pulbic Key Authentication, and not permit directly root access to the machine via SSH... The only thing that i saw in the log files /var/log/auth.log is that someone brute force me to gain access via root.Also it does not happen every day. May take 1-2 days to happen or more.

I do not believe that server is compromised. I think the problem is some disk corruption.
What to you thing?

---

### Post by thnewguy on 2014-06-14
You said it is not possible to login as root, but the text in your first post clearly shows you are being prompted to change the root password. So, eiher you are trying to login as root and that is why your login is failing, or your system has been comprimised and the attacker is fishing for your password. If rebooting the machine causes you to be able to login normally without the weird prompt, but then the reset prompt appears again later, then your server has almost certainly been compromised and you should re-install.

---

