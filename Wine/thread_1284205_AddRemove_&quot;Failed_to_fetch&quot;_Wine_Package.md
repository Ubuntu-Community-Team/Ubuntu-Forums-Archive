---
title: "Add/Remove &quot;Failed to fetch&quot; Wine Package #3"
date: 2009-10-06
forum: Wine
---

### Post by bayouwillie on 2009-10-06
In Add/Remove, Synaptic, and using the terminal, I am getting a "failed to fetch" for package #3 (...winbind_3.3.2-1ubuntu3.1_i386.deb) when I try to install Wine. At the bottom of the error message: 404 Not Found, and then it lists an IP address.

I finally decided to install it anyway (chose "yes" to install with missing packages) and Wine now works fine on 2 different machines. Installed Evernote in Wine and it works well. Don't know what the error messages are about.

---

### Post by Cytomax on 2009-10-17
The exact error message is this... anyone know why?
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.3.2-1ubuntu3.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.3.2-1ubuntu3.1_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]

I browsed [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba) and the only thing there is 
winbind_3.3.2-1ubuntu3_i386.deb

winbind_3.3.2-1ubuntu3.1_i386.deb does not exist........ i wonder why

---

