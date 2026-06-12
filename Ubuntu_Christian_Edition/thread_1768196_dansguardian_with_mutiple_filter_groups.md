---
title: "dansguardian with mutiple filter groups"
date: 2011-05-26
forum: Ubuntu Christian Edition
---

### Post by slaz on 2011-05-26
Hello,
 
I am running Ubuntu server 11.04, and I installed dansguardian 2.10.1.1, and squid 2.7.STABLE9. I have a working server, dansguardian starts up and so does squid. However when I copy dansguardianf1.conf to make f2.conf, f3.conf, f4.conf, etc.. and restart dansguardian I get this message:
 
Error reading file : No such file or directory
Error reading file : No such file or directory
Error opening exceptionextensionlist
Error opening filter group config: /etc/dansguardian/dansguardianf1.conf
Error reading filter group conf file(s).
Error parsing the dansguardian.conf file or other DansGuardian configuration files

I have configured the dansguardain.conf file to use 4 filter groups. I am in need of help, I am lost how to get this to work. I can get this to work when I just use one filter group, but not when I add more, I am aslo filtering by ips, and have the ip authplugin enabled. Let me know if more information is needed. 
 
Thanks again,
slaz

---

### Post by mbraidy on 2011-12-17
I have the same problem.  However when I disable all Auth Plugins, it works fine.
Is it related to authentication?

---

