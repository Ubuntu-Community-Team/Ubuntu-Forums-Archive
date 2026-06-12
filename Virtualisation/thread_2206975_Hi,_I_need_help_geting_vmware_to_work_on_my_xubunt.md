---
title: "Hi, I need help geting vmware to work on my xubuntu 13.10"
date: 2014-02-21
forum: Virtualisation
---

### Post by andreadixon825 on 2014-02-21
Hi, Im new to vmware and xubuntu, I have went to the vmware website and talked to them on the phone, they told me to download VMware Workstation for Linux 64-bit, I have done that but xubuntu will not open the file from there website, I have check the ubuntu software center and can not find that poroduct, is there some other way to get this to install, I just want to get windows xp on vmware. I have tryed VirtualBox and it works good for windows xp but, some stuff in it I can not do because they said it dose not do what I want it to do. I just wanted to open windows xp and beable to install software though cd dvd and floppy drive and send files to my linux to the windows xp, and they said that VirtualBox can not do that, Thats why Im trying the vmware. Is there other programs beside vmware and virtualbox, I dont know how to install vmware, can you guys give me some tips to do this, thanks so much for reading my post. :D

Andrea Dixon

---

### Post by TheFu on 2014-02-21
Asking any commercial vendor about F/LOSS versions of competing software and expecting the whole truth is not likely to lead to 100% complete answers.

VMware Workstation is an impressive product, but mainly for the better handling of snapshots, which is critical for professional software testing teams. Virtualbox can do that too, just not as slick.

Though I cannot completely understand the issues you are trying to solve, the grammar is odd to my, there is nothing above that VirtualBox cannot accomplish.

Mounting the disks from the physical machine has been available and working for 4+ yrs.
Writing files from any clientOS to the hostOS has been solid for 3+ yrs, though not supporting all native file system features - very few end-users even understand those capabilities.
Writing files from any hostOS to the ClientOS can be performed using whatever network sharing the clientOS supports - CIFS, NFS, sshfs, whatever. This has nothing to do with virtualization. It is possible to go the other way too, but using the built-in virtualization hostOS mount is often easier.

So, if you could clarify the exact needs, I'm fairly certain someone can provide links to the [virtualbox manual]("http://www.virtualbox.org/manual/UserManual.html") which describes how to accomplish it.

---

### Post by andreadixon825 on 2014-02-21
Hi, thanks for the replay this is what I said at virtualbox fourm. I asked this question.

(Hi, Im new to VirtualBox, Is there away to drag files to my Virtual  windows xp, Because Im using xubuntu and I have alot of windows files I  have downloaded to my linux and I want to put thoughs files on my  windows xp virtualbox, is there away to do this. And I have one more  question, When ever I put a cd or dvd in my drive it shows up in linux  but dose not on windows xp virtualbox or and floppy drive. Thanks for  leting me post Im glade that Im now part of this community)

And got a replay back saying this.

(Drag'n'drop is only supported to a Linux guest ( at this time )You should read about guest additions & shared folders in your VirtualBox users manual.

---

### Post by TheFu on 2014-02-21
Setup a shared folder inside the guestOS. Then from the hostOS, mount that shared folder and drag-n-drop away. This has NOTHING to do with virtualbox or Workstation - it is standard network file sharing.

See how asking the question in a specific way returned an answer that wasn't a solution even when there was an EASY solution?

---

### Post by andreadixon825 on 2014-02-21
Hi, so somewhere in linux theres a guestos folder, this is what im trying to do, I just want to put files on to my guestos and form the gestos to the hostos wich is linux xubuntu, can I do that, or should what do you mean by networking file sharing do I set this up in linux or my windows xp virtualbox. I hop that makes sents. Basicy I just want to send file to from host to guest and guest to host. Thanks for the replay.

Andrea Dixon

---

### Post by TheFu on 2014-02-21
Inside the guestOS - that is what we call the virtual machine ... enable a shared folder using the normal OS shared folder method. On WinXP (which is going out of support in 6 weeks), right click on the folder and select "sharing".

After you share the folder, from Linux(hostOS) using the file manager, browse to the WinXP machine (guestOS) on the network and access the shared folder.
I can't help any more than that.

---

### Post by andreadixon825 on 2014-02-21
Thanks for your help, I can get it working it may take a sometime but I can figer it out, thanks agine.

Andrea Dixon

---

