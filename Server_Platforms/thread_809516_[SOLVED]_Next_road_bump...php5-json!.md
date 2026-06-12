---
title: "[SOLVED] Next road bump...php5-json!"
date: 2008-05-27
forum: Server Platforms
---

### Post by sparkyjoe34 on 2008-05-27
OK so this is where I am with the server set-up since following the [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts) tutorial. My last step on page 6, step 17 before running into a snag was this:
Quote:
Next we install PHP5 and Ruby (both as Apache modules):
Code:

apt-get install libapache2-mod-php5 libapache2-mod-ruby php5 php5-common php5-curl php5-dev php5-gd php5-idn php-pear php5-imagick php5-imap php5-json php5-mcrypt php5-memcache php5-mhash php5-ming php5-mysql php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl

Now the problem that I am running into is after running this command, The screen returns:
Quote:
Reading package lists... Done
Building dependency tree
Reading state information...Done
Package php5-json is a virtual package provided by:
php5-common 5.2.4-2ubuntu5.1
You should explicitly select one to install.
E: Package php5-json has no installation candidate
I'm not quite sure what to do about this. Any suggestions? Is it saying that I need to apt-get a specific version?

---

### Post by johnl on 2008-05-27
It's saying that php5-json is provided by 'php5-common' which you are already installing, so you can just remove the json package from your command.  As for why, I couldn't tell you.  Sometimes old packages stick around but don't do anything just so that upgrades work properly;  sometimes there's more than one package that implements what you want.

---

### Post by NateMan on 2008-05-27
Yeah that's a common problem with the perfect server guides. Packages will become outdated after they are written.(when I first followed the guide, it worked, but later on I had to take that package out.)You should be find after removing it from the install command.

---

### Post by sparkyjoe34 on 2008-05-27
Thanks guys,

I was actually reading on a different page that php5-json was now part of php 5.2.0 so i kinda got same idea that you stated about removing it. Thanks for the quick responses! On to page 7, step 19.
Just out of curiosity will I be able to do a:
```
apt-get install webmin 
```
to install the webmin gui or do I have to take a different route?

---

### Post by NateMan on 2008-05-27
you can apt-get install webmin, but it will install the older version. Luckily however, the webmin people are nice enough to host a .deb of their newest version on their website, [www.webmin.com](www.webmin.com). Download that and use dpkg --install followed by the name of the downloaded .deb. That should get you up and running the newest version quite well.

---

### Post by NateMan on 2008-05-27
ps to copy it directly on your server use copy the link and then wget it.

---

### Post by sparkyjoe34 on 2008-05-27
Ok I had to install some dependencies for webmin, other than that it is installed. Now since I have set this up as a testing server(for now)If I want to upload a file to my server where do I upload it to? I saw a spot on Webmin on the left sidebar for Upload and Download. What directory do I upload my files to for testing?

---

### Post by NateMan on 2008-05-27
If your trying to test a webpage file then it needs to be uploaded to /var/www . If not let me know what type of file you mean and I'll be glad to help.

---

### Post by sparkyjoe34 on 2008-05-27
Ok I found the directory /var/www. Now lets say I edit the index.html page in that directory and I want to be able to look at it like any other website in my browser, what would I type in the address bar? I know I can view how it will look in webmin, but I don't know how to view it any other way.

---

### Post by NateMan on 2008-05-27
Well from there you can, on the local network, point your browser at the [http://Your.Ip.Address](http://Your.Ip.Address) or if you have it forwarded to the web then you can point the browser at your public ip or dyndns address. Those should all take you to your webpage.

---

### Post by sparkyjoe34 on 2008-05-27
> If you have it forwarded to the web then you can point the browser at your public ip or dyndns address Ok how do you do this?

---

### Post by NateMan on 2008-05-27
Well what router hardware do you have? It varies depending on hardware, but is similar for each router. Basically you have to go in and using your server's ip address open up ports for it to work. First test it on the local network and see if its working, and then go from there. I'd be glad to help you configure your setup.

---

### Post by sparkyjoe34 on 2008-05-27
Linksys WRT54G Wireless Broadband Router. 
> using your server's ip address open up ports for it to work Are you talking about the port forwarding settings?

> I'd be glad to help you configure your setup
That would be great! Let me know what other information you need in order to point me in the right direction.

---

### Post by NateMan on 2008-05-27
Yes I am talking about port forwarding, specifically port 80 for http. You just put the ip address of your server (It is static right?) in and make a rule for it, apply changes. I used a wrt54g for awhile and it was a very decent router. I can actually help you out with specifics on that model. I believe it is in applications and gaming? I might be wrong though. If not its the tab to the left I believe.

---

### Post by sparkyjoe34 on 2008-05-27
BEAUTIFUL! That was very easy and painless. OK I have a couple more questions for you. Say I want my family to be able to access that page from their homes. Is that possible? If so what do I need to do?
Also, how do you go about giving a name to a site on the server. Like google.com, yahoo.com. Each one has an actual numerical IP address. How can I set it up to where I type in a name instead of my IP address to access the page?

---

### Post by NateMan on 2008-05-27
Yes your family should be able to access it and to get a named server you would have to either get a dyndns account of some kind, or get a business  level account from your isp. Then you can link it to your static ip that you will have. There are disadvantages to a dyndns, as its kinda a hack job and is actually a redirection.

---

### Post by wgregori on 2008-08-17
Any reason you are using Webmin rather than ISPconfig for your user interface.  (the Server HowTo? recommends ISPconfig)

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p7]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p7")

Thanks,
Wayne

---

