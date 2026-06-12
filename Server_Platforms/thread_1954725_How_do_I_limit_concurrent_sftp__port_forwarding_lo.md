---
title: "How do I limit concurrent sftp / port forwarding logins?"
date: 2012-04-08
forum: Server Platforms
---

### Post by Kyoku on 2012-04-08
I have ssh set up so my users can only access sftp and port forwarding, how can I limit the number of concurrent logins on a per user basis?

In my sshd_config I have UsePAM set to yes and in /etc/security/limits.conf I have:

username - maxlogins 1

I also tried:

username hard maxlogins 1

Neither of these works and the users can still log in multiple times.

---

### Post by bbl123 on 2012-11-30
Hi 

Have you found a solution yet? If not, let me know

---

### Post by chadk5utc on 2012-11-30
heres a good reference for ssh also discusses what your attempting:
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

