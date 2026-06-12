---
title: "Help with Apache VirtualHosts. Using 1 IP for two sites. One is not loading"
date: 2009-08-25
forum: Server Platforms
---

### Post by jocampo on 2009-08-25
Hello forum friends.

Need a little help with my Apache configuration. I've registered two websites on internet (domain registration) The idea is use my webserver to hosts both sites with my only public IP. I already change the A host record for my sites to point to my home webserver. But no matter what, the 2nd site is not loading, I'm always seeing the 1st default webpage. I'll describe my configuration a bit, just changing the real url...

The two folders that hosts my web content:
- /var/wwww ---> for site [www.fake1.com](www.fake1.com)
- /var/joe  ---> for site [www.fake2.com](www.fake2.com)

I have NOT changed /etc/apache2/apache2.conf ... no changes here regarding my virtualhosts.

Inside /etc/apache2/sites-available/ you will find "default". I use default for my virtual hosts, something like this

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
.
.
.
</VirtualHost>


<VirtualHost *:80>
        ServerName fake2.com
        ServerAlias www.fake2.com

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/joe/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>


```

I think is something like that ... did not copy paste everything in order to simplify. Problem is that no matter what, if I use [www.fake2.com](www.fake2.com) on my browser, it will display the default page for [www.fake1.com](www.fake1.com) instead.

How can I make it work for both of my websites using my only public IP? Both domain names have been registered. And I know A records are pointing to my own webserver because wwww.fake1.com and [www.fake2.com](www.fake2.com) both displays something from internet: the default web page content.

---

### Post by cdenley on 2009-08-25
That looks like that configuration should work. Are you sure your browser isn't displaying a cached page? Try running this command:
```

echo -e "GET / HTTP/1.0\nHost: fake2.com\n"|nc fake2.com 80

