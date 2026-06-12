---
title: "HOWTO: Setup Ampache for Music Streaming"
date: 2007-04-30
forum: Tutorials
---

### Post by zetsumei on 2007-04-30
**[SIZE="4"][COLOR="Red"]Setup Ampache for Music Streaming[/COLOR][/SIZE]**
**This was written for 7.04 Fiesty, so I'm not sure if it'll work the same on other versions.**



I know there are other tutorials for music streaming but heres one for Ampache, which is what I use.

1.)  First, you'll need a web server with mysql setup.  You can use LAMPP for that.  To get LAMPP, go [here]("http://www.apachefriends.org/en/xampp-linux.html").  Just follow the instructions on their site and you'll have a successful LAMPP install.

2.)  After you got a web server setup and working go to [http://ampache.org/downloads/ampache-3.3.3.1.tar.gz](http://ampache.org/downloads/ampache-3.3.3.1.tar.gz),  Moving on.

3.)  Once ampache-3.3.3.1 is downloaded, go to a terminal and type.

```
tar -xvfz ampache-3.3.3.1
```
this will untar it to a ampache-3.3.3.1 folder in your home directory or where ever you downloaded the file to.

4.)  Extract ampache-3.3.3.1 and move it to your htdocs directory of your webserver and go to [http://localhost/ampache-3.3.3.1](http://localhost/ampache-3.3.3.1).  Once there just follow the on screen instructions until you have it setup.  To move the folder to htdocs go to a terminal and type

```
sudo mv ampache-3.3.3.1 /opt/lampp/htdocs
```

changing the /opt/lampp/htdocs to the path to your htdocs for your webserver.

5.)  Once Ampache is setup.  Login and go to Admin>Catalog and click on Add a Catalog,  Fill in the name of the catalog and the absolute path to your music files.  Example: /home/bryce/Music would be what I would enter since my Music folder contains my music which is in my home directory.  Then once done, click on Add Catalog button.

6.)  Go back to the Admin>Catalog page and click on Add next to your catalog.  It'll take a while depending on how much music you have.  If you get any not readable errors go to a terminal window and type

```
chmod 755 pathtomusic/*
```

That should fix it.  Then just go and click add again to get the music in your catalog.

7.)  Once all that is done, just go look at your playlist and enjoy.

This is my first guide so don't be to harsh but tell me what you think about it.

---

### Post by zetsumei on 2007-05-01
If you don't like my guide just say so jeez.  I don't like being ignored when I write something like this.

---

### Post by ErikTheRed on 2007-05-02
Pretty good guide. You might consider throwing something in there about changing permissions on the files in the ampache folder to be more secure (although I don't exactly know how to do this, I'm new to this stuff too).

---

### Post by userthebuntu on 2007-05-06
Good tutorial.
Do you know anything about how to get an NTFS partition which is read-only for my ubuntu to work with ampache?
I don't have enough space on my linux partition to move my music about and then transform the NTFS partition into ext3 or w/e to make it readable for linux.

Anyone have an idea?

---

### Post by Jason Weiss on 2007-05-08
is there a way that I can get this to stream over the web?

so that I can listen to music form home at work>?

---

### Post by Jason Weiss on 2007-05-08
OH Please help me 

I am getting this error message in step 3

> Ampache.cfg.php Exists  	[ ERROR ]
Ampache.cfg.php Configured? 	[ ERROR ]
  	[Check for Config]


i followed this howto perfectly and I cannot get past step 3

---

### Post by rich.bradshaw on 2007-05-08
look at port forwarding on your router.

---

### Post by Jason Weiss on 2007-05-09
> **rich.bradshaw said:**
> look at port forwarding on your router.

Hmm I thought this problem may have related to writing to the sql database. 

Has anyone else seen this error?

---

### Post by Jason Weiss on 2007-05-10
ok 

these are the 2 pre requisites 

    >     *  A MySQL Server with a username and password that can create/modify databases
    * Your webserver has read access to the /sql/ampache.sql file and the /config/ampache.cfg.php.dist file



so this is the only place that I can see I am going wrong. 

can anyone give me a little advice here?

---

### Post by Nier1690 on 2007-05-13
Notice how it says **If access is denied it will prompt you to download the config file. Please put the downloaded config file in /config** Do just that down load the config file and move it to the config directory.

---

### Post by PoisoN2003 on 2007-06-21
When i try to go to step 3 it says error access denied

What should i do?

---

### Post by cjssmo on 2007-08-27
One thing you missed is that you need this in your /etc/apache2/conf.d

Alias /ampache /usr/share/ampache

<Directory /usr/share/ampache>
  Options FollowSymLinks
  AllowOverride Limit Options FileInfo
</Directory>


Regards

Charlie

---

### Post by cjssmo on 2007-08-27
PoisoN2003

Check the permissions of your music files needs to have read/right permissions

Hope this helps

Charlie  :)

---

### Post by cjssmo on 2007-08-27
For those having trouble with ampache you can post on the forum 

[http://ampache.org/forums/](http://ampache.org/forums/)

or 

go on IRC freenode #ampache

as they have much more knowledge about Ampache there than I do



Charlie

---

### Post by cancaseiro on 2012-01-30
First tutorial to set up ampache, and it worked, nice one zetsumei :)

---

