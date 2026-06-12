---
title: "Attach / detach problem for passthrough/SR-IOV in libvirt"
date: 2014-03-27
forum: Virtualisation
---

### Post by mohsen-ghaemi-8 on 2014-03-27
[FONT=Arial][B]Hi all

[/B][/FONT]
[FONT=Arial]I just encountered a problem in libvirt while was trying to attach and detach a sr-iov vf to my VM[/FONT]

[FONT=Arial][/FONT][FONT=Arial]The version of my libvirt is 1.1.1-0ubuntu8.5 [/FONT]

[FONT=Arial][/FONT][FONT=Arial]I tried to attach the device using following xml[/FONT]

[FONT=Arial][/FONT][FONT=Arial]***<interface type='hostdev' managed='yes'>***[/FONT]
[FONT=Arial]***    <mac address='5c:01:fd:12:34:58'/>***[/FONT]
[FONT=Arial]***    <source>***[/FONT]
[FONT=Arial]***        <address type='pci' domain='0x0000' bus='0x04' slot='0x01' function='0x1'/>***[/FONT]
[FONT=Arial]***    </source>***[/FONT]
[FONT=Arial]***</interface>***[/FONT]

[FONT=Arial][/FONT][FONT=Arial]When i attached device it worked properly and i managed to ping another host.[/FONT]

[FONT=Arial][/FONT][FONT=Arial]**virsh # attach-device t5 1.xml**[/FONT]
[FONT=Arial]**Device attached successfully**[/FONT]

[FONT=Arial][/FONT][FONT=Arial] But when i detached it still i had network traffic in my VM but libvirt (virsh) said that [/FONT]

[FONT=Arial][/FONT][FONT=Arial]***virsh # detach-device t5 1.xml***[/FONT]
[FONT=Arial]***Device detached successfully***[/FONT]

[FONT=Arial]******[/FONT][FONT=Arial]The next time i tried to attach it libvirt said that [/FONT]

[FONT=Arial][/FONT][FONT=Arial]***virsh # attach-device t5 1.xml***[/FONT]
[FONT=Arial]***error: Failed to attach device from 1.xml***[/FONT]
[FONT=Arial]***error: Requested operation is not valid: PCI device 0000:04:01.1 is in use by domain t5***[/FONT]

[FONT=Arial][/FONT][FONT=Arial]I tried it with different VMs and different guest OSs that the same happend.[/FONT]

[FONT=Arial][/FONT][FONT=Arial]The same action was done with another host running libvirt version [/FONT]

[FONT=Ubuntu]******[/FONT][FONT=Ubuntu]***Installed: 1.0.2-0ubuntu11.13.04.5~cloud1***[/FONT]
[FONT=Ubuntu]*** Candidate: 1.0.2-0ubuntu11.13.04.5~cloud1***[/FONT][FONT=Arial]******[/FONT]

[FONT=Arial][/FONT][FONT=Arial] and it worked pretty OK. No problem. [/FONT]

[FONT=Arial][/FONT][FONT=Arial]Do you have any idea what is wrong?[/FONT]

[FONT=Arial][/FONT][FONT=Arial]More information:[/FONT]
[FONT=Arial]***Kernel : 3.8.0-37-generic ***[/FONT]

[FONT=Arial]******[/FONT][FONT=Arial]*** /etc/libvirt/qemu.conf :  security_driver = "none”***[/FONT]

[FONT=Arial]******[/FONT][FONT=Arial]***root@compute01:~# ethtool -i eth5***[/FONT]
[FONT=Arial]***driver: bnx2x***[/FONT]
[FONT=Arial]***version: 1.78.58***[/FONT]
[FONT=Arial]***firmware-version: bc 7.4.22 phy 1.34***[/FONT]
[FONT=Arial]***bus-info: 0000:04:00.1***[/FONT]
[FONT=Arial]***supports-statistics: yes***[/FONT]
[FONT=Arial]***supports-test: yes***[/FONT]
[FONT=Arial]***supports-eeprom-access: yes***[/FONT]
[FONT=Arial]***supports-register-dump: yes***[/FONT]

[FONT=Arial]******[/FONT]
[FONT=Arial]******[/FONT]
[FONT=Arial]******[/FONT]

---

### Post by mohsen-ghaemi-8 on 2014-03-28
Just solved by downgrading libvirt from 1.1.1 to 1.0.2 and it works perfect now !!

---

