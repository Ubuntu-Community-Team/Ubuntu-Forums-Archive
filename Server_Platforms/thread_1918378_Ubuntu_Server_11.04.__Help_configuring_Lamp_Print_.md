---
title: "Ubuntu Server 11.04.  Help configuring Lamp Print Server."
date: 2012-01-31
forum: Server Platforms
---

### Post by jupiter_spunk on 2012-01-31
I have Ubuntu server 11.04  with Lamp installed using the following instructions. 

[http://www.ubuntugeek.com/step-by-step-ubuntu-11-04-natty-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-11-04-natty-lamp-server-setup.html)

Its been up and running for some time but I wanted to add a print server to use locally. 


I ran taskel and added the print server. 

Then I installed the hp tools. and ran 


```
sudo hp-setup -i
```


I'm showing the printer configured, and I set it to default.
 ```
lpstat -p -d
printer HP_LaserJet_P1006 is idle.  enabled since Tue 31 Jan 2012 07:23:53 PM CST
no system default destination

```

```
lpoptions -d HP_LaserJet_P1006
```

```

lpstat -p -d
printer HP_LaserJet_P1006 is idle.  enabled since Tue 31 Jan 2012 07:23:53 PM CST
system default destination: HP_LaserJet_P1006
```

I tried printing a test page. 

```
lpr /etc/fstab
```

The Printer is showing as Printing but nothing happens. 

```
lpstat -p -d
printer HP_LaserJet_P1006 now printing HP_LaserJet_P1006-1.  enabled since Tue 31 Jan 2012 07:46:06 PM CST
system default destination: HP_LaserJet_P1006
```

I also cannot find the device when trying to add it on another box running mint 10.

cups.conf settings

```
# Only listen for connections from the local machine.
#Listen localhost:631                   #existing loopback Listen       
#Listen /var/run/cups/cups.sock         #existing socket Listen
#Listen 192.168.1.20:631                #Listen on the LAN interface, Port 631 (IPP)
Port 631                                #Listen on port 631 on all interfaces

```

```
# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseLocalProtocols CUPS dnssd
BrowseAddress @LOCAL

```


Help,  what am I doing wrong?

---

### Post by LHammonds on 2012-02-01
I had problems getting CUPS setup as well...mainly because I'm a Linux noob.  A nice person pointed me in the direction of [Zentyal](http://www.zentyal.org/) and I was able to setup a new (virtual) print server very quickly with dozens of HP LaserJets and Brother HL printers.

I know this probably won't help your situation for bolting on another service to an existing server but thought I'd share anyway.

I am also working on documenting everything I did setting up this print server in my environment and will post my how-to notes on Zentyal's forums today or tomorrow.  If I remember, I will update this post with a link to it.

LHammonds

---

### Post by jupiter_spunk on 2012-02-01
> **LHammonds said:**
> I had problems getting CUPS setup as well...mainly because I'm a Linux noob.  A nice person pointed me in the direction of [Zentyal](http://www.zentyal.org/) and I was able to setup a new (virtual) print server very quickly with dozens of HP LaserJets and Brother HL printers.

I know this probably won't help your situation for bolting on another service to an existing server but thought I'd share anyway.

I am also working on documenting everything I did setting up this print server in my environment and will post my how-to notes on Zentyal's forums today or tomorrow.  If I remember, I will update this post with a link to it.

LHammonds


That looks like A nice custom Linux Distro for small office use. 
I may switch my box over to that and dump the web server portion.
I should really buy dedicated hosting to for that type of service anyways.  

I was looking. Do you know if they offer a Nas Option?  I would setup a box with Raid, and use an NFS etc.

---

### Post by jupiter_spunk on 2012-02-01
Never mind.  they do with CIFS sharing.

[http://doc.zentyal.org/en/installation.html?highlight=raid](http://doc.zentyal.org/en/installation.html?highlight=raid)

---

### Post by LHammonds on 2012-02-02
As promised, here is [the thread](http://forum.zentyal.org/index.php/topic,9472.0.html) I created to document my install / setup notes.  It is still a work-in-progress.

LHammonds

---

