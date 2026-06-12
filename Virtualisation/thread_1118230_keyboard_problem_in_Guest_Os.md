---
title: "keyboard problem in Guest Os"
date: 2009-04-06
forum: Virtualisation
---

### Post by aharoon111 on 2009-04-06
I have kubuntu 8.10 as host Os and Xp as Guest Os. I use Vmware Server v2.0 the problem is when i use the xp i found my keyboard letters are working wrong. for example when i press arrows up or down or right or left it it act as win key and i found the start menu appears also when i press alt+shift. and i cannt select a line and delete i have to delete letter at once. and back space doesnt work. all this errors in the guest Os. but on Kubuntu "the host Os" it works fine. before i move to linux i had Xp on this Machine and evevrything was working perfect with no problems at all so i want it work fine in both Oss.

---

### Post by Lunatico_22 on 2009-04-06
In this page there are some workarounds for your problem:

[http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html](http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html)

When I used VMWare workstation, the solution 3 worked for me, but I think solution 2 is better. However, a few moths ago I found that VirtualBox (the one from the page: [http://www.virtualbox.org/](http://www.virtualbox.org/) , not the OSE that can be found on the repositories) did not have that problem with the keyboard and offered the same level of funcionality for me, so I made the switch.

---

### Post by aharoon111 on 2009-04-07
Yes man i tried virtualbox before but on xp host. it was good on xp but i didnt try it on linux. but i think vmware is more stable and have more tools what u think in this?. i'll try the solution u gave to me and tell u if it solved the broplem or not

---

### Post by Lunatico_22 on 2009-04-10
Yes, VMWare has more tools than virtualbox, but I dont use them :P. The tools that I use are the 3d acceleration, USB support (for ipod touch sync because i am too lazy to configure it for amarok) and shared folders. 

For the programs that I use inside the virtual machine (Autocad, Archicad, Revit) I find no difference in speed between VMWare and Virtualbox, however, the time the VM takes to resume is A LOT shorter in Virtualbox than in VMWare. If you always turn off the VM, you wont note that difference. 

The only feature I think Virtualbox needs and VMWare has is the drag and drop of files between the host and the guest OS. In Virtualbox this can be done only with text. So to transfer files you have to copy them inside one of the shared folders between the host and the guest os. Also, I think the GUI of VMWare is a lot friendlier than Virtualbox's.

---

### Post by aharoon111 on 2009-04-13
Thanks it worked for me

---

