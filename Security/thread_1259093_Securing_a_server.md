---
title: "Securing a server"
date: 2009-09-05
forum: Security
---

### Post by phillw on 2009-09-05
In my search for some better understanding of how to 'harden' a server, I stumbled upon this

[http://secure-ubuntu-server.blogspot.com/2009/07/howto-hardening-your-apache-and-php-on_07.html](http://secure-ubuntu-server.blogspot.com/2009/07/howto-hardening-your-apache-and-php-on_07.html)

The stuff is relevant to my 9.04 installation, it is in bite sized chunks and I have been following up on his recomendations, and following up on other replies to his blog.

The $64,000 is, do you guyz and galz with loads of experience think it is 

a) useful to follow 
b) implement what he has added
c) don't go anywhere near his recommendations.

You're the ones in the know !!

Thanks,

Phill.

---

### Post by HermanAB on 2009-09-06
Step one:
Always use very long passwords.  Mine are typically 12 to 16 characters semi pronounceable.

There is no step two.
:)

---

### Post by unspawn on 2009-09-06
> **phillw said:**
> useful to follow (..) implement what he has added

Yes, with a few notes. The first and most generic three most important items I would like to put forward are:
- don't take "answers" at face value (but try to understand what they mean before implementing them and discuss or ask for details or examples if unclear),
- don't take one arbitrary source of information as all-encompassing and authoritative (but also check your distributions documentation, the security documentation stickies in this security forum, the extensive Debian Security HOWTO and authoritative outlets like the software vendors documentation, the SANS Reading Room, etc.)
- security is not "fire and forget", it is a continuous process of checking, reading logs and readjusting configuration. 


That said, you didn't post about doing it (and the web log entry doesn't advertise it) but like everything else things start with a solid foundation. So before hardening your "AMP" part of LAMP you should properly configure and harden your OS installation using the sources of documentation mentioned before hardening services. 


The second thing you didn't post about is what you're going to run *on top of LAMP*. PHP is favoured by many but this also means that there many products of many different levels of (code) quality). For example there are still people who think that they could run quick prototyping development products (like XAMPP) publicly accessable without repercussions (while the developers docs explicitly state it shouldn't be) or that allowing a password of "test" will do fine "just for now" (guess what) or flipping a boolean like allow_url_fopen to "off" again after installation (some products will not install without).
The web log mentions Cross-Site-Tracing attacks and using mod_security. That's good but not the only measures or only attacks to look at so, combined with how what you run affects the security posture of your machine, you should check the vendors docs, [http://www.sans.org/top20/](http://www.sans.org/top20/) and [http://www.owasp.org/index.php/Top_10_2007](http://www.owasp.org/index.php/Top_10_2007) (couldn't find a more recent version, sorry).


Finally I'd like to suggest that after making changes you test your setup with local assessment tools (say GNU Tiger), remote scanning tools (Nessus or an equivalent) and maybe a online scanning service like securityspace.com.


//* Password policy, as HermanAB mentioned is a small part of that. While it may have been meant jocularly I strongly disagree with the "There is no step two" as it's not funny and utterly incomplete as my reply shows.

---

### Post by bodhi.zazen on 2009-09-06
The blog you linked to basically does 3 tings :

1. security through obscurity. Basically you have disabled information in error messages.

2. Mod_evasive.

3. Mod_security.

I suggest you start by learning about Apache, Mysql, and PHP. Mod security can be tricky to use.

Those things are nice, but IMO they are the icing on the cake.

---

### Post by unspawn on 2009-09-06
> **bodhi.zazen said:**
> security through obscurity. Basically you have disabled information in error messages.
With all due respect but I think it's a bit much to call it that due to the negative connotations "security through obscurity" has. In my book "security through obscurity" is creating a false sense of security, deliberately deploying to measures that do not measurably enhance security *when they are available*. A good (and unfortunately too common) example of "security through obscurity" would be for example, when asked for measures to secure SSHd, answering to only to use another port instead of offering your average multi-layer approach of disallowing root account access, using AllowUsers/Groups, using tcp wrappers, firewalling, fail2ban (or equiv.).

While I wouldn't go as far as to call it a "best practice", restricting access to version information (even though probably retrievable by other means) is definately *common sense* and nothing to scoff at.

---

