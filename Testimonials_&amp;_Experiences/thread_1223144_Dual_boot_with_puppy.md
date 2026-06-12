---
title: "Dual boot with puppy"
date: 2009-07-25
forum: Testimonials &amp; Experiences
---

### Post by kf6gse on 2009-07-25
[B][SIZE=5]Too many different advice with no real tangible results
[/SIZE][/B][SIZE=5][SIZE=2]So here we go. Having puppeeeB4.2 installed on my Asus 701 already imagine my surprise when I tried to add Jaunty 9.04 and then could no longer boot my puppy. Having spent many hours searching the various forums I found no real solutions. Hence, I began playing around with the Ubuntu's grub menu.lst and finally have both booting at start from Ubuntu's grub loader. The very first thing folks need to understand is how to get a multiple choice at boot. As the machine is leaving POST and begins the stage 1 grub _**HIT "Esc"**_ on your keyboard. This will stop the countdown and allow seeing the other boot options. Too many newbies do not understand this concept. That having been said, now onto the problem. If a user doesn't know the puppy's install location stop now and boot your puppy with the **LiveCD **that you used to install puppy. **"It might be good to mention that your puppy should be installed before installing Ubuntu" **At any rate check where your puppy is installed. It could be HD??, SD?? or many different locations. The point is to locate where it is and write it down on a piece of paper. Mine happened to be installed at **/dev/sda2** . Armed with this piece of information I found several posts in various forums which give hints about editing the Ubntu's grub menu.lst but none quite explained enough for an Ubuntu newbie to complete the task. So remove your puppy **LiveCD** and boot into Ubuntu. Once up and running go to **Places **on the toolbar and scroll down to  **Computer** and click on it. Once that opens click on **Filesystem** and then **Boot** and then **Grub**. Look down the files until you see **menu.lst** and click it and choose to display. What I did was to add the following at the bottom of the page.
  ### END DEBIAN AUTOMAGIC KERNELS LIST

[COLOR=DarkRed]# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        unknown Linux distribution (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz root=/dev/sda2 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        unknown Linux distribution (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz root=/dev/sda2 
savedefault
boot [COLOR=Black]
Exactly as is in red above. Of course it is required to save it and then get into a terminal and sudo update-grub and exit but that has all been well explained in all of the forums.
**Rebooted **my little Asus 701 and low and behold, hitting **"Esc" **at grub opened up the Ubuntu choices as well as two unidentified linux choices. I scrolled down to one of them and **wala!** puppy booted. Naturally I tried each choice at boot and now am a very happy Ubuntu/Puppy user with both installed to my 4GB SSD without having any USB or SD card inserted to get it up and running. Hope this helps some of those who have lost as much hair as I have over this issue.:popcorn:  
[/COLOR][/COLOR] [/SIZE]
[/SIZE]

---

