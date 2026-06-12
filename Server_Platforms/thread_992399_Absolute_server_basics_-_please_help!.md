---
title: "Absolute server basics - please help!"
date: 2008-11-24
forum: Server Platforms
---

### Post by doctorbighands on 2008-11-24
There seems to be so much confusing information out there about how to set up a home server, and I'm terribly lost. I'm hoping that I can have some consolidation within this one thread!

Here's what I have:

-An old PII beast with 256MB RAM
-Ubuntu desktop (not server) edition already installed on the beast
-A broadband (cable) connection with a wired/wireless router

Here's what I want:

-A server which can deliver files no matter where I am - at home or on the road
-A server that may, someday, host a website

I don't even know where to begin. I know I need Apache, but I wouldn't know how to do anything with it once it's installed. I probably should've installed Server edition, but I'm not comfortable on the CLI (for instance, I couldn't have come here and posted this thread from the CLI!).

I'm so dumb, I don't even know where in my network "chain" to place the server! Should my setup look like

Modem > Server > Router > Clients

or

Modem > Router > Server and Clients

?

I'd like the server to be headless, but I don't know if it's safe to unplug the peripherals once the machine is switched on.

If anyone out there has the constitution to step me through this in baby-talk terms, I would be eternally grateful. I know this stuff is painfully easy for a lot of you.

Thank you!!

---

### Post by spiderbatdad on 2008-11-24
clients< >modem>router>server

well...start with sudo apt-get install apache2 apache2.2-common

make sure it is running ```
sudo /etc/init.d/apache2 start
```

open your browser and type localhost into the address bar...let us know if you see "It Works!"

---

### Post by cdtech on 2008-11-24
Servers require less memory to run than a standard desktop computer. There are some security risk by using a GUI. If you want a top notch server with all the bells and whistle's you should start out with the server edition and read up on each area you would like to install. By installing the server edition you are starting out with a fairly secured system by default.

Installing the basic LAMP server gives you all the toy's your talking about. Using the command line is really a must for a very secure well maintained server.

Good luck.....

---

### Post by tuxxy on 2008-11-24
Have you tried the [server guide?]("https://help.ubuntu.com/8.04/serverguide/C/index.html")

---

### Post by spiderbatdad on 2008-11-24
server security can become a never ending obsession. the question you have to ask is how vital is it that no one, I don't want in, can get in? If the answer is very vital...you have yourself a full time job, all for the sake of having a little fun, hosting files, and playing with a web site...hardly worth it!
So I say, start with the basics and learn as you go. There is nothing wrong with using a gui as you learn about server config files, and apache, and openssh-servers. Employ basic auth for your apache server, and so long as you aren't hiding the secret to life the universe and everything on your server, you should be fine.

---

### Post by sam702 on 2008-11-24
I just started ubuntu last week.  I have somewhat intermediate experience with windows desktop platforms.  But this linux stuff is addictive like caffeine.  Actually, since I've taken on ubuntu, my caffeine dosage is insan.  Why?  There is so much information out there, so many different roast, it's crazy.  Trust you me, I've done much internet reading.  I would recommend you to get some Gunnar glasses for computer vision syndrome (CVS).

Anyway, here is my advice.  Read as much as you can on the internet, search as many forums as you can and follow/root through all the links in the forum thread.

Basic steps- 

1.  Be patience.

2.  Have another computer system that you can access the internet, make CD-rom, and print documents.

3.  Make sure your hardwares are Linux compatible.  Here is my setup.

Motherboard- ECS G33T-M2 @ $40
RAM- 8G, 4 2-G Corsair DDR2-800 @ $100 after mail-in-rebate
PSU- Corsair 450W ATX @ $70
CPU- Intel E6400 Core Duo @ free from a build 2 years ago
Hard Drives- 2 of SATA-II 300G Seagate 7200.10 @ free for previous build
CD/DVD rom-  Emperex @ $50
Monitor- old CRT @ free from a throw-a-way
Keyboard- PS/2 setup
Case- broke down ATX @ free from a throw-a-way

4.  Burn the Ubuntu Server CD from the ISO file you downloaded.  Make sure the downloaded file is good, using MD5sum check program.  Google MD5sum to learn more, read the ubuntu section (after you click on the download), there should be links on how to make the CD-rom from the ISO file and check the MD5sum with the hash number.

5.  Assemble/setup your computer.  Plug your computer to an active internet connection.  Make sure in the BIOS, you boot from the CD/DVD rom drive as your first boot.

6.  Insert in the the installation CD and power/restart your computer.

7.  Ubuntu installation starts, follow the instructions.  when you come to select application, use the spacebar to select File server Samba installation. 

8.  Ubuntu install properly.  You are at the login screen.  Sign in and you are now at the command prompt.

