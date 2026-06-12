---
title: "Centralize users' directories with sshfs?"
date: 2009-01-05
forum: Server Platforms
---

### Post by jamil5454 on 2009-01-05
Hello Ubuntu Community,

I'm trying to use sshfs on a few client machines to mount users' home directories from /home on the server.

In other words, I'm trying to centralize users' home directories on a single server and then have them mounted securely on bootup on each client.


I know I can add sshfs lines in /etc/fstab to mount a single user's home directory, but the user's private key won't be available before the mount (so mounting will be impossible?) and this will only mount that single user's homedir instead of all available in /home on the server.

I checked into tunneling NFS over a secure ssh tunnel but sshfs seems like it would be simpler and faster if I can get it to work.

I know I could put something like this in /etc/fstab:
```

sshfs#root@server:/home /home fuse defaults 0 0

```
This would use root's private key in /root/id_rsa but would the permissions be borked after doing so (i.e. would users be able to access their home directories?)


Thanks for the help!

---

### Post by HermanAB on 2009-01-05
In my experience mounting home directories on a central server is not worth the effort.  

That being said, note that NFS version 4 has encryption built in, though I haven't used that feature so I cannot vouch whether it works.

Cheers,

Herman

---

### Post by nkassi on 2009-01-06
What you need is a pam module. look at this article
[URL="http://www.debian-administration.org/articles/587"]
http://www.debian-administration.org/articles/587[/URL]

---

