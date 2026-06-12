---
title: "Hosting a site for the first time. What security precautions to take?"
date: 2014-12-23
forum: Security
---

### Post by Wiking on 2014-12-23
I am building a website and will upload to the server soon. 

I've never hosted a site before so I would like to know what security issues I should be aware of.

I'll be using wordpress as the cms, and will have various social plugins. I'm leaning towards hosting on hostgator.

I'm in a programming course in college so I should be good with scripts and any back-end stuff. I would just like to know of any vulnerabilities or precautions that I should take care of before I go online.

I know it would be hard to diagnose without looking at my site, but just in general, any good practices to make my site more hack proof.

thanks

---

### Post by slickymaster on 2014-12-23
*Moved to the ***Security*** sub-forum*

---

### Post by kpatz on 2014-12-23
Are you running on shared hosting, dedicated, or VPS (virtual private server)?  The steps for securing things differ for these, and the shared hosting is simplest since you don't have to worry about securing the server itself, only your site.

For Wordpress, don't name your administrative account "admin".  Hackers often try to brute-force this account.  Give it a username only you know and a strong password.

You'll need some sort of anti-spam add-in as the most retarded of spammers always target Wordpress sites.  If you're installing Wordpress yourself or have access to the .php files, you can install ZB Block (from spambotsecurity.com) to keep some of the riffraff out.

Securing a dedicated or VPS server is a bit more involved, and reading up in the Security forum here will give you some ideas of what needs to be done.

---

### Post by Wiking on 2014-12-23
> **kpatz said:**
> Are you running on shared hosting, dedicated, or VPS (virtual private server)?

The package and company I'm considering would use shared hosting.

> 
You'll need some sort of anti-spam add-in as the most retarded of spammers always target Wordpress sites.  If you're installing Wordpress yourself or have access to the .php files, you can install ZB Block (from spambotsecurity.com) to keep some of the riffraff out.

What kind of spam are we talking about? Spamming comments and forms? Would Joomla be a better option for future sites taking into consideration spamming?

---

### Post by kpatz on 2014-12-23
I don't know anything about Joomla, but spammers will abuse anything that allows stuff to be posted--blogs/comments, forums, etc.

At the very least, you'll want to make it so only you (and any other person you want to allow) can post actual blogs, and allow comments by everyone but have them be moderated, so you have to approve them before they'll appear.  You'll soon find yourself deleting spam comment after spam comment but at least they won't be seen by your viewers.  Or, just disable comments entirely if you don't want people to post them at all.  That'll stop the spam cold.

---

### Post by Habitual on 2014-12-23
[http://codex.wordpress.org/Hardening_WordPress](http://codex.wordpress.org/Hardening_WordPress)

---

### Post by sandyd on 2014-12-24
> **Wiking said:**
> The package and company I'm considering would use shared hosting.



What kind of spam are we talking about? Spamming comments and forms? Would Joomla be a better option for future sites taking into consideration spamming?

Implement some kind of spam blocking (akismet/etc), or use an comment system (e.x. Disqus, livefyre,etc) that has advanced comment spam blocking and flagging. You can then set the comment system to require moderator approval before comments are posted. Disqus/etc should send you an email indicating that there are comments waiting to be reviewed.

The most danger comes from not Wordpress, but its wordpress plugins. There are thousands of wordpress plugins out there are insecure, and are a target for hackers. Even plugins that are popular, such as Mailpoet [have been the target of hackers]("http://support.mailpoet.com/knowledgebase/site-hacked-what-to-do/"). It is important to keep Wordpress and its plugins up to date, and to replace plugins that are no longer maintained. Keeping backups is also essential in order to have something to restore to after the site has been hacked.

Secondly, use some kind of brute force protection on your wp-login/admin area so that users will be logged out after a number of incorrect password attempts.

---

### Post by HermanAB on 2015-03-14
Make sure that all users have loooooooooong passwords and backup your data.

---

### Post by open2reason on 2015-03-14
Some thoughts on length and the complexity of passwords / passphrases via Stanford IT department and Arstechnica [http://arstechnica.com/security/2014/04/stanfords-password-policy-shuns-one-size-fits-all-security/](http://arstechnica.com/security/2014/04/stanfords-password-policy-shuns-one-size-fits-all-security/). A lot may depend upon constraints placed upon you by the software you are using.

---

### Post by bashiergui on 2015-03-14
Plan on your site getting taken over by hackers. Have good, frequent full backups so that you can reformat and reinstall when it happens. 

Apply updates ASAFP. Wordpress is highly targeted by attackers. Give them fewer vulnerabilities to work with.

Also have good backups.

The link above to harden Wordpress is a start.

And have good backups. You won't if you're like the vast majority of WP site operators.

---

