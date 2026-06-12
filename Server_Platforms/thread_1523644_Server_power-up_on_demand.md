---
title: "Server power-up on demand"
date: 2010-07-04
forum: Server Platforms
---

### Post by slick666 on 2010-07-04
I've done some searching on the forums and on Google but I'm afraid I'm using the wrong terms and am not finding anything on what I'm trying to do. 

I have a sever whose usage fluctuates where it may go unused for weeks. What I would like to happen is that the server hibernate automatically after going unused for a period of time. Then when trying to connect (ssh, http etc.) the server would automatically resume.

Does anyone know if this is possible and what mechanism(s) are used?

---

### Post by DJYoshaBYD on 2010-07-04
Yes.. google a feature called "wake on LAN" or "wake on ethernet"

you cannot do it from a full power down.. but from sleep you can.. i just know that linux has some issues with sleep mode, so test it well before putting it into production..

---

### Post by Ryan Dwyer on 2010-07-04
I thought you could do it from a full power off. The network card stays on standby (usually with an orange light) and listens for some certain packets. When it gets them, it powers on the computer if it supports it.

The downside is you need another computer in the network to stay on so it can send the packet data required to wake the machine.

---

### Post by DJYoshaBYD on 2010-07-04
i have heard of mobos that support a full power off feature, but they usually dont work right..

if you have a good router running dd-wrt or something, im sure there is a way you can try to access a port forwarded IP:port, and have it send the start-bits to the computer.. 

it really does work from almost a full power off, but I have never actually seen one boot from a full shutdown.. not saying it doesnt work.. just never seen one..

---

### Post by WinstonChurchill on 2010-07-04
> **slick666 said:**
> I've done some searching on the forums and on Google but I'm afraid I'm using the wrong terms and am not finding anything on what I'm trying to do. 

I have a sever whose usage fluctuates where it may go unused for weeks. What I would like to happen is that the server hibernate automatically after going unused for a period of time. Then when trying to connect (ssh, http etc.) the server would automatically resume.

Does anyone know if this is possible and what mechanism(s) are used?WakeOnLAN is what you want - and it does work from a full shutdown; you just have to be sure that it is enabled in your BIOS. It will either be called "Wake on LAN" or "PME" - it varies depending on the BIOS vendor. Most home routers have a utility that will do this, and that's your best option. 

If that's not possible, this makes it more difficult... the "Magic Packet" that triggers the wakeup can be anything at all (it doesn't even have to have any headers above Layer 2) - it just has to contain six bytes of "FF" followed by sixteen repetitions of the computer's MAC address (the one you're waking up). It is usually sent as a UDP datagram on port 7. The idea here is that you send a magic packet to your home router's public IP, which will then be sent to your server and wake it up. But, you can't just port-forward port 7 to your server's IP, because the Ethernet switch on your home router will forget your server's physical address when it is turned off. The magic packet has to be sent to the broadcast address for your subnet so the Ethernet switch will send it out on all its ports and your server will "see" it. So, if your home network is on the subnet 192.168.1.0/24, for example, you should port-forward to 192.168.1.255, which should end up sending the packet to a Layer 2 address of FF:FF:FF:FF:FF:FF - I'm not entirely sure about that however; you'd have to experiment with it.

---

### Post by Vegan on 2010-07-04
Wake on LAN does not like NAT, everything needs an IP address.

---

### Post by lisati on 2010-07-04
I agree that "Wake on LAN" might have some possibilities. My server machine also has a BIOS option to power up automatically after a power cut, but I don't remember seeing an option to "Power-up on LAN".

---

### Post by slick666 on 2010-07-16
I've been trying to do as much reading and learning as I can but it seems that WOL is only half of the configuration. How would (or do) you determine if a machine can sleep and what program/package would you use.

---

### Post by slick666 on 2010-11-21
I've been thinking about this some more recently and found this link that was helpful for those looking into this.

[http://www.lesswatts.org/tips/ethernet.php]("http://www.lesswatts.org/tips/ethernet.php")

---

