---
title: "Upload via FTP or SSH to apache2?"
date: 2007-05-23
forum: Server Platforms
---

### Post by a.d.gardiner on 2007-05-23
Hey all,

I'm running an Apache2 web server on ubuntu with MYQSL and PHP5 (+suhosin) installed.

I'm trying to configure my system so that I can allow a couple of friends to host their sites here.

The question is what the consensus opinion on the best way to do this?

I've had a good look around at existing methods and solutions, but I'm quite new to linux and wanted to know what others thought?

I thought about installing FTP.

But then I figured would it be possible, and more secure, for me to simply create 'limited' user accounts on my machine with their own home directory situated within /var/www/exampleusersite/ and allow them to SSH files in that way? Both of these guys will be using mac's to connect to the apache so I guess they can do it via command line in OS X or something like 'fugu ssh'.

Is this a seriously bad idea/insecure thing to do?

---

### Post by atoponce on 2007-05-23
I would **highly** recommend SSH over FTP.  First off, it's more secure.  Second, you only have to deal with one open port, instead of 2.  Third, it's just as easy, if not more so, using SSH.  Fourth, it's far more powerful.  SSH is just superior to FTP in every way.

---

### Post by a.d.gardiner on 2007-05-23
Fantastic! :) Thanks for the speedy info!

Have I got the wrong end of the stick though, or am I going about this the right way?

 I had planned to create as many users as I have sites hosted, giving each user account limited read/write access to their specified folder in /var/www/name-of-users-site/?

Is this standard procedure or would you recommend a specific tool to set this kinda thing up?

---

### Post by atoponce on 2007-05-23
I would recommend setting up limited user accounts, but having them build their account in /home/user rather than /var/www.  When the account is created, have it build a public_html folder, where they can host their site.  This way, they only have permissions in their respective home folder, and not anywhere else in the system, and if something goes south, it's just their home folder that needs to be rebuilt without touching other aspects of the filesystem.  Creating the new user will create the home folder anyway, so why not just have them host their site there?  [Check out this link]("http://www.brennan.id.au/13-Apache_Web_Server.html#users") for help on getting that setup with Apache.

---

### Post by a.d.gardiner on 2007-05-23
Many thanks! Will do.

You are a true gentleman :cool:

---

