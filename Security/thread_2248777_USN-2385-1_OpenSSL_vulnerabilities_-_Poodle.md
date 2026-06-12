---
title: "USN-2385-1: OpenSSL vulnerabilities - Poodle"
date: 2014-10-17
forum: Security
---

### Post by ltitodem on 2014-10-17
Hi list,

I read about the OpenSSL Poodle vulenaribity:
[http://blog.canonical.com/2014/10/16/ubuntu-security-update-on-poodle-cve-2014-3566-and-sslv3-downgrade-attack/](http://blog.canonical.com/2014/10/16/ubuntu-security-update-on-poodle-cve-2014-3566-and-sslv3-downgrade-attack/)

So I did the security upgrade of libssl as per:
[http://www.ubuntu.com/usn/usn-2385-1/](http://www.ubuntu.com/usn/usn-2385-1/)
and rebooted the computer.

My libssl is now:
libssl1.0.0 1.0.1f-1ubuntu2.7

But when I test it on the page below, my browser still appears as vulnerable.
WARNING and DISCLAIMER:
This link was suggested by the IT people at my University so I presume it is safe, but I cannot be sure so use at your own risk.
I willingly wrote le link below with blank spaces to avoid involuntarily clicking:
https:          //www.        poodletest.        com/

So my question is two fold:
1) If this test page is correct why does my browser still appear vulnerable ?
2) Does anybody know if the above test page is safe and effective, or does anybody know about another way to test for the vulnearbility ?

Thank you for your help.

ltitodem

Ubuntu version: 14.04 all available updates done on October 17 2014
Browser: 33.0 Mozilla Firefox for Ubuntu canonical 1.0
libssl: libssl1.0.0 1.0.1f-1ubuntu2.7

---

### Post by oceola2 on 2014-10-17
There are two packages updated this morning for 14.04LTS 64bit:
libssl1.0.0 (1.0.1f-1ubuntu2.5) to 1.0.1f-1ubuntu2.7
openssl (1.0.1f-1ubuntu2.5) to 1.0.1f-1ubuntu2.7

ps: Tried the posted site initially and got an invalid url warning.
Posted that as an error and found the copied link I posted worked with the same result as initially posted, Poodle showed up.
At the same time, though was logged out somehow from the forum.
Odd beyond normal operator error.

---

### Post by kurt18947 on 2014-10-17
There seems to be a pretty simple fix for Firefox.  Enter 'about:config' in the address bar, search for security.tls.version.min and set the value to '1'. That should disable OpenSSL in Firefox at least.  According to the article I read, the major effect of disabling SSL on web servers is that it will break I.E.6.  Shame, that.

---

### Post by oceola2 on 2014-10-18
Be careful turning on and off various SSL items in browsers.
In some cases it will block ISP home pages or other important sites if they are not up to speed on the changes or only appear to be vulnerable.
In some cases only part of the SSL may be used in conjuction with other items (example: the list under security in Firefox's about:config)
There appears to be some handshaking issues with the SSL items in Firefox so changing settings should be carefully considered.
Experienced blocked access due to some careful SSL item edits and had to reset defaults, prior to this most recent SSL vs Poodle issue..

---

### Post by CharlesA on 2014-10-19
What oceola2 said. In my case, I just turned off SSLv3 on my SSL sites cuz anyone who is using Windows XP and IE6 can just use an updated browser.

Instead of "fixing" this on the client side, let the server operators deal with it.

---

