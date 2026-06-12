---
title: "virtual box shared folder"
date: 2010-06-17
forum: Virtualisation
---

### Post by lovo on 2010-06-17
hi,
Im using virtual box to have a winXP and I need to see my linux folder which are in ext4 partition. 
I have installed guest addition, restarted. I then Device>shared folder > and I enter my home/user/ folder... 
This is how I do usually but here its not working.
I would appreciate any help
swan

---

### Post by TheFu on 2010-06-18
Which OS is the host and which it the client?
What version x.x.x and OSE or PEUL of virtualbox?

These instructions for a Linux client mounting a shared folder may help too [http://jdpfu.com:82/2008/10/26/virtualbox-host-drive-access](http://jdpfu.com:82/2008/10/26/virtualbox-host-drive-access)

---

### Post by naknak987 on 2010-06-20
I'm having the same problem. I'm running Ubuntu 10.04 as the host and windows xp pro as the guest. I made a folder in my home folder called share, and in the vb settings made it a share folder. Start up the Windows and open the command prompt and enter net use x:\\vboxsvr\share and it comes back with error 67 : the network name cannot be found. I have the guest additions installed as well.

---

### Post by TheFu on 2010-06-21
Have you tried it the GUI way?  Does vboxsrv show up in your "network neighborhood"?

I cannot tell, but is there a space between "X:" and "\\vboxsvr"?  That {space} is critical.

---

