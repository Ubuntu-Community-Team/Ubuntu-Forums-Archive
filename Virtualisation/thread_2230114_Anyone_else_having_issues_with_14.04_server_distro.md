---
title: "Anyone else having issues with 14.04 server distro and xrdp?"
date: 2014-06-17
forum: Virtualisation
---

### Post by akcorr on 2014-06-17
I have 14.04 LTS desktop version running at home on oracle's virtualbox  and that seems to work fine with XRDP.  I came to work and fired up the server distro on our vmware environment all I get when  trying to RDP to the server is a grey screen.  I've heard installing  something like lxde will work but that didn't get me anyway.  Anyone  else having these issues?

---

### Post by TheFu on 2014-06-18
Welcome to the forums.

"Server" additions do not have a GUI. NONE.  So, expecting a GUI tool to work, well .... that just won't.  The preferred way to interface with any UNIX/Linux server is over an **ssh** connection - this is text.  **putty** is the normal Windows program for this. From any Linux, just open a terminal and use ssh directly.

If you explain more about your VMware environment - like which product - we might be able to help more. There will be a non-GUI console available. This should be enough to get the IP address for the server, then use some ssh client to connect, provided you installed the ssh-server.

---

### Post by oldos2er on 2014-06-18
Moved to Virtualisation.

---

