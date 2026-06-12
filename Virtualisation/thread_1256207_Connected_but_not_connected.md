---
title: "Connected but not connected"
date: 2009-09-02
forum: Virtualisation
---

### Post by olymacfoogal on 2009-09-02
Hi all,

Brand new to ubuntu, still have a windows head. using ubuntu in a virtual box with Vista as host (training wheels). I can ping websites and it works fine but i cannot go online. I tried changing to a bridged network from NAT but now I'm not connected at all. I'm in a college so i'm connecting via a proxy server.

---

### Post by olymacfoogal on 2009-09-03
Ok made a mistake  before, I can ping locally in ubuntu so the network card is working and i can get online in windows. But i cannot ping outside in my virtual ubuntu. Any ideas/things to try would be great!

---

### Post by Perryg on 2009-09-03
Ping may be disabled by the school and or proxy.  You say that you are able to get out with the guest so I guess I need to know more about what it is you need to do that you can not.

---

### Post by olymacfoogal on 2009-09-14
Hey there, sorry for not being clear. Things have changed since my last post. On my host (windows vista) I can connect to everything I like. On my guest (Ubuntu 9.04 in virtual box with guest additions installed) i can now connect to the outside with firefox and a server located in the uni. However i cannot connect to the repositories to update or install new software. it gives the following error:

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'cache.it."myuniversity".com'

Firefox automatically detects network settings and I think I need the package manager to do the same. Any ideas on how I can change the package manager so it detects settings automatically?

---

### Post by olymacfoogal on 2009-09-14
Ok problem solved, the update manager was trying to connect to an old proxy, applying changes system-wide in proxy settings didn't change this, so I manually changed it in the program to the new proxy.

---

