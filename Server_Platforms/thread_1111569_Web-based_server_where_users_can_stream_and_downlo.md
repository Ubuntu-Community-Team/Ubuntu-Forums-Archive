---
title: "Web-based server where users can stream and download"
date: 2009-03-30
forum: Server Platforms
---

### Post by koontz on 2009-03-30
Good day,

This is my first post therefore you can assume I am pretty new to Ubuntu.  I have searched the forums and am having trouble finding exactly what I want, and as I have found in the past with open source, someone has already done everything.  

My question to you is, is there a web-based server I can create that people can access from anywhere.  I was hoping they'd have to use a user name and password to access.  Then I want them to be able to stream and then download things they want.  Is there something on sourceforge I could use that anyone knows of?  I checked a few others, but most programs are made for streaming only.  If there isnt anything for streaming and downloading, is there something that I can use so people could just download?

I appreciate any and all help. 
Thanks

---

### Post by spiderbatdad on 2009-03-30
That is Apache. It is found in synaptic package manager. I have a beginners tutorial here: [http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)
And at the end is a section on authentication. Also I no longer argue for moving apaches client files from /var/www to a file in your /home, but it is up to you. Note it is a very basic set up. The only security is in the authentication. You may want to look into "fail2ban" as a resource for blocking ip addresses that make mutiple bad login attempts. The learning curve for apache can go on and on. I recommend not exposing your primary computer to the world by allowing access to it via port 80, nor would I recommend PHP and mysql for newcomers. If you want to host files like you say, you should have a machine dedicated to the purpose. Even an old machine with 256 RAM and Xubuntu will serve the purpose if you expect relatively few users.

---

### Post by volkswagner on 2009-03-30
[Jinzora]("http://en.jinzora.com/") allows users with passwords to login, they can choose to download or stream.

If you want to force users to login, don't allow anonymous users.  It has very little support, but it is the most feature rich I have found.

---

### Post by koontz on 2009-03-30
Thanks for the quick replies,

Jinzora allows for stream and downloading?  I know you jsut said that but I was under the impression that it was just streaming.

---

### Post by R.Bucky on 2009-03-31
Yes, Jinzora allows users to stream and download music. It operates on a Linux-Apache-MySQL-PHP (LAMP) server. So, you would need to install taskel if this is a priority. I use Jinzora daily for streaming music from home to work. It works like a charm. Works much better than Gnump3d.

---

### Post by tarahmarie on 2009-04-08
I have dithered about creating a server on my primary machine or on a backup machine that lets me access my files from anywhere.  

The biggest problem I've seemed to encounter, and the one that pushes me away from continuing is the fact that I live behind a dynamically assigned IP address and router.  

Is there any way to run a home-based server I can access from anywhere if I'm stuck with a dynamically assigned IP?

I'm not afraid of Apache, MySQL, or PHP, but if I'm going to spend the time setting this stuff up, I want to know first if it's even possible.

Thanks!

---

### Post by R.Bucky on 2009-04-08
Oh yes, people run sites without static IP's. I hosted my site for about a year on a dynamic IP until payinf $5/mo. extra on my cable bill. Check out [http://www.dyndns.com/services/dns/dyndns/]("http://www.dyndns.com/services/dns/dyndns/"). Read up

---

