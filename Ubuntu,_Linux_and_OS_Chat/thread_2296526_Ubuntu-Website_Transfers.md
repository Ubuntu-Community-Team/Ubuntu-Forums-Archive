---
title: "Ubuntu-Website Transfers"
date: 2015-09-26
forum: Ubuntu, Linux and OS Chat
---

### Post by brian-mccumber on 2015-09-26
Here is an image that depicts just how easy it is to transfer websites from one host to another using Nautilus file manager in Ubuntu. If anyone has done any web design, especially on other operating systems, the simplicity of this process should bring a tear of joy to your eye.

[ATTACH=CONFIG]264667[/ATTACH]

---

### Post by TheFu on 2015-09-27
For static sites, **rsync** is the tool.  Something like ```
rsync -avz SOURCE TARGET
``` - the source and target can be network locations userid@server/path/to/directory ....

For DB drive sites, a mix of rsync and the DB backup method is used.

After all, servers donlt have GUIs or GUI tools.

Of course, both to these methods are likely to loose owner/group and perhaps other permissions, so having a backup that honors those could be very important.

---

### Post by brian-mccumber on 2015-09-29
Well this is mainly a site I built for a client. I moved it from the preview site I set up on a free web host so clients can watch it being built, to it's permanent home on the clients web host.

Moving a site that utilizes a db has a few more steps but I just like being able to drag and drop sites from one web host to another using the file manager. When I was using windows, if I wanted to move a site from host to host I would have to download it via ftp then re-upload it to the new host. Using the file manager in this way I no longer have to download it first.

I will check out rsync tho, so thanks for that.

---

### Post by TheFu on 2015-09-29
[http://www.troyhunt.com/2015/09/introducing-you-to-browser-security.html](http://www.troyhunt.com/2015/09/introducing-you-to-browser-security.html)
It's a fun little exercise that brings to light what sort of CSP a company may or may not have.

Be careful out there.  Don't want your site to be pwnd.

---

