---
title: "A specific implementation of integration with Active Directory"
date: 2009-03-06
forum: Server Platforms
---

### Post by nosnetrom on 2009-03-06
Hello all, a Linux n00b here, hoping someone can enlighten me.  I'm building our company's intranet Web server with 8.10 Server, Apache 2, MySQL 5, etc. ...  I'm seeing a need to install a wiki, and I'm wondering how to do so while integrating authentication to that wiki with our Active Directory.

I see that the MediaWiki engine has some posted solutions on integrating with AD.  Am I right in assuming that I should follow the instructions for integrating at the MediaWiki level, or should I try to integrate with AD at the Apache level?  Or even at the server level?  (Also, if you have any recommendations on other wiki engines, I'm still open at this point.)

As you might guess, I have more questions than answers at this point.  TIA for your assistance!

---

### Post by koenn on 2009-03-07
It always amazes me how people admit to being Linux noobs/newbies/novices/... and then set out to set up coorporate servers without preparation and having to resort to anonymous volunteers on a web forum to get things sorted.

But anyway ...

AD integration "at the server level" is meaningless unless you're planning to have users log in to the server itself (remote shells, remote X, remote desktops, ...). 

The users will use the intranet through your web server, so that's where you're authenticate. Whether it's apache or your wiki who needs to handle this, depends on what your plan is. If only your wiki is subject to user authentication, you can let your wiki handle it. If the entire intranet is subject to user authentication, you probably want to do apache with LDAP, but you'd have to find out to what extend apache's authentication covers your wiki user management needs. Once you know this, you can go find out if apache will allow you to do this at the wiki-level. 

Which brings us to the next question: what do you want user authentication for, wiki-wise ?
Do you just want to allow access to selected users ?  Do you only want to identify the users so you can see who edited what ? Do you want to implement access control to grant read or write access to specific users ? groups ? to the whole wiki or designated parts ?

Depending on the answer to that last question, mediawiki might be the wrong choice, because it's designed to be extremely open : you can manage write access, but restricting read access can be a pain.

I happen to be doing some research because I'm thinking about setting up a corporate wiki myself, and I found dokuwiki a good candidate for the case I have in mind. 

here are my notes : 
mediawiki : [http://users.telenet.be/mydotcom/howto/linux/wikiconf.htm](http://users.telenet.be/mydotcom/howto/linux/wikiconf.htm)
dokuwiki : [http://users.telenet.be/mydotcom/howto/linux/dokuwiki.htm](http://users.telenet.be/mydotcom/howto/linux/dokuwiki.htm)

Dokuwiki can authenticate users against an LDAP DS, including AD : [http://www.dokuwiki.org/auth:ldap](http://www.dokuwiki.org/auth:ldap)

---

