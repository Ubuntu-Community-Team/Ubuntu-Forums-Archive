---
title: "New to Ubuntu Server. Running 12.04 in VirtualBox, need some help..."
date: 2013-04-28
forum: Server Platforms
---

### Post by icebox83 on 2013-04-28
I've spent about ten hours with Ububtu Server 12 the past couple days just fooling around with commands, SSH, live WordPress hosting through port forwarding in my router, etc., but I'm having trouble figuring a few things out. My goal is to run a few low key websites I have built on WordPress from a physical box (I'm on a static IP) because my web hosting at a hundred bucks a year is really, really slow for WP. Some general questions I have in mind right now include the following:

Is Webmin an acceptable method of server management? Why or why not?
How can I set up FTP (or sFTP)?
How do I learn about virtual hosts...basically methods by which I can host multiple sites on the same server?
Are there any recommended books or video training series on familiarizing myself with Server?
Lastly, I am right to be running Ubuntu Server instead of something like XAMPP on Windows or Ubuntu Desktop?

Thanks!

---

### Post by brent1975 on 2013-04-30
icebox83, 
              First of all welcome to Ubuntu! lets go question at a time.

Should you use webmin or not use it?
Webmin is like buying a car. Some people like it others don't. I can honestly say when I first got into Linux on the server side I used webmin. It was great I could manage my server get security updates etc... After while I started getting errors and things breaking. I feel if you truly want to learn Linux and understand what is going on you are going to have to get into the terminal. Ubuntuforums is a really good resource.  Get an Idea what you want and ask. Someone will point you in the right direction with a tutorial or write up there own how too for you.

How to install FTP?
There are a few different packages you can use. I have personally used [COLOR=#282828][FONT=helvetica]vsftpd. a quick google search gave me this simple tutorial
[/FONT][/COLOR][https://www.digitalocean.com/community/articles/how-to-set-up-vsftpd-on-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-set-up-vsftpd-on-ubuntu-12-04) If you are wanting the users to access their webspace then you will have to change the home directory to be in /var/www/site1. it's pretty straight forward.

How to set up virtual hosts? I created a little how to for myself just using virtual hosts for subdomains. subdomain.domain.com you can use it just dont use the subdomain portion and use the different domain names for each site. [http://forums.kc-linux.com/index.php/topic/37-creating-subdomains-in-apache/](http://forums.kc-linux.com/index.php/topic/37-creating-subdomains-in-apache/)

books videos? I am sure there is alot of different books that you can check out from barnes and noble Amazon etc.... But why when you have the internet. Google should and will become your best friend when setting up your server. Ubuntu is a really popular Linux distro and every day company's are jumping on board with it.  I recommend that you utilize this site and google for all your request needs.

Windows vs Ubuntu server or Ubuntu Desktop.

Windows vs Linux as a server. This is going to be the battle between ford and Chevy. I personally have ran both and feel that Linux is so much smoother then windows. Bloat wise, resources, start up the list can go on and on. As far as using a desktop GUI vs actual server is up to you. I personally prefer the server. You don't need to have a desktop. Once you have the server configured you are going to throw it in a dark cold place with out a monitor keyboard and mouse. Actually after you have installed the server and have SSH setup you no longer need to be at the server to configure.... I would however recommend setting up a static IP address before doing anything else. This way you don't have to be sitting at the server configuring it. Do you really need those extra resources being used up with a GUI?  
At the end of the day it will be your decision. If you ask me I will say use Server version without webmin and say good bye to windows server.  :) 

Just make sure that if this is going to be a production server you stick with the LTS (long term support) version. current is 12.04 Which you are using.

---

### Post by darkod on 2013-04-30
I would say forget about webmin, the main reason being something I read a while ago (not sure if it still applies). I read that it changes config files not always how the programs/services expect them to be, so it can create issues for you.
Few days ago a friend had to restart his server and recover the apache config from backup because touching something in it with webmin corrupted it.

What do you need FTP for? If for your own personal use, to upload/download data and config files from time to time, forget about it too. I assume you will have SSH installed for administration, you can use WinSCP or even Filezilla with ssh.
WinSCP would be better since it can work with ssh keys, which Filezilla can't support. But in any case, if you try to connect on port 22 (or your ssh port if you changed it) with Filezilla, it will make a session over ssh.

Too bad it can't use keys since the best way is to disable password ssh login all together, and use only key authentication. definitely disable root login over ssh as soon as you install the server.

There is nothing much about vhosts on apache. But for more details there should be plenty of tutorials.

---

### Post by CharlesA on 2013-04-30
I used to use Webmin back on 9.04 when I was first learning about server management. Now I just use SSH to manage most of my stuff.

As far as FTP goes, unless you have a need for it, don't use it and use SFTP or SCP instead.

Filezilla supports keys, but only if they are passphraseless, at least that was how it was the last time I checked. I don't use Filezilla anymore and use WinSCP now (or rsync if I'm on a *nix box).

---

