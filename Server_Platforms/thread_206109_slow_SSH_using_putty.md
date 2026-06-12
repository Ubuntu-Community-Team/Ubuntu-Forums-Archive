---
title: "slow SSH using putty"
date: 2006-06-29
forum: Server Platforms
---

### Post by daageep on 2006-06-29
Hi everyone.

I'm fairly new to SSH servers and would like some help. I am running my old Pentium IBM laptop using SSH on my home network with port 22 open and pointing to the IBM. On the other side of my house, I have a windows machine using putty trying to SSH into the machine. If I use the local address assigned by the router (192.168.0.X), the connection is really fast. 

I also have my router setup such that it updates my IP address to a redirecting service (dyndns.org). The problem is when I use putty to connect to the dns address (which directs to my IBM's IP): it's REALLY, REALLY slow. After I log in, entering commands and getting output lag really badly. 

I also tried connecting directly to the IP address, same issue. Here's the other problem: both putty and ssh (on a linux machine also on the network) complain about keys not matching and possible security issues. SSH complains that there might be a man in the middle attack. :roll: I checked my router and no outsider is connected.

In summary, here are my questions:
1) why is it so slow? 
2) why do i have those warning messages? are they really security threats?
3) i just want to control my ibm laptop remotely (when I'm on campus). is there a better solution?

thanks everyone

---

### Post by houstonbofh on 2006-06-30
What is the IBM?  There is some computational load, so if it is real old...

---

### Post by MJN on 2006-06-30
[quote=daageep]1) why is it so slow?[/quote]
 
Firstly, the encryption overhead for SSH obviously exists but it's not significant to cause a problem. Besides which, you have confirmed your IBM has got enough oomph given that when you connect directly to it's private address it runs fine.
 
Putting DNS aside (it's a red herring - it's only relevant when you first connect and it translates the domain name to your public IP address - after that it's just like you've typed the public IP manually) the only difference between you connecting to your IBM via it's LAN IP address and the public WAN IP address (of the router) is that the latter sends everything via your routers **NAT** function.
 
Hence, the likely cause is your router - what is it? Perhaps other owners can comment on how their's performs.
 
[quote=daageep]2) why do i have those warning messages? are they really security threats?[/quote]
 
When you connect directly to your IBM's LAN address the server signature is stored by Putty and associated with that address. However, when you then connect to the IBM via the WAN address of the router Putty spots that a **different** machine is now using the same server signature hence why it throws up a warning that somebody could be trying to spoof your IBM hence the 'man in the middle' caution. Of course, you know it's the same machine so nothing to worry about (in this instance).
 
[quote=daageep]3) i just want to control my ibm laptop remotely (when I'm on campus). is there a better solution?[/quote]
 
Your solution is the correct one, it just sounds like your router is either not up to the job (domestic 'routers' can be a mixed bag - I've never used one that doesn't have its own quirks and faults) or is misconfigured (although I can't imagine what you could tweak here - these things are usually not that configurable).
 
Post your router model and see if anyone else has one.
 
Also, try forwarding port 7 for ping's from your router to your IBM - if it'll let you - ping uses ICMP packets which use neither TCP or UDP, the usualy transport protocols that domestic port forwarders are usually geared up for. Then ping the IBM via it's LAN address and the router's WAN address. Do you see any difference in round-trip times? Also try with **ping -s 1024** to send larger packets to the IBM - it may be that your router is degrading the performance by fragmenting the packets.
 
Mathew

---

### Post by daageep on 2006-07-01
Thanks for the quick replies everyone. The replies made a lot of things more clear. :D 

My router is a Netgear MR814v2. My IBM is an old Pentium laptop with 266mhz of awesome power =) and 128mb ram. It is connected to the router through a cat5 cable.

Also, the wifi connection at my university is not that secure. When I'm associated, I need to open up firefox and enter my school id and password at their login page. The login process is encrypted with SSL (i hope that's what it is). Anything beyond the login process is not.

If I connect to my SSH server at home through the wireless using openSSH/putty, can the information sending back and forth be seen or sniffed? I guess more specifically, I was running Centericq (text based AIM/icq client) through the SSH connection. Is that relatively secure? If so, is everything through the SSH client secure?

How about X11 forwarding through SSH?

edit: if anyone is willing, will someone suggest how to securely surf the web at home with a wireless router more secure? i don't mean like WEP/WPA for router protection but protection for the computers surfing the web etc. I read "ssh tunneling", "vpn", and some other techniques might help. will someone point me to the right direction? thanks

---