### Post by Sporkman on 2009-09-06
> **unspawn said:**
> With all due respect but I think it's a bit much to call it that due to the negative connotations "security through obscurity" has. In my book "security through obscurity" is creating a false sense of security, deliberately deploying to measures that do not measurably enhance security *when they are available*. A good (and unfortunately too common) example of "security through obscurity" would be for example, when asked for measures to secure SSHd, answering to only to use another port instead of offering your average multi-layer approach of disallowing root account access, using AllowUsers/Groups, using tcp wrappers, firewalling, fail2ban (or equiv.).

While I wouldn't go as far as to call it a "best practice", restricting access to version information (even though probably retrievable by other means) is definately *common sense* and nothing to scoff at.

I'd categorize the obscurity angle as not giving anything away for free. If a hacker wants that info, let him exert the time & effort obtaining it. You're bound to have some percentage of them give up out of laziness or fail due to lack of info. While not a solution, it's an easy way to lower the probability (albeit slightly) of getting hacked.

---

### Post by jobst on 2009-09-07
> **phillw said:**
> In my search for some better understanding of how to 'harden' a server, I stumbled upon this

[http://secure-ubuntu-server.blogspot.com/2009/07/howto-hardening-your-apache-and-php-on_07.html](http://secure-ubuntu-server.blogspot.com/2009/07/howto-hardening-your-apache-and-php-on_07.html)


Phill.

The stuff he mentions is ok, but its only a part of it. What about firewalls, ssh from everywhere?, file access, passwords, running apache as nobody, DMZ and MUCH more.

This is only the egg shell.


Jobst

---

### Post by phillw on 2009-09-07
Wow !!

Thanks everyone :-)

As a couple of the mods here will know - I made a pigs ear of setting up my SSH and got compromised.

On Passwords - I use the ones generated by phpmyadmin, with a couple of 'understandable' 10+ character passwords.

After about a week, I do actually get to remember the likes of  2#r%_u(w)?Dt+![@    

HTTP will be the 1st thing to be turned on, once I've learned enough to stop the various security issues with it.

I'm using firestarter at the moment, but will eventually be switching to shorewall - I find firestarter a good way to learn the basics of iptables. 

ossec is on & running.

As mentioned, I do learn about what each layer of the security onion does before implementing them, that blog being part of my reading of other sources - There seems little to be gained from me reading other views / blogs / how-to's if what they are suggesting is either non-effectual or even down right harmful.

I've ensured that the likes of MySQL has the default users removed, disabled root etc. After what happened the last time, I will certainly be configuring and checking very heavily, each port that i open.

Once again, thanks for your replies - and a special thanks to bodhi for his tutorials in this section. A headache they may cause, but nothing to that I had when I didn't quite setup SSH correctly.

For Configuring Apache, which is where I am at present, I'm getting my head round what is here [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)
I'm figuring that what they say about configuring it up is recommended reading.

Phill.

---

### Post by phillw on 2009-09-07
Tip toes ....

When I installed mod-security, I made the link as instructed, so I have

```

lrwxrwxrwx   1 root root    30 2009-09-04 11:31 logs -> /var/log/apache2/mod_security/


```

Am I correct in thinking that I should alter the permissions on that link to something like **640**   ?

```

phillw@piglet:/etc/apache2$ ls -l /var/log/apa*

drwxr-xr-x 2 root root  4096 2009-09-04 23:42 mod_security  

```

```

phillw@piglet:/etc/apache2$ ls -l /var/log/apa*/mod*
-rw-r----- 1 root root 0 2009-09-04 23:42 modsec_audit.log
-rw-r----- 1 root root 0 2009-09-04 23:42 modsec_debug.log


```

Thanks,

Phill.

---

### Post by bodhi.zazen on 2009-09-07
First, that is a link, and so you set permissions on the target.

Second apache runs as www-data, so I 

chown root.www-data
chmod 660

on the mod_sec logs in /var/log/apache

---

### Post by phillw on 2009-09-07
> **bodhi.zazen said:**
> First, that is a link, and so you set permissions on the target.

Second apache runs as www-data, so I 

chown root.www-data
chmod 660

on the mod_sec logs in /var/log/apache

Is this correct ?

```

drw-rw---- 2 root www-data  4096 2009-09-04 23:42 mod_security


```

---

