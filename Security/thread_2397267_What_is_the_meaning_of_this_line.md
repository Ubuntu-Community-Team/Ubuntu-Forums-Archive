---
title: "What is the meaning of this line ?"
date: 2018-07-27
forum: Security
---

### Post by linuxyogi on 2018-07-27
```
$ dmesg |tail[   10.312411] PKCS#7 signature not signed with a trusted key
[   10.312659] VBoxNetFlt: Successfully started.
[   10.316221] PKCS#7 signature not signed with a trusted key
[   10.316407] VBoxNetAdp: Successfully started.
[   10.320358] PKCS#7 signature not signed with a trusted key
[   10.320607] VBoxPciLinuxInit
[   10.322338] vboxpci: IOMMU not found (not registered)
[   18.300357] r8169 0000:02:00.0 enp2s0: link up
[   18.300373] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[  167.858768] [COLOR=#ff0000]nf_conntrack: default automatic helper assignment has been turned off for security reasons and CT-based  firewall rule not found. Use the iptables CT target to attach helpers instead[/COLOR].



```

What the meaning of this line (in red) ?

---

### Post by oldos2er on 2018-07-29
Does anything here help? [https://askubuntu.com/questions/906197/weird-iptables-log-messages-after-upgraded-to-server-zesty-17-04](https://askubuntu.com/questions/906197/weird-iptables-log-messages-after-upgraded-to-server-zesty-17-04)

---

### Post by linuxyogi on 2018-07-29
> **oldos2er said:**
> Does anything here help? [https://askubuntu.com/questions/906197/weird-iptables-log-messages-after-upgraded-to-server-zesty-17-04](https://askubuntu.com/questions/906197/weird-iptables-log-messages-after-upgraded-to-server-zesty-17-04)


> The new AutomaticHelpers configuration setting has been added to   firewalld.conf

But Ubuntu uses ufw (not firewalld). Is there a need to tweak anything from my end ?

I connect to the Internet  directly without a router I use  

```
*sudo ufw default deny incoming* 
```

---

