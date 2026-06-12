---
title: "VirtualBox wireless bridging"
date: 2008-03-15
forum: Virtualisation
---

### Post by Silvr2008 on 2008-03-15
I am trying to set up a VB WinXP guest. I am trying to bridge my wireless connection with a vbox interface to get online with the guest. My network card is an Intel 2200bg. I added the following lines to /etc/network/interfaces:

auto br0
iface br0 inet static
    address 192.168.1.150
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
    bridge_ports all

When I reboot, the network manager pops up repeatedly for my WPA key. I am sure I am typing it correctly. In the VB manual it says that it is not possible to bridge a wireless connection, but I have read posts from other people saying that they have done it. Could someone please help me with this?

---

### Post by Hero of Time on 2008-03-15
Check [http://ubuntuforums.org/showpost.php?p=4507341&postcount=14](http://ubuntuforums.org/showpost.php?p=4507341&postcount=14) for the 'howto'. It should work.

---

### Post by scottro on 2008-03-15
Naw, that was written by a jerk.  Just ask my wife.  :)

Please post if anything in it isn't clear.  I did my best to make it newcomer friendly.  

Re the iptables part--that's been  updated but only solved (for me) with Fedora.  Actually,  I don't think that I tested iptables with Ubuntu.

---

### Post by Silvr2008 on 2008-03-17
Thanks for your replys. I followed the howto and it did not work for me. Although when I *sysctl net.ipv4.ip_forward=1* along with the instructions in the vbox manual, it did get it working with the NAT configuration. I wonder why it didnt mention that in the part specific to Ubuntu. Still no connection when I am trying with it attached to a host interface.

---

### Post by scottro on 2008-03-17
Ok, let's try to keep it on one thread (I see there's another where both you and I had replied.)

I'll be busy till this evening, (EDT) but let's try to clarify.

