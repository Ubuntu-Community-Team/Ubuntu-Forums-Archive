---
title: "Creating an Ftp folder thats also webfolder"
date: 2008-10-27
forum: Server Platforms
---

### Post by misheck on 2008-10-27
I have Ubuntu Server installed on my server machine. I have installede and ftp pro, I would like to create an ftp folder that should also serve as webfolder because the default folder does not give access to users other than the root user.

Is my problem to do with configuring the apache config file or can I mount the ftp folder to another folder which everyone has access to?

Any help is appreciated because I need to access the server remotely. I will be using it as a webserver only.

---

### Post by baudday on 2008-10-27
So you wanna make a folder outside of /var/www/ accessible on the internet? If this is the case, all you have to do is make a link in /var/www/ to the folder. Do this:

```
sudo ln -s /path/to/ftp_folder/ /var/www/ftp_folder/
```

Hope this helps.

---

### Post by misheck on 2008-10-28
Thanks thats worked but I now need to make the folder an FTP folder. Thanks for your help otherwise in the mean time I will be looking on the internet for help.

Thanks again.

---

### Post by misheck on 2008-10-28
I was using Xampp and Proftp so all I did I was use chmod and changed permission for the chmod 777 /opt/lampp/htdocs and then created a folder there and then put the permission back and then changed the permission on the new folder I created chmod 777 /opt/lampp/htdocs/*newfolder*. After this I entered the code you gave me and I had to use the sudo command all the way. So everything is working fine. Thanks **baudday** for the help.

---

### Post by baudday on 2008-10-28
You may not wanna make it 777. That gives anyone write permissions. try 

```
sudo chown user -R folder
```

then

```
sudo chmod 755 -R folder
```

That way you make it read write for the owner, aka the ftp user, and just read for everyone else. Just a tip, maybe you already know what you're doing there though. Glad I could help.

---

### Post by misheck on 2008-10-28
Sorry I am still new to Linux all together, but how do I make an ftp user because I was using my admin user and password.How do I create an ftp user. Ideally I would like to create folders and have ftp users to have access to their own folder only hence each user should have a seperate password. I am using Xampp and Proftp and there is no admin for the Proftp. If you can help I will be grateful. Thanks in advance.

---

### Post by baudday on 2008-10-28
So when I set up my ftp, I wasn't sure how to accomplish this in the correct way either. There is a way that you can create virtual users on the machine instead of users that can actually log into the machine, so basically they can only ftp, and ideally that's what you'd like. If someone would like to explain how to do that, you should probably listen to thme. But I'm not sure how to do this. It wasn't too important for me to have to do this, so I just settled for actual users on the machine. 

If you're planning on having a lot of users, I would just suggest installing webmin. It's an easy way to manage all users and servers, ie apache, php, mysql. if you go to the link in my sig, the very bottom post explains how I installed webmin, just look for webmin within the post. After you install it you can click on manage users/groups and there you can create a new user and lock him to his home folder which you can set just by typing it into a field. There's also a way on there to make them virtual, I just am not sure how. But yeah, I suggest webmin.

---

### Post by misheck on 2008-10-29
Sorry for the late reply. I will have to try next week. I am back at work so I will let you know. I was trying to sort the server out and leave somewhere where I can work online hence I wanted the ftp. I will let you know later.

Just out of curiosity **(will I be ble to run webmin on a server without a desktop gnome or Xserver?)**

---

### Post by baudday on 2008-10-29
Yes, webmin is something you access from a browser. If you've ever heard of CPanel, it's like that. You set it up so that you can access it from outside the network, and then on another computer you navigate to [http://your.ip.address:10000](http://your.ip.address:10000)

---

### Post by 080801jk on 2008-10-30
Patch 2.4 without the expansionReader Sebastian wrote in to us with an interesting question: what good is patch 2.4 if you don't have the Burning Crusade expansion yet? [** buy wow gold **](http://www.oofay.com/)He has a lower level character that hasn't hit 70 yet (he's on level 46), and wants to know exactly what 2.4 is doing for him. [**cheap wow gold**](http://www.oofay.com/)From what we can tell, wow goldnot much.You'll still get some of the good interface updates -- so you'll get the buffs to Inspect, wow goldthe combat log improvements, and all of the other additions Blizzard has made to the UI. All of the talents you have by 46 that got changes will change, too, [**world of warcraft gold**](http://www.oofay.com/)and of course the improvements to Warsong Gulch are great for characters of almost any level (since almost everyone can go in there).[**cheap wow gold**](http://www.oofay.com/) And let's not forget the biggest change this patch: Old Blanchy's Feed Pouch is now an 8 slotter. That's huge.[** buy wow gold **](http://www.oofay.com/)it's good to find out what Blizzard's been up to for the past few months

---

### Post by Lars Noodén on 2008-10-30
> **misheck said:**
> Any help is appreciated because I need to access the server remotely. I will be using it as a webserver only.

You might look into WebDAV 

 [http://www.debian-administration.org/articles/285](http://www.debian-administration.org/articles/285)
 [http://tldp.org/HOWTO/Apache-WebDAV-LDAP-HOWTO/](http://tldp.org/HOWTO/Apache-WebDAV-LDAP-HOWTO/)

WebDAV will allow you to access folders via the webserver itself with not much more than the addition of the mod_dav and mod_dav_fs:

 [http://httpd.apache.org/docs/2.2/mod/mod_dav.html](http://httpd.apache.org/docs/2.2/mod/mod_dav.html)
 [http://httpd.apache.org/docs/2.2/mod/mod_dav_fs.html](http://httpd.apache.org/docs/2.2/mod/mod_dav_fs.html)

Note that with both FTP and Basic HTTP Authentication the user names and passwords are transmitted unencrypted for anyone between you and your server (or on the same subnet as you and your server) to read.  HTTP over SSL or SFTP (different from FTPS) are safer, more modern options.  SFTP is part of OpenSSH-Server

---

