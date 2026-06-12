---
title: "Where/how to download vmware-server-console"
date: 2007-10-04
forum: Server Platforms
---

### Post by satimis on 2007-10-04
Hi folks,


Ubuntu 7.04 server amd64 - Host OS
vmware-mui-distrib-1.0.4-56528  
vmware-server-distrib-1.0.4-56528


I have both VMWare-mui and VMWare-server installed on /usr/local/src/

They are now running.  Both of them can be started on Console/Terminal, NO GUI.


I follow following document;
How to obtain, secure, install, monitor and log in to VMware's MUI using Linux
[http://searchservervirtualization.techtarget.com/tip/0,289483,sid94_gci1245056,00.html](http://searchservervirtualization.techtarget.com/tip/0,289483,sid94_gci1245056,00.html)

to proceed.


Coming to "VMware Server Console" on the same document, re Downlaod;


I can't resolve how "to obtain the bits for the VMware Server Console. Just point a Web browser at the VMware Server, [https://MGMT_NIC_IP:8333/](https://MGMT_NIC_IP:8333/) and the Web page that comes up will present you with a drop-down menu that lists the different versions of the VMware Server console. Select the version for Linux that is labeled "VMware Server Console for Linux (tar.gz)""

MGMT-NIC_IP is the IP address of the server.  Please help me to understand what is "Just point a Web browser at the VMware Server, https://MGMT_NIC_IP:8333/".

TIA


B.R.
satimis

---

### Post by primski on 2007-10-04
[http://download3.vmware.com/software/vmserver/VMware-server-linux-client-1.0.4-56528.zip](http://download3.vmware.com/software/vmserver/VMware-server-linux-client-1.0.4-56528.zip)

unzip

untar

./vmware-server-console.pl


gl ;)

---

### Post by satimis on 2007-10-04
> **primski said:**
> [http://download3.vmware.com/software/vmserver/VMware-server-linux-client-1.0.4-56528.zip](http://download3.vmware.com/software/vmserver/VMware-server-linux-client-1.0.4-56528.zip)

unzip

untar

./vmware-server-console.pl

Tks for your URL.

It is "VMware-server-linux-client-1.0.4-56528.zip" a zip file under another name.  Are they the same? 


B.R.
satimis

---

### Post by primski on 2007-10-04
yep they are...in the server-linux-client zip, there is a server-console tar.gz and .rpm

---

### Post by satimis on 2007-10-04
> **primski said:**
> yep they are...in the server-linux-client zip, there is a server-console tar.gz and .rpm
Noted with thanks.  I got it.


satimis

---

