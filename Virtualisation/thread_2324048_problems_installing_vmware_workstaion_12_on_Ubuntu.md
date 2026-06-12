---
title: "problems installing vmware workstaion 12 on Ubuntu 16.04"
date: 2016-05-10
forum: Virtualisation
---

### Post by voriain on 2016-05-10
Hello
So I downloaded the bundle and did the following
                         **$ sudo  chmod +x   VMware-Workstation-Full-12.1.0-3272444.x86_64.bundle ** 
                   **   $   sudo   ./ VMware-Workstation-Full-12.1.0-3272444.x86_64.bundle   **
 but I got the errors:
(vmware-installer.py:4296): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",    [approx 33 times]
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

and then the installation halted.

Anyone know how I should proceed?

---

### Post by QDR06VV9 on 2016-05-10
> **voriain said:**
> Hello
So I downloaded the bundle and did the following
                         **$ sudo  chmod +x   VMware-Workstation-Full-12.1.0-3272444.x86_64.bundle ** 
                   **   $   sudo   ./ VMware-Workstation-Full-12.1.0-3272444.x86_64.bundle   **
 but I got the errors:
(vmware-installer.py:4296): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",    [approx 33 times]
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

and then the installation halted.

Anyone know how I should proceed?
I have moved your thread to Virtualisation to get you the best chance for a solution.
And in the mean time have a look here: [https://communities.vmware.com/thread/453282?start=0&tstart=0](https://communities.vmware.com/thread/453282?start=0&tstart=0)
You might need to read the whole page carefully.
Good luck:)

---

### Post by voriain on 2016-05-10
When I rebooted and tried 
    sudo ./ VMware-Workstation-Full-12.1.0-3272444.x86_64.bundle
the same errors appeared, but this time the installation proceeded !!

Don't know why, but at least its working now

---

### Post by QDR06VV9 on 2016-05-10
Hey That's great.:)
Glad that it worked.

---

