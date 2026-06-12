---
title: "A bootable source for Virualbox??"
date: 2008-06-08
forum: Virtualisation
---

### Post by Redptc on 2008-06-08
How to boot windows in Virtualbox?

I have only one need outside Ubuntu and that is MYOB, which is an accounting program I have used for years. I don't run a huge business, just a small, one man consulting sort of thing.

I tried running my version of MYOB in Wine but it was only partially successful. It will not print invoices and refuses to lock in changes to print formats. It is also very 'choppy'.

So I tried Virtualbox which I have up and running to the point where it "can't find a bootable disk". I only have the original Win98 OEM disk which is ok for restore only and, essentially, not bootable.

Any suggestions on how to substitute a bootable disk or even run this restore disk effectively. 

At present I dual boot to Win98 to use MYOB but would really prefer not to. The Linux accounting packages are not 'country specific' whereas my version of MYOB suits Australian tax practise.

I basically need a Win98 bootable floppy disk!

---

### Post by pytheas22 on 2008-06-08
Are you sure your Windows 98 disk isn't bootable--you can't put it in the CD drive and boot to the installer?  How else would you use it to restore your Windows system if something is wrong and you can't boot to the hard disk?

Make sure you've configured VirtualBox correctly to look for the Windows disk and boot to it.  It doesn't know to look automatically; you need to click Settings and go to the CD/DVD-ROM section to tell it where to look.

Otherwise, if it really is the case that for some reason your Windows disk isn't bootable, then I don't know what else you could try besides getting a Windows disk that you can boot to.  There are (legal) images for DOS boot CDs and floppies around the Internet if you search; they might get you somewhere if you're able to boot to them and then run the Windows set up CD from there.  But without knowing how exactly the Windows 98 CD is supposed to behave, it's hard to know whether this would work or not.

---

### Post by Redptc on 2008-06-09
Thanks Pytheus22, I do get the Win98 CD to the stage of saying that it is booting, then we get to a screen that is predominantly red with some garbled letters and digits...nothing can be activated? 

This CD allows you to restore your Win98. When you run it in windows you get to a menu that lets you choose the complexity of your 'repairs'.

In Win98, they had a way of setting up a boot floppy-disk which got you to the point where you could install the special 'Quick Restore' CD and get Your PC running again. 

When I run this 'bootable Win98 CD floppy' in Windows, it works (so does the CD). It is not read when I run it in Virtualbox.

I have downloaded 4 different Win98, so-called bootable floppies, but they don't seem to do the trick. I have tried the image and the other choice. My guess is that I do need the image version?

I will keep trying the downloads to see what I come up with. I'm pretty sure I have Virtualbox configured correctly by the I  can get to the point of actually booting to the menu in the Win98 restore CD. 

Any Ideas?

---

### Post by Shazaam on 2008-06-09
The Win98 cd that you have sounds like an OEM disk that came with a pc. Might be a problem because they usually look for a hidden restore partition on the hard drve.

---

### Post by pytheas22 on 2008-06-09
> The Win98 cd that you have sounds like an OEM disk that came with a pc. Might be a problem because they usually look for a hidden restore partition on the hard drve.

Yes, this could explain the problem.

The only other solution I can think of is to install Windows 98 to a real computer and then make an image of it to put on your VirtualBox drive.  This seems to me like it would probably work (although the hardware of the virtual machine and the real machine would obviously be different; hopefully Windows 98 could cope), but I've never actually done anything like that.

Another idea is to get a Windows 98 CD from somewhere else (e.g. the Internet) and then install using that.  I'm not sure how legal this is, but if you put in the Microsoft key from your OEM CD (they should have given you a key somewhere), then I don't see why it would be illegal, since you'd be running a validly licensed system.  Of course, you'd also be in possession of a Windows CD that you didn't pay for, I guess.  Also, your the key from your OEM CD might not work with normal install CDs.

Maybe you could also contact the vendor who supplied the OEM CD and ask for a real install CD.

Otherwise, I don't know how to solve the problem without turning to explicitly illegal means.

---

### Post by Redptc on 2008-06-09
Thanks for your help fellas but it sounds like it isn't going to work. I did indicate that it was an OEM version of Win98. 

It just means I will continue to dual boot to Windows to run this (and only this) accounting software.

Can't win them all, I guess.

---

