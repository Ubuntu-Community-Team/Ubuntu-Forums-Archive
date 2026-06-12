---
title: "Firewall"
date: 2006-05-03
forum: Server Platforms
---

### Post by Coruba67 on 2006-05-03
Hi again guys,

Was wondering if anyone knew how to open Firewall ports via SSH and what the port/s are that need to be opened to allow samba in...

Anyone know where the config files are?

Cheers

---

### Post by 0x3 on 2006-05-03
Hi dude

[PHP]pico /etc/apf/conf.apf[/PHP]

------

and here is you would 2 add any port ( open it in your machine )


goes to the control of the firewall list
then
Common egress (outbound) ports 
[PHP]# Common egress (outbound) TCP ports 
EG_TCP_CPORTS='21,25,80,443,43' 
# 
# Common egress (outbound) UDP ports 
EG_UDP_CPORTS='20,21,53'[/PHP]
if you would 2 close any port ! goes 2

Common ingress (inbound) ports 

then you'll see this
[PHP]# Common ingress (inbound) TCP ports -3000_3500 = passive port range for Pure FTPD 
IG_TCP_CPORTS='21,22,25,53,80,110,143,443,2082,2083, 2086,2087, 2095, 2096,30000_35000' 
# 
# Common ingress (inbound) UDP ports 
IG_UDP_CPORTS='53'[/PHP]

Then close The Pico with Saveing your editing 

finaly [PHP]Crtl+x[/PHP] = [PHP]Y[/PHP] :=)


regard's

---

### Post by superman69 on 2007-10-08
Hi there

Do you know how to make bfd work with apf on ubuntu?

Please let me know thanks

---

