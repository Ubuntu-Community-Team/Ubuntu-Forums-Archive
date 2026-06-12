---
title: "Netplan to NetworkManager"
date: 2021-02-15
forum: Server Platforms
---

### Post by #&amp;thj^% on 2021-02-15
How to change renderer from systemd-networkd NetworkManager

First view the config file using the cat command:
```
cat /etc/netplan/01-netcfg.yaml  ### or your filename
```

Sample outputs:
```

# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s31f6:
      dhcp4: yes

```
The above config tells of bringing up the Ethernet interface named enp0s31f6 via DHCP.
Network Manager as the backend for netplan

Network Manager strives for Network Connectivity, which “Just Works” for new Linux users. The machine should use the wired network connection when it’s plugged in but automatically switch to a wireless connection when the user unplugs it. Similarly, you can easily configure a VPN network and many other options. Edit the config file using a text editor such as nano command or vim command:
```

sudo cp -v /etc/netplan/01-netcfg.yaml /root/
sudo vim /etc/netplan/01-netcfg.yaml
```

Update it as follows:
```

# This file describes the network interfaces available on your system
# For more information, see netplan(5).
# Set and change netplan renderer to NetworkManager GUI tool 
network:
  version: 2
  renderer: NetworkManager
```

Save and close the file. You can reboot the Linux computer or apply change by typing the following command:
sudo netplan apply

The above command applies the current netplan configuration to a running system.
How do I use a GUI tool to configure networking?

Open the Activities (press the Super key on your keyboard) overview and start typing Settings.
Activities overview to start Setting in Ubuntu Linux

Make sure you click on Settings.
Next click on Network:
Activities overview to start Setting in Ubuntu Linux

Now you can edit or and set new IP address. Select IPv4 or IPv6. Type in the IP Address and Gateway, as well as the appropriate Netmask. In the DNS section, switch the Automatic switch to off. Enter the IP address of a DNS server you want to use and so on:
Ubuntu change netplan renderer from networkd to NetworkManager for networking.

Or simply use this script: (with back-ups included)
***********************************************
Script: Author  @dbkinghorn Named: netplan2NM.sh 
```

 Change Ubuntu 20.04 server netplan to use NetworkManager instead of networkd
netplan2NM.sh
#!/usr/bin/env bash

# netplan2NM.sh
# Ubuntu server 20.04  Change from netplan to NetworkManager for all interfaces

echo 'Changing netplan to NetowrkManager on all interfaces'
# backup existing yaml file
cd /etc/netplan
cp 01-netcfg.yaml 01-netcfg.yaml.BAK

# re-write the yaml file
cat << EOF > /etc/netplan/01-netcfg.yaml
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: NetworkManager
EOF

# setup netplan for NM
netplan generate
netplan apply
# make sure NM is running
systemctl enable NetworkManager.service
systemctl restart NetworkManager.service

echo 'Done!'

```
**Important Note: >>** It would first be a good idea to check if that file exists.
```
cat /etc/netplan/01-netcfg.yaml
```
Right off the get go I had already named mine, "01-network-manager-all.yaml">>>with the shown code.
```
network:
  version: 2
  renderer: NetworkManager
```
  Now you should be using Network-Manager.
  
 To be fair I've included a link for Netplan as well. [https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-configure-networking-in-ubuntu-20-04-with-netplan/](https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-configure-networking-in-ubuntu-20-04-with-netplan/)
 Good Luck! Remember spacing with yaml is crucial.

---

### Post by TheFu on 2021-02-16
Maybe this belongs in the tutorial sub-forum?

---

### Post by LHammonds on 2021-02-17
Thanks for creating and sharing this script.

It was interesting to see a script changing out the backend render for netplan.  It was only one way and thought it would be handy to have it toggle between both and have more error checks in place since sometimes things do not work as intended when scripted for various reasons (such as unexpected permission settings different from default, etc.)

