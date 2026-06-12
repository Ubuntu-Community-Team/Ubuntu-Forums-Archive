---
title: "static ip"
date: 2024-04-26
forum: Server Platforms
---

### Post by greg612 on 2024-04-26
Hello   Ever since the last update of 22.04 something changed in the way they are using ip's. The ip i used for a very long time no longer worked.  So I decided to update to 24.04 hoping the fix was in there  ......  well no its not  Works out of box  just dont set static ip  you will lose internet everytime.  The static ip works  just no internet... which in turn makes this server useless to me

---

### Post by TheFu on 2024-04-26
Which distro package?  The ISO filename would be helpful to see if others have the same experience.

Sometimes, multiple, unrelated, issues happen at the same time.  It is rare, but it does happen.

Of course, trying a different cable and using a different port on the switch/router.

---

### Post by greg612 on 2024-04-26
ubuntu server 24.04,    ubuntu-24.04-live-server-amd64.iso 

  But it started with the last update to 22.04 ubuntu server.  

I guess it was about two weeks ago.  It all works but internet.

I also noticed in 24.04 cant use a renderer  neither networkd  or NetworkManager .  I tried both it wont even give a good addy. I have to log directly into server take either of them totally out    

Thats new to me anyway

---

### Post by TheFu on 2024-04-26
Looking at my 22.04 systems (none are production), 

at a VPS, I have this configuration:
```
$ sudo more /etc/netplan/50-cloud-init.yaml 
network:
    version: 2
    ethernets:
        enp1s0:
            dhcp4: true
            match:
                macaddress: 56:00:04:7c:06:94
            set-name: enp1s0

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:        22.04
Codename:       jammy

```

And for a VM that I've been playing around with:
```
$ more /etc/netplan/00-installer-config.yaml 
# This is the network config written by 'subiquity'
network:
  ethernets:
    enp1s0:
      addresses:
      - 172.22.22.70/24
      gateway4: 172.22.22.1
      nameservers:
        addresses:
        - 172.22.22.80
        - 172.22.22.81
        search:
        - example.foo
        - example.com
  version: 2

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:        22.04
Codename:       jammy

```

Not seeing any issues with either for LAN or internet connectivity.  Perhaps this weekend I'll try a play 24.04 install.  All my systems use Intel NICs, but both of the 22.04 systems are virtual machines.  I don't have any physical installs with any release except 20.04.6.  Stability matters most to me, so I'm slow to upgrade.

---

### Post by MAFoElffen on 2024-04-27
Backup please.

What do you think changed with networking and what diagnostics did you do?

It doesn't sound like you did enough in your diagnostics... Like checking to see if you had DNS Resolv(?)

Do this please and post the (replicated) results
```

ping -c 4 google.com
ping -c 4 8.8.8.8
sudo systemctl status systemd-resolved --no-pager

```
You think you might have done that before deciding it was something that 'changed' in how networking worked, and it required you to upgrade the release?

Not saying that upgrading Server Edition releases is a bad idea. Server Edition 24.04 LTS has some great improvements and features... But if it were me, I would research what is happening first, before such a big leap. 

Being I'm on the Server Team, and trying to support Server Edition and Virtualization issues here. I sort of have a vested interest in what is going on. 

22.04.4 is stable. I like 24.04, but I personally don't feel a Server Edition LTS release is "production class" (certified) Stable until the first point release, which usually occurs in August of the release year. I usually upgrade my own 'favored' machines, at least until after a few weeks after the release, when things settle in the Repo's.

I think TheFu has some thoughts on that with his 'own'.

Maybe that's just me.

---

### Post by TheFu on 2024-04-27
When I patched this morning, I did see cloud-init was updated. Since I don't use that package for anything, wish it would just go away, I'm definitely not impacted.  

I don't use systemd-resolved ... after having an issue with it when it was first introduced.  I point my resolv.conf to my LAN DNS servers, so having a local caching DNS is pretty useless to me.  People with laptops or not on a well-managed network would probably be happier using systemd-resolved and fixing that issue, if it was the root cause of the "networking" problems described.

I don't move to new server releases until my current releases have less than 6 months remaining for support OR there is a compelling reason to migrated.  That usually doesn't happen, though I do play with newer releases, just outside any production needs.  For play stuff, new can be fun.  I've already pulled 3 variants of 24.04 down to play with at my LUG meeting tomorrow.  The first systems that might get 24.04 around here will be bog-standard servers that don't have any external, funny, dependencies.  So, stuff like an email gateway or a VPN server.  Those use only Canonical repos.  There are external system dependencies, so finding those sooner than later isn't bad.  I've been tripped by my backup tool version being incompatible between two different LTS releases.  That forced some solutions to be considered and I tried a few options.  After a bit, the newer backup software version was back-ported to the older release.  A few years later, I migrated the backups to a different, newer, server with a newer OS and created a container with the older backup software version for the few older systems that still needed that older backup software.

Migrating to a new release hoping it will fix existing issues is seldom a good idea. The issues with the old version generally are brought forward.

Anyway, new releases always bring incompatible dependencies. If not on the system, with external dependent systems.

---

### Post by greg612 on 2024-04-27
network:
    ethernets:
        eno1:
          dhcp4: no
          dhcp6: no
          addresses: [192.168.25.3/24]
          routes:
              - to: default
                via: 192.168.25.1
          nameservers:
                addresses: [ "9.9.9.9", "149.112.112.112" ]
    version: 2

This is what I have used for a long time. worked fine till update on 22.04 just before new release.

When I lost all internet I thought the fix was in 24.04  My Bad on that.

And yes i usually wait a month or so before major upgrade.

everything works now except internet

ames@mustang:/$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^Z
[1]+  Stopped                 ping 8.8.8.8   ( I stopped this took forever)
james@mustang:/$ ping google.com
ping: google.com: Temporary failure in name resolution

thats what i get since 22.04 update

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 24.04 LTS
Release:        24.04
Codename:       noble

---

### Post by greg612 on 2024-04-27
```
network:
    ethernets:
        eno1:
          dhcp4: no
          dhcp6: no
          addresses: [192.168.25.3/24]
          routes:
              - to: default
                via: 192.168.25.1
          nameservers:
                addresses: [ "9.9.9.9", "149.112.112.112" ]
    version: 2
```

Nmap scan report for _gateway (192.168.25.1)
Host is up (0.0015s latency).
Nmap scan report for 192.168.25.3
Host is up (0.00069s latency).

---

### Post by TheFu on 2024-04-27
If you don't use forum code tags, the indentation is lost.  _YOU MUST EDIT_ the posts and wrap terminal output (and commands) in _[COLOR="#FF0000"]**code-tags**[/COLOR]_ for anyone to be able to know anything about your netplan.yaml file.  It is best to use them for all terminal output so it is clear, but things where whitespace is critical make it mandatory.
Forum code tags: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)  But it is really easy. Use like quote/bold/underline/italics, just with 'code'. The advanced editor has a '#' button to make it easier.  I use quote tags, then just replace the 2 places that have  "QUOTE"  with "code". Easy.

---

