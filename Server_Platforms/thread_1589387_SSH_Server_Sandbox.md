---
title: "SSH Server Sandbox"
date: 2010-10-06
forum: Server Platforms
---

### Post by Ubentoo on 2010-10-06
I like to setup an SSH-Server on my desktop computer for remote access. Some time ago I found an article about doing this somehow in a sandbox such that possible break-ins go into the void. Does anybody know how this works and do I lose functionality when using the sandbox?Thanks a lot,Ubentoo

---

### Post by arrrghhh on 2010-10-06
Are you talking about [BasciChroot](https://help.ubuntu.com/community/BasicChroot)...?  Doesn't sound like it based on your description, but I'm not sure what you are describing.

---

### Post by amauk on 2010-10-06
it's probably easier to install something like denyhosts or fail2ban

These are daemons that monitor /var/log/auth.log, and if they detect suspicious activity (brute forcing SSH login, for example) they add that IP to /etc/hosts.deny which bans the IP from further connections

---

### Post by memilanuk on 2010-10-06
If your machine is behind a router with a firewall, and/or has a firewall on the local box itself, you can control or at least cut down on where you accept ssh connections from.  And if you use passwordless ssh (with keys)... it becomes very difficult for someone to break into your ssh login at all, at which point the whole 'sandbox' thing starts to seem like a wee bit of overkill.  An interesting exercise, though...

---

### Post by Ubentoo on 2010-10-07
Thank you very much, I think Basic Chroot was the thing I was looking for. Fail2ban is of course good against attackers, but in case of a successful intrusion a sandbox seems to be nice.

---

### Post by CharlesA on 2010-10-07
Instead of chrooting ssh, why not just use key authentication and disable password authentication, and leave it at that?

That would effectively prevent someone from authenticating with a password.

---

### Post by Jsdey on 2010-10-07
You might consider using port blocking that could be used to open and close port 22 in iptables

---

