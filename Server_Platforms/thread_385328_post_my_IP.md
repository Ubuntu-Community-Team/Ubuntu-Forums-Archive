---
title: "post my IP?"
date: 2007-03-15
forum: Server Platforms
---

### Post by finer recliner on 2007-03-15
so i've set up ftp server and ssh server on my comp to occasionally get files and whatnot from my comp when away from it. however, at my school, they use DHCP servers to assign IPs and everytime i reboot my comp, its more than likely that i get a new IP address. I dont want to constantly check my IP address and try to memorize each time.

so i had the idea of writing a short perl script that would find my IP address everytime i boot up and upload the result as text file to my website (i.e [www.mydomain/ftp.txt](www.mydomain/ftp.txt)) so i will always know what my IP address is when away from the computer.

are there any risks associated w/ posting my IP address like that?

---

### Post by BeachBum on 2007-03-15
There will always be some risk if its in plain text.  

A much safer way to do what you're seeking is to sign up for a free dynamic dns service (dyndns.com is what I use).  Basically, it links a web address (whatever.whatever.com) to your ip address.  Since your ip address is dynamic, you create a script on your server computer to capture your current IP and update your dynamic dns account.  If your server is behind a router, check the router docs to see if it has this functionality.  Read more here:

[http://www.ubuntuforums.org/showthread.php?t=247563&highlight=dyndns+static+ip]("http://www.ubuntuforums.org/showthread.php?t=247563&highlight=dyndns+static+ip")

---

### Post by Frosty Cold Drink on 2007-03-15
> **finer recliner said:**
> so i've set up ftp server and ssh server on my comp to occasionally get files and whatnot from my comp when away from it. however, at my school, they use DHCP servers to assign IPs and everytime i reboot my comp, its more than likely that i get a new IP address. I dont want to constantly check my IP address and try to memorize each time.

so i had the idea of writing a short perl script that would find my IP address everytime i boot up and upload the result as text file to my website (i.e [www.mydomain/ftp.txt](www.mydomain/ftp.txt)) so i will always know what my IP address is when away from the computer.

are there any risks associated w/ posting my IP address like that?

Its not that big of a deal, no. You'll likely want to try something like DynDns.org though. Its easier.

---

