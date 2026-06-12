---
title: "PHP file browsing"
date: 2006-01-19
forum: Server Platforms
---

### Post by sitara on 2006-01-19
I have a problem browsing PHP files on my Apache server. When I enter the address of a .php file, the browser doesn't know what to do with it. Konqueror opens the 'Open with..' dialog and Firefox asks 'What should Firefox do with this file?' - I don't know what to say! I can access HTML files on the same server with no problem.

I have been running Apache2, PHP5 and MYSQL quite successfully for several months, but yesterday I tried to do a couple of things:

1) Connect to my MYSQL database from Openoffice.
2) Install MYPHPMONEY.

I was unsuccessful on both counts, but in my efforts I installed and removed a few packages. 

The first problem I had with my PHP application was a message saying that 'mysql_connect' could not be found. I tried reinstalling MYSQL and PHP and APACHE, but just mad matters worse! Now I sit with the problem described at the top of this post.

The strange thing is that I have a PHP CLI app that is running quite happily as a cron job, accessing the MYSQL database.

One other symptom is that Synaptic cannot remove PHPMYADMIN. It gives me this error: 'E: phpmyadmin: subprocess pre-removal script returned error exit status 127'.

I don't know if it's relevant, but I also had a problem removing MYPHPMONEY. There was a message in the console saying that APACHE was being reloaded, then Synaptic hung. I restarted APACHE manually and the removal completed. 

Any help would be appreciated.

---

### Post by ZylGadis on 2006-01-19
What MySQL are you using?
In general it is safe for php4 to go with mysql4.x and for php5 to go with mysql5.x

Now to the matter in hand. I had a very similar problem recently. I am using apache2, php4 and mysql4 to run a phpbb forum. After the last synaptic update for apache2, I experienced exactly the same problem that you have - php files would be downloaded instead of executed on the server.
After several hours of uninstalling, reinstalling, reconfiguring and what not, I finally figured out that apparently the problem was on the **client** side. I accidentally accessed the server through firefox (I usually use epiphany and had used it to access the server before the update) and it went smoothly. Then I proceeded to clear epiphany's cache and it loaded the php page, too. I have no idea why it did so, but I was happy to solve the problem.

So here is my recommendation:
- uninstall everything related to php and apache - not just the "php" and "apache" packages. Rather, run a search in synaptic, and manually mark everything for removal.
- install back apache2, phpX and mysql. They will pull their dependencies with them. Also do not forget to install the php-mysql package whose exact name I don't remember right now.
- sudo dpkg-reconfigure <php-mysql-package> -- that will put it into the global php config file.
- configure apache to use php. As far as I remember, the ubuntu version of apache2 automatically loads everything necessary.
- clear the cache, cookies and what not of the browsers you are using. Or, alternatively, use a browser you have not used to access the site before the update (including ones on different machines).

That should fix the main problem with php. You can then proceed to install whatever else you need.
Good luck!

---

### Post by sitara on 2006-01-20
I eventually got things working here, but it was a bit messy!

I discovered that my /etc/apache2 directory was virtually empty. The /mods_available and /mods_enabled subdirectories didn't exist. I tried removing apache2, deleting the /etc/apache2 directory and re-installing, but it still didn't work.

Eventually I copied the entire /etc/apache2 directory from another server with the same config and now I'm up and running.

I would really like to understand what happened here if anyone can enlighten me!

---

### Post by kafkaian on 2006-12-28
I hjave the same problem when doing searches with Firefox on phpBB.com's search. I get a dialogue box "Open with" instead of obtaining the search results. Most frustrating

---

### Post by Brazen on 2006-12-28
Are you using Edgy?  I've heard of some funkiness with Edgy webservers.  Ubuntu Foundation has said to use Dapper for production servers.  Edgy contains some bleedig edge stuff that can cause funkiness.  Dapper is meant to be their rock solid server platform until the next LTS release.

---

