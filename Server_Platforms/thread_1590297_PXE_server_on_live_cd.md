---
title: "PXE server on live cd"
date: 2010-10-07
forum: Server Platforms
---

### Post by Z.K. on 2010-10-07
I was wondering if anyone knows of any PXE server that is on a live CD and it does not have to be Ubuntu.  I have tried and tried to get a PXE server working, but have been unable to do so.  I managed to get the dhcp server working and I can see the ip address is assigned to the client, but the menu never comes up.

The only way I was able to get a pxe server to work was to use tftp32 in windows.  That one works okay though I have yet to figure out how to modify it so I can do multiple distributions.  Still, I would prefer to use a Linux solution, but I have not had much success yet.

I have tried all the tutorials that I could find, but still I cannot get it to work.  Maybe I need to install the exact distribution and version for the tutorial, but I did not want to mess up my current server that I have running.  I guess I could buy another hard drive and try it that way.

:confused:

---

### Post by lykwydchykyn on 2010-10-07
Knoppix used to have a pxe server built in, you just had to activate it.  I don't know what's up with Knoppix these days, though.

I've set up several PXE boot servers using Debian and Ubuntu.  Sounds like you're having trouble with tftpd configuration.

---

### Post by druhboruch on 2010-10-07
[http://www.livedistro.org/gnu/linux/voyage-linux-live-cd-03](http://www.livedistro.org/gnu/linux/voyage-linux-live-cd-03)

I never tried it myself and it is quite old. 

May I ask why do you need it to be live-cd?  You could play with your setup on virtual machine until you get it right.

---

### Post by Z.K. on 2010-10-10
> **druhboruch said:**
> [http://www.livedistro.org/gnu/linux/voyage-linux-live-cd-03](http://www.livedistro.org/gnu/linux/voyage-linux-live-cd-03)

I never tried it myself and it is quite old. 

May I ask why do you need it to be live-cd?  You could play with your setup on virtual machine until you get it right.

Because I can't get the tftp server to work.  I have tried multiple times and it would be great if there was something I could just use.  I am not on a domain.  It is a private network hooked to a router.  I managed to get the dhcp server working, but I can't seem to get the tftp server working.  After a ip address is assigned to the client, it just sits there forever.

As far as using a virtual machine I am not exactly sure what you mean.  Are you referring to virtualbox?  If so I would think I would have the same problems I am having now.

:confused:

---

### Post by Z.K. on 2010-10-10
> **lykwydchykyn said:**
> Knoppix used to have a pxe server built in, you just had to activate it.  I don't know what's up with Knoppix these days, though.

I've set up several PXE boot servers using Debian and Ubuntu.  Sounds like you're having trouble with tftpd configuration.

Yes, I think so.  I have tried several tutorials in how they configure the tftp server, but nothing seems to work.  I will try again, but I am not too hopeful.

:confused:

---

### Post by lykwydchykyn on 2010-10-10
What OS is running on your server?  If it's Debian or Ubuntu I'm sure we could walk you through setting this up and troubleshooting any errors.

---

### Post by druhboruch on 2010-10-11
> **Z.K. said:**
> 
As far as using a virtual machine I am not exactly sure what you mean.  Are you referring to virtualbox?  If so I would think I would have the same problems I am having now.

:confused:

Well, If you setup your tftp server on VM it will be easy for you to save the state of your work and if necessary rollback quickly.
It saved me a lot of time.

If you send us the links to the guides you tried, it would be much easier to find a solution.

With TFTP the hardest thing is to setup DHCP server.  Therefore I would suggest to use a distro (like IPCop or PFSense) with DHCP server configured via web.

I am not runnig it since Karmic, but if I remember correctly with TFTP there was not much to configure...

[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)
Here is the full howto:
[https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

---

### Post by vikjon0 on 2010-10-25
> . It is a private network hooked to a router
And this router does not have a working dhcp running? You need to disable it or use a dhcpproxy instead of the standard ubuntu dhcp.

---

