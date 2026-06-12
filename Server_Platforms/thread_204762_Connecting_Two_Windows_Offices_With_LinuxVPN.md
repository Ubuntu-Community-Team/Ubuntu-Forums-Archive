---
title: "Connecting Two Windows Offices With Linux/VPN"
date: 2006-06-27
forum: Server Platforms
---

### Post by johndavid on 2006-06-27
Ok, right now i have a base office running 3 servers on a single domain. Primary Domain Controller is Windows SBS 2000, One member server is running windows server 2000 and the other member server is running server Server 2003 R2, We have about 8 or 9 client machines on this local network. Accross town we have a second office that is currently connecting to our primary office via, a VPN. now at the base office we have a linksys VPN router.  Problems we are currently having is Authentication taking a while and the vpn seems slow,  people had recomended that i setup a linux machine t controll the second office and keep the tunnel connected all the time? would i be wasting my time trying to setup a linux server at this second office? or do you think configuring this linux box to handle authentication and keeping this connection live at all times is worth the effort?  Right now the primary office is on DSL, second office is on Cable.  both came back with 1.5 megabits on the bandwidth test. sorry for the long post but im not sure if we should setup this box or upgrade our bandwidth or both?](*,)

---

### Post by Soleil-Raid on 2006-06-27
Try OpenVPN. It's very secure, nice and fast, and runs on Windows, Linux, Mac, BSD, Solaris... So you can connect up different boxes and each end without issues.

---

### Post by LordHunter317 on 2006-06-27
[QUOTE=johndavid]Ok, right now i have a base office running 3 servers on a single domain. Primary Domain Controller is Windows SBS 2000,[/quote]Active Directory DC, you mean.  PDC are deprecated tech.

>  Problems we are currently having is Authentication taking a while and the vpn seems slow,Well, the Linksys may not be fast, but auth is always going to be slow until you put another server in there.  Seperate sites should have seperate DCs and domains.   Get another Windows server.

> both came back with 1.5 megabits on the bandwidth test.1.5 up?  That's going to be the limiting factor and I doubt that.

---

