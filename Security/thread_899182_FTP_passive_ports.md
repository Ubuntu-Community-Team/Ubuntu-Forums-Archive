---
title: "FTP passive ports?"
date: 2008-08-24
forum: Security
---

### Post by Kain000 on 2008-08-24
Hey everyone, 
I've recently built a server running Ubuntu 8.04 out of spare parts to host my music and video library for both my home network and as a FTP server for anywhere access to my files.   
I figured out that even though i've allowed all traffic on port 21 from anywhere, because FTP clients like to use passive ports connections get blocked by iptables.  The program I am using for the FTP's is ProFTP and it's GPROFTP for the GUI.  It lists a passive port range by default that is arround 2000 ports long, I'm wondering is that universal?   
I'm no security expert by any stretch but opening 2000 ports just seems like madness!  On most FTP clients, where you can tell it to use active mode only on port 21 or use passive mode, but doesnt let you specify what ports it should consider passive mode ports.  THis led me to believe that those default ports in GPROFTP must be a standard for passive FTP ports.   
Maybe i'm being paranoid but it seems that having that huge of a hole in my firewall would defeat the porpass.

---

### Post by ds[de] on 2008-09-01
Hi,

being (a little) paranoid about security is never a bad idea :-)

When a FTP client issues a 'pasv' command to the server, it opens up a random port without the (pre-defined) port range, the ports aren't open all the time.
The server will reply with something like 
```
227 Entering Passive Mode (ip,ip,ip,ip,porth,portl)
```

Where the server IP is being displayed in the usual fashion (four decimal bytes), and the port is being specified by multiplying porth by 256 and adding portl.

So for example, (127,0,0,1,4,15) tells the client to open up a TCP connection to 127.0.0.1:1039.

Hope I could clear things up for you.


Regards,
ds[de]

---

### Post by Kain000 on 2008-09-01
hey thanks.  so the client would request a passive port to talk to, and PROFTP (using the specified port range) would give it a free one?  After witch the port would close again?

---

### Post by ds[de] on 2008-09-01
Exactly (that's at least how it is supposed to work :-)

---

### Post by kevdog on 2008-09-01
The use of FTP with passive ports is totally possible if you are using iptables along with the contrack module.  This module keeps track of the passive ports allocated -- and dynamically alters the firewall rules to allow use of certain ports as long as the command channel remains open.  

Do you still plan on using iptables on the ftp server?

---

### Post by Kain000 on 2008-09-02
yes, I thought having a computer always online would require a firewall, (espacially with bittorent traffic)  Where would I find contrack? I dont see it in synaptic.

---

### Post by kpatz on 2008-09-02
```

sudo apt-get install conntrack conntrack-tools

```

This will get you the conntrack package.

---

### Post by kevdog on 2008-09-02
How are you configuring your iptables?  Through a script or a GUI.

I configure mine through a shell script and include for the FTP contrack modules:

MODPROBE=/sbin/modprobe


### load connection-tracking modules
#
$MODPROBE ip_conntrack
$MODPROBE ip_conntrack_ftp

---