We are only worried about wireless bridging at this point, correct?  (The other thread mentions a bridge, which my howto doesn't use for wireless.)

When you say part specific to Ubuntu, did you mean my howto or the VBox docs.  I found their distro specific docs to have problems, at least in Fedora, it might be that it's all being written by someone who uses something else.  :)
Anyway, I'll post more on this in the evening, but I'd just like to clarify is one thread for wired and the other for wireless?

---

### Post by scottro on 2008-03-18
I did a fresh install on Hardy today to see if there's anything I missed.  The only thing I can think of is that this time (installing via apt-get from the repos) is that I did, this time (but not in the past) have to change the default emulated network card . The default is PCNet-PCII.  I had to change that to PCNet-FASTIII.  

Also, I found it necessary to give both tap0 and the guest O/S static IP addresses.  (Different addresses--I believe that's made clear on my page.)

At any rate, it definitely worked.

---

### Post by alkadia on 2008-03-18
I'have similar issue. 
My PC I have eth0 (wireless) and eth1 (wired).
Ubuntu 7.10 is the OS-Host and Windows is OS-guest, I run this script before launch VM on VBox :

tunnel.sh
----
sudo tunctl -t tap0 -u $2
sudo chmod 666 /dev/net/tun
sudo ifconfig $1 0.0.0.0 promisc
sudo ifconfig tap0 0.0.0.0 promisc
sudo brctl addbr br0
sudo brctl addif br0 $1
sudo brctl addif br0 tap0
sudo dhclient br0
----

where $1 is the phisical interface and $2 is the user who launch VM.

So if I need tunnel in wired LAN I run :
# sh tunnell.sh eth1 my_user

and if I need tunnel in wireless LAN I run :
# sh tunnell.sh eth0 my_user.

In wired LAN this script work fine, in wireless LAN it doesn't work.
Someone can help me ?
thanks

---

### Post by scottro on 2008-03-18
Yes, the first post in this thread links to my page on it.  I made.
[http://home.nyc.rr.com/computertaijutsu/vboxbridge.html](http://home.nyc.rr.com/computertaijutsu/vboxbridge.html)

It usually works.  After reading Silvr2008's post, I checked my instructions last night, and it worked with Hardy without too much trouble.   I found I had to make a couple of minor changes from my original instructions, which have now been added to the page.)

---

### Post by Silvr2008 on 2008-03-21
I reinstalled VirtualBox, this time via apt-get and followed your instructions and still no dice. One thing I thought was interesting was that I could not ping the IP of tap0 on the host machine, but if I changed the IP on the guest to the same IP as tap0, it would give me an error saying there is an IP conflict. 

Also, I no longer have the option to change the virtual interface to the type III card. Is it possible we are getting a different version or something? In the VB about it says I am on version 1.50_OSE which is the same as what I thought I had before though.

I am a total newb to linux, but could it be that parprouted is simply not compatible with my Intel 2200bg NIC? I have had lots of problems running things with it.

---

### Post by scottro on 2008-03-21
It shouldn't be incompatible with the card.  I was using a later version of VBox though, I think.  

Let's go through the steps.  You have a firewall or is it off?  (For testing, we might want to temporarily turn it off, though Hardy's default firewall, at least, wasn't a problem.)

We enable ip forwarding with sysctl as described.  We create tap0 and you have rights to it (I think Ubuntu does that by default.  

ls -l /dev/net/tun 
and make sure that vboxusers have some rights. 

We create tap0 with you as the user.  We set its address on the same subnet as the regular wireless NIC with the ip command as stated. 
We do parprouted eth1 tap0

(You might, at least once, do parprouted -d eth1 tap0)   Replace eth1 with whatever your system calls your wireless card.  That -d is for debug and will cause parprouted to output to the terminal, so you might see something obvious.  (You might not, too, at one point when it wasn't working for me, it was just giving its usual got ARP blah blah.)

In VirtualBox, we chose Attached to Host Interface and gave it the name tap0.   As I say in my howto, I changed the default card.  However, when I was running a machine with the 2100, a close relative of yours, I didn't have to change it.  I would try it with all choices available--I think there's those two and one more. 

We then gave the guest OS an address on the same subnet.  (If any of this isn't clear, as you say you're a newcomer, don't be embarrassed to ask.  I'm assuming you know what I mean by a subnet, that eth1, tap0 and the guest O/S will have address like 192.168.1 20, 192.168.1.21 and 192.168.1.22 all with a netmask of 255.255.255.0.)

Did you use the OSE version (which is, I think, the one from apt.  I'm using Hardy though, so it might be different.)

---

### Post by Silvr2008 on 2008-03-21
I did it over again just to make sure, the only thing I do different is use tunctl rather than VBoxtunctl. For whatever reason I dont have VBoxtunctl. Could this be the problem? Sorry I didn't think about it before. I think I have done parprouted too many times, or something, too since there is a weird line in the output. Am I supposed to clear it?

 
zac@Ub:~$ sudo sysctl net.ipv4.ip_forward=1
net.ipv4.ip_forward = 1
zac@Ub:~$ sudo tunctl -b -u zac
tap0
zac@Ub:~$ sudo ip link set tap0 up
zac@Ub:~$ ip addr add 192.168.1.150 dev tap0
RTNETLINK answers: Operation not permitted
zac@Ub:~$ sudo ip addr add 192.168.1.150 dev tap0
zac@Ub:~$ sudo parprouted -d eth1 tap0
parprouted[9835]: Starting.
add entry: IPAddr: '192.168.1.1' HWAddr: '00:18:01:64:E6:47' Dev: 'eth1'
Created ARP thread for eth1.
Created ARP thread for tap0.
RTNETLINK answers: File exists
parprouted[9835]: '/sbin/ip route add 192.168.1.1/32 metric 50 dev eth1 scope link' unsuccessful!
Refreshing ARP entries.
Sending ARP request for 192.168.1.1 to eth1
Received reply: updating kernel ARP table for 192.168.1.1(eth1).
Received ARP request for 192.168.1.2 on iface eth1
Did not find match for 192.168.1.2(eth1)
Sending ARP request for 192.168.1.2 to tap0
Adding 192.168.1.1 to request queue
Refreshing ARP entries.
Sending ARP request for 192.168.1.1 to eth1
Received reply: updating kernel ARP table for 192.168.1.1(eth1).

---

### Post by scottro on 2008-03-21
Yeah, maybe we better start over again. 
Close VirtualBox.  (I'm just going to use vbox from now on, easier to type.) 

Then, 
sudo ifconfig tap0 down
tunctl -d tap0
(you should get a message here that it's inactive or something similar.
sudo pkill parprouted

(To answer your other question, I don't think using tunctl instead of the VirtualBox one will make a difference, unless, for some reason /dev/net/tun doesn't have the permissions you want. 

Now make sure there isn't a tap0 running

ifconfig
(make sure there isn't a tap0).
If there is then repeat that procedure of bringing it down and tunctl -d again. 
(I'm assuming the tunctl command is -d, just as it is with the vbox one.)

So, now we should have a clean slate, where ifconfig is just showing the loopback and eth1, or whatever your wireless is called--I'm just guessing eth1 because that's what it called my 2100. 

Then let's try again.  In VirtualBox, make sure you have it set to attached to host and set at tap0 for the interface name.  You might even regenerate the Mac address, by clicking that button. 

Then, let's try again.  At this point, with tap0 down, there probably isn't a /dev/net/tun.  Check though
ls /dev/net

If it's there, check the permissions on it
ls -l /dev/net/tun
Make sure that vboxusers have rights to it.  
However, for the moment, let's assume it isn't there.  So once again
sudo tunctl -b -u Silvr (or whatever your user name is).

Once again, please doublecheck that permissions are OK on /dev/net/tun
You want to see something like
crw-rw--- 1 root vboxusers
If you don't have that, then change the permissions--we can loosen it up for the moment while trying to get it to work, something like

sudo chmod 666 /dev/net/tun

sysctl should still be good. 

Now give the address to tap0 as described.
Do the parprouted -d again, if you don't mind, 
parprouted -d eth1 tap0

(eth1 definitely is your wireless card, correct?)

At this point if you have another machine on the network, see if it can ping tap0's address.

Then, after making sure the settings for the virtual machine are set to use host interface and the interface name is tap0, try again.  

If you're running Windows Xp as the virtual machine, for now turn its firewall off.

---

### Post by Silvr2008 on 2008-03-21
okay, I did it again. eth1 is definantly my wireless. I can ping tap0 from my other PC and tap0 is set in the VB settings. I turned off the windows firewall and the net settings are:

IP:192.168.1.151
Sub:255.255.255.0
Gateway:192.168.1.1
DNS:192.168.1.1

Its gotta be a problem with VB and my adapter.

---

### Post by scottro on 2008-03-21
Ok, so we have three addresses with a 192.168.1.x address.  
The other computer can ping tap0.

However, the guest OS can't ping anything. 

I dunno, I don't think it's the adapter.  About the only thing I can suggest at tihs point is to try the other cards listed as possibilities in VirtualBox settings.  However, each time, I would first stop VirtualBox, remove tap0 like we did before and kill parprouted.  Then start them up again, and try the other two cards--maybe the Intel virtual card will work. 
Also, for what it's worth, I see I'm running version 1.5.4 OSE.

Again, in each case, I'd do this--stop VBox, pkill parprouted, ifconfig tap0 down tunctl -d tap0.  Then start it again.

However, this is quite weird--all of a sudden, it isn't working for me on Ubuntu either.   I did a system update, but didn't pay attention to whether or not VBox was updated. 

Ok, now we're both in the same boat.  :)

---

### Post by Silvr2008 on 2008-03-21
LOL, see what happens when you try to help someone. I am going to uninstall VB and install from their webpage. Last time when I did the reverse, I just moved my folder called Machines and moved it to the new VB folder, but I got all kinds of errors. Have you done this before?

---

### Post by scottro on 2008-03-21
Yes, and I've had no problems. Make sure you get the big one, errm--I just shut down the laptop running Ubuntu in disgust, so now I can't think of the name.  It's in .VirtualBox (note the dot) and it might be loose in there--I think it's the one with the .vdi file.  What I do is this.  

I take the file and put it anywhere.  Then, when creating a new machine with the new installation I stop, and put it in the new .VirtualBox directory that has just been created.  (This is at the point when they say new disk or use something--I'm sorry, I'm irked right now. ) :)  Hopefully, you know the part I mean, where you can create a new file system or use an existing one.   At that point, I move the .vdi (if that's what it's called) into the new .VirtualBox directory, click add and it finds the file.                  

Just keep in mind that when you install it from their website, you will probably have to run the vboxdrv update each time you update the kernel.  It's not a big deal, takes a minute or two and they tell you exactly what command to run.  Just don't panic if the kernel gets upgraded and you start VirtualBox and get an error saying you won't be able to use it until you run the command.  

I suspect I could get it working (yeah, sure) but right now, I'm just irked at it.  
In fairness, though, I'm working with Hardy which is still beta.  
(I actually don't run it very often on Ubuntu--I had just put it in when you posted that my marvelous guide wasn't working for you.)  

All I can say now is that it has worked for me, on Ubuntu, in the past.  :)

Also, again in fairness, although right now Ubuntu is the only one of several distros where I can't get it working, as a rule, one reason I keep Ubuntu around is because it's the most likely to Just Work(TM). 

Not in this case, however.  :-(

---

### Post by Silvr2008 on 2008-03-22
Reinstalled VBox with 1.5.6 and started the Host configuration from scratch and still nothing.

---

### Post by Silvr2008 on 2008-03-22
Last night I was messing with some stuff and broke my wireless. I couldn't figure out how to fix it so I reinstalled Ubuntu. When I reinstalled VBox this morning and followed your tutorial it worked great. Thanks for your help.

---

### Post by scottro on 2008-03-22
Now I'm the one laughing.  I'm glad it is working,

I wish we could figure out what in our respective installs keeps it from working sometimes.

---

### Post by modnar0741 on 2008-04-06
I'm having this same problem.  I've followed the tutorial.  I have a wireless connection on my laptop.  When Windows XP boots up in VirtualBox it claims there's a conflicting IP.  I can ping the tap0 IP address from another box, but I cannot ping from the tap0 interface to any other IP (not even the wireless IP) using "ping -I tap0 xx.xx.xx.xx".  I'm capable of using Wireshark, so please let me know what I need to do to solve this problem.

---

### Post by Silvr2008 on 2008-04-06
You must have set the vbox IP the same as the host IP or another IP on your network maybe. You want all computer including the vbox to have differant IP's but on the same net if you want them to communicate with each other.

---

### Post by modnar0741 on 2008-04-06
No, I didn't set it to the same IP.  Is tap0 supposed to have the same IP as XP or different?  I've tried both, neither works.

---

### Post by Silvr2008 on 2008-04-06
It needs to be different. So, eth1, tap0, and the virtual adapter in vbox will all have different IP's.

---

### Post by modnar0741 on 2008-04-07
Well, I booted it up again and everything worked (no configuration changes).  So I don't know how but it's working now.

---

### Post by galusha1 on 2008-05-06
Ok, so its a little later than anyone else but, im running suse 10.2, cause 10.3 is dumb, and running the newest virtualbox with windows xp, the bridge to use the wireless input from the wlan0 is read fine by xp and i use that wireless. when i was looking through all these forums what i was really looking for was a way for windows to use the wifi card and connect that way since the windows drivers for the usb pen drive work far better and pick up 4 or 5 times as many networks and stays connected longer.

---

### Post by xmanwe on 2008-05-27
well, i have exactly the same problem as Silvr2008.. i went thtough loads of tutorials and articles, but there is still something wrong and i am no able to bridge the wireless into a virtual machine. (i've try both vms - win and linux also)

here is the script vbox_wlan_start
[I]
#!/bin/bash
sudo chmod 0666 /dev/net/tun
sudo chmod 0666 /dev/vboxdrv
sysctl net.ipv4.ip_forward=1
sudo tunctl -b -u manwe
ip link set tap0 up
ip addr add 192.168.169.53/24 dev tap0
sudo parprouted wlan0 tap0
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE[/I]

and here is the wbox_wlan_stop
[I]#!/bin/bash
sudo ifconfig tap0 down
tunctl -d tap0
sudo pkill parprouted
sysctl net.ipv4.ip_forward=0[/I]

present default ifconfig for wlan0 is:

[I]wlan0     Link encap:Ethernet  HWaddr 00:30:05:de:38:35
          inet addr:192.168.169.50  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:44841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24619794 (23.4 MB)  TX bytes:3468256 (3.3 MB)[/I]

and after running of vbox_wlan_start:

[I]wlan0     Link encap:Ethernet  HWaddr 00:30:05:de:38:35
          inet addr:192.168.169.50  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:44842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24619836 (23.4 MB)  TX bytes:3468298 (3.3 MB)

tap0      Link encap:Ethernet  HWaddr 00:ff:5c:b6:ef:42
          inet addr:192.168.169.53  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::2ff:5cff:feb6:ef42/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:19 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/I]

you mae be interested in /etc/network/interfaces, so here it is:

[I]auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto wlan0
allow-hotplug wlan0
iface wlan0 inet dhcp

auto tap0
iface tap0 inet manual
  tunctl_user root

#  auto br0
#  iface br0 inet manual
#  bridge_ports eth0 tap0
#  bridge_maxwait[/I]


so, do you have any idea what i am doing wrong? when i started virtual xp (just for the test, i need the connection for the centos and trixbox voip pbx) and nearly after it's starting i checked the ipconfig and it gave me the right hostname which belongs to my wifi.. but nothing more. no ip address or whatever.. when i tried to set it manually, it returns "limited or no connectivity" and hostname si gone as well...

could it that be because of kubuntu hardy beta? when i was upgrading over the internet (from hardy beta to official stable), i remember there were some weird problems (at the end of upgrd) and i am not sure if it was upgraded correctly. i am not able to upgrade via cd (it gives me command not found when i run /cdrom_mount_point/cdromupgrade)

and when the grub is starting, there are ubuntu 8.10 development, branch titles.. so i don't really know.. i did full update again (fetch all of the upgradable packages) and there were no "distribution upgrade" button, so i've just applied the changes.

---

### Post by scottro on 2008-05-27
I'm rushing off to work, so might have missed something. 

However it looks as if you didn't do the route add part that we discuss somewhere in the thread and that is on my page--the place where after parprouted we add the route to tap0.

Also, if it's VirtualBox 1.6, that's having serious trouble with bridged networking, where it works, but only occasionally. 

I don't see mention of which version of VBox that you're using, and I didn't see that adding of the route, but as I said, I only took a VERY quick look and if both of those are there, I apologize.

---

### Post by xmanwe on 2008-05-28
No, my mistake, I did not write about VBox version.. It's 1.5.6

And actually I did use *sudo route add -net 192.168.169.0 (//according to my network) netmask 255.255.255.0 tap0*

but it has done nothing at all.. :(

---

### Post by bluefrog on 2008-05-28
if you need/want host networking on a computer which has a wifi card AND an ethernet card (not talking about the cable to be plugged in, just the ethernet card device) follow the How To (written with virtualbox 1.6 and Hardy)

[http://ubuntuforums.org/showthread.php?t=782936&highlight=virtualbox+wifi](http://ubuntuforums.org/showthread.php?t=782936&highlight=virtualbox+wifi)

It only uses tools that are already included on your ubuntu computer (besides bridge-utils uml-utilities which you must install as per virtualbox help)

James Dupin

---

### Post by scottro on 2008-05-28
If the link bluefrog gave you doesn't work, about the only other thing I could suggest is trying it without iptables.  Something like sudo iptables -F and seeing if it works then. 

Otherwise, I confess I'm stuck.  I can't duplicate the problem.

---

### Post by timjohn7 on 2008-06-03
Could someone PLEASE direct me to the definitive solution to getting wireless networking working from VBox 1.6 (Non OSE) running WinXP SP2 guest under Hardy (with all updates) host?
My wireless card is an Artheros chipset and works perfectly under Hardy as ath0
I have looked at the numerous HOWTOs and Solveds on this forum, but have not yet found THE one that works... and many refer to wired connections.
I am a newb, so please post code and some explanation for my education.

---

### Post by bushsux on 2008-06-04
Well I finally got it work and in the end I didn't use parprouted. Here is what work for me with the guest os set to 192.168.0.52.

VBoxTunctl -b -u bushsux
ifconfig tap0 192.168.0.51 up
sysctl net.ipv4.ip_forward=1
sysctl net.ipv4.conf.tap0.proxy_arp=1
arp -Ds 192.168.0.52 eth1 pub
route add -host 192.168.0.52 dev tap0

Hardy
VBox 1.6
Guest XP
Cisco VPN Client works!

---

### Post by scottro on 2008-06-04
Thanks for that information.  I will have to try it that way next.

(Won't be for awhile though I fear, incredibly busy these days.)

---

### Post by echo6 on 2008-07-31
> **bushsux said:**
> arp -Ds 192.168.0.52 eth1 pub
Aren't you missing an argument here, e.g. -i <interface>

I got this method working :-) On a Linux Guest and a XP guest, but I used the following.
arp -i wlan0 -Ds 10.0.0.33 tap0 pub
route add -host 10.0.0.33 dev tap0

guest IP has the IP address of 10.0.0.33
wlan0 has an IP address of 10.0.0.11
tap0 has an IP address of 10.0.0.254

Which if I understand it correctly means wlan0 interface will answer all ARP requests for the IP 10.0.0.33,  and tap0 has an added host on its interface of 10.0.0.33.

This is a bit of kuldge all round really, it would be ideal if there was a way to make this work auto-magically.  Remembering IPs for all your added guests and tap interfaces is going to be a nightmare.

---

### Post by bushsux on 2008-12-22
Well VirtualBox 2.1 is magic! Networking now just works.

---

### Post by yonas on 2009-05-06
> **bushsux said:**
> Well VirtualBox 2.1 is magic! Networking now just works.

Wireless networking does not work outofthebox for me.
- Ubuntu Jaunty, VB 2.1

**EDIT:**
"Select host interface (or bridge network in 2.2) and then your wifi card."

---

