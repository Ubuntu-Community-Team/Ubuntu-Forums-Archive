---
title: "new dell inspiron no Wifi detected (no eternet card installed)"
date: 2016-11-07
forum: Ubuntu/Debian BASED
---

### Post by pascale64 on 2016-11-07
Please help,
I have received for my birthday a brand new dell inspiron 15 3000 3552
with Ubuntu installed.
on  my old net book I had #! loved it, so i installed #! on the new one,  same problem no wifi, followed numerus leads, no result, so decided to  install Hydrogen,
during installation no ethernet card was detected,  no ethernet card installed so no problem, but after installation I have  the same problem, the wifi card is not detected 

Dell Wireless 1707 Card (802.11BGN + Bluetooth 4.0, 2.4 GHz)
I have spoken to dell but they do not support ubuntu

I have internet access on my old notebook but not on the new machine.
I have tried following the link [http://ubuntuforums.org/showthread.php? … st12762259]("http://ubuntuforums.org/showthread.php?t=2168816&p=12762259#post12762259") but no luck 

Can any body help??
Please!!!!
And save my birthday (today)
 					
 				 			 		 		 			 				**Online**

---

### Post by jeremy31 on 2016-11-07
Check results for ```
lspci -nnk | grep -iA2 net
```
Some reports indicate that this wireless is a Qualcomm Atheros 9565.  Also check ```
rfkill list all
```
See if there are any blocks that report yes

Welcome to the forums, happy birthday

---

### Post by pascale64 on 2016-11-07
Thanks for your reply, 
I tried lspci -nnk | grep -iA2 net
This gave no reply at all
I tried "rfkill list all"
This gave "0: hci0: bluetooth
                      soft blocked: no
                      hard blocked: no"

And that is it
regards Pascale

---

### Post by ajgreeny on 2016-11-07
Are you aware that #! has been discontinued, and is therefore unsupported now; could be a security risk to you.

There may be other, and possibly better, distros for you to use than #! in view of this current situation, but with no real info so far about the hardware it is difficult to give you recommendations.

Run command ```
sudo lshw >hw.txt
``` and copy the hw.txt which will be in your home folder, back here in a reply, using code tags for clarity, see Code-Yags in my signature for a How-To, or attach it using the paperclip icon in the toolbar above, (if using Quick Reply go to the Go Advanced box.)

---

### Post by howefield on 2016-11-07
Moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by pascale64 on 2016-11-07
Thank you for your reply,
This is a brand new computer pre instaled with ubuntu 14,04 [http://www.dell.com/fr/p/inspiron-15-3552-laptop-ubuntu/pd?oc=cn55220&model_id=inspiron-15-3552-laptop-ubuntu](http://www.dell.com/fr/p/inspiron-15-3552-laptop-ubuntu/pd?oc=cn55220&model_id=inspiron-15-3552-laptop-ubuntu)
There is no ethernet card so all downloads must use my old out dated computer
555-BBTT : Dell Wireless 1707 Card (802.11BGN + Bluetooth 4.0, 2.4 GHz)
in terminal I have tried the following
```

lspci -nn gives
"pascale@pascale:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:2280] (rev 35)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:22b1] (rev 35)
00:0b.0 Signal processing controller [1180]: Intel Corporation Device [8086:22dc] (rev 35)
00:13.0 SATA controller [0106]: Intel Corporation Device [8086:22a3] (rev 35)
00:14.0 USB controller [0c03]: Intel Corporation Device [8086:22b5] (rev 35)
00:1a.0 Encryption controller [1080]: Intel Corporation Device [8086:2298] (rev 35)
00:1b.0 Audio device [0403]: Intel Corporation Device [8086:2284] (rev 35)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:229c] (rev 35)
00:1f.3 SMBus [0c05]: Intel Corporation Device [8086:2292] (rev 35)
pascale@pascale:~$ "

```
I hope that some of this helps
the txt doc is attached as it is 361 lines long
When I open Ubuntu the icon for internet  displays a message that the network card is not available( I can attache a screen shot but my computer is set up in french)
The bluetooth icon works and it is possible to find other bluetooth devices like phones.
regards
paul

---

