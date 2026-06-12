---
title: "VMware player. New problems here...."
date: 2010-06-13
forum: Virtualisation
---

### Post by flycojet on 2010-06-13
Hello everyone.
Can not run VMware Workstation and VMware Palyer on UBUNTO 10.04 with kernel 2.6.32-22-generic
Installation is quiet. But does not work... compilation error in the kernel.
I tried the recommendation of CALC and TJet1.8 without success. ([Http://ubuntuforums.org/showthread.php?p=9253619](Http://ubuntuforums.org/showthread.php?p=9253619))

Could someone help me

---

### Post by fjgaude on 2010-06-13
If you are trying to run both WS and Player on the same host I don't think it can work, not possible.

---

### Post by flycojet on 2010-06-13
Hi fjgaude. Tks for replay.
Actually I can  not use none of the versions.
The installation is quiet, no errors.
But when I run the  first time  ( VMware palyer or VMware workstation) the following module:
vmare kernel  module updater
The step that gives error is as follows: Virtual network  device
The error message is: Unable to start service
see log file /  temp/vmware-root/setup-19708.log for detail
******************************************************
Jun 13 21:33:10.987: app-3078158016| Log for VMware Workstation pid=19708 version=7.0.0 build=build-203739 option=Release
Jun 13 21:33:10.987: app-3078158016| The process is 32-bit.
Jun 13 21:33:10.987: app-3078158016| Host codepage=UTF-8 encoding=UTF-8
Jun 13 21:33:10.987: app-3078158016| Calling: "/usr/lib/vmware/bin/vmware-modconfig --launcher=/usr/bin/vmware-modconfig --icon=vmware-player --appname=VMware --gcc=/usr/bin/gcc --headers=/lib/modules/2.6.32-22-generic/build/include --gcc-ignore-minor"
Jun 13 21:33:10.988: app-3078158016| Using configuration file /etc/vmware/config.
Jun 13 21:33:10.988: app-3078158016| Using library directory:  /usr/lib/vmware.
LOG NOT INITIALIZED | Created dependency tree.
LOG NOT INITIALIZED | -- Processing libgtkmm-2.4.so.1 --
LOG NOT INITIALIZED | libgtkmm-2.4.so.1 validator returned true.
LOG NOT INITIALIZED | Using the system version of libgtkmm-2.4.so.1.
LOG NOT INITIALIZED | -- Finished processing libgtkmm-2.4.so.1 --
LOG NOT INITIALIZED | Accessibility is not enabled.
LOG NOT INITIALIZED | Accessibility is not enabled.
LOG NOT INITIALIZED | -- Processing libgtk-x11-2.0.so.0 --
LOG NOT INITIALIZED | libgtk-x11-2.0.so.0 validator returned true.
LOG NOT INITIALIZED | Using the system version of libgtk-x11-2.0.so.0.
LOG NOT INITIALIZED | -- Finished processing libgtk-x11-2.0.so.0 --
LOG NOT INITIALIZED | -- Processing libglib-2.0.so.0 --
LOG NOT INITIALIZED | libglib-2.0.so.0 validator returned true.
LOG NOT INITIALIZED | Using the system version of libglib-2.0.so.0.
LOG NOT INITIALIZED | -- Finished processing libglib-2.0.so.0 --
LOG NOT INITIALIZED | System libcurl.so.4 has version 7.19.7 (need 7.19.5) and has NOT been compiled with c-ares support.
LOG NOT INITIALIZED | libpangoxft-1.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libcairomm-1.0.so.1 <SYSTEM>
LOG NOT INITIALIZED | libXcomposite.so.1 <SYSTEM>
LOG NOT INITIALIZED | libglibmm_generate_extra_defs-2.4.so.1 <SYSTEM>
LOG NOT INITIALIZED | libgdkmm-2.4.so.1 <SYSTEM>
LOG NOT INITIALIZED | libstdc++.so.6 <SYSTEM>
LOG NOT INITIALIZED | libXrandr.so.2 <SYSTEM>
LOG NOT INITIALIZED | libsexymm.so.2 <SHIPPED>
LOG NOT INITIALIZED | libpangomm-1.4.so.1 <SYSTEM>
LOG NOT INITIALIZED | libvmware-modconfig.so <SHIPPED>
LOG NOT INITIALIZED | libgtk-x11-2.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libXdmcp.so.6 <SYSTEM>
LOG NOT INITIALIZED | libssl.so.0.9.8 <SYSTEM>
LOG NOT INITIALIZED | libgtkmm-2.4.so.1 <SYSTEM>
LOG NOT INITIALIZED | libcurl.so.4 <SHIPPED>
LOG NOT INITIALIZED | libfontconfig.so.1 <SYSTEM>
LOG NOT INITIALIZED | libexpat.so.0 <SHIPPED>
LOG NOT INITIALIZED | libvmwarebase.so.0 <SHIPPED>
LOG NOT INITIALIZED | libgthread-2.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libXcursor.so.1 <SYSTEM>
LOG NOT INITIALIZED | libpng12.so.0 <SYSTEM>
LOG NOT INITIALIZED | libcrypto.so.0.9.8 <SYSTEM>
LOG NOT INITIALIZED | libXrender.so.1 <SYSTEM>
LOG NOT INITIALIZED | libXdamage.so.1 <SYSTEM>
LOG NOT INITIALIZED | libart_lgpl_2.so.2 <SYSTEM>
LOG NOT INITIALIZED | libglib-2.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libpangoft2-1.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libglibmm-2.4.so.1 <SYSTEM>
LOG NOT INITIALIZED | libgdk-x11-2.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libpangox-1.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libpango-1.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libgobject-2.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libpangocairo-1.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libatkmm-1.6.so.1 <SYSTEM>
LOG NOT INITIALIZED | libcairo.so.2 <SYSTEM>
LOG NOT INITIALIZED | librsvg-2.so.2 <SYSTEM>
LOG NOT INITIALIZED | libgmodule-2.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libxml2.so.2 <SYSTEM>
LOG NOT INITIALIZED | libsexy.so.2 <SHIPPED>
LOG NOT INITIALIZED | libXinerama.so.1 <SYSTEM>
LOG NOT INITIALIZED | libgvmomi.so.0 <SHIPPED>
LOG NOT INITIALIZED | libview.so.2 <SHIPPED>
LOG NOT INITIALIZED | libfreetype.so.6 <SYSTEM>
LOG NOT INITIALIZED | libgcc_s.so.1 <SYSTEM>
LOG NOT INITIALIZED | libsigc-2.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libgio-2.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libatk-1.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libvmwareui.so.0 <SHIPPED>
LOG NOT INITIALIZED | libgiomm-2.4.so.1 <SYSTEM>
LOG NOT INITIALIZED | libXau.so.6 <SYSTEM>
LOG NOT INITIALIZED | libXft.so.2 <SYSTEM>
LOG NOT INITIALIZED | libgdk_pixbuf-2.0.so.0 <SYSTEM>
LOG NOT INITIALIZED | libXfixes.so.3 <SYSTEM>
LOG NOT INITIALIZED | Loading system version of libpangoxft-1.0.so.0.
LOG NOT INITIALIZED | Loading system version of libcairomm-1.0.so.1.
LOG NOT INITIALIZED | Loading system version of libXcomposite.so.1.
LOG NOT INITIALIZED | Loading system version of libglibmm_generate_extra_defs-2.4.so.1.
LOG NOT INITIALIZED | Loading system version of libgdkmm-2.4.so.1.
LOG NOT INITIALIZED | Loading system version of libstdc++.so.6.
LOG NOT INITIALIZED | Loading system version of libXrandr.so.2.
LOG NOT INITIALIZED | Loading system version of libpangomm-1.4.so.1.
LOG NOT INITIALIZED | Loading system version of libgtk-x11-2.0.so.0.
LOG NOT INITIALIZED | Loading system version of libXdmcp.so.6.
LOG NOT INITIALIZED | Loading system version of libssl.so.0.9.8.
LOG NOT INITIALIZED | Loading system version of libgtkmm-2.4.so.1.
LOG NOT INITIALIZED | Loading system version of libfontconfig.so.1.
LOG NOT INITIALIZED | Loading system version of libgthread-2.0.so.0.
LOG NOT INITIALIZED | Loading system version of libXcursor.so.1.
LOG NOT INITIALIZED | Loading system version of libpng12.so.0.
LOG NOT INITIALIZED | Loading system version of libcrypto.so.0.9.8.
LOG NOT INITIALIZED | Loading system version of libXrender.so.1.
LOG NOT INITIALIZED | Loading system version of libXdamage.so.1.
LOG NOT INITIALIZED | Loading system version of libart_lgpl_2.so.2.
LOG NOT INITIALIZED | Loading system version of libglib-2.0.so.0.
LOG NOT INITIALIZED | Loading system version of libpangoft2-1.0.so.0.
LOG NOT INITIALIZED | Loading system version of libglibmm-2.4.so.1.
LOG NOT INITIALIZED | Loading system version of libgdk-x11-2.0.so.0.
LOG NOT INITIALIZED | Loading system version of libpangox-1.0.so.0.
LOG NOT INITIALIZED | Loading system version of libpango-1.0.so.0.
LOG NOT INITIALIZED | Loading system version of libgobject-2.0.so.0.
LOG NOT INITIALIZED | Loading system version of libpangocairo-1.0.so.0.
LOG NOT INITIALIZED | Loading system version of libatkmm-1.6.so.1.
LOG NOT INITIALIZED | Loading system version of libcairo.so.2.
LOG NOT INITIALIZED | Loading system version of librsvg-2.so.2.
LOG NOT INITIALIZED | Loading system version of libgmodule-2.0.so.0.
LOG NOT INITIALIZED | Loading system version of libxml2.so.2.
LOG NOT INITIALIZED | Loading system version of libXinerama.so.1.
LOG NOT INITIALIZED | Loading system version of libfreetype.so.6.
LOG NOT INITIALIZED | Loading system version of libgcc_s.so.1.
LOG NOT INITIALIZED | Loading system version of libsigc-2.0.so.0.
LOG NOT INITIALIZED | Loading system version of libgio-2.0.so.0.
LOG NOT INITIALIZED | Loading system version of libatk-1.0.so.0.
LOG NOT INITIALIZED | Loading system version of libgiomm-2.4.so.1.
LOG NOT INITIALIZED | Loading system version of libXau.so.6.
LOG NOT INITIALIZED | Loading system version of libXft.so.2.
LOG NOT INITIALIZED | Loading system version of libgdk_pixbuf-2.0.so.0.
LOG NOT INITIALIZED | Loading system version of libXfixes.so.3.
LOG NOT INITIALIZED | Loading shipped version of libexpat.so.0.
LOG NOT INITIALIZED | Loading shipped version of libview.so.2.
LOG NOT INITIALIZED | Loading shipped version of libsexy.so.2.
LOG NOT INITIALIZED | Loading shipped version of libsexymm.so.2.
LOG NOT INITIALIZED | Loading shipped version of libcurl.so.4.
LOG NOT INITIALIZED | Loading shipped version of libvmwarebase.so.0.
LOG NOT INITIALIZED | Loading shipped version of libgvmomi.so.0.
LOG NOT INITIALIZED | Loading shipped version of libvmwareui.so.0.

---

### Post by flycojet on 2010-06-15
Please?

---

### Post by fjgaude on 2010-06-15
I can't say what is wrong here. I would suggest you uninstall whatever you have installed for Player and WS and then re-install only one of them. I have no experience with WS but Player 3.1 is totally solid with all versions of Ubuntu since about 9.04. Good luck!

---

### Post by flycojet on 2010-06-16
Dear Fjgaude,
I followed your advice. I downloaded and installed another version. Now this works well. Grateful for the  cooperation.

---

### Post by fjgaude on 2010-06-16
Very good, glad I could help!

---

