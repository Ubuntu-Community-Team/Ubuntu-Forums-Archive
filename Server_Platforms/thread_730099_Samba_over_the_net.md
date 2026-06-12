---
title: "Samba over the net??"
date: 2008-03-20
forum: Server Platforms
---

### Post by SuperMiguel on 2008-03-20
Well i seted up a samba server, is there a way to sends file over the net?? or im better off using ssh for files over the net?

---

### Post by smileypaul on 2008-03-20
Can't use samba directly over the net.

use ftp, or ssh.

---

### Post by HermanAB on 2008-03-20
You can tunnel Samba over SSH, Stunnel or OpenVPN.

Cheers,

Herman

---

### Post by SuperMiguel on 2008-03-20
any advantage over regular ssh?

---

### Post by netlogic on 2008-03-20
If you are sharing with other Unix box that has ssh, just use Gnome's ssh mount utility. If you aren't using Gnome, use the sshfs package. If you are trying to mount windows share from UNIX using ssh, you have to route your 443 port to another port using -D option. I believe WINS and broadcast will totally break. Also, you have to poke holes on the firewall on the both side. This only works if you have DNS configured, but you can also mount by the ip address. It is easier to use OpenVPN if Windows is involved.

---

