---
title: "FTP only accessable locally ?"
date: 2009-08-22
forum: Server Platforms
---

### Post by Pnuts on 2009-08-22
I think I might just be missing something simple, but I'm really not sure.

I have a box running 9.04 amd64, clean install. Installed openssh-server and vsftpd.

I changed the ports for each of them in their config files, say ftp on 1021 and ssh on 1022

I enabled port forward for both ports on my router (running Tomato 1.25)

Remotely (or using my external IP locally) I can connect through ssh without any problems.

When I attempt to connect to my ftp through firefox with [ftp://xx.xx.xx.xx:1021](ftp://xx.xx.xx.xx:1021) I eventually time out.

[http://canyouseeme.org/](http://canyouseeme.org/) reports the port is open.

If I swap the ports between ssh and ftp, i can still connect via ssh, so it makes me think there is a setting on the server itself that is causing the issue, but really, I'm at a loss and have no idea.

Any suggestions?

-Pnuts

---

### Post by cariboo on 2009-08-22
Instead of ftp why not use sftp, it is part of the openssh-server package. Most gui ftp clients support sftp. By using sftp you don't need to run another server, and you don't have to have another port open, it runs on the same port as ssh.

---

### Post by Pnuts on 2009-08-22
Does sftp through openssh-server support anonymous?

I went with vsftpd simply because it is the only one with a guide in the Ubuntu Server guide: [https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html)

Also of note, but should not matter. The jaunty install is using the f4 option for virtual-servers and the install is running via KVM.

---

### Post by hessiess on 2009-08-23
> **Pnuts said:**
> Does sftp through openssh-server support anonymous?

I went with vsftpd simply because it is the only one with a guide in the Ubuntu Server guide: [https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html)

Also of note, but should not matter. The jaunty install is using the f4 option for virtual-servers and the install is running via KVM.

Not sure if it supports anonymous users, however I guess you could just set up a user `anonymous' with no password. You want to avoid ftp if possible as it isn't that secure because it transmits everything, including passwords in the clear(unencrypted) and the protocol design is outdated and dousent work well with modern networking technologies(NAT).

can you assess a server running on any port from outside, if no your ISP is probably blocking it.

---

### Post by Pnuts on 2009-08-23
Yeah, I can access multiple other servers remotely on various ports that I changed for ssh. I also am able to access 2 separate IP cameras with custom ports. I am very sure it is not an issue of a port being blocked.

All this talk of sftp though has peeked my interest and I guess I always could just make an anonymous user.

Last night I was unable to locate a good guide in using openssh-server for this purpose. Does anyone know of a good guide for this, or if not, recommend a different server application for this purpose?

Thanks,
Pnuts

---

### Post by zelekt on 2009-08-24
Hi, check if the server is configured to listen to your external ip, and if it isnt, check if your router translates lan-ip to wan-ip when its ftp traffic :)

---

