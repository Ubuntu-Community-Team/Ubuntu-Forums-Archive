---
title: "How to access virtual host by IP"
date: 2016-06-05
forum: Server Platforms
---

### Post by fernandoch on 2016-06-05
Hello,

I have a server with many apache virtual hosts.

I'd like to create a new fresh wordpress.

How can I access that new installation folder via web to make the installation?

Thanks

---

### Post by einom on 2016-06-06
hello 

show the output of this command:

sudo apachectl -S | grep DocumentRoot

---

### Post by fernandoch on 2016-06-06
It says 

Syntax OK

---

### Post by einom on 2016-06-06
it must show something like 

Main DocumentRoot: "/var/www"

that is the route to place the main directories to load from wrobser.

---

### Post by fernandoch on 2016-06-06
It is not showing with that command, but I have like 10 different document roots.

I want to have access to a new one without a domain though...

---

### Post by darkod on 2016-06-06
So who created those 10 different virtual hosts (sites)? You? If you did, what is the problem creating a new one?

I don't know how wordpress works in details but basically you will need new virtual host (or an existing one), and then simply go to the document root using ssh session and install wordpress. If I'm not mistaken you finish off the install using the GUI after that.

---

### Post by fernandoch on 2016-06-06
I did, but they had a domain.

Now I need to create a fresh wordpress with no domain, to migrate an old server to that new server.

The installation is via browser.

---

### Post by darkod on 2016-06-06
But eventually it will have a domain right? Create the new site/server with the domain it needs, but do not switch the public DNS until you have finished the migration. Is that what you want to do?

Just setting a domain name on a site doesn't make it active without correct DNS settings...

---

### Post by fernandoch on 2016-06-06
I create it with the domain it needs, but then how do I access the installer via web?

---

### Post by darkod on 2016-06-06
Make a temp entry in your local hosts file pointing the wanted domain name to the public IP of the new server. That way the browser will open the new server. After that you can delete the entry and switch the public DNS.

---

### Post by fernandoch on 2016-06-06
I will try that, thanks.

---

### Post by volkswagner on 2016-06-06
Wordpress can be picky about migration to a new machine.

Notice Wordpress does not use relative links, it uses the full path to files. If you want to successfully move an install to another machine
you should replicate everything. If you install Wordpress to /home/tommy/wp on your development server, you'll want to do the same
at it's new location. Also if you call it my.wpblog.com on your development server, you'll want to do the same at it's new location.
In other words, you will want to know exactly where the Wordpress will be installed, and do the same for the development site.

As mentioned, you can edit your /etc/hosts and point your development server to the domain name of your Wordpress vhost.  Simply comment
out the line, if you need to go to the live/public site. You'll edit /etc/hosts on your workstation, not the server.

---

