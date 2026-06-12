---
title: "Ubuntu 16.04 Server on HP MicroServer Gen8. No display!"
date: 2016-07-03
forum: Server Platforms
---

### Post by AnWi on 2016-07-03
I really thought I had a boot-problem when I installed Ubuntu 16.04 64-bit Server on a HP MicroServer Gen8, with software RAID, as the display turned black after reboot. Many installation attempts later and after using the boot rescue tool I found that the server actually boots but absolutely nothing shows on the terminal.
Installing Webmin helps me manage the server so now it not a big issue to me but maybe for others using this relatively handy and nice server.

Thanks
Anders Wikström
Sweden

---

### Post by MAFoElffen on 2016-07-03
It's because of the Matrox MGA G200 GPU that that server has. It is sort of non-standard ... and even though HP said that server was fully supported by RHEL (Red Hat), Red Hat had problems with that GPU also. Even though Server is thought to be a Text console (CLI), it is actually a virtual tty console displayed in VGA graphics.

Fix would be to get to your Grub menu... default at install is to only show that menu for 2 seconds, so > At the end of the BIOS messages, start intermittently pressing the <left-shift> key.  > When the menu displays, quickly press the <down-arrow>. Once a valid key is pressed (in this case the <down-arrow>) the menu timeout timer stops. If you miss that, reboot and try again!

<up-arrow> back to the first menu item. > Press <E> to get into Edit mode. In the menu item edit pane, <down-arrow> down to the line that starts with "linux".

<right-arrow> to the end of that line. If it has the text "quiet", remobve that. At the end of the line, append the text
```

debug --verbose text

```
Press <Cntrl><X> to boot... It will flash many, detailed boot messages and show end up at a large sized text console without any video enhancements at all.

Login with your credentials. Start an editor to edit file /etc/default/grub:
```

sudo vim /etc/default/grub

```
edit the kernel boot option line to reflect this:
```

nomodeset video=uvsesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap,noedid

```
If you know the device name (VGA-x, DVI-x, etc.) of the graphics port you are connected to and only want to set that port to a mode, then you could alternately change that line to 
```

video=VGA-0:1024x768-24@60

```
You can also change the resolution to what you want it to be via that line. That CPU does better, but it depends on the attached display and your eyes.... I would also change the timeout to 4-5 seconds. Only adds 2-3 seconds to the bootup time, but easier to maintain if you do...

Save and Exit. Then pick up the changes in Grub. And reboot.
```

sudo update-grub
sudo shutdown -r now

```
Tell me how it goes, or if you have questions.

---

### Post by AnWi on 2016-07-03
Thank you for your quick reply.
I will certainly test this later this week when I'm back

Thanks
Anders

---

### Post by MAFoElffen on 2016-07-03
No problem. I have to do on some of my servers here. My HP TFT5600RKM console (rack mount display-keyboard-mouse module) connected through KVM, is touchy about what it is connected to. So, unfortunately, I have lots of practice at that tweak.

I'll follow the thread and see how it goes for you.

---

### Post by dulinux on 2017-01-03
Hello: for the HP Proliant Microserver Gen8 G2020T adding just "nomodeset" to the linux line will fix the black screen problem. Thanks.

vim /etc/default/grub:

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

And then:

sudo update-grub
sudo init 6

---

