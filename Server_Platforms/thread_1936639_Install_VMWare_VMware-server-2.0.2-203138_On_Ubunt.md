---
title: "Install VMWare VMware-server-2.0.2-203138 On Ubuntu Server 11.10"
date: 2012-03-06
forum: Server Platforms
---

### Post by BobGbob on 2012-03-06
Hi all,  

Very new to Ubuntu/Linux.  I have installed an Ubuntu 11.10 server and am attempting to install VMware-server-2.0.2-203138 on top of it.  ( VMware-server-2.0.2-203138.i386.tar.gz) on top of it to run other OS's.   The reason I chose Ubuntu server as the base is because: 

1. I want to become more proficient at using the Linux language, especially the command line and the OS structure. 
2.  From everything I have read,  Ubuntu uses much less overhead than than an MS based OS. 

At any rate,  can anyone point me in the best direction to install VMWare on an Ubuntu 11.10 server?   I have done some checking, but the only directy reference I have found is  

[http://ubuntuforums.org/showthread.php?t=1747360](http://ubuntuforums.org/showthread.php?t=1747360)

and 

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)


Is there a better alterntative?  Is VMPlayer 4 the same thing?   

Thanks!!  

Bob G.

---

### Post by Diametric on 2012-03-06
I can't help you with setting up VMWare on a server, but I can refer you to Virtual Box.  Go here:  [https://www.virtualbox.org/](https://www.virtualbox.org/)  and check it out.  It is very similar to VmWare's Vplayer software and is easy to set up.  I use it regularly.

Good luck.

---

### Post by Catalyph on 2012-03-06
VMware server has not been touched or developed since 2009, it is unlikely it will work in Ubuntu 10.X or higher.

Try Player 4.0 for Linux

[http://downloads.vmware.com/d/info/desktop_end_user_computing/vmware_player/4_0](http://downloads.vmware.com/d/info/desktop_end_user_computing/vmware_player/4_0)

---

### Post by BobGbob on 2012-03-06
Thanks to both of you for the advice! I will give both a try. The worst that can happen is that I screw it up and have to rebuild it it. In which case, I learn that much more. :)  

Catalyph, what is the difference between VMPlayer and VM server? I would assume that the server is a more robust package?

---

### Post by BobGbob on 2012-03-07
Okay, answered my own question.  Defitely don't need a VMServer.  Just looking at the pros and cons of VMPlayer vs VirtualBox.   Thanks again guys!

---

