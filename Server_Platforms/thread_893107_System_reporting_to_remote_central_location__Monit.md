---
title: "System reporting to remote central location / Monitoring / alerting"
date: 2008-08-17
forum: Server Platforms
---

### Post by rslrdx on 2008-08-17
Hi, and TIA,

I'm here looking for some ideas and opinions on some things I want and need to do related to network monitoring and system reporting.

I'm looking for some tool/agent/client that can run on a box (server or desktop) and collect some data about the box state, like CPU average, uptime, traffic, ups status, hd space, services like apache, samba, Asterisk, cups, mysql, etc, and based on that generate report and send the information to a central server, but not on the same network at all, most likely just a reporting gateway with a web address, and the information can be processed on by the central server and displayed on a admin interface..

What I need this for? well, I got a few servers setup for friends and clients, and they are not on my network at all, but they come back to me when there is a problem, and this would really help to avoid that situation as I can monitor their state and perhaps be alerted about this problems.

I know there is lots of tools like nagios, zabbix, zenoss, among many others, but most require that the server be setup to go out and check for stuff, and they do that greatly, but in this case unfortunately its not an option. I know zabbix has an agent, but I'm not sure its what i need as i have not tried all options out there and this tools work great for the Intranet, but I'm talking remote reporting. I like to avoid using email reporting if I can.


I don't have a domain registered to host the server to report to or an static IP, I just have a broadband connection and ddns setup.

So please, if you got any input on this let me know. It would just help me a lot if I could just avoid being cought by surprise with a call saying, "Hey, the system is not working again"

TIA,
Rodrigo.

---

### Post by rslrdx on 2008-08-19
/bump

anyone?

---

### Post by hyper_ch on 2008-08-19
a simple version would be to run a php script that executes "ps aux"... you then call that remote php script and parse it... or something similar.

---

### Post by rslrdx on 2008-08-24
got any sample coding on that php script with ps aux ? i'm looking for something that has the ability to run without interaction and just report back, and have a interface for me to look at rather than logs, so i guess the script would workd, but not sure thats the only option, so if anyone can think any other options i'm all ears.

---

