---
title: "ubuntu 10.10 server can't sudo apt-get update"
date: 2011-03-16
forum: Server Platforms
---

### Post by adduds on 2011-03-16
ok I wanted to installed transmission on my buntu server box 10.10 tonite so from my laptop top i ssh'd into it...which took an unordinary amount of time.. went to type in sudo apt-get install transmission

half way through each word at the terminal prompt it would just hang...had to wait then it would recognize my typing and i could continue....pressed enter waited a long time; then noticed i coulnd't connect to the repos? 

so i manually (as in sitting at the box not over ssh) tried to ping google nothing....sudo apt-get update....nothing....

- i restarted the machine twice 
-sudo ifdown eth0 /sudo ifup eth0 

sudo nano /etc/networking/interfaces made sure it said

> auto eth0
iface eth0 inet dhcp


i have my router saved to assign 192.168.0.100 to the machines eth0 MAC of 00:14:2a:e9:15:0b so i can always use my webUI w/o having to guess my ip

ifconfig shows my broadcast running i dunno i'm sooo confused and lost :( scared...a lil' cold....kinda hungry..pretty tired....lol!

but seriously i don't know wtf to do now! i'm on cli no gui anyone ever have this?

> 
ad@desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:2a:e9:15:0b  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:fee9:150b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:275270 (275.2 KB)  TX bytes:1389111 (1.3 MB)
          Interrupt:23 Base address:0x6000 

---

### Post by volkswagner on 2011-03-16
Have you tried to restart your router?

Run top in a terminal to see if any process is running wild.

```
top
```

To exit top
```
q
```

Other things to run

```
route
```

```
cat /etc/resolv.conf
```

```
host google.com
```

Is your disk filling up?
[code[df[/code]

You can also try changing the ip address in your router, or stop the mac association and see if the server picks up a unique address.

Check logs for any info, and see if the card actually gets activity (blinking lights).... possibly reseat the card if it is addon.  Don't rule out possible hardware failure.  An easy test to see if the port works and can get DHCP, try a live CD and check for internet/network connection.  I think checking with live CD should go to the top of the list....

Good luck!

---

### Post by Bucky Ball on 2011-03-16
Just a point but LTS releases always advisable for servers. More stable and five year support. ;)

---

### Post by adduds on 2011-03-16
i did restart my router that's when the problem occured

when i run route i get

Destination   Gateway     Genmask     Flags Metric Ref  Use  Iface
192.168.0.0     *      255.255.255.0    U     0     0     0    eth0
default       192.168.0.1  0.0.0.0      UG   100    0     0    eth0

but when i ifconfig it still says the ip is 192.168.0.100

cat /etc/resolv.conf
nameserver 192.168.0.1
domain domain_not_set.invalid
search domain_not_set.invalid

host google.com
;; connectoin timed out; no servers could be reached 

when i ran route from live usb (which did work right away)

Route = 

Destination   Gateway     Genmask     Flags Metric Ref  Use  Iface
192.168.0.0     *      255.255.255.0    U     1     0     0    eth0
link-local      *      255.255.0.0      U    1000   0     0
default       192.168.0.1  0.0.0.0      UG     0    0     0    eth0

host google.com = 
google.com has address 74.125.226.84
google.com has address 74.125.226.83
google.com has address 74.125.226.82
google.com has address 74.125.226.81
google.com has address 74.125.226.80


i hope this info provides enough information to possibly resolve a solution

it looks from a lamen the my route is all screwed up? and even when i remove mac ip addessing my server still has ip 192.168.0.100?

---

### Post by TechSupportx86 on 2011-03-16
i would change it from the router assigning the IP to /network/interfaces tell the router it's IP (if that makes sense). 

open your /etc/networking/interfaces and change it look like:

```

auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway [COLOR=Red]your gateway IP[/COLOR]

```save it and restart the server. while that's restarting disable the IP assignment from the router, then restart the router. This will make it so the server will tell the router it's IP address, rather than the router having to figure it out it based on the MAC address. 

If it doesn't work change it back and try something else, worth a shot and is easy to undo :D

---

### Post by adduds on 2011-03-16
well i have done that it didn't work :(

i shouldn't have to re-install the os for this should i? :(

---

### Post by TechSupportx86 on 2011-03-16
After reading your post again i realized i had a very similar problem not long ago. here is a link to the thread:

[COLOR=Red][http://ubuntuforums.org/showthread.php?t=1691491&highlight=techsupportx86](http://ubuntuforums.org/showthread.php?t=1691491&highlight=techsupportx86)
[/COLOR] 
my server basically couldn't find the gateway, ssh worked, but couldn't connect to any external servers. all i had to do was add the gateway to my interfaces file and that fixed it, but since you tried that there must be *Another* file somewhere overiding that one? Since you disabled the assigned IP and it still shows up under ifconfig that's most likely your problem.

Also go back into /etc/networking/interfaces and **MAKE SURE** the comment lines start with a # , that happened to me once and i never found out the cause.

---

### Post by volkswagner on 2011-03-16
> **adduds said:**
> well i have done that it didn't work :(

i shouldn't have to re-install the os for this should i? :(

I wouldn't run out and reinstall just yet.

What does your interface file look like now?

```
cat /etc/network/interfaces
```

What happens when you run dhclient manually?

```
sudo dhclient eth0
```

Any errors?

Anything odd in /var/lib/dhcp3/dhclient.leases

Perhaps you can clear it and try again.

```
sudo cp /dev/null /var/lib/dhcp3/dhclient.leases
```

Then run dhclient again.
```
sudo dhclient eth0
```

All the above should be done with no special reference in your router ie: no mac address association or static assignments, plus a router restart.

---

### Post by adduds on 2011-03-16
so it came to me backing up my router config and resetting it to factory defaults....after the clean reset.....it worked. np    :confused:

i've done this before once only after i restart my router it does this but thanks very much for all the help and have gotten it working and i learned some awsome ways to set static ip that i wasn't aware of! thanks again!

ad.

hopefully i can return the favor someday :popcorn:

---

