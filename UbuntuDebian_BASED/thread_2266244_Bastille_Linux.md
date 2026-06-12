---
title: "Bastille Linux"
date: 2015-02-21
forum: Ubuntu/Debian BASED
---

### Post by Matthew_Harrop on 2015-02-21
I have attempted to download and install Bastille Linux, however apt-get says the package is no longer hosted (I added the appropriate repositories) and the Debian website no longer lists it. Has it been taken down?

---

### Post by Lars Noodén on 2015-02-21
Bastille isn't really maintained, the last update was from 2008 : [http://sourceforge.net/projects/bastille-linux/files/bastille-linux/](http://sourceforge.net/projects/bastille-linux/files/bastille-linux/)

So even if the principle were sound, which it isn't, security isn't anything you can add on after the fact, it would still be too out of date to be of any use.

You can go through some checks to make sure you've done what you can.  What version of Ubuntu do you have and what do you have installed?

---

### Post by oldos2er on 2015-02-21
Moved to Other OS Support & Projects.

---

### Post by Matthew_Harrop on 2015-02-22
Hmm, interesting. Their source forge page says that they reactivated it in 2012...
Further, all the literature on the Ubuntu help sections indicates that its still used as a security tool.

So far I have installed:
Apache2 (currently switched off)
Postfix (Not configured)
Git
GitLab (Currently switched off)
SSH Server - Configured with keys
ufw - I've defined the ports I want open and closed (Only a few)
Eclipse
X11
gksudo
Tiger
Dia
ClamAV Antivirus
And some other utility programs like GCC and binutils.
I read that Tiger is a good place to start with security. I figure I'll start there and scroll through the list and see what I can and can't do
Do you have any other suggestions for what I can use?

---

### Post by Lars Noodén on 2015-02-22
You might look at SSHGuard.  It can scan logs for known types of attacks on certain services and block problematic hosts at the firewall.  But it does have a lot of limitations which become apparent if you think about how it works, the sources of the attacks and what can in practice be done.  

I would also subscribe to the [Ubuntu Security Notices](http://www.ubuntu.com/usn/) mailing list.  Other than that, it's the harder matter of mastering the configuration of your services, though specific guides might warn of common gotchas.  Unfortunately there is no one-size-fits-all solution even for specific daemons.  The three tools that stand out in your list above are the web server, the mail server and the SSH server.  If you have PHP and things written in PHP, such as WordPress, on top of the HTTP/HTTPS server that complicates things further.  With the SMTP server, it all depends how you plan to use it, but if you don't need it, it's good to remove it.  With the SSH server, you already have keys set up.

---

### Post by Matthew_Harrop on 2015-02-22
Hmm, thanks for the advice. I plan to use the SMTP server to run my mail (I am attempting to migrate from remote hosted to local)

I'll look into getting sshguard too. As I said before: Thank you very much! Again, your advice is very much appreciated :)

---

