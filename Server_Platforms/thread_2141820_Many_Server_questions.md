---
title: "Many Server questions"
date: 2013-05-03
forum: Server Platforms
---

### Post by beengone on 2013-05-03
I have a handful of questions (if you have very large hands; otherwise maybe a boatload). I am not asking for hand-holding necessarily, but need pointed in many right directions as I'm not overly-skilled with Linux administration. Here's what I'm trying to accomplish. I run a small IT services business. I do some websites, custom integration stuff, etc. So, I have a Windows test server, a couple Windows and Mac OS client machines, and a Linux server. My goal with the Linux server is to handle the following roles:

[LIST=1]
[*]Web Server
[LIST]
[*]Production CRM server. I'm running SugarCRM, but want to be sure only I can access it.
[*]Test web server for both internal and external access. Best would be if I could flip some switch that would allow and disallow outside access easily.
[/LIST]
[*]SFTP Server - I want to get clients to stop emailing me large files.
[*]Local Backup Server - I have this working now. My Windows box backups up to it using Bvckup, which works great.
[/LIST]

Here's what I have so far: Ubuntu 12.04 running on a crappy old Dell Optiplex 170L. It works. Eventually, if I settle into running this environment, I'll replace it. If there any red flags right away let me know. I have a slightly faster box this could run on. I'm running Webmin on it and, of course, have SSH access.

-I'd like to set up DDNS and get it working properly so I can give a client something like ftp.domain.com or websites.domain.com/yoursite or whatever. Am I best off just setting up an account with dyn.com or noip.com, etc? 

- How do I wall off the backups from the FTP and websites? If I leave it as a user called "backups" for the backups and some other user for the websites will that work?

- I've read a bunch online about setting up sftp/scp/ssh/ftp/ftps and am more confused than when I started. I know ftps and ftp are out. My goal is to be able to easily give a user an account that can only be used for SFTP/SSH access. Most of my clients will need to do this through Explorer on Windows, though some will use Filezilla, etc. can someone point me to an article that steps me through the best way to set this up? ProFTP/SSH/vsftpd? If I can administer this through Webmin, great. If the instructions are through the terminal that's fine too. This will be used only a few times / week and mostly for files under 10mb. In the future that may change, but for now...

- How do I make some websites accessible to me only, some have a password to get into from outside, and some fully-public? For instance, I'll be working on some that have no need for anyone else to see that are in the very beginning stages of developmnet, SugarCRM should be available to me anywhere in the world but only to me and maybe some others by password, some should be fully-public.

-Long-term I would love to learn to make this my gateway/firewall/etc. Should that be a separate device? If I do something like this can I somehow run my own nameserver with the above results for less money (free?) compared to using a service like dyndns or noip? 

- Out of the box will this be relatively secure? Any good articles for me to to look at that might help if not?

- Is Ubuntu a good solution for all this? 

- Webmin a good or bad idea here?

- Anything else I should look into doing with this that maybe I missed?

- I'll be installing a gigabit card in this machine soon as well as setting up a HDD raid and backup. That I can handle, but any concerns?

Again, mostly I need advice on which way to get SFTP access for clients simply and whether I'm thinking about this right. I know it's a lot in one post, but I want to make sure one box can do everything and be sure I have my head on straight about this.

Thank you all.

---

### Post by CharlesA on 2013-05-03
It is usually a good idea to have your servers separated from your firewall/gateway.

At least according to the [requirements]("http://support.sugarcrm.com/05_Resources/03_Supported_Platforms") of SugarCRM, it should be able to run on a *nix box, but it would be a good idea to check with them to be sure.

As far as using sftp to deal with files from customers/clients, do you really think they would use it if it required more steps as opposed to just emailing you the files?

---

### Post by beengone on 2013-05-04
> **CharlesA said:**
> It is usually a good idea to have your servers separated from your firewall/gateway.

At least according to the [requirements]("http://support.sugarcrm.com/05_Resources/03_Supported_Platforms") of SugarCRM, it should be able to run on a *nix box, but it would be a good idea to check with them to be sure.

As far as using sftp to deal with files from customers/clients, do you really think they would use it if it required more steps as opposed to just emailing you the files?

Great, I'll plan to keep my router as the firewall/gateway for now and keep additional firewalls on each box as needed. Thank you for the advice.

Sugar works fine, I already have it running. My questions are more about security, limiting access, dns.

