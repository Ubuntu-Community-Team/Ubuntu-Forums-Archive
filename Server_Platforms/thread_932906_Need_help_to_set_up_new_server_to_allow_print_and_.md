---
title: "Need help to set up new server to allow print and file sharing"
date: 2008-09-28
forum: Server Platforms
---

### Post by k3lt01 on 2008-09-28
Hi

I have finally got time to setup my SOHO server and have already installed Ubuntu 8.04 Server with LAMP, SSH, Cups and Samba. I have been reading the Ubutu Wiki and Ubuntu Server documentation etc pages and find them to be as clear as mud (especially when they say they don't contain everything and suggest ou check out other pages which are even less understandable, lol).

So here is what I want to do.
1. Finish setting up my server to be the print server for 4 other machines (2 Ubuntu Hardy Heron, 1 Windows XP, 1 Windows Vista).
2. Finish setting up so each machine can not only see the server but can also access their own /home directory.

Regarding Samba, I have read there is a program called SWAT which is a GUI for smb.conf but I am unable to get it onto my server via the repositories.

About the server, the server name is my name and I want the permissions to be setup as my family members names so when they access the server they access their own /home folders, is this possible?

If there is an easy way to cli through this I would be grateful, I also woulnd't say no to a GUI that culd do it either. I'm thinking Webmin but I need to read up on it.

Thanks in advance

---

### Post by lykwydchykyn on 2008-09-28
Webmin is great, I highly recommend it.  Configuring samba shares is quite easy with it.  

When it comes to printing, I strongly recommend skipping Samba and just using IPP to share printers.  Windows 2k/XP/Vista handle this just fine, and you don't have headaches over passwords and things.

---

### Post by k3lt01 on 2008-09-29
> **lykwydchykyn said:**
> When it comes to printing, I strongly recommend skipping Samba and just using IPP to share printers.Is IPP in the Repos?

---

### Post by cariboo on 2008-09-29
Download this [guide]("http://ww.samba.org/samba/docs/Samba3-ByExample.pdf") it gives example of setups for everything from a small office to a large organization. It walks you through everything you are looking for.

Jim

---

### Post by lykwydchykyn on 2008-09-29
> **k3lt01 said:**
> Is IPP in the Repos?

IPP is the print sharing protocol that is built in to CUPS.

---

### Post by phillik747 on 2008-09-29
> **cariboo907 said:**
> Download this [guide]("http://ww.samba.org/samba/docs/Samba3-ByExample.pdf") it gives example of setups for everything from a small office to a large organization. It walks you through everything you are looking for.

Jim

Error in link, forgot 3 w's

[http://www.samba.org/samba/docs/Samba3-ByExample.pdf]("http://www.samba.org/samba/docs/Samba3-ByExample.pdf")

---

### Post by k3lt01 on 2008-09-29
Ok, if IPP is easier than a full SAMBA setup, how do I set IPP to work?

That PDF is good except for the fact you have to get through about 30 pages before you actually get anything. I'll have a better look at it tonight.

---

### Post by lykwydchykyn on 2008-09-29
> **k3lt01 said:**
> Ok, if IPP is easier than a full SAMBA setup, how do I set IPP to work?


Well, first point your web browser to the server at port 631 ([http://your_servers_ip:631](http://your_servers_ip:631)).  This gets you to the CUPS web interface.  click over to the administration tab and check the boxes "Share published printers connected to this system" and "Allow printing from the Internet".  Then click "change settings".

BAM!  IPP is set up.  Now you just have to configure your clients.

If they're Linux clients, you just navigate the the same interface on the clients ([http://localhost:631](http://localhost:631)) and check that first box ("Show printers shared by other systems") and wait about 30 seconds.  Your shared printers should show up automagically.

If they're windows clients, you crank up the add printer wizard and do this:
 - Select Network printer
 - Select "Connect to a printer on the Internet... (etc)"
 - Put in a URL like this: [http://your_servers_IP:631/printers/name_of_printer](http://your_servers_IP:631/printers/name_of_printer)
 - Install the driver
 - Head for the finish line

---

### Post by joris1977 on 2009-02-05
Wow this thread helped me a lot.

lykwydchykyn putted me in the right direction.

For future reference. I was trying to print from my labtop to my desktop computer where the printer is attached. The laptop is connected to the wireless and the desktop is behind a firewall. So the laptop cannot see any printers on the desktop. But with ssh you can easy solve this problem. (Without standing up and getting a lan cable)  

With ssh i forwarded local port 9000 on the labtop to port 631 (cups) on the desktop   

ssh -L9000:localhost:631 -Nf [email]joris@mynetwork.no-ip.org[/email]

than on the desktop:

I went to  cups administration (localhost:631) and ticked "Share published printers connected to this system" and "Allow printing from the Internet"

IPP is set up on the desktop. Now on my laptop

So here i went to cups on the laptop ([http://localhost:631](http://localhost:631)) and ticked Show printers shared by other systems

The printer on my desktop didn't show up, so i added it manually with the  add new printer wizard in gnome->system->administration->printing  

there i selected
- IIP printer
- Selected "Connect to a printer on the Internet... (etc)"
- Put in a URL like this: [http://your_servers_IP:631/printers/name_of_printer](http://your_servers_IP:631/printers/name_of_printer)
- Installed the driver

and it works!

:)

---

