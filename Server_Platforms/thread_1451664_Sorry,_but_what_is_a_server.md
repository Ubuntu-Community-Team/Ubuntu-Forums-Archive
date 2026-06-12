---
title: "Sorry, but what is a server?"
date: 2010-04-10
forum: Server Platforms
---

### Post by TheNerdAL on 2010-04-10
I want to get into computers and hardware and stuff like that but I don't know what a server is. Thanks.

---

### Post by wojox on 2010-04-10
In short it provides services to client machines. [http://en.wikipedia.org/wiki/Server_%28computing%29](http://en.wikipedia.org/wiki/Server_%28computing%29)

---

### Post by TheNerdAL on 2010-04-10
Give me an example.

---

### Post by lisati on 2010-04-10
> **TheNerdAL said:**
> Give me an example.

When you type in [www.ubuntuforums.org](www.ubuntuforums.org) on your browser and something gets displayed, your browser gets the information that it displays from a server.

---

### Post by new_tolinux on 2010-04-10
> **TheNerdAL said:**
> Give me an example.
Ok, example:

A company has 10 employees.
Every employee is given a login-name and a password.
There are 10 workstations and 1 server.
The employee enters his/her login-name and password on the client-machine
The client-machine verifies these credentials with the server
If the server returns an "accepted" message, the user is logged in.

After that, the user can be allowed to save his/her files on the server, so that every time he/she logs in on any workstation he/she can access those files.

In this example it's a "file-server" and a "login-server".

Another example: A webserver serves pages on the internet each time one of the pages on that server is requested by someone.

---

### Post by TheNerdAL on 2010-04-10
Okay, thanks! :D

---

### Post by wojox on 2010-04-10
Click on my signature. Your client ( web browser ) is requesting a page from my server ( ubuntu 9.10 )

---

### Post by jflaker on 2010-04-10
Simpler yet.

What differentiates a SERVER from a DESKTOP computer is simply the services available.  A few years ago, this difference would be the hardware, but the lines between what is a server and what is a desktop as far as processing power is blurring...

In short, your desktop computer is a desktop computer UNTIL you share a folder.  Now you are a file server.  If you load Apache Web Server, you are now a web server...if you have MySQL installed, you are a SQL Server....All these services can be run concurrently....as with my "Desktop"....I have a few shared folders, MySQL server, Apache and I can add or remove these if I choose.

Server means to serve...to serve up services to remote/LAN clients.

---

### Post by bab1 on 2010-04-10
> **TheNerdAL said:**
> I want to get into computers and hardware and stuff like that but I don't know what a server is. Thanks.

Originally the term *server * meant "a process that ran in the background waiting to a request from a client".  Some examples of this are HTTP (web server) DNS (Domain name Service) Samba (file shares) DHCP (Dynamic Host Control Protocol).  These severs run on any host (computer).

When marketing started using the term the convention of "The Server", a dedicated piece of hardware, came into being.  I feel the original client-server architecture still best describes what you are asking for.  See [**_[COLOR="DarkSlateGray"]here [/COLOR]_**]("http://www.webopedia.com/TERM/C/client_server_architecture.html")and  [**_[COLOR="DarkSlateGray"]here  [/COLOR]_**]("http://en.wikipedia.org/wiki/Client-server") for a basic description of Client-Server.

---

### Post by rcayea on 2010-04-10
I'll throw in my brief info...

The best info I ever was told to help me was that in the computer internet world, everything is either a server or a client. The server would serve up the information. The client would access the information.

---

### Post by Skidbladnir on 2010-04-10
The client, Firefox for example, sends a request to the server, twitter for another example, as "GET twitter.com".  Your client send a request to your DNS server, the servers that lookup domain names and get you to where your going.  It's usually provided by your ISP in DHCP, or manually in resolv.conf on Ubuntu.  If it doesn't know what you are talking about, it sends it to another server, and so on, until it fails or finds the entry.  The DNS server returns the IP address to you and your computer send a request for that data.  The server at that IP then returns the information that you want, based on port (web is 80) and hostname you requested.  The server parses the information if it is a CGI language, such as PERL or PHP and sends it your client.  Your client then renders it, with Gecko in Firefox, as HTML and parses the CSS and JavaScript.

---

