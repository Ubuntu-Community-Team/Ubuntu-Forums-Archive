---
title: "IP address keeps comming?"
date: 2006-03-08
forum: Server Platforms
---

### Post by iMac on 2006-03-08
I have firestarter and i've noticed it is repediatley blocking the same 2 ip addresses at the exact same time. 205.188.176.103 TCP, and 64.12.165.67 

The ip addresses are being blocked about every 2 seconds. I did a WHOIS on the ip addresses and they are comming from the same place. Someone with America Online internet service. Here is part of the WHOIS for the one ip.
64.12.165.67
Record Type: 	  	IP Address

OrgName:    America Online, Inc. 
OrgID:      AMERIC-158
Address:    10600 Infantry Ridge Road
City:       Manassas
StateProv:  VA
PostalCode: 20109
Country:    US
___________________________ _________________________
Should I be worried? I also disconnected my router and reconnected it and i haven't gotten anymore yet.

---

### Post by Zelut on 2006-03-08
My guess is that its some script sourced from one of many windows viruses/worms.  Its probably trying to spread itself with the user at 64.12.165.67 completely unaware.

If firestarter is blocking it then I wouldn't worry about it.. at least its being blocked.  I dont have firestarter just in front of me but you should be able to set a rule to ignore/refuse/drop anything from those IPs.  That way they are just refused from now on.

---

### Post by iMac on 2006-03-08
I found the ignore feature, i'll add it. Thanks for your help!

---

