---
title: "Security tip - Don't do this"
date: 2010-03-25
forum: Security
---

### Post by noway2 on 2010-03-25
For all that have a Blackbery and would like to use it to SSH into a remote location, give BBSSH a try.  You can find more about it here: [http://marcparadise.com/articles/tag/bbssh](http://marcparadise.com/articles/tag/bbssh).  From initial appearances it works better than midpSSH.

Now, if you want to use key based authentication you need to use a trick that isn't obvious at first as the generate key button does not work.  You will need to use a separate client to generate a key (ssh-keygen -t rsa -f (filename)).  You will then need to import the private key to the Blackberry.  To do this you need to iport it from an http link, such as a private page on a web server.

I did this earlier today, and then quickly realized that the private key to access my server was just transmitted in plain text across a work network (who knows whose capturing what) - DOH!

So for anyone that is interested in this technique, be sure you use an HTTPS location.  Don't repeat my mistake!

---

