---
title: "cloud-init and snap - Remove?"
date: 2022-06-03
forum: Server Platforms
---

### Post by LHammonds on 2022-06-03
My 22.04 LTS servers are not cloud servers and I have no need to utilize anything these apps offer.  However, "systemd-analyze blame" shows it to be slowing down the boot-time of the server...however, uninstalling cloud-init and the snap applications and then snapd itself seems to break its back (2 minute timeout delay during boot) and syslog errors.

Is cloud-init and snapd embedded into the OS like Internet Explorer was for Windows?


Here is the process I used to remove them:

```

sudo snap remove --purge lxd
sudo snap remove --purge core20
sudo snap remove --purge snapd
sudo apt --purge autoremove snapd
sudo apt --purge autoremove cloud-init
sudo rm -rf /etc/cloud/
sudo rm -rf /var/lib/cloud/

```

LHammonds

---

### Post by TheFu on 2022-06-03
I think snaps can be removed.
I started removing cloud-init in 18.04, but it kept getting brought back, so I gave up. I just ignore it.  My 20.04 servers don't have  /etc/cloud/ directories, so it must be something new.

My 20.04 VPN server: 
```
$ dpkg -l cloud-ini*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version      Architecture Description
+++-===========================-============-============-===================>
**un  cloud-init                  <none>       <none>       (no description ava>**
ii  cloud-initramfs-copymods    0.45ubuntu2  all          copy initramfs modu>
ii  cloud-initramfs-dyn-netconf 0.45ubuntu2  all          write a network

$ snap list

Command 'snap' not found, but can be installed with:

sudo apt install snapd
```
So, perhaps it was just a fluke that it returned in 18.04? It is still uninstalled on 20.04. Also, snapd has been purged.

I'm still just playing with 22.04. Probably won't go production for it until after my last 18.04 system is migrated to 20.04.  I tend to move the email gateway and VPN servers to the newest release first. Those are pretty standard server OS installs.  The systems that are full of users and data go last. I don't 'wing-it' with those.

---

### Post by ameinild on 2022-06-09
I've removed cloud-init from my Ubuntu 22.04 (although upgraded from 20.04), and I experience no problems. So I think maybe the problem could be isolated to snapd? 

I haven't really played with removing snapd yet though.

---

### Post by LHammonds on 2022-06-10
I restored my server prior to the point of uninstalling cloud-ini and snapd.

While watching it boot, it sat on the screen with this message (it timed out after 2 minutes):

```
A start job is running for Wait for Network to be Configured
```

When the system was available, I ran this command:

```
# systemd-analyze blame
2min 225ms systemd-networkd-wait-online.service
    1.964s dev-mapper-LVG\x2dusr.device
    1.947s dev-mapper-LVG\x2droot.device
     729ms udisks2.service
     639ms networkd-dispatcher.service
     487ms ufw.service
```

Then I ran this command:

```
# systemctl show -p WantedBy network-online.target
WantedBy=cloud-final.service cloud-config.service open-iscsi.service iscsid.service
```

After doing some research and trial-n-error, I finally found the odd-ball trick to let my system boot quickly (~15 seconds).  The trick was to add "optional: true" to my network card in NetPlan.  This made the system ignore the network card while booting since something expects the network card to be configured before it "can" be configured.  Something seems backwards in the boot process.  My network configuration is static IP so it is not a case where a DHCP server is not responding.

Example config:

```

network:
  ethernets:
    ens160:
      optional: true
      dhcp4: false
      dhcp6: false
      addresses:
      - 192.168.1.2/24
      routes:
      - to: default
        via: 192.168.1.1
      nameservers:
        addresses:
        - 1.1.1.1
        - 8.8.8.8
        search: []
  version: 2

```

Current system boot speed:
```
# systemd-analyze
Startup finished in 4.959s (kernel) + 7.590s (userspace) = 12.550s
graphical.target reached after 7.561s in userspace
```

I removed cloud-init using these commands:
```
sudo apt --purge autoremove cloud-init
sudo rm -rf /etc/cloud/
sudo rm -rf /var/lib/cloud/
```

After a reboot, I check the boot time again to see 4 seconds being shaved off:

```
Startup finished in 4.236s (kernel) + 4.150s (userspace) = 8.386s
graphical.target reached after 4.116s in userspace
```

LHammonds

---

### Post by #&amp;thj^% on 2022-06-10
For me, I just disabled it via:
```
sudo systemctl disable NetworkManager-wait-online.service
```
Prior to that it showed:
```
systemctl show -p WantedBy network-online.target
WantedBy=nordvpnd.service

```
I heard mixed results, very few bad, and majority found it favorable

---

### Post by LHammonds on 2022-06-10
Seems like just about the same workaround.

I have my server booting in 8 seconds now so I'm happy and can finalize my setup documentation.

LHammonds

---

### Post by Hammi on 2022-09-18
> **LHammonds said:**
> 
I removed cloud-init using these commands:
```
sudo apt --purge autoremove cloud-init
sudo rm -rf /etc/cloud/
sudo rm -rf /var/lib/cloud/
```


This, I believe, can have unwanted consequences. My fresh installed minimal Ubuntu server with 22.04.1:

