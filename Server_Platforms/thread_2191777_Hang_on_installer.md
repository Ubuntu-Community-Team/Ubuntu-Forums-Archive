---
title: "Hang on installer"
date: 2013-12-04
forum: Server Platforms
---

### Post by joshua.reg on 2013-12-04
Dear All,

I am planning to install a VM Host with VGA passthought to a Guest VM.

I created a USB stick for Ubuntu Server 13.10 installation. 


However it "hang" on the language selection screen.


I guess the installer could not recognize the USB keyboard and mouse. 
How could I add the usb support into installer?


I am using Asrock FM2A85X-ITX, A10-5700. May be it is caused by AMD chipset?


Thank you very much.

---

### Post by joshua.reg on 2013-12-04
Do any one kindly give me a hints of solution?

---

### Post by nerdtron on 2013-12-05
No just you, I also have problems in 13.10 (Kubuntu) for not detecting keyboard and mouse. My problem wasn't solved though. But I suggest you try Ubuntu 12.04 LTS, it is supported until 2017 and it should be the first choice when it comes to server version (unless you want to wait for 14.04).

Anyway, just to make sure that the ISO or USB stick has the complete files, have you tried to install it on a different machine? It it also fails, then you should re-download or "re-burn" the ISO.

---

### Post by joshua.reg on 2013-12-05
> **nerdtron said:**
> No just you, I also have problems in 13.10 (Kubuntu) for not detecting keyboard and mouse. My problem wasn't solved though. But I suggest you try Ubuntu 12.04 LTS, it is supported until 2017 and it should be the first choice when it comes to server version (unless you want to wait for 14.04).

Anyway, just to make sure that the ISO or USB stick has the complete files, have you tried to install it on a different machine? It it also fails, then you should re-download or "re-burn" the ISO.

Thank you for the information. I am thinking it is my problem of lack knowledge but never though it is a unsolved problem.

I tried to re-burn the usb with different bootable USB creator but without any luck to detect the K/M.

Does the 12.04 support usb K/M at install time?
Since it will be my VM host.  I need 3.x kernel, I hope I will know how to upgrade it.

Thank you very much.

---

### Post by cariboo on 2013-12-05
Do you have a working network connection, and if so which mirror are you choosing during the install process?

---

### Post by joshua.reg on 2013-12-05
I download it from Server -> Overview ->Download Ubuntu Server -> Get Ubuntu 13.10.

It direct me to [http://www.ubuntu.com/download/server/thank-you?distro=server&bits=64&release=latest](http://www.ubuntu.com/download/server/thank-you?distro=server&bits=64&release=latest)
The image should be downloaded from [http://www.ubuntu.com/start-download?distro=server&bits=64&release=latest](http://www.ubuntu.com/start-download?distro=server&bits=64&release=latest)

---

