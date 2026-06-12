---
title: "rkhunter scan results"
date: 2015-09-21
forum: Security
---

### Post by ethernetfast on 2015-09-21
Hi guys,
Im new to Ubuntu and im looking for some help.
I've scanned my Ubuntu with rkhunter and I have some concerning results:
   Warning: **The following processes are using deleted files**:
          Process: /sbin/init    PID: 1    File: /var/log/upstart/systemd-logind.log.1
          Process: /usr/sbin/cups-browsed    PID: 1168    File: /etc/passwd
          Process: /sbin/init    PID: 2170    File: /home/pwn20wn/.cache/upstart/indicator-bluetooth.log.1
          Process: /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon    PID: 2400    File: /home/pwn20wn/.local/share/gvfs-metadata/root
          Process: /usr/lib/firefox/firefox    PID: 2703    File: /var/tmp/etilqs_F4ZmiXL3Bx5CrjT
          Process: /usr/bin/unity-scope-loader    PID: 2959    File: /home/pwn20wn/.cache/software-center/software-center-agent.db/record.DB
 **Warning**: Process '/sbin/wpa_supplicant' (PID 1167) is listening on the network.
 **Warning**: Process '/sbin/dhclient' (PID 1349) is listening on the network.
 **Warning**: Suspicious file types found in /dev:
          /dev/.udev/rules.d/root.rules: ASCII text
 **Warning**: Hidden directory found: /etc/.java: directory  
 **Warning**: Hidden directory found: /dev/.udev: directory  

 **Warning**: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs' 

 **Warning**: Application 'openssl', version '1.0.1f', is out of date, and possibly a security risk.
I would like to know if these are false positives or real threats abd how to fix them.
Thank you very much!

---

### Post by Habitual on 2015-09-21
read /etc/rkhunter.conf

---