### Post by bodhi.zazen on 2009-09-07
for directories you need rwx
for files (logs) you need rw

www-data is the user that need access.

---

### Post by phillw on 2009-09-07
Forgive me for being a pain - After what happened before, and I see still happening to others - I really want to get this bit right.

I have reset owner & group to me .... It matters not, piglet is not allowed out to play with incoming internet connections for quite a while yet - router is fully firewalled, as is firestarter !!

Let me know if this is correct ....

cd  /var/log/apache2/mod_security
chmod 600 *log            (modsec_audit.log   &   modsec_debug.log)
cd ..                          ( puts me in /var/log/apache2)
chmod 600 *            (all the other .log files and other_vhosts_access.log.2.gz  etc)
sudo chmod 700 mod_security
sudo chgrp -R root *
sudo chown -R www-data *
cd ..                         (puts me in /var/log)
sudo chmod 700 apache2
sudo chgrp root apache2
sudo chown www-data apache2

A couple of questions, 

[LIST=1]
[*]will rotate-log still be able to rotate my vhosts_access.log
[*] how do I read the logs ? (the login of 'root' is disabled).
[/LIST]
Once again, thanks ever so much for bearing with me - i REALLY want to get this right.

Phill.

P.S., tomorrow I want to try and make a start on the permissions for /etc/apache2 and the likes of mods-enabled, sites-enabled etc. I hope you guyz & galz don't mind me asking - It'll make a gr8, easy tutorial, once it's done !!  :)

---

### Post by Bachstelze on 2009-09-07
> **bodhi.zazen said:**
> First, that is a link, and so you set permissions on the target.

Second apache runs as www-data, so I 

chown root.www-data
chmod 660

on the mod_sec logs in /var/log/apache

Surely you mean [font=monospace]chown root**:**www-data[/font]. ;)

---

### Post by phillw on 2009-09-07
> **HymnToLife said:**
> Surely you mean [FONT=monospace]chown root**:**www-data[/FONT]. ;)


Possibly why I am asking for it in an 'idiot' (me) proof method  :)

:lolflag:

---

### Post by __p1n__ on 2009-09-07
When you've finished configuring your server and after you've backed up the configuration/installation and before you install any data then perhaps you can ask an aquaintance to do a pen test on your machine.

A rudimentary (I stress rudimentary) DIY approach could include a comprehensive portscan followed up by service-specific MSF attack attempts against any non-closed ports.  Complement this with a w3af scan of your website.  This really is a script-kiddie approach but it might highlight any soft points in your installation and application.

---

### Post by bodhi.zazen on 2009-09-08
> **HymnToLife said:**
> Surely you mean [FONT=monospace]chown root**:**www-data[/FONT]. ;)

no, the dot ( . ) works

---

### Post by phillw on 2009-09-08
In the absence of people screaming "DON'T DO IT !!!" - I have transferred permissions and ownerships as detailed above.

Going to have a read round and see what is recommended for /etc/apache2 and sub directories - I'll be back - lol

While I have a dig round for them - A question to leave you good people with.

I installed OSSEC HIDS and have 'aquired' 3 extra users on my 'switch users' screen - these being ossec, ossecm and ossecr - Is this normal ?

Once again, thanks for bearing with me.

Phill.

---

### Post by HermanAB on 2009-09-08
Note that passwords need not be hard to remember and incomprehensible.  You can trade off complexity for length.  Something like "MaryHad3LittleFarms" or "UncleDonaldHad5Lambs" are actually good passwords.  They do not have to be total gobbledygook, just long enough not to feature in any dictionary.

---

### Post by phillw on 2009-09-08
> **HermanAB said:**
> Note that passwords need not be hard to remember and incomprehensible.  You can trade off complexity for length.  Something like "MaryHad3LittleFarms" or "UncleDonaldHad5Lambs" are actually good passwords.  They do not have to be total gobbledygook, just long enough not to feature in any dictionary.

I was saving the bawdy tale of the good ship venus for my pass-phrase for SSH - lol

As a mini bump... any one got an idea on ossec & my new users ?

Thanks,

Phill.:)

---

### Post by bodhi.zazen on 2009-09-08
Those users are "normal" system users for ossec

---

### Post by phillw on 2009-09-09
> **bodhi.zazen said:**
> Those users are "normal" system users for ossec

Thanks :)

---

