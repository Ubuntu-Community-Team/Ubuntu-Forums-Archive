---
title: "IP address"
date: 2011-07-07
forum: Server Platforms
---

### Post by thep8ntballfreak on 2011-07-07
i have set up a lamp server with samba installed, i also have webmin installed as im just getting used to this server stuff. when i type the ip address:port number it will take me to the machine that webmin is hosted on. however the name of the server is ubuntuserver and i would like to just be able to type ubuntuserver into the address bar and it take me to where i need to go. basically instead of typing 192.168.1.68 everytime i would like to be able to type ubuntuserver and it take me to the same place.

---

### Post by arrrghhh on 2011-07-07
Unless you have a lot of clients, its probably easiest to change the hosts file on the client computer.  Each client OS is different, for example Ubuntu is /etc/hosts.

Just put the IP then the hostname you want.  You have to update client machines manually, but if there's only 2-3 it's not a big deal because you'll only need to do it once.

---

### Post by thep8ntballfreak on 2011-07-07
im on windows vista and it worked for what i needed thanks for the information

---

