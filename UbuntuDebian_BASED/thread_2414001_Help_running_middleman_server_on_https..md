---
title: "Help running middleman server on https."
date: 2019-03-04
forum: Ubuntu/Debian BASED
---

### Post by dsipe110 on 2019-03-04
**Serving Slate/middleman server over HTTPS?**


[COLOR=#16171A][FONT=-apple-system]I'm not familiar with middleman server or slate but I also can't seem to find any documentation on how to run slate/middleman server over https.

[/FONT][/COLOR]
[COLOR=#16171A][FONT=-apple-system]I run the slate app using docker per the github link and it works very well. I can change the docker-compose.yml file to support port 443 as well as the config.rb middleman config file to serve slate on port 443.[/FONT][/COLOR]
[COLOR=#16171A][FONT=-apple-system]The problem I'm encountering is that this seems to offer the slate server on port 443 over http[/FONT][/COLOR]
[COLOR=#16171A][FONT=-apple-system][http://slate-server:443]("http://slate-server:443/") <-----works 
[https://slate-server]("https://slate-server/") <---- does not work
It seems as if the server is configured to listen on port 443 but not configured for SSL traffic. In other words I merely changed the port from 80 to 443, so it is serving HTTP on port 443

[/FONT][/COLOR]
[COLOR=#16171A][FONT=-apple-system]Any help on configuring middleman server/slate to run on https or related documentation would help.[/FONT][/COLOR]

---

### Post by TheFu on 2019-03-04
No clue about docker or either of those servers, but if you want HTTPS, much more setup and configs and external certs will be necessary.  The specific web server used is where I'd begin. There are plenty of guides for setting up HTTPS on nginx or apache.  They aren't difficult, just every step and very close attention to details is mandatory.

How docker or any container may help or hinder that setup is beyond me. Sorry.

---

