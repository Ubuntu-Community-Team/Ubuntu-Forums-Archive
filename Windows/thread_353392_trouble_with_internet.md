---
title: "trouble with internet"
date: 2007-02-04
forum: Windows
---

### Post by Hranj on 2007-02-04
my father is having trouble connecting to the internet with our one and only windows machine. its running xp, and just recently the CPU and MB fried and we just put a new CPU and MB in.

he started up windows and everything is going fine except we cant connect to the internet. usually its just plug and play with the internet right? it is an onboard ethernet plug. any suggestions?

---

### Post by Trebuchet on 2007-02-04
Open Control Panel to Network Connections and see what it shows. Click on the existing network and the select Status under File on the left hand of the Toolbar. He may need to set up a new network or repair the existing one (Repair is another option under File). Some ISPs check to see what systems are online and they may not recognize your "new" system.

It is also possible that whatever damaged your mobo and CPU also damaged your router or modem.

---

### Post by insane_alien on 2007-02-04
are you using a NIC or is it built into the motherboard? also have tried reinstalling the software? some of it record the mac address of your ethernet so if you got it replaced(if its built into the mother board) then it might not work right.

---

### Post by Hranj on 2007-02-04
Trebuchet: it shows a connection like 1394 or something like that and when i try to repair it it says something like TCP/IP settings are incorrect or w/e and that it cannot fix it. and when i try to make another connection and choose the right settings it says that i already have a connection set up like that and it should work fine but it doesnt.

i know that its not the ISP thing because ive been able to plug in any random computer in the past with no problems. and im getting internet on all of my other computers and consoles so i dont think that i damaged my router/modem.

insane_alien: the port is built right into the mobo like my other one. what software should i reinstall?



anyone have an idea how i can fix this now that ive narrowed it down a little.

---

### Post by Trebuchet on 2007-02-04
> **Hranj said:**
> Trebuchet: it shows a connection like 1394 or something like that and when i try to repair it it says something like TCP/IP settings are incorrect or w/e and that it cannot fix it. and when i try to make another connection and choose the right settings it says that i already have a connection set up like that and it should work fine but it doesnt.

i know that its not the ISP thing because ive been able to plug in any random computer in the past with no problems. and im getting internet on all of my other computers and consoles so i dont think that i damaged my router/modem.1394 indicates a Firewire connection; most routers and external modems use USB or Ethernet connections. If the modem is working with other computers then I'd try uninstalling the connection and then use the New Connection Wizard in Network Connections to try and reestablish the connection from scratch. If you can get a connection you may have to reenter your ID and password from scratch; I hope you've got them written down.

If you have an Ethernet cable then use that because those are always less problematical than USB connections. USB has come a long way since the old days of Plug 'n' Pray, but it's still not perfect.

EDIT: If you haven't already, try a different connection cable. It's possible the cable or plug is damaged; I had that problem a few weeks ago and kept losing my net connection. Turns out one of the USB sockets on my elderly mobo had gone bad. I installed an ethernet card and it's worked perfectly ever since.

---

### Post by Hranj on 2007-02-04
the ethernet plug im trying to use is right on the mobo. no usb involved here.

my connection goes from my modem to my router and then to my computer.

idk why it would be coming up as a firewire since its right on the board. 

ive tried switching out the cables. had no effect whatsoever. 

i think something else is at work here because there is all kinds of hell going on now. there is no more welcome screen when i log out. i tried to change it back but it says the NetWare has changed it because its "faster". says to uninstall it but cant. does anyone have any idea what the hell is going on. dads yelling at me cause i cant figure it out, but i have no idea what is going on. 

this is supposed to be a no bashing forums but

WINDOWS SUCKS!!!!

---

### Post by empthollow on 2007-02-04
try this, go to start -> run type "command", at the prompt type
```
ipconfig /release
```
when that is complete type
```
ipconfig /renew
```
that will release and renew ip addresses to connect to the internet, if that fails you may want to unplug your modem or reset your router (or both) whichever applies because the dhcp may not be being distributed correctly.  If the dhcp server has reached it's max capacity for ips and it has ips tied to dead mac addresses it may not be distributing new ones.  I have had this problem myself when i got a new router and it baffeled me until my roomate finally unplugged the modem and plugged it back in.

---

### Post by Trebuchet on 2007-02-04
> **Hranj said:**
> the ethernet plug im trying to use is right on the mobo. no usb involved here.

my connection goes from my modem to my router and then to my computer.

idk why it would be coming up as a firewire since its right on the board. 

ive tried switching out the cables. had no effect whatsoever. 

i think something else is at work here because there is all kinds of hell going on now. there is no more welcome screen when i log out. i tried to change it back but it says the NetWare has changed it because its "faster". says to uninstall it but cant. does anyone have any idea what the hell is going on. dads yelling at me cause i cant figure it out, but i have no idea what is going on. 

this is supposed to be a no bashing forums but

WINDOWS SUCKS!!!!When you replaced the mobo and CPU, did you also reinstall Windows? The hard drive stores data about your mobo, and with a new mobo Windows may be looking in the wrong places for data. Obviously you're having other problems, and my suspicion here is you need to do a Repair on your Windows installation. Please tell me you have a real Windows disc and not one of those damned vendor "restore" discs?

Any computer OS sucks when it's not working.

---

### Post by FuturePilot on 2007-02-04
Maybe try rebooting the modem. Just unplug the power for a minuet or two. I had a similar problem when I tried to temporarily hook up my laptop to out existing line. The modem knows what it's connected to so it saw my laptop as a different computer and wouldn't let me connect. I simply disconnected the power and then it let me connect. Chances are with the new motherboard and it's seeing it as a different computer.

---

