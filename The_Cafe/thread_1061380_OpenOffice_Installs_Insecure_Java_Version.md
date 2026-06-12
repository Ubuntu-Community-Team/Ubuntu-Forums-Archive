---
title: "OpenOffice Installs Insecure Java Version"
date: 2009-02-05
forum: The Cafe
---

### Post by newbie2 on 2009-02-05
from Brian Krebs on Computer Security :
> An alert reader let me know that the latest version of OpenOffice, the open source alternative to the Microsoft Office productivity suite, also installs a very old, insecure version of Java.

Users who accept the default installation options for OpenOffice 3.0.1 also will get Java 6 Update 7, a version of Java that Sun Microsystems released last spring (the latest version is Java 6 Update 12).
[http://voices.washingtonpost.com/securityfix/2009/02/openoffice_installs_insecure_j.html](http://voices.washingtonpost.com/securityfix/2009/02/openoffice_installs_insecure_j.html)
:rolleyes:

---

### Post by jrusso2 on 2009-02-05
I think the happens with the Windows version but I think the Linux one uses the installed Java not a static linked one.

---

### Post by Polygon on 2009-02-05
its most likely a bug on their part. but i dont think the windows version is static-linked either, because all that does is just download the java installer and runs it when your setting up open office. Once people install that old version of java, java will bug them to upgrade to the latest version.

---

### Post by adamlau on 2009-02-06
OO from the Arch Linux repos do not include Java as a dependency, but as an optional dep :) .

---

### Post by jespdj on 2009-02-06
> a very old, insecure version of Java
This is highly exaggerated. Sun Java 6 update 7 is not a "very old" nor "insecure" version of Java. In fact, it is the version of Sun Java 6 that's still in the Hardy repository today. If it really were insecure, then there would have been a newer version in the repository.

Note that there haven't been updates 8 and 9 - Sun jumped from update 7 to update 10 with their Java.

Java 6 update 12 has been out for just a few days.

---

### Post by disturbed1 on 2009-02-06
Here's one of many security flaws that were not fixed until JRE 6 update 11
[http://sunsolve.sun.com/search/document.do?assetkey=1-66-244990-1](http://sunsolve.sun.com/search/document.do?assetkey=1-66-244990-1) 
if you need more flaws -
[http://securitytracker.com/alerts/2009/Jan/1021589.html](http://securitytracker.com/alerts/2009/Jan/1021589.html)

Hardy (Ubuntu in general) isn't *_**that**_* up to date on security ;) It still has Firefox 3.0.5, openssl 0.9.8g and Bind 9.4.2_P2, even Slackware has FF 3.0.6, openssl 0.9.8i and Bind 9.4.3_P1 
[SIZE=-1] [https://www.isc.org/node/373](https://www.isc.org/node/373)
       [http://www.ocert.org/advisories/ocert-2008-016.html](http://www.ocert.org/advisories/ocert-2008-016.html)
       [http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-5077](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-5077)
       [http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2009-0025](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2009-0025) 

[/SIZE]Bind and openssl where patched on Jan 14 2009.

---

