---
title: "creating a webmail subdomain"
date: 2009-01-27
forum: Server Platforms
---

### Post by bluethundr on 2009-01-27
Hi guys

 I was able to do some cool things with my mail server. I was able to mysqlize my postfix backend and setup roundcube and everything works. Even pop and imap work now. (to a degree.. pop and imap receive mail and show my inbox but does not currently send. roundcube sends and receives just fine, so that'll be a battle for another day).

 What I would like to know now is this... 

 as of now to get to my roundcube setup, you surf to:

 [http://mydomain.com/mail](http://mydomain.com/mail)

 I would like that to be 

 [http://webmail.mydomain.com/](http://webmail.mydomain.com/)

 Any ideas on how I can accomplish this? Any good tutorials out there I can reference?

 Thanks!

---

### Post by tomwerner470 on 2009-01-27
Assuming you are using Apache as your webserver, you need to do add an entry to your virtual hosts configuration in your config file. You also need to add a relevant entry into your DNS.

ie.

**DNS**
Add something like:
```
webmail IN CNAME mydomain.com.
```

**Apache Virtualhost config**
```

<VirtualHost *>
ServerName webmail.mydomain.com
DocumentRoot /home/httpd/htdocs/webmail/
</VirtualHost>
```

Taken from:
[http://content.websitegear.com/article/subdomain_setup.htm](http://content.websitegear.com/article/subdomain_setup.htm)

Btw, this assumes that the webmail is on the same machine as the frontend, if not you may need to look at the apache reverse_proxy module.

Regards,

Tom

---

### Post by volkswagner on 2009-01-27
I use squirrel mail, but I just setup a virtual host with the subdomain.  I use DynDns since well I have a dynamic dns.  With DynDns I add the subdomain as a host there, along with my other domains.

Give a little information on your network structure.  If you need help with the virtual host look at the Ubuntu Documents for [Apache2]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html").

[Server Guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html")

---

### Post by bluethundr on 2009-01-27
Hi and thanks for the info. 

I am running apache 2.foo (forget the exact version) on Ubuntu 8.10 server. My website is a twiki site.

Will twiki run withing a virtual host? As of now my twiki setup is sprawled throughout the apache config file.

So I assume the steps will be to 1) put my twiki setup into a virtual host 2) setup my webmail subdomain in dns 3) setup my webmail subdomain as a virtual host in my apache config file. 3) ???? 4) PROFIT!!!

Thanks again!

---

### Post by tomwerner470 on 2009-01-27
Sounds pretty much like thats OK, however, the twiki stuff shouldn't need to be touched (i.e put into a virtual host), just add the extra virtual host declaration at the end of the httpd.conf file and it should work (and the DNS of course). And as far as I am aware, there is no 3 !!!

---

### Post by bluethundr on 2009-01-28
Thanks for the input.

I tried just putting in the new virtual host at the end of twiki.conf (which is actually an alias to httpd.conf) and even though my DNS seems quite correct I got no love.

In fact, if I use a wildcard '*' to represent my IP address my entire site goes down! Completely confusing to me as to why it might do that. If I then substitute the correct IP for wildcard, magically my site comes back up.

I actually just copied this and substituted my actual values, and that's when my site went down:

```

<VirtualHost *>
ServerName webmail.mydomain.com
DocumentRoot /home/httpd/htdocs/webmail/
</VirtualHost>

```

When I changed it to 

```

<VirtualHost 212.202.201.25> #not my real IP obviously
ServerName webmail.mydomain.com
DocumentRoot /home/httpd/htdocs/webmail/
</VirtualHost>
```

The site came back.

I then figured it might not hurt to put the entire twiki into a virtual host. And to my surprise and delight it works just fine!

However, it's a qualified victory. Again, I cannot use the wildcard '*', because if I do then the site, yes, once again goes down until I substitute my actual IP address.

In addition, I tried adding a 

```

NameVirtualHost 212.202.201.25:80

```

Directive. The site works. 

Written as 
```

NameVirtualHost *:80

```

The site goes away. Unfortunately even with the working config with the IP, no subdomain appears.

Now, I'm not real DNS savvy (just yet), so for now I'm using Godaddy's DNS. I've enclosed a pic (with obscured domain info) of what my CNAME looks like that I tried setting up to get my webmail subdomain setup.

