---
title: "Automatic File permissions?"
date: 2005-04-07
forum: Server Platforms
---

### Post by Belldandy on 2005-04-07
On my web server, whenever I upload files, by default its only readable by the owner. I want all of my files by default to chmod 755 in a particular directory. How can I do this?

Thanks!

---

### Post by dataw0lf on 2005-04-07
This is known as the umask.  
'man umask'
(sorry, I'm tired and about to go to bed, so I'm just going to point you in the right direction)

---

### Post by Belldandy on 2005-04-07
Thank you!!!

---

