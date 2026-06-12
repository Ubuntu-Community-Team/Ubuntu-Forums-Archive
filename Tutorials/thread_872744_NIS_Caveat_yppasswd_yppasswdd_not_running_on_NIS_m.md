---
title: "NIS Caveat: yppasswd: yppasswdd not running on NIS master host (&quot;localhost.localdomai"
date: 2008-07-28
forum: Tutorials
---

### Post by Krischu on 2008-07-28
I was seeking for a solution to the problem why I got constantly:

```
yppasswd: yppasswdd not running on NIS master host ("localhost.localdomain")
```

on my NIS (yp) clients.

All HOWTOs I could find so far, also in this [**forum**]("http://ubuntuforums.org/showthread.php?t=226437"),didn't lead to a solution. I followed everything given already in the HOWTOs to no avail.

Now I finally found the solution.
For some reason I don't know, ubuntu writes during installation
a line into /etc/hosts like

```
#
#
127.0.0.1 localhost mybox mybox.mydomain.com
#

``` 
(where mybox is the actual hostname that the computer has been given in DNS of mydomain.com).

This leads to confusion.
Changing the above to the more meaningful lines:
```
#
127.0.0.1 localhost
192.168.2.1 mybox mybox.mydomain.com
#
```

has immediately solved my problem after doing a

```
/usr/lib/ypinit -m

/etc/init.d/nis restart
```

(the latter on both, the server and the client)

---

### Post by TJCIB on 2008-12-03
Very nice!  Two things:

your last two commands should be 
```
sudo /usr/lib/yp/ypinit -m

sudo /etc/init.d/nis restart
```

I added the "sudo", but you were missing the /yp/ directory

Second, a question:
Any idea how to pass a forced password change on to NIS clients?

if I invoke
```
chage -d 0 username
```
It does not ask the user to change the password on login to a client, but it does request it if try to log in on a server.  I have tried rebuilding the maps and everything after invoke the command.  Nothing works so far.

The user, once logged in, is able to change a password via "yppasswd" so I know the daemon is running correctly.

---

### Post by meadmarc on 2012-02-05
Yes.

Apparently, 

make -C /var/yp 

will rebuild the password list, and force any changes you made at the server level to apply to clients.

But I still can't find a way to let my users change their own passwords, and can't even find yppasswd anywhere...

---

