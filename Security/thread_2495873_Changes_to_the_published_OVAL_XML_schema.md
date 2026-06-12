---
title: "Changes to the published OVAL XML schema"
date: 2024-03-05
forum: Security
---

### Post by thomasnagel on 2024-03-05
Hi, I'm interested in scanning a Ubuntu LTS system for vulnerabilities - I've got a script set up to download the OVAL file from Ubuntu for OpenSCAP to then evaluate against an OS image, and have noticed that sometime within the last week the format has changed such that the USN files (eg [https://security-metadata.canonical.com/oval/com.ubuntu.bionic.usn.oval.xml.bz2](https://security-metadata.canonical.com/oval/com.ubuntu.bionic.usn.oval.xml.bz2)) no longer have CVEs referenced directly, but now only include them in the "description" field. For example, the following is a snippet of the XML output from OpenSCAP (version 1.3.5):

Before:

```
<title>USN-5804-1 -- Linux kernel vulnerabilities</title>
<affected family="unix">
  <platform>Ubuntu 18.04 LTS</platform>
</affected>
<reference source="USN" ref_id="USN-5804-1" ref_url="https://ubuntu.com/security/notices/USN-5804-1"/>
<reference source="CVE" ref_id="CVE-2022-3643" ref_url="https://ubuntu.com/security/CVE-2022-3643"/>
<reference source="CVE" ref_id="CVE-2022-42896" ref_url="https://ubuntu.com/security/CVE-2022-42896"/>
<reference source="CVE" ref_id="CVE-2022-43945" ref_url="https://ubuntu.com/security/CVE-2022-43945"/>
<reference source="CVE" ref_id="CVE-2022-45934" ref_url="https://ubuntu.com/security/CVE-2022-45934"/>
<description>It was discovered that the NFSD implementation in the Linux kernel did not properly handle ...
```

After:
```
<title>USN-5804-1 -- Linux kernel vulnerabilities</title>
<affected family="unix">
  <platform>Ubuntu 18.04 LTS</platform>
</affected>
<reference source="USN" ref_id="USN-5804-1" ref_url="https://ubuntu.com/security/notices/USN-5804-1"/>
<description>It was discovered that the NFSD implementation in the Linux kernel did not properly handle ...

```

For completeness, the OpenSCAP evaluation command I'm running looks like:
```
oscap oval eval --report report.html --results results.xml com.ubuntu.bionic.usn.oval.xml
```
and it's the results.xml file which I've included snippets of above.

Is there something that has led to this change in schema? I'm wanting to link together a USN ID and a CVE ID for a given vulnerability without having to manually parse the description entry, but currently this doesn't seem easily possible. Is there something else I'm missing, or is there a better way to do this?

---

### Post by ebarretto on 2024-03-06
Hi Thomas,

Thanks for reporting this, and indeed this was a bug that got introduced after some code refactoring recently.
I will be working on fixing it today and adding tests for this to not happen again. I will let you know here when it is applied.

Thanks again and sorry for the issue.

---

### Post by ebarretto on 2024-03-06
Hi Thomas,

The fix already landed and I could confirm the fields are added back to the file.
Let us know in case of other issues! 
I appreciate the report, thanks!

---

### Post by thomasnagel on 2024-03-13
Hi ebarretto, I've just checked on my system and it works as before, big thanks for the quick fix! :)

---

