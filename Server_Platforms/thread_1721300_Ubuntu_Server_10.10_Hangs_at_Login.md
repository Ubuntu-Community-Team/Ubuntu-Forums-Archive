---
title: "Ubuntu Server 10.10 Hangs at Login"
date: 2011-04-04
forum: Server Platforms
---

### Post by idny on 2011-04-04
Hi,

I have been running Ubuntu Server 10.10 for a while now, The server is running file itself
But...

When I login using SSH the server hangs at the login screen,
I enter my username, hit enter and then it hangs for around 2 mins before prompting for the password.
I have checked active sessions using "w" and there is none active except for the one im using.

What could be causing this?
Thanks

---

### Post by falko on 2011-04-04
Try this: [http://llbb.wordpress.com/2007/07/11/ssh-takes-exactly-1-minute-20-seconds-or-80-seconds/](http://llbb.wordpress.com/2007/07/11/ssh-takes-exactly-1-minute-20-seconds-or-80-seconds/)

---

### Post by idny on 2011-04-07
Thanks, I disable gssapi-with-mic authentication in /etc/ssh/sshd_config: # GSSAPI options GSSAPIAuthentication no #GSSAPIAuthentication yes GSSAPICleanupCredentials no #GSSAPICleanupCredentials yes

But it doesn't seem to have fixed the problem.
I still get the login hang.
And more ideas?

---

### Post by idny on 2011-04-11
bumping for help...

---

### Post by idny on 2011-04-20
I hate bumping threads.
But i need help on this.

---

### Post by usatonycuba on 2011-04-20
> **idny said:**
> bumping for help...

> **idny said:**
> I hate bumping threads.
But i need help on this.
then don't 

> **idny said:**
> Hi,

I have been running Ubuntu Server 10.10 for a while now, The server is running file itself
But...

When I login using SSH the server hangs at the login screen,
I enter my username, hit enter and then it hangs for around 2 mins before prompting for the password.
I have checked active sessions using "w" and there is none active except for the one im using.

What could be causing this?
Thanks
The OpenSSH server will log its information to this log file, including informational messages, errors, and user logins. could you post the result of it?
> /var/log/auth.log

---

