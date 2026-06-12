---
title: "help using apache and sudo to start/stop sshd"
date: 2009-01-26
forum: Security
---

### Post by e1mer on 2009-01-26
I keep seeing dictionary attacks on my server.

I have created a php web page that asks me for
a valid user and a password to start and stop 
the ssh daemon.

The user must be a valid user, and the password is
shared (so any of my users can start/stop it remotely)

The key is apache should not be able to run anything
else as root except /etc/init.d/sshd.

I set up a group called rcusers (not really that)
and added the user apache (not really that either)
to the group.

In visudo I put a line:
%rcusers root= NOPASSWD: /etc/init.d/sshd

I thought this would allow a script run as apache
to start and stop the ssh server with no password,
but the script, run as su - apache still asks for
the apache password. (The password is disabled in 
the shadow file, which is correct.)

What am I missing?

PS:
Ultimately I will use cron to watch until nobody is 
logged in by ssh and stop the server then.

---

### Post by bodhi.zazen on 2009-01-26
Wow, that seem way more complicated then it needs to be.

First , since you already have a ssh server running, just re-start the server over ssh.

You can do this very easily with keys. Make a key for root and enter the command /etc/init.d/sshd restart as the command to run.

See man ssh for the configuration , I think you want 

root no-password

you can either google search for how to configure the keys, or I wrote a blog page on the topic

My blog page uses ssh+svn, but it should give you the general idea.

[http://blog.bodhizazen.net/?p=6](http://blog.bodhizazen.net/?p=6)

You can also just restart the ssh server from cron.

If you want to go your route, try

%rcusers root= NOPASSWD: /path/to/script

then run sudo /path/to/script

---

### Post by HermanAB on 2009-01-26
You can stop any and all DOS and brute force attacks with a one line iptables rule.  Just put the following in /etc/rc.d/rc.local (so it will run after a reboot) and execute it once from the command line:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit \
--limit 30/minute --limit -burst 5 -j ACCEPT

That rule will provide sufficient protection, but you could also change the SSH port to something non-standard in /etc/ssh/sshd_config.  Edit that file, change the port to say 2222 and restart sshd.  Al those other complicated stuff that you are doing is not necessary.

Cheers,

Herman

---

### Post by e1mer on 2009-01-27
I can and do use iptables, but as the
number of blocked addresses grows, it 
slows stuff down.  

Further, a distributed attack will not be blocked
this way.

I would rather not have the service running 
until I wish to use it.

I would like to use this technique on other 
services too.

---

### Post by HermanAB on 2009-01-27
Hmm, I hear you, but you should maybe also be pragmatic about it, since there are no distributed SSH attacks in the wild and all ongoing attacks are against the default port 22.  

So in practice, you can actually avoid the whole problem very easily just by selecting a non-standard port and the rate limiting filter will protect all services against abuse including FTP, HTTP, SMTP and more, not just SSH.

Your proposed solution is nice, but overkill for the present threats.

Cheers,

Herman

---

### Post by The Tronyx on 2009-01-27
One problem with this is that the user which Apache runs as most likely won't be able to execute a command requiring privilege escalation such as /etc/init.d/apache restart.  In theory you could use the exec function in a PHP script to do this but in practice the issue of privileges makes this somewhat irritating.  You could add the www-data user (which I believe Apache runs as on Ubuntu) to sudoers however this would more or less be a terrible idea for someone worried about security and then you need to worry about getting the script to authenticate your password.  You could look into mod_bash but again, that isn't really plausible/maintained/used and PHP's exec would work just as well.  If you have a generic idea of the location the attacks are coming from you can find most IP blocks available in a given country and then just proceed to add the blocks/ranges to hosts.deny.

Keep in mind that brute force attacks are only initiated after a valid listening port is found.  With this in mind, if the port isn't there, there is nothing to brute force, right?  If you want an intricate solution I would take a look at [this]("http://ubuntuforums.org/showthread.php?t=812573").

I am not sure if Webmin provides this functionality, but if you would like, try installing it on your server.  There is a good chance that it will allow you to stop/(re)start the SSH service thus making it available only when you want to be.  Please be advised that I have very little experience with Webmin so this might not actually work but iirc, it does provide a terminal somewhere in the interface.

Best of luck!

---

### Post by bodhi.zazen on 2009-01-27
To be honest, "all" that is needed for ssh is :

1. Use keys only (to log in).

2. Change the port from 22 to another.

3. I use denyhosts , fail2ban is also nice. 

4. To be honest a few short lines in iptables also takes care of it.

I published a "primer" on iptables here :

[http://bodhizazen.net/beginners/Firewall/](http://bodhizazen.net/beginners/Firewall/)

Please keep in mind that that page is still in "development", ie. I am still needing to work on both content and presentation so I provide it to you "as is" a work in progress.

Any feedback welcome (PM me on the forums if you wish).

---

### Post by e1mer on 2009-01-27
Thank you all for your answers.
My goal here is to implement a generic extensible
and powerful security mechanism.  While this will
exceed any current threats, I don't doubt that
the black-hats are constantly pushing the frontier.
(Who would have thought that DES was not enough
encryption?)

I am already using iptables to block most of the
Asia Pacific region.  The down side is that as the
filter list grows, the packets are (perhaps trivially)
slowed as you search the rules.

The reason I want this is that there are other
services I want to be able to start/stop with Apache.
(Including webmin.)

As to changing the sshd port, IMHO that is just
security by obscurity.  The common wisdom is that
is just not a solution, no matter how pragmatic.

I believe that a two layer security mechanism is
a better way to discourage attacks.

That's why I want to have users authenticate once
to enable the server, and a second time to log in.

The 'port knocking' technique may be
a good way to go, the web server can even be
used to do the knocking.  The authentication
could be done by a daemon running with root 
privileges.

BTW, bodhi.zazen, is there a reason that some of the
links in your firewall page are links and others aren't?

---

### Post by bodhi.zazen on 2009-01-27
> **e1mer said:**
> As to changing the sshd port, IMHO that is just
security by obscurity.  The common wisdom is that
is just not a solution, no matter how pragmatic.

I agree with that , but I suggest you try it. Most hits on port 22 seem to be "script kiddies" and changing the port SIGNIFICANTLY reduces the number of cracking attempts. If you do not believe me, try it and watch your logs.

> BTW, bodhi.zazen, is there a reason that some of the
links in your firewall page are links and others aren't?Well, as I tried to convey, the site is still "under construction".

EDIT: Thanks for reporting that, I updated the links I found on review. I appreciate the time you took to report that back to me.

---

