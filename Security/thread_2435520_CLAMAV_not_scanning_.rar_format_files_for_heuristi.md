---
title: "CLAMAV not scanning .rar format files for heuristics"
date: 2020-01-22
forum: Security
---

### Post by vijkuma on 2020-01-22
Using version : 0.102.1
Command : clamscan test.rar --max-files=1 --heuristic-alerts=yes --heuristic-scan-precedence=yes --alert-exceeds-max=yes

When this command is ran on Mac machine (same version of clamav), it returns "Heuristics.Limits.Exceeded FOUND" whereas same command on Ubuntu clamav marks the file as passed.
Also, if a zip format file is used. Proper error is returned on both mac and ubuntu.

Is this a known issue ? Is there any workaround ?

---

### Post by CelticWarrior on 2020-01-22
Have you installed RAR support? If not then is entirely understandable that ClamAV can't open and consequently can't test rar files.

---

### Post by johnsingam on 2020-01-23
I think ClamAV never scan a rar file as default. Its need some extra extensions get installed.

---

### Post by SeijiSensei on 2020-01-23
I'm going to take a guess and say you probably need to install libclamunrar9 from the repositories. "apt-cache search clamav" returns libclamunrar9 with the description, "anti-virus utility for Unix - unrar support."

Unlike open compression formats like GZIP, RAR is [proprietary](https://en.wikipedia.org/wiki/RAR_(file_format)). ZIP was once proprietary but was [released into the public domain]("https://en.wikipedia.org/wiki/Zip_(file_format)#History") in 1989.

---

