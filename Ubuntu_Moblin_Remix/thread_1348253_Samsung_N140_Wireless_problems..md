---
title: "Samsung N140 Wireless problems."
date: 2009-12-07
forum: Ubuntu Moblin Remix
---

### Post by dmedine on 2009-12-07
I have installed Ubuntu remix 9.10 on my girlfriend's new netbook and surprise, surprise, wireless doesn't work. I have got ndiswrapper to use the windows driver (32 bit, just like it should be) for the Realtek wireless hardware that comes with the machine, but the computer still won't see the hardware. I have been through many angles on this and not found the solution. If I have to reinstall Windows 7 she will break up with me for sure! So far I haven't seen any threads about this problem specifically. Anybody know the answer?

---

### Post by blazemore on 2010-01-12
> surprise, surprise, wireless doesn't work.

There's no need to be like that.

Are there any updates on this issue, as using ndiswrapper only works for a few minutes before giving up.

---

### Post by helliewm on 2010-01-12
This works for the N140 too. See this thread [http://ubuntuforums.org/showthread.php?t=1321340&page=2]("http://ubuntuforums.org/showthread.php?t=1321340&page=2") 

I have also posted the solution below:

o compile the Realtek driver. I am using Karmic Netbook Remix UNR

Download driver from here [http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz](http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz)

[http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz](http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz)

On Netbook Remix it should download into your Download folder. Go to your Download folder and Extract the file. Click on it, it will open then click Extract.

Open the Terminal and Change Directory to Extracted File by typing this into the Terminal

cd Downloads/rtl819Xe

Next in the Terminal type

sudo su

./install.sh

Ignore any error messages it will say kernel mismatched 5 times.

Your wifi driver on the N130 should now work. The above was adapted from this thread [http://ubuntuforums.org/showthread.php?t=1329254&page=2](http://ubuntuforums.org/showthread.php?t=1329254&page=2)

Hope this helps. It worked first time on my N130.

Helen
RE my instructions above if the wifi driver does not load at start up open up the Terminal and type the following:

sudo gedit /etc/modules

Type in your password

A text file with appear add the following line:

r8192_pci

and SAVED IT.

Reboot and your wifi will start or alternatively to save rebooting in the Terminal type:

sudo modprobe r8192_pci

This command simply restarts your wifi and Text file where you added the line r8192_pci (as the instructions above) restarts wifi every time you reboot

I have tried this myself.

Any queries leave a post or PM me and I will try to help.

Helen

---

### Post by blazemore on 2010-01-12
Whoops, I'm already compiling the kernel with support built in!
Still, yours it probably better.

---

### Post by freeflyer52 on 2010-03-27
Hi complete novice to unbuntu and linux.Using netbook remix from a usb stick on my np-n140 samsung.Thanks to your instructions i now have the wireless up and running.the only problem is saving the settings.Just a little confused with adding the lines r8192_pci and SAVED IT. How are they typed?.Two seperate lines? leaving the and out?.As i said a complete novice here but learning quickly..

---

### Post by blazemore on 2010-03-27
> **freeflyer52 said:**
> Hi complete novice to unbuntu and linux.Using netbook remix from a usb stick on my np-n140 samsung.Thanks to your instructions i now have the wireless up and running.the only problem is saving the settings.Just a little confused with adding the lines r8192_pci and SAVED IT. How are they typed?.Two seperate lines? leaving the and out?.As i said a complete novice here but learning quickly..

SAVED IT is just bad English (sorry helliewm!)
(s)he means save the file after you add that line.

---

### Post by freeflyer52 on 2010-03-28
Thanks Blaze

---

