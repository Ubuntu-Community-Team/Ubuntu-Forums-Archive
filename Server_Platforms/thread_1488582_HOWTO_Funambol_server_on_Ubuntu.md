---
title: "HOWTO: Funambol server on Ubuntu"
date: 2010-05-20
forum: Server Platforms
---

### Post by hakkie42@gmail.com on 2010-05-20
Hi all,

I wanted to synchronize address book and calendar data of Thunderbird/Lightning clients, possibly Outlook on Windows, Mac OSX ical, Nokia mobile phone address book/calendar etc.

After searching in vain for idiot-proof documentation for Funambol server on Ubuntu I've written my own, with thanks to marckaplan's guide and others (see references in document).
I succeeded in setting up Funambol 6.5 community edition on Ubuntu 8.10 or thereabouts; I've finally switched to Funambol 8 on Ubuntu 9.10 and it still seems to work on Ubuntu Lucid Lynx/10.04. I've now moved to Funambol 9 on Debian 6, but the principles remain the same.

If this howto is up to scratch, I'd like to put it into the documentation wiki, but first I'm eagerly awaiting comments.
I've pasted parts of the text below for reference/keyword hits on forum searches. Looks like it needs to be reformatted quite a bit; at least the OpenOffice document looks a bit better (see attachment below).
Keywords: Funambol, Ubuntu, Server, SyncML, OMA, PostgreSQL, java, Tomcat

Reactions welcome.

regards,
jb

          **Funambol on Ubuntu**

 
 This document described how I set up Funambol on Ubuntu server. Of course, there are more ways of doing this. I've tried to document the reasons why I've chosen this path.
 The Configuration and Funambol administration client sections are required for proper operation; at least some of the other staps can probably be omitted, but I haven't tested all possible configuration combinations.
 I've marked things that may need further improvement, but the text should be usable as-is.
 If you want to send me improvements to this text, please do so!
 hakkie42 at gmail free mail
 © 2010 jimbeam. Feel free to (re)use this text, but no warranties, express or implied, are given.  
 
Configuration
Below is a table where you can record your specific configuration information. The rest of the guide should explain the meaning of the terms or indicate where you can find more information.
Item
Suggested value/value
Description
Install location
/opt/Funambol
I suggest keeping the default value of /opt/Funambol. We assume you used this setting in the text below. Change to match your own setting if that differs.
Host
funambolserver
Host name that will become part of the sync URL. If you don't have proper DNS set up, use the IP address of the server.
Tomcat HTTP sync port
<nothing, as we use the Apache web server reverse proxy>
Port Funambol/Tomcat listens on for sync requests. Configured in /opt/Funambol/tools/tomcat/conf/server.xml
Default 8080 
Tomcat HTTPS sync port
<nothing, as we use the Apache web server reverse proxy>
Port Funambol/Tomcat listens on for sync requests over SSL/TLS.
Configured in /opt/Funambol/tools/tomcat/conf/server.xml
Default 8443
Tomcat AJP port
8009
Port Funambol/Tomcat listens on for AJP proxy requests. We use this for our Apache web server reverse proxy.
Configured in /opt/Funambol/tools/tomcat/conf/server.xml
Default 8009
Funambol admin username
admin
Administrative user used by Funambol Administration tool to manage Funambol (users, devices etc)
Funambol admin password
sa
Password for that user. Good idea to change this!
Sync URL
https://<serverip>:8080/funambol/ds
or
[https://serverip/sync](https://serverip/sync)
URL that you use on your client devices to synchronize. Consists of hostname Funambol/Tomcat listens on, Tomcat http sync port and /funambol/ds, unless you changed that in the config ;)
You can use the shorter form if you use my Apache reverse proxy configuration.
External sync URL
https://<publicserverip>:34528/funambol/ds
or
https://<publicserverip>:34528/sync
Same as Sync URL but for  users outside your LAN. Giving a suggested value is impossible as it depends on your external ip address/name. 
You can also use the shorter form if you use my Apache reverse proxy configuration.
JAVA_HOME
/usr/lib/jvm/java-6-sun/
Environment variable/location of the Java JDK/JRE/whatever it's called this week.
If you strip Java from the Funambol bundle (as I do), Funambol needs to point to the proper JAVA_HOME directory
jdbc.classpath
/usr/share/java/postgresql.jar
Sync server Java database driver setting in /opt/Funambol/ds-server/install.properties
It points to the jar file containing the PostgreSQL driver.
jdbc.driver
org.postgresql.Driver
Sync server Java database driver setting in /opt/Funambol/ds-server/install.properties
Java driver class. Modificaton should be unnecessary, unless you use a non-PostgreSQL database.
jdbc.url
jdbc:postgresql://localhost/funambol
Sync server Java database driver setting in /opt/Funambol/ds-server/install.properties
URL to the Postgresql server and database.
jdbc.user, same as funambol user
funambol
Sync server Java database driver setting in /opt/Funambol/ds-server/install.properties
User name for the funambol database on PostgreSQL
jdbc.password
4890hjEla#aas&d2sk2
Sync server Java database driver setting in /opt/Funambol/ds-server/install.properties
Password for the user connecting to the funambol database on PostgreSQL

