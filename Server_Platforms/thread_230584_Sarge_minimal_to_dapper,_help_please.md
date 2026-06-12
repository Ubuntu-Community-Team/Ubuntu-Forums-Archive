---
title: "Sarge minimal to dapper, help please"
date: 2006-08-06
forum: Server Platforms
---

### Post by jimcooncat on 2006-08-06
I'm renting a new UML instance from an online hosting provider I've been using for years. It's the kind that comes with a choice of distributions and root access. With this new instance, I want to run a web server with lighttpd and django.

I'm not looking for advice on the applications, but on the os environment.

So I was given a choice between a very minimal sarge install, or a full dapper install with gnome and everything in ubuntu-desktop. Since I'll be running a web server, I don't care to have all the x.org stuff installed and gain back some space -- even though gdm or startx are not run on init.

I could not find a simple way to bring back the dapper install back down to a minimal ubuntu system. This would be my preference, so if someone knows an apt-get command to do that, please let me know! 

So I took the minimal sarge, changed the repositories to ubuntu ones, and dist-upgraded. That worked nicely, but I still don't have quite the enviroment I expected. [SIZE="1"]*For instance, sudo isn't installed. I went to install it and received an "Untrusted packages" notice. Maybe I just need to install the GPG keys? -- solved*[/SIZE]

To get to the "Ubuntu Server" environment, is there a simple meta-package I should install? ubuntu-minimal?

Also, I did a netstat -ta, and see that time, discard, daytime, smtp, and ssh are listening, though I can't figure if they're listening to localhost or the network. I must not have the correct command.

Once I've closed the listening ports I don't want, install the software I do want, I'll just end up with port 80 and 443 (and some other port for sshd) listening to the outside. This instance will not be protecting other computers, is configuring iptables necessary or advised? I don't want to make more work for myself if it doesn't add security.

I will continue to work on these issues and not leave it up to the forums to do my work for me, but if you have a quick answer to any one of these, won't you please jot a reply?

---

### Post by isharra on 2006-08-06
Note: I'm new to ubuntu myself. So this is to the best of my knowledge but may not be complete.

Yes, install ubuntu-minimal to ensure you have the minimum packages installed to support working.

You do want a firewall. Take a look at firehol if you don't want to be bothered with a complex iptables setup. (I talked my kid through it on the phone in less than 5 minutes.) It's remarkably easy to set up once you've read the examples on the firehol pages.

After that I'm afraid you need to install any servers manually.

there is a package for lighttpd.
you'll need to install python-dev (for django installation from source) there isn't a django package that i've seen

'sudo apt-get ubuntu-minimal firehol lighttpd python-dev sshd'

---

### Post by jimcooncat on 2006-08-06
Thanks! I'll install ubuntu-minimal. I does have some packages I wasn't sure were applicable to a server (alsa-base) but most they'll do is just take a little disk space.

Firehol was also recommended on the provider's forum. I'm glad you've found it easy to set up. I didn't want to get too deep into networking as I have my hands full with the application I'm developing. So I'll do that.

I knew I'd be doing some manual installation. I'm not sure python-dev has all I need to use FastCGI with lighttpd (flup). And django is just untarring and running a python script.

Yes, it would be really nice if these all were available with apt-get. It would be a very good alternative to LAMP, making database-driving websites easy. And I can understand the configuration files, where it seems every time I do an Apache install, things wind up in different places than last time I did it. I was always ending up with both Apache and Apache2, making for great confusion.

I did give Ruby on Rails a shot, but it was too confusing, and a little scary since I saw a post about gem being possibly incompatible with Debian installations. I'd rather be learning python anyway, since many of the tools in this distro are python-oriented.

---

### Post by isharra on 2006-08-06
Well the biggest advantage to ubuntu-minimal is that it allows for an easy upgrade path. I agree that alsa seems a bit much here but I didn't make up the package. :)

You might look at ubuntu-standard (utility and command line tool meta package) in addition to ubuntu-minimal though you'll end up with packages you don't use.

I use lighttpd with php-cgi myself. So I'm of minimal help getting python going.

firehol is very easy to understand, do make sure you test with an open ssh connection just in case.

A simple example:

edit /etc/firehol/firehol.conf
```
version 5
# the local interface 'lo' is handled automatically
# Accept all client traffic on any interface 
# Change this to specific client applications for tighter security
# but it's easy to forget basic clients like dns and smtp :)
# Accept server traffic for http, https and ssh on any interface
# For good or bad, ping is commonly used by service providers
# to test server uptime so I enable it too.
interface any world
        server "ping http https ssh" accept
        client all accept
```
edit /etc/default/firehol
```
START_FIREHOL=YES
```

/etc/init.d/firehol start

---

### Post by jimcooncat on 2006-08-07
Isharra, for being "new to ubuntu" you sure have a wealth of information! Thanks so much for your help. I had to pay bills this morning, but I'll try the firehol installation if I get a chance at work today. It does look easy to understand.

---