### Post by greg612 on 2024-04-27
```
systemd-resolved.service - Network Name Resolution
     Loaded: loaded (/usr/lib/systemd/system/systemd-resolved.service; enabled; preset: enabled)
     Active: active (running) since Fri 2024-04-26 16:40:06 CDT; 22h ago
       Docs: man:systemd-resolved.service(8)
             man:org.freedesktop.resolve1(5)
             https://www.freedesktop.org/wiki/Software/systemd/writing-network-configuration-managers
             https://www.freedesktop.org/wiki/Software/systemd/writing-resolver-clients
   Main PID: 810 (systemd-resolve)
     Status: "Processing requests..."
      Tasks: 1 (limit: 38294)
     Memory: 7.8M (peak: 8.3M)
        CPU: 5.801s
     CGroup: /system.slice/systemd-resolved.service
             &#9492;&#9472;810 /usr/lib/systemd/systemd-resolved

Apr 27 15:05:49 mustang systemd-resolved[810]: Using degraded feature set UDP instead of TCP for DNS server 149.112.112.112.
Apr 27 15:05:54 mustang systemd-resolved[810]: Using degraded feature set TCP instead of UDP for DNS server 9.9.9.9.
Apr 27 15:06:04 mustang systemd-resolved[810]: Using degraded feature set TCP instead of UDP for DNS server 149.112.112.112.
Apr 27 15:06:14 mustang systemd-resolved[810]: Using degraded feature set UDP instead of TCP for DNS server 9.9.9.9.
Apr 27 15:06:19 mustang systemd-resolved[810]: Using degraded feature set UDP instead of TCP for DNS server 149.112.112.112.
Apr 27 15:06:24 mustang systemd-resolved[810]: Using degraded feature set TCP instead of UDP for DNS server 9.9.9.9.
Apr 27 15:06:34 mustang systemd-resolved[810]: Using degraded feature set TCP instead of UDP for DNS server 149.112.112.112.
Apr 27 15:06:54 mustang systemd-resolved[810]: Using degraded feature set UDP instead of TCP for DNS server 149.112.112.112.
Apr 27 15:06:59 mustang systemd-resolved[810]: Using degraded feature set UDP instead of TCP for DNS server 9.9.9.9.
Apr 27 15:07:04 mustang systemd-resolved[810]: Using degraded feature set TCP instead of UDP for DNS server 149.112.112.112.
```

---

### Post by greg612 on 2024-04-27
after waiting for a bit:

```
systemd-resolved.service - Network Name Resolution
     Loaded: loaded (/usr/lib/systemd/system/systemd-resolved.service; enabled; preset: enabled)
     Active: active (running) since Fri 2024-04-26 16:40:06 CDT; 22h ago
       Docs: man:systemd-resolved.service(8)
             man:org.freedesktop.resolve1(5)
             https://www.freedesktop.org/wiki/Software/systemd/writing-network-configuration-managers
             https://www.freedesktop.org/wiki/Software/systemd/writing-resolver-clients
   Main PID: 810 (systemd-resolve)
     Status: "Processing requests..."
      Tasks: 1 (limit: 38294)
     Memory: 7.8M (peak: 8.3M)
        CPU: 5.876s
     CGroup: /system.slice/systemd-resolved.service
             &#9492;&#9472;810 /usr/lib/systemd/systemd-resolved

```


Status is still processing requests Looks stuck to me

---

### Post by The Cog on 2024-04-27
Do please use code tags when posting code (while editing click Go Advanced, and use the '#'  at the top). That way you can retain the indentation, which is critical for yaml files.
Can you also post the results of the commands **[FONT=Courier New]ip addr[/FONT]** and **[FONT=Courier New]ip route[/FONT]**

---

### Post by greg612 on 2024-04-27
```
 ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether f8:b1:56:e4:ca:fc brd ff:ff:ff:ff:ff:ff
    altname enp0s25
    inet 192.168.25.3/24 brd 192.168.25.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet6 fe80::fab1:56ff:fee4:cafc/64 scope link 
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:55:9c:7a:54 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
```

---

### Post by greg612 on 2024-04-27
```
default via 192.168.25.1 dev eno1 proto static 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 
192.168.25.0/24 dev eno1 proto kernel scope link src 192.168.25.3 
```

---

### Post by The Cog on 2024-04-28
I don't see anything wrong with your netplan file other than it doesn't set the renderer (I gather the default is networkd). 
I don't see anything wrong with the routing - IP addresses and the routing table look sensible.

Just testing connectivity, please can you try **[FONT=Courier New]ping -c3 8.8.8.8[/FONT]** and post the result. If no reply, please the use the command **[FONT=Courier New]ip nei[/FONT]** to list the known neighbours. We *should* should see the IP address of your gateway as a neighbour, even if you don't get a ping result (maybe the router doesn't answer pings). Also, try **[FONT=Courier New]ping -c3 8.8.8.8[/FONT]**. Between them we should get an idea how far your connectivity is working.

A couple of off-topic hints:
- When viewing files, **less** is a better viewer than **more** because you can scroll and text-search the view. If you just want to print the file content, **cat** is the program to use.
- When you want to stop a process, Ctrl-C is the key to use. Ctrl-Z (which is what you would use in Windows) just pauses the process and puts it into the background (use **fg** to bring it back to the foreground).

---

### Post by TheFu on 2024-04-28
I'd like to know if this device can ping other devices on the same LAN/subnet.  If so, then we assume it isn't a driver issue.  Time to start looking external to the system - in other network equipment.

If not, it is probably a driver issue and things get ugly.  **inxi -Nxxz** will show the driver and some details.  There are lots of commands that can do something similar, but not as nice to read.  **lspci**, **lshw** are some of the other commands.

---

### Post by greg612 on 2024-04-28
if i use any renderer I get no ips  or something real weird.   I have tried networkd  and NetworkManager and I have to take them off to get it to work.  I have to physically get into server to take out.  as far as ping goes i can ping everything on my network 

but cant ping anything on internet

will post results soon  have to fix a garage door for mother in law

everything works but internet on server can ping i am typing this from my laptop on same system

---

### Post by TheFu on 2024-04-28
Well, without a renderer, I'm surprised that any IP is being provided that isn't DHCP.

If you cannot ping the internet, then I don't see how any external DNS will work.  BTW, it cannot.

If there aren't any firewall rules preventing outbound connections, then the problem is 99.9% somewhere else - like in the router or switch configs.

The only time I've had any issue where the LAN was 100% fine and the internet wasn't that didn't get traced back to a network misconfiguration external to Linux, it was a strange bug in QEMU with networking.  All the VMs on 1 machine worked perfect, but 1 of them didn't.  This was before netplan.  Never figured our a solution.  Happened a 3 times over a 6th month period, but most of the time everything worked.  I migrated off a full VM to separate Linux Containers for those services and never saw the issue again.  The same VM host is still being used and all the other VMs on it haven't had any unexpected (i.e. bonehead, self-inflicted) issues.

Anyway, here's another netplan.yaml file that uses the more modern "via" method.  Of course, don't forget to run **sudo netplan generate** and **sudo netplan apply** after any changed.  You can add the **--debug** switch to get more output that might trace issues with the netplan,yaml input.  YAML is picky, so getting spacing (never tabs!) correct is important.

```
network:
  version: 2
  renderer: networkd
  ethernets:
     ens3:
       addresses:
          - 172.22.22.5/24
       dhcp4: false
       dhcp6: false
       routes:
         - to: default
           via: 172.22.22.1
       optional: true
       nameservers:
         addresses: [ "172.22.22.81","172.22.22.80" ]
         search: [example.foo,example.com]
```

Anyway, another point of reference.

---

### Post by greg612 on 2024-04-28
I will try that  but what u said got me curious so i dug out the ethernet cable from server and im typing this from that  so switches routers all work.   Server is fresh install no firewall active on it.

Like i said everything worked it had internet all that til I made a static ip 

This all started with 22.04 last update it lost it then  never could get it back     Thats why i tried the 24.04  but still there 

I dont know never ran into anything like this     I can put it back to dynamic but thats going to be a real pain in ---  every time the ip changes

i agree about renderer but it wont have it in yaml  that causes real problems  I get weird ip    then have to have keyboard on server to fix  dont understand that either. 

