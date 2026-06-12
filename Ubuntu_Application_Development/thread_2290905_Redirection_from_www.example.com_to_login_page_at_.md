---
title: "Redirection from www.example.com to login page at www.example.com/index.jsp"
date: 2015-08-16
forum: Ubuntu Application Development
---

### Post by tech6 on 2015-08-16
[COLOR=#000000][FONT=Arial]I have setup apache2 and tomcat7 on ubuntu 14.04.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]my domain name is [www.example.com]("http://www.example.com") , which I want to redirect to thewww.example.com/index.jsp on to the tomcat as this is the login page. Howcan this be done? The set up works fine for a request made towww.example.com/index.jsp. The apache virtualHost setting is ProxyPass /ajp://localhost:8009/ ProxyPassReverse / ajp://localhost:8009/[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]the redirection in my understanding should happen on the apache. As theapache is acting just as a proxy and not serving any requests by itself canwe use the directive ? Where and how to make the change. Any pointersappreciated[/FONT][/COLOR]

---

