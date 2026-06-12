---
title: "warty (security)update components misunderstanding"
date: 2005-04-03
forum: Repositories &amp; Backports
---

### Post by e^pi on 2005-04-03
Hi folks.
Warty brings firefox 0.93 but why dont I get updates when upgrading the system via apt-get upgrade?

[http://www.ubuntulinux.org/ubuntu/components/document_view](http://www.ubuntulinux.org/ubuntu/components/document_view) says:

"When you install software from the main component you are assured that the software will come with security updates and technical support."

Firefox on  Warty is still vulnerable to many securityholes even after upgrading the system. Installing the firefox binaries from the official website is no problem but now I dont understand the ubuntu update philosophy anymore.  [-o<  How can I be sure which packages will be supported and which will not (excl. universe and multiverse packages).

thanks e^pi

---

### Post by clb137 on 2005-04-03
got me there, why do you not upgrade all your system?  Or just download and install it? I do see your point though, however you do have 2 ways of making your system secure.

keep going


clinton

---

### Post by e^pi on 2005-04-03
>why do you not upgrade all your system?

that is what i did:
apt-get update
apt-get -u upgrade
;)
But that >doesnt< fix all firefox securityholes!

Then I installed firefox from the official website (v1.02). Now all "known" ;) bugs are fixed ...
My question is why apt-get upgrade doesnt fix the bugs ...

---

### Post by Buffalo Soldier on 2005-04-03
[QUOTE=e^pi]But that >doesnt< fix all firefox securityholes![/QUOTE]FireFox is in the main and security repository. It does get security fix. Not seeing the version number increases (to 1.x or whatever) does not you're not getting security fixes.

Running the latest version does not mean/guarantee you're having the best for you system in general.

There was a long "discussion" about it here -> [http://ubuntuforums.org/showthread.php?t=21766](http://ubuntuforums.org/showthread.php?t=21766)

---

### Post by e^pi on 2005-04-03
>FireFox is in the main and security repository.

yes thats my "problem" ... thats the point! 

>It does get security fix.

would you try out one of these exploits :
[http://www.heise.de/security/dienste/browsercheck/demos/nc/](http://www.heise.de/security/dienste/browsercheck/demos/nc/)

There is also no ubuntu security notice about Firefox :
[http://www.ubuntulinux.org/support/documentation/usn/errorreferencefolder_view](http://www.ubuntulinux.org/support/documentation/usn/errorreferencefolder_view)


>Not seeing the version number increases (to 1.x or whatever) does not you're not getting security fixes.

yes I know

---

### Post by Buffalo Soldier on 2005-04-03
ermm the sites you gave me is in german? the only word i see in english is "sponsored by Microsoft".

---

### Post by e^pi on 2005-04-03
sponsored by Microsoft  :-k  

However ... what about "firescrolling"?
[http://www.mikx.de/firescrolling/](http://www.mikx.de/firescrolling/)

Or this one:
[http://secunia.com/multiple_browsers_window_injection_vulnerability_test/](http://secunia.com/multiple_browsers_window_injection_vulnerability_test/)

Or this:
[http://archives.neohapsis.com/archives/fulldisclosure/2004-12/0160.html](http://archives.neohapsis.com/archives/fulldisclosure/2004-12/0160.html)

---

### Post by Buffalo Soldier on 2005-04-03
Yeah, I think you're right.

I was unable to scroll the "firescrolling" page, passed the secunia test, haven't tried the last test.

---

### Post by nocturn on 2005-04-04
An update to 1.0.x is out of the scope of Warty, but I agree with you, there where no backported security fixes on the warty version, I hope this improves in Hoary (which currently has 1.0.2).

---

### Post by e^pi on 2005-04-04
yes but how do I know that firefox is the only package that doesnt get security updates although its in main component? I`m a little confused about that. Like I said, installing firefox by my own is no big problem but I need to know which packages wont be supported! How can I figure that out? I dont want an insecure System  :cry: Or would you say firefox is the only non-updated package? Thats strage isnt it?
thanks anyway greetings e^pi

---

### Post by e^pi on 2005-04-04
ok this is what I found
[https://bugzilla.ubuntu.com/show_bug.cgi?id=4679](https://bugzilla.ubuntu.com/show_bug.cgi?id=4679)

> This is marked as a critical security bug, and has been open for over a month
> now.  What is its status?

This issue is fixed in FireFox 1.0.1 and Mozilla 1.7.6, both are supposed to be
packaged for Hoary.

Warty is a difficult issue, though. The proposed patch is huuuge and does not
apply at all to 0.9.3 (Thom already tried in vain for hours). Thus I have no
idea how this could be fixed in Warty.

---

