---
title: "I think I messed up my Hard Drive helpAnoob"
date: 2017-12-20
forum: Windows
---

### Post by guyluke on 2017-12-20
Hey guys,
I'm not sure if this is the place for this but I was having a problem with Windows Update don't liking Grub so I tryied replacing it with the Windows BCD and now NO OS will boot up with my HD inserted.

*The short version is:* I tryied Bootrec /fixmbr (OK) and /fixboot (ERROR: Element not found) so someone said select the partition as active on diskpart, when I did that I waited but it seemed like Diskparted stopped responding, I force closed it, when I tryied /fixboot again it also stopped responding. 

And just like that as soon I restarted my Asus notebook BIOS would hang, I coudn't even go to Setup with the HD inserted. I tryied changing settings without it but as soon as it was inserted it wouldn't start anymore. I tryied changing to another PC this would POST but any operating system you throw on it wouldn't load. I tryied starting Windows, Hirens Boot, DBAN and none would load so I could try doing something.

If anyone cares for the long version I will try to detail all the stuff that I did.
Anyway HALP!

---

### Post by SuperFreak on 2017-12-20
You might be able to resurrect the OS by using Boot Repair. Boot to a live USB or DVD of Ubuntu. Go to [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and follow the instructions for installing boot repair. Run boot repair and generate a report. Link that report on your next post and hopefully someone will help you.
If you are feeling lucky you can try the recommended fix on your own using boot repair but I recommend you put the report or a link to it in a post so someone with more knowledge than myself can see what is wrong with your system

---