9.  Now you are ready to setup the file server.

Are you now here?

Be patience, I've installed and re-installed ubuntu server about 10 times to get a feel of what partitioning does with and without raid setup, what do auto partitioning do.

If you are at the command line.  Learn the basic commands-

make directories (file folders)
change folder ownerships
copy files
move files
edit using gedit or nano
install other applications

Bottom line is experiment.  Get comfortable.  Have fun.  Then re-install.  Learn some more and have some caffeine while you're at it.

to be continued......

---

### Post by doctorbighands on 2008-11-24
Okay, I installed Apache. It says it's using 127.0.1.1 for ServerName. I typed "localhost" into Opera, and It Works!

What's the next step?

To everyone who has commented so far: Thank you!!! I'm checking into the Ubuntu Server Guide as we speak (type?).

---

### Post by spiderbatdad on 2008-11-24
the folder apache accesses to view that simple html file called "index.html" is /var/www

Your apache config files are in /etc/apache2. Go to the folder /etc/apache2/sites-available. You will see a file called "default" make a file called "mysite" in the same directory and copy the contents of "default" to "mysite."
Then run the command: ```
sudo a2dissite default && sudo a2ensite mysite
```This leaves the default site as is, and gives you a template to build upon...it also tells apache to use "mysite" as the virtual host file. Next reload or restart apache anytime changes are made to configuration files: ```
sudo /etc/init.d/apache2 restart
```next add the option Indexes to "mysite" directory directives, after the document root section. ```
<Directory /var/www/>
                Options **Indexes** FollowSymLinks MultiViews
		AllowOverride none
		Order allow,deny
		allow from all
        </Directory>

```Then navigate to /var/www. move the index.html to your home folder if you want to save it. Instead put some files and or folders into /var/www. make sure they have permissions 644. Then go to localhost again...you should see the files you added to /var/www

---

### Post by spiderbatdad on 2008-11-24
Next, tell apache to require authorization before allowing access. Add the following to /etc/apache2/sites-available/mysite
```
DocumentRoot /var/www/
	<Directory />
               [B] AuthType Basic
                AuthName "Restricted Files"
                AuthUserFile /home/your_user_name/.htpasswords
                Require valid-user
		Options FollowSymLinks
		AllowOverride none[/B]
	</Directory>
	<Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
		AllowOverride none
		Order allow,deny
		allow from all
        </Directory>

```
Then create the password file and add a user with a single command. Note only use the -c option the first time you run the command...not to add additional users. Everytime the -c option is used, a new file will be written from scratch.

```
htpasswd -c /home/user_name/.htpasswords some_name
``` where user_name is your user name and some_name is a name you want to use to log in to apache. You will be prompted to create a password. .htpasswords will be created as a hidden file in your home directory...restart apache and go to localhost again...you should be prompted for login.

---

### Post by doctorbighands on 2008-11-24
> **spiderbatdad said:**
> Then navigate to /var/www. move the index.html to your home folder if you want to save it. Instead put some files and or folders into /var/www. make sure they have permissions 644. Then go to localhost again...you should see the files you added to /var/www

Gedit wouldn't let me save directly to /var/www, so I had to save to my home folder and use the mv command to move it.

When I type in "localhost" all it says is "It Works!" I added a text file to /var/www, but it isn't showing up.

Also, I have no concept of what "permissions 644" means.

EDIT: I have discovered that if I type in "127.0.1.1" into the browser instead of localhost, it shows me the contents of the /var/www folder.

---

### Post by spiderbatdad on 2008-11-24
I suspect your browser is showing you a cached page.

ok. if you are going to start out with a graphical text editor...which is fine, as you will easily see all the files, use the command```
gksu gedit /etc/var/www 
OR
gksu nautilus
```be careful, you are root with this command. so don't go browsing all kinds of system files as root in text editor mode. You can work on permissions graphically too, but it is more reliable via cli...navigate to the directory:```
cd /var/www
```look at permissions:```
ls -l
```rwx=read, write, execute, in the order of owner, group, other...hence rwx(owner)rwx(group)rwx(others). read=4, wite=2, execute=1. So from the cli, inside /var/www run:```
sudo chmod 644 *
```the star will treat all files in there. 644=rw r r

---

### Post by doctorbighands on 2008-11-24
I've done everything you've said so far (THANK YOU). When I tried to log into my new password-protected localhost, I received the following message:

```
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
```

EDIT: I should mention that I deleted the index.html file from /var/www. Was that stupid? Is that the reason for the 500 error?

---

### Post by doctorbighands on 2008-11-24
I know I'm nowhere near the finish line here, but I just wanted to pause and say how appreciative I am of the time and effort you're putting into this, spiderbatdad. I'm already learning SO much!

---

### Post by spiderbatdad on 2008-11-24
ok. this is where the fun starts. make sure "mysite" points to the .htpasswords file correctly...```
<VirtualHost *:80>
ServerAdmin <your email>
        ServerName <your_ip>
	
	DocumentRoot /var/www/
	<Directory />
                AuthType Basic
                AuthName "Restricted Files"
               ** AuthUserFile /home/docbighands/.htpasswords**
                Require valid-user
		Options FollowSymLinks
		AllowOverride none
	</Directory>
	<Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
		AllowOverride none
		Order allow,deny
		allow from all
        </Directory>
