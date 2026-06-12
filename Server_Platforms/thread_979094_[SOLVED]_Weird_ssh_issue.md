---
title: "[SOLVED] Weird ssh issue"
date: 2008-11-11
forum: Server Platforms
---

### Post by ARhere on 2008-11-11
My server at home is running ssh service and I have tested it by logging on using a different machine on the same router, everything works fine.  But when I try to log in form my office I keep getting...
```
ar****@76.**.***.174's password: 
Permission denied, please try again.
ar****@76.**.***.174's password: 
Permission denied, please try again.
ar****@76.**.***.174's password: 
Permission denied (publickey,password).
```

I am positive I am using the correct password and I have double checked that my firewall is forwarding port 22 to the server.
***NOTE:** I masked my user name and IP in the quote above for my privacy.  I am not actually getting astricks!*  ;-)

-AR

---

### Post by Iowan on 2008-11-11
I'm certainly no expert...
Firewall blocking port 22?
/etc/ssh/ssh_config limit to local network?

---

### Post by hictio on 2008-11-11
I would double or triple check your username/ password, since you are getting up to a password prompt, a network (and firewall, includes TCP Wrappers) problem gets ruled out.

Try executing that ssh session from your work issuing a multitude of '-vvv' to increase the verbosity, perhaps you can get something on the error message.

You aren't trying to login as root, right? :D
Another option, thin one, is checking the '/etc/ssh/sshd_config' file, for the 'AllowUsers' directive, but that's far fetched, specially if you haven't play around with it.

---

### Post by hictio on 2008-11-11
Another thing, if gain access to the box remotely, or when you get home, be sure to check the log file '/var/log/auth.log', looking for lines with these:
```

pam_unix(sshd:auth): authentication failure

```

---

### Post by ARhere on 2008-11-11
> **hictio said:**
> Another thing, if gain access to the box remotely, or when you get home, be sure to check the log file '/var/log/auth.log', looking for lines with these:
```

pam_unix(sshd:auth): authentication failure

```

Ah HA!  I found the problem thanks to you.
```
Nov 11 15:46:57 Fileserv sshd[13591]: Invalid user areynolds from 63.145.92.242
Nov 11 15:46:57 Fileserv sshd[13591]: Failed none for invalid user areynolds from 63.145.92.242 port 2942 ssh2
Nov 11 15:47:01 Fileserv sshd[13591]: pam_unix(sshd:auth): check pass; user unknown
Nov 11 15:47:01 Fileserv sshd[13591]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=63-145-92-242.dia.static.qwest.net 
Nov 11 15:47:03 Fileserv sshd[13591]: Failed password for invalid user areynolds from 63.145.92.242 port 2942 ssh2
Nov 11 15:47:30 Fileserv sshd[13591]: pam_unix(sshd:auth): check pass; user unknown
Nov 11 15:47:32 Fileserv sshd[13591]: Failed password for invalid user areynolds from 63.145.92.242 port 2942 ssh2
Nov 11 15:47:44 Fileserv sshd[13591]: pam_unix(sshd:auth): check pass; user unknown
Nov 11 15:47:45 Fileserv sshd[13591]: Failed password for invalid user areynolds from 63.145.92.242 port 2942 ssh2
Nov 11 15:47:45 Fileserv sshd[13591]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=63-145-92-242.dia.static.qwest.net 
Nov 11 15:57:22 Fileserv sshd[13603]: Invalid user areynolds from 63.145.92.242
Nov 11 15:57:22 Fileserv sshd[13603]: Failed none for invalid user areynolds from 63.145.92.242 port 32847 ssh2
Nov 11 15:57:26 Fileserv sshd[13603]: pam_unix(sshd:auth): check pass; user unknown
Nov 11 15:57:26 Fileserv sshd[13603]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=63-145-92-242.dia.static.qwest.net 
Nov 11 15:57:28 Fileserv sshd[13603]: Failed password for invalid user areynolds from 63.145.92.242 port 32847 ssh2
Nov 11 15:57:35 Fileserv sshd[13603]: pam_unix(sshd:auth): check pass; user unknown
Nov 11 15:57:37 Fileserv sshd[13603]: Failed password for invalid user areynolds from 63.145.92.242 port 32847 ssh2
Nov 11 15:57:46 Fileserv sshd[13603]: pam_unix(sshd:auth): check pass; user unknown
Nov 11 15:57:48 Fileserv sshd[13603]: Failed password for invalid user areynolds from 63.145.92.242 port 32847 ssh2
Nov 11 15:57:48 Fileserv sshd[13603]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=63-145-92-242.dia.static.qwest.net 
```

