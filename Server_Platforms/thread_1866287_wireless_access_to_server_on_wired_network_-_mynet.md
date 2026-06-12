---
title: "wireless access to server on wired network - mynet"
date: 2011-10-21
forum: Server Platforms
---

### Post by pzaw on 2011-10-21
hi
 
I have a network at home. Please see the picture with all relevent info.
 
[IMG]http://i54.tinypic.com/19wcwx.jpg[/IMG]
 
I want to access the server (lucid) from the red machine. 
I don't know if this is correct but I have assigned the same workgroup=Mynet for the red computer as the green computers although the networks are different one is 10.2.0.0 and the other is 10.1.1.0.
 
First, is this possible? ie. access samba from the red computer.
second, how do I setup the smb.conf file to do this on the red machine .
What needs to be changed on the samb.conf on the server if any?
 
Thanks,
Pzaw

---

### Post by newbie-user on 2011-10-21
Assuming your samba server is set up correctly, you could access the samba server by mounting a share onto your 11.04 machine.  I like to make an icon on my desktop that links to smb://[your smb server]/[share folder]/[share]

---

### Post by volkswagner on 2011-10-21
I believe you will need some complicated [static route]("http://www.dd-wrt.com/wiki/index.php/Linking_Subnets_with_Static_Routes") setup.

I think you may have more joy setting up a separate wireless access point and hang it off your switch.  Most any wireless router can double as an access point if you don't use the wan port.

---

### Post by pzaw on 2011-10-31
hi,

Thanks for replying.
All internet/squid and samba shares work on the network except for the red machine.
I have renamed the workgroup to "test" on the red machine.

when the firewall is down the red can see the Samba shares so I am thinking it is just the firewall.

I use Shorewall firewall to make life easier.
I am not sure about the correct syntax to limit the access to samba from the net.

will this do the trick?

SMB(ACCESS)    net    loc    10.1.1.3

any help would be appreciated.

regards
Pzaw

---

