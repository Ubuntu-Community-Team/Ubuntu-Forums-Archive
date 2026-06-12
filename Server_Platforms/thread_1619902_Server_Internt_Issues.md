---
title: "Server Internt Issues"
date: 2010-11-12
forum: Server Platforms
---

### Post by andrewcow on 2010-11-12
Hi
So I am new to Ubuntu Server. I am installing it on one of my old PCs and am trying to connect to the internet. The OS detects the two ethernet cards I have installed and I try connecting through the one on the motherboard but to no avail. I  try connecting through the one in a PCI card but the same problem saying something like "The DHPC settings can not be configured". I have tried setting up a static IP on my router but probably did it wrong. All I want to be able to do is connect to the internet so I can install apache and host a web site. What am I doing wrong?
Thank you
AndrewCow

---

### Post by CharlesA on 2010-11-12
Can you post the output of these commands when run in a terminal:

```
ifconfig
```
```
cat /etc/network/interfaces
```
```
route
```

---

### Post by Skavenger0 on 2010-11-12
Firstly you might want to post the results of ifconfig

Second heres a guide to add a static IP to the server:

```
sudo nano /etc/network/interfaces
```

You will see this:

```
auto eth0
iface eth0 inet dhcp
```

Change to somthing like this:

```
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

Now restart the network service

```
sudo /etc/init.d/networking restart
```

---

### Post by andrewcow on 2010-11-12
ifconfig - 

Link encap:Locap Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carriers:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B)    TX bytes: 0 (0.0 B)

cat /etc/network/interfaces - 

(after the # notes)
auto lo
iface lo inet loopback

route - 

Kernal IP routing table
Destination       Gateway         Genmask         Flags Metric Ref     Use  Iface


Thanks
Ill try the static ip things thanks :)
AndrewCow

---

### Post by Skavenger0 on 2010-11-12
According to the results from ifconfig Ubuntu hasnt picked up your network cards at all so its not getting an IP or settings.

I'm not sure how to test drivers, hopefully charles or someone else can be more helpful on that part.

Do you know what make and model your network cards are?

---

### Post by CharlesA on 2010-11-12
Try this:

```
sudo ifconfig eth0 up
```

Then post ifconfig again (and any error messages with the above command)

---

### Post by andrewcow on 2010-11-12
They are a bit old. One is built into my motherboard. During setup, it is detected and called
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
The other one is the PCI card which is detected on setup as
Silicon Integrated Systems [SYS] SiS900 PCI Fast Ethernet

I hope that means something. I thought it might be something to do with drivers.
Thanks:)
AndrewCow

---

### Post by andrewcow on 2010-11-12
Hi
I did what you said. I didn't get any error messages. Here is the ipconfig
[ SORRY THE QUALITY IT NOT GREAT]("http://picasaweb.google.com/lh/photo/MyFcyB8GJk7OjNYJ85YHag?feat=directlink")

Thanks
AndrewCow

---

### Post by andrewcow on 2010-11-12
Hmmm. I may now have internet. How do I tell. I still cant seem to install anything external but the ifconfig is sending and receiving packets......i think....
Thanks
Andrew

---

### Post by CharlesA on 2010-11-12
Well it found that one.

Do you have a DHCP server on the network somewhere?

Try setting it as a static IP based on Skavenger0's post above, and see if it shows an ip.

Just ping google and see if you get a reply.

---

### Post by andrewcow on 2010-11-12
:( oops I actually didn't get it working.
if I ping google I get
ping: unknown host [www.google.com](www.google.com)

if I ping 192.168.0.1 I get
It pings it but gets no responses

:(
Could it be the drivers?
Thanks
AndrewCow

---

### Post by CharlesA on 2010-11-13
What is the IP address of yer router (and brand/model).

If you set a static IP, are you able to access anything on the local network by IP address?

---

### Post by milocat on 2010-11-13
Not trying to hijack this thread, but I am having very similar problems. I have found that if I execute[PHP] sudo /etc/init.d/networking restart[/PHP]my networking will work fine. On a warm reboot or cold restart, my networking will not restart until I manually enter the line above from the prompt.

I have tried both dynamic and static addressing.

It is as if the network is not being started automatically at start-up.

I am running 10.10 Server on a brand new ASUS TS Mini.

---

### Post by andrewcow on 2010-11-17
oo got it working thanks all:)

---

