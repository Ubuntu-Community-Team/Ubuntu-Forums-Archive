---
title: "LAMP + Ruby on Rails"
date: 2007-08-12
forum: Server Platforms
---

### Post by Nevon on 2007-08-12
Right, I was trying to add Ruby on Rails to my existing LAMP installation, and failed miserably. I think the installation went fine, but configuring apache to work with Ruby just didn't work. So now I've completely uninstalled everything related to LAMP or Ruby on Rails, and I wanna start over. 
First of all, is it even possible to have a LAMP installation (to me that's Linux, Apache2, Mysql and PHP) working alongside with Ruby on Rails? If so, how? I tried googling, but I could just find guides on how to install either, but never combined. 

I would be a very very happy man if someone could either point me to a tutorial where they do exactly that, or post step by step instructions on at least the installation part.

---

### Post by unixhead on 2007-08-16
I always compile Ruby from source on Ubuntu cause Ubuntu lacks several dependencies.

Follow [this post](http://greenprogrammer.blogspot.com/2006/05/ruby-wreadline-on-ubuntu.html) and [short compilation guide](http://www.rubywizards.com/viewtopic.php?pid=19) to find out how.

But there's an [easier way](http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu) if you are fine with 1.8.4 or 1.8.2 that Dapper/Edgy/ Feisty provide from package repos.

There's one more [post on the subject](http://www.urbanpuddle.com/articles/2007/05/09/install-ruby-on-rails-on-ubuntu-feisty-fawn) I'd found that looks as safe bet.

---

### Post by unixhead on 2007-08-16
Oops. I mean I do compile it from source cause Ubuntu Ruby packages are mess and only Gutsy got 1.8.6 that I prefer.

If you have no such requirement then feel free to use packages.

---

