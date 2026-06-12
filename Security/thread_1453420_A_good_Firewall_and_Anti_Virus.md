---
title: "A good Firewall and Anti Virus"
date: 2010-04-13
forum: Security
---

### Post by ubun2warrior on 2010-04-13
I have heard that Ubuntu is virus free. But when we browse the net we are always exposed to innumerable threats. One way to get security is through firewalls(which is considered to be the best way by many people). I have tried firestarter to implement security on my desktop. I created some policy regarding which all sites should be allowed so that I am constantly working in a secured environment. But the internet experience was not good(infact i found it was working slowly for some reason(may be because it was doing a lot of blocking)). I also have avast installed on my pc. 

I am looking for some good firewall and antivirus security for my desktop and also some guidance regarding internet security. 

Hope i get some answers.

---

### Post by cdenley on 2010-04-13
Firewalls only protect you from yourself. If you haven't installed any server software, then there is nothing to keep people from connecting to. Anti-virus will only protect windows computers. Firestarter is no longer maintained. Linux is very different from windows. Read the security sticky.
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by HermanAB on 2010-04-13
Relax and enjoy your Linux system.

You don't really need to add any security junk to it.

---

### Post by lovinglinux on 2010-04-13
[Ubuntu Security](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by bodhi.zazen on 2010-04-13
> **ubun2warrior said:**
> I have heard that Ubuntu is virus free. But when we browse the net we are always exposed to innumerable threats. One way to get security is through firewalls(which is considered to be the best way by many people). I have tried firestarter to implement security on my desktop. I created some policy regarding which all sites should be allowed so that I am constantly working in a secured environment. But the internet experience was not good(infact i found it was working slowly for some reason(may be because it was doing a lot of blocking)). I also have avast installed on my pc. 

I am looking for some good firewall and antivirus security for my desktop and also some guidance regarding internet security. 

Hope i get some answers.

Antivirus is not needed. If you must look at clamav.

To enable your firewall, open a terminal and type```
sudo ufw enable
```

"Internet security" is complex and the only things you can do are to secure your browser and use apparmor to restrict any network aware applications.

For the vast majority of users such things are unnecessary and IMO you are better off learning how your system works then blindly applying your windows mentality to Ubuntu.

[http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/](http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/)

---

### Post by new_tolinux on 2010-04-13
> **bodhi.zazen said:**
> For the vast majority of users such things are unnecessary and IMO you are better off learning how your system works then blindly applying your windows mentality to Ubuntu.
Only partly agreed.

The major security flaw in both Windows _and linux_ is _the admin_.
Although virusses are uncommon (but existing) in Linux, browser-hijacks etc. _are_ existing (google:[FONT=Fixedsys] firefox about:blank[/FONT]).

You might want to learn to read before you click. In my opinion the first-click-then-read behaviour is the biggest problem to every OS. And Linux is no exception, although a flaw in Linux is that not everything is working via GUI's and therefore not every command does produce the warning it should.
You can have a state-of-the-art virusscanner _and_ a state-of-the-art firewall but if it's misconfigured or someone (you ;)) decide to allow this-and-that without knowing what you're allowing...... they are useless. In both Windows and Linux.

---

### Post by lovinglinux on 2010-04-13
> **new_tolinux said:**
> (google:[FONT=Fixedsys] firefox about:blank[/FONT]).

That is an old vunerability, that only affects old versions of Firefox.

[http://news.softpedia.com/news/Firefox-About-Blank-Vulnerability-Could-Expose-You-to-Hackers-86661.shtml](http://news.softpedia.com/news/Firefox-About-Blank-Vulnerability-Could-Expose-You-to-Hackers-86661.shtml)
[http://www.securityfocus.com/bid/22601](http://www.securityfocus.com/bid/22601)

---

