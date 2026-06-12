---
title: "Virtualbox and clonezilla powah"
date: 2010-07-20
forum: Virtualisation
---

### Post by Nerflander on 2010-07-20
Hello there, 

Been configuring Ubuntu servers for a few weeks now.... and the company i work for has a virtualbox ubuntu server running magento....

Now they orderd a new Server where they want the package to run on. Ofcours the messed to much with the core files of magento so i cant copy them over.

Now my question is can i make out of a virtual machine a .img file so i can clone/ghost something this on a real HD of the server (A)

sounds all silly but it would be a dream solution.

Hope some1 knows something ;)

Cheers!

---

### Post by varunendra on 2010-07-21
I have no idea about a real solution for this. But here's what I would have had tried first:

[LIST]
[*]Create a backup image of the current installation using partimage or clonezilla.
[*]Partition the destination physical hard disk similar to the virtual HDD (regardless of their size, keeping only format, type & sequence of partitions the same).
[*]Restore the image to the similar partition on the physical HDD.
[*]As driver problems are obvious to occur, I'd boot (hopefully;)) into recovery mode & try updating the system.
[/LIST]
VMware has tools for doing so but first it does not deal with any VM other than VMware's, second the OS has to be one of a few Windows versions.:(

I'd love to know if there's a generic solution for this as I also play a lot with VMs both on VMware & VirtualBox.

---

### Post by Nerflander on 2010-07-22
Hmh ye ive pretty much coverred the solution but making a new ubuntu server and tried to duplicate websites to the new apache2 module there.

Though i play alot with Virtual box etc. I stil ldont get it how virtualisation really works in the .ovf standards. Caus if i want to make a new server test it and find out ye this is awesome i would like to make it sationairy and use it but thats not very usefull for a desktop pc :)

I quess il just have to research more on how REAL virtualisation works. In form of a server with vmware on it where you have 4 servers running virtual for example.


thanks for your help :)

---

