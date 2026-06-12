---
title: "Cannot install newest Intel Graphics 1.0.2"
date: 2013-08-20
forum: System76 Support
---

### Post by raphael-estrada on 2013-08-20
I get an error at 11% when running the graphics installer I obtained from here: [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)
The particular installer I chose for Ubuntu x64: [https://download.01.org/gfx/ubuntu/13.04/main/pool/13.04/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.2-0intel3_amd64.deb](https://download.01.org/gfx/ubuntu/13.04/main/pool/13.04/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.2-0intel3_amd64.deb)

I run it with sudo via the command line and it fails, complaining that it cannot remove libdrm2.

Error screenshot:
[http://imagebin.org/268117](http://imagebin.org/268117)

Any suggestions?

Edit: system details
Galago UltraPro with Ubuntu 13.04 x64, factory installation after running automatic software updates.

---

### Post by raphael-estrada on 2013-08-21
I solved this. A PGP key for the intel repo was missing in apt.

I noticed this when running "sudo apt-get update", it complained about this key missing: 8D8847D52F4AAA66

On key server:
[http://keyserver.ubuntu.com:11371/pks/lookup?op=vindex&search=0x8D8847D52F4AAA66](http://keyserver.ubuntu.com:11371/pks/lookup?op=vindex&search=0x8D8847D52F4AAA66)

To resolve, I added the key to apt like so:

wget -q "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x8D8847D52F4AAA66" -O- | sudo apt-key add -

After, running the intel installer via sudo went through and after reboot everything is ok.

---

