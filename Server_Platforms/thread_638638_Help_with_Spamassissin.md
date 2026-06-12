---
title: "Help with Spamassissin"
date: 2007-12-12
forum: Server Platforms
---

### Post by zaber on 2007-12-12
Hello all I need a little help getting Spamassissin to modify headers of messages.

I am Currently using 64 bit Ubuntu 7.10 Server on an AMD 64X2.  I have set up postfix to be my email server using amavis-new for a content filter.   Everything seems to be working fine, but Spamassassin is not marking the headers in the messages.  I can see in the log where messages are scanned and marked as spam (using gtube to test), but no modification is made to the message.  

I am not sure if it related but when I add options in Spamassissin's local.cf like "use_dcc 1" I get a message about failing to parse the line.  I do have " rewrite_header Subject *****SPAM*****" in local.cf as well as "$sa_spam_subject_tag = '***SPAM*** ';" and "$sa_tag_level_deflt  = -200.0;" in my amavis configuration.

Does anyone have any suggestions on where to look or what the issue may be?

---

### Post by HermanAB on 2007-12-12
Note that when you run SpamAssassin through Amavisd-new, most of the settings in the SpamAssassin config files are ignored.  Which ones are not ignored are mostly left as an exercise to the reader...

The trick is to configure things in the Amavisd config file and mostly ignore the SpamAssasson config file.

Cheers,

H.

---

### Post by zaber on 2007-12-12
> **HermanAB said:**
> 
The trick is to configure things in the Amavisd config file and mostly ignore the SpamAssasson config file.

Cheers,

H.
Thank you for the tip.  

I do have the Amavisd files configured correctly (I think).  Could my issue be perhapps caused by a conflict between the two configurations?  

When trouble shooting this I went so far to take the /etc/amavis/ directory and the /etc/spamassissin directories from a working system, and not even that helped.
:confused:

---

### Post by HermanAB on 2007-12-12
BTW, I have run into that same problem years ago.  I don't think I ever found a fix.  See whether there is a mailing list on the amavisd-new web site and ask there.

Cheers,

H.

---

### Post by zaber on 2007-12-12
OK thank you again, I will dig deeper.

---

