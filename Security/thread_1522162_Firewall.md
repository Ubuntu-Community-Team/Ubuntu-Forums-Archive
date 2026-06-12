---
title: "Firewall"
date: 2010-07-01
forum: Security
---

### Post by Scott Swinyard on 2010-07-01
Is there a firewall installed and running in 10.04? If so are there any gui tools for configuring it and where are they?

If there is not a firewall, what should I install to get one properly up and running?

---

### Post by cgroza on 2010-07-01
There is iptables. Just install Firestarter to configure it. After you do that there is no need to run Firestarter again(many do).

---

### Post by bodhi.zazen on 2010-07-01
> **Scott Swinyard said:**
> Is there a firewall installed and running in 10.04? If so are there any gui tools for configuring it and where are they?

If there is not a firewall, what should I install to get one properly up and running?

This is a recurring discussion and is covered in the sticky at the top of these forums:

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

The default firewall in netfilter and iptables is in turn the front end for netfiler.

iptables is considered the firewall for Linux, but it is configured on teh command line or with scripts.

The default configuration tool for Ubuntu is UFW.

By default there are no significant open ports so a firewall is not necessary. If for some reason you feel you need a firewall I suggest you use ufw

```
sudo ufw enable
sudo ufw default deny
```

If your reason is that you are coming from windows and you think you need a firewall in Linux just like you need a firewall in Windows, you probably shold read teh security sticky as Linux is not Windows.

If you prefer a graphical tool, use gufw.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)


> **cgroza said:**
> There is iptables. Just install Firestarter to configure it. After you do that there is no need to run Firestarter again(many do).

This is bad advice getting worse every time it is repeated. Firestarter is no longer maintained and will likely not run on Ubuntu 10.10.

Firestarter also conflicts with UFW, and unless you are willing to provide support for broken firewalls, please do not advise new users install firestarter. If you do, please include information on how to properly remove it if needed.

```
sudo apt-get purge firestarter
```

So while some old users may feel they need or prefer firestarter, to some extent they are living in the past and new users should be taught the default tools.

If there is some need not provided by the default tools, firestarter is probably not the best solution, and you really need to identify what is needed before you blindly install firestarter.

---

