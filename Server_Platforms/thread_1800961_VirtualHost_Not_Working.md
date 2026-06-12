---
title: "VirtualHost Not Working?"
date: 2011-07-09
forum: Server Platforms
---

### Post by jmalz on 2011-07-09
Hello World!

I've been reading tons of tutorials, blogs and googled sites but I can't get this to work! :( I've even watched videos on youtube for help! I'be been at this for 2 weeks off and on using virtualbox and now with a stand alone box.

So I've been trying to figure what exactly it is that I'm doing wrong with NameVirtualHost's in apache2, and why it's not showing any other site besides the default "It works" page. I own 2 domains that are being forwarded with masking since I can't use port 80 (ISP blocks this port) to my routers public IP address, and I'm forwarding all the ports for the server.

My IP looks like:
```
1.23.345.678:81
```Here's what I've done so far:

Installed LAMP using apache v2.2.17 and webmin (working fine)

I then create the directories for my sites using:
```
mkdir -p /var/www/site1
mkdir -p /var/www/site2
```I add a user so I can FTP files to the "www" folder
```
chown -R user:user /var/www
```Ok, so after that I create 2 separate files in /etc/apache2/sites-available, called "site1" and "site2", then I add the directives for the sites
```
<VirtualHost *>
        ServerName site1.net
        ServerAlias www.site1.net
    DocumentRoot /var/www/site1
</VirtualHost
```and the other

```
<VirtualHost *>
        ServerName site2.com
        ServerAlias www.site2.com
    DocumentRoot /var/www/site2
</VirtualHost
```httpd.conf file is blank and the only thing I did to the apache2.conf file was change the port that the server listens on to "81" and remove the ":80" from the "NameVirtualHost" option. I also added a simple "Servername localhost" because I kept getting a pesky warning about the TLD not being found, so adding that solved that problem.

I added 2 entries to the hosts file
```
127.0.0.1        localhost
127.0.0.1        site1.net
127.0.0.1        site2.com
```After that I added my index pages to the directories and enabled the sites by using
```
a2ensite site1
```and
```
a2ensite site2
```I also disable the default site
```
a2dissite default
```I then reload/restart the server. The only site that comes up is the first site "site1.net" and that's only if I have the default disabled because if I don't then the default site will be the only one to load.

What am I doing wrong? I'm at the end of my rope and I would greatly appreciate any guidance and direction with this issue.

Many Thanks! :)

---

### Post by volkswagner on 2011-07-09
I'm guessing it may have to do with the masking.

Can you first try without the masking, or try on your local lan with a second machine by pointing to your server internal ip with a host file.

Example if you have a Linux desktop add the following to /etc/hosts, or for windows ~/sytem32/drivers/etc/hosts, using the LAN ip of your server.

```

192.168.1.3        site1.net
192.168.1.3        www.site1.net
192.168.1.3        site2.com
192.168.1.3        www.site2.com


```

This will help diagnose if it is an Apache problem or if issue is related to something else.

If you go the hosts file route you should be able to navigate to any of the above addresses using port 81 (site2.com:81) to see if Apache sorts them correctly.

Check in /var/log/apache2/access.log to see if you have any hint as to what the http request looks like.  If it does not match your serverName apache won't know how to sort it and will default sort alphabetically in sites-enabled.

---

### Post by jmalz on 2011-07-09
Hi volkswagner, Thanks for replying :)

Ok, I added the entries that you suggested to my hosts file for my Win 7  machine, but it didn't load any site :( not even the default site. Says  "The connection was reset" in the browser (firefox). If I remove them,  the default site loads again even if I type in "site1.net" or  "site2.com". **Could you elaborate further on why you think the masking may be the problem?**

I can load the site from my mac and my win 7 machines without editing  the hosts file. How do I copy my access.log file so I can paste it here?  Sorry, I'm still a new to the command line in linux :\

---

### Post by volkswagner on 2011-07-09
Did you replace the ip address with actual ip of your server.  I only wrote 192.168.1.3 for example.

You can find the ip of your server by running,

```
ifconfig
```

I find it easiest to copy and paste using ssh.  If you are running mac OS X, you can ssh directly to your server.  If ssh is not installed on your server you will need to install it first.

```
sudo apt-get install ssh
```

Then open a terminal in Mac OS X, applications > utlilites > Terminal

```
ssh username@192.168.1.3
```

Again with the above you need to replace username with actual user on Server and the ip of the server also.

You can also use pastebin for larger files.

Install pastebinit.

```
sudo apt-get install pastebinit
```

You can then run it against a file which will create a web link to the output.

```
pastebinit /var/log/apache2/access.log
```

Then post the link here.

It may be best to simply check the file and post a couple lines that may be relevant. 

There are several ways to output the contents such as cat or less.

```
cat /var/log/apache2/access.log
```

or

```
less /var/log/apache2/access.log
```

---

### Post by jmalz on 2011-07-10
Thanks for the pastebinit tip! :) I also have ssh installed and I've been using putty through my windows machine.

