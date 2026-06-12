---
title: "can't connect to mysql"
date: 2005-11-28
forum: Server Platforms
---

### Post by fm1234 on 2005-11-28
I've a default mysql install which works fine when I connect locally to it. I'm also trying to access it from a windows machine through ODBC. However I get an ODBC error "Can't connet to mysql on 'server' (10061)".

I checked nestat an I got:

tcp        0      0 localhost.localdo:mysql *:*                     LISTEN

Does it mean that mysql only listens to localhost requests?? 

TIA,
Fernando

---

### Post by kairu0 on 2005-11-28
Did you install the mysql ODBC driver and set up your specific tables in ODBCConfig?

---

### Post by heftigrat on 2005-11-28
Maybe this is a dumb question, but are you behind a firewall?  Try connecting the 2 machines (server and client) directly with a crossover cable (or a switch or hub), put them both on the same private subnet and see what happens (one thing you can try is telnet over the proper mysql port and see if you get a response other than an immediate refusal).  I don't know anything about anything, but based on:

"tcp 0 0 localhost.localdo:mysql *:* LISTEN"

...it looks like your machine is listening on the mysql port for any connection from a remote host over any source port (*:*).  But like I said, I don't know anything about anything.

---

### Post by LordHunter317 on 2005-11-28
No, your server is only listening on localhost.  That's why it can't connect.  You need to edit /etc/mysql/my.cnf and change the appropriate parameter (you'll see it, I forget off hand) to let it listen on all interfaces.  Then restart mysql.

---

### Post by fm1234 on 2005-11-29
Thanks LordHunter317,

it is bind-address. The manual is too brief ("address to bind to") .This parameter indicates which network address will be used by mysql to receive requests. I don't know what will mysql do without this parameter set.

Regards,
Fernando

---

### Post by dudus on 2005-11-29
try acces it trought telnet to check if it is a firewall issue

---

### Post by LordHunter317 on 2005-11-29
[QUOTE=fm1234] I don't know what will mysql do without this parameter set.[/QUOTE]Killing it ought to cause it to listen on all interfaces.

---

### Post by J.C. Denton on 2005-11-30
[QUOTE=fm1234]Thanks LordHunter317,
I don't know what will mysql do without this parameter set.[/QUOTE]
I think it will still bind to localhost.  To disable networking, you'd need to include the "skip-networking" directive.

---

### Post by heftigrat on 2005-12-01
[QUOTE=dudus]try acces it trought telnet to check if it is a firewall issue[/QUOTE]

That's what I thought too (see my previous post).  ;) 

It seems these guys know what they're talking about though as far as what port mysqld listens on by default.

---

### Post by dudus on 2005-12-01
I had an issue trying to access mysql trought php with the socket. When you connect to the localhost the php connector try to get it trought the mysql.sock file. But he couldn't find thi in my system.

Althoght if you connect to 127.0.0.1 witch of course is the same machine it tries the port instead of the sock. 

But I don't know if ODBC looks like this anyway.

---

### Post by heftigrat on 2005-12-02
when dealing with accessing a server over a network, sockets can only act as an abstraction for binding an ip with a port, so essentially t/s-ing from the perspective of TCP/IP sockets specifically only serves to generalize the issue and not get to the root of the problem.  when referring to sockets as in inter-process communication, you are again taking the TCP/IP aspect out of the equation.

dudus, could you please clarify your post?

---

### Post by fm1234 on 2006-01-28
for the sake of completeness of this thread, commenting out the parameter bind-address in /etc/my.cnf allows mysql to receive connections from any IP.

Cheers,
Fernando

---

