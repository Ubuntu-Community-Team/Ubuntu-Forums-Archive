---
title: "Mysql hostname resolve problem"
date: 2011-02-02
forum: Server Platforms
---

### Post by yd290276 on 2011-02-02
Hi all,
first sorry for my bad english, i'm french and so not very english fluent.

I've setup a little LAN at home :
> One media-center runnin W7 and running ubuntu server 10.10 in a VM
> One DLINK DIR-655 router with DHCP enabled
> Two or more laptops

On the server i mainly had installed :
> Samba with wins enable
> Apache 2
> Mysql 5.1
> Some web tools like webmin, phpmysqladmin, drupal etc...

**_There is my problem :_**
I can ping every computer with its netbios name, so the media-center is called 'linux-server', then i can do a "ping linux-server" or connect to its web sites within any web browser and type in the url "http://linux-server/mywebsite".
All that stuff works perfectly !

But, when i try to connect to my Mysql server from my laptop with soft like "mysql workbench tools", it returns an error saying "Host 192.168.0.105 not allowed to connect to the mysql server".
(192.168.0.105 is the LAN IP of my laptop named house-yann)

Of course, in mysql i've granted all access to root@house-yann. But what i don't understand is why mysql translate my laptop name into an IP ?

Does any one has an answer or can tell me if this problem is due to mysql or my ubuntu server config ?

In addition i've setup nsswitch.conf to have WINS support and so resolve host name : "host : wins host dns".

Thank you !

---

### Post by rudelgurke on 2011-02-02
Hello,

vôtre anglais est très bon - bien sûr :)

About your problem - did you maybe set:

skip name resolve ([http://dev.mysql.com/doc/refman/5.0/en/server-options.html#option_mysqld_skip-name-resolve](http://dev.mysql.com/doc/refman/5.0/en/server-options.html#option_mysqld_skip-name-resolve))

in your my.cnf ?

If so, maybe consider using IP's instead of hostnames. if you rely on hostnames, MySQL will have an additional DNS lookup for connections which is bad for performance.

---

### Post by yd290276 on 2011-02-02
Hello and thank you for my very good english talking :-)

Can you tell me how i can set --skip-name-resolve in my.cnf ? I tried several ways to achieve this but without success :

in my.cnf, set variable "skip_name_resolve=ON"
--> mysql server never restart and command "sudo service mysql restart" don't return.

in /etc/init/mysql.conf startup-job tried to set "exec /usr/sbin/mysqld --skip-name-resolve"
--> when checking with "sudo mysqladmin variables" the variable skip_name_resolve is still sets to "OFF".

Thank you !

---

### Post by yd290276 on 2011-02-02
i forgot to add that i really don't want to deal with IP because i want to use DHCP.

---

### Post by rudelgurke on 2011-02-02
If you want to set, setting:

skip_name_resolve

in my.cnf does the job without any ON / OFF switches. Leaving out the setting enables it.
Checking it on runtime is also possible:

show variables like "skip_name_resolve";

Anyways - maybe set it in my.cnf or on the next upgrade your modified init script will be replaced. ;)

EDIT: If you don't want to deal with IP's - setting:

192.168.0.%

also works. And if you still want to rely on DNS, just remove the "skip_name_resolve" and check it with the show variables command from above if it's on or off.
If it's on:

Checking ps auwx | grep mysql will show if a script (like mysqld_safe) still sets the variable or checking your MySQL configuration files (my.cnf etc.) if the setting is set somewhere.

---

### Post by yd290276 on 2011-02-02
hey ! find how to set --skip-name-resolve in my.cnf (what a clever man ;)

But bad news, this doesn't work and change nothing... always getting same error "host 192.168.0.105 is not allowed to connect to this mysql server"

Does it really can't work with WINS ?

---

### Post by yd290276 on 2011-02-02
sorry, i answer too fast, i didn't read your previous answer.
So when i set --skip-name-resolve, it was "ON", but mysql still saying that it doesn't allow 192.168.0.105 to connect.

I want to tell it house-yann (192.168.0.105 IP) is allowed. By the way, i haven't DNS server. DHCP leases are given by my DLINK DIR-655 router and of course it doesn't provide any DNS software...

Maybe i'll set 192.168.0.% to allow all network machine to be allowed to connect to this mysql server, but i think it's not very secure.

---

### Post by rudelgurke on 2011-02-02
Oh - MySQL will use the DNS server set in /etc/resolv.conf to resolve names, it also tries to resolve local names.
If you don't run your own DNS, these names should never resolve to anything and so the connection will fail, if you rely on DNS names instead of IP's.

If you don't want to use 192.168.0.% to open it for your entire local network, either setup a local DNS server that gets it's addresses from your DHCP - doubt your Dlink will allow this - or setup your Dlink to give the hosts you want to connect to MySQL a static IP.
That's maybe the best solution that doesn't require any additional setups like a local DNS (and refreshing your Zones with your IP's from the DHCP).

If you just want to allow one IP to connect:

CREATE USER 'example'@'192.168.0.105' IDENTIFIED BY 'secret_password';
GRANT ALL ON *.* TO 'example'@'192.168.0.105' WITH GRANT OPTION;
FLUSH PRIVILEGES;

This will create a new Admin user that can connect from 192.168.0.105 - and only from there. Just setup the privileges to match your needs.

---

### Post by yd290276 on 2011-02-02
you are really helpfull !

1) i con confirm that my dlink router is completely unable to give DHCP adresses. Maybe a cisco router but not the same price and not really helpfull for a little home LAN ;)

2) i've already set my dlink router to set "statics" IP (by setting adresses reservation, but... it is doing that with MAC adresses, not completely reliable, but it works)

My first idea was to grant access to 192.168.0.105, but i think it was "quick and dirty". I believe this is the only one solution in my case.

Thank you very much for your help ! No Cisco router to sell ? ;)

---

### Post by rudelgurke on 2011-02-02
> **yd290276 said:**
> Thank you very much for your help ! No Cisco router to sell ? ;)

Let me look what such a thing costs. Then I'll sell you one ;) :D

Of course I'll add some euro's :p

Et, peut-être vous savez, nos européennes sont très serviable ;)

---

### Post by yd290276 on 2011-02-02
oh ! i'm really not a network expert, so i'm even not able to find a router that has an integrated DNS server (with wifi).

Do you know some models, just for the "fun" of the price (cisco routers go from 1000 to more than 10 000€, but some are under 600€)

---

### Post by yd290276 on 2011-02-02
just to close this thread : cisco routers are really to heavy to configure (i've just read some tutorials on how getting it to run).

==> static IP's power :-)

Thank again for your help !

---

