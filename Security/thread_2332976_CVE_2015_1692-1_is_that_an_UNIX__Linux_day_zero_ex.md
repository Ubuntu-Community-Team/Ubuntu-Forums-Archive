---
title: "CVE_2015_1692-1 is that an UNIX / Linux day zero exploit number?"
date: 2016-08-05
forum: Security
---

### Post by xenon3 on 2016-08-05
I can't imagine they number day zero exploits all through the open  source software, like a CVE number can be for GIMP, LIBREOFFICE,  (Ubuntu) LINUX, FireFox etc.

Could be an exploit of LINUX through FireFox, since its an HTML exploit?

One LINUX exploit I know has an CVE number (the exploit also has code name "Ghost")

[https://securityintelligence.com/ghost-in-the-machine-linux-zero-day-vulnerability-opens-door-for-attack/](https://securityintelligence.com/ghost-in-the-machine-linux-zero-day-vulnerability-opens-door-for-attack/)

---

### Post by QIII on 2016-08-05
"CVE" comes from the US Homeland Security Department's catalog of "Common Vulnerabilities and Exposures".  It's not a "Linux thing".

---

### Post by xenon3 on 2016-08-05
> **QIII said:**
> "CVE" comes from the US Homeland Security Department's catalog of "Common Vulnerabilities and Exposures".  It's not a "Linux thing".


On Tuesday, Jan. 27, a zero-day vulnerability (CVE-2015-0235) was  disclosed in the Linux operating system that allows malicious code to be  executed on servers that use the GNU C Library (glibc) functionality.  Linux programs that contain glibc are also affected. The specific call,  gethostbyname(), can be triggered by any type of Domain Name System  (DNS) resolution within the code, although the primary effect is on  systems that accept host names from clients and attempt to resolve them  through DNS. In reference to the GetHOST functionality, the  vulnerability has been nicknamed “Ghost.”

---

### Post by QIII on 2016-08-05
That happens to be a CVE that applies to Linux.  Others apply to Windows.  Others apply to software.  Others apply to cell phones.  Etc.

---

### Post by xenon3 on 2016-08-05
> **QIII said:**
> That happens to be a CVE that applies to Linux.  Others apply to Windows.  Others apply to software.  Others apply to cell phones.  Etc.


[h=2]Could CVE_2015_1692-1 also happen to apply to LINUX?[/h]

---

### Post by QIII on 2016-08-05
This comes from a pretty good resource:  [https://www.cvedetails.com/google-search-results.php?q=+CVE_2015_1692&sa=Search](https://www.cvedetails.com/google-search-results.php?q=+CVE_2015_1692&sa=Search)

Could it affect Linux?  Likely not from the looks of it.

---

### Post by xenon3 on 2016-08-05
> **QIII said:**
> This comes from a pretty good resource:  [https://www.cvedetails.com/google-search-results.php?q=+CVE_2015_1692&sa=Search](https://www.cvedetails.com/google-search-results.php?q=+CVE_2015_1692&sa=Search)

Could it affect Linux?  Likely not from the looks of it.

Not wanting to bother you but this CVE_2015_1692 not CVE_2015_1692-1 which is not in that database, however is very unlikely that when CVE_2015_1692 is for Internet Explorer and CVE_2015_1692-1 is for FireFox, but I can't rule that out

Thanks anyway

PS: I thought it could be an LINUX exploit through FireFox messing with the HTML Compiler

---

### Post by cariboo on 2016-08-06
Ubuntu has it's own Security Notice page, available [here]("http://www.ubuntu.com/usn/").

---

### Post by xenon3 on 2016-08-06
> **cariboo said:**
> Ubuntu has it's own Security Notice page, available [here]("http://www.ubuntu.com/usn/").

Nice now I got all UBUNTU exploits :smile: are CVE numbers the same as USN? Then I got it: [http://www.ubuntu.com/usn/usn-1692-1/](http://www.ubuntu.com/usn/usn-1692-1/)

Could very well be the same, because it makes the system crash and freeze

---

### Post by SeijiSensei on 2016-08-06
That very link you posted, [http://www.ubuntu.com/usn/usn-2485-1/](http://www.ubuntu.com/usn/usn-2485-1/), shows that the vulnerability does not exist in versions after 12.04LTS and was patched in 10.04 and 12.04.  14.04 and beyond include C libraries that have already been patched against the vulnerability.  See [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GHOST](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GHOST).

---

### Post by xenon3 on 2016-08-07
> **SeijiSensei said:**
> That very link you posted, [http://www.ubuntu.com/usn/usn-2485-1/](http://www.ubuntu.com/usn/usn-2485-1/), shows that the vulnerability does not exist in versions after 12.04LTS and was patched in 10.04 and 12.04.  14.04 and beyond include C libraries that have already been patched against the vulnerability.  See [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GHOST](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GHOST).

Thanks, do you think CVE_2015_1692-1 is a LINUX zero day exploit number? Only clue I have that USN-1692-1 is, I cannot find the CVE in any database, however CVE_2015_1692 is an Internet Explorer hack

---

### Post by SeijiSensei on 2016-08-07
It certainly looks like 2015-1692 is an IE exploit.  USN-1692-1 is a vulnerability in the [QEMU virtualization software]("http://wiki.qemu.org/Main_Page") that dates back to 2013.  It has nothing to do with the vulnerabilities in 2015-1692 which affect the C libraries.

I don't why you think this is some "zero-day" exploit.  Is it the 1692-1 designation?  I know of no CVEs with a "-1" at the end.  It seems pretty obvious that the numbering scheme used by Ubuntu doesn't correspond to the scheme used by Mitre for CVEs.

---

### Post by Habitual on 2016-08-08
Where are you getting these CVE references?
I usually search [https://web.nvd.nist.gov/view/vuln/search](https://web.nvd.nist.gov/view/vuln/search) for Common Vulns

---

### Post by xenon3 on 2016-08-08
> **Habitual said:**
> Where are you getting these CVE references?
I usually search [https://web.nvd.nist.gov/view/vuln/search](https://web.nvd.nist.gov/view/vuln/search) for Common Vulns

CLAMTK:

> **SeijiSensei said:**
> It certainly looks like 2015-1692 is an IE exploit.  USN-1692-1 is a vulnerability in the [QEMU virtualization software]("http://wiki.qemu.org/Main_Page") that dates back to 2013.  It has nothing to do with the vulnerabilities in 2015-1692 which affect the C libraries.

I don't why you think this is some "zero-day" exploit.  Is it the 1692-1  designation?  I know of no CVEs with a "-1" at the end.  It seems  pretty obvious that the numbering scheme used by Ubuntu doesn't  correspond to the scheme used by Mitre for CVEs.

Found 3 possible threats (16631 files scanned).

/home/kingdom/.cache/mozilla/firefox/aqh4dyo8.default/cache2/entries/815B44C98D0E4A46439EA7FCF6F3446185E8881A       PUA.Win.Tool.Packed-178              
/home/kingdom/.cache/mozilla/firefox/aqh4dyo8.default/cache2/entries/A6C802A807F83E69366253EB093BAE09083748E7       PUA.Html.Exploit.CVE_2015_1692-1     
/home/kingdom/.cache/mozilla/firefox/aqh4dyo8.default/cache2/entries/58F6DB7F45CF6156837EF06B84C151BFE897DF46       PUA.Html.Exploit.CVE_2014_0322-1     

---
...the frog jumps, watersound...

---

### Post by Habitual on 2016-08-08
You need to clean your browser cache?

---

### Post by xenon3 on 2016-08-24
> **Habitual said:**
> You need to clean your browser cache?

OK! I remove them with CLAMTK, but there could be more bad stuff in the cache CLAMTK does not see.

Question remains are the CVE's lethal to the system when they remain there (or do malicious things)? CVE's like in the subject I get 2 or 3 of them practically every day.

---

### Post by Habitual on 2016-08-24
You can leave them there, if you like.
They are after all, only Potentially Unwanted Applications

clam hits on my Lenovo Stuff I downloaded 8 years ago, and it's still on my drive.
```
rm -fr /home/kingdom/.cache/mozilla/firefox/
```
clamscan again.

fire up Firefox
clamscan again.

Let us know.

---

### Post by xenon3 on 2016-08-25
> **Habitual said:**
> You can leave them there, if you like.
They are after all, only Potentially Unwanted Applications

clam hits on my Lenovo Stuff I downloaded 8 years ago, and it's still on my drive.
```
rm -fr /home/kingdom/.cache/mozilla/firefox/
```
clamscan again.

fire up Firefox
clamscan again.

Let us know.

Yes they are all gone, thanks, is the cache directory the only for the internet accessible directory? Of the whole $HOME file system?

---

### Post by Habitual on 2016-08-25
> **xenon3 said:**
> Yes they are all gone, thanks, is the cache directory the only for the internet accessible directory? Of the whole $HOME file system?

Using the system should have no effect from running this firefox cache "cleaning" command.
It's not a filesystem operation.

---