I never seen anything like this....   This always worked before   total lost here on static ip

---

### Post by TheFu on 2024-04-28
Swap the switch port used. Sometimes 1 switch port will have issues that others do not.

---

### Post by greg612 on 2024-04-28
same thing

---

### Post by greg612 on 2024-04-28
```
~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2049ms


```

---

### Post by greg612 on 2024-04-28
```
ip nei
192.168.25.53 dev eno1 lladdr f8:0d:ac:10:85:09 REACHABLE 
192.168.25.55 dev eno1 lladdr 3c:52:82:d9:39:fc REACHABLE 
192.168.25.1 dev eno1 lladdr ac:15:a2:6e:36:32 REACHABLE 

```

---

### Post by greg612 on 2024-04-28
```
 ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2046ms
```

---

### Post by greg612 on 2024-04-28
theFU:   this is after I installed your yaml  networkd is now working it didnt go all weird on me and kept ip this time But still no internet  <<<<<<<<<<<<<bangs head against wall

```
sudo netplan status --all
     Online state: online
    DNS Addresses: 127.0.0.53 (stub)
       DNS Search: .

&#9679;  1: lo ethernet UNKNOWN/UP (unmanaged)
      MAC Address: 00:00:00:00:00:00
        Addresses: 127.0.0.1/8
                   ::1/128

&#9679;  2: eno1 ethernet UP (networkd: eno1)
      MAC Address: f8:b1:56:e4:ca:fc (Intel Corporation)
        Addresses: 192.168.25.3/24
                   fe80::fab1:56ff:fee4:cafc/64 (link)
    DNS Addresses: 9.9.9.9
                   149.112.112.112
           Routes: default via 192.168.25.1 (static)
                   192.168.25.0/24 from 192.168.25.3 (link)
                   fe80::/64 metric 256

&#9679;  3: docker0 bridge DOWN/UP (unmanaged)
      MAC Address: 02:42:55:9c:7a:54
        Addresses: 172.17.0.1/16
           Routes: 172.17.0.0/16 from 172.17.0.1 (link)
```

---

### Post by greg612 on 2024-04-28
```
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/usr/lib/systemd/system/NetworkManager.service; enabled; preset: enabled)
     Active: active (running) since Sun 2024-04-28 17:14:30 CDT; 1h 27min ago
       Docs: man:NetworkManager(8)
   Main PID: 894 (NetworkManager)
      Tasks: 4 (limit: 38294)
     Memory: 25.4M (peak: 42.2M)
        CPU: 268ms
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;894 /usr/sbin/NetworkManager --no-daemon

Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7486] dhcp: init: Using DHCP client 'internal'
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7491] manager: (lo): new Loopback device (/org/freedesktop/NetworkManager/Devices/1)
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7512] manager: (eno1): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7530] failed to open /run/network/ifstate
Apr 28 17:14:30 mustang systemd[1]: Started NetworkManager.service - Network Manager.
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7539] bus-manager: acquired D-Bus service "org.freedesktop.NetworkManager"
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7547] manager: startup complete
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7558] modem-manager: ModemManager available
Apr 28 17:14:31 mustang NetworkManager[894]: <info>  [1714342471.5337] manager: (docker0): new Bridge device (/org/freedesktop/NetworkManager/Devices/3)
Apr 28 17:14:32 mustang NetworkManager[894]: <info>  [1714342472.6463] device (eno1): carrier: link connected
```

---

### Post by greg612 on 2024-04-28
```
sudo journalctl -b 0 -u NetworkManager
Apr 28 17:14:29 mustang systemd[1]: Starting NetworkManager.service - Network Manager...
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.0841] NetworkManager (version 1.46.0) is starting... (boot:5a38b17e-ef6a-4874-a656-3b81bb68c1ca)
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.0842] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, 10-globally-managed-devices.con>
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.0938] manager[0x56a872190a80]: monitoring kernel firmware directory '/lib/firmware'.
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.0938] monitoring ifupdown state file '/run/network/ifstate'.
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1486] hostname: hostname: using hostnamed
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1487] hostname: static hostname changed from (none) to "mustang"
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1507] dns-mgr: init: dns=systemd-resolved rc-manager=unmanaged (auto), plugin=systemd-resolved
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1510] manager[0x56a872190a80]: rfkill: Wi-Fi hardware radio set enabled
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1510] manager[0x56a872190a80]: rfkill: WWAN hardware radio set enabled
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1576] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.46.0/libnm-device-plugin-blueto>
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1595] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.46.0/libnm-device-plugin-team.so)
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1601] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.46.0/libnm-device-plugin-adsl.so)
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1608] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.46.0/libnm-device-plugin-wwan.so)
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1623] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.46.0/libnm-device-plugin-wifi.so)
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1626] manager: rfkill: Wi-Fi enabled by radio killswitch; enabled by state file
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1627] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1628] manager: Networking is enabled by state file
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1643] settings: Loaded settings plugin: ifupdown ("/usr/lib/x86_64-linux-gnu/NetworkManager/1.46.0/libnm-settings-plug>
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1644] settings: Loaded settings plugin: keyfile (internal)
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1644] ifupdown: management mode: unmanaged
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.1647] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7486] dhcp: init: Using DHCP client 'internal'
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7491] manager: (lo): new Loopback device (/org/freedesktop/NetworkManager/Devices/1)
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7512] manager: (eno1): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7530] failed to open /run/network/ifstate
Apr 28 17:14:30 mustang systemd[1]: Started NetworkManager.service - Network Manager.
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7539] bus-manager: acquired D-Bus service "org.freedesktop.NetworkManager"
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7547] manager: startup complete
Apr 28 17:14:30 mustang NetworkManager[894]: <info>  [1714342470.7558] modem-manager: ModemManager available
Apr 28 17:14:31 mustang NetworkManager[894]: <info>  [1714342471.5337] manager: (docker0): new Bridge device (/org/freedesktop/NetworkManager/Devices/3)
Apr 28 17:14:32 mustang NetworkManager[894]: <info>  [1714342472.6463] device (eno1): carrier: link connected
Apr 28 19:20:04 mustang NetworkManager[894]: <info>  [1714350004.0081] manager: disable requested (sleeping: no  enabled: yes)
Apr 28 19:20:04 mustang NetworkManager[894]: <info>  [1714350004.0081] manager: NetworkManager state is now ASLEEP
Apr 28 19:20:04 mustang NetworkManager[894]: <info>  [1714350004.0083] audit: op="networking-control" arg="off" pid=2146 uid=0 result="success"
Apr 28 19:20:04 mustang NetworkManager[894]: <info>  [1714350004.0322] manager: enable requested (sleeping: no  enabled: no)
Apr 28 19:20:04 mustang NetworkManager[894]: <info>  [1714350004.0322] manager: NetworkManager state is now DISCONNECTED
Apr 28 19:20:04 mustang NetworkManager[894]: <info>  [1714350004.0323] audit: op="networking-control" arg="on" pid=2155 uid=0 result="success"
```

---

### Post by TheFu on 2024-04-28
I think the problem is outside the computer, if you are 100% certain no firewall is in the way.  Generally, desktop linux filewalls block inbound, not outbound.

---

### Post by greg612 on 2024-04-28
no firewall and if it was outside  i wouldnt work with a dynamic which it will just not static   thats inside server

---

### Post by greg612 on 2024-04-28
after a quick internet search  This is happening to more than just me  and it all started after last 22.04 update. looking now to see if anyone got it fixed

---

### Post by TheFu on 2024-04-28
> **greg612 said:**
> no firewall and if it was outside  i wouldnt work with a dynamic which it will just not static   thats inside server

Could the Docker bridge be in the way?