> Did you replace the ip address with actual ip of your server.  I only wrote 192.168.1.3 for example.

Yes, my internal server IP is actually 192.168.1.5 and it's a static IP that I setup through my router.

Here's a few lines from the apache2 access.log file copy and pasted;

```
127.0.0.1 - - [09/Jul/2011:21:19:37 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [09/Jul/2011:21:19:37 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [09/Jul/2011:21:19:37 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [09/Jul/2011:21:19:37 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [09/Jul/2011:21:19:37 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [09/Jul/2011:21:19:37 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.17 (Ubuntu) (internal dummy connection)"
```

What do you think?

---

### Post by volkswagner on 2011-07-10
The dummy connection is not related, nor is an issue.  

Can you post from the log when you try to access the server?

You can do this like the following.

First tail the access log so you can see it in real time, then try to access the site as you would normally.

```
tail -f /var/log/apache2/access.log
```

The try to navigate to your sites one and two to see what outputs to the log file.

You can also check the error log for relevant information.

---

### Post by jmalz on 2011-07-10
Here are the last few lines of the error log file

```
[Sat Jul 09 17:37:15 2011] [notice] caught SIGTERM, shutting down
[Sat Jul 09 17:37:16 2011] [notice] Apache/2.2.17 (Ubuntu)  PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal  operations
[Sat Jul 09 21:04:41 2011] [error] [client 192.168.1.14] File does not  exist: /var/www/favicon.ico, referer: http://192.168.1.5:81/
[Sat Jul 09 21:05:16 2011] [notice] caught SIGTERM, shutting down
[Sat Jul 09 21:05:17 2011] [notice] Apache/2.2.17 (Ubuntu)  PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal  operations
[Sat Jul 09 21:05:21 2011] [notice] Graceful restart requested, doing restart
[Sat Jul 09 21:05:21 2011] [notice] Apache/2.2.17 (Ubuntu)  PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal  operations
[Sat Jul 09 21:12:38 2011] [notice] caught SIGTERM, shutting down
[Sat Jul 09 21:12:39 2011] [notice] Apache/2.2.17 (Ubuntu)  PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal  operations
[Sat Jul 09 21:12:41 2011] [notice] Graceful restart requested, doing restart
[Sat Jul 09 21:12:41 2011] [notice] Apache/2.2.17 (Ubuntu)  PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal  operations
[Sat Jul 09 21:19:37 2011] [notice] Graceful restart requested, doing restart
[Sat Jul 09 21:19:37 2011] [notice] Apache/2.2.17 (Ubuntu)  PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal  operations
[Sat Jul 09 21:19:41 2011] [notice] caught SIGTERM, shutting down
[Sat Jul 09 21:19:42 2011] [notice] Apache/2.2.17 (Ubuntu)  PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal  operations
```

I tried doing the tail -f /var/log/apache2/access.log command but it  doesn't show the connections in real time when I go to site1 and/or  site2.

---

### Post by volkswagner on 2011-07-10
Since you mention that editing the hosts file does not allow access to the server, I believe apache is not honoring nameVirtualHosts directive.

Lets add the directive in httpd.conf

```
sudo nano /etc/apache2/httpd.conf
```

add the following line:

```
NameVirtualHost *
```

If you want to keep the default site active or enabled you may have to edit the virtualhost directive to exactly match the above and your other vhost file, ie:

```
VirtualHost *
```

No ip or port reference.

After the changes restart apache and check for errors.

There is also some cleanup you can do which I don't think is an issue, but just not the normal way of doing things.

When editing /etc/hosts you need only one line containing identical information.  When you want to add hostnames to an ip just use a space separated list.

```
127.0.0.1        localhost
127.0.0.1        site1.net
127.0.0.1        site2.com
```

Should be changed to:

```
127.0.0.1        localhost site1.net site2.com
```

---

### Post by jmalz on 2011-07-10
Ok, I've added "NameVirtualHost *" to the httpd.conf file and cleaned up the hosts file. I've also changed the vhost files to match "VirtualHost *" no IP or port specified.

