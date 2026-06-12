---
title: "IRCd-hybrid + Hybserv help"
date: 2011-03-23
forum: Server Platforms
---

### Post by Drise on 2011-03-23
Well, after many many hours trying to get this to work properly with most of them me smashing my head on the desk hoping my latest change will work, I'm sucking up my pride and asking for help. 

I have an ubuntu server that is running IRCd-hybrib 7.2.2. Granted this works and get the job done that my server needs it for, but we are looking to get NickServ and ChanServ to work. Ive spent a number of hours trying to get this to work, and I get nothing. I think NickServ is somewhat working, but all I get when I type /nickserv is "NICKSERV :Not enough parameters". Any other commands do not work. I don't know a lot about setting up an IRC server but I figured it would be a learning experience. I have enough Linux knowledge to do what I need to, but anything advanced is... well advanced. I'm paste-bin-ing my ircd.conf and hybserv.conf respectively. 

[ircd.conf]("http://pastebin.com/P8Rk6x42")
[hybserv.conf]("http://pastebin.com/Et2g21qm")

Also on login, I get this before I'm allowed in: 
> * Looking up drise.servegame.com
* Connecting to drise.servegame.com (24.236.91.225) port 6667...
* Connected. Now logging in...
* *** Looking up your hostname...
* *** Checking Ident
* *** Couldn't look up your hostname
* *** No Ident response

Also #2: I've done the compiling bit needed for hybserv(or so I read) but not sure if I did that right.

Also #3: If you so like, the IRC server ip is drise.servegame.com. Usually I reside in #minecraftchat

Thank you for anyone who has any idea on what I need to do to fix this.

---

