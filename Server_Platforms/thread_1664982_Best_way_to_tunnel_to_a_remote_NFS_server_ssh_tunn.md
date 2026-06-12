---
title: "Best way to tunnel to a remote NFS server? ssh tunnel, stunnel or openvpn?"
date: 2011-01-11
forum: Server Platforms
---

### Post by damang111 on 2011-01-11
Does anyone know the best and simplest way to do this?
I'd like the share to be mounted over the tunnel on boot with as little scripting as possible and be as secure as possible without exposing more than one port to the outside.

I will be trying this method:
[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

once the tunnel is established and 'always on' NFS would take care of the file system mount obviously.

Lots of the information I have been reading is not up to date it seems.

Does anyone have any experience with this?

tia.

---

### Post by sj1410 on 2011-01-12
Try openvpn. it can get you a bridged as well as routed vpn tunnel.

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

