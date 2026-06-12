---
title: "Need help determining Postfix address range"
date: 2013-01-05
forum: Server Platforms
---

### Post by siado on 2013-01-05
Hello all,
 
Recently set up a Ubuntu LTS 12.04 box to act as a web and mail server.

I'm having some difficulty figuring out what to set in the Postfix configuration for the "Local Networks" setting using:

```
sudo dpkg-reconfigure postfix
```

- I have 5 static IP Addresses from my provider.   xxxx.xxx.xxx.25 thru xxx.xxx.xxx.30
- The mail server FQDN is set to mail.xxxxxxx.com and the IP address is xxx.xxx.xxx.25
- under the Local Networks setting, I have the default of 127.0.0.0/8 and then I'm not sure what to use next for the ??? portion of xxx.xxx.xxx.25/??? 

Ideally, i would like it to just cover that single ip address. Should I then use xxx.xxx.xxx.25/32  ?

Thanks in advance

---

### Post by Doug S on 2013-01-05
If you do not have a local area network, then I do not think you have to worry about it.
My server is also a router to my lan, so my line in the postfix.cf file is:```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.111.0/24
```where 192.168.111.0 is my lan. In your case, if your server has no LAN on it, you would not want that part of the line.

---

