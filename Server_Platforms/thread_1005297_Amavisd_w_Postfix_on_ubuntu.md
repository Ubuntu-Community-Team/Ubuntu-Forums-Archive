---
title: "Amavisd w/ Postfix on ubuntu"
date: 2008-12-08
forum: Server Platforms
---

### Post by scof-mon on 2008-12-08
Hi all,

I am new to postfix, amavisd and ubuntu in all as well. I am using Hardy Heron. I installed amavisd-new version 2.5.3-1. I want to send all the mails (globally) to amavisd and from there call my external python script to perform some function on each mail. So basically I want to filter all mails an run my script on each one of them.

I have 2 questions:
1. I wanted to configure amavisd so that all mails go to amavisd. I referred to the following link:
[http://www.ijs.si/software/amavisd/README.postfix](http://www.ijs.si/software/amavisd/README.postfix) (since I am using postfix as the MTA).

The link talks about the config file amavisd.conf. However with the package that I got from the repos, there is no single conf file. However various files such as 50-user, 15-content_filter_mode, 20-debian_defaults, etc.

So I dont get, in which file I need to make the specified changes. (I am using ubuntu hardy heron).

2. Is it possible to call an external script from amavisd and run it on each mail received by the amavisd. If yes, how? Is there some online resource for that?

Thank you in advance for the help.

cheers,
Monica.

---

