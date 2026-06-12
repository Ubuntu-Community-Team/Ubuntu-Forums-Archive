---
title: "unable to access Virtual network editor - Workstation 14.1 Ubuntu 17.10"
date: 2018-06-24
forum: Virtualisation
---

### Post by ayman-1 on 2018-06-24
[COLOR=#111111][FONT=Ubuntu]Hi,
I've just installed VMWare Workstation 14 on My PC with OS Ubuntu 17.10.
When attempting to run it via the vmware workstation (Edit > Virtual Network Editor), ask me password and nothing happens.
so I tried to launch the Virtual network editor via cli sudo vmware-netcfg I get prompted for root credential and then i get this error, anyone seen this that can help?
```
pc1@mypc$vmware-netcfg
```
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
```
pc1@mypc$sudo /usr/lib/vmware/bin/vmware-netcfg
```No protocol specified
xcb_connection_has_error() returned true
No protocol specified
xcb_connection_has_error() returned true
No protocol specified
** (vmware-netcfg:14122): WARNING **: Could not open X display
No protocol specified
(vmware-netcfg:14122): Gtk-WARNING **: cannot open display: :0
```
 root@mypc#/usr/lib/vmware/bin/vmware-netcfg 
```   No protocol specified
xcb_connection_has_error() returned true
XDG_RUNTIME_DIR (/run/user/1000) is not owned by us (uid 0), but by uid 1000! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
No protocol specified
xcb_connection_has_error() returned true
XDG_RUNTIME_DIR (/run/user/1000) is not owned by us (uid 0), but by uid 1000! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
No protocol specified
** (vmware-netcfg:14043): WARNING **: Could not open X display
No protocol specified
(vmware-netcfg:14043): Gtk-WARNING **: cannot open display: :0


[/FONT][/COLOR]

---

### Post by ayman-1 on 2018-06-30
[COLOR=#111111][FONT=Ubuntu]Problem fixed after upgrading my OS to ubuntu 18.04 and reinstall vm workstation 14.1.2. 
note:
after installing vmware go to: Shared VM ( right click ) ---> permission and check if you have privilege. you can remove / add user.[/FONT][/COLOR]

---

