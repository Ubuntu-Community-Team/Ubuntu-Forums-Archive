---
title: "Suggestions for bare bones file sharing?"
date: 2014-01-21
forum: Server Platforms
---

### Post by Robert_Boutin on 2014-01-21
Hi, nube here, hope I've posted to the correct forum.

I have a server in my basement that I set up to get away from my e-mail/web hosting service and, miracle of miracles, it actually works great.  Now I want to install a very basic file sharing app but I'm struggling to find the right software for my needs.

I am looking for something that offers:

-basic login via http
-the ability to add multple users
-a folder for each user.  The user would see only his/her individual workspace upon login, admin sees all folders
-local hosting
-no unnecessary bells or whistles like revision control, contacts, calendar, blah, blah
-very simple file uploading for users, i.e. browse for file and click to upload
-users can access simply via web browser

I am just looking for a package that let's someone safely and securely upload a file to the server and be confident that the only other user that can see it is me.  Nothing else is needed.  I am looking at ownCloud and Pydio, but they are really a lot more than I need.  Can anyone suggest a VERY basic and secure file sharing app that is easy to install and easy to use?

I am running Ubuntu 12.04 with Apache.  I'm not sure if more info is needed.

Thanks!

---

### Post by tfrue on 2014-01-22
Well, to get the browser part you would have to use apache, which I'm sure you knew, but I don't know how to configure maybe edit the /etc/hosts file... I don't know.

On the other hand, I would set up Samba as it is super easy to use, and can be configured from the terminal so you can set up SSH and access it remotely.

To install samba, type:
```
sudo apt-get install samba
```
Let it install and once it's finished type, to begin editing the config file for Samba:
```
sudo vim /etc/samba/smb.conf
```

Let's say that you have three users that needed to access their share with authentication then I would set up different mount points for each user. You could even give them their own separate partitions if you wanted. Anyway, lets say you have Chris, Tom, and Sue mounted at /media/chris, /media/tom, /media/sue and we want them to access only their share with their passwords.

So let's begin!
```

[NewShare]
comment= Chris's Share
path= /media/chris
browseable= yes
read only= no
guest ok= no
valid users= chris
(Hold *Shift* and press *zz* to save and exit vim)

```
Tom's and Sue's would look the same but the path would be different, but now we need to take care of some things. You need to change the security type in the smb.conf, and we need to add Chris, Tom, and Sue to the local server and add them using smbpasswd. You can add users without giving them a home directory, but you could also let them have their own home directory and change the mount points in the smb.conf from "path= /media/chris to path= /home/chris" after you have added the users.

Anyway, type:
```
sudo vim /etc/samba/smb.conf
```
Again to edit the config file, then under the Authentication heading remove the ";" in front of security= user and then save and exit vim once again.

To add them using smbpasswd so we can utilize the "valid user" option in our share, tyep:
```

smbpasswd -a chris
enter password
re-enter password

```
And you should be set! Now lets restart the Samba deamon services and see how it works.
```

sudo service smbd restart && sudo service nmbd restart
```

Hope all goes well,
Chris

---

### Post by volkswagner on 2014-01-22
Well file sharing over the internet is does not necessarily constitute bare bones.

I believe OwnCloud is your best bet.  An alternative would be to setup a [WebDAV]("http://ubuntuguide.org/wiki/WebDAV") server.

---

### Post by Robert_Boutin on 2014-01-22
Having had to wipe my hard drive to start over countless times when I was setting up the mail server, I'm a little nervous about having to do too much coding.  I learned enough to muddle through, but I'm not a programmer by any stretch.  I'll try out the options above on my laptop before attempting it on my server.  I was just hoping something already existed that's as easy as say ispConfig 3 where I'd have a GUI to create a workspace within a subdirectory of my website (e.g. [www.mysite.com/fileshare/]("http://www.mysite.com/fileshare/")), create a user, password, and directory, and then add R/W permissions to the folder.  I've seen a lot of info on the forums that working through the command line is more powerful, efficient, etc. but I'm really not there yet (and actually probably never will be).  I'll probably try ownCloud only because in the end having the GUI will probably be worth the setup headaches I'll experience being a non-programmer.  But if any of you have any other suggestions, I'm open.  Otherwise I'll remain silent until I've tried the above suggestions and ownCloud and posted my experience with all.  Thanks.

By the way, I spent hours in this and other forums setting up my server, I'd like to thank everyone who contributes their knowledge and experience.  I couldn't have pulled it off without people like you getting involved and I know other people in my situation feel the same.

---

### Post by lykwydchykyn on 2014-01-22
I'll second owncloud; it's pretty slick.  Yeah it probably has more features than you want, but I don't think you're going to find something with *just* the features you want and nothing else.

---

### Post by SeijiSensei on 2014-01-24
If you've configured your Apache server manually, I'd also suggest giving WebDAV a shot.  I set one up for the management committee of a client so they could exchange files easily and have them automatically backed up.  In Windows you can create a desktop icon that points to the shared directory, so copying files to and from the share is pretty simple.

If you need some more documentation, here's the section about DAV on the [Apache site]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html").

---

### Post by Robert_Boutin on 2014-01-26
Ok...  I tried the suggestions above but it became clear pretty quickly that they're above my head.  So I'm trying to install Pydio (Ajaxplorer) first because it seems to have the web interface I'm looking for and I want it to be as easy to use as possible for my users.  I ran into an install issue that I think should be easy to resolve, but it has me stumped.

I loaded all the Pydio files to web directory /var/www/mysite.com/web/upload/ and when I try to open mysite.com/upload, I get an error stating:  *Impossible write into the AJXP_DATA_PATH folder: Make sure to grant write access to this folder for your webserver!*

This is normal as the installation instruction states I need to then run  (as example) **chown -R www-data:www-data /var/www/pydio/data**

[FONT=arial]When I view the folder properties using nautilus, www-data is indeed the owner and group, but does not have write permission (and I can't change the permissions using the nautilus GUI).

So I opened a terminal window, logged in as root, and entered:  **[FONT=courier new]sudo chmod 770 /var/www/mysite.com/web/upload/data/[/FONT]**

Now when I check folder properties for "data", www-data has folder create/delete permission but still no file-level read/write permission.  I'm guessing I need that because I still get the same error after opening my browser (after clearing cache).  I am using Ubuntu 12.04.  How do I give the owner of the "data" folder file-level read/write permission?

Thanks (again)
[/FONT]

---

