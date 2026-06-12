---
title: "systemd-networkd-wait-online.service failed"
date: 2023-09-21
forum: Virtualisation
---

### Post by nasgul on 2023-09-21
Running a VM of Ubuntu 22.04.3 LTS. I just encountered  systemd-networkd-wait-online.service failed. Not sure how or why this  happened as it's been running fine up until now.  Anyone know how to fix  this?

```
&#9484;&#9472;[administrator@ubuntusrv]&#9472;[~]
&#9492;&#9472;&#9472;&#9596; $systemctl --type=service --state=failed
  UNIT                                 LOAD   ACTIVE SUB    DESCRIPTION
&#9679; systemd-networkd-wait-online.service loaded failed failed Wait for Network to be Configured

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.
1 loaded units listed.
&#9484;&#9472;[administrator@ubuntusrv]&#9472;[~]
&#9492;&#9472;&#9472;&#9596; $sudo systemctl restart systemd-networkd-wait-online
[sudo] password for administrator:
Job for systemd-networkd-wait-online.service failed because the control process exited with error code.
See "systemctl status systemd-networkd-wait-online.service" and "journalctl -xeu systemd-networkd-wait-online.service" for details.
&#9484;&#9472;[&#10007;]&#9472;[administrator@ubuntusrv]&#9472;[~]
&#9492;&#9472;&#9472;&#9596; $systemctl status systemd-networkd-wait-online.service
× systemd-networkd-wait-online.service - Wait for Network to be Configured
     Loaded: loaded (/etc/systemd/system/systemd-networkd-wait-online.service; enabled; vendor preset: disabled)
     Active: failed (Result: exit-code) since Thu 2023-09-21 22:36:52 PST; 3min 31s ago
       Docs: man:systemd-networkd-wait-online.service(8)
    Process: 143981 ExecStart=/lib/systemd/systemd-networkd-wait-online --any (code=exited, status=1/FAILURE)
   Main PID: 143981 (code=exited, status=1/FAILURE)
        CPU: 3ms

Sep 21 22:34:52 ubuntusrv systemd[1]: Starting Wait for Network to be Configured...
Sep 21 22:36:52 ubuntusrv systemd-networkd-wait-online[143981]: Timeout occurred while waiting for network connectivity.
Sep 21 22:36:52 ubuntusrv systemd[1]: systemd-networkd-wait-online.service: Main process exited, code=exited, status=1/FAILURE
Sep 21 22:36:52 ubuntusrv systemd[1]: systemd-networkd-wait-online.service: Failed with result 'exit-code'.
Sep 21 22:36:52 ubuntusrv systemd[1]: Failed to start Wait for Network to be Configured.
&#9484;&#9472;[&#10007;]&#9472;[administrator@ubuntusrv]&#9472;[~]
&#9492;&#9472;&#9472;&#9596; $journalctl -xeu systemd-networkd-wait-online.service
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; The unit systemd-networkd-wait-online.service has entered the 'failed' state with result 'exit-code'.
Sep 21 16:46:36 ubuntusrv systemd[1]: Failed to start Wait for Network to be Configured.
&#9617;&#9617; Subject: A start job for unit systemd-networkd-wait-online.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; A start job for unit systemd-networkd-wait-online.service has finished with a failure.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 12 and the job result is failed.
Sep 21 22:34:52 ubuntusrv systemd[1]: Starting Wait for Network to be Configured...
&#9617;&#9617; Subject: A start job for unit systemd-networkd-wait-online.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; A start job for unit systemd-networkd-wait-online.service has begun execution.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 3334.
Sep 21 22:36:52 ubuntusrv systemd-networkd-wait-online[143981]: Timeout occurred while waiting for network connectivity.
Sep 21 22:36:52 ubuntusrv systemd[1]: systemd-networkd-wait-online.service: Main process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; An ExecStart= process belonging to unit systemd-networkd-wait-online.service has exited.
&#9617;&#9617;
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
Sep 21 22:36:52 ubuntusrv systemd[1]: systemd-networkd-wait-online.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; The unit systemd-networkd-wait-online.service has entered the 'failed' state with result 'exit-code'.
Sep 21 22:36:52 ubuntusrv systemd[1]: Failed to start Wait for Network to be Configured.
&#9617;&#9617; Subject: A start job for unit systemd-networkd-wait-online.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; A start job for unit systemd-networkd-wait-online.service has finished with a failure.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 3334 and the job result is failed.
&#9484;&#9472;[administrator@ubuntusrv]&#9472;[~]
&#9492;&#9472;&#9472;&#9596; $lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:        22.04
Codename:       jammy
&#9484;&#9472;[administrator@ubuntusrv]&#9472;[~]
&#9492;&#9472;&#9472;&#9596; $uname -r
6.3.3-060303-generic
```

---

### Post by Frogs Hair on 2023-09-22
Moved to *Virtualisation.*

---

### Post by #&amp;thj^% on 2023-09-22
Would you please try this:
```
sudo systemctl edit systemd-networkd-wait-online.service
```
And modify to read exactly like:
```
[Service]
ExecStart=
ExecStart=/usr/lib/systemd/systemd-networkd-wait-online --any
```
If that not satisfactory then change:
```
ExecStart=/lib/systemd/systemd-networkd-wait-online --interface=eth0
```

