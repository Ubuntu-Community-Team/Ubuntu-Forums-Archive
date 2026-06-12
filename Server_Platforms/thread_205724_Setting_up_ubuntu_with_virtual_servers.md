---
title: "Setting up ubuntu with virtual servers"
date: 2006-06-28
forum: Server Platforms
---

### Post by cconk01 on 2006-06-28
Hello, I am pretty new to ubuntu but I have a question or two, and if the can be answered by other threads please feel free to link me to them. 

I would like to start hosting a few websites for friends and others. It would be roughly 3 or 4 virtual websites. I understand I must configure apache with virtual host but im a little confused.

Let&#8217;s say godaddy.com is my domain register. Would I point all three/four domains to the same ip address of that of my ubuntu web server and then apache is able to tell which virtual website to go to? Or do I need to set up a local DNS server on the ubuntu server or is it already taken care of because go daddy is my domain register?

Question 2:
In setting up virtual domains can I also set up virtual ftp connections so my friends could connect to there web root and modify there webpage&#8217;s?

Question 3: 
In your opinion what would be adequate computer power for 4 websites hosted on one computer getting roughly 50 to 100 hits total a day? For the time I would have php installed and maybe* mysql, but I would only use Mysql for one of the 4 websites (my domain).

All together from a 1 to 10 (10 being extremely difficult) how hard would all this be to set up?

Thank you for taking your time to read this and I hope this isn&#8217;t to vague.
. ;)

---

### Post by crouton on 2006-07-03
1) You can have multiple sites going to one IP address as long as those sites are distinct, e.g. abc.com, def.com, ghi.com, etc...  Known as name-based virtual hosting, more info is [here.]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html")

2) Yes.  You would likely create local user accounts, and assign permissions to each user based on which site(s) they have access to.  Pretty sure there's a proftp HOWTO lurking about, and there's always Google if you don't like proftpd.

3) 400 hits over 24 hours is a pretty small load.  You would likely be OK with a P2-400 and 128-256MB of RAM, if you still have a machine of that era.  Anything newer than that will likely be more than enough to handle that load, provided the other users don't write strange or runaway PHP files.

---

### Post by Disstress on 2006-07-04
[QUOTE=cconk01]Hello, I am pretty new to ubuntu but I have a question or two, and if the can be answered by other threads please feel free to link me to them. 

I would like to start hosting a few websites for friends and others. It would be roughly 3 or 4 virtual websites. I understand I must configure apache with virtual host but im a little confused.

Let’s say godaddy.com is my domain register. Would I point all three/four domains to the same ip address of that of my ubuntu web server and then apache is able to tell which virtual website to go to? Or do I need to set up a local DNS server on the ubuntu server or is it already taken care of because go daddy is my domain register?

Question 2:
In setting up virtual domains can I also set up virtual ftp connections so my friends could connect to there web root and modify there webpage’s?

Question 3: 
In your opinion what would be adequate computer power for 4 websites hosted on one computer getting roughly 50 to 100 hits total a day? For the time I would have php installed and maybe* mysql, but I would only use Mysql for one of the 4 websites (my domain).

All together from a 1 to 10 (10 being extremely difficult) how hard would all this be to set up?

Thank you for taking your time to read this and I hope this isn’t to vague.
. ;)[/QUOTE]
Ok to start off do you have a static or dynamic IP? You need nameservers regardless of IP type, so choosing to set up your own DNS or to use dynamic DNS for your solution is up to your answer. Either way I think it would be easier to use dynamic DNS, like dnydns.org or something similar, a google search will pull up a bunch of different DNS solutions.

You can set up as many FTP services you want to, you can link those FTP services to a particular folder like /www/var/bob/html or whatever you choose as the default FTP folder, this is seperate from Apache, and you can probably find good information on setting up a FTP server with a search on these forums.

A computer to power four websites with 400 hits a day... I'd say a Intel Celeron 600Mhz 64mb RAM on a dsl connection would be more than enough.

As far as rating how hard it would be to do this, that is subjective. I think it would be easy, I even remeber my first Apache install on Windows, it was pretty easy to figure out. Setting up the FTP servers would take the most time, installing apache with Ubuntu is brainless, even using a boxed solution like bitrock.com 's lamp stack is a good idea.

If you can think of any other questions, I'll be glad to help if I can! \\:D/

---

### Post by paul.maddox on 2006-07-07
One thing to note is that if you are intending to use SSL (https) then you can only have 1 SSL VirtualHost per IP address. Not sure if you're going to need SSL though.

---

### Post by maino82 on 2006-07-08
If you're using GoDaddy.com it's easiest to just use their domain name servers and point all the websites to your one IP address (someone mentioned whether it was a dynamic IP or static, but if you have a broadband connection this is kind of a moot point as it will be the same most of the time anyway). After that you just need to set up your apache config with the virtual hosts similar to this:

> 
NameVirtualHost *:80

<VirtualHost *:80>
   ServerName website1.com
   ServerAlias [www.website1.com](www.website1.com) *.website1.com
   ServerAdmin [email]admin@website1.com[/email]
   DocumentRoot /var/www/web1
</VirtualHost>

<VirtualHost *:80>
   ServerName [www.website2.org](www.website2.org)
   ServerAlias website2.org *.website2.org
   ServerAdmin [email]admin@website2.org[/email]
   DocumentRoot /var/www/web2
</VirtualHost>


You can use all the <Directory> items you need to as well inside the virtualhost definitions. I have the same thing setup for a number of websites I admin and it works pretty well. Much easier and hassle free than setting up your own DNS.

---

### Post by hdpc on 2006-07-25
> **maino82 said:**
> If you're using GoDaddy.com it's easiest to just use their domain name servers and point all the websites to your one IP address (someone mentioned whether it was a dynamic IP or static, but if you have a broadband connection this is kind of a moot point as it will be the same most of the time anyway). After that you just need to set up your apache config with the virtual hosts similar to this:



You can use all the <Directory> items you need to as well inside the virtualhost definitions. I have the same thing setup for a number of websites I admin and it works pretty well. Much easier and hassle free than setting up your own DNS.

Hi maino82,

I got mine setup but I can't seem to get my second domain to work properly.  Meaning when I type
[http://www.firstdomain.com](http://www.firstdomain.com)  <--- This works
[http://www.seconddomain.com](http://www.seconddomain.com) <--- Does NOT work
[http://seconddomain.com](http://seconddomain.com) <--- This works

I have ServerAlias set too.  Can anyone help?  Thanks.

-haiN

---

