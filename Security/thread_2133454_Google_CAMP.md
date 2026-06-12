---
title: "Google CAMP"
date: 2013-04-08
forum: Security
---

### Post by mike acker on 2013-04-08
I have often wondered,-- to what level does a browser browse thru the user's system and report back what it finds ?

suggested reading
[http://www.darkreading.com/security-monitoring/167901086/security/client-security/240152413/google-uses-reputation-to-detect-malicious-downloads.html](http://www.darkreading.com/security-monitoring/167901086/security/client-security/240152413/google-uses-reputation-to-detect-malicious-downloads.html)

i would dearly love to find detailed info on the AppArmor that we use on Firefox here --
i suspect we need to use that to keep the browser from reporting the entire content of our computers back to the browser owners and heaven only knows who else. most likely anyone with money

---

### Post by mike acker on 2013-04-09
such an analysis is guaranteed to be ineffective  . as we know a good root kit hides from any analysis launched from an app program running under the infected o/s by
[LIST]
[*]modifying directory services so that the presence of the un-authorized program(s) is not reported 
[*]modifying directory services such that the space taken by the un-authorized programming is added back into the reported free DASD space 
[*]keeping original copies of improperly modified programs in hidden places so that if any dump or analysis of the affected programs is requested the original un-modified copy of the affected program is supplied in place of the one that is actually in service
[*]alter the system such that any attempt to update/replace affected programs only updates/replaces the original hidden and out of service copies of infected programs not the infected copies that are actually being used by the system . 
[/LIST]

understanding this we realize that scanning an o/s for un-authorized programs from an app program -- or any program running under control of the infected o/s is going to be ineffective

which leads us to the question:

what is "CAMP" really looking for?  is it just a clumsy attempt at virus hunting?  from Google?  One would not think so.  Is it a "quick and dirty" solution intended to take out the "low hanging fruit" knowing full well that it is not a real solution ?  possible.  it is an excuse to collect intel from user systems? i do not rule that out .

---

### Post by cariboo on 2013-04-11
That seems to me to be another reason not to use chrome.

---

