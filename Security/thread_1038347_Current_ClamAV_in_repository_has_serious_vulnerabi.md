---
title: "Current ClamAV in repository has serious vulnerabilities"
date: 2009-01-12
forum: Security
---

### Post by gracedman on 2009-01-12
Hello, all.  I have clamav installed on my fully patched Ubuntu 8.0.4.  I've just completed an OpenVAS scan for vulnerabilities and it returned the following:

Reported by NVT "ClamAV < 0.93.1 vulnerability" (1.3.6.1.4.1.25623.1.0.90000):

The remote host is probably affected by the vulnerabilities described in
CVE 2007-6335 CVE 2007-6336 CVE 2007-6337 CVE-2008-0318 CVE-2008-1100 CVE-2008-1387 CVE-2008-2713

Impact
   CVE 2008-2713
     libclamav/petite.c in ClamAV before 0.93.1 allows remote attackers to
     cause a denial of service via a crafted Petite file that triggers an
     out-of-bounds read. 
   CVE 2008-1387
     ClamAV before 0.93 allows remote attackers to cause a denial of service
     (CPU consumption) via a crafted ARJ archive, as demonstrated by the 
     PROTOS GENOME test suite for Archive Formats.
   CVE 2008-1100
     Buffer overflow in the cli_scanpe function in libclamav (libclamav/pe.c)
     for ClamAV 0.92 and 0.92.1 allows remote attackers to execute 
     arbitrary code via a crafted Upack PE file.
   CVE 2008-0318
     Integer overflow in the cli_scanpe function in libclamav in 
     ClamAV before 0.92.1, as used in clamd, allows remote attackers 
     to cause a denial of service and possibly execute arbitrary code
     via a crafted Petite packed PE file, which triggers a heap-based 
     buffer overflow.
   CVE 2007-6337
     Unspecified vulnerability in the bzip2 decompression algorithm
     in nsis/bzlib_private.h in ClamAV before 0.92 has unknown impact
     and remote attack vectors.
   CVE 2007-6336
     Off-by-one error in ClamAV before 0.92 allows remote attackers
     to execute arbitrary code via a crafted MS-ZIP compressed CAB file.
   CVE 2007-6335
     Integer overflow in libclamav in ClamAV before 0.92 allows remote
      attackers to execute arbitrary code via a crafted MEW packed
      PE file, which triggers a heap-based buffer overflow.


References:
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-2713](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-2713)
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-1387](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-1387)
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-1100](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-1100)
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-0318](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-0318)
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-6337](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-6337)
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-6336](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-6336)
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-6335](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-6335)

Solution:
    All ClamAV users should upgrade to the latest version:


Risk factor : High


The current repository version appears to be 0.92.1 whereas the latest clamav version is 0.94.2.  Are there any plans to update the repository as I hate to bypass it for updates.  Thanks - John

---

### Post by bodhi.zazen on 2009-01-12
> **gracedman said:**
> Hello, all.  I have clamav installed on my fully patched Ubuntu 8.0.4.  I've just completed an OpenVAS scan for vulnerabilities and it returned the following:

Reported by NVT "ClamAV < 0.93.1 vulnerability" (1.3.6.1.4.1.25623.1.0.90000):

The remote host is probably affected by the vulnerabilities described in
CVE 2007-6335 CVE 2007-6336 CVE 2007-6337 CVE-2008-0318 CVE-2008-1100 CVE-2008-1387 CVE-2008-2713

Impact
   CVE 2008-2713
     libclamav/petite.c in ClamAV before 0.93.1 allows remote attackers to
     cause a denial of service via a crafted Petite file that triggers an
     out-of-bounds read. 
   CVE 2008-1387
     ClamAV before 0.93 allows remote attackers to cause a denial of service
     (CPU consumption) via a crafted ARJ archive, as demonstrated by the 
     PROTOS GENOME test suite for Archive Formats.
   CVE 2008-1100
     Buffer overflow in the cli_scanpe function in libclamav (libclamav/pe.c)
     for ClamAV 0.92 and 0.92.1 allows remote attackers to execute 
     arbitrary code via a crafted Upack PE file.
   CVE 2008-0318
     Integer overflow in the cli_scanpe function in libclamav in 
     ClamAV before 0.92.1, as used in clamd, allows remote attackers 
     to cause a denial of service and possibly execute arbitrary code
     via a crafted Petite packed PE file, which triggers a heap-based 
     buffer overflow.
   CVE 2007-6337
     Unspecified vulnerability in the bzip2 decompression algorithm
     in nsis/bzlib_private.h in ClamAV before 0.92 has unknown impact
     and remote attack vectors.
   CVE 2007-6336
     Off-by-one error in ClamAV before 0.92 allows remote attackers
     to execute arbitrary code via a crafted MS-ZIP compressed CAB file.
   CVE 2007-6335
     Integer overflow in libclamav in ClamAV before 0.92 allows remote
      attackers to execute arbitrary code via a crafted MEW packed
      PE file, which triggers a heap-based buffer overflow.


References:
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-2713](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-2713)
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-1387](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-1387)
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-1100](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-1100)
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-0318](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-0318)
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-6337](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-6337)
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-6336](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-6336)
    [http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-6335](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2007-6335)

Solution:
    All ClamAV users should upgrade to the latest version:


Risk factor : High


The current repository version appears to be 0.92.1 whereas the latest clamav version is 0.94.2.  Are there any plans to update the repository as I hate to bypass it for updates.  Thanks - John

You should probably file a bug report with this information on Launchpad rather then the forums.

---

