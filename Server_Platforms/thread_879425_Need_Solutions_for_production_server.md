---
title: "Need Solutions for production server"
date: 2008-08-04
forum: Server Platforms
---

### Post by anindya23 on 2008-08-04
Hello,
      i am a noob at Ubuntu and also linux. I want to set up production web server on Ubuntu Server Edition.At server i'll put my php files which i can access intranet and also Internet.
      All pcs connected to this network is running on windows except Server.That means,there must be options to access server from windows machine(i'm not interested to use Remote Desktop) to transfer php files to server and access the web site using it's IP address.
      Moreover Server uses real ip and has 2 NIC card.One for internet and another for local.

      Can anyone tell me what exactly i have to do to set up this Server in a sequential order(i.e Step by step) plz?I have only 2days in my hand to do this.

      Thanx in advance.

---

### Post by windependence on 2008-08-04
OK, to transfer files to the Windoze boxen, I would suggest WinSCP. 

You may want to consider installing SAMBA if you want to access shares on your server from the Windows boxes. 

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

I'm not exaclty sure what you are going to do with this box so if you can give me a bit more info I can point you in the right direction. Is it going to be a webserver accessible from the outside? If so, are you behind a router and do you have a static external IP address?

If you can gove me the info above and a bit more about what you want to accomplish, I can help you get started. :)

-Tim

---

### Post by anindya23 on 2008-08-04
thanx. yes it is going to be a webserver accessible from the outside and also intranet.

"Moreover Server uses real ip and has 2 NIC card.One for internet and another for local." plz consider this while networking.

and plz tell me i there any need to raid(Software or Hardware) configuration?

> If so, are you behind a router and do you have a static external IP address?

Yes i'm behind a router and have a static external IP address.

I need step by step solution plz and if anything more you need to know plz ask me.I'll try my best to help you for understanding my requirements.Thanx once again.

---

### Post by windependence on 2008-08-04
OK sorry, skimmed over the "real IP" thang. :)

Here are afew tutorials. The Perfect Server tutorial is good, but I just want to add that you do NOT need a DNS server (bind9), proftp or ISPConfig to run your site. Some people may also tell you you need RAID, but that is your choice, and for a small site it would be more trouble than it's worth.

[http://theubuntublog.wordpress.com/2008/02/07/setting-up-a-webserver-in-ubuntu/](http://theubuntublog.wordpress.com/2008/02/07/setting-up-a-webserver-in-ubuntu/)

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

[http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html)

-Tim

---

