---
title: "No Internet access on my XP"
date: 2007-11-11
forum: Virtualisation
---

### Post by AndyCat on 2007-11-11
hello there. I just installed my VMWARE server and everything is running. I needed to access internet on my virtual XP and couldnt do it. How do i bridge my connection? Before i had it connected it with a cable but now I need to use a wireless card (netgear) to have access both to my network and Internet.Ubuntu has internet but not my VMware server.

thanks

---

### Post by Martym on 2007-11-14
I am trying to figure that out myself.  I thought I had it last night, XP said it was connected at 1Gbps, but I could not get anywhere.

---

### Post by Shazaam on 2007-11-14
Are you running XP as a guest on Ubuntu? If you are, set up Ubuntu (host) for internet access first. Once you have that working set up your XP guest in the .vmx file (open with a text editor) to use either "host-only" or "nat" networking.

This is a copy of part of the vmx file for my XP guest:

# First network interface card
ethernet0.present = "TRUE"
ethernet0.virtualDev = "vlance"
ethernet0.connectionType = "nat"
ethernet0.addressType = "generated"
ethernet0.generatedAddressOffset = "0"

Once you have that set up, connect to the internet with Ubuntu first, start your XP vm and you should be able to surf the net from the XP guest. Make sure you have your internet options set up for "Direct Connection to the Internet" for Internet Explorer AND any other browsers you have.

---

