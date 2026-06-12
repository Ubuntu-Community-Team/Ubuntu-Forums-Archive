---
title: "Cannot log in from xp via ssh to linux server"
date: 2009-02-25
forum: Server Platforms
---

### Post by donaldd on 2009-02-25
I've created a minimal Intrepid server for home use I can connect to it from an xp laptop via ssh using putty and the user created when doing the install, not root :-) 
I added a couple of users for my family, the problem is I cannot log into the server remotely with them although directly it's possible.

Appreciate if someone could point me in the right direction.
Regards,
Donald

---

### Post by JeppeM on 2009-02-25
Hey donald,

When you're on the server, do you get any messages in the /var/log/messages file when you try to login? You can test it by SSHing to the server and logging in with the login that works, and then type _tail -f /var/log/messages_. While you watch this log, open a new putty window and try to log in with the other users.

Also, could you verify that when you're logged in on the server, you are able to change to the other users? (command: _su username_, for example _su david_)

---

### Post by HermanAB on 2009-02-25
Another possibility:  Did you forward port 22 in your firewall to the target machine?

Test basic connectivity with telnet:
C:\> telnet remotemachineipaddress 22

You should get a server banner.  If not, then you have a network routing problem.

Cheers,

Herman

---

### Post by hictio on 2009-02-25
Is the sshd daemon running??

```

/etc/init.d/sshd status ENTER

```

You'll have to see something like:

```

 * sshd is running.

```

---

### Post by donaldd on 2009-02-25
doh! found problem needed to add user in the sshd_config file under Authentication AllowUsers

Thanks for all your replies.
Regards,
Donald

---

