---
title: "Netatalk zone"
date: 2006-07-15
forum: Server Platforms
---

### Post by coobav on 2006-07-15
I set up PC/MAC file server using samba&netatalk. But i have one problem, chooser doesnt see my server. I connects thru given ip, but that is unconvenient. I think the problem is here:

Jul 15 10:02:55 server afpd[6204]: Can't register server:AFPServer@net1
Jul 15 10:02:55 server afpd[6204]: ASIP started on 192.168.0.240:548(4) (2.0.3)
Jul 15 10:02:55 server afpd[6204]: DSIConfigInit: Error registering afp://192.168.0.240/?NAME=server&ZONE=net1 with SRVLOC

i tried to set zone (ATALK_ZONE=@net1) in configs but it didnt help

---

