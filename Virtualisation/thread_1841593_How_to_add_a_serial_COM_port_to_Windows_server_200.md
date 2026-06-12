---
title: "How to add a serial COM port to Windows server 2008 using Linux + KVM + Qemu?"
date: 2011-09-09
forum: Virtualisation
---

### Post by supersaya on 2011-09-09
We are using Linux + KVM + Qemu with libvirt on our servers to manage virtual WIndows 2008 Servers. The Host is Ubuntu 11.04.

The point is on one of our Windows server 2008 guest, we need to connect a dial-up modem. After connecting the modem to the Host, we found that it was connected to /dev/ttyS0. We did checked that the modem was recognized using

echo atdt3333333 > /dev/ttyS1

Server .xml configuration contains

<serial type='pty'>
  <target port='0'/>
</serial>
<serial type='dev'>
  <source path='/dev/ttyS0'/>
  <target port='1'/>
</serial>
<console type='pty'>
  <target type='serial' port='0'/>
</console>

Now, launching our virtual server, Windows doesn't see any COM port at all, and therefore doesn't see the modem ( all sort of virsh define / stop / start ... had been done )

Does anyone know how to achieve this ?

---

