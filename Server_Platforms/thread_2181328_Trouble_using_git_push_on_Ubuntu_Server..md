---
title: "Trouble using git push on Ubuntu Server."
date: 2013-10-17
forum: Server Platforms
---

### Post by Travier on 2013-10-17
I'm having a lot of trouble with internet connectivity on a Dev server I'm working with. Currently we are attempting to push a commit to github but are having no luck. Here's what I've gathered so far:

*Can ping any outside address
*wget will not work with any address
*ssh -T [EMAIL="git@github.com"]git@github.com[/EMAIL] results in a timeout error
*Other computers on the same network have no trouble connecting to github
*Iptables seem to be set correctly:
[HTML]Chain INPUT (policy ACCEPT)target     prot opt source               destination         
Chain FORWARD (policy ACCEPT)target     prot opt source               destination         
Chain OUTPUT (policy ACCEPT)target     prot opt source               destination [/HTML]

My assumption is that some part of the server's configuration is not set but I'm sure not where to look.

Thanks for your time!

---

### Post by houstonbofh on 2013-10-17
Ping is a very small packet, so MTU problems do not show up there.  Try setting the MTU to 1400 and see if things resolve.

Here are a few different links on how to do that.

[http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html)
[http://askubuntu.com/questions/230926/how-do-i-change-the-mtu-value-on-ubuntu](http://askubuntu.com/questions/230926/how-do-i-change-the-mtu-value-on-ubuntu)
[http://ubuntuforums.org/showthread.php?t=1887063](http://ubuntuforums.org/showthread.php?t=1887063)

---

