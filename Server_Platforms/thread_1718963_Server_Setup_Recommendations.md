---
title: "Server Setup Recommendations"
date: 2011-04-01
forum: Server Platforms
---

### Post by ductiletoaster on 2011-04-01
Ok I have been look into redeploying my server with Ubuntu 10.04 Server edition. But I wanted some advice on partitioning scheme.
the server will serve as a development platform for myself and will maintain FTP via ssh, LAMP, maybe Tomcat.... basically anything a web developer would use. It may also eventually host my personal blog so I want to keep that in mind. I may also setup a diskless (another computer laying with no drive) around cluster that will remote boot from this server

Server Specs: 
Amd Athlon 64 3700 single core
2gb DDR 400
200gb sata HDD
1000gb sata HDD

Current Plan:
200gb
|boot|root|swap?|

1000gb
|home|swap?|

Partitioning Scheme Questions: 
1) Should each drive have its own Swap? Does it matter?
2) Any suggestions on other partitions?
3) I was thinking of using the home as follows

home/
     backups/    (I rsync to my windows machine)
     www/        (this would be were web files are hosted)
     admin/      (this would be the user account folder)

---

