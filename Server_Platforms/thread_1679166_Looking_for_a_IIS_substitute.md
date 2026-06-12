---
title: "Looking for a IIS substitute"
date: 2011-01-31
forum: Server Platforms
---

### Post by spikeon on 2011-01-31
I am setting up an ubuntu server, and i was wondering if there was a program that i could apt-get that would manage my Domain names and create directories and FTP and all that good stuff like IIS does in windows.  While i am fully capable of editing the files and working the server through the terminal, noone else in my office is and if we are to switch to a linux server they will need to be able to work it.  anything will help!
):P

---

### Post by koenn on 2011-01-31
If you want to run a linux server and all your colleagues know is IIS, I suggest you get them some training first. You can't stubtitute knowledge with wizards (although some Windows sysadmins seem to think so)

Also, this is the first time I hear IIS manages domain names. AFAIK, DNS servers do that, not web servers. 

Apache is an excellent web server for Linux, but if you confuse it with DNS etc, you're going to have trouble understanding the documentation.

---

### Post by arrrghhh on 2011-01-31
+1, they'll need training... You can't expect them to pickup such a big change without some prior knowledge transfer.

There's utilities that can help tho, so you're not just editing configuration files - like Webmin.

---

### Post by SeijiSensei on 2011-01-31
Once you've got the site set up and running, there's usually little need to play with the Apache configuration files unless you're adding new virtual hosts.  Of more importance is uploading content to the server.  Samba is the easiest solution for this since you can make the website appear as a mapped drive on Windows desktops.  You'll need to be careful about setting up permissions, though.  Apache runs as the user "www-data" on Ubuntu, so I often add "force user = www-data" and "force group = www-data" to the Samba configuration so Windows users can copy files to the web server and not worry about permissions.

---

### Post by spikeon on 2011-01-31
my bad, what i mean is, to host multiple sites on one computer there is a setup process which basically involves first creating a folder in /var/www/ for the site, editing 2 or 3 files such as the files in /etc/apache2/sites-enabled, setting up vsftp to add a user and give that user access to the specific folder only, etc... i want to know if there is a GUI solution for this process.  I am the only developer in the building.  My boss is older and does not have the ability to learn something this new, and the other person in the department can't wrap their head arround basic php.  i basically need a moron-map for this process.  i know that there are web applications that do this, for instance cPanel does it, but i was hoping there was something that wasn't web-based like webmin, and instead could be accessed via remote desktop connection.

---

### Post by spikeon on 2011-01-31
> **koenn said:**
> If you want to run a linux server and all your colleagues know is IIS, I suggest you get them some training first. You can't stubtitute knowledge with wizards (although some Windows sysadmins seem to think so)

Also, this is the first time I hear IIS manages domain names. AFAIK, DNS servers do that, not web servers. 

Apache is an excellent web server for Linux, but if you confuse it with DNS etc, you're going to have trouble understanding the documentation.
IIS doesn't manage domains per-se, but it does manage what domains the server listens for and how they are handled.

---

### Post by Thirtysixway on 2011-01-31
It's been said again and again, but if you're looking for a GUI something like Webmin might be useful.  It has a 'gui' of sorts, and can make adding users and websites a little easier for people who don't know the command line.

---

### Post by spikeon on 2011-02-01
so nothing that can be accessed via remote desktop?  just a web-panel?  

this makes me saddened!

---

### Post by spynappels on 2011-02-01
Can I ask why? why is there a preference for Remote Desktop? It will use more resources, and the Webmin administration panel can be set up to only listen to LAN traffic if your worry is about outside access to it.

What have I missed here?

---

### Post by HermanAB on 2011-02-01
Basically, you have a choice between Ubuntu with Webmin or OpenSuse with Yast.

---

### Post by arrrghhh on 2011-02-01
> **spikeon said:**
> so nothing that can be accessed via remote desktop?  just a web-panel?  

this makes me saddened!

I guess you could install ubuntu-desktop, but this is overkill... Serious overkill..

Linux does this differently - if there is no graphic environment needed, you can install it without one - and in the case of a webserver, there is no need for a GUI.  It might seem daunting at first, but in the end you'll be much happier.  It'll run better, and come update time there's A LOT less to update.  You can do anything and more from the command line.

Also, as was stated earlier - are the actual configuration settings of the webserver changing frequently?  Usually those things are setup once, and assuming nothing changes with hosting or domains, it doesn't change...

