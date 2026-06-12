---
title: "In need of newbie server opinions."
date: 2011-09-08
forum: Server Platforms
---

### Post by virtualliquid on 2011-09-08
Hello all :) I am new here 1st post! 

Just got a couple of questions, I am attempting to set up ubuntu server, I just downloaded it and installed it on a computer, I am able to ssh into it as well as use winscp to access the file explorer. The webpage is up telling me it works on my LAN. My question is.. I am looking for a few good tools to use, I tried EHCP and did not like it as it is over done, but I do like some of the features such as phpmyadmin, and the system information page that tells me all the stats of my server. I know that I can install phpmyadmin separately, What I am looking for is something that will easily manage some of the php software I plan on installing. EHCP is a good idea but it is overkill for what I am doing.

I just want a simple, secure webpage capable of handling a "at home webserver", that has lots of easy to use system stats and information.

Hope this makes some sort of sense, thank you for all your help in advance :)

---

### Post by SlugSlug on 2011-09-09
maybe webmin is for you?

---

### Post by Lars Noodén on 2011-09-09
> **virtualliquid said:**
> I just want a simple, secure webpage capable of handling a "at home webserver", that has lots of easy to use system stats and information.

[Cacti](http://packages.ubuntu.com/natty/cacti) might give you the stats you want.

Also, instead of winscp you might want to look at FileZilla for SFTP.

---

### Post by cj13579 on 2011-09-09
> **SlugSlug said:**
> maybe webmin is for you?

+1 for Webmin 


Another stats thing that might be good for you (although not as thorough as cacti) is phpSysInfo: [http://sourceforge.net/projects/phpsysinfo/](http://sourceforge.net/projects/phpsysinfo/)

---

### Post by virtualliquid on 2011-09-09
Wow, these all seem to be very good addons, I am going to review each one, and then I will post back here :)

---

### Post by a2j on 2011-09-09
try webmin and let us know if you like it.
one at a time...

---

### Post by drdos2006 on 2011-09-09
As a newbie, here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



regards

---

### Post by Cheesemill on 2011-09-09
I'm not sure if Webmin is actually supported anymore using Ubuntu due to the way that Ubuntu uses different config file locations.

You could check out [Zentyal]("http://www.zentyal.org/") (formally eBox), it is very full featured but you only have to install the modules that you require.

---

### Post by virtualliquid on 2011-09-09
I installed Webmin, I had to modify a few file permissions to get it to work, but I got it to work, I have been playing with it for a few hours, it is very nice!! So far I was able to monitor my system stats and usage, as well as create extra partitions on the HD the OS is running on, and even view, modify and delete existing php database tables ( which is a big thing to me). I really like this addon thank you so much for recommending it, it is perfect for what I am doing :) 

Only problem I had with it so far was, it did not use the correct root username and password, I had to run ./changepass.pl /etc/webadmin root 1234 command to reset my root PW to 1234 so I could login and change it, other than that It is a very valuable addon.

---

### Post by CharlesA on 2011-09-10
last time I used webmin, it was able to use any user that has sudo rights. Is that not the case anymore?

---

### Post by virtualliquid on 2011-09-10
Yeah, that was my first problem, the user I was trying to login with did not have sudo rights, as I do not want to use my root user I had to make a new user with a new password and give that user sudo rights. I did not realize it did that on the installation by default. 

Sometimes I get way ahead of what I am doing and assume, rather then reading the instruction manual, and wonder why stuff is broken :P

---

