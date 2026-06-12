---
title: "conection to a vpn"
date: 2019-03-12
forum: Security
---

### Post by bhasher on 2019-03-12
Hello,

(Sorry for my bad english)

I have a VPN (nordVPN) on my web browser but I want to use it directly in ubuntu.

I have download the .ovpn give by the VPN, but when I import it in Settings>Network>VPN, I have this alert: "The file uk141.nordvpn.com.tcp.ovpn cound not be read or does not contain recognized VPN connection information".

Ubuntu VPN doesn't support openvpn files ?

Thank you ;)

---

### Post by TheFu on 2019-03-13
The uk141.nordvpn.com.tcp.ovpn file is just text. If it isn't then it isn't in the correct format.  You can run the "file" command on it to see if the system recognizes it - perhaps it is .gz or .zip and the suffix was lost somehow?

I use openvpn a bunch - both with a paid service and with my own vpn server.  I've never used the normal GUI stuff to enable/disable the openvpn stuff.  You can try running something like this inside a terminal for troubleshooting:
```
cd /etc/openvpn/
sudo openvpn /path/to/uk141.nordvpn.com.tcp.ovpn
``` to see if any errors are shown.  You need to supply the correct path to uk141.nordvpn.com.tcp.ovpn, of course.  Then troubleshooting with the exact cause can be done.

Or if your shell is in the same directory as uk141 .... , then you can try ```
sudo openvpn ./uk141.nordvpn.com.tcp.ovpn
```

Troubleshooting GUIs is just too hard.

---

