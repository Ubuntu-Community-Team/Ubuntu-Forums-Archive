---
title: "Remote server as Windows mapped drive"
date: 2009-08-24
forum: Server Platforms
---

### Post by peekaboo on 2009-08-24
How can I map a shared folder on my **ubuntu server at home** as a drive on my **windows machine at work**?

I have no problem mapping at home using ```
\\server_dhcp_address\shared_folder
```
but when I try ```
\\home_ip_address\shared_folder
``` it fails.

What am I doing wrong?

---

### Post by Warren Watts on 2009-08-24
Is your server at home behind a router?  If so, you you have the proper ports forwarded?

---

### Post by dmizer on 2009-08-24
Before you start thinking about forwarding ports, please consider that samba is NOT safe to forward across the internet.

You should consider setting up a VPN so you can connect from work.

---

### Post by peekaboo on 2009-08-24
> **Warren Watts said:**
> Is your server at home behind a router?  If so, you you have the proper ports forwarded?
Ports 22 and 80 are forwarded to the server.
I can connect to my server from work with Filezilla and Putty.

I'm working on my thesis from home and work and it's a pain trying to synch the files all the time so I want to work on the same file from both places.

---

### Post by peekaboo on 2009-08-24
> **dmizer said:**
> Before you start thinking about forwarding ports, please consider that samba is NOT safe to forward across the internet.

You should consider setting up a VPN so you can connect from work.OK.  should I unforward port 80?

Will VPN allow me to mount my home server folder from so I can have MATLAB, LaTex, etc. work directly on files on my home server?

---

### Post by flabdablet on 2009-08-25
If your home router is already forwarding port 22 to your home server, then presumably you can already ssh into your home server from work. That being the case, you can probably use ssh port forwarding to get to Samba on your home server; you probably don't need a full blown VPN. Have a look at this:

[http://www.blisstonia.com/eolson/notes/smboverssh.php](http://www.blisstonia.com/eolson/notes/smboverssh.php)

---

### Post by dmizer on 2009-08-25
> **peekaboo said:**
> OK.  should I unforward port 80?
Most likely ... yes. Unless you plan to host a website. Port 80 is for www.

> **peekaboo said:**
> Will VPN allow me to mount my home server folder from so I can have MATLAB, LaTex, etc. work directly on files on my home server?

Yes

Edit:
This is probably a less complicated solution ... 
> **flabdablet said:**
> If your home router is already forwarding port 22 to your home server, then presumably you can already ssh into your home server from work. That being the case, you can probably use ssh port forwarding to get to Samba on your home server; you probably don't need a full blown VPN. Have a look at this:

[http://www.blisstonia.com/eolson/notes/smboverssh.php](http://www.blisstonia.com/eolson/notes/smboverssh.php)

---

