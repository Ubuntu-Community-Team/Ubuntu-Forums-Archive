---
title: "Cant open Ubuntu GUI on Ubuntu Server"
date: 2021-11-15
forum: Server Platforms
---

### Post by aaasixaaa on 2021-11-15
Hello everyone, I am learning linux and started my first project today. I am running a dogecoin node and like to see the desktop and the gui so I followed this tutorial [https://phoenixnap.com/kb/how-to-install-a-gui-on-ubuntu](https://phoenixnap.com/kb/how-to-install-a-gui-on-ubuntu) . When I finish the tutorial, I can't access the gui or the desktop. I have installed everything im pretty sure. Can someone please help me.

---

### Post by GhX6GZMB on 2021-11-15
I think the point about Ubuntu _Server_ is that it doesn't have a GUI desktop. Install normal Ubuntu instead.

---

### Post by TheFu on 2021-11-15
If you installed "Ubuntu Server", then there isn't any GUI.
If you want a GUI, install one of the many desktop flavors.  The "Server", install doesn't integrate many of the typical things that desktop users expect - like a point-n-click control interface for networking or firewall or DNS and lots of other things.

We need to know the Ubuntu release, the GUI you tried to install and the exact commands you entered along with the exact, relevant, output - especially any errors reported, to be able to help.

Not just any display manager can worth with any DE. There are dependencies.  I don't think Gnome works with anything except gdm, for example.  I don't use Gnome or gdm, so I don't have any first-hand experience.

BTW, if you install more than 1 DE and those DEs are in the same "family" - usually Gnome (GTK) or KDE (Qt), it is possible to have settings written by one of the DEs conflict with a different DE and cause minor to extremely serious problems.  I don't imagine that having 1 GTK-based DE and 1 Qt-based DE would have many, if any, conflicts, however.

In general, is a a really bad idea to load a GUI onto a Server install. Best to just start with the DE-install ISO you want, then add the server programs to it. They will all work.

---

### Post by ActionParsnip on 2021-11-16
Install the desktop version of Focal (Ubuntu 20.04) and you'll be fine. As stated, the whole point of Ubuntu server is to not have a GUI. There is absolutely no difference under the hood

---

### Post by slickymaster on 2021-11-16
*Thread moved to **Server Platforms**.*

---

