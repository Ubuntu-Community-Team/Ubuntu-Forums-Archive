---
title: "vpn config help"
date: 2007-11-27
forum: Utah Team - US
---

### Post by Zelut on 2007-11-27
I'm trying to setup a VPN connection between my laptop and my office. We have some VPN config setup instructions on the office wiki, but they were written for the fedora guys there and don't seem to work on ubuntu.

What I've done so far is install the openvpn and network-manager-openvpn packages.  I've then configured via network manager > vpn to connect to the IP of the VPN server, using the default 1194 port.  I've imported the office .pem file and placed it into the /etc folder.  I've also included my username.  It prompts me for my password at connection and then errors saying:

Could not start the VPN connection 'Guru Labs' due to a connection error.  The VPN login failed because the VPN program could not connect to the VPN server.

If anyone has any ubuntu-specific suggestions, or other things you may have used for VPN connections on Ubuntu I'd love some.  Right now I'm running out of ideas.

---

### Post by stults on 2008-01-02
I'm having the same issue, but have not yet found any solution in the forums so far.  I have used the setup here:

[http://forum.openwrt.org/viewtopic.php?id=9689](http://forum.openwrt.org/viewtopic.php?id=9689)

I have had no luck in connecting.  It would make my life a lot easier if I could get this working.  Also, could someone please explain the ip address fields in the network manager vpn applet.  Thanks!

---

### Post by jkilgrow on 2008-06-13
I'm guessing you are talking about the "Only use VPN connection for these addresses" field?

If so, this is a space separated list of ip address ranges. This is so that the vpn will only try to use vpn connection for that particular ip address range. If you don't specify this network manager will try to use vpn for all your ip traffic. So, it will even try to use the vpn connection for things like [www.google.com](www.google.com), etc. This will result in your computer not being able to find that address. So you will be able to get into your vpn network and nothing else.

Let's say that the ipaddress range for the network that you want to vpn into is 128.132.10.1 through 128.132.10.100. You would put 128.132.10.1/100 in that field so that vpn is only used when trying to go to something in that ip range. If you have multiple ip adress ranges you would do this:
128.132.10.1/20 128.132.10.50/100.

I hope that helps.

Oh! By the way....I'm having the same difficulty. However, my problem is that I can connect via vpn fine at work but not from home.

Any suggestions there?

---

### Post by Castorpoluks on 2010-06-05
jkilgrow
Give me some closer informations mate.Are you have same OS on both computer company/home?

---

