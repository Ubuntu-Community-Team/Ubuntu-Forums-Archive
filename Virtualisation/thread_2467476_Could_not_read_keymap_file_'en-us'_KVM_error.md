---
title: "Could not read keymap file: 'en-us' KVM error"
date: 2021-09-27
forum: Virtualisation
---

### Post by Heeter on 2021-09-27
Hi Guys,

did some updates on Ubuntu18LTS server with only KVM server installed. It took a keyboard update of some sort. Now I can't start a virsh vm:

```

root@serv:/home/adminpc# virsh start mailserv
error: Failed to start domain mailserv
error: internal error: process exited while connecting to monitor: Could not read keymap file: 'en-us'

root@serv:/home/adminpc# systemctl enable virtlogd.socket & systemctl start virtlogd.socket
[1] 1852
[1]+  Done                    systemctl enable virtlogd.socket
root@serv:/home/adminpc# virsh start mailserv
error: Failed to start domain mailserv
error: internal error: process exited while connecting to monitor: Could not read keymap file: 'en-us'

root@serv:/home/adminpc# systemctl status virtlogd.socket
&#9679; virtlogd.socket - Virtual machine log manager socket
     Loaded: loaded (/lib/systemd/system/virtlogd.socket; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2021-09-27 17:37:16 MDT; 3min 10s ago
   Triggers: &#9679; virtlogd.service
     Listen: /run/libvirt/virtlogd-sock (Stream)
      Tasks: 0 (limit: 115886)
     Memory: 0B
     CGroup: /system.slice/virtlogd.socket

Sep 27 17:37:16 serv systemd[1]: Listening on Virtual machine log manager socket.
root@serv:/home/adminpc# 

```

Anyone can help me with this error?

Regards

---

### Post by Heeter on 2021-09-28
Hi

Anyone able to assist me?

Regards

---

### Post by MAFoElffen on 2021-09-29
Look for this file:
```

/usr/share/qemu/keymaps/en-us

```
Open it with a text editor to confirm it is readable...

If not... look in 
```

/var/log/apt/history.log

```
And search on "qemu" to see which packages where installed and if there where any errors on installing those packages... You may have to reinstall those packages.

---

### Post by Heeter on 2021-09-30
Ok thank you, will do.

---

