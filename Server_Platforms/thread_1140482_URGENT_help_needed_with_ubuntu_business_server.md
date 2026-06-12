---
title: "URGENT help needed with ubuntu business server"
date: 2009-04-27
forum: Server Platforms
---

### Post by mattyb_53 on 2009-04-27
Hi all.
Sorry for the Urgent tag, but this is mighty urgent. 
I've setup a File Server for a business using the latest and greatest stable Ubuntu distro. It was working totally fine until one day, out of the blue, the server started freezing up.

A reboot fixes the issue, everyone re-connects and then bam, the server freezes up again. 

For example, using the GUI on the server, dragging the mouse across the screen takes a while. Everyone is locked out of the file shares, the CPU jumps. 

Looking at the log files, I cant seem to work my way through the verbose output. Hoping a real techy can get me through this !

I've attached the log files. A user hit the reset button at 10.30, hence the time delay there!

Help!

---

### Post by matt the destroyer on 2009-04-27
You seem to have forgotten the attachment...

In the mean time, what kind of file server? ftp? samba? nfs?

---

### Post by mattyb_53 on 2009-04-27
Darn, 
thought the files attached.
its actinge purely as a Samba Server. I did install the MySql and other packages but they are not in use

---

### Post by mattyb_53 on 2009-04-27
Just looking at it (call me Newbie I have no idea :) ) but it appears to fall over at:

NETDEV WATCHDOG: eth0 (tulip): transmit timed out

Is this something to do with the Ethernet driver??

---

### Post by matt the destroyer on 2009-04-27
I would like to ask you to troubleshoot with me a bit.

First, we should try to eliminate a kernel update as the root of the problem.  When your machine updates the kernel, the old ones will still be installed.  When grub boots, the lower version numbered kernels should still be there.  Select one of the older ones and boot it.

If that fixes the problem, then you need to uninstall the updated kernel and try the next one when it comes out.

If that does not work, try restarting the network to see if this is a network problem:
sudo /etc/initd/networking restart

It that does not work, try restarting samba
sudo /etc/initd/networking restart

Also, just to be sure, this server is on a private network behind a firewall, right?  There is no chance it got hacked?

---

### Post by matt the destroyer on 2009-04-27
hey, what are the machines at 192.168.0.10 and 192.168.0.104?

---

### Post by mattyb_53 on 2009-04-27
I'll give that a try soon.
It is behind a firewall and not hackable!

I hope

Ill get back to you soon.

---

### Post by mattyb_53 on 2009-04-28
Hi All.
Thanks for the help. As it turns out here is how we identified the issue:

The client has several PST files per user which is accessed over a network (TCP / IP connections). Microsoft state that this is a non-supported format.

The client has recently upgraded their Router and Ethernet switch to a very high spec'd switch. This is then linking back into the Ethernet card which is tied to a lower spec machine.

When the number of users increases, the number of links/connections through PST files dramatically slows the network down as the eth0 connection on the file server struggles to keep up.

We closed all outlook connections down, and the problem dissappeared. 

Funny how its always the little things that make the difference. Obviously the fix here is for the client to use.. um.. a Email Server!

---

