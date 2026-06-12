---
title: "Looking for advice for a noob setting up a FTP server"
date: 2006-02-11
forum: Server Platforms
---

### Post by wilsonisme on 2006-02-11
Hey mates, I have an extra computer with a fresh ubuntu install on it. I have it wirelessly connected to my linksys wireless router (works flawlessly, im typing this on it right now). 

I want to make it run a FTP server I can access from school, friends house, ect. I would prefer to have some kind of **GUI** for the server, but if it is easy to set up without a GUI I suppose I could handle it :(

What I want the server to do:
1) Serve my stuff! I want to set it up so everything I put in a single folder will be accesable "from the outside" 
2) Have two accounts for acessing the ftp server, one "administrator" who can read/write files in the folder, and one "user" who can only read files in the folder. Both need to have passwords
3) Be secure so someone doesn't some how crack the server and start hosting their own stuff on it or something <-- Within reason, as long as it is not something likely to happen I am happy.
4) Have the server work. I presume I will need to open ports on my wireless router?

I read this tutorial: [Setting up FTP server with GUI]("http://www.ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server")
However it seems outdated so I didn't try it. 
I also thought maybe webmin would work for what im trying to do but I don't know, figured I would ask before I go screwing stuff up or make things more complicated then need be for what im trying to do.

Any suggestions to get the above acomplished? My biggest concern is the router, I am pretty noob so all I know is that I would need to "open the ports" in my router's firmware which I know how to do, but I don't know how I would connect to the server outside my house (ie with what ip adress, port.. what would I type in the ftp client, or a browser... ect) I presume it would be like [http://ipadress: port](http://ipadress: port) ?

Thanks in advance for any tips or info! :KS

---

### Post by bastya_elvtars on 2006-02-11
Tried proftpd with webmin and webmin-proftpd?

---

### Post by wilsonisme on 2006-02-11
alright ill give that a shot, but I heard the webmin in the repositories is outdated - should I get it from somewhere else?

Also, any input on the other questions?

Edit: I installed webmin, webmin-proftpd, and proftpd. When I go to webmin in my browser it asks for user and password, which I never set up. What would this be?

---

### Post by rcpettit on 2006-02-11
you need to use this command to install a webmin user.

/usr/share/webmin/changepass.pl /etc/webmin root <password>

I believe this is also if you install webmin outside the repository but it may be in /usr/local/webmin also depending on your setup.

---

### Post by squirrelyosis on 2006-02-12
After you get proftpd setup you can register for a NO-IP.org account which will give you a yourname.no-ip.org type domain name.  Then you can compile and install the no-ip updater on your "server" which will constantly announce your IP address so that you can always reach your home server from anywhere outside.  You will have to forward the ports in your router too.

---

### Post by nihilocrat on 2006-02-13
You could always use plain old vanilla ftpd through xinetd or something.

Your initial configuration isn't going to be in a GUI (at least I don't know of any, maybe there's some xinetd-admin web app out there somewhere) but it doesn't take that long.

Also, the tutorial looks like it is still up-to-date. Proftpd's config file format might have changed (I've never used it,  so I wouldn't know), but the other stuff about file permissions, etc., is still completely valid.

---

