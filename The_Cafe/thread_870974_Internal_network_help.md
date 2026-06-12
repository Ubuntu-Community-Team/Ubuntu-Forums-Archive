---
title: "Internal network help"
date: 2008-07-26
forum: The Cafe
---

### Post by macmichael01 on 2008-07-26
Hello, I am setting up an internal network so that my company can have an internal wiki. On macs and linux you can specify the host_name in your /etc/hosts file to point the the correct server containing the wiki. But I am not sure how to make this work with windows. so if I go to [http://hostname/wiki/](http://hostname/wiki/) it will point to my wiki. Perhaps there is a better method for setting up an internal network.

Any suggestions or tutorials on this?

Thanks in advance

---

### Post by popch on 2008-07-26
There's a 'hosts' file in Windows, too. I am not at the moment near a Windows machine, so I can not tell you its exact location. Use your exploder to find it.

Beware: there's also a sample file which looks right but will be ignored by Windows.

Presumably, some other members here will shortly tell you how to properly set up a small LAN, complete with name resolution.

---

### Post by Daveski on 2008-07-26
You should use a DNS server if there are more than a couple of hosts. In Windows, the HOSTS file is in **C:\WINDOWS\system32\drivers\etc**

---

