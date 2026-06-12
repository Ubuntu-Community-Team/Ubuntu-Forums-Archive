---
title: "Break Ins: Points Of Entry, Attacks, Detection, Solutions?"
date: 2006-11-02
forum: Server Platforms
---

### Post by Count Noobulus on 2006-11-02
In the coming year I'm hoping to set up a storage unit that I can access from the web..problem is, I'm not sure how to go about it securely. I think ssh is the method best suited for me rather than mail/http/ftp for data transfered to/from the web. I think I can manage that much on my own without mucking it up I guess. Are there any security risks that require special attention when using ssh?   

I'm also very concerned about break ins and corruption of the file system. How do I know when someone has gotten privileged user, or root access to the machine before something sinister takes place (any system file changes to look for)? When someone that gets in is out to bug or destroy the system in an undetectable way, what are some of the most likely attacks to anticipate before they try to do damage?

Lastly, how many different ways could someone get in a box connected to the net? I know of brute forcing for passwords, but how do others work?

---

### Post by johnnymac on 2006-11-02
I can't answer everything - but I can give you some help...

As far as ssh - it's fairly secure but just like anything else if someone gets the username and password (regardless of how) it's a bad thing.  The best thing to so would be to set up and SFTP type of access with restricted-shell.  This way the account you use remotely is restricted to a very specific directory upon login.  That account and only that account should have access from the outside.

As far as break-ins - keep an eye on logs in your /var/log/ directory.  There's a ton of different logs that will help you in tracking down if someone is doing naughty things.  You best bet (and I'm sure people will say you don't need anti-virus for linux) is to install an anit-virus, a root-kit hunder, and possible attach an intrusion detection methodology to it (snort, etc).

There's tons of different ways you can get hacked; however, most of the people who get hacked (not businesses or the like) get hacked because they aren't remotely protected.  I mean no firewall, no anti-virus...just nekkid out on the Web.  So you'd do yourself a ton of justice by simply adding a router between you and the internet.

Good luck - I hope I was a little bit helpful.

---

### Post by Count Noobulus on 2006-11-02
Thanks, I feel like I have a good overview of it now. This really caught my attention - "The best thing to so would be to set up and SFTP type of access with restricted-shell." Do you know of any good tutorials on this? Is this better than trying  to tunnel things to a intranet site over ssl?  

Also, does anybody know what a break-in log file looks like?

---

### Post by johnnymac on 2006-11-03
There are many tutorials available...here's an example of one:

[http://www.ubuntuforums.org/showthread.php?t=128206&highlight=SFTP+rssh](http://www.ubuntuforums.org/showthread.php?t=128206&highlight=SFTP+rssh)

Also I did one some time ago for Freshmeat using Gentoo...

[http://freshmeat.net/articles/view/1576/](http://freshmeat.net/articles/view/1576/)

---

