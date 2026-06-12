---
title: "my LAMP has just been hacked please help!"
date: 2007-05-04
forum: Server Platforms
---

### Post by envis on 2007-05-04
i just been victim of an hacker attack on my website, which is hosted on a proud Ubuntu 6.10 server version

despite of their efforts, the hackers who had already taken down many of my competitors, have not managed to really get into the system and "delete the website folder" as they claimed they were trying to.. but they did manage to crash my apache somehow!

its no big deal but it is annoying cos i was sleeping and im the only admin of my site, so now i never know when they gonna go and crash my apache again.. i cant watch it all the time to make sure its always up....

when i woke up, i noticed my site was unreachable!... so i tried to ssh into my server and that worked fine. tried to restart apache, it failed! it said it was unable to connect to socket 80 or something like that... forgive me if i dont remember the error message better, im a newbie webmaster and i was quite in a hurry to restart the machine at this moment.

after the machine had restarted, all was fine again, my website was up and running again... hopefully they had left some threats on my pages and that gave me their ip and the time, it even let me see that they probably were one of my competitors cos, just before the two threats they posted, they left another anonymous post recommending to visit two websites in perticular (two of my competitors)... anyways, i reported them to their ISP for abuse... im canadian, im not sure if im supposed to call the police....

but what i would like to know is, does anyone have any idea what kind of attack this might have been? how to prevent that? it looks like they somehow ****** up my port 80..

where in my proud Ubuntu can i find logs to see what happened?

thanks!

---

### Post by envis on 2007-05-04
i want to mention that im not behind any firewall, but if i had been, the port 80 would have been jsut as open anyways, right?

---

### Post by gombadi on 2007-05-05
> 
i just been victim of an hacker attack on my website, which is hosted on a proud Ubuntu 6.10 server version

.. but they did manage to crash my apache somehow!

but what i would like to know is, does anyone have any idea what kind of attack this might have been? how to prevent that? it looks like they somehow ****** up my port 80.

where in my proud Ubuntu can i find logs to see what happened



I would like to apologize now if you take offense from my reply. I am not meaning to offend but...


Where is your evidence?

You are not providing much information to go on. All I can work out is -
* You are running Ubuntu 6.10
* You are running apache web server
* You woke up one day and found you could not access your web site
* You decided that you had been hacked by some remote person who crashed apache.

What you do not say is what brought you to this conclusion. Also you did not say what web application you are running or is it just static pages?

You tell us that you are a newbie webmaster but you also ask the location of the log files to see what happened. Well it has been eight hours since your post - did you google and find the answer? Just in case you have not have a look in /var/log and sub directories for all system log files. Also you may want to have a look in the apache config files as they have the location of the log files. They also have a lot of other information that a webmaster should be aware of.

One of the first tasks of a webmaster is to know the location of the config and log files. Before the site goes live.

You tell us very little about the problem but ask us what kind of attack(if any) it was. 
Instead of rushing to restart things you need to see what actually happened.

The error about unable to connect to port 80 indicates that apache, or something, was already running so it had not been crashed by some remote person.

Please update the thread with new information so we can help you find out what happened.

And again sorry if I have offended but you have to start helping yourself by giving us something to go on.

---

### Post by tr333 on 2007-05-05
log files are kept in /var/log/
if you're running any sort of server connected to the internet with remote ssh login, you should install fail2ban which will block access for a limited time after a set number of failed logins.
if your server is connected directly to the internet (not behind a router firewall or similar), then you should configure iptables with a suitable firewall program (search the forums or google for firewall programs on ubuntu).

---

### Post by useLinux, on 2007-05-05
> **tr333 said:**
> log files are kept in /var/log/
if your server is connected directly to the internet (not behind a router firewall or similar), then you should* configure iptables with a suitable firewall program * (search the forums or google for firewall programs on ubuntu).

