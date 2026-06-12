---
title: "problem in Vmware Tools Configuration"
date: 2008-12-17
forum: Virtualisation
---

### Post by sai438 on 2008-12-17
[FONT="Arial"]Hi,

      After installing VMware Tools in Ubuntu server 8.10 for VMware server 1.0.8, i'm unable to configure it. It is throwing me errors in VMHgfs module and vmxnet compilation. can any one suggest me a solution?

Regards,
sairam[/FONT]

---

### Post by sai438 on 2008-12-17
I'm running it on a P4 3GHz PC with 1 GB ram and assigned 512 MB RAM for the VM. its fast but i wanted to have vmxnet support for it and i'm having problem in compiling it.

--
sairam

---

### Post by Dedoimedo on 2008-12-17
Hi there,

You will need the compilation tools before you can install VMware Tools. This means, install build-essential package in the guest machine. Then try installing the tools again.

P.S. You need the build-essential package (make, gcc, kernel source, and kernel headers) also when installing VMware Server on the host, but I guess you've got this covered.

Dedoimedo

---

### Post by hongri1998 on 2008-12-17
**[ball valve](http://www.valvesupplier.net/petro-valve.htm)** featuring with uni-body, top entry trunnion mounted ball. This type of valves gives convenient of in-line repair or replace valve internal components without dismantling it from pipeline. series [ball valve]("http://www.valvesupplier.net/petro-valve.htm") is all fire safe designed comply with API 607 & API 6FA.

---

