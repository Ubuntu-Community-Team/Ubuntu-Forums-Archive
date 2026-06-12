---
title: "DHCP Server Installation-"
date: 2011-05-30
forum: Server Platforms
---

### Post by ajrutta on 2011-05-30
Ive tried on multiple occasions to setup a dhcp server, but all the google searches return legitimate results it seems, and ill set everything up, except the last few instructions i have to configure /etc/dhcp3/dhcpd.conf and /etc/default/dhcp3-server, but ubuntu says its not there. Does anyone know whats wrong? Im running Ubuntu Server 11.04 and using nano to edit files

---

### Post by ruffEdgz on 2011-05-30
The first question is "Did you install dhcp3-server?" To install, just us either command below:
```

sudo aptitude install dhcp3-server

or

sudo apt-get install dhcp3-server

```

Once that is complete. Run the following commands to find the files you need:
```

sudo updatedb

locate "dhcpd.conf" "dhcp3-server"

```

Hope this helps.

---

### Post by ajrutta on 2011-05-30
Well thanks I'll have to try that. I dont have a very colorful vocabulary in the command line, so i didnt think it could locate something.

---

### Post by brettg on 2011-05-31
I think you will find that [this guide]("http://tuxnetworks.blogspot.com/2010/12/howto-dhcp-server.html") is pretty simple and straight forward. Let me know how you go!

---

### Post by jodoj80 on 2011-06-02
> **brettg said:**
> I think you will find that [this guide]("http://tuxnetworks.blogspot.com/2010/12/howto-dhcp-server.html") is pretty simple and straight forward. Let me know how you go!

This guide couldn't resolve my issue. Everytime I try to restart the DHCP service I get the FAIL message. I change the IP information that appears in the guide with my network information.

I found in other post that the dhcp3-server service has been changed by the isc-dhcp-server. So, if you restart the service dhcp3-server you will get the unrecognized message.

I could find the situation that doesn't let the DHCP service start.

---

