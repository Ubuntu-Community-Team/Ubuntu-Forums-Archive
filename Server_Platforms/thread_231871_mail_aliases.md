---
title: "mail aliases"
date: 2006-08-07
forum: Server Platforms
---

### Post by TravisNewman on 2006-08-07
I'm setting up a multi-purpose server for me and my wife-- file/print/email, etc.

The point of the mail server is so that we can have imap access so we can keep our folder structure no matter where we log in. I have fetchmail downloading mail from our different accounts, I've tried postfix, sendmail, and exim for the MTA, courier-imap for the mail server, and squirrelmail for webmail access. All is well with that, I've done it a few times in the past just for fun so I'm good with setting it up.

Here's the problem. We have mail coming in from all over the place. My wife has her university email and gmail, I have gmail, work email, and mail from the isp. Any mail that we send out comes from user@servername. I think I've found ways in all the MTA's to have it show up as a specific domain, for example [email]user@gmail.com[/email], but if I do that, all mail we both send will look like it's coming from gmail, even if we want to send it from some other place. Make sense? My wife NEEDS to send out from her university email, and would like to be able to send out from gmail when she replies to mail she's recieved from gmail.

My question, is there any way to set up aliases anywhere to accomplish this?

---

### Post by Glut on 2006-08-08
As a rule, the 'From' field and domain are controlled by the User agent, i.e. Thunderbird or Evolution. In thunderbird you setup your mail accounts (even if you are forwarding to your own server) and then at send time select from the drop-down list your persona.

---

### Post by TravisNewman on 2006-08-08
in this case the user agent will usually be squirrelmail, which doesn't allow that. And besides, even when using thunderbird or evolution, it will be connecting to the mail server I'm setting up, so the persona will be user@myserver, though in that case it IS possible to set a reply-to address. Reply-to addresses break mailing lists a lot of the time though.

---

### Post by Glut on 2006-08-08
A quick google search reveals the 'Custom From' plugin for SquirrelMail: [http://www.squirrelmail.org/plugins_category.php?category_id=11](http://www.squirrelmail.org/plugins_category.php?category_id=11)
I think that this is what you're after.

After this you will need to configure your mail server to send mail from any domain. *****WARNING***** Make absolutely sure that no-one can send email from outside your network, preferrably only send mail from that machine. Becoming an open relay is not fun.

---

### Post by TravisNewman on 2006-08-08
yes, I refuse to become an open relay. I think Charter would kick me.

I also found somehting similar in Horde that I'm thinking of trying out. Thanks Glut!

---

