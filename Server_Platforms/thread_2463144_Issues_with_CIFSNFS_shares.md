---
title: "Issues with CIFS/NFS shares"
date: 2021-06-04
forum: Server Platforms
---

### Post by xopher8713 on 2021-06-04
Hello all

I am having some issues with CIFS/NFS shares. Currently I am running Ubuntu Server 20.04 LTS on a VM, ESXI is the hypervisor, The network connection is a 10GB link between the ESXI server and a separate TureNAS server, The 10GB connection is then ran through a Distributed Virtual Switch inside of ESXI. Checking speeds of the connection indicate that I am getting the full 10GB speed between TrueNAS and Ubuntu. I then have a mount point setup to mount on boot and have tried both CIFS and after running into issues there I tried NFS and get the same issues. Plex is running on Ubuntu and when I am streaming small files I do not run into any issues but when I stream video files that are 25GB+ I get stuttering in the video, or it will skip parts of the video, or the video will not play at all. I am posting here because I have deployed a Windows 10 VM and a OpenSUSE VM testing a similar setup and I do not run into issues on those. Any thoughts or suggestions would be appreciated. All of my Google results point to only how to setup CIFS or NFS but not issues with them.

Thanks

---

### Post by TheFu on 2021-06-04
Best to split this up into 3 questions.
CIFS
NFS
ESXi network setup.

The expertise for each of those probably aren't something anyone here would have.  I've used all of those, but not with ESXi and I haven't touched anything from VMware since around 2011 when they forced us to leave by increasing license costs.

At first guess, I'd suggest checking the network settings.  For Ubuntu, if I need a bridge with a 10Gbps physical card, I'd use openvswitch, not the standard bridge-utils.

I don't have any 25G videos either. I've not seen stuttering with NFS, but I have with CIFS.  Most of the time, the stuttering was due to a client player issue, not on the server.

Those are all the ideas I have.  Maybe drawing a detailed diagram and labeling it with what you intend, then checking that against what is actually configured would be helpful?  The process of trying to explain it to someone else, in extreme detail, will usually shine a light on the issue.

I'm assuming you are using virtio drivers for both storage and networking, yes?

---

