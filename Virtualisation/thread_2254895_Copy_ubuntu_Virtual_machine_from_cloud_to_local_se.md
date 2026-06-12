---
title: "Copy ubuntu Virtual machine from cloud to local server"
date: 2014-11-30
forum: Virtualisation
---

### Post by lambayd on 2014-11-30
I have a production server that is currently hosted on Linode.com cloud server. I would like to download an exact copy to my local server which will act as a development server. Any advice on the process will be much appreciated.

---

### Post by newbie-user on 2014-12-01
Is it possible to export/backup the VM from Linode and download it as an .ova or .ovf file? If so, you can then import the file to a hypervisor.

---

### Post by coldraven on 2014-12-01
Why not find out what version of OS, PHP, Apache etc. they are using and just replicate it?

---

### Post by carlwsnyder on 2014-12-01
I understand that you want to replicate all of the settings as well as the software from your production server.
According to the Internet, Linode uses the Xen hypervisor for their virtual machines (VMs).  As Xen is available for Ubuntu, all you need to do is to backup your VM, even in native format, and fire it up from Xen as a VM.
If you are attempting to convert from Xen VM to a physical machine, that may be more complicated.

---

### Post by lambayd on 2014-12-01
I can download the entire image as .img format. Currently, my local server is running Wiindows 2012,  can I install ubuntu within Microsoft Hyper-v and somehow mount the downloaded image from Linode?

---

### Post by carlwsnyder on 2014-12-01
This MIGHT work, but Xen wants to run on bare-metal for its DOM0 device.  Not sure if it will even work as a virtual device in another virtual environment, and not sure how well Hyper-V would work mounting a Xen image.

---

### Post by SeijiSensei on 2014-12-02
I've looked from time to time to see if I could export my Linode VMs, but I don't believe it is possible. Open a ticket at Linode, and ask the question there.  I'll be curious to hear the answer.

I use Linode's own backup service to take daily snapshots of my VMs, but I don't see any way to ship a snapshot to my office.

---

### Post by TheFu on 2014-12-04
> **lambayd said:**
> I can download the entire image as .img format. Currently, my local server is running Wiindows 2012,  can I install ubuntu within Microsoft Hyper-v and somehow mount the downloaded image from Linode?

Mixing VM-hypervisors isn't a good idea, if it is even possible.
For a Linux VM, having an image backup really isn't necessary and will waste 4G of download data for the OS that you can freshly install using a minimal install into the hypervisor of your choice (within reason).

Here's how I migrate entire VMs: [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview)
This works for backups, VMs, and/or physical Linux systems and doesn't leave you with a sorta-working VM in the end or any unsolvable performance issues due to different hypervisors providing different virtual hardware.

BTW, if you plan to virtualize more Linux VMs, using a Linux hostOS really does make 100x more sense than running Windows.

---

