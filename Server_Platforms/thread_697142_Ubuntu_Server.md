---
title: "Ubuntu Server"
date: 2008-02-14
forum: Server Platforms
---

### Post by tom_the_drummer on 2008-02-14
Hi guys,

What I would like to do, is a have a computer which just sits there, as a server, with some programs installed which I can run off the sever, and a place to store all my documents - on the server.

a) I asume this is possible with ubuntu server?

b) can I remote desktop control the server?

c) can the sever also be used as a normal computer or is it best to leave it?

d) is it possible to set up a domain say "x network" which the server hosts, then set up "x network" on a couple of other computers? I know this is possible with windows server eiditions (somehow - this is all new to me!) but wouldn't know how in Ubuntu

e) can anyone recommend me any good books on servers/netowrking etc.?


Thanks a lot guys and look forward to your replies!



Tom

---

### Post by lnx4me on 2008-02-14
Samba - 3 By example would be the best place to start.

---

### Post by canh_nguyen on 2008-02-14
b) What's type of remote?

Windows<->Ubuntu : Using an vncviewer software (Ex [tightvnc]("http://www.tightvnc.com/download.html")) to connect to Ubuntu from Windows because Ubuntu support VNC and Windows only support RDP.

Linux(Ubuntu)<->Ubuntu:

More infomation [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html")

c) Yes.

e) You can using google. It's a good book :D

---

### Post by faulkes on 2008-02-15
By default, the server does not ship with X installed.  Which is a pre-requisite for tightvnc (iirc).

It is entirely possible to install X on the server and use either tightvnc or other X based desktop connections.

Servers are best left doing what servers do, serve.  However, in the case of a home user, there is nothing preventing you from making additional use of it.  On that note however, it would probably be easier to intsall the desktop edition and add server software packages as required.

Samba is well supported (re: x network) by ubuntu and the community, which would allow you to setup shares, printers, etc like windows does.

You can find documentation at:

[https://help.ubuntu.com/7.10/server/C/](https://help.ubuntu.com/7.10/server/C/)

and

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

Faulkes

---

