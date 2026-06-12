---
title: "Access Web Server Behind Router and ADSL Modem"
date: 2011-12-21
forum: Server Platforms
---

### Post by MONODA on 2011-12-21
So Ive setup a web server which I have been able to successfully access via the 192.168... IP but have been unable to access it through the internet. I have enabled port forwarding on ports 80 and 22 (for ssh) in both my router and modem. I have successfully ssh-ed into the server using the public internet address through port 22 so I guess that means that Ive properly setup the server. When I load the public IP in a web browser expecting the web page to be served, I am taken to the config page of the router (Speedtouch 546v6) and cant find a way to access my web page even though I have enabled port forwarding and configured the modem and disabled the feature which loads the config page by default.

Thanks in advance and let me know if any information would be helpful.

---

### Post by elliotbeken on 2011-12-21
if you use this sit and test the ports you should have open and it should tell you if they are open/accessible or post or PM the dns/ip address of the server and i can see it for you.

Hope this helps

---

### Post by MONODA on 2011-12-21
So it seems that port 80 is closed and port 22 is open. When I run "# nmap localhost -p 1-65535" on my server, I am told that they are both open.

---

### Post by arrrghhh on 2011-12-21
> **MONODA said:**
> So it seems that port 80 is closed and port 22 is open. When I run "# nmap localhost -p 1-65535" on my server, I am told that they are both open.

Some ISP's block port 80... might want to try to move the web server to a different port just to rule that out.

Since ssh works fine over 22, and the configuration (I assume) is identical... that certainly is a possibility.

Have you looked at [GRC's website](https://www.grc.com/x/ne.dll?bh0bkyd2)...?  It can help establish which ports are visible to the internets.

---

### Post by elliotbeken on 2011-12-21
you can also use [http://canyouseeme.org/](http://canyouseeme.org/) its is a very simple tool and works well.

that is a good idea, change the port to something like 8080 and then forward that port. if that does not work try another port etc.

---

### Post by Tteddo on 2011-12-21
What brand router? I know my Trendnet shows the router page when I try to access my webserver from inside, but it actually works when I am not here.

---

### Post by arrrghhh on 2011-12-21
> **Tteddo said:**
> What brand router? I know my Trendnet shows the router page when I try to access my webserver from inside, but it actually works when I am not here.

That's a good point too that I always overlook.

Are you actually trying to hit your webserver from the outside, or are you trying to hit it from the outside, inside the LAN?  That doesn't always work (depends on the router).

Please ensure you are testing with another connection, thanks.

---

### Post by MONODA on 2011-12-22
Well its a SpeedTouch by Alcatel. Ill try accessing it from anothing network but the thing is when I check the port from a port checking site it says that 80 is closed by 22 is open. Im thinking that my ISP is blocking my access to it, any ideas as to how I can change the port my server uses?

---

### Post by elliotbeken on 2011-12-22
Who is your ISP ?

---

### Post by arrrghhh on 2011-12-22
> **MONODA said:**
> Well its a SpeedTouch by Alcatel. Ill try accessing it from anothing network but the thing is when I check the port from a port checking site it says that 80 is closed by 22 is open. Im thinking that my ISP is blocking my access to it, any ideas as to how I can change the port my server uses?

Assuming you're using Apache...

[http://www.cyberciti.biz/faq/linux-apache2-change-default-port-ipbinding/](http://www.cyberciti.biz/faq/linux-apache2-change-default-port-ipbinding/)

---

