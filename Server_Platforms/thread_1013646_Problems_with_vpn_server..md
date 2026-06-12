---
title: "Problems with vpn server."
date: 2008-12-17
forum: Server Platforms
---

### Post by al_do on 2008-12-17
Hi i need some help about ubuntu ssh server. I connect two distant networks over the internet by vpn conections (I use pptpd). My question is this how i can enable file sharing between two pcs conected to the server over the internet.
Thank before.:confused:

---

### Post by gtdaqua on 2008-12-17
You can use Samba - is very popular. But use it under a secure cloud. If you have ssh server running, then you can browse the other computer's folders by "ssh://" (which will inititate an sftp communication). Windows clients can use WinSCP to share files via ssh.

---

### Post by al_do on 2008-12-17
Thank i will try this

---

### Post by al_do on 2008-12-17
I understand but is it posible to view the other pcs in windows explorer like a normal network???

---

### Post by al_do on 2008-12-17
the schema is this 

windows network A- Dsl modem - internet - Dsl modem - Ubuntu server - windows network B.

I want to view shared files from pcA on pcB on windows explorer

---

### Post by gtdaqua on 2008-12-17
It is possible. You can browse windows networks but it takes a bit of work to make it happen.

---

### Post by al_do on 2008-12-17
Ok can you help me

---

### Post by gtdaqua on 2008-12-17
> **al_do said:**
> Ok can you help me

You will have to use Samba for accessing files between Ubuntu and Windows seamlessly.

Familiarize yourself with Samba. An excellent post that I followed to setup Samba is here:
**[HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605")**

Secure your samba mounts (to certain extent):
**[[HOW TO] Mounting smbfs Shares Permanently]("http://ubuntuforums.org/showthread.php?t=255872)**

---