Full HOWTO (OpenOffice and PDF):
[ATTACH]185853[/ATTACH]
[ATTACH]185854[/ATTACH]

---

### Post by cocoa117 on 2010-05-25
very nice, I was looking for similar document for Ubuntu, so glad you have done it and wish you could have done sooner.

---

### Post by hakkie42@gmail.com on 2010-05-26
Glad you like it. Like you, I wish it had been done before ;)

---

### Post by 3L33T on 2010-05-26
eeek!!! your post jussssssssst reminded me that I did sign up for funambol and 'promised' to test it on my BB8900 and SonyEricsson P1i but never got to it (sooo busy).  THANK YOU for the doc.

---

### Post by mutrax on 2010-05-31
you sir, are my personal hero for the next few months!

I'll be reading your tutorial troughly. Been messing with funambol as with as basic settings as possible and the damn server refuses to run after a while without any idea howto debug the problem...](*,)

thank you!

Groetjes,
Ed

---

### Post by hakkie42@gmail.com on 2010-06-04
Hi guys,

Thanks! If anything in the doc is incomplete, wrong or vague, let me know...

Ciao,
me

---

### Post by smaffulli on 2010-06-11
this is a great document, thank you. Would you like to share it on [Funambol Forge wiki]("http://core.forge.funambol.org/wiki"), too? I think it would make life easier for many Funambol users out there.

---

### Post by hakkie42@gmail.com on 2010-06-13
[3L33T]("http://ubuntuforums.org/member.php?u=774645"), any news on those clients? If you have any info, I'd be glad to update the doc!

---

### Post by hakkie42@gmail.com on 2010-06-13
> **smaffulli said:**
> this is a great document, thank you. Would you like to share it on [Funambol Forge wiki]("http://core.forge.funambol.org/wiki"), too? I think it would make life easier for many Funambol users out there.
I'd love to. I suppose a page in the CategoryServerUser called something like HOWTOFunambolPostgreSQLUbuntu would be appropriate?
I'll try and upload it there. If you or anyone else would like to do it, please be my guest.

BTW, I've slightly updated the document, to fix some potential issues with PostgreSQL user names (only happens on non-default install of PostgreSQL on Ubuntu), and hopefully clarify the text in places.

---

### Post by mutrax on 2010-06-14
> **hakkie42@gmail.com said:**
> [3L33T]("http://ubuntuforums.org/member.php?u=774645"), any news on those clients? If you have any info, I'd be glad to update the doc!
Well It does work on a **Nokia E52** phone... No glitches... Just make sure that when erging email and phone contacts, all contacts have the name field filled.. or you'll hava a lot of nameless contacts on your phone.

---

### Post by mutrax on 2010-06-14
> **mutrax said:**
> you sir, are my personal hero for the next few months!

I'll be reading your tutorial troughly. Been messing with funambol as with as basic settings as possible and the damn server refuses to run after a while without any idea howto debug the problem...](*,)

thank you!

Groetjes,
Ed

Oh yeah, I sorted the unpredictability. When I ran VMware server with it's own java shrinkwrapped into it (just as funambol does). The loaded java apps from vmware prevent funambol's webserver to load.

---

### Post by hakkie42@gmail.com on 2010-07-19
> **mutrax said:**
> Well It does work on a **Nokia E52** phone... No glitches... Just make sure that when erging email and phone contacts, all contacts have the name field filled.. or you'll hava a lot of nameless contacts on your phone.
Mutrax, I've updated the document quoting you. Thanks!

---

### Post by hakkie42@gmail.com on 2010-07-19
> **smaffulli said:**
> this is a great document, thank you. Would you like to share it on [Funambol Forge wiki]("http://core.forge.funambol.org/wiki"), too? I think it would make life easier for many Funambol users out there.
Hi smaffuli, I created an account on funambol forge (hint: email address should look familiar). However, I have no idea how I can get permission to add a wiki page. Do I have to become member of some www project? If so, how do I do that?

If you want to drop me a hint, please feel free to send me an email...

---

### Post by mutrax on 2010-07-30
Hmmm, I linked the wife's nokia 6303 classic and I seem to be getting double entries that where entered via lightning.... Birthdays that where on her phone seem to have moved dates. Bummer. I use the default sync settings from the phone (nu funambol software).

Anyone with the same experience? I'll be digging in to this anyway.

Regards,
Ed

