---
title: "LTSP server trouble"
date: 2009-07-20
forum: Server Platforms
---

### Post by asai on 2009-07-20
Hi,
I have installed a 9.04 LTSP server and trying to log in from a thin client.
The client connects fine, and the login screen appear.
I'm typing the username and password, but after a little while, there's a error message saying "No response from server, restarting" and the login screen is back.
I have tried login to the server with ssh username@serverip, and that works perfectly.
What could be wrong?

---

### Post by asai on 2009-07-20
Solved it!
> sudo ltsp-update-sshkeys
sudo ltsp-update-image

But I have another issue on a 8.04 LTS server.
When trying to boot from the client, it hangs for a while after IP address is assigned, and then a error message appear:
> UDP checksum error
This message keeps coming every 5 min or so, until i CTRL-C and system halts. Any ideas on this matter?

---

### Post by asai on 2009-07-21
*bump*

---

