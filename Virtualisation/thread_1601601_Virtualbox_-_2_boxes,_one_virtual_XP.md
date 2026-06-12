---
title: "Virtualbox - 2 boxes, one virtual XP"
date: 2010-10-20
forum: Virtualisation
---

### Post by sydbat on 2010-10-20
I tried a search of the forum and via Google, but could find nothing. Maybe my search terms sucked.

Anyway, I am wondering if I install Virtualbox on 2 Ubuntu 10.04 boxen, if I could access one a single XP instance. 

To clarify (if that is possible), can I set up a virtual XP on one box, then access it as well from another box?

Thanks for your help.

---

### Post by HermanAB on 2010-10-20
Yes, if you access it over a network such as NFS.

A virtual machine is just a bunch of files in a directory.  You can copy it, save it to a DVD, make a tar ball of it, put copies of it on multiple machines, etc.  I have a zoo of pre-installed VM systems that I can deploy in minutes.

---

### Post by sikander3786 on 2010-10-20
> then access it as well from another box?

Couldn't get the actual meaning of that statement. If it means remote desktop access, you can also use VNC for instance.

---

### Post by sydbat on 2010-10-20
> **HermanAB said:**
> Yes, if you access it over a network such as NFS.

A virtual machine is just a bunch of files in a directory.  You can copy it, save it to a DVD, make a tar ball of it, put copies of it on multiple machines, etc.  I have a zoo of pre-installed VM systems that I can deploy in minutes.Thanks. Kinda thought that.

> **sikander3786 said:**
> Couldn't get the actual meaning of that statement. If it means remote desktop access, you can also use VNC for instance.I knew I wasn't being clear...friggin head cold...

What I meant was - I install Virtualbox on 2 computers, Box A and Box B. XP is loaded onto Box A via Virtualbox. Can I then load that same XP Virtualbox image/folder/what-have-you on Comp B? Or would that screw things up?

---

### Post by JKyleOKC on 2010-10-22
I'm doing exactly what you asked about. I run XP as a guest on one machine on my LAN, and access it from any and all of the others -- but only one box can access it at any given time.

The trick, for me at least, was to install the "vboxtool" package to launch the guest machine in "headless" mode, and then use "vrdp" from all of the other machines to access it. I even use vrdp on the actual host machine, since the usual vbox access method isn't available when running headless.

The vbox packages include the necessary vrdp program; while I do have vbox installed on all my boxes, it's not necessary to have it on any but the actual host. 

Using this approach is better, from a security standpoint, than using VNC since the vrdp protocol isn't so open to the net. I also have its port blocked from my WAN interface so that it's only available within my LAN.

You'll have to google for "vboxtool" since it's not in the repositories; I found it via the vbox web site's forums...

---

### Post by sydbat on 2010-10-22
> **JKyleOKC said:**
> I'm doing exactly what you asked about. I run XP as a guest on one machine on my LAN, and access it from any and all of the others -- but only one box can access it at any given time.

The trick, for me at least, was to install the "vboxtool" package to launch the guest machine in "headless" mode, and then use "vrdp" from all of the other machines to access it. I even use vrdp on the actual host machine, since the usual vbox access method isn't available when running headless.

The vbox packages include the necessary vrdp program; while I do have vbox installed on all my boxes, it's not necessary to have it on any but the actual host. 

Using this approach is better, from a security standpoint, than using VNC since the vrdp protocol isn't so open to the net. I also have its port blocked from my WAN interface so that it's only available within my LAN.

You'll have to google for "vboxtool" since it's not in the repositories; I found it via the vbox web site's forums...Cool. I'll look into this. Thanks.

---

### Post by JustinR on 2010-10-22
> **sydbat said:**
> Thanks. Kinda thought that.

I knew I wasn't being clear...friggin head cold...

What I meant was - I install Virtualbox on 2 computers, Box A and Box B. XP is loaded onto Box A via Virtualbox. Can I then load that same XP Virtualbox image/folder/what-have-you on Comp B? Or would that screw things up?

Hi,

[http://download.virtualbox.org/virtualbox/UserManual.pdf](http://download.virtualbox.org/virtualbox/UserManual.pdf)

Page 93.

> 
**_7.2 Teleporting_**

Starting with version 3.1, VirtualBox supports &#8220;teleporting&#8221; &#8211; that is, moving a virtual machine
over a network from one VirtualBox host to another, while the virtual machine is running. This
works regardless of the host operating system that is running on the hosts: you can teleport
virtual machines between Solaris and Mac hosts, for example.


---

