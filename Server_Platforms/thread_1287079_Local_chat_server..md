---
title: "Local chat server."
date: 2009-10-09
forum: Server Platforms
---

### Post by rnodal on 2009-10-09
Hello all,

I would like to set up a chat server for my ubuntu server. I'm looking for pretty much something that allow only logged in users to chat. So the idea in general would be that once an user logins via ssh the can type a command that will get them into the chat and they can chat with one another. Does anyone know of something that is simple and secure? Any recommendations would be fine. The simpler the better :).

Thank you very much.

-r

---

### Post by R.Bucky on 2009-10-11
I was looking myself. Check out [http://www.phpfreechat.net](http://www.phpfreechat.net). Many other chat architectures still run through a 3rd party site, but it appears that this does not. 

Additional resources might include [http://www.go2web20.net/](http://www.go2web20.net/) or [www.opensourcecms.com/](www.opensourcecms.com/)

---

### Post by Rem0te C0ntr01 on 2009-10-12
You may have already found a solution to make a chat server. On my server we just use the good old write command.

hostname$ write user

This does have its limitations, but is good for a quick chat with another user logged in through ssh. 

Another option is to set up a full collaboration suite like Citadel. In addition to being a mail server it also offers some really cool chat features.

---

### Post by rnodal on 2009-10-12
Thank you all for replying.

write works like wall. 

I was looking for something like a console chat client to IRC but the server only allows local chat.

Thanks.

---

### Post by nandemonai on 2009-10-12
Might be a bit of overkill but you could always run a local only IRC server and have clients use irssi to connect?

---

### Post by rnodal on 2009-10-13
I think I'm just going to write my own.
To many dependencies just to allow local communication
between local users.

Thank you all.

---

### Post by tharvish777 on 2009-10-20
A “socket” is the basic connector in network communication. A socket can send and receive data, and a socket can listen for incoming connections. Think of an electrical wall socket in your home. It is sitting there, waiting for a connection. We call waiting for a connection “listening.” When you plug in a vacuum cleaner, the socket comes alive and provides electricity (the metaphor for network data) to the device. Plugging in the device is called “connecting” to the socket. When you unplug the vacuum cleaner, the flow is interrupted and the vacuum cleaner no longer receives power. This unplugging is called “disconnecting.”
 To put the above into technical terms, here is the flow of a socket’s use.
 
[LIST=1]
[*]The socket sits, listening for an incoming connection.
[*]When a connection is made, the socket is capable of sending and receiving data to the connected device.
[*]The client disconnects from the socket.
[*]The socket again begins listening for incoming connections.
[/LIST]
 The above is fine and dandy if you will ever only have a single vacuum cleaner. 
_____________________________________________
[Egypt Holiday Deals](http://www.bestategyptholidays.co.uk)
[nondual](http://www.endless-satsang.com/advaita.htm)

---

