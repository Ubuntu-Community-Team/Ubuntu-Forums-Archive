---
title: "Enigmail not working after upgrade"
date: 2010-11-13
forum: Security
---

### Post by gewitty on 2010-11-13
I recently upgraded to Ubuntu 10.10. This was a clean install, so all packages are up to date.

I'm using Thunderbird 3.1.6 with Enigmail 1.1.2.

Thunderbird works OK, but if I try to create an encrypted message, I get an error saying that the Enigmime module is not available. When I checked the Enigmail 'About Open PGP' details, it showed the following message:

Running Enigmail version 1.1.2 (20100630-0917)

Warning: Enigmime module not available

ERROR: Failed to access Enigmime service!
Enigmime Service not available

I've been searching for an answer to this problem for some time now but cannot come up with a solution. Can anyone tell me what the problem is and how I can sort it out?

---

### Post by chiron80 on 2011-02-11
I don't know if you are still having this problem, but just in case.

I was having this same problem. I just fixed it by first removing (complete removal) the version of enigmail installed from the Ubuntu repositories. I then downloaded Enigmail directly from the website.
[http://enigmail.mozdev.org/download/index.php.html](http://enigmail.mozdev.org/download/index.php.html)

I chose "Linux (x86-64)" and "Thunderbird 3.1" (there were two options, I picked the top one, which was listed as

```
built on Debian squeeze x86_64 with gcc-4.4.3-20100108, comm-1.9.2 tree
Contributed by Jonathan Protzenko <jonathan DOT protzenko AT gmail DOT com>
```

I installed this version directly in Thunderbird, and it worked like a charm.

- Ben

---

### Post by rookcifer on 2011-02-11
> **gewitty said:**
> I recently upgraded to Ubuntu 10.10. This was a clean install, so all packages are up to date.

I'm using Thunderbird 3.1.6 with Enigmail 1.1.2.



Try updating thunderbird.  I am using version 3.1.**7** with Enigmail 1.1.2 and everything works just fine.  

BTW, the thunderbird version I use is in the repos.  No PPA's or compiling required.

---

