---
title: "Help Setup MixMaster Remailer"
date: 2012-10-25
forum: Security
---

### Post by SpookyZ on 2012-10-25
Hey Guys,

I figured this would be the right forum since this focuses on privacy. I am trying to setup Mixmaster Remailer. Basically this is TOR for email. It allows you to send email that cant be traced back to you which is great for whistleblowers. The problem is there is not nearly enough nodes, even if every exit point was compromised as long as there were non compromised middle remailers the security is still in effect.

How can I set this up to be a remailer? How can this be setup to work through gmail?

I did the following:
sudo apt-get install ncurses
sudo apt-get install mixmaster
Mixmaster
[Here I can create message, choose route, send message, send from pool. But the message never arrives to newsgroup or my own email.
Maybe my port 25 is blocked but not sure how to check? Mixmaster installs postfix so that should work. I dont see where I can enter my gmail details and such]

Any pros mind helping me out to get this working.

Running Ubuntu 12.10 x64

---

### Post by kevdog on 2012-10-25
Let me get back to you, a few months ago I got things setup to work.  I remember a problem setting up postfix.  Let me see what I can find

---

### Post by SpookyZ on 2012-11-07
Any luck yet finding it KevDog?

---

### Post by bustard on 2013-02-05
> **SpookyZ said:**
> 

How can I set this up to be a remailer? How can this be setup to work through gmail?

I did the following:
sudo apt-get install ncurses
sudo apt-get install mixmaster
Mixmaster
[Here I can create message, choose route, send message, send from pool. But the message never arrives to newsgroup or my own email.
Maybe my port 25 is blocked but not sure how to check? Mixmaster installs postfix so that should work.If you want to set up a remailer, see middlerem at apasreader.yolasite.com.

I recommend you remove postfix, unless you are sure you have it set up correctly, and replace it with exim4. The instructions in middlerem describe how to configure exim4 - it is a one-line change in the config file.

Once you have exim4 installed properly, you can use it with the remailer and can also use it using mixmaster as a client - I mean typing 'mixmaster' from the command line and entering and sending a message. Probably the reason that is not working is that postfix is not configured. I have no idea how to configure postfix, which is why I recommend exim4.

The instructions in middlerem should be detailed enough to allow you to set up the remailer; if they are not, ask here or at alt.privacy.anon-server.

---

