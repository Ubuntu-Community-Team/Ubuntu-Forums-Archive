---
title: "FileZilla PC to PC file transfer via wifi [Xubuntu to and from Mint]"
date: 2017-04-30
forum: Ubuntu/Debian BASED
---

### Post by weyland42 on 2017-04-30
I routinely use FileZilla to do file transfers between Xubuntu and Android devices using home wifi. Same with Mint, same Android devices. The Android app is ES File Explorer.

When ES FE connects it tells me what IP and Port to use in FileZilla. For example [ftp://192.168.1.106:3721/](ftp://192.168.1.106:3721/). Works fine.

How do I do the same thing between the Mint desktop and the Xubuntu laptop, both using FileZilla? FileZilla doesn't tell me what Port to use, and every one I've tried fails.

I've tried 21 and several in the range 6000 to 50000. Nothing works.

What am I missing?

---

### Post by Dennis N on 2017-04-30
Maybe you don't want to hear about another tool, but between my Linux computers on the local network, I have been using gigolo for years to initiate the connections with SSH (said to be more secure than ftp). You can open file manager window on the other machine, so you are not just looking at two side-by-side lists of files, and can easily browse. Copy and paste work between client and host; no file download queues. Can handle multiple connections too.

You need to install openssh-server on the host machine (or both machines, it you want to work from either). The client, openssh-client is installed on Ubuntu by default.

As to the port, in the initial connection with gigolo you are not required to specify, but in my bookmarked connection details, I see it has supplied port 22 for SSH.

---

### Post by weyland42 on 2017-04-30
Thanks, Dennis. I'll give it a go.

---

### Post by weyland42 on 2017-05-01
Gigolo works like a charm, Dennis. Thanks again. :D

---

