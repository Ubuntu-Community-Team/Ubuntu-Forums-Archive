---
title: "How secure is a shared printer?"
date: 2016-11-29
forum: Security
---

### Post by Bob_Younkin on 2016-11-29
I do tech support for a volunteer organization that does incomes taxes for seniors and the.economically disadvantaged.  The software is cloud based, so our computers are basically internet appliances.  We frequently find ourselves in Senior Centers or Libraries where the only internet access is unsecured wi-fi.  We generally try to set up a repeater to put our network behind our own firewall, but increasingly these public networks are blocking our ad hoc networks.

The IRS is satisfied with the security that our TSL connection with the software server provides, but only if the tax forms are printed to a local printer.  The IRS deems shared Windows printers as insecure.

If we use Ubuntu machines, can we set up a secure way to share printers over an otherwise unsecure network?

Bob

---

### Post by kpatz on 2016-11-29
> **Bob_Younkin said:**
> The IRS deems shared Windows printers as insecure.Does the IRS also consider networked printers to be insecure?  If not, connect a network printer to the network and print to it from any OS.

Otherwise, you'll have to connect the printer directly to a machine and do all printing from there.

Can you use a VPN rather than an "ad hoc network" to access your network/firewall?

---

### Post by HermanAB on 2016-11-30
The IRS is concerned about other people viewing the printed forms - physical security.  Therefore the printer must be right next to the user.

My question is why print the forms at all?  Save the trees!

---

### Post by SeijiSensei on 2016-11-30
If you can download a PDF version of the documents, send them to a local machine and use its printer.  You'll presumably be moving the PDF over an HTTPS connection, so that preserves their security.

If the issue is physical security of the printer as Herman suggests, then printing to a desktop printer connected via USB or serial, or to a nearby networked printer in full view, are the only options.  Printing to a networked printer in another room probably violates the spirit and maybe the law of the regulation in force. If you cannot rely on there being such a local printer at the locations you serve, you'll probably need to bring your own like maybe [this Canon]("http://www.newegg.com/Product/Product.aspx?Item=9SIA4P02CG5977") with the wireless receiver turned off, of course.

Whether you use Ubuntu, Windows, OSX or something else doesn't really matter in this model.

---

