---
title: "Ubuntu Server - general questions"
date: 2005-08-02
forum: Server Platforms
---

### Post by Mr. Electric Wizard on 2005-08-02
Hello everyone,
I just came upon an old pc that I am trying to figure out what to do with...
I am leaning towards replacing my Microsoft router with a gigabit switch, and handing over all of the router functionality (firewall, dhcp, port forwarding, etc.) to a Ubuntu server with two nics.

First off, how should I go about doing this?
Should I do a Server install with one nic connected directly to my cable modem, get it configured correctly, then install the second one?

I might eventually install Apache on this machine also...
I'm guessing that any Intel Nic should be able to be configured under Ubuntu (that's what I'm using now, and have had no problems).

---

### Post by LordHunter317 on 2005-08-02
Put both NICs in.  Connect the server to the cable modem, get it and only it talking over the Internet.

Then setup NAT.  Then add filtering plus any services you want.

---

### Post by Mr. Electric Wizard on 2005-08-02
Do you know if you can configure NAT with shorewall?

And, when you say to get the server and only the server talking to the internet, do you mean to connect the server to the internet, and to the switch (that connects to the rest of the network) and see if the computers behind the switch can talk to the internet or not?

---

### Post by LordHunter317 on 2005-08-02
[QUOTE=Mr. Electric Wizard]Do you know if you can configure NAT with shorewall?[/quote]Yes, but I don't know how.

And, when you say to get the server and only the server talking to the internet, do you mean to connect the server to the internet, and to the switch (that connects to the rest of the network) and see if the computers behind the switch can talk to the internet or not?[/QUOTE]Just the first part.

---

### Post by Mr. Electric Wizard on 2005-08-02
I just thought of something else also, I won't be needing gigabit nics in the server, because it will be the gateway, and Cable has an upper limit of 5 megabit.
I guess I'll get to save a little cash... :)

---

### Post by nocturn on 2005-08-03
There are specialized distributions out there for the thing you want to do (like IpCop).  They are preconfigured for routing/firewall/...

But you can do that with any distro off course.

---

### Post by Mr. Electric Wizard on 2005-08-03
Thanks nocturn, I didn't realize that IPCop was a linux distro.
I always thought it was just a program.

---

### Post by h4rdwire on 2005-08-04
[QUOTE=Mr. Electric Wizard]I just thought of something else also, I won't be needing gigabit nics in the server, because it will be the gateway, and Cable has an upper limit of 5 megabit.
I guess I'll get to save a little cash... :)[/QUOTE]

Well you could do that, but by getting a decent gigabit switch you could have a "Gigabit LAN" which is also pretty nice especially if you do a lot of file transfers, gaming, or beta testing new weaknesses etc etc.

hmm i hope i'm not stealing but, if i set up ubuntu as the server to a switch and from switch uplink to a wifi AP, it should work properly correcT?

---

### Post by Mr. Electric Wizard on 2005-08-04
Actually that is my plan, I just meant that my Firebox (IpCop) doesn't nee two gigabit Nics.  The Firebox LAN Nic (the green card) will be connected to a Gigabit LAN, for File Transfers around the network.

Finally the price is starting to come down on the Gigabit stuff! :)

---

