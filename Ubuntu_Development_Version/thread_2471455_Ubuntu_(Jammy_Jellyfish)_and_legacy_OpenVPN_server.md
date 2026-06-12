---
title: "Ubuntu (Jammy Jellyfish) and legacy OpenVPN servers"
date: 2022-01-31
forum: Ubuntu Development Version
---

### Post by biffcannibal on 2022-01-31
In case if someone faces the same problem with the OpenVPN client (2.5.1-3ubuntu4) while trying to connect to a legacy server (TLS 1.0 with BF-CBC).
The problem:
[LIST=1]
[*]Ubuntu 22.04 Jammy Jellyfish
[*]OpenVPN client 2.5.1-3ubuntu4.
[LIST=1]
[*]it doesn't allow to use BF-CBC cipher by default
[*]it doesn't allow legacy TLS negotiation
[/LIST]

[*]NetworkManager-openvpn doesn't support new OpenVPN client 2.5.1 configuration parameters, hence, it's not possible to properly configure it to work with legacy servers
[/LIST]

The solution:
[LIST=1]
[*]The last working version is 2.5.1-3ubuntu1, it works just fine, even though it's the same 2.5.1 version
[*]Remove the 2.5.1-3ubuntu4 package
[*]Install 2.5.1-3ubuntu1 with dpkg manager
[*]Install NetworkManager-openvpn if needed.
[/LIST]

---

### Post by TheFu on 2022-02-01
Why would someone use a VPN that still uses TLS v1?  That protocol has been cracked for a decade. 
[https://www.pcworld.com/article/477017/hackers_crack_internet_encryption_should_you_be_worried_.html](https://www.pcworld.com/article/477017/hackers_crack_internet_encryption_should_you_be_worried_.html)
If your VPN uses TLS, it needs to use TLS v1.3 or later or just use PPTP which has been cracked since 2005.  That would be better than having a false sense of privacy/security by using a busted protocol, IMHO.

NetworkManager-openvpn isn't mandatory. The configuration is stored in .ovpn files. Edit those. Step away from the GUI.

---

