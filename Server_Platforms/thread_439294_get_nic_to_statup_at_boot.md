---
title: "get nic to statup at boot"
date: 2007-05-10
forum: Server Platforms
---

### Post by systimax on 2007-05-10
Can someone tell me how to add a nic that has no ip addresses assigned to it to start up at boot?

Also can someone tell me the command line util to run after installing another nic into a server box?

And finally is there good docs on these types of server questions? I should i just look at debian server docs?

thanks

---

### Post by Aberrix on 2007-05-10
> **systimax said:**
> Can someone tell me how to add a nic that has no ip addresses assigned to it to start up at boot?

no ip at all? or do you want to use DHCP?

> **systimax said:**
> 
Also can someone tell me the command line util to run after installing another nic into a server box?

you really don't need to do anything, just an ifconfig and it should list the new nic. go into /etc/network/interfaces if you want to change the ip to a static one

---

### Post by systimax on 2007-05-10
thanks..yes no ip at all

its a nic that will be bridge with a vmserver virtual switch, or i nic that i want to use with ethereal or some other security prog

And also ifconfig doesn't show the new nics. Probably cause there not up since i need to learn how to add them with out a ip to the boot sequence

---

### Post by systimax on 2007-05-11
no one uses snort, vmserver, or bridges network adapters that can answer?

Can anyone tell me what script starts your network at boot up. Maybe I can add a line to that that says ifconfig eth1 up

---

