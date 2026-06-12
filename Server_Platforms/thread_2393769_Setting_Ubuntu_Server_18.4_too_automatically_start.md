---
title: "Setting Ubuntu Server 18.4 too automatically start VPN with my provider at boot."
date: 2018-06-07
forum: Server Platforms
---

### Post by daniel228 on 2018-06-07
Do any of you gyes know how to set my OpenVPN Connection too initialize upon booting my server.

I've tried:

sudo openvpn --daemon /etc/openvpn/"file name hear.ovpn"

I just cant seem to get it up and running with the CLI on Ubuntu 18.4 Server.

I've installed the "sudo apt-get install openvpn"  with out quotation .

Thanks Gyes in advance because this has really had me stressed getting my installation to were I need it too be.

---

### Post by darkod on 2018-06-07
The .ovpn file extension is usually used in Windows. In Ubuntu you need to call the configuration file .conf. Simply leave it in /etc/openvpn and it will start automatically on boot. If the file is correct...

You don't need anything else, just to have a .conf file in /etc/openvpn.

---

### Post by daniel228 on 2018-06-07
In /etc/openvpn/ I have all the .ovpn files from my VPN Provider. Their is about two or three dozen. Should I delete all of them except the one I would use for a 24 \ 7 connection.

What would the command be as when I previously tried to rename the files I got an error message.

What would the two commands be as I'm struggling to figure it out to rename the .ovpn and set it up too automatically start when I boot the server.

Thanks.

---

### Post by darkod on 2018-06-08
You need one file for each connection. I don't know how many connections you want to have. If only one needs to auto-start, then create just one .conf file. Otherwise all .conf files will start on boot so all connections will be 24/7. You can leave the rest with extension .ovpn or use something else, just not .conf

Depending who is the owner of the file you might need sudo rights to rename it.

---

