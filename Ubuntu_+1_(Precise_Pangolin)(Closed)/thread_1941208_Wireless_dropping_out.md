---
title: "Wireless dropping out"
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kiwinewt on 2012-03-15
I have a Belkin F5D8053. This worked perfectly with 11.10. I upgraded to 12.04 today and ever since the wireless shows as connected in wicd, but cannot ping anything and no other machines on the network can access it.
I can usually get up to 5 minutes MAX before it drops out. Leaving it will bring it up a few hours later until it falls off again.

I have tried:
checking resolv.conf
checking correct drivers
etc...

I am on Mythbuntu with an 802.11 network secured with WEP (no comment ;) )

Thanks in advance

Nate

---

### Post by kiwinewt on 2012-03-15
I am going to try this tonight: [http://ubuntuforums.org/showpost.php?p=10473282&postcount=14](http://ubuntuforums.org/showpost.php?p=10473282&postcount=14)

---

### Post by jonnyboysmithy on 2012-03-15
I get the same occasionally.
Workaround for me: click the wireless tray icon. go 'edit connections' 
under the wireless tab delete the profile for the connection. then under the tray icon connect again and it works (for me).

---

### Post by kiwinewt on 2012-03-15
Thanks. It's a MythTV Frontend which makes it tricky to have to delete the profiles often.
It would be better for a proper fix than a workaround, of course :)
I'll give that a try tonight too though
Nate

---

### Post by kiwinewt on 2012-03-16
OK I have tried both options
Deleting the wireless caused nm-tool to show it as unavailable.
Rebooted and network came up fine, tried to copy a file off the samba share and it crashed

Installed the firmware as per my link - fully would not connect to the network after that.

Has anyone else had issues with Belkin wireless devices after upgrading?

---

### Post by jonnyboysmithy on 2012-03-16
Edit: ----------------------------------------

---

### Post by kiwinewt on 2012-03-17
Managed to get the connection up for long enough to do an apt-get update... now there are no networks showing in network-manager but ifconfig wlan0 shows up and connected... weird as...

---

### Post by kiwinewt on 2012-03-17
Had to fully blacklist the 2800 and 2x00 drivers then compile and install the rt2870 drivers... interesting as they worked before... lol
for anyone else with this issue, the rt2870 fix is here: [http://linuxforums.org.uk/index.php?topic=852.0](http://linuxforums.org.uk/index.php?topic=852.0)

---

### Post by grahammechanical on 2012-03-17
There is one little bit of information that I can supply and it is this:

Things do not work well if you have two network managers installed at the same time. Network Manager does not use the interfaces file.

---

### Post by kiwinewt on 2012-03-17
Thanks Graham. That could have been one of the things too... the joys of multiple suggestions from different places... ;)

As your signature says: "It will not stop us from doing stupid things."

---

