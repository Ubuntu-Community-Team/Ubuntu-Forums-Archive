---
title: "Webserver stopped serving web content"
date: 2017-05-22
forum: Server Platforms
---

### Post by Daniel_Clarke on 2017-05-22
Hey all,

I am new to Ubuntu/Linux and have created a VPS web server using Ubuntu 16.04 LTS. Everything was working fine, however I was also using Webmin and a few updates came through, I applied the updates and now the server is no longer serving content? The websites are down, webmin is down. When I try to go to any of the websites I get:

[SIZE=3]This site can’t be reached[/SIZE]

192.168.200.203 refused to connect.

Try:

Checking the connection

Checking the proxy and the firewall

ERR_CONNECTION_REFUSED

Any and all help would be greatly appreciated, the server is still showing the correct IP configuration however I am only able to ping local? What is going on here, I'm stuck and not sure where to look.

Thanks in advance for any help.

-daniel

---

### Post by slickymaster on 2017-05-22
*Thread moved to **Server Platforms*** for a better fit

---

### Post by darkod on 2017-05-22
Does ssh session to the server work? Can you get in to do some checks?

Webmin is really not recommended and not supported, although many people unfortunately see it as an easy way to get linux server with GUI. I would encourige you to learn administering your linux servers on the command line. I can't say for sure this was because of webmin, but it has been known that sometimes some files can be changed differently if you use webmin.

---

### Post by QIII on 2017-05-22
Hello!

If you cannot start an ssh session, does your VPS provider give you some sort of a control panel that allows you to gain access to the machine?

---

### Post by Daniel_Clarke on 2017-05-23
Hey,

Thank you for the responses, I am a little embarrassed but relieved to say this was a user error, doh! ALL is good and the web server is back online!

Thanks again

---

