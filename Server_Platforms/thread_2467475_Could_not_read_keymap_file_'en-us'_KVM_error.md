---
title: "Could not read keymap file: 'en-us' KVM error"
date: 2021-09-27
forum: Server Platforms
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

### Post by TheFu on 2021-09-27
I've never seen that sort of error.  
Can you connect to the libvirt from the GUI manager ... virt-manager on a different workstation?  

For any lurkers, /var ran out of space which has been resolved (I believe).

Looks like something related to the keymap for that VM got modified.  Any clues in the VM.xml file?
Do other VMs start on the same server?

I think you'll have to figure this out. I have no special knowledge about that error and have 4 VMhosts on 18.04 today.  None of mine use root/sudo to start them up.  My normal userid is in the libvirtd group and has full control over all VMs.

---

### Post by Heeter on 2021-09-27
Yes, I will [solved] this thread 

I have 2 vm, both virsh images has same error when opening.

I tried virt-manager on ubuntu laptop same error shows up in popup

How do I check my userid, FU?

---

### Post by MAFoElffen on 2021-09-29
Check the thread of "this" that you opened in the Virtualization Section (the continuing saga?)...

---

