---
title: "Server to replace Win7 box for SMB"
date: 2012-12-18
forum: Server Platforms
---

### Post by beengone on 2012-12-18
A small business client of mine has been using an in-use Win7 box as their file share. Obviously, not the best setup. They really don't need much more than a simple file share and remote access to that share would be great. When they move locations I'll likely set them up with a Windows server running RDS sessions and thin clients, but for now I need something quick and simple. I've been testing Windows Home Server a bit and just started the downloads for SME Server and Ubuntu Server. No worries on client machine backups as they don't store anything [important] locally. So, I just need to back up the server and would love to have a bare metal restore option.

Other details: They have 10-12 workstations and a few network printers using direct IP printing. They also have a bunch of USB shared printers. I'm upgrading them to a gigabit unmanaged (probably) switch soon to replace their chain of consumer hubs.

Any advice as to what is the best system with regards to easy-of-maintenance, file permissions by user, integration with their all-windows(Vista/7 Home Premium)environment, reliability, and long-term cost including setup time? Pros/Cons to each?

Thanks a ton.

---

### Post by chadk5utc on 2012-12-18
you may want to consider a look at Zentyal
[http://www.zentyal.org/](http://www.zentyal.org/)

---

### Post by beengone on 2012-12-18
interesting. Could someone please compare (pros/cons) on the four?

---

### Post by chadk5utc on 2012-12-18
First thing I find is Linux being open source is Cost effective(FREE) from the start, and a true multi user OS again cost savings no extra license fees. You can however pay for support or a commercial version if so desired but with the flexibility of open source and great community support forums its not necessity. Personally I will choose Linux/Unix products over windows any day for performance, security and stability, fast updates, less systems overhead. 
 Just my opinion based on personal and professional experience. I work for an IT company and of all of the locations we provide services for we have far less trouble with our Linux systems than any of the windows machines.

 Chad

---

### Post by beengone on 2012-12-19
That's very helpful. Would you be able to comment on features and ease of use for the end-users? This has to be dead simple to them and I need to be able to get in and get my bearings quickly. Can anyone comment on strengths/weaknesses to each product?

---

