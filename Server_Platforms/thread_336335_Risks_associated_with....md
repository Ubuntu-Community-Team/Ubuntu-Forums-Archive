---
title: "Risks associated with..."
date: 2007-01-11
forum: Server Platforms
---

### Post by echo $USER on 2007-01-11
FTP anonymous upload?  Is there anything I should worry about?  I only have it so I can tranfers crap I find on teh net at work to one of my home PCs.

---

### Post by MontanaMax on 2007-01-12
it's possible that the information could be "packet sniffed" and reconstructed by someone as it's not encrypted, and it's also possible that someone could log into the FTP server using the anonymous account and copy your data. Those aren't usually a huge concern for me.

However, if you're running an FTP server with anonymous account write access turned on, you will very likely become host to a whole bunch of "black hat" type files as people decide that your nice little system is a great place to stash and transfer stuff. I had this problem once in the late 90's and swore I'd always use at least a password access on all services with the ability to write information.

---

### Post by echo $USER on 2007-01-12
> **MontanaMax said:**
> 
However, if you're running an FTP server with anonymous account write access turned on, you will very likely become host to a whole bunch of "black hat" type files as people decide that your nice little system is a great place to stash and transfer stuff. I had this problem once in the late 90's and swore I'd always use at least a password access on all services with the ability to write information.

That is what worries me.  I would be aware though right?  If I always checked the folder and log file?

---

### Post by Brazen on 2007-01-12
It _could_ make is easier to take advantage of a remote execution exploit, though if you are using vsftp, then you are pretty safe from this.  Is it really worth the trouble though, always double checking your files and logs, when you could just type in a simple password each time.  Filezilla (a Windows program, I know) at least will save your credentials if you are using this from one computer most of the time.

---

### Post by MontanaMax on 2007-01-14
News articles like this one about a poor teenage boy who had illegal porn files loaded onto his machine by "infected files" yet still nearly went to prision and had to endure two years of being labeld as a "sex offender" make me just paranoid enough to not leave anything unprotected on my systems if at all possible - and I use hardware firewalls in addition to the software ones on my computers. 

[http://abcnews.go.com/2020/LegalCenter/story?id=2785054](http://abcnews.go.com/2020/LegalCenter/story?id=2785054)

I just don't want someone to tell a sad story like this about me some day.

---

### Post by echo $USER on 2007-01-15
> **MontanaMax said:**
> News articles like this one about a poor teenage boy who had illegal porn files loaded onto his machine by "infected files" yet still nearly went to prision and had to endure two years of being labeld as a "sex offender" make me just paranoid enough to not leave anything unprotected on my systems if at all possible - and I use hardware firewalls in addition to the software ones on my computers. 

[http://abcnews.go.com/2020/LegalCenter/story?id=2785054](http://abcnews.go.com/2020/LegalCenter/story?id=2785054)

I just don't want someone to tell a sad story like this about me some day.

JFC!!!  I'm shutting it down as soon as I get home.

---

### Post by msgyrd on 2007-01-15
If you're the only user, just setup SSH/SCP server.  It's a secure way to transfer files and access your machine remotely. Just about every *nix distro has a client for it (OSX too), and you can download PuTTY and WinSCP for windows (they'll run off USB drives also).  Much less risk involved than an an open FTP connection.

---

