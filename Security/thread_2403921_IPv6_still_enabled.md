---
title: "IPv6 still enabled"
date: 2018-10-17
forum: Security
---

### Post by cam17 on 2018-10-17
I am using 18.04 Desktop and have WIFI IPV6 disabled in the wifi configurations. but when I go to the "details" tab it shows an IPv6 address as if disabling IPV6 had no affect.

---

### Post by #&amp;thj^% on 2018-10-25
The only way "I" have found to disable "IPV6" is to do so via grub:
```
sudoedit /etc/default/grub
```
And add to this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet ipv6.disable=1"
```
So you will need to add "ipv6.disable=1" save and close, and then run:
```
sudo update-grub
```
Now after a reboot you should have IPV6 disabled, and check this for verification:
```
sudo sysctl -a|grep disable_ipv6
[sudo] password for me: 
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.enp0s25.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
net.ipv6.conf.tun0.disable_ipv6 = 1
net.ipv6.conf.wlp3s0.disable_ipv6 = 1

```

---

### Post by Doug S on 2018-10-25
> **1fallen said:**
> The only way "I" have found to disable "IPV6" is to do so via grub:
I do the same as 1fallen.

---

### Post by cam17 on 2018-10-25
I understand what your saying 1fallen but the grub is for boot up paramaters the operating system should override the settings once up and running. This should be corrected as Ubuntu has the option to turn opv6 off but it does not work.

---

### Post by The Cog on 2018-10-26
> **cam17 said:**
> I understand what your saying 1fallen but the grub is for boot up paramaters the operating system should override the settings once up and running. This should be corrected as Ubuntu has the option to turn opv6 off but it does not work.

How do you think you have disabled it? I can't find a setting to disable IPv6, only to ignore the interface, enable DHCP or to add additional IPv6 addresses.

---

### Post by #&amp;thj^% on 2018-10-26
> **cam17 said:**
> This should be corrected as Ubuntu has the option to turn opv6 off but it does not work.

You will have to show me that one. ;) ignore and disable have two very different meanings here.

---

### Post by The Cog on 2018-10-26
These are the settings I could find:

---

### Post by deadflowr on 2018-10-26
Gnome control center looks like this


Older control center layout had it marked as ignore.
(Like that used by unity)

---

### Post by SeijiSensei on 2018-10-26
Edit the file sysctl.conf as root with the command "sudo nano /etc/sysctl.conf".  Add these two lines to the bottom of the file:

```

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1

```

Reboot.  You should no longer see an IPv6 entry if you use "ifconfig".

---

### Post by 1clue on 2018-10-26
Just out of curiosity, what's your motivation in disabling ipv6? Is it just a lack of understanding of what's involved, or a security issue, or something else?

If you're worried about a security issue, then turning off IPV6 at the router will likely be all you need. But that said, if you want to be extra safe you could do what everyone else is saying.

Your ISP may not supply IPV6 access anyway, you can find out by looking for global addresses:

```

$ sudo ip -6 address list
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 state UNKNOWN qlen 1000
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 state UP qlen 1000
    inet6 dad:ea75:dead:beef:3cd0:a325:e5c2:976f/64 scope [COLOR=#ff0000]**global**[/COLOR] temporary dynamic 
       valid_lft 541585sec preferred_lft 23136sec
    inet6 fe80::406:100e:3594:9b6c/64 scope [COLOR=#ff0000]**link**[/COLOR] noprefixroute 
       valid_lft forever preferred_lft forever

```

If you don't have global addresses then your router doesn't supply ipv6 functionality, or your ISP doesn't.

If your addresses start with fe80 then they will never be accessible on the public Internet.

---

### Post by SeijiSensei on 2018-10-26
In my case, it was because Comcast introduced IPv6 addressing and complicated life for our combo gateway/mail scanner.  I could have gone through and made everything IPv6 compliant, including adding the required AAAA records in DNS, but we decided that was more work than it was worth and just turned off IPv6 instead.  Then external mail servers never got confused and just sent everything to us via IPv4.

---

### Post by 1clue on 2018-10-26
Gotcha. So you're on an office connection then? Makes sense you'd want to go at that gradually.

And you'd need a static ipv6 address I think that way too for your publicly accessible servers.

---

### Post by 1clue on 2018-10-26
You could also do something like this at the end of /etc/conf.d/net:
```

postup() {
             if [[ "${IFACE}" != "lo" ]] && [[ ! "${IFACE}" =~ ^tap. ]]; then
                         sysctl net.ipv6.conf.$IFACE.accept_ra=0
                         sysctl net.ipv6.conf.$IFACE.autoconf=0
                         sysctl net.ipv6.conf.$IFACE.disable_ipv6=1
             fi
}

```

---

### Post by #&amp;thj^% on 2018-10-28
> **SeijiSensei said:**
> **_In my case, it was because Comcast introduced IPv6 addressing and complicated life _**for our combo gateway/mail scanner.  I could have gone through and made everything IPv6 compliant, including adding the required AAAA records in DNS, but we decided that was more work than it was worth and just turned off IPv6 instead.  Then external mail servers never got confused and just sent everything to us via IPv4.
+1 ;)

---

### Post by cam17 on 2018-11-07
Securing a machine means disabling any protocols that are not being used. since WIFI WPA2 has a compromise and WPA3 is on its way having any workstation only perform communications on required protocols is always more secure whether or not the router has IPV6 off.

---

