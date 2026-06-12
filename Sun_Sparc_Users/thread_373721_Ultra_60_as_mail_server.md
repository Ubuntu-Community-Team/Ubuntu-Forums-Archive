---
title: "Ultra 60 as mail server"
date: 2007-03-01
forum: Sun Sparc Users
---

### Post by whitebunnyflock on 2007-03-01
After much fun getting my new dust-covered Ultra 60 and installing fast 10k SCSI drives and Ubuntu 6.06 I have decided to make it my mail server.

I have been all over the web trying to find a decent walkthrough in the hope of finding software for the Sparc in connection with my mail server project.

What I am looking for is a virus scanner, intelligent spam blocker, and mail server that has POP3 and IMAP capabilities and that is pretty much it.

Does anyone have experience with any of these and can recommend something?

---

### Post by jimflip on 2007-03-02
Yes I do :)

Ditch Ubuntu and install Debian sarge in fact follow this: 

[http://www.howtoforge.com/perfect_setup_debian_sarge](http://www.howtoforge.com/perfect_setup_debian_sarge)

And you will be sorted in a couple of hours :) assuming you don't want to use RAID?

Make sure u don't install mysql5 as it's flakey, it will install mysql4 by default following that guide.

You will also get some other stuff such as your own web server, but you can disable that or just block the port.
Jim.

---

### Post by netztier on 2007-03-02
> **jimflip said:**
> Yes I do :)

Ditch Ubuntu and install Debian sarge in fact follow this: 

[http://www.howtoforge.com/perfect_setup_debian_sarge](http://www.howtoforge.com/perfect_setup_debian_sarge)



Ah well - and what would be the argument against installing the same packages on Ubuntu 6.06 LTS? Postfix, Courier and the likes ar all available for Ubuntu, too.

I find your suggestion misses the question, by a mile and a half. The OP asked what packages to install for a mail server in an *Ubuntu* forum. To me, this is a clear hint that Ubuntu is the platform of choice - but this is debatable.

But he even asked for specific functionality, half of which the guide you suggested doesn't cover. He didn't ask for FTP, webmail, web services or DNS. He very probably has reasons to ask for mail functionality specifically, and not for "how to build a general-purpose internet server".

Sorry for not contributing - I have little experience with mail systems - but I just couldn't resist writing a little rant against your "forget ABC, because here's this cool guide to XYZ at www.coolguide.org" style posting. You might just as well have suggested to run M$ Exchange or Lotus Notes instead.

**To the OP:**
Some topics of your question are probably not specifiy to SPARC, and most of the software you will require should be available for Ubuntu on SPARC, too. So you might find more information about what server software to choose for what task in the [Servers & Security]("http://www.ubuntuforums.org/forumdisplay.php?f=7") sub-forum.

best regards

Marc

---

### Post by jimflip on 2007-03-02
Wrong...your questions won't get answered on forums and you will have to do several re-installs, when things just suddenly don't work with no error log or more typically "Segmentation fault" or "Bus error".

If you are not too clued up on setting up a mail server, particularly on a Sparc and don't want to waste your time, follow that guide I suggested.  If you really want to dick around you could always try Solaris10 it is a free download now days!

---

### Post by whitebunnyflock on 2007-03-02
thanks guys for your responses.  I think for now I will stick to Ubuntu as I have already configured the majority of my postfix and dovecot software.  now onto spam and virus.  Plus this is a great learning experience and there are no time constraints on it

---

### Post by Mr. C. on 2007-03-02
> **whitebunnyflock said:**
> thanks guys for your responses.  I think for now I will stick to Ubuntu as I have already configured the majority of my postfix and dovecot software.  now onto spam and virus.  Plus this is a great learning experience and there are no time constraints on it

I'm a big fan of, and have many years experience with:

* postfix
* amavisd-new  w/
   - spamassassin
   - clamav
   - mcafee's uvscan (second a/v scanner)

I personally use Courier-IMAP for IMAP/POP.

MrC

---

