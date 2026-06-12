---
title: "So Apache... Doesn't Work"
date: 2011-03-10
forum: Server Platforms
---

### Post by Sansari on 2011-03-10
I swear it's always the simple stuff...
Ok so I installed xubuntu 10.04 and got a vnc over ssh server running fine (unrelated, but that's the only other thing I've done). Then I tried setting up a simple Apache HTTP server, mostly following [the documentation page]("https://help.ubuntu.com/community/ApacheMySQLPHP") and [this slicehost page]("http://articles.slicehost.com/2010/5/19/installing-apache-on-ubuntu"). I used "sudo tasksel install lamp-server", which seemed to work fine. I checked the synaptic package manager and all necessary packages seem to be installed.

After that I created /etc/apache2/conf.d/servername.conf and wrote "ServerName Dell", then in /etc/hosts I added "127.0.1.1 Dell" under the existing localhost (actually I think this happened automatically when I made ServerName Dell)

That's all I remember doing, but Apache's not working properly. I can see the 'It worked' page on the server itself, but other computers on the same network can't see [http://localhost](http://localhost) or the server's ip address.
Any idea what's wrong?

---

### Post by An Sanct on 2011-03-10
Welcome to the forums!

Well in Ubuntu, this is the command to install the whole package
```
sudo apt-get install lamp-server^
```
Also [http://localhost]("http://localhost/") drops me to *my own* LAMP server and also any other machine, since it is a special address, maybe you meant [http://dell?](http://dell?)

After install, did you restart the server? Maybe a quick reboot will do miracles...

---

### Post by mciverza on 2011-03-10
> **Sansari said:**
> 
After that I created /etc/apache2/conf.d/servername.conf and wrote "ServerName Dell", then in /etc/hosts I added "127.0.1.1 Dell" under the 
existing localhost 


That is what is wrong. Your apache server knows that "dell" is a hostname available on its internal networking (127.0.0.1 / loopback)
so nothing else will be able to connect to dell.

You also face a secondary problem, that none of your external computers know where "dell" is. That is a DNS/hosts issue. You need to either add "dell" to your local DNS server, or manually add it to your other PC's host file

---

### Post by stlsaint on 2011-03-10
> but other computers on the same network can't see [http://localhost](http://localhost)
Maybe im reading this wrong but it looks like you are trying to run "localhost" on a client and looking for it to connect to your server. Running localhost on a client will make that client look for its own localhost. Not the server.

---

### Post by Sansari on 2011-03-10
Ok I did sudo apt-get install lamp-server^, got a long list of 'already at newest version', then 0 updated, 0 installed, etc.
So I was right about that one.

I tried [http://localhost](http://localhost) as well as [http://Dell](http://Dell) and the server's internal ip address. None worked.

I also tried this while making apache listen to different ports (by changing ports.conf and the sites-enabled file for the site) like 80, 587, 8000, none got through. This shouldn't be a problem on local connection though, right? I was only expecting to deal with this once I tried to get it online through dyndns.

Every time I changed something, I restarted the apache server with sudo /etc/sbin/apache2ctl restart *and* sudo /etc/init.d/apache2 restart.

mciverza, what do you suggest I do with /etc/hosts then? I could swear it made that change by itself. And is adding the server to a local DNS/local machines really necessary? Right now I'm just trying to get the server available to the other computers on the same LAN through a wireless router. I don't think there's a DNS server involved...

-Super important edit-
Ok so after restarting the computer a couple of times  (and not really changing anything) I can access the web page with 192.168.0.100 (server ip), but not with [http://Dell/](http://Dell/), which is kinda weird... Anyway, I was able to get dyndns to connect to it, so now my website is up :D Thanks a lot guys!

---

