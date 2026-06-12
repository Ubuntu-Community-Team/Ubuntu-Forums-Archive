---
title: "How to implement forced commands in SSH"
date: 2011-01-05
forum: Security
---

### Post by ScottTParker on 2011-01-05
I am trying to set up an automatic backup using rsync and a publickey SSH, which requires using an empty password on the private key.  I would like to lock down the key on the server so that it can only run rsync, but my attempts to use a forced command (or any other option such as no-port-forwarding) do not appear to have any effect when I run ssh -v.
I am currently debugging using the following line in  ~/.ssh/authorized_keys
```
command="/bin/echo goodbye world" ssh-rsa [key string] comment
```but when I connect, it opens up an interactive command prompt and does not display the "goodbye world" that I expect.


I am running an OpenSSH server on Ubuntu 10.04

---

### Post by ScottTParker on 2011-01-05
OK I got it solved now.  There were duplicate keys in the authorized_keys file.  Well, sort of.  The comments were different, but the key itself was the same.  Strange though, since one was generated using PuTTy's key generator, and one was generated using OpenSSH's ssh-keygen (not that I really expect either one of these tools to create a duplicate key anyway).

---

### Post by bodhi.zazen on 2011-01-05
Hard to tell from the (little) information you posted. My guess is that you are not logging in with the key.

When you use that command the session run your echo and then close. You have not included any options for any of the other limitations you mention.

The syntax would be something like:

command=”rsync&#8243;,no-port-forwarding,no-agent-forwarding,no-X11-forwarding,no-pty

Several detailed how-tos on this

[http://www.debianhelp.co.uk/rsync.htm](http://www.debianhelp.co.uk/rsync.htm)

[http://troy.jdmz.net/rsync/](http://troy.jdmz.net/rsync/)

---

