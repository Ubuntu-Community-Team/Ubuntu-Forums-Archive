---
title: "LAN party need networking help"
date: 2008-07-18
forum: Windows
---

### Post by nerdman978 on 2008-07-18
Hello,

Tomorrow I am hosting a LAN party with 5 friends. I bought a nice Netgear 8 port 10/100 ethernet switch to hook all the computers up and play video games nicely. Then I came to the sudden realization that some computers will be using Vista, some XP. In the past I occasionally had networking issues between Vista and XP, so I figured when one of my friends came over tonight (Vista on his laptop), we could play Call of Duty 2 to see if everything was hunky dory. It hasn't been so far. I can create a multiplayer LAN game (we are connected with the switch I bought) and can join it myself without a hitch. He, however cannot see the game in his menu and everything is connected (after multiple checks to make sure). 

Are there settings I need to check on all the XP and Vista computers to ensure that everything networks properly? The other games we will be playing tomorrow are Battlefield 2 and Battlefield 1942. We may play Warcraft 3 on LAN.

Thanks in advance, you guys have always been helpful with even the most random issues (including the non-Linux related ones).

---

### Post by drubin on 2008-07-18
Just make sure that each of the network cards are set to DHCP.  (or at least make sure that the ip's of each machine are unique).

Haven't really had an issue networking with Vista and XP(PRO) the XP(home) edition is rather lacking in the networking dept. Still not 100% sure what the differnces are but I always had some issues with home.

Sorry I can't be of more advice is is rather late..

---

### Post by nerdman978 on 2008-07-18
I just realized my computer's wired connection was set to manual IP configuration...so testing that now.

wow I can't believe I didn't see that it worked masterfully. I appreciate it much greatly lawl

---

### Post by drubin on 2008-07-18
If you need a "static" local ip address use your router most of then now support assigning ip via mac address. -Just my thought

---

### Post by D-EJ915 on 2008-07-19
make sure you use the same subnet

---

### Post by gletob on 2008-07-19
When i was on the dark side I used a program called network magic that made my pcs talk and play nice

---

### Post by p_quarles on 2008-07-19
Moved to Windows Discussions.

---

### Post by sixblades on 2008-07-21
The only differences in networking between OSs is how to set up IP addresses and handle hardware, in essence the configuration aspect. It doesn't matter if you're using Vista, XP, or even Linux (via wine) to network a game, if the PCs are set up correctly (IE have the right ports open & using the same networking protocol) then they're all "equal" in the eyes of the network, regardless of the OS.

---

### Post by rickyjones on 2008-07-22
1. If this is just a switch then it might be easier to assign static IPs to all systems. 
2. Disable any and all firewalls on the computers.
3. Have fun.

-Richard

---

### Post by Nessa on 2008-07-23
^He's right. A switch does not give out IP addresses. You have to have static ip addresses on all devices connected to it.

---

