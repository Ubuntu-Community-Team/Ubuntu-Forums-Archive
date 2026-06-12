---
title: "Virtualbox 1.6.2 and 1280x800 resolution?"
date: 2008-06-14
forum: Virtualisation
---

### Post by Tridion2000 on 2008-06-14
I've been using VMWare Server on Ubuntu 8.04 but getting a little bit disappointed with some things. So I decided to try Virtualbox and downloaded the 1.6.2 deb from their site.

I've now installed a XP Pro SP3 virtual machine. To start with it would only give me 4:3 resolutions. So I installed the guest additions and then only got 640x480 and 800x600 options. I read somewhere about this command line:

 VBoxManage setextradata global GUI/MaxGuestResolution 1280,800

This now gives me an additional 1024x768 option but still no 1280x800 option.

Has anyone had a similar problem and/or knows how to fix it?

---

### Post by techstop on 2008-06-14
I run that resolution an a Dell laptop, and it works fine for me with a Windows XP guest on VirtualBox. I haven't had to run any command line commands either.

From your guest OS window, click the "Machine" menu and then select "Auto-resize guest display". Then go fullscreen (Right Ctrl + F) and you should get 1280 x 800 on your guest. HTH.

---

