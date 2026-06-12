---
title: "ESXi: deleted NIC, added new one - now I have no connectivity"
date: 2016-09-11
forum: Virtualisation
---

### Post by MattDamon on 2016-09-11
Greetings,

I'm running Ubuntu server 16 in a vm through ESXi. My NIC wasn't configured for the e1000 driver. I couldn't see how I could change this without deleting the NIC so I went ahead and deleted it. I added a new one and now I have no network connection in the vm. [COLOR=#292F34][FONT=verdana]I'm trying to static assign an IP in /etc/network/interfaces. The card isn't named eth0; its ens160. I tried to restart it after the changes using systemctl restart ifup@ens160 but it's still not getting an IP. D[/FONT][/COLOR][COLOR=#292F34][FONT=verdana]oing an ifconfig shows a different name for the card - ens33. At this point, I'm not sure what I should do to get my vm connected.[/FONT][/COLOR]

---

### Post by TheFu on 2016-09-11
Please post the  /etc/network/interfaces file and output from 
```
$ sudo lshw -C network
``` to show all the network devices in the system.

BTW, no virtio?

---

### Post by MattDamon on 2016-09-11
I wasn't able to copy the output so I snipped it and uploaded to [imgur]("http://imgur.com/a/qe8lS")

I'm not familiar with virtio. All I did was just add the adapter(s) when I setup the VM. Should I have done something else?

---

### Post by TheFu on 2016-09-17
interfaces is using the wrong device name. Make it match the one in the lshw output.

BTW, the interfaces files is doing a static IP. If it isn't on the correct subnet, with the correct gateway and DNS settings, it won't work.

---

### Post by MAFoElffen on 2016-09-19
(Back home now...)

Yes, what TheFu said.. but more specifically, you said it was "ens160" when the device is showing up as "ens33".

---

