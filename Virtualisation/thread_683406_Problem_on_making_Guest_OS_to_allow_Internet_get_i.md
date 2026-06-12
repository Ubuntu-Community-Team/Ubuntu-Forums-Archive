---
title: "Problem on making Guest OS to allow Internet get in"
date: 2008-01-30
forum: Virtualisation
---

### Post by satimis on 2008-01-30
Hi folks,


Ubuntu 7.10 server amd64 (Host)
Postix, SquirrelMail
IP addr 192.168.0.10

CentOS 5 x86_64 (Guest)
Apache2
IP addr 192.168.0.20

VMWare server
VMWare-server-console
Bridged connection
Shared NIC (one NIC)
One public IP


Having spent >2 weeks to make web port 8080 forwarded to 192.168.0.20 (CentOS) w/o result.  CentOS can connect Internet but Internet can't get in CentOS.  Finally I found all www ports 80, 443 and 8080 must be forwarded altogether.  Then Internet can get in CentOS;

[http://public_ip](http://public_ip)

can display the defaut page of CentOS (Apache2 Test Page powered by CentOS)

(Or set 192.168.0.20 CentOS as DMZ.  But all other ports will be forwarded leaving Ubuntu no port to use)


Now another problem comes up.  SquirrelMail can't start on Ubuntu.  It is a web-base application.  I think it also needs www port to work.


Is there any clue to solve this problem?  TIA.

On this test I expect to make Ubuntu as a Mail Server and CentOS as web Server.  Whether to forward all 3 www ports is only required on sharing NIC.  For 2 NIC one www port forwarded will work?


Futhermore on Ubuntu I found besides;

/etc/init.d/apache2

also

/etc/init.d/httpd.vmware


What is "/etc/init.d/httpd.vmware"  for ???  "/etc/init.d/apache2" already starts Apache2


B.R.
satimis

---

