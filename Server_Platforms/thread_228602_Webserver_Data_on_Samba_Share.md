---
title: "Webserver Data on Samba Share?"
date: 2006-08-03
forum: Server Platforms
---

### Post by IrishMLK on 2006-08-03
I'm currently working on migrating our web server from a WAMP box to a LAMP box with Dapper. 

Can I place the data for our website on a Samba share without too much performance loss? The data in question is primary images that we are proofing to our photography studio customers.  File size averages 90 KB or so.  

I want to use our File server that gets regular backups for this so the web server backup isn't that big.  We have a gigabit ethernet and the dapper box has an AMD 3800+ with 1GB of RAM.  

As a side note, once I have everything setup I am under the impression that our existing network firewall/router should be able to handle most intrusion/egress problems.  What else can I do to make the box as secure as possible given that port 80 and an FTP port will be open?

Thanks for the direction.
MLK

---

### Post by cantormath on 2006-08-03
> **IrishMLK said:**
> I'm currently working on migrating our web server from a WAMP box to a LAMP box with Dapper. 

Can I place the data for our website on a Samba share without too much performance loss? The data in question is primary images that we are proofing to our photography studio customers.  File size averages 90 KB or so.  

I want to use our File server that gets regular backups for this so the web server backup isn't that big.  We have a gigabit ethernet and the dapper box has an AMD 3800+ with 1GB of RAM.  

As a side note, once I have everything setup I am under the impression that our existing network firewall/router should be able to handle most intrusion/egress problems.  What else can I do to make the box as secure as possible given that port 80 and an FTP port will be open?

Thanks for the direction.
MLK

Compared to WAMP, LAMP is gonna rock.  Why do you want to do that with samba, are the images on a windows machine?  

some security ideas
[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)
[http://packages.ubuntu.com/dapper/admin/harden](http://packages.ubuntu.com/dapper/admin/harden)
[http://www.petefreitag.com/item/505.cfm](http://www.petefreitag.com/item/505.cfm)
[http://www.howtoforge.com/apache_mod_security](http://www.howtoforge.com/apache_mod_security)

a great all around way to setting up a dapper box
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by IrishMLK on 2006-08-03
cantormath, Thanks for the links. I will check them out them later at work. 

The images are currently on a windows box, but I was looking to streamline the backup process.  We currently have a Small Business Server (I know, I know) running for file, calendar,  and printer sharing.  I want to be able to leverage that box for the images as it already houses all of our other data. 

Thanks.
MLK

---

### Post by cantormath on 2006-08-03
> **IrishMLK said:**
> cantormath, Thanks for the links. I will check them out them later at work. 

The images are currently on a windows box, but I was looking to streamline the backup process.  We currently have a Small Business Server (I know, I know) running for file, calendar,  and printer sharing.  I want to be able to leverage that box for the images as it already houses all of our other data. 

Thanks.
MLK

LOL, Yeah, i have had my experiences and heard plenty of stories about Small Business server.  Sometimes you got to do what you goto do. 

 As far as a samba share, on the ubuntu box, effecting the performance of the windows server, I dont think the windows server will mind to much, you just need to configure it right.  You can also setup active directory type solutions that work with samba and windows machines.  You might want to ask around on that because that is only my opinion.  

As far as samba running on the dapper box, you do what you have to do.  If you need it, you got to do it.  Depending on how much the samba shares are being accessed, I think, will determine the effect it has on the server.  I personally dont think it has to be all that bad.  You can also use webadmin, which is in the repositories, to manage the samba shares etc... check it out, its a nice web based application. All in all, I think it will all work better with dapper then windows, even if you have to use a litte samba. 
 Again, you might want to ask around and see what others have to say on this because again this is only my opinion based off of my own experiences.

---

