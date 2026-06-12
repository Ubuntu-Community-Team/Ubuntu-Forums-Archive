---
title: "HOWTO: Run Ubuntu Server under VirtualBox (without changing the kernel)"
date: 2008-05-07
forum: Server Platforms
---

### Post by knorr.orange on 2008-05-07
As many people know, the standard Ubuntu Server install will not boot in a VirtualBox VM.  This is/was because VirtualBox lacked PAE support.  I have just tried out the new (as of this post at least) version of VirtualBox and it now has PAE support available.  The version is 1.6.0 and can be found here (no repo for it yet):
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

The only thing you need to know (aside from how to use VirtualBox in the normal way) is that when making the virtual machine you should look for PAE support.  You can find it in settings, in the "General" section and then in the "Advanced" tab.  Click the checkbox for "Enable PAE/NX" and you're good to go.  Booting without that option will give crazy errors in previous VirtualBox versions and in 1.6.0 it will at least give a friendly message explaining that the feature is not there.

So the point here is to make sure that box is checked before expecting your Ubuntu Server VM to boot.

Hope this helps someone.

---

### Post by ckasprzak on 2008-05-16
Thanks, that helped me out!  Was wondering why I couldn't boot my server vm and was able to boot the desktop vm.

---

### Post by mediajunkie on 2008-07-30
Thanks,

I have to try that. 

My setup:

Toshiba notebook with dual boot Win XP and Ubuntu 8.04
In the main partition, Ubuntu; I have Virtual box running 2 windows versions perfectly. 
Now, I wanted to run a virtual Ubuntu-server too so I can do all my development on one machine without having to reboot.


mmm while typing this, my install ended but unfortunately with the same error message:


> This kernel requires the following features not present on the cpu: 0:6
Unable to boot - please use a kernel appropriate for your cpu. 

Any Ideas??

---

### Post by falinx on 2008-09-05
I just wanted to say thank you very much for this as this was the error I was getting!! You're the king dude !!! :)

---

### Post by grg3 on 2008-10-24
Thanks! That was a great help.

---

### Post by kazak_vmik on 2009-02-28
Thank you very much! I solved my problem with error in VirtualBox xVM 2.1.4 "please use a kernel appropriate fro your CPU".

**Solution:**
In Settings of current virtual machine check check-box
**"Settings->Advanced->Enable PAE/NX"**

---

