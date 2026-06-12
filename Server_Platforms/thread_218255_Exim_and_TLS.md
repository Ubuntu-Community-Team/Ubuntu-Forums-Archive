---
title: "Exim and TLS"
date: 2006-07-18
forum: Server Platforms
---

### Post by egon on 2006-07-18
Hey all - I'm trying to set up a mail server with exim using a AMD64 Dapper server.  I have the following packages installed:

root@mail:~# dpkg --get-selections | grep -i exim
exim4                                           install
exim4-base                                      install
exim4-config                                    install
exim4-daemon-heavy                              install

The problem is that when my mail server attempts to send a message to another mailserver that speaks TLS, the one I'm trying to set up seems to hang.  If I try to force a delivery, it looks like this:

(In this instance, it's trying to deliver to "colet@code-energy.com")

root@mail:~# exim4 -v -v -v -qff
LOG: queue_run MAIN
  Start queue run: pid=11428 -qff
delivering 1G2QHf-00026H-4V (queue run pid 11428)
Connecting to mail.code-energy.com [64.34.179.90]:25 ... connected
  SMTP<< 220 portman.code-energy.com ESMTP Exim 4.50 Tue, 18 Jul 2006 09:42:45 -0400
  SMTP>> EHLO mail.example.org
  SMTP<< 250-portman.code-energy.com Hello home.tuininga.org [63.127.199.26]
         250-SIZE 10485760
         250-PIPELINING
         250-STARTTLS
         250 HELP
  SMTP>> STARTTLS
  SMTP<< 220 TLS go ahead

At this point, the connection just hangs.  Can anybody offer any ideas?  Thanks in advance...

---

### Post by psyncho on 2006-08-18
I have the exact same problem. Please let me know when/if you find a solution.  In a day or two I'll just use postfix instead of exim and see what happens.

Looking on the web I've found references to entropy and the random number generator.  It could be that the kernal for amd64 doesn't handle this. 
Indeed when I check my entropy it seems to have issues...meaning the sockets for TLS use random numbers for the encryption and if it can't get those generated then it hangs.  That's the only theory I've really seen so far.  

If you go to google groups and do a group search with:
-> STARTTLS timeout exim4
you'll find some stuff.

Here's a post:
[http://lists.alioth.debian.org/pipermail/pkg-exim4-maintainers/2004-December/000729.html](http://lists.alioth.debian.org/pipermail/pkg-exim4-maintainers/2004-December/000729.html)

I installed rng-tools and it said my hardward didn't have a random number generator.  I find that hard to believe since its a new machine and this is a newer hardware feature apparently, thus it could be that the kernel simply isn't supporting this.

involved packages are libgnutls...

again, if you find anything please do let me know.  Good luck...

thanks, 
John

---

### Post by psyncho on 2006-08-19
Well, I booted up my machine today to try debugging some more (lots of reboots are good since restarting the obviously related daemons isn't always enough) - and voila, TLS is working.

The problem is, I don't know what I did to fix it.  Here are a number of things I remember doing:

I fixed my hosts file to have the domain I'm relaying mail for on one line for the public IP address, and localhost is on 127.0.0.1, and then some configuration file set the local unqualified name of my machine to 127.0.1.1, so I left that on its own line (before I had localhost and my other fqdn on the line for 127.0.0.1 for some reason, most likely a simple mistake.)

I had also stored the login information for my smarthost (I'm delivering using smtp by configured for a smarthost) in the password.client file in the /etc/exim4 directory.  I had also recreated my certificates for exim, entering my public domain name which will mache the fqdn of my machine.

After this, some test emails I sent a while ago finally went through, which were hung up on something, probably logging into the smart host or something.  So perhaps it was sending a message before everything was configured correctly  that gummed up the "pipes", or something else.  I don't know.

In any case, TLS seems to be working now.  The only other thing I did was to the TLS line in the exim4.conf.template file, restart the daemon, then put it back and restart the daemon again.  

I'd be very receptive if someone who knew a lot more than I do explained how I accidentally fixed this, or maybe there's something I'm forgetting, or maybe its one of those problems where things work every now and then and its terribly difficult to debug...I don't know, but its working.

sorry I'm so verbose.

John

---

### Post by miahfost on 2006-10-10
Please look at this page: [http://wiki.debian.org/PkgExim4KnownBugsInSarge](http://wiki.debian.org/PkgExim4KnownBugsInSarge)

It sounds to me as if you have been bitten by the entropy bug in debian / ubuntu. This is nearly certainly so since you generated more entropy when you rebooted but I suspect exim will hang once it runs out of entropy when TLS kicks in. Read the above link for more info and how to use a work around.

---

