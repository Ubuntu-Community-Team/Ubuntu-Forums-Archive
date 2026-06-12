---
title: "SSH - Connection refused"
date: 2011-06-29
forum: Server Platforms
---

### Post by luka1002 on 2011-06-29
Hello 

running Ubuntu Server 11.04 on Virtual VMware Professional ,hosted by Windows 7.
SSH worked at first time until i changed IP address of Ubuntu. From that time i get connection refused by PuTTY on Win7. 
I tried from another subnet another pc and worked. Seems that problem is in "known_hosts" file.
I have user named luka , so i found at home my folder /.ssh known_hosts file and deleted everything inside.. same problem, then i delete hole file and nothing. 
Friend from another subnet named "petar" have his folder at home but no /.ssh folder???
He connected and login to my PC by PuTTY, should he have his folder (/.ssh)??
How to solve this? :confused::cry:

---

### Post by arrrghhh on 2011-06-29
What do you have in /etc/hosts.deny?  Make sure your IP isn't in there...

---

### Post by luka1002 on 2011-06-29
> **arrrghhh said:**
> What do you have in /etc/hosts.deny?  Make sure your IP isn't in there...

I am really sorry. Problem solved. I had IP conflict, something is wrong with DHCP....  Thanks again!

---

