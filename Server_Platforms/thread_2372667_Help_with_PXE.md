---
title: "Help with PXE"
date: 2017-09-27
forum: Server Platforms
---

### Post by jahwillprovide on 2017-09-27
I work in an environment where we have to make 100s of usbs that constantly corrupt themselves
I’ve decided that the best way to do this is through pxe booting all the servers, but I can’t seem to find any tutorials at all that help me do what I need to do. I can set up the dhcp and tftp, but I want to boot up a preconfigured ISO to all of the servers. Is this actually possible, there isn’t any tutorials on it that I’ve found on this forum or others.

---

### Post by wildmanne39 on 2017-09-27
*Thread moved to **Server Platforms**.*

---

### Post by Tadaen_Sylvermane on 2017-09-28
LTSP makes this easy. It's was originally for thin clients but you can pxe boot anything with it. I use it for media centers at my house, they all boot off of the server. Can have a single image to manage that all the "clients" boot from and use.

---

### Post by jahwillprovide on 2017-09-28
I’ll try that out, just set up a new vanilla ubuntu and made my dhcp, I’ll let you know

Edit
I tried to get it running but by including the LTSP dhcpd config it breaks my dhcp and doesn’t wanna work

---

