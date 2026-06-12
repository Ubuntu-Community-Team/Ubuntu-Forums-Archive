---
title: "Watching TV in Virtualbox"
date: 2010-06-05
forum: Virtualisation
---

### Post by mahdif62 on 2010-06-05
Hi everybody
Currently the only reason I have to dual-boot is for watching TV as my usb tv card is not recognized by ubuntu. I installed virtualbox in ubuntu and installed widows 7 and then the drivers for the tv card. I used media center to scan for channels. All channels were found but when I click on a channel Media Center says "files required for playing video are not installed or don't work correctly". can anyone help me please. If I can solve this issue I can delete Windows and use only ubuntu.

---

### Post by howefield on 2010-06-05
If the device doesn't work in Linux, then it won't work in Virtualbox, as far as I know.

I had the same issue some time ago, and to be honest, the best solution was to buy a Linux compatible TV tuner and use it in Linux.

---

### Post by mahdif62 on 2010-06-05
You didn't read my post carefully. I installed it in windows (inside Virtualbox) and even it scanned and found the channels. I just don't have any picture.

---

### Post by howefield on 2010-06-05
I read your post very carefully, I had the same issue.

Period.

---

### Post by zappal on 2010-06-06
Is 3D or 2D rendering enabled?

---

### Post by mahdif62 on 2010-06-06
Yes, both are enabled.

---

### Post by littlepeon on 2010-06-06
k, first of all, howfield's response to you is correct. Virtualbox is not a native install of windows--everything virtualbox does acts THRU ubuntu/linux. If ubuntu/linux does not know how to correctly find/act with your device, it will corrupt the way that virtualbox/windows talks to the device.

That could be your main problem!!

Question though, you say you use 'media center to scan for channels'--what is this 'media center'? Is this 'media center' the cards software or something in windows?(we could help you more if you name the card/software used)

Knowing the tv-cards name would help here--we have all gone through the pain of getting hardware to work--and if given details we could share that experience/knowledge with you.

if it is some 'no-name' cheap foreign made card--do you know the chipset that the card uses to decode video? (normally that is given under device manager in windows, btw)

---

### Post by mahdif62 on 2010-06-06
First of all, thank you all for caring. My card is as you said is a no-name card but I have realized the chipset is Realtek. There's a method for installing it under linux but as I'm on dial-up I can't use that method (it's through bzr or something like that).
By media center I meant Windows 7's built-in Media Center.
As I said it even found the channels.

---

### Post by TheFu on 2010-06-06
Please specify the exact chips used in the tuner card if you'd like help. Use the `lshw` command to determine them. "Realtek" is not specific enough.

bzr is just a version control system, so dialup access doesn't prevent the use. In fact, you want the source since it will be much smaller than the compiled drivers to transfer.

I don't believe you'll be able to view TV from Win7 MC without direct access to the video card - ie. it won't work in any current virtualization tool. I think Win7 MC uses directshow to output video directly to the video card hardware efficiently. I could be wrong, I just know that 7MC video playback doesn't work with any remote protocol. You might ask your question in the card manufacturers support forums too.

However, you may be able to record the show in Windows, then play it back inside Linux after removing the WTV container from the files. Use the Shared Folder method to place the files on the host OS.

---

### Post by mahdif62 on 2010-06-06
Thank you, but I want live tv in linux. Attached is the output of lshw. The name of the chipset is rtl2832. I got the chipset name from the Windows driver cd that came with the tv card.

---

### Post by mahdif62 on 2010-06-06
Oops it was not attached.  Please find my hardware specs here: [http://pastebin.com/Wur3hgB5](http://pastebin.com/Wur3hgB5)

---

### Post by TheFu on 2010-06-07
> **mahdif62 said:**
> Thank you, but I want live tv in linux. Attached is the output of lshw. The name of the chipset is rtl2832. I got the chipset name from the Windows driver cd that came with the tv card.

There appears to be a Linux driver for rtl2832u and perhaps that is compatible with rtl2832?  [http://ubuntuforums.org/showthread.php?p=9319492](http://ubuntuforums.org/showthread.php?p=9319492) . 
There were links on google with "linux rtl2832" searches too. You probably already saw those, none jumped out to me as THE ANSWER, unfortunately. You are on a "quest", not just a quick 'apt-get install' I'm sorry to say.  Linux isn't loading a driver for the device (assuming it was plugged in when you did the `lshw`).  Hardware that is close will often work well enough, so be certain to search for other realtek tuner linux drivers.

This link has a conversation that looks promising [http://comments.gmane.org/gmane.linux.drivers.video-input-infrastructure/16914](http://comments.gmane.org/gmane.linux.drivers.video-input-infrastructure/16914)  the name of his device is "LeadTek WinFast DTV Dongle" - any device with "Win" in the name probably won't work so well with Linux.  Searching on that name + linux found [http://www.mythtv.org/wiki/Leadtek_Winfast_DTV_Dongle_Gold](http://www.mythtv.org/wiki/Leadtek_Winfast_DTV_Dongle_Gold)

You might check the LHC list [http://tldp.org/HOWTO/Hardware-HOWTO/](http://tldp.org/HOWTO/Hardware-HOWTO/) before purchasing hardware. We have all been get caught with some Windows-only hardware once or twice, then we learn to check the list going forward.

Good luck.

---

### Post by mahdif62 on 2010-06-11
Dear TheFu, your post intrigued me into making a second attempt, and this time I managed to install it using the driver from [http://www.turnovfree.net/~stybla/linux/v4l-dvb/lv5tdlx/linux_install_package_091207.rar](http://www.turnovfree.net/~stybla/linux/v4l-dvb/lv5tdlx/linux_install_package_091207.rar). Thanks a million. Now I have live tiv in linux. However, I have a strange problem with my usb tv dongle.  When I reboot it does't work. The modules are loaded as I understand from the "lsmod | grep dvb output", but vlc and othe programs can't play live tv. Also the "scan" command fails to tune to channels, saying "tuning failed". 
The only workaround I've found is rebooting into Windows 7 and opening live tv with Windows Media Center. Afterwards when I reboot back to linux tv works! I think I need a way to "reset" the dongle so that I don't have to reboot into Windows and back into linux. Can anyone please help me?

```
$ lsmod | grep dvb
dvb_usb_rtl2832u      126599  8 
dvb_usb                17567  1 dvb_usb_rtl2832u
dvb_core               85933  1 dvb_usb
```

```
$ dmesg | grep dvb
0......[   13.172804] dvb-usb: found a 'USB DVB-T Device' in warm state.
[   13.172810] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.176735] dvb-usb: USB DVB-T Device successfully initialized and connected.
[   13.176750] dvb-usb: found a 'USB DVB-T Device' in warm state.
[   13.176755] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.179271] dvb-usb: USB DVB-T Device successfully initialized and connected.
[   13.179292] usbcore: registered new interface driver dvb_usb_rtl2832u

```

---

