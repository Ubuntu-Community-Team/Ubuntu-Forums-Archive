---
title: "advantages of using Ubuntu as a server"
date: 2006-05-31
forum: Server Platforms
---

### Post by Arc Owner on 2006-05-31
I'm still fairly new to running a server, and I have been running one with ClarkConnect for a couple months. For those who don't know, it is very easy to setup with a web-based configuration tool. It was recommended to me by the guru's at my local LUG, but now I am thinking about switching to Ubuntu server. I've seen documentation for setting up ubuntu as a server and it looks very difficult and overwhelming (and this is coming from someone who has installed Gentoo many times). I use my server as a web and mail server. Would there be any significant advantages to using ubuntu as a server as opposed to ClarkConnect? I know most people run a server on a distro which requires them to setup everything manually, editing .conf files, so I though there would be a reason as to why they don't use something more easy to setup.

---

### Post by Iowan on 2006-06-01
I've never seen/used ClarkConnect, so I can't give a fair evaluation, but your post deserved a response of SOME sort.  I doubt setting up Ubuntu as a server is much (if any) more difficult than any other distro.  My installation was fairly painless - but I'm not completely done yet, either.  [http://www.howtoforge.com/perfect_setup_ubuntu_5.10]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10")  You've probably already seen this, but in case you haven't...

---

### Post by Klaidas on 2006-06-01
Well, a few reasons:
[LIST]
[*]Stability. It's stable.
[*]Updates. They come fast ;)
[*]Community. The best you can imagine
[/LIST]

---

### Post by Arc Owner on 2006-06-01
I've been looking at the official Ubuntu server guide, and have seen that there is very good documentation. I think I'll try something different and install an ubuntu dapper drake server. :D 

I know this has nothing to do with my initial post, but in Ubuntu I can choose between Postfix and Exim for SMTP. Which one would you guys recommend using?

---

### Post by diebels on 2006-06-01
[QUOTE=Arc Owner]I've been looking at the official Ubuntu server guide, and have seen that there is very good documentation. I think I'll try something different and install an ubuntu dapper drake server. :D 

I know this has nothing to do with my initial post, but in Ubuntu I can choose between Postfix and Exim for SMTP. Which one would you guys recommend using?[/QUOTE]
Postfix

---

### Post by Bokonon on 2006-06-01
Mail servers and me do not get along.  I have tried sendmail, qmail, exim, postfix and a few others, but the only one I got working well was postfix.

I am sure it is easier to setup now than in the past, but for some reason, my brain does not work in the right way in regards to mail servers.  I hope I never have to setup one again.

So, postfix gets my vote.  If I remember, configuration is generally easier and it has good security.

Here is a quick [comparison]("http://www.geocities.com/mailsoftware42/") of the server types.  If I remember, O'Reily had a good chart back when I was researching.

---

### Post by dtfinch on 2006-06-02
I've never used ClarkConnect, but I've usually run CentOS (what ClarkConnect is based on) on servers and Ubuntu on desktops, but there's no reason Ubuntu can't fill both roles now that it's getting 5 years of updates. ClarkConnect is advertising only 3 years of updates, which is odd, because CentOS is advertising another 4 years of security maintenance after the initial 3 years of full updates.

---

### Post by FredSambo on 2006-06-02
i haven't used clarkconnect.

i have moved several of my client's servers over to breezy, from windows SBS 2k3, in april and all is well so far.  i think i could probably do as well with suse or debian, but i am here because of the community and the mission.  ubuntu is going to take over the server world, and then the desktop world, and then the world.  :)

---

### Post by Tortanick on 2006-06-03
Fred, that is not a good idea. One OS is vunerable to viruses, one OS with diffrent distro's is a lot safer.

---

### Post by tribaal on 2006-06-03
Well I have never used ClarkConnect either, but I just set up a couple of Ubuntu webservers (using the "LAMP install" from the server install disk).

They are dead simple to set up. As for the mail server, I would guess there are packages in the repos that pretty much "auto-setup"... no?

Cheers

- trib'

---

### Post by FredSambo on 2006-06-03
> Fred, that is not a good idea. One OS is vunerable to viruses, one OS with diffrent distro's is a lot safer.

thanks for the tip, but i am a MCSA from a past life, so i think i have my windows machines under control.

:)

---

### Post by shreko on 2006-06-03
I've tried ClarkConnect, it works as advertised. Paid support is good, but community support is minimal. I like the idea of server management over web config tool, which works pretty good in CC. I've had some problems with bacula, but http, samba and vpn work great. If Ubuntu server would have a similar tool then it would have full advantage over cc and similar distros. Til then, Ubuntu advantage would be excellent community support and better update/install system.

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=Arc Owner]I use my server as a web and mail server. Would there be any significant advantages to using ubuntu as a server as opposed to ClarkConnect?[/QUOTE]

no matter which Internet Service Provider or hosting company you use. I always prefer my own installation using my own selected and prefered Linux distrubution. I never would use a pre-configured setup from any hosting company.

To be honest: you need some good Linux and server knowledges and also experiences to install and run a production web server without problems. Without good knowledges and experiences a pre-configured setup could be real helpfull.

All my production servers run the same system. Furthermore I run the same system as Desktop machine at home (except some server specific software). By this way I do use only one system and can share experiences between desktop and internet server.
Furthermore I use my desktop as development machine and all PHP web apps tested at home does run on the internet server, too.

For several years I used Mandrake on server and desktop. Past year I decided to move to Ubuntu-Server and Kubuntu (desktop). Many reasons forces this decision, like the force to upgrade the entire system at least once a year (if you want to get updates) or the too complicated RPM dependencies (too much rpm packages depends on many useless and unwanted other packages).
I tested lot of distributions and Kubuntu was the big hit, so I first changed my desktop and after some weeks I re-installed all my internet servers.

I use netqmail-1.05 (qmail including some usefull patches), vpopmail, qmailadmin, courier-imap, apache2, php4, mysql, proftpd. But I compiled and configured netqmail, vpopmail, qmailadmin, courier-imap and proftpd myself. Only the basic system is installed from ubuntu.

Thomas

---

### Post by jgeiselman on 2006-07-15
I have had the advantage of using both clark and ubuntu at work. Due to state req. we use clark as a firewall and filter, and I use ubuntu as a backoffice webserver/fileserver. In my humble opinion ubuntu was and has been far easier to setup and support. Like an earlier post said the community is fantastic! This is actually my first post b/c I've never had a problem I couldn't find the answer for.

---

