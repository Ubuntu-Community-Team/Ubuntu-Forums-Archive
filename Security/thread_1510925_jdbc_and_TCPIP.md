---
title: "jdbc and TCP/IP"
date: 2010-06-16
forum: Security
---

### Post by iammyr on 2010-06-16
Hi,
I'm experiencing problems with my jdbc connector (the last one available, but it's the same using previous versions) for mysql 5.1.41 (the last one available too) on sun-java-6 vm, while everything works fine if I connect with the same username and password, from the same host, by mean of the mysql application (bin/mysql -u usernam -h hostname -p) or phpmyadmin; and no-exception is thrown if I run the same java code on other machines. These problems came up suddenly yesterday after updating some libraries as suggested by my update manager notification  (everything worked fine before that).

I've read that jdbc uses TCP/IP to connect to mysql instead of the mysql application that uses UNIX sockets, then to find out the cause of my exception ( com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure ) 
I would know which is the best way to monitor TCP/IP communications in Ubuntu 10.04 so that I could use such logs to better debug my application.

Thanks a lot in advance
to anyone who would be sooooo kind :) to help me 
myriam

---

### Post by yeleek on 2010-06-16
wireshark imo is the best way to monitor traffic, however it will produce a lot of information so need to be prepared to filter it down then to the data you require.

Wireshark is in the ubuntu repositories - and heres the user guide
[http://www.wireshark.org/docs/wsug_html_chunked/](http://www.wireshark.org/docs/wsug_html_chunked/)

---

### Post by iammyr on 2010-06-16
Hi yeleek,
thanks a lot for your answer ;)
Now I'm using wireshark but filtering communications by mean of my own static ip address or by mean of the port number 3306 didn't solved my issue regarding jdbc: when I run my java application and get that connection refused exception, no communication is catched up by wireshark...

I've tried to catch something setting the parameter bind-address into mysql/my.cnf file either as my static ip addres or as localhost or as 127.0.0.1 but nothing get catched by wireshark...

(i've tried also setting jdbc to connect to 127.0.0.1:3306, localhost:3306, 127.0.0.1, localhost, staticIp:3306, staticIp)

...maybe if someone has some other suggestion...thanks a lot :(

---

### Post by yeleek on 2010-06-16
No info captured by wireshark?

Try running it from terminal via

sudo wireshark

Select the relevant interface (eth0 for example)

Once main window appears, it should automatically start capturing

click in textbox next to the filter button

and enter

ip.addr == 192.168.60.6

192.168.60.6 being the ipaddress of machine you want to filter on

then run your test.

---

### Post by iammyr on 2010-06-16
Hi
thanks yeleek! :)
However in my previous post I meant that nothing get catched by wireshark "when I try to open my jdbc connection", in every other moment it catches something even while filtering by mean of my static ip address ;)
However I've tried to run wireshark and open my jdbc connection on another machine where that jdbc connection works fine, and wireshark doesn't catch it neither there..so maybe it doesn't catch connections from a machine to itself...I don't know :p

---

### Post by yeleek on 2010-06-16
Sure the port is right?

Try netstat i.e. something like

```
netstat -enp > /tmp/netstatresults
```

and then to view

```
more /tmp/netstatresults
```

you are after the Active Internet Connections (at the top), will show you what connections on what ports you have to what addresses.  Will also show you the applications responsible, will work on local too.

---

### Post by yeleek on 2010-06-16
I may have been very stupid, have you opened a port on the machine firewall for this?  I presumed you had...........

---

### Post by iammyr on 2010-06-16
Hi! I have no firewall running ;)
my troubles with jdbc stop rising up....and I really don't understand why, unfortunately...otherwise I could have helped someone else having that same exception thrown (it's very common).

I'm sorry to have bothered you and thanks a lot again ;)

---

