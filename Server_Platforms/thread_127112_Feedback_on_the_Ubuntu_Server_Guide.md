---
title: "Feedback on the Ubuntu Server Guide"
date: 2006-02-08
forum: Server Platforms
---

### Post by mattheweast on 2006-02-08
Hi all,

Throughout this release cycle, the Ubuntu Documentation Team has been working on the Server Guide for release with Ubuntu 6.04. It is coming along nicely, but we need lots of community help! We'd be very happy if people who follow this forum could have a look at the guide and provide some feedback: we're especially interested in what could be done better, and what you feel is missing. If questions come up frequently here, and the answer is not in the guide, tell us!!

The guide is here: [http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

You can just reply to this thread, or to get more fully involved, visit [http://doc.ubuntu.com](http://doc.ubuntu.com). New contributors are always very welcome.

Thanks for your time!

Matt

---

### Post by az on 2006-02-08
[QUOTE=mattheweast]
The guide is here: [http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)
Matt[/QUOTE]


404!  It don't work!

Impossible d'afficher la page 
La page que vous recherchez est actuellement indisponible. Le site Web rencontre peut-être des difficultés techniques ou il vous faut peut-être modifier les paramètres de votre navigateur.

---

### Post by Jedeye on 2006-02-08
> Firefox can't establish a connection to the server at doc.ubuntu.com

grrr

---

### Post by mattheweast on 2006-02-08
Yes, the server is down :(

Sorry for any inconvenience, it should be up again soon!

Matt

---

### Post by mattheweast on 2006-02-09
It is working now. We'd love your feedback!

---

### Post by nocturn on 2006-02-09
The guide suggests some particular programs for some tasks, like courier for IMAP.  Is there any reason for this choice?

Depending on your needs, you may be better of with Cyrus (or another).  I choose Cyrus because it is stable and has support for different auth mechanisms, including GSSAPI.

Also, a chapter on LDAP/Kerberos intergration may be very nice.

---

### Post by mattheweast on 2006-02-09
[QUOTE=nocturn]The guide suggests some particular programs for some tasks, like courier for IMAP.  Is there any reason for this choice?
[/quote]

We have not been able to cover all programs. In some cases (for example IMAP), I think it is likely that the choice was made according to what software is in Ubuntu's main component. Main programs are preferred to Universe programs.

That said, this is not set in stone, and if you have good reasons to prefer one over another, please feel free to raise them on this thread.

Thanks for your other suggestions. If anyone would like to contribute some text for the guide, they can paste it here, or even better, submit a patch to our source code. Instructions on how to contribute are at [https://wiki.ubuntu.com/DocumentationTeam/GettingStarted](https://wiki.ubuntu.com/DocumentationTeam/GettingStarted)

Matt

---

### Post by nocturn on 2006-02-09
[QUOTE=mattheweast]We have not been able to cover all programs. In some cases (for example IMAP), I think it is likely that the choice was made according to what software is in Ubuntu's main component. Main programs are preferred to Universe programs.

That said, this is not set in stone, and if you have good reasons to prefer one over another, please feel free to raise them on this thread.
[/quote]

cyrus21 in not in universe.  I prefer it because it can do everything courier can but supports many forms of authentication through SASL.

You need SASL anyway for some other servers (Postfix can also use it).

Besides that, it is one of the few that support Kerberos (GSSAPI), which is needed to achieve single-sign-on.

I would also recommend a section on using mailscanner (which is in universe unfortunately).  It is much easier that amavis and can keep a server clean.

---

### Post by seifen on 2006-02-10
Hello:

Is it possible to include some documentation on Tomcat and Java Servlets?  I am very interested in serving apps on the upcoming Ubuntu 6.04 using JSPs and such.

And does anyone know if it is possible to serve PHP and Tomcat at the same time?  :D 

Thanks so much.

---

### Post by jinacio on 2006-02-18
Here's some nice software choices:

 [PHP]("http://www.php.net/") 4/5 along with apache

 [ProFTPD]("http://www.proftpd.org/") as FTP server 

 [Dovecot]("http://www.dovecot.org/") for pop3/imap with or without ssl

[Shorewall]("http://www.shorewall.net/") for a great firewall.

 [webmin]("http://www.webmin.com/") (next version, 1.270) will support ubuntu "out-of-the-box". it's great to manage everything very easily.

other possible tools could include:
quotas
spamassassin
clamav


i'm no expert in any of these tools but i will be glad to help out.

Cheers
Joao Inacio

---

### Post by rich on 2006-02-19
What is a "dual license strategy" ? What does the word "includes" mean in this sentence ?

This document is made available under a dual license strategy that includes the GNU Free Documentation License (GFDL) and the Creative Commons ShareAlike 2.0 License (CC-BY-SA).


I hope to find a section that I can contribute to without drawing too much attention to the superficiality of my knowledge. 

Rich

---

### Post by mattheweast on 2006-02-19
[QUOTE=rich]What is a "dual license strategy" ? What does the word "includes" mean in this sentence ?

This document is made available under a dual license strategy that includes the GNU Free Documentation License (GFDL) and the Creative Commons ShareAlike 2.0 License (CC-BY-SA).
[/quote]

I find it hard to explain that without repeating what it says, but it means that the document is available to modify/copy/redistribute if you comply with the terms of two licenses, which are those named.

HTH

Matt

---

### Post by bhuvan on 2006-02-20
vsftpd is already part of server guide. One more ftp server is unnecessary. All other tools are valid contenders. We will consider to include these tools and it is depend on time factor. First priority is to review existing sections.

---

### Post by jamesr on 2006-02-28
It has been useful to me but I think a useful addition would be to make a PDF edition available. I personally prefer to read from paper than a computer if I am reading a full document, Also when travelling a paper copy is easier to handle.

---

### Post by lazyleg on 2006-03-02
I think the FTP section was abit short. It pretty much had more information on what the FTP protocol is then on how you can set up a FTP program AND configurate it. I followed the guide and everything worked fine up until i was to configure vsftpd. There was simply no documentation on that, it only said "More information about each configuration parameter is available in the configuration file", but in the configuration file there was only the settings that where enabled.

It should be said that im a old windows user, and just recently started using Ubuntu. It seems Ubuntu users need to spend way more time in a manual then just playing around with settings.

---

### Post by jinacio on 2006-03-03
Though i agree that preferably, software from main should be used, i do also believe that a few some cases, where there is more than one good software package for the same service but with distinct purposes/uses, it would be usefull if both were included alongside a brief description of that specific software uses.

from the top of my head, i think the best example would be pop3. i am sure the need exists both for simple and fast pop3 servers and full-featured ones.

of course, it all comes down to time/space available to include software in the guide...

---

### Post by gmclachl on 2006-03-07
I think it would be nice to include a section on mod_authz_svn this is automatically build and installed with mod_dav_svn. 

 It allows for finer grained access to the subversion repositories. It's also nice and straighforward to set up.  

 George

---

### Post by spelingchampeon on 2006-03-12
I installed the server, and after logging in wound up at this point:

[COLOR="DarkRed"]linuxserver@name:~$[/COLOR]

Being a noob, I had no idea where to go from there, and thought maybe I installed something incorrectly. I reinstalled the server software again, keeping track of my possibilities and answers. Nowhere did I see any reference to start at the command line like that. After about 3 hours of reading and rereading the doc and posts on the site, I stumbled onto a post where someone said to try the line below:

[COLOR="Green"]sudo apt-get install ubuntu-desktop[/COLOR] and after the installation finished..just typing in [COLOR="Green"]startx[/COLOR] at the command line.. I was golden. 

That fixed my problem, but I still have no clue where those instructions are (I did have a few black and tans beforehand...hmmm). I sometimes wonder if the design of Linux is built to help make users learn the command line shortcuts, as opposed to point and click GUI freedom. I'm all for both :mrgreen:

I did want to say GREAT JOB to everyone at Ubuntu.. I tried Mepis out for 2 weeks, but couldnt even get XMMS installed. I have since let other noobs like myself know about Ubuntu. Keep up the good work.

---

### Post by haircut on 2006-03-13
[QUOTE=spelingchampeon]I installed the server, and after logging in wound up at this point:

[COLOR="DarkRed"]linuxserver@name:~$[/COLOR]
[/QUOTE]

This would be correct. This "Server" install is a minimal install, no GUI (Gnome) is installed.

If you required a "Standard" install then when prompted by the Install CD, you should have just pressed enter and not typed in "server".

If you required a Server install with a GUI, then you have done the right thing by installing the GUI after installing the Server.

Whether this needs to be added to the Server guide is another thing :) 

Maybe a comment stating that it’s a GUI’less interface might help?

---

### Post by Velvet Elvis on 2006-03-17
I'm in the process of configuring my first LAMP setup.  I'm having to use debian stable becuase I couldn't find a reliable VPS host with ubuntu clients on it anywhere.

The places I've been having the most trouble have been mod_rewrite, and .htaccess files in nested directories with conflicting AlowOveride directives.  I don't believe these are mentioned.

An explanation of debian's /cgi-bin/ setup should be in there somewhere. 

I'm not real sure who this is supposed to be for. 

If the target audience of this document is new users who have never set up a server before it needs to go on to explain the kind of stuff they are likely wanting to do with their servers such as blogs (wordpress), wikis (moinmoin or dokuwiki), CMS (drupal?) and stuff like that.

If the target audience is existing server admins, the document doesn't contian much that they won't already know.  

For exammple if the target audience is new server admins, go into some more deatail about what DNS is and how it works.  If the target audence is enterprise server jockies, talk specificly about Ubuntu's bind9 (or whatever it has) configuration. 

The section on databases needs much more.  A mention of phpmyadmin would likely spare lots of agonly and late-night irc questions..

It needs more detials and theory both.  If you're talking about servers it's OK for the documentation to read like the UNIX manual it is.

IMHO, the best thing to to do further the adoption of Ubuntu in the enterprise server market is focus on how it differs from Debian and compeating products so there are no suprises when people try it.

---

### Post by mattheweast on 2006-03-17
[QUOTE=Velvet Elvis]I'm in the process of configuring my first LAMP setup.  I'm having to use debian stable becuase I couldn't find a reliable VPS host with ubuntu clients on it anywhere.[/quote]

[http://www.linode.com](http://www.linode.com)

> The section on databases needs much more.  A mention of myphpadmin would be a godsend to many I'm sure.

It needs more detials and theory both.  If you're talking about servers it's OK for the documentation to read like the UNIX manual it is.

I tend to agree. I think the ftp section needs more detail as well. However, we are limited on time and contributors: if anyone would like to contribute some more material (in the next week or so), I'm sure we can add it to the guide.

Thanks,

Matt

---

### Post by pchr on 2006-03-19
Apologies if newb me missed something obvious but...

I'm playing with server install on a spare pc I've got and I thought as it's a server I'd better give it a permanent IP address.

I ran ifconfig eth0 [IP Address] and that worked fine, at reboot however the IP address went back to DHCP.

In the end I (can't remember where I stumbled on this) edited /etc/network/interfaces with the details I wanted - I checked the format by looking on my Ubuntu box.

Is this considered the best way of doing this or is there a better way.

Anywho, I think it would be worth mentioning this in the Server Guide.

Thanks.

---

### Post by bhuvan on 2006-03-20
[QUOTE=mattheweast][http://www.linode.com](http://www.linode.com)



I tend to agree. I think the ftp section needs more detail as well. However, we are [/QUOTE]

Valid feedback. I've elaborated the FTP section further. Hope it helps! Thank you.

---

### Post by pmilani on 2006-03-24
I think the work on Server Guide is a very good base.
I think it is intended for a reader that has basic administration skills: this is good.
Anyway, I would expect to find also the more complex concepts and techniques.

A topic I 'd like to see, is **cluster setup**, with the tools included in the Main dist. Are these packages corresponding to the RedHat Cluster Suite?
Personally I would be interested in setup for distributed storage via GFS.

PS: if anyone has a clue, how to install CLVM on Ubuntu Server 'Dapper'?

---

### Post by s7eam on 2006-03-31
Great Guide!

For the first time I succeed to understand and manage to setup apache2 with SSL support. I like especially how documentation is well clarifying each of the steps.

---

### Post by arkopII on 2006-03-31
Hello!

This guide is a good job, I have an ubuntu server and I've always missed a way to monitor network traffic, state of daemons, disk, memory, etc.

I have nothing installed yet but, how about including a section in this guide of how to install nagios or something like that?

Thank you very much.

---

### Post by mtron on 2006-04-03
hi i know you guys are from the doc team but maybe you can get this feauture request to the right persons. it's very important for me that the server install (or at least the install cd) comes with lynx. 

first it's always good to test some stuff, second, and more important is that my isp uses a "login script" they redirect me to their login page where i have to provide a user id & password before they actually open my connection. so it was never possible for me to make a server install, cause i needed a webbrowser to use the apt-get system.

the dam thing is that lynx doesn't fit on a floppy, (it has 1.8 megs) so i had to burn a cd with it. what a waste...

anyway long story short. please, please please with sugar on top include lynx on the server install cd.

---

### Post by mattheweast on 2006-04-03
[QUOTE=mtron]anyway long story short. please, please please with sugar on top include lynx on the server install cd.[/QUOTE]

You need to mail the developers about this. See the mailing list at [https://lists.ubuntu.com/mailman/listinfo/ubuntu-server](https://lists.ubuntu.com/mailman/listinfo/ubuntu-server)

Matt

---

### Post by mtron on 2006-04-03
thanks dude! 

will do that.

---

### Post by Absolute on 2006-04-03
[QUOTE=mtron]anyway long story short. please, please please with sugar on top include lynx on the server install cd.[/QUOTE]
I was upset to discover that RHEN doesn't come with lynx anymore either; the newer users might be used to links, but I still instinctively type in 'lynx' every time I try to load the text browser.

I'd also vote for lynx to be included in the images by default; I still install it on every server I manage.

---

### Post by mtron on 2006-04-04
i tired to subscribe to the list, but i didn't get any response from the moderator... could sb. already subscribed please post this request? thanks! 

@ matthew: sorry for the off topic posts, i'll stop now ;)

---

### Post by mtron on 2006-04-12
Concerning lynx:

> mtron wrote:
>> anyway long story short. please, please please with sugar on top
>> include lynx on the server install cd.
>
> Will be done.
>

Done, it is available from today's daily CD.

Fabio

---

### Post by brentoboy on 2006-04-21
is there a way to get this guide in one page so I can just print it and look it over without having to sit at my desk?  This is he same issue I had with the debian docs, you have to read them one web page at a time, and some of the pages are all but empty.

the gentoo docs have options to view them all on one page, or one page per chapter.  That would be really nice here.  People like to print docs so they can see them while they sit at the command line on thier server.

just a thought.

---

### Post by mattheweast on 2006-04-21
[QUOTE=brentoboy]
the gentoo docs have options to view them all on one page, or one page per chapter.  That would be really nice here.  People like to print docs so they can see them while they sit at the command line on thier server.[/QUOTE]

We will be shipping multiple pages, single pages, and PDF versions of the guides.

Thanks everyone for their feedback: we've now frozen our strings for Dapper, and have stopped amending the guide. We hope you will enjoy the guide and find it useful.

Matt

---

### Post by dk_pa on 2006-05-01
I liked what I saw so far.  What about setting up and using the LVM (very useful for a server), rsync for backups, setting up offsite backups, VPN, and other tools like that.  

What's documented is great but tools like I mentioned in some ways, I think, will be more of a good impact on the guide because of how much documentation already exsists on the others. Definitely would dig a cluster setup (like mentioned earlier in this thread).  Just some thoughts, great so far! :)

---

### Post by ixus_123 on 2006-05-03
I wonder if you could perhaps **bold** the text that a user has to change in some commands so that it is obvious what to change.

Sometimes - especially if doing something for teh first time it can be confusing as to what has to be changed.

for example:
```
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');
```

could be changed to something like
```
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('**yourpassword**');
```

The first time I had to use this command I was a little unsure on wheather to  the bit in brackets was to be included at all or just replace the block capitals - easy once you know but obvious to newbies like myself.

---

### Post by munch on 2006-06-07
It would be great if we could get a little more information on user accounts/groups...  

more specifically - how to migrate user accounts from one system to another... I'd hope we don't need to do this often... I'm faced with a need to do it in near future...

---

### Post by Gtaylor on 2006-06-08
Edit: Never mind, ignore this :)

---

### Post by boyou on 2006-06-08
Hi I notice in chapter 2 when you boot up from a CD it will give you two options "Install to hard disk"  or "Install a LAMP server" i  never got the options im installing on a power G5.

---

