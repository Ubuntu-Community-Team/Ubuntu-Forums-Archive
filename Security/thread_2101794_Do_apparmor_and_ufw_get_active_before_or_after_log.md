---
title: "Do apparmor and ufw get active before or after logging in?"
date: 2013-01-05
forum: Security
---

### Post by arroy_0209 on 2013-01-05
I use ubuntu 12.04. My doubt is this: in my computer there are two accounts: myself and guest. Now, when I boot ubuntu, the connection to internet is generally established before I log in. Are apparmor and ufw active during the small interval of setting up of net connection and my logging in to ubuntu or are they not? In case they are not, it would imply that for that small duration my ubuntu is unprotected. Is that true?

---

### Post by samiux on 2013-01-05
> **arroy_0209 said:**
> I use ubuntu 12.04. My doubt is this: in my computer there are two accounts: myself and guest. Now, when I boot ubuntu, the connection to internet is generally established before I log in. Are apparmor and ufw active during the small interval of setting up of net connection and my logging in to ubuntu or are they not? In case they are not, it would imply that for that small duration my ubuntu is unprotected. Is that true?

The Apparmor and UFW are activated after the network interface is up and got the IP address when the box is booting up.  There is a gap between network interface is up-ed and Apparmor and UFW are activated.

Samiux

---

### Post by Soul-Sing on 2013-01-05
The iptables/firewall set-up, and ufw is a frontend for iptables, should be applied at an early stage of the boot proces: preferably before any network interfaces are active, and before the network service.
You could install the iptables-persistent package to enable this.
```
iptables-persistent start
``` should do the trick.
But this is a bit offtopic.

---

### Post by unspawn on 2013-01-05
> **samiux said:**
> The Apparmor and UFW are activated after the network interface is up (..).  There is a gap between network interface is up-ed and Apparmor and UFW are activated.
...additionally service starting order can be changed. For example if networking starts as item 11 you can start AppArmor as item 10 with:
```
sudo update-rc.d apparmor start 10 S
```
Be mindful though about services requiring networking to be active for whatever reason and updates reverting service starting order.

---

### Post by arroy_0209 on 2013-01-06
> For example if networking starts as item 11 you can start AppArmor as item 10How do I know the starting order in current (default) configuration? Which command will show that?

I tried the command ```
sudo apt-get install iptables-persistent
``` and two windows appeared giving me option to auto-save ipv4, 6 related files/configurations and my response was "yes". Later I tried ```
sudo iptables-persistent start
``` and the respons was "command not found". What did I do wrong?

Also this suggestion seemed good. It should make ufw active even before network connection is established but why was it called "off-topic"?

---

### Post by unspawn on 2013-01-06
> **arroy_0209 said:**
> How do I know the starting order in current (default) configuration? Which command will show that?
For a service called "fail2ban" list directory contents:
```
ls -1 /etc/rc$(runlevel|awk '{print $2}').d/S*fail2ban
```
or use sysv-rc-conf (or rcconf?):
```
sysv-rc-conf  --list fail2ban
```
**Addressing spin-off questions may be considered off-topic (doesn't address the original q) plus it isn't in security territory anymore (basic knowledge or system maintenance more like it).*

---

### Post by arroy_0209 on 2013-01-06
Thanks for response. However I am sot sure what to do about the command "sudo apt-get install iptables-persistent". I am always getting "command not found" in response to commands suggested before. Should I remove it using apt-get? But I am not sure if this will create any problem with ipv4,6 configurations. Any suggestions will be appreciated.

---

### Post by Soul-Sing on 2013-01-06
> **arroy_0209 said:**
> How do I know the starting order in current (default) configuration? Which command will show that?

I tried the command ```
sudo apt-get install iptables-persistent
``` and two windows appeared giving me option to auto-save ipv4, 6 related files/configurations and my response was "yes". Later I tried ```
sudo iptables-persistent start
``` and the respons was "command not found". What did I do wrong?

Also this suggestion seemed good. It should make ufw active even before network connection is established but why was it called "off-topic"?

```
sudo service iptables-persistent start

```

---

