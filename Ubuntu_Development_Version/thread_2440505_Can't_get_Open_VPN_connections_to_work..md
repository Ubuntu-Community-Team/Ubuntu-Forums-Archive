---
title: "Can't get Open VPN connections to work."
date: 2020-04-11
forum: Ubuntu Development Version
---

### Post by dynamitebeaver on 2020-04-11
I've tried using the .ovpn files from my VPN provider, and also a couple of free .ovpn config files from other sources. None of the connections work. It used to work fine on 19.10 so I'm wondering if I'm missing a package or something.

Basically, *has anyone else successfully initiated an open vpn connection using the network manager gui in 20.04?*

Once I know it actually works, I can persevere, but right now I'm thinking its either a missing package or if not, I'll raise a bug report.

**Update**, here are 2 .ovpn files. The first one is the one from my VPN provider. In this case, ZoogVPN, and the other is a publick gateway .ovpn file I found. The ZoogVPN file doesn't work, and the free one does. I've asked support at Zoog and that is ongoing, but I feel like their support for Linux isn't a high priority for them.

[VPN Provider .ovpn (does not work)]("https://drive.google.com/file/d/1wzSnXu7RX8XLCI4mjrqtNTnITT4BPTBE/view?usp=sharing")
[Public .ovpn (works)]("https://drive.google.com/file/d/17moZYANqbxZXRuVutGYsbHeeG9jNKj_Q/view?usp=sharing")

---

### Post by miguelpires on 2020-04-11
Hi,
I solve my problem put this in the vpn file that is created in

/etc/NetworkManager/system-connections/

[vpn] (put this in the first line after vpn)
**tls-cipher=DEFAULT:@SECLEVEL=0 **

Source [https://forums.openvpn.net/viewtopic.php?t=23979](https://forums.openvpn.net/viewtopic.php?t=23979)

Regards
Miguel

---

### Post by dynamitebeaver on 2020-04-12
No joy unfortunately. I have updated my post after finding an .ovpn file that works without any tweaking, its a public one. I have also linked to the private .ovpn file that does not work.

[VPN Provider .ovpn (does not work)]("https://drive.google.com/file/d/1wzSnXu7RX8XLCI4mjrqtNTnITT4BPTBE/view?usp=sharing")
[Public .ovpn (works)]("https://drive.google.com/file/d/17moZYANqbxZXRuVutGYsbHeeG9jNKj_Q/view?usp=sharing")

---

### Post by yapu13 on 2020-04-13
> **dynamitebeaver said:**
> No joy unfortunately. I have updated my post after finding an .ovpn file that works without any tweaking, its a public one. I have also linked to the private .ovpn file that does not work.

[VPN Provider .ovpn (does not work)]("https://drive.google.com/file/d/1wzSnXu7RX8XLCI4mjrqtNTnITT4BPTBE/view?usp=sharing")
[Public .ovpn (works)]("https://drive.google.com/file/d/17moZYANqbxZXRuVutGYsbHeeG9jNKj_Q/view?usp=sharing")

Could you please take a look in your syslog and let me know what kind of error do you have there? Ar at least if any error pops up when you're not able to connect? I'm also having problems connecting with a specific Open VPN profile but have no idea if our problems are similar.

[HERE]("https://askubuntu.com/questions/1226488/openvpn-ca-md-too-weak-error-in-ubuntu-2004-beta") are details on my issue. Yes, the post is closed now as I didn't know I shouldn't have been posting a question on ubuntu+1.

---

