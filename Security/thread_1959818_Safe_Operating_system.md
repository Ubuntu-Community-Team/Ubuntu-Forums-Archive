---
title: "Safe Operating system"
date: 2012-04-16
forum: Security
---

### Post by gordie69 on 2012-04-16
Hey guys I love Ubuntu and I'm getting to like the Unity Interface of 11.10 and I tried 12.04 and so I'm thinking on getting rid my Windows 7 and going Ubuntu just for like banking and finance so I'm just asking how secure Ubuntu is for that.
:guitar:

---

### Post by roelforg on 2012-04-16
> **gordie69 said:**
> Hey guys I love Ubuntu and I'm getting to like the Unity Interface of 11.10 and I tried 12.04 and so I'm thinking on getting rid my Windows 7 and going Ubuntu just for like banking and finance so I'm just asking how secure Ubuntu is for that.
:guitar:

Let's see...
* Almost no viruses (linux-general)
* If one ever get's to your pc, no root for the virus
* The fact it's linux... (all linux-generic security stuff applies)

---

### Post by Hungry Man on 2012-04-16
Well, that's a bit difficult to say. For banking you're talking about online interaction and also keyloggers/ anything that would sniff your traffic locally.

Linux isn't very targeted for viruses/ keylogger type deals (it's more targeted for remote code execution in servers etc) and running a limited user account would prevent most keyloggers from functioning anyways.

That's all good.

The problem is then your network. Are you on a router? Is it secured with WPA2? Have you changed the routers access username and password?

Consider using HTTPS Everywhere to prevent sniffing your traffic between you and a bank. [https://www.eff.org/https-everywhere](https://www.eff.org/https-everywhere)

Consider using NoScript if you're a Firefox user. noscript.net

Other than that there's not much to do that's specific to banking/ websites.

---

### Post by 2F4U on 2012-04-16
If you are concerned just about banking, you could run a liveCD of Ubuntu to access your banking web site. The advantage is that you always have a clean environment and nothing can be stored on the disk.

---

### Post by Dave_L on 2012-04-16
This point has been discussed in earlier threads, but the disadvantage of the Live CD approach is that you won't have the latest security patches.

---

### Post by gordie69 on 2012-04-16
Thanks guys I'm running W7 for my banking and personnals with mcafee 2012 plus with malware bytes both paid but just thought I'd pass that up for when my subscription runs out I thought Linux was safe for things like these whether then Windows besides I really how Ubuntu has come alone. I'm also running Zorin os 5.2 64 bit for downloading software, games etc. and like it also nice and light and Ubuntu based.

---

### Post by cortman on 2012-04-16
It makes a big difference whether you're using a local program to do your banking and finance, or if you do it all online- if it's all browser based, Ubuntu will be the best OS for it. If you're using an installed program like TurboTax, Quickbooks- you'll need Windows.

---

### Post by Ms. Daisy on 2012-04-16
> **gordie69 said:**
> Hey guys I love Ubuntu and I'm getting to like the Unity Interface of 11.10 and I tried 12.04 and so I'm thinking on getting rid my Windows 7 and going Ubuntu just for like banking and finance so I'm just asking how secure Ubuntu is for that.

I'll second what Hungry Man said.

Also, I'll add that Ubuntu will be as secure as you make it.  You can get yourself owned just as easily on Ubuntu as on Windows if you're in the habit of downloading and clicking on any old thing from any old site. Use smart surfing habits & check out the [basic security wiki]("https://wiki.ubuntu.com/BasicSecurity") if you want to increase your security.  (You could actually apply a fair amount of the advice in the basic security wiki to Windows for increased security there.) There's also a lot of additional security advice in the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812").

I have to go on the record about the live CD option for banking because it seems to be a fairly common suggestion.  I HATE HATE HATE that idea.  It does absolutely nothing to harden your browser, which IMO might be the most important thing you can do for your security. Sure, no malware will get written to your hard drive but meanwhile your cookies and credentials could all get stolen if you erroneously believe you're safe from browser attacks.

---

### Post by bubylou on 2012-04-16
> **cortman said:**
> It makes a big difference whether you're using a local program to do your banking and finance, or if you do it all online- if it's all browser based, Ubuntu will be the best OS for it. If you're using an installed program like TurboTax, Quickbooks- you'll need Windows.

Not necessarily. Wine should allow you to use your windows programs. Better yet , there is most likely a program for Linux which achieves the same goals.

Linux is definitely  what your looking for if you want a secure OS. I highly recommend you install it. Also if you want we could assist you in hardening your system.

+1 to Ms.Daisy

Linux cannot stop you from doing something you should have.

---

### Post by gordie69 on 2012-04-16
All I would use Ubuntu for is just my personal banking etc and I use firefox I also use Zorin os 5.2 64 bit and I play games and download but in Ubuntu should enable the firewall or leave dissibled
I also heard to keep your os updated and use the newest os version

---

### Post by aysiu on 2012-04-16
Ubuntu is about as secure for banking as any major OS is.

The real things you have to worry about are the wireless network you're on (Who else is on it? Is it encrypted? How is it encrypted?), that you're actually on your bank's website (not a spoof of it), and the up-to-date state of your web browser. Very little of that has anything to do with what operating system you're using. Almost all of it has to do with you as a user.

I'll also add a +1 to Ms. Daisy's recommendation *against* using a live CD as some kind of security. The live CD has well-known (and most likely unchanged) default settings, *sudo* authentication without any password authentication, and a most-likely outdated and unpatched web browser.

The most important thing to remember is that security is a multi-layered process, not a once-made-then-forgotten choice. Ubuntu is a safe operating system. Windows is a safe operating system. Mac OS X is a safe operating system. **Nothing** is an invincible operating system.

---

### Post by OpSecShellshock on 2012-04-16
If you are able to use a dedicated machine for nothing but financial business then you're in pretty good shape right there, provided you can maintain discipline. That is, if you 1. don't conduct sensitive/financial business on any other devices and 2. don't use the dedicated computer for anything else, then that's just about the next best thing to not doing online transactions at all (which is the safest, but also least useful).

---

### Post by aysiu on 2012-04-16
Oh, I forgot one more thing no one else has mentioned: use a strong (hard-to-guess) login password for your banking account.

---

### Post by Hungry Man on 2012-04-16
> **aysiu said:**
> Oh, I forgot one more thing no one else has mentioned: use a strong (hard-to-guess) login password for your banking account.

I strongly second this one.

12 characters and don't make it "abcd12345678" or something easy to guess. Use at least one capital letter, at least one lower case letter, at least one number, and (if your bank allows you to) at least one symbol.

---

