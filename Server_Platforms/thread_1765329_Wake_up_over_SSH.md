---
title: "Wake up over SSH"
date: 2011-05-23
forum: Server Platforms
---

### Post by grants on 2011-05-23
My question is how can I put my computer to sleep and be able to wake it up remotely?

I have VPN access to my firewall so I can get a LAN IP, I also have port forwarding set up for ssh and Samba. 

I don't really need my computer on all the time so I'm hoping I can save some energy by putting it to sleep if there are no process running or no one logged in. In the event I need remote file access to my Samba server have the ability to wake it back up.

Any thoughts?

---

### Post by papibe on 2011-05-23
Almost all modern motherboards supports the [Wake On LAN]("http://en.wikipedia.org/wiki/Wake_on_lan") standard.

Check out this [help]("https://help.ubuntu.com/community/WakeOnLan") page, and this helpful [thread]("http://ubuntuforums.org/showthread.php?t=360901&highlight=wakeonlan").

I would start testing if you can wake your computer from your LAN before trying it out over the internet.

I hope it helps.

---

### Post by Lars Noodén on 2011-05-23
For Wake on LAN to function, you'll need to have another computer on the same LAN already awake from which to send the WOL signal.

---

### Post by grants on 2011-05-23
So if I wanted to do wake on lan I would need to VPN in to my router then use a command line tool to broadcast the wake up signal?

---

### Post by Lars Noodén on 2011-05-23
> **grants said:**
> So if I wanted to do wake on lan I would need to VPN in to my router then use a command line tool to broadcast the wake up signal?

No VPN is needed.  SSH will give you the shell access you need to run the program that does Wake-On-LAN for you.  But yes, the broadcast does need to come from inside the same LAN as the machine to be woken up.

---

### Post by grants on 2011-05-23
How would I have ssh access if the host is off? does a ssh authentication request do the wake on line with a command line switch?

---

### Post by Lars Noodén on 2011-05-23
For Wake-on-LAN to function, the magic packet must be sent from another machine on the same LAN.  If there is not a machine available, then WOL cannot be used.  You have to have a platform to launch it from.

---

### Post by papibe on 2011-05-23
To clarify some things..

The Wake-On-LAN standard works in a MUCH lower level. When the machine is off, you don't have SSH server running, neither the OS! When you managed to set up correctly both the machine you want to wake up and the client that sends the WOL package, you'll be able to turn on the first machine. After a few seconds, you can SSH to it.

WOL was designed to work on a LAN, however it can be use over the Internet. I actually use it both ways. Again, I strongly recommend to first make sure it is working on your LAN, that is, sending the WOL package from another computer in the same LAN that the sleeping/off machine.

In order to wake up a comp from the Internet, you need a router that can pass the package. It is VERY hard to know if yours does, since it's not a common operation. It probable won't be in the manual (unless you have DD-WRT for example).

Anyway, the steps to configure your router are similar to any service that you port forward to your machine. Usually the port required to forward is 9.

Here is a very useful [tutorial]("http://www.dd-wrt.com/wiki/index.php/WOL") for DD-WRT (open software for routers). 

I hope this helps a little bit more,
Regards.

---

### Post by Lars Noodén on 2011-05-23
> **papibe said:**
> 
In order to wake up a comp from the Internet, you need a router that can pass the package. It is VERY hard to know if yours does, since it's not a common operation. It probable won't be in the manual (unless you have DD-WRT for example).

[s]Can you point to the DD-WRT documentation for passing such a packet? [/s] I'd like to see about trying this.

Edit: Found it.

---

### Post by volkswagner on 2011-05-23
[Dsl reports]("http://www.dslreports.com/wakeup") has a nice utility to send WOL over internet.  As mentioned, verify the machine can wake locally before even venturing outside LAN.  The nice thing about DSLreports utility, it sends packet via internet even if you're inside your LAN.... great for testing!

WOL, can be limited on some MOBO's to wake from S3 (standby), while others are happy to wake from fully off.  From my personal experience System builders Like DELL, HP, etc. are more likely to be limited to wake from standby only.

Standby on a server is a whole ball of wax on it's own (power management).

---

