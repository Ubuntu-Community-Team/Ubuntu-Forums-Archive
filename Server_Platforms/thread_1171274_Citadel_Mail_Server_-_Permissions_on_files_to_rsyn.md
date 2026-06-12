---
title: "Citadel Mail Server - Permissions on files to rsync to backup server"
date: 2009-05-27
forum: Server Platforms
---

### Post by greavette on 2009-05-27
Hello,

I've successfully installed Citadel easy-install on an Ubuntu Hardy VM in VMware.  Works like a charm!

I've searched the Citadel forums and the Ubuntu forums and I've successfully used this rsync command to copy my /usr/local/citadel folder from my primary mail server to my backup mailserver (which is also Ubuntu Hardy VM in VMware):

rsync -va /usr/local/citadel/ 192.168.x.x:/usr/local/citadel/  

 
I found that in order to issue this rsync command though, I had to login to my primary mail server as root.  If I tried logging in with my regular user id and elevate my privileges using "sudo", I received rsync permission errors.

What have others here in the community done to get the above rsync command to work? Do you also use root access, or did you change permissions on the folder?

What I'd like to eventually do is setup an Cron task to rsync the citadel folder to my backup server on a nightly basis to ensure we always have a mail server at the ready.

Your insight as to what you did would be greatly appreciated!

Thanks!

---

### Post by albinootje on 2009-05-27
> **greavette said:**
> 
What have others here in the community done to get the above rsync command to work? 

For making remote backups with rsync I use ssh keys, and restrictions (on name + ip) with AllowUsers in sshd_conf.

---

### Post by greavette on 2009-05-27
Hello albinootje,

Thanks very much for the reply to my question.  I've setup ssh keys on my server as well.  I thought I used the AllowUsers option in sshd_conf, but now I'm not so sure.  I'll give this a try.

Thanks!

---

