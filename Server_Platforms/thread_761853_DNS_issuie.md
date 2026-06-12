---
title: "DNS issuie"
date: 2008-04-21
forum: Server Platforms
---

### Post by roas300 on 2008-04-21
I am getting my first ubuntu server up and going, my goal is web server, mail server and so on.

I have rebuilt several times due to messing something up.

Here is my currnet problem.

I have attempted to setup DNS using bind9.

when I do the dig command after following the ubuntu documentaion for setting up DNS here is the result

Dig roachnrg

it reports back that it worked

dig roachnrg.com

it does not find it.

I do have a fully quailfied domain name "roachnrg.com" 

My godaddy setup has ns1 xxx.xxx.xxx.xxx  my ip adress
                                     ns2 xxx.xxx.xxx.xxx same ip
:)

---

### Post by HermanAB on 2008-04-21
Hmm, for us to be of any help, you'll have to post all your BIND configuration files.  That is not very practical.  So the best you can do is to go to the BIND web site and read the manual a few times.

Put a tail on the log file ($ sudo tail -f /var/log/messages) before you restart BIND, then look for errors and warnings returned by BIND.

Cheers,

Herman

---

### Post by roas300 on 2008-04-21
would it be foolish to let some one from this forum to telnet in and look at my setup?:lolflag:

---

### Post by MJN on 2008-04-21
Give the full output of the dig commands (ideally with the +trace option) rather than just 'it works' - this isn't enough for us to go off.

Neither 72.29.40.94 or 72.29.40.95 are responding to DNS queries. Are they accepting connections on UDP port 53? (the port needs forwarding on your router if you have one)

Mathew

---

### Post by HermanAB on 2008-04-21
I could SSH into your box and take a look, but not now and not tonight.  I work in a secure lab, so I can help you on Tuesday night.  Send me a private message if you want.  Due to the work I do, you have been trusting me with your life for the past 20 years already so this is nothing... :)

---

### Post by MJN on 2008-04-21
:lolflag:

---

