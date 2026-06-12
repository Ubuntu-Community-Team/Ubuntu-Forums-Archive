---
title: "Squid3 Multiple users with restricted dedicated ip"
date: 2017-02-15
forum: Server Platforms
---

### Post by kks21199 on 2017-02-15
[COLOR=#242729][FONT=Arial]I would like to restrict users to single IP so that each will get their own dedicated IP. Currently, I set up squid with a single IP for multiple users. I follow this [instruction]("https://thetechterminus.com/http-proxy-with-advanced-authentication-in-squid/") to setup the squid server.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]For example, if I have the following IPs[/FONT][/COLOR]

[LIST]
[*]10.10.10.1
[*]10.10.10.2
[*]10.10.10.3
[*]10.10.10.4
[/LIST]
[COLOR=#242729][FONT=Arial]and the 4 users,[/FONT][/COLOR]

[LIST]
[*]user1
[*]user2
[*]user3
[*]user4
[/LIST]
[COLOR=#242729][FONT=Arial]I want to restrict user1 to 10.10.10.1 (once logged in, user1 will access the web with 10.10.10.1) and user2 to 10.10.10.2 no matter which IP they login from or which site they try to access. I have only found answers to restrict login IPs and access to certain domains.

I don't care where the user's login from. The users can login from any ip and any machine but they can only login to the ip they are given and serve the web with it.

[/FONT][/COLOR]

---

