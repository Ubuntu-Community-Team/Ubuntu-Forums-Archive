---
title: "citrix receiver installation guide"
date: 2018-10-07
forum: Virtualisation
---

### Post by maclenin on 2018-10-07
Here's a brief guide to installing and running a citrix reciever in 64 bit xubuntu in chrome / chromium.

These steps should work across all *ubuntu flavors.

1. Download latest version of the debian full package "Receiver for Linux (x86_64)"
```
[https://www.citrix.co.uk/downloads/citrix-receiver/linux/receiver-for-linux-latest.html]("https://www.citrix.co.uk/downloads/citrix-receiver/linux/receiver-for-linux-latest.html")
```

2. Double-click .deb to install the citrix receiver
```
icaclient_xx.xx.x.xx_amd64.deb
```
3. Replace citrix cacerts with *ubuntu cacerts 
```
cd /opt/Citrix/ICAClient/keystore/
sudo rm -r cacerts
sudo ln -s /etc/ssl/certs cacerts
```
4. Set browser to open the citrix .ica file automatically
```
[https://support.citrix.com/article/CTX136578](https://support.citrix.com/article/CTX136578)
```
References
```
[https://askubuntu.com/questions/1064452/citrix-receiver-13-10-on-ubuntu-18-04-1/1069929#1069929](https://askubuntu.com/questions/1064452/citrix-receiver-13-10-on-ubuntu-18-04-1/1069929#1069929)
[https://productforums.google.com/d/msg/chrome/7mZxGSFpxMY/xd7qHzpgBgAJ](https://productforums.google.com/d/msg/chrome/7mZxGSFpxMY/xd7qHzpgBgAJ)
```
Good luck!

---

### Post by satwant.hundal on 2018-11-18
:KS thanks for detailed guide.

---

