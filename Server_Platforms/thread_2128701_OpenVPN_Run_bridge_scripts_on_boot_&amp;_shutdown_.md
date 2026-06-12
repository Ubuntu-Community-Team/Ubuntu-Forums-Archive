---
title: "OpenVPN: Run bridge scripts on boot &amp; shutdown before and after OpenVPN service"
date: 2013-03-24
forum: Server Platforms
---

### Post by cconover on 2013-03-24
[COLOR=#000000][FONT=Arial]I've got OpenVPN working properly on my server, using [/FONT][/COLOR][bridge-start and bridge-stop scripts]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html")[COLOR=#000000][FONT=Arial] to create and remove network bridge, respectively. How do I set these scripts up to run bridge-start at boot before starting OpenVPN, and bridge-stop at shutdown after stopping OpenVPN? I've tried adding 'up "/path/to/bridge-start"' and 'down "/path/to/bridge-stop"' to server.conf but the bridge interface doesn't get created. It appears these scripts absolutely have to be run separate from OpenVPN's own startup/shutdown.[/FONT][/COLOR]

---

### Post by kevdog on 2013-03-24
I'm just going to throw out an idea since it's been awhile since I played around with what you want to do however I believe you would have to create your own udev script and add your networking scripts to be called from the preup and postdown sections. Writing a udev script is really easy to do so don't be intimidated.

---

### Post by cconover on 2013-03-24
Ok cool, I'll check it out.  Thanks!

---

