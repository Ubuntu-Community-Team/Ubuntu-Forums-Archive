---
title: "Web developement access to customer account"
date: 2010-05-20
forum: The Cafe
---

### Post by JMJ_coder on 2010-05-20
So I'm helping someone else build a web site. It is their web hosting account -- so how do I have access to it (say via ssh or the control panel) for uploading, setting up databases, etc.?

---

### Post by samalex on 2010-05-20
Depends on the setup at the host.  If they're using cPanel they can either give you their login or setup a login for you.  You should be able to upload the site and setup the database using it.

If cPanel or another similar app isn't available, then SSH is the best option.  You can use SFTP to send over files and also setup the database via command line.  Honestly this is my preferred way of doing it :-D  Just be sure you have the appropriate passwords for MySQL.

If old-school FTP is the only option, then you're very limited.  Given you have privileges in MySQL you can possibly create a PHP script to setup the database and run it via the web server, but that's cumbersome at best. 

Do you know what host they're using?  

Sam

---

### Post by JMJ_coder on 2010-05-20
> **samalex said:**
> Do you know what host they're using?

Looks like the host will be Webfaction and development using Django and Postgres.

---

### Post by sydbat on 2010-05-20
> **JMJ_coder said:**
> Looks like the host will be Webfaction and development using Django and Postgres.They're not paying you enough...

---

### Post by JMJ_coder on 2010-05-20
> **sydbat said:**
> They're not paying you enough...

Why do you say that?

---

### Post by samalex on 2010-05-20
> Looks like the host will be Webfaction and development using Django and Postgres. 

I've never used either really, though I know a few people who are die hard Postgres users and love it.

The Webfaction does say "Extra SSH and SFTP users - Unlimited" so they should be able to give you an account to get in and do what you need to without them giving you the master account.  So getting in shouldn't be a problem.

The site also says "One click installer for tons of applications including Rails, Django, Drupal, WordPress and a lot more" so I wonder if they are using something like cPanel.  Either way I'd suggest rolling your own Django or whatever because often times these pre-packaged ISP apps don't have the latest versions or security updates.  If you download the latest of whatever canned app you choose, whether it be Django or whatever, you can verify it's the latest and greatest and update it as you see fit without being dependent on the ISP.  

Stepping away from your question for a sec, what type of site will it be - static "here we are" site, e-commmerce site, etc?  Django is more of a framework from what I understand, so you may have more foundation if you ran with something like Joomla or even Wordpress or MediaWiki depending on what the needs are.  Also is this something you'll set-up and pass to them or will you be maintaining the content.  If the former then Joomla can be written to pass off to the client to update with some simple training.  If you code something from ground up the client will be dependent on you for all changes which might sound good until you start getting a dozen calls a week for minor tweaks.

Just some thoughts...

Sam

---

### Post by JMJ_coder on 2010-05-20
> **samalex said:**
> Stepping away from your question for a sec, what type of site will it be - static "here we are" site, e-commmerce site, etc?  Django is more of a framework from what I understand, so you may have more foundation if you ran with something like Joomla or even Wordpress or MediaWiki depending on what the needs are.  Also is this something you'll set-up and pass to them or will you be maintaining the content.  If the former then Joomla can be written to pass off to the client to update with some simple training.  If you code something from ground up the client will be dependent on you for all changes which might sound good until you start getting a dozen calls a week for minor tweaks.

Just some thoughts...

Sam

It's an ongoing project that will require a lot of customization (such as music lyric alteration). I will be maintaining the site indefinitely along with other volunteers as they come aboard. Thus, I need a framework as this really isn't something that already exists (though it may borrow aspects of a CMS).

---

### Post by sydbat on 2010-05-20
> **JMJ_coder said:**
> Why do you say that?This answers it better than I can...

> **samalex said:**
> I've never used either really, though I know a few people who are die hard Postgres users and love it.

The Webfaction does say "Extra SSH and SFTP users - Unlimited" so they should be able to give you an account to get in and do what you need to without them giving you the master account.  So getting in shouldn't be a problem.

The site also says "One click installer for tons of applications including Rails, Django, Drupal, WordPress and a lot more" so I wonder if they are using something like cPanel.  Either way I'd suggest rolling your own Django or whatever because often times these pre-packaged ISP apps don't have the latest versions or security updates.  If you download the latest of whatever canned app you choose, whether it be Django or whatever, you can verify it's the latest and greatest and update it as you see fit without being dependent on the ISP.  

Stepping away from your question for a sec, what type of site will it be - static "here we are" site, e-commmerce site, etc?  Django is more of a framework from what I understand, so you may have more foundation if you ran with something like Joomla or even Wordpress or MediaWiki depending on what the needs are.  Also is this something you'll set-up and pass to them or will you be maintaining the content.  If the former then Joomla can be written to pass off to the client to update with some simple training.  If you code something from ground up the client will be dependent on you for all changes which might sound good until you start getting a dozen calls a week for minor tweaks.

Just some thoughts...

Sam

---

### Post by samalex on 2010-05-20
> **JMJ_coder said:**
> It's an ongoing project that will require a lot of customization (such as music lyric alteration). I will be maintaining the site indefinitely along with other volunteers as they come aboard. Thus, I need a framework as this really isn't something that already exists (though it may borrow aspects of a CMS).

Without knowing your coding skills, from my experience I'd suggest sticking with one of the more mainstream CMS systems like Joomla which has TONS of plug-ins/add-ons at your disposal, and it's pretty simple to write something custom if something doesn't already exist.  Plus being in PHP you can tap into an almost infinite repository of code to use.  

Again, I've never used Django so it may rock the socks off anything I've ever touched, but given it's so obscure I'm not sure what it could bring to the table.  Our LUG is a member of the OReilly Book Group and we get books once or twice a month to give away to the LUG.  I've found they normally send us the overflow books they can't sell, and last year a book on Django was one of those books which was the first and time I had heard of it.

Once more just my observations...  Take care,

Sam

---

