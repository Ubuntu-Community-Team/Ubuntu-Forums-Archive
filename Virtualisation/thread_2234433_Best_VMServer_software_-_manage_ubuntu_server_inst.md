---
title: "Best VMServer software - manage ubuntu server installations"
date: 2014-07-14
forum: Virtualisation
---

### Post by Fredrik_Magnussen on 2014-07-14
I am currently working on some small installations of Ubuntu server, and I need to keep the installations separate, and I also need to dedicate some different hardware to each installation (like giving one installation access to one of my networking cards, and the others should share a second card). Now, I have looked a little at XenServer, but I am unsure. My uncle (mainly a Windows Certified guy) recommends Hyper V, but he is unsure about compatibility with linux installations.

Information about my setup:
[LIST]
[*]consumer grade HW (i5 2500k, DDR3 non-ecc RAM, standard intel desktop networking card.
[*]Only ubuntu server installations (currently kept on separate computers, but they are now needed as standard desktop computers)
[*]Windows client for managing them (Win8 if it matters)
[/LIST]

TL:DR; best software for VM's of Ubuntu server, needs to be able to run on consumer HW.

---

### Post by TheFu on 2014-07-14
"best" - sorry, it isn't that easy.  I can say
* don't use hyper-whatever from microsoft to run Linux servers
* don't use "desktop VM tools" like virtualbox or VMware player, workstation, et al.
* look at xen and kvm.
* oh ... and don't get burned by VMware server products (esxi) - they've screwed their customers too many times, IMHO.
* may want to look at proxmox ... I've never used it, but people like the web interface for management and it supports kvm and a paravirtual thing.
* May want to look at docker for light application virtualization too, though I wouldn't put anything production on it for another year.

Management will either be through ssh or virt-manager (using an ssh tunnel).  I don't think virt-manager runs on Windows, but you can run it on any Linux with a GUI on real hardware or inside a VM local or with a remote desktop like NX. 

BTW, there is a virtualization sub-forum. That is the best place to ask this question.

---

### Post by Fredrik_Magnussen on 2014-07-15
I know that "best" is a bit too "easy", but I wanted people to say what they prefer :p

Thanks, I think I might roll with XenServer then. (My uncle did do some checking on Hyper-V btw, it does support linux installations, but you need to fiddle a bit appearantly.)

I saw that subforum, but I thought that was more for desktop virtualization (like VMWare Workstation)

---

### Post by slickymaster on 2014-07-15
Moved to the **Virtualisation** sub-forum.

---