---

### Post by MAFoElffen on 2024-04-28
It is wonky, for sure.

You say that if you specify a renderer then it gets confused and has not connect at all. That, I see as the first problem.

You said it was server right? Then it should be systemd.networkd. But your output of errors shows "NetworkManager"... I personally stay away from NetworkManager, and specify networkd as my renderer. I think a lot of us here do that. Even when NetworkManager is working right, it seems to connect/disconnect, and fill logs with errors.

You say you can ping things in your local, by nothing outside of it...

What happens, if per say we set it up for networkd as the renderer...
```

sudo systemctl stop NetworkManager
sudo systemctl disable NetworkManager
sudo systemctl mask NetworkManager
sudo systemctl unmask systemd-networkd
sudo systemctl enable systemd-networkd
sudo systemctl start systemd-networkd

```
systemd.resolved seems to already be enabled and started, so nothing to be done with that...

Copy your NetPlan .yaml file with a .old file extension so it is backed up... Add "renderer: networkd to the active .yaml file. Comment out all the static IP lines and set "dhcp4: yes"... do netplan generate and apply...

Then see if it has connectivity. Post the results of the pings and ip addr within codes tags. Successful or not. That should show us what is there when it is successful (crossing fingers). If not then we can work on that underneath, and then know it isn't something in the static IP defines.

If successful, then uncomment the static IP define lines and change back the "dhcp4: no" line, netplan generate, apply... retest.

That is what I would suggest as a plan for the initial diagnostics of that.

@TheFu -- Early on in the Noble Dev Cycle, I posted that I found where it looks like in the future that they might be trying/wanting to use cloud.init for netplan yaml changes on the first boot, after the install finishes/first boot. The framework in the install image was setup for something like that, but I never saw where they actually touched any of that again, after those initial additions of the hooks to that. When I first saw that, I thought, ah-oh... some changes to how things have worked. But nothing else came of that in the Dev Cycle.

---

### Post by greg612 on 2024-04-28
I will do this and gladly shut off network manager Really dont know why its using it. I put the yaml from thefu in and its renderer is networkd.. I personally dont care for it   ok I will do this

---

### Post by greg612 on 2024-04-28
well this is interesting:
```
 sudo systemctl disable NetworkManager
Removed "/etc/systemd/system/multi-user.target.wants/NetworkManager.service".
Removed "/etc/systemd/system/network-online.target.wants/NetworkManager-wait-online.service".
Removed "/etc/systemd/system/dbus-org.freedesktop.nm-dispatcher.service".
james@mustang:/$ sudo systectl mask NetworkManager
sudo: systectl: command not found
james@mustang:/$ sudo systemctl unmask systemd.networkd
Unit systemd.networkd.service does not exist, proceeding anyway.
james@mustang:/$ sudo systemctl enable systemd.networkd
Failed to enable unit: Unit file systemd.networkd.service does not exist.
```

---

### Post by greg612 on 2024-04-28
after commenting out and regenerating I have internet

```
 ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=117 time=19.0 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=117 time=16.4 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=117 time=16.3 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=117 time=16.7 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=117 time=18.3 ms
^C
--- 8.8.8.8 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 16.263/17.315/18.951/1.105 ms
```

---

### Post by greg612 on 2024-04-28
changed back and well 

```
ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether f8:b1:56:e4:ca:fc brd ff:ff:ff:ff:ff:ff
    altname enp0s25
    inet 192.168.25.3/24 brd 192.168.25.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet 192.168.25.56/24 metric 100 brd 192.168.25.255 scope global secondary dynamic eno1
       valid_lft 7146sec preferred_lft 7146sec
    inet6 fe80::fab1:56ff:fee4:cafc/64 scope link 
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:15:08:54:93 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
james@mustang:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

```     



internet gone

---

### Post by greg612 on 2024-04-28
the ping is still blinking the whole time posting this reply  I will have to stop it

---

### Post by greg612 on 2024-04-28
```
 ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
271 packets transmitted, 0 received, 100% packet loss, time 276474ms


```

---

### Post by greg612 on 2024-04-28
when I comment all static out I get this and it works


```
ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=117 time=18.3 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=117 time=17.1 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=117 time=16.3 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=117 time=16.2 ms
^C
--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 16.232/16.991/18.292/0.830 ms
james@mustang:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether f8:b1:56:e4:ca:fc brd ff:ff:ff:ff:ff:ff
    altname enp0s25
    inet 192.168.25.56/24 metric 100 brd 192.168.25.255 scope global dynamic eno1
       valid_lft 6916sec preferred_lft 6916sec
    inet6 fe80::fab1:56ff:fee4:cafc/64 scope link 
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:15:08:54:93 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
```

when i apply static

```
james@mustang:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether f8:b1:56:e4:ca:fc brd ff:ff:ff:ff:ff:ff
    altname enp0s25
    inet 192.168.25.3/24 brd 192.168.25.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet6 fe80::fab1:56ff:fee4:cafc/64 scope link 
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:15:08:54:93 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
james@mustang:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.


``` no internet I stopped ping on last one it just sat there blinking at me

---

### Post by TheFu on 2024-04-29
Use --debug on all netplan commands.
Remove the docket stuff.
Stick with networkd as the renderer.  Keep the netplan simple either using one that works on other systems or from a simple example from netplan.io/examples.
As long as you can use DHCP to get an IP to reload packages, this isn't a huge risk, purge nm-* and network-manager* from the system. No server needs those.  

Use **ip a** and **ip r** to see the setup and routing table for the system.  BTW, in the release notes for 24.04 there is something about the way docker containers won't work anymore due to some changes to cgroup defaults.

Instead of using en0, what happens if you use enp0s25?  That appears to be the correct device name.

BTW, I loaded Xubuntu 24.04 yesterday into a virtual machine. In about 10 minuter of using it, the screen went black twice and locked up the machine.  This was a 100% default install (next, next, next, next .... ) that took 10 minutes.  The first reboot created windows that couldn't be moved, then locked up.  I have both Server and Lubuntu to try today (probably when it gets hot outside, not this morning).  Let's just say, 24.04 isn't impressing me so far.

---

### Post by greg612 on 2024-04-29
Ok I reloaded this thing  its fresh as fresh can be......  this is what im starting with now I will purge all network manager crap and see how it goes  will post results

```
ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether f8:b1:56:e4:ca:fc brd ff:ff:ff:ff:ff:ff
    altname enp0s25
    inet 192.168.25.56/24 metric 100 brd 192.168.25.255 scope global dynamic eno1
       valid_lft 6405sec preferred_lft 6405sec
    inet6 fe80::fab1:56ff:fee4:cafc/64 scope link 
       valid_lft forever preferred_lft forever
```


```
# This file is generated from information provided by the datasource.  Changes
# to it will not persist across an instance reboot.  To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        eno1:
            dhcp4: true
    version: 2

```

---

### Post by greg612 on 2024-04-29
ok after purging network manager off no docker nothin  in it 

```
ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether f8:b1:56:e4:ca:fc brd ff:ff:ff:ff:ff:ff
    altname enp0s25
    inet 192.168.25.3/24 brd 192.168.25.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet6 fe80::fab1:56ff:fee4:cafc/64 scope link 
       valid_lft forever preferred_lft forever
```

```
network:
  version: 2
  renderer: networkd
  ethernets:
     eno1:
       addresses:
          - 192.168.25.3/24
       dhcp4: false
       dhcp6: false
       routes:
         - to: default
           via: 192.168.25.1
       optional: true
       nameservers:
         addresses: [ "9.9.9.9","149.112.112.112" ]
```

BOOM there goes the internet gone 

```
ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

```

