---
title: "Samba Problems"
date: 2008-03-27
forum: Server Platforms
---

### Post by Masteroc on 2008-03-27
So i followed the guide in the ubuntu community wiki and i installed samba, changed the samba conf file and added the users plus their passwords. The only problem is that i cannot access them from the windows computers. I type in "\\192.168.1.109" and the login box comes up. I put in the username and password and it just comes up again....i tried many times and it just wont work. I also tried using Swat and this didnt help either.

---

### Post by netlogic on 2008-03-27
Samba isn't an instant gratification server like Apache. You really have to read some of the documentations. It is hard to guess others problems regard to Samba without the configs, all the logs, and sniffer captures.

However, I have a strong feeling you haven't bothered to create a samba user.
smbpasswd -a username

---

### Post by jonabyte on 2008-03-28
can you post your smb.conf file, that would be a big help to those trying to help you..:)

---

### Post by HermanAB on 2008-03-28
Maybe this will help: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

---

