---
title: "Wireless PEAP connection setup (manual)"
date: 2015-04-25
forum: Ubuntu Phone and Tablet
---

### Post by ockelz on 2015-04-25
I'm having troubles setting up a wifi connection from my ISP (Ziggo) which is using PEAP for wifi (so called hotspots).
These are the specifications of the connection:

Wireless SSID    Ziggo
Protection Type :   WPA2-Enterprise 
Encryptiontype:    AES (CCMP) 
EAP Methode    PEAP 
Phase 2-verificatie    :empty
Certificate:     empty
Anonymous identity: empty 
Identity: [my isp provided username] 
Password: [my isp provided password]

This connection has been set up on my 14.04 ubuntu box and is working flawlessely. So i figured it should be working on the Aquarius as well ...
But unfortunately not. Since the BQ has no extra settings to setup a wifi connection besides WPA(2) and WEP the connection can't be made.
Setting up a hidden connection does not provide more options.

I have tried to manually edit the connection info from my working setup to my phone with adb shell and editting the created profile in /etc/NetworkManager/system-connections.
But this did not bring up the expected result... 

Contents of the edited file [U]/etc/NetworkManager/system-connections/Ziggo
[/U]
```

[connection]
id=Ziggo
uuid=3c31ba07-bf71-413c-a653-aa2fdb******
type=802-11-wireless

[802-11-wireless]
ssid=Ziggo
mac-address=4C:74:03:*********
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-eap
auth-alg=open

[802-1x]
eap=peap;
identity=[provided by isp]
phase2-auth=mschapv2
password=[provided by isp]

[ipv4]
method=auto

[ipv6]
method=auto

```

[B]Aquarius BQ4.5 PHONE connection dialog (not-working because no extra settings):
[/B]
[IMG]http://i.imgur.com/LU86JTl.jpg?1[/IMG]
[B]
Desktop connection dialog (working):[/B]

[IMG]http://i.imgur.com/TYjg9xh.jpg?1[/IMG]

---

### Post by ockelz on 2015-04-26
[B]EDIT:

Information below is outdated, PEAP and other methods are now fully supported 
---------------------

Solved[/B] :p

After multiple failures i have it working  on my BQ phone. I finally got it working!
I followed this guy's help (TX!) 

[http://askubuntu.com/questions/598980/ubuntu-touch-wireless-peap-workaround](http://askubuntu.com/questions/598980/ubuntu-touch-wireless-peap-workaround)

I  only stumbled in to an unusable nano editor (non-saving and messed up layout) to edit the connection in  /etc/NetworkManager/system-connections/<#your connection here>.
Since i'm not a vi user i did the following to edit the connection:

```

sudo cp /etc/NetworkManager/system-connections/<#your connection here> /home/phablet/Downloads/
sudo chown phablet:phablet /home/phablet/Downloads/<#your connection here>
sudo chmod 644 /home/phablet/Downloads/<#your connection here>

```

Navigate with nautilus on your regular desktop to the Downloads folder on your phone and edit the connection file with gedit (or whatever).
The file should look like this:

DO NOT change the first 4 lines!

```

[connection]
id=Ziggo 
uuid=28e376fd-78cb-451f-9b18-a489819b6927
type=802-11-wireless


[802-11-wireless-security]
key-mgmt=wpa-eap
auth-alg=open

[802-11-wireless]
ssid=Ziggo
mode=infrastructure
mac-address=4C:74:03:5F:**:**
security=802-11-wireless-security

[802-1x]
eap=peap;
identity=<provider username here>
phase2-auth=mschapv2
password=<provider username here>

[ipv4]
method=auto

[ipv6]
method=auto

```

Save the file and copy the file back:

```

sudo cp  /home/phablet/Downloads/<#your connection here> /etc/NetworkManager/system-connections/

```

Select the network in wifi settings on your phone and it will connect.

Dutch instruction here: [https://forum.ubuntu-nl.org/index.php?topic=88578.0](https://forum.ubuntu-nl.org/index.php?topic=88578.0)

---

