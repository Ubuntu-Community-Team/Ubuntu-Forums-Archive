---
title: "Force SSL"
date: 2015-08-16
forum: Server Platforms
---

### Post by john442 on 2015-08-16
Hello guys,
i try to force a https connection to my ownlcoud.
But it doesnt work if i try to connect over http.

When i try:
[http://5.9.105.59:4423/](http://5.9.105.59:4423/)

This error comes:
[PHP]<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>400 Bad Request</title>
</head><body>
<h1>Bad Request</h1>
<p>Your browser sent a request that this server could not understand.<br />
Reason: You're speaking plain HTTP to an SSL-enabled server port.<br />
Instead use the HTTPS scheme to access this URL, please.<br />
<blockquote>Hint: <a href="https://static.59.105.9.5.clients.your-server.de:4423/"><b>https://static.59.105.9.5.clients.your-server.de:4423/</b></a></blockquote></p>
<hr>
<address>Apache/2.2.22 (Debian) Server at static.59.105.9.5.clients.your-server.de Port 4423</address>
</body></html>[/PHP]


When i try [https://5.9.105.59:4423/](https://5.9.105.59:4423/) everything works fine.

/etc/apache2/sites-enabled/000-default is like this:
[[IMG]http://www11.pic-upload.de/thumb/16.08.15/sh43t34wluq9.jpg[/IMG]]("http://www.pic-upload.de/view-28025710/Unbenannt.jpg.html")


Someone gots a idea?





Sry for my bad english

---

### Post by SeijiSensei on 2015-08-17
Replace the first <VirtualHost> declaration with this:
```

<VirtualHost *:80>
ServerName intranet.local
Redirect /  https://5.9.105.59:4423/ 
</VirtualHost>

<VirtualHost 5.9.105.59:4423>
[same as before]
</VirtualHost>

```

---

### Post by john442 on 2015-08-17
But i want that the ip 10* can be only used with a vpn connection
When i put a virtual host *:80 i can connect from everywhere or not?

---

### Post by SeijiSensei on 2015-08-18
Then use
```
<VirtualHost 10.10.10.10:80>
```
with the correct 10 address instead.

---

### Post by john442 on 2015-08-18
I cant do it like

> <VirtualHost *:80>
ServerName intranet.local
Redirect / [https://5.9.105.59:4423/](https://5.9.105.59:4423/)
</VirtualHost>

<VirtualHost 5.9.105.59:4423>
[same as before]
</VirtualHost>




Because we have a secound service on a nother port with ssl too

---

### Post by SeijiSensei on 2015-08-18
I don't think that should matter.  Is Apache handling connections for that port as well?  Just add another <VirtualHost> stanza.  SSL certificates are tied to hostnames, not ports, so you should be fine with the one certificate.  

Have you actually tried my suggestion, and it did not work?  What errors do you get?

---

### Post by john442 on 2015-08-18
Idk if i understood u right.
Should i delete everything at <VirtualHost 10.8.0.1:80> ?
That it looks like ur example?:

<VirtualHost 10.8.0.1:80>
ServerName intranet.local
Redirect / [https://5.9.105.59:4423/](https://5.9.105.59:4423/)
</VirtualHost>


Or just edit my <VirtualHost 10.8.0.1:80> and add the
ServerName intranet.local
Redirect / [https://5.9.105.59:4423/](https://5.9.105.59:4423/)
stuff?

---

### Post by SeijiSensei on 2015-08-18
Yes, you want to delete all the stuff you had before for 10.8.0.1 and just include the Redirect directive.

---

### Post by john442 on 2015-08-19
Didnt work for me.
I will ask a sysadmin

---

### Post by CharlesA on 2015-08-19
You really shouldn't be editing your posts to remove all the information after the fact, but since you did I'm going to go ahead and close the thread.

---

### Post by PaulW2U on 2015-08-19
For the benefit of john442 and anyone else reading this thread, such actions will not endear you to other forum users that might offer to help with future requests for help.

If you wish to close any thread that you have started then please report any post, preferably one of your own, giving the reason(s) that you want it closed and the forum staff will happily oblige if they see it as appropriate. I've always seen that the editing of posts is a privilege granted to users to correct spelling or grammar errors and to add anything that had been forgotten when creating the initial post and not to delete the original request.

---

### Post by coffeecat on 2015-08-19
The forum policy on this is quite clear:

[http://ubuntuforums.org/showthread.php?t=2231107](http://ubuntuforums.org/showthread.php?t=2231107)

>  Removal of significant content from a number of posts is considered to be forum vandalism and will probably be dealt with by the account being banned and restoration of original post content.


As soon as I've posted I'll restore the original content to the OP's posts.

---

