---
title: "ubuntu server failed to start network time syncronisation"
date: 2020-06-01
forum: Server Platforms
---

### Post by arthurd3nt on 2020-06-01
Hello,

I have a server with ubuntu 18.04.4 installed. The server was working fine, no errors or issues. 

This morning I decided to install Samba to share some stuff over my network, I installed and configured everything and it worked fine. 
After the installation I shutdown the server and when I try to boot back up i get the following error:
```

[ERROR] failed to start Network Time sycronisation

```

and many others cause by that error, this leads to a loop and it's impossible for the machine to boot.

I tried the following things:
[LIST]
[*]Booting into recovery mode and trying to enable networking, nothing happens, no errors but networking is not enabled
[*]When I do ifconfig I have no network interfaces
[*]Using the lspci command returns the output i was expecting, all 4 interfaces are there so I assume it's not a hardware issue
[*]Eth0,1,2,3 are nowhere to be found in /etc/network/interfaces and even adding eth0 manually doesn't change a thing
[/LIST]

If this is the wrong place to post this I'm sorry, I will move this in another place, it's my first post on the forum so please be kind.

---

### Post by LHammonds on 2020-06-01
I assume you have Ubuntu installed on bare-metal (physical) machine rather than inside a virtual machine.

Is the BIOS time correct?  If the CMOS battery is dead, it is possible that the year gets reset to 1980 which can cause havoc on a system.

If the system is not showing any ethernet devices, I have to wonder if something got corrupted or if your motherboard is failing.

I would stick a CD-ROM into the drive that has Ubuntu Desktop on it and see if that boots up in a "try-before-you-buy" scenario without installing.  Then see if the CD version can see the network device(s) to see if we are looking at a configuration/corruption problem or if your hardware is failing.

**EDIT**: Because you made recent changes (installed Samba), there is a high likelihood that commands you issued (or changes made to files) caused the problem.  So if hardware is not the problem and Ubuntu live image is running, mount the root file system and look at the home directory of the user you used to issue those commands and examine the ~/.bash_history file to see the commands you issued to see if that clues you into the problem area.

LHammonds

---

### Post by SeijiSensei on 2020-06-01
Let's see the results of these commands:

```

date
sudo hwclock

```

You could make your server an NTP server by installing the ntp package.  Then it will synchronize itself with other Internet time servers.

---

