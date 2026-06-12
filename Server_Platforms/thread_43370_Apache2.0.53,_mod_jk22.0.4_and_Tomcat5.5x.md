---
title: "Apache/2.0.53, mod_jk2/2.0.4 and Tomcat5.5x"
date: 2005-06-21
forum: Server Platforms
---

### Post by Ab3 on 2005-06-21
I have a server (Ubuntu 5.04 Hoary) running apache2 and tomcat5.5 up and running and also hosted. I am able to access the server through the ip and the domain name 
eg. [www.xyz.com](www.xyz.com) 

I am also able to access the tomcat and apps using tomcat.
eg. [www.xyz.com:8080](www.xyz.com:8080)
eg. [www.xyz.com:8080/app123](www.xyz.com:8080/app123)

What I would like to do is 'connect' [www.xyz.com:8080/app123](www.xyz.com:8080/app123)  to [www.xyz.com/app123](www.xyz.com/app123) so the customers dont need to type in the port 8080. I tried following steps listed on the jakarta tomcat site, and also through other sites found by googling, but to no avail . Has anyone had any success with this?

Link for the connector config from jakarta:
[http://jakarta.apache.org/tomcat/connectors-doc/howto/quick.html](http://jakarta.apache.org/tomcat/connectors-doc/howto/quick.html) 

thanks, 
Ab3

---

### Post by Enki on 2005-06-24
[QUOTE=Ab3]
Link for the connector config from jakarta:
[http://jakarta.apache.org/tomcat/connectors-doc/howto/quick.html](http://jakarta.apache.org/tomcat/connectors-doc/howto/quick.html) 
[/QUOTE]

I think your link is for older versions of Apache/mod_jk. Try the examples in /usr/share/doc/libapache2-mod-jk2/examples/

---

### Post by larry007 on 2005-07-05
Quick and dirty way is...

Create an index page inside the desired folder in Apache.  Merely create it with two frames - the top being 0 and the 'big' frame loading the actual page on port 8080 from any Jakarta folder into Apache...   :-#  No one will notice....  

Even though not every browser support frames, it is very likely to do so if it is going to support Java anyway.  Good luck!!

 \\:D/

---

### Post by coreteam on 2005-07-29
:) Take a look at  [http://jroller.com/page/coreteam/?anchor=apache2_54_tomcat5_5_9](http://jroller.com/page/coreteam/?anchor=apache2_54_tomcat5_5_9)
or 
[http://www.mini-idea.com](http://www.mini-idea.com)

Maybe it can help you

---

### Post by h4rdwire on 2005-08-02
Whats the file folders in apache2 ?.. :( i'm used to apache 2.0 with the /etc/httpd/conf/httpd.conf etc etc, and also used to RH so ... any thing will help :P

---

### Post by theQmaster on 2005-08-02
I'm not able to get the mod-jk2 installed 

1. tried sudo apt-get install libapache2-mod-jk2 
but says that there no package named like that
2. tried to compiled the latest source but it says the couldn't find the WebServer.

BTW how do I install the lastest apache 2.0.54 - do I have to wait till it's released in repositories ?

Q

---

### Post by theQmaster on 2005-08-02
I had to update my sources.list.

---

### Post by adeh on 2005-08-03
Do yo really need to use Apache and AJK?  I have a similar setup but I bypass apache, using Tomcat as the webserver. Granted, this particular application only has 2 remote users, so performance is not an issue.

In any case, I used iptables forwarding to forward all incoming traffic on port 443 to port 8443, you couls do the same with 80 and 8080. 

The exact code to do this... hold on...got it:
add the following lines to /etc/network/interfaces
[code]
# configure the port redirection that allows Tomcat to run as non-root
up /sbin/iptables -t nat -F
up /sbin/iptables -t nat -A PREROUTING -p tcp --dport 443 -j REDIRECT --to-ports
 8443
[code]

---

### Post by theQmaster on 2005-08-03
The idea using Apache comes from load balancing.
Later on I can have two tomcat instances and one apache.

Right now what I want to have tomcat dedicate to treat only dynamic request while apache2 would server, mindless, the static file. I don't want to load tomcat with unnecesary work.

---

### Post by Animus` on 2005-11-13
Hello,
Did anyone got Apache/2.0.53, mod_jk2/2.0.4 and Tomcat5.5x to work together? I tried to find this out, but without success. Help needed :) It would be great to see some howto. 
thanks!

---

