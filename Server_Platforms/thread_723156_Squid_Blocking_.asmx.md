---
title: "Squid Blocking .asmx"
date: 2008-03-13
forum: Server Platforms
---

### Post by u4david on 2008-03-13
I have ubuntu LTS 6.10.
Squid Version 2.5.STABLE12
All set up and working on vmware virtual machine.
Stand alone set up _that means  only selected users/browser is forced
through this proxy.

Purpose of squid: Block access to all internet sites allowing only
"white listed sites"

This is all working and i'm happy with the functionality.

PROBLEM:

One program our company is using is accessing  site for parts brake
down.
All works fine till you get to the point when you need to send email
out of this application.
The email is used to submit parts order or warranty claim.

.trisoftinc.com is in white list and accessible

Squid access log Show series of four(4) attempts to email warranty
claim:

1204825469.465    742 192.168.10.70 TCP_MISS/200 7697 GET
[http://www.trisoftinc.com/QPServices/QPServices45.asmx?](http://www.trisoftinc.com/QPServices/QPServices45.asmx?) sfs DIRECT/
209.221.150.92 text/xml
1204825469.522      0 192.168.10.70 TCP_DENIED/407 1893 POST
[http://www.trisoftinc.com/QPServices/QPServices45.asmx](http://www.trisoftinc.com/QPServices/QPServices45.asmx) - NONE/- text/
html

1204825479.484    673 192.168.10.70 TCP_MISS/200 7697 GET
[http://www.trisoftinc.com/QPServices/QPServices45.asmx?](http://www.trisoftinc.com/QPServices/QPServices45.asmx?) sfs DIRECT/
209.221.150.92 text/xml
1204825479.509      0 192.168.10.70 TCP_DENIED/407 1893 POST
[http://www.trisoftinc.com/QPServices/QPServices45.asmx](http://www.trisoftinc.com/QPServices/QPServices45.asmx) - NONE/- text/
html

1204825483.224   1163 192.168.10.70 TCP_MISS/200 7697 GET
[http://www.trisoftinc.com/QPServices/QPServices45.asmx?](http://www.trisoftinc.com/QPServices/QPServices45.asmx?) sfs DIRECT/
209.221.150.92 text/xml
1204825483.242      0 192.168.10.70 TCP_DENIED/407 1893 POST
[http://www.trisoftinc.com/QPServices/QPServices45.asmx](http://www.trisoftinc.com/QPServices/QPServices45.asmx) - NONE/- text/
html

1204825486.014    284 192.168.10.70 TCP_MISS/200 7697 GET
[http://www.trisoftinc.com/QPServices/QPServices45.asmx?](http://www.trisoftinc.com/QPServices/QPServices45.asmx?) sfs DIRECT/
209.221.150.92 text/xml
1204825486.027      0 192.168.10.70 TCP_DENIED/407 1893 POST
[http://www.trisoftinc.com/QPServices/QPServices45.asmx](http://www.trisoftinc.com/QPServices/QPServices45.asmx) - NONE/- text/
html

Please email me any hints on where to pass through this communication.
u4davidATgmailDOTcom

---

