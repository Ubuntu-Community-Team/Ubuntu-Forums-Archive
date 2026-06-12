---
title: "script driven email send receive app"
date: 2011-04-01
forum: Server Platforms
---

### Post by dazz100 on 2011-04-01
Hello

I am looking for a very lite weight email send receive application that can be easily driven by scripts.  I want to install it in a remote webcam server connected via wireless broadband to the internet.  The Telco does not allow unsolicited traffic into it's wireless network.

I want the webcam server to 
send a daily status emails to me to let me know the system is alive and healthy.
receive an email which causes the server to send an acknowledge email and then initiate a VPN connection to me so I can do admin.  

I need something simple and easy to use.  sSMTP would be ideal if it also received email.  

I definitely do not want to run sendmail.  The server only has a 10GB HD.

Any suggestions??

---

### Post by BkkBonanza on 2011-04-01
Are you going to have a web server running on that machine anyway? I have some very lightweight pop3/smtp php scripts that I use for exactly this on mine. They could be run from the cmd line too if you installed php-cli. (I didn't write them but they have been used my me non-stop in a production machine for over 5 years)

Another approach is to use ssh in reverse tunnel mode. This has the remote server open a tunnel connection to your machine (outgoing from remote). Then any time you like you can just connect to that port locally and do anything you like on the remote machine. It's like having an external port listening for your server.

You would want to start that tunnel in an init script with "respawn" so that if the connection is lost it will auto-reconnect.

---

### Post by dazz100 on 2011-04-01
Hello

No, I definitely won't be running a web server on the webcam machine.  The broadband wireless plan has a 500MB monthly allocation after which obscene $$$/MB apply.  Running a web server would not allow me to control traffic (and $$$$)

The Webcam uses scp to transfer images to another server via wireless (not mine).  From there it is uploaded to a webpage server (also not mine).  This gives me 100% control over traffic in/out of the webcam machine.

I have found quite a few people trying to find a simple send/receive email application for the same reason I want one.  All the popular ones I have found are far more complex than I need.

I have found a perl script called sendemail, but I haven't tried it.  I would be keen to get a copy of the script you use.

The reverse ssh sounds like a good idea.   It would still be convenient to have the webcam send out a daily status/ I'm alive report. 

Regards

Dazz100

---

### Post by BkkBonanza on 2011-04-01
Here's the php code I use. There's a class each for pop3 and smtp.

Re: html2txt class, if you don't want to send multi-part alternative versions in html and plain text then you could remove the alternate code from the smtp class and the reference to the html2txt class to reduce files/footprint needed. 

I use this code with gmail and so it can support ssl use. You just use a host value like "ssl://smtp.gmail.com" and port 465 for smtp or for pop3 use "ssl://pop.gmail.com" and port 995 instead of usual port 25 and 110.

Note again this isn't my code but I did make several changes to it to fix/enhance it's operation. See the comment headers in files for original authors.

The example file I just threw together for you to show how to use. It's untested, as is. It should work as I cut/paste from my working code. No guarantee and if it doesn't it's no doubt a simple fix.

[http://www.sendspace.com/file/0m58pm](http://www.sendspace.com/file/0m58pm)

---

### Post by dazz100 on 2011-04-03
Hi

Thanks for that.  I will give it a try.

---

### Post by dazz100 on 2013-02-16
Hello

I ended up using ssmtp.  It is a simple send-only program that is easy to setup and use.  Ideal for sending messages from server logs etc.

Dazz

---

