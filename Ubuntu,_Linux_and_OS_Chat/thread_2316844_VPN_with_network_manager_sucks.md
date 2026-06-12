---
title: "VPN with network manager sucks"
date: 2016-03-11
forum: Ubuntu, Linux and OS Chat
---

### Post by pgib8 on 2016-03-11
I'm not so much looking for help, this is a negative feedback. I'm trying to connect to a VPN and most resources talk about using the network manager. I've done everything it says, including chopping up the .ovpn file. After I'm done, I click on the VPN connection and it immediately receives a check mark. That's all the feedback that I get. It doesn't say "you're connected", it doesn't say "connection failed". There is no feedback at all, it's like it does nothing.
If I do the same thing on my beloved Windows machine, using the ovpn client, everything works great and there is plenty of feedback for me to see what's going on, up to an icon that turns green when the connection is successful.

On Ubuntu the documentation says "It will try to establish a VPN connection - the network icon will change as it tries to connect."
I do not see anything changing, like I have no idea what it's doing or trying to do.

Please dear Ubuntu developers, improve the VPN functionality.

PS: If anybody knows a great VPN client that I can use instead of network manager, please let me know.

---

### Post by pgib8 on 2016-03-11
Here is a quick solution via terminal that worked for me. I already had openvpn installed but if you don't, type:
sudo apt-get install openvpn

Then cd to the directory where your .ovpn file is located. Now type:
sudo openvpn --config yourfile.ovpn

It worked really well and my public IP now shows up as if I was at the remote location.

---

