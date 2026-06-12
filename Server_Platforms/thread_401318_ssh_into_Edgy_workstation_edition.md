---
title: "ssh into Edgy workstation edition"
date: 2007-04-04
forum: Server Platforms
---

### Post by JohnnyTarr on 2007-04-04
Hi,

I'm just curiuos about what one would need to do or enable to allow ssh or telnet connectins to one's ubuntu box.

---

### Post by huygens on 2007-04-04
Maybe I misunderstood you. But if all you want is being able to connect to your Ubuntu via SSH, then here is the solution:
Install openssh-server and that's it :-) You can use either the command line (e.g. apt-get or aptitude) or a graphical interface (e.g. Synaptic).
After installing it, you have a default and decent installation of SSH working out of the box.

Now, if you want to use ssh from Ubuntu to connect somewhere else. The package to install is openssh-client.

---

