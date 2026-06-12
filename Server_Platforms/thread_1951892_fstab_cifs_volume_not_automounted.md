---
title: "fstab cifs volume not automounted"
date: 2012-04-03
forum: Server Platforms
---

### Post by RMSe17 on 2012-04-03
Hi, I added a line to mount a cifs volume to the fstab.  When the computer restarts, the volume does not get automounted.  If I actually log into the machine, and run "sudo mount -a", the volume gets mounted correctly.  

How do I make fstab automatically mount the cifs volume?

Thanks,
RMSe17

Ubuntu 10.04.04 LTS

---

### Post by Morbius1 on 2012-04-03
There could be a couple of things getting in the way.

* Did you add the mount option: [COLOR=Blue]**_netdev **[COLOR=Black]( don't forget the "_" at the beginning ) to your fstab statement. It's supposed to prohibit the execution of that line until the network is up on your local machine. It doesn't seem to work reliably anymore but it's worth a shot.

* Are you specifying a netbios name or an ip address in fstab. If it's netbios name then it may just not be ready to do that at the time it's executed. 


[/COLOR][/COLOR]

---

