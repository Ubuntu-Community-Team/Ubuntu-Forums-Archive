---
title: "LTSP Authentication help...please!"
date: 2010-04-19
forum: Server Platforms
---

### Post by NetmanDH on 2010-04-19
Hi All,

I just inherited an Ubuntu 8.10 server network where I have roughly 100 clients who log on via a diskless fat client.  They all log on fine.  When my predessor left he/she mucked something up (perhaps on purpose) so now new users added to the system cannot log on.  Newly added users appear in /et/passwd, but logon just gives 'username or password incorrect' messages.  I'm quite new to Ubuntu (i'm used to Windows servers) so go easy on me if it's something simple that i've missed.

There appears to be some sort of LDAP, PAM and all sorts of rubbish on there...also, when doing some checking (ltsp-update-image) there aren't any i386 images or anything - there is an hfi386 image file which contains another /etc/ file and another passwd file - is this the one that authenticates clients??

Help!

Cheers,

D.

---

### Post by ICEB3AR on 2010-04-19
ltsp uses ssh so you have to enable them, that they are able to log in on the terminal-clients.

Try the following: ```
sudo ltsp-update-sshkeys 
```

Best Regards

---

### Post by NetmanDH on 2010-04-20
Hi,

Thanks, but tried that - still no joy.  The new user has appeared in /etc/passwd but still cannot log on to a client PC.  I'll have a read about the SSH authentication process - but if you have any further ideas, i'd welcome them!

Cheers,

D.

---

### Post by sgiomlaireachd on 2010-11-17
After you update the sshkeys you also need to update the image.  Enter these commands on the server: 

sudo ltsp-update-sshkeys  
sudo ltsp-update-image 

After the image update is complete restart the clients so they download the new image.  I know this is an old post, but I hope this helps.

---

### Post by comp_parter on 2011-09-11
> 
After the image update is complete restart the clients so they download  the new image.  I know this is an old post, but I hope this helps.This was an old post but it helped me.  Thanks

---

