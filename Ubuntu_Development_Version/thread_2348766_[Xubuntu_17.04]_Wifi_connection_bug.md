---
title: "[Xubuntu 17.04] Wifi connection bug"
date: 2017-01-07
forum: Ubuntu Development Version
---

### Post by enricobe on 2017-01-07
Hello,
I've installed in this moment the lastest daily of Xubuntu 17.04. The wifi internet connection did not work out of the box. 

The wifi works and I can reach the router (192.168.1.1), but internet doesn't work. The default network setting "Automatic DHCP" doesn't let me surf the web. I have to set the network on "Automatic (DHCP) addresses only" and manually set the DNS.

Is this a bug? Can you help me to understand why?

---

### Post by mc4man on 2017-01-08
Exact same thing here on a machine where wireless has always & continues to work fine in 14.04 > 16.04 (Intel Wireless 7260
It connects to wireless router with  no issue but absolutely  no internet unless doing what you also have to do.
Looks like wireless will be a significant issue in 17.04 for many (relatively speaking  as not sure many & Ubuntu will belong together much longer..

---

### Post by enricobe on 2017-01-08
Tank you for your reply. I'm "happy" to know that I'm not the only one with this problem. I have a Realtek Wi-Fi card, so it doesn't seems to be related to a particular vendor.

---

### Post by dhruvramdev on 2017-03-20
I also have same problem. My Laptop gots connected to WIFI but internet doesnot seem to work. DNS PROBE BAD CONFIG is the error message. It seems to be a problem with Automatic DHCP configuration.

---

### Post by avatara9 on 2017-03-20
Same problem in ubuntu 17.04 - it works if I delete connection, restart system, then create new connection. And every now and than it brokes again :(

```
emerald@emerald-N750JK ~> lspci -nnk | grep net -A2
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169
    Kernel modules: r8169
```

---

### Post by gacb on 2017-03-25
I bought a device from ThinkPenguin specifically created for Linux that stopped working when I upgraded to 17.04. I left a message with their support people and will post again when I have a reply.

---

### Post by karan1458 on 2017-03-26
Same issue here. What i generally do '$sudo apt update' to get my internet working. If it's fails, disable-enable networking to get it working. All temporary workaround. Wondering the main cause of issue. 

**Update : **After further checking, I found that i can access websites using IP address. Just like we can reach at our router via IP. It has something to do with DNS resolvr which is somehow not working properly. It's just not reacting to google.com else i can reach the google via IP. Hope it helps to sort out our issue.  

Regards,
Karan

---

### Post by foone2 on 2017-04-17
I had this issue as well on a fresh install, and after looking in the journal I saw lots of DNSSEC errors. Expired signatures, no signatures, etc. 
I realized my computer's clock was way off (6 months in the past), so I fixed that. I had to reboot to make it take effect, but once I'd booted with the clock set correctly there were no more DNSSEC issues and it worked fine.

---

### Post by forjest on 2017-04-26
Downloadlink 
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.164.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.164.1_all.deb)
main page: [https://www.ubuntuupdates.org/pm/linux-firmware](https://www.ubuntuupdates.org/pm/linux-firmware)

---

### Post by cariboo on 2017-04-27
Seeing as we are now testing Artful, thread closed.

---

