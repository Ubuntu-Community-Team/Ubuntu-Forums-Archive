---
title: "Ubuntu-samba-fileserver"
date: 2006-09-26
forum: Server Platforms
---

### Post by Gaimlz on 2006-09-26
Hi.

I'm setting up a small fileserver at work. Just for testing out linux as a server. I have a small config, is it enough you guys think?

samba.conf
```
[global] 
workgroup = Workgroup
netbios name = IT 
domain master = no
invalid users = no 

 
[share1] 
path = /home/root/IKT
comment = Program, filer. 
```

Is the config good enough?

Ihave placed it on a workgroup, and not the windows domain, for safty reasons.

It will stand as an simpel fileserver, handling some importan programs, as It can be easy to get them were you are on the local network.

---

### Post by bluefrog on 2006-09-26
You should read "by example" at [http://samba.org](http://samba.org)

The guide is there to help you set a very simple network and when you feel confident you can move on to something more complicated.

James

---

