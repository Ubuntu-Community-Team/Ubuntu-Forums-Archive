---
title: "Looking for open sourcesatelite server"
date: 2019-08-27
forum: Ubuntu, Linux and OS Chat
---

### Post by venkanna1521 on 2019-08-27
[FONT=Ubuntu]Dear Friends,

[/FONT]
[FONT=Ubuntu]In my current environment we have around 200 virtual + Physical Linux machines which are running on Ubuntu,Cent OS ,Redhat ,Suse Linux and Debian open source Os. We are planning to patch them . So could you please share/ recommend best satellite server which we can patch in single time. Thanks in advance.

[/FONT]
[FONT=Ubuntu]Regards,
Venky[/FONT]

---

### Post by TheFu on 2019-08-27
I've never used satellite, but we use [ansible]("https://www.ansible.com/") for patching.  Any devops tool can do it, but so can ssh with a script.  Systems can automatically patch themselves completely or just security patches as well.  I don't do that.

For a bare metal OS deployment solution, that's what [Cobbler]("https://cobbler.github.io/manuals/quickstart/") is about.

APT packages can be locally cached on a local server. This can reduce WAN bandwidth if there are lots of similar systems. I think my systems see about a 50% cache hit. This is because there are multiple releases and the servers are mostly snowflakes.  It works for debian and any APT-based distro.

If you are using Juju, there might be other solutions. I've never touched it.  I think the Ubuntu Server market is more about cloud deployments than internal enterprise deployments.

---

### Post by Tadaen_Sylvermane on 2019-08-27
I have very little intelligent to add as I don't do anything on this scale, just a home user. But I can say that the apt-cacher-ng proxy server for ubuntu / debian and apt can also cache packages for centos and redhat. No idea about suse though. 1 stop shop mostly. A server running this would exponentially reduce your wan traffic with updates, and only gets better the more machines use it. I unfortunately don't know anything about automating it all short of ssh scripts.

---

### Post by scorp123 on 2019-09-11
> **venkanna1521 said:**
> [FONT=Ubuntu]Dear Friends,

[/FONT]
[FONT=Ubuntu]In my current environment we have around 200 virtual + Physical Linux machines which are running on Ubuntu,Cent OS ,Redhat ,Suse Linux and Debian open source Os. We are planning to patch them . So could you please share/ recommend best satellite server which we can patch in single time. Thanks in advance.

[/FONT]
[FONT=Ubuntu]Regards,
Venky[/FONT]

Where I work we have 400+ server installations, both physical and virtual. We do everything with **Puppet **(the free, unpaid version)
[https://puppet.com](https://puppet.com)

At home I also have a handful of Linux and Mac installations too and there I use **Ansible** so I can roll out configurations and updates to all of them with one single command. It saves me a lot of time.

Personally, I find **Ansible **easier and more pleasant to get started with. Puppet, while also very very powerful, can get complicated rather quickly. I only work with it because at work I have to, it's what we have. Personally I would not have chosen it if that decision were up to me. 

The other advantage I see is that Ansible is *"agent-less"*, e.g. the installations you want to manage do not require any special software (e.g. unlike Puppet which requires there be a central Puppet Server and the clients have a Puppet Agent installed). For Ansible it's enough that SSH is open and you know how to login on the target. Ansible does everything via SSH and "sudo" or "su" if it needs to (can be defined per target host as needed). Therefore, I find it's relatively easy to get started with Ansible and achieve good results.

Also, YouTube has lots of good tutorials on these topics, e.g. Ansible vs. Puppet vs. Chef. Take a look :)

---

