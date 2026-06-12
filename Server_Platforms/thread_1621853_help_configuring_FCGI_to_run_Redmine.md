---
title: "help configuring FCGI to run Redmine"
date: 2010-11-14
forum: Server Platforms
---

### Post by NathanScrivener on 2010-11-14
Hi, I am new to server administration, so please forgive me if this comes across stupid. I have installed Redmine according to the instructions on [[[http://www.redmine.org/wiki/1/HowTo_Install_Redmine_in_Ubuntu]]](http://www.redmine.org/wiki/1/HowTo_Install_Redmine_in_Ubuntu]]), according to the mod_cgi instructions which seem to be the easiest to follow.

The script installed in the installation directory was called 'dispatch.fcgi', and not parsing when I visited the page through the browser, just displaying the contents of the script. OK, so I installed the apache mod libapache2-mod-fastcgi using apt-get. Then 'a2enmod fcgid' followed by an apache restart.

Now when I visit the Redmine folder through the web browser I get 'Forbidden You don't have permission to access /redmine/dispatch.fcgi on this server.'

I checked to ensure www-data owns all files and has correct permissions to the folder. But this doesn't seem to work. Would somebody advise how to get around this issue, if they have some ideas?

Thanks

---

### Post by James78 on 2010-11-14
I recommend you use the Apache module passenger-phusion instead of fcgi. It's a much better solution. It's what I'm currently doing for my website.

---

### Post by NathanScrivener on 2010-11-14
Thanks, is there a package in the Ubuntu 10.04 repositories? If so, what is its name? If there isn't, I'll definitely give it a miss.

In the meantime, if anyone else can answer my question re FCGI, I'd be grateful. I don't need the fastest implementation, the simplest is what I need.

Cheers

---

### Post by James78 on 2010-11-14
I think passenger is actually simpler lol, and still faster.

The package is libapache2-mod-passenger, and for setting things up, just install it, make the default directory /public_html/public, go to config/environment.rb, then uncomment ENV['RAILS_ENV'] ||= 'production' and copy dispatch.rb.example to dispatch.rb. [RedmineInstall]("http://www.redmine.org/wiki/1/RedmineInstall") still needs to be done of course. As far as I can remember, that's pretty much it. Not just simple, but since it runs Ruby on Rails natively, it's better.

My steps may be incomplete, but I think they're complete as far as I can think of, minus the Apache VHost configuration and maybe file permissions (check the link for those)

[http://www.redmine.org/wiki/1/HowTo_Install_Redmine_on_Debian_with_Ruby-on-Rails_and_Apache2-Passenger](http://www.redmine.org/wiki/1/HowTo_Install_Redmine_on_Debian_with_Ruby-on-Rails_and_Apache2-Passenger)

As per your fcgi error though, it's likely you just haven't setup your VHost correctly.

---

