---
title: "installing ubuntu 16.10 in virtualbox 5.1.16"
date: 2017-03-14
forum: Virtualisation
---

### Post by willcej on 2017-03-14
Hello,
    I can't find the "post as a beginner" so I'm posting here.
I'm trying to install Ubuntu 16.10 64 bit in Virtualbox 5.1.16. I've gotten as far as the third screen (installation type) which has the choices of:1. Erase disk and install Ubuntu.2. Encrypt the new Ubuntu installation for security. 3. Use LVM with the new Ubuntu installation. 4. Something else.
   I assume choice 1 is the right one since Ubuntu is being installed in virtualbox and not on my physical hard disk. However, the warning "Warning: This will delete all your programs, documents, photos, music, and any other files in all operating systems." stopped me. What disc are they talking about? Surely not my physical hard disk? Since I'm installing Ubuntu on a completely empty virtual disk in Virtualbox, they couldn't mean that disk could they? Probably being paranoid, but I do not want to do something stupid like erase my real hard disk.
Thanks in advance for an answer
willcej

---

### Post by QIII on 2017-03-14
Hello!

That is the virtual disk you created.  You can reassure yourself by looking at the reported size of the disk that is the target of the installation and comparing that to the size of the virtual disk you created.  

If you created a 50GB virtual disk on a 1TB physical disk, for instance, you should expect that Virtualbox is installing to a 50GB disk and *not* a 1TB disk.

Cheers!

---

### Post by willcej on 2017-03-14
Thanks for the unexpectedly quick reply Qlll.
   So you're saying it's ok to go with choice #1 which is "erase disk and install ubuntu"? I don't know how to look at the reported size of target disk. I could have answered my own question if I knew where to see what disk Virtualbox was installing to. The size of the virtual disk is 16GB. The size of the real hard disk is 500GB. Like I said in the original message, I assumed that virtualbox was installing to virtual disk, but seeing that warning created great fear in me. 
Thanks again,
willcej

---

### Post by SeijiSensei on 2017-03-14
VirtualBox can only see the virtual disk it creates without additional services like mounting network shares or "shared folders" using the Extension Pack.  You're installing to that 16 GB "drive" which is actually just a large file in /home/username/VirtualBox VMs/.  I usually use 32 GB to give the VM some room for additional files.

---

### Post by willcej on 2017-03-15
Thank you Qlll. You've set me on the right track
Regards

---

### Post by willcej on 2017-03-15
Thank you SeijiSensei,
   I finally understand. Thanks for the tip about virtual disk size. If I can figure out how to go back to that setting, I'll increase it to 32GB also.
willcej

---

### Post by norafaithrainbow on 2017-03-15
The setting is there when you first create a new virtual box, after a few steps. Just go through the process of creating a new one, then when you get to that part, you can allocate as much as you like. Just stay over 10gbs and as previously mentioned, I would recommend 32 gb.

---

### Post by willcej on 2017-03-15
Thank you norafaithrainbow,
   I should've thought of that, because, after reading your post, I realized that you would have to create a new one to increase the size of the disk.
Regards,
willcej

---

