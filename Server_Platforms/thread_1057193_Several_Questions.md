---
title: "Several Questions"
date: 2009-02-01
forum: Server Platforms
---

### Post by spinanicky on 2009-02-01
Hi guys, 

I have just completed setting up my ubuntu server on a P3 intel (cost me 50 pence ;-) )

1) Now first question, I have three other house mates that access the server to watch movies etc. How can I see who is currently using bandwidth on the server or who is accessing it. Keeping in mind that they simply connect via samba (ie file sharing). Also Looking at the samba log files, they show nothing, they are empty?!


2) If I wanted to block a certain IP from accessing the server how would I do that?

3) I am trying to set up vsftpd and was wondering how I could create limited users that are only allowed to read and write to a certain folder and can login via ftp. ONLY THAT. So I dont want them to be able to login via ssh or change anything etc. (I don't trust one of my house mates)

4) What should my www folder permissions be... it is currently on 777 which im pretty sure was wrong but I was having trouble writing to it before. Should I chown to my user (nicky) and only give myself write abilities (keeping in mind I read and write to the folder over the network, samba)

4) The maximum speed I'm getting over the network when copying files from the NAS onto my desktop is about 7mb/s. The hard drive is a 1TB high speed usb drive plugged into a usb 2.0. Should I not be getting a lot faster speeds? I have already checked to make sure it is actually a 2.0 usb slot, is there any way to identify where it is being bottlenecked?

Thanks for the help guys. 

Nicky

---

### Post by inphektion on 2009-02-01
1.  ```
aptitude install iftop
```
      then just run iftop and you'll see.
2. [http://www.samba.org/samba/docs/server_security.html](http://www.samba.org/samba/docs/server_security.html)
       I assume you mean from samba since that is how they connect.  just add the hosts deny to the conf file.
3.  search for vsftpd and virtual users.  This is the best way to use it anyway and fits in with your needs.  You can do what I do and set up the users in an htpasswd file for authentication so unless you've created the users in htpasswd they won't get in.  They will have no access but to the ftp and whatever home folder for ftp you use for them.
4.  Yes def shouldn't be 777.  I guess you can chown to nicky but then I would chgrp to www-data and do maybe a 754 permission.
5.  Possibly.  but you have nas overhead with the nfs or samba share going to the usb overhead.  Then there is how fast the Hdd's are in the box and the files you are copying could be small which takes time off.  
Keep in mind usb2 is 480Mbps which means max theoretical speed is 60MB/s.  Seeing 7MB/s on a random file copy probably isn't too bad.  
There are a billion settings you could tweak on NAS side and on ubuntu size, caching, journaling, jumbo frames, etc all will affect the speed.  Start searching and tweaking I guess but overall with no tweaks and a random copy that isn't too bad.

---

### Post by spinanicky on 2009-02-01
all i get from ftop is 

IP address is: 192.168.1.69
MAC address is: 00:50:8b:90:a3:95
pcap_open_live(eth0): socket: Operation not permitted


Thanks for the rest of the tips

Edit... nevermind... forgot the sudo...

---

