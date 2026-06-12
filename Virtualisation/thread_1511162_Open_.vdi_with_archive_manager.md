---
title: "Open .vdi with archive manager?"
date: 2010-06-16
forum: Virtualisation
---

### Post by mooserider2 on 2010-06-16
I was working with ubuntu that was installed on a vdi, for various reasons i decided to install xfce on there. I thought it would be a good idea to delete ubuntu with: 

sudo apt-get remove ubuntu-desktop

After doing this I rebooted and it gets me to the xubuntu splash screen but it won't get any farther. I thought if i could open the vdi like an iso in archive manager or any other program i could copy my home folder and start over, or fix this problem. Is this possible or is there another way I could fix this that I cant figure out.

Oh new idea could I boot ubuntu from a live disk into vb and mount the vdi as a hard drive and do what i got to do from there?

---

### Post by mooserider2 on 2010-06-16
Ok if anyone finds them selves in this situation heres what to do. Create a new vdi and install your os. Go to virtual box and click settings and then storage. Add ur new vdi to the IDE controller list. Boot into your new vdi and go to your file manager and look for your old vdi's filesystem and do what you gotta do from there.

---

### Post by TheFu on 2010-06-17
This might not be the best answer, but it is another option.

You can convert the .VDI into a raw image and mount that from a Linux host using the loop device. I do this to perform incremental VM backups. 
[B]VBoxManage clonehd --format RAW ubuntu.vdi ubuntu.img
[/B]Then [B]
mount -t ext3 -o loop,rw ./ubuntu.img  /mnt[/B]
You will need to KNOW the type of file system, ext3 in this case.  After it is mounted, go in and edit away with the editor of your choice. Don't confuse files inside the /mnt location with the running host, or it will be bad.

Good luck.

---

