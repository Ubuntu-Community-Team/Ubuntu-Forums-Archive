---
title: "need help understanding server options"
date: 2008-07-22
forum: Server Platforms
---

### Post by govee on 2008-07-22
I guess some backround first. I built a home server(Xubuntu 8.04) for my family that lives behind my firewall. I use samba for file share (I have desktop OS's from linux to win 2000, XP , and Vista). I access the server with VNC through an SSH tunnel. All has worked well, but recently we started building a house and our first grandchild was born, so we have the need to show pictures to a family that is spread all accross the US. 

I have spent a couple weeks trying to understand the options available to host a "Website" so we can share pictures. I don't know if that is even right sense I would like to give others the chance to upload photos as well.

I want this to be as secure as possible (I am constrained by a limited knowledge base) without being complicated. I have read using Apache 2 I can run a virtual host or use VMserver to obtain a level of security that would let me sleep at night.

I dont mind searching but I am not sure what the right terms to search for are in this case. Do I need webhosting or FTP? what are my options? with the number of Wikis or Blogs I am sure someone has done this with ubuntu, I am just not finding the site that makes the light come on.

Thanks.

---

### Post by sp0nge on 2008-07-24
IMHO, this depends on several variables that you need to specify. 

There are many places that you can get free hosting from with enough space to do what you're trying to accomplish. My ISP gives some web space as well. These are most likely better options than hosting your own as server security is quite the nightmare (as I'm learning by experience). 

What's more, you can log on to Yahoo. Start a group for your family and upload your pictures there. If you really want to serve the data yourself, it's possible and a lot of fun. I just suggest these options not to talk you out of learning, but to show the alternatives that exist.

---

### Post by dfreer on 2008-07-24
Indeed, it's probably far better for you to use a hosting service (a site that provides the space and bandwidth), where you can simply upload the pictures.

However, if you really want to run your website entirely from your home internet connection, you'll need to check a few things first before you even begin worrying about security:
(1). Does my ISP allow incoming port 80? If not, is there another incoming port that I can use like port 8080?
(2). Do I have sufficient upload bandwidth to be able to accomplish what I need?
(3). Do I have a hardware firewall between my server and the Internet, and can I access it to open up the incoming ports I need?

---

### Post by tinny on 2008-07-24
I dont think there is any reason for you to have to host this yourself. There are plenty of free services available.

Have a look at Picasa

[http://picasaweb.google.com/](http://picasaweb.google.com/)

You can create "Unlisted" photo albums that you can control access too.

---

### Post by erwall on 2008-07-24
I've had much success with gallery2, [http://gallery.menalto.com](http://gallery.menalto.com)

---

### Post by govee on 2008-07-25
I realized I was still using the argument that I use with the boss lady when I start a project. Give her the WIFM (Whats in it For Me). I do want to learn to do this!!! There I admited it. I am taking baby steps. I built a SAMBA server and it works well. I am taking the next step. I installed Apache and PHP. I can access the /var/www from my lan and I have just port forwarded 80to the Static IP of my server and I have internet access. 

While I build the site I am finishing figuring out dynamic IP configuration. I curently do not have a static IP and If the Dynamic IP support is easy enough, I amy live with an ocassional nuisance. 
I will jump to FTP last.
Do I have a physical Firewall? If by that I can answer yes because I have a netgear 4 port wireless modem. Then yes.

Sufficient upload bandwidth? I have a cable broadband and since most of my family is on 56K modem, I think the point will be moot.

Checking into No-IP

---

### Post by bab1 on 2008-07-25
How about a middle of the road approach?  Run your web server as an internal testbed for your web pages.  When you have what you want the family to see, you can publish them at a comercial hosting site.

---

### Post by tinny on 2008-07-26
> **govee said:**
> I realized I was still using the argument that I use with the boss lady when I start a project. Give her the WIFM (Whats in it For Me). I do want to learn to do this!!! 

:lolflag: I think I know what you mean.

This stuff is cool to play with, but you need to sell the idea to the boss.

If this is the case then ive been though the same experience. I managed to sell a Mythbuthu install to my lady boss. WIFM = clear TV with scheduled recordings etc. Little did she know that I was enjoying every minute hacking around with linux :)

So you want to do it all yourself, good one!

To get something up and running that does the job I think you will need the following.

[Dynamic DNS]("http://www.dyndns.com/services/dns/dyndns/") to allow you to point a domain name to your dynamic IP address.

