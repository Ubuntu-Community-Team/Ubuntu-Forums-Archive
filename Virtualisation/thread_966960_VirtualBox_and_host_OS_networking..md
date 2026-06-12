---
title: "VirtualBox and host OS networking."
date: 2008-11-01
forum: Virtualisation
---

### Post by bogdanbiv on 2008-11-01
A friend of mine (using Kubuntu 8.0.4, KDE 3.5.9, ) has installed Virtual Box from the software channel and broke her networking setup. Basically after she had setup Virtual Box and its virtual ethernet interface, bridge the gateway has been replaced by the virtual ethernet interface. 
Also when typing "sudo ifconfig eth2 down" it does not really bring down the interface. Same for knetwork-manager GUI.

I noticed that the network works properly in Recovery root mode: eth2 is not enabnled and google responds to ping.

Also where is the network bridge interface configuration?

---

### Post by lavy on 2008-11-01
Hy,
I've solved the problem.
I mean I find a workaround that worked. I rebooted the system and still works :)

I went in KNetworkManager, opened eth2 (Configure interface)  and changed from dhcp to bootp. I think that disabled the interface. Then I tried to configure the default gateway from KNetworkManager and didn't work. So I typed the following command in shell:

sudo route add default gw ip

where ip is the ip of default gateway
Now everything works fine.
But still do you know a normal way to disable the interface created by virtualbox?
Tx

---

