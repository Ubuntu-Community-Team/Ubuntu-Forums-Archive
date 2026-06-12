---
title: "ProtonVPN failing with new protonvpn.service"
date: 2024-02-17
forum: Ubuntu/Debian BASED
---

### Post by pilotone on 2024-02-17
Hi,
I am running Ubuntu 22:04 
Bodhi Distrubution
Protonvpn

I am trying to start ProtonVPN at startup .
I have created /etc/systemd/system/protonvpn.service

which protonvpn-app
/usr/bin/protonvpn-app

 users
glb


# Buttitta added this to start protonvpn at startup
#  2/17/2024
# to start it at boot
#run below to activate
#sudo systemctl daemon-reload
#sudo systemctl enable protonvpn
#sudo systemctl start protonvpn
#
#
[Unit]
Description=Proton VPN
Wants=network-online.target
[Service]
Type=forking
ExecStart=/usr/bin/protonvpn-app c --cc ch
Environment=PVPN_WAIT=300
Environment=PVPN_DEBUG=1
Environment=SUDO_USER=<glb>
[Install]
WantedBy=multi-user.target

When I run:
sudo systemctl start protonvpn.service
Job for protonvpn.service failed because the control process exited with error code.
See "systemctl status protonvpn.service" and "journalctl -xeu protonvpn.service" for details.

 systemctl status protonvpn.service
× protonvpn.service - Proton VPN
     Loaded: loaded (/etc/systemd/system/protonvpn.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Sat 2024-02-17 13:50:59 AKST; 1min 0s ago
    Process: 6038 ExecStart=/usr/bin/protonvpn-app c --cc ch (code=exited, status=1/FAILURE)
        CPU: 123ms

Feb 17 13:50:59 Mario systemd[1]: Starting Proton VPN...
Feb 17 13:50:59 Mario protonvpn-app[6038]: 2024-02-17T22:50:59.474060 | proton.vpn.connection.vpnconnector:168 | INFO | CONN:STATE_CHANGED | Disconnected (initial state)
Feb 17 13:50:59 Mario protonvpn-app[6038]: 2024-02-17T22:50:59.474306 | proton.vpn.app.gtk.app:57 | INFO | APP:PROCESS_START | self=<app.App object at 0x7fe975f0cb40 (proton+vpn+app+gtk+app+>
Feb 17 13:50:59 Mario protonvpn-app[6038]: Unknown option --cc
Feb 17 13:50:59 Mario systemd[1]: protonvpn.service: Control process exited, code=exited, status=1/FAILURE
Feb 17 13:50:59 Mario systemd[1]: protonvpn.service: Failed with result 'exit-code'.
Feb 17 13:50:59 Mario systemd[1]: Failed to start Proton VPN.

and 

b 17 13:36:29 Mario systemd[1]: protonvpn.service: Control process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; An ExecStart= process belonging to unit protonvpn.service has exited.
&#9617;&#9617;
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
Feb 17 13:36:29 Mario systemd[1]: protonvpn.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; The unit protonvpn.service has entered the 'failed' state with result 'exit-code'.
Feb 17 13:36:29 Mario systemd[1]: Failed to start Proton VPN.
&#9617;&#9617; Subject: A start job for unit protonvpn.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; A start job for unit protonvpn.service has finished with a failure.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 2253 and the job result is failed.
Feb 17 13:50:59 Mario systemd[1]: Starting Proton VPN...
&#9617;&#9617; Subject: A start job for unit protonvpn.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; A start job for unit protonvpn.service has begun execution.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 2682.
Feb 17 13:50:59 Mario protonvpn-app[6038]: 2024-02-17T22:50:59.474060 | proton.vpn.connection.vpnconnector:168 | INFO | CONN:STATE_CHANGED | Disconnected (initial state)
Feb 17 13:50:59 Mario protonvpn-app[6038]: 2024-02-17T22:50:59.474306 | proton.vpn.app.gtk.app:57 | INFO | APP:PROCESS_START | self=<app.App object at 0x7fe975f0cb40 (proton+vpn+app+gtk+app+>
Feb 17 13:50:59 Mario protonvpn-app[6038]: Unknown option --cc
Feb 17 13:50:59 Mario systemd[1]: protonvpn.service: Control process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; An ExecStart= process belonging to unit protonvpn.service has exited.
&#9617;&#9617;
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
Feb 17 13:50:59 Mario systemd[1]: protonvpn.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; The unit protonvpn.service has entered the 'failed' state with result 'exit-code'.
Feb 17 13:50:59 Mario systemd[1]: Failed to start Proton VPN.
&#9617;&#9617; Subject: A start job for unit protonvpn.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; A start job for unit protonvpn.service has finished with a failure.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 2682 and the job result is failed.


I'm pretty new at this having given up on windows. 
Any Ideas why this is happening?
Thanks

---

### Post by howefield on 2024-02-17
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by #&amp;thj^% on 2024-02-17
Maybe remove the auto start stuff you added, also show this:
```
 protonvpn-app status 

```
Please use Code tags for terminal returns ie:
[noparse]```
 your copied paste here
```[/noparse]

---

