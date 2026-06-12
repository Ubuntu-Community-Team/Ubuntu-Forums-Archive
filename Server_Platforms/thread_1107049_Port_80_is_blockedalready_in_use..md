---
title: "Port 80 is blocked/already in use."
date: 2009-03-26
forum: Server Platforms
---

### Post by Johnsie on 2009-03-26
Someone else is already using port 80 so I have to use a different port. I have a domain name, but I dont want users having to type ":90" at the end of the url. Is there any way around this?


I've seen that no-ip.com seem to have some kind of option for this but it is a paid service. Does anyone know. I would prefer the other ports on the domain to act as normal so basic url forwarding might not be an option.


Thanks in advance,

John M.

---

### Post by albandy on 2009-03-26
Could you describe your network topology? When you said someone it's using port 80 are you talking about other computer or other service?

---

### Post by Johnsie on 2009-03-26
Port 80 forwards to another computer that I am not allowed to touch due to it being used by other departments.

I can get port forwarding for any other port, just not that one.

---

### Post by bigbearomaha on 2009-03-26
Port 80 is the default port Apache web server uses.  if it is running on that machine and you want to use another webserver app you can either change apache to use a different port or the new one you want to install to use a different port.

most web browsers are pre-set to automatically look for port 80 as a web server so users don't have to enter :80 at the end of the url they type in.

actually, most browsers have certain pre-sets for a variety of common used ports for that purpose.

If you just want to run a different website apart from the already running apps/pages being served on the main one in apache currently, you can setup another virtual server within apache to server a different domain name, you then use your control panel at the domain host to use the specs for your new virtual web server on that machine.

Big Bear

---

### Post by albandy on 2009-03-26
a little trick it's to define a index.html in an external account and make a redirection with an http refresh, something like this:

<html>
<head>
<meta http-equiv="Refresh" content="0; url=/thisismyip:8080">
</head>

---

### Post by Johnsie on 2009-03-26
.

---

