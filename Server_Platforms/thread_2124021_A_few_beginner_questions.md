---
title: "A few beginner questions"
date: 2013-03-09
forum: Server Platforms
---

### Post by petarpetrovic on 2013-03-09
I'm not sure if this is the right forum to ask, since my question involves virtualization, but I'm talking about the Server edition anyway.

I am planning to get a dedicated server at the certain hosting company, and I am planning to run Ubuntu Server (most probably 12.04 version) on it. However, I would like to put one virtual machine (since the server will have 12 GB of RAM) for a mail server (probably Zimbra or Debian running Postfix + Dovecot, haven't decided yet). Now, I know nothing about virtualization on Linux, so I wanted to ask which virtualization route is best for me?

Also, I want to know whether I will need 2 IPv4 addresses or just one, since I'm going to have Ubuntu Server and a virtual machine inside it? Is there a way for a virtual machine to be accessible from the same IP as the dedicated OS? I need a VM only for Zimbra, everything else (nginx, MySQL, etc.) will run on a dedicated OS.

Can someone point me to some tutorials or web sites where I can get more info on this particular situation? I have modest experience with Linux administration, but only on a VPS, this is the first time that I'm getting a dedicated server, so I suppose that some things are different, especially when it comes to virtualization.

Thank you in advance for your help.

---

### Post by cariboo on 2013-03-10
I've been playing with running a virtual server on top of the sever install, and virtual box worked quite well for me. I used the virtual appliances from [Turnkey Linux]("http://www.turnkeylinux.org/") in my experimentation.

---

### Post by prodigy_ on 2013-03-10
You don't always need visualization to run Linux (even if it's a different distro) upon Linux. In some cases [chroot](http://maketecheasier.com/how-to-run-multiple-linux-distros-without-virtualization/2009/08/11) is enough.

---

### Post by cheshire mouse on 2013-03-10
Here is a manual for ubuntu [https://help.ubuntu.com/12.04/serverguide/virtualization.html](https://help.ubuntu.com/12.04/serverguide/virtualization.html)
  But i think, you should first read about so called "bare metal" hypervisors, like Xen or ESXi. And choose your OS only after you decide what hypervisor suits best your needs

---

### Post by thnewguy on 2013-03-10
My initial thought is that it might be better for you to get two low-end virtual private servers, rather than one high-end one which would in turn run a virtual server. Having two low-end VPS would probably be less expensive and would make configuring the network easier.

---

### Post by lykwydchykyn on 2013-03-10
You need to take a look at ProxMox VE.  It's a hypervisor OS based on Debian, KVM, and OpenVZ that lets you do both traditional VM's and container-based Linux VM's.  It runs a web interface that looks almost exactly like the old VMWare client (we use an old version of ESX at work, looks just like VIC).

I've been playing with it on a server at work, it's pretty slick.  There was a recent Linux Action Show where they talked about ProxMox and interviewed some sysadmins who are using it to run all their company's VM's.  

It's got a rough edge here and there, but overall it's pretty impressive considering it's free (you can buy support from the company if you want it).

EDIT: Ok, after re-reading your post proxmox may not be the right thing for you.  But I think you might want to look into OpenVZ and just use containers rather than a VM.

---

