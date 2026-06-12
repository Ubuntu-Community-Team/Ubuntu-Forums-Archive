---
title: "Can I use gotomypc (remote access) with virtual Windows?"
date: 2015-10-29
forum: Virtualisation
---

### Post by AbleTassie on 2015-10-29
Can I use gotomypc (remote access) with virtual Windows XP or other virtualized Windows using virtualbox? That is, can I access virtualized windows on ubuntu (host) from another machine? The gotomypc website says it works for Windows, Mac, iOS, Android and Kindle; See [http://www.gotomypc.com/remote-access/](http://www.gotomypc.com/remote-access/)

Thanks,

A.

---

### Post by TheFu on 2015-10-30
Don't know about this, but I remote into my Linux systems from around the world using ssh and x2go.
[https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative](https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative)
Those instructions use a different account.  Not necessary. Use the normal account.

This can be used to connect to any Linux desktop on the same subnet, then "hop" to any other computer on the same subnet easily and securely. For example, I have a win7  media center VM and use RDP from a Linux desktop to access it.  That Linux desktop runs x2go-server and is available from anywhere with an internet connection in the world. I've used this from 5 continents. [http://blog.jdpfu.com/2012/10/23/remote-desktops-rock](http://blog.jdpfu.com/2012/10/23/remote-desktops-rock) explains.

---

### Post by SeijiSensei on 2015-10-30
You'll need to tell VirtualBox to use a "bridged adapter" rather than "NAT".  With bridging the VM is directly on the same network as the host computer.  With NAT it will be "behind" the host and not easily manageable remotely.  

In the VirtualBox manager, right-click on the VM you wish to use and choose Settings.  Then in the Network tab you'll see a drop-down box for the adapter called "Attached to".  Choose "Bridged".

---

### Post by AbleTassie on 2015-11-01
Thanks Fu and Seiji,

Just one more question. Have you ever used Teamviewer? See [https://www.teamviewer.com/en/index.aspx](https://www.teamviewer.com/en/index.aspx)

Thank you, I will mark this thread as SOLVED

A.

---

### Post by TheFu on 2015-11-01
Nope.  F/LOSS, it is a lifestyle,  not just an acronym.  ;)

---

### Post by AbleTassie on 2015-11-10
Thanks,

A.

---

