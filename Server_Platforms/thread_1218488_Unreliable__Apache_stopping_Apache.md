---
title: "Unreliable / Apache stopping Apache"
date: 2009-07-20
forum: Server Platforms
---

### Post by jtdeloach10 on 2009-07-20
Every couple of days Apache stops or something, just bam - nothing. Sometimes SSH goes with it and I have to manually (push the button) restart the server, once it comes back up SSH and everything is running fine except Apache...
I have figured out the problem, and a slow/painful solution, the problem is that when Apache tries to start it says that the ports 8080 and 443 ( I don't use 80 ) are already taken and it can't start.
netstat -tupan will show me it is true those ports are being used. The program using it is apache so I get it's pid and kill it then manually start apache2. 


I would like to know if there is a way to solve the problem of the ports, or a way to automatically kill apache then start it?

---

