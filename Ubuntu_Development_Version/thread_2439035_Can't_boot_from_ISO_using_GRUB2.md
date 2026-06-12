---
title: "Can't boot from ISO using GRUB2"
date: 2020-03-21
forum: Ubuntu Development Version
---

### Post by julianbrelsford on 2020-03-21
I have grub2 as my bootloader -- installed it independently of any distribution and I created my own grub.cfg and edited it directly (rather than using, for example, one auto-generated in Ubuntu). 

With grub installed, Windows & Fatdog64 are working fine, however i was not able to boot a Lubuntu Focal Fossa ISO. Years ago, i used to successfully boot various Ubuntu flavors (2016-2017 versions i believe) directly from an ISO stored on USB stick or hard disk, no problem.. so i thought i'd try that. I'm guessing the choice of desktop environment didn't have any impact but I don't actually know that. The ISO i used was the most up-to-date Focal iso as of March 20th. 

I don't *think* i missed anything important in terms of GRUB2 commands in order to boot correctly, which made me wonder -- is this a capability that is currently broken in Focal? Is it just a feature that's being dropped .... or maybe I'm doing it wrong? 

Capturing the exact errors my computer was tossing up on screen is not within my skillset but I saw a LOT of different messages go up and then it would stop with a bunch of words including "kernel panic" on screen. 

Does anyone have any insight into this?

Side note, I was a member of this forum for years, probably 10 or 20 posts or more during that time... but either i lost track of my old username or it may have been deleted. I haven't had any real involvement in Ubuntu & Linux in a couple years.

---

### Post by julianbrelsford on 2020-03-21
[https://scontent.fphl2-4.fna.fbcdn.net/v/t1.15752-9/90446728_225755031957217_4589752582519390208_n.jpg?_nc_cat=107&_nc_sid=b96e70&_nc_ohc=R1NhnFib00AAX-hPAFP&_nc_ht=scontent.fphl2-4.fna&oh=a39025c31fdbc9413ef7dfa02ac6d5bb&oe=5E9A9B1A](https://scontent.fphl2-4.fna.fbcdn.net/v/t1.15752-9/90446728_225755031957217_4589752582519390208_n.jpg?_nc_cat=107&_nc_sid=b96e70&_nc_ohc=R1NhnFib00AAX-hPAFP&_nc_ht=scontent.fphl2-4.fna&oh=a39025c31fdbc9413ef7dfa02ac6d5bb&oe=5E9A9B1A)

---

### Post by julianbrelsford on 2020-03-21
just to expand on this, i didn't succeed in getting Lubuntu Focal to work using dd OR unetbootin to create a live-USB either. Different error messages with each; with dd i got a message saying one file was corrupted after it had gotten as far as a black/white text covered screen with a mouse cursor i could move around ...and with a usb stick created by dd it was something about the kernel not being found (?)

---

### Post by wildmanne39 on 2020-03-21
Hello and welcome to the forum julianbrelsford, when posting terminal output instead of using an image post the test between code tags, the image is very hard to read.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, if you are editing a post to add code tags click the edit button then click the go advanced button, highlight the code then select the # symbol from the tool bar.

If you do post an image of something but not for terminal output of course please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by C.S.Cameron on 2020-03-21
You cant boot ISOs using grub 2.04.
You can build a System that uses grub 2.02, starting with mkusb.
See the following Note 1 for reference.
[https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-19-10-to-usb-device-step-by-step/1217839#comment2049271_1217839](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-19-10-to-usb-device-step-by-step/1217839#comment2049271_1217839)

Ubuntu 18.04 should also still work.

---

### Post by julianbrelsford on 2020-03-21
sorry, this was a computer crash / kernel panic. I did not have access to the text any way besides taking a photo of it with another device. CS Cameron thanks for the advice! I didn't realize grub 2.04 did not allow boot to ISO

---

### Post by C.S.Cameron on 2020-03-21
For reference see:
[https://askubuntu.com/questions/1216401/how-to-boot-an-usb-installer-iso-image-from-an-internal-ssd/1216479#1216479](https://askubuntu.com/questions/1216401/how-to-boot-an-usb-installer-iso-image-from-an-internal-ssd/1216479#1216479)

---

### Post by oldfred on 2020-03-21
See also bug report.
2.04 Out of memory error loop mount
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311)

Please add to it as the more that post that it applies the more likely someone will work on fixing it.

---

