---
title: "Apache2 multiple processes"
date: 2009-11-02
forum: Server Platforms
---

### Post by cowguru2000 on 2009-11-02
Hi everyone,

I use an Apache 2 server. I am having trouble with it; I essentially can't access my website. I think this may be due to two or more conflicting apache2 processes, because when I killall all the apache2 processes and then enter sudo /etc/init.d/apache2 start, once the server is started I can view my site just fine.
Obviously I can open up the command line, killall to the apache2 processes, and then restart apache2 every time I boot up my computer, but that would be irritating, and more importantly that wouldn't solve the problem.

Any help would be MUCH appreciated.

Thanks,
-Joe

---

### Post by will81 on 2009-11-02
It doesn't really help you solve your problem, but I think it's pretty normal for Apache to have several processes running.  As I understand it, they're "helper" processes - the busier your site is, the more processes Apache launches to deal with the demand.  My very lightly loaded server currently has 11 such processes.

---

### Post by Lars Noodén on 2009-11-03
You can stop them all:
sudo /etc/init.d/apache stop

See the various run time directives StartServers, MinSpareServers, MaxSpareServers, and MaxClients.  These can be used to set upper and lower bounds for the number of processes and the connections.

[http://httpd.apache.org/docs/2.2/mod/mpm_common.html](http://httpd.apache.org/docs/2.2/mod/mpm_common.html)
[http://httpd.apache.org/docs/2.2/mod/prefork.html](http://httpd.apache.org/docs/2.2/mod/prefork.html)

The busier your site is, the more processes you need in order to serve client requests.  If it's just you and your dog, then you can get by with very few and save some RAM.

---

### Post by neonas on 2009-11-03
I have this problem with apache2 configuration. I have installed mambo and I don't know how to configurate redirect. To access mambo I use my ip\mambo insted I wont to access it like this: my ip\blabla(anything) and whe I type my ip\a it shoul redirect me to my ip\mambo\administrator\ so how to do that?
any ideas?
pls help :(

---

