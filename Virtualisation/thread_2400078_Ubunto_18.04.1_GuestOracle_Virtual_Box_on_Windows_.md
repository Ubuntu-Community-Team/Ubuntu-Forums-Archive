---
title: "Ubunto 18.04.1 Guest/Oracle Virtual Box on Windows 7 -&gt; No Internet Connection"
date: 2018-09-02
forum: Virtualisation
---

### Post by jazzbox2 on 2018-09-02
I recently created an Ubunto 18.04.1 virtual guest using Oracle Virtual Box on a Windows 7 machine and have the network settings in Oracle Virtual Box set to NAT, however can't seem to get an internet connection.

 
New to this, but just checked to see if there's an IP address using ifconfig and this is what I got:

[IMG]https://preview.ibb.co/jg0MkK/Untitled.png[/IMG]

Thanks.

Doug

---

### Post by 8h567t20 on 2018-09-05
hello 

i found this link this might have somthing thta can help you

[https://askubuntu.com/questions/363003/no-internet-connection-on-virtualbox-windows-7-as-guest-ubuntu-13-04-as-host](https://askubuntu.com/questions/363003/no-internet-connection-on-virtualbox-windows-7-as-guest-ubuntu-13-04-as-host)

---

### Post by SeijiSensei on 2018-09-05
Try using a bridged connection instead.  That puts the VM directly on the same network as the host.

---

