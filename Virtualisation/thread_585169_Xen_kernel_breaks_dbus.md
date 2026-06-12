---
title: "Xen kernel breaks dbus"
date: 2007-10-21
forum: Virtualisation
---

### Post by navaburo on 2007-10-21
I just installed the ubuntu-xen-server package on my gusty system.

When i try to login th Gnome i get logged out immediately because dbus exited unexpectedly.

Openbox works however, though apps that use dbus complain.

Restarting dbus gives:
```
cmerck@alderan:~$ sudo /etc/init.d/dbus restart
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ] 
 * Stopping ConsoleKit daemon console-kit-daemon                         [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                             
Segmentation fault (core dumped)
```

Reverting to the old kernel works fine (by setting default 2 in /boot/grub/menu.lst).

Any ideas why Xen would break dbus?

Thanks

---

### Post by deta on 2007-11-10
I have this bug too when i tried to start dbus with the init script.
Navaburo, did you found any solution? Or somebody from ubuntu xen maintainers?
I can only guess what the problem can be... maybe the missing of libc6-xen package, but i could not install it because of unmet dependency problem...
Navaburo, did you install libc6-xen package?

---

### Post by deta on 2007-11-10
relevant information maybe: [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/161783](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/161783)

---

