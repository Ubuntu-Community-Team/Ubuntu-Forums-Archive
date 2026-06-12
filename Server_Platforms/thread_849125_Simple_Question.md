---
title: "Simple Question"
date: 2008-07-04
forum: Server Platforms
---

### Post by ptgood on 2008-07-04
Hi everybody, i've just got a simple question.

I have a old computer, and i want to make it the server of my home network, in order to use it as an hard disk for all my clients.

Which is the main difference between installing the ** SERVER EDITION** or **XUBUNTU** (with nfs-kernel-server)???

Can you tell me the advantages and disadvantages of the two installations?

Thanks
Ptgood

---

### Post by ibutho on 2008-07-04
The server version does not include any GUI apps and it comes with many server apps for dhcp, web, ftp etc. These are not present on the desktop oriented versions although you can install them using the package manager.

---

### Post by dominiquec on 2008-07-04
If it's an old computer, Ubuntu 8.04 Server probably won't work on it.  The kernel of the server version now requires PAE (to address memory beyond 4GB) and your old computer won't have it.

Suggestion is to download the alternate install version of Ubuntu 8.04 and install a command-line system.

---

### Post by hyper_ch on 2008-07-04
it is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

