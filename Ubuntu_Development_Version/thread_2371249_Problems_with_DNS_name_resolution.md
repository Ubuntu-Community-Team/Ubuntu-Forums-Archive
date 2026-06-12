---
title: "Problems with DNS name resolution"
date: 2017-09-12
forum: Ubuntu Development Version
---

### Post by wgarcia on 2017-09-12
I'm having problems with DNS name resolution in a system upgraded to 17.10 (from 17.04). 

At times it takes something between 20 to 30 seconds to resolve some DNS host names. In my syslog I get messages of this type:
```
Sep 12 17:38:17 user systemd-resolved[2186]: Using degraded feature set (TCP) for DNS server 8.8.8.8
```

If I do:
```
sudo service systemd-resolved status
```

at the end of the output produced by this command I see some lines with this type of messages:
```
Sep 12 17:38:37 user systemd-resolved[2186]: Using degraded feature
```

A part of taking some time to solve some DNS hostnames, the network seems to be working fine in this system.

I've looked for bug reports related to this but only found some old fix-released bugs that looked related, but I'm not sure: 
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1449001](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1449001)

---

### Post by SeijiSensei on 2017-09-12
Searching Google for "Using degraded feature set (TCP)" brought up some pages about this.  Didn't see an obvious resolution, though.

---

### Post by wgarcia on 2017-09-13
I have done further investigation. It seems that my system has a conflict between two services: resolvconf and systemd-resolved. I checked my /etc/resolv.conf file, and it was a symlink to /run/resolvconf/resolv.conf, and for the nameserver line it said
```
nameserver 127.0.0.53
```

But I noticed that there is another resolv.conf file in /run/systemd/resolve/resolv.conf, and that one has two nameserver lines, the first one with my local DNS server and the second one with the Google DNS server (8.8.8.8). 

I changed the symlink in /etc/resolv.conf to this second version and the problem seems to be gone. 

I don't know what am I doing, and why I have this conflict (probably messed up my system around 17.04, I also had DNS name resolution problems there).

---

### Post by dino99 on 2017-09-13
Looks like your system still have the old config in the place; and then disturb the actual processes.

'sudo gtkorphan' might help you find & purge the old packages and their outdated configs.

---

### Post by wgarcia on 2017-09-13
Thanks, I tried it and it lists a very large list of packages. Is it safe? I seem to have seen in the list some packages I installed for specific non-standard things I do, like some libraries I 
installed to use ID cards with a chip with digital certificates. What criteria does it use to consider a package "orphan", if you would know?

---

### Post by dino99 on 2017-09-13
i've never got false positive with gtkorphan; so i can tell it is safe to purge the proposed listed packages.
If it propose a known needed package, then that means a more recent version is also installed; or the dependencies have changed. 
You can easily verify with synaptic before purging.

note for synaptic with a wayland session (now default on artful): first copy/paste that script into a terminal:  xhost +si:localuser:root

---

### Post by wgarcia on 2017-09-13
In any case for the case I report in this thread, it seems that I had a wrong symlink to /etc/resolv.conf, probably eliminating obsolete packages wouldn't have solved it. Unless purging the package also purges the wrong symlink, who knows.

---

### Post by zika on 2017-09-14
```
dpkg -l | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
```work{s,ed} for me for years now. It does clean all the stuff that is left behind and it is easy to maintain and have control of.
[COLOR=#ff0000]Even though I do use it daily I do not give any kind of even limited guarantee and do not encourage anyone to use it before he/she fully gets what it really does... ;)[/COLOR]

---

### Post by wgarcia on 2017-09-14
Also [etckeeper]("http://etckeeper.branchable.com/") can be handy if anything happens.

---

### Post by macnux on 2018-03-12
DNS server is always tricky.
I used BIND all the time. Yet, it not that new. I think this guide is enough for non cloud DNS server [https://likegeeks.com/linux-dns-server/]("https://likegeeks.com/linux-dns-server/")
Most admins now use something like AWS Managed Cloud DNS for the sake of simpilicity.
Hope that helps.

Regards,

---

### Post by slickymaster on 2018-03-12
17.10 is already released.

Thread closed

---