Here is a similar script that goes both ways.  Source code posted on [GitHub](https://github.com/LHammonds/ubuntu-bash/blob/master/netplan-render-toggle.sh) and copied below:
```

#!/bin/bash
#############################################################
## Name          : netplan-render-toggle.sh
## Version       : 1.0
## Date          : 2021-02-17
## Author        : LHammonds
## Purpose       : Toggle netplan render between networkd and NetworkManager
## Compatibility : Verified on Ubuntu Desktop 20.04 LTS
## Requirements  : run as root
## Run Frequency : Manually as needed
## Parameters    : None
## Exit Codes :
## 0  = Success
## 1  = ERROR: Must be root user
## 2  = ERROR: Expected networkd configuration file missing
## 3  = ERROR: Could not create NetworkManager file
## 4  = ERROR: Failed to rename networkd file
## 5  = ERROR: Failed to rename NetworkManager file
## 6  = ERROR: Failed to rename NetworkManager file
## 7  = ERROR: Failed to rename networkd file
## 8  = ERROR: Failed to ping test IP address
###################### CHANGE LOG ###########################
## DATE       VER WHO         WHAT WAS CHANGED
## ---------- --- ----------- ---------------------------------------
## 2021-02-17 1.0 LHammonds   Created script.
#############################################################

## NOTE: This script assumes you have a working networkd configuration file.

## Define variables ##
NetworkManagerFile="/etc/netplan/01-network-manager-all"
NetworkdFile="/etc/netplan/01-netcfg"
TestIP="8.8.8.8"

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  echo "[ERROR:1] Root user required to run this script."
  exit 1
fi

## Make sure our primary assumption of an existing default Networkd file exists ##
if [ ! -f ${NetworkdFile}.yaml ] && [ ! -f ${NetworkdFile}.bak ]; then
  ## Abort script since the required default file does not exist ##
  echo "[ERROR:2] Default networkd file nor the backup was found."
  exit 2
fi

## Check if NetworkManager file exists ##
if [ ! -f ${NetworkManagerFile}.yaml ] && [ ! -f ${NetworkManagerFile}.bak ]; then
  ## Create NetworkManager file ##
  echo "[INFO] NetworkManager file not found.  Creating a new one..."
  touch ${NetworkManagerFile}.bak
  chown root:root ${NetworkManagerFile}.bak
  chmod 0644 ${NetworkManagerFile}.bak
  cat << EOF > ${NetworkManagerFile}.bak
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: NetworkManager
EOF
  if [ ! -f ${NetworkManagerFile}.bak ]; then
    echo "[ERROR:3] Could not create NetworkManager file."
    exit 3
  fi
fi

## Toggle between NetworkManager and Networkd each time this script runs ##
if [ -f ${NetworkdFile}.yaml ]; then
  echo "[INFO] Switching from networkd to NetworkManager"
  mv ${NetworkdFile}.yaml ${NetworkdFile}.bak
  ## Make sure the rename worked ##
  if [ ! -e ${NetworkdFile}.bak ]; then
    echo "[ERROR:4] Could not rename ${NetworkdFile}.yaml"
    exit 4
  fi
  ## Rename NetworkManager file ##
  mv ${NetworkManagerFile}.bak ${NetworkManagerFile}.yaml
  ## Make sure the rename worked ##
  if [ ! -f ${NetworkManagerFile}.yaml ]; then
    echo "[ERROR:5] Could not rename ${NetworkManagerFile}.bak"
    exit 5
  fi
  echo "[INFO] Enabling NetworkManager service..."
  systemctl enable NetworkManager.service > /dev/null 2>&1
  systemctl start NetworkManager.service > /dev/null 2>&1
else
  echo "[INFO] Switching from NetworkManager to networkd"
  mv ${NetworkManagerFile}.yaml ${NetworkManagerFile}.bak
  ## Make sure the rename worked ##
  if [ ! -f ${NetworkManagerFile}.bak ]; then
    echo "[ERROR:6] Could not rename ${NetworkManagerFile}.yaml"
    exit 6
  fi
  ## Rename networkd file ##
  mv ${NetworkdFile}.bak ${NetworkdFile}.yaml
  ## Make sure the rename worked ##
  if [ ! -f ${NetworkdFile}.yaml ]; then
    echo "[ERROR:7] Could not rename ${NetworkdFile}.bak"
    exit 7
  fi
  echo "[INFO] Disabling NetworkManager service..."
  systemctl disable NetworkManager.service > /dev/null 2>&1
  systemctl stop NetworkManager.service > /dev/null 2>&1
fi

echo "[INFO] Applying changes to NetPlan..."
netplan generate
netplan apply

if [ -f ${NetworkManagerFile}.yaml ]; then
  echo "[INFO] Restarting NetworkManager service..."
  systemctl restart NetworkManager.service > /dev/null 2>&1
fi

echo "[INFO] Current network settings..."
ip address | grep inet

echo "[INFO] Current interfaces that are UP..."
ip link | grep -i -w UP

ping -c 1 ${TestIP} > /dev/null
ReturnCode=$?
if [ ${ReturnCode} -eq 0 ]; then
  echo "[INFO] Successful ping test to ${TestIP}"
else
  echo "[ERROR:8] Cannot ping ${TestIP}"
  echo "[INFO] Something is incorrect with the configuration or network"
fi

## Clean exit of script at this point ##
exit 0

```


Output when going from networkd to NetworkManager:
```

[INFO] Switching from networkd to NetworkManager
[INFO] Enabling NetworkManager service...
[INFO] Applying changes to NetPlan...
[INFO] Restarting NetworkManager service...
[INFO] Current network settings...
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
    inet 192.168.50.106/24 brd 192.168.50.255 scope global dynamic noprefixroute enp0s3
    inet 192.168.50.75/24 brd 192.168.50.255 scope global secondary noprefixroute enp0s3
    inet6 fe80::41b:135b:2378:e93e/64 scope link noprefixroute 
[INFO] Current interfaces that are UP...
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
[INFO] Successful ping test to 8.8.8.8

```

Output when going from NetworkManager to networkd:
```

[INFO] Switching from NetworkManager to networkd
[INFO] Disabling NetworkManager service...
[INFO] Applying changes to NetPlan...
[INFO] Current network settings...
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
    inet 192.168.50.75/24 brd 192.168.50.255 scope global noprefixroute enp0s3
    inet6 fe80::41b:135b:2378:e93e/64 scope link noprefixroute 
[INFO] Current interfaces that are UP...
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
[INFO] Successful ping test to 8.8.8.8

```

LHammonds

---

### Post by #&amp;thj^% on 2021-02-17
Now we're cooking :), This is the whole point of this thread, Thanks for the added comments.
Any improvements are welcome.
@LHammonds Looks well thought out. Nice.

---

