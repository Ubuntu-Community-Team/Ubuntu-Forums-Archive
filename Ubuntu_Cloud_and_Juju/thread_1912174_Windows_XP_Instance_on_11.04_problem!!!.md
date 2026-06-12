---
title: "Windows XP Instance on 11.04 problem!!!"
date: 2012-01-20
forum: Ubuntu Cloud and Juju
---

### Post by cloudsetup on 2012-01-20
Hi,

We have set up a cloud with one CC, one NC and one client, using UEC from **Ubuntu 11.04** . On the NC we installed KVM and created a** Windows XP Image.** The bundling and registering of the image went on smoothly. However, when we tried to run a instance of the image, we faced some problems. We used "SYSTEM" mode.

Firstly the instance is unable to get an ip from the enterprise DHCP. :( So, when we use private addressing, the instance is in "running" state and gets a ip address (172.19.1.2) but we are not able to **SSH or Ping or view it from a remote desktop.** 

When we connect from VNC it says[B]

"Windows could not start because of a computer disk hardware configuration problem. Could not read from the selected boot disk. Check boot path and disk hardware. Please check the windows documentation about hardware disk configuration[/B]"

A hack has been given for the /usr/share/gen_kvm_libvirt_xml file on the NC to correct this problem in Ubuntu 10.04 
[http://cssoss.wordpress.com/2010/05/05/uec-windows-instance-on-lucid-lynx-hack/#comment-504](http://cssoss.wordpress.com/2010/05/05/uec-windows-instance-on-lucid-lynx-hack/#comment-504)

But the /usr/share/gen_kvm_libvirt_xml file looks very different in 11.04, so we are not sure how to go about changing it in our case! Can anyone please help? Thanks! :)

---

