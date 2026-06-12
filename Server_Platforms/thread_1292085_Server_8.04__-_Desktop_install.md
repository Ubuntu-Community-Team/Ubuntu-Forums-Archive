---
title: "Server 8.04  - Desktop install"
date: 2009-10-15
forum: Server Platforms
---

### Post by Go_WoW on 2009-10-15
Hi,

I just installed Ubuntu 8.04 server i386.
To my knowledge it only installed the command line, and not the desktop, right?

So, I'm trying to install the desktop using "sudo apt-get update", right so far?

But when I do this I get "Could not resolve 'security.ubuntu.com'".  Why?

I can ping my window workstation, so I know the network is working.
I believe there is something wrong with my DNS, right?

When I do a cat /etc/network/interfaces, everything looks right except dns-nameserver is 192.168.1.1 which is my linksys router.

Any ideas?

Is there a good book for Ubuntu server 101?

Thanks for your help,

---

### Post by Sarmacid on 2009-10-15
You're right about it being a DNS problem. What you can do for now is adding the nameservers manually. Check your windows machine and put the servers in the /etc/resolv.conf file. After you get the ubuntu desktop I'm guessing the network manager will take care of adding the nameservers automatically.

---

### Post by prshah on 2009-10-15
> **Go_WoW said:**
> 
But when I do this I get "Could not resolve 'security.ubuntu.com'".  Why?

When I do a cat /etc/network/interfaces, everything looks right except dns-nameserver is 192.168.1.1 which is my linksys router.


The actual DNS server will be mentioned in /etc/resolv.conf.

Usually, the router acts as a DNS server, in most setups; it picks up the correct DNS address when negotiating a WAN/PPP connection. So a DNS setting that points to your linksys router is probably correct.

If you feel that it is a DNS problem, you can manually change the DNS servers in /etc/resolv.conf. You can do this by either editing the resolv.conf file directly or for a more permanent solution [see this]("http://ubuntuforums.org/showpost.php?p=6942058&postcount=3") (Includes OpenDNS server details).

What kind of Internet connection are you using? Does it require a dial up access (Eg, PPPoE broadband username/password)? Or do you just turn it on, wait a while and you are automatically connected?

There's plenty of documentation suitable for setting up various kinds of servers; you can start with the [Community Documentation]("https://help.ubuntu.com/community/Servers")

---

### Post by Go_WoW on 2009-10-16
Hurray!  This worked.  Now I am going to install the desktop using "sudo apt-get install ubuntu-desktop".  Why does Ubuntu not come with GUI interface to manage?  Thanks and appreciate your help!

---

### Post by epsolon77 on 2009-10-16
> **Go_WoW said:**
> Hurray!  This worked.  Now I am going to install the desktop using "sudo apt-get install ubuntu-desktop".  Why does Ubuntu not come with GUI interface to manage?  Thanks and appreciate your help!
Ubuntu does come with Gnome for a GUI (Graphical User Interface)
Ubuntu SERVER does not come with a GUI to keep the system resources used down, thus allowing more use out of the hardware (less resources spent making it look pretty, more spent making it work pretty).

---

### Post by Carl Hamlin on 2009-10-16
> **Go_WoW said:**
> So, I'm trying to install the desktop using "sudo apt-get update", right so far?

I'd recommend against it, actually. Desktop environments on servers degrade the performance of the server.

---

