---
title: "Apache Memory Usage"
date: 2009-10-14
forum: Server Platforms
---

### Post by Gizmokid2005 on 2009-10-14
I'm at wits end everyone, and I've come to you for help.

I recently got a VPS with FiveBean and am LOVING having full access to it.  After lots of configuring and reloads, and installing, repeat, I've got just about everything installed that I need, but I've come to an issue.

Apache2 will just EAT ram like there is no tomorrow.  it's not uncommon for it to be using nearly 400MB of my total ram.  I've googled and gone through different configs, but I cannot figure out why it's utilizing so much memory.

Most of the articles/info I've found have related to Ubuntu Desktop edition, not Server, and I've even tried them in desperation to no avail.

The only way I've managed to even *partially* manage the usage is set a cron to restart apache every 10 minutes to keep the usage down.

I need some help optimizing it to actually run and behave as it should.

Let me know what information you want/need and I'll get it to you.

TIA!

-Gizmokid2005

---

### Post by Gizmokid2005 on 2009-10-15
Anybody have any ideas?

---

### Post by t3r0 on 2009-10-15
> **Gizmokid2005 said:**
> Anybody have any ideas?

Hi, Please tell a little more about your config there: what kind of pages you are hosting, how much traffic the server is handling at the moment, apache configuration etc etc..  so we can get some kind of idea what going on there :) 


- Tero

---

### Post by Gizmokid2005 on 2009-10-15
Most of the pages I'm hosting are PHP, I run my single [WP blog]("http://gizmokid2005.com") off of it, typically less than 20 visits per day.  So it shouldn't be serving up that much info.  I can watch the mem usage spike when I visit the page as well.

Here's a link to my [PHP Info]("http://vps.gizmokid2005.com/phpinfo.php").  

I'm currently using the mpm_worker_module as I tried the mpm_prefork_module and the performance was no better.

I've attached my apache2.conf as well.

Let me know any other info you need.

---

### Post by R.Bucky on 2009-10-16
have you used top or htop to see the process that is chewing up the RAM. clearly, there is a config issue. I operate 9 or so domains from my server and rarely eat up 500MB RAM.

---

### Post by Gizmokid2005 on 2009-10-16
> **R.Bucky said:**
> have you used top or htop to see the process that is chewing up the RAM. clearly, there is a config issue. I operate 9 or so domains from my server and rarely eat up 500MB RAM.

I know for a fact it's apache.  I've been watching top ever since I originally configured the server to see what package would be good for me.  I've attached a screenshot below, but apparently apache was recently restarted and this is after I visited my site once, typically there'll be 5+ apache processes using 29M+ ram at a time.

[img]http://gizmokid2005.com/top.png[/img]

---

### Post by Gizmokid2005 on 2009-10-16
Here's a better image of what top normally looksl ike with apache not behaving:

[img]http://gizmokid2005.com/top2.png[/img]

And instead of a new post, here's another idea.

[img]http://gizmokid2005.com/top3.png[/img]

---

### Post by t3r0 on 2009-10-17
Hi,

Looks like a normal behavior of apache with that config. With your traffic you really don't to tune your apache at all. If you don't want the apache to start so many processes try to revert the worker module settings to defaults (or even lower). Here are the defaults of ubuntu 9.04

```

<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

```  

You can also turn off KeepAlive, and tune some other settings but if you don't have much of ram there and if you are worried about the current ram use  of apache then you should maybe consider using some other web server software. some good examples of http servers with low memory footprint are Lighttpd and Nginx. Both can be found from ubuntu repos and are easy to setup and configure.


- Tero

---

### Post by Gizmokid2005 on 2009-10-17
> **t3r0 said:**
> Hi,

Looks like a normal behavior of apache with that config. With your traffic you really don't to tune your apache at all. If you don't want the apache to start so many processes try to revert the worker module settings to defaults (or even lower). Here are the defaults of ubuntu 9.04

```

<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

```  

You can also turn off KeepAlive, and tune some other settings but if you don't have much of ram there and if you are worried about the current ram use  of apache then you should maybe consider using some other web server software. some good examples of http servers with low memory footprint are Lighttpd and Nginx. Both can be found from ubuntu repos and are easy to setup and configure.


- Tero

I tried both setting the mpm_worker back to those defaults and turning off KeepAlive and neither has helped.

I know that apache can run with a MUCH smaller memory footprint than it's running at now, typically it's at 250M+ ram usage...and that seems more than excessive for one website...

---

### Post by R.Bucky on 2009-10-18
250MB total is not an out of the ordinary RAM usage based on my current and previous installations. You operate a GUI server, so that 250-400MB RAM is normal.

---

### Post by Gizmokid2005 on 2009-10-18
> **R.Bucky said:**
> 250MB total is not an out of the ordinary RAM usage based on my current and previous installations. You operate a GUI server, so that 250-400MB RAM is normal.

That's the thing. I don't run a gui server. I'm running ubuntu server, all cli and ssh. I would understand if it was a gui server but it's not.

---

### Post by R.Bucky on 2009-10-18
Ok. What do your error.log and dmesg logs say?  A script to restart apache would not solve the problem, only making the problem seem to go away. What sort of scripts do you have on these pages, if any. You might try removing your content  from the apache directory to try and narrow down the problem from a content perspective?  Just a couple of thoughts...

