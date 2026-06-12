---
title: "Virtualisation Beginner Questions"
date: 2014-09-20
forum: Virtualisation
---

### Post by jeff96 on 2014-09-20
Hi all,

So i've been looking through the sticky to get a better idea of virtualisation. I was told that there isn't much point in continuing to dual boot my systems, but rather I should virtualise them. I have installed virtual box and seem to have got the hang of it. I've also used a trial of vmware workstation. It seems to me that the virtual "Guest" gets pretty good access to the CPU and RAM, but quite lousy access to the graphics card. if this a fair assessment?


I was looking at the VMware page and noticed that VMware fusion for mac is advertised as "near native" speeds. Is there anyway to get this without a mac? I have a 2008 macbook air, but it can't really spare any resources to virtualise.

I've been using Ubuntu for about a year and pretty much used it as my sole OS, occasionally booting into windows to play some games. However my new laptop needs to use windows because the manufacturer provides loads of tuning apps that only work on windows, But I want to use mostly Ubuntu, so I'm thinking I can boot up windows 8.1 as they intended, but boot to Ubuntu full screen and use that primarily. 

Does anyone have any tips on how to best implement this? like I say I only use windows for games, and would have got rid of it if it wasn't for all the manufacturer stuff. 

Also, could someone help my understand Qemu and KVM - the sticky really confused me, do I need a "hypervisor"?

Thanks guys!

---

### Post by SeijiSensei on 2014-09-20
In VirtualBox, you can improve matters by making sure you have installed the [Extension pack]("http://www.virtualbox.org/manual/ch01.html") as well as VB itself.

Games often require direct access to the graphics hardware and won't run properly in a virtual machine.  Final Fantasy XIV refused to install into a Win7 VirtualBox running on top of Kubuntu.  When my daughter recently built a gaming computer, she installed Win7 as the primary OS with Kubuntu as the guest.

---

### Post by ibjsb4 on 2014-09-20
I use VirtualBox and find setting up guest (gnome) with two processors works better than one.

---

### Post by jeff96 on 2014-09-20
> **ibjsb4 said:**
> I use VirtualBox and find setting up guest (gnome) with two processors works better than one.
Thanks ibjsb4, is this where you assign the cores? I have a quad core (4810mq) which shows as 8 cores because of the 4 virtual cores. 

[QUOTE=SeijiSensei]Games often require direct access to the graphics hardware and won't run properly in a virtual machine. Final Fantasy XIV refused to install into a Win7 VirtualBox running on top of Kubuntu. When my daughter recently built a gaming computer, she installed Win7 as the primary OS with Kubuntu as the guest.[/QUOTE]

Thanks SeijiSensei, it does sound like this may be the best idea for me. As I only play games on my odd free evening and sunday afternoons, I'm thinking maybe assign 6/8 cores and 12/16GB ram to the ubuntu guest while using normally and power the guest down when i do play games? or is 75% too much resource?

Thanks!

---

### Post by ibjsb4 on 2014-09-20
This swayed me to stay with vBox.

[http://ubuntuforums.org/showthread.php?t=2241504&p=13108768&viewfull=1#post13108768](http://ubuntuforums.org/showthread.php?t=2241504&p=13108768&viewfull=1#post13108768)

---

### Post by ibjsb4 on 2014-09-21
> **jeff96 said:**
> is this where you assign the cores?
In your vBox main screen.

Machine>Settings>System>Processor

If its grayed out this may be because guest is in a saved state.  Guest needs to be shut down to change certain processes.

Also keep in mind that assigning too many processors to a guest system will actually slow it down.  To date, two has been the max for me.

---

