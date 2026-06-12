---
title: "A keylogger through WINE"
date: 2008-05-26
forum: Security
---

### Post by jasontu on 2008-05-26
Just a quick question.  I just read a horror story about someone having their computer hacked by a secondary web program which logged keystrokes and compromised various passwords.  I was wondering if such a program would ever work if I'm running programs in WINE.

Thank you.

---

### Post by mbaker824 on 2008-05-26
> **jasontu said:**
> Just a quick question.  I just read a horror story about someone having their computer hacked by a secondary web program which logged keystrokes and compromised various passwords.  I was wondering if such a program would ever work if I'm running programs in WINE.

It's definitely possible, and you don't even need to be running Wine - there are keystroke loggers out there for Unix and Linux systems, not to mention  sniffers that'll do basically the same thing from a compromised machine elsewhere on your network.

There's a bit of a misconception out there that Linux is somehow perfectly secure.  More secure than Windows, yes (but what isn't?); completely secure, no.  In Counter Hack Reloaded, chapter 3 (Linux and UNIX Overview), Ed Skoudis has this to say:
> With [their] great power and widespread use on the Internet, **Linux and UNIX systems are common targets of attackers**. (emphasis mine)

My advice is, don't listen to those who say Linux is already secure and there's no need for firewalls and such.  Don't take my word for it, though - read Counter Hack and find out for yourself.

Mark

---

### Post by Dr Small on 2008-05-26
Keyloggers may work through wine, I don't know, as I have never tried. But in order to get a keylogger on Linux, it would require you to either install it, or some social engineering to get you to install it just the same.

Someone just can't knock on your IP address and install a keylogger. It isn't that simple. It would require you to install it, or the attacker, if he bruteforced his way in.

Dr Small

---

### Post by jasontu on 2008-05-29
This is really good information for a newcomer.  I suppose the requirement of a password to install anything is one of the simple, yet powerful, strengths of both Linux and Vista.  

I barely understand how the new generation of malware really works, so I tend to err on the side of caution.

For the sake of my enlightenment and others, what would be the best security software to run on my Hardy installation?  I know that AVG, for example has a Linux virus scanner.  Can anyone suggest any other malware scanners?

Thanks again

---

### Post by Dr Small on 2008-05-29
The AVG linux scanner is built to be installed on Linux, but does not scan Linux Viruses (there are few anyhow). Antiviruses on Linux are mainly built to scan files that could be coming from Windows users, to protect them. (Like if you run a email or file server, an antivirus could be useful).

---

