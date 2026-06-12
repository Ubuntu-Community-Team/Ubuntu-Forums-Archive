---
title: "KVM host setup strategies"
date: 2010-03-01
forum: Server Platforms
---

### Post by admkenshin on 2010-03-01
Hello,

I am setting up a new workstation/server at my office (development, not production), and I have came up with a few interesting ways to do it, but I wonder which one would be the best from a security and performance point of view.

On the computer, I will need to run: An Ubuntu 9.10 Desktop install, a file server, a groupware server (zimbra, simple groupware or citadel), an HTTP/FTP server, and some other services. I will also need to virtualize a win7 install from linux.

Preferably, the servers should keep running even if I crash my desktop install. So, I thought of using KVM. However, I am worried about performance, which one of the following would you think is best?

[LIST]
[*]A barebone ubuntu server running vm’s and an X-server. KVM virtualization of all servers and the desktop install, windows running as needed. LVM and encryptfs on the host, no encryption on the guests.
[/LIST]
[LIST]
[*]As above, but with no encryption on the host, and encryption on the guests instead (less risk of data loss?)
[/LIST]
[LIST]
[*]As above, but encryption at both host and guests. Slow?
[/LIST]
[LIST]
[*]Servers run natively on the host, desktop is virtualized. Best performance, but a crash in one server could bring the system down? Also, host might be open to attacks.
[/LIST]
[LIST]
[*]Desktop is the host, servers run directly on it. Best 3d performance, but if I crash the desktop its all over.
[/LIST]
[LIST]
[*]Something else...
[/LIST]

As I am not (yet) an IT administration professional, I would be very happy for any suggestions you may lend me.

Thank you for taking your time to read this,
admkenshin

---

