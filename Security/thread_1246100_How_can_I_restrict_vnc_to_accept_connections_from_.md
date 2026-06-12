---
title: "How can I restrict vnc to accept connections from localhost only?"
date: 2009-08-21
forum: Security
---

### Post by sefs on 2009-08-21
I tried putting -localhost=1 in the server_args or the /etc/xinetd.d/Xvnc but no cigar.

Any help is appreciated.

Thanks.

---

### Post by XCan on 2009-08-21
I'm not familiar with the config file you're trying to edit. But wouldn't it be easier if you simply configured IPtables, like GUFW? I simply enabled UFW, and that automatically closed down any access to my VNC port from the outside, only way to access it is through tunnel.

---

### Post by cariboo on 2009-08-21
In order for changes to config files to take place, you have to restart the service. So if you stop vino and restart it, your changes should take affect.

---

### Post by sefs on 2009-08-21
> **XCan said:**
> I'm not familiar with the config file you're trying to edit. But wouldn't it be easier if you simply configured IPtables, like GUFW? I simply enabled UFW, and that automatically closed down any access to my VNC port from the outside, only way to access it is through tunnel.


Yes that could be done, but there is no harm in some extra hardening.

Thanks.

---

### Post by sefs on 2009-08-21
> **cariboo907 said:**
> In order for changes to config files to take place, you have to restart the service. So if you stop vino and restart it, your changes should take affect.


It's VNC4Server, and I've been restarting it but can't seem to get it right.

How i restar it is like this...

```

sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start

```

I've even rebooted to be sure but just can't get it to work.  

the -localhost param is there in the help file but it just is not working or I am using it wrong.

---

