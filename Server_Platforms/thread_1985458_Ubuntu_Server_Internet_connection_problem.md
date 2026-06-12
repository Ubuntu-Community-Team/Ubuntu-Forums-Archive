---
title: "Ubuntu Server: Internet connection problem"
date: 2012-05-23
forum: Server Platforms
---

### Post by bikefreakvinnie on 2012-05-23
I have installed Ubuntu 12.04 server at home as a central file storage and it is working ok. The server is connected to the router with a network cable.

The only issue with it is that the server will not now connect to the internet (to install updates/programmes etc). It was connecting before I configured the server.


During the setup of the server I changed the IP address to a static IP and I wonder did I miss something along the way which has caused the internet connection problem.

Just in case this may not be it the other things which I did was:
-Edited the smb.conf file (to set up a directory)
-Edited the sshd_config file
-Edited the interface file (to change the IP address)

In editing the interface file I entered values for
address
netmask
gateway
Perhaps should I have entered broadcast and gateway as well?
Thanks for any help with this

---

### Post by bikefreakvinnie on 2012-05-23
I've since narrowed it down to my editing of the interface file to change the IP address...

& I tried with values added for broadcast and gateway into this file but to no avail.

Wonder is it a case of my internet service provider not allowing a static ip address access to the internet, the reason why i changed it was because i read that the ip was likely to change once in a while (ie if the server or router was rebooted etc) and that my saved connections to it on different computers would have to be adjusted ie change ip... Perhaps its unnecissary to change to a static ip at all?

---

### Post by bikefreakvinnie on 2012-05-27
Bump -any one got any idea about this -no prob if not i won't try again after this bump..

---

