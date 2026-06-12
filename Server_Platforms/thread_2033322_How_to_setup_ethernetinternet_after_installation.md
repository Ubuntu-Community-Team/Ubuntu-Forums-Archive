---
title: "How to setup ethernet/internet after installation?"
date: 2012-07-26
forum: Server Platforms
---

### Post by hesson on 2012-07-26
Hi,

i recently installed Ubuntu server 12.04 on my computer. During the installation process, I could not connect to the internet so I skipped that step and I never established a proper connection (I didn't know I had to connect an ethernet cable so I guess that's why it didn't work). Anyways, now I can't really download or install applications on my server because I don't have a connection. So what do I do now? How can I configure a network connection. My network details:

gateway: 192.168.0.1(lan) / 216.58.60.129(wan)
subnet mask: 255.255.255.0 on my other computer's wireless internet 
but it says 255.255.255.224 on router's page for some reason.
primary dns: 209.197.128.2
sec dns: 209.195.95.95

results of ifconfig -a give eth0,eth1, and lo. I think eth0 is wireless and eth1 is ethernet, although i may be wrong.

/etc/resolv.conf:
nameserver 209.197.128.2
nameserver 209.195.95.95

(i added these manually based on dns ip's)

/etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

(i added the latter part)

pinging 192.168.0.1 actually does the ping but none of the packets reach, it says "Destination Host Unreachable" for every ping

(all this with the ethernet cable connected - i connected it after installation completed)

now i'm confused. how should I go about configuring an ethernet connection (i'll worry about wireless later)?

Thank you so much.

---

### Post by stlsaint on 2012-07-26
[https://help.ubuntu.com/11.10/serverguide/network-configuration.html](https://help.ubuntu.com/11.10/serverguide/network-configuration.html)

---

### Post by BkkBonanza on 2012-07-26
Generally eth* device names are ethernet (wired) and wifi names use wlan*.

Do you have two ethernet ports on that machine? If so make sure you are connecting the cable to the correct one.

Try **sudo /etc/init.d/networking restart** to make sure everything has been reset fully.

Check the output of **route -n** and make sure you have a default gateway and that the network routes are as expected. It sounds like you have your interfaces file set correctly so just be sure eth1 is the interface you are actually connecting your cable to and not eth0.

If you have changed a network adapter since installing, or had two but removed one or swapped one, then it can end up with both names. Usually only one will show up with ifconfig -a but perhaps there's a reason for both to show up. Again, be sure the one you configure in the interfaces file is the actual one active.

Try **ifconfig** (without the -a) to see which interface is actually up and has an IP assigned. 

Make sure that the IP you ping is actually in the network range being used by your DHCP server. The route command should show that IP in the range associated with your interface, or if not it should be reachable by the default gateway machine, otherwise you will get the "unreachable" error message.

Hmm. Not sure what else I'd do now but these steps would typically clear up this kind of problem for me.

---

### Post by darkod on 2012-07-26
Since you are only activating eth1, if you have plugged the cable in eth0 it will not work.

In any case, having your server use DHCP to get an address is not a good practice since usually you would like a static unchangeable address on your server. In that case you will need to modify /etc/network/interfaces something like:
```
auto eth1
iface eth1 inet static
   address 192.168.0.x
   netmask 255.255.255.0
   gateway 192.168.0.1
   dns-nameservers 209.197.128.2 209.195.95.95
```

The above is under the assumption you are using eth1. If you are using eth0 just replace eth1 with eth0.

And since you are little bit confused about the subnet masks (netmasks). Don't confuse the mask your computer has towards your home LAN, and the mask your router has towards the ISP network. That's why they are different. For your home LAN you would usually use 255.255.255.0.

---

### Post by hesson on 2012-07-26
Thanks guys, I appreciate your help. I'm at work right now so I can't do anything on my server just yet. I'll make sure to try out your suggestions first thing when I get home.

---

### Post by darkod on 2012-07-26
Just to add, to be more exact. When I wrote 192.168.0.x for your server address of course you will replace the x with a number between 2 and 253 (since your router is 1).

First you should confirm the DHCP range that your router is serving, and select a static IP for the server OUTSIDE that range (so that the same IP is not allocated to any computer by chance).

Your router will rarely issue all range between 2 and 253, if it does, make it smaller. You probably don't have 250 machines at home. :)

Any static IP that is outside the DHCP range and that is unique (not allocated to any device on the LAN), is good.

---

### Post by hesson on 2012-07-26
Thanks guys, that solved my problem.
First, I changed my interfaces file for a static ip as darkod suggested. I used eth1. Also, I used 192.168.0.2, since that wasn't used by any other machine (I checked on my router's page). I don't have two ethernet ports on my computer, just one, but I have a phone jack which is likely treated as an ethernet interface. After restarting the network as suggested by BkkBonanza, the ip's that I had written in my interfaces file were now showing up in the route table and ifconfig whereas they hadn't before. I'm just wondering if this is permanent? I guess I'll find out the next time I boot. I started pinging various websites, and voila it worked. Thanks a bunch guys. Now I'll try to configure the wireless network.

---

### Post by darkod on 2012-07-27
Yeah, /etc/network/interfaces content is permanent. The line 'auto ethX' tells it to activate that interface on boot. Without that line for example, the IP configuration is worthless since it will not activate eth1. You have to watch out for that in ubuntu server. Not all interfaces are activated by default.

If you had two ethernet ports, one can be configured during installation and activated automatically, but the other not. Without the 'auto ethX' it will not start to work.

---

