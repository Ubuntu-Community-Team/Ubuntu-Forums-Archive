---
title: "iptables.up.rules file example"
date: 2009-05-12
forum: Server Platforms
---

### Post by wattaman on 2009-05-12
Hi!
I have no idea on how to configure the firewall and to be honest I haven't understood too much from all the tutorials on the web, so... I need some help, please.
The only thing I want is an iptables.up.rules configured to block all ports except those needed for http, https, ssh and ftp (can't think of anything else that needs to be open) and eventually to restrict the ssh access to users from a particular IP range (ex. all 76.*.*.* plus all 89.*.*.* plus ... etc)

That's if I understood right; all the firewall rules are written in the iptables.up.rules file, right?!

Thanks!

---

### Post by cdenley on 2009-05-12
I would suggest using UFW for simple firewall configurations like this. I think this would work, but I haven't tested it.
```

sudo ufw enable
sudo ufw default deny
sudo ufw allow http
sudo ufw allow https
sudo ufw allow ftp
sudo ufw allow ssh from 76.0.0.0/8
sudo ufw allow ssh from 89.0.0.0/8

```
Simply running those commands will create a persistent firewall configuration.

---

### Post by wattaman on 2009-05-12
didn't knew about this tool... looks simple to use :)
Anyway, can't install UFW, dunno why. I get this:
> The following packages have unmet dependencies:
  libapache-mod-security: Depends: mod-security-common (= 2.5.9-1) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

... and if I try 'apt-get -f install' it wants to remove the mod-security, which I don't want.
Do you have any suggestions for this?
##################
Also, I've followed the tutorial here:[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) but I got stuck at the end, when I needed to execute > sudo chmod +x /etc/NetworkManager/dispatcher.d/01firewall, since there's not even a NetworkManager folder in that location

Thanks for your help!

---

### Post by cdenley on 2009-05-12
You appear to be using ubuntu 9.10. It is very early in development, since 9.04 was just released a few weeks ago. You're bound to run into problems. Your apt problem may be fixed by
```

sudo apt-get update

```
Are you using the server version? NetworkManager is only installed by default with desktop configurations. UFW has been installed by default for server and desktop since 8.04. You shouldn't need to install it.

---

### Post by wattaman on 2009-05-12
K, I've installed it in webmin. It seems to work.
So, if I understood right, to allow all the IP range starting with 87. I have to run > sudo ufw allow ssh from 87.0.0.0/8?!

Have 8.04, UFW wasn't there by default, BTW.

---

### Post by alejandrove on 2009-05-12
hello.

I have problems understanding The NAT table, somebody know how to build the NAT rules to have a LAN network with access to internet trough the firewall ?

thanks

---

### Post by cdenley on 2009-05-12
> **wattaman said:**
> K, I've installed it in webmin. It seems to work.
So, if I understood right, to allow all the IP range starting with 87. I have to run ?!

Have 8.04, UFW wasn't there by default, BTW.

It was added as a dependency in February 2008 a couple months before 8.04 was released, so unless you used a minimal install or a beta release, it should have been there.

[http://en.wikipedia.org/wiki/Subnetwork#IPv4_classes](http://en.wikipedia.org/wiki/Subnetwork#IPv4_classes)

> 
I have problems understanding The NAT table, somebody know how to build the NAT rules to have a LAN network with access to internet trough the firewall ?
Perhaps you should start your own thread, since your post doesn't seem relevant to this thread.

---

### Post by wattaman on 2009-05-12
Maybe a minimal install it was, it was done by the hosting company.
Anyway, please tell what to run to allow SSH only from IP ranges. In your example, the _sudo ufw allow ssh from 76.0.0.0/8_ will allow from all the 76.*.*.* range?
Also, can't find this information on the net: if I run the *ufw default deny* it means it will block anything that's not already allowed? I don't want to get locked outside the server after turning it on :)

---

### Post by cdenley on 2009-05-12
> **wattaman said:**
> Maybe a minimal install it was, it was done by the hosting company.
Anyway, please tell what to run to allow SSH only from IP ranges. In your example, the _sudo ufw allow ssh from 76.0.0.0/8_ will allow from all the 76.*.*.* range?
Also, can't find this information on the net: if I run the *ufw default deny* it means it will block anything that's not already allowed? I don't want to get locked outside the server after turning it on :)

Yes. As explained in the link I posted, the /8 is the same as a 255.0.0.0 netmask, which means it will match any value for the last 3 octets.

The "ufw default deny" command will filter any unestablished incoming connections. If you already have an established connection, I think it would be fine, but you can change it to something like this to be safe.
```

sudo ufw default allow
sudo ufw enable
sudo ufw allow http
sudo ufw allow https
sudo ufw allow ftp
sudo ufw allow ssh from 76.0.0.0/8
sudo ufw allow ssh from 89.0.0.0/8
sudo ufw default deny

```
I still make no guarantees, though.

---

### Post by wattaman on 2009-05-12
K, m8. Thanks for all your advices.
I'll close this now.

---

