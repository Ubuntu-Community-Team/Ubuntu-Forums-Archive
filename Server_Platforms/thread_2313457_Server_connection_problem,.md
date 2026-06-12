---
title: "Server connection problem,"
date: 2016-02-12
forum: Server Platforms
---

### Post by Lexion45 on 2016-02-12
Hello.
I recently set up an Ubuntu home server (15.10) 
on a Dell Optiplex 755.
 It is plugged in to a Linksys AC1200 + router.
My Linksys admin page shows the server is detected, gives the correct name of the server and a local i.p is assigned.

I can ping the server with its i.p. or 'loacalhost' from the terminal on my main computer, but I can not access the server with it. It simply says server not found.
With a monitor and keyboard hooked to the server,, I can access it with the password prompt.
Also, I am looking to keep this server 'local' for now, so I am not interested in remote access outside my home.
 I would be extremely grateful for any suggestions you may have.
Thank you  
P.S.  I also installed SSH, and I can connect to the internet with the server directly.

---

### Post by darkod on 2016-02-12
Using localhost from your desktop is looking at your desktop, not your server. Using localhost on any computer is always looking into that same computer.

If you installed ssh server on your server, you should be able to reach it but it depends whether your desktop is using linux or windows.

From linux desktop, open Terminal and simply open ssh session to your server IP using the username you set on it (it will prompt you for a password):
```
ssh username@IP
```

From windows, the most used ssh client is Putty. Get it from the internet and again you can open ssh session to your server.

Another thing, did you set static IP on the server or it uses dhcp? Using static IP is preferred on a server, that way you always know what IP it has. Using dynamic can sometimes change the IP...

---

### Post by Lexion45 on 2016-02-12
Thank You darkod!
That got me right in.  I was sort of expecting somewhat of a backend control panel.
Now, off to rtfm :)
Thanks for the help

---

### Post by darkod on 2016-02-13
Linux servers by default come with a command line interface only. And it is not really recommended installing GUI interfaces although you can do it if you want to (it's your machine after all :) ).

Be assured that the command line is enough for all server administration. And we all had to learn it at some point... :)

---

