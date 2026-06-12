---
title: "Security Flaw On Ubuntu?"
date: 2014-06-13
forum: Security
---

### Post by tomsubt on 2014-06-13
Hello Everyone, I just got an artical from worldstart newsletter about a flaw in Linux, I could not
open it to read the whole article for some reason but anyway here is what I was able to copy and paste >>>>   Patches Available For Linux Security Flaw

Patches are now available for what experts are calling a “moderately serious” issue that effects Linux Ubuntu, Debian and some Red Hat operating systems.  The flaw could be exploited and allow someone to launch a denial of service attack or gain privileges to a system and even crash it. 

The flaw has been there for awhile, it came about as the result of changes made in 2009, but has only recently been discovered. Ubuntu patch details are here.  You can find
 information about the patches for other systems by going to their websites.

Does anyone know about this flaw and where can I get it patched, since I could not get to there link?   Thank You  PS here is the article>>>

[http://www.worldstart.com/newsletters.php/computer_tips/2014-06-13](http://www.worldstart.com/newsletters.php/computer_tips/2014-06-13)

---

### Post by TheFu on 2014-06-13
I won't be clicking on some random website I've never heard of based on 4 non-specific paragraphs.

**Patches available** pretty much covers it for me. Distros have it covered. The only people who should be worried about this stuff are people making distros that are** not upstream** from the main distros.

There are always security issues being patched. ALWAYS. CERT publishes reported issues daily with the expected fix date for Linux and Microsoft platforms (perhaps more). Every major distro has their own filtered security RSS feed - feel free to follow the [ubuntu one.]("http://www.ubuntu.com/usn/")

---

### Post by Habitual on 2014-06-13
> **TheFu said:**
> I won't be clicking on some random website I've never heard of based on 4 non-specific paragraphs.

Good advise. and poorly formatted links to [http://people.canonical.com/~ubuntu-security/cve/2014/CVE-2014-0196.html](http://people.canonical.com/~ubuntu-security/cve/2014/CVE-2014-0196.html) doesn't help the end user.

Flaw details are at [http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-0196](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-0196)
which leads to [http://www.ubuntu.com/usn/USN-2204-1/](http://www.ubuntu.com/usn/USN-2204-1/)

With Security, facts are important and poorly written articles without them are "click bait" IMO.
I'd un-signup from worldstart mailings myself.

---

### Post by tomsubt on 2014-06-13
Ok, Thanks anyway

---

### Post by Nobody Nessie on 2014-06-18
What I have done is "apt-get update" !

---

### Post by tomsubt on 2014-06-18
nessie2,   Will do,  ThankYou

---

### Post by buzzingrobot on 2014-06-18
Remember that a newly discovered potential security flaw is not the same thing as a newly discovered *exploited* security flaw, in any OS.

The computer media often sensationalizes these stories to attract more clicks and more ad revenue.

Ubuntu, and other distros, maintain security mailing lists you can join if you want to follow security issues.

---

### Post by tomsubt on 2014-06-18
Yeah I never thought of it, when I saw security flaw, I guess I got over excited and did not think of the difference you stated, also I will try to get on the security mailing list, Thank You

---

### Post by nuts2 on 2014-08-01
[COLOR=#000000][FONT=Verdana]The n_tty_write function in drivers/tty/n_tty.c in the Linux kernel through 3.14.3 does not properly manage tty driver access in the "LECHO & !OPOST" case, which allows **local** users to cause a denial of service (memory corruption and system crash) or gain privileges by triggering a race condition involving read and write operations with long strings.[/FONT][/COLOR]

---

