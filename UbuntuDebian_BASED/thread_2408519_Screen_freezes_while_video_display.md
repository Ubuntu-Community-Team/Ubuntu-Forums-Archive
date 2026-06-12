---
title: "Screen freezes while video display"
date: 2018-12-19
forum: Ubuntu/Debian BASED
---

### Post by jossysola on 2018-12-19
Hello, I’m new to Ubuntu. I’m currently using a new desktop computer and when I tried to open the League of Legends website my screen completely froze so I had to turn it off. Today I tried to visit Youtube in the browser and the same happened. I suspect it has to do with video displaying because LoL website tends to have videos and gifs around it and when I opened Youtube the video commercial on the main page was about to start when it froze.

My system specifications are the next:
elementary PS 5.0 Juno (64-bit)
Linux 4.15.0-42-generic
GTK+ 3.22.30
Intel core i5-8400 2.80GHz
NVIDIA GTX 1050 ti
16GB RAM
255 GB Storage

It is important to highlight that I built this computer on my own, so there’s a probability that it has to do with the hardware.
also note that currently, my mother board has a red light above the following text: “pwr_led”

Beforehand, thank you.

---

### Post by deadflowr on 2018-12-19
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by Autodave on 2018-12-19
What motherboard are you using?  Did you install any driver for the Nvidia card?  If so, what one and where did you get it from?

---

### Post by jossysola on 2018-12-19
I&#8217;m using  [COLOR=#111111][FONT=&amp]ASUS Strix Z370-E Gaming Motherboard. I tried installing a program called Aorus Graphic Driver and a driver from the Geforce website. However, both are meant for Windows because they have .exe extension. Neither of both worked. I do have some CDs for installation but I don&#8217;t have a CD reader. I don&#8217;t know if there are any drivers for linux based systems.

**EDIT**: I found a driver called &#8220;Linux x64 (AMD64/EM64T) Display Driver&#8221; in the geforce website. Is the only one that pop up when searching drivers for linux. However I&#8217;m getting an error when executing from terminal. The message is the next: &#8220;You appear to be running an X server; please exit X before installing. For further details, please see the section INSTALLING DRIVER in the README available on the Linux driver download page at [www.nvidia.com&#8221;]("http://www.nvidia.com&#8221;"), press enter and this is next: &#8220;Installation has failed. Please see the file &#8216;/var/log/nvidia-installer.log&#8217; for details.

**EDIT** **2**: I&#8217;ve been trying to do these steps from this site: [https://askubuntu.com/questions/149206/how-to-install-nvidia-run](https://askubuntu.com/questions/149206/how-to-install-nvidia-run), but I had no luck from the first step.

**EDIT** **3**: I managed to do the steps from edit 2. Now other errors appear. Something about Nouveau kernell driver being installed and not being compatible with the one I&#8217;m trying to install and it should be disabled before proceeding to install the one I want.
**EDIT 4**: I followed these steps [/FONT][/COLOR][https://askubuntu.com/questions/841876/how-to-disable-nouveau-kernel-driver](https://askubuntu.com/questions/841876/how-to-disable-nouveau-kernel-driver), didn&#8217;t work and made my screen resolution look worse.
[COLOR=#111111][FONT=&amp]**EDIT 5**:I&#8217;m formatting my computer and reinstalling the OS, this is too much for the first day using Linux.
 
**As for the red light above &#8220;pwr_led&#8221; I found out it is supposed to tell you the motherboard is on.*[/FONT][/COLOR]

---

### Post by jossysola on 2018-12-19
Now I&#8217;m stuck with this: &#8220;Executing &#8216;grub-install/dev/sdb&#8217; failed. This is a fatal error&#8221;, I can&#8217;t even format my computer jeez
[B]
EDIT 1: [/B]I formatted my computer once again and this is what I did:
             Once the installation was done, I declined ALL the updates and left them in &#8220;stand by&#8221;. None of the drivers downloaded 
             from Nvidia or Geforce worked. So I used the Terminal and these commands in the following order:
             [I]$ sudo apt update
             $ sudo apt install nvidia-[COLOR=#ff0000]*see notes below*
[/COLOR]             $ sudo add-apt-repository ppa:graphics-drivers/ppa

             [/I]Then I downloaded &#8220;Software & Updates&#8221;, went to &#8220;Additional Drivers&#8221; and marked the one I wanted instead of the       default one (X.Org, X server). I clicked Apply Changes and rebooted.
[COLOR=#ff0000]*NOTE: In this space goes the version you want to install. I suggest going to NVIDIA or Geforce websites to see which is the most recent one. For example, if the version is 4.10.73, then you are going to write in this space 410.[/COLOR]

---

