---
title: "file grep question"
date: 2010-03-17
forum: Server Platforms
---

### Post by mewrei on 2010-03-17
I've been using grep to run a few PII scans and while its finding results, its indeed finding too many false positives.

Is there a way that I can tell grep not to trigger a match for a file unless it contains other data?

For instance, can I tell it not to trigger an alert on a regex for a SSN unless the file includes text like "ssn" or "social security number" somewhere else in the file?

---

### Post by jrssystemsnet on 2010-03-17
> **mewrei said:**
> For instance, can I tell it not to trigger an alert on a regex for a SSN unless the file includes text like "ssn" or "social security number" somewhere else in the file?

```
grep -l "ssn" * | xargs -I% grep -l "social security number" %
```

The above would look through all files in the current directory, and return the filenames of any files that contained both "ssn" and "social security number" in the file.

```
grep -l "ssn" * | xargs -I% grep "social security number" %
```

The above would do the same, except instead of returning just filenames, would return the filename AND any lines matching "social security number".

---

### Post by KB1JWQ on 2010-03-17
It might be easier with perl if you end up going TOO deep into regular expressions...

---

### Post by mewrei on 2010-03-19
> **KB1JWQ said:**
> It might be easier with perl if you end up going TOO deep into regular expressions...

Yeah you're probably right there.  I was hoping this was going to be relatively simple, but it doesn't look to be so.

---

