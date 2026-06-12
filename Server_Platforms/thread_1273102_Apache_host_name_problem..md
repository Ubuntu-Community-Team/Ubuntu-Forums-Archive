---
title: "Apache host name problem."
date: 2009-09-23
forum: Server Platforms
---

### Post by bayasaa on 2009-09-23
Hello

My name is Bayasaa. are you can me? I used my operation system on ubuntu-9.04. I installed apache, but now restart following message appear;

bayasaa@bayasaa:~$ sudo /etc/init.d/apache2 restart
[sudo] password for bayasaa: 
 * Restarting web server apache2                                               
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
bayasaa@bayasaa:~$ 

I can't repair its error message

Now, its how to repair. You Please help me


Regards

Bayasgalan.B

---

### Post by blackened on 2009-09-23
> **bayasaa said:**
> Hello

My name is Bayasaa. are you can me? I used my operation system on ubuntu-9.04. I installed apache, but now restart following message appear;

bayasaa@bayasaa:~$ sudo /etc/init.d/apache2 restart
[sudo] password for bayasaa: 
 * Restarting web server apache2                                               
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
bayasaa@bayasaa:~$ 

I can't repair its error message

Now, its how to repair. You Please help me


Regards

Bayasgalan.B

I'm pretty sure the domain name comes from the ServerName field in /etc/httpd/httpd.conf. I'm no apache expert though, so I could be wrong.

---

### Post by d4rk5h4dow5 on 2009-09-23
> **blackened said:**
> I'm pretty sure the domain name comes from the ServerName field in /etc/httpd/httpd.conf. I'm no apache expert though, so I could be wrong.


I get this same message.. When I look in httpd.conf It has nothing in it.. wasn't sure if I needed to add it in there or what..

I also tried fixing this issues by checking (sites-enabled / sites-available / ports.conf / apache2.conf) but nothing I set seemed to fix this error. I haven't spent a lot of time investigating just cause I have a more urgent issue with setting up virtual hosts.. But if I find something I will def let you know. Maybe i could try the above and see what happens.

---

### Post by blackened on 2009-09-23
> **d4rk5h4dow5 said:**
> I get this same message.. When I look in httpd.conf It has nothing in it.. wasn't sure if I needed to add it in there or what..

I also tried fixing this issues by checking (sites-enabled / sites-available / ports.conf / apache2.conf) but nothing I set seemed to fix this error. I haven't spent a lot of time investigating just cause I have a more urgent issue with setting up virtual hosts.. But if I find something I will def let you know. Maybe i could try the above and see what happens.

I would definitely start by specifying the ServerName in httpd.conf. A quick google should turn up the proper format. Worst case scenario, it doesn't work and you're no worse off than you already were.

---

### Post by cariboo on 2009-09-23
You are getting the error message, becuase you don't have a name aliased to the ip address in /etc/hosts. For example my internal server's name is willy, /etc/hosts looks like this:

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	willy.aplus	willy
```

---

### Post by Iowan on 2009-09-23
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache") may not be the most elegant way to fix the problem...

---

### Post by alienatom on 2009-09-23
Try editing your /etc/apache2/apache2.conf and include 

ServerName nameofserver

Replace nameofserver with whatever you want it to be.

For example, if your server name is zippy you would add this to your apache2.conf

ServerName zippy

Then just restart the server.

sudo /etc/init.d/apache2 restart

---

### Post by d4rk5h4dow5 on 2009-09-25
> **cariboo907 said:**
> You are getting the error message, becuase you don't have a name aliased to the ip address in /etc/hosts. For example my internal server's name is willy, /etc/hosts looks like this:

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	willy.aplus	willy
```

So I checked this and added something similar but after restarting the apache server it still gave the same message.. After digging around with all the host(s)* files I found that my hostname file (/etc/hostname) didn't have the .org portion of my domain.. After adding it and restarting the service it worked no more error message. Thanks for the help I think now I have all that I need to be functional. 

:)

Now on to setting up Virtual Hosts :( lol

---

### Post by Iowan on 2009-09-25
That help page link I posted has some material on virtual hosts, as well...

---

### Post by d4rk5h4dow5 on 2009-09-28
> **Iowan said:**
> That help page link I posted has some material on virtual hosts, as well...

Yeah I have been checking it out... seems like so many little fires to put out so little time hahahaha 

thanks for the help if I have any issues with Virtual Hosts I will post somethin :)

---