If you dont know how to set up up tables (like me) [http://webmin.com]("http://webmin.com") is good as you can log into it via localhost and it lets you create ip tables with a GUI easily. It also can configure a linux firewall (shore) and has many features to help with webservers, such as installing ftp servers, mail servers etc. Generally a good all purpose program.  The installer is your looking for is .deb since ubuntu is based on debian. :) Hope that helps.

---

### Post by MJN on 2007-05-06
As Gombadi says there is nowhere enough info yet to ascertain what the problem is here so it's futile recommending any security measures particularly things like fail2ban and firewall rules as there's no foundation that either of these would've helped in this situation. 

All good general advice of course, but not helpful in these circumstances - there's been no mention of attempted/failed logins so fail2ban will be of no help, and there's been no suggestion as to what vulnerability has been exploited so a firewall will not help - what open ports would you suggest blocking?

Envis, provide more information otherwise we're shooting in the dark and will not be able to help you.

Mathew

---

### Post by envis on 2007-05-12
yes.. it happened a couple of times again, and thats because im playing with the apache2.conf

i am mostly playing with the IfModule prefork.c

it currently looks like this at the moment

<IfModule prefork.c>
StartServers          50
MinSpareServers       25
MaxSpareServers      250
ServerLimit         1024
MaxClients          1024
MaxRequestsPerChild  100
</IfModule>
 
though, before i go to bed, i set it like this: (same but 1600 servers instead of 1024)

<IfModule prefork.c>
StartServers          50
MinSpareServers       25
MaxSpareServers      250
ServerLimit         1600
MaxClients          1600
MaxRequestsPerChild  100
</IfModule>

and it was down when i woke up... same thing again, apache cannot restart, seems to say unable to use port 80 or something, ssh is super slow (normally ssh is always fast). so i have to reboot the computer and after everything is fine again...

the problem is that i dont know so much what those numbers represent, but im fiddling with it and inspiring myself of examples i see on the net left and right, trying to keep the same proportions.

the server is an AMD 64, 3000 Mghz, 1 gig of RAM, SATA hard drive, Ubuntu server 6.10, Apache2, PHP5, MySQL5, ftp, ssh, postfix installed...

its not a bad machine and has nothing else to do... its connected at some "server collocation" service on a very good connection....

i am not asking for help, even though any help or advice is always welcome, but basically, im 99.9% sure now, that i have not been hacked, not once.. yet : )  i think some ppl may have tried, but they were probably expecting to run into some IIS box and got confused :P or maybe they got nothing good out of my htaccess file (which i dont use, its all PHP and rotating folder for protected content (pictures, audi and video) all PHP, what can you do... you need to login to the box, DDOS it or forget it..)

my pages that have power or getting name of rotating folder needs you to click a button (which is a post form).. im relatively well protected.. anyways, theres no so much to hotlink from my site at the moment, so my problem is more: trying to stay UP and RUNNING!

---

### Post by envis on 2007-05-12
i downloaded and had a look at some of the files in log... i saw many attempts at loggin in from various locations areound the globe.. always failed though... it made me decide to start changing my passwords regularily...

some knowledgable collegue at work told me that someone would need about 3 days to find the password of my box with i dont remember which program if your password at least is not a word of the dictionary...

---

