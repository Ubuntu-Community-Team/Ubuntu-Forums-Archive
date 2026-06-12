---
title: "Update DynDNS on startup?"
date: 2006-02-10
forum: Server Platforms
---

### Post by joppe on 2006-02-10
I followed the little guide on [http://ubuntuguide.org/#assignhostnametodynamicip](http://ubuntuguide.org/#assignhostnametodynamicip) and the dyndns works.
However, after reboot it dont, until I run it manually when logged in.
I dont know if Ive done something wrong or not, but it would be nice if it updated the ip when started the computer.

New to Linux but hoping for answer
/ Thanks

---

### Post by skirkpatrick on 2006-02-10
You could put the command in /root/.bashrc and it will be run everytime the machine comes up.  Remember to use sudo to edit.

---

