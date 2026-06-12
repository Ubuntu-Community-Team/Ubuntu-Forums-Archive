---
title: "http pendrive application"
date: 2008-05-03
forum: Server Platforms
---

### Post by wilkerlucio on 2008-05-03
Hi all,

i installed a lamp server at by ubuntu and all is running correctly, but... i has one application that i work in different places (in my home and at my work) and for portability reasons i keep this application at my pendrive (Kingston 4GB). To run this application direct by my pendrive i tried to create a symbolic link at www folder to link at pendrive application folder.

at this point i'm getting 2 problems

1 - when i try to access the application apache gives a Forbidden error: [Sat May 03 20:11:42 2008] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www/intranet

2 - when the symbolic link is working i cant unmount the pendrive... and because of this i need to create the symbolic link everytime i plug the pendrive and need to remove the link before unmount... i want to know if is possible to configure to automatic create this link when pendrive is inserted and automatic remove the link before unmount, this is not required but will be usefull

for the first error, the pendrive is normally accessible and i sure that link pointing correctly...

---

