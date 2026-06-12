---
title: "vmware or virtual box"
date: 2009-06-22
forum: Server Platforms
---

### Post by xkaliburx on 2009-06-22
Need to stage a new VM type server.  I will be using ubuntu 9 server edition.  I have used VMware in the past with some success, not sold on performance.  My laptop (running u9) I have virtualbox and very happy with performance, etc.

So the question is VirtualBox used out in the 'real world'?  Next, how easy to transfer machines.  I could get a 2 day head start as I can stage a virtualbox server on my laptop, then move the file(s) to an external. When the server is ready simply copy over and fire up (I am assuming I can do that), but never used virtualbox 'remotely', meaning start the admin here, server is at a co-lo, then howto get to console if need be, etc.

Thanks for any realtime feedback

---

### Post by anonmars on 2009-06-22
I've not used a console or server-based version of VirtualBox. Does it even exist? Also, are any of the free VMware products strictly console based? Or did you install a GUI in Ubuntu server?

If you don't want a GUI-based server KVM would probably be the best Ubuntu Server thing to try (assuming your hardware supports it: intel-vt or amd-v). If not, I've also had luck with Xen on some little servers I've setup.

---

### Post by windependence on 2009-06-22
You need to use the correct VMware product to get good performance. The best way to do this free is to use VMware ESXi. You don't need an underlying OS with that so it's lightning fast, and the footprint is only about 32MB. If you need help setting it up, just post here or PM me as the setup can be confusing.

-Tim

VMware Partner

---

### Post by LepeKaname on 2009-06-22
> If you need help setting it up, just post here or PM me as the setup can be confusing.

If you have time, it would be nice for Ubuntu community if you write a blog on how to setup it. Also it may help you in the future if you need to do it again.

---

### Post by windependence on 2009-06-22
Great idea! Let me see if I have time this weekend. I would love to help.

-Tim

---

### Post by xkaliburx on 2009-06-22
> The best way to do this free is to use VMware ESXi.

I did setup a box a while back, actually tried doing a VM convert of a physical machine to him but had problems.  Ignoring that, I remember (had to just check) as I still have one ESXi server running.  When I connect via infrastructure client I get a message about licensing and it is reverting and can't do consolidated backups.  I didn't read to much on it, as I had other things in progress.

So now that you rekindled that fire, I did think the ESXi was in fact free (you can't convert a working physical to vm w/o a license).  But with that, can you just fire up the manager, create a new server all still free?

If so I think I would agree and go that route.   Also will keep an eye for that how-to!

** Update ** 
Well I did create a new clean server, allocate all, copy over the .iso, mount it and when I tried to start got a license error.  Looking at the server/config tab, I see the license options says 'expired'.  I will now do some more reading to see in fact if you can have an ESXi server free, the same way you can download VM Server 2.

---

### Post by windependence on 2009-06-23
Although ESXi is free as in beer, it still requires a license key. When you do the product download, a license key is sent to you via e-mail unless you install the evaluation version

I have a feeling you installed ESXi or ESX evaluation version instead of ESXi free though. ESX is the paid version and does have a trial version that expires in 60 days. There is also an evaluation version of ESXi.

ESXi does not support consolidated backups, that is an ESX feature, but there are other ways to back up your VMs.

You can use the free VMware Converter tool to convert a physical machine to a VM.  You can download it here: [https://www.vmware.com/download/converter/](https://www.vmware.com/download/converter/)

Trust me, you can indeed have ESXi totally free (as in beer). After the install, you go to the IP address of your server to download the VIC (VMware Infrastructure Clent) that is used to manage your VMs. You cannot use VirtualCenter without a license which allows you to manage several servers centrally, but most of us don't mind logging into each of our ESXi servers to manage our VMs. If you have a 64 bit machine you should use version 4.0. Downloads are here: [https://www.vmware.com/download/](https://www.vmware.com/download/). You must register to get a free license key. Just create an account, it's easy.

I'll try to outline all this stuff in my How To. I have several of these in production for a while now.

-Tim

---

