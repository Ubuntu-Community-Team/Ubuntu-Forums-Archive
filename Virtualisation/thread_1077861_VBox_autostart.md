---
title: "VBox autostart?"
date: 2009-02-22
forum: Virtualisation
---

### Post by ToshiBoy on 2009-02-22
I've got a Ubuntu 8.10/LAMP server installed in a VBox, which is running on a Ubuntu 8.04LTS machine. Works fine. However, when the server is rebooted, I need to manually log in, start VBox and then the webserver. 

I know how to set it up to start VBox and the image when I log into the server, but is there a way to set it up so that VBox and the image start automatically when the server is rebooted without having to log into the server?

Thanks.

---

### Post by bgates on 2009-02-22
System > Preferences > Sessions > Startup Programs > Add

VBoxManage startvm [name of your vm]

That should about do it I believe.

---

