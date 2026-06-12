---
title: "Add a .com name to apache using webmin in server 6.10"
date: 2006-12-03
forum: Server Platforms
---

### Post by dj2501 on 2006-12-03
Hello everybody.

I have a fresh install of server 6.10 up and just setup webmin 1.310 on it also.

My question is, I have multiple domains that I want to host on the server. When I go into webmin how do i configure it to send domain1.com to /var/www/domain1 and domain2.com to /var/www/domain2

Any help would be great but I need to know how to do this from webmin. Thanks

-DJ 2501-

---

### Post by mssever on 2006-12-03
> **dj2501 said:**
> Hello everybody.

I have a fresh install of server 6.10 up and just setup webmin 1.310 on it also.

My question is, I have multiple domains that I want to host on the server. When I go into webmin how do i configure it to send domain1.com to /var/www/domain1 and domain2.com to /var/www/domain2

Any help would be great but I need to know how to do this from webmin. Thanks

-DJ 2501-

You do that using Apache's VirtualHost directive. I don't use webmin, but if you're interested in editing the config files by hand, I can help you with that.

---

### Post by dj2501 on 2006-12-03
any way would be great. I have to create a user first correct?

I need step by step intructions.

this is my first time with a linux server

---

### Post by mssever on 2006-12-03
> **dj2501 said:**
> any way would be great. I have to create a user first correct?

I need step by step intructions.

this is my first time with a linux server

First, you'll find the Apache manual to be very helpful.

There are several ways to do this. I'll tell you the way that I consider to be the easiest. Edit /etc/apache2/sites-available/default.

At the end of the file, just before the </VirtualHost> line, insert something like the following: ```
# include the server name in the filenames used to satisfy requests
    VirtualDocumentRoot /home/scott/webmaster/%0
    VirtualScriptAlias /home/scott/webmaster/%0/cgi-bin
```Adjust the paths as you see fit, but take note of the %0. That stands for a directory with the same name as the hostname. So, if I had a site example.com, I would store my files in /home/scott/webmaster/example.com.
Then, restart Apache: ```
sudo apache2ctl graceful
```You need a folder for every hostname you'll use, so I would set up the appropriate symlinks: ```
cd /home/scott/webmaster
ln -s example.com www.example.com
ln -s example.com 123.45.67.89 #The IP address, if it's a dedicated IP
```Do the same for every domain you want to host. You can add domains without restarting Apache. The only requirement is that they resolve properly, via DNS and/or /etc/hosts.

EDIT: I forgot. You need to enable mod_vhost_alias before this will work: ```
sudo a2enmod vhost_alias
sudo apache2ctl graceful
```

---

### Post by dj2501 on 2006-12-03
Wow i didnt realize how new i was to all this until i read that.

Does anybody know how this can be done from inside webmin?

I tryed doing it the way you stated but i get lost about half way through.

Iv heard there is a way to do this from webmin, i guess ill have to wait untill someone that knows webmin gets online.

Thanks for your help.

---

### Post by drokmed on 2006-12-14
I'm trying to remember offhand.  Webmin does have a virtual server config screen.

There are several excellent webmin apache howto's on the Internet.  Google/Yahoo search for them.

---

### Post by MJN on 2006-12-14
> **mssever said:**
> First, you'll find the Apache manual to be very helpful.
 
There are several ways to do this. I'll tell you the way that I consider to be the easiest. Edit /etc/apache2/sites-available/default.
 
At the end of the file, just before the </VirtualHost> line, insert something like the following: ```
# include the server name in the filenames used to satisfy requests
    VirtualDocumentRoot /home/scott/webmaster/%0
    VirtualScriptAlias /home/scott/webmaster/%0/cgi-bin
```
 
Why are you using the vhost_alias module? That is massively overkill for simple (2 site) virtual hosting as in this case... it's simply not needed! That module is designed for managing hosts with upto *thousands* of virtual sites hosted on it, each being dynamically created on the fly.
 
EDIT: Just spotted that you've said *you* find it the easiest way hence I'm assuming that you know the difference between this method and standard virtual hosting.. fair enough.. however this implentation is far from the norm hence if the OP has troubles down the line you may find you'll be his personal support line as the vast majority of Apache users don't of course use vhost_alias.
 
Mathew

---

### Post by hockey97 on 2007-11-13
Hi I am trying to do the same, I have a paid domain name, and trying to virtuial host it , with apche2.

I am using ubuntu 7.10 and webmin .

I one time got it to work well kinda, I got it so that only on my computer with apache if you type in thw web browser the [www.mysite.com](www.mysite.com) it would take you to apache config, like the file you claim is the index, so it took me to my website.

How ever when I restarted my computer I then was not able to do it.

I never was able to on my network with other computers in my house, I never could type [www.mysite.com](www.mysite.com) and get the page it just plainly was not found errors I got, the 404 errors.

I followed alot of how to's on this and couldn't get it working.



You need a folder for every hostname you'll use, so I would set up the appropriate symlinks:
Code:

cd /home/scott/webmaster
ln -s example.com [www.example.com](www.example.com)
ln -s example.com 123.45.67.89 #The IP address, if it's a dedicated IP



is that mainly, I hav eto config somthing in apache2 or config the folder, what are you saying in that step??

do we have to config a file to add our dns info ???




I even made couple of post on here, and tried what advice I was given I still havent' gotten anything working. 

what is  the appropriate symlinks

---

### Post by MJN on 2007-11-14
> **hockey97 said:**
> I even made couple of post on here, and tried what advice I was given I still havent' gotten anything working.
 
That is **exactly** why I have not responded to your queries - not only are you cross-posting the same query over and over but you are hijacking other user's threads in the process (and given you don't know the cause of your problem you don't know of yours is related to theirs).
 
Post your own thread describing **your** problem then you might get the assistance you are looking for whilst allowing others to get the help they've requested.
 
Mathew

---

### Post by hockey97 on 2007-11-15
I have created my own post, I only got 2 replies and that was it.

I posted on my post more info and stuff and no one is replying.

it's been up for long time.

my problem is similar to this, somewhat, it's about apache2 virtuial hosts.

I have seen many howto's on the internet followed those and didn't get it working.

I config bind9 , and also apache2 according to the howto's . 

the replies I got on my post was, to google howtos and also make sure I put the vhost file in the folder /etc/apache2/sites-enabled 

and what was it.

I am not trying to steal this post, I was hopeing to get more replies,

by going to similar post's that have the same somewhat goal or problem,

---

### Post by MJN on 2007-11-15
I didn't mean to offend, it's just very frustrating to keep reading what appears to be the same posts from you in multiple threads! Perhaps my perception is exaggerated but it feels like they're everywhere!

I know you're keen to get your problem sorted but you can't just tag your issue onto any post that happens to mention 'virtual' and 'host' in the same sentence! ;) Okay, you can but it's kind of hard to dedicate time to go through the issue when you could well be doing so in parallel in another thread with others - it could easily be a waste of our, and your, time and effort doing so.

I was about to say I'll see you over in your own thread that you've started and help diagnose the problem - but where is it?!

Mathew

---