```

---

### Post by Kolipoki on 2009-08-25
Kk, I'm not a guru, but for what I've looked so far in your post I saw 2 things that intrigued me a bit:

1. One of the sites seems to be the "default" enabled site. Probably that's the one you can see in the browser w/o problems. Need to make sure of having both sites enabled, and, I might be wrong but I think there's a chance that you might have to dissable the default site. I hope someone can add to this.

2. As far as I know, everything intended to be published has to be inside the /var/www directory (actually, popular opinion is that it's best to add subfolders for websites under the /www, as www is owned by the root user). You already have 1 site there, but the other is outside, in /var/joe ? I can see that path is defined in the config file but I've never seen it like that (in my rather short Ubuntu life), not sure is it should work as it is.

Again, not a guru here, but almost sure your problem could be somewhere around these issues. Cheers...

---

### Post by jocampo on 2009-08-25
> **Kolipoki said:**
> Kk, I'm not a guru, but for what I've looked so far in your post I saw 2 things that intrigued me a bit:

1. One of the sites seems to be the "default" enabled site. Probably that's the one you can see in the browser w/o problems. Need to make sure of having both sites enabled, and, I might be wrong but I think there's a chance that you might have to dissable the default site. I hope someone can add to this.

2. As far as I know, everything intended to be published has to be inside the /var/www directory (actually, popular opinion is that it's best to add subfolders for websites under the /www, as www is owned by the root user). You already have 1 site there, but the other is outside, in /var/joe ? I can see that path is defined in the config file but I've never seen it like that (in my rather short Ubuntu life), not sure is it should work as it is.

Again, not a guru here, but almost sure your problem could be somewhere around these issues. Cheers...

Hi

I lived in Puerto Rico for 9 years :-) ... nice place...

Welcome to the forum and Ubuntu life, I love both! lol ... you can keep your web content in different folders as long as you specify that on the sites-available files configuration, so when apache.conf calls it, will know where to find the files. And yes, /var/wwww and /var/joe are owned by root and have same permissions. In fact, I checked it putting default in disable and enable the other one ... you can retrieve the information from there.

Both sites are in enable state ... getting no errors but when you go to internet, content for default or 1st site is displayed, not the second one.

---

### Post by DaithiF on 2009-08-25
Hi,
Why haven't you set a document root for the 2nd virtual host.

And why no ServerName/ServerAlias for the 1st?

---

### Post by cdenley on 2009-08-25
> **DaithiF said:**
> Hi,
Why haven't you set a document root for the 2nd virtual host.

And why no ServerName/ServerAlias for the 1st?

Of course! You set the options for /var/joe, but never made it DocumentRoot. I can't believe I missed that. You said that wasn't an exact copy-and-paste, though, so do you have DocumentRoot in your second vhost configuration?

I don't think the ServerName or ServerAlias is required for the first (default) vhost as it is used for any hostname that isn't configured with another vhost.

---

### Post by jocampo on 2009-08-25
Now I'm confused...

But ok, let me ask this. What changes/options do I need to do at

/etc/apache2/apache2.conf   ?

Can i put all my virtual host directives inside /etc/apache2/sites-available/default file? or should I create another file like /etc/apache2/sites-available/site2

I'm at work, but I can play a little bit now on the files remotely and check again ;-)

---

### Post by scottybwoy on 2009-08-25
There are instructions in the Ubuntu Forums website somewhere about setting up Virtual Hosts under Apatche2.  Due to the fact that Virtual hosting is done differently under Ubuntu than any other distro the Apatche docs aren't too helpfull but tI think their is also a specific section addresssing it now.

I had a similar issue and what I had to do was put the ServerName *:80 in the relevant section (nr the bottom) in the httpd.conf file, then take that value out of all the virtual host conf files.

As this one version is more modular, you may find it easier to create a website1.conf, website2.conf in your sites-available folder, then use a2ensite for each to symlink the files to sites-enabled.

I can't find the relative info for you at the mo, but I hope that points you in the right direction.

---

### Post by cdenley on 2009-08-25
> **jocampo said:**
> Now I'm confused...

But ok, let me ask this. What changes/options do I need to do at

/etc/apache2/apache2.conf   ?

Can i put all my virtual host directives inside /etc/apache2/sites-available/default file? or should I create another file like /etc/apache2/sites-available/site2

I'm at work, but I can play a little bit now on the files remotely and check again ;-)

Generally, there is one vhost configuration per file. Once you create a new "site", you would need to enable it (sudo a2ensite site2). Putting multiple vhost configurations in /etc/apache2/sites-available/default would work, but isn't really the standard way of doing things in ubuntu.

You shouldn't edit apache2.conf to configure virtual hosts (sites). It is only for global configurations unrelated to any module or listening configuration. Also, you shouldn't edit httpd.conf for anything in ubuntu (I've seen it suggested in other threads).

---

### Post by cdenley on 2009-08-25
> **scottybwoy said:**
> 
I had a similar issue and what I had to do was put the ServerName *:80 in the relevant section (nr the bottom) in the httpd.conf file, then take that value out of all the virtual host conf files.


I believe you are actually referring to the NameVirtualHost directive, correct? I think it used to be at the top of the default site configuration, but it has been moved to "/etc/apache2/ports.conf" in recent releases. If you have "NameVirtualHost *:80" used more than once anywhere in your configuration, I think that would cause a problem.

---

### Post by jocampo on 2009-08-25
> **cdenley said:**
> Generally, there is one vhost configuration per file. Once you create a new "site", you would need to enable it (sudo a2ensite site2). Putting multiple vhost configurations in /etc/apache2/sites-available/default would work, but isn't really the standard way of doing things in ubuntu.

You shouldn't edit apache2.conf to configure virtual hosts (sites). It is only for global configurations unrelated to any module or listening configuration. Also, you shouldn't edit httpd.conf for anything in ubuntu (I've seen it suggested in other threads).

Your are complete right! And believe me, I've checked, read several documents before posting, but Ubuntu configuration is kind of different.

Like I said, site is enable (and I tried via two files/sites before, with no success) but I'll try again from scratch. What I'm planning to do this

-NOT TOUCHING /etc/apache2/apache2.conf, I WILL NOT ADD ANY LINE HERE
-Create two files (for each virtual host) under /etc/apache2.conf/sites-available/ like deafult and site2 
-Enable both sites via command: a2ensite

Can someone please post two "fakes" virtual hosts sites configuration like an example or guide to me :-) ... I will only change the site content pointers to /var/www and /var/site2, it will help a lot

Thanks,

---

### Post by jocampo on 2009-08-25
Wohoo! just found this super article/guide (which is Debian): [http://www.debian-administration.org/articles/357]("http://www.debian-administration.org/articles/357") can't wait for lunch so I can test it ...

---

### Post by jocampo on 2009-08-25
OK, is working now, yeah! :-D  so I am happy ... but I am kind of confused, this is what I did (following this document: [http://www.debian-administration.org/articles/357#virtual_host]("http://www.debian-administration.org/articles/357#virtual_host") and here are questions 

1st...

```
        <Directory /var/www/mydomain.com/docs>
                [COLOR="Red"]Order Deny,Allow[/COLOR]
                Allow from all
                # Don't show indexes for directories
                Options -Indexes
        </Directory>

