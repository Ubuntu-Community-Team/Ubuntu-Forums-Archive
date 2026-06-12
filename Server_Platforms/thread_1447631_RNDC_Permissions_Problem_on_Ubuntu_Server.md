---
title: "RNDC Permissions Problem on Ubuntu Server"
date: 2010-04-05
forum: Server Platforms
---

### Post by debianfan on 2010-04-05
I am running Ubuntu server 9.10 and running into issues with the  rndc.key in my Bind 9 configuration.  In particular, I believe I have an  RNDC permissions error that I am trying to figure out how to resolve  safely.

Here are the details. After configuring my Bind 9 server and restarting  the daemon, the following error message appeared:

```

 * Stopping domain name service... bind9
rndc: connect failed: 127.0.0.1#953: connection refused
   ...done.
 * Starting domain name service... bind9
   ...fail! 
```So I checked the /var/log/daemon.log messages to see what was  going on, which showed it to be a permissions problem:

 ```

03-Apr-2010 21:08:56.880 loading configuration from '/etc/bind/named.conf'
03-Apr-2010 21:08:56.880 /etc/bind/named.conf:8: open: /etc/bind/rndc.key: permission denied
03-Apr-2010 21:08:56.880 loading configuration: permission denied
03-Apr-2010 21:08:56.880 exiting (due to fatal error) 

```I regenerated the key using this command, but the problems  persisted regardless:

 ```

sudo rndc-confgen -r /dev/urandom -a 

```Does anyone have any ideas on how to straighten out this  permissions issue and ensure it does not arise again. I think it is an  apparmor issue but have no concrete idea on how to fix it.  From all the  flack I have seen about this on the ubuntu forums I think it may be a  bug.  I am just hoping there is a workaround.  Thank you for any help  you can provide.

---

### Post by terazen on 2010-04-06
I had this problem before and after recreating the key a reboot fixed the error.

---

### Post by debianfan on 2010-04-06
I will try that, I recreated the key and then restarted bind a couple of times.  I will try to recreate the key and then reboot (rather than restart bind) to see if that works.

---

