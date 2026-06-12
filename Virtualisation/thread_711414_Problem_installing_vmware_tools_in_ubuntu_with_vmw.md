---
title: "Problem installing vmware tools in ubuntu with vmware fusion under osx"
date: 2008-02-29
forum: Virtualisation
---

### Post by OCTOG3N on 2008-02-29
Hi, I have a 20" aluminum iMac and am using the vmware trial to test drive Ubuntu (I've played with it before on PCs) ubuntu is running great under vmware but in order to get better graphics and more interoperability between osx and ubuntu I wanted to install the vmware tools package. I've looked at several tutorials but when I select Virtual Machine, install vmware tools, the mounted cd is just full of text files with no packages to speak of. Can someone help me? I'm sure I installed ubuntu properly under vmware and it's working great.

[IMG]http://i71.photobucket.com/albums/i128/octolink_64/Ubuntuissue.png[/IMG]

---

### Post by fjgaude on 2008-02-29
I haven't had any experience with Fusion but if memory serves when I clicked on the Install Tools item in the VM menu the tools starting installing automatically. At least that is the way it was under VMware Server. But Fusion maybe different.

---

### Post by rwessman on 2008-03-01
I'm having the same problem as well. It looks like the perl script is being interpreted by the system as a directory. Weird.

                                          Rick

---

### Post by barrylawson on 2008-03-12
I was having the same issue initially.

I updated all software through Synaptic, rebooted, and then the VMWare Tools install went off without a hitch.

(MacBook Air [Leopard], VMWare Fusion 1.1.1, Ubuntu 7.10)

---

### Post by spacejunk on 2008-03-12
I had the same problem with the Windows version of VMware. For some reason, having the ISO still tired to the CD-ROM drive when I activated the VMware tools install screwed it up. I changed the drive back to one of my physical drives and attempted again; everything worked correctly the second time.

---

