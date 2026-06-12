---
title: "Virtual Machine Sans Gnome"
date: 2008-06-21
forum: Virtualisation
---

### Post by einraz on 2008-06-21
How can I run VMWare Workstation without the overhead from Gnome? Someone said that you can kill Gnome and then start VM with the following code, but I can't get it to work.

```
sudo /etc/init.d/gdm stop
sudo X :1 -ac & DISPLAY=:1 vmware
```

Edit: This is 8.04 Hardy Heron

---

### Post by einraz on 2008-06-23
Nobody has any suggestions?

---

### Post by bradmkjr on 2008-06-24
I think you are confusing VMware server with VMware workstation. VMware server can run "headless", on a basic server, and then the virtual machines can be accessed via ssh, vnc, rdp, etc from a second system which is running a desktop platform such as gnome, kde or windows. VMware workstation is a gui based application, which I believe requires the gui to load.

Hope this helps,
Bradford Knowlton
[http://x86v.com](http://x86v.com)

---

