---
title: "Is this to do with Apache?"
date: 2008-07-05
forum: Server Platforms
---

### Post by expatCM on 2008-07-05
Ubuntu 7.10 Server.

I have just installed Torrentflux and wish to install Joomla. Torentflux seems to have a bug so perhaps I will not be able to use it but that is not the problem.

The problem I have is that if I go to either [http://servername](http://servername) or [http://serverIP](http://serverIP) then Torrenflux login immediately appears.

I would like to be able to enter [http://servername/torrentflux](http://servername/torrentflux) or [http://serverIP/torrentflux](http://serverIP/torrentflux) so that will then let me open torrentflux (so adding another layer).

I cannot figure out how to do this. I have added a new directory in /var/www and then added torrentflux to that directory but it is not recognized through the browser. At present torrentflux is at /var/www/torrentflux.

I looked at the Apache page from Webmin and got the idea that this was the place to be but I do not know what to edit ......

Any suggestions welcome........

---

### Post by windependence on 2008-07-05
I am not familiar with Torrentflux but I suspect it probably runs it's own webserver. Read up on the torrentflux documentation. You should be able to set the port it listens on to something other than 80.

-Tim

---

### Post by expatCM on 2008-07-05
Torrentflux is basically a layer on top of BitTornado. It runs on a server and stays working even if the rest of the network is not used.  It listens to the outside world on say port 40000 and is managed through a browser interface on a client PC.

I do not quite understand your response though.  If there is a setting to change from port 80, will that not mean that I cannot access the program using the browser since port 80 is the browser default?  (I do not want to find the setting and change it from port 80 to then find that I cannot access the program)

The other point is that when I then install Joomla, presumably I will then have to also change this to another port?

---

### Post by windependence on 2008-07-05
Joomla should probably be served on 80, so you should move your torrent port to something else. You can then access it by going to [http://yourservername:8080](http://yourservername:8080) or whatever port you choose. Here I used 8080 as an example.

-Tim

---

### Post by expatCM on 2008-07-06
Thanks for the suggestion.  Changing the port address does sound like a very good idea.

I could not find out how to do this so had a go at changing the address on the Apache virtual server.  All I got was a 111 Connection refused error and so what I have done is to open a question on the TorrentFlux installation forum now that I know what I am asking .........

Thanks for your help ...  it keeps me moving forward ...

---

### Post by osjak on 2008-07-06
As expatCM said, torrentflux is a web interface to BitTornado, nothing more. There's no need to change Apache's port 80 to something else. In order to use [http://servername/torrentflux](http://servername/torrentflux)  address, you need to move your torrentflux to <webserver_root>/torrentflux directory. That's all. There may be a couple of path variables in torrentflux config file that you'll have to adjust accordingly. I have set up torrentflux before this way and it worked fine.

And then you can install Joomls into webserver root directory.

---

### Post by expatCM on 2008-07-06
I find your comment very interesting.  I created a directory in /var/www and then put TF in that directory before opening this thread.  

I was unable to subsequently browse to the directory / view content.  If I recall I got a not found notice which was strange since there was a sub directory with TF there. 

It must be the path variables but there is really not a lot to play with in the conf.php file or the other files ...

---

### Post by windependence on 2008-07-06
This is what I have been trying to tell him but he said he tried this already.

-Tim

---

### Post by osjak on 2008-07-06
> **expatCM said:**
> I find your comment very interesting.  I created a directory in /var/www and then put TF in that directory before opening this thread.  

I was unable to subsequently browse to the directory / view content.  If I recall I got a not found notice which was strange since there was a sub directory with TF there. 

It must be the path variables but there is really not a lot to play with in the conf.php file or the other files ...
I am confused a bit. Your Apache document root is at /var/www and you can see your index.html there by going to [http://servername](http://servername), right? Then you need to create /var/www/torrentflux directory and put all TorrentFlux files there. Then just go to [http://servername/torrentflux/index.php](http://servername/torrentflux/index.php) and it should work (or complain about incorrect path). Make sure you add that index.php at the end to eliminate Apache default file name setting missing.

---

