---
title: "automatic login on ubuntu server 12.04 after boot"
date: 2012-08-16
forum: Server Platforms
---

### Post by hagonbc on 2012-08-16
Hi guys! I need to configure my Ubuntu Server 12.04 installation in order to enable automatic login on normal user account (hagonbc) after boot. I googled on this topic but the only tutorial which i found was invalid (not working). Please help me :-)

---

### Post by cariboo on 2012-08-16
The only reason I can think of that you would want to enable auto login, is if you are using a gui on your server, and you want to login remotely. I suggest you think very carefully about doing that, especially if your server is facing the internet, as remote login is one of the most often used methods to break into a system.

If you aren't comfortable working from the command line, I'd suggest using ssh and X-forwarding. Have a look at [this]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding") wiki page, in the Single applications section it shows you how to run a graphical program remotely.

---

### Post by CharlesA on 2012-08-16
What cariboo said.

What are you trying to do with your server?

---

