---
title: "Ubuntu 12.04 Server -not showing on Network"
date: 2012-11-12
forum: Server Platforms
---

### Post by itpro007ca on 2012-11-12
I just installed Ubuntu 12.04 Server(I've ran the Desktop version and other Linuzes in the past and am a Network Admin. by trade,trained on Windows and Netware) with Ubuntu-Desktop.

Firstly,since my modem/router is set for dhcp and I have ip addresses reserved for ea. PC;in this case,192.168.2.10,I installed with dhcp as default.

Secondly,I have installed tightvnc on the Server and all Windows PCs.

I can 'tightvnc' and 'Putty' )and use Remina Remote Desktop fine to Windows ) from all PCs and ping comes back fine.

But...

Ubuntu Server(I call it 'Blackbox') does not appear in Windows Networking on my Windows XP PC,or my Win7 Laptop,but they appear to it and I can acess their folders no problem.

Do I need to punch a hole in its firewall,or is there something else I need to do?

Thanks,
Richard


However,the Ubuntu Server'

---

### Post by bab1 on 2012-11-13
> **itpro007ca said:**
> I just installed Ubuntu 12.04 Server(I've ran the Desktop version and other Linuzes in the past and am a Network Admin. by trade,trained on Windows and Netware) with Ubuntu-Desktop.

Firstly,since my modem/router is set for dhcp and I have ip addresses reserved for ea. PC;in this case,192.168.2.10,I installed with dhcp as default.

Secondly,I have installed tightvnc on the Server and all Windows PCs.

I can 'tightvnc' and 'Putty' )and use Remina Remote Desktop fine to Windows ) from all PCs and ping comes back fine.

But...

Ubuntu Server(I call it 'Blackbox') does not appear in Windows Networking on my Windows XP PC,or my Win7 Laptop,but they appear to it and I can acess their folders no problem.

Do I need to punch a hole in its firewall,or is there something else I need to do?

Thanks,
Richard


However,the Ubuntu Server'
VNC and Putty use DNS and TCP/IP for naming and communication.  When you browse the network you are using NETBIOS and TCP/IP.  With ubuntu you need Samba to advertise the shares.  It sounds like you have installed a Desktop Environment (DE) on the server.  Is this so?

Usuually the DE includes the client routines to allow network browsing.  See if you have at least the *samba-common* package installed.  See if you have the 2 Samba daemons (smbd and nmbd) running.  You should see 2 smbd and 1 nmbd running initially.

---