starts ping then just sits there   Im lost   never seen anything like this   wow just wow

this is after sitting like 15 min 

```
ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
883 packets transmitted, 0 received, 100% packet loss, time 903146ms
```

---

### Post by greg612 on 2024-04-29
also tried this also 

```
james@mustang:~$ sudo apt-get purge network-manager
[sudo] password for james: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'network-manager' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dns-root-data dnsmasq-base libbluetooth3 libndp0 libnm0 libteamdctl0 ppp pptp-linux
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
james@mustang:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  dns-root-data dnsmasq-base libbluetooth3 libndp0 libnm0 libteamdctl0 ppp pptp-linux
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
After this operation, 3,981 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 84346 files and directories currently installed.)
Removing dns-root-data (2023112702~willsync1) ...
Removing dnsmasq-base (2.90-2build2) ...
Removing libbluetooth3:amd64 (5.72-0ubuntu5) ...
Removing libndp0:amd64 (1.8-1fakesync1build1) ...
Removing libnm0:amd64 (1.46.0-1ubuntu2) ...
Removing libteamdctl0:amd64 (1.31-1build3) ...
Removing pptp-linux (1.10.0-1build4) ...
Removing ppp (2.4.9-1+1.1ubuntu4) ...
Stopping all PPP connections...done.
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for dbus (1.14.10-4ubuntu4) ...
Processing triggers for libc-bin (2.39-0ubuntu8.1) ...
```

---

### Post by TheFu on 2024-04-29
- 192.168.25.3/24 to 192.168.25.1 using that subnet mask?

That doesn't seem right.
When you allow DHCP, what's the IP and gateway that works?
Doesn't the gateway need to be in the same subnet as the LAN?

---

### Post by MAFoElffen on 2024-04-29
Sorry. I had typo's in Post #32. Was in a hurry. Corrected now.

Please go back an redo from the 3rd command on...

---

### Post by TheFu on 2024-04-30
For networking to work correctly, 3 things are needed.
[LIST]
[*]IP address
[*]Subnet/Netmask
[*]Gateway IP
[/LIST]

Many posts ago, I asked to see two commands (ip a AND ip r) from a working config which would have shown these things. I asked to see it with DHCP and a working configuration. Then we could easily setup the correct values for a static IP from the working DHCP information.

This stuff isn't really that hard.

---

### Post by MAFoElffen on 2024-05-01
Look at the format of your nameservers address line...

Here is yours:
```

network:
  version: 2
  renderer: networkd
  ethernets:
     eno1:
       addresses:
          - 192.168.25.3/24
       dhcp4: false
       dhcp6: false
       routes:
         - to: default
           via: 192.168.25.1
       optional: true
       nameservers:
         addresses: [ "9.9.9.9","149.112.112.112" ]

```

Here is mine:
```

# Let networkd manage all devices on this system
network:
  version: 2
  renderer: networkd
  ethernets:
    enp12s0:
      addresses:
        - 10.0.0.3/8
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4, 1.1.1.1]
      routes:
        - to: default
          via: 10.0.0.1
          metric: 100
          on-link: true
      dhcp4: false
      dhcp6: false
      optional: yes

```

---

### Post by TheFu on 2024-05-01
Both types of nameserver lines work fine, IME.

---

### Post by greg612 on 2024-05-02
Thanks sorry been away for work I eill look into this in morning my bedtime

---

### Post by TheFu on 2024-05-03
Earlier this week, I installed Lubuntu 24.04 and setup a static IP using netplan.  It worked fine using the examples I posted. The only issue I had was self-inflicted because I forgot to change the ethernet device name in the netplan YAML.  The --debug option didn't show any error with that, which is disappointing.  That error showed up somewhere else. It wasn't in my face, but it only took a 1-2 minutes to figure out and correct.  Enabled systemd-networkd, then I purged nm-* and network-manager* from the system.  Just feels better without that junk in the way.

I also installed Xubuntu 24.04, but it was too unstable and locked up too many times, so I deleted that install.

I still need to install Ubuntu Server 24.04. Just haven't gotten around to it.  Appears that two of my issues with snap packages have better workarounds now. There's only 1 major issue remaining for me that is still a show-stopper.  Access to non-hard-coded storage locations on a program-by-program basis.   I did discover that my nextcloud snap install upgraded again without my approval after I've tried multiple times to hold it on a specific major release.  Sigh.

I'm happy to post the working 24.04 YAML, if you like.

---

### Post by greg612 on 2024-05-03
Let me give this one more shot first  I want to figure out what im doing wrong.  will let you know  thanks

upon further trying yes please post a working yaml  I want to test it on this

---

### Post by TheFu on 2024-05-03
```
$ lsb_release -d
No LSB modules are available.
Description:    Ubuntu 24.04 LTS

$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: [COLOR="#008000"]enp1s0[/COLOR]: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 52:54:00:aa:fd:df brd ff:ff:ff:ff:ff:ff
    inet [COLOR="#FF0000"]172.22.22.12[/COLOR]/24 brd 172.22.22.255 scope global enp1s0
       valid_lft forever preferred_lft forever
    inet6 fe80::5054:ff:feaa:fddf/64 scope link 
       valid_lft forever preferred_lft forever

sudo more /etc/netplan/01-network-manager-01.yaml network:
  version: 2
  renderer: networkd
  ethernets:
     [COLOR="#008000"]enp1s0[/COLOR]:
       addresses:
          - [COLOR="#FF0000"]172.22.22.12[/COLOR]/24
       dhcp4: false
       dhcp6: false
       routes:
         - to: default
           via: 172.22.22.1
       optional: true
       nameservers:
         addresses: [ "172.22.22.81","172.22.22.80" ]
         search: [example.foo,example.com]
```

This is a new install, so I still need to disable IPv6 and do a few more network things, but the static IP has been working since 5 minutes post-install.  However, I am having an issue getting ssh with keys working which has stumped me so far.  **ssh -vvvv** is providing lots of information and my key is seen, accepted, but not used. I have more research ... but I'm inclined to blame IPv6 right now.

---

### Post by Doug S on 2024-05-04
> **TheFu said:**
> For networking to work correctly, 3 things are needed.
[LIST]
[*]IP address
[*]Subnet/Netmask
[*]Gateway IP
[/LIST]

Many posts ago, I asked to see two commands (ip a AND ip r) from a working config which would have shown these things. I asked to see it with DHCP and a working configuration. Then we could easily setup the correct values for a static IP from the working DHCP information.

This stuff isn't really that hard.Agreed.

We still need to see the output for "ip r" from the working DHCP setup. From reviewing the 6 pages of this thread, nowhere has it been confirmed/proved that 192.168.25.1 is actually the gateway.

---

### Post by greg612 on 2024-05-04
```
james@mustang:~$ ip r
default via 192.168.25.1 dev eno1 proto static 
192.168.25.0/24 dev eno1 proto kernel scope link src 192.168.25.3 
```

---

### Post by TheFu on 2024-05-04
> **TheFu said:**
> - 192.168.25.3/24 to 192.168.25.1 using that subnet mask?

That doesn't seem right.
When you allow DHCP, what's the IP and gateway that works?
Doesn't the gateway need to be in the same subnet as the LAN?

I've been reading through the entire thread 1 more time.  I get confused because short answers that don't include the question being answered clearly are confusing. 

As I read my post above, I don't know what I was thinking.  192.168.25.3/24 via  192.168.25.1 (gw) DOES make perfect sense.


For some clarity, after any change is made to a netplan.yaml file, 2 commands are mandatory, 
```
sudo netplan generate --debug  # assuming this doesn't have any errors/warnings.
sudo netplan apply
```

