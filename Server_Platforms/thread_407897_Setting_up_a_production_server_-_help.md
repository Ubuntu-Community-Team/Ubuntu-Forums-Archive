---
title: "Setting up a production server - help"
date: 2007-04-12
forum: Server Platforms
---

### Post by v8YKxgHe on 2007-04-12
Hey,

I've just brought VPS hosting as I want more freedom that you don't get with a shared hosting, such as full root access via SSH. 

I have setup a small LAMP server before on my local PC, how ever I need help setting it up on a production server. I really have no idea where to put things (such as main htdocs, svn) and how to setup the users, which users can FTP etc?

I would be highly grateful if someone could guide me into setting up a production server for:
[LIST]
[*]Apache2
[*]MySQL
[*]PHP5
[*]SVN repository
[*]FTP
[/LIST]

Then how to setup the users and groups and what users have access to. I also have limited SVN knowledge, but am going to spend tomorrow learning how to use it.

Regards

---

### Post by BitHosts on 2007-04-12
Ubuntu server comes with a LAMP installation option - Linux Apache Mysql Php - Id go down that route and then find a "How To" for the rest of the things your looking to install.  Search this forum, Im ever amazed at how many good quides there are already here.

---

### Post by v8YKxgHe on 2007-04-13
I don't have the option to install LAMP as it's an automated proccess install (which takes around 2 mins to complete!) of any distro I want (well, out of the list they give).

I am wondering, is the [Perfect Ubuntu 6.10 Server]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10") guide any good?

---

### Post by BitHosts on 2007-04-13
Erm, upgrades from 6.10 to 7.04 arent gaurenteed to run as smoothly as we may like, until 7.04 is released i would go with 6.06.

In that case I would google each of the how tos your looking for.  Read through it first - if your happy you understand all the steps then save it, find the rest of your how tos and then run them one after the other.

---

### Post by v8YKxgHe on 2007-04-13
hum? I'm not running 7.04 on the server, it'll be 6.10 ...  may switch to 6.06 though.

My main concern is where to put stuff, what users and groups to create?

---

### Post by BitHosts on 2007-04-13
6.06 is an LTS version, 6.10 isnt - LTS = Long Term Support

Useful for production servers - 7.04 is the next LTS version to be released and hopefully will be out in the next week or two.

Basically the upgrade process needs to be smoother because otherwise itll mess alot of people around - the upgrade to 6.10 from 6.06 was a little shakey depending on how you had things set up.

---

### Post by v8YKxgHe on 2007-04-13
7.04 is not the next LTS, 7.10 isn't even LTS. 8.04 is though, how ever.

---

### Post by BitHosts on 2007-04-13
Oh... why have i got that in my head then - nevermind.  Anyway - you know what im trying to get at.

---

### Post by v8YKxgHe on 2007-04-13
hehe yeah, I've just upgraded ... downgraded what ever you want to call it, to 6.06. About to install LAMP now, however do I need to create extra users/groups? who should have access to /var/www? How would I add more FTP users (IIRC, they are just system users?)

This is what I need a guide on, I can setup Apache, PHP and MySQL fine, that bit is easy ... but it's more of the who/what and where I need help with :P

---

### Post by BitHosts on 2007-04-13
hmmm - depends how you set it up.  I believe you can set most services up so that they use SQL for authentication.

Ive gotta dissapear now - but if no one else has pointed you in the right direction ill see what i ccan do later on.

---

### Post by v8YKxgHe on 2007-04-13
Thanks, would be great if you could.

---

### Post by MilesZS on 2007-04-13
I'll see if I can help a bit, as I am also setting up a VPS at the moment.  Out of curiosity, what host did you go with?

Are you intending to host multiple sites on the VPS?  In this case you will need to use Apache's virtual hosts abilities.  Luckily, the userdir mod is typically enabled by default, and Apache2 is typically set up to utilize virtual hosts when installed via apt-get. 

I don't know where a guide is, right off hand, but if you look around in your apache's base directory (likely /etc/apache2), you should see the directories sites-enabled and sites-available.  Within sites-available is a default virtual host file that you can use as an example.  So, unless I am mistaken (stranger things happen daily), you will first need to create a new user for each site you will create.  In their home directory, you'll need a 'public_html' file (where their website files will go).  You'll need to also create a new file for them in the 'sites-available' directory, modeled after 'default'.  Use the command 'a2ensite' to enable that site (basically just creates a symbolic link to 'sites-enabled', but it's a cool sounding command... and it saves some keystrokes).  

Typically, I would say you would want to create a different user for each MySQL database, and only allow that user to access that database in particular.  You don't want your scripts using a super user, or even a user with more-than-the-usual rights.  

If I just told you a bunch of crap you already knew, I'm sorry.  I hope this helps though.  It helped me to go through it explicitly, actually.  I have to write some automation scripts for this stuff.  (Designers don't want to spend too much time looking at the ugly command line interface.)

---

### Post by v8YKxgHe on 2007-04-13
Hey Miles,

I went with VPSLink on their link-3 plan, how about you?

Thanks for the help, I'll be hosting 2/3 websites so I should create 2/3 more users and give them a home folder of /home/username - in each of those then create a public_html directory, correct?

I'm going to play around with that.

---

### Post by MilesZS on 2007-04-13
> **AlexC_ said:**
> Hey Miles,

I went with VPSLink on their link-3 plan, how about you?

Thanks for the help, I'll be hosting 2/3 websites so I should create 2/3 more users and give them a home folder of /home/username - in each of those then create a public_html directory, correct?

I'm going to play around with that.

I am currently with Slicehost.com, using their largest 'slice'.  In fact, you might look around their wiki/forums, as there is some decent information there.

If you were to run the command 
```
adduser --ingroup=[basic_user_group] [new_user_name]
```

It will create the home directory for you.  You'll just need to make the public_html directory.

---

### Post by pjbgravely on 2007-04-13
Have you read [Ubuntu Server Guide?]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html")

If so then there are simpler and more complete ones out there. There is also lots of Howto's here in this forum. 

Apache2 in Debian/Ubuntu is a lot different than other distributions, there is a specific how to included with the package.

Paul

---

