---
title: "vmware workstation 6.05 incompatible with ubuntu 8.04 gtk libraries?"
date: 2008-10-07
forum: Virtualisation
---

### Post by nigelito on 2008-10-07
So I've upgraded my VMware Workstation (on Windows host) from 6.4.x to 6.5.0. It's running an 32-bit ubuntu-8.04 guest.

The good news is that I can now install the standard vmware tools on ubuntu-8.04, and the kernel modules at least seem install and work correctly with the ubuntu kernel. However the user-level tools crash: when vmware-user is run I see two error messages. The first is non-fatal, and reading the vmware forum suggests that it can be safely ignored:

[INDENT][COLOR="Red"]    (vmware-user): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
[/COLOR][/INDENT]

The second however appears to be fatal:

[INDENT][COLOR="Red"]    /usr/lib/vmware-tools/bin/xorg71/vmware-user: symbol lookup error: /usr/lib/vmware-tools/bin/xorg71/vmware-user: undefined symbol: uriComposeQueryCharsRequiredA
[/COLOR][/INDENT]

From what I can see this symbol is supplied by liburiparser.so in the VMware tree (/usr/lib/vmware-tools/lib32/liburiparser.so.1/liburiparser.so.1), but is not present in the Ubuntu version in /usr/lib/liburiparser.so.1.0.0

According to the [uriparser documentation]("http://uriparser.sourceforge.net/doc/html/_uri_8h.html#5d79be075b94fd3292844feb107e0b75") this symbol has only been present since version 0.7.0 of liburiparser, but ubuntu 8.04 has version 0.6.0.

So this appears to be an incompatibility between the version of Gtk used by the vmware-tools and the version supplied by ubuntu 8.04. Or am I missing something else? Does anyone have any clue how to work around this?

Thanks

---

