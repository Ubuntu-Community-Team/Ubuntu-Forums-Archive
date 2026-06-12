---
title: "Setting Up A Web Server For My First Time"
date: 2007-08-21
forum: Server Platforms
---

### Post by jlacroix on 2007-08-21
Hello everyone! This is my first time setting up an Ubuntu server, so please bear with me.

I am hosting a site on a dedicated Ubuntu box with a LAMP installation complete with phpmyadmin. The web site I am hosting is internal, so its not going to go outside of my network. It's actually working right now, however there are a few things I am not clear on.

1.) I need to be able to copy a file that is generated from the website to a UNC path. (Like //server/directory). I'll probably need a shell script to do this. The thing is, this share needs a username and password to connect to. What command(s) would I use to copy a text file to the share complete with username/domain/password?

2.) I'm actually going to host two sites on this box. Each one needs its own static IP. Right now the entire server is using something like "10.x.x.x" and the secondary web page will need a different IP. Can I do that?

Basically I want it to be where the user types in IP address A, it goes to site A, or if they type ip address B, it goes to syte B:

[http://10.x.x.x/](http://10.x.x.x/) (Go to  site A)
[http://10.y.y.y/](http://10.y.y.y/) (Go to site B)

I know how to have a static ip, but how do I do two of them?

Thanks for any help in advance!!!

---

### Post by milosz.galazka on 2007-08-21
> **jlacroix said:**
> 
2.) I'm actually going to host two sites on this box. Each one needs its own static IP. Right now the entire server is using something like "10.x.x.x" and the secondary web page will need a different IP. Can I do that?


Look at [http://www.linuxquestions.org/questions/showthread.php?t=575214](http://www.linuxquestions.org/questions/showthread.php?t=575214) and related topics if you are using one NIC. 

Here is probably answer you are searching for: [http://www.debianhelp.co.uk/virtualhosts.htm](http://www.debianhelp.co.uk/virtualhosts.htm)

---

### Post by jlacroix on 2007-08-21
Thanks! I followed those directions and I have both IP's set up. That was easier than I thought it would be. :)

Now, all I need to do is figure out how to copy a text file to a printer share, that is shared at //printserver/JetForm so I can automatically print generated files from my web page. Anyone know how I can pull that off?

---

### Post by milosz.galazka on 2007-08-21
[http://oslabs.mikro-net.com/mcifs.html](http://oslabs.mikro-net.com/mcifs.html)
[http://linux.die.net/man/8/mount.cifs](http://linux.die.net/man/8/mount.cifs)
samba-client
?

PS. if you mean printer then search for informations about cups :)

---

### Post by jlacroix on 2007-08-21
I tried those steps earlier, I guess I'm not sure what method I need to use. I'll explain what I used to do on the Windows server that I'm trying to replicate with Ubuntu.

On the Windows server, before I converted it to Ubuntu, the web page would save a file to the hard drive, and a MS-DOS batch file would copy that file to the UNC path //printserver/JetForm. Once the file was placed in that directory it would automatically print.

I can mount a Windows directory with the information you provided, but I cannot mount a printer share as a folder to copy files to. 

I guess what I need is the file "worequest.dat" to be copied automatically.

---

### Post by Wim Sturkenboom on 2007-08-22
Not 100% rekated to your question but do you need 2 ip-addresses? The only reason I can see for that is when you use http**[COLOR="Red"]s[/COLOR]**, else name based virtual hosting is the way to go.

---

### Post by jlacroix on 2007-08-22
To be honest, I'm not sure. The network administrator here told me to use two IP addresses so I did. I'd like to learn more about the differences, though.

---

### Post by jlacroix on 2007-08-22
Thanks everyone! All I have left now is to fix a small samba issue, so I posted that over at the networking forum.

---

### Post by Wim Sturkenboom on 2007-08-22
There are two ways of virtual hosting, *name based* and *ip based*.

In the first one, apache can host multiple sites based on the site name (e.g. [http://mydomain.com](http://mydomain.com)) that is in the http request. Apache receives a request for a site and will check its virtual hosts for the name in the http request.

In the second case, apache can host multiple sites based on ip addresses. Apache will use the ip address in the tcp/ip data to find an entry in the virtual hosts.

The trick comes when you want to use https. The http request is encrypted and apache can not determine the requested site name. Therefor it's necessary to use ip based virtual hosts.

---

### Post by jlacroix on 2007-08-23
Thank you for the information.

---

