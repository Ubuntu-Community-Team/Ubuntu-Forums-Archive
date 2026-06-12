---
title: "Dazed and confused: Ubuntu or Fedora?"
date: 2005-07-21
forum: Server Platforms
---

### Post by farao on 2005-07-21
Hi all,

The concrete question is:
are there easy server configuration tools for Ubuntu, and is there a way to install the latest versions of mysql and php5 without the hassle of compiling from source?

Ok, I admit, I'm a Linux n00b, but I'm willing to learn. After rumagging the forum (found the posts regarding BUM, php5, the fedora-discussion and more), I've learned a lot, but I've also found there's a lot more that I don't know (yet).

The rest of this post is just what brought me to this question, and can be skipped by those who don't like long posts.

After playing around with FC4 and Hoary, I've come to like Ubuntu for the ease of installing apps with apt-get, and the painless installation of a base system.
However, there are a few things that make me consider FC4 for my home server:
- installing apache2, php5 and mysql 4.1 is not painless on ubuntu, so far I've not managed to get it all working (with php4 I get a phpinfo displayed on localhost, but not remote (although it DOES work with IE, so I suspect another culprit)).
- the configuration of apache is needlessly complicated, with every directive in a separate file. I admit, it saves the trouble of editing the lengthy httpd.conf, but it took me a while before I found out how it works.
- setting up the services requires a GUI that's not installed by default, and though BUM is a great app, the app FC4 uses is slightly handier.
- configuring the servers (web, ftp, samba) is all done through a prompt, and while I don't shy away from a prompt, I like the preferences to be set through a GUI (and yet again I contradict myself when stating that the config-GUI in FC4 adds a lot of blank lines to the files when editing through the GUI, which is annoying if you need to edit them through ssh once in a while).

*sigh* what to do? I like Ubuntu, and will in the end probably get it all working (apache2, php5, mysql4.1, couple of domains, ftp etcetera), but if every update requires another complete dive into the bowels of the machine, pff, maybe not.
FC4 on the other hand comes prety much out of the box with bleeding edge, and seemes more geared toward server use than Ubuntu. I DO however like the underlying message of Ubuntu a lot better: humanity. Compared to the Fedora message: corporate playground, it's contrast.

Anyway, thanks for any reply, I'll keep plodding on.

Best, Farao

Edit: the save-dialog in firefox is solved, at least my server now displays correctly instead of asking me what to do (it knows what to do, so why ask me, right?)

---

### Post by lorenzo on 2005-07-21
Hi,
regarding php5 on ubuntu, have a look here:

[http://gfabio.blog.free.fr/old/index.php?2004/12/15/108-ubuntu-installer-php5](http://gfabio.blog.free.fr/old/index.php?2004/12/15/108-ubuntu-installer-php5)

The steps to follow are very easy.

Ciao,
Lorenzo

---

### Post by farao on 2005-07-21
Thanks Lorenzo,

I got it to work, it now says: Apache/2.0.53 (Ubuntu) PHP/5.0.4-0.6.hoary.1 Server at 10.1.11.103 Port 80

and the php-files display as expected.
Actually, this plodding is becoming more fun by the minute (but only because it's actually working now, obviously).

I'll keep at it, and stick to Ubuntu for now (I find it easier to learn using just one distro, instead of switching from one to another). Once I'm a bit more familiar with Linux, I can start looking around at other distro's.

Thanks again, Farao

---

### Post by dcraven on 2005-07-21
I don't think any GUI is required to set up services at all. At least I've never come across a service like this. 

~djc

---

### Post by benkong2 on 2005-07-21
[QUOTE=lorenzo]Hi,
regarding php5 on ubuntu, have a look here:

[http://gfabio.blog.free.fr/old/index.php?2004/12/15/108-ubuntu-installer-php5](http://gfabio.blog.free.fr/old/index.php?2004/12/15/108-ubuntu-installer-php5)

The steps to follow are very easy.

Ciao,
Lorenzo[/QUOTE]
 I am not good at all with French is this guide available in English?

---

### Post by mcewen98 on 2005-07-23
[QUOTE=farao]Hi all,

The concrete question is:
are there easy server configuration tools for Ubuntu, and is there a way to install the latest versions of mysql and php5 without the hassle of compiling from source?
[/QUOTE]

Remember that most production servers do not use KDE or Gnome, to save system resources and eliminate potential security issues that are not essential to the machine.  For home use though, I don't see what's wrong with using Gnome or KDE (this is what I do).  I agree with you, however, some easier to use config tools for server type services, that are installed by default, would be nice.  You can also install webmin using apt.  I've found this useful for adding samba shares, rather than hand editing the file.  It does take a little effort to set up, and make sure you get the needed modules for it.

About FC4.  I thought about using this instead of Ubuntu when I built my home server, and I am glad that I didn't.  This may not be a big deal and I may be wrong, but I don't like the fact that FC is really just an edition for Redhat to get some free community testing with for their commercial enterprise distro's.  

I don't feel that there is as good support for Fedora, and the things I have heard about the helpfullness, and non-elitism Ubuntu community have so far been true.  I may be wrong about the upgradablity from one major revision to the next of FC, but I remember reading that it was very difficult, and sometimes impossible to do.  It seems like new version of FC comes out pretty frequently .  The thought of having to reformat my server, even if it's once a year is too daunting.  With ubuntu, it sounds like it will be easy to upgrade to Breezy and beyond, and doesn't the older version still continue to recieve security updates for like 18 months?  I'm not sure what the policy is with Fedora.  

I have found Ubuntu's automatic package updates and apt to be much more of a time saver compared to what it would be having a gui tool for the server configuration.  You set that once and forget about it, but you will always be faced with doing updates.  With other RPM distro's I found myself compiling a lot of apps myself, and these of course would not get automaticlly updated.  I now have apache2, ssl, php, mysql, samba, ssh, mythtv backend, and ftp all installed using apt and working wonderfully together, with relativly little effort.  All of which will recieve automatic updates as they become available saving me the time and worry of having to do it myself.

Anyway, my two cents.

---

### Post by XoloX on 2005-07-24
Two weeks ago I set up a file- (Samba) and web-server (Apache). Under Debian Sarge BTW, but I'm seriously considering Ubuntu at the moment :). I've used webmin for a week, but for some reason it kept screwing up config files. So I've removed webmin. Because I still want to edit Samba's shares once in a while, I've decided to install SWAT. If you don't like webmin but still want to configure Samba from a web-interface I suggest you give it a try. Note that you have to enable SWAT after install. I forgot the file you have to edit, but you should find it in the docs (man swat). Then you can call [http://nameofserver:901](http://nameofserver:901) and configure aswell as browse the doc's from that address. Good luck!

---

### Post by farao on 2005-07-28
Thanks everyone, I've been playing around with both distro's, and indeed have come to like Ubuntu better.
@mcewen98: You're right, a server is pretty  'set and forget', whereas updating is a constant challenge. I've installed Ubuntu in the server-mode, and that seems to speed up a lot of things.
Still, I'd like to see a little more bleeding edge in Ubuntu. On Windows, I'ver run MySQL 4.1 for some time now, but on Ubuntu, it took some effort to even get it installed. Same goes for PHP5 (it's been around long enough, it should be in the standard repositories).
@Xolox: I'll give SWAT a try, though samba is lower on my list, first I want http and e-mail services up and running (hence the mysql and php question). 

Thanks again,
Farao

---

