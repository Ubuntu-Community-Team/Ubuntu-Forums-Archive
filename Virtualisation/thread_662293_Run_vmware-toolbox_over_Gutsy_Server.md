---
title: "Run vmware-toolbox over Gutsy Server"
date: 2008-01-08
forum: Virtualisation
---

### Post by frankabel on 2008-01-08
Hi all,

I want run vmware-toolbox command on a Gutsy Server, not GUI. After some initial errors due to lack on server of some library I install libx11-6, libxi6 and gksu packages but still get the following errors, here what I did to get the error:

I log in with "ssh -X RemoteServerWithVMwareServer", then I execute "gksudo vmware-toolbox" and get the following error "(gksudo:4032): Gtk-WARNING **: cannot open display:", when try with "sudo vmware-toolbox" the error is "Gtk-WARNING **: cannot open display: localhost:10.0".

I have X11Forwarding yes

Just add that I want keep my server installation with the minimal GUI related packages, just the minimal things to run vmware-toolbox.

Thanks in advanced

Salute
Frank Abel

---

