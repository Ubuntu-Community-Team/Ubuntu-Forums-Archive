---
title: "How to install network-manager-vpnc?"
date: 2013-07-01
forum: Security
---

### Post by WhiteHatGuy on 2013-07-01
Hi

Ok I put this command

sudo apt-get install network-manager-vpnc

And succesfully install it. Everything works fine. Except for one thing. When I try to connect to the vpn, does not connect. Everything is properly configured in gui network-manager-vpnc.

And actually I know what it is the problem. I know I am missing one command. But I can remember what it was. I was able to find this command in a website but I didnt save it to bookmarks.

I know that if I put this command is going to work fine. But I cant remember it. In the website said in order to install network-manager-vpnc

1) sudo apt-get update
2) Then, the command I am missing
3) sudo apt-get install network-manager-vpnc


Thanks

---

### Post by Soul-Sing on 2013-07-01
is the package not network-manager-gnome? instead of that vpnc one? (or kde)
this package comes with vpn support.

---

### Post by WhiteHatGuy on 2013-07-01
I am using Lubuntu 13.04. With LXDE desktop enviroment

I am not using gnome. 

I am going to try to install it from synaptic package manager and see what happends.

I have not figure it out this one yet

So weird

---

### Post by Soul-Sing on 2013-07-01
I am using LXDE , with that package. No problems here.

---

### Post by WhiteHatGuy on 2013-07-01
> **Soul-Sing said:**
> I am using LXDE , with that package. No problems here.


Yep, you are right, also synaptic package manager its sais that I should install it. I thought only people using gnome desktop enviroment had to install it.

Ok I am going to try that. I hope it works. Cross fingers :D

Thanks.

---

### Post by Soul-Sing on 2013-07-01
Indeed fingers crossed. If you need help setting up a VPN you can pm me about that, or better the FAQ/wiki of your VPN service.

---

### Post by WhiteHatGuy on 2013-07-01
> **Soul-Sing said:**
> Indeed fingers crossed. If you need help setting up a VPN you can pm me about that, or better the FAQ/wiki of your VPN service.





LOL I didnt see this one coming. It was the firewall gufw. I was blocking the port that the vpn use. hahahaha. OMG

Now it works fine. :lolflag:

---

