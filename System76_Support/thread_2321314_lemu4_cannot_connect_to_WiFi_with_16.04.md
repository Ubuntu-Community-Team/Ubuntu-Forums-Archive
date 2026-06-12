---
title: "lemu4 cannot connect to WiFi with 16.04"
date: 2016-04-21
forum: System76 Support
---

### Post by shochatd on 2016-04-21
I just upgraded my System76 Lemur Ultra (lemu4) from 15.10 to 16.04 and now it cannot connect to WiFi. It can connect via wired Ethernet and using that, I was able to install the System76 Driver version 16.04.1. When I type in my password and click Connect, nothing happens (no error message, no connection and if I click on the networking menu again, my WiFi is still showing as available as if I had not yet tried it). Is there anything I can do, or do I have to wait for a still newer version of System76 Driver?

---

### Post by shochatd on 2016-04-22
I just tried reinstalling 16.04 from ISO. Still no change with the WiFi. It still behaves exactly as described above. This laptop uses the Centrino chipset for wireless. It has worked without problem for the 4 years that I have owned it, and across many Ubuntu upgrades. I guess the next step will be to do this: [https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure)

---

### Post by shochatd on 2016-04-22
Here is the result of the diagnostics from the instructions in the link above:
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/292023](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/292023)
I did notice in the output that there were several nearby networks using channel 11 (same as the access point I've been trying to connect to), so I changed it to channel 7, but I still see the same problem.

---

### Post by shochatd on 2016-04-22
Somehow finally got it to connect. Maybe changing to channel 7 did help after all. Also System76 folks suggested "forgetting" the network which I tried several times and finally logged out and back in after doing so. It was also timing out pretty fast while I typed in the password, so finally put the pw in a file so I could paste it quickly. No idea what finally made the difference. Now that I'm on a new clean install, time to restore all my stuff from backup.

---