```

If I follow that structure, apache complains about, it says can not use both directives at same time or something like that. Unfortunately, did not save the error

2nd
I had to create a two folders under /var/wwww One is the parent folder for the 2nd site and a folder inside that one, for docs  ... why? I thought I can create anything on /var/ and then point the VirtualHost file to that.

3rd and final doubt
I had to create another site under /etc/apache2/sites-available/ . One was there already, "default" ... I create another one blahblahblah.com and edit it; I put something inside like in point 1st. Do I have to create separate files for each site in order to work or this is just for good admin purposes?

Thanks in advance,

---

### Post by jocampo on 2009-08-26
OK, almost there, but getting a funny error when retrieving my second site... if I do not append "www" at the beggining, it just displays the other site instead. For instance ...

If I put [www.fake1.com](www.fake1.com) browser displays--> [www.fake1.com](www.fake1.com) (right)

If I put fake1.com browser displays--> fake1.com (right)

Now...

If I put: [www.fake2.com](www.fake2.com) browser displays--> [www.fake2.com](www.fake2.com) content (right)

If I put fake2.com browser displays--> [COLOR="Red"]fake1.com[/COLOR] (**wrong!!!**)

Why I'm getting the wrong website content when "www" is omitted??? I do not understand. Here's the exact content of each file, which now I am copy/pasting in its total

For fake1.com

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        #I want to be able to access the web site using www.fake1.com
        ServerName www.fake1.com
        DocumentRoot /var/www/fake1.com/docs

        <Directory /var/www/fake1.com/docs>
                Order Deny,Allow
                Allow from all
                # Don't show indexes for directories
                Options -Indexes
        </Directory>
</VirtualHost>
```

For fake2.com

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        #I want to be able to access the web site using www.fake2.com
        ServerName www.fake2.com
        DocumentRoot /var/www/fake2.com/docs

        <Directory /var/www/fake2.com/docs>
                Order Deny,Allow
                Allow from all
                # Don't show indexes for directories
                Options -Indexes
        </Directory>
</VirtualHost>
```

This is driving me crazy...am I missing something or this is a normal behaviour or what?

---

### Post by Adina on 2009-08-26
I'm not sure if this will help but maybe you need to put your domain names in  your /etc/hosts file similar to this, say the local ip is 192.168.1.10 is nated to your public ip:

```
127.0.0.1       localhost
127.0.1.1       LinuxServer

192.168.1.10 fake1.com www.fake1.com
192.168.1.10 fake2.com www.fake2.com


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

or maybe try to check your www redirecting at your registrar or your DNS service.

---

### Post by DaithiF on 2009-08-26
> **jocampo said:**
> OK, almost there, but getting a funny error when retrieving my second site... if I do not append "www" at the beggining, it just displays the other site instead. For instance ...

If I put [www.fake1.com]("http://www.fake1.com") browser displays--> [www.fake1.com]("http://www.fake1.com") (right)

If I put fake1.com browser displays--> fake1.com (right)

Now...

If I put: [www.fake2.com]("http://www.fake2.com") browser displays--> [www.fake2.com]("http://www.fake2.com") content (right)

If I put fake2.com browser displays--> [COLOR=Red]fake1.com[/COLOR] (**wrong!!!**)

Why I'm getting the wrong website content when "www" is omitted??? I do not understand. Here's the exact content of each file, which now I am copy/pasting in its total

This is driving me crazy...am I missing something or this is a normal behaviour or what?
Since fake1 config is loaded first by Apache it acts as a default for any servernames that it doesn't find a match for.  So fake1.com, fake2.com get served by the [www.fake1.com](www.fake1.com) virtual host.  If you want fake2.com to match to [www.fake2.com](www.fake2.com) then i think you can just add it as a ServerAlias in that virtual host config.

---

### Post by Kolipoki on 2009-08-26
> **DaithiF said:**
> If you want fake2.com to match to [www.fake2.com](www.fake2.com) then i think you can just add it as a ServerAlias in that virtual host config.I was about to suggest the same:

```
ServerName www.fake2.com
[COLOR="Red"]ServerAlias[/COLOR] fake2.com
```
Also, if I was troubleshooting for myself, one option I might try is: disabling [www.fake1.com](www.fake1.com) as the default Apache site, but creating it as a non-default site (using the correspondent sites-available config). So you'll probably need something like:

```
sudo a2dissite default && sudo a2ensite fake1.com
```(I hope I got that line right :P). Good luck.

