---
title: "using a PCI wireless Card in VirtualBox"
date: 2008-01-29
forum: Virtualisation
---

### Post by ianb72 on 2008-01-29
Hi
I have set up Virtualbox in Gusty and installed Win XP with my Belkin wireless card that I use under Gusty and used to use in Windoze.

But when I try to run the software after install, it tells me there are no adapters found :(

Can I use my wireless card in Virtualbox???
Many Thanks for any help anyone can give me

Ian

---

### Post by dark_harmonics on 2008-01-29
Your virtualbox should pick it up as a connection no matter how your ubuntu is connected. Sounds to me like you might be having an issue getting the wireless card to work under gutsy. I've never fixed this sort of problem (outside of using madwifi or ndiswrapper) but you should definately attack it from this angle.

---

### Post by Seisen on 2008-01-29
Actually you might need to activate the network adapter in Virtualbox, Virtualbox doesn't use your wireless card and graphics card, it basically creates virtual one's.

---

### Post by ianb72 on 2008-01-29
> **dark_harmonics said:**
> Your virtualbox should pick it up as a connection no matter how your ubuntu is connected. Sounds to me like you might be having an issue getting the wireless card to work under gutsy. I've never fixed this sort of problem (outside of using madwifi or ndiswrapper) but you should definately attack it from this angle.

I have My wireless card working fine under gusty without Ndiswrapper, just using Gusty's networking manager.

---

### Post by ianb72 on 2008-01-29
> **Seisen said:**
> Actually you might need to activate the network adapter in Virtualbox, Virtualbox doesn't use your wireless card and graphics card, it basically creates virtual one's.

I have the network adapter selected in Virtualbox but it still doesn't pick up the card, when it used to work fine under windoze great, well its a windoze card and software.

It is working great in Gusty using the networking manager, the card is a Belkin F5D7000 v3

---

### Post by bollix47 on 2008-01-29
Are you using NAT for your network connection in VirtualBox?

That's the setting to get VB to use your host's network connection.

---

### Post by ianb72 on 2008-01-30
> **bollix47 said:**
> Are you using NAT for your network connection in VirtualBox?

That's the setting to get VB to use your host's network connection.

Hi 
Yeah I have selected the NAT for my network connect, should I of done that or not??

Ian

---

### Post by dark_harmonics on 2008-01-30
Yea i've never had to select the network card or mess with drivers. Whatever network connection i have is just shared over. For instance, if i switch to wireless (on a macbook gutsy 64bit install) on my 32bit install of windows from my wired connection, i dont need to do anything. It just works. I thought virtualbox just ports over your linux connection??

---

