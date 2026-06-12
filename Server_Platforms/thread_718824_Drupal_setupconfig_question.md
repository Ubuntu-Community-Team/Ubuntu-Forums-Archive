---
title: "Drupal setup/config question"
date: 2008-03-08
forum: Server Platforms
---

### Post by Stochastic on 2008-03-08
Hi, I've built a site using drupal on my personal (ubuntu) server and am looking to transfer the site to my school's server but I'm not terribly fluent with drupal and am looking for some help.

The webmaster for my school's servers explained this much to me but then said any further details are Drupal specific and they don't give technical support for Drupal.  So I'm wondering if anyone can help me determine which files need this header 
> The server currently only supports "CGI" mode. Drupal is
written to expect a 
server using the "mod_php" module for the web server: that means that you 
have to do some 
digging around in Drupal (and similar applications) to add the line
"#!/usr/local/bin/php" to 
the start of most of the .php files that ship with Drupal in order to
make them executable. If 
you've not done this before: it can be a bit tricky because it's only the 
directly executable 
files in Drupal that would need to have that line added. If you add that
line to say, an 
included module, then you'll see that line displayed on the page,
probably multiple times. If 
you're not really familiar with the application you're installing, this
can be a bit of a slow 
process. 

So my question is which files in Drupal 6.0 are the directly executable files?  Thanks.

---