### Post by MJN on 2007-05-12
(when I read *(pictures, audio and video)* I read it as *(pictures, adult video*)! :eek:

I really wouldn't play around with those numbers if you're not sure what they mean/do - if it ain't broke don't fix it! Set them all back to default and see if your problem goes away...

Which logs have you found the authentication attempts in? Apache's? As someone suggested above for SSH you could always use fail2ban to curb these attempts as it'll happily cover Apache authentication too.

Incidentally, if your colleagues' sums are right then you *really* need to strengthen your passwords - 3 days is absolutely nothing. Your aim should be making the average brute force period at least years if not more - this is quite achievable with an 8 character non-dictionary full-character-map (not just alphanumerics) password without sacrificing any convenience of using it. There is a nice Wiki article on password strengths that you might be interested in which probably covers more than you need to know - [http://en.wikipedia.org/wiki/Password_strength](http://en.wikipedia.org/wiki/Password_strength) Be aware though (before you panic too much) that much of the article is discussing password cracking by running through password lists, computing the hash and comparing it with the system-stored hash - this is *very* fast. However, in your case your 'attackers' don't have the luxury of your password hash list and so are resigned to simply attempting a login every, say, second or so and hence are drastically slowed down (but 3 days is *not* slow!).

Mathew

---

### Post by MrHorus on 2007-05-12
[QUOTE=envis;2640105]i downloaded and had a look at some of the files in log... i saw many attempts at loggin in from various locations areound the globe.. always failed though... it made me decide to start changing my passwords regularily...
[QUOTE]

That's because everyone knows SSH runs on port 22.

What you might want to do is eding sshd_config to run SSH on another port, say 2222 - you will notice a MASSIVE drop off in the number of people trying to connect.

---

### Post by envis on 2007-05-12
right now i cant seem to bring my site back up... i keep getting


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Sat May 12 14:58:38 2007 from lalalla
envis@mybox:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                   [Sat May 12 15:37:57 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
(98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
envis@mybox:~$ sudo shutdown -r now

usually that always came back fine after restart but not now... oh wait.. i just lowered all the values but put clients at 9999 like a dumbass because you know... clients! i want a lot :P ... ok i set that i 256...

its saturday afternoon.. and the traffic was coming in very well... either that or i was under DDOS attack.. probably just traffic i assume..

Max  In:  	2155.4 kb/s (21.6%)  	 	Average  In:  	786.7 kb/s (7.9%)  	 	Current  In:  	11.7 kb/s (0.1%)
Max  Out: 	337.3 kb/s (3.4%) 		Average  Out: 	140.7 kb/s (1.4%) 		Current  Out: 	44.3 kb/s (0.4%)

those are my daily connection stats and right now my connection was at its peak of the day so far 2155.4 kb/s... thats when it all started going wrong...

i still cant seem to get my site back up after lowering the clients so far... its stupid i never had any problems for months before...

oh wow.. i actually just loaded a page now.. but its terrribly slow!
ok.. its up now... even reasonable speed.. slow, but usable.. maybe its just cos most ppl finally left after all that downtime :P

and now its lightning fast all of a sudden?!.. still fast... maybe i have a good balance in my values now... 

<IfModule prefork.c>
StartServers          16
MinSpareServers        4
MaxSpareServers      256
ServerLimit         1024
MaxClients          1024
MaxRequestsPerChild   64
</IfModule>

<IfModule worker.c>
StartServers          16
MaxClients           256
MinSpareThreads        4
MaxSpareThreads      256
ThreadsPerChild      256
MaxRequestsPerChild   64
</IfModule>

<IfModule perchild.c>
NumServers          1024
StartThreads          16
MinSpareThreads        4
MaxSpareThreads      256
MaxThreadsPerChild   512
MaxRequestsPerChild  256
AcceptMutex fcntl
</IfModule>


does that look good? lol... its hard to say for me...

---

### Post by envis on 2007-05-12
it keeps running super fast now.. maybe faster that i ever seen... i will cross my fingers :P

---

### Post by MJN on 2007-05-12
You are dabbling with performance configuration you don't understand - it's no wonder it's so unstable.

Mathew

---

### Post by Selmer79 on 2007-05-13
In my experience, Apache will run just fine with default configs 99.999999% of the time..
Unless people run a massively busy site, there is no need to tweak anything.

---

### Post by envis on 2007-05-13
it crashed again while i was sleeping... lowered some values again...

the problem is that, even though im quite a newbie, i DO run a massively busy site...

and i am making Lots of money from it to!!!!.. (more than my real job) as long as it stays up.... i stayed on the default apache config for many months at first.... but some day the website started "falling asleep" all the time.. meaning, you would click somewhere and it would wait... wait.. wait.... and then oh! the page starts changing and then the page loads... slowly.. so i first thoughed i just needed more bandwidth.. but i saw anything else i would connect over the same connection (example ssh into server or VNC into other comp at home on same connection) was happening super fast, i came to the conclusion that my bottle neck was not my bandwidth but it was my apache settings, so i went in apache2.conf and doubled all values in there and pop! my problem was fixed for another maybe month!.... then it started falling asleep again... boosted the values some more and it fixed it again for a while..

..and then one day, i boosted them too much, lost the balance in those unknown numbers... and now what happens is that everytime i receive a massive barrage of traffic (ex a saturday night).. apache crashes... so when it happens while i sleep it makes me go mad!!...

i just found that i have a file called apache2.conf.save next to my apache2.conf... and that apache2.conf.save seems to have the default values in it.... so i will go for a direct proportion of this config.. like maybe the default config x10 or something... that should be safe.... :P

---

### Post by MJN on 2007-05-13
Massively busy? Your 'max out' stat the other day was 337kb/s!

What's the URL? I'll see how responsive it is from this end if you like - I've got a 10mb/s download connection, what's your upload?

Mathew

---

### Post by envis on 2007-05-13
i was able to go back to a more cochere configuration by looking at:

/etc/apache2/apache2.conf.save
and
[http://www.debuntu.org/book/export/html/91](http://www.debuntu.org/book/export/html/91) (basic apache optimization)
and
[http://ubuntuforums.org/showthread.php?t=437650&highlight=example+of+apache2.conf](http://ubuntuforums.org/showthread.php?t=437650&highlight=example+of+apache2.conf)  (some thread on ubuntu forums)

oh this will give me back some stabilty

---

### Post by envis on 2007-05-13
well the max out is not so important.. its the max in that counts... the server doesnt really need to know so much about the outside wolrd.. its more the outside world that wants to view the contents of the server
i am also on a full duplex 10Mbps connection....

---

### Post by MJN on 2007-05-13
Of course it matters! Your output/upload is all the traffic to your clients! The more clients, the more they want to 'view', hence the more output you want to give! What else are you optimising your config for?

Let me test it from this end - that'll give you a good idea of how well it's performing off-base. (PM me if for whatever reason you don't want it public)

If you wish I can also run through how you can get some stats giving the current server performance. You really ought to be doing this anyway rather that just blindly tweaking numbers up and up.

Mathew

---

### Post by envis on 2007-05-13
i emailed you my domain name

---

### Post by envis on 2007-05-13
at the moment its low-traffic.. im in "entertainment" and most of my visitors are from USA (about 80%).. so right now... theyre still in church :P... i should get my peak of the week today though.. in the afternoon and evening

---

### Post by MJN on 2007-05-13
Got your e-mail (I thought your username rang a bell - forgot we'd crossed paths before!)

I've had a quick scout round but it doesn't look like the content is that 'heavy' i.e. no large files (unless I missed them, or perhaps given I don't have a login) hence I'm surprised you really need to tweak the options from default.

Try this...

Add the following to your <Virtualhost> config:

```
<Location /status>
SetHandler server-status
</Location>
```and, optionally given there can be a slight performance hit (but it's worth it given the extra output) add **Extendedstatus on** to /etc/apache2/apache2.conf.

Restart Apache and got to /status and you'll see a whole load of performance info which is essential if you're going to tweak performance options. Doing it 'blind' is futile - you need feedback on the results so you can identify the bottlenecks.

Of course, leave it in this state for some time to amass results as the most significant gains will be obtainable from tweaking the longer-term averages, and monitor it particularly during what you consider to be your peak periods.

Mathew

P.S. You sure you've got 10mbps upload? It's really not seeming it...

---

### Post by envis on 2007-05-13
no, you actually helped me more than once before! thanks a lot by the way!

---

### Post by envis on 2007-05-13
i still havent celebrated my first birthday as a linuxian.. but the server is so cool...

---

### Post by envis on 2007-05-13
why do you say my connection is not 10mbps? how do you see that? cos thats defenetly what i pay for...

---

### Post by MJN on 2007-05-13
The in-transfer download speed (it's not foolproof given transient network condition but it's a good start).

You with B2B2C? What package?

Edit: Ah, I just spotted you're colocated and hence will be on their backbone. Perhaps they've just got (temporary) local issues.

Nevertheless I really think you're best off going back to defaults - again if it ain't broke don't fix it! (and it sounds like it broke *because* you 'fixed' it!)

Mathew

---

### Post by Enverex on 2007-05-13
Just leave your "Homepage" on the forum blank if you don't want people to know one rather than entering garbage like "http://rather.keep.my.domain.hidden.with.all.the.security.matters.i.discuss.here/" in it.

And in all honestly, it seems like the only person that's broken your server is you, fiddling is bad when you don't know what those things do... so is paranoia.

---

### Post by envis on 2007-05-13
i agree with you  Enverex.. thats my conclusion too

i dont see though why it matters that i put garbage instead of my domain instead of leaving it blank..

i should change the title of this thread but i dont know how or if i can

my plan is basically, 10mbps half duplex, and you pay extra if the average speed of the month is over 1mbps

---

### Post by envis on 2007-05-13
there must be a way to do a speed test from the command prompt...

---

### Post by envis on 2007-05-13
...after almost a year of running that website.. having set everything myself, i, for the first time, have a look at /var/log/apache2/error.log

i see there that i have many problems!

---

### Post by envis on 2007-05-13
and i seem to have helped my problem a lot by setting KeepAlive at Off. KeepAlive allows ppl to get a long term continuous connection (default 15 seconds)...

---

### Post by DoneRightI.T. on 2007-06-11
heres a small bit of advice, use ascii in your password... there doesn't exist a program that will automatically create the acii chars. unless this has changed in the past month... this leaves people (bad side is  even you) wondering what the password is.... gl in the future... and that guy is correct... the forums are not a quick answer for anything or anyone.... do some of your own legwork and read the manuals, if all else fails, come to the forums....  and don't jump to conclusions, know one really cares whats on your site.... sorry.

---

