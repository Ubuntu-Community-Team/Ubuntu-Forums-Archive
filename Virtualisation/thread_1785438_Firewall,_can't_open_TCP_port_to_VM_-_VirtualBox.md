---
title: "Firewall, can't open TCP port to VM - VirtualBox"
date: 2011-06-18
forum: Virtualisation
---

### Post by cwmoser on 2011-06-18
I have a VirtualBox VM that needs access to a TCP port.
I'm using TCP port 20666.
I cannot communicate with the VM on the port outside of the VM.
I can telnet 127.0.0.1 20666 and get success.

My host is Ubuntu 10.04 64-bit version.
My guest VM is Windows XP.

I've turned off the Windows firewall and have no other firewalls.
Don't have an anti-virus program either.

I have Bridge mode and my guest VM gets a DHCP IP on the same LAN as the host.

I have tried this to open the port on the host Ubuntu OS:
```
$ vboxmanage  setextradata  "WinXP-VirtualBox"  –-natpf1  "myport,tcp,127.0.0.1,20666,,20666"
```

No success.

Anyone else having fire-walling issues with Virtual Box VM's?

Thanks

Carl

---

### Post by Jake.Debord on 2011-06-20
Are you telnetting to 127.0.0.1 from the VM or from the host?

---

### Post by doas777 on 2011-06-20
in your windows guest, run 
```
netstat -a
``` and see if there is a listener for 20666.

should look like this:
```
TCP    0.0.0.0:20666             MyPC:0              LISTENING
```

also, when attempting to connect to your guest via your host, don't use 127.0.0.1, but the guest machines IP on the VMNet

---