What is the specific model of router you have? If you are not 100% happy with the level of security it provides you could setup a firewall on your server machine.

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

Sounds to me like you have the basics under your belt...right? (E.g. LAMP server stuff)

I think that setting up Drupal could be for you. Here is a Tutorial that I found that looks good.

[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

Also check out the Drupal official documentation.

[http://drupal.org/handbooks](http://drupal.org/handbooks)

---

### Post by songshu on 2008-07-26
drupal as mentioned earlier is a nice set up, personally i have good experience with Joomla wich basically does the same thing, there are a lot of options and very user friendly to use (also for your relatives if you give them an account) to make new web pages where they can blog and upload pictures etc...

---

### Post by antilog on 2008-07-26
> **tinny said:**
> I dont think there is any reason for you to have to host this yourself. There are plenty of free services available.

Have a look at Picasa

[http://picasaweb.google.com/](http://picasaweb.google.com/)

You can create "Unlisted" photo albums that you can control access too.

I second that idea.  I use it after using Gallery and other solutions.  Picassa Web Albums is bar far the easiest and quickest to use.  Of course, it integrates with Picassa, so choosing and uploading pictures is easy.

BTW - I run 4 websites using Apache2 VirtualHosts on a Ubuntu Server 8.04.1 virtual machine running on an Ubuntu Server 8.04.1 host.  It took a bit of time getting the virtualhosts to work, due to the large amount of conflicting info in tutorials and wikis, and of course my own lack of experience.

---

### Post by songshu on 2008-07-26
> **antilog said:**
> I second that idea.  I use it after using Gallery and other solutions.  Picassa Web Albums is bar far the easiest and quickest to use.  Of course, it integrates with Picassa, so choosing and uploading pictures is easy.

BTW - I run 4 websites using Apache2 VirtualHosts on a Ubuntu Server 8.04.1 virtual machine running on an Ubuntu Server 8.04.1 host.  It took a bit of time getting the virtualhosts to work, due to the large amount of conflicting info in tutorials and wikis, and of course my own lack of experience.

i definitely would like to -1 that idea, if that would be sensible reasoning there would be very little left in life to accomplish things and learn new things. Why have hobbies at all, its only bothersome after all.

As the topic starter already mentioned its a fun thing to do, and it is certainly a most satisfying learning experience and a nice result in the end to be proud of.

By the way, ever since i've learned to set up such things myself i really can't be bothered with these dreadful online registration forms, i never get these captchas right in one go anyway, and my favorite pet? Even thinking of a new name cause mine is already taken takes me more time to install it myself ;)

---

### Post by govee on 2008-07-26
> If this is the case then ive been though the same experience. I managed to sell a Mythbuthu install to my lady boss. WIFM = clear TV with scheduled recordings etc. Little did she know that I was enjoying every minute hacking around with linux 

:lolflag: I used this arguement often. Just recently built a Touchscreen Jukebox(MP3 Player) out of a 1970ish Admiral stereo. She loves it and I got to play with a 15" ELO touchscreen and reuse a throw away stereo (I am green too!:KS).

> What is the specific model of router you have? If you are not 100% happy with the level of security it provides you could setup a firewall on your server machine.
Netgear WGR614 V6. I know that I am not smart enough to determine wether or not my router should be repaced in referencre to net, firewall, and wireless performance. 

I spent some more time with the help of Siteaid writing the webpages and all is progressing. I know that's a windows program, but my only laptop with linux has a bad power recepticle.

The curent server is headless, but I am trying to do everything on the server through CLI or FTP. In the end I want to strip out the X desktop or atleast stop it from auto starting at startup. How do I accomplish that?

Pressing on......

---

### Post by windependence on 2008-07-26
X shouldn't be installed if you loaded server.

For web developement try Kompozer. 

[http://www.kompozer.net/](http://www.kompozer.net/)

-Tim

---

### Post by tinny on 2008-07-26
Are you using Gnome, KDE or XFCE?

For Gnome....

```

sudo aptitude remove ubuntu-desktop

```

For KDE...

```

sudo aptitude remove kubuntu-desktop

```

For XFCE...

```

sudo aptitude remove xubuntu-desktop

```

---

### Post by govee on 2008-07-26
Thanks,
I have XFCE (Xubuntu)

---

### Post by tinny on 2008-07-27
Sounds like you have decided to go with static web pages, right?

As mentioned earlier [KompoZer]("http://kompozer.sourceforge.net/") is a good web page development tool and is available from the Ubuntu repositories.

You will also want to implement a basic security mechanism for authentication.

Have a look at [Apache Basic Authentication]("http://httpd.apache.org/docs/2.2/howto/auth.html") (what version of apache are you using? 2.2?)

Basically you create a password file and add users.

This command creates a password file and adds one user.
```

sudo htpasswd -c /www/passwords/passwd user_name

```

Add a second user
```

sudo htpasswd /www/passwords/passwd user_name

```

Then you need to protect your web directory, something like...
```

<Directory /www/docs/private>
AuthName "Private"
AuthType Basic
AuthBasicProvider file
AuthUserFile /www/passwords/passwd
Require valid-user 
</Directory>

```

The above should work, but have a read of the docs :)

---

### Post by govee on 2008-07-27
Late last night I went through the process of creating a dyndns account and loaded ddclient. I am happy to report that I accidently got it working! I did have problems with the last question on ddclient config setup, "What Interface does DYNDNS use?" I accidently ended the setup program before I answered and ddclient failed due to an a problem at line 7 of the config. After some searching I ended up back at the DNS site and used the line from thier sample config. I coded Sudo ddclient and it reported sucessfully updating my domain with my external IP. :guitar: 
I am now going to research if this process is automated, or do I have to setup something further to automate it.:-k

> Sounds like you have decided to go with static web pages, right?

Darn it. It is questions like that, that make the new car smell on me really bad. I dont know how to answer that.:(

KomPozer looks really nice. I like the on the fly option. I travel for my work a lot and being able to automate the process of grabbing the site as it exsists on the net is awesome. I see that I will to do the ftp server, but thats ok, I wanted to try that any way.  

thanks

---

### Post by tinny on 2008-07-27
If your developing HTML files then your doing static web pages, nothing wrong with that.

---

### Post by govee on 2008-07-27
Ok, thanks Tinny. I have learned another term for the tool box.

I spent some time reading about Drupal and it looks like an ineresting package. It appears that it could do all the things I was asking about and more, website, and picture hosting? I have a couple of questions about it. 
If I use does that mean I am not using static web pages? 
In the how to link is shows all the programs for a LAMP server. I did not instal mysql or php for mysql. Do I need them to try out Drupal? 

I was playing aroun with kompozer It loks as though I would have to have a FTP server running to get access to the site for downloading and uploading. Is that right?


thanks

---

### Post by tinny on 2008-07-27
> 
I spent some time reading about Drupal and it looks like an ineresting package. It appears that it could do all the things I was asking about and more, website, and picture hosting? I have a couple of questions about it. 
If I use does that mean I am not using static web pages? 


Yes. But dont get hung up on the whole Dynamic / Static thing.
A Dynamic page is just one thats HTML code is generated by some "code behind" the scenes. (in Drupals case PHP) 

> 
In the how to link is shows all the programs for a LAMP server. I did not instal mysql or php for mysql. Do I need them to try out Drupal? 


Yes, Drupal requires Apache, PHP and MySQL (or PostgreSQL). LAMP install on Ubuntu Hardy...

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install apache2 php5 mysql-server-5.0

```

> 
I was playing aroun with kompozer It loks as though I would have to have a FTP server running to get access to the site for downloading and uploading. Is that right?


Yes this is one way. You could also use SSH. Are you using a Ubuntu desktop for your development? If so you can connect to your server using SSH and drag and drop your files in place. (Something like "Places" > "Connect to server")

Also FileZilla can be used as a FTP client or SSH client.

---

### Post by govee on 2008-07-27
I am using XFCE so I am not quite sure what you mean. My server is headless and I acess it with Putty and I when I have to I VNC. I do use WINSCP from my desktop/Laptop until I get my Linux Laptop up and running.

---

### Post by govee on 2008-07-28
I need to correct the "user" and "Password" for the DB I created in mysql for Drupal so I can configure Drupal or replace it. How do I code the correction in CLI? Or do I just redo the adding of the DB?

---

### Post by tinny on 2008-07-28
> **govee said:**
> I need to correct the "user" and "Password" for the DB I created in mysql for Drupal so I can configure Drupal or replace it. How do I code the correction in CLI? Or do I just redo the adding of the DB?

For MySQL admin I would suggest you look at the [MySQL GUI Tools]("http://dev.mysql.com/downloads/gui-tools/5.0.html").

From here you could "drop" that DB and recreate it. Use MySQL query browser to execute SQL scripts.

---

