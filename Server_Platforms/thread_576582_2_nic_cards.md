---
title: "2 nic cards"
date: 2007-10-15
forum: Server Platforms
---

### Post by infinitezero on 2007-10-15
The box is acting as a server/workstation. So, I am using eth0 for my connection to windows boxes in our local network for file/printer sharing. eth1 is the connection for my static IP (for the outside world to access my wiki/ftp/svn servers). As far as eth1 goes everything works find, people can access the wiki/ftp/svn servers but as soon as someone from inside the local network access a shared folder on eth0 it hoses eth1 and nobody can access my wiki/ftp/svn servers.

Thanks,
iz

---

### Post by infinitezero on 2007-10-15
Do I need to install a NAT server?


iz

---

### Post by fatbastard spice on 2007-10-15
Definitely need some sort of masquerading/NAT for the windows machines. I just use an iptables bash script to set it up. I've also set it up using shorewall. 

No idea if that's responsible for the eth1 issue though.

---

