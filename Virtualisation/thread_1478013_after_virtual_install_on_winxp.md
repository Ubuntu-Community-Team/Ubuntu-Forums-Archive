---
title: "after virtual install on winxp"
date: 2010-05-09
forum: Virtualisation
---

### Post by harDRain on 2010-05-09
I just installed ubuntu on virtualbox as the os.  Winxp home edition is the physical computers os.  How can I get ubuntu to use our air card, printer, scanner and other things that are in the windows folders.  I thought there was some networking and sharing involved, but I can't seem to get it.  This is my first experience with Linux.  I installed Ubuntu 9.10. 
Thanks

---

### Post by cariboo on 2010-05-09
Make sure you have the guest additions installed in order to use the usb ports.

We have to know the make model and chipset of your network device, before we can help with that. If you don't know the details, go to Applications->Accessories->Terminal to open a terminal. At the prompt in the terminal type:

```
lspci
```

this will list all the devices connected to your system, look for you network device in the list.

---

### Post by cariboo on 2010-05-09
Moved to virtualization.

---

