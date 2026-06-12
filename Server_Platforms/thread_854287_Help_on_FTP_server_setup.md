---
title: "Help on FTP server setup"
date: 2008-07-09
forum: Server Platforms
---

### Post by thumpr99 on 2008-07-09
I just installed the Ubuntu server and would like to setup a FTP site for users to login with username & password.

The Ubuntu machine is located on a Windows network (I changed the WORKGROUP to be the same as the Windows machines).

I want only users that I have specified to have access to upload & download files.

I would like the most simple and secure way to setup the machine.

Your help would be much appreciated......

---

### Post by derekroyce on 2008-07-09
Curious, I'm working on the same thing.

What did you do to set up your server to the WORKGROUP?

---

### Post by windependence on 2008-07-09
```
sudo apt-get install vsftp
```

-Tim

---

### Post by derekroyce on 2008-07-15
This helped me set mine up perfect.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=HOWTO%3A+Setup+Samba+peer-to-peer+Windows]("http://ubuntuforums.org/showthread.php?t=202605&highlight=HOWTO%3A+Setup+Samba+peer-to-peer+Windows")

---

### Post by chuck jessup on 2008-07-16
> **windependence said:**
> ```
sudo apt-get install vsftp
```

-Tim



-- 
$E: couldn't find package vsftp

any idea on how to direct dl it?

Thanks Jesse Fender

---

### Post by windependence on 2008-07-16
Try doing a 

```
sudo apt-get update
```


and then try the command again.

-Tim

---

