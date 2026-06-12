---
title: "OpenNTPd setup correctly?"
date: 2008-09-24
forum: Server Platforms
---

### Post by Dr Small on 2008-09-24
Greetings,

I installed openntpd on my server (mycroft; 192.168.0.70) edited /etc/openntpd/ntpd.conf and allowed it to 'listen *' for all interfaces. I then restarted the services, and proceeded to install openntpd on all the Ubuntu clients.

I then edited the /etc/openntpd/ntpd.conf file on each client to have all listen directives commented out, and changed the server on each, to 'server 192.168.0.70', then restarted the service on each client.

I was wondering, did I set this up correctly?
Dr Small

---

### Post by TomB19 on 2008-09-24
You can choose to broadcast updates and have the clients listen for the broadcast or you can have the clients poll the server.  You have configured the clients to poll the server so make sure this line is in the server config.

restrict 192.168.0.0 mask 255.255.255.0

---

### Post by Dr Small on 2008-09-24
Ok, thanks. I have added that line to the server. Now, one last question that I have, and I think everything should be cleared up about this.

How often do the clients check to update the time, and how can I set this?

Dr Small

---

### Post by TomB19 on 2008-09-24
I think the client will sync up and take care of your time clock as long as it's hardware clock is reasonably close to the server time.  If not, it will just quit.

It's a good idea to run ntpdate prior to starting your ntp client for the first time.

ntpdate 192.168.0.70

/etc/init.d/ntp start

NTP will update the clock frequently, I think it's once per second, but only for a short time.  NTP polls the server less and less over time, using established jitter and offset values to make interim corrections without asking the server.

There is no need to configure this behavior.  NTP is designed to be extremely bandwidth efficient.

---

### Post by Dr Small on 2008-09-25
Ok. Well, I have only installed openntpd on each client. Do I need to install ntp on each client also?

---