---

### Post by lesswatts on 2009-10-18
I would try installing mpm-prefork.  I had a similar issue, and using mpm-prefork instead of mpm-worker greatly reduced my memory usage.

```
sudo apt-get install apache2-mpm-prefork
```

---

### Post by Gizmokid2005 on 2009-10-18
> **lesswatts said:**
> I would try installing mpm-prefork.  I had a similar issue, and using mpm-prefork instead of mpm-worker greatly reduced my memory usage.

```
sudo apt-get install apache2-mpm-prefork
```

They are both installed, I tried both, and they both yielded about the same RAM utilization.  I'd seen that recommendation a few times in my searches.

---

### Post by Gizmokid2005 on 2009-10-18
> **R.Bucky said:**
> Ok. What do your error.log and dmesg logs say?  A script to restart apache would not solve the problem, only making the problem seem to go away. What sort of scripts do you have on these pages, if any. You might try removing your content  from the apache directory to try and narrow down the problem from a content perspective?  Just a couple of thoughts...

My error.log seems to be full of just hits from people who are trying to get to files that are linked to my IP by IP.  Old links that are dead and bad, nothing out of the ordinary.

I'm not sure what the dmesg logs are.  All the logs that have "dmesg" in the name, and are in /var/log/ are all empty.  There are a few "dmesg, dmesg.0, dmesg.1.gz, dmesg.2.gz, dmesg.3.gz, dmesg.4.gz", but they are all empty.

I know the apache restart doesn't fix it, it's just a way for me to keep the usage back down so my host doesn't get mad that I'm almost always over my Dedicated RAM limit.  I would preferably not have to restart apache at all unless I make changes or something.

I'm going to do some tests with just standard HTML pages and see if that makes a difference.

Like I said before, I'm just running some normal PHP pages, a wordpress blog, and phpBB (which doesn't ever get accessed).

---

### Post by Gizmokid2005 on 2009-10-18
I just switched it up a bit.  Apache seems to be ok with most plain HTML pages, but as soon as I loaded up PHPMyAdmin and browsed that for a few pages, it was up to 250M RAM utilization already.

It seems that apache just doesn't like PHP at all?  I really don't know, I'm at my wits' end, hence why I'm here :(

---

### Post by Vegan on 2009-10-18
I use PHP and my old IBM has 768MB of RAM, so its no big deal. I have not seen the memory load all that bad with a standard LAMP stack.

---

### Post by Gizmokid2005 on 2009-10-18
I really don't mind using LAMP or something if it comes down to it, I use xampp on my windows box here at home, but I'd like to get this issue figured out.  Nothing irks me more than an issue like this and not being able to solve it.

---

### Post by R.Bucky on 2009-10-18
Never really had this issue. Weird. As a last resort, have you tried a complete apache remove and install? Hate to even suggest it, but I have install a dozen or so Apache install on individual boxes, never having this type of issue. I'm tapped out!

---

### Post by Gizmokid2005 on 2009-10-18
I did.  I actually did it a few times when I was first setting everything up that I needed.  This is my first real delve into ubuntu without a gui.  I thought it might've been due to the way I was setting things up, and the removal/addition of apps/modules.  But it seems that isn't the case.

EDIT****

I might give it a shot though, just see if it helps...just make a backup beforehand, can't hurt.

---

### Post by Gizmokid2005 on 2009-10-19
Well, I've found a partial fix finally, with the help of some fellow IRC users (thanks to both of you :D ).

Adding "ServerLimit" in my apache2.conf worked, I added it right outside of the <IfModule mpm_worker_module> closing tags as such:

```

<IfModule mpm_worker_module>
StartServers       2
MaxClients        200
MinSpareThreads    15
MaxSpareThreads    80
    ThreadsPerChild      25
    MaxRequestsPerChild  100
        MaxMemFree       75000
</IfModule>

ServerLimit 5

```

Now I only have 5 processes that are semi-ram hungry, typically between 25 and 55M each.


I'm still open for any other options on how to tame apache down any more.  This is at least a start.

---

### Post by lesswatts on 2009-10-19
What modules do you have enabled?

---

### Post by Gizmokid2005 on 2009-10-19
My full mods-enabled file:

```
" ============================================================================
" Netrw Directory Listing                                        (netrw v132)
"   /etc/apache2/mods-enabled
"   Sorted by      name
"   Sort sequence: [\/]$,\.h$,\.c$,\.cpp$,*,\.o$,\.obj$,\.info$,\.swp$,\.bak$,\~$
"   Quick Help: <F1>:help  -:go up dir  D:delete  R:rename  s:sort-by  x:exec
" ============================================================================
../
alias.conf@
alias.load@
auth_basic.load@
authn_file.load@
authz_default.load@
authz_groupfile.load@
authz_host.load@
authz_user.load@
autoindex.conf@
autoindex.load@
cgi.load@
deflate.conf@
deflate.load@
dir.conf@
dir.load@
env.load@
mime.conf@
mime.load@
negotiation.conf@
negotiation.load@
php5.conf@
php5.load@
rewrite.load
setenvif.conf@
setenvif.load@
status.conf@
status.load@

```

---

