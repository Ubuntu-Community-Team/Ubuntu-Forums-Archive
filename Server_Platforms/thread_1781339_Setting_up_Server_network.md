---
title: "Setting up Server network"
date: 2011-06-13
forum: Server Platforms
---

### Post by FerraraZ on 2011-06-13
Hey everyone, firstly I'm a huge newbie with Ubuntu but slowly learning as I go. I've been following the this guide:

[http://net.tutsplus.com/tutorials/ph...rver-for-free/](http://net.tutsplus.com/tutorials/ph...rver-for-free/)

To setup a web server at my office (intern). I'm stuck at updating the web server with the given distro's. We dont use DHCP and the computer must have static ip address. I've checked this in /etc/network/interfaces and from what I am seeing, everything is correct (ip address, subnet mask, default gateway, dns servers) however when I go to update I'm still receiving "temporary failure resolving 'us.archive.ubuntu.com etc"

Is there something I am missing or something that I can change or check? Weird thing is, when I install the ubuntu live disk and have eht0 sets with these values, I can connect to the internet without a problem.

---

### Post by collisionystm on 2011-06-13
> **FerraraZ said:**
> Hey everyone, firstly I'm a huge newbie with Ubuntu but slowly learning as I go. I've been following the this guide:

[http://net.tutsplus.com/tutorials/ph...rver-for-free/](http://net.tutsplus.com/tutorials/ph...rver-for-free/)

To setup a web server at my office (intern). I'm stuck at updating the web server with the given distro's. We dont use DHCP and the computer must have static ip address. I've checked this in /etc/network/interfaces and from what I am seeing, everything is correct (ip address, subnet mask, default gateway, dns servers) however when I go to update I'm still receiving "temporary failure resolving 'us.archive.ubuntu.com etc"

Is there something I am missing or something that I can change or check? Weird thing is, when I install the ubuntu live disk and have eht0 sets with these values, I can connect to the internet without a problem.


post your /etc/network/interfaces file output

Can you ping google.com or ubuntu.com


Your DNS server address should be placed in

/etc/resolv.conf

it should say

nameserver xxx.xxx.xxx

I.E..

nameserver 8.8.8.8

---

### Post by FerraraZ on 2011-06-13
> **collisionystm said:**
> post your /etc/network/interfaces file output

Can you ping google.com or ubuntu.com


Your DNS server address should be placed in

/etc/resolv.conf

it should say

nameserver xxx.xxx.xxx

I.E..

nameserver 8.8.8.8

I cannot ping to google or ubuntu, says unknown host.

As for giving you the outputs I'm unsure how I could do that within Ubuntu Server unless I type it all out.  I will make sure the DNS server is in the correct place and try pinging.

---

### Post by FerraraZ on 2011-06-13
Alright well alittle bit better now.  Atleast its saying its trying to connected:

Writing extended state information... Done
0% [Connecting to us.archive.ubuntu.com] [Connecting to security.ubuntu.com]
err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Temporary failure resolving 'security.ubuntu.com'

It just keeps repeating that.

---

### Post by cabaro on 2011-06-13
Hi,

please post the output for following commands:

```
cat /etc/network/interfaces
```
```
cat /etc/resolv.conf
```
```
ifconfig
```
```
host www.google.com
```

/cab

---

### Post by FerraraZ on 2011-06-13
> **cabaro said:**
> Hi,

please post the output for following commands:

```
cat /etc/network/interfaces
```
```
cat /etc/resolv.conf
```
```
ifconfig
```
```
host www.google.com
```

/cab

I am sorry I'm so very new that I'm unsure how I can copy and post the output of those commands that you asked other than retype them on my laptop.

---

### Post by Cheesehead on 2011-06-13
Well, you can look at the output and google the more interesting strings on your laptop. You can learn a lot that way.

Or you can simply google the filenames we're asking for...a lot of tutorials for them are out there. Any of them will tell you what *should* be in those files, and then you know what to do.

Or, you can save output from those files (if you know how) to a USB drive (if you know how to mount/unmount it) and walk it over to your laptop.

But, yeah, you can also type them into your laptop if that's easiest for you. Please be careful with the spelling.


Tip: One of the easiest ways to learn about basic server setup is to use a VM. You can make lots of mistakes (and undo them) before doing the process on real hardware. You can save days of frustration that way....

---

### Post by cariboo on 2011-06-14
> **FerraraZ said:**
> I am sorry I'm so very new that I'm unsure how I can copy and post the output of those commands that you asked other than retype them on my laptop.

Just highlight the text in a terminal, leave the terminal open, and use the middle mouse button to paste. or

highlight the text in a terminal, then right-click and select copy, the in your post right-click to paste

---

### Post by FerraraZ on 2011-06-14
> **cariboo907 said:**
> Just highlight the text in a terminal, leave the terminal open, and use the middle mouse button to paste. or

highlight the text in a terminal, then right-click and select copy, the in your post right-click to paste

I have VMware on my macbook with ubuntu server and am going to try putting in the static ip address and network details here and see if I can connect to the ubuntu update servers.  I will post back what it tells me!  I really appreicate the help everyone!

---

### Post by collisionystm on 2011-06-14
I believe what you need to do is SSH to this box from your laptop. That way you can copy and paste the output.

---

### Post by FerraraZ on 2011-06-14
> **collisionystm said:**
> I believe what you need to do is SSH to this box from your laptop. That way you can copy and paste the output.

I took a pic of every command that was requested.  I also did a Vmware install however I wasnt having internet connection problems in that since it was using the DHCP from my laptop.  This computer is connected to the university network and therefore needs to have static address in order to work properly.  Anyway hopefully this helps :)

[http://i.imgur.com/dD1WZ.jpg](http://i.imgur.com/dD1WZ.jpg)

---

### Post by collisionystm on 2011-06-14
Can you ping your DNS server? 

Try making your DNS server 8.8.8.8 just to test. It is the google public DNS

---

### Post by FerraraZ on 2011-06-14
> **collisionystm said:**
> Can you ping your DNS server? 

Try making your DNS server 8.8.8.8 just to test. It is the google public DNS

I'm getting network is unreachable.  Could it be that the system is using "auto lo" instead of "autho eth0".  auto eh0 seems to have the correct network information for connecting.

Edit: Also if it helps.  When I run ifconfig - a   ,  I notice that eht0 is not listed, instead eth1 and lo are listed but neither have the correct network details.  Should I change eth1 to have the correct ip address and gateways etc.  How would I go about doing that?

Again sorry for the newbness, growing pains right?

---

### Post by FerraraZ on 2011-06-14
Thank you everyone for the help.  I basically reinstalled Ubuntu Server and configured a different network adapter, seems like I was using the incorrect one :popcorn:

Either way thanks for the help!

---

