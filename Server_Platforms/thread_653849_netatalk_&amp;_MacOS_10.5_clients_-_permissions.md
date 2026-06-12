---
title: "netatalk &amp; MacOS 10.5 clients - permissions"
date: 2007-12-30
forum: Server Platforms
---

### Post by der mike on 2007-12-30
Hello,
first post here, hope you can help me figuring this one out - a search around here found unfortunately nothing. I have a Feisty fileserver on my home network, running both samba and netatalk (2.0.3-5) for the various clients for a while without problems. 

Now, I have added an Mac mini to my network, running MacOS 10.5 (Leopard) and I've run into a permission issue with folders created from the new machine. Under MacOSX 10.4.x, creating new files/folders on the atalk volumes produced file permissions of 777 on them. Now with Leopard, those folders end up being created with 700 permissions (files end up with 777), making it impossible for other users to access them.

My guess is that the real culprit is Leopard, by using a more stringent policy for folders on servers, but is there a way around it (like with samba, where you can define global file/folder permissions)?

thanks for your help,
Mike

---

