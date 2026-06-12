---
title: "Can't load html on Ubuntu Server from other computer within home network"
date: 2019-03-19
forum: Server Platforms
---

### Post by forsberg4president on 2019-03-19
Hi guys!

If you could help me I would be greatful.. :)

I just started programming js and installed Ubuntu on my laptop. To make things cheaper I used another old laptop and installed Ubuntu Server. I'll be damned but I actually managed to do that and to install a GUI to it. I also installed Mongodb. I'm even more proud about that I read about SSH and managed to log onto the Ubuntu Server from the other laptop. Feeling cocky I created a folder on the Ubuntu Server and added an HTML and a CSS thinking that I could load it in my browser-window on my laptop. I tried writing the inet number and then the folders with a slash in between and then index.html, but ofcourse it didn't work. Example "192.193.1.354/webstuff/htmltest/index.html"

How can I write in the browser to see my html-file that's located on my ubuntu server that's located on a separate computer within my wifi network? (I can, like i mentioned, reach it from the terminal using SSH)

Good vibes/ Gandalf

---

### Post by freemedia2018 on 2019-03-19
What happens if you run this from SSH?

```
wget -O- http://127.0.0.1/webstuff/htmltest/index.html
```

---

### Post by forsberg4president on 2019-03-19
> **freemedia2018 said:**
> What happens if you run this from SSH?

```
wget -O- http://127.0.0.1/webstuff/htmltest/index.html
```


Risking to sound stupid, but I don't understand what you want me to do?
Try that command in the server terminal? Try that command in my computer terminal? Try it in the web browser on my computer?
How do I ssh it? When I'm logged onto my server through SSH I'm already in, right?.. hehe
I'm very new to this.. 

Created this Ubuntu Server to host my projects including HTML, CSS, JS and MongoDB.
A friend told me today that it wouldn't be enough with a Ubuntu Server and that I needed to use a node server. Is that true?
I am lost.. :P

---

### Post by spjackson on 2019-03-20
> it didn't workWhat happened? Did you get an error message? If so, what was it?

You need a webserver running on port 80 on the server, e.g. Apache or nginx. Do you have one? If so, which? In the case of a default installation of Apache, the url [http://192.193.1.354/webstuff/htmltest/index.html](http://192.193.1.354/webstuff/htmltest/index.html) would refer to the file /var/www/html/webstuff/htmltest/index.html on 192.193.1.354.

> 
```

wget -O- http://127.0.0.1/webstuff/htmltest/index.html
```

That command is meant to be run on the server (hence 127.0.0.1). It would help in diagnosing what is going on by removing the web browser and connectivity between client and server from the equation.

Edit: Oops. I've just noticed that 192.193.1.354 isn't valid anyway since 354 > 255 - I'm guessing that must be a typo.

---

### Post by The Cog on 2019-03-20
You need to install some kind of webserver on the server before you can use a web browser to see the files. The Ubuntu server install CD normally asks if you want to install a web server. Did you say yes to that? If so, do you know what web server it installed (probably apache or nginx). If not then you need to either install one of those two. Both have their pwn configuration files that have to be edited to get things working.

To see if a server is listening, you could use the command **ss -ltp** on the server and look for a local address ending in http or https. Actually, this will also tell you the name of the web server software (if it's there).

I assume that you have created a folder /webstuff and put the files in there - this is not a directory that either apache or nginx will use unless you edit their configuration files. 

As a quick test, you can run a web service by running these two commands on the server:
```
cd /webstuff
python -m SimpleHTTPServer
```
This second command won't return to the command prompt - it sits there serving HTTP requests until you kill the command with Ctrl-C. It listens on port 8000 so the URL for the browser would be:
[http://192.193.1.354/htmltest/index.html](http://192.193.1.354/htmltest/index.html) or simply [http://192.193.1.354/htmltest](http://192.193.1.354/htmltest) as the index is served by default if it exists in a requested folder.

---

### Post by neutronforrest on 2019-03-21
Dear All,

I have the same issue as stated in this thread.  I have successfully setup a server on an ubuntu computer.  I used Nginx and setup an example .html file.  To see the server on this local computer I had to add this to /etc/hosts

192.168.x.x [www.example.com]("http://www.example.com")

I can now login into the web browser and see my simple text from the .html file.  My issues is that I cannot see this file from another computer within my home network.  I can see the default nginx page using the IP address 192.168.x.x but I am unable to see [www.example.com]("http://www.example.com").  I have disabled the ufw.  Here is my simple .conf file.

server {
    listen 80;
    listen [::]:80;
    root /var/www/example;
    index index.html;
    server_name [www.example.com;]("http://www.example.com;")
}

When I type wget -O- [http://192.168.1.101/var/www/example.index.html](http://192.168.1.101/var/www/example.index.html)

--2019-03-21 09:59:48--  [http://192.168.1.101/var/www/example.index.html](http://192.168.1.101/var/www/example.index.html)
Connecting to 192.168.x.x:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2019-03-21 09:59:48 ERROR 404: Not Found.

Any help is appreciated.

---

### Post by The Cog on 2019-03-22
@neutronforrest: Please don't hijack other people's threads. There's no evidence that you have the same problem. I think yours is that you are trying the wrong url. I think the web server regards /var/www as its root folder, so your url would be [http://192.168.1.101/example.index.html](http://192.168.1.101/example.index.html). As for [www.example.com](www.example.com) - try the command "ping example.com" and make sure you get the right address quoted - this might be a name resolution issue.

---

### Post by neutronforrest on 2019-03-22
My intention was not to hijack this thread.  My apologizes.  And unfortunately, your suggestion did not seem to work.  But thank you!

---

