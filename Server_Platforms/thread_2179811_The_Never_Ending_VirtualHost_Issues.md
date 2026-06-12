---
title: "The Never Ending VirtualHost Issues"
date: 2013-10-10
forum: Server Platforms
---

### Post by lktech on 2013-10-10
Howdy all. I'm new to the concept of using virtual hosts, and the reason I'm doing so is there is a small pocket of sites I will be hosting (about 3-5). I've read up on quite a few posts/forums on this site and others, seem to come across a mix of opinions and directions to take. So I'm gonna cut right to what I'm after, what I'm using, and where I'm at (which FYI has not worked just yet). Before getting into the screenshots, just want to run the basics by you guys.

My objective= Host 3-5 sites on a physical server, 1 IP address, use virtual hosts based on name to have them resolve on the internet. The DNS side of that is taken care of (won't be done locally). 

Using Ubuntu Server 12.04.3 LTS, running just the lamp stack and openSSH, of which I manage from my home. Before I actually implement all these configurations on the actual server, I have the identical setup running at home on a VM, once that's nailed down, apply the same setup on the physical server.

With that all being said, here's where I'm at and the issues I'm having. Hopefully some kind folks can steer me in the right direction. Here's a (somewhat modified for privacy) layout:

[LIST]
[*]Going to host mysite1.com, mysite2.com, mysite3.com. All are using wordpress.
[*]LAMP is running fine.
[*]In var/www, creating  "mysite1.com" folders for all 3 sites
[*]Each site directory mentioned above has the wordpress files moved in, with there own independent wp-config.php settings (an easy mistake to make), setup properly and working.
[/LIST]
Now for the steps I've taken as to setup vhosts for them:
[LIST]
[*]Lets say the IP of the server is 192.168.1.134 (just a fyi)
[*]I ran $ sudo a2enmod vhost_alias  (no errors were displayed)
[*]Then, $ sudo cp /etc/apache2/sites-available/default mysite1.com
[*]Then, edited the following in the above mysite1.com file:
[LIST]
[*]Added: ServerName mysite1.com    (just above the very first DocumentRoot directive)
[*]Added: DocumentRoot /var/www/mysite1.com     (this was the first DocumentRoot directive like above, no slash at the end)
[*]Added: DocumentRoot /var/www/mysite1.com/    (the next DocumentRoot directive, with slash)
[/LIST]

[*]Then, $ sudo service apache2 reload    (no errors)
[*]Added 127.0.01 mysite1.com  in /etc/hosts    (just cause, even though on the VM server copy I removed the GUI and will be only using the browser to nav these sites from the machine I SSH from)
[*]Added 192.168.1.134 mysite1.com in /etc/hosts from the machine I SSH from, so I can view the site without the whole [http://192.168.1.134](http://192.168.1.134) or pre-vhost approach with 192.168.1.134/mysite1/ yadda yadda
[/LIST]
So, with that all being said, it works just fine....the PROBLEM hehe, is when I take the exact same approach with mysite2.com. The issue I have, is:
[LIST]
[*]A) if i browse using the IP of the VM server copy, i just get mysite1.com's page (which I can understand as it's not name based, also I read that the vhost will read alphabetically if no host header is present in the request)
[*]B) if i go directly to [http://mysite2.com](http://mysite2.com) , I just get blank pages, and I mean nothing. Now there could be something due to wordpress, im not really sure. I couldn't get to the mysite2.com/wp-admin/install.php script to finalize the setup since it wouldnt load. I tried to comment out the 192.168.1.134 mysite1.com   addition in the /etc/hosts file in the machine I SSH from, but still showed me dead blank pages when I browse to mysite2.com
[/LIST]
It also makes me think that mysite1.com, did NOT load using this vhost setup properly, but rather just loaded as if I threw a website in /var/www 

Very, very open to suggestions, feedback and ideas :) 
Thanks

---

### Post by rvwbug on 2013-10-10
This may be a permissions issue on the site directory and/or files.  What are the permissions for the document root?

You can also check /var/log/apache2/error.log and access.log for help.

---

### Post by Lars Noodén on 2013-10-10
In addition to the tail of the error log, you might explicitly test the configuration files:

```

apache2ctl configtest

```

But if all you changed was the DocumenRoot, they should be ok.

---

### Post by lktech on 2013-10-10
Ok, lol...so I had one of those I'm an idiot moments. I reverted to a snapshot of the VM server we're talking about, wanted to walk through the steps again and grap some screen so I could answer the responses visually...and low and behold I left out a step for mysite2....ENABLING IT!

---

### Post by lktech on 2013-10-10
Apologies, having some issues uploading the next series of screens, to sum it up, the "a2ensite" was run only on mysite1.com and not the next ones. once that was done, they all worked!

---

