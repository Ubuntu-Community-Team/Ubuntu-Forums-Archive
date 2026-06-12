---
title: "Ubuntu Server 10.04 / Mac OS X 10.5"
date: 2010-08-13
forum: Server Platforms
---

### Post by ShadowcatX on 2010-08-13
On a Windows Network, I've set up a Samba Ubuntu Server for several macs to use as storage space. I'm currently running 4 hard drives as a RAID 5 on the Server. On the RAID I have created a shared folder and set it to allow guest access. 

From the server I can find the macs just fine. I can find the pcs just fine. I can retrieve files from the pc server. 

However, from the macs I can find the Ubuntu server, and I can find the shared folder (by logging on as guest). However, any time I attempt to access that folder, I get an error message. The name of the folder is sharedcomm. 

"The operation cannot be completed because the original item for "sharedcomm" cannot be found." 

I have been banging my head against a wall on this for a day, I thought it was all set up and I was excited then this happened and I haven't been able to get past it. 

I tried everything I could think of, I've googled the error message but its hard to sort through replies that are to similar but different problems from several years ago to get any helpful information. I'm new to these forums so I apologize if I haven't observed all the proper protocols. 

One other thing I've come across in trying to trouble shoot this problem bothers me. The server is running a static IP address. However Netstat, when it lists all my listening devices and ports shows my IP address under UDP rather than TCP. I can't believe that is the source of my problem but its an oddity that I can't be sure is not the source of my problem.

I posted this in the apple forum yesterday, I'm not sure what the rules are for posting in more than one forum, I didn't see the server forum then so I apologize if this is against the rules.

---

