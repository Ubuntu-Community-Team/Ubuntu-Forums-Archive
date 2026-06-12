---
title: "Setting up an ftp server with debian etch?"
date: 2008-04-10
forum: Server Platforms
---

### Post by patrickaupperle on 2008-04-10
I am wanting an ftp server and was wondering if anyone can link me to a good how-to to set up debian etch (stable) as an ftp server.

Sorry if this topic comes up a lot.

---

### Post by ibutho on 2008-04-10
This [article]("http://howtoforge.com/perfect_setup_debian_etch") may help.

---

### Post by kerry_s on 2008-04-10
> **ibutho said:**
> This [article]("http://howtoforge.com/perfect_setup_debian_etch") may help.

good link, added to my bookmarks. :)
thanks

---

### Post by patrickaupperle on 2008-04-10
> **ibutho said:**
> This [article]("http://howtoforge.com/perfect_setup_debian_etch") may help.
Thank you, 
what do I put for host name? Domain name?

---

### Post by ibutho on 2008-04-11
For the hostname, put your machines name (the one that will be running the ftp server). For the domain, you can use your top level domain if you have one or if the ftp server is for a local lan, use the domain name for your lan (I usually make one up e.g. somedomain.lan).

---

### Post by hyper_ch on 2008-04-11
is there a reason why you want a ftp server? SSH/SCP server is very simple to setup (and secure)

---

### Post by patrickaupperle on 2008-04-11
> **hyper_ch said:**
> is there a reason why you want a ftp server? SSH/SCP server is very simple to setup (and secure)

Is that the kind of server that apache sets up? If not, how do I set one of these up?

---

### Post by hyper_ch on 2008-04-11
apache is webserver

ssh is an encrypted remote access...  ssh can be employed in a similar fashion that a traditional ftp server uses but normally ssh relays on system users.

it just depends on what you want to do with the ftp server.. if it's just a question of you getting access to your files from everywhere, setup a ssh server and use scp for transfer.

---

### Post by patrickaupperle on 2008-04-11
> **hyper_ch said:**
> apache is webserver

ssh is an encrypted remote access...  ssh can be employed in a similar fashion that a traditional ftp server uses but normally ssh relays on system users.

it just depends on what you want to do with the ftp server.. if it's just a question of you getting access to your files from everywhere, setup a ssh server and use scp for transfer.

Would I be able to read and write files to a server from any computer world wide? Would friends of mine be able to access these files, with a password of course? Would I need a special program to access these files? And Lastly. Would I be able to access and use these files without downloading them?

Also can you tell me how I can set this up?

---

### Post by syncrondi on 2008-04-11
> **patrickaupperle said:**
> Would I be able to read and write files to a server from any computer world wide? Would friends of mine be able to access these files, with a password of course? Would I need a special program to access these files? And Lastly. Would I be able to access and use these files without downloading them?

Also can you tell me how I can set this up?

