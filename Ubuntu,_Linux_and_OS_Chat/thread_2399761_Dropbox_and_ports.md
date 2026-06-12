---
title: "Dropbox and ports"
date: 2018-08-29
forum: Ubuntu, Linux and OS Chat
---

### Post by johnaaronrose on 2018-08-29
[SIZE=2][COLOR=#242729]I'm confused about Dropbox and its use of ports re firewall. Looking at [https://www.dropbox.com/en/help/desktop-web/configuring-firewall?_locale_specific=en](https://www.dropbox.com/en/help/desktop-web/configuring-firewall?_locale_specific=en) it states that may need to open ports 80 & 443. I've done that in GUFW on my Ubuntu computers but is there really a need to do that?
NB I allow input from established connections by having used: sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT followed by: sudo netfilter-persistent save[/COLOR][/SIZE]

---

### Post by SeijiSensei on 2018-08-29
You presumably already permit outbound traffic to 80 or 443, or you couldn't browse the web.  If you explicitly filter outbound traffic, you'll need to permit the ports >17000 in that online document.

---

### Post by johnaaronrose on 2018-08-29
I allow all outbound traffic. I don't modify it or filter it in any way. I do allow all ports to input from other PCs (identified by static addresses assigned by my router) on my home network. If I understand correctly, that means that I don't have to explicitly permit inbound traffic from ports>17000.

---

### Post by johnaaronrose on 2018-08-29
I allow all outbound traffic. I don't modify it or filter it in any way. I do allow all ports to input from other PCs (identified by static addresses assigned by my router) on my home network. If I understand correctly, that means that I don't have to explicitly permit inbound traffic from ports>17000.

---