### Post by arthurd3nt on 2020-06-01
Thanks for the answer:
[LIST]
[*]I checked on the bios and the date and time are fine, the time zone it's wrong (could this be the cause?)
[*]I booted a usb media with ubuntu live and all the ethernet intefaces are recognised
[*] I checked my bash_history file for both root and my user and there is nothing that could cause any issue, the last root command is the reboot command (idk why i did sudo su instead of simply sudo but doesn't seem like i did anything before that with root user)
[*]date and hwclock ouputs are the same as the bios clock
[/LIST]

Changing the bios time with the correct one didn't resolved the issue

EDIT:
I just remembered that I enabled ufw before rebooting, could this be a firewall issue? -> disabling ufw didn't change a thing

---

### Post by SeijiSensei on 2020-06-01
If you have no network interfaces, that's the problem, and it's much bigger than just time sync.

18.04 uses netplan, not /etc/network/interfaces, to activate interfaces and assign them IP addresses.  See [https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-18-04-bionic-beaver-linux) or an equivalent HOWTO.

---

### Post by LHammonds on 2020-06-01
Wait a second, you were looking for network settings in /etc/network/interfaces?

That is the default location for Ubuntu 16.04 and lower.  Since 18.04, the default has been the use of Netplan and its configuration file is located in /etc/netplan/

The command to see your IP address for 18.04+ (assuming you did not change the network software) is:

```
ip address
```

ifconfig is still installed by default (i think) on 18.04 but is not part of the base install in 20.04 (you would have to install net-tools to get it now).

**EDIT:** An example of how I setup netplan can be [found here]("https://hammondslegacy.com/forum/viewtopic.php?p=616#p616").

LHammonds

---

### Post by arthurd3nt on 2020-06-02
Thanks again for the answers.

ip address outputs this:
[ATTACH=CONFIG]286066[/ATTACH]

ifconfig outputs this:
[ATTACH=CONFIG]286067[/ATTACH]

The netplan config file is:
```

network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: true
    eno2:
      dhcp4: true
    eno3:
      dhcp4: true
    eno4:
      dhcp4: true

```

Now I edited it to this:
```

network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: no
      addresses: [172.16.0.209/24]
      gateway4: 172.16.0.1
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
    eno2:
      dhcp4: true
    eno3:
      dhcp4: true
    eno4:
      dhcp4: true

```
because eno1 is the only one connected

Doing "netplan --debug generate" outputs this:
[ATTACH=CONFIG]286065[/ATTACH]

I rebooted and still no changes.

---

### Post by LHammonds on 2020-06-02
Let's verify the network card name (they might not be eno), here is how you can get a network device name list:

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

LHammonds

---

### Post by arthurd3nt on 2020-06-02
The outputs of what you told me to do are these:
[ATTACH=CONFIG]286068[/ATTACH]

Thanks again

---

### Post by LHammonds on 2020-06-02
Ok, so we are looking at physical layer 1 issue which means we need to verify that the cable is plugged in and working (maybe even swap the network cable or plug into a different port in the switch).  But the 1st and easiest thing to try first is to make sure it is even enabled.

You said eno1 is the device that should be in use so let's make sure it is enabled:
```
ip link set eno1 up
```
Check status with:
```
ip -br link show
```

If that makes no difference in status, check/trace the physical hardware.

LHammonds

---

### Post by arthurd3nt on 2020-06-02
Ok, I've used "ip link set eno1 up"

and "ip -br link show" outuput is:
[ATTACH=CONFIG]286069[/ATTACH]

If I try to ping I get:
```

connect: Network is unreachable

```

When I try to reboot (without safe mode) error persist.
After rebooting again into safe mode the interface is down again.

EDIT
I tried to change cable, same result 
I changed swich port and even connected directly to the router doesn't change nothing
Also when I booted with ubuntu desktop live everything worked fine

Thanks for the immense patience

---

### Post by LHammonds on 2020-06-02
Your posted /etc/netplan config "looks" valid...but if you change dhcp back to yes, do you get the same results of the nic staying down after you do "netplan --debug generate" and "netplan --debug apply"?

There should be no need to reboot unless you are testing that the nic will continue working after a reboot.

Can you ping 1.1.1.1 after setting nic to dhcp?  If so, what does "ip address" look like while in dhcp mode?

I am curious if DHCP is working and what the range is for addresses being issued verses what is guarenteed static addresses you can make use of.

When you get a good DHCP address, I want you to ping the static IP you are trying to use just to verify it is not currently in use by another device.

LHammonds

---

### Post by arthurd3nt on 2020-06-02
"netplan -- debug generate" and "netplan --debug apply" outputs:

```

DEBUG:netplan generated networkd configuration changed, restarting networkd
Failed to list units: Connection timed out
Failed to expand names: Connection timed out
Traceback (most recent call last):
File "/usr/sbin/netplan", line 23, in <module>
netplan.main()

File "/usr/share/netplan/netplan/cli/core.puâ€œ, line 50, in main
self.run_connand()

File â€œ/usr/share/netplan/netplan/cli/utils.py, line 186, in run_command
self.func()

File "/usr/share/netplan/netplan/cli/commands/apply.py", line 46, in run
self.run_command()

File "/usr/share/netplan/netplan/cli/utils.py". line 186, in run_command
self.func()

File "/usr/share/netplan/netplan/cli/commands/applg.pg", line 116, in command.
30019
utils.sgstemctl_networkd('stop', sync=sgnc. extra-services=mpa_services)
File "/usr/share/netolan/netplan/oli/utils.py, line as, in systemctl_netmorkt
subprocess.check.call(command)

File "/usr/lib/pgthona.6/subnrocess.pg". line 311. in check_call
raise CalledProcessError(retcode. cmd)

NetworKManager: definition eno4 is not

subprocess.CalledProoessError: Command 'systemctl', 'stop', '-- no-block', 'sys subprocess.check_call(command)
temdâ€”networkd.service', 'netplanâ€”wpa-*.service ] returned non-zero exit status
```

ip -br link show says the interface is up

(for some reason I cannot attach images to this thread anymore, when i click upload it does nothing i used a image to text converter sorry if it looks messy)

pinging 1.1.1.1 says network unreachable

pinging the previous static address with another machine:

```

frama@dell:~$ ping 172.16.0.209
PING 172.16.0.209 (172.16.0.209) 56(84) bytes of data.
From 172.16.0.236 icmp_seq=1 Destination Host Unreachable
From 172.16.0.236 icmp_seq=2 Destination Host Unreachable
From 172.16.0.236 icmp_seq=3 Destination Host Unreachable
^C
--- 172.16.0.209 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5093ms
pipe 4



```

---

### Post by LHammonds on 2020-06-02
Well, don't worry about screenshots at this point then.  Just the crux of the output will do.

Can you ping 1.1.1.1 successfully or does it timeout?

What IP address are you assigned as shown by "ip address" on eno1? ( **EDIT**: assuming you changed it back to DHCP.)

LHammonds

---

### Post by arthurd3nt on 2020-06-02
pinging 1.1.1.1
```

connect: network is unreachable 

```

ip address on eno1 (yes it's set to DHCP)

```

2: enol: <BROADCAST, MULTICAST, UP, LDHER_ UP> mtu 1500 qdisc mq state UP group default qlen 1000

link/ether fo:4d:az:00:cb:'37 brd ff:ff:ff:ff:ff:ff

inetE. feBo: ::f24d a2ff: feoo: cb97/64 scope link
valid_lft forever preferred_lft forever
```

---

### Post by LHammonds on 2020-06-02
From what I can see, it looks like just an IPv6 IP address ("inet6" line...and no "inet" line) that DHCP picked up and not an IPv4 address similar to what you were wanting to use (172.16.0.???).

Are there other devices working on your network?  Do they use DHCP?  What kind of IP addresses do they get?

If your router is the device handing out DHCP, what range is it configured to hand out?

LHammonds

---

### Post by arthurd3nt on 2020-06-02
Yes there are other devices on my network, as an example:

ifconfig on my laptop
```

frama@dell:~$ ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3200  bytes 323009 (323.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3200  bytes 323009 (323.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp59s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.16.0.236  netmask 255.255.255.0  broadcast 172.16.0.255
        inet6 fe80::dfaa:385e:ce5a:209  prefixlen 64  scopeid 0x20<link>
        ether 9c:b6:d0:bb:b2:cf  txqueuelen 1000  (Ethernet)
        RX packets 67891  bytes 38931005 (38.9 MB)
        RX errors 0  dropped 2633  overruns 0  frame 0
        TX packets 39096  bytes 11559352 (11.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



```

I have no control over my router ad dhcp server sadly, is there a way for me to know the range?

---

### Post by LHammonds on 2020-06-02
> **arthurd3nt said:**
> I have no control over my router ad dhcp server sadly, is there a way for me to know the range?If you do not have access, the best you can do is guess based on what it hands out.

172.16.0.236 / 255.255.255.0 is a class C network so you should have 254 addresses from 172.16.0.1 (probably your router) to 172.16.0.255 (reserved broadcast IP)

Look at all your other devices and if they are all over 200, then it might be safe to assume DHCP range is 200+

I would scan all the IP addresses to see what is/is not active to also get a feel for what you have and mark down which of those addresses you have configured as static.

Also, make sure your router/gateway is 172.16.0.1 by looking at your laptop that has working DHCP and type:
```
ip route
``` and see if it says "default via 172.16.0.1"

**EDIT #1:** Since you don't have the option to install nmap or other scanner utilities, here is a script you can use to show all active IP addresses (that respond to ICMP pings)

To create the script, do this:
```

touch ~/ping-subnet.sh
chmod 755 ~/ping-subnet.sh

```

Now edit the script and past the following into it:
```

#!/bin/bash
#############################################################
## Name          : ping-subnet
## Version       : 1.0
## Date          : 2020-06-02
## Author        : LHammonds
## Purpose       : Ping subnet to find active IP addresses.
## Compatibility : Verified on Ubuntu Server 20.04 LTS
## Requirements  : None
## Run Frequency : Run as needed.
## Parameters    :
##    1 = (Optional) Subnet prefix.  e.g. 192.168.0
## Exit Codes    : None
###################### CHANGE LOG ###########################
## DATE       VER WHO WHAT WAS CHANGED
## ---------- --- --- ---------------------------------------
## 2020-06-02 1.0 LTH Created script.
#############################################################

ColorReset="\033[0m"
ColorActive="\033[01;32m"
ColorInactive="\033[01;31m"

## Check existance of optional command-line parameter.
case "$1" in
  "")
    Subnet="172.16.0"
    ;;
  *)
    Subnet="${1}"
    ;;
esac

function f_ping()
{
  if ping -w 2 -q -c 1 ${Subnet}.${1} > /dev/null ; then
    echo -e "Active IP:${ColorActive}" ${Subnet}.${1} ${ColorReset}
#  else
#    echo -e "No Response:${ColorInactive}" ${Subnet}.${1} ${ColorReset}
  fi
}

index=1
while [ ${index} -lt 255  ]; do
  f_ping ${index} &
  index=$(expr ${index} + 1)
  sleep 0.1
done

```

If you type ~/ping-subnet.sh it should being scanning your subnet for IP addresses that respond to a ping request.  You can also pass it a parameter to scan a different subnet than what you specified such as "~/ping-subnet.sh 192.168.0" which will look at 192.168.0.1 thru 192.168.0.254

**EDIT #2:** I just realized 10 seconds after posting the script that you would be running this from your working laptop...and thus could install nmap or other scanners.  *Derp*  Well, you can use this script now and not have to install anything. LoL.

LHammonds

---

### Post by arthurd3nt on 2020-06-03
Wow, thanks a lot for the help. I will try this in 3 hour from now

EDIT:
Couldn't wait to do this LoL.

ip route output:
```
default via 172.16.0.1 dev wlp59s0 proto dhcp metric 600 
169.254.0.0/16 dev wlp59s0 scope link metric 1000 
172.16.0.0/24 dev wlp59s0 proto kernel scope link src 172.16.0.236 metric 600
```

ping-subnet script output
```
Active IP: 172.16.0.1 
Active IP: 172.16.0.212 
Active IP: 172.16.0.215 
Active IP: 172.16.0.217 
Active IP: 172.16.0.226 
Active IP: 172.16.0.235 
Active IP: 172.16.0.236 
Active IP: 172.16.0.234 
Active IP: 172.16.0.242 
Active IP: 172.16.0.243 
Active IP: 172.16.0.248 

```

Thanks for the useful script :)

---

### Post by LHammonds on 2020-06-03
Well, assuming none of those were statically assigned, we can plainly see 212 thru 248 have been assigned via DHCP.  DHCP servers typically assign the lowest IP, then the next in line and so on.  These numbers jump around and look like they "might" have reached the top of what it can assign.  So the DHCP server might need to recycle previously handed out IPs but depending on how that is setup, it may or may not be able to find one to lease.  Small potential of a problem but let's not ignore it.  Since you do not have access to see the settings to know if a problem with it exists, can you at least reboot / unpower the device that hands out the IPs?

After you reboot the DHCP server, be sure to power up all 10 devices that request an IP, run that IP scanning script again and see if it starts at 212 and goes to 222.   I would not be surprised if the DHCP pool is 200-250 or 210-250.

But regardless of the DHCP server reboot, it seems any static IP you pick between 2 and 199 should be safe...assuming all active devices responded to the ping request (which some do not).

So, instead of picking 209 for your server's static IP, it would be safer to pick a lower number.  I recommend 172.16.0.100/24 with the gateway4 pointing to 172.16.0.1 (which we verified as the gateway assigned by DHCP and is active to ping request)

LHammonds

---

### Post by arthurd3nt on 2020-06-03
So, I rebooted my router/dhcp server and I ran your script:
```

frama@dell:~$ ./ping-subnet.sh
Active IP: 172.16.0.1 
Active IP: 172.16.0.212 
Active IP: 172.16.0.215 
Active IP: 172.16.0.226 
Active IP: 172.16.0.236 
Active IP: 172.16.0.242 
Active IP: 172.16.0.248 

``` 

I also changed the server ip adress to 172.16.0.100/24 and nothing changed, network still unreachable

I we cannot fix this do you think reinstalling ubuntu will fix it? everything worked with the "try before installation" approach.

EDIT:
I was thinking that maybe we could investigate the fact that the server fails to boot, seems strange that it won't boot because it has no Ethernet connection

---

### Post by LHammonds on 2020-06-03
Well, something is definitely off kilter which is why I suggested looking through your command history earlier to see if anything stuck out as dangerous.

Another thing you can do is remove the software you installed.  So everywhere in your command history where you recently typed "apt install" then type "apt remove" which sounds like it is mainly just samba.  I just don't know what in Samba would prevent the network card from working or the server from booting.

If you re-install, make sure you have a backup of any data or configuration files that you have on it.  I would actually create another server in a virtual machine and try to get all the data/configs onto it so that you know you have a 2nd working copy.  You can use Oracle VirtualBox to create a virtual machine on your desktop/laptop.

LHammonds

---

### Post by arthurd3nt on 2020-06-03
I will do a reinstall, luckily I have all my config files/docker-compose stuff all backed up, I will first try do that on vbox to be sure.

Thanks a lot for the patience and the time you have dedicated to this, I really appreciated it.

---

