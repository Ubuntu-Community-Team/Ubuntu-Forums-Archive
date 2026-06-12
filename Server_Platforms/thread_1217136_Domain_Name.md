---
title: "Domain Name"
date: 2009-07-19
forum: Server Platforms
---

### Post by georgerobbo on 2009-07-19
In the setup of ubuntu server you are asked for a hostname and a domain name. I accidently gave an incorrect domain name, with .org.uk instead of .org. 

How can I edit this? I am currently logged in with openSSH.

---

### Post by windependence on 2009-07-19
```
sudo nano /etc/hostname

```
ctl+o to save
ctl+x to exit

-Tim

---

