---
title: "Syncing Media across network"
date: 2009-07-02
forum: Server Platforms
---

### Post by Nagrom_17 on 2009-07-02
Hello, I recently set up a home server for my family's photos and I was wondering if you could help me figure out how to do a few things.

network is 2 macs, 6 pcs(1 on vista, 1 on windows 7 and 4 on xp), and the server running ubuntu 9.04 server edition.

1.How can I get all the pictures from the computers on the network and move them to the server?

2.How can I then access the pictures in an organized fashion?(picasa? iPhoto?)

3.How can I make sure the server stays synced to all the computers on the network when someone adds new photos to their computer(from a camera mostly)?

Thank you for your time and I am leaving today for a week so I probably wont respond

---

### Post by jhannah on 2009-07-02
Depending on how sophisticated you want to get, it might be best to setup an NFS share on the Ubuntu server (provided that is where your primary storage is going to be) then simply mount that share on the other machines. I know that Vista and XP provide an NFS client (which is part of Windows Services for UNIX. See [http://support.microsoft.com/kb/324055](http://support.microsoft.com/kb/324055) and [http://www.microsoft.com/downloads/details.aspx?familyid=896C9688-601B-44F1-81A4-02878FF11778&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=896C9688-601B-44F1-81A4-02878FF11778&displaylang=en)). I imagine the mac also has support for NFS but I'm not sure of the details on that, it might even be anagolous to Linux.

This way each machine will have a mounted copy of the NFS share and be able to modify a centrally stored copy seamlessly. NFS works pretty well but I have heard reports of the Windows client being flaky (generally when you are really pushing it) so ymmv.

As for actually moving the files over, once you have the NFS share mounted everywhere, you can copy over your files from each machine one at a time.

Do keep in mind that having a single central location for file storage, while convenient, does put you at a higher risk for catastrophic data loss if you don't have RAID and/or a backup strategy and treating RAID like a backup is really just a nightmare waiting to happen.

Lastly, to organizeing your media, that is really a personal preference but Linux does offer quite a few applications one of the most popular being F-Spot. There is also a beta version of Piscasa for Linux which you might want to check out ([http://picasa.google.com/linux/](http://picasa.google.com/linux/)).

I hope that points you in the right direction.

---

### Post by Nagrom_17 on 2009-07-02
Thanks for you help I will look your suggestions but would I organize them just when the client is looking(I believe picasa does this) or can I run fspot on the server to organize them?

---

