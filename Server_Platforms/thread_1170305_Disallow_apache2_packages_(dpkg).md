---
title: "Disallow apache2* packages (dpkg?)"
date: 2009-05-26
forum: Server Platforms
---

### Post by Parama on 2009-05-26
Is it possible to completely disallow Apache2* packages on a system (Intrepid and Jaunty servers)? Maybe even get packages with apache2* dependencies to ignore these apache2 packages?
It seems like apache2 comes back every time I install or update PHP packages (e.g. php5-sybase, phpmyadmin, squirrelmail) even after I've uninstalled and purged the apache2* packages. Only way to not get it installed seems to be not to install PHP packages.
The reason is I'm in the process of moving our hosted sites from Apache to Nginx with php-cgi since the performance gains from this move is well worth it and then some. Since I really don't want to go through all this and then still have the Apache2 running taking up ressources I would like it to be gone for good.

---

### Post by LepeKaname on 2009-05-26
As, for example, phpmyadmin depends on "libapache2-mod-php5" and "libapache2-mod-php5" depends on "apache2" I think it would not be possible to prevent it to be installed. Of course you can manually compile each package, but I'm sure that is not what you want...

I agree with you. Somehow those packages must not depend on apache2, because we know that apache2 is not the only php capable web server out there. However, having that dependency helps to facilitate its setup (because it will automatically setup apache2 and deploy the application in the corresponding path).

It would be nice to suggest that to the "Ubuntu Team" so depending of the web server you have installed, a different script should apply for its installation...

---

### Post by Parama on 2009-05-26
> **LepeKaname said:**
> As, for example, phpmyadmin depends on "libapache2-mod-php5" and "libapache2-mod-php5" depends on "apache2" I think it would not be possible to prevent it to be installed. Of course you can manually compile each package, but I'm sure that is not what you want...
Exactly :-) I make an effort to stay as close to a *basic* Ubuntu server installation as possible. But since Apache2 caused performance issues on our reverse proxy cluster some time ago I stumpled upon nginx and now I've made a promise never to go back to Apache so now it's kind of annoying having to deal with it anyway.

> **LepeKaname said:**
> I agree with you. Somehow those packages must not depend on apache2, because we know that apache2 is not the only php capable web server out there. However, having that dependency helps to facilitate its setup (because it will automatically setup apache2 and deploy the application in the corresponding path).

It would be nice to suggest that to the "Ubuntu Team" so depending of the web server you have installed, a different script should apply for its installation...
Yes, that sure would make things easier, but to begin with just untying the dependency knot between PHP and Apache2 would be greatly appreciated. Especially since php-cgi is running as a seperate process tree without any real ties to the webserver itself. On nginx you just tell it to forward requests for .php files to this php-cgi process.

---

### Post by LepeKaname on 2009-05-26
Why don't you add your idea in Ubuntu brainstorm? ([http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/))

I will definitely vote for it!

If you do, please post your link here. :p

---

### Post by SoreGums on 2009-05-26
How do I get "apache2" out of the list of services when I run sysv-rc-conf?

I've long been a non-installed of Apache. I've also been a Gentoo user. The hosting provider doesn't do Gentoo so now I'm learning Ubuntu.

So far I've removed everything to do with apache2 - now I just need to get it out of the services list

Thanks :)

---

### Post by LepeKaname on 2009-05-26
SoreGums:

To disable apache2 to load at the beginning, just chmod 644 or 600 /etc/init.d/apache2 or do as I do, move it to another path like: /etc/manual.d/ in which I put all the services I want to start manually.

---

### Post by SoreGums on 2009-05-26
> **LepeKaname said:**
> SoreGums:

To disable apache2 to load at the beginning, just chmod 644 or 600 /etc/init.d/apache2 or do as I do, move it to another path like: /etc/manual.d/ in which I put all the services I want to start manually.

It is all ready disabled and I've removed the package.
I want it out of the list. If you know how to remove it from the list I'm assuming the same command will get something into the list.

Gentoo has rc-update add <service>
CentOS has chkconfig

What does Ubuntu have?

---

### Post by LepeKaname on 2009-05-26
In ubuntu there is rcconf and bum(graphical) (but they are not installed by default).

To install, Run:

sudo aptitude install rcconf

or

sudo aptitude install bum

the just run "rcconf" or "bum"

In there all the service list will come up and you can activate or deactivate them. 

If you want to get rid of apache2, then use:

sudo aptitude purge apache2

This will remove apache2 and its config files too.

If after doing this, you still see the script in /etc/init.d/apache2
just delete it. 

If you just want to remove the service but not the package, then you can use:

sudo update-rc.d -f apache2 remove

which will remove all the rc.X links too.

To add a new service :

sudo update-rc.d apache2_myscript defaults

---

### Post by SoreGums on 2009-05-26
I've all ready removed everything.

apache2 is showing up in the list that sysv-rc-conf generates.

There are no apache2 files in /etc
That means I have deleted /etc/init.d/apache2

So how do I get apache2 out of the list that is generated by sysv-rc-conf?

Edit: right so sysv-rc-conf has a cache, clear it by using the -P option - apache2 is now totally purged - woohoo!

---

### Post by Parama on 2009-05-27
> **LepeKaname said:**
> Why don't you add your idea in Ubuntu brainstorm? ([http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/))

I will definitely vote for it!

If you do, please post your link here. :p

Here it is: [http://brainstorm.ubuntu.com/idea/20018/](http://brainstorm.ubuntu.com/idea/20018/)
Now go vote ;)

---

### Post by LepeKaname on 2009-05-27
I post my comment there... I will wait until it is available for voting. Good luck!

---

