---
title: "PostGreSQL:"
date: 2010-01-08
forum: Server Platforms
---

### Post by WitchCraft on 2010-01-08
I have a problem configuring my PostGreSQL server for internal network access.

I want to be able to access my postgre server from 192.168.1.10

It works when I set listen_address to *, but if I input 192.168.1.10, or any other IP address, I always get:
> 
WARNING:  could not create listen socket for "192.168.1.10"
FATAL:  could not create any TCP/IP sockets


postgresql.conf section
```

listen_addresses = '*'		# what IP address(es) to listen on;
					# comma-separated list of addresses;
					# defaults to 'localhost', '*' = all
					# (change requires restart)
port = 5432				# (change requires restart)
max_connections = 100			# (change requires restart)
# Note:  Increasing max_connections costs ~400 bytes of shared memory per 
# connection slot, plus lock space (see max_locks_per_transaction).
#superuser_reserved_connections = 3	# (change requires restart)
unix_socket_directory = '/var/run/postgresql'		# (change requires restart)
#unix_socket_group = ''			# (change requires restart)
#unix_socket_permissions = 0777		# begin with 0 to use octal notation
					# (change requires restart)
#bonjour_name = ''			# defaults to the computer name
					# (change requires restart)

```

---

### Post by bodhi.zazen on 2010-01-09
See if this link helps you =)

[http://keith.dev-x.net/2008/02/01/SettingUpPostgreSQLForExternalAccess.aspx](http://keith.dev-x.net/2008/02/01/SettingUpPostgreSQLForExternalAccess.aspx)

---

### Post by BkkBonanza on 2010-01-09
You can't listen on an IP on another machine, only on your machine. The listen statement doesn't deny users from a certain place, it determines what address you will listen on. So it should be your own IP address on the LAN. You can find this from ifconfig.

To stop connections from an address other than 192.168.1.10 you either need to add a firewall rule or edit the /var/lib/pgsql/data/pg_hba.conf file to control access.

See here,
[http://www.cyberciti.biz/faq/postgresql-remote-access-or-connection/](http://www.cyberciti.biz/faq/postgresql-remote-access-or-connection/)

You would need the following if only one ip can connect,

host all all 192.168.1.10 255.255.255.255 trust

and in your conf file,

tcpip_socket = true

---

### Post by WitchCraft on 2010-01-09
> **bodhi.zazen said:**
> See if this link helps you =)

[http://keith.dev-x.net/2008/02/01/SettingUpPostgreSQLForExternalAccess.aspx](http://keith.dev-x.net/2008/02/01/SettingUpPostgreSQLForExternalAccess.aspx)

Unfortunately not.
I've already set up the necessary lines in pg_hba.conf.
And I can access the database, so they work.

But as soon as I change listen_addresses = '*'  
to listen_addresses = 'localhost, 192.168.1.10'
or only  listen_addresses = '192.168.1.10' then I get the error message.

And I'm not very comfortable with *

---

### Post by WitchCraft on 2010-01-09
> **BkkBonaza said:**
> You can't listen on an IP on another machine, only on your machine. The listen statement doesn't deny users from a certain place, it determines what address you will listen on. So it should be your own IP address on the LAN. You can find this from ifconfig.

To stop connections from an address other than 192.168.1.10 you either need to add a firewall rule or edit the /var/lib/pgsql/data/pg_hba.conf file to control access.

See here,
[http://www.cyberciti.biz/faq/postgresql-remote-access-or-connection/](http://www.cyberciti.biz/faq/postgresql-remote-access-or-connection/)

You would need the following if only one ip can connect,

host all all 192.168.1.10 255.255.255.255 trust

and in your conf file,

tcpip_socket = true


But I cannot connect anymore if I change it back to localhost.
I think it rather looks like a permission problem.
In my opinion, the postgres user might not have permisson to open tcp/ip sockets. Is that possible ?

---

### Post by BkkBonanza on 2010-01-09
You don't change it to localhost. That's not what I said.
You change it to your system's external IP, like 192.168.1.104 or whatever it is.
This IP is on your network, localhost is not.

You CANNOT listen on an IP that isn't bound to your machine. If 192.168.1.10 is another machine it's impossible to listen on it. You can connect to it but not listen.

If you only have one network card in your machine then * is as good as using the interface's assigned IP. * doesn't mean any more than "every" and you only have one in that case.

It's /var/lib/pgsql/data/pg_hba.conf that restricts access, not the listen directive.

It's not a permission problem because for a program to bind to any port below 1024 it needs to be root and that's not the error message you got. You got an error saying that you tried to bind to an IP that is not even on your own machine.

There is a difference between listen ON and listen TO. You listen ON your machine TO the other machine.

---

### Post by WitchCraft on 2010-01-09
> **BkkBonaza said:**
> You don't change it to localhost. That's not what I said.
You change it to your system's external IP, like 192.168.1.104 or whatever it is.
This IP is on your network, localhost is not.

You CANNOT listen on an IP that isn't bound to your machine. If 192.168.1.10 is another machine it's impossible to listen on it. You can connect to it but not listen.

If you only have one network card in your machine then * is as good as using the interface's assigned IP. * doesn't mean any more than "every" and you only have one in that case.

It's /var/lib/pgsql/data/pg_hba.conf that restricts access, not the listen directive.

It's not a permission problem because for a program to bind to any port below 1024 it needs to be root and that's not the error message you got. You got an error saying that you tried to bind to an IP that is not even on your own machine.

There is a difference between listen ON and listen TO. You listen ON your machine TO the other machine.

Ah, localhost listens on 127.0.0.1, I had to change it to 192.168.1.4, then it worked. I think I'll change it back to * in this case.


Understood, ON vs. To. Thanks !

---

