---
title: "I cant access my Webpage from Internal network but does work fromthe outside world"
date: 2014-04-25
forum: Server Platforms
---

### Post by Chris_Cato on 2014-04-25
Hi,

I need some help to resolve an issue.
I cant access my Webpage from Internal network but it does work from the outside world.

I have set up a LAMP server and am also using Webmin.

My Virtual server works fine. My default webpage works outside my LAN but inside, when I type in the full address "[www.Webpage.]("http://www.Webpage")com" I get my Router Admin logon page (which happens to be what's doing DNS).

I have a static IP and port forward to my server IP.  Which obviously works as externally the Webpage resolves back to the server.

When I type in the browser on the internal network ip. [http://10.1.1.8](http://10.1.1.8),  I get the message below.
[B]
Index of /[/B]
Apache/2.4.7 (Ubuntu) Server at 10.1.1.8 Port 80

Can someone please help me,  I gather its going to be to do with localhost. etc/hosts.


Thanks in advance
CC

---

### Post by slickymaster on 2014-04-25
Hi Chris_Cato, welcome to the forums. I'm moving your thread to the Server Platforms sub-forum where you'll have a more adequate help.

---

### Post by volkswagner on 2014-04-25
This is likely due to router settings.  Look for NAT settings in either firewall or security.  What is the model of your router?

---

### Post by Chris_Cato on 2014-04-25
Its an iinet router, i can set up as below, but there are also special applications for trigger ports available
but No NAT settings set up currently.

Would i setup my Static IP as Global,
and my Server IP below/

[TABLE="width: 55%, align: center"]
[TR]
[TD="class: tdTitle, width: 98%"]Address Mapping[/TD]
[/TR]
[TR]
[TD="class: tdText"]1. Global IP:... is transformed as multiple virtual IPs[/TD]
[/TR]
[TR]
[TD="class: tdText"]    from 10.1.1.8 to 10.1.1.8[/TD]
[/TR]
[/TABLE]

or set up a trigger port

[TABLE="width: 90%, align: center"]
[TR]
[TD="class: tdTitlec"][/TD]
[TD="class: tdTitlec"]Trigger Port[/TD]
[TD="class: tdTitlec"]Trigger Type[/TD]
[TD="class: tdTitlec"]Public Port[/TD]
[TD="class: tdTitlec"]Public Type[/TD]
[TD="class: tdTitlec"]Wan Interface[/TD]
[TD="class: tdTitlec"]Enabled[/TD]
[/TR]
[TR]
[TD="class: tdText"]1.[/TD]
[TD="class: tdTextc"][/TD]
[TD="class: tdTextc"]TCPUDP[/TD]
[TD="class: tdTextc"][/TD]
[TD="class: tdTextc"]TCPUDP[/TD]
[TD="class: tdTextc, align: left"][/TD]
[TD="class: tdTextc"][/TD]
[/TR]
[/TABLE]

---

### Post by Chris_Cato on 2014-04-25
Oops, should checked this earlier. 
I was Port forwarding to Server IP  and I still had my old DMZ zone active.

Turned off DMZ and left only Port forwarding on..
Feel like a damn goose now.

I have now made so many mods to my server..  who knows if i have caused more problems..

Thanks for your help..   Pushed me to the answer..

CC

---

