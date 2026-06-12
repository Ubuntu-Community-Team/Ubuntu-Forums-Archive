---
title: "Trouble setting up SAMBA"
date: 2007-08-14
forum: Server Platforms
---

### Post by tigerstudios on 2007-08-14
Hello everyone, 
  

  I really need some help with this.  I'm setting up a samba server with Ubuntu 7.04.  I have the server setup and running however in windows when I click on "View workgroup computers" from the network places window I get a long pause, and then eventually an error saying
"Markland is not accessible. You might not have permission to use this network resource. Contact  the......."

Markland is the name of the workgroup.  I have made sure that my XP Machine is in the proper workgroup.  

Here is my smb.conf file

[global]
    workgroup = MARKLAND
    interfaces  = eth0, lo
    bind interfaces only = yes
    encrypt passwords = No
    preferred master = no
    local master = no
    domain master = no
    admin users = michael
    hosts allow = all

[share1]
    comment = Shared folder
    path = /share
    valid users = lisa, wendy, susan
    invalid users = wayne


Can anyone see what may be causing this problem?     I have both computers hooked up to a dlink router.  I made it as simple as possible.  Both computers are given static IP addresses.

Please help..

Thanks, 

Michael Rhodes
    read only = no

---

