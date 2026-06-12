---
title: "port forwarding in openssh"
date: 2009-09-29
forum: Server Platforms
---

### Post by bbala2020 on 2009-09-29
I maintain a server which can access internet via proxy pointing to another server. I want users of my server to access internet only via my server. ie they need to ssh to my server with X11 forwarding and open up a firefox or elinks etc.. but because of port forwarding feature, users computer can get internet without having to use resources of my server. ie 
```
ssh username@myserver -L 3128:proxyserver:proxyport
``` gives their computer the full internet access. This is not desirable and they should be banned to do so. How do i prevent it?

---

### Post by Lars Noodén on 2009-09-29
'AllowTcpForwarding' in [sshd_config](http://linux.die.net/man/5/sshd_config) might be what you want to look at.  

You can then disallow forwarding for all users and use [b]Match[/b&#305;] to allow it for a certain group, like staff. 

If they have shell access they can still probably find a way to forward, unless further measures are taken.  **ForcedCommand** might be one option.  So might **ChrootDirectory**.  usermod could be used to set a restricted shell, too, like rbash.  

I know the above options are present in Ubuntu 9.10a6

---

