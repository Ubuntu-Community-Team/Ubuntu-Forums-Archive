---
title: "Windows suddenly stopped detecting Ubuntu server"
date: 2014-04-01
forum: Server Platforms
---

### Post by gabriel14 on 2014-04-01
So I configured some weeks ago my 12.04Lt server with Samba client and everything was running fine, I could connect to the server from any device within the home network (Win8 pc, Android phone and tablet, win7 pc).
I didn't try to get into the server shared folder for the last 3 days and last night I installed AVG Internet Security 2014. 
So today I was going to copy some files that I downloaded with TransmissionBT into the server to my Windows 8 pc and I got stuck with some Windows message that told me Windows couldn't reach any machine or device with that name and that it could be some network problem, so I selected the "Diagnose" button and waited, but windows couldn't find any trouble and said that it couln't reach any machine with that name (again). 
I started looking for solutions online but I couldn't find anything like that. I didn't thought it was the new Antivirus though because Windows Defender didn't gave me that trouble.

So I started thinking about the programs I installed recently that could change the network configuration and realized it could be the AVG. 
The solution was to enter in Options>Firewall Settings...>Expert Mode>Defined Networks, then choose the "IP addresses whitelist" and "Add Network", type in the IP address of the server, mask (255.255.255.0) and save.
Now I can see the server again. Since I didn't saw any post from this problem, I hope this can help someone.

PD: I speak spanish, sorry for my bad english.

---