Thanks again, the ubuntu community is simply amazing!:KS

---

### Post by tomwerner470 on 2009-01-29
> Now, I'm not real DNS savvy (just yet), so for now I'm using Godaddy's DNS. I've enclosed a pic (with obscured domain info) of what my CNAME looks like that I tried setting up to get my webmail subdomain setup.
In your DNS screen, the "points to hostname" field needs to change to just fakedomain.com.

Basically subdomains work by always pointing back to the root of the domain and the webserver picking up the subdomain in the http request and going to the right virtual server entry. 

Hope that works,

Tom

---

### Post by bluethundr on 2009-01-29
Hmmm.. no success here following your directions. Interesting result though. I tried setting up two subdomains.


I tried setting up webmail.fakedomain.com and mblog.fakedomain.com

I tried altering the CNAME records for those subdomains so that they read just fakedomain.com 

Now what happens is when I hit either webmail.fakedomain.com or mblog.fakedomain.com it takes me to the homepage for my site, instead of the pages for those directories.


These are the entries for those subdomains in my apache config:

```

<VirtualHost 212.201.215.25:80>
ServerName webmail.fakedomain.com
DocumentRoot /var/www/mail/
</VirtualHost>

```

```

<VirtualHost 212.201.215.25:80>
ServerName mblog.fakedomain.com
DocumentRoot /var/www/mublog/
</VirtualHost>

```

I think I am getting closer to a solution here and the prospect of success is getting tantalizing!

---

### Post by volkswagner on 2009-01-29
You should not be using alias in your DYNdns Account.  Alias is used to let [www.fakesite.com](www.fakesite.com) to fakesite.com and the like.

You should be adding hostname.  Select "Add hostname", not "Add alias (CNAME)".

---

### Post by bluethundr on 2009-01-30
Well, for the record I have 5 statics. Pay $100 a month for a business account so that my mail account could function properly. Back when I had dynamic my postfix logs would literally read "such and such server will not talk to me". I have no idea how anyone runs a mail server on a static.

Of course, the mail server is not the issue at the moment. It's the subdomain. I have taken your suggestion and added a host (A record) to my DNS setup with godaddy.

Zilch in the results. Same as before, when I hit [http://webmail.fakedomain.com/](http://webmail.fakedomain.com/) it takes me to my homepage. Very confusing. So obviously, apache is doing it's job.

I went with a suggestion from a apache guy at my old web company and added [www.fakedomain.com](www.fakedomain.com) to my virtual hosts. still nada. 

```

<VirtualHost 212.202.215.25:80>
ServerName www.fakedomain.com

```

Apache config still looks like
```

<VirtualHost 212.202.215.25:80>
ServerName webmail.fakedomain.com
DocumentRoot /var/www/mail/
</VirtualHost>

```

Enclosed is a copy of my (obscured) A record.

---

### Post by volkswagner on 2009-01-30
I am not at all familiar with running multiple IP's.  You may want to explain your network topology.  Are you behind a router?  Do you have an NIC in the server for each static IP?

I am not familiar with using external IP's in apache2 configs.

---

### Post by bluethundr on 2009-01-30
> 
***************
I am not at all familiar with running multiple IP's.  You may want to explain your network topology.  Are you behind a router?  Do you have an NIC in the server for each static IP?

I am not familiar with using external IP's in apache2 configs.
***************


Okay, so I am using one of my statics for this endeavor. It is only one static IP. I'm sorry if I confused you because I may have used more than one number accidentally in my examples in an effort to obscure my real IP information. Just don't want to be broadcasting vital information like that on a forum, ya know? ;)

So, to reiterate, it's just one IP that we'll call 212.202.215.25 (the area codes of some of my favorite cities, with a 25 tacked on at the end lol!).

That IP is being fed to a router which NATs to a 192.168.0.0 subnet. The network behind the router is dynamic, but I've assigned a static IP on the same subnet.

And everything just ..uhm.. *works* in this fashion. Postfix is postfixing, apache is apache-ing.. and all is well. _EXCEPT_ that my subdomains won't manifest which... saddens me. :cry:

---

### Post by volkswagner on 2009-01-30
At godaddy, I think you want to put webmail in the host field, not webmail.fakename.com

I think?  I don't have any set up there.

---

