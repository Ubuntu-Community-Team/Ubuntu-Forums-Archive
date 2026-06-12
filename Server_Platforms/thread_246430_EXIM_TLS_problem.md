---
title: "EXIM TLS problem"
date: 2006-08-29
forum: Server Platforms
---

### Post by jimm on 2006-08-29
Hi,

I have just migrated my old Redhat mail system to Ubuntu server (6.06). For various reasons... Number one being I don't really understand what the deal is with Fedora any more. Ubuntu on the other hand seems to have a more clear cut vision.

Anyway... I also decided to move my mail server away from Sendmail and try out EXIM. Having used sendmail for several years, moving to a new MTA was a little bit of a risk, but I was pleasantly suprised to find that it is quite easy to setup and manage. However I have had a couple of issues...

Firstly, has anyone else seen this: When EXIM is configured to use TLS it will use the STARTTLS option if the remote MTA offers it. Fine... I did a testing install of EXIM on my old RedHat box to see if I could migrate my old sendmail setup across and it worked fine straight from the package install. However on Ubuntu EXIM stops dead when the remote MTA offers STARTTLS. The Redhat install went straight ahead and used TLS with no extra config and mail flowed fine. I didnt even have to generate new certs or anything. However Ubuntu does the following (EXIM session verbose debug trace):

LOG: MAIN
  <= [email]XXX@XXX.com[/email] U=XXX P=local S=284
ik55050:/etc/exim4# delivering 1DmARj-0004ok-M1
R: dnslookup for [email]XXXX@xxx.com[/email]
T: remote_smtp for [email]XXXX@xxx.com[/email]
Connecting to XXX.xxx.com [XXX.XXX.XXX.XXX]:25 ... connected
  SMTP<< 220 XXX.XXX.com ESMTP Postfix (Debian/GNU)
  SMTP>> EHLO XXX.XXX.com
  SMTP<< 250-XXX.XXX.com
         250-PIPELINING
         250-SIZE 10240000
         250-VRFY
         250-ETRN
         250-STARTTLS
         250-AUTH PLAIN LOGIN DIGEST-MD5 CRAM-MD5
         250-AUTH=PLAIN LOGIN DIGEST-MD5 CRAM-MD5
         250 8BITMIME
  SMTP>> STARTTLS
  SMTP<< 220 Ready to start TLS

And that's where it stops. The 220 line just holds the EXIM instance open forever and I have to kill the job to free it up. I have tried everything to get it going but I can't figure it out. The EXIM config on my redhat box is identical to the Ubuntu one so I can't see it being a config issue per se. Something else is messing me up. Has anyone else seen this happen? Any thoughts clues or solutions? 

I have put a work around in place telling my server to avoid using TLS (option in the config file) so my mail works fine for now, but doesnt use TLS. Any help on this would be great!

Another thing I found was that EXIM was much slower than sendmail was. It looked like lookup errors but DNS was fine so I discovered this was due to an IDENT timeout. As I didnt want to install and IDENT server I added the following lines to the config and it all came right:

rfc1413_hosts = *
rfc1413_query_timeout = 0s

So if you are experiencing slow EXIM sending from your mail client you might want to check your DNS config and make those changes to your config if you dont want to use IDENT on your mail server. 

Having set up a mail server, DNS, Apache2 Web server and other stuff on Ubuntu now, I am very happy with it. However that EXIM TLS issue still bugs me. Please let me know if you have any clues as to why it might not be working.

Thanks,
James

---

### Post by miahfost on 2006-10-10
This looks like a possible known bug. TLS requires system entropy and your system may not have enough for TLS. Please look here to see if this is in fact your issue: [http://wiki.debian.org/PkgExim4KnownBugsInSarge](http://wiki.debian.org/PkgExim4KnownBugsInSarge)

A quote from the above link: "To see whether you're bitten by that problem, look at the contents of /proc/sys/kernel/random/entropy_avail. If that number is well below 1000, you're in trouble."

---

### Post by jimm on 2006-10-10
Hi miahfost,

Thanks very much for that. It does indeed look like I am suffering from that bug! I will try the suggested work arounds and see if I can make it work as it is supposed to.

I'll check out the bug in more detail as well and see if there are any fixes in progress or if I can have some input somehow.

Many thanks for pointing this one out to me!

Thanks,
James

---

