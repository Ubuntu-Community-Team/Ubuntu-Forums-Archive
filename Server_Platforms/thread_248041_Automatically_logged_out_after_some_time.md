---
title: "Automatically logged out after some time?"
date: 2006-08-31
forum: Server Platforms
---

### Post by wilspang on 2006-08-31
How can inactive users be automatically logged out after some 
time (via SSH and SAMBA)? 



/Michael Wilspang

---

### Post by dragze on 2006-08-31
Ok well to timeout ssh connections it is very simple:

```
sudo nano /etc/ssh/ssh_config
```

and uncomment the following line:

> #   ConnectTimeout 0

and add a timeout length (not sure if it is in seconds or minutes but one assumes that it is in seconds), so the above line should now look something like this:

>     ConnectTimeout 30

And that is it just press Ctrl+X folowed by Y to save the changes made.


As for timing out samba connections, as far as i am aware this is not possible + most likely pointless because as im sure ur aware samba is used to connect to windows shares and if somebody connects/mounts an smb share yes it is possible to find out who is connected and what directory there in but there is no way of telling whether they are actually active. I could be wrong mind you but that is just my understanding.

Hope this helps!

Kind Regards,
dragze.

---

### Post by wilspang on 2006-08-31
Thanks very much for the SSH tips!
You're probably right regarding the SAMBA issue.

/Michael Wilspang

---

