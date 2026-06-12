---
title: "Failed to use functions in webmin - Ubuntu 6.1."
date: 2008-01-14
forum: Server Platforms
---

### Post by newppl2 on 2008-01-14
I am a new comer and found that when open webmin and check some information. many error message come out.

 It is running in DELL Poweredge server.

After login in webmin, I want to check Samba setting or other server functions.

It prompted below error messages as examples :

Failed to write to /etc/webmin/logrotate/version when closing : No space left on device

Failed to create temp directory /tmp/.webmin

Failed to save log : Failed to write to /etc/syslog.conf when closing : No space left on device

Failed to write to /etc/webmin/samba/version when closing : No space left on device

Failed to write to /etc/webmin/sshd/version when closing : No space left on device

I check the disk space is sufficient (250GB hard disk). I think it is log file size problem. How should I fix it ? I have reboot it but problem is exist again.

Please help.
  
:(:(:(

---

### Post by benanzo on 2008-01-14
This is not really a problem for running Ubuntu on an Intel Mac, but I'll give you some pointers anyway.  It's not just logfiles you're unable to write, it's system config files as well as seen here:

**Failed to write to /etc/syslog.conf when closing : No space left on device**

You can check the amount of disk space you're using with:
```
df -h /
```
or
```
df -h /etc
```

The second one will print the physical device partion that /etc lives on (if different than /) -- this will at least narrow it down to something other than an actual space problem, something more like a quota problem in Webmin.  Are you able to write files as your regular user?  or even as root?

try:
```
sudo touch /etc/testfile && sudo rm /etc/testfile
```

If you don't get any errors then it's likely a problem with Webmin.

---

### Post by Sef on 2008-01-14
Moved to servers and security.

---

