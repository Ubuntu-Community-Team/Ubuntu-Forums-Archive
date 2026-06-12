---
title: "Apache Running... but doesn't exist?"
date: 2006-04-28
forum: Server Platforms
---

### Post by alcon on 2006-04-28
I'm trying to get a server running ubuntu up on my Mac Mini.  I got sick of trying to run Mac Os X as a server, it kept bugging out on me.  I installed the Ubuntu Breezy Badger power-pc distro and then went about setting up as a server.  I used apt-get install under sudo to download apache2, php5, and mysql.

Everything went find up until mysql.  It would start up after installing.  I got a very weird error.  I went hunting for it on the forums and in google, found out that several other people had gotten it but none of the posts were answered.  Seems that it hasn't been fixed yet and no one had any ideas.

So I scrapped the mysql.  Used apt-get purge to remove it and then installed it from source.  After a false start I got it working.  

Except now php wouldn't talk to it.  Phpmyadmin simply couldn't seem to connect to it, despite the fact that I could with the mysql command.  After searching through user docs I gave up on php and went to reinstall the whole server from source.  I used apt-get purge to remove php and apache2, dled the latest source versions and installed apache2.  After I reinstalled it, I noticed it was still running.  I tried using the newly installed version of apachectl to stop it.  No dice.  Then I tried starting it.  Yep the socket was in use.  I went looking for the old apache files, but they'd all been successfully removed.  So now I seemed to have a version of apache running that didn't exist?  I tried restarting the computer.  The non-existant version of apache restarted with it.  

So ... any hints on tracking this sucker down and finally purging it?  I checked /usr/bin where it was original, there's nothing there with the name apache.  Nor is there in bin nor sbin nor /usr/sbin.  And far as I can tell my newly install apache2 in /usr/local/apache2 isn't running, using apachectl to stop it reports that it isn't running.  Where else might it be?

---

### Post by TreetopClimber on 2006-04-29
there is a full set of directions on this link > [https://www.wiki.ubuntu.com/ApacheMySQLPHP](https://www.wiki.ubuntu.com/ApacheMySQLPHP) < try this

---

