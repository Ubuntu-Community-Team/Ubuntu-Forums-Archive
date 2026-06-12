---
title: "Virt-Manager Prompting for Password"
date: 2015-06-30
forum: Virtualisation
---

### Post by richb2 on 2015-06-30
Hi Ubuntu Folks,

I have a little quandry here and I was wondering if you guys can provide some input on this. I'm install Virtualization on Ubuntu 15.04 server following this guide: [http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/)

However, When I launch a console for the guest, the console window keeps prompting me for my password and it never shows anything in the window (black screen). When I close it it continues to ask me for my password. I'm not sure if I messed up the configuration somewhere where it's causing this issue.

Anyone have an idea to cure my madness?? 

TIA

---

### Post by deadflowr on 2015-06-30
Assuming you added your user to the libvirtd group (the adduser command)
did you logout and log back in?

---

### Post by richb2 on 2015-06-30
Yup, I need so I login to the host with Virt-Manager and hit open to open the console and it has "Enter password for xyz" I did that and it keeps prompting me until I kill the process

---

### Post by TheFu on 2015-06-30
When you connect to the console, you are expected to login.  If you want automatic logins, use ssh with keys, but console access will always require userid/password.

Or I'm I completely missing where the userid/password prompt is coming from?

---

### Post by richb2 on 2015-07-02
When I launch the guest console from VM Manager. It keeps prompting for the password over and over. However, when I switch the display to VNC from spice, it works just fine. Strange.

---

### Post by TheFu on 2015-07-02
Are there ssh leys setup or do you always use a userid/password for credentials?
Also, is virt-manager running on the same machine as the VMs or over the network? 

I've only run a GUI on the KVM host once or twice - usually I connect over the network using ssh connectivity built-into virt-manager (really libvirt).

---