I don't recognize the DNS servers being used.  I use 1.1.1.1 and 1.0.0.1 for public DNS.  When using IP addresses, DNS doesn't matter, so I've ignored it.
8.8.8.8 is google's (we want to watch you) DNS. Mostly it is just an easy, known, IP to ping.  That's the entire point.

So, after each change with generate/apply steps, run these commands to provide a clear answer:
```
ip a  # show the IP address on the system
ip r |column -t   # show the routing table
ping 192.268.25.1   # ping your LAN router (use the correct IP for it if this is wrong)
ping 8.8.8.8   # ping a well-known internet IP

```

If we are starting over 100%, showing the working DHCP version, then the desired static IP version would be helpful.
Clearly label each group of commands with the scenario.  Let's act like this is 100% new thread and step back.
You should also verify that the DHCP range configured inside your DHCP server has limits. It shouldn't be the entire /24 subnet.  When choosing the range for static IPs, always choose an IP outside the DHCP range and ensure it isn't already being used.

We all know these things, but for being very clear, thought I'd post them.

---

### Post by greg612 on 2024-05-04
```
 ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=58 time=18.0 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=58 time=16.5 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=58 time=15.9 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=58 time=16.8 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=58 time=16.3 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=58 time=17.0 ms
64 bytes from 8.8.8.8: icmp_seq=7 ttl=58 time=16.6 ms
64 bytes from 8.8.8.8: icmp_seq=8 ttl=58 time=16.1 ms
64 bytes from 8.8.8.8: icmp_seq=9 ttl=58 time=16.6 ms
64 bytes from 8.8.8.8: icmp_seq=10 ttl=58 time=17.3 ms
^C
--- 8.8.8.8 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 15.936/16.705/17.995/0.577 ms


james@mustang:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether f8:b1:56:e4:ca:fc brd ff:ff:ff:ff:ff:ff
    altname enp0s25
    inet 192.168.25.54/24 metric 100 brd 192.168.25.255 scope global dynamic eno1
       valid_lft 7011sec preferred_lft 7011sec
    inet6 fe80::fab1:56ff:fee4:cafc/64 scope link 
       valid_lft forever preferred_lft forever


james@mustang:~$ ip r
default via 192.168.25.1 dev eno1 proto dhcp src 192.168.25.54 metric 100 
192.168.25.0/24 dev eno1 proto kernel scope link src 192.168.25.54 metric 100 
192.168.25.1 dev eno1 proto dhcp scope link src 192.168.25.54 metric 100 
james@mustang:~$ 

```

Stock out of box working network.

---

### Post by greg612 on 2024-05-04
The dns I use is quad9

---

### Post by greg612 on 2024-05-04
```
 lsb_release -d
No LSB modules are available.
Description:    Ubuntu 24.04 LTS
james@mustang:~$ ip r
default via 192.168.25.1 dev eno1 proto static 
192.168.25.0/24 dev eno1 proto kernel scope link src 192.168.25.3 
james@mustang:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether f8:b1:56:e4:ca:fc brd ff:ff:ff:ff:ff:ff
    altname enp0s25
    inet 192.168.25.3/24 brd 192.168.25.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet6 fe80::fab1:56ff:fee4:cafc/64 scope link 
       valid_lft forever preferred_lft forever

```

---

### Post by greg612 on 2024-05-04
I got this straight from netplan for this 24.04 working yaml

```
network:
    version: 2
    renderer: networkd
    ethernets:
        eno1:
          addresses:
              - 192.168.25.3/24
          nameservers:
              addresses: [9.9.9.9, 149.112.112.112]
          routes:
              - to: default
                via: 192.168.25.1
```

```
 ping 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
^C
--- 1.1.1.1 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5151ms

james@mustang:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7156ms


```

nope

---

### Post by greg612 on 2024-05-04
```
ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether f8:b1:56:e4:ca:fc brd ff:ff:ff:ff:ff:ff
    altname enp0s25
    inet 192.168.25.3/24 brd 192.168.25.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet6 fe80::fab1:56ff:fee4:cafc/64 scope link 
       valid_lft forever preferred_lft forever
james@mustang:/etc/netplan$ ip r
default via 192.168.25.1 dev eno1 proto static 
192.168.25.0/24 dev eno1 proto kernel scope link src 192.168.25.3 

```

---

### Post by greg612 on 2024-05-04
All this was done right after i changed yaml to static see post #56 for out of box yaml

```
network: 
    version: 2
    renderer: networkd
    ethernets:
        eno1:
          addresses:
              - 192.168.25.3/24
          nameservers:
              addresses: [9.9.9.9, 149.112.112.112]
          routes:
              - to: default
                via: 192.168.25.1
```

Here is pinging all the way out the door I can ping everything everything can ping it
james@mustang:/$ sudo netplan generate --debug and 
sudo netplan apply

got no errors but it didnt show anything either  I believe that is good?

```
james@mustang:/$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether f8:b1:56:e4:ca:fc brd ff:ff:ff:ff:ff:ff
    altname enp0s25
    inet 192.168.25.3/24 brd 192.168.25.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet6 fe80::fab1:56ff:fee4:cafc/64 scope link 
       valid_lft forever preferred_lft forever

james@mustang:/$ ip r
default via 192.168.25.1 dev eno1 proto static 
192.168.25.0/24 dev eno1 proto kernel scope link src 192.168.25.3
 
james@mustang:/$ ping 192.168.25.1
PING 192.168.25.1 (192.168.25.1) 56(84) bytes of data.
64 bytes from 192.168.25.1: icmp_seq=1 ttl=64 time=0.830 ms
64 bytes from 192.168.25.1: icmp_seq=2 ttl=64 time=0.776 ms
64 bytes from 192.168.25.1: icmp_seq=3 ttl=64 time=0.810 ms
64 bytes from 192.168.25.1: icmp_seq=4 ttl=64 time=0.754 ms
64 bytes from 192.168.25.1: icmp_seq=5 ttl=64 time=0.795 ms
64 bytes from 192.168.25.1: icmp_seq=6 ttl=64 time=0.807 ms
^C
--- 192.168.25.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5138ms
rtt min/avg/max/mdev = 0.754/0.795/0.830/0.024 ms

james@mustang:/$ ping 192.168.145.1
PING 192.168.145.1 (192.168.145.1) 56(84) bytes of data.
64 bytes from 192.168.145.1: icmp_seq=1 ttl=64 time=0.928 ms
64 bytes from 192.168.145.1: icmp_seq=2 ttl=64 time=0.787 ms
64 bytes from 192.168.145.1: icmp_seq=3 ttl=64 time=0.677 ms
64 bytes from 192.168.145.1: icmp_seq=4 ttl=64 time=0.674 ms
64 bytes from 192.168.145.1: icmp_seq=5 ttl=64 time=0.734 ms
64 bytes from 192.168.145.1: icmp_seq=6 ttl=64 time=0.661 ms
^C
--- 192.168.145.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5134ms
rtt min/avg/max/mdev = 0.661/0.743/0.928/0.093 ms

james@mustang:/$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
14 packets transmitted, 0 received, 100% packet loss, time 13312ms

james@mustang:/$ ping google.com
```

---

### Post by TheFu on 2024-05-04
I must be stupid.  
Some posts aren't labeled.
I don't understand *which outputs* are for *which configurations*.  Please _**CLEARLY LABEL**_ which outputs go with which netplan config.  Don't be afraid to edit prior posts, so this thread doesn't get even longer. Usually if a thread isn't answered in the first 20 posts, it becomes a discussion or deadend because people get sidetracked.

