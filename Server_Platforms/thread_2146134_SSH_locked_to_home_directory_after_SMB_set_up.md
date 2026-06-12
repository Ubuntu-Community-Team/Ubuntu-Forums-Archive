---
title: "SSH locked to home directory after SMB set up"
date: 2013-05-17
forum: Server Platforms
---

### Post by unbuntunewb on 2013-05-17
Hello,

I set up an SMB share on my server now whenever I SSH into the server I am locked in my home directory. This was not the case before I set up SMB. How do I fix this? If I use sudo su I get control back as it was but Id rather not do that. Anyone have any advice?

Thanks

---

### Post by rubylaser on 2013-05-17
Are you SSHing in with a standard user (not root)? If so, being put into your home directory to start is the standard behavior. You can also cd into any directory you have the permissions to view. or you can sudo up to have have root access and get anywhere.

---

