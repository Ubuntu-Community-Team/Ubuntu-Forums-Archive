---
title: "Anybody use any good Web based KVM Managers?"
date: 2015-07-08
forum: Virtualisation
---

### Post by npinn001 on 2015-07-08
Hi all,

Have a bit of a dilemma I want to try solve. I'd like to manage the remote server without needing a linux box to do it, as I mainly use a chromebook at home - so Chrome browser is my option.

I tried Proxmox, dont like it though as its a testing repo. 

I've seen a few others, Webvirtmgr but that is a pain to install and get running.

Kimchi wouldnt work properly on the VNC side either.

Considering making the leap from Ubuntu to CentOS for OVirt which looks like a good bet. Before I do, any others I should consider?

Thanks

---

### Post by KillerKelvUK on 2015-07-08
I'd do your homework on how CentOS supports or otherwise your requirements from your other thread as you maybe into kernel rebuild just to enable some VFIO functions let alone the chance of vga arbitration and acs overides.

What functions do you want to be able to do from the web admin tool?

---

### Post by npinn001 on 2015-07-08
> **KillerKelvUK said:**
> I'd do your homework on how CentOS supports or otherwise your requirements from your other thread as you maybe into kernel rebuild just to enable some VFIO functions let alone the chance of vga arbitration and acs overides.

What functions do you want to be able to do from the web admin tool?

Thanks for the reply. I want to be able to create VMs and perform the initial install, and then from there happy to just SSH or remote desktop to the machines directly. I'm mainly trying to eliminate the need for a linux box just to manage the VMs...

---

### Post by TheFu on 2015-07-08
You can ssh in and run virsh and virt-install to do all of that.  Doing a non-GUI install is easy.

BTW - I'm on a chromebook (acer c720) now and it easily runs ubuntu with a lite-GUI and virt-manager.

---

### Post by jason_gibson2 on 2015-07-08
Been asking the same question myself for a year or 2 now, web based kvm management. There really is nothing that is easy and just works straight away. At the moment I'm dealing with a Kubuntu vm on my laptop so I can use virt-manager. I need to explore other options though as the vm is 8.5 gigs large, laptop has a 120gig ssd and I am looking forward to Windows 10 very much so I won't be going back to Linux as my main os on the laptop.

---

### Post by rms-mit on 2016-04-08
Just answering this old thread in case someone is looking. 

I have had webvirtmgr working in a docker image but it took me some fiddling to get the Spice console to work and then my docker image got corrupt (don't use docker with Dev mapper) 

This time around I used Kimchi which is now a packaged App on fedora 23. Worked fine once I update the host.py script in   [FONT=monospace][COLOR=#000000]/usr/lib/python2.7/site-packages/kimchi/model/host.py[/COLOR]
[/FONT] and changed the 

[FONT=monospace][COLOR=#000000]     res['cpus']   = psutil.[/COLOR][COLOR=#ffffff]NUM[/COLOR][COLOR=#000000]_CPUS[/COLOR]
     res['memory'] = psutil.TOTAL_PHYMEM

to 
     r[/FONT][FONT=monospace][COLOR=#000000]es['cpus']   = psutil.cpu_count() [/COLOR][COLOR=#000000] [/COLOR]
     res['memory'] = psutil.virtual_memory().total
[/FONT]

---

