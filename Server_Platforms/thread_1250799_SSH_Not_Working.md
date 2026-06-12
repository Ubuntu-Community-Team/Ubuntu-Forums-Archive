---
title: "SSH Not Working"
date: 2009-08-26
forum: Server Platforms
---

### Post by PadawanGeek on 2009-08-26
I was messing around with some settings about the SSH port and accidentally messed up my server. Now SSH won't load. I got an error about unprotected key files, so I tried recreating the files with: ```
sudo ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
sudo ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key  
```

Now when I type ```
/etc/init.d/ssh reload
``` it comes out with ```
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
* Reloading OpenBSD Secure Shell server's configuration sshd
```

Will someone please help? I am getting desperate.

---

### Post by jocampo on 2009-08-26
Try this and see if fix your problem (please notice the SUDO command)

```
sudo /etc/init.d/ssh restart
```

If you're still getting the error, look in /etc/ssh and see if there is a host key

```
ls -l /etc/ssh/ssh_host_rsa_key
```

You should get some information, if not ... try this ...

```
sudo /usr/bin/ssh-keygen -t rsa1 -f /etc/ssh/ssh_host_key -N
sudo /usr/bin/ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key -N 
sudo /usr/bin/ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N
```

Restart SSH using sudo and try again ...

---

### Post by PadawanGeek on 2009-08-27
no luck...

also, ```
sudo /usr/bin/ssh-keygen -t rsa1 -f /etc/ssh/ssh_host_key -N
``` didn't work.

Any other ideas?

---

### Post by jocampo on 2009-08-27
> **PadawanGeek said:**
> no luck...

also, ```
sudo /usr/bin/ssh-keygen -t rsa1 -f /etc/ssh/ssh_host_key -N
``` didn't work.

Any other ideas?

deleted the keys in /etc/ssh/ and reboot ... verify SSH is up this time ...

---