---

### Post by jocampo on 2009-08-26
> **DaithiF said:**
> Since fake1 config is loaded first by Apache it acts as a default for any servernames that it doesn't find a match for.  So fake1.com, fake2.com get served by the [www.fake1.com](www.fake1.com) virtual host.  If you want fake2.com to match to [www.fake2.com](www.fake2.com) then i think you can just add it as a ServerAlias in that virtual host config.

DaithiF, I think you are right, it took me some hours to realize that and I came with this solution (maybe not too elegant) please see below...

Adina:
Thanks for your help anyway :-) ... but problem is that I have a Public IP. And yes, the A records were edited so both are pointing to my webserver/public IP, and the CNAME record "www" is also pointing to my public IP. 

This is my solution (not sure if is the more elegant or the only one)

Fake2 file (_now_)

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        #I want to be able to access the web site using www.fake2.com
        ServerName www.fake2.com
        DocumentRoot /var/www/fake2.com/docs

        <Directory /var/www/fake2.com/docs>
                Order Deny,Allow
                Allow from all
                # Don't show indexes for directories
                Options -Indexes
        </Directory>
</VirtualHost>

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        #I want to be able to access the web site using www.fake2.com
        [COLOR="Red"]ServerName fake2.com[/COLOR]
        DocumentRoot /var/www/fake2.com/docs

        <Directory /var/www/fake2.com/docs>
                Order Deny,Allow
                Allow from all
                # Don't show indexes for directories
                Options -Indexes
        </Directory>
</VirtualHost>


```

On same second file, I added another entry for Servername without "www". It did the trick. Now fake2 loads no matter what ;-) , with or without the "www" ...

Thank you all guys for your help. I'll put a SOLVED tag and hopefully this will help others. I've noticed Apache configuration is not so complex but intuitive, problem is that Apache lacks of Ubuntu specific documentation; most of How To online describe processes for other distros. Ubuntu has a different folder structure.

Thanks again!

---

### Post by jocampo on 2009-08-26
> **Kolipoki said:**
> I was about to suggest the same:

```
ServerName www.fake2.com
[COLOR="Red"]ServerAlias[/COLOR] fake2.com
```
Also, if I was troubleshooting for myself, one option I might try is: disabling [www.fake1.com](www.fake1.com) as the default Apache site, but creating it as a non-default site (using the correspondent sites-enabled config file). So you'll probably need something like:

```
sudo a2dissite default && sudo a2ensite fake1.com
```(I hope I got that line right :P). Good luck.

More elegant solution than mine! ;-) ... thanks ... maybe I'll try it this weekend just to validate Apache Behaviour. I appreciate your help!

---

### Post by Kolipoki on 2009-08-26
> **jocampo said:**
> 
On same second file, I added another entry for Servername without "www". It did the trick. Now fake2 loads no matter what ;-) , with or without the "www" ...

Thank you all guys for your help. I'll put a SOLVED tag and hopefully this will help others. I've noticed Apache configuration is not so complex but intuitive, problem is that Apache lacks of Ubuntu specific documentation; most of How To online describe processes for other distros. Ubuntu has a different folder structure.

Thanks again!

Actually, I forgot to mention, I might be wrong, but I think you can also include both names for the ServerName directive. Like:

```
ServerName www.fake2.com fake2.com
```

That would save you from repeating the whole stuff. Please someone correct me if I'm wrong.

---

### Post by cdenley on 2009-08-26
> **Kolipoki said:**
> 
Please someone correct me if I'm wrong.

I believe you are wrong. That is what the ServerAlias directive is for.
[http://httpd.apache.org/docs/2.2/mod/core.html#servername](http://httpd.apache.org/docs/2.2/mod/core.html#servername)
[http://httpd.apache.org/docs/2.2/mod/core.html#serveralias](http://httpd.apache.org/docs/2.2/mod/core.html#serveralias)

---

### Post by jocampo on 2009-08-26
The SeverAlias instruction did the trick on my fake2 file

Now fake2 file looks like this

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName www.fake2.com
        [COLOR="Red"]ServerAlias fake2.com[/COLOR]
        DocumentRoot /var/www/fake2.com/docs

        <Directory /var/www/fake2.com/docs>
                Order Deny,Allow
                Allow from all
                # Don't show indexes for directories
                Options -Indexes
        </Directory>
</VirtualHost>

```

Now, if I skip the "www" on fake2.com in my browser, it will retrieve the right content anyway NOT fake1.com

---

