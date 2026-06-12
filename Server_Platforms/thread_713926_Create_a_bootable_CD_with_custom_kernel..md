---
title: "Create a bootable CD with custom kernel."
date: 2008-03-03
forum: Server Platforms
---

### Post by hugle on 2008-03-03
Hello everyone! 

It is my first post here, so I would like to say hello to every user around here:)

The reason I'm writing here-  I want create a custom CD with kernel only.

mkdir iso
mkdir -p iso/boot/grub
cp /usr/lib/grub/i386-pc/stage2_eltorito iso/boot/grub
cp /boot/* iso/boot/
cp /boot/grub/* iso/boot/grub/
#and we crate iso...
mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso iso

After booting this iso onto CD i get grub menu, but can't even start loading it, I get :
"Grub error 21: Selected disk does not exist"

What I'm missing ? 

What I'm trying to do is just put MBR onto CD, and wanna mount root partition via root=/dev/sda1 later ..

But beacause of this error I don't know what I'm doing wrong.

Thanks for any suggestions!

Keraj.

---