_[This guide](https://help.ubuntu.com/7.10/server/C/openssh-server.html)_ should help with setting up OpenSSH.

SSH provides remote terminal access to your server securely. It is the most preferable way to allow access to users. You can execute and read files on the server over SSH. On the client side, you can use terminal or _[PuTTY](http://en.wikipedia.org/wiki/PuTTY)_ on Windows.

---

### Post by patrickaupperle on 2008-04-11
Sweet. That looks awesome. 
2 more questions. If I have an mp3 file on the sever and I use putty from a win pc to access it, will it come up in windows media player? 

Can I download a file off this server?

edit: I just keep thinking of questions.

It looks like attaching a domain name, rather than using the IP, is possible. I am assuming I would need a domain name to do this, but domain are only $9 a year. Even I can afford that. Is this done easily?  Can I do it by just changing some config file?

Edit2: This is a less important question.
I was reading the "The Perfect Setup" article posted earlier and was wandering what Database Servers and DNS Servers are. What are they?

---

### Post by hyper_ch on 2008-04-11
> **patrickaupperle said:**
> Sweet. That looks awesome. 
2 more questions. If I have an mp3 file on the sever and I use putty from a win pc to access it, will it come up in windows media player?
I don't think so... but you could setup a streaming mp3 server... if you have more than one file there...

> **patrickaupperle said:**
> 
Can I download a file off this server?
What do you mean?


> **patrickaupperle said:**
> It looks like attaching a domain name, rather than using the IP, is possible. I am assuming I would need a domain name to do this, but domain are only $9 a year. Even I can afford that. Is this done easily?  Can I do it by just changing some config file?
Using a real domain name is a bit more complicated... however you can use a dyn. ip service like [www.no-ip.com](www.no-ip.com) or [www.dyndns.org](www.dyndns.org)

They are free of charge and there are the clients available in the repos to update your dynamic IP...


> **patrickaupperle said:**
> 
Edit2: This is a less important question.
I was reading the "The Perfect Setup" article posted earlier and was wandering what Database Servers and DNS Servers are. What are they?
You know what a database is?

and dns servers are needed for setting up a domain name ;)

---

### Post by patrickaupperle on 2008-04-11
> **hyper_ch said:**
> I don't think so... but you could setup a streaming mp3 server... if you have more than one file there...

I would like to know how to do this, too. 
Does this mean that I could not use a native app to edit something on the server?
> **hyper_ch said:**
> 
What do you mean?

Copy a file from the server to the local computer hard drive.
> **hyper_ch said:**
> 
Using a real domain name is a bit more complicated... however you can use a dyn. ip service like [www.no-ip.com](www.no-ip.com) or [www.dyndns.org](www.dyndns.org)

They are free of charge and there are the clients available in the repos to update your dynamic IP...


No big deal
> **hyper_ch said:**
> 
You know what a database is?

and dns servers are needed for setting up a domain name ;)
No I don't know what a database is. I am guessing it is not important to me?

---

### Post by syncrondi on 2008-04-11
> **patrickaupperle said:**
> Does this mean that I could not use a native app to edit something on the server?

You can run programs that are installed on your server. They will output (text based) to your shell terminal

> **patrickaupperle said:**
> 
Copy a file from the server to the local computer hard drive.

This is where you use SCP that was mentioned earlier. For Windows, you can connect via _[WinSCP](http://en.wikipedia.org/wiki/Winscp)_ to make secure transfers.

---

### Post by patrickaupperle on 2008-04-11
> **syncrondi said:**
> You can run programs that are installed on your server. They will output (text based) to your shell terminal


This is where you use SCP that was mentioned earlier. For Windows, you can connect via _[WinSCP](http://en.wikipedia.org/wiki/Winscp)_ to make secure transfers.

To make sure I have this straight, If I have a .doc on the server, I can not use MS Word to modify it?

Can someone elaborate on the mp3 server? It would be very nice, too.

Edit: Will WinSCP work with just the OpenSSH server?

---

### Post by syncrondi on 2008-04-12
> **patrickaupperle said:**
> To make sure I have this straight, If I have a .doc on the server, I can not use MS Word to modify it?

It sounds like you've not worked very much with Linux. Basically, with pure SSH, you get a [terminal](http://people.warp.es/~jorge/screenshots/galleries/gnome-terminal-prompt2.png) to execute commands remotely. You can run text editors like [nano](http://en.wikipedia.org/wiki/Nano_%28text_editor%29) or vi to edit text files, but not do any word processing. 

> **patrickaupperle said:**
> 
Edit: Will WinSCP work with just the OpenSSH server?
WinSCP runs SCP or SFTP without any additional setup of OpenSSH.

---

### Post by hyper_ch on 2008-04-12
for the music server have a look at gnump3d

and yes, winscp will work with the openssh-server...

---

### Post by patrickaupperle on 2008-04-12
Thank you both for the replies. I have finally run out of questions:lolflag:. I may post again at some point, though.

I think I will set-up OpenSSH and a web server.  I can play mp3s just by opening the location on the web. For example I can go to totem and go movie, open, and put in a location on the web.

---

