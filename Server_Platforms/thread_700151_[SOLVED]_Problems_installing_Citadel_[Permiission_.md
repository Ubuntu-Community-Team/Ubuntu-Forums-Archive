---
title: "[SOLVED] Problems installing Citadel [Permiission Denied]"
date: 2008-02-18
forum: Server Platforms
---

### Post by ade234uk on 2008-02-18
I am trying to install Citadel. I am getting the following error

../var/lib/dpkg/info/citadel-server.postinst: 78: /usr/lib/citadel-server/migrate_aliases.sh: Permission denied

How do I unlock this?

---

### Post by freebeer on 2008-02-18
I'm guessing that you need to run the install script with sudo privileges.

---

### Post by ade234uk on 2008-02-18
I did run it sudo command.
Now it keeps asking me to sudo dpkg --configure -a

Which I do, and then it still get stuck with permission denied again.

How do I break out of this loop?

---

### Post by Wizard of Aahz on 2008-02-18
ade234uk - 

I went bugged one of the citadel developers. He gave me this direction for you.

sudo chmod a+x /usr/lib/citadel-server/migrate_aliases.sh
sudo dpkg --pending --configure


He asked me to let you know that they'll be fixed in the debs soon. He's working on it.

Good luck with citadel.
-Aahz

---

### Post by ade234uk on 2008-02-23
Thank you very much for your help.

---

