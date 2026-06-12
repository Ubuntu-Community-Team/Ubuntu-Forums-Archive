---
title: "SSH and VCN"
date: 2008-09-14
forum: Security
---

### Post by idyllhands on 2008-09-14
Hello there.
I just got into Linux a few weeks back and got a new laptop and put Ubuntu/XP Home dual boot on it.
I want to be able to access my PC at home (running XP Pro 64-bit), and after lots of surfing, have come to the (maybe incorrect) conclusion that VCN is the way to go.
So I looked up tutorials on securing VCN connections and it seems that it is agreed that SSH2 is the best way to connect two desktops remotely, and found this [tutorial]("http://pigtail.net/LRP/printsrv/cygwin-sshd.html") [http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)
But that seems like a whole lot of work just to get an SSH connection going...
Can anyone at least verify that this is the best way to do it?  Or help me find a better way to (securely) connect two desktops?  I am also interested in tutorials on making sure that my home PC isn't vulnerable (since I have to open ports to get it to connect)
Thanks for any tips/links you have.

---

### Post by HermanAB on 2008-09-15
XP Pro has remote desktop.  Enable it and forward port 3389/tcp in your firewall.  Then access the PC using 'rdesktop'.  RDPis secure, safe and works well.

VNC is the wrong solution in this case.

Cheers,

Herman

---

### Post by idyllhands on 2008-09-15
I am not able to connect from XP Home on my laptop to XP Pro at my desktop.  I can get to Accessories>Remote Desktop but it says unable to connect.  Supposedly, XP Home doesn't include RDP...or do they mean that I can't RD *into* the Home box?  Sorry, I know this isn't a windows forum, so if you have a link to a good explanation I would be glad to read it.
So rdesktop is the Ubuntu command to attempt a RDP connection to a windows box?  Do I need any special packages?  Also, are there any settings in Windows I need to tweak (I think I disabled RDP a while ago before I ever planned on setting it up...how do I make sure all the services are running again?)  Lastly, is it safe to open ports on my firewall and router?

---

