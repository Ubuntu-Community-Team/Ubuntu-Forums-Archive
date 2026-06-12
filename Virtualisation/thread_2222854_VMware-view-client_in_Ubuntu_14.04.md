---
title: "VMware-view-client in Ubuntu 14.04"
date: 2014-05-08
forum: Virtualisation
---

### Post by vendethiel on 2014-05-08
[FONT=arial]Started a thread on [vmware forums]("https://communities.vmware.com/message/2378181#2378181") but thought i'd try my luck here as well:[/FONT]

[FONT=arial]Has anyone had any success getting the view client installed on a Ubuntu 14.04 x64 host? It's not in the canonical repo (it is in 12.04 x32)

I can get the client installed by doing the following:

*     dpkg --add-architecture i386*
*     apt-get update*
*     wget [http://archive.canonical.com/ubuntu/pool/partner/v/vmware-view-client/vmware-view-client_2.2.0-0ubuntu0.14.04_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/v/vmware-view-client/vmware-view-client_2.2.0-0ubuntu0.14.04_i386.deb) /opt*
*     wget [http://mirrors.kernel.org/ubuntu/pool/universe/o/openssl098/libssl0.9.8_0.9.8o-7ubuntu3.1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/o/openssl098/libssl0.9.8_0.9.8o-7ubuntu3.1_i386.deb) /opt*
*     (using gdebi [apt-get install gdebi]*
*     debi /opt//libssl0.9.8_0.9.8o-7ubuntu3.1_i386.deb*
*     gdebi /opt/vmware-view-client_2.2.0-0ubuntu0.14.04_i386.deb*

I can successfully connect using the client, however when I launch a VM I just get a blank console that eventually closes on its own. Error Log below:

May 08 09:45:19.738: vmware-view.bin 22581| Spawn of vmware-view-usb failed: Failed to execute child process "vmware-view-usb" (No such file or directory)
May 08 09:45:19.738: vmware-view.bin 22581| ViewUsblib: mmfw_RegisterClient: error opening connection: error 2 (No such file or directory)
May 08 09:45:19.738: vmware-view.bin 22581| ViewUsblib: ViewUsb_InitLib: cannot connect to vmware-view-usbd: mmfw_ret=1
May 08 09:45:19.738: vmware-view.bin 22581| CdkViewUsb_Init: ViewUsb_InitLib returned ViewUsbStatus_UsbdCommsFailure
May 08 09:45:19.738: vmware-view.bin 22581| CdkViewUsb_Init: (is vmware-view-usbd running?)
May 08 09:45:19.990: vmware-view.bin 22581| PCoIP Client(23151): CreateMKSInterface: forcing mount, Remote MKS already present
May 08 09:45:19.991: vmware-view.bin 22581| PCoIP Client(23151): OnMountUnmount: (0, 0) 1024 X 791.
May 08 09:46:23.152: vmware-view.bin 22581| PCoIP Client(23151): Remote MKS network connection status changed: DISCONNECTED
May 08 09:46:23.152: vmware-view.bin 22581| PCoIP Client(23151): OnMountUnmount: remote MKS not present!

Any thoughts?[/FONT]

---

### Post by vendethiel on 2014-06-03
This ended up being a networking issue. We were hitting an ACL on our firewall.

---

