---
title: "Looking to host / setup a small development web server at home."
date: 2015-03-28
forum: Server Platforms
---

### Post by hayden10 on 2015-03-28
Hi all, I'm currently in the process of trying to setup a small development server (development environment).

Ideally it would work like below..

1) My development site can be accessed from anywhere (e.g [www.domainname.com]("http://www.domainname.com") would link to my network's IP (locally & remotely)),
2) I can modify the web files on my server through windows explorer on another computer which is on the same network. 
3) I will use virtualmin to control each development site & each site will be posted on a subdomain, e.g subdomain.mydevelopmentserver.com
4) Later I will then connect it up to bitbucket and use that for version control.

At the moment I'm currently this far..

1) I have a server box which is hosted in my home office. (Dell Server, Xeon 3440, 8GB ram, 2.53ghz quad core).
2) I have setup and installed ubuntu server 14.04 onto it and can access the server by going to the local IP: 192.168.1.6.
3) I have port forwarded my modem so it allows remote connections, a few people have been able to connect remotely and access my laptop's server (not the server above). I can't access my full real IP as it keeps displaying my modems network page.
4) I have purchased a domain name for my development server.
5) I am currently able to connect VIA ssh OR FTP to my Dell Server and can edit the files if I'm logged in as root.


I was wondering if anybody had any advice on the best way to get my system running or preferable link me in the right direction as I'm having trouble googling for the right guides. 

Thanks, Hayden

---

### Post by nerdtron on 2015-03-28
> **hayden10 said:**
> 
3) I have port forwarded my modem so it allows remote connections, a few people have been able to connect remotely and access my laptop's server (not the server above). I can't access my full real IP as it keeps displaying my modems network page.
4) I have purchased a domain name for my development server.
5) I am currently able to connect VIA ssh OR FTP to my Dell Server and can edit the files if I'm logged in as root.


The direct ip address showing the modem network page: you should disable remote wan management on the modem. Then port forward port 80 to the local IP of the server 192.168.1.6. Then on your domain registrar, create an A records DNS entry that will point your domain to your Public IP address.

> 2) I can modify the web files on my server through windows explorer on another computer which is on the same network. 
I don't think this is safe. It's better to use version control like git to log-in to the server and then export the needed files/codes or just compress the web files, then upload and extract on the server.

>  3) I will use virtualmin to control each development site & each  site will be posted on a subdomain, e.g  subdomain.mydevelopmentserver.com
You can control subdomains on apache2, just create a vhost entry for each subdomain and declare the document root for each. as for DNS, you can go to your registrar and point the subdomains to your Public IP address.

---

### Post by Lars Noodén on 2015-03-28
> **hayden10 said:**
> 4) I have purchased a domain name for my development server.
5) I am currently able to connect VIA ssh OR FTP to my Dell Server and can edit the files if I'm logged in as root.


4) If your home office does not have a static IP address you will have to get one or else to subscribe to a dynamic DNS service and use that as an intermediary.  To do the latter, configure your router (or server) to login with your dynamic DNS service and the for your real domain, make a CNAME and point that at the dynamic DNS name.  

5) If you have SSH available, you can use SFTP instead, and [urlhttp://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp]stop using FTP[/url] as it's not safe.  There are a lot of SFTP clients available, some built-in like [sftp] and [url=http://manpages.ubuntu.com/manpages/trusty/en/man1/nautilus.1.html]nautilus](http://manpages.ubuntu.com/manpages/trusty/en/man1/sftp.1.html).  About editing files, that's a permission question.  If you are the only user of that machine then you can just take ownership of the directories and files with [chown](http://manpages.ubuntu.com/manpages/trusty/en/man1/chown.1.html) at the DocumentRoot for each Apache2 virtual host.  If you're sharing work with one or more others then groups are needed.

---

### Post by TheFu on 2015-03-28
Great responses above.  Really any developer needs to learn all the capabilities of ssh - it is an amazing, secure, tool.
[http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)  Do not use passwords - [only use keys]("http://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication").

Don't use plain ftp anymore. Please.  There are a few good sftp clients for every OS - winscp is nice on Windows. Forget cifs. I'd also suggest forgetting webmin, since that won't help with setting up a VPS. Spend the time to learn the apache config files. It really isn't very hard - or use a lighter web server like nginx.  If you don't need the kitchen sink, don't run apache.

I would also suggest the OP start with some directed Linux learning rather than using google. By spending 5 hrs getting some background will really save hours, days, weeks, months of frustration.  [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - the first 4 items in the list should be read in less than an hour. Then reading the CLI PDF for a few hrs will teach absolutely critical skills for someone hoping to run a *nix server.

And please learn file and directory permissions. This is the basis of all *nix security - you shouldn't need root to edit files for a web server.  Just sayin'.  Using root shows laziness AND a misunderstanding of basic file/directory permissions, group and userid management.

Anyway - hope this helps get you started on the path towards mastery.

---

