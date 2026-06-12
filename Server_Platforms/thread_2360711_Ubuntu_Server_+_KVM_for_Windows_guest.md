---
title: "Ubuntu Server + KVM for Windows guest?"
date: 2017-05-07
forum: Server Platforms
---

### Post by lks45br on 2017-05-07
Hello guys!

Im starting working now with kvm, and at Ubuntu Desktop is very easy to work cause it haves graphical environment, and with desktop edition is very easy deploy windows guest on vm manager.

But the desktop edition take a lot of memory and cpu usage for desktop env, for vm hosting is the best using just the ubuntu server. The problem is: how can i deploy windows guest at ubuntu server if its does not have desktop environment to install the windows guest?

Thank you!

---

### Post by darkod on 2017-05-07
You use virt manager on any Ubuntu Desktop machine to connect to the KVM host, and you have the same GUI to work with while deploying any linux/windows guests.

PS. Just to clarify more, the virt manager connection to KVM hosts works on the standard ssh port 22. So as long as you have ssh access to the remote server that is KVM host, you can use virt manager from any ubuntu desktop with a GUI. You can also deploy guests on command line on the KVM host, but especially for windows guest installations it is much more comfortable using the graphical virt manager.

---

