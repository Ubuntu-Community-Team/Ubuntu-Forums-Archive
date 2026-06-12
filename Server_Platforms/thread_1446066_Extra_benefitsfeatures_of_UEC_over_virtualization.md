---
title: "Extra benefits/features of UEC over virtualization"
date: 2010-04-03
forum: Server Platforms
---

### Post by Sivaa on 2010-04-03
Hi&#8626;I have set up UEC and have installed the store images.  I have seen that we can create and run instances which are similar to virtual machines.&#8626; We can utilize virtualization and create virtual machines and thereby fully utilize the server. Not sure what extra benefits or features can be achieved using cloud (say UEC). &#8626;I suppose I am missing something. Kindly let me know how cloud adds more value than server virtualization.&#8626;Cheers Siva

---

### Post by Old_Grey_Wolf on 2010-04-04
If you have a few servers with a few VM on each, then UEC or their competitors' products may not help that much. However, if you have 10, 20, 30, ..., servers with a dynamically changing set of VMs running; then, the tools help you manage the data center. You have a centralized place to know what is running, where it is running, and what resources it is consuming. If a server is low on resources, you can find one in the data center that has free resources, and move a VM to that server. You can also manage storage. With simple virtualization you need to know where the virtual image is stored, and what server the disk/raid is connected to. The cloud tools keep track of that for you in a centralized control center. If you are the only person managing the data center then you may have an undocumented way of doing things. If you have a department of people managing a data center, the cloud tools can be used so that everyone does the same things the same way.

Edit: Then there is the LAN. Management of virtual LAN security; which, is a long winded topic in itself.

---