That will cause the service to ignore all other interfaces. 
Keep us posted.
And as pointed out:
> **crtlbreak said:**
> Dont forget to do a 
```
systemctl restart systemd-networkd-wait-online.service
```

---

### Post by x-olof on 2023-09-23
I have the same issue on multiple ubuntu 22.04 virtual servers, they run fine, but take longer to boot up.
The first time I saw the error in monitoring was September 13.

[QUOTE=1fallen;14158617

```
ExecStart=/lib/systemd/systemd-networkd-wait-online --interface=eth0
```

That will cause the service to ignore all other interfaces. 
Keep us posted.[/QUOTE]

I tested the two, --any had no effect, same error when I restarted the service,  but --interface=eth0 fixed it.

To me it looks like systemd-networkd-wait-online somehow doesn't know about the interfaces.

---

### Post by MAFoElffen on 2023-09-24
Just an observation...

Maybe do:
```

ip a

```
Change "--interface=[COLOR=#ff0000]eth0[/COLOR]" to the active Ethernet device name from that output. Linux deprecated using ethX a while ago, and now remaps them to denote PCIe bus/slot. Example: enp7s0

---

### Post by nasgul on 2023-09-25
> **1fallen said:**
> 
```
ExecStart=/lib/systemd/systemd-networkd-wait-online --interface=eth0
```


This one worked for me but in my case it's ```
ExecStart=/lib/systemd/systemd-networkd-wait-online --interface=enp6s18
```

Before I got any responses in this thread, I also tried out changing the **/etc/netplan/00-installer-config.yaml** config with renderer set from **NetworkManager **to **networkd **which also resolved the issue for me:

```
network:
  ethernets:
    enp6s18:
      dhcp4: no
      addresses: [192.168.1.239/24]
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses: [192.168.1.239, 9.9.9.9, 1.1.1.2, 208.67.222.222]
  version: 2
  renderer: networkd
```

---

### Post by MAFoElffen on 2023-09-26
LOL. Yup. 

By coincidence, both 1fallen and I were just talking privately the other day about the log error messages we see from systems using NetworkManager and that we both use networkd as our preference.

---

### Post by crtlbreak on 2023-10-17
> **1fallen said:**
> Would you please try this:
```
sudo systemctl edit systemd-networkd-wait-online.service
```
And modify to read exactly like:
```
[Service]
ExecStart=
ExecStart=/usr/lib/systemd/systemd-networkd-wait-online --any
```
If that not satisfactory then change:
```
ExecStart=/lib/systemd/systemd-networkd-wait-online --interface=eth0
```

That will cause the service to ignore all other interfaces. 
Keep us posted.


Dont forget to do a 
```
systemctl restart systemd-networkd-wait-online.service
```

---

### Post by #&amp;thj^% on 2023-10-17
> **crtlbreak said:**
> Dont forget to do a 
```
systemctl restart systemd-networkd-wait-online.service
```
+1
> **MAFoElffen said:**
> LOL. Yup. 

By coincidence, both 1fallen and I were just talking privately the other day about the log error messages we see from systems using NetworkManager and that we both use networkd as our preference.
```
systemctl status systemd-networkd
&#9679; systemd-networkd.service - Network Configuration
     Loaded: loaded (/usr/lib/systemd/system/systemd-networkd.service; enabled;>
     Active: active (running) since Tue 2023-10-17 10:43:41 MDT; 2min 34s ago
TriggeredBy: &#9679; systemd-networkd.socket
       Docs: man:systemd-networkd.service(8)
             man:org.freedesktop.network1(5)
   Main PID: 681 (systemd-network)
     Status: "Processing requests..."
      Tasks: 1 (limit: 18275)
   FD Store: 0 (limit: 512)
     Memory: 3.4M
        CPU: 55ms
     CGroup: /system.slice/systemd-networkd.service
             &#9492;&#9472;681 /usr/lib/systemd/systemd-networkd

```

---

### Post by smakodak on 2024-09-25
I tried everything suggested in the thread to no avail. What finally solved it for me was adding "**link-local: [ ]" **to the network configuration file as shown below.

/etc/netplan/00-installer-config.yaml
> 
network:
  version: 2
  ethernets:
    ens160:
**      link-local: [ ]**
      dhcp4: false


  vlans:
      vlan.671:
          id: 671
          link: ens160
          link-local: [ ipv4 ]
          dhcp4: true


---

### Post by psylem on 2025-01-04
I have a desktop Ubuntu 22.04 that started taking over 2 minutes to start, and I determined this is probably because I did a server install and then installed Xfce on it which brought in NetworkManager from looking through these threads. This fixed it for me...

[FONT=Courier New]
sudo systemctl stop systemd-networkd
sudo systemctl disable systemd-networkd
sudo systemctl mask systemd-networkd

sudo systemctl stop systemd-networkd-wait-online.service
sudo systemctl disable systemd-networkd-wait-online.service
sudo systemctl mask systemd-networkd-wait-online.service
[/FONT]

Then I figured I don't need cloud-init and disabled that, plus why does NetworkManager need to wait for network either? So now my system has never been faster to start up...

[FONT=Courier New]
sudo touch /etc/cloud/cloud-init.disabled

sudo systemctl stop NetworkManager-wait-online.service
sudo systemctl disable NetworkManager-wait-online.service
sudo systemctl mask NetworkManager-wait-online.service
[/FONT]

---

