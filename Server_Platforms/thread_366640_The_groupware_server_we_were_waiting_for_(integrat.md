---
title: "The groupware server we were waiting for (integrated LDAP auth anyone?)"
date: 2007-02-21
forum: Server Platforms
---

### Post by Tasu on 2007-02-21
Hi all,
has anyone noted this new distro? [http://deeproot.in/deepofix](http://deeproot.in/deepofix)
It looks like the server we were waiting for! ^_^

The repo for their packages is:
deb [http://packages.deeproot.in/deepofix](http://packages.deeproot.in/deepofix) oldthink main deepofix

It's based on debian (so it would be easy to integrate the server customizations like the good web interface, in our beloved ubuntu), but I believe more in collaboration... I think it would be good for our community to work together with that project that IMHO looks like an Ubuntu for servers.
It has LDAP integrated and fully configurable from the web for user authentication, groups, addressbook, etc., smtp, pop, imap, well everything that SME Server has with the two bonuses of being based on debian and having LDAP integrated, I'm trying it at home.. it looks like it's really well done, with some really usefull admin options (in email part of the server) that can make happy an administrator...

However the LDAP feature itself is already a really great feature alone, imho...

Is there a way of letting ubuntu developers know about this distro? Who knows, some integration of the projects could be done since it's debian based as well and shares the common headline of being easy for the end user! ^_^

---

### Post by Macchi on 2007-02-21
Interesting Tasu, their deepOfix messaging server has some useful components and I am curious to have a look at it. 

I would also like to add some simplified web configuration interface to the ubuntu server, actually a "Linux Server for Human Beings". 

I also believe that it is very important to create a ground for cooperation among projects, instead of just branching yet another niche distro with a weaker brand and low probability of survival. A big challenge can be to find the right blend of functionality for a server. It has to attract a reasonable number of developers and users. My opinion is that the final administrators and users must to decide what is necessary, given a feasible range/combination of options. Thus I am looking for a very modular way to choose, install and configure the functions of a small enterprise or home server.

Lets keep in touch.

---

### Post by nocturn on 2007-02-21
Cool, but it does not have a groupware (calendering) component at all...

---

### Post by Tasu on 2007-02-21
> **nocturn said:**
> Cool, but it does not have a groupware (calendering) component at all...

Well, that's not quite true... from a groupware server I expect at least ldap addressbook, and it's in there and, as you stated, a shared calendar... well ics specifications state that the ics files can reside on an ftp server as well as on a webdav server... thunderbird, kontacts and evolution can access ics files on an ftp server without a problem... and from what I can see from the possible configurations, deepofix has ftpserver capabilities... and being a lazy person myself, I always used ftp for shared calendars in the networks I manage... (always used SME Server and created an ftp accessible ibay for this purpouse, nothing more than 2 clicks...) ^_^

---

### Post by nocturn on 2007-02-21
> **Tasu said:**
>  thunderbird, kontacts and evolution can access ics files on an ftp server without a problem... and from what I can see from the possible configurations, deepofix has ftpserver capabilities... and being a lazy person myself, I always used ftp for shared calendars in the networks I manage... (always used SME Server and created an ftp accessible ibay for this purpouse, nothing more than 2 clicks...) ^_^

For Evolution, this is only true for reading calendars (it expects them on a http connection actually).  But it cannot write to them.
Evolution only supports caldav.

In any case, FTP is not a calendaring server.  Something like egroupware would be a different matter, even though it also lacks caldav support.

---

### Post by Tasu on 2007-02-21
> **Macchi said:**
> Interesting Tasu, their deepOfix messaging server has some useful components and I am curious to have a look at it. 

I would also like to add some simplified web configuration interface to the ubuntu server, actually a "Linux Server for Human Beings". 

Lets keep in touch.

Well, I'm really interested in start working on that project... and amongst all the all-in-one server solutions I tried during these years (SME, eBox, Miru) this seems the most advanced and comprehensive, a really good ground to start from... I can say, I really thank SME Server for saving me a lot of time, but the lack of central LDAP Authentication and addressbook is something I always suffered... as stated on the op, I'm trying it and finding there almost everything I need in small to medium enterprises... this is the first project of this size I feel as complete for my needs.. this is why I think that it could be a good Ubuntu server (intended as product supported by our community) even if it's not ubuntu but debian based... I'll surely start to contribute as a ruby/python/php/perl programmer to that project... I just think they need a bit more advertising... ^_^

---

### Post by Tasu on 2007-02-21
> **nocturn said:**
> 
In any case, FTP is not a calendaring server.

Ok! Good point, however what I would express is that this project is the first I've found amongst competitors (SME Server, eBox platform), that lacks just this feature to be mature and ready enough to put aside MS Exchange (this is the target of such distros and egroupware alone is not a sb server, the three i mentioned are trying to be sb servers, but by now just deepofix manges to authenticate ms, apple and linux users alltogether, sme and ebox are geared more towards a windows only client network)... so this would be, imho, a good choice for the Ubuntu server people to build upon...

That said I thing I've mistaken the word when I wrote groupware server, I would have written small business server like ms exchange (and possibly more), sorry! ^_^

---

### Post by nocturn on 2007-02-21
> **Tasu said:**
> Ok! Good point, however what I would express is that this project is the first I've found amongst competitors (SME Server, eBox platform), that lacks just this feature to be mature and ready enough to put aside MS Exchange... so this would be, imho, a good choice for the Ubuntu server people to build upon...

I agree that it would make a very good starting point, but without any groupware functionality, we have nothing stable today to put against Exchange, which makes me sad.

I'm using Evolution on Exchange at work and it's wonderful, but it pains me that I cannot put an OSS solution forward to replace it.

This project is a good start and adding real groupware to it in addition to maybe Kerberos would make it revolutionary.

---

### Post by Tasu on 2007-02-21
> **nocturn said:**
> I'm using Evolution on Exchange at work and it's wonderful, but it pains me that I cannot put an OSS solution forward to replace it.

Hmmm! Probably on our jobs we target different markets, but on small to medium enterprises to be really happy with their authentication, mail and file server they just need shared addressbook and calendars on the server accessible from different people, I've tens of sme server installations with contribs to add shared addressbook, and ftp to serve ics files and I can say that my users are really happy to have switched from Exchange to Sme Server... they didn't found lacks of functionalities after the switch (and the addition of contribs to the sme servers), this deepofix has the LDAP thing that's just a really good plus for me as administrator... and the integration of the addressbook in a easy to use web interface...

This said in my reality I truly managed to "put an OSS solution forward to replace it" since now using SME Server, however sme and deepofix are targetting the small medium market, in this market the groupware server can be just that: central authentication, LDAP addressbook and group calendars on the server... btw it would be great if the developers would create a module for caldav integrated in the users management to allow sharing, but the small medium market can already be purged by microsoft products using the solutions I'm using for years.

---

### Post by Abhas Abhinav on 2007-02-22
> **Tasu said:**
> Well, I'm really interested in start working on that project... and amongst all the all-in-one server solutions I tried during these years (SME, eBox, Miru) this seems the most advanced and comprehensive, a really good ground to start from... I can say, I really thank SME Server for saving me a lot of time, but the lack of central LDAP Authentication and addressbook is something I always suffered... as stated on the op, I'm trying it and finding there almost everything I need in small to medium enterprises... this is the first project of this size I feel as complete for my needs.. this is why I think that it could be a good Ubuntu server (intended as product supported by our community) even if it's not ubuntu but debian based... I'll surely start to contribute as a ruby/python/php/perl programmer to that project... I just think they need a bit more advertising... ^_^

Thanks a lot for your kind words, Tasu!

Let me introduce myself - I lead the development team at [DeepRoot Linux]("http://www.deeproot.in") - developers of the deepOfix Mail Server. We are very glad that you find deepOfix useful and worthy of contributing to.

Meanwhile, I'd like to point out that eventhough deepOfix is Debian-based, you **can** configure an Ubuntu repository as its APT source and install just about any Ubuntu packages on it. We have users who run desktops on top of deepOfix by justing installing the relevant desktop components - it does not really interfere with the desktop functioning at all.

Hope this helps you...

Cheers, Abhas
[email]abhas@deeproot.co.in[/email]

---

### Post by Macchi on 2007-02-22
Great to see you here Abhas, as a direct representative for an open source project with the server functionality that we are talking about!

Could you post a Howto for deepOfix Mail Server on Ubuntu?
 
I am sure you will get some attention and new users around here. As we know this is often a win-win: A benefit for the open source community and a good way to introduce less known products in the market, attracting new customers for your products and services.

---

### Post by compudude86 on 2007-02-22
ok, stupid question, but does it come with smarthost and smtpauth? i need to be able to use it to serve mail from behind my sbc yahoo dsl, and they block 25 except for those going through their mailers, basically it needs to be able to be configured like sendmail would.

---

### Post by nocturn on 2007-02-23
> **compudude86 said:**
> ok, stupid question, but does it come with smarthost and smtpauth? i need to be able to use it to serve mail from behind my sbc yahoo dsl, and they block 25 except for those going through their mailers, basically it needs to be able to be configured like sendmail would.

It will be running an smtp server like sendmail, postfix or exim and if the web based admin panel does not display this, you can always put a smarthost in the config files.
Each of these MTA's supports that.

---

### Post by Tasu on 2007-02-23
> **nocturn said:**
> 
Each of these MTA's supports that.

From what I can see it uses qmail and it looks like that the web interface allows a lot of options... but now I'm not at home and can't see if those options are configurable via Web Interface (but I guess yes!).

---

### Post by compudude86 on 2007-02-23
ok, i just played with their live online demo version, and it does indeed allow this! thank you to whoever created this!!!!

---

### Post by compudude86 on 2007-02-26
ok, i need some help with this. i installed this on my servers, all went well. i read deepofix's documentation, it tells me to log in on http://<server-ip>:4080 so i do. it tells me its a secure connection. so i set it to https://<server-ip>:4080, it gives m e the login. i use the user (admin) like the docs say, and my system password i chose in the beginning. no luck. anyone know about this?

---

### Post by compudude86 on 2007-02-26
ok, i fixed it, i just reinstalled deepofix. i have another issue now. i ask here because im feeling that if i post a seperate question nobody will understand what im talking about, so dont think im threadjacking. now, i need to accept mail on this server, and send from it, both of which dont work. i need to send any outgoing mails to smtp.att.yahoo.com , using authentication. any mails sent to (user)@jicomnet.com and jicomnet.sytes.net , both individually. how do i set this up?

---

### Post by Tasu on 2007-02-27
> **compudude86 said:**
> i need to send any outgoing mails to smtp.att.yahoo.com , using authentication. any mails sent to (user)@jicomnet.com and jicomnet.sytes.net , both individually. how do i set this up?

I'll have a glance at it soon, usually in my environments I don't need to forward email to other servers, the corporate mail server delivers it by itself....

---

### Post by compudude86 on 2007-02-27
> **Tasu said:**
> I'll have a glance at it soon, usually in my environments I don't need to forward email to other servers, the corporate mail server delivers it by itself....
ok. heres my configuration. i have two setups now, both on sbc dsl. they both use no-ip to get a domain name (dynamic DNS) one goes through a D-link router, and the other goes through a "freesco" router (old 486 made into a router with linux) on both ive opened up port 110 and 25, yet any time i send a mail to one of the accounts, nothing shows up in the inbox. ive even tried to turn off the firewall on the deepofix box, nothing. im replacing a communigate mail server on one, and that received mails right after installation. thanks for all your help

---

### Post by compudude86 on 2007-02-27
well, i dont think ill have to worry much longer, i got the "d-link router" one working, i emailed AT&T and had them turn off port 25 blocking, and i got the mail moving. now, for the "freesco router" one i have at home. i had them unblock the port there as well, so now i will try when i get home from work. i will definately keep posted, and as far as im concerned on this one at work that i got working, this mail server is a really stable and reliable server, and really would be a good asset if ported to ubuntu.

---

### Post by Tasu on 2007-02-27
> **compudude86 said:**
> well, i dont think ill have to worry much longer

Happy that you've found the solution to the problems! ^_^

---

### Post by compudude86 on 2007-02-27
one last question..how do i get the webmail server and the easypush server to the outside? i punched holes in the hardware firewall...yet when i use the browser to go to the ports for it, it times out or wont connect..

---

### Post by compudude86 on 2007-02-27
ok, using switchboard to disable the firewall lets me access it. how do i edit the firewall port file or disable the firewall completely?

---

### Post by jonic on 2007-03-05
Well it really looks interesting, but I wouldn't call it the server that we are waiting for. It really is just an email server so it could replace MS Exchange, but MS Small Business Server or SME ,  offer a lot more functionality. I haven't used SBS, but I use SME and the lack of samba services, web server and multiple domains support immediately come to mind. Of course they could be added, but you couldn't use the web interface to manage them. And you could add a lot more features to SME using contribs, that integrate well with the web management console.

Also I didn't spot any forums on deeproot site, and that's a big minus for everyone that is not buying support from deeproot.

So I would call it a great distribution for an email server, and certainly one that is easier to build upon than the Ubuntu Server, as it has a great deal of functionality already built in, but definitely not a complete and easy to administer small business server.

---

### Post by hortimech on 2007-03-05
I tend to agree, it is interesting but not great. I am looking for something to replace our Mdaemon mail server, this seems to be the closest yet, but it still has problems, not least that there are no security updates unless you buy support, documentation is non existant and you have to set samba up manually.

Hortimech

---

### Post by jonic on 2007-03-05
> **hortimech said:**
> I tend to agree, it is interesting but not great. I am looking for something to replace our Mdaemon mail server, this seems to be the closest yet, but it still has problems, not least that there are no security updates unless you buy support, documentation is non existant and you have to set samba up manually.

Hortimech

I suggest you to check SME Server, it really has a lot of functionality built in, more can be added via contribs, a dedicated team that supports it, and a great community.

---

### Post by compudude86 on 2007-03-05
im going to try this SME server you guys suggest. i have deepofix running on 2 servers, my home and my work. my home one is buggy, it delivers and receives some days, others it just  dies on me, while my one at work had to be reinstalled the same day i launched it because it locked me out of root. ive attempted to ask them for help. ive attempted to buy support. neither are responding, at this point it seems like its a dead distro. but im definately gonna try this SME distro. thanks

---

### Post by Lod on 2007-03-06
> **Tasu said:**
>  I'll surely start to contribute as a ruby/python/php/perl programmer to that project... I just think they need a bit more advertising... ^_^There is a project going on to make such a server based on Ubuntu, called Legus It is discussed in  [this thread](http://ubuntuforums.org/showthread.php?t=344943).

---

### Post by dexem on 2007-03-06
Legus seems to be not updated since December'06 and I haven't been able to find any work done (probably is my mistake :P )

Apart from being based on Debian, does any problem exist with eBox? ([http://www.ebox-platform.com](http://www.ebox-platform.com))

---

### Post by Tasu on 2007-03-08
> **dexem said:**
> Apart from being based on Debian, does any problem exist with eBox? ([http://www.ebox-platform.com](http://www.ebox-platform.com))

Well, even eBox looks really good, I'll try it this week end, but from what I can see, it has no ldap authentication for the network, it just uses ldap internally, so no way of easily authenticating linux users in the network... and can't find an ldap address book... or I just have to dig the website more? Sigh it looks like that therea are plenty of those preconfigured servers, all with a lot of applications in common, but none really full featured, if just the devs would meet and stop reinventing the wheel... it would be really good to have a sbserver like ebox, with added a ldap addressbook like deepofix has and the ability to authenticate linux users via ldap and why not, some of the good ideas behind the mass handling of users like in deepofix... otherwise it would be good to see a deepofix server with samba-ldap preconfigured to allow auth of windows users and easy setup of samba shares... It always look like that they are both really good, but not perfect... 

They just seem to have to integrate some of their features into each other...

---

### Post by dexem on 2007-03-09
> **Tasu said:**
> Well, even eBox looks really good, I'll try it this week end, but from what I can see, it has no ldap authentication for the network, it just uses ldap internally, so no way of easily authenticating linux users in the network... and can't find an ldap address book... or I just have to dig the website more?

Ok, that's true. Now it's impossible but it was planned on the roadmap. Now eBox is in 0.9 version, and probably 0.9.1 won't have LDAP just listening at lo interface, so authentication for users could be done :)

More ideas are truly welcome :)

---

### Post by curuxz on 2007-04-04
after a careful review of deepofix i would like to give the following comment:

**[SIZE="7"]DO NOT USE DEEPOFIX ON ANY PRODUCTION SERVER IT IS NOT FIT FOR PURPOSE[/SIZE]**

I can not warn people against this product enough, the reasons are countless but just a few points:

It loses email esp BCC messages

its control panel SUCKS, so many errors and so little ablity to configure things remotely!

It breaks package wise for a past time with simple installs of programs like webmin, so replace the afore mentioned piece of crap control panel

ITS REPOS DO NOT WORK, the stock repos are forbidden no doubt an attempt to get money from users.


After looking into the company who makes it and the lack of forum, working wiki, documentation etc i realised its just another company from guess where?! (lets just put it like this the place where all the other crap software companies come from).

They are trying to pedle out a half finished distro built on other peoples work that they have the gual to charge for! Test it out for your selfs and see what you think, but this to me is one of the worst distro's ever and while the concept is sound (suggested by many before so no points for originality only for bothering to try others' ideas) but the implementation is terrible.

a fat 0/10

---

### Post by Tasu on 2007-04-04
I must do a public amend for letting my first impressions obfuscate my judice and make me behave like a fanboy.. sorry guys, sorry all, deepofix has really a lot of features that must be ironed out, and is not really ready for a production environment.

---

### Post by Tasu on 2007-04-04
> **dexem said:**
> More ideas are truly welcome :)

Indeed ebox looks like a good project by now, not had the reliability problems deepOfix indeed gave me with mail, I just had a little problem in adding computers to the domain, but if I add them using the wizard, all works good. I'm now looking for a RW ldap addresbook solution (user and group based to let people access it) and it would be great if there will be even a webdav/caldav solution to share celendars. Are you planning on working on these? I'm willing to help.

---

### Post by dexem on 2007-04-04
> **Tasu said:**
> Indeed ebox looks like a good project by now, not had the reliability problems deepOfix indeed gave me with mail, I just had a little problem in adding computers to the domain, but if I add them using the wizard, all works good. I'm now looking for a RW ldap addresbook solution (user and group based to let people access it)

This can be done with a small hack made by-hand. If you edit /var/run/slapd.args you can add the IP address for the internal interface you want slapd listen. Now only listens for localhost.

> **Tasu said:**
>  and it would be great if there will be even a webdav/caldav solution to share celendars. Are you planning on working on these? I'm willing to help.

You can install with apt-get you favourite webdav/caldav solution, but it will only work for your internal interfaces. If you want to access them from outside, you should create an VPN and get them through it.

Some of these have been yet required from some users, but we cannot work faster ;) Good luck with these changes :) Oh! and of course feel free to join #ebox at freenode or join the mailing lists. 

Regards

---

### Post by kevindontenville on 2007-04-30
Zimbra.com now has an alpha version offline web client which works with the OSS version as well as an OSS Evolution connector that syncs mail, contacts and calendars. I am using the Evolution connector quite successfully using a user contibuted binary using Feisty and Evolution 2.10.1 . The Ubuntu Zimbra Server install is just about point and click so long as DNS has been configured properly. Recommend look at it for many groupware services esp the document/wiki feature.

K

---

