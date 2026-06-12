---
title: "sql-ledger"
date: 2005-11-30
forum: The Cafe
---

### Post by phil123 on 2005-11-30
Hi, I wonder if someone could give a pointer here. I installed sql-ledger via synaptic packages. It downloaded and installed fine, but I dont know how to use it after that. There is no icon or launcher. It says that it is for invoicing and other business tasks and I just want to see if I can make use of it. 
Thanks!!

---

### Post by ember on 2005-11-30
If I am correct (I used only Lx-Office, a fork of sql-ledger) then there will not be an icon or program, because you have to run it on a webserver. Basically you just register Perl-Skripts for execution outside CGI-bin and put a few other directives into your apache2.conf.

Then you can access it via [http://your.web.server/path.where.you.installed/](http://your.web.server/path.where.you.installed/)

Best,
ember

---

### Post by mykrob on 2005-11-30
on my Suse box, sql-ledger is accessed via browser by

[http://localhost/sql-ledger/login.pl](http://localhost/sql-ledger/login.pl)

to access from outside, it would be

[http://my.ipaddress/sql-ledger/login.pl](http://my.ipaddress/sql-ledger/login.pl)

of course, if you have a router or firewall, you will need to forward port 80 to the sql-ledger machine to access it from any machine other than the local one(s)

---

### Post by phil123 on 2005-11-30
Great. But now I did the same thing with GnuChess and once it downloaded it just dissapeared into the system. I managed to find thi icon deep down in a directory somewhere but it doesnt open the program. Im itching to play chess.
Phil

---

