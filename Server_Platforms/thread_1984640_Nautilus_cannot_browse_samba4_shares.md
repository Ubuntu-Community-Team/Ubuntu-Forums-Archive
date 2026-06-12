---
title: "Nautilus cannot browse samba4 shares"
date: 2012-05-22
forum: Server Platforms
---

### Post by tenmoi on 2012-05-22
Hi,

I am running samba4 alpha 20 as a domain controller on a fully updated ubuntu x64 12.04. 

My network is entirely on a Virtualbox host-only network. Ubuntu x64 server provides dhcp and dns services for other clients on the host-only network.

dhcp and dns services are working fine. I've tested thoroughly.

Winxp SP2 can join the domain and browse a share on the Ubuntu x64 server.
Ubuntu desktop x64 can join the domain BUT I cannot browse the share with nautilus.
Fedora 16 x32 can join the domain BUt I can't browse the share with nautilus.

However,
smbclient -L //server-share-address -U domain-user-password 
shows the share.

mount -o username=x,password=x //remote-share /local-directory
works fine. I can copy and delete files in the shared folder.

What's wrong with nautilus? 

Thank you.

P.S I joined the linux machines to samba4 dc using likewse open 6.1.

---

### Post by tenmoi on 2012-05-22
Update:

From the terminal:
nautilus smb://server-ip-address
or
nautilus smb://server-FQDN

Nautilus immediately shows the share.

Maybe nautilus has a bug?

---

### Post by druhboruch on 2012-05-22
> There is no NetBIOS browsing support (network neighbourhood) in the 'samba' binary (use nmbd and smbd instead) 

[http://wiki.samba.org/index.php/Samba4/Releases/4.0.0alpha20](http://wiki.samba.org/index.php/Samba4/Releases/4.0.0alpha20)

---

### Post by tenmoi on 2012-05-22
Many thanks. I didn't know this.

---

