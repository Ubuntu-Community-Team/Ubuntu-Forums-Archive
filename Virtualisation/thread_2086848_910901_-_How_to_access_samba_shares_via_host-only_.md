---
title: "910901 - How to access samba shares via host-only adapter?"
date: 2012-11-22
forum: Virtualisation
---

### Post by hamidi on 2012-11-22
hi
using virtualbox, i've nat adapter and host-only adapter. host is Windows 7, guest is Ubuntu 10.10.
how can i access samba shares?
i could use bridge instead of nat before, and i had no problem. i could  handle samba shares with ease. but now I HAVE FORCED TO SWITCH TO NAT.  so please don't suggest me to still use bridge. just let me know is it  possible to access samba shares via host-only adapter? is yes, how?
i've heard that i CAN'T access samba shares via nat, is it right?
but they say it's not a problem to use host-only adapter or Internal Network as well as nat.
also let me know what's the difference between Internal Network and  host-only? i just needed a way to access guest via host. so i added a  host-only adapter for this purpose.
anxiously waiting for any useful reply.
thx

---

### Post by sabrinaclough on 2012-11-22
[LEFT][COLOR=#000000][FONT=Arial]Hello,
Well, i think you should try to use a Bridge Adapter in virtualbox.After that you can follow this..virtual box>settings for your machine->Network->Adapter 1 and select Bridged Adapter. May be this will make you virtual machine part of your main network.
Thanks,
[[COLOR=#222222][FONT=arial]INFRASTRUCTURE VIRTUALIZATION[/FONT][/COLOR]]("http://cocoresolutions.com/infrastructure-virtualization")



[/FONT][/COLOR][/LEFT]

---

### Post by ZippyUbu on 2012-11-27
Hi hamidi,

I'm not that familiar with VirtualBox although I have myself been reading about using it. To hopefully answer some of your questions you can read about the differences between networking modes in VirtualBox on the below link; there is some reading regarding NAT also: 
>  let me know what's the difference between Internal Network and  host-only?> i've heard that i CAN'T access samba shares via nat, is it right?[Introduction to networking modes]("http://www.virtualbox.org/manual/ch06.html")

--Zu

---

