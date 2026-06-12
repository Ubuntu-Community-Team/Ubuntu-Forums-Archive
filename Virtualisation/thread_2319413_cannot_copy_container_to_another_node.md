---
title: "cannot copy container to another node"
date: 2016-04-04
forum: Virtualisation
---

### Post by f-matt-o on 2016-04-04
i have ubuntu 14.04 with lxd ppas installed and running on two machines. I am trying to copy an existing working container from one machine to the other to repurpose the original machine.

command i used  lxc copy node1:cont1 node2:cont1

Doing this will freeze the command prompt for about 20 minutes then it kicks me off the ssh session.
Looking at the destination node I do see that the container is now in the list using lxc list, but it seems the copy never finishes and is corrupt when trying to launch. using ps | grep lxd I can see rsync running.

I did add the server using lxc remote add node2 xxx.xxx.xxx.xxx with no problems and it shows in the list lxc remote list.

Is there something I am doing wrong?

Thanks,

Matt

---

### Post by MAFoElffen on 2016-04-05
One method, from the lxc-users mail list:
[http://comments.gmane.org/gmane.linux.kernel.containers.lxc.general/4741](http://comments.gmane.org/gmane.linux.kernel.containers.lxc.general/4741)

---

