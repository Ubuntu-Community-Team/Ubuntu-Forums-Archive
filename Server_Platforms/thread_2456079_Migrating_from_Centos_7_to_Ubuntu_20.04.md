---
title: "Migrating from Centos 7 to Ubuntu 20.04"
date: 2021-01-04
forum: Server Platforms
---

### Post by wp.rauchholz on 2021-01-04
I run currently my home server under CENTOS 7 and I want to move to Ubuntu.
The server provides functionality of modem/router, DNS ( I got a FQDN under dynamic IP), OPENVPN, LAMP and media (emby). I have been looking around and it appears that the differences in setting up the configs are not very different.
Just some questions / confirmations I am looking for:
* Has somebody in this community experience with this migration and can share best practices?
* I understand that there is a pppoe package available in Ubuntu
* Can I use firewall (iptables) as is on my current server (attached file)?
* Anything you want me to look out for?

Than you for your help.

Wolfgang

---

### Post by rsteinmetz70112 on 2021-01-04
I haven't used CENTOS so I can't comment on transferring to Ubuntu. It should be similar. All of the parts you list above are available and if you understand the configuration is should be doable. 

The biggest difference is probably that CENTOS is a Red Hat variant while Ubuntu is a Debian variant and the package management tools are different.

---

### Post by wp.rauchholz on 2021-01-06
Thank you for your response.
I do have a few follow-up questions.

1) I will setup eth0/1 (or whatever network devices are called in Ubuntu) manually. Question: Do I need to stop/disable NetworkManager to prevent the manual config being overwritten?
2) I have ~ 2TB of hard disk. I have ~ 1TB of data (photos, videos, e-docs (Nextcloud). For space reason, I have them currently stored in /home/..., which I understand is not the best solution. What partitioning of the HDDs do you suggest?

---

### Post by LHammonds on 2021-01-06
Are you planning on using Desktop?  The headless server is just a matter of modifying the /etc/netplan/*.yaml file that is in there...if using the "classic" install which does not include the CloudInit stuff.

You might want to browse through how I setup servers but it may be overkill for your situation but it does cover setting up LVM and using multiple partitions so you can dynamically allocated to whatever partition you need...such as /home

[https://hammondslegacy.com/forum/viewtopic.php?f=40&t=273](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=273)

LHammonds

---

### Post by rsteinmetz70112 on 2021-01-06
> **wp.rauchholz said:**
> Thank you for your response.
I do have a few follow-up questions.

1) I will setup eth0/1 (or whatever network devices are called in Ubuntu) manually. Question: Do I need to stop/disable NetworkManager to prevent the manual config being overwritten?
Your interfaces should be set up automatically when you install Ubuntu. The naming varies - I not sure how it's determined because I haven't looked into it. Usually they get set up correctly. You can use NetworkManager to change the configuration if necessary, that is the default way Ubuntu handles network configuration, there are other options but I always advocate using the default methods unless you have a good reason for not.
> 2) I have ~ 2TB of hard disk. I have ~ 1TB of data (photos, videos, e-docs (Nextcloud). For space reason, I have them currently stored in /home/..., which I understand is not the best solution. What partitioning of the HDDs do you suggest?
That's up to you, depending on what you store. I typically set up a separate filesystem called /files and then create directories under it for the broad classification of things I intend to store like /files/Photos, /videos/Videos,

---

### Post by wp.rauchholz on 2021-01-06
Hi LHammonds,

the server is headless and physically at my home. The same I have the current server which runs under Centos 7.
I will have a look at your config. Thanks

The laptops / desktops at home will eventually all run under Ubunto too.

---

### Post by wp.rauchholz on 2021-01-06
Good input too for the partitioning. Thanks

Concering NetworkManager. Under Centos I disabled the devise to prevent NetworkManager overwriting it with evey reboot or restart
I guess I will have to look how to do it the standard way.

---

