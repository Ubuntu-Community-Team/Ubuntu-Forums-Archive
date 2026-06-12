---
title: "No realtime kernel in Xubuntu 8.1 but I installed it"
date: 2009-01-29
forum: Ubuntu Studio
---

### Post by pixelblip on 2009-01-29
Hi
I'm using XUbuntu 8.10 and wanted to install the realtime kernel so jack is realtime. I followed some instructions on the web:

sudo apt-get install linux-rt

And it said installing 50MB ....
When I rebooted and try to start jack with 'Realtime' ticked it won't start. 
Jack is starting without realtime ticked.

I've installed all the apps that come with Ubuntu studio ( there was a command I saw that installs them all in one go ) - this problem with Jack/no realtime was occurring before and after I installed the apps.....

Can anyone help? I'd love to get Xubuntu working with a real time kernel in Jack - it would rock. 
Thanks

---

### Post by kvk on 2009-01-29
When you boot, go into the GRUB menu by pressing Esc during boot. There you will see all the varous operative kernels listed, including the rt kernel. Select the rt kernel for boot and you should be good to go.

To make the rt your default boot choice, open:

/boot/grub/menu.lst

Set the default number to whatever corresponds to your rt kernel in the GRUB listing. You're set!

I have the rt kernel running on an Xubuntu 8.10 system as well, although I'm not running JACK on it.

---

