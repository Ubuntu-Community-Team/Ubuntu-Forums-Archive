---
title: "commit to Ubuntu from dual boot"
date: 2024-10-01
forum: The Cafe
---

### Post by jwl247 on 2024-10-01
I'm currently dual booting Ubuntu and Windows 10 pro. I want to clone my windows partions and run windows in a VM in Ubuntu.. I've downloaded vhd windows thing, I just wanted to ask for advice here. Linux is going to be my only physical Os might as well cut the cord and transition

---

### Post by 0f4d0335 on 2024-10-01
Cool, I've been running Ubuntu as my main operating system for over a decade. It's very possible. And you can run many Windows applications from wine or virtualized as a web application. VM might be a big task, so don't fret if it doesn't turn out exactly how you'd like. Virtualbox is a good application.

---

### Post by makitso on 2024-10-02
I did this about a month ago, with Virtualbox,  and it was difficult.  First problem is the grub boot menu. VHD  will clone the boot partition and that includes grub.  In my case, I had to boot the windows repair disk and fix the mbr.  Then my system would boot directly to windows where I did the VHD thing.  When I was all done, I fired up the Ubuntu live CD, installed boot repair, and regenerated the grub dual boot mbr.

---

