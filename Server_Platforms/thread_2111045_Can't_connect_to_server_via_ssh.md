---
title: "Can't connect to server via ssh"
date: 2013-01-31
forum: Server Platforms
---

### Post by lazarojhr16 on 2013-01-31
I just installed a second server in my home and I guess I did something wrong, but can't figure out what. I can connect to the server via terminal with ssh but can't connect through the gui(Dolphin), I'm using kubuntu 64bit. I can connect to my other server just fine. I can post anything you guys need me to post. Thanks for the help in advance.

---

### Post by papibe on 2013-01-31
A little confused. You can connect using ssh, but not using Dolphin (using stfp I guess?).

Is that right?

Regards.

---

### Post by lazarojhr16 on 2013-01-31
> **papibe said:**
> A little confused. You can connect using ssh, but not using Dolphin (using stfp I guess?).

Is that right?

Regards.

yes. I'm not sure what the problem is. any ideas?

by the way its ubuntu server 12.04

---

### Post by lazarojhr16 on 2013-01-31
I got my laptop running ubuntu and everything worked. Went back to my kubuntu pc and tried using ( fish ) that worked. sftp doesn't work. I've never used fish, whats the difference?

---

### Post by papibe on 2013-01-31
Could you post the result of this command on the **server**?
```
grep -i sftp /etc/ssh/sshd_config 
```
Regards.

---

### Post by lazarojhr16 on 2013-02-17
> **papibe said:**
> Could you post the result of this command on the **server**?
```
grep -i sftp /etc/ssh/sshd_config 
```Regards.

Hey sorry I had no internet, but here is the output.
```
 Subsystem sftp /usr/lib/openssh/sftp-server 
```

---

### Post by papibe on 2013-02-17
Thanks. It looks OK.

Try adding a network location using the following urls:

First:
```
sftp://yourserver
```
Or this:
```
sftp://user@yourserver
```
Or this other one:
```
sftp://user:password@yourserver
```
If that doesn't work, try the same 3 examples above, but instead of sftp, try using the fish url:
```
fish://...
```
Let us know how it goes.
Regards.

---

### Post by lazarojhr16 on 2013-02-18
> **papibe said:**
> Thanks. It looks OK.

Try adding a network location using the following urls:

First:
```
sftp://yourserver
```
Or this:
```
sftp://user@yourserver
```
Or this other one:
```
sftp://user:password@yourserver
```
If that doesn't work, try the same 3 examples above, but instead of sftp, try using the fish url:
```
fish://...
```
Let us know how it goes.
Regards.

Went back and tried it again. It all works now, not sure I'm guessing it was because during the time I was having issues with my internet. It all works now. Thanks will be closing this thread.

---

