---
title: "Unable to connect VirtualBox RDP server"
date: 2013-02-08
forum: Virtualisation
---

### Post by tedius on 2013-02-08
I'm trying to connect to the RDP server running on my virtualbox install.

The setup I have is VirtualBox 4.1.12, with the extensions pack, running on Ubuntu 12.04, with Windows XP as the guest OS.

```

rdesktop localhost

```

This works fine.  I then go to my laptop, a Samsung N220 running Mint 14, and run the command
```

rdesktop 192.168.0.13

```

This will eventually timeout with the exit code 76 "Protocol error or unable to connect to remote host".  

Can anyone tell me why I cannot connect to the RDP server?
Thanks

P.S. I've attached a file with the output from "VBoxManager showvminfo"

---

