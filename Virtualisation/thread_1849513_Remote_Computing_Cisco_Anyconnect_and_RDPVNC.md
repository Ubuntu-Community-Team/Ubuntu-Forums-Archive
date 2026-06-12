---
title: "Remote Computing: Cisco Anyconnect and RDP/VNC"
date: 2011-09-24
forum: Virtualisation
---

### Post by luciusthecanine on 2011-09-24
Situation: I'm a Linux Noob.

I'm using Cisco Anyconnect VPN tunnel to pass through a Cisco 5000 series Router and remote into my workstation @ the office.

I'm using a dual-boot Vista/Ubuntu 11.04 (Natty) laptop.

In Vista:
 I fire up the Cisco Anyconnect vpn tunnel program, connect to the IP of the VPN server (Cisco 8000 series Router at the Office), log in, and use the built-in Windows RDP program to connect to my office workstation's IP address.
This process works flawlessly.

In Natty:
I do the same thing, the Anyconnect VPN tunnel connects and accepts my login.
When I try to use any RDP app and point it at my workstation's IP, the RDP program fails the connection or times out.
I've tried adding username/password to the RDP programs that accept that info, still no luck.

I also tried installing tightvnc server on the office workstation and pointing several vnc viewers from Nattty at the correct IP and Port (expressed as  ip.address.of.workstation:port)...and just at the IP to no avail. I haven't yet tried to use the tightVNC viewer in Vista or Natty, I downloaded it but can't figure out how to compile/build it in Natty - I'm a Terminal Noob and haven't had time to google that process.

I've tried a good number of RDP and VNC apps on Natty with no luck.
At one point I saw an error that the IP address of my office workstation was not found at all... indicating that the Anyconnect VPN tunnel program is not doing it's job in Natty (making the remote IP network available for my Laptop to access).

I'll add more specifics about what specific apps I'm using (incl. Screenshots and the output of ifconfig... which may tell me that I actually have no VPN connections active since the Office Workstation IP was not found...) when I'm in front of the laptop later... but does anybody have an idea about what I'm doing wrong?

Thanks for putting your eyes on this post.

---

### Post by luciusthecanine on 2011-09-25
Found the answer...

Cisco's website says the Anyconnect client will not validate connections from Ubuntu unless it's 9.x or 10.x.

I guess I'm marking this as "Solved".

Thanks for reading this over!

---

