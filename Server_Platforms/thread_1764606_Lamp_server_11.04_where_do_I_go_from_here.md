---
title: "Lamp server 11.04 where do I go from here?"
date: 2011-05-21
forum: Server Platforms
---

### Post by RadarG on 2011-05-21
Hello, I need somebody to point me in the right direction. Below is what I have done up to this point

ubuntu server LAMP 11.04 installed in VM
openssh (putty good)
phpmyadmin installed
apache2 website test is good. I can get to "it works page"

I need to know where I should go from here to accomplish my goals. Maybe it would help if somebody can help me break it down into smaller steps.

I need the following;
create user logon/access and account creation plus verification emails

users will need to be able select choices from multiple drop down menus. Inputs selected by users need to be stored in an mysql db. Any recommendations for books,links, or howtos videos will be most welcome. Thanks

V/r
RadarG

---

### Post by Blasphemist on 2011-05-21
I don't know the full set of needs and requirements that you have from your post but what I use as a cms to create what you describe is Drupal 7. [http://drupal.org/documentation/install](http://drupal.org/documentation/install)

A basic Drupal site isn't real hard to set up but it can get quite complex. An easy way to get a feel is to set up a very quick site on drupal gardens. [http://www.drupalgardens.com/](http://www.drupalgardens.com/)

If you want to do this without a cms, you are better than I am for sure.

---

### Post by RadarG on 2011-05-22
cms ??? what is cms? Are they modules? I was looking into drupal but I wasnt sure if it was right for me. What are the pros and cons?

---

### Post by Lars Noodén on 2011-05-22
> **RadarG said:**
> cms ??? what is cms? Are they modules? I was looking into drupal but I wasnt sure if it was right for me. What are the pros and cons?

CMS is a Content Management System.  They are programs or suites of programs to help manage site users and publication of site content.  There are a lot of options out there and they are all good but some might fit your needs better than others.  That is really hard to figure out in advance. The best you can do is find some sites using each one and see if you can spot the differences.  

In addition to Drupal, there are [Joomla](http://www.joomla.org/), [Plone](http://plone.org/), [Lenya](http://lenya.apache.org/), [OpenCMS](http://www.opencms.org/), [WordPress](http://wordpress.org/) and many others.

---

### Post by Blasphemist on 2011-05-22
Sorry, I made an assumption there about using the term cms. Can you more fully describe your idea to us? I'm curious about what hosting plan you have. Do you plan to use a free host? WordPress and Drupal Gardens both would allow you have a cms and yet use free hosting. You wouldn't even have to pay for a domain. If you plan to host this yourself, what domain plans do you have? How much use do you plan? Is the main thing to perform a service/meet a need? Or is to learn?

---

### Post by RadarG on 2011-05-22
> **Blasphemist said:**
> Sorry, I made an assumption there about using the term cms. Can you more fully describe your idea to us? I'm curious about what hosting plan you have. Do you plan to use a free host? WordPress and Drupal Gardens both would allow you have a cms and yet use free hosting. You wouldn't even have to pay for a domain. If you plan to host this yourself, what domain plans do you have? How much use do you plan? Is the main thing to perform a service/meet a need? Or is to learn?

I don't have a hosting plan. I'm running the server from a VM using virtualbox. Eventually I'll set up a ESX server and host it myself after I get the bugs worked out using a business connection. My end goal is to have this in production in 1-2 years from now, after I work out all the bugs. I don't want to buy a domain name and web host until I have my project up and running. My goal is that I would like users to be able to logon using accounts and also anonymously and input data into a mysql db using the web,android, and through itunes.

---

### Post by Blasphemist on 2011-05-23
This may be of interest to you then. [http://drupal.org/project/quickstart](http://drupal.org/project/quickstart)

Your approach really depends on just how good you plan to get by the time you go live, in my opinion. An easy end of the scale way to do this would be to use drupal gardens and when you are solid with the site from using it's base, you could export the site to hosted. The harder way but one that ends up with you being more skilled is to do things more hands on. Quickstart is in between.

This explains creating a multi-site development environment for Drupal on Linux. This would be a good environment to use for learning enough to stage and create what you want. It would also guide you to practices that some people who know more than us have already learned.
[http://drupal.org/node/823990](http://drupal.org/node/823990)

This link is written for 10.10 but really not much changes for 11.04 and in using it you see what someone professional uses and you'll learn from the doing.
[http://vmirgorod.name/11/1/20/drupal-development-environment-based-ubuntu-1010](http://vmirgorod.name/11/1/20/drupal-development-environment-based-ubuntu-1010)

---

