---
title: "help - cannot connect to instance"
date: 2011-07-12
forum: Ubuntu Cloud and Juju
---

### Post by zoranpantic on 2011-07-12
Hi Everyone,
 
I installed 11.04 on three virtual machines (inside VMware Workstation):
- server01: clc, ws3; public net 192.168.1.0/24, private net 10.0.0.0/24
- server02: cc, sc; public net 192.168.1.0/24, private net 10.0.0.0/24
- server03: nc; private net 10.0.0.0/24
 
I was following the guide "Eucalyptus Beginner's Guide", I installed all 3 servers with success, and opened admin web interface, downloaded images, and credentials.
 
When I connect to the cloud via Hybridfox, I can see the instances, and I can launch them (though some are just pending - forever, but once in a while I get an instance running.
 
Next problem is that I cannot connect to the running instance via Hybridfox (putty just times out), and I cannot ping the public DNS IP listed for the instance.
 
If I try to lounch an instance from a terminal, i.e.:
euca-run-instances DCC21051 -a WKy3rMzOWPouVOxK1p3Ar1C2uRBwa2FBXnCw -s hirJ3LM3ravNxML1veyXLFqcG29H5C3l6ng -U [http://192.168.1.98:8773/services/Eucalyptus](http://192.168.1.98:8773/services/Eucalyptus)
... I don't get response, though I can see in Hybridfox that the instance is pending, and then it terminates.
 
What do I do wrong, and where do I start troubleshooting?
 
Thanks in advance!
 
Regards,
 
Zoran

---

