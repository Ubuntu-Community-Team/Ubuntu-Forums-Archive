---
title: "New - Aid in getting up and running."
date: 2006-08-22
forum: Server Platforms
---

### Post by Low-Key on 2006-08-22
Im new to linux and I have a spare PC lying around and decided that I should get a server up and running.

So I downloaded Ubuntu 6.06 server and installed as a LAMP this morning.

I am now following this guide to get set-up. 
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3)

Remember this entire command line only stuff is new to me as im a windows boy at heart.

I followed the instructions

vi /etc/network/interfaces
and changed it to
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 192.168.123.110
        netmask 255.255.255.0
        network 192.168.123.0
        broadcast 192.168.123.255
        gateway 192.168.123.254

I got the values from these from windows ipconfig 

Then I did this:
vi /etc/hosts

the original said 
127.0.0.1 localhost
127.0.0.1 ubuntu

I changed it as per the guide to say:
127.0.0.1       localhost.localdomain localhost
192.168.123.110   server1.example.com     server1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Then the guide says to type 
hostname
hostname -f

and both should say "server1.example.com"

but mine dont. hostname shows
"ubuntu"
and hostname -f shows
"hostname: Unknown host"

So before I continue and screw things up I figured I would post and ask what I have done wrong so far.

Yes I did shutdown the system as well and it has made no change, and yes I have saved the files.


Thanks!

---

### Post by Low-Key on 2006-08-22
If im asking in the wrong forum please let me know. I just want to get ssh working so I dont have to be on the machine itself and can work from my windows machine.

---

