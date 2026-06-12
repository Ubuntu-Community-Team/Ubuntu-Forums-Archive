---
title: "Virtualhost can not access folders apache2"
date: 2008-01-24
forum: Server Platforms
---

### Post by yanny on 2008-01-24
Hi,

I've made a virtual host for yanny.nl.

When I go to [http://yanny.nl/](http://yanny.nl/) in my browser I get the index page of [http://yanny.nl](http://yanny.nl) which is good.

In /etc/apache2/httpd.conf I have typed this:

<virtualhost *:80>
ServerName yanny.nl
DocumentRoot /var/www/yanny.nl
</virtualhost>

With that code above it will be redirected to [http://yanny.nl/](http://yanny.nl/) and show the contents of it when I type [http://localhost/](http://localhost/) in my browser.

My problem is if I make a new folder in /var/www/
the browser doesn't recognize it... it says it doesn't exitst...:(

I noticed in /etc/apache2/apache.conf these two lines:

Include /etc/phpmyadmin/apache.conf
Include /etc/squirrelmail/apache.conf

Because of these two lines I can go to [http://yanny.nl/phpmyadmin](http://yanny.nl/phpmyadmin) and [http://yanny.nl/squirrelmail](http://yanny.nl/squirrelmail)
Should I make an include for all the folders I want to access? Oh my god that is really too ridiculous then... 
it should work automatically...

---

### Post by MJN on 2008-01-24
Hi Yanny,
 
> **yanny said:**
> Hi,
 
I've made a virtual host for yanny.nl.
 
When I go to [http://yanny.nl/](http://yanny.nl/) in my browser I get the index page of [http://yanny.nl](http://yanny.nl) which is good.
 
In /etc/apache2/httpd.conf I have typed this:
 
<virtualhost *:80>
ServerName yanny.nl
DocumentRoot /var/www/yanny.nl
</virtualhost>

 
That code should not go in httpd.conf - nothing should on Debian-based systems as Apache's config is now 'modularised' i.e. the config is split up amongst numerous files. Httpd.conf exists now purely for backwards compatibility in case some packages expect it to be there.
 
So, you need to be looking in /etc/apache2/sites-available/default - this file is your default website and hence, in the absence of any other sites, you should put your config in there (there will already be a <VirtualHost> container so use that one).
 
> My problem is if I make a new folder in /var/www/
the browser doesn't recognize it... it says it doesn't exitst...:(
 
That's because you've told Apache that the web root is /var/www/yanny.nl/ and so anything above that, including for example /var/www/test/, does not exist - it is outside (above) of the root. Hence, any folders you wish to create should be under yanny.nl e.g. /var/www/yanny.nl/folder You would then browse to it with [http://www.yanny.nl/folder](http://www.yanny.nl/folder)
 
Speaking of URLs, you should add **ServerAlias [www.yanny.nl]("http://www.yanny.nl")** to your config above.
 
> I noticed in /etc/apache2/apache.conf these two lines:
 
Include /etc/phpmyadmin/apache.conf
Include /etc/squirrelmail/apache.conf
 
Because of these two lines I can go to [http://yanny.nl/phpmyadmin](http://yanny.nl/phpmyadmin) and [http://yanny.nl/squirrelmail](http://yanny.nl/squirrelmail)
Should I make an include for all the folders I want to access? Oh my god that is really too ridiculous then... 
it should work automatically...
 
Ridiculous indeed - fortunately it was a misunderstanding on your part. ;)
 
All those lines are saying is 'include the configuration found in these files as if they were written here'. Take a look in the files - they'll look similar to what you've configured yourself.
 
Does that help? Shout for further clarification if required.
 
Mathew

---

### Post by yanny on 2008-01-24
> **MJN said:**
> 

Speaking of URLs, you should add **ServerAlias [www.yanny.nl]("http://www.yanny.nl")** to your config above.
 
Does that help? Shout for further clarification if required.



Thanks for the fast reply! Yeah I'm very new to Linux and servers etc.. I need to this for school.

How do I add server Alias to the config?

---

### Post by MJN on 2008-01-24
Just put it underneath your ServerName directive (which I assume now lives inside /etc/apache2/sites-available/default file if you've followed the above!).
 
This is probably a good time to suggest you familarise yourself with the Apache documentation, particularly that related to directives. For example, see [http://httpd.apache.org/docs/2.0/mod/core.html#serveralias](http://httpd.apache.org/docs/2.0/mod/core.html#serveralias) for the ServerAlias directive - it tells you what it's for, how it looks, where it fits (i.e. <virtualhost> containers in this case) etc. The example should help illustrate its use too.
 
Mathew

---

### Post by yanny on 2008-01-24
I've got some questions, I have read all what you have written above.

Shouldn't it be 000-default in /etc/apache2/sites-enabled, to put the config in? Because the color of that filename is light blue like this emoticon :confused: 
But it works!

I got another problem I cannot access [http://localhost/postfixadmin](http://localhost/postfixadmin) ... why, I know it's a lil off-topic... but I can access [http://localhost/test](http://localhost/test)

---

### Post by MJN on 2008-01-24
> **yanny said:**
> I've got some questions, I have read all what you have written above.
 
Shouldn't it be 000-default in /etc/apache2/sites-enabled, to put the config in? Because the color of that filename is light blue like this emoticon :confused: 
But it works!
 
Here comes the second Apache thing you'll have learnt today..!
 
All of those 'files' in sites-enabled/ are actually symlinks (a bit like shortcuts) to the files in sites-available. That's why they're light blue (and will also be shown alongside a pointer to the real file). Hence, when you opened/edited the 000-default file you were actually opening/editing the default file in sites-available.
 
Incidentally, the purpose of this setup is that you can have a whole load of different sites' config in sites-available and turn them on/off by adding/removing the symlinks in sites-enabled. Rather than do this manually there are two tools to do this - a2ensite and a2dissite.
 
Note you won't find any of this in the Apache online docs - it's a Debian/Ubuntu thing.
 
> I got another problem I cannot access [http://localhost/postfixadmin](http://localhost/postfixadmin) ... why, I know it's a lil off-topic... but I can access [http://localhost/test](http://localhost/test)
 
Given your documentroot is /var/www/yanny.nl/ do you have a /var/www/yanny.nl/postfixadmin folder? If not then presumably postfixadmin is a package (I'm not familiar with it) in which case it will likely have added some config to Apache to alias the /postfixamin folder to somewhere within its own files. Has this ever worked?
 
Mathew

---

### Post by yanny on 2008-01-24
Thank you for explaining sites-enabled and sites-available! :)

I accidentally deleted the config in sites-enabled. So I can make the link with a2ensite?

This is the first time I installed postfixadmin, it had never worked, maybe reinstalling help?

---

### Post by MJN on 2008-01-24
> **yanny said:**
> Thank you for explaining sites-enabled and sites-available! :)

I accidentally deleted the config in sites-enabled. So I can make the link with a2ensite?

Remember, there is no config in sites-enabled - just pointers to the config in sites-available. However, to get that symlink back just type **sudo a2ensite** and you will be given a choice (if applicable) of sites/config to include - specify **default**.

> This is the first time I installed postfixadmin, it had never worked, maybe reinstalling help?

Perhaps. I've never used it so don't know anything about how it works or interfaces with Apache etc.

Mathew

---

### Post by yanny on 2008-01-24
Ok, it says sites already enabled.

I've a last question (I hope), when I go to localhost in the browser then it displays the content of localhost and when I go to yanny.nl it displays the content of yanny.nl but then... I want if I go to localhost it displays yanny.nl content... maybe I ask too much?

Well why do I want this? Because when I make a mailserver I need a domain name (I don't want to register an internet domain) so I want to use virtual domain yanny.nl and displays the content of yanny.nl instead of localhost...

It works if I put the following in httpd.conf:

<virtualhost *:80>
ServerName yanny.nl
DocumentRoot /var/www/yanny.nl
</virtualhost>

then it displays the content of yanny.nl when I go to [http://localhost](http://localhost)

but it's not the good way to do, because other folders above wouldn't be displayed then we come back to my first post's problem ;)

How can I do?

---

### Post by MJN on 2008-01-24
Stay out of http.conf. Seriously. If you go back in there you're on your own.

Clarify what you want to -

What do you want [http://localhost](http://localhost) to show? (the contents of which folder?)

What do you want [http://yanny.nl](http://yanny.nl) to show? (the contents of which folder?)

The mail server bit is confusing me - what does Apache have to do with this?

I know you know what you want to achieve, but you need to explain it to me in order for me to help you achieve it. (and here's me accusing *you* of being confusing!)

Mathew

Edit: Post your current /etc/apache2/sites-available/default file too - we'll use that as our default base.

---

### Post by yanny on 2008-01-24
Matthew, 

Here is the code of /etc/apache2/sites-available/default

NameVirtualHost *:80
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                RedirectMatch ^/$ /apache2-default/
        </Directory>
      ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
ServerSignature On


 Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>

<virtualhost *:80>
ServerName yanny.nl
ServerAlias yanny.nl [www.yanny.nl](www.yanny.nl)
DocumentRoot /var/www/yanny.nl
</virtualhost>


Well, the reason why I make a virtual host ([www.yanny.nl](www.yanny.nl)) is because I thought I can use that as domain name for my mailserver...

I'm not good in that too, maybe you are? I've posted in another topic something about mailserver, maybe you can read that: [http://ubuntuforums.org/showthread.php?t=675941?](http://ubuntuforums.org/showthread.php?t=675941?)

I'm going to sleep now, bye hope to hear your reactions!

---

### Post by MJN on 2008-01-24
The domain you use for your mail has no impact on Apache. Remember Apache is a web server hence is only concerned with hosting websites. You don't need any mention of yanny.nl in the Apache config in order for your mail server to function.

You config, as stands, provides the following:

- Requests for [http://localhost](http://localhost) (or direct IP address e.g. 127.0.0.1) will result in the contents of /var/www/ being displayed.

- Requests for [http://yanny.nl](http://yanny.nl) will display the contents of /var/www/yanny.nl. This assumes you've either got yanny.nl configured in a DNS or you have an entry in /etc/hosts

Is this what you want? If not, what is it you want?

Mathew

P.S. I did see your other post but stayed away as it was not clear to me what you were trying to achieve (deja vu?! ;))

---

### Post by yanny on 2008-01-25
What I want is what you said DNS or /etc/hosts.
I want to display the content of yanny.nl when I type in localhost.

This is my /etc/hosts file:

127.0.0.1 localhost localhost.localdomain yanny.nl [www.yanny.nl](www.yanny.nl)

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

By the way I noticed that when I go to yanny.nl I get the contents of localhost.. why?
Yesterday it was not like this...

I'm soooo desperate. :( Because I'm afraid what I'm doing is very wrong.. or at least doesn't work. At the other thread I asked for some info about mailserver, I got proper response, but then it seems like I cann not use virtual image to make the mailserver, it seems like I need to have one at home and then port forwarding... :( That's my biggest problem my parents wouldn't want port forwarding .. 

I know it's off-topic, but could you clarify for me? Must I really have a static ip-address etc.. and a computer at home which is 24 hours on?

---

### Post by MJN on 2008-01-25
> **yanny said:**
> What I want is what you said DNS or /etc/hosts.
I want to display the content of yanny.nl when I type in localhost.
 
In that case scrap your second virtualhost and dump everything from it into the first (default) virtualhost container in the above config. Remember to overwrite the DocumentRoot setting to be /var/www/yanny.nl
 
> I'm soooo desperate. :( Because I'm afraid what I'm doing is very wrong.. or at least doesn't work. At the other thread I asked for some info about mailserver, I got proper response, but then it seems like I cann not use virtual image to make the mailserver, it seems like I need to have one at home and then port forwarding... :( That's my biggest problem my parents wouldn't want port forwarding .. 
 
It's really not clear what you're trying to do - perhaps to you it is but not me!
 
You mentioned in the other thread about setting up a mailserver for local use only. What do you mean by this? What actually is it you're trying to achieve? (Describe the end goal, not the means you think you need to achieve it)
 
Mathew

---

### Post by yanny on 2008-01-25
> **MJN said:**
> In that case scrap your second virtualhost and dump everything from it into the first (default) virtualhost container in the above config. Remember to overwrite the DocumentRoot setting to be /var/www/yanny.nl


Ok, I will do that...

>  
It's really not clear what you're trying to do - perhaps to you it is but not me!
 
You mentioned in the other thread about setting up a mailserver for local use only. What do you mean by this? What actually is it you're trying to achieve? (Describe the end goal, not the means you think you need to achieve it)
Mathew

What I want to achieve is to have a mailserver on vmware (virtual machine) as you know yanny.nl works I want to build my website (webmail) there people on the same LAN (locally) can send email to me and vice versa. People must go to [http://yanny.nl](http://yanny.nl) and then they can login to send email to me...That's my final goal. As I work on different computers I always bring my external harddrive everywhere to use it (home & school), so I don't want to port fowarding... 

I hope it's clear now, ask questions if you like.

---

### Post by MJN on 2008-01-25
> **yanny said:**
> What I want to achieve is to have a mailserver on vmware (virtual machine) as you know yanny.nl works I want to build my website (webmail) there people on the same LAN (locally) can send email to me and vice versa. People must go to [http://yanny.nl](http://yanny.nl) and then they can login to send email to me...That's my final goal.
 
Okay - I understand. So who/where will these LAN users be?
 
What webmail client are you going to use? I'd recommend Squirrelmail - nice and simple and works well. Whatever you choose you'll need a backend IMAP/POP server for the mail storage and retrieval (again, my preference is Dovecot).
 
> As I work on different computers I always bring my external harddrive everywhere to use it (home & school), so I don't want to port fowarding...
 
That bit I really don't understand. Are all these LAN clients coming with you?
 
All in all it sounds either like a very bizarre way of doing things, or a unique solution to your unique situation. I cannot put my finger on which it is yet!!
 
Mathew

---

### Post by yanny on 2008-01-25
I have very very little acknowledgment of these stuffs, bare with me..

> That bit I really don't understand. Are all these LAN clients coming with you?

I don't understand that LAN thing too, I want to make a network as well so other clients can join my network... is that possible then?

---

### Post by MJN on 2008-01-25
I really don't know - it's not clear to me what you're doing here. I'm sure it's my misunderstanding so hopefully someone might know and be able to help!

Mathew

---

### Post by yanny on 2008-01-25
Shall I explain again?

---

### Post by yanny on 2008-01-25
I want to have Dovecot as backend IMAP/POP server and Squirrelmail client on the **same **computer! Is that possible?

---

### Post by MJN on 2008-01-25
Of course!

---

### Post by yanny on 2008-01-26
Ok, if that is possible then could I send email to other computers as well? Or how can I make it so that other computers can access mine to get connected to IMAP/POP server?

---

### Post by MJN on 2008-01-26
That all depends on your configuration. Your intention of carrying around a virtual machine on a hard drive is unusual to say the least so you'll have to figure that one out for yourself I'm afraid!

Mathew

---

### Post by yanny on 2008-01-26
Thanks for your reply!

I carried the virtual machine mainly because I want to work at school and at home. My teacher (which has not much experience with it says it's a good idea to carry the virtual machine everywhere...).

The presentation will be held at school, so finally it must work in the school network. What I worry now is could I finish this assignment or else I failed in graduating...

---

### Post by MJN on 2008-01-26
No pressure then! ;)

It's strikes me as being an unusual configuration, but then if it is part of a project then that's by-the-by - it it were easy there'd be little point in doing it.

I'm not saying any of this is impossible by the way, it's just that I don't personally have any experience of such a setup hence cannot really help with the nuances of the issues.

Mathew

---

### Post by yanny on 2008-01-31
I just want to tell that I succeed in making a mail server part 1.

 I finally configured the Postfix correctly so that it works, they (my classmates) recommended me to use a new image to do this without other useless programs. I can send email to myself locally. 

I have tried to send email to user [email]yanny@yanny.nl[/email] via root and it works, I used Thunderbird to connect to yanny.nl and I received that email. By the way yanny.nl is a fake domain in other words it's a DNS, in etc/hosts I set my ipaddress and next to it yanny.nl.

Now I need to see if other computers can send email to me... etc..

---

