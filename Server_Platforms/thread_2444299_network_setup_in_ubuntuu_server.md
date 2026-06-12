---
title: "network setup in ubuntuu server"
date: 2020-05-28
forum: Server Platforms
---

### Post by hmiersch on 2020-05-28
i'm downloading the server version of ubuntu 20.04 for my raspberry pi. once it is running on the pi, how do i go in and configure the network? so far i've always done network configuration using a GUI, never a CLI/shell/whatever you want to call it.  to put it another way, i know WHAT information to enter, but i don't know HOW.

---

### Post by slickymaster on 2020-05-28
*Thread moved to **Server Platforms**.*

---

### Post by LHammonds on 2020-05-28
While you are accessing it via a keyboard and monitor locally plugged in, you login with the credentials you supplied and immediately configure the network card.  Once you have your static IP configured, you can then logout, unplug the monitor and keyboard and access it remotely from SSH at that point using PuTTY.

Here is the [Network Configuration]("https://hammondslegacy.com/forum/viewtopic.php?p=813#p813") part of my server setup tutorial.  Make sure you utilize the name of your network card instead of what I have listed which is likely going to be named differently. (enp0s3)

Here are the pertinent steps from that article copied here: (text in [COLOR=#ff0000]red[/COLOR] will be specific to you so adjust as necessary)

```
sudo vi /etc/netplan/01-netcfg.yaml
```

```

network:
  version: 2
  renderer: networkd
  ethernets:
    [COLOR=#ff0000]enp0s3[/COLOR]:
      dhcp4: false
      dhcp6: false
      addresses: [[COLOR=#ff0000]192.168.107.2[/COLOR]/24]
      gateway4: [COLOR=#ff0000]192.168.107.1[/COLOR]
      nameservers:
        addresses: [[COLOR=#ff0000]192.168.107.212,192.168.107.213,1.1.1.1,8.8.8.8[/COLOR]]

```

NOTE #1: The above YAML format is extremely sensitive to spaces. Each indentation needs to be exactly 2 spaces. Visit NetPlan.io for more information.

NOTE #2: The network card name (enp0s3) might be something different on your machine, be sure to use it instead of what I have.

NOTE #3: You may need to manually remove the DHCP record (lease) associated to this Ubuntu server from your DHCP server so the correct IP can be found by other machines on the network. This can be avoided by temporarily configuring the VM Network Adapter connection to be "Host Only Network" instead of "VM Network" so the server is isolated during setup...at least until you reach the testing of the static IP below.

NOTE #4: You might also need to manually add a HOST(A) record to your Windows DNS server (for srv-ubuntu.mydomain.com and srv-ubuntu.work.mydomain.com)

Verify that the configuration file syntax is good:

```
sudo netplan --debug generate
```

If there were no errors, restart the network by typing the following:

```
sudo netplan --debug apply
```

Sanity check! Type "ip address" and make sure the settings are correct. Then type ping [www.google.com]("http://www.google.com") or similar and see if ping works.

LHammonds

---

### Post by hmiersch on 2020-05-30
i tried to put that into the config file, of course adjusting the info according to my system, and when i said:    

sudo netplan --debug generate    

it gave me this output:   

DEBUG:command generate: running ['/lib/netplan/generate']  
** (generate:17795): DEBUG: 15:24:27.352: Processing input file /etc/netplan/50-cloud-init.yaml..  
** (generate:17795): DEBUG: 15:24:27.353: starting new processing pass  
** (generate:17795): DEBUG: 15:24:27.353: We have some netdefs, pass them through a final round of validation  
** (generate:17795): DEBUG: 15:24:27.353: eth0: setting default backend to 1  
** (generate:17795): DEBUG: 15:24:27.353: Configuration is valid  
** (generate:17795): DEBUG: 15:24:27.353: Generating output files..  
** (generate:17795): DEBUG: 15:24:27.354: NetworkManager: definition eth0 is not for us (backend 1)   

i have to say that last line is a bit confusing. what does it mean?  
anyway, beyond the ssh session i'm using i haven't tested these settings. i'm gonna reboot the pi and then i'll see what i can see... 
and why the hell does this forum keep screwing up my posts???

---

### Post by TheFu on 2020-05-30
Are you positive that eth0 is the correct device?

---

### Post by hmiersch on 2020-05-30
ifconfig lists 2 interfaces: eth0: at 192.168.1.6 and lo: at 127.0.0.1
wifi is not configured.

---

### Post by LHammonds on 2020-05-30
ifconfig?  I suppose you installed that utility because it does not exist in the base install.

If you are unsure about the network card name, here is how you can get a network device name list:

```
ls /sys/class/net
[COLOR=#40e0d0]ens32  lo[/COLOR]
```

And here is how you can get the status of each device:

```
ip -o link show | awk '{print $2,$9}'
lo: UNKNOWN
ens32: UP
```

Here is an example output of my good/working setup (notice the red line "Configuration is valid"):

```

netplan --debug generate
DEBUG:command generate: running ['/lib/netplan/generate']
** (generate:581450): [COLOR=#008000]DEBUG[/COLOR]: [COLOR=#0000ff]17:18:11.764[/COLOR]: Processing input file /etc/netplan/01-netcfg.yaml..
** (generate:581450): [COLOR=#008000]DEBUG[/COLOR]: [COLOR=#0000ff]17:18:11.764[/COLOR]: starting new processing pass
** (generate:581450): [COLOR=#008000]DEBUG[/COLOR]: [COLOR=#0000ff]17:18:11.764[/COLOR]: We have some netdefs, pass them through a final round of validation
** (generate:581450): [COLOR=#008000]DEBUG[/COLOR]: [COLOR=#0000ff]17:18:11.764[/COLOR]: ens32: setting default backend to 1
** (generate:581450): [COLOR=#008000]DEBUG[/COLOR]: [COLOR=#0000ff]17:18:11.764[/COLOR]: [COLOR=#ff0000]Configuration is valid[/COLOR]
** (generate:581450): [COLOR=#008000]DEBUG[/COLOR]: [COLOR=#0000ff]17:18:11.764[/COLOR]: Generating output files..
** (generate:581450): [COLOR=#008000]DEBUG[/COLOR]: [COLOR=#0000ff]17:18:11.764[/COLOR]: NetworkManager: definition ens32 is not for us (backend 1)
(generate:581450): GLib-[COLOR=#008000]DEBUG[/COLOR]: [COLOR=#0000ff]17:18:11.764[/COLOR]: posix_spawn avoided (fd close requested)

```

LHammonds

---

### Post by hmiersch on 2020-05-31
i don't remember installing ifconfig. are you sure it didn't come with the raspberry pi version of 18.04?  

anyway, ls /sys/class/net gives me the following output:  

eth0  lo  wlan0

---

### Post by LHammonds on 2020-05-31
> **hmiersch said:**
> i'm downloading the server version of ubuntu  20.04 for my raspberry pi

> **hmiersch said:**
> i don't remember installing ifconfig. are you sure it didn't come with the raspberry pi version of 18.04?
Say what?  Your initial post said 20.04.  I have not installed the ARM version of Ubuntu but I would assume 20.04 is using the same networking component which is netplan unless there is something broken with ARM+Netplan.  But if the OS is using /etc/network/interfaces instead of /etc/netplan, then you need to edit the right network file.  Netplan was introduced in 18.04 and is still used in 20.04.

> **hmiersch said:**
> anyway, ls /sys/class/net gives me the following output:  

eth0  lo  wlan0Then you have indeed confirmed you were right using "eth0" as the device name.  So, did you ever do "netplan --debug apply" and see if you can ping your router and then someplace on the internet like 1.1.1.1?

LHammonds

---

### Post by coconutdog2 on 2020-07-19
In Ubuntu 20.04, ifconfig has to be installed, it does not come as standard. Do the following to install:

> apt install -y net-tools

otherwise use:

> ip a

I prefer ifconfig, it is neater.

---

