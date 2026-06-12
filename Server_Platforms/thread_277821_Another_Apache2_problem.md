---
title: "Another Apache2 problem"
date: 2006-10-15
forum: Server Platforms
---

### Post by Avarus on 2006-10-15
I have installed Ubuntu Daper Drake server version on my breadbox. Apache 2 is automaticaly installed (LAMP). But when I check on a computer on the same network [http://192.168.1.1:80](http://192.168.1.1:80) , it can't find the page. Port 80 is open, there is an index.htm in /var/www. What did I do wrong (or better: what did I not do right?) ?

---

### Post by adwait on 2006-10-15
Is apache listening? Can you access the page from the same computer using that IP?

---

### Post by Avarus on 2006-10-15
> **adwait said:**
> Is apache listening? 

You mean a port is listened? Yes, 80 (default). I also opened the port in my router

> **adwait said:**
> Can you access the page from the same computer using that IP?

I don't have GUI on my server...

---

### Post by adwait on 2006-10-15
Well, I know this is a dumb suggestion, but try running nmap on the server and see if its showing the port 80 as open. Are you sure apache is running? Try
```
sudo /etc/init.d/apache2 start
```

---

### Post by Avarus on 2006-10-15
> **adwait said:**
> Well, I know this is a dumb suggestion, but try running nmap on the server and see if its showing the port 80 as open.

nmap? What is that?

---

### Post by adwait on 2006-10-15
Use
```
 sudo apt-get install nmap
nmap 192.168.1.1
```

Its a port scanning utility, it shows which ports are open on a given host.

---

### Post by Avarus on 2006-10-15
It says:

```

Nmap fnished: 1 IP adress (0 hosts up) scanned in 0.388 seconds
```

---

### Post by adwait on 2006-10-15
That means it can't find the IP address that you are trying to access. Theres no problem with apache, there's a problem with your network settings..

---

### Post by Avarus on 2006-10-15
So... do you know how to open a port?

---

### Post by Ronbo on 2006-10-15
When I scan my web server with nmap I get:

> Starting Nmap 4.10 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-10-15 11:15 EDT
Interesting ports on server (xxx.xxx.xxx.xxx):
Not shown: 1677 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
8080/tcp open  http-proxy

Nmap finished: 1 IP address (1 host up) scanned in 0.207 seconds

Did you try to restart Apache, I see someone had suggested it but I didn't see any reply saying that you did.  Give it a try and let us know what happens.

> 
sudo /etc/init.d/apache2 stop

then
> 
sudo /etc/init.d/apache2 start

---

### Post by Avarus on 2006-10-15
```
Starting Nmap 4.03 ( http://www.insecure.org/nmap/ ) at 2006-10-15 16:34 CEST
Note: Host seems down. If it is really up, but blocking our ping probes, try -P[falling from the edge of screen]
Nmap fnished: 1 IP adress (0 hosts up) scanned in 0.387 seconds
```

This is the full message I got. I tried restarting Apache multiple times already (everything going ok), but still no access...

---

### Post by adwait on 2006-10-15
Basically the computer you are trying to access the server from can't see the server. hence the problem. Why it can't see it would require more info about the network. How are the computers connected?

---

### Post by Avarus on 2006-10-15
Outside --> Router --> Hub --> Computer

---

### Post by Avarus on 2006-10-15
Very strange, but it seems the computer gave me the wrong IP. When I use 192.168.1.106 it does work!

---

### Post by Avarus on 2006-10-15
Well, here we go again. In apache2.conf I've changed the Serverroot to .... , but when I check my server on another computer, I still see the files from /var/www. Also, I think I've added another indextype (index.htm), but it doesn't recognise it, so I see all maps and documents instead of my index.htm. 

How can I change my root so I can upload my files directly to there, and how do I add index.htm as a valid index type?

---

### Post by adwait on 2006-10-16
SErveroot doesn't refer to the files to be served but to the location of the server config files, log files etc.

As for index.htm, did you reload apache after changing the settings? 
```
sudo /etc/init.d/apache2 reload
```

---

### Post by Avarus on 2006-10-16
Sigh... 

Avarus grabs the nearest blunt object and starts hitting himself with it ](*,) 

One problem solved, other pops up. I used chmod -R a+r /var/www to make all the stuff there readable by all. And I can read the files directly in /var/www, but I can't read files from /var/www/directory1, even if I chmod that one too. Is Apache supposed to be this hard?

---

### Post by adwait on 2006-10-17
Not really..setting up Apache is normally very easy :)

post the output of
```
ls -al /var/www
```
and I'll try......

Maybe the owner of the directory is different...

---

### Post by Avarus on 2006-10-17
```
ls -al /var/www
total 28
drwxrwxrwx 5 root root 4096 2006-10-16 19:24 .
drwxr-xr-x 14 root root 4096 2006-10-16 17:11 ..
drwxrwxrwx 2 root root 4096 2006-10-17 09:19 apache2-default
-r--r--r-- 1 root root 362 2006-10-16 19:23 index.htm
dr-xr--r-- 2 root root 4096 2006-10-16 19:29 map
-r--r--r-- 1 root root 452 2006-10-16 19:29 pagina.htm
drwxrw-rw- 12 root root 4096 2006-10-16 19:00 phpBB2
```

---

### Post by adwait on 2006-10-17
If you are trying to access the map directory, try giving all users the execute permission for it.
```
sudo chmod +x map
```

---

### Post by tomBorgia on 2006-10-17
You can change the ownership of the /var/www files to www-data - then you should be able to view them in a web browser. 
I'd use DirectoryIndex index.htm (or whatever file) for your default page in /etc/apache2/apache2.conf (not serverroot)
If you need a web browser to test this but don't have a GUI install lynx (sudo apt-get install lynx) - then run it with lynx localhost.
Hope this helps.:)

---

### Post by Avarus on 2006-10-17
It... it works:-k 

Thank you very much :D

---

