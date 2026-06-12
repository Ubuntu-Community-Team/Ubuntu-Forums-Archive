---
title: "Have I lost my mind??? Newbie"
date: 2020-03-23
forum: Virtualisation
---

### Post by randypecker6 on 2020-03-23
I have been trying for at least a month to get linux running in a VM on my iMac.  I believe that I have downloaded and installed ever first level flavour in the world, BUT......
I must me an idiot.   Proficient with Windows amd Mac OS, I don't seem to be able to get ANY data into Ubuntu.  I cannot see any drives attached to my iMac nor can I find anything on the main mac partition. Have messed with samba, guest app, etc. etc. Dose Ubuntu maintain a war criminals data base? How about really unattractive men?

I can't figure it out.

Surely it can't be that hard.

Thanks in advance.
Cheers

---

### Post by wildmanne39 on 2020-03-23
Hello and welcome to the forum.

*Thread moved to **Virtualisation a more appropriate sub-forum**.*

---

### Post by crip720 on 2020-03-24
Some VMs have extensions or addons that would need to be added or permissions granted to see other drives.  Should add which VM you are using so somebody else can give proper instructions.  Should add also exactly what you are trying to do,  I am thinking you want to add/copy data from one drive to the VM Ubuntu.

---

### Post by ank2 on 2020-03-24
No direct help. But since MacOS runs on top of some UNIX, why not exploit that and use UNIX (without VM)?

Then, in a VM like VirtualBox, you need to install and configure the package Guest Additions to share folders between the host and the emulated system.

[https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

Yes, a lot to read...

---

### Post by SeijiSensei on 2020-03-24
Virtual machines are self-contained.  All their interactions with the host system depend on additional software.

If you're running VirtualBox, you need to install the matching [Extension Pack]("https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack") for your VB version.  Then you can use the "shared folders" method to mark directories on the host machine that are accessible to the VM.

---

