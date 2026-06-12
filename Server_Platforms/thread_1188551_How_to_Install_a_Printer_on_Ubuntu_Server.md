---
title: "How to Install a Printer on Ubuntu Server"
date: 2009-06-15
forum: Server Platforms
---

### Post by 2quick on 2009-06-15
I have been looking for the very basic steps on how to install a printer on my linux server(9.04) so that I can then share it to a network of windows computers.  When I mention basic step I could use some help after plugging it in ;)  I have never installed a printer on manually before.  Thanks so much for the help!

---

### Post by HermanAB on 2009-06-15
Install CUPS and use the system-config-printer wizard.

---

### Post by cariboo on 2009-06-16
An even easier way to install your printer is to use the cups web interface. The first thing to do is make sure your printer is supprted. Check the [OpenPrinting Database]("http://openprinting.org/printer_list.cgi") first.

If your printer is supported, on your server open a web browser, if your running without a gui, elinks works quite well. With a gui open Firefox and in the address bar type:

```
http://localhost:631
```

See the attached screenshot to see what the interface looks like. Once you have the printer set up make sure you have **Share published printers connected to this system**
enabled.

---

### Post by ghen on 2009-06-16
Wow, thanks for the link to the OpenPrinting Database. I've been burned on drivers before so that's definitely a keeper.

---

### Post by 2quick on 2009-06-17
Thank you guys so much for the help!

---

