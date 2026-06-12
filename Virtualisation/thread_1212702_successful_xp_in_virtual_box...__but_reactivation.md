---
title: "successful xp in virtual box...  but reactivation??"
date: 2009-07-14
forum: Virtualisation
---

### Post by wcasper4 on 2009-07-14
I dual boot XP (SP3) and Ubuntu 9.04 because I need some Windows programs (iTunes, Office, MATLAB, Maple, etc.) 
I have successfully loaded the existing copy of my xp into virtualbox. However, whenever I open XP, I have to reactivate it over the phone... and when I boot to XP natively I have to reactivate it again. 
It pretty much has defeated the purpose of virtualbox, as it is easier to just boot natively so I don't have to reactivate everytime. 
Has anyone found any inkling of hope or resolution to this problem... it has to be out there somewhere??

Thank you.

---

### Post by cybergalvez on 2009-07-14
> **wcasper4 said:**
> I dual boot XP (SP3) and Ubuntu 9.04 because I need some Windows programs (iTunes, Office, MATLAB, Maple, etc.) 
I have successfully loaded the existing copy of my xp into virtualbox. However, whenever I open XP, I have to reactivate it over the phone... and when I boot to XP natively I have to reactivate it again. 
It pretty much has defeated the purpose of virtualbox, as it is easier to just boot natively so I don't have to reactivate everytime. 
Has anyone found any inkling of hope or resolution to this problem... it has to be out there somewhere??

Thank you.

I've never had to do that, are you using the "same" XP install for both your vbox and your dual boot? that is did you link vbox with a real HD rather then using virtual drive, because thats the only way I can see happening what your talking about, and if that is the case then yes XP would be operating as expected because your hardware would be different depending on how you booted into XP

---

### Post by aesis05401 on 2009-07-14
> **wcasper4 said:**
> I dual boot XP (SP3) and Ubuntu 9.04 because I need some Windows programs (iTunes, Office, MATLAB, Maple, etc.) 
I have successfully loaded the existing copy of my xp into virtualbox. However, whenever I open XP, I have to reactivate it over the phone... and when I boot to XP natively I have to reactivate it again. 
It pretty much has defeated the purpose of virtualbox, as it is easier to just boot natively so I don't have to reactivate everytime. 
Has anyone found any inkling of hope or resolution to this problem... it has to be out there somewhere??

Thank you.

I run all sorts of licensed Windows Products inside VBox and I have never heard of or had this problem.  

Please post back as you find out more.  Good luck.

---

### Post by wcasper4 on 2009-07-14
OK... maybe there is a different way I can set it up?

I first cloned my hardware profile in windows, so I have a Virtual and Physical. 

Then in linux ran:

$ sudo apt-get install mbr
$ cd ~
$ install-mbr --force .VirtualBox/vboxmbr.mbr
 <<this created the new MBR>>

<<To create my virtual machine>>

$ sudo fdisk -l

<<windows is on sda/1>>

$ sudo VBoxManage internalcommands createrawvmdk -filename /home/walter/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 1 -mbr /home/walter/.VirtualBox/vboxmbr.mbr -relative -register

<<Then I created it in VBOX>>
$ sudo chown walter .VirtualBox/WindowsXP.vmdk .VirtualBox/WindowsXP-pt.vmdk

In vbox I added this vmdk as a virtual hard disk and then created my virtual machine.

it was based off of this blog I read on it [http://anderstornvig.dk/2008/06/03/running-existing-windows-in-virtualbox-on-ubuntu/#comment-142]("http://anderstornvig.dk/2008/06/03/running-existing-windows-in-virtualbox-on-ubuntu/#comment-142")

I have SP3 on windows (if that matters)

did I do something wrong, or is there a better way of doing this where I won't have to reactivate?

---

### Post by aesis05401 on 2009-07-14
It's a good question.  I have no experience with that manner of mounting an existing image inside a .vdi file.  

Out of curiosity, when you make changes to system settings do they persist from reboot to reboot?  

If not, it is possible that you are set to launch a fresh copy of the image each time the VM starts.  Unfortunately, this is a little out of my experience, but a temporary workaround would be to snapshot the VM after activating windows, and then always restore from that snapshot instead of simply rebooting.

---

### Post by wcasper4 on 2009-07-14
> **aesis05401 said:**
> It's a good question.  I have no experience with that manner of mounting an existing image inside a .vdi file.  

Out of curiosity, when you make changes to system settings do they persist from reboot to reboot?  

If not, it is possible that you are set to launch a fresh copy of the image each time the VM starts.  Unfortunately, this is a little out of my experience, but a temporary workaround would be to snapshot the VM after activating windows, and then always restore from that snapshot instead of simply rebooting.

I have been told that it will save changes either natively and bring them to virtualbox or in vb and back into native, which is why I want to get this to work... but the reactivation issue is killing me... I can't seem to get around it, nor find anyone else who has xp pro sp3 as an existing image in vb...

---

### Post by Ubtuntu on 2009-07-15
See this workaround for VMWARE maybe you can use it with Virtual Box. See the comments and someone talks about adapting it for Virtual Box. 

[http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/](http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/)

---

### Post by wcasper4 on 2009-07-15
> **Ubtuntu said:**
> See this workaround for VMWARE maybe you can use it with Virtual Box. See the comments and someone talks about adapting it for Virtual Box. 

[http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/](http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/)

Thanks... unfortunately I have tried this and it does not work. 
I just find it hard to believe I'm the only person in this situation...

---

### Post by Ubtuntu on 2009-07-15
Hrmm, well if you changed the boot detection in the example script on that link I gave so it looks for your Vbox virtual eth adapter  and you are sure it is executing then it is probably SP3 changes. Sucks when the only solution appears to be a crack for your legal copy of XP which I do not advocate.

---

### Post by wcasper4 on 2009-07-16
Exactly, which is why I find it hard to believe that there's not a way around this... Or is there?

---

