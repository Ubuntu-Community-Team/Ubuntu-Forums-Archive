---
title: "createing a Virutal machine from web?"
date: 2021-02-07
forum: Virtualisation
---

### Post by josephchrzempiec on 2021-02-07
Hello is it possible to create like vm like hosting companies do from a web interface? 


Joseph

---

### Post by TheFu on 2021-02-07
yes.  Almost anything is possible with sufficient skill and time.

---

### Post by josephchrzempiec on 2021-02-07
Time i have, Skills I'm somewhat lacking. I love to learn as much as i can but where to start or figure out to end is always been my problem. 
I'm looking at something now for virtualbox. Also thank you for the reply back.


Joseph

---

### Post by TheFu on 2021-02-07
So, there are lots of choices, but really a web interface is a huge security liability.  For VM management on Linux, the best, most security, solution is virt-manager using libvirt. It is pretty bone-head proof and all commands are via ssh tunnels. Also, if you launch a desktop, that screen will be over an ssh tunnel which is generally considered secure enough for use over the internet.  Basically, virt-manager provides an interface like virtualbox, but the client side can be anywhere with ssh access into the VM host.  

I consider virtualbox a toy.  For desktop on desktop virtualization, I suppose it is fine.  The performance for server workloads isn't great. 

If you don't know ssh, learn that before doing anything else.  Setup key-based authentication between your client and all servers. That's about 30 seconds for each connection and just a few commands.  ssh-keygen, ssh-copy-id ... and Bob's your uncle.  Security connectivity from anywhere in the world. About 50 commonly used tools use ssh-based protocols.  ssh, scp, sftp, rsync, most Unix backup tools, sshfs, any NX-based remote desktop, and the list goes on.  You can use ssh tunnels as an easy VPN for web browsing too.  LEARN SSH.

If you can dedicate the entire system to VMs, then you can use **proxmox**, but that isn't Ubuntu for the hostOS. No desktop, just a web interface.

In general, web interfaces for systems management simply provides too many attack vectors for noobs to configure securely ... and there are better solutions.  Heck, any web based management interface should only work from the localhost anyways ... accessed after an ssh tunnel connection is made.

I get most of this is probably too nerdy for your current level. In short, avoid web interfaces whenever possible. Don't use phpMyAdmin, mysqladmin, webmin.  When you run servers on the internet, you'll see nearly constant attacks against each of those tools, daily, every second.

For running VMs, just install KVM, bridge-utils, virt-manager.  Virt-manager can be run either local or remote. There are plenty of how-to videos on youtube for this. You'll thank me.

Or, there is oVirt from Redhat if you prefer. But the hostOS will need to be running RHEL/CentOS and the machine will need to be beefier do to all the overhead that oVirt requires. In corporate environments, they seem to love oVirt. It is pretty slick to use, but I understand setting it up is non-trivial.

In the end, only you can decide if this stuff is useful or not. I wish you success and security.

---

### Post by josephchrzempiec on 2021-02-08
Hello TheFu Thank you for the reply back. I did in the past used proxmox. I actually forgot all about it. I will look back at it once again. I remember proxmox did everything i need. We use to use that at my old work.  thank you


Joseph

---

