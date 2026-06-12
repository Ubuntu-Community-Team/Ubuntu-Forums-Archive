---
title: "ufw on Gutsy?"
date: 2008-08-07
forum: Security
---

### Post by uberpop on 2008-08-07
Hi All,

Just a quick question - I'm running Gutsy 7.10 server and I'm wondering if I can install and run ufw on it or is ufw only for the 8.x series? If its able to be run, do I just use the standard apt-get? Many thanks.

---

### Post by tuxxy on 2008-08-07
Try running it from terminal;

```
ufw
```

---

### Post by uberpop on 2008-08-07
Hi Tuxxy,

No, it doesn't look like it. I get this:
-bash: ufw: command not found

---

### Post by tuxxy on 2008-08-07
You can also use firestarter to configure the firewall

---

### Post by uberpop on 2008-08-07
I looked at that but I think it would mean I would need to install a gui and I was hoping to keep this machine gui free. Configuring iptables seems quite time consuming whereas using gui tools seems unecesssary (this is a web dev server being used inside a local network) so ufw seemed a good middle option.

---

### Post by pparks1 on 2008-08-07
You could install something like webmin from [www.webmin.com](www.webmin.com).   This will allow you to remotely configure the machine through a web browser.   You can configure the firewall through webmin.   So, this gives you a GUI without installing a GUI.  Best of both worlds.

---

### Post by uberpop on 2008-08-07
OK, tried running sudo apt-get install ufw but it can't find the package. I guess wherever apt-get looks for packages to download is dependent on the version of the os requesting the package so maybe ufw is not compatible with Gutsy.

Thanks pparks1, I'll have a look and see what Webmin is like. Otherwise, I guess its back to learning iptables.

---

### Post by tuxxy on 2008-08-07
Maybe you could do an upgrade to 8.04.1 its great OS :)

---

### Post by ibutho on 2008-08-07
You can use [Shorewall]("http://www.shorewall.net") as a frontend to netfilter+iptables if you do not want to use GUI tools like firestarter.

---

### Post by uberpop on 2008-08-11
Thanks for all your suggestions everyone. I think I will upgrade to the 8.x os.

---