```
# apt purge cloud-init -yReading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cloud-guest-utils eatmydata fdisk gdisk gir1.2-packagekitglib-1.0 groff-base
  iproute2 isc-dhcp-client isc-dhcp-common libappstream4 libatm1 libbpf0
  libcap2-bin libcurl3-gnutls libdns-export1110 libdw1 libeatmydata1 libfdisk1
  libglib2.0-bin libgstreamer1.0-0 libisc-export1105 libmnl0 libnetplan0
  libpackagekit-glib2-18 libpam-cap libstemmer0d libuchardet0 libunwind8
  libxmlb2 libxtables12 netplan.io packagekit packagekit-tools
  python-babel-localedata python3-attr python3-babel python3-certifi
  python3-chardet python3-configobj python3-idna python3-jinja2
  python3-json-pointer python3-jsonpatch python3-jsonschema python3-markupsafe
  python3-netifaces python3-pyrsistent python3-requests python3-serial
  python3-software-properties python3-tz python3-urllib3
  software-properties-common tzdata
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  cloud-init*
```

So "autoremove" will remove, inter alia, netplan.io and iproute2. Which means you end up with a system without any network connectivity anymore, if you follow this path.

---

### Post by LHammonds on 2022-09-20
> **Hammi said:**
> This, I believe, can have unwanted consequences.

So "autoremove" will remove, inter alia, netplan.io and iproute2. Which means you end up with a system without any network connectivity anymore, if you follow this path.

Not sure what these steps are doing right this second on a freshly-installed server but when I setup my template server at the time of this post (which is used to roll out all my other servers), I do not have that issue.  Here is one of those servers that I rolled out using this method (which is still has an extremely fast boot time with applications installed)

```
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy
```

 ```
apt search netplan.io
Sorting... Done
Full Text Search... Done
netplan.io/jammy-updates,now 0.104-0ubuntu2.1 amd64 [installed,automatic]
  YAML network configuration abstraction for various backends
```

```
apt search iproute2
Sorting... Done
Full Text Search... Done
iproute2/jammy,now 5.15.0-1ubuntu2 amd64 [installed,automatic]
  networking and traffic control tools
```

```
apt search cloud-init
Sorting... Done
Full Text Search... Done
cloud-init/jammy-updates,jammy-security 22.2-0ubuntu1~22.04.3 all
  initialization and customization tool for cloud instances
```

```
systemd-analyze
Startup finished in 5.146s (kernel) + 4.717s (userspace) = 9.863s
graphical.target reached after 4.706s in userspace
```

As you can see, this server has cloud-init removed but the network modules are still installed and working.

---

### Post by Hammi on 2022-09-20
Good for you. I had this issue with 2 freshly installed VMs with minimal server (first thing I did was to remove cloud-init), so thought pointing it out might help somebody.

---

### Post by LHammonds on 2022-09-20
Minimal server?   The OS I used is the standard Ubuntu Server 22.04 LTS ISO image.

EDIT: Oh, there is a minimal option during install....yeah, that option is brutal.  I could never get a useful system using that option.  I decided to use standard and strip away problem areas which is far fewer than what is needed to add after is basically just a kernel install. ;)

---

### Post by Hammi on 2022-09-20
Indeed, that's the option in the installer I used for installation, hoping for a minimal footprint...

---

### Post by LHammonds on 2022-09-20
> **Hammi said:**
> Indeed, that's the option in the installer I used for installation, hoping for a minimal footprint...
Yep, nothing I do for any of my tutorials or advice applies to "that" scenario.  It's not the same "minimal" server in the past that I found useful but I don't care to hand-craft every part of an OS.  Just realize most-everything you read will not directly apply to that "minimal" install.  It is a different creature.  I'm sure it is useful to some but I have no scenario where its useful for me.

LHammonds

---

### Post by MAFoElffen on 2022-09-21
> **LHammonds said:**
> While watching it boot, it sat on the screen with this message (it timed out after 2 minutes):

```
A start job is running for Wait for Network to be Configured
```

After doing some research and trial-n-error, I finally found the odd-ball trick to let my system boot quickly (~15 seconds). [COLOR=#ff0000] The trick was to add "optional: true" to my network card in NetPlan.  This made the system ignore the network card while booting since something expects the network card to be configured before it "can" be configured.[/COLOR]  Something seems backwards in the boot process. 

LHammonds
This is what I figured out with 20.04 about a year ago... It was driving me crazy until I found an answer for that on AskUbuntu.com

I saw immediate results. At first I thought it had something to do with my SR-IOV configs, but knew all my network devices all came up later in the boot process, with no problems. I have had no problems with them since adding those lines.

---

### Post by VMC on 2022-09-21
> **MAFoElffen said:**
> This is what I figured out with 20.04 about a year ago... It was driving me crazy until I found an answer for that on AskUbuntu.com....

Since you didn't show the link, I'm guessing this is it:
[https://askubuntu.com/questions/972215/a-start-job-is-running-for-wait-for-network-to-be-configured-ubuntu-server-17-1](https://askubuntu.com/questions/972215/a-start-job-is-running-for-wait-for-network-to-be-configured-ubuntu-server-17-1)

---

### Post by Hammi on 2022-09-21
... and in my experience, this only happens with static IPs. Don't have them with DHCP, but with netplan and static IP configuration, the upgrade to 22.04 introduced this 15 secs of waiting during boot without the "optional" parameter.

---

### Post by MAFoElffen on 2022-09-21
Yes. That was the link. 

As I remember mine was cycling 3 times, and timing out each time.

---

