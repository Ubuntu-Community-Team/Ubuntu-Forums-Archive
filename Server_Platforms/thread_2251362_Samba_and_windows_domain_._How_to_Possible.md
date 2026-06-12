---
title: "Samba and windows domain . How to? Possible?"
date: 2014-11-03
forum: Server Platforms
---

### Post by jose52 on 2014-11-03
Hi there, sorry to bother, im beginning to mount a network, in two sides connection by a VPN , in one side i would live to have as primary domain controller a windows server, and in the other side as secondary domain controller a samba.
In this scenario i would like to have them replicating information, so i can have a some redundancy a efficiency in the network. Is this possible? Thanks and sorry to bother once again

---

### Post by jose52 on 2014-11-04
Hi there, sorry to bother, im beginning to mount a network, in two sides connection by a VPN , in one side i would live to have as primary domain controller a windows server, and in the other side as secondary domain controller a samba.
In this scenario i would like to have them replicating information, so i can have a some redundancy a efficiency in the network. Is this possible? Thanks and sorry to bother once again

---

### Post by slickymaster on 2014-11-04
Threads merged.

Please do not create duplicate threads, not only it dilutes community effort but also it's not the proper way to get help.

---

### Post by shurguywutt on 2014-11-06
You will have to edit the samba conf file.

```
vi /etc/samba/smb.conf
```

First makes sure your workgroup is labeled correctly and is identical to your windows workgroup.

So you would like Samba to replicate your data?

I have never used Samba for this but it looks like it can be done.
[https://www.google.com/search?q=Samba+replicate+data&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a&channel=fflb]("https://www.google.com/search?q=Samba+replicate+data&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a&channel=fflb")

---

### Post by jose52 on 2014-11-06
something like this:[ATTACH=CONFIG]257787[/ATTACH]


diferent cities, and i just want to replicate profile and politics, so if one server fails the other can do the job:)

what you think?

---

