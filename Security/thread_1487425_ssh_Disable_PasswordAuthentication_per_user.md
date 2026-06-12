---
title: "ssh: Disable PasswordAuthentication per user"
date: 2010-05-19
forum: Security
---

### Post by lavinog on 2010-05-19
I have a server that will be used for forwarding ports.
The users will have no reason to use the shell.
I set up key pairs for the users, but I would like to the server to not prompt for a password if it refuses the key.
I can set PasswordAuthentication to no in the sshd config file, but I would still need to be able to login with a password.

Is there a way to configure this per user?

---

### Post by lavinog on 2010-05-19
I removed the users' passwords which prevents logging in with a password.  So I guess I can consider this solved.

---

### Post by bodhi.zazen on 2010-05-19
Aye, just lock the user account

```
sudo passwd '!' user
```

The user can still log w/ other means, such as ssh /w a key.

You would prevent shell access by using "forced commands" , basically you set what commands can be run w/ the key.

In addition if you wish to prevent shell access set the shell to /bin/false .

[http://oreilly.com/catalog/sshtdg/chapter/ch08.html](http://oreilly.com/catalog/sshtdg/chapter/ch08.html)

---

### Post by lavinog on 2010-05-20
> **bodhi.zazen said:**
> Aye, just lock the user account

```
sudo passwd '!' user
```

The user can still log w/ other means, such as ssh /w a key.

You would prevent shell access by using "forced commands" , basically you set what commands can be run w/ the key.

In addition if you wish to prevent shell access set the shell to /bin/false .

[http://oreilly.com/catalog/sshtdg/chapter/ch08.html](http://oreilly.com/catalog/sshtdg/chapter/ch08.html)

Good info, thank you for taking the time to answer.

---

### Post by bodhi.zazen on 2010-05-20
> **lavinog said:**
> Good info, thank you for taking the time to answer.

No problem, I like to play with SSH , there are a ton of [s]advanced[/s] geeky things you can do with it.

---

### Post by lumbricus on 2010-12-18
I had a slightly different problem and found this thread now when googeling for the solution.

I want to disable password login through SSH, because I'd like to have a simple password and to login through SSH with a public key. But I can't set PasswortAuthentication to no, becauser there are other Users who want to use their passwords also to login through SSH nor can I lock my password (passwd -l) because I want to use it to login locally and for sudo.

The solution is quite simple:
Match User myusername
        PasswordAuthentication no


Put these lines to the end (!) of the file /etc/ssh/sshd_config
and reload the SSH config: sudo /etc/init.d/ssh reload

Manual:
[http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config&sektion=5](http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config&sektion=5)

---