As for sftp, no some will not use it. However, some will due to security, which is important. This is especially true between myself and some of my freelancers where it's one thing for a client to leak data and a very different thing for me to do so.

Any direction as to sftp server? Again, I keep reading sources who say different things constantly. ProFTP is supported out-of-the-box by webmin, but I'm not even certain if webmin is a good idea. Thoughts?

Thank you.

---

### Post by SeijiSensei on 2013-05-04
You might take a look at [WebDAV]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html") as an alternative to SFTP.  If you use an https:// connection to the DAV server, it's quite secure.  It's also easy for people to use.  In Windows, for instance, you can drop a DAV-mounted folder onto the desktop and drag-and-drop items into it.  

I once set up a WebDAV instance for a bunch of attorneys who were running a membership organization.  They used it to share documents and the like among the executive committee and had no problems with it.

---

### Post by beengone on 2013-05-04
> **SeijiSensei said:**
> You might take a look at [WebDAV]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html") as an alternative to SFTP.  If you use an https:// connection to the DAV server, it's quite secure.  It's also easy for people to use.  In Windows, for instance, you can drop a DAV-mounted folder onto the desktop and drag-and-drop items into it.  

I once set up a WebDAV instance for a bunch of attorneys who were running a membership organization.  They used it to share documents and the like among the executive committee and had no problems with it.

Sounds like Dropbox without the versioning and local copies, right?

Trying to figure out the users/permissions bit here. I'm reading a lot of posts around the web saying people were confused trying to set this up, but have yet to see one that has a solution and I can understand. Ideally I'd create a folder for each project or client and assign permissions to that folder to those who need it. I'd also have a public drop-box if possible. Thoughts?

---

### Post by beengone on 2013-05-04
I'm still reading up on WeDAV and it looks promising and I'm still trying to figure out the details like users. 

However, I'm also seeing information on vhosts. This seems very interesting if I understand any of it correctly.

So, with all I'm trying to accomplish, could someone please give me a logical set of steps I should take. Example:

Install Ubuntu > Enable (or not) firewall > configure Apache using xyz > read zyx primer on vhosts (or not) > set up WebDAV > make user for backups and secure it using blah

I'm pretty sure I can figure each step out, but find I should have done one thing before 3 I already did, etc.

THanks!

---

### Post by SeijiSensei on 2013-05-05
Virtual hosting enables the server to respond to requests for multiple domain names while using just one IP address.  In general it makes sense to treat every web server as a virtual host.  Ubuntu essentially does just that since the default Apache configuration is one possible entry in /etc/apache2/sites-available/.

If you have control over your DNS so you can create arbitrary host names, you could consider setting up a virtual called webdav.example.com that references a vhost definition just for that service.

I haven't used WebDAV for a very long time now, but I recall just using Apache's own [basic authentication]("http://httpd.apache.org/docs/2.2/howto/auth.html") methods to handle logins.  I think I set up two groups with separate memberships since only some of the members were authorized to access the organization's financials.  Usually all the transactions between the web server and the shared directory takes place using the web server's account, which on Ubuntu is "www-data".  So I think you need only grant www-data rights to the shared directory; you manage access in Apache.

---

### Post by beengone on 2013-05-14
> **SeijiSensei said:**
> Virtual hosting enables the server to respond to requests for multiple domain names while using just one IP address.  In general it makes sense to treat every web server as a virtual host.  Ubuntu essentially does just that since the default Apache configuration is one possible entry in /etc/apache2/sites-available/.

If you have control over your DNS so you can create arbitrary host names, you could consider setting up a virtual called webdav.example.com that references a vhost definition just for that service.

I haven't used WebDAV for a very long time now, but I recall just using Apache's own [basic authentication]("http://httpd.apache.org/docs/2.2/howto/auth.html") methods to handle logins.  I think I set up two groups with separate memberships since only some of the members were authorized to access the organization's financials.  Usually all the transactions between the web server and the shared directory takes place using the web server's account, which on Ubuntu is "www-data".  So I think you need only grant www-data rights to the shared directory; you manage access in Apache.

Fantastically helpful. Now to get the time to get back to this. A couple things dropped in my lap that put this down the list. I'll focus my attention in this direction. I also realized my upload speed is so miserable hosting any larger files is really impractical. I'll figure out whethr I want to use Dropbox or purchase a VPS/other. Maybe just upgrade my connection. We'll see.

Thank you again.

---

