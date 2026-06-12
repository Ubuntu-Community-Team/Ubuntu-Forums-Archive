---
title: "Newbie Q: How to share USB printer with Ubuntu Server 16.04?"
date: 2017-04-28
forum: Server Platforms
---

### Post by paulgj on 2017-04-28
Hi, have a server up and running mostly sharing media but also running Samba shares.   I would like to share a Brother laser printer (USB) on my network and am having no luck getting anything seen by my Windows 10 laptop.

-I have plugged in the printer to a USB port on the server box
-Installed CUPS
-Made sure the SAMBA conf file specifies browseable and guest OK as described in this doc: [https://help.ubuntu.com/lts/serverguide/samba-printserver.html](https://help.ubuntu.com/lts/serverguide/samba-printserver.html)
-powered on the printer

No luck

I haven't been able to find any instructions related to setting up a shared printer from the server so any assistance would be welcome.

Thanks!

---

### Post by joedkoop on 2017-04-28
My best answer is to go the long way around.

Install LXDE (Its a lightweight desktop environment), and x11vnc (VNC server!)
You won't see any response by the terminal when you type your password but don't worry, it's working!
```
sudo apt-get install lxde x11vnc
```
You start LXDE with startx or something... (sorry)
And then play around with printers...

I won't be surprised if you don't like this answer.

---

### Post by SeijiSensei on 2017-04-28
Can you print directly to the printer from the server to which it is attached? From another machine on the network, go to [http://server_IP:631/](http://server_IP:631/), replacing "server_IP" with the server's IP address, and print a test page. Or find a simple text file on the printer and use "lpr /path/to/file.txt".

Does the printer have an Ethernet network port as many Brothers do?  If so, you'll be much better off plugging the printer into your hub or router and printing to it directly.  Give it a static IP address.  On my Brother, I had to do that from the setup menu on the printer itself.  Again if you use the CUPS web-based manager, it should detect the printer automatically if it's on the network.  Windows machines can use auto-discovery as well.

---

### Post by paulgj on 2017-04-28
Thanks for the responses, I tried accessing the server using port 631 but there was no response, am guessing CUPS needs some additional tweaking beyond just doing the install, i'll play around with the /etc/cups/cupsd.conf file.

---