[https://netplan.readthedocs.io/en/latest/using-static-ip-addresses/](https://netplan.readthedocs.io/en/latest/using-static-ip-addresses/) is the official documentation.  The example at the top of that page ... seems pretty clear. Maybe following it would be better?  

I do a number of things different on all my systems, so perhaps my working netplan files don't have the same complex interactions that Ubuntu forces?  IDK.

When I look again at the netplan.yaml in post #42, I don't see anything wrong.  In some of the others, I see missing dhcp4/6 lines or lines with "no", not "false".
I also don't see any **search:** lines.  I've never NOT had those, but I have multiple LAN and WAN domains, so it has always made sense to have them. IDK if it matters, just that #42 doesn't.

Think I need a few days off from this problem. Hopefully, someone else will have some fresh ideas.

---

### Post by greg612 on 2024-05-04
I've never had search on there ever  lol  always worked  thats what gets me out of all this.

I NEVER had a problem with setting a static ip  They have all worked just fine

Til the last upgrade to 22.04 then it all quit working and hasnt worked since.

well im giving up growing real tired of this, maybe debain or the free red hat   dont know   Thanks

---

### Post by MAFoElffen on 2024-05-05
@TheFu, @greg612 --
> **TheFu said:**
> 
[https://netplan.readthedocs.io/en/latest/using-static-ip-addresses/](https://netplan.readthedocs.io/en/latest/using-static-ip-addresses/) is the official documentation.  The example at the top of that page ... seems pretty clear. Maybe following it would be better?  

I do a number of things different on all my systems, so perhaps my working netplan files don't have the same complex interactions that Ubuntu forces?  IDK.

@TheFu -- You are going to hate this. But I have an alternate work-around at the end that goes along with what you do... I know this is a long-read (which isn't what you like), but it has details that will explain what changed, and what works now. I tried to summarize it without losing those details...

I brought this up in the Noble-DEV Cycle... That things were changing with Server 24.04 under-the-covers, that started back with 18.04...
RE: [https://ubuntuforums.org/showthread.php?t=2492108&highlight=netplan](https://ubuntuforums.org/showthread.php?t=2492108&highlight=netplan)
People blew me off, so I researched it, looked into it deeply, and made it work for me... I haven't shared (yet) what I really found under the covers there.

As TheFu knows that in 18.04, Ubuntu got deeper into using cloud-init... Which he hates. LOL. He has fought against it and used different ways to try to uninstall, disable and cripple it. Each release since then has deeper hooks using cloud-init. I keep that in the back of my mind, when things like this come up...

First thing is that, for security, they took away a bunch of the usual read permissions, and changed other permssion of system files like the netplan .yaml files, and the cloud-init .cfg files... So now to look at them with grep now, you have to use sudo.

This is how it is through 24.04 now...

 Look at this (new) header to the new /etc/netplan/50-cloud-init.yaml file that is generated by the newer installs:
```

mafoelffen@maf-server1-0:~$ sudo grep . /etc/netplan/50-cloud-init.yaml
[sudo] password for mafoelffen: 
[COLOR=#ff0000]# This file is generated from information provided by the datasource.  Changes
# to it will not persist across an instance reboot.[/COLOR]  [COLOR=#008000]To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}[/COLOR]
network:
    ethernets:
        enp1s0:
          dhcp4: true
          dhcp: true
    version: 2

```
The part in red, is how it is configured now, which will be explained in Option #1. The part of that in green will be explained in Option #2.

[SIZE=3]_**Option #1**_[/SIZE]
What that means, is that, like when the old /etc/resolv.conf file changed from being a static file, to a dynamic file that can be overwritten, now this file is the same, overriden and overwritten if cloud-init reapplies it's settings. If you don't want that to happen, and make that into a static file again, skip to Option #2...

To make this work, how it is currently configured now, you have to edit file /etc/cloud/cloud.cfg.d/90-installer-network.cfg
```

mafoelffen@maf-server1-0:~$ sudo grep . /etc/cloud/cloud.cfg.d/90-installer-network.cfg
# This is the network config written by 'subiquity'
network:
  version: 2
  ethernets:
    enp1s0:
      dhcp4: true
      dhcp6: true

```
Note, when you first go to edit this file, it will contain whatever was used as network settings in the installer when it was installed. It used this file on the first boot, and used cloud-init to apply them...

This is what I changed that file to:
```

mafoelffen@maf-server1-0:~$ sudo grep . /etc/cloud/cloud.cfg.d/90-installer-network.cfg
# This is the network config written by 'MAFoElffen'
network:
  version: 2
  ethernets:
    enp1s0:
      addresses:
      - 192.168.122.52/24
      nameservers:
        addresses:
        - 9.9.9.9
        - 149.112.112.112
        search: []
      routes:
      - to: default
        via: 192.168.122.1
      optional: yes

```
Notice I changed things there to mirror what this OP is trying to use, except the specific address, which my server KVM VM was on a different subnet...

To trick cloud-init into thinking it is the first reboot, and reapply the changed network config... without changing major things with it, do this:
```

sudo rm /var/lib/cloud/data/instance-id
sudo cloud-init init --local

```
That will generate the new/updated /etc/netplan/50-cloud-init.yaml file... But if you check your ip stats, or do cloud-init... It is not applied yet... but check the .yaml file to make sure it was updated by cloud-init, before applying it...
```

mafoelffen@maf-server1-0:~$ sudo grep . /etc/netplan/50-cloud-init.yaml
# This file is generated from information provided by the datasource.  Changes
# to it will not persist across an instance reboot.  To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        enp1s0:
            addresses:
            - 192.168.122.52/24
            nameservers:
                addresses:
                - 9.9.9.9
                - 149.112.112.112
                search: []
            optional: true
            routes:
            -   to: default
                via: 192.168.122.1
    version: 2

```
If updated, then apply it.
```

sudo netplan generate
sudo netplan apply

```
Check it:
```

mafoelffen@maf-server1-0:~$ sudo cloud-init init
Cloud-init v. 24.1.3-0ubuntu3 running 'init' at Sun, 05 May 2024 17:09:38 +0000. Up 4890.62 seconds.
ci-info: ++++++++++++++++++++++++++++++++++++++Net device info++++++++++++++++++++++++++++++++++++++
ci-info: +--------+------+----------------------------+---------------+--------+-------------------+
ci-info: | Device |  Up  |          Address           |      Mask     | Scope  |     Hw-Address    |
ci-info: +--------+------+----------------------------+---------------+--------+-------------------+
ci-info: | enp1s0 | True |       192.168.122.52       | 255.255.255.0 | global | 52:54:00:3e:5f:43 |
ci-info: | enp1s0 | True | fe80::5054:ff:fe3e:5f43/64 |       .       |  link  | 52:54:00:3e:5f:43 |
ci-info: |   lo   | True |         127.0.0.1          |   255.0.0.0   |  host  |         .         |
ci-info: |   lo   | True |          ::1/128           |       .       |  host  |         .         |
ci-info: +--------+------+----------------------------+---------------+--------+-------------------+
ci-info: +++++++++++++++++++++++++++++++Route IPv4 info+++++++++++++++++++++++++++++++
ci-info: +-------+---------------+---------------+---------------+-----------+-------+
ci-info: | Route |  Destination  |    Gateway    |    Genmask    | Interface | Flags |
ci-info: +-------+---------------+---------------+---------------+-----------+-------+
ci-info: |   0   |    0.0.0.0    | 192.168.122.1 |    0.0.0.0    |   enp1s0  |   UG  |
ci-info: |   1   | 192.168.122.0 |    0.0.0.0    | 255.255.255.0 |   enp1s0  |   U   |
ci-info: +-------+---------------+---------------+---------------+-----------+-------+
ci-info: +++++++++++++++++++Route IPv6 info+++++++++++++++++++
ci-info: +-------+-------------+---------+-----------+-------+
ci-info: | Route | Destination | Gateway | Interface | Flags |
ci-info: +-------+-------------+---------+-----------+-------+
ci-info: |   0   |  fe80::/64  |    ::   |   enp1s0  |   U   |
ci-info: |   2   |    local    |    ::   |   enp1s0  |   U   |
ci-info: |   3   |  multicast  |    ::   |   enp1s0  |   U   |
ci-info: +-------+-------------+---------+-----------+-------+
mafoelffen@maf-server1-0:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 52:54:00:3e:5f:43 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.52/24 brd 192.168.122.255 scope global enp1s0
       valid_lft forever preferred_lft forever
    inet6 fe80::5054:ff:fe3e:5f43/64 scope link 
       valid_lft forever preferred_lft forever

```

[SIZE=3]_** Option #2**_[/SIZE]
To stomp on that, and make your .yaml file(s) from getting overwritten... Create the file /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following contents:
```

network: {config: disabled}

```
You can then either delete file /etc/cloud/cloud.cfg.d/90-installer-network.cfg or not. Since the newer file is numbered starting with "99-*" the order of precedence is canonical, so it will apply what is later.

You can also either edit the /etc/netplan/50-cloud-init.yaml file with your changes, or delete it and create your own netplan .yaml file (or just rename it) that is more descriptive, implying it is no loner using cloud-init, such as /etc/netplan/01-network-config.yaml

Option #2 is the simpler way, which I think most people might follow... Because it follows what has been working recently, and is know, with less steps to make changes. Just be aware that with every release, it digs deeper into this newer strategy in Option #1.

---

### Post by Doug S on 2024-05-05
I agree this thread has been hard to follow.

> **greg612 said:**
> 

```

james@mustang:/$ ping 192.168.145.1
PING 192.168.145.1 (192.168.145.1) 56(84) bytes of data.
64 bytes from 192.168.145.1: icmp_seq=1 ttl=64 time=0.928 ms
...

``` Okay, well, that is address is new. It might be an idea to know more about your LAN and if packet monitoring is possible on 192.168.25.1 and/or 192.168.145.1?

If you are willing, I'd like to try something different. It might be waste of time. The question I am wanting to answer is: Is it the send or return path that is the problem? I would PM you my external static IP address and set tcpdump on that externally facing server to monitor ICMP traffic to observe if your ping packets are actually being sent out to internet.

EDIT: If you have some packet monitoring ability on your routers, you should be able to check the send and return paths yourself. Example from mine:

1: External IF:
```

doug@s15:~$ sudo tcpdump -tttt -n -i enp1s0 icmp
[sudo] password for doug:
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on enp1s0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
2024-05-05 14:18:40.656692 IP WW.XXX.YYY.ZZZ > 8.8.8.8: ICMP echo request, id 4030, seq 1, length 64
2024-05-05 14:18:40.661764 IP 8.8.8.8 > WW.XXX.YYY.ZZZ: ICMP echo reply, id 4030, seq 1, length 64
2024-05-05 14:18:41.658189 IP WW.XXX.YYY.ZZZ > 8.8.8.8: ICMP echo request, id 4030, seq 2, length 64
2024-05-05 14:18:41.662782 IP 8.8.8.8 > WW.XXX.YYY.ZZZ: ICMP echo reply, id 4030, seq 2, length 64
2024-05-05 14:18:42.660189 IP WW.XXX.YYY.ZZZ > 8.8.8.8: ICMP echo request, id 4030, seq 3, length 64
2024-05-05 14:18:42.664789 IP 8.8.8.8 > WW.XXX.YYY.ZZZ: ICMP echo reply, id 4030, seq 3, length 64
2024-05-05 14:18:43.662198 IP WW.XXX.YYY.ZZZ > 8.8.8.8: ICMP echo request, id 4030, seq 4, length 64
2024-05-05 14:18:43.666787 IP 8.8.8.8 > WW.XXX.YYY.ZZZ: ICMP echo reply, id 4030, seq 4, length 64
^C
8 packets captured
8 packets received by filter
0 packets dropped by kernel

```
2: Internal IF:
```

doug@s15:~$ sudo tcpdump -tttt -n -i br0 icmp
[sudo] password for doug:
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on br0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
... delete some unrelated ICMP  "tcp port 443 unreachable" packets ...
2024-05-05 14:18:40.656639 IP 192.168.111.136 > 8.8.8.8: ICMP echo request, id 4030, seq 1, length 64
2024-05-05 14:18:40.661788 IP 8.8.8.8 > 192.168.111.136: ICMP echo reply, id 4030, seq 1, length 64
2024-05-05 14:18:41.658163 IP 192.168.111.136 > 8.8.8.8: ICMP echo request, id 4030, seq 2, length 64
2024-05-05 14:18:41.662804 IP 8.8.8.8 > 192.168.111.136: ICMP echo reply, id 4030, seq 2, length 64
2024-05-05 14:18:42.660163 IP 192.168.111.136 > 8.8.8.8: ICMP echo request, id 4030, seq 3, length 64
2024-05-05 14:18:42.664811 IP 8.8.8.8 > 192.168.111.136: ICMP echo reply, id 4030, seq 3, length 64
2024-05-05 14:18:43.662172 IP 192.168.111.136 > 8.8.8.8: ICMP echo request, id 4030, seq 4, length 64
2024-05-05 14:18:43.666809 IP 8.8.8.8 > 192.168.111.136: ICMP echo reply, id 4030, seq 4, length 64
^C

```
3: The internal client computer (192.168.111.136):
```

doug@s19:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=60 time=5.34 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=60 time=4.84 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=60 time=4.84 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=60 time=4.83 ms
^C
--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3006ms
rtt min/avg/max/mdev = 4.832/4.962/5.341/0.218 ms
doug@s19:~$

```

---

### Post by greg612 on 2024-05-05
I will report back packing to leave for work at moment . If i cannot get to it tonight it will be thursday....... I wont leave u hanging we all have to much invested in it now....   Besides I really want to know wtf   ya know

---

### Post by MAFoElffen on 2024-05-05
+1 -- Also traceroute, tracepath, mtr & netstat...

Since I did this for a while, having 'many' hats and being exposed to a whole lot of things (CISCO Academy being part of that), people these days do not seem to bring up the older tools that have been around for ages. WireShark is very powerful and a great tool for seeing exactly what is going on. I used that a lot for network diagnostics.

Seeing things as they happen, you can try to understand what is not working right. Lack of information, is like... Then you have to rule out all the myriad of possibilities. Better to check things off, of what isn't the problem to narrow the search to what something 'could be'.

One of my niche's is "diagnostics"... Logically breaking things down to how they should work, and what happens if that step doesn't, into a flow chart kind of affair, to figure out what may be the problem,

---

### Post by TheFu on 2024-05-06
Don't forget **chattr**, for when files are being changed and you don't want that. For a few years right after resolvconf was introduced, I'd delete the symlink for /etc/resolv.conf, create a new file with my DNS settings, then make it immutable.  Worked great, until I forgot the flag was set and couldn't update it.  Same with setfacl.  When normal permissions aren't working as expected, it can drive me crazy. Now I know to check both ACLs and attribs, but 25 yrs ago, those were new enough to me that I didn't think of them as likely.

In capture the flag competitions, I like to screw with other teams using chattr. Nobody thinks of it. They just don't.

---

### Post by greg612 on 2024-08-16
Hello  Sorry its been awhile work family comes before any of this...  but anyway   Its fixed.... The ONLY way I could do it was at install  yep had to redo the whole thing.... Luckily it was fresh anyway   but for some reason would not do it any other way.

---

