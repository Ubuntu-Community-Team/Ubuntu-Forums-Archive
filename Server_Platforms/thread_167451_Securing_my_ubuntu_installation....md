---
title: "Securing my ubuntu installation..."
date: 2006-04-28
forum: Server Platforms
---

### Post by sefs on 2006-04-28
Hi there.  I am a new convert from Windows to Ubuntu.  But I ran into a problem that gave me a scare and need some help in proper configuration.

Here are my three (3) questions


Question 1
----------
how do i configure firestarter to disallow all incoming traffic from a specific IP address.


Question 2
----------
Background: I am providing the following services on my machine:

VNC
FTP
SSH
Media Streaming
HTTP
Samba (SMB) -- for the internal LAN

Initally my Firestarter Configuration was:

* INBOUND TRAFFIC POLICY *
Allow connections from host 
192.168.0.0/24
255.255.255.255/24 <-- I put this in assuming that I needed this to connect from any machine i am at outside my LAN

Allow Service (xxx is my place holder for the port I have set)
VNC         xxx  everyone
FTP         xxx  everyone
SSH         xxx  everyone
HTTP        xxx  everyone
M.Stream    xxx  everyone
Samba (SMB) xxx 192.168.0.0/24

My understanding of the above was that this would allow all machines on the lan to connect as well as anyone on the internet, but since the Samba service has "for" set to lan clients only that no one but lan clients would be able to connect there.

I found that this was not the case when I open up firestarter and saw someone connect to the smb share.  I quickly removed the 255.255.255.255/24 policy from "Allow connections from host" and then the events page showed that the person was now being blocked by firestarte.

To properly configure firestarter so that I can share all services EXCEPT samba with the internet what are the polices I should set up.  I only wish to share the samba service with machines on the lan.


Question 3
----------
Since that scare I have installed snort-mysql following the HOWTO here on the forums. I know that it starts at boot and all that.  When I run it in terminal mode. I can see visually the traffice wizzing by and I could see the attacks of the person trying to access the Samba service.  However When I go to Base, I see nothing in this application. There are no logs or alerts ect. as if nothing is being written to the database. Can anyone tell me what I should do here.  I tried running a port scan with NMap, and running nessus but not a peep in Base.  Let me know what I am doing incorrectly.

Thanks.

---

