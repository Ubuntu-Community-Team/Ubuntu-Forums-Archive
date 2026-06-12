---
title: "Web server"
date: 2009-05-19
forum: Server Platforms
---

### Post by davidho on 2009-05-19
hi i hope i am in the right place for the help i need
i am currenty running windows vista with xammp and my email server and sql server
i have my modem conected to my router and have set the router to forward all the standard ports for web hosting to my windows server
now i dont want to convert my windows server but would like to add a linux server
one of the resons i want to add a linux server is so i can use front page extions
i run a few domains some free though dyndns and some paided for on namecheap.com
at the moment there all running to my windows server 
now i could build the linux server and set it on none standard ports and set the router to send the none standard port request to the linux server but dont rely want to do that
is there a way to have one of the server set that if the site is not hosted on it to look at the other server for the site
i have read a bit about proxy but it just confused me
also i dont have a static ip so i have software running on my windows server that updates my ip address to the dns 
so is there an app that i could install on the windows or even an app that would do it from linux 
 
Thanks David
[http://www.davidscomputers.co.uk](http://www.davidscomputers.co.uk)

---

### Post by ActiveFrost on 2009-05-19
You have 2 servers and you want "someone" to verify, which one is currently online ? That's pretty insane as you can't verify 2 servers from the thin air - you need a base server which will do that for you ( in other case, you will need to use one of your boxes as a default one, though, it should always be online ).

---

### Post by dmizer on 2009-05-19
If you're dead set on using two separate boxes to host two separate web servers, you have two choices.

1) Configure a firewall for forwarding rules according to domain and put it between your router and your webservers. This would require one of three physical configurations: a virtual machine, a third server, or placing the linux webserver box between the router and your Vista box.

2) Rather than using non-standard ports, do what most places do when they have more than one web server. Use port 80 for one server and port 8080 for the second.

A word of warning: xampp is meant primarily for development, not production. Since it's a compact version of apache, it doesn't have all the security tools necessary for a live server. From their [website](http://www.apachefriends.org/en/xampp.html):
> The philosophy behind XAMPP is to build an easy to install distribution for developers to get into the world of Apache. To make it convenient for developers XAMPP is configured with all features turned on.

The default configuration is not good from a securtiy point of view and it's not secure enough for a production environment - **please don't use XAMPP in such environment.**

They do say that since version 0.9.5 you can make xampp secure by calling /opt/lampp/lampp security, but I would still strongly advise against using xampp as a live server.

---

### Post by ActiveFrost on 2009-05-19
> **dmizer said:**
> If you're dead set on using two separate boxes to host two separate web servers, you have two choices.

1) Configure a firewall for forwarding rules according to domain and put it between your router and your webservers. This would require one of three physical configurations: a virtual machine, a third server, or placing the linux webserver box between the router and your Vista box.

2) Rather than using non-standard ports, do what most places do when they have more than one web server. Use port 80 for one server and port 8080 for the second.

A word of warning: xampp is meant primarily for development, not production. Since it's a compact version of apache, it doesn't have all the security tools necessary for a live server. From their [website](http://www.apachefriends.org/en/xampp.html):


They do say that since version 0.9.5 you can make xampp secure by calling /opt/lampp/lampp security, but I would still strongly advise against using xampp as a live server.

And it loves to say "sorry" ( crashes all the time - not sure if it's my PC or xampp but haven't seen anything similar in lamp or windows manual apache webserver ).

---

