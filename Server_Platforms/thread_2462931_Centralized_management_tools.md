---
title: "Centralized management tools"
date: 2021-05-30
forum: Server Platforms
---

### Post by WhiteTigerIT on 2021-05-30
I have half a dozen servers between VPS and VM and some Xubuntu / Ubuntu PCs.
Isn't there a centralized management tools, at least as far as updates are concerned?
Something similar to the tools for centralized management of Joomla and Wordpress that at a glance allow me to understand what there is to do and where to do it.
Thanks in advance.

---

### Post by CharlesA on 2021-05-30
You can use a tool such as Ansible to apply updates to multiple servers at the same time.

You will need to write a playbook but that shouldn't be too difficult.

---

### Post by scorp123 on 2021-05-30
> **WhiteTigerIT said:**
>  Isn't there a centralized management tools, at least as far as updates are concerned?

Ansible.

[https://www.cyberciti.biz/faq/ansible-apt-update-all-packages-on-ubuntu-debian-linux/]("https://www.cyberciti.biz/faq/ansible-apt-update-all-packages-on-ubuntu-debian-linux/")

---

### Post by TheFu on 2021-05-30
Cockpit, ansible, or a little ssh script.
For weekly patching, I use a little ssh script. The simplicity is why.

Ansible and Cockpit need ssh configured anyway, so a little loop over all the DNS names or IPs in a list works fine. Regardless, you'll probably want to setup a "deployXYZ123" account on each system that allows ssh via ssh-keys and sudo without a password for **apt-get update** and **apt-get full-upgrade**, just to make life easy.

```
#!/bin/sh
CMD1="apt-get update"
CMD2="apt-get dist-upgrade"
ssh server1  "sudo $CMD1; sudo $CMD2;"
ssh server2  "sudo $CMD1; sudo $CMD2;"
....
ssh server99  "sudo $CMD1; sudo $CMD2;"
```

May want to setup a ~/.ssh/config file to fill in what "server32" means - userid, IP/hostname, non-standard port?
If you need special other things in the command on a box, add those too.  I like to remove all excess snap package versions, for example, but only 3 of my systems have snaps loaded.  
I like to force a youtube-dl update on 3 systems as well - not the same.  The youtube-dl install isn't in the "deployXYZ123" account, it is in my personal account on those systems ... so I don't use the same "serverX" name, I use the real hostname, but the **ssh romulus "youtube-dl -U"** command does the right thing.

"KISS" - [https://en.wikipedia.org/wiki/KISS_principle](https://en.wikipedia.org/wiki/KISS_principle) . Only make things as complex as necessary.

Sure, we can use all sorts of tools - F/LOSS, freeware, or paid for these things.  But none are as easy as the simple ssh-script above, IMHO.

---

### Post by LHammonds on 2021-06-01
I setup each server to handle his own business and do not let other servers tell it what to do.  [Example](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=273)

I use custom Bash scripts for each server to do its own OS updates and to log the results of those updates.  [My GitHub Repository](https://github.com/LHammonds/ubuntu-bash)

These scripts will email me if they run into a problem (since I have my own internal mail server)

However, I do have a centralized monitoring system ([Nagios](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=267)) that keeps tabs on all my servers / services.  Each server has standards for reporting health such as CPU/Memory/swap/HD Space/APT Updates.  But each server usually serves a specific purpose so I make sure a health check covers that service too.  A MariaDB server will have a script that ensures it can connect to a test database, issue an SQL command and get a good result.  A PHP server will have a script that retrieves a web page to ensure that the service / website is responding correctly. etc.

It takes a bit of time to design, install and configure a monitoring system.  But once in place, it is fairly quick to add / remove new machines.

Regarding the time to setup the scripts, it took me a while to code them initially but when I deploy a virtual machine server from a template, all of it is done and the only thing I have to tweak are the service-specific things that are different from server to server.

The only times I need to manually "mess with" a server are when there are issues such as running out of space (a script has already expanded the partition to the max size available) or when there is a hang-up in an APT update process it cannot resolve by itself or when I need to deploy a new version of the OS and migrate the data to the new platform which happens shortly after each major release (e.g. Ubuntu 20.04.5 LTS --> 22.04.1 LTS) because I never do in-place upgrades between versions.

LHammonds

---

### Post by WhiteTigerIT on 2021-06-02
I thank everyone for the reply.
Now I will read better the references and the documentation that you have pointed out to me.
Thanks again.

---

