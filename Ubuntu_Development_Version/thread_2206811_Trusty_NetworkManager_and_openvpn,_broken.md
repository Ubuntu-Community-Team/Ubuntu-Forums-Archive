---
title: "Trusty: NetworkManager and openvpn, broken?"
date: 2014-02-20
forum: Ubuntu Development Version
---

### Post by zonum on 2014-02-20
Hello all, 

After I update'd/upgrade'd/dist-upgrade'd this morning (2/20/2014), my openvpn connections broke.  I use TorGuard, and have been using it for over a year without issues, with the last time I used it was this past weekend.

However, I now get:

$ nmcli con up uuid <log string of hex charcters>
Error: Connection activation failed: the VPN service stopped unexpectedly.

I aslo get the same error when I use the nm-applet on the task/status bar.  I am running Unity, not Gnome.

This is on current Trusty 14.04.

I have another system where I have not done the "apt-get update/upgrade/dist-upgrade" thus far, and it continues to work (openvpn).  I see the following differences (maybe there are more):

Both systems have this same version of network-manager:

ii  network-manager                                       0.9.8.8-0ubuntu1                            amd64        network management framework (daemon and userspace tools)

Working system:
ii  libnm-gtk-common                                 0.9.8.4-1ubuntu2                            all              network management framework (common files for wifi and mobile)
ii  libnm-gtk0                                            0.9.8.4-1ubuntu2                            amd64        network management framework (GNOME dialogs for wifi and mobile)
ii  network-manager-gnome                        0.9.8.4-1ubuntu2                            amd64        network management framework (GNOME frontend)

Not working system:

ii  libnm-gtk-common                                 0.9.8.4-1ubuntu3                            all              network management framework (common files for wifi and mobile)
ii  libnm-gtk0                                            0.9.8.4-1ubuntu3                            amd64        network management framework (GNOME dialogs for wifi and mobile)
ii  network-manager-gnome                        0.9.8.4-1ubuntu3                            amd64        network management framework (GNOME frontend)

Any of you have similar issues?

Thanks,
zonum

---

### Post by zonum on 2014-02-20
All,

OK, I can now confirm that the above issue is a NetworkManager issue as I have been able to manually use openvpn as follows, and thus bypassing NetworkManager:

For example,
sudo openvpn --client --config ~/vpn/config/vpn.ovpn --ca ~/vpn/config/vpn.ca.crt

The above works without any issues, and although not optimal, I can connect via openvpn (using my TorGuard service).  I do have to enter my TorGuard credentials everytime I invoke the above command, but it does work.

Thoughts?!

zonum

---

### Post by sammiev on 2014-02-20
> **zonum said:**
> All,

OK, I can now confirm that the above issue is a NetworkManager issue as I have been able to manually use openvpn as follows, and thus bypassing NetworkManager:

For example,
sudo openvpn --client --config ~/vpn/config/vpn.ovpn --ca ~/vpn/config/vpn.ca.crt

The above works without any issues, and although not optimal, I can connect via openvpn (using my TorGuard service).  I do have to enter my TorGuard credentials everytime I invoke the above command, but it does work.

Thoughts?!

zonum

I do not use TorGuard but I do use openvpn daily. I use Xubuntu 14.04 and Gnome 14.04 (Gnome 14.04 since day one) and I never had any issues to date.

---

### Post by zonum on 2014-02-20
sammiev.

I never had any issues with NetworkManager and openvpn using TorGuard's VPN service until today.  As stated, my other system that I have yet to update with "today's" updates, work using the NetworkManager, openvpn and TorGuard.  And, as you can see above, I can exclude the NetworkManager all together and run the openvpn command I show above, which is using the same TorGuard *ovpn/*crt files that NetworkManager uses, and it works.

Thanks for the feedback.

zonum

---

