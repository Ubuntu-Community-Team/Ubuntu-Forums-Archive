---
title: "mail from servers on home network"
date: 2008-08-01
forum: Server Platforms
---

### Post by worthspending on 2008-08-01
I have a small home network consisting of three machines running ubuntu.  one machine (among other things) is a dedicated file server.  I need to use cron to perform tasks and I would like to send email from cron.

I did try apt-get install mailx and I was able to send mail to self@localhost.  However, I am unable to send mail to a GMail account from my local machine.  "Remote domains not supported".  I assume it has to be something related to the fact that my local machine does not have a domain name that will resolve via DNS and no valid MX record can be found.

Bottom line, I am interested in sending email from cron from machines on my local network.  What would be the best solution??

Thanks

---

### Post by windependence on 2008-08-01
DNS and your MX record are not the problem.

Install postfix.

sudo apt-get install postfix

Then configure your hostname, domain, etc. and you should be good to go.

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

Are you trying to send mail through gmail's servers? If so, why? You can send mail from your own box.

-Tim

---

### Post by exssnrg on 2008-08-04
I like a solution that I found from my days when I worked with Gentoo called "email". It's perfect when you just want to send out a simple email from a command line.  Works good with scrips initiated from a cron job.

This is a very simple command line emailer that requires no other infrastructure, and just one config file to edit. I find most folks have no desire to set up an email MTA, etc. and already have an email server from their ISP that works just fine.  There is no Ubuntu package for this so you'll have to build from source.  Which is really not hard.  Just do a little reading of the readme file and you'll figure it out. 

Check out [http://www.cleancode.org/projects/email](http://www.cleancode.org/projects/email)

---

### Post by exssnrg on 2008-08-04
I just tried installing "email" on a fresh hardy build. To get the program to compile, I needed to add this package as shown:

sudo apt-get install libc6-dev g++ gcc

---

