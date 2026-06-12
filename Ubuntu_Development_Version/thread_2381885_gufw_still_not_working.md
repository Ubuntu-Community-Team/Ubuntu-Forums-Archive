---
title: "gufw still not working"
date: 2018-01-06
forum: Ubuntu Development Version
---

### Post by ventrical on 2018-01-06
gufw still not working in wayland. (now a critical bug) Is wayland to be void of  a firewall or do we just run ufw from terminal.

[https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1713238](https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1713238)

---

### Post by zika on 2018-01-06
> **ventrical said:**
> gufw still not working in wayland. (now a critical bug) Is wayland to be void of  a firewall or do we just run ufw from terminal.

[https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1713238](https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1713238)This is a rhetorical question? Right? Or a bit sarcastically driven... ;)

---

### Post by ventrical on 2018-01-06
> **zika said:**
> This is a rhetorical question? Right? Or a bit sarcastically driven... ;)

Huh?

No.. I'm serious... what do we use as a firewall for18.04 with wayland.

---

### Post by cariboo on 2018-01-06
Doesn't this work-a-round work?

```
xhost +si:localuser:root
```

You can set firewall rules using iptables. See [here]("https://help.ubuntu.com/community/IptablesHowTo").

---

### Post by Frogs Hair on 2018-01-06
If you don't use a gui , check ufw status.

```
sudo ufw status
```

```
sudo ufw status
[sudo] password for d-book: 
Status: active



```

---

### Post by ventrical on 2018-01-06
> **cariboo said:**
> Doesn't this work-a-round work?

```
xhost +si:localuser:root
```

You can set firewall rules using iptables. See [here]("https://help.ubuntu.com/community/IptablesHowTo").

I thought that only worked for synaptic..

thanks..

regards..

---

### Post by ventrical on 2018-01-06
> **Frogs Hair said:**
> If don't use a gui , check ufw status.

```
sudo ufw status
```

```
sudo ufw status
[sudo] password for d-book: 
Status: active



```

Thanks... I also thought the workaround was a security issue also. Problem solved for now.

---

