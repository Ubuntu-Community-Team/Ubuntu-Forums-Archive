---
title: "Restrict Python to untrusted users"
date: 2007-03-16
forum: Server Platforms
---

### Post by cookfromfrozen on 2007-03-16
I have a server that allows remote shell access.  Remote users who connect are in a group called "untrusted" and that is limited through /etc/security/limits.conf.  They are limited to 15 processes.

Regular Bash forkbombs etc do not work, but we are being repeatedly DoS'd with the following Python command:

```
python -c 'while 1: __import__("os").fork()'
```

Load averages rise to 50-60+ as all the processes are being killed.  Sometimes this will cause every service to freeze, though the system will still respond to pings.  SSH stops working so new users cannot log in.

We have banned IPs/accounts in question but they keep coming back using Tor.  Is there a way to stop this, if not, how would I go about stopping people in the untrusted group from executing python.  Obviously I cannot uninstall python as the system depends on it.

thank you

---

### Post by louis_nichols on 2007-03-16
hm... I'm no expert, but I have one idea.

you could try just modifying permissions for the python executable. Set its owner to a user in group "untrusted" and then set permissions to 750 or something like that.

---

### Post by name7ess on 2007-03-16
Strange problem, you could restrict the access to /usr/bin/python, but the users would probably install it then by themself. However if you can dos it with python, then i think you can do it with any other programm too. Can you post your limits.conf?

---