Oh yeah, I more ore less used the instructions (with my db names and urls) found here... [http://www.memotoo.com/infoSyncML.php](http://www.memotoo.com/infoSyncML.php)

---

### Post by HDave on 2010-10-11
I see in the how-to that you are using AJP protocol from the apache reverse proxy and the tomcat servlet container.  Any reason you are not just using regular http?

I ask because I have been struggling for some time now to get apache (on an edge machine in the DMZ) to reverse proxy http to the funambol sync server (running on the LAN).  Using AJP is not a problem, but since this DMZ server already proxies http for 7 other LAN servers I thought I'd just keep things consistent.

Any light you can shed on the subject is much appreciated.

---

### Post by hakkie42@gmail.com on 2011-01-25
HDave,

Sorry to get back so extremely late, but I'll answer anyway. I used AJP because I remember reading it's specially written to let Tomcat communicate efficiently with Apache, that's the only reason. It just seemed a bit superfluous to use a web server to serve http/https and then proxy http to Tomcat.

Just proxying http probably works just fine.

---

### Post by kubwit on 2011-03-24
Hallo. You did a great job. I subscribed to funambol web and i liked it. So i decided to setup my private server for my company.

I'm not new to ubuntu (we are only running ubuntu 10.04 machines) but i cannot understand where the admin of funambol is started or configurated. Is it a graphical frontend if yes how can i start it?? if it has a config file where is it??

Maybe somebody can tell me because in the very detailed howto this doesn't come out.

Thanks for you interest and reply

---

### Post by hakkie42@gmail.com on 2011-03-25
The admin program (Funambol Administration Tool) is a separate Java program; you can find it in the installed funambol bundle I think (in the howto I remove it because I don't need it - I use the windows version of the tool). Regardless, you should be able to download the admin tool separately from the Funambol site if you still have problems... 

hth

---

### Post by mutrax on 2011-03-25
FWIW,

I've migrated my systems & customer systems from funambol to Egroupware. Easier to setup (installing external repo's, pinning php to 5.2 and removing php-acp). And you have a great gui for your end-users! I personally also use the timeregistration and taskmgmt. 

As a personal opinion, I found myself constantly jumping trough flaming hoops to get/keep it running. 

Please note that this is a personal opinion, I just fugured to tell you guys that there is an goot alternative as funambol server. The clients remain reliant on the funambol plugin or syncml.

Regards,

---

### Post by Planetom on 2011-09-16
Hi Chaps,
Sry I to retard your enthusiasm but no https variant is working in my setup. I mean lucid runs well, so does funambol but no SSL whatsoever. I did every single bit from the howto - nothing. 
Well I could not follow all instructions hence not all parts are explained such as the certficates one. Guess which part creates the trouble.
No offense but unless you are a SSL / certificates expert you are lost. I am not the person to give up easily but after having spent night after night for 2 weeks reading a zillion forum entries, incomplete howtos and cryptic documentation, frustration is driving me over the edge. 
Does anyone have a full howto to install a running version of reverse proxy SSL? I mean sth. a false beginner level user can follow?
Thx & Cheers,
Murmel

---

### Post by hakkie42@gmail.com on 2011-09-17
@Mutrax, ok, however, Funambol is only a sync server, so only comparable to egroupware if you factor in clients such as PDAs, Evolution, Thunderbird etc.
But I get your point: less hassle = better :wink:
I'm looking at getting Sogo as groupware server, which syncs with Funambol as well, has a web interface, good Thunderbird/Lightning connectivity, and is collaborating with OpenChange to get native Outlook support going (Microsoft Exchange drop-in replacement). 

@Planetom: if you don't know about SSL & Apache, I'd start in getting a regular website working with SSL and apache (first with the default, snakeoil cert, then with a self-signed cert). I presume Ubuntu documentation has enough info on getting a basic SSL site set up. If not, I'd file a bug with the docs guys and look for other documentation.
Only if that works, move on to testing with Funambol.

You do have to understand a bit what you're doing so blindly copying instructions won't help much. I'd look for a tutorial that explains what's going on, and reading openssl/Apache/Ubuntu documentation until you understand a bit more why and how you are doing things.

As for the howto not being complete, sorry, but it cannot ever be complete for beginners: I'd have to go over Ubuntu install, apt-get/aptitude, Apache install, Postgresql install, self-signed or externally signed SSL certs etc.
The possible variations/needed clarifications would be endless, so I decided to focus on the things that seemed obscure to me. SSL wasn't one of them.
I understand your frustration though, had the same with Funambol initially, that's why I decided to write up my experiences.

Good luck & if you get it figured out, please feel free to make suggestions for improvement of the tutorial.

---

### Post by Planetom on 2011-09-17
God helps those who help themselves.

---

### Post by hakkie42@gmail.com on 2011-09-17
... and then help others, I hope.

I DID write a tutorial on Funambol for others to use, for free, out of the goodness of my heart. Do you know how many hours that cost, after spending all that time to read through the same kind of half-complete information you're struggling with?

If you get to the bottom of the SSL stuff, you're more than welcome to add information to it.

I'll leave it at that.

Good luck.

---

### Post by xxlray on 2012-08-23
Maybe someone reads this although the thread is rather old.

I tried to install funambol 10.0.3 on Ubuntu 10.10 64Bit. Unfortunately when I try to start the server "cd /opt/Funambol/bin && sudo ./funambol start" nothing seems to happen. "sudo ps | grep funambol" does not show anything, the web interface can not be openend and the admin tool does not connect. There is no error message at all when trying to start the server.

I read that you might have to install ia32-sun-java6-bin but this did not work for me. any idea how I can find out why it does not start?

---

