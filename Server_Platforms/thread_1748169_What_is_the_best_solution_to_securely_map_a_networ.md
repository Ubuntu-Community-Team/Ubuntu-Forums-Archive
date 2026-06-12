---
title: "What is the best solution to securely map a network drive over internet?"
date: 2011-05-03
forum: Server Platforms
---

### Post by gunnarflax on 2011-05-03
Hi! I'm trying to set up a remote desktop setup for one of my clients but the problem is that the program they are using is for Windows. In their office network they have a Ubuntu file server and Windows clients with mapped network shares (samba) which is how their program access the files.

My first thought was that I should install their Windows program on the server through Wine and let them connect to it through a FreeNX server and NoMachine's NX-viewer. Unfortunately I've had no progress at all in getting the program to work in Ubuntu so I thought I might try with the same approach as their office clients are using (Unless anyone can help me getting the program to work with wine).

So I want to map their network share over the internet to a Windows client but I also want it to be encrypted and safe. My first thought was to go with SSH and SFTP. That way it would be encrypted. Though that won't work since Windows can't handle network drives through sftp, only ftp. But FTP is completely unprotected!

What do you propose is the best solution for this problem?

---

### Post by kgatan on 2011-05-03
You can setup a VPN server on the Ubuntu file server. That way you can connect with a windows machine and the samba shares.

---

### Post by gunnarflax on 2011-05-03
I've never worked with VPN's before, is there any good tutorial you can recommend for me?

---

### Post by kgatan on 2011-05-03
To be honest i have never set it up in Linux myself, only used it on windows servers.
Search google for OpenVPN, there are tons of information out there.

---

### Post by gunnarflax on 2011-05-03
Ok thanks, I will look into it!

---

### Post by stmiller on 2011-05-03
openvpn is a nightmare, IMO.

Another option for a vpn is pptp. Basically set a few options in the config file, and save.

[http://www.howtogeek.com/51237/setting-up-a-vpn-pptp-server-on-debian/](http://www.howtogeek.com/51237/setting-up-a-vpn-pptp-server-on-debian/)

---

### Post by gunnarflax on 2011-05-04
Thanks! That sounds like a great alternative, but I read on the tutorial that it isn't as secure as VPN. Why is that?

---

### Post by Lars Noodén on 2011-05-06
> **gunnarflax said:**
>  My first thought was to go with SSH and SFTP. That way it would be encrypted. Though that won't work since Windows can't handle network drives through sftp, only ftp. But FTP is completely unprotected!


It looks like there might be Windows clients for SSHFS: Dokan and WinFUSE + ExpanDrive, that would let you use SFTP.

---

### Post by spynappels on 2011-05-06
Actually, OpenVPN works very well and is secure. There are lots of examples of how to get it set up, but I'd look for a routed setup as you can still use the LAN IP address when mapping the drive. This way, the share would work whether it is connected to the LAN directly or through the VPN when working remotely.

The OpenVPN how-tos on the OpenVPN website are great, you can also search in the Security forum and here for OpenVPN, there are loads of threads on how to set it up.

---

### Post by gunnarflax on 2011-05-06
Thanks Spynappels, I will look into it!

---

### Post by spynappels on 2011-05-06
If you have some specific questions once you have done your research, come back and ask them in this thread and I'll do my best to help you, I have set up quite a few routed (and a few bridged) OpenVPN installations.

---

### Post by gunnarflax on 2011-05-09
I tried first with OpenVPN but it all got messed up and the internet connection stopped working. It was very complicated to set up, at least for me. So I tried with PPTP and it worked without any troubleshooting what so ever so I guess I will stick with it until I fully understand how OpenVPN works. Thank you so much for all the help!

---

### Post by Sven6210 on 2011-05-10
Well, I installed a VPN on a virtual machine and use it for surfing the internet (I am in a country where the internet is filtered by the government). I admit, I also struggled setting up OpenVPN but once I succeeded it worked perfectly.

I prefer OpenVPN compared to PPTP as it allows to route traffic through port 443 which is also used for SSL connections. So any authority analysing the web trafic can actually not really see the difference between the VPN tunnel and a SSL encrypted website.

Instead of creating CA certificates, user certificates and keys for the encryption with the command line I hardly recommend to use "tinyca", a small tool allowing to create the relevant certificates rather easily and without typing too much. I still do not understand why most of the tutorials do not recommend "tinyca".

If you are happy with PPTP please keep on using it. It also supports Apple products like ipad, iphone etc. but it is also easier to be blocked by authorities censoring the internet.

---

### Post by gunnarflax on 2011-05-10
When I learn how to get it working correctly I will go for OpenVPN instead, I just didn't have the time right now to learn all that was required.

---

### Post by spynappels on 2011-05-10
> **gunnarflax said:**
> When I learn how to get it working correctly I will go for OpenVPN instead, I just didn't have the time right now to learn all that was required.

Do you have a test system you can experiment with, and do you have time to play with it? If you are having specific problems, I'd be happy to help.

---

### Post by gunnarflax on 2011-05-10
That'd be much appreciated :) I will set up a virtual machine to experiment with as soon as I get time!

---

