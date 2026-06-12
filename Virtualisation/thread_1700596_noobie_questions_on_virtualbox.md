---
title: "noobie questions on virtualbox"
date: 2011-03-05
forum: Virtualisation
---

### Post by bodselecta on 2011-03-05
Sorry for asking daft questions but better to ask a daft question than not to :)

I've removed the vista partition from my laptop. I have the dell install/restore disk and key. My aim is to get 2 or 3 versions of IE running in virtualbox for web development testing.

I'm right thinking that there'll be no free guest OS's for windows I can install and I'll need legit copies?
I don't understand this link [http://www.microsoft.com/downloads/en/details.aspx?FamilyID=21eabb90-958f-4b64-b5f1-73d0a413c8ef&displaylang=en#AffinityDownloads](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=21eabb90-958f-4b64-b5f1-73d0a413c8ef&displaylang=en#AffinityDownloads) which says to download windows IE testing ISO's. It looks like these have their own key which you can use but the xp ISO's are .exe files, though the instructions are to unrar the file - it's not a rar file.

I was about to install the dell vista restore onto a guest VM but then started to worry because it's a dell disk, it might try and reclaim the whole disk again as it'll be a specific install? So I stopped before pressing install. I'm thinking it should be safe though as the VM will only see the 10gb VDI disk?

Any help would be appreciated

---

### Post by SeijiSensei on 2011-03-05
The installation won't be able to "escape" the VM, but you may have bigger problems with licensing.  That Dell restore disk may only work on the actual Dell hardware.  It may or may not install, but even if it does, your key will likely be rejected when you try and register the VM copy of Windows.

Someone here once posted a method to use the OEM version of Windows that comes with a machine within VirtualBox and preserve the license.  You'll have to do some searching, but I remember seeing this posting sometime in the past six months.

One thing you most definitely cannot do is create multiple VM instances of Windows and register each of them with the same key.  Each instance will require its own license.

---

### Post by bodselecta on 2011-03-05
Thanks, the disc looks like it's an OEM, will it not just check the ID number of the machine from BIOS, see it's the same machine and allow the install? It's the same laptop it's being installed on
Or is it because it'll be running as a VM it'll be seen a different machine?

If I want other versions of windows will I have to look at buying copies from amazon etc?

edit: is that microsoft link useless then? it kinda looks like they provide limited license ISO's for IE testing

> **SeijiSensei said:**
> The installation won't be able to "escape" the VM, but you may have bigger problems with licensing.  That Dell restore disk may only work on the actual Dell hardware.  It may or may not install, but even if it does, your key will likely be rejected when you try and register the VM copy of Windows.

Someone here once posted a method to use the OEM version of Windows that comes with a machine within VirtualBox and preserve the license.  You'll have to do some searching, but I remember seeing this posting sometime in the past six months.

One thing you most definitely cannot do is create multiple VM instances of Windows and register each of them with the same key.  Each instance will require its own license.

---

### Post by Old_Grey_Wolf on 2011-03-05
I am on my Dell laptop right now with Virtualbox running the Dell OEM Vista I installed as a VM from the restore disks.

Try installing it. It will only format the VDI disk.You will probably want a VDI disk that is 40GB. I am using 26GB and only have Vista, anti-virus, Open-Office, and Firefox installed.

---

### Post by bodselecta on 2011-03-05
Thanks OGW

Far too easy! I even moved home to a seperate unused partition so I've got lots to play with....

One last question, whats the chances I can create a snapshot of this session for IE8? 

> **Old_Gray_Wolf said:**
> I am on my Dell laptop right now with Virtualbox running the Dell OEM Vista I installed as a VM from the restore disks.

Try installing it. It will only format the VDI disk.You will probably want a VDI disk that is 40GB. I am using 26GB and only have Vista, anti-virus, Open-Office, and Firefox installed.

---

### Post by Old_Grey_Wolf on 2011-03-05
> **bodselecta said:**
> 
One last question, whats the chances I can create a snapshot of this session for IE8?

I would suggest reading the Virtualbox PDF document regarding snapshots.

You should be able to save snapshots of various configurations of Vista with IE7, IE8, etc.

You can make a backup copy of your existing VM by going to your home folder > .VirtualBox hidden folder > Machines and HardDisks folders and make a backup copy of the Vista Virtual Machine folder and Vista Disk file (copy and paste them to a new file/folder with a different name).

Then you can play with snapshots until you are comfortable using them. If you need to recover your original VM, rename the backup copies of the Virtual Machine and Disk folder/files back to their original name.

---

### Post by Old_Grey_Wolf on 2011-03-05
> **bodselecta said:**
> 
One last question, whats the chances I can create a snapshot of this session for IE8?

Also check out the "VBoxManage clonevdi" command in the Vortualbox PDF documentation. You can make several copies of your VM VDI disk. Then create new VMs using the cloned disks. Select use exiting disk when creating the new VM and select the cloned disk you want to use for each instance of Vista. Then customize each of the new VM instances of Vista the way you want. Note that each cloned VM VDI disk uses a lot of disk space.

Edit: if you need help with the "VBoxManage clonevdi" command, just post back here on the forum. Basically use a terminal to go to /home/[user]/.VirtualBox/HardDisks and enter "VBoxManage clonevdi [oldvdiname] [newvdiname]".

---

### Post by bodselecta on 2011-03-05
Thanks for the tips. I wanted to try another install I so created a new vdi installing from the same install disk, would have been easier just copying the orig vdi but i just wanted to try :)
I'm getting IE9 on that one just now

I really do love unbuntu

> **Old_Gray_Wolf said:**
> Also check out the "VBoxManage clonevdi" command in the Vortualbox PDF documentation. You can make several copies of your VM VDI disk. Then create new VMs using the cloned disks. Select use exiting disk when creating the new VM and select the cloned disk you want to use for the instance of Vista. Then customize each of the new VMs the way you want. Note that each cloned VM VDI disk uses a lot of disk space.

---

### Post by Old_Grey_Wolf on 2011-03-05
I have edited my previous post; therefore, you may what to read it.

Edit: Don't run more that one Vista VM at a time or you will be violating Microsoft's EULA. :)

---

