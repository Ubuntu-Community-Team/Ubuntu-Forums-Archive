---
title: "Hardy Heron - Ruby On Rails install and Wifi Issues"
date: 2008-09-05
forum: Server Platforms
---

### Post by MasterMaxus on 2008-09-05
Hi All,

Two questions firstly, what is the proper way to install Ruby On Rails? I have seen several articles via Google and I'm not sure which the right way is?

These all seem to do it slightly differently:

[http://www.rubyhead.com/2008/04/25/installing-ruby-rails-on-ubuntu-804-hardy-heron/](http://www.rubyhead.com/2008/04/25/installing-ruby-rails-on-ubuntu-804-hardy-heron/)

[http://www.urbanpuddle.com/articles/2008/04/28/install-ruby-on-rails-hardy-heron](http://www.urbanpuddle.com/articles/2008/04/28/install-ruby-on-rails-hardy-heron)

[http://nicktarc.wordpress.com/2008/08/30/installing-ruby-on-rails-ubuntu-804-hardy-heron/](http://nicktarc.wordpress.com/2008/08/30/installing-ruby-on-rails-ubuntu-804-hardy-heron/)

The other issue, I have configured my wifi connection but when the server reboots the wifi doesn't connect, I have seen a few dodgy ways to get it going eg editing the rc files is there a proper way to bring the interface up?

Thanks
M

---

### Post by forger on 2008-09-05
For ruby on rails, I believe the first link will give you everything you need.
Note: You can skip "Step 1", dependencies are handled properly if you just type:
```
sudo apt-get install rails
```

Note 2: Not sure about this, but you might need setting up mysql as well

---

