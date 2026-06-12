---
title: "Setting up a printer server"
date: 2023-02-24
forum: Server Platforms
---

### Post by actavis on 2023-02-24
Do I use Cups or Samba or both?

---

### Post by slickymaster on 2023-02-24
Thread moved to **Server Platforms** for a better fit

---

### Post by SeijiSensei on 2023-02-24
Both. Set up the printer in CUPS and make sure you can print to it. Then install Samba if you need to support Windows clients. Linux clients should see the printer automatically.

---

### Post by actavis on 2023-02-24
Ok thanks.

---

### Post by mIk3_08 on 2023-02-24
If your printer/scanner is connected directly from your router. I think, you'll never need to install samba or anything to be found the printer/scanner using any operating system. I do have network printer/scanner and it is installed directly to my local router and its working to any kind of operating system as long as the pc unit is connected to the router. Regards and cheers.

---

### Post by volkswagner on 2023-03-08
I've used [this guide]("https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint") with great success, including Airprint (using
a usb only printer).

---

### Post by mIk3_08 on 2023-03-09
> **volkswagner said:**
> I've used [this guide]("https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint") with great success, including Airprint (using
a usb only printer).

On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

