---
title: "Ports needed by a network printer under a corporate environment"
date: 2009-11-10
forum: Security
---

### Post by Sarmacid on 2009-11-10
Does anyone know which ports does a network printer need under a corporate environment to work?

I've been searching hopelessly and need to leave some printers with as few ports open as possible.

---

### Post by fargle on 2009-11-10
Normally just 9100 for RAW printing and 515 for LPD spooling.  However, I know Windows clients (and I think Linux as well?) want to use SNMP to the printer to check on status, so consider 161 and 162 UDP as well.

If you need to remotely administer the printer's network interface card, you might need 80 and/or 443 as well to pull up the Web management interface.

---

### Post by Sarmacid on 2009-11-11
Thanks for the reply. The ports on the printer are ```
TCP 80 (HTTP)
TCP 443 (HTTPS)
UDP 137 (WINS)
UDP 161 (SNMP)
UDP 162 (SNMP Traps)
TCP 515 (LPR/LPD)
TCP 631 (IPP)
TCP 5000 (XML)
TCP 5001 (IPDS)
UDP 5353 (MDNS)
TCP 8000 (HTTP)
TCP 9000 (Telnet)
TCP 9100 (Raw Print)
TCP 9200 (IR Alerts)
UDP 9200 (Discovery)
UDP 9300 (NPAP)
TCP 9400 (Lexmark Print Port)
TCP 9500 (NPAP)
TCP 9600 (IPDS)
UDP 9700 (Plug-n-Print)
TCP 10000 (Telnet)
```
I know that I don't need FTP and Telnet, but I do need http and https for administration, dns and wins are needed too. However I overdid closing ports yesterday and problems arose, so I'm trying to not let that happen again. Wouldn't I need to enable ipp?

---

### Post by fargle on 2009-11-11
I highly doubt it - IPP is not used all that much as far as I know.  We regularly open printers over our WAN here with nothing but 9100 and they work fine.

---

