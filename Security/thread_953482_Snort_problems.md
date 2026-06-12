---
title: "Snort problems"
date: 2008-10-20
forum: Security
---

### Post by Drezard on 2008-10-20
I have snort and base installed, connected to a mysql database. (Followed bodhi.zazen's tut at the top). 

I just did a complete Nessus, aggressive scan against the host running snort and base shows nothing. The only thing I can think of is when installing base, i put all the signatures (the weird files name 12342341.txt and 10009293.txt) into my base directory (on the webserver) in a directory called signatures. Am I supposed to put them straight in the base directory on my webserver? 

Daniel

---

### Post by Sarmacid on 2008-10-20
Are you sure snort is running?

```
pgrep -l snort
```

Should return a number and snort.

---

