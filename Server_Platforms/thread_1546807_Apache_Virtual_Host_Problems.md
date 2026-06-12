---
title: "Apache Virtual Host Problems"
date: 2010-08-05
forum: Server Platforms
---

### Post by jjacquay712@gmail.com on 2010-08-05
I recently bought a VPS and am trying to configure Apache. I'm new to setting up virtual hosts and I have been having problems. I've been over the documentation numerous times but am still stuck. Here are my requirements:
[LIST]
[*]A request sent to the ip address of the server will be served the default content of example1.com
[*]A request sent to example1.com and [www.example1.com](www.example1.com) will be served the content of example1.com
[*]A request sent to example2.com and [www.example2.com](www.example2.com) will be served the content of example2.com
[*]A request sent sent to example3.com either on port 80 or over ssl will be sent to the content of example3.com
[/LIST]
The problems I am getting with my current configuration is all the sites will be sent to the example1.com site rather than the correct one and if you go to the https version of a site it will go to example3.com. I should also mention that all of these sites are hosted on a single ip.

If someone could show me the correct way to set this up I would be so grateful :D

---

### Post by bschelst on 2010-08-06
can you post your apache config file?

---

