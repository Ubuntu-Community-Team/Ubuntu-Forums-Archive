---
title: "Only 1 XP can connect to via samba"
date: 2008-06-21
forum: Server Platforms
---

### Post by max_power on 2008-06-21
I created a simple samba file server for my home. I have a laptop with XP professional  as well as a desktop running XP pro. 

I am able to connect to the file server with my laptop but the desktop says the workgroup is not accessible. I read some place that because there is no domain controller the XP boxes freak out because they are both trying to take control of the network.

If anyone has any suggestions how to fix this I would appreciate it .

---

### Post by freebeer on 2008-06-21
This usually happens (in my experience) when you don't add the machine accounts along with the user accounts.

---

### Post by windependence on 2008-06-21
Have you added the second machine to the SAMBA workgroup?

-Tim

---

