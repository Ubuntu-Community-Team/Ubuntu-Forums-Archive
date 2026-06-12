---
title: "Ubuntu repositories question"
date: 2009-08-24
forum: Server Platforms
---

### Post by AlexenderReez on 2009-08-24
Hi all gurus,

i have successfully install 4 ubuntu server 8.04 as virtual machine in XenServer.



I'm having problem that i can't update software or install anything .

sudo apt-get update will resulting update failed. 

i'm sorry i can't post the output because XenCenter doesn't allows me to copy its output to other machine.


 I did configure static ip at

/etc/network/interfaces

> # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 168.118.218.185
netmask 255.255.255.0
gateway 168.118.218.1


i can ping [www.google.com](www.google.com) ip..so i don't think i'm having internet problem..is it because repositories ip is still dhcp or difference with my static ip?

any clue how to solve this?

---

### Post by Sam Lars on 2009-08-25
Could you be more specific about what you get when the update fails?

---

### Post by slakkie on 2009-08-25
Post the output of aptitude update

---

