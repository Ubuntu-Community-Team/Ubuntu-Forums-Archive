---
title: "How  does ruby on rails work?"
date: 2011-10-18
forum: Server Platforms
---

### Post by daled on 2011-10-18
I'm a php developer trying to set up a ruby on rails environment to try it out.  After hours of trying I simply can't.

I can create rb files and run them using [FONT=Courier New]ruby filename[/FONT], but I can't get rb files to run in Apache.  Passenger is installed.

I have a file test.rb in apache's DocumentRoot, but when i try to access it through the web browser, the browser wants to download it.  It seems that apache doesn't want to execute the file.  Do .rb files work like .php files or am I completely off here?

So what I'm asking is what the hell is the difference between how LAMP and LAM-ROR work? and how can i get ROR to work with apache and passenger?

:edit:
I've gotten something "working", but it's an error message.  this can be seen here: [http://ruby.enhatchortho.com/ror/]("http://ruby.enhatchortho.com/ror")

Here is the apache virtual host configuration:
        [FONT=Courier New]ServerName ruby.enhatchortho.com
        DocumentRoot /var/www/

        <Directory /var/www/>
                Options Indexes FollowSymLinks -MultiViews
                AllowOverride all
                Order allow,deny
                allow from all
        </Directory>

        RailsBaseURI /ror
        <Directory /var/www/ror>
                Options -MultiViews
        </Directory>[/FONT]

It seems like its looking for /var/www/config/environment.rb instead of /var/www/ror/config/environment.rb  Can someone shed some light on this?

---

### Post by vasile002 on 2011-10-18
Change the last lines of you apache config to this:
```

[FONT=Courier New]<Directory /var/www/ror>
[/FONT][FONT=Courier New]RailsBaseURI /ror[/FONT]
[FONT=Courier New]                 Options -MultiViews
        </Directory>

```

Move the RaisBaseURI inside the Directory clause


[/FONT]

---

### Post by daled on 2011-10-18
I appreciate the response.  Unfortunately I still get the same error message with the modified apache conf

---

### Post by rubylaser on 2011-10-18
Ruby on Rails is a framework that adds a bunch of helper methods to standard Ruby.  The standard view file would be like this index.html.erb.  If you really want to understand Rails, [Agile Development with Rails (3rd edition)]("http://pragprog.com/book/rails3/agile-web-development-with-rails") is a great place to start (I learned on the first edition and it was a great intro to Rails).  Just like you didn't learn PHP by randomly typing things in and hoping that they work, you'll need to read and understand Rails and Ruby before you'll be able to create something from scratch.

Have you looked at any of the [Docs]("http://rubyonrails.org/documentation") or [Getting Started with Rails]("http://guides.rubyonrails.org/getting_started.html")?

P.S. Passenger expects a Rails application and what you have isn't that. You don't want to use Passenger for development.  It's for a Production, deployed application.  For development, you'd just use Webrick or Mongrel. 

You'd need to setup ruby, rubygems, and install rails.  Then you'd create your first Rails app like this...
```
rails new myapp
```

You'll end up with a standard Rails app with scaffolding already in place.  You'd then cd into that directory and start your development site up with Webrick
```
rails s
```

You're application would then be available on [http://localhost:3000](http://localhost:3000) or [http://your_ip:3000](http://your_ip:3000)

---

### Post by daled on 2011-10-18
Thanks for the rails overview. I looked at those docs and followed the getting started guide to set up a rails app. I'll have to look into that book. Thanks for the suggestion.
 
edit
thanks for the insight on passenger. Another thing to try. Hope it works.

---

