---
title: "VMWare Server 2.0 on Ubuntu 11.04"
date: 2011-10-05
forum: Server Platforms
---

### Post by Fmslick on 2011-10-05
hey what up guy's?

I have a server running Ubuntu 11.04 an i am trying to set up VMWare Server 2.0, i have gottin all the way up to this part whit no error's n what not but this one 
( ***sudo ./vmware-install.pl*** ) 
i get "***sudo: ./vmware-install.pl: command not found***" 
 How do i fix this or get it to work?

[IMG]http://img844.imageshack.us/img844/7671/errn.png[/IMG]

---

### Post by collisionystm on 2011-10-05
sudo bash

chmod +x vmware-install.pl

./vmware-install.pl

---

### Post by Fmslick on 2011-10-05
> **collisionystm said:**
> sudo bash

chmod +x vmware-install.pl

./vmware-install.pl


Thanks collisionystm it worked.

---

### Post by Fmslick on 2011-10-05
looks like i need some more help here, now i am getting error's out the butt :(

---

