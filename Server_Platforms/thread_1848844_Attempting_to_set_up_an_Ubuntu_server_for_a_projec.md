---
title: "Attempting to set up an Ubuntu server for a project at my school. Need serious help."
date: 2011-09-23
forum: Server Platforms
---

### Post by danielelicker on 2011-09-23
We have an Ubuntu 11.04 server in our class, and we need to connect it to eight computers running Windows 7 to it in order to share a single folder. Our teacher is too busy to help us with it, we could use some serious help with this project. Step by step instructions would be greatly appreciated. Thank you.

---

### Post by dozycat on 2011-09-23
just install the server, and install sambax. Configure it.

[http://www.unixmen.com/linux-tutorials/1060-how-to-configure-samba-using-a-graphical-interface-in-ubuntu]("http://www.unixmen.com/linux-tutorials/1060-how-to-configure-samba-using-a-graphical-interface-in-ubuntu")[http://www.unixmen.com/linux-tutorials/1060-how-to-configure-samba-using-a-graphical-interface-in-ubuntu](http://www.unixmen.com/linux-tutorials/1060-how-to-configure-samba-using-a-graphical-interface-in-ubuntu)

In a terminal type:
sudo smbpasswd -a userusedtoconnecttosambafromother machine

and type a newpassword.

Now you can navigate from the other machines to the server.

---

