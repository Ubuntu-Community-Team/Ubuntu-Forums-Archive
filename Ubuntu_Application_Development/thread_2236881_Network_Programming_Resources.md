---
title: "Network Programming Resources"
date: 2014-07-29
forum: Ubuntu Application Development
---

### Post by amish_otaku on 2014-07-29
I would love to know if there's anything anyone could point me to that would help explain how to write a network service/daemon. can anyone point me on how to do this? I will probably be using my language as c++.

---

### Post by ian-weisser on 2014-07-29
That's pretty broad. A network service/daemon that does what?

Any service should behave properly in an Upstart (soon to be replaced by systemd) init environment. Especially the socket bridges.
Most services should be able to communicate usefully using dbus.
Services should generally not open a listening port without good reason and documentation. The user will need to open a hole in the firewall for it. 
Classic daemons are becoming more rare. Many services terminate when not in use. Upstart, systemd, and dbus can spawn new instances as needed.
Some services (like printers and media severs) advertise themselves across a LAN using Avahi and/or Samba. 

Or do you just want to write a plain old customized http server?

---

### Post by amish_otaku on 2014-07-30
Basically it would fall closer to a customized http server. I'm more or less wanting to play around with coding that will allow me to figure out exactly how to successfully create network programs with more emphasis on the server end of it. That way in the future I could write my own customized servers for my own environment. One option I could do would be to write my own chat server/client, I do think this would help me understand exactly how the client/server communication works on a more basic level. I mean I do understand the high level stuff, but I would love to learn more of the nitty gritty.

---

### Post by ian-weisser on 2014-07-30
An http server is just one of many kinds of servers.
Http is common, and pretty easy to use. It also has a lot of baggage.

Mostly, you need to learn about sockets, and when/why/how you bind() and connect() to them. You'll need to write a socket server to handle the inbound and outbound connections.

[Here is a sample]("http://cheesehead-techblog.blogspot.com/2013/12/handy-pipe-and-socket-reference.html") that I wrote back when I was learning about network programming.

If you really want to do http, then there's some extra baggage - URL parsing, error codes, etc. that you need to worry about.

Then you write a handler, which handles all the input and output logic. This is usually the part you care most about; the fun part! It receives the input from the socket server, and sends the reply.

Usually, the socket server spawns a new handler thread for each connection (or session), and terminates when the connection completes.

---

