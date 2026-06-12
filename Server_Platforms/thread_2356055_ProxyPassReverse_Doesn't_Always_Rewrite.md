---
title: "ProxyPassReverse Doesn't Always Rewrite"
date: 2017-03-19
forum: Server Platforms
---

### Post by theonlytalkinggoat on 2017-03-19
[COLOR=#242729][FONT=Arial]I am trying to proxy to another server in our network and, for the most part, it works. However, in some situations, the rewrite does not work. To start, the setup is pretty simple...
```
ProxyPassReverse /a7V43BDr/zm http://192.168.15.79/zm
ProxyPass /a7V43BDr/zm http://192.168.15.79/zm

```Where 192.168.15.79 is a DVR server. When I pull up the server using [https://example.com/a7V43BDr/zm](https://example.com/a7V43BDr/zm), the website comes up correctly. All of the links work and show the information I need. All of the cameras work, correctly. The problem comes into play when I try to do anything that involves a button. For instance, if I click logout, I am given the correct page, through a popup. The logout page displays, but when I click the actual logout link, I get a 404 and the address is changed to [https://example.com/zm](https://example.com/zm) Notice the a7V43BDr is missing.
Am I not doing something right?


[/FONT][/COLOR]

---

