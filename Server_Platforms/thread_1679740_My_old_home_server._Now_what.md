---
title: "My old home server. Now what?"
date: 2011-02-01
forum: Server Platforms
---

### Post by dustykeys on 2011-02-01
Hello everybody! My first post. I dont want to waste any time so here goes:
I had an old computer lying around so i decided to mess around with it and turn it into a server. The old computer had windows 98 on it but i chose to partition the whole drive during installation. So now it's just running ubuntu server only.

The version I installed from disk is "UBUNTU-10.10-server-i386.iso" because it's an old machine with 32bit architecture.

I personally want to use this server as one user (me) and I would like to host some of my own websites on it.

What do I do now to get websites on it?

Do I have to set up a DNS?
How do I upload my sites via SSH?
How do I organize the files?
I dont want to install a GUI because I heard they use unnecessary resources.

Specs of the server:
433mhz intel Celeron
9.6 GB ultra DMA HD
96 MB SDRAM

You dont have to try to explain everything. If you know of a guide, or link, or book that would help i'll gladly research it myself.

Thank You!

ps I have zero experience with linux and linux server. i have a few sites of my own but they're all managed via cpanel.

---

### Post by rubylaser on 2011-02-01
That's going to be an endeavor :)  You'll need to install the programming language of your choice, and your database (if your application is backed by a database), then choose a webserver you'd like to run (Apache, Lighttpd, Nginx, etc.).  

To have a website on the internet, you will need a DNS entry for each website you'll run. You'd set this up with your Domain Registrar, unless you choose to manager you're own DNS.

You can upload your sites via any transfer protocol, but scp (secure copy), sftp (ssh file transfer protocol) are what I use.

Normally with Apache, you'd put your files into /var/www, and chown them to the user and group  www-data:www-data.  So, I'd put all my files in that directory.

With the amount of resources you have in that box, I wouldn't recommend trying an GUI, and frankly Apache might be too heavy too.  You'll probably want to try nginx or lighttpd for your webserver.

Google will probably be your best friend for learning. Good luck.

---

### Post by wojox on 2011-02-01
Have a read [Ubuntu Server Guide]("https://help.ubuntu.com/10.10/serverguide/C/index.html")

---

### Post by ozanamn on 2011-02-01
Hey

here is a download-able Linux Apache server

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

Everything you need is here. It has sql and php guides you through setting up your security. 

I have used it in the past and is very good.

Enjoy.

Oz

---

### Post by dustykeys on 2011-02-01
Thanks for the info. I'll check out the resources and come back with some more detailed questions later. probably much later. Slow learner :redface:

btw - i chose the LAMP option when installing the server from the CD. I have SSH installed also.

how will the DNS work? When installing sites on a server i had to assign a url to my vps. Then point the url to the it. Like this:
NS1.myserverurl.com
NS2.myserverurl.com

How do I set that up on my server? In other words how do I assign myserverurl.com in my home server?

Then I can go to my registrar and point the url to my server right?

Thanks

---

### Post by YesWeCan on 2011-02-01
96MB RAM?
You are lucky to have been able to install Ubuntu at all.

---

### Post by dustykeys on 2011-02-01
pretty weak huh? it was lying around collecting dust so instead of adding to the land fill I decided to use it. I'm not sure if I can get an upgrade but that could be an option. I just need to learn how to run a website on it first then i'll have a better idea of it's capabilities.

---

### Post by drdos2006 on 2011-02-01
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by YesWeCan on 2011-02-01
I am fully behind your desire to reuse. Good on you.
There is a chance it will cease up and if it does you may need to investigate a lighter Linux variant. But you may just get away with it too so go for it.
I am not expert on web servers. Obviously you will need to install one, such as Apache or Glassfish. I have some experience with Glassfish and like it. You are after as light-weight a server as you can find. Hopefully a more knowledgeable reader will have some suggestions.

---

### Post by dustykeys on 2011-02-01
Thanks for all the helpful tidbits. After I  find time to research and play around with it i'll come back with the results and inevitably more questions.

---

### Post by dustykeys on 2011-02-03
@yeswecan
I think you're right about it ceasing up. I'm trying to set up my ip. I type this:
sudo vi /etc/network/interfaces
hit enter and a bunch of tildes go down the screen and the word "recording" at the bottom. 

I guess i need to look into upgrading the ram?

---

