---
title: "Help with patching PHP in Ubuntu"
date: 2008-02-19
forum: Security Discussions
---

### Post by Gagnefury on 2008-02-19
I would like to upgrade php using prebuilt packages if possible to address the following vulnerabilities outlined here:

[http://www.securityfocus.com/bid/26403](http://www.securityfocus.com/bid/26403)

[http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-4887](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-4887)

I am currently running Ubuntu gutsy for x86. If prebuilt packages are not available, I would appreciate it if someone could guide me through installing from source to replace the existing prepackaged 5.2.3-1ubuntu6.3 that I am currently running. Any help is welcome. I have read that upgrading to latest alpha version of ubuntu will upgrade php to 5.2.4-2ubuntu4 but this version still appears to be vulnerable. ](*,)

---

### Post by honeydew on 2008-02-19
well.. you could see if a deb is available for this file, or you could download the most recent source and install it.  I doubt you would have any dependency issues.. if you already have it installed.

usually information on how to install is under the 

srcdirectory/INSTALL

probably along the lines of configure make make install....

---

### Post by Gagnefury on 2008-02-19
If I am using the prebuilt php that came with Gutsy, should I purge it first before installing php 5.2.5 from source? What would be the safest method of upgrading php? I can't seem to find any 5.2.5 debs for gutsy or hardy

---

### Post by honeydew on 2008-02-19
hrmm... not sure.. I think a installer would install over the old php.. but maybe to be safe remove before hand..  does purge remove dependencies? if so I dont think you should go that route,.. if it removes just config files thats prolly a good way to go..

---

### Post by cdenley on 2008-02-20
It might overwrite the original file, or it might install to a different location. I would suggest removing all the original php packages (a source install would cover several packages), then compile, then install with checkinstall so it can be easily removed or replaced in the future. You might have a problem with build dependencies.

```

sudo apt-get build-dep php5

```

---

### Post by tubezninja on 2008-02-21
Just for reference: aren't the php pre-pacakged bundles for ubuntu patched for security vulnerabilities as well?  I've seen a few patches come up such as this one:

[http://www.ubuntu.com/usn/usn-549-1](http://www.ubuntu.com/usn/usn-549-1)

and also:

[http://www.ubuntu.com/usn/usn-549-2](http://www.ubuntu.com/usn/usn-549-2)

The official PHP release number doesn't change, but the -ubuntu appended version number does. I had thought that the ubuntu dev team were applying their own patches.

---

### Post by cdenley on 2008-02-21
That's what I was going to say, but then I checked the [changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.3-1ubuntu6.2/changelog"), and didn't see a reference to CVE-2007-4887. I didn't find it [here]("http://www.ubuntu.com/usn/") either.

---

### Post by Gagnefury on 2008-02-26
Does anybody know if 5.2.5 is going to be included in Hardy? If not, is there a plan to address CVE-2007-4887 ?

---

### Post by tubezninja on 2008-02-26
Apparently [other distros have already weighed in on the subject]("http://nvd.nist.gov/nvd.cfm?cvename=CVE-2007-4887"):

> Official Statement from Mandriva (9/18/2007)
Because the argument passed to the dl() function are always under the control of the author, Mandriva does not consider this a security issue.

Official Statement from Red Hat (9/14/2007)
The argument passed to the dl() function must always be under the control of the script author. We therefore do not consider this to be a security issue.


---

### Post by Gagnefury on 2008-02-27
> **scaredpoet said:**
> Apparently [other distros have already weighed in on the subject]("http://nvd.nist.gov/nvd.cfm?cvename=CVE-2007-4887"):

Thank you for your reply.

---