---

### Post by spikeon on 2011-02-01
ok, let me put it this way
we host 120 sites on a windows server, and 30 more on a linux el-cheapo hosting server.  we want to combine.
My boss is used to IIS and MailEnable.  i need to find things that work as fluidly as those programs.

---

### Post by arrrghhh on 2011-02-01
> **spikeon said:**
> ok, let me put it this way
we host 120 sites on a windows server, and 30 more on a linux el-cheapo hosting server.  we want to combine.
My boss is used to IIS and MailEnable.  i need to find things that work as fluidly as those programs.

You're not going to find it.  Windows is not Linux, so they're going to be differences.

You can try try as hard as you can, but if he's stubbornly used to IIS, probably best to stick with IIS.  If he's willing to learn a new way of doing things, then by all means teach him how to work with Apache.

---

### Post by spikeon on 2011-02-01
how hard would it be to write a quick program that would prompt for a domain name, username and password; create a new folder for it, add it to sites-enabled, and create a ftp user and password for it?

---

### Post by lykwydchykyn on 2011-02-01
I wonder if something like syscp might be a better fit here than webmin.  It's in the repository.

[http://www.syscp.org/](http://www.syscp.org/)

---

### Post by lykwydchykyn on 2011-02-01
> **spikeon said:**
> how hard would it be to write a quick program that would prompt for a domain name, username and password; create a new folder for it, add it to sites-enabled, and create a ftp user and password for it?

Sounds pretty trivial, as long as you're happy with default settings on everything.

---

### Post by spikeon on 2011-02-01
OOOOO i likey that one.
webmin is a bit too cluttered and clunky for my tastes, but this one i can stand!
I will try it on my dev server immediately.

---

### Post by spikeon on 2011-02-01
If i allready had apache setup and running, should i remove it before installing this?  because all of the domains i setup with this point to the main /var/www/ that the server has set in /etc/apache2/sites-enabled/

---

### Post by arrrghhh on 2011-02-01
> **spikeon said:**
> If i allready had apache setup and running, should i remove it before installing this?  because all of the domains i setup with this point to the main /var/www/ that the server has set in /etc/apache2/sites-enabled/

I'm assuming by "this" you mean syscp.  No, you will not have to remove Apache to install syscp.

---

### Post by spikeon on 2011-02-01
then should i remove the configuration settings that used to be in /etc/apache2/sites-enabled/ ? becuase it's showing whats currently in /var/www/ as it used to (i think i may have set sties enabled to catch all)

---

### Post by lykwydchykyn on 2011-02-01
> **spikeon said:**
> then should i remove the configuration settings that used to be in /etc/apache2/sites-enabled/ ? becuase it's showing whats currently in /var/www/ as it used to (i think i may have set sties enabled to catch all)

Keeping in mind that I haven't much used syscp (just saw it in the repos once and it looked nice), I'd suggest disabling the default site definition, or changing the syscp configuration to put virtual domains somewhere else (don't ask me how, but I'd bet a cup of coffee it's an option somewhere).  I don't know how apache handles having conflicting site definitions, but I'm guessing it's not pretty.

---

### Post by rudelgurke on 2011-02-01
SysCP ? Really ?

[http://wiki.syscp.org/contrib/cryptedmailpasswords](http://wiki.syscp.org/contrib/cryptedmailpasswords)

"... continue to write plaintext passwords ..."

For sure a good idea to encrypt passwords just to write them in the next column in plaintext.

Nah - throw it - don't use.

And - unlike recommended - do NOT install Samba on a webserver. Samba is a fileserver daemon, such things must not be used on a webserver.
Also using www-data etc. - hope you use Suexec when running various Vhosts so this enforce users directive won't do much.

Generally - maybe Uniformserver, Cpanel or a similar solution can do the job. Still this all needs time and may cost money - yes, Linux is free, but not free as in beer ;)

---

### Post by spikeon on 2011-02-01
uniform server is for windows....
and cpanel is a paid program.

i am honestly shocked that there is no GUI for apache that can be accessed non web-based.  this seems like something that would've been with apache from the start.

---

### Post by rudelgurke on 2011-02-01
So if Webmin is too hard to use and you don't want to pay anything - why was Windows ever a choice ?
Windows isn't free too, specially the Server versions.

You can maybe work-around by setting up user directories and let your users place their files there, still there's no "click and let it do the rest" wizard available for Apache, at least no free one.

Apache was, like a lot of Unix software, developed with the "let it do one job, but that job pretty good" principle in mind while a lot of Windows software is developed like "let it try to do everything, but nothing perfect" (personal opinion of course)

---

### Post by arrrghhh on 2011-02-01
> **spikeon said:**
> uniform server is for windows....
and cpanel is a paid program.

i am honestly shocked that there is no GUI for apache that can be accessed non web-based.  this seems like something that would've been with apache from the start.

Apache does its job extremely well.  Much like rtorrent, it does its job with no GUI necessary.

Those who feel it needs a GUI, need to add onto it - this is how Linux (and UNIX really) does things.  Little packages that do their one job well - extremely well in fact.  Then you put all the pieces together to have a distro.  Remember, Linux is not Windows...

Sorry, basically restated what was said above... but it's true!

---

### Post by SeijiSensei on 2011-02-01
Most *nix server software is designed to be run from the command prompt and use text-based configuration files.  I can name a long list of major server programs that have no GUI whatsoever.

> My boss is used to IIS and MailEnable. i need to find things that work as fluidly as those programs.

I don't know what "fluidly" means in the context of server configuration, but I think you all should just stick to IIS.  It's what you know, and it doesn't sound like anyone there is especially eager to learn how to manage a server from the command prompt.

It does sound like this is one of those, "say, we should be doing this in Linux," kind of projects.  Linux isn't for everyone.  Sometimes Windows is the right choice.

---

### Post by lykwydchykyn on 2011-02-02
> **spikeon said:**
> uniform server is for windows....
and cpanel is a paid program.

i am honestly shocked that there is no GUI for apache that can be accessed non web-based.  this seems like something that would've been with apache from the start.

There are.  Just not on Ubuntu.  Take a look at Suse, there is a yast module for apache (at least on SLES, don't know about opensuse).  I think redhat may also have something like that, but I don't know for sure.

Ubuntu server has never really been a "configure your server with a simple GUI" kind of distro, ironically enough.

---

### Post by spikeon on 2011-02-02
ugh, i've only recently started using linux and chose ubuntu.  i'm quite a few levels away from being able to re-class, as ubuntu still confuses the living **** out of me, but if the few things i DO know how to do change, then i'd just give up...

Do you think there'd be a way to re-package that gui for ubuntu?

---

### Post by arrrghhh on 2011-02-02
> **spikeon said:**
> ugh, i've only recently started using linux and chose ubuntu.  i'm quite a few levels away from being able to re-class, as ubuntu still confuses the living **** out of me, but if the few things i DO know how to do change, then i'd just give up...

Do you think there'd be a way to re-package that gui for ubuntu?

No, even if it was doable, probably not even close to being worth the effort.

Honestly, it sounds like your company would be better off sticking with IIS.  Don't try to fit a round peg into a square hole... I love Linux, but it's not for everyone.

---

### Post by Don Barzini on 2011-02-03
> **spikeon said:**
> ugh, i've only recently started using linux and chose ubuntu.  i'm quite a few levels away from being able to re-class, as ubuntu still confuses the living **** out of me, but if the few things i DO know how to do change, then i'd just give up...

Do you think there'd be a way to re-package that gui for ubuntu?

I think for your purposes.... you might want to take a look at ClearOS.


[http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)

---

### Post by lykwydchykyn on 2011-02-03
> **spikeon said:**
> ugh, i've only recently started using linux and chose ubuntu.  i'm quite a few levels away from being able to re-class, as ubuntu still confuses the living **** out of me, but if the few things i DO know how to do change, then i'd just give up...

Do you think there'd be a way to re-package that gui for ubuntu?
Yast is pretty well tied in to Suse.  I don't think anyone has ported it to another distro family.

It's not that hard to switch over to Suse (though I'm not a big fan, having to wrangle with SLES machines at work), especially if you prefer doing things the (non-web) GUI way.  I can understand wanting to stick to the distro you know, but sometimes you have to accept that it's the wrong one for the job.

Since someone mentioned ClearOS (which is very slick, but based on CentOS), another option (that I'm less familiar with) is Zentyal, which installs on top of Ubuntu server.  It's another web admin panel, but cleaner looking than webmin.  Don't know why I didn't think of it before.

---

