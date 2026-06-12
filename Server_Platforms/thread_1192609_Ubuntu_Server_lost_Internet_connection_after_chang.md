---
title: "Ubuntu Server lost Internet connection after changing router"
date: 2009-06-20
forum: Server Platforms
---

### Post by philtrim on 2009-06-20
I replaced my router, and changed my router LAN ip as well. (Probably should have kept it the same as the old one) Every since I have done this, I can't access my website (externally); Port 80 is open on new router.  I also can't get OUT to the web from my Ubuntu server (to get updates etc..) The only thing that is different is the IP address (lan/eth) IP of the new router.

I changed the Interfaces setting to reflect the new gateway settings in Ubuntu /etc/network/interfaces. I restarted networking, actually restarted the whole machine. Still not working.  

I thought maybe I should change the router IP back to what the other was to see if this solves the problem.

Any thoughts?

---

### Post by philtrim on 2009-06-20
I went ahead and changed the router IP back to what is was, and I noticed immediately that my Putty login was fast, (it slowed way down after I changed the rtr IP.  I haven't tried the external web site yet.  But I will.

Perhaps there is some internal routing that was cached inside Ubuntu server somewhere that I should have cleared.

Any thoughts?

Thanks.

---

### Post by Bachstelze on 2009-06-20
The network settings (IP address, subnet mask, gateway address) are stored in the [font="monospace"]/etc/network/interfaces[/font] file. Open that file in your favourite text editor, change the settings as appropriate and run [font="monospace"]/etc/init.d/networking restart[/font] to restart the networking system.

EDIT: oh well, now you'll know. :p Anyway, no, there's nothing particular to do if you chnged the router's IP back to what it was.

---

