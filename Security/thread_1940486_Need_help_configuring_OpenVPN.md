---
title: "Need help configuring OpenVPN"
date: 2012-03-13
forum: Security
---

### Post by Riothamus on 2012-03-13
Okay so I signed up for OpenVPN, which works fine on Windows. But my reason for using it is that this guy is trying to hack me, so I'd rather use it on Ubuntu, which is more secure than Windows. But it's a lot more difficult to set up on Ubuntu. On Windows, all I had to do was install their MSI file and then click connect. I installed the openvpn deb package on Ubuntu, but when I try to run it, it wants all these configuration options that I don't know what to put for.

Is there any simple way of getting OpenVPN to work on Ubuntu?

---

### Post by Riothamus on 2012-03-13
Okay, I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=1881124](http://ubuntuforums.org/showthread.php?t=1881124)

But they aren't working. When I try to connect, it just says the connection to PrivateTunnel failed, and I've tried doing it both solo and while logging into PrivateTunnel via their website. One thing I noticed is that the instructions say that on the Advanced tab, Use custom gateway port should be checked and set to 1194, but when I click OK and then click Advanced again, it's unchecked by itself. It seems like that's not a valid option. The same thing happens with Use custom renogotiation level, and it sets that back to 10,000 because it seems like that's the maximum allowed, not the 604800 that the instructions say.

Any ideas?

---

### Post by xenon87 on 2012-07-07
To get this to work for me I had to copy out the "remote" field from the .ovpn file downloaded from PrivateTunnel and use it instead of the one supplied in the tutorial. Works like a charm now.

I too see the box is unchecked, however when I look in the actual configuration file (located in /etc/NetworkManager/system-connections/[name-of-connection]) the field was indeed set so I assume that's some kind of bug.

---

### Post by samiux on 2012-07-08
> **Riothamus said:**
> Okay so I signed up for OpenVPN, which works fine on Windows. But my reason for using it is that this guy is trying to hack me, so I'd rather use it on Ubuntu, which is more secure than Windows. But it's a lot more difficult to set up on Ubuntu. On Windows, all I had to do was install their MSI file and then click connect. I installed the openvpn deb package on Ubuntu, but when I try to run it, it wants all these configuration options that I don't know what to put for.

Is there any simple way of getting OpenVPN to work on Ubuntu?

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install network-manager-openvpn
```

Then configure the OpenVPN under the Network Manager.

Samiux

---

### Post by tehowe on 2012-07-10
This is the procedure I followed to get it working. There's a bug in network manager where it doesn't do ovpn import properly - since 2010 (!)

[https://bugs.launchpad.net/ubuntu/+s...pn/+bug/606365]("https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/606365")

Until that's fixed, I found this site

[http://howto.praqma.net/ubuntu/vpn/o...ient-on-ubuntu]("http://howto.praqma.net/ubuntu/vpn/openvpn-access-server-client-on-ubuntu")

PROCEDURE

Create a new folder in your home dir - I called mine vpn.config
Copy your downloaded client.ovpn file into the new folder

Open client.opvn in an editor

Open a new file
Cut the lines between <ca> tags in client.ovpn
Paste into new file, save this file as ca.crt
Remove both <ca> tags from client.ovpn

Open a new file
Cut the lines between <cert> tags in client.ovpn
Paste into new file, save this file as client.crt
Remove both <cert> tags from client.ovpn

Open a new file
Cut the lines between <key> tags in client.ovpn
Paste into new file, save this file as client.key
Remove both <key> tags from client.ovpn

Open a new file - this is the last one :smile:
Cut the lines between <tls-auth> tags in client.ovpn
Paste into new file, save this file as ta.key
Remove both <tls-auth> tags from client.ovpn

And remove this line:
key-direction 1


Now position the cursor in client.ovpn, right above the line # -----BEGIN RSA SIGNATURE-----

Insert the following lines

ca ca.crt
cert client.crt
key client.key
tls-auth ta.key 1

Save and close all the files.

Goto Network Manager -> Edit Connections ->VPN
click Import, browse to the modified client.ovpn in the folder you  recently created - and where your certificates are, and import that file
Enter vpn username and password if prompted
On the VPN page, select Advanced
On the General Tab, uncheck the first option, "Use custom gateway"

Save

Use...

---

