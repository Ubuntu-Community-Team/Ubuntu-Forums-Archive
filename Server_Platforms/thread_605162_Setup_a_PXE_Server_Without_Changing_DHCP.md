---
title: "Setup a PXE Server Without Changing DHCP"
date: 2007-11-06
forum: Server Platforms
---

### Post by mikaelsnavy on 2007-11-06
Hello,
I am trying to setup a PXE server on my network. The machines on the network all are connected to a switch, which goes to a Windows DHCP server which I cannot modify. Every guide for PXE I have seen says you have to modify the DHCP server. Is there any way to setup a PXE server (on any Ubuntu distro) without changing the Windows DHCP server? Maybe install another DHCP server on the Ubuntu box?
Thanks A Lot,
Mikael

---

### Post by talktechnow on 2007-11-06
You could setup an Ubuntu ( or any linux) Box, with 2 x NIC's, one connecting to your Windows DHCP and have a DHCP server running on the 2nd one, and just use a crossover cable to connect one PC at a time.

---

### Post by mikaelsnavy on 2007-11-06
I was trying to do a GhostCast image, so I needed to keep all of the network infrastructure the same. Any ideas??

---

### Post by talktechnow on 2007-11-06
Im unsure on this one, would a DHCP relay work in this case?

[http://en.wikipedia.org/wiki/Preboot_Execution_Environment](http://en.wikipedia.org/wiki/Preboot_Execution_Environment)

That site seems to have some good info, maybe a solution on there.

---

### Post by HermanAB on 2007-11-06
Turn the Windows DHCP server off for the duration of the PXE exercise and use another.

---

### Post by mikaelsnavy on 2007-11-06
I cannot touch the DHCP server, hence I cant turn it off. I will do some research and possibly try the relay.

---

### Post by bwinfrey on 2007-11-13
deleted.

---

