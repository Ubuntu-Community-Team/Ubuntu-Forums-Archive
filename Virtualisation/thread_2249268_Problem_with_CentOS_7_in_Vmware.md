---
title: "Problem with CentOS 7 in Vmware"
date: 2014-10-20
forum: Virtualisation
---

### Post by sports fan Matt on 2014-10-20
I just got VMware from a friend over the weekend, but I seem to have run into this issue. I know it's a different system (YUM) but this message appears.  I know the fix is to remove .config/monitors.xml, but how can I achieve this if I can't get to a terminal to apply the required commands? And how would you in a terminal remove it?

---

### Post by TheFu on 2014-10-21
a) Which VMware?  They make 6+ virtualization programs.  VMware is the company name, not the program name.
b) Thanks for the image, but I don't know what it could be from.  You could connect a liveCD to the VM and have the hypervisor to boot off that, then modify files.  This is not a noob-friendly method.  
c) if you are positive of the fix, you can change to a different console using the alt-F1 thru alt-F8 keys, login, and remove the file. I've never heard of that file, but I've only been doing this 20+ yrs, so I could be mistaken. Perhaps just renaming the file would be safer? Use the **mv** command for that. 

Perhaps you would be better off creating a new VM with settings you decide, then connecting the installation media (iso file) to the VM, booting and performing the installation yourself? That way, the installed OS will configure itself for the specific VM settings you've provided.  Lots of youtube videos for how to do this based on the VMware hypervisor you are using (whatever that may be).  This stuff should work fine for Player or Workstation hypervisors - for ESX, and ESXi you'll probably need to run vsphere to get console access. It depends on which release.

---

### Post by sports fan Matt on 2014-10-21
The Fu,

1.  VMware workstation.
2. I figured that, as I need to just keep up to date because I may be starting to work with more clients and deal with more networks that run Linux servers etc
3.  I actually did what you suggested last night and destroyed and reinstalled, but still curious why the error

Do you think I made a good investment in time by setting these all up in VMware? I currently have Windows 7 (main/host), Windows 10 tech (120 GB), centOS 7 (120 GB) and Ubuntu 14.04 (120 GB) all on the same machine

---

### Post by TheFu on 2014-10-21
> **sports fan Matt said:**
> The Fu,

1.  VMware workstation.
Good if you aren't paying for it. Just not as good for servers as Linux-based tools like KVM, Xen, IMHO. Having Windows as the hostOS is extremely limiting.

> **sports fan Matt said:**
> 2. I figured that, as I need to just keep up to date because I may be starting to work with more clients and deal with more networks that run Linux servers etc Sorry - don't see the connection between using a Linux ISO to troubleshoot an install and keeping upto date. It will take awhile to get used to the idea there isn't any limit to the number of installs, media, uses, for Linux. We ain't got no license keys to worry about. Booting off an ISO is a common troubleshooting technique. Learn it, know it, love it. ;)

> **sports fan Matt said:**
> 3.  I actually did what you suggested last night and destroyed and reinstalled, but still curious why the error I've never seen that error - perhaps trying to connect the OS installed elsewhere for different hardware to new hardware isn't always a good idea - especially if GPU drivers have been loaded that aren't compatible with the new environment?

> **sports fan Matt said:**
> Do you think I made a good investment in time by setting these all up in VMware? I currently have Windows 7 (main/host), Windows 10 tech (120 GB), centOS 7 (120 GB) and Ubuntu 14.04 (120 GB) all on the same machine

I think you are wasting too much storage.  Windows7 needs 60G.  Linux installs rarely need more than 20G.  Keep large files on the network, **not** inside a VM.  Also, if you don't run more than 1 VM at a time, you can share the swap partition.  My main desktop is a VM running in a private cloud. It is ... 
```
$ df
Filesystem                                                 Size  Used Avail Use% Mounted on
/dev/vda1                                                   14G   12G  1.5G  89% /

```
15G in size. Been using this for web-app server development for about 4 yrs.  This ain't Windows. Leave the bloat expectations elsewhere. My blog article on virtual machine performance might be helpful for you to review too. It is posted here all over the place.

I am NOT a fan of VMware corporate. They've make some extremely harmful decisions to my company and clients in the past.  Fool me once ... type stuff.  I never plan to use anything from them again - NEVER. It was caused by greed - pure greed.  Everyone needs to learn lessons like that on their own and I hope you don't get burned where it costs any money like we did. BTW - almost 2x the previous costs for our clients. Within 6 months, we'd migrated them all to KVM. The clients are much happier now.  

With that said, VMware Workstation is an impressive tool, but most people here will be using VirtualBox and many of those people will run it on a Linux hostOS.  I wouldn't change if I were you, just know that support questions will get fewer, useful, answers here. The best place for support of commercial software tends to be the support forums run by that company you paid.

---

