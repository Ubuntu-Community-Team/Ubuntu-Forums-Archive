---
title: "gazelle professional"
date: 2011-12-10
forum: System76 Support
---

### Post by ramus313 on 2011-12-10
with the default NVidia graphics card, 8 gb of ram, the i5 2.4 ghz cpu, and the hybrid 500gb 4gb ssd drive, would i be able to use virtual machine for windows, and even play games on like fifa 12 or CoD on it the virtual machine (with no lag)? if not would wine work? 

im just asking because im going to have to be able to use windows on my computer (the actual os not just wine), for school things. 

p.s. i have heard that when physically dual booting windos on a linux/ubuntu computer, it erases the entire harddrive, erasing ubuntu. is this the case even with thee laptops? even if i make a partition? 

thanks!

---

### Post by isantop on 2011-12-12
You would be able to run a virtual machine just fine, but games would be out of the question, since they all depend on Graphics hardware that virtual machines simply can't have right now. Maybe sometime in the future, but for now, it's not possible. Wine would work fine for the games if you can get it configured, but you can also keep a separate Windows partition just fine, without erasing Ubuntu. We have instructions for all of this on our knowledge base, here:

[http://knowledge76.com/index.php/Category:Windows](http://knowledge76.com/index.php/Category:Windows)

Once you install Windows, you do need to use a LiveCD to reinstall Grub, Ubuntu's bootloader, before you can boot it, but it's technically still there. Windows's Bootloader just can't start it.

---

