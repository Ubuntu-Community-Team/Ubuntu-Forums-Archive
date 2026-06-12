---
title: "KVM - No login Prompt"
date: 2017-10-04
forum: Virtualisation
---

### Post by SuprScotte on 2017-10-04
Hello,

I am having an issue with Ubuntu 16.04, and KVM's noVNC console.   I am not getting a login prompt, and it was working prior to doing updates.   I have tried adding the following to the grub boot prompt, and been have no luck on getting a prompt within the noVNC console.  The VM's are utilizing Proxmox, but this issue is isolated to the recent updates on Ubuntu 16.04.  I have attached an image of were the startup gets stuck.

relay1:~ $ uname -r
4.4.0-96-generic

GRUB_CMDLINE_LINUX_DEFAULT="text" or GRUB_CMDLINE_LINUX_DEFAULT="nomodeset" or GRUB_CMDLINE_LINUX_DEFAULT="console=ttys0".

root@lax-edge1-ice-relay1:~ $ systemctl status systemd-logind
&#9679; systemd-logind.service - Login Service
   Loaded: loaded (/lib/systemd/system/systemd-logind.service; static; vendor preset: enabled)
   Active: active (running) since Wed 2017-10-04 19:45:45 UTC; 5min ago
     Docs: man:systemd-logind.service(8)
           man:logind.conf(5)
           [http://www.freedesktop.org/wiki/Software/systemd/logind](http://www.freedesktop.org/wiki/Software/systemd/logind)
           [http://www.freedesktop.org/wiki/Software/systemd/multiseat](http://www.freedesktop.org/wiki/Software/systemd/multiseat)
 Main PID: 931 (systemd-logind)
   Status: "Processing requests..."
    Tasks: 1
   Memory: 940.0K
      CPU: 30ms
   CGroup: /system.slice/systemd-logind.service
           &#9492;&#9472;931 /lib/systemd/systemd-logind

Oct 04 19:45:43 relay1 systemd[1]: Starting Login Service...
Oct 04 19:45:45 -relay1 systemd-logind[931]: New seat seat0.
Oct 04 19:45:45 lax-edge1-ice-relay1 systemd-logind[931]: Watching system buttons on /dev/input/event0 (Power Button)
Oct 04 19:45:45 lax-edge1-ice-relay1 systemd[1]: Started Login Service.
Oct 04 19:45:49 lax-edge1-ice-relay1 systemd-logind[931]: New session c1 of user newrelic.
Oct 04 19:46:13 lax-edge1-ice-relay1 systemd-logind[931]: New session 1 of user root.
Oct 04 19:46:13 lax-edge1-ice-relay1 systemd-logind[931]: New session 2 of user root

relay1:~ $ systemctl --failed
0 loaded units listed. Pass --all to see loaded but inactive units, too.
To show all installed unit files use 'systemctl list-unit-files'

relay1:~ $ systemctl --full list-units | egrep -i "console"
systemd-ask-password-console.path                                                         loaded active     waiting         Dispatch Password Requests to Console Directory Watch
console-setup.service                                                                     loaded active     exited          Set console font and keymap
keyboard-setup.service                                                                    loaded active     exited          Set console keymap

---

### Post by howefield on 2017-10-04
Thread moved to the "*Virtualisation*" forum.

---

### Post by SuprScotte on 2017-10-10
*BUMP*

I've posted this thread over on Proxmox's forums, and they believe it's more related too Ubuntu.   Anyone experience this type of issue, or have any recommend tips I could follow?

---

