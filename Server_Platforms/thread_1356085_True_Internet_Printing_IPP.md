---
title: "True Internet Printing IPP"
date: 2009-12-15
forum: Server Platforms
---

### Post by Tony Ricena on 2009-12-15
Hello everyone, 

I installed Ubuntu Server edition 9.04 on an old Dell computer that I have to act as a Print Server for my LAN.  I have a HP Photosmart p1000 connected via USB on the server and everything is set up correctly as far as I know.  Local Computers (Kubuntu 9.04) add the printer with no problems, everything works great.  The one thing though, I want to use my server for internet printing via CUPS.  I went into my router and set a static IP address for my server and opened up appropriate ports via port forwarding for cups to that server.  I even enabled DMZ to the server to make sure I am not forgetting anything.  I want my father to add my local printer via ipp through the internet so he can print things via my printer that is directed to me.  Its more for experimental purposes.  Now for some reason, he is unable to connect to my printer when he adds it on his computer.  We go through the motions and i have him set the new printer via IPP Cups in the add printer section, but it can never connect to my server.  I make sure to give him the CORRECT IP address (ie the internet address not the LAN address) but we still cannot create a connection.  Firewall on server is set up for this.  We can do almost everything via remote (ie VNC from his computer to my server, ssh etc) but cannot for the life of me get this working.  He can access my webmin:10000, my cups:631 http websites but we can't get the actuall printer connected via internet printing protocol.  Has anyone ever attempted this, if so can I get some help?  Could it possibly be a problem with my route tables?  My LAN IP address are of course much different from Internet IP address.  Any help would be great, thanks.  

If you need any additional questions let me know.

---

### Post by Tony Ricena on 2009-12-15
bump?

---

### Post by craigp84 on 2009-12-15
Just a stab in the dark but are there any restrictions defined in your cups conf for access to ipp://<hostname>/printers/ ?

IPP is just http traffic, so if you can see the cups webpages being served up from the remote client, then all the network level config is good.

Worth having a look at the cupsd logging, see what it says. The only thing i can think of is permissions on /printers/ or authentication issues -- can you print from another computer on the local LAN (a virtual machine on the same host, with its own IP would also do to test this)?

I don't know about more recent ubuntu releases but we used to have to add the cups user to the shadow group (which carries security implications in the case that a certain class of bug is found in cups) for cups to be able to authenticate for user accounts on the serving host.

---

### Post by Tony Ricena on 2009-12-15
Yes, I can print from all my PC's on the LAN.  I have allowed public access (no password yet for printing, just testing until i know it works).

I have enabled the following in CUPS via webpage
Share published printers connected to this system
         Allow printing from the Internet
 Allow remote administration

I can connect via my Windows XP partition as well.  It just seems anything outside my LAN, nothing.  Its being shared for public use

---

### Post by craigp84 on 2009-12-15
Ok, don't give up on this, it's definately solvable :-)

Next steps are to check what cupsd is saying, what does it think of the connections coming in from the outside world? You may need to bump up the logging level of cups to get more info, but even on the default logging level i'd expect to get a message telling us why cupsd is choosing to ignore external connections. Cups logs via syslog so you'll find the logs in /var/log on your box.

Next up, and kind of a last resort in terms of pinpointing what the cause of this is, would be to use a packet sniffer on the cupsd host. So if we dont get anywhere by finding out what cups is saying about the connections, install wireshark if you want a gui or tcpdump if you're happy on the command line. This will help us see what's going on in case the router is blocking the packets (we'd see no traffic at all in the sniff session), or maybe you have an iptables rule you're not aware of which is rejecting packets etc. etc.

---