```

that the name match ie, /home/doc/.htpasswords vs. /home/doc/.htpassword

make sure .htpasswords has good permissions:
```
cd
ls -al
```should see .htpasswords rw r r. If not:```
chmod 644 .htpasswords
```

---

### Post by doctorbighands on 2008-11-24
I fixed it! This IS fun! :)

I copied/pasted from one of your posts, so instead of saying /home/nick/.htpasswords, it said /home/your_user_name/.htpasswords. I got a kick out of that.

Anyway, I now have access to my localhost.

---

### Post by spiderbatdad on 2008-11-24
remember to restart the server after making changes to the virtual hosts file, /etc/apache2/sites-available/mysite

---

### Post by doctorbighands on 2008-11-24
Apache has been restarted. What's next?

---

### Post by spiderbatdad on 2008-11-24
i suppose...the next step, if you like, is to tell your router to send http requests to your server machine. So in the terminal run```
 ifconfig
``` and make a note of your local ip address...perhaps:192.168.1.100 then run netstat -r and make a note of the route to your router...default gateway, perhaps 192.168.1.1   Finally use your browser and go to [www.whatismyip.com](www.whatismyip.com) to see your external ip address.

type the address of your router (192.168.1.1) into the address bar...input credentials as found here:[http://www.phenoelit-us.org/dpl/dpl.html](http://www.phenoelit-us.org/dpl/dpl.html)

figure out how to point the router on port 80 to your machine's ip address. usually under the games & applications menu. Create an administrative password for you router. save the router config. type your external ip into the address bar...nothing...lol. go back to "mysite" add **ServerName <your external ip>**
restart apache

---

### Post by doctorbighands on 2008-11-24
Where do I put the ServerName line? I've tried two different places, and neither seem to do the trick.

EDIT: I figured it out, and I was able to access the server from my laptop! Woohoo! :)


So, next question: How do I move files from my laptop onto my new server?

---

### Post by spiderbatdad on 2008-11-24
one way would be to install php5 from syynaptic, then enable the module in apache with```
sudo a2enmod php5
```you can the create an uploader program or use something much fancier like filethingie:[http://www.solitude.dk/filethingie/](http://www.solitude.dk/filethingie/)

a free file you can put in folders in /var/www/ to have a graphical file uploader/folder creator...read how to use filethingie. Also /etc/php5/apache2/php.ini will need a couple of minor tweaks, and /var/www will need permissions 777 for file thingie to work. You can also use post via a terminal...but that gets into more than I can easily cover here...especially with authentication...so read all about it in tutorials and man pages. Also getting started with ssh would be another solid way. Check the community docs.[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by spiderbatdad on 2008-11-24
looks like we've learned enough to cripple any computer system we own...next read all about how to secure apache and go crazy trying...lol. or learn how to create html pages. Any page named index.html in your root doc, /var/www will automatically be displayed. Also read all the apache documentation you can stand. There is way too much for me to even attempt to touch upon. This is truly a grain of information on a really big beach, but you are hosting files you can easily index and access from another machine. Beware of your router if it reboots and assigns a different ip to your machine...you will have to edit the router config...also your isp may periodically change your external ip. You can get service from dyndns to regiter a domain name instead of using the ip address and they have a service to reset your ip if it is changed by your isp. cheers.

---

### Post by doctorbighands on 2008-11-24
What are the necessary tweaks to the .ini file you mentioned?

---

### Post by doctorbighands on 2008-11-24
Thank you very, very much for all of your help. You truly have no idea how much I appreciate it.

I have registered with DynDNS, so that shouldn't be an issue. I have experience building web pages, so that shouldn't be an issue, either.

Thank you again. You're amazing.

---

### Post by spiderbatdad on 2008-11-24
not sure what if anything will be necessary in php5.ini...safe mode=off for sure, and you may need to point it to your apache2 root doc...just read through it if php isnt working for you. Filethingie faqs should get you going if you choose to use it. Thanks for all the kind words, but be sure your "server" is not inherently safe from hacking...if anyone, with the skill, would care to hack it. You can look into debootstrapping, but this requires rebuilding apache from source, and a bit of other work. You may want to look into it, if you get serious about web hosting. Right now you have a simple file server with http access.

---

