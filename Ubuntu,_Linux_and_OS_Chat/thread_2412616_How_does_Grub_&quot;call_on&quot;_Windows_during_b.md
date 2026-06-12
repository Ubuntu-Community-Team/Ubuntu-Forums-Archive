---
title: "How does Grub &quot;call on&quot; Windows during boot on a dual boot PC?"
date: 2019-02-15
forum: Ubuntu, Linux and OS Chat
---

### Post by raphaell2 on 2019-02-15
This is not in any way an "urgent" question or anything like that, just something I'm a bit curious about: when I boot up Windows on my dual boot PC (Windows 7 to be precise), what exactly happens at the moment when Grub "hands over responsibilities" to Windows?

---

### Post by freemedia2018 on 2019-02-15
The best technical info I could find on the GRUB chainload process is on this page: [https://wiki.osdev.org/I_use_a_Custom_Filesystem_-_What_Bootloader_Solution_is_right_for_me%3F](https://wiki.osdev.org/I_use_a_Custom_Filesystem_-_What_Bootloader_Solution_is_right_for_me%3F)

> For Windows, a record is placed which indicates the partition Windows is installed on, and an instruction to *chainload*  one sector (512 bytes) into RAM at 0x7C00, and jump to it; In other  words, simply load the Windows bootloader into RAM as if it was placed  there by the BIOS.

After that, you'd have to ask someone about Windows itself.

---

### Post by raphaell2 on 2019-02-15
> **freemedia2018 said:**
> The best technical info I could find on the GRUB chainload process is on this page: [https://wiki.osdev.org/I_use_a_Custom_Filesystem_-_What_Bootloader_Solution_is_right_for_me%3F](https://wiki.osdev.org/I_use_a_Custom_Filesystem_-_What_Bootloader_Solution_is_right_for_me%3F)



After that, you'd have to ask someone about Windows itself.

Thank you!

---

### Post by oldfred on 2019-02-15
Some more info on the Windows boot process.
       [http://thestarman.pcministry.com/asm/mbr/VistaVBR.htm](http://thestarman.pcministry.com/asm/mbr/VistaVBR.htm)
[http://thestarman.pcministry.com/asm/mbr/W7MBR.htm#INTRO](http://thestarman.pcministry.com/asm/mbr/W7MBR.htm#INTRO) 
    
       [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)

Grub only boots working Windows, and the load of Windows PBR from grub seems to be faster than BIOS MBR to PBR, so barely enough time to press f8 to get into Windows repair console. 
Best then to always have Window repair flash drive for current version of Windows.

---

### Post by raphaell2 on 2019-02-16
> **oldfred said:**
> Some more info on the Windows boot process.
       [http://thestarman.pcministry.com/asm/mbr/VistaVBR.htm](http://thestarman.pcministry.com/asm/mbr/VistaVBR.htm)
[http://thestarman.pcministry.com/asm/mbr/W7MBR.htm#INTRO](http://thestarman.pcministry.com/asm/mbr/W7MBR.htm#INTRO) 
    
       [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)

Grub only boots working Windows, and the load of Windows PBR from grub seems to be faster than BIOS MBR to PBR, so barely enough time to press f8 to get into Windows repair console. 
Best then to always have Window repair flash drive for current version of Windows.

Thank you!

---

