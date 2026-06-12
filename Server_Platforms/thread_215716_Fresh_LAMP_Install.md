---
title: "Fresh LAMP Install"
date: 2006-07-14
forum: Server Platforms
---

### Post by Sajji on 2006-07-14
Guys,

On a fresh LAMP install, I cannot seem to login using MySQL Admin from a remote machine.  I can SSH into my server and login to MySQL...but from the same client box, the Admin utility can't connect.  Any firewall issues, maybe?  If so, what do I need to do to open it up?

Thanks,

Saj

---

### Post by Sajji on 2006-07-14
I fixed the problem.  Just in case anybody else is having the same problem...here was my solution.

I installed fresh LAMP Server.  I'm able to connect to the database fine both on the server and from a remote MAC using ssh.  I wanted to use the MySQL graphical utility to connect from my MAC to the MySQL database.  I wasn't having much luck.  The Admin kept giving me error 2003.

So on my LAMP Server, the config file for MySQL located under /etc/mysql/my.cnf contained a line that said:

bind-address = 127.0.0.1

I had to put in the actual IP address of the LAMP Server.

I restarted the database

From my MAC, I opened MySQL administrator and entered the IP address of my LAMP Server, login id and password (couldn't use root - created a new ID) and it worked fine.

This seems like an obvious first step...why isn't this in the documentation?

---

### Post by cocotu on 2006-07-14
Sajii, I'm getting something similar. I'm getting "Access Denied". I'm trying to user my root account with a blank password. I went to the sshd_config and change the value of ALLOWBLANKPASS yes or something similar. I'm using Putty to connect to my LAMP here at work. I'm able to ping the LAMP machine a vice-versa. What other settings do I have to change or do??

---

### Post by DrSturgeon on 2006-07-15
cocotu, sajji was talking about not being able to connect to the server via mysql.  It sounds like you're having trouble logging in with ssh (putty)?

You should never ever ever ever have a root account with a blank password.  The way to fix this problem is not to configure a security hole in ssh; the way to fix this problem is to set a root password.

Are you sure you even have the root account enabled?  It isn't by default in ubuntu.  Try logging in with a normal user account.

And finally, I don't think ssh by default will let you log in as root.  There is a configuration option to change that, but that creates a pretty big security hole.  The proper procedure is to use a normal account to log in, and then use sudo (or, if you must, su) for privelege escalation.


---

Now, if instead you're talking about the mysql root account, it shouldn't have a blank password either.  You probably want to set one (I think in the mysql config).  Then pretty quickly, you want to add another mysql account so you aren't using root.  The easiest way to manage mysql is with phpmyadmin:

```
sudo aptitude install phpmyadmin
```

Then browse to [http://yourserver/phpmyadmin/](http://yourserver/phpmyadmin/) and log in.

Hope this helps.

---

### Post by cocotu on 2006-07-24
Thanks Dr. I got the ssh working. Yes, after I installed the LAMP server the only acct. available was root.  During the process of installation I was not asked to create a user name or create any password for the root acct.  When I installed LAMP the only way to get in was by using root and a blank password.

Thanks...

---

### Post by az on 2006-07-24
> **Sajji said:**
> 
This seems like an obvious first step...why isn't this in the documentation?

It's not in the readme in /usr"share/doc/mysql-server?

---