I've restarted/reloaded the server and no errors seem to appear in the log file or the command prompt. But it's still giving me the default "it work's!" apache page when I try going to site1.net or site2.com :(.

---

### Post by volkswagner on 2011-07-10
I'm running out of ideas.  I'd concentrate locally before moving onto your forward and mask.

I have re-read you original posts many times.  The most recent time I have come across one minor error in both your vhost files.  

The last line reads:

```
</VirtualHost
```

but should read:

```
</VirtualHost>
```

Notice the missing closing "**>**"

It really could be that simple, but one would hope for some sort of error!  This could be why nameVirtualHost is not honored!

---

### Post by jmalz on 2011-07-10
Ah! I wish it was that simple, but my vhost files have the ending ">" symbol. It was a typo on my part when typed it here, sorry.

I don't understand why this isn't working. I have followed several different guides and tutorials to no avail. Could it be a DNS problem? I'll try anything at this point.

---

### Post by volkswagner on 2011-07-13
Since all your sites are located in /var/www, you should be able to access all sites using your ip.  This does not help with NameVirtualHosts, but may help diagnose if there is any underlying problem.

From a LAN connected machine you should be able to browse your sites as follows:

1.23.345.678:81            for default site
1.23.345.678:81/site1      for site1
and
1.23.345.678:81/site2      for site2

Although I have setup NameVirtualHosts using httpd.conf, some folks say the directive belongs in ports.conf.  You could try moving that directive also.

Also if your router has the ability to port forward to a different port, you may be able to keep apache2 running on port 80.

If your router allows:

port forward http <port 81>  to ip 1.23.345.678 to <port 80>

This would at least allow local testing to drop the port from the address.

You should also investigate why using /etc/hosts to access your server does not work.  This should bypass all DNS and give the most direct route to your server.

For example I can take one of google's ip's and add it to my /etc/hosts file with any name I like.  When navigating to that name it will bring me directly to google.com

```
74.125.93.104 coolsite.biz

```

Please also make sure your browser is not caching, which can give unpredictable results.  Clear cache and restart browser if need be (Internet Explorer can be a bugger here).

---

### Post by Jake.Debord on 2011-07-13
I would suggest looking into Webmin to help you manage your sites at first. It run 3 different virtual servers on mine on my Headless Ubuntu. Being able to look at the big picture with webmin helped me A LOT! Some people are just fine with the conf files and logs, but every now and then Webmin can be a pretty handy crutch!

---

### Post by jmalz on 2011-07-15
I'm going to try your suggestions guys. I'll report what happens, thanks again.

---

### Post by jmalz on 2011-07-16
**UPDATE**

So I decided to reinstall ubuntu server and a fresh install of apache2  with webmin. Now, I'm confused! It kind of works but only if I add the  server's IP to the hosts file from the computer that's visiting the  site. for example, on my win 7 machine I have edited the hosts file but  on my mac the hosts file is unchanged and it won't work. I have left  apache2 basically at it's default settings, only added "NameVirtualHost  *" to the ports.conf file. No errors when I restart/reload apache2, and I  have the listen port set to 80 and forwarding  81 from my router's  public IP to internal 80 so I can test locally without adding :81. I  used webmin to create the virtualhosts, and I clear the cache constantly  after every edit.

The one other thing that I did was change the path for site1 from  "/var/www/site1" to "/home/web/site1" and I left the default path for  site2 as "/var/www/site2". This seems to work, even with the default  page ("/var/www") if I go to the servers IP address, it shows the  apache2 "It works!" page. But as I mentioned before, I'm not sure if  this will work from an external connection trying to reach either site1,  site2 or the default. It feels like I'm missing something here. :/.

What do you guys think?

**UPDATE**

I can reach site1 and site2 by typing 192.168.1.5/site1.net and 192.168.1.5/site2.com or using my public IP address. Maybe this info might be helpful. It's not supposed to work like this is it?

---

### Post by volkswagner on 2011-07-17
I don't like the way Webmin handles some config files.  You may get unexpected results, especially if editing/creating config files both by and and using Webmin. If using Webmin it is best to use it exclusively.  It has been a long time since I have tried it.  One key point I recall is the tick box for "server for any address not handled by another server".  When I selected this box on ALL Vhosts, I got my best results.

In my opinion adding Webmin just added another layer of complexity without aiding to the root of your initial problem.

It may be helpful to post what how-to's you followed to set up your server, so we can see if there were any instructions that may have landed you here.

Your router may be offering some weird behavior.  You may want to try a webProxy service like hidemyass.com, if you can't test with an outside connection.

---

### Post by jmalz on 2011-07-21
Here are just 2 of the multitude of guides that I followed, but all of the guides were similar, if not exactly the same.

[http://library.linode.com/web-servers/apache/installation/ubuntu-10.10-maverick](http://library.linode.com/web-servers/apache/installation/ubuntu-10.10-maverick)

&

[https://help.ubuntu.com/10.10/serverguide/C/httpd.html](https://help.ubuntu.com/10.10/serverguide/C/httpd.html)

I'm not sure if it's my router that's causing the problem, anyway to test it? I can reach my server from my office computer at work by typing either "site1.net" or "site2.com" or the routers public IP, but the default site shows no matter what.

I'm beginning to think it has something to do with either DNS, CNAME or the "A" name. What, if anything do you guys do to your zone files when adding another virtual host?

---

### Post by volkswagner on 2011-07-22
I handle DNS externally.  I don't use Bind.

When adding a domain or subdomain that you want to have directed to the same name, you need an Arecord not a CNAME.  The Arecord should point to your public ip address of your server.

Again I must stress, editing your /etc/host file on mac or c:\win..\sys32\drivers\etc\hosts on windows pointing the domain names to your local ip of server should direct traffic there.  If this is not working you did something wrong in /etc/hosts, or you have some unique proxy settings, or Apache is not working correctly.  When diagnosing problems, you need to be methodical.  This means introducing limited changes and verify the results.


If all your rewrite and mask is happening external to the server, it is best to get everything working local-LAN before venturing to the outside world.

---

