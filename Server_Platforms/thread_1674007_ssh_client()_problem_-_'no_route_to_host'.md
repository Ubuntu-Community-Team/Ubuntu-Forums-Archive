---
title: "ssh client(?) problem - 'no route to host'"
date: 2011-01-23
forum: Server Platforms
---

### Post by mistafeesh on 2011-01-23
Hi. I have an ubuntu fileserver and an ubuntu laptop both running 10.10. 

For some reason I can't connect to the server (file or remote terminal) from the laptop, even though I can access ssh through terminal on my mac and have been able to mount the filesystem on another computer running the ubuntu liveCD. I just get the error 'no route to host'. 
I've tried turning off the firewall on the laptop and re-installing ssh on both computers, but I don't have a clue what to do next!

---

### Post by CharlesA on 2011-01-23
Are you trying to connect using the hostname or ip address?

---

### Post by elico on 2011-01-23
can you ping to any host?
your route?
ip 8.8.8.8

---

### Post by mistafeesh on 2011-01-24
I'm connecting to the IP address - I have my router set up to use dhcp but reserve a specific address for the server.
I can ping the server, look at its web server in my browser, connect to a samba share and use VNC. It's just ssh from that one computer.

EDIT - now this is very weird. I physically moved the server into my office (which is further away from the router, and it uses a wireless card to connect to the network anyway) in order to plug a screen into it as it suddenly started misbehaving - not letting any computer log into anything, so I couldn't see if it was even booting up properly. as soon as I did this - before even changing anything it al worked fine and now I can ssh from the laptop.

I haven't tried putting it back where it lives yet, but this suggests it's not a software issue I suppose. Still it's pretty weird and I obviously can't trust it to not all fall apart randomly. Any ideas what could be causing this?

---

### Post by mistafeesh on 2011-01-24
merde, I spoke too soon. I can login with remote terminal now, which I couldn't before, but I still can't mount the server via ssh - I get DBus.Error.NoReply

---

### Post by GeekUnder on 2011-01-24
Sounds like something on the laptop is blocking the connection, check if you can connect to outbound port 22 at [http://port22.icannotconnect.com/](http://port22.icannotconnect.com/)

---

### Post by mistafeesh on 2011-01-25
That test doesn't seem to do anything... Just sits there once I've clicked 'start test'... I might be being daft but wouldn't the firewall on my router stop that working?

I can now (without having made any changes, somehow) ssh remote login from the client laptop, and I can ssh remote login into the laptop from the server, but even when remotely logged in I can't connect to the ssh file server.

eg I type 'ssh 192.168.0.2' into a terminal and it asks for my password and logs me in. I then go to the Places menu, click 'Connect To Server'. In the dialogue that comes up I select 'server type' as SSH, enter 192.168.0.2 into the 'Server' field and put 'dan' in the username field. This results in the error > DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

Am I doing anything wrong? I booted from a liveCD and this worked as soon as the network was recognised.

---

### Post by mistafeesh on 2011-01-26
I'm worried this may be part of a larger issue. I get a lot of problems with my network - samba problems, losing contact with my server entirely, internet connection dropping, etc. I just use a standard netgear DG834g router and on the network there is:
a G4 mac running osx 10.4
an ubuntu laptop running version 10.10
a windows 7 laptop which my kids use for homework and the internet and not much else
a PC running ubuntu 10.10 which has become my server. It runs a web server (lamp stylee) and file server - appletalk, samba, ssh... It is running headless although it currently still boots into the gnome desktop. I'll change this when all the other stuff is sorted! It [the server] has a USB wifi dongle for the network...

EDIT - I reckon it's the wifi dongle. I plugged the server into a keyboard mouse and screen today and noticed that it kept dropping the connection. It'll take a bit of reorganising but I'm going to try plugging it into the router with a good ol' fashioned ethernet cable! Just decided to move house too, so I think I'll limp along like I am for now and then try and sort this all out after the move...

---

### Post by mistafeesh on 2011-02-08
Right, it's plugged in with a proper cable now, and all the other issues are sorted. I've also installed ubuntu on the other laptop (with wubi). I *can* connect with the new ubuntu installation but I still can't with the one I use. At the moment I'm just using samba to share the files I need to, but I'd rather get ssh set up, what with file permission on test websites etc.

---

### Post by CharlesA on 2011-02-08
What's the error you get when trying to connect?

---

### Post by mistafeesh on 2011-02-10
If I try to connect with the IP address it's > Cannot display location "sftp://dan@192.168.0.2/"
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

If I try to connect with the server name it's > Cannot display location "sftp://dan@ubuntuserver/"
ssh program unexpectedly exited

---

### Post by CharlesA on 2011-02-11
Try connecting like this:

Open a terminal and type:

```
sftp dan@ubuntuserver
```

---

### Post by mistafeesh on 2011-02-11
I get this > ssh: connect to host ubuntuserver port 22: Connection timed out
Couldn't read packet: Connection reset by peer

---

### Post by CharlesA on 2011-02-11
That normally means that sshd is not running or the firewall is blocking access.

Try this:

```
service ssh status
```

If it's not running, run this:

```
sudo service ssh start
```

---

### Post by mistafeesh on 2011-02-16
Hi, I wasn't sure which computer you were suggesting I check with this, so I ran it on both...
On the server  the status check gives 'ssh start/running, process 792' and on the client it gives 'ssh start/running, process 894' 

I can use the ssh remote terminal - it's only the ssh file server I can't connect to, and it's only that one client with the problem...

---

