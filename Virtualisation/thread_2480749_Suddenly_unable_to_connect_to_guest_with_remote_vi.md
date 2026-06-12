---
title: "Suddenly unable to connect to guest with remote_viewer"
date: 2022-11-08
forum: Virtualisation
---

### Post by stony777 on 2022-11-08
I was able to install virtual machines on my HP Server and am able to start and connect via QEMU/KVM. 

I want to connect to the spice session via [FONT=monospace][COLOR=#000000]```
remote-viewer 192.168.178.62:5900 
``` because then I am able to use multiple monitors which i need for home-office work.

The port on the server seems to be open 
[/COLOR]
[/FONT]```
[FONT=monospace][COLOR=#54ff54]**server@ProLiant-ML350-Gen9**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/**[/COLOR][COLOR=#000000]$ sudo netstat -tap | grep 5900 [/COLOR]
tcp        0      0 0.0.0.0:[COLOR=#ff5454]**5900**[/COLOR][COLOR=#000000]            0.0.0.0:*               LISTEN      53376/qemu-system-x[/COLOR]
[/FONT]
```[FONT=monospace]

But when i scan the virtual machine via nmap the port doesn't show as open: 

[/FONT]```
[FONT=monospace][COLOR=#54ff54]**stony@Aperture-Science**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo nmap 192.168.178.62     [/COLOR]
Starting Nmap 7.80 ( https://nmap.org ) at 2022-11-08 21:58 CET 
Nmap scan report for DESKTOP-2BBTU3D.fritz.box (192.168.178.62) 
Host is up (0.00091s latency). 
Not shown: 997 filtered ports 
PORT    STATE SERVICE 
135/tcp open  msrpc 
139/tcp open  netbios-ssn 
445/tcp open  microsoft-ds 
MAC Address: 52:54:00:51:81:33 (QEMU virtual NIC) 
Nmap done: 1 IP address (1 host up) scanned in 5.13 seconds
[/FONT]
```[FONT=monospace]
So when I try to connect to the Virtual Machine with remote_viewer I get "Connectiontype could not be determined by URI" (Verbindungstyp konnte nich von URI ermittelt werden)

and on the console 
```
[FONT=monospace][COLOR=#54ff54]**stony@Aperture-Science**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ remote-viewer spice:&#8260;&#8260;192.168.178.62:5900 [/COLOR]

** (remote-viewer:15934): [COLOR=#ff54ff]**CRITICAL**[/COLOR][COLOR=#000000] **: [/COLOR][COLOR=#1818b2]22:00:09.619[/COLOR][COLOR=#000000]: virt_viewer_util_extract_host: assertion 'uri != NULL' failed[/COLOR]

[/FONT]
```[FONT=monospace].


Sorry - but I am currently lost - does anybody have a hint for me how to solve or where to look?

Think is - it used to work like charm - i didn't change a thing.

Cheers and Thanks in advance 

Stony[/FONT]

[/FONT]

---

### Post by MAFoElffen on 2022-11-08
More info needed.

KVM default vSwitch is on network id 192.168.122.0/24... You are trying to connect a guest on network id 192.168.178.0/24 through what type of vSwitch or Bridge to what host network? Can you ping to each, each way?

---

### Post by stony777 on 2022-11-08
Sorry about the lack of information

My network is 192.168.178.x. 

The NIC on the server is bridged to br0 so the guest system is using that and gets the IP 192.168.178.62. 
I just read that the remote-viewer connection is done to the server it self which has the IP 192.168.178.51. The result is the same - same error - no connection. (i remembered that I did that connection that way as well - don't know how i got confused and tried to connect to the Guest-IP on Port 5900.

I can ping back and forth:

```
[FONT=monospace][COLOR=#54ff54]**stony@Aperture-Science**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ping 192.168.178.51 [/COLOR]
PING 192.168.178.51 (192.168.178.51) 56(84) bytes of data. 
64 bytes from 192.168.178.51: icmp_seq=1 ttl=64 time=0.211 ms 
64 bytes from 192.168.178.51: icmp_seq=2 ttl=64 time=0.193 ms 
^C 
--- 192.168.178.51 ping statistics --- 
2 packets transmitted, 2 received, 0% packet loss, time 1005ms 
rtt min/avg/max/mdev = 0.193/0.202/0.211/0.009 ms 
[COLOR=#54ff54]**stony@Aperture-Science**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ping 192.168.178.62 [/COLOR]
PING 192.168.178.62 (192.168.178.62) 56(84) bytes of data. 
64 bytes from 192.168.178.62: icmp_seq=1 ttl=128 time=1.90 ms 
64 bytes from 192.168.178.62: icmp_seq=2 ttl=128 time=0.520 ms 
^C 
--- 192.168.178.62 ping statistics --- 
2 packets transmitted, 2 received, 0% packet loss, time 1002ms 
rtt min/avg/max/mdev = 0.520/1.211/1.903/0.691 ms 
[COLOR=#54ff54]**stony@Aperture-Science**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]
```

and from the server to my desktop:
```
[FONT=monospace][COLOR=#54ff54]**server@ProLiant-ML350-Gen9**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/**[/COLOR][COLOR=#000000]$ ping 192.168.178.56 [/COLOR]
PING 192.168.178.56 (192.168.178.56) 56(84) bytes of data. 
64 bytes from 192.168.178.56: icmp_seq=1 ttl=64 time=0.162 ms 
64 bytes from 192.168.178.56: icmp_seq=2 ttl=64 time=0.153 ms 
^C 
--- 192.168.178.56 ping statistics --- 
2 packets transmitted, 2 received, 0% packet loss, time 1020ms 
rtt min/avg/max/mdev = 0.153/0.157/0.162/0.004 ms 
[COLOR=#54ff54]**server@ProLiant-ML350-Gen9**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]
```[FONT=monospace]
[/FONT]
The windows guest can also ping every machine.

---

### Post by MAFoElffen on 2022-11-08
I see a Microsoft port open, but not open for VNC port 5900...

Windows Guest? Try turning off your firewall. If it comes up, then add a firewall rule to open up port 5900.

---

### Post by stony777 on 2022-11-09
Hi,

I turned off the Firewall on the guest Windows10. And turned of the firewall on the server itself (sudo  ufw disable) Then I checked if the spice server listens to all devices - it does.
```
[FONT=monospace][COLOR=#54ff54]**stony@Aperture-Science**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ nmap -p5900 192.168.178.51 [/COLOR]
Starting Nmap 7.80 ( https://nmap.org ) at 2022-11-09 06:59 CET 
Nmap scan report for ProLiant-ML350-Gen9.fritz.box (192.168.178.51) 
Host is up (0.00021s latency). 

PORT     STATE SERVICE 
5900/tcp open  vnc

[/FONT]
```
Port 5900 on the server is open. When i changed it to localhost only - it showed up as closed. So that should be alright.

As far as I understand is the spice-server a layer on top of the quest-os so that it has no choice than to show the remote session?

On the server though the port is shown as before: 
```
[FONT=monospace][COLOR=#54ff54]**server@ProLiant-ML350-Gen9**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo netstat -tap | grep 5900 [/COLOR]
tcp        0      0 0.0.0.0:[COLOR=#ff5454]**5900**[/COLOR][COLOR=#000000]            0.0.0.0:*               LISTEN      67801/qemu-system-x [/COLOR]
[/FONT]
```

Trying to establish the remote-viewer connection (like i did last week as it was working) still results in an error that the connectiontype could not be determined.

---

### Post by stony777 on 2022-11-09
Okay - somehow solved: I was able to connect to the spice session with  running it with sudo and specifying the user on the server

```
[FONT=monospace][COLOR=#000000]sudo remote-viewer spice://server@192.168.178.51:5900 [/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]

Maybe this helps someone in the future.

For the background why I am doing all this for a private server:

I  got this HP Proliant G350 9gen for free and I figured to go all in and  use all the capabilities it brings - including virtualization. I know  that this is an advanced topic but I wanted to try nevertheless - just  because I am curious.
I know that this could be kind of annoying when  "users" try to play in the pro league - so I appreciate everyone who  thought about my problem and I wanna thank [/COLOR][/FONT][**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547") for trying to help and answering.
So  basically this topic is SOLVED  - even though i yet dont know why it  used to work last week without sudo and specifying and what broke it in the meantime - or if I just  miss the obvious  (which can be as well)

Thanks again!

Stony

---

### Post by MAFoElffen on 2022-11-09
You are welcome. I am happy you found a solution.

If you go to the "Thread Tools" link in the upper right of this thread page, please mark the thread as "Solved" so that others may find your solution to solve their similar issues.

---

### Post by TheFu on 2022-11-10
I use remote viewer to connect to SPICE VMs with this:
```
/usr/bin/virt-viewer --connect qemu+ssh://hadar/system regulus &
```

hadar is the VM-host.
regulus is the VM-guest.
No need for sudo. Actually, I don't use root to manage any KVM-based VMs at all. Just my normal account which is a member of libvirt and kvm unix groups on the VM-host and my local workstation.

---

