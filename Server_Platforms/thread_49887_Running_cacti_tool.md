---
title: "Running cacti tool"
date: 2005-07-18
forum: Server Platforms
---

### Post by kikoga on 2005-07-18
Hi all,

I have installed cacti and all of its dependancies (see apache, mysql server, net smnp, rrdtools...) using Synaptic tool.

I had cacti under /usr/share/cacti so I made a synbolic link under /var/www so as to see cacti in [http://localhost/cacti](http://localhost/cacti). First off I had some problems with the mysql database, so I had to edit /usr/share/cacti/include/config.php according to the cacti user (my usual user), password (new password) and database name. All this parameters were introduced while the packets were being configured by synaptic.

Finally, I had to use the cacti.sql file to replace the mysql database with the one provided by cacti developers.

Now cacti is running, but I am asked for a login, and none of the user/passwd I introduced work.
I have taken a look at the oficial FAQ and actually made a post in the official forum. The tips on the faq related to the login matters do not work. See:

 I have forgotten my 'admin' password to Cacti, how do I reset it?

To reset the admin account password back to the default of 'admin', connect to your Cacti database at the command line.

shell> mysql -u root -p cacti

Now execute the following SQL:

mysql> update user_auth set password='21232f297a57a5a743894a0e4a801fc3' where username='admin';


I did that and then tried to login but I still couldnt log in. I dont know what to do and I still need cacti for personal reasons.

I hope anyone can help me setting it up in Ubuntu. It first seem so easy... :P

See you. Thanks in advance.

---

### Post by LordHunter317 on 2005-07-18
[QUOTE=kikoga]I had cacti under /usr/share/cacti so I made a synbolic link under /var/www so as to see cacti in [http://localhost/cacti](http://localhost/cacti).[/quote]You shouldn't have had to do this.  I don't remember having to do this, with Apache2 on Debian anyway.  

You may have to for Apache 1.3.  But instead of using a symbolic link, edit your Apahce configuration and use an alias instead.

> I did that and then tried to login but I still couldnt log in. I dont know what to do and I still need cacti for personal reasons.Any errors?  Messages?  If you change the PHP logging level, do you get any output?  Anything in the Apache error_log?

---

### Post by kikoga on 2005-07-19
[QUOTE=LordHunter317]You shouldn't have had to do this.  I don't remember having to do this, with Apache2 on Debian anyway.  

You may have to for Apache 1.3.  But instead of using a symbolic link, edit your Apahce configuration and use an alias instead.

Any errors?  Messages?  If you change the PHP logging level, do you get any output?  Anything in the Apache error_log?[/QUOTE]
 Log in problem has been solved. I was asked a password when I bruteforced the index.php and now I can log in normally.

I have some graphics going on but when I am modifying the devices in cacti I see a *BAD* message: SNMP not in use.

It is true because I am trying to see a graph of my bandwidth but it doesnt appear. The other ones (such as process, cpu load etc) are just ok. I have created a file unde /etc called snmpd.conf and filled it with the lines I saw in the cacti faq:

syslocation HOME
syscontact "xxxx @ yyy"

# auth
rocommunity public

# disk monitoring
disk /



Another thing I do not understand is how to make this graphs available for everyone. There's a guest account but there is no way to view the graphs directly as in mrtg?

Thanks for all :)

---

