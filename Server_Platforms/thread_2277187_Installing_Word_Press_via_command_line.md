---
title: "Installing Word Press via command line"
date: 2015-05-07
forum: Server Platforms
---

### Post by Mike_Hughes on 2015-05-07
[COLOR=#000000][FONT=UICTFontTextStyleBody]I have seen several YouTube Videos on installing Word Press. All show Word Press being installed and the MySQL data base being set up with a GUI. I need an installation recipe using command line from a terminal. Also what free panel would you use on an Ubuntu 14.04 Server?

Mike Hughes[/FONT][/COLOR]

---

### Post by tgalati4 on 2015-05-07
Did you read through these instructions?  [https://codex.wordpress.org/Installing_WordPress#Detailed_Instructions](https://codex.wordpress.org/Installing_WordPress#Detailed_Instructions)

There's a section for installing using the *mysql* command-line client.  I use *ssh* to monitor and perform server maintenance.

I'm confused.  You don't want to use the GUI to install this service but you want to use a GUI to monitor it?

---

### Post by Mike_Hughes on 2015-05-07
I am running this server headless. So that is why I can't use GUI to install. I have 6 websites on this server. right now need two Word Press installs. I was wanting to use a Panel to setup clients database and install Word Press in thei Directory and give them the "keys" so to speak from there. I want to change my current Website - [www.mikealrhuges.com](www.mikealrhuges.com), hosted on this machine to a word press site. Hope that helps with the confussion.

---

### Post by tgalati4 on 2015-05-07
For a headless server, I like to use *tasksel* and install the LAMP stack.  That gives you a working apache, mysql, php, etc.  Then you can follow the wordpress instructions to install using the webpage GUI wordpress installer.  To me, that is the easiest way to do it.  Of course you need another machine to view the web pages and configure the wordpress service.

```
sudo apt-get install tasksel
sudo tasksel
```

---

### Post by Doug S on 2015-05-07
Wordpress installation and setup is covered in the [Ubuntu Serverguide]("https://help.ubuntu.com/lts/serverguide/wordpress.html"). It is a relatively new chapter, and I was the proofreader, and installed and got it working with only the one reference and all via SSH to my test server.

---

### Post by Mike_Hughes on 2015-05-08
What I have is a Web Server with 6 websites on it. I want to convert my website [www.mikealrhughes.com](www.mikealrhughes.com) to a word press site. I know a couple of others whose websites I host want to as well. So there will be at least 3 different Word Press sites going. Will that make a difference how I install? I am thinking it might. Any ideas with that info?

---

### Post by SeijiSensei on 2015-05-08
I have two WordPress blogs.  All I needed to do was unpack the WP zip file into the appropriate directory for each site.  In the Apache .conf file defining the virtual host I pointed the DocumentRoot to the Wordpress directory, restarted Apache, then ran the GUI installer from a browser.  

When you say "from the command line," surely you still intend to run the native WP configuration script with a web browser, right?  I can't imagine trying to track down all the individual settings in their individual configuration files and editing those files from the command prompt.

---

### Post by Mike_Hughes on 2015-05-08
Ok, I found this one. 
[https://www.digitalocean.com/community/tutorials/how-to-set-up-multiple-wordpress-sites-on-a-single-ubuntu-vps?comment=32121](https://www.digitalocean.com/community/tutorials/how-to-set-up-multiple-wordpress-sites-on-a-single-ubuntu-vps?comment=32121)
This one is closer to what I am trying to do. I have 6 sites on my current Ubuntu 14.04 Server. If this was just one site on the box I think the one you sent me would work. I want my site moved to a Word Press type site. I am sure some of my other clients will want to do the same. I tried to go by the instructions above  and ran into error messages. 

Here is what I am trying to do:

I am trying to locate my Word Press files at = var/www/mikealrhughes.com/wp_mikealrhughes.com

my home directory is - /home/macmike

my SQL database is - eacmikedatabase

I had trouble when I tried to setup the MySQL user - create user macmike@localhost;

Any help appreciated.

Mike Hughes

---

### Post by Habitual on 2015-05-08
[The Famous 5-Minute Installation]("https://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install")

---

### Post by Mike_Hughes on 2015-05-12
Ok I finally got Word Press loaded onto my server. I have been watching Morten Hendrickson on Lynda.com trying to get up to speed on this program. I host my own Web Sites 6 of them. I currently have a Web Site with Word Press. I have tried to do two things. I wanted to load the InfiniteWP plugin thinking that might make it easier to manage Word Press especially when some of my clients want to host a Word Press page. I also have Webmin installed. When I try to upload the iwp plugin I get this error message - Unable to create directory wp-content/uploads/2015/05. Is its parent directory writable by the server? Which leads me to believe I have a permissions problem. I used FileZilla and change permissions on the wp-content directory to 755 and recursed it to directories below it. I still get the same message unable to create directory wp-content/uploads/2015/05. Is its parent directory writable by the server? I don't know where to go set permissions so this will work. Apparently I don't know how to make the directory writable by there server. Any ideas appreciated. Who do I change ownership too for this parent directory? I currently have the directories set to 755 permissions.

Next issue is with FTP. I wanted to upload a new Theme from WordPress.org called DarkElements 2.4 I get this message - Unable to locate WordPress Content directory (wp-content). So how do I set the location for WordPress Content Directory?
Any and all help gratefully appreciated.

I had an issue yesterday not being able to sudo su into my Ubuntu Server so I had to reinstall the software. I reinstalled Word Press fresh again using the instructions from site Calle digital ocean. Called installing word press for multi-user use. All the install goes ok until I get to this line. sudo user do -a -G www-data linux_user_name. I am not sure who the linux_user_name is suppose to be. That is the only line that I can think of causing my issue. I have tried to upload themes, plugins and get can't create directory. So I must either have the wrong owner set for Wordpress or the permissions are wrong. Permissions on directories are set to 755. Any ideas?

Problem with that one. That assumes you only have one site on your server. I have 6 sites currently on my Server.

mike

---

### Post by Ron_Greve on 2015-05-14
Hi,

I just change owner ship of all files to www-data:www-data (my web server). 

chown -R www-data:www-data

These are the notes I made for my installation:
mysql -u root -p
create database myblog;
create user [EMAIL="myblog@localhost"]myblog@localhost[/EMAIL] identified by 'Some password here';
GRANT ALL PRIVILEGES ON myblog.* TO my[EMAIL="myblog@localhost"]blog@localhost[/EMAIL];



[LIST]
[*] Files must be owned (group and user) by web server.
[*] Make sure a directory wordpress/wp-content/uploads exists again owned by the web server
[*] Make sure that directory is set in Settings->Media->Store uploads in this folder in the GUI
[/LIST]

Regards, Ron

---

### Post by SeijiSensei on 2015-05-14
I run two WP sites on the same server.  Each one resides in a separate DocumentRoot.  Each has its own unpacked version of the [latest WordPress zip file]("https://wordpress.org/latest.zip"), and each has a separate database.

---

### Post by Mike_Hughes on 2015-05-16
What do I need to do to get the server to send email?

---

### Post by Ron_Greve on 2015-05-17
Login in as admin on the site->settings->email address

Obiously you need to have mail working from the command line

echo "Hello" |me@example.com

If that doesn't work setup/install postfix/dovecot (installation depends whether it just relays it to another mail server or you own a domain and this is your mail server).

Regards, Ron

---

