---
title: "ruby on rails"
date: 2012-05-06
forum: Server Platforms
---

### Post by oren tal on 2012-05-06
Hi,

If I have an ubuntu server that already including php, apache and mysql and I want to add ruby on rails.

can I do it without removing the php?

do you know about good tutorials about ruby on rails on ubuntu server?
I have found tutorials but since I am using ubuntu server I think it will be easier for me to learn for a tutorial that is directed to ubuntu server?

anyway if I want to add ruby on rial to a server that already include php, what should I do?

---

### Post by A2llex on 2012-05-06
> **oren tal said:**
> Hi,

If I have an ubuntu server that already including php, apache and mysql and I want to add ruby on rails.

can I do it without removing the php?

do you know about good tutorials about ruby on rails on ubuntu server?
I have found tutorials but since I am using ubuntu server I think it will be easier for me to learn for a tutorial that is directed to ubuntu server?

anyway if I want to add ruby on rial to a server that already include php, what should I do?


of u can, PHP has nothing to do with RUBY.
If you want to run a RoR app, just create a new vhost and add /edit these directives as follows:

```

<Directory /var/www/RoR/public>
                Options Indexes FollowSymLinks MultiViews ExecCGI
                AllowOverride All
                Order allow,deny
                allow from all
                AddHandler cgi-script .cgi
</Directory>
```

---

### Post by rubylaser on 2012-05-06
I'd suggest you use Passenger Phusion with Apache (or Nginx).  Here's pretty [good directions]("http://coding.smashingmagazine.com/2011/06/28/setup-a-ubuntu-vps-for-hosting-ruby-on-rails-applications-2/") to get you running. An Apache Passenger vhost entry can be as simple as this.
```

<VirtualHost *:80>
  ServerName www.domain.com
  DocumentRoot /var/www/website/public/
</VirtualHost>

```

Also, if you're trying to learn Rails, this is a [good place to start]("http://ruby.railstutorial.org/ruby-on-rails-tutorial-book").  It covers all of the aspects of getting started developing in Rails correctly.

---

### Post by A2llex on 2012-05-07
> **rubylaser said:**
> I'd suggest you use Passenger Phusion with Apache (or Nginx).  Here's pretty [good directions]("http://coding.smashingmagazine.com/2011/06/28/setup-a-ubuntu-vps-for-hosting-ruby-on-rails-applications-2/") to get you running. An Apache Passenger vhost entry can be as simple as this.
```

<VirtualHost *:80>
  ServerName www.domain.com
  DocumentRoot /var/www/website/public/
</VirtualHost>

```Also, if you're trying to learn Rails, this is a [good place to start]("http://ruby.railstutorial.org/ruby-on-rails-tutorial-book").  It covers all of the aspects of getting started developing in Rails correctly.


i think Passenger is more slowly solution.

---

### Post by rubylaser on 2012-05-07
Based on what?  That's just not true.  Passenger is capable of handling very large work loads when coupled with Ruby Enterprise Edition.  If you want the ultimate in speed, you shouldn't be using Apache for Rails anyways.  You'd want to use Nginx + Unicorn, but that can be a little complicated for someone to get started developing on Rails.  Passenger Phusion is dead simple and still quick enough for most work loads.

---