My username for both the server and box I was testing it with are the same, but my username for work is different and it looks like my work username was passed to the server.  Since no user exist on my server with that name, it fails.

What I don't get is it never asks a user name.  How do I correct that?

-AR

***NOTE:** Yes, I noticed my name and IP is displayed above.  I guess I am too lazy or to trusting to erase it.  Meh!*

---

### Post by oneloveamaru on 2008-11-11
What are you using to SSH into the box? Putty or on another Linux box with a console? I always get in the habit or putting in the user name. I always do "ssh [email]username@myipaddressordomain.com[/email]"

---

### Post by hictio on 2008-11-11
Ok, to avoid typing repetitive info, that is pron to error, you should use the '~/.ssh/config' file, besides, that file will be used not only for ssh, but also for scp as well.

There are a lot of options, but here is a little example:
```

Host work
        HostName serverat.work.com
        User corporate.username

Host home
        HostName serverat.home.dydns.org
        Port xxxxx
        User myregulauser

```
 
So, you just type 'ssh work' or 'ssh home' and ssh takes care of the rest.
Take a look at the man page for more options.

---

### Post by ARhere on 2008-11-11
I am looking at the man page now to try and figure out how to set my server to always ask for username along with password, which is what I prefer.

It was like this at my last job, but I don't know how that was set up.

-AR

---

### Post by oneloveamaru on 2008-11-11
Are you SSH'ing from an SSH client like Putty or are you SSH'ing from a console in Linux?

---

### Post by ARhere on 2008-11-11
> **oneloveamaru said:**
> Are you SSH'ing from an SSH client like Putty or are you SSH'ing from a console in Linux?

both

-AR

---

### Post by hictio on 2008-11-11
> **ARhere said:**
> I am looking at the man page now to try and figure out how to set my server to always ask for username along with password, which is what I prefer.

It was like this at my last job, but I don't know how that was set up.

-AR

If might ask...
Why would like this?  I have seen plenty of Logwatch logs with the password typed as username, besides, why bother? Let the machine do the work for you.

---

### Post by oneloveamaru on 2008-11-11
If you are using Putty, then it should ask for a username when you try and log in. If you are SSH'ing from a console window in Linux, it defaults to the username you are logged in as, unless you put in a -l or do the username@ before the IP or domain name. At your old job, could you SSH from a Linux console and it still ask for a username? I've never seen that before, only from Putty.

---

### Post by ARhere on 2008-11-12
> **hictio said:**
> If might ask...
Why would like this?  I have seen plenty of Logwatch logs with the password typed as username, besides, why bother? Let the machine do the work for you.

i see it as a extra step to help with security.  Someone has to guess username along with password.

[quote=oneloveamaru]If you are using Putty, then it should ask for a username when you try and log in. If you are SSH'ing from a console window in Linux, it defaults to the username you are logged in as, unless you put in a -l or do the username@ before the IP or domain name. At your old job, could you SSH from a Linux console and it still ask for a username? I've never seen that before, only from Putty.[/quote]

Honestly I don't know.  Maybe it was putty but I know I was logging onto remote systems from a Fedora Core. But I guess using -l is not a big deal.

Thanks everyone!

-AR

---

