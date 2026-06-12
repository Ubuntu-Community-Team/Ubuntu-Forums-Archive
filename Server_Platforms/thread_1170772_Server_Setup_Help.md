---
title: "Server Setup Help"
date: 2009-05-26
forum: Server Platforms
---

### Post by fuzzman54 on 2009-05-26
I followed this guide: [http://www.instructables.com/id/Set-up-your-very-own-Web-server/](http://www.instructables.com/id/Set-up-your-very-own-Web-server/)

and this one: [http://rimuhosting.com/support/bindviawebmin.jsp](http://rimuhosting.com/support/bindviawebmin.jsp)

and I installed webmin and I'm trying to install virtualmin but when I check the configuration I get the following errors:

>  
[LIST]
[*]BIND DNS server is installed, and the system is configured to use it. However, the default master DNS server beast is not a fully qualified domain name. 
A problem was found with your Postfix virtual maps : No map sources were found in the [Postfix configuration]("https://99.23.126.237:10000/postfix/")
[/LIST]
  **[COLOR=#ff0000].. your system is not ready for use by Virtualmin.[/COLOR]**  
  

I'm a complete n00b to all of this, so I don't know what to check, what I've done wrong, or anything at all really.. I'm trying to set the server up so that it has a virtualmin panel that my friend can use like he signed up for a host with cpanel, with full support for email,ftp,mysql and everything. 

I tried setting up the nameservers to the domain that I got from Godaddy and had the catch 22 problem and called the tech support and have them registered and they're in the propagation period. 

I apologize for the lack of information to help you help me, but I don't know where to get anything or what is even needed. If you'd like to take a look at everything for yourself (webmin, my router) just send me a pm and I'll give you the information. Or if you'd like me to give you more information, just tell me what and how to get it. 

So yeah... HELP!

edit: just a question. Could the first error be from when I chose the server's name during the installation and set it to beast when I was actually supposed to set it to the ip of the server?

---

### Post by uzi09 on 2009-05-27
Hey,

I was just going at this myself. The first error you'll hit is the BIND DNS server one. The error was a bit confusing for me as well, but all it's trying to say is to uncheck the BIND option on the previous page (just before you hit save).

Since I didn't have any mail servers installed either, I got an error about that as well, and so had to uncheck that too.

The next couple told me that I needed to install the following packages & enable them from Apache's module configuration page.
[LIST]
[*]mod_suexec
[*]mod_actions
[/LIST]

Once that was done as well, the real kicker was this error:
```

Failed to save enabled features : The Suexec command on your system is configured to only run scripts under /var/www, but the Virtualmin base directory is /home. CGI and PHP scripts run as domain owners will not be executed

```
Because I installed Webmin from apt-get since I already had my apache server preinstalled, the suexec module for apache was already precompiled to be set for the /var/www directory.
Unfortunately, my two options now are to either:
[LIST]
[*]recompile apache - which I don't have the time to spend on
[*]have a fresh install and run the install.sh script provided on the [Virtualmin page]("http://www.webmin.com/vinstall.html") - also no can do since I don't have a fresh install (nor is 8.10 listed in the supported systems list of the script).
[/LIST]
Any help is appreciated :)

---

### Post by Francewhoa on 2009-06-29
I wrote a how-to handbook at [http://ubuntuforums.org/showthread.php?t=1197883](http://ubuntuforums.org/showthread.php?t=1197883)
It covers installing Virtualmin, Webmin & Usermin.

---

### Post by uzi09 on 2009-06-30
Looks like you put a lot of hard work into that. Thanks for sharing.
I did realize that you could do it with the install script relatively easily, however in my situation, I already had a LAMP pre-installed. 

Any ideas how to overcome the above mentioned error?

---

