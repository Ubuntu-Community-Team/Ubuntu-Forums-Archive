---
title: "Need Assistance with a Dual Boot"
date: 2013-06-05
forum: Ubuntu Christian Edition
---

### Post by parkernathan on 2013-06-05
I'm running into a little ordeal and I'm hoping the community can assist. 

I'm attempting to dual boot Windows and UCE on the same machine.

I have just performed a clean install of Windows.

However, instead of the normal process where Ubuntu detects Windows and offers to run them side by side, Ubuntu is not detecting Windows and is asking me to either wipe my drive entirely clean, or something else, where I can specify how and where I wish to install Ubuntu.

Here's the details of my setup:

Hardware is VIA Artigo A1250 (see [http://www.viaembedded.com/en/products/systems/1990/1/ARTiGO_A1250_(Pico-ITX).html)](http://www.viaembedded.com/en/products/systems/1990/1/ARTiGO_A1250_(Pico-ITX).html)). It's a cute little machine and will give me a lot of Windows and Ubuntu power in a tiny little box.

Hard drive is Samsung SSD 840 Series 500 GB.

Windows OS is Windows 7 Professional 64 Bit (I have the ability to upgrade to 8 Pro if need be).

Ubuntu OS is UCE 12.04 LTS 64 Bit.

I created two partitions when installing Windows (basically splitting my drive in half).

Here's where the issue probably lies. My machine boots over EFI instead of a regular BIOS. So there's probably something I need to do to kick in the dual boot working with an EFI instead of a BIOS.

Here are screenshots of what I'm seeing at the Ubuntu installation (look at them from right to left, the order reversed when uploading them):

[ATTACH=CONFIG]243537[/ATTACH][ATTACH=CONFIG]243538[/ATTACH][ATTACH=CONFIG]243539[/ATTACH]

Here's a picture of my EFI boot screen (when I boot up and hold down delete):

[ATTACH=CONFIG]243540[/ATTACH]

I'd prefer to ditch dual booting and use virtualization, and while my processor supports hardware virtualization, the manufacturer hasn't fully baked it into the EFI, so I can only run VM's with a single processor at a time and very low video memory, which wouldn't do for my applications. I need Windows and Ubuntu to have the full power of the hardware.

Any help would be much appreciated.

Thanks a bunch!

---

### Post by skimo12 on 2013-06-07
Hi Parkernathan,
I think you can quite safely go with the 'something else' option. I think that there are guides to show you what kind of ratios to use when you create the new partitions. I don't have your kind of EFI hardware, so I can't test it, but I would think that it should work. 
I think also that you won't need to worry about resizing your windows partition. You've basically done that by leaving a spare partition for UCE. Click Select 'other' then Click 'next' and see what options it gives you. From what I can see, you won't be deleting your Windows partition. I think that it's Windows 8 that is often a bit hard to get around. You can post back here before you take the last step that could possibly erase your data.
If you have some time, you can also get on the UCE IRC page, for slightly faster responses. I'll keep an eye on this page here, in case you bring up something.


Cheers,
skimo12

---

### Post by skimo12 on 2013-06-07
..and some interesting answers here..
[http://askubuntu.com/questions/193144/dual-boot-uefi-windows-7-and-ubuntu-12-04-both-64-bits-w7-entry-doesnt-appea](http://askubuntu.com/questions/193144/dual-boot-uefi-windows-7-and-ubuntu-12-04-both-64-bits-w7-entry-doesnt-appea)

---

### Post by parkernathan on 2013-06-07
Good news! I got it going. I posted this over in the Installation thread, and seems my drive had some partition gunk left over from a previous Ubuntu installation. I had to run fixparts on the Window side, then booting into Ubuntu allowed it to discover the Windows installation and run them side by side. My dual boot is in business, and now I'm wrapping up installing any leftover drivers I need, then I can press on!

---

### Post by skimo12 on 2013-06-08
hi parkernathan, Wow. ooops :) Sorry to have given you the wrong information earlier. I'm glad that you got the correct information now.
..looking forward to seeing more of your posts about UCE.

---

### Post by parkernathan on 2013-06-08
No worries! I was thinking that's what I should have done as well. I was thinking I should choose the Something Else option and just click in what I needed. I never heard of FixParts until the other post brought it up. Glad it's working now! Glad to be a part of the UCE community and looking forward to participating here.

---

