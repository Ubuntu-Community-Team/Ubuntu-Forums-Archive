---
title: "Samba"
date: 2011-01-05
forum: Server Platforms
---

### Post by Captainnow on 2011-01-05
I have my samba setup and working. I have 2 computers all on the same router as my server. The two windows 7 computer can map the drives and access the shared folder those the networking option of windows 7.

My issue or question is this.
Does samba work to map network drives to computer outside of my router? 

For Example - I was remoted in to my mom's PC through logmein.She lives about a 3 hour drive away from me. When I try to map a network drive it will prompt for the log on for the drive and then just kick the log in back up. I tried a few times to make sure I wasn't making any typing errors. 

I have ports 137, 138, 139, 445 open on my router for both TCP and UDP.

Can samba work to map the drives if outside of my router? And if so what would make it work with them behind the router, but then not work outside the router?

Thank You for any and all information you can give me.

---

### Post by karlson on 2011-01-05
> **Captainnow said:**
> 
I have ports 137, 138, 139, 445 open on my router for both TCP and UDP.

Can samba work to map the drives if outside of my router? And if so what would make it work with them behind the router, but then not work outside the router?

Thank You for any and all information you can give me.

I am assuming you are sitting behind the router that does NAT and have a single outside IP address.

So one thing that you will need to do with the ports you have listed above is port forward them to the server that runs samba.

You can look at:

[http://ubuntuforums.org/showthread.php?t=1360250](http://ubuntuforums.org/showthread.php?t=1360250)

---

### Post by Captainnow on 2011-01-05
Yes. I have it forwarding to the internal IP address of my server.
I also have FTP, and SSH setup and they work outside of my router.

---

### Post by Captainnow on 2011-01-06
Anyone know more on how to get Samba to work outside of my router?

I would like to get this to work so I can map a drive to my mom's windows 7 computer so she has more space available to save some of her files since her laptop doesn't have a huge hard drive.

This should be possible shouldn't it?

---

### Post by HermanAB on 2011-01-07
Howdy,

Don't open Samba to the internet.  It is not secure.  You will regret it pretty soon.

You can run Samba over SSH by tunneling port 445 though.  You don't need to forward the other ports.  

However, the best way is with a SSL VPN, which can also be done with a new version of SSH.

---

### Post by Captainnow on 2011-01-07
> **HermanAB said:**
> Howdy,

Don't open Samba to the internet.  It is not secure.  You will regret it pretty soon.

You can run Samba over SSH by tunneling port 445 though.  You don't need to forward the other ports.  

However, the best way is with a SSL VPN, which can also be done with a new version of SSH.

Do you know where I can find information on how to set those up for my server to work that way and what I'd need to do on a windows 7 machine to make it work? Thanks.

---

