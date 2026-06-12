---
title: "Can't boot my USB in Ubuntu."
date: 2017-05-22
forum: Windows
---

### Post by avatarnikhil on 2017-05-22
I am currently on  Ubuntu 16.04.2 LTS. I want to do a clean install of Windows 10 by booting it in my USB. So I can't boot.
Backstory, earlier I had installed Ubuntu to dual boot with Windows 10, which failed. So, I ended up doing a clean install of Ubuntu. Am new to Ubuntu and miss my windows apps. So I wanted to install Windows 10 by a clean install. That's not going very well.

**Please HELP! :(**

Images - 
[FONT=arial][http://imgur.com/EEQhqad](http://imgur.com/EEQhqad)
[http://imgur.com/6ic9HgM](http://imgur.com/6ic9HgM)

[IMG]http://imgur.com/6ic9HgM[/IMG][IMG]http://imgur.com/EEQhqad[/IMG][/FONT]

---

### Post by mörgæs on 2017-05-22
Which Windows apps do you need? Maybe we can find you an alternative which runs in Ubuntu.

---

### Post by avatarnikhil on 2017-05-22
I already, checked. Adobe Suite. 
I agree there are really cool free open source software. But I rally invested so much time  into learning them and have assets. 

Please help me with the issue. 
Thanks

---

### Post by LastDino on 2017-05-22
Everything you can open with Adobe can be with these free tools as well, and in my opening certain tools perform better than adobe software. For example, GIMP, Blender and many more.

Right place for this request is windows forum, but general info to note would be this

Image you posted is talking about "softreset" and not clean install.

For clean install you need to either boot into recovery DVD or Win10 DVD / Live usb, follow the installation process as you will usually do and get rid of Ubuntu partitions if you only need Win 10.

If you were using genuine windows, there shouldn't be problem to get key from Microsoft as you're installing on same machine. (It would be different case if it was different machine). If not, then, well, not the right place to get advice.

---

### Post by avatarnikhil on 2017-05-22
I tried booting into Win10 via USB. I end up getting that "soft reset" error. Am I making any mistake in making the USB bootable? any suggestion as to which software I must use to boot. ?

Initially, my plan was to Dual Boot, so that I can migrate with easy. Take the best of the two worlds. That, well, got complicated. Grub2, etc.. So i installed ubuntu. I just wish dual booting was easy.

---

### Post by howefield on 2017-05-22
Thread moved to the "*Windows*" forum.

---

### Post by avatarnikhil on 2017-05-22
I found a link 
[HTML]https://answers.launchpad.net/ubuntu/+question/14023
[/HTML]

[COLOR=#333333][FONT=Ubuntu]Such things are generally solved by adding "all_generic_ide" to the kernel line in grub (press escape when grub loading message appears, press e, select kernel line, press e and add this at the end after a space). This might be a bit to strong in your case ( should work nevertheless :).



[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]
But I have no idea to do that. 
Can anyone please guide me. :D

Thanks!

---

### Post by yancek on 2017-05-22
Before installing Ubuntu to try to dual boot with windows 10, did you read the Ubuntu documentation on it at the link below?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do you have the windows installer files on a usb/flash drive now?  If so, how did you put them there? More details on that might help someone to help your.  Are you now able to boot Ubuntu?  If you follow the instructions at the site below, you should be able to boot the windows installer usb from the grub menu on the installed Ubuntu.  Just put the entry in that file rather than trying to install Grub on the flash drive.

 [https://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](https://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

